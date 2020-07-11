---
title: 고가용성 페더레이션 인증 4 단계 웹 응용 프로그램 프록시 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: '요약: Microsoft Azure에서 Microsoft 365에 대 한 고가용성 페더레이션 인증용 웹 응용 프로그램 프록시 서버를 구성 합니다.'
ms.openlocfilehash: 005497f9da7986fb4538b4d4c9699e55fe26fa65
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102496"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="fd6dd-103">고가용성 페더레이션 인증 4단계: 웹 응용 프로그램 프록시 구성</span><span class="sxs-lookup"><span data-stu-id="fd6dd-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

<span data-ttu-id="fd6dd-104">Azure 인프라 서비스에서 Microsoft 365 페더레이션 인증을 위해 고가용성을 배포 하는이 단계에서는 내부 부하 분산 장치 및 두 개의 AD FS 서버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="fd6dd-105">[5 단계: Microsoft 365에 대 한 페더레이션 인증 구성](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)에서 이동 하기 전에이 단계를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-105">You must complete this phase before moving on to [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="fd6dd-106">모든 단계에 대 한 자세한 내용은 [Azure에서 Microsoft 365에 대 한 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="fd6dd-107">Azure에서 인터넷 부하 분산 장치를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-107">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="fd6dd-108">Azure가 인터넷에서 수신되는 클라이언트 인증 트래픽을 두 웹 응용 프로그램 프록시 서버에 균등하게 분배할 수 있도록 인터넷 부하 분산 장치를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-108">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="fd6dd-109">다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-109">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="fd6dd-110">[Azure PowerShell을 시작 하기를](https://docs.microsoft.com/powershell/azure/get-started-azureps)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-110">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="fd6dd-111">위치나 리소스 그룹 값이 제공되면 Azure PowerShell 명령 프롬프트나 PowerShell ISE에서 결과 블록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-111">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="fd6dd-112">사용자 지정 설정에 따라 실행 가능한 PowerShell 명령 블록을 생성 하려면이 [Microsoft Excel 구성 통합 문서](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-112">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="fd6dd-113">로컬 컴퓨터에 있는 Azure PowerShell 명령 프롬프트의 다음 명령을 실행하여 인터넷 부하 분산 장치에 할당된 공용 IP 주소를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-113">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="fd6dd-114">페더레이션 서비스 FQDN을 확인하고 DNS 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-114">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="fd6dd-115">인터넷에서 페더레이션 서비스 이름을 식별 하기 위한 DNS 이름을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-115">You need to determine the DNS name to identify your federation service name on the Internet.</span></span> <span data-ttu-id="fd6dd-116">Azure AD Connect는 5 단계에서 Microsoft 365를 구성 하 고,이 이름은 Microsoft 365에서 보안 토큰을 가져오기 위해 연결 하는 데 사용 하는 URL의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-116">Azure AD Connect will configure Microsoft 365 with this name in Phase 5, which will become part of the URL that Microsoft 365 sends to connecting clients to get a security token.</span></span> <span data-ttu-id="fd6dd-117">예를 들면 fs.contoso.com (fs for federation service)입니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-117">An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="fd6dd-118">페더레이션 서비스 FDQN이 있으면 Azure 인터넷 연결 부하 분산 장치의 공용 IP 주소로 확인되는 페더레이션 서비스 FDQN의 공용 DNS 도메인 A 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-118">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="fd6dd-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-119">**Name**</span></span>|<span data-ttu-id="fd6dd-120">**종류**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-120">**Type**</span></span>|<span data-ttu-id="fd6dd-121">**TTL**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-121">**TTL**</span></span>|<span data-ttu-id="fd6dd-122">**값**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-122">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="fd6dd-123">페더레이션 서비스 FDQN</span><span class="sxs-lookup"><span data-stu-id="fd6dd-123">federation service FDQN</span></span>  <br/> |<span data-ttu-id="fd6dd-124">A</span><span class="sxs-lookup"><span data-stu-id="fd6dd-124">A</span></span>  <br/> |<span data-ttu-id="fd6dd-125">3600</span><span class="sxs-lookup"><span data-stu-id="fd6dd-125">3600</span></span>  <br/> |<span data-ttu-id="fd6dd-126">Azure 인터넷 부하 분산 장치의 공용 IP 주소(이전 섹션에서 **Write-Host** 명령으로 표시됨)</span><span class="sxs-lookup"><span data-stu-id="fd6dd-126">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="fd6dd-127">예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-127">Here is an example:</span></span>
  
|<span data-ttu-id="fd6dd-128">**이름**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-128">**Name**</span></span>|<span data-ttu-id="fd6dd-129">**종류**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-129">**Type**</span></span>|<span data-ttu-id="fd6dd-130">**TTL**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-130">**TTL**</span></span>|<span data-ttu-id="fd6dd-131">**값**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-131">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="fd6dd-132">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fd6dd-132">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="fd6dd-133">A</span><span class="sxs-lookup"><span data-stu-id="fd6dd-133">A</span></span>  <br/> |<span data-ttu-id="fd6dd-134">3600</span><span class="sxs-lookup"><span data-stu-id="fd6dd-134">3600</span></span>  <br/> |<span data-ttu-id="fd6dd-135">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="fd6dd-135">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="fd6dd-136">그런 다음 조직의 개인 DNS 네임스페이스에 DNS 주소 레코드를 추가하여 페더레이션 서비스 FQDN을 AD FS 서버의 내부 부하 분산 장치에 할당된 개인 IP 주소로 확인합니다(표 I, 항목 4, 값 열).</span><span class="sxs-lookup"><span data-stu-id="fd6dd-136">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="fd6dd-137">Azure에서 웹 응용 프로그램 프록시 서버 가상 컴퓨터 만들기</span><span class="sxs-lookup"><span data-stu-id="fd6dd-137">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="fd6dd-138">다음 Azure PowerShell 명령 블록을 사용하여 두 웹 응용 프로그램 프록시 서버의 가상 컴퓨터를 만듭니다. </span><span class="sxs-lookup"><span data-stu-id="fd6dd-138">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="fd6dd-139">다음 Azure PowerShell 명령 집합은 다음 테이블의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-139">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="fd6dd-140">테이블 M, 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="fd6dd-140">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="fd6dd-141">테이블 R, 리소스 그룹</span><span class="sxs-lookup"><span data-stu-id="fd6dd-141">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="fd6dd-142">테이블 V, 가상 네트워크 설정</span><span class="sxs-lookup"><span data-stu-id="fd6dd-142">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="fd6dd-143">테이블 S, 서브넷</span><span class="sxs-lookup"><span data-stu-id="fd6dd-143">Table S, for your subnets</span></span>
    
- <span data-ttu-id="fd6dd-144">테이블 I, 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="fd6dd-144">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="fd6dd-145">테이블 A, 가용성 집합</span><span class="sxs-lookup"><span data-stu-id="fd6dd-145">Table A, for your availability sets</span></span>
    
<span data-ttu-id="fd6dd-146">[2 단계: 도메인 컨트롤러](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 와 테이블 R, V, S, I, A를 [1 단계: configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)에서 정의한 표 M을 정의 했습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-146">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="fd6dd-147">모든 적절한 값이 제공되면 Azure PowerShell 명령 프롬프트나 PowerShell ISE에서 결과 블록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-147">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="fd6dd-148">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-148">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="fd6dd-149">However, this also means that you cannot connect to them from the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-149">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="fd6dd-150">The **Connect** option is unavailable when you view the properties of the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-150">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="fd6dd-151">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-151">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="fd6dd-152">이 단계를 성공적으로 완료하면 자리 표시자 컴퓨터 이름과 함께 이 구성을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-152">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="fd6dd-153">**4단계: Azure의 고가용성 페더레이션 인증 인프라용 인터넷 부하 분산 장치 및 웹 응용 프로그램 프록시 서버**</span><span class="sxs-lookup"><span data-stu-id="fd6dd-153">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![웹 응용 프로그램 프록시 서버를 사용 하 여 Azure의 고가용성 Microsoft 365 페더레이션 인증 인프라 4 단계](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="fd6dd-155">다음 단계</span><span class="sxs-lookup"><span data-stu-id="fd6dd-155">Next step</span></span>

<span data-ttu-id="fd6dd-156">[5 단계: Microsoft 365에 대 한 페더레이션 인증 구성](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) 을 사용 하 여이 작업을 계속 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6dd-156">Use [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fd6dd-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd6dd-157">See Also</span></span>

[<span data-ttu-id="fd6dd-158">Azure에서 Microsoft 365용 고가용성 페더레이션 인증 배포</span><span class="sxs-lookup"><span data-stu-id="fd6dd-158">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="fd6dd-159">Microsoft 365 개발/테스트 환경용 페더레이션 id</span><span class="sxs-lookup"><span data-stu-id="fd6dd-159">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="fd6dd-160">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="fd6dd-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

