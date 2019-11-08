---
title: 고가용성 페더레이션 인증 4 단계 웹 응용 프로그램 프록시 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: '요약: Microsoft Azure에서 Office 365에 대 한 고가용성 페더레이션 인증을 위한 웹 응용 프로그램 프록시 서버를 구성 합니다.'
ms.openlocfilehash: c0a469f8945b9e69415b511c253e72a0118a4cfa
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027672"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>고가용성 페더레이션 인증 4단계: 웹 응용 프로그램 프록시 구성

 **요약:** Microsoft Azure에서 Office 365에 대 한 고가용성 페더레이션 인증을 사용 하도록 웹 응용 프로그램 프록시 서버를 구성 합니다.
  
이 단계에서는 Azure 인프라 서비스의 Office 365 페더레이션 인증의 고가용성을 배포하며 내부 부하 분산 장치 및 두 개의 AD FS 서버를 만듭니다.
  
[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)으로 넘어가기 전에 이 단계를 완료해야 합니다. 모든 단계에 대해 [Azure에서 Office 365에 대 한 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 를 참조 하세요.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Azure에서 인터넷 부하 분산 장치를 만듭니다.

Azure가 인터넷에서 수신되는 클라이언트 인증 트래픽을 두 웹 응용 프로그램 프록시 서버에 균등하게 분배할 수 있도록 인터넷 부하 분산 장치를 만들어야 합니다.
  
> [!NOTE]
> 다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell cmdlet으로 시작](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)을 참조하세요. 
  
위치나 리소스 그룹 값이 제공되면 Azure PowerShell 명령 프롬프트나 PowerShell ISE에서 결과 블록을 실행합니다.
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
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

로컬 컴퓨터에 있는 Azure PowerShell 명령 프롬프트의 다음 명령을 실행하여 인터넷 부하 분산 장치에 할당된 공용 IP 주소를 표시합니다.
  
```
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>페더레이션 서비스 FQDN을 확인하고 DNS 레코드를 만듭니다.

DNS 이름을 확인하면 인터넷에서 페더레이션 서비스 이름을 식별할 수 있습니다. Azure AD Connect는 5단계에서 이 이름으로 Office 365를 구성합니다. Office 365는 클라이언트 연결에 보내서 보안 토큰을 얻을 수 있는 URL의 일부가 됩니다. 예: fs.contos.com(fs는 페더레이션 서비스를 나타냄).
  
페더레이션 서비스 FDQN이 있으면 Azure 인터넷 연결 부하 분산 장치의 공용 IP 주소로 확인되는 페더레이션 서비스 FDQN의 공용 DNS 도메인 A 레코드를 만듭니다.
  
|**이름**|**종류**|**TTL**|**값**|
|:-----|:-----|:-----|:-----|
|페더레이션 서비스 FDQN  <br/> |A  <br/> |3600  <br/> |Azure 인터넷 부하 분산 장치의 공용 IP 주소(이전 섹션에서 **Write-Host** 명령으로 표시됨) <br/> |
   
예제는 다음과 같습니다.
  
|**이름**|**종류**|**TTL**|**값**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
그런 다음 조직의 개인 DNS 네임스페이스에 DNS 주소 레코드를 추가하여 페더레이션 서비스 FQDN을 AD FS 서버의 내부 부하 분산 장치에 할당된 개인 IP 주소로 확인합니다(표 I, 항목 4, 값 열).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Azure에서 웹 응용 프로그램 프록시 서버 가상 컴퓨터 만들기

다음 Azure PowerShell 명령 블록을 사용하여 두 웹 응용 프로그램 프록시 서버의 가상 컴퓨터를 만듭니다.  
  
다음 Azure PowerShell 명령 집합은 다음 테이블의 값을 사용합니다.
  
- 테이블 M, 가상 컴퓨터
    
- 테이블 R, 리소스 그룹
    
- 테이블 V, 가상 네트워크 설정
    
- 테이블 S, 서브넷
    
- 테이블 I, 고정 IP 주소
    
- 테이블 A, 가용성 집합
    
고가용성 [페더레이션 인증 2 단계: 도메인 컨트롤러](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 와 테이블 R, V, S, I 및 A를 고가용성 [페더레이션 인증 1 단계: 구성 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)에서 정의한 테이블 M을 정의 합니다.
  
모든 적절한 값이 제공되면 Azure PowerShell 명령 프롬프트나 PowerShell ISE에서 결과 블록을 실행합니다.
  
```
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
> 이러한 가상 컴퓨터는 인트라넷 응용 프로그램용이므로 공용 IP 주소나 DNS 도메인 이름 레이블에 할당되지 않으며 인터넷에 표시되지 않습니다. 그러나 이는 Azure Portal에서 연결할 수 없음을 의미합니다. 가상 컴퓨터의 속성을 보면 이 **연결** 옵션을 사용할 수 없습니다. 원격 데스크톱 연결 액세서리 또는 다른 원격 데스크톱 도구를 사용하여 개인 IP 주소나 인트라넷 DNS 이름 및 로컬 관리자 계정의 자격 증명을 사용하는 가상 컴퓨터에 연결할 수 있습니다.
  
이 단계를 성공적으로 완료하면 자리 표시자 컴퓨터 이름과 함께 이 구성을 얻을 수 있습니다.
  
**4단계: Azure의 고가용성 페더레이션 인증 인프라용 인터넷 부하 분산 장치 및 웹 응용 프로그램 프록시 서버**

![웹 응용 프로그램 프록시 서버를 포함 하는 고가용성 Office 365 Azure의 페더레이션 인증 인프라 4 단계](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>다음 단계

[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)을 사용하여 이 작업을 계속 구성합니다.
  
## <a name="see-also"></a>참고 항목

[Azure에서 Office 365용 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 개발/테스트 환경에 대 한 페더레이션된 id](federated-identity-for-your-office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)

