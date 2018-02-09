---
title: "고가용성 페더레이션 인증 단계 4 구성 웹 응용 프로그램 프록시"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "요약: Microsoft Azure의 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 웹 응용 프로그램 프록시 서버를 구성 합니다."
ms.openlocfilehash: 3465281c6ba27c52cc7a991e400fb4f4a892b244
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="b3c7b-103">고가용성 페더레이션 인증 4단계: 웹 응용 프로그램 프록시 구성</span><span class="sxs-lookup"><span data-stu-id="b3c7b-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="b3c7b-104">**요약:** Microsoft Azure의 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 웹 응용 프로그램 프록시 서버를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="b3c7b-105">이 단계에서는 Azure 인프라 서비스의 Office 365 페더레이션 인증의 고가용성을 배포하며 내부 부하 분산 장치 및 두 개의 AD FS 서버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="b3c7b-p101">레코드로 이동 하기 전에이 단계를 완료 해야 [고가용성 페더레이션 인증 5 단계: Office 365에 대 한 연결 된 인증을 구성](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)합니다. 모든 단계에 대 한 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="b3c7b-108">Azure에서 인터넷 부하 분산 장치를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="b3c7b-109">Azure가 인터넷에서 수신되는 클라이언트 인증 트래픽을 두 웹 응용 프로그램 프록시 서버에 균등하게 분배할 수 있도록 인터넷 부하 분산 장치를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b3c7b-p102">Azure PowerShell의 최신 버전을 사용 하는 다음 명령 집합입니다. [Azure PowerShell cmdlet 시작](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="b3c7b-112">위치나 리소스 그룹 값이 제공되면 Azure PowerShell 명령 프롬프트나 PowerShell ISE에서 결과 블록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="b3c7b-113">모든이 문서와 사용자 지정 설정을 기반으로 준비 간편 실행 PowerShell 명령 블록을 생성 하는 Microsoft Excel 구성 통합 문서에 PowerShell 명령을 포함 하는 텍스트 파일에 대 한 Office 365에 대 한 페더레이션 인증 [에서 참조 Azure 배포 키트](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="b3c7b-114">로컬 컴퓨터에 있는 Azure PowerShell 명령 프롬프트의 다음 명령을 실행하여 인터넷 부하 분산 장치에 할당된 공용 IP 주소를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="b3c7b-115">페더레이션 서비스 FQDN을 확인하고 DNS 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="b3c7b-p103">DNS 이름을 확인하면 인터넷에서 페더레이션 서비스 이름을 식별할 수 있습니다. Azure AD Connect는 5단계에서 이 이름으로 Office 365를 구성합니다. Office 365는 클라이언트 연결에 보내서 보안 토큰을 얻을 수 있는 URL의 일부가 됩니다. 예: fs.contos.com(fs는 페더레이션 서비스를 나타냄).</span><span class="sxs-lookup"><span data-stu-id="b3c7b-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="b3c7b-119">페더레이션 서비스 FDQN이 있으면 Azure 인터넷 연결 부하 분산 장치의 공용 IP 주소로 확인되는 페더레이션 서비스 FDQN의 공용 DNS 도메인 A 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="b3c7b-120">**Name**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-120">**Name**</span></span>|<span data-ttu-id="b3c7b-121">**종류**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-121">**Type**</span></span>|<span data-ttu-id="b3c7b-122">**TTL**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-122">**TTL**</span></span>|<span data-ttu-id="b3c7b-123">**값**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b3c7b-124">페더레이션 서비스 FDQN</span><span class="sxs-lookup"><span data-stu-id="b3c7b-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="b3c7b-125">A</span><span class="sxs-lookup"><span data-stu-id="b3c7b-125">A</span></span>  <br/> |<span data-ttu-id="b3c7b-126">3600</span><span class="sxs-lookup"><span data-stu-id="b3c7b-126">3600</span></span>  <br/> |<span data-ttu-id="b3c7b-127">Azure 인터넷 부하 분산 장치 (이전 섹션의 **쓰기 호스트** 명령으로 표시 됨)의 공용 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b3c7b-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="b3c7b-128">예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-128">Here is an example:</span></span>
  
|<span data-ttu-id="b3c7b-129">**Name**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-129">**Name**</span></span>|<span data-ttu-id="b3c7b-130">**종류**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-130">**Type**</span></span>|<span data-ttu-id="b3c7b-131">**TTL**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-131">**TTL**</span></span>|<span data-ttu-id="b3c7b-132">**값**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b3c7b-133">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b3c7b-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="b3c7b-134">A</span><span class="sxs-lookup"><span data-stu-id="b3c7b-134">A</span></span>  <br/> |<span data-ttu-id="b3c7b-135">3600</span><span class="sxs-lookup"><span data-stu-id="b3c7b-135">3600</span></span>  <br/> |<span data-ttu-id="b3c7b-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="b3c7b-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="b3c7b-137">그런 다음 조직의 개인 DNS 네임스페이스에 DNS 주소 레코드를 추가하여 페더레이션 서비스 FQDN을 AD FS 서버의 내부 부하 분산 장치에 할당된 개인 IP 주소로 확인합니다(표 I, 항목 4, 값 열).</span><span class="sxs-lookup"><span data-stu-id="b3c7b-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="b3c7b-138">Azure에서 웹 응용 프로그램 프록시 서버 가상 컴퓨터 만들기</span><span class="sxs-lookup"><span data-stu-id="b3c7b-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="b3c7b-139">다음 Azure PowerShell 명령 블록을 사용하여 두 웹 응용 프로그램 프록시 서버의 가상 컴퓨터를 만듭니다. </span><span class="sxs-lookup"><span data-stu-id="b3c7b-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="b3c7b-140">다음 Azure PowerShell 명령 집합은 다음 테이블의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="b3c7b-141">테이블 M, 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="b3c7b-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="b3c7b-142">테이블 R, 리소스 그룹</span><span class="sxs-lookup"><span data-stu-id="b3c7b-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="b3c7b-143">테이블 V, 가상 네트워크 설정</span><span class="sxs-lookup"><span data-stu-id="b3c7b-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="b3c7b-144">테이블 S, 서브넷</span><span class="sxs-lookup"><span data-stu-id="b3c7b-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="b3c7b-145">테이블 I, 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b3c7b-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="b3c7b-146">테이블 A, 가용성 집합</span><span class="sxs-lookup"><span data-stu-id="b3c7b-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="b3c7b-147">표 M에서 정의한 회수 [고가용성 페더레이션 인증 2 단계: 도메인 컨트롤러를 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 및 테이블 R, V, S, I 및 A에서 [고가용성 페더레이션 인증 1 단계: 구성 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="b3c7b-148">모든 적절한 값이 제공되면 Azure PowerShell 명령 프롬프트나 PowerShell ISE에서 결과 블록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="b3c7b-p104">이러한 가상 컴퓨터는 인트라넷 응용 프로그램에 대 한 되므로 하지 공용 IP 주소 또는 DNS 도메인 이름 레이블 할당 되며 인터넷에 노출 됩니다. 그러나, 즉, Azure 포털에서 자신에 게 연결할 수 없습니다. 가상 컴퓨터의 속성을 볼 때에 **연결** 옵션을 사용할 수 없습니다. 원격 데스크톱 연결 액세서리 또는 다른 원격 데스크톱 도구를 사용 하 여 개인 IP 주소 또는 인트라넷 DNS 이름 및 로컬 관리자 계정의 자격 증명을 사용 하 여 가상 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="b3c7b-153">이 단계를 성공적으로 완료하면 자리 표시자 컴퓨터 이름이 포함된 다음 구성이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="b3c7b-154">**4 단계: 인터넷 연결 부하 분산 장치 및 Azure에서 사용 하도록 고가용성 연결 된 인증 인프라에 대 한 웹 응용 프로그램 프록시 서버**</span><span class="sxs-lookup"><span data-stu-id="b3c7b-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![웹 응용 프로그램 프록시 서버를 포함한 Azure에서 고가용성 Office 365 페더레이션 인증 인프라 4단계](images/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="b3c7b-156">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b3c7b-156">Next step</span></span>

<span data-ttu-id="b3c7b-157">사용 [고가용성 페더레이션 인증 5 단계: Office 365에 대 한 연결 된 인증을 구성](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) 를 계속이 작업을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b3c7b-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3c7b-158">See Also</span></span>

[<span data-ttu-id="b3c7b-159">Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포</span><span class="sxs-lookup"><span data-stu-id="b3c7b-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="b3c7b-160">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="b3c7b-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="b3c7b-161">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="b3c7b-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="b3c7b-162">Office 365용 페더레이션 ID</span><span class="sxs-lookup"><span data-stu-id="b3c7b-162">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


