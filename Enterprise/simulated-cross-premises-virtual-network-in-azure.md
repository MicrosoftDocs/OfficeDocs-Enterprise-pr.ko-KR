---
title: 시뮬레이션된 Azure의 크로스-프레미스 가상 네트워크
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: '요약: 시뮬레이션된 프레미스 간 가상 네트워크를 Microsoft Azure에 개발/테스트 환경으로 만듭니다.'
ms.openlocfilehash: 4f68bff2713119d3deb37e7dd7dc5b20107e6905
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031513"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>시뮬레이션된 Azure의 크로스-프레미스 가상 네트워크

 **요약:** 시뮬레이션된 프레미스 간 가상 네트워크를 Microsoft Azure에 개발/테스트 환경으로 만듭니다.
  
이 문서는 2개의 Azure 가상 네트워크를 사용하여 Microsoft Azure에 시뮬레이션된 하이브리드 클라우드 환경을 만드는 방법을 단계별로 설명합니다. 결과 구성은 다음과 같습니다. 
  
![XPrem VNet의 DC2 가상 컴퓨터를 사용한 시뮬레이션된 크로스-프레미스 Virtual Network 개발/테스트 환경 3단계](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Azure IaaS 하이브리드 클라우드 프로덕션 환경을 시뮬레이트하며 다음으로 구성됩니다.
  
- Azure 가상 네트워크(TestLab 가상 네트워크)에서 호스트되고 시뮬레이션된 간소화된 온-프레미스 네트워크.
    
- Azure(XPrem)에서 호스트되고 시뮬레이션된 프레미스 간 가상 네트워크.
    
- 2개의 가상 네트워크 간 VNet 피어링 관계입니다.
    
- XPrem 가상 네트워크의 보조 도메인 컨트롤러입니다.
    
이 컨트롤러는 다음 작업을 수행할 수 있는 기본적이고 일반적인 시작 지점을 제공합니다. 
  
- 시뮬레이션된 Azure IaaS 하이브리드 클라우드 환경에서 테스트 응용 프로그램을 개발하고 테스트합니다.
    
- 일부 TestLab 가상 네트워크 및 일부 XPrem 가상 네트워크 내에서 컴퓨터의 테스트 구성을 만들어서 하이브리드 클라우드 기반 IT 작업을 시뮬레이션합니다.
    
이 개발/테스트 환경의 3가지 주요 설정 단계는 다음과 같습니다.
  
1. TestLab 가상 네트워크를 구성합니다.
    
2. 프레미스 간 가상 네트워크를 만듭니다.
    
3. DC2를 구성합니다.
    
> [!NOTE]
> 이 구성을 위해서는 유료 Azure 구독이 필요합니다. 
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> [여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>1단계: TestLab 가상 네트워크 구성

[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)의 지침을 사용하여 TestLab이라는 Azure 가상 네트워크에서 DC1, APP1, CLIENT1 컴퓨터를 구성합니다.
  
다음은 현재 구성입니다. 
  
![CLIENT1 가상 머신을 사용한 Azure의 기본 구성 4단계](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>2단계: XPrem 가상 네트워크 만들기

이 단계에서는 새로운 XPrem 가상 네트워크를 만들고 구성한 다음 이를 VNet 피어링을 통해 TestLab 가상 네트워크에 연결합니다.
  
먼저 로컬 컴퓨터에서 Azure PowerShell 프롬프트를 시작합니다.
  
> [!NOTE]
> 다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell cmdlet으로 시작](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)을 참조하세요. 
  
이 명령을 사용하여 Azure 계정에 로그인합니다.
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that has all of the PowerShell commands in this article.
-->
  
이 명령을 사용하여 구독 이름을 가져옵니다.
  
```
Get-AzSubscription | Sort Name | Select Name
```

Azure 구독을 설정합니다. \< 및 > 문자를 포함하여 따옴표 안에 있는 모든 것을 올바른 이름으로 바꿉니다.
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

그런 다음, 해당 명령을 통해 XPrem 가상 네트워크를 만들고 가상 보안 그룹으로 네트워크를 보호합니다.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

그런 다음, 해당 명령을 통해 TestLab 및 XPrem VNet 간의 VNet 피어링 관계를 만듭니다.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

다음은 현재 구성입니다. 
  
![XPrem VNet 및 VNet 피어링 관계를 사용한 시뮬레이션된 크로스-프레미스 Virtual Network 개발/테스트 환경 2단계](media/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>3단계: DC2 구성

이 단계에서는 XPrem 가상 네트워크에 DC2 가상 컴퓨터를 만들고 복제본 도메인 컨트롤러로 구성합니다.
  
먼저 DC2에 대한 가상 컴퓨터를 만듭니다. 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에서 해당 명령을 실행합니다.
  
```
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

그런 다음, 로컬 관리자 계정 이름과 암호를 사용하여 [Azure Portal](https://portal.azure.com)에서 새로운 DC2 가상 컴퓨터에 연결합니다.
  
그런 다음, 기본 연결 테스트에 트래픽을 허용하도록 Windows 방화벽 규칙을 구성합니다. DC2의 관리자 수준 Windows PowerShell 명령 프롬프트에서 해당 명령을 실행합니다. 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

ping 명령으로 인해 IP 주소 10.0.0.4에서 네 번의 성공적인 응답이 발생해야 합니다. VNet 피어링 관계 전반에 걸친 트래픽 테스트입니다. 
  
다음으로 DC2의 Windows PowerShell 명령 프롬프트에서 이 명령을 사용하여 추가 데이터 디스크를 드라이브 문자 F:의 새로운 볼륨으로 추가합니다.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

그런 다음 DC2를 corp.contoso.com 도메인에 대한 복제본 도메인 컨트롤러로 구성합니다. DC2의 Windows PowerShell 명령 프롬프트에서 해당 명령을 실행합니다.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

CORP\\User1 암호와 디렉터리 서비스 복원 모드(DSRM) 암호 모두를 제공하고 DC2를 다시 시작하라는 메시지가 표시됩니다. 
  
이제 XPrem에는 자체 DNS 서버(DC2)가 있으므로 이 DNS 서버를 사용하도록 XPrem 가상 네트워크를 구성해야 합니다. 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에서 해당 명령을 실행합니다.
  
```
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

로컬 컴퓨터의 Azure Portal에서 CORP\\User1 자격 증명을 사용하여 DC1에 연결합니다. 컴퓨터와 사용자가 로컬 도메인 컨트롤러를 사용하여 인증하도록 CORP 도메인을 구성하려면 DC1의 관리자 수준 Windows PowerShell 명령 프롬프트에서 해당 명령을 실행합니다.
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

다음은 현재 구성입니다. 
  
![XPrem VNet의 DC2 가상 컴퓨터를 사용한 시뮬레이션된 크로스-프레미스 Virtual Network 개발/테스트 환경 3단계](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
시뮬레이션된 Azure 하이브리드 클라우드 환경은 이제 테스트 준비 중입니다.
  
## <a name="next-step"></a>다음 단계

이 개발/테스트 환경을 사용하여 [Azure에서 호스트된 SharePoint Server 2016 인트라넷 팜](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)을 시뮬레이션할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


