---
title: "고가용성 페더레이션 인증 단계 3 구성 AD FS 서버"
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
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: "요약: 만들고 Microsoft Azure에서 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 Active Directory Federation Services (AD FS) 서버를 구성 합니다."
ms.openlocfilehash: fb31aba6e68358740e316983206bddae1df00548
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="e168b-103">고가용성 페더레이션 인증 3단계: AD FS 서버 구성</span><span class="sxs-lookup"><span data-stu-id="e168b-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="e168b-104">**요약:** 페이지를 만들고 Microsoft Azure에서 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 Active Directory Federation Services (AD FS) 서버를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="e168b-105">이 단계에서는 Azure 인프라 서비스의 Office 365 페더레이션 인증의 고가용성을 배포하며 내부 부하 분산 장치 및 두 개의 AD FS 서버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="e168b-p101">레코드로 이동 하기 전에이 단계를 완료 해야 [고가용성 페더레이션 인증 4 단계: 웹 응용 프로그램 프록시를 구성](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)합니다. 모든 단계에 대 한 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e168b-p101">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="e168b-108">Azure에서 AD FS 서버 가상 컴퓨터 만들기</span><span class="sxs-lookup"><span data-stu-id="e168b-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="e168b-p102">PowerShell 명령의 다음 블록을 사용하여 두 AD FS 서버의 가상 컴퓨터를 만듭니다. PowerShell 명령 집합은 다음 테이블의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="e168b-111">테이블 M, 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="e168b-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="e168b-112">테이블 R, 리소스 그룹</span><span class="sxs-lookup"><span data-stu-id="e168b-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="e168b-113">테이블 V, 가상 네트워크 설정</span><span class="sxs-lookup"><span data-stu-id="e168b-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="e168b-114">테이블 S, 서브넷</span><span class="sxs-lookup"><span data-stu-id="e168b-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="e168b-115">테이블 I, 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="e168b-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="e168b-116">테이블 A, 가용성 집합</span><span class="sxs-lookup"><span data-stu-id="e168b-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="e168b-117">표 M에서 정의한 회수 [고가용성 페더레이션 인증 2 단계: 도메인 컨트롤러를 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 및 테이블 R, V, S, I 및 A에서 [고가용성 페더레이션 인증 1 단계: 구성 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e168b-p103">Azure PowerShell의 최신 버전을 사용 하는 다음 명령 집합입니다. [Azure PowerShell cmdlet 시작](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e168b-p103">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="e168b-p104">첫째, Azure 내부 부하 분산 장치를 두 ad FS 서버를 만듭니다. 제거 하는 변수에 대 한 값을 지정 된 \< 및 > 문자입니다. 모든 적절 한 값을 제공한 경우 PowerShell ISE 또는 Azure PowerShell 명령 프롬프트에서 결과 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-p104">First, you create an Azure internal load balancer for the two AD FS servers. Specify the values for the variables, removing the \< and > characters. When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="e168b-123">모든이 문서와 사용자 지정 설정을 기반으로 준비 간편 실행 PowerShell 명령 블록을 생성 하는 Microsoft Excel 구성 통합 문서에 PowerShell 명령을 포함 하는 텍스트 파일에 대 한 Office 365에 대 한 페더레이션 인증 [에서 참조 Azure 배포 키트](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-123">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzureRMLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="e168b-124">다음으로 AD FS 서버 가상 컴퓨터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-124">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="e168b-125">모든 적절한 값이 제공되면 Azure PowerShell 명령 프롬프트나 PowerShell ISE에서 결과 블록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-125">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="e168b-p105">이러한 가상 컴퓨터는 인트라넷 응용 프로그램에 대 한 되므로 하지 공용 IP 주소 또는 DNS 도메인 이름 레이블 할당 되며 인터넷에 노출 됩니다. 그러나, 즉, Azure 포털에서 자신에 게 연결할 수 없습니다. 가상 컴퓨터의 속성을 볼 때에 **연결** 옵션을 사용할 수 없습니다. 원격 데스크톱 연결 액세서리 또는 다른 원격 데스크톱 도구를 사용 하 여 해당 개인 IP 주소 또는 인트라넷 DNS 이름을 사용 하 여 가상 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="e168b-p106">각 가상 컴퓨터에 원하는 원격 데스크톱 클라이언트를 사용하고 원격 데스크톱 연결을 만듭니다. 인트라넷 DNS나 컴퓨터 이름 및 로컬 관리자 계정의 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="e168b-132">Windows PowerShell 프롬프트에 있는 이러한 명령을 사용하여 각 가상 컴퓨터를 적합한 Windows Server AD 도메인에 참가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-132">For each virtual machine, join them to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="e168b-133">이 단계를 성공적으로 완료하면 자리 표시자 컴퓨터 이름과 함께 이 구성을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-133">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="e168b-134">**3 단계: AD FS 서버와 Azure에서 사용 하도록 고가용성 연결 된 인증 인프라에 대 한 내부 부하 분산 장치**</span><span class="sxs-lookup"><span data-stu-id="e168b-134">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![AD FS 서버를 포함한 Azure에서 고가용성 Office 365 페더레이션 인증 인프라 3단계](images/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="e168b-136">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e168b-136">Next step</span></span>

<span data-ttu-id="e168b-137">사용 [고가용성 페더레이션 인증 4 단계: 웹 응용 프로그램 프록시를 구성](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) 를 계속이 작업을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e168b-137">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e168b-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e168b-138">See Also</span></span>

[<span data-ttu-id="e168b-139">Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포</span><span class="sxs-lookup"><span data-stu-id="e168b-139">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="e168b-140">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="e168b-140">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


