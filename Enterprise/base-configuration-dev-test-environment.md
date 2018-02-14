---
title: "기본 구성 개발/테스트 환경"
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
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: "요약: Microsoft Azure의 개발/테스트 환경으로 단순화 된 인트라넷을 만듭니다."
ms.openlocfilehash: 04da1037dbebed9f9a5d2aa2fb37b03b88218839
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="base-configuration-devtest-environment"></a>기본 구성 개발/테스트 환경

 **요약:** Microsoft Azure의 개발/테스트 환경으로 단순화 된 인트라넷을 만듭니다.
  
이 문서에서는 Azure에는 다음과 같은 기본 구성 개발/테스트 환경을 만드는 단계별 지침을를 제공 합니다.
  
**그림 1: 기본 구성 개발/테스트 환경**

![CLIENT1 가상 컴퓨터를 사용한 Azure의 기본 구성 4단계](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
그림 1의 기본 구성 개발/테스트 환경에서 클라우드 전용 Azure 가상 네트워크를 인터넷에 연결 하는 간소화 된, 개인 인트라넷을 시뮬레이션 하는 테스트 실습 라는 회사 서브넷으로 이루어져 있습니다. Windows Server 2016를 실행 하는 세 Azure 가상 컴퓨터를 포함 합니다.
  
- D c 1에는 인트라넷 도메인 컨트롤러와 도메인 이름 시스템 (DNS) 서버 구성
    
- A p p 1 일반 응용 프로그램 및 웹 서버 구성
    
- 인트라넷 클라이언트로 CLIENT1 역
    
이 구성에서 d c 1, a p p 1, CLIENT1, 및 추가 회사 서브넷 컴퓨터 수를 허용: 
  
- 업데이트를 설치 하려면 인터넷에 연결을 사용 실시간으로 인터넷 리소스에 액세스 하 고 Microsoft Office 365 및 기타 Azure 서비스와 같은 공용 클라우드 기술에 참여 합니다.
    
- 인터넷 이나 조직 네트워크에 연결 된 컴퓨터에서 원격 데스크톱 연결을 사용 하 여 원격으로 관리 합니다.
    
결과 테스트 환경에 사용할 수 있습니다.
  
- 응용 프로그램 개발 및 테스트 합니다.
    
- 으로 가상 컴퓨터를 추가, Azure 서비스 또는 Office 365 및 엔터프라이즈 보안 + 이동성와 같은 다른 Microsoft 클라우드 서비스를 포함 하는 디자인의 확장된 테스트 환경의 초기 구성 합니다.
    
Azure의 기본 구성 테스트 환경을 설정 하는 4 단계로 가지가 있습니다.
  
1. 가상 네트워크를 만듭니다.
    
2. D c 1을 구성 합니다.
    
3. A p p 1을 구성 합니다.
    
4. CLIENT1을 구성 합니다.
    
Azure에 구독 아직 없는 경우 무료 평가판을 신청 [시도 Azure](https://azure.microsoft.com/pricing/free-trial/)에서 서명할 수 있습니다. MSDN 또는 Visual Studio 구독이 있는 경우 [Visual Studio 구독자에 대 한 월별 Azure 신용](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)를 참조 하십시오.
  
> [!NOTE]
> Azure에 가상 컴퓨터를 실행 하는 경우는 진행 중인 통화 비용을 발생 시킵니다. 이 비용 무료 평가판, MSDN 구독에 대 한 청구 또는 구독 된 급여입니다. Azure 가상 컴퓨터를 실행 하는 비용에 대 한 자세한 내용은 [가상 컴퓨터 가격 정보](https://azure.microsoft.com/pricing/details/virtual-machines/) 및 [Azure 가격 계산기 (영문)을](https://azure.microsoft.com/pricing/calculator/)참조 하십시오. 비용을 유지 하려면 [Azure의 테스트 환경 가상 컴퓨터의 비용을 최소화 하기](base-configuration-dev-test-environment.md#mincost)를 참조 합니다. 
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-create-the-virtual-network"></a>1 단계: 가상 네트워크 만들기

먼저, Azure PowerShell 프롬프트를 시작 합니다.
  
> [!NOTE]
> Azure PowerShell의 최신 버전을 사용 하는 다음 명령 집합입니다. [Azure PowerShell cmdlet 시작](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)을 참조 하십시오. 
  
다음 명령 사용 하 여 Azure 계정에 로그인 합니다.
  
```
Login-AzureRMAccount
```

> [!TIP]
> 클릭 [여기](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) 이 문서의 모든 PowerShell 명령을 포함 된 텍스트 파일을 가져오도록 합니다.
  
다음 명령을 사용하여 구독 이름을 가져옵니다.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Azure 구독을 설정합니다. <and> 문자를 포함하여 따옴표 안에 있는 모든 것을 올바른 이름으로 바꿉니다.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

다음으로, 기본 구성 테스트 랩 환경에 대 한 새 자원 그룹을 만듭니다. 고유한 리소스 그룹 이름을 확인 하려면 기존 리소스 그룹을 나열 하려면이 명령을 사용 합니다.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

이러한 명령을 사용 하면 새 자원 그룹을 만듭니다. 교체 따옴표를 포함 하 여 입력을 내에 있는 모든 항목은 < 및 > 올바른 이름 사용 하 여 문자입니다.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

다음을 기본 구성의 회사 서브넷 호스트 되며 네트워크 보안 그룹과 보호 하는 테스트 실습 가상 네트워크를 만듭니다.
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

현재 구성입니다.
  
![Virtual Network 및 서브넷을 사용한 Azure의 기본 구성 1단계](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a>D c 1을 구성 하는 2 단계:

이 단계는 d c 1에 가상 컴퓨터 만들기 하 고 corp.contoso.com Windows Server Active Directory (AD) 도메인에 대 한 도메인 컨트롤러 및 테스트 실습 가상 네트워크의 가상 컴퓨터에 대 한 DNS 서버를 구성 합니다.
  
D c 1에 대 한를 Azure 가상 컴퓨터를 만들려면 자원 그룹의 이름을 입력 하 고 로컬 컴퓨터에서 Azure PowerShell 명령 프롬프트에서 다음이 명령을 실행 합니다.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

사용자 이름 및 d c 1에 로컬 관리자 계정에 대 한 암호를 묻는 메시지가 나타납니다. 강력한 암호를 사용 하 고 안전한 위치에 이름 및 암호를 기록 합니다.
  
다음으로, d c 1에 가상 컴퓨터에 연결 합니다.
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a>D c 1에 연결할 로컬 관리자 계정 자격 증명을 사용 하 여

1. [Azure 포털](https://portal.azure.com)클릭 **리소스 그룹 >** <the name of your new resource group> **> d c 1 > 연결**합니다.
    
2. 를 다운로드 하는 DC1.rdp 파일을 열고 **연결**을 클릭 합니다.
    
3. D c 1에 로컬 관리자 계정 이름을 지정 합니다.
    
  - Windows 7:
    
    **Windows 보안** 대화 상자에서 **다른 계정 사용**을 클릭 합니다. **사용자 이름**입력 **d c 1\\**[로컬 관리자 계정 이름].
    
  - Windows 8 또는 Windows 10:
    
    **Windows 보안** 대화 상자에서 **추가 선택 항목**클릭 한 다음 **다른 계정을 사용**을 클릭 합니다. **사용자 이름**입력 **d c 1\\**[로컬 관리자 계정 이름].
    
4. **암호**로컬 관리자 계정의 암호를 입력 하 고 **확인**을 클릭 합니다.
    
5. 대화 상자가 나타나면 **예**를 클릭 합니다.
    
그 다음 문자로 드라이브 f: d c 1에 게 관리자 수준 Windows PowerShell 명령 프롬프트에서이 명령 사용 하 여 새 볼륨으로 추가 데이터 디스크를 추가 합니다.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

다음으로 도메인 컨트롤러와 corp.contoso.com 도메인에 대 한 DNS 서버 d c 1을 구성 합니다. 관리자 수준 Windows PowerShell 명령 프롬프트에 다음이 명령을 실행 합니다.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

안전 모드 관리자 암호를 지정 해야 합니다. 이 암호를 안전한 위치에 저장 합니다.
  
이러한 명령은 완료하는 데 몇 분 정도 걸릴 수 있습니다.
  
D c 1에는 다음 작업을 다시 시작 되 면 d c 1에 가상 컴퓨터를 다시 연결 합니다.
  
### <a name="connect-to-dc1-using-domain-credentials"></a>D c 1에 연결할 도메인 자격 증명을 사용 하 여

1. [Azure 포털](https://portal.azure.com)클릭 **리소스 그룹 >** <your resource group name> **> d c 1 > 연결**합니다.
    
2. 를 다운로드 하는 DC1.rdp 파일을 실행 하 고 **연결**을 클릭 합니다.
    
3. **Windows 보안** **다른 계정 사용**을 클릭 합니다. **사용자 이름**입력 **CORP\\**[로컬 관리자 계정 이름].
    
4. **암호**로컬 관리자 계정의 암호를 입력 하 고 **확인**을 클릭 합니다.
    
5. 대화 상자가 나타나면 **예**를 클릭 합니다.
    
다음으로 CORP 도메인 구성원 컴퓨터에 로그인 할 때 사용 되는 Active Directory에서 사용자 계정을 만듭니다. 관리자 수준 Windows PowerShell 명령 프롬프트에서이 명령을 실행 합니다.
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

이 명령은 User1 계정 암호를 입력 하 게 묻는 메모 합니다. 이 계정을 사용할 모든 CORP 도메인 구성원 컴퓨터에 대 한 원격 데스크톱 연결을 하기 때문에 강력한 암호를 선택 합니다. User1 계정 암호를 기록 하 고 안전한 위치에 저장 합니다.
  
다음으로 새 User1 계정으로 엔터프라이즈 관리자가 구성 합니다. 관리자 수준 Windows PowerShell 명령 프롬프트에서이 명령을 실행 합니다.
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

D c 1에 있는 원격 데스크톱 세션을 닫은 다음는 회사를 사용 하 여 다시 연결\\User1 계정을 합니다.
  
다음으로, Ping 도구에 대 한 트래픽을 허용, 된 관리자 수준 Windows PowerShell 명령 프롬프트에서이 명령을 실행 합니다.
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

현재 구성입니다.
  
![DC1 가상 컴퓨터를 사용한 Azure의 기본 구성 2단계](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a>A p p 1을 구성 하는 3 단계:

A p p 1에서는 웹 서버 및 파일 공유 서비스를 제공 합니다.
  
A p p 1에 대 한 Azure 가상 컴퓨터를 만들려면 이름에 리소스 그룹, Azure 위치 및 저장소 계정 이름을 입력 하 고 로컬 컴퓨터에서 Azure PowerShell 명령 프롬프트에서 다음이 명령을 실행 합니다.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

다음으로 a p p 1 로컬 관리자 계정 이름과 암호를 사용 하 여 a p p 1 가상 컴퓨터에 연결 하 고 Windows PowerShell 명령 프롬프트를 엽니다.
  
A p p 1과 d c 1에 이름 확인 및 네트워크 통신을 확인 하려면 **ping dc1.corp.contoso.com** 명령을 실행 하 고 응답을 4 번 남아 있지 않은지 확인 합니다.
  
다음으로, Windows PowerShell 프롬프트에 다음이 명령 사용 하 여 회사 도메인에 a p p 1 가상 컴퓨터에 참가 합니다.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

메모는 회사를 제공 해야\\User1 도메인 계정 자격 증명 **추가 컴퓨터** 명령을 실행 합니다.
  
A p p 1을 다시 시작한 후에 회사를 사용 하 여 연결\\User1 계정 하 고 다음 열기를 관리자 수준 Windows PowerShell 명령 프롬프트입니다.
  
다음으로 확인 a p p 1이이 명령 사용 하 여 웹 서버 a p p 1에서 Windows PowerShell 명령 프롬프트에서.
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

다음으로 만들 공유 폴더 및 폴더 내에 있는 텍스트 파일을 a p p 1 이러한 PowerShell 명령을 사용 합니다.
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

현재 구성입니다.
  
![APP1 가상 컴퓨터를 사용한 Azure의 기본 구성 3단계](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a>4 단계: CLIENT1 구성

일반적으로 랩톱, 태블릿, 또는 Contoso 인트라넷에서 데스크톱 컴퓨터 CLIENT1 작동합니다.
  
> [!NOTE]
> 다음 명령 집합 만듭니다 CLIENT1 모든 유형의 Azure 구독에 대 한 수행할 수 있는 Windows Server 2016 Datacenter를 실행 합니다. Visual Studio 기반 Azure 구독을 설치한 경우 [Azure 포털](https://portal.azure.com)와 CLIENT1 실행 중인 Windows 10, Windows 8 또는 Windows 7을 만들 수 있습니다. 
  
CLIENT1에 대 한 Azure 가상 컴퓨터를 만들려면 이름에 리소스 그룹, Azure 위치 및 저장소 계정 이름을 입력 하 고 로컬 컴퓨터에서 Azure PowerShell 명령 프롬프트에서 다음이 명령을 실행 합니다.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

다음으로 CLIENT1 로컬 관리자 계정 이름과 암호를 사용 하 여 CLIENT1 가상 컴퓨터에 연결 하 고 관리자 수준 Windows PowerShell 명령 프롬프트를 엽니다.
  
CLIENT1 및 d c 1 간의 이름 확인 및 네트워크 통신을 확인 하려면 Windows PowerShell 명령 프롬프트에서 **ping dc1.corp.contoso.com** 명령을 실행 하 고 응답을 4 번 남아 있지 않은지 확인 합니다.
  
다음으로, Windows PowerShell 프롬프트에 다음이 명령 사용 하 여 회사 도메인에 CLIENT1 가상 컴퓨터에 참가 합니다.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

참고 하면 회사를 제공 해야\\User1 도메인 계정 자격 증명 **추가 컴퓨터** 명령을 실행 합니다.
  
CLIENT1를 다시 시작한 후에 회사를 사용 하 여 연결\\User1 계정 이름 및 암호를 한 다음 관리자 수준 Windows PowerShell 명령 프롬프트를 엽니다.
  
그런 다음 CLIENT1에서 a p p 1에서 웹 서버 및 파일 공유 리소스에 액세스할 수 있는지 확인 합니다.
  
### <a name="verify-client-access-to-app1"></a>A p p 1에 대 한 클라이언트 액세스를 확인 합니다.

1. 서버 관리자에서 트리 창에서 **로컬 서버**를 클릭 합니다.
    
2. **CLIENT1에 대 한 속성** **에서** **IE의 보안 강화 구성을**옆에 있는 클릭 합니다.
    
3. **Internet Explorer 보안 강화 구성** **관리자** 및 **사용자**대 한 **해제** 를 클릭 한 다음 **확인**을 클릭 합니다.
    
4. 시작 화면에서 **Internet Explorer**클릭 한 다음 **확인**을 클릭 합니다.
    
5. 주소 표시줄에 **http://app1.corp.contoso.com/**입력 하 고 ENTER 키를 누릅니다. A p p 1에 대 한 기본 인터넷 정보 서비스 웹 페이지를 참조 해야 합니다.
    
6. 바탕 화면 작업 표시줄에서 파일 탐색기 아이콘을 클릭 합니다.
    
7. 주소 표시줄에 입력 ** \\ \\a p p 1\\파일**를 누른 다음 ENTER 키를 누릅니다. 파일 공유 폴더의 내용이 들어 있는 폴더 창이 표시 됩니다.
    
8. **파일** 공유 폴더 창에서 **Example.txt** 파일을 두번클릭 합니다. Example.txt 파일의 내용을 표시 됩니다.
    
9. **Example.txt-메모장** 및 **파일** 공유 폴더 창을 닫습니다.
    
마지막 구성입니다.
  
![CLIENT1 가상 컴퓨터를 사용한 Azure의 기본 구성 4단계](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Azure의 기본 구성을 추가 테스트 환경 만들기 (영문) 또는 응용 프로그램 개발 및 테스트에 대 한 준비가 되었습니다. 
  
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>Azure의 테스트 환경 가상 컴퓨터의 비용을 최소화
<a name="mincost"> </a>

테스트 환경 가상 컴퓨터를 실행 하는 비용을 최소화 하려면 다음 중 하나를 수행할 수 있습니다.
  
- 테스트 환경 만들기 및 필요한 테스트 및 데모를 최대한 신속 하 게 수행 합니다. 완료 되 면 테스트 환경에 대 한 리소스 그룹을 삭제 합니다.
    
- 테스트 환경 가상 컴퓨터를 할당 취소 된 상태로 종료 됩니다.
    
Azure PowerShell을 사용한 가상 컴퓨터를 종료 하려면 자원 그룹 이름을 입력 하 고이 명령을 실행 합니다.
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

가상 컴퓨터가 제대로 때 시작 하 여 모든 상태가 중지 됨 (Deallocated)에서 작동 하려면, 다음 순서 대로 시작 해야 있습니다.
  
1. DC1
    
2. A P P 1
    
3. CLIENT1
    
Azure PowerShell을 사용한 순서를 가상 컴퓨터를 시작 하려면 자원 그룹 이름을 입력 하 고이 명령을 실행 합니다.
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>참고 항목

<a name="mincost"> </a>

[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경에 대 한 위협 보호 고급](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


