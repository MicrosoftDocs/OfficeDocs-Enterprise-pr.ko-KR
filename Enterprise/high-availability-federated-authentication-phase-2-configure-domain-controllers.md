---
title: 고가용성 페더레이션 인증 2 단계 도메인 컨트롤러 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: '요약: Microsoft Azure에서 Office 365에 대 한 고가용성 페더레이션 인증을 위한 도메인 컨트롤러 및 디렉터리 동기화 서버를 구성 합니다.'
ms.openlocfilehash: 853f7c55039fb4dcd09ae9d0d748a4e559d5564a
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257507"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>고가용성 페더레이션 인증 2단계: 도메인 컨트롤러 구성

Azure 인프라 서비스의 Office 365 페더레이션 인증을 위해 고가용성을 배포 하는이 단계에서는 Azure virtual network에서 두 개의 도메인 컨트롤러 및 디렉터리 동기화 서버를 구성 합니다. 인증에 대 한 클라이언트 웹 요청은 온-프레미스 네트워크에 대 한 사이트 간 VPN 연결을 통해 인증 트래픽을 전송 하는 것이 아니라 Azure virtual network에서 인증 될 수 있습니다.
  
> [!NOTE]
> AD FS (active Directory Federation Services)는 Active Directory 도메인 서비스의 대체 도메인으로 Azure Active Directory 도메인 서비스를 사용할 수 없습니다. 
  
[3 단계: AD FS 서버 구성](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)으로 넘어가기 전에이 단계를 완료 해야 합니다. 모든 단계에 대해 [Azure에서 Office 365에 대 한 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 를 참조 하세요.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Azure에서 도메인 컨트롤러 가상 컴퓨터 만들기

먼저, 테이블 M의 **가상 컴퓨터 이름** 열을 채우고 **최소 크기** 열에서 가상 컴퓨터 크기를 필요한만큼 수정합니다.
  
|**항목**|**가상 컴퓨터 이름**|**갤러리 이미지**|**저장소 유형**|**최소 크기**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![](./media/Common-Images/TableLine.png)(첫 번째 도메인 컨트롤러, 예: DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![](./media/Common-Images/TableLine.png)(두 번째 도메인 컨트롤러, 예: DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![](./media/Common-Images/TableLine.png)(디렉터리 동기화 서버, 예: DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![](./media/Common-Images/TableLine.png)(첫 번째 AD FS 서버, 예: ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![](./media/Common-Images/TableLine.png)(두 번째 AD FS 서버, 예:: ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![](./media/Common-Images/TableLine.png)(첫 번째 웹 응용 프로그램 프록시 서버, 예: WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![](./media/Common-Images/TableLine.png)(두 번째 웹 응용 프로그램 프록시 서버, 예: WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **테이블 M-Azure의 Office 365에 대 한 고가용성 페더레이션 인증용 가상 컴퓨터**
  
가상 컴퓨터 크기의 전체 목록은 [가상 컴퓨터 크기](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)를 참조하세요.
  
다음 Azure PowerShell 명령 블록은 두 도메인 컨트롤러에 대 한 가상 컴퓨터를 만듭니다. 변수 값을 지정 하 \< 고 및 > 문자를 제거 합니다. 이 Azure PowerShell 명령 블록은 다음 테이블의 값을 사용 합니다.
  
- 테이블 M, 가상 컴퓨터
    
- 테이블 R, 리소스 그룹
    
- 테이블 V, 가상 네트워크 설정
    
- 테이블 S, 서브넷
    
- 테이블 I, 고정 IP 주소
    
- 테이블 A, 가용성 집합
    
[1 단계: Azure 구성](high-availability-federated-authentication-phase-1-configure-azure.md)에서 테이블 R, V, S, I 및 A를 정의한 것을 기억 합니다.
  
> [!NOTE]
> 다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell을 시작 하기를](https://docs.microsoft.com/powershell/azure/get-started-azureps)참조 하세요. 
  
올바른 값을 모두 제공하면 Azure PowerShell 프롬프트나 로컬 컴퓨터의 PowerShell ISE(통합 스크립트 환경)에서 결과 블록을 실행합니다.
  
> [!TIP]
> 사용자 지정 설정에 따라 실행 가능한 PowerShell 명령 블록을 생성 하려면이 [Microsoft Excel 구성 통합 문서](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)를 사용 합니다. 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> 이러한 가상 컴퓨터는 인트라넷 응용 프로그램용이므로 공용 IP 주소나 DNS 도메인 이름 레이블에 할당되지 않으며 인터넷에 표시되지 않습니다. 그러나 이는 Azure Portal에서 연결할 수 없음을 의미합니다. 가상 컴퓨터의 속성을 보면 이 **연결** 옵션을 사용할 수 없습니다. 원격 데스크톱 연결 액세서리 또는 다른 원격 데스크톱 도구를 사용하여 개인 IP 주소나 인트라넷 DNS 이름을 사용하는 가상 컴퓨터에 연결할 수 있습니다.
  
## <a name="configure-the-first-domain-controller"></a>첫 번째 도메인 컨트롤러 구성

원하는 원격 데스크톱 클라이언트를 사용하고 첫 번째 도메인 컨트롤러 가상 컴퓨터에 대한 원격 데스크톱 연결을 만듭니다. 인트라넷 DNS나 컴퓨터 이름 및 로컬 관리자 계정의 자격 증명을 사용합니다.
  
다음으로 **첫 번째 도메인 컨트롤러 가상 컴퓨터의**Windows PowerShell 명령 프롬프트에서 다음 명령을 사용 하 여 첫 번째 도메인 컨트롤러에 추가 데이터 디스크를 추가 합니다.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

그런 다음 **ping** 명령으로 조직 네트워크의 리소스 이름과 IP 주소를 ping하여 조직 네트워크의 위치에 대한 첫 번째 도메인 컨트롤러의 연결을 테스트합니다.
  
이 프로시저에서는 DNS 이름 확인이 제대로 작동하는지(가상 컴퓨터가 온-프레미스 DNS 서버와 올바르게 구성되었는지)와 프레미스 간 가상 네트워크에서 이 패킷을 보낼 수 있는지 확인합니다. 기본 테스트가 실패하면 DNS 이름 확인 및 패킷 배달 문제의 해결 방법을 IT 부서에 문의합니다.
  
다음으로 첫 번째 도메인 컨트롤러의 Windows PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

도메인 관리자 계정의 자격 증명을 제공하라는 메시지가 나타납니다. 컴퓨터가 다시 시작됩니다.
  
## <a name="configure-the-second-domain-controller"></a>두 번째 도메인 컨트롤러 구성

원하는 원격 데스크톱 클라이언트를 사용하고 두 번째 도메인 컨트롤러 가상 컴퓨터에 대한 원격 데스크톱 연결을 만듭니다.  인트라넷 DNS나 컴퓨터 이름 및 로컬 관리자 계정의 자격 증명을 사용합니다.
  
다음으로 **두 번째 도메인 컨트롤러 가상 컴퓨터의**Windows PowerShell 명령 프롬프트에서 다음 명령을 사용 하 여 추가 데이터 디스크를 두 번째 도메인 컨트롤러에 추가 해야 합니다.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

그리고 다음 명령을 실행합니다.
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

도메인 관리자 계정의 자격 증명을 제공하라는 메시지가 나타납니다. 컴퓨터가 다시 시작됩니다.
  
다음으로 Azure가 두 개의 새 도메인 컨트롤러의 IP 주소를 DNS 서버로 사용할 가상 컴퓨터를 할당하도록 가상 네트워크의 DNS 서버를 업데이트해야 합니다. 변수를 입력 하 고 로컬 컴퓨터의 Windows PowerShell 명령 프롬프트에서 다음 명령을 실행 합니다.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

이제 온-프레미스 DNS 서버가 DNS 서버로 구성되지 않도록 두 도메인 컨트롤러를 다시 시작합니다. 모두 DNS 서버이므로 도메인 컨트롤러로 수준을 올리면 온-프레미스 DNS 서버가 DNS 전달자로 자동 구성됩니다.
  
다음으로 Azure Virtual Network의 서버가 로컬 도메인 컨트롤러를 사용하도록 Active Directory 복제 사이트를 만들어야 합니다. 도메인 관리자 계정을 사용 하 여 도메인 컨트롤러에 연결 하 고 관리자 수준 Windows PowerShell 프롬프트에서 다음 명령을 실행 합니다.
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>디렉터리 동기화 서버 구성

원하는 원격 데스크톱 클라이언트를 사용 하 고 디렉터리 동기화 서버 가상 컴퓨터에 대 한 원격 데스크톱 연결을 만듭니다. 인트라넷 DNS나 컴퓨터 이름 및 로컬 관리자 계정의 자격 증명을 사용합니다.
  
다음으로, Windows PowerShell 프롬프트에서 다음 명령을 사용 하 여 해당 AD DS 도메인에 가입 합니다.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

이 단계를 성공적으로 완료하면 자리 표시자 컴퓨터 이름이 포함된 다음 구성이 설정됩니다.
  
**2 단계: Azure의 고가용성 페더레이션 인증 인프라에 대 한 도메인 컨트롤러 및 디렉터리 동기화 서버**

![도메인 컨트롤러를 사용한 고가용성 Office 365 Azure의 페더레이션 인증 인프라 2 단계](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>다음 단계

[3 단계: CONFIGURE AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) 을 사용 하 여이 작업을 계속 구성 합니다.
  
## <a name="see-also"></a>참고 항목

[Azure에서 Office 365용 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 개발/테스트 환경에 대 한 페더레이션된 id](federated-identity-for-your-office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


