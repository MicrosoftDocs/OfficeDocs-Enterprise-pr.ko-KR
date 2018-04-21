---
title: Azure의 시뮬레이션 된 크로스-프레미스 가상 네트워크
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: '요약: Microsoft Azure의 개발/테스트 환경으로 시뮬레이션 된 크로스-프레미스 가상 네트워크를 만듭니다.'
ms.openlocfilehash: 775c5b19de75ac63cbc3da7fb4e6dc21cb10212c
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>Azure의 시뮬레이션 된 크로스-프레미스 가상 네트워크

 **요약:** 개발/테스트 환경으로 Microsoft Azure의 시뮬레이션 된 크로스-프레미스 가상 네트워크를 만듭니다.
  
이 문서와 Microsoft Azure 두 Azure 가상 네트워크를 사용 하 여 시뮬레이션 된 하이브리드 클라우드 환경 만들기 (영문)에 대해 설명 합니다. 결과 구성은 다음과 같습니다. 
  
![XPrem VNet의 DC2 가상 컴퓨터를 사용한 시뮬레이션된 크로스-프레미스 Virtual Network 개발/테스트 환경 3단계](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Azure IaaS 하이브리드 클라우드 프로덕션 환경에서 시뮬레이션 하 고 구성 됩니다.
  
- 네트워크에 연결 시뮬레이션 된 간소화 된 온-프레미스 및 Azure 가상 네트워크 (테스트 실습 가상 네트워크)에서 호스팅됩니다.
    
- Azure (XPrem)에서 호스팅되는 시뮬레이션 된 크로스-프레미스 가상 네트워크입니다.
    
- 두 가상 네트워크 간의 VNet 피어 링 관계입니다.
    
- XPrem 가상 네트워크에서 보조 도메인 컨트롤러입니다.
    
이렇게 기준 및 일반적인 시작 하는 수를 가리킵니다. 제공 됩니다. 
  
- 개발 및 시뮬레이션 된 Azure IaaS 하이브리드 클라우드 환경에서 응용 프로그램을 테스트 합니다.
    
- 컴퓨터, 테스트 실습 가상 네트워크 내에서 일부 및 하이브리드 클라우드 기반 IT 작업 부하를 시뮬레이션 하기 위해 XPrem 가상 네트워크 내에서 일부 테스트 구성을 만듭니다.
    
이 개발/테스트 환경의 3가지 주요 설정 단계는 다음과 같습니다.
  
1. 테스트 실습 가상 네트워크를 구성 합니다.
    
2. 크로스-프레미스 가상 네트워크를 만듭니다.
    
3. D c 2를 구성 합니다.
    
> [!NOTE]
> 이 구성을 위해서는 유료 Azure 구독이 필요합니다. 
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>1 단계: 테스트 실습 가상 네트워크 구성

[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md) 에서 테스트 실습 라는 Azure 가상 네트워크에서 d c 1, a p p 1을 및 CLIENT1 컴퓨터를 구성 하는 지침을 따르십시오.
  
현재 구성입니다. 
  
![CLIENT1 가상 컴퓨터를 사용한 Azure의 기본 구성 4단계](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>2 단계: XPrem 가상 네트워크 만들기

이 단계에서 하 고 새 XPrem 가상 네트워크 구성 만들고 VNet 피어 링으로 테스트 실습 가상 네트워크에 연결 합니다.
  
먼저, 로컬 컴퓨터에서 Azure PowerShell 프롬프트를 시작 합니다.
  
> [!NOTE]
> 다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell cmdlet으로 시작](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)을 참조하세요. 
  
다음 명령 사용 하 여 Azure 계정에 로그인 합니다.
  
```
Login-AzureRMAccount
```

> [!TIP]
> 이 문서의 PowerShell 명령을 모두 포함하는 텍스트 파일을 가져오려면 [여기](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0)를 클릭합니다.
  
다음 명령을 사용하여 구독 이름을 가져옵니다.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Azure 구독을 설정 합니다. 교체 따옴표를 포함 하 여 입력을 내에 있는 모든 항목은 \< 및 > 올바른 이름 사용 하 여 문자입니다.
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

다음으로 XPrem 가상 네트워크를 만들고 이러한 명령으로 네트워크 보안 그룹과 보호 합니다.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$Testnet=New-AzureRMVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzureRMVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

그런 다음 이러한 명령을와 테스트 실습 및 XPrem VNets 간의 VNet 피어 링 관계를 만듭니다.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

현재 구성입니다. 
  
![XPrem VNet 및 VNet 피어링 관계를 사용한 시뮬레이션된 크로스-프레미스 Virtual Network 개발/테스트 환경 2단계](images/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>3 단계: d c 2를 구성 합니다.

이 단계에서 d c 2 가상 컴퓨터 XPrem 가상 네트워크에서 만들고 복제 도메인 컨트롤러를 구성 합니다.
  
먼저 d c 2에 대 한 가상 컴퓨터를 만듭니다. Azure PowerShell 명령 프롬프트에서 로컬 컴퓨터에서 이러한 명령을 실행 합니다.
  
```
$rgName="<your resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzureRMVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

다음으로, 로컬 관리자 계정 이름과 암호를 사용 하 여 [Azure 포털](https://portal.azure.com) 에서 새 d c 2 가상 컴퓨터에 연결 합니다.
  
다음으로 기본 연결을 테스트 하는 것에 대 한 트래픽을 허용 하도록 Windows 방화벽 규칙을 구성 합니다. 프로그램 관리자 수준 Windows PowerShell 명령 프롬프트에서 d c 2에서 다음이 명령을 실행 합니다. 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

IP 주소 10.0.0.4에서에서 4 개의 성공적인 회신을 받으면 ping 명령을 발생 해야 합니다. 이것은 VNet 피어 링 관계 별 트래픽의 테스트 합니다. 
  
그 다음 d c 2에서 Windows PowerShell 명령 프롬프트에서 추가 데이터 디스크 드라이브 문자로 f:가이 명령 사용 하 여 새 볼륨으로 추가 합니다.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

다음으로, corp.contoso.com 도메인에 대 한 복제 도메인 컨트롤러로 d c 2를 구성 합니다. D c 2 Windows PowerShell 명령 프롬프트에서 다음이 명령을 실행 합니다.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

두는 회사를 제공 하 라는 메시지가\\User1 암호와 디렉터리 서비스 복원 모드 (DSRM) 암호를 d c 2를 다시 시작 하 고 있습니다. 
  
XPrem 가상 네트워크 부여한 후 자체 DNS 서버 (d c 2),이 DNS 서버를 사용 하 여 XPrem 가상 네트워크를 구성 해야 합니다. Azure PowerShell 명령 프롬프트에서 로컬 컴퓨터 이러한 명령을 실행 합니다.
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

로컬 컴퓨터에서 Azure 포털에서 d c 1에는 회사와 연결\\User1 자격 증명입니다. 파일을 컴퓨터 및 사용자 인증에 대 한 자신의 로컬 도메인 컨트롤러를 사용할 수 있도록 CORP 도메인을 구성 하려면 d c 1에는 관리자 수준 Windows PowerShell 명령 프롬프트에서 다음이 명령을 실행 합니다.
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

현재 구성입니다. 
  
![XPrem VNet의 DC2 가상 컴퓨터를 사용한 시뮬레이션된 크로스-프레미스 Virtual Network 개발/테스트 환경 3단계](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
시뮬레이션 된 Azure 하이브리드 클라우드 환경 테스트를 수행할 준비가 되었습니다.
  
## <a name="next-step"></a>다음 단계

[Azure에서 호스팅되는 SharePoint Server 2016 인트라넷 팜](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)시뮬레이션 하기 위해이 개발/테스트 환경을 사용 합니다.
  
## <a name="see-also"></a>참고 항목

[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


