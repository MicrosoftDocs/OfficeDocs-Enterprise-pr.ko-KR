---
title: "Office 365 개발/테스트 환경에 대 한 페더레이션된 id"
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
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "요약: Office 365 개발/테스트 환경에 대 한 연결 된 인증을 구성 합니다."
ms.openlocfilehash: 62d3b5483a405a591038f347af2b9bcc798b1917
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경에 대 한 페더레이션된 id

 **요약:** Office 365 개발/테스트 환경에 대 한 연결 된 인증을 구성 합니다.
  
Office 365 페더레이션된 id를 지원합니다. 이 자격 증명의 유효성 검사를 자체 수행 하는 대신 Office 365 연결 하는 사용자를 참조 Office 365에서 트러스트 된 연결 된 인증 서버를 의미 합니다. 사용자의 자격 증명이 올바른지, 연결 된 인증 서버 클라이언트 다음에 전송 하는 Office 365 인증 증거로 보안 토큰을 발급 합니다. 페더레이션된 id는 오프 로드 및 Office 365 구독 및 고급 보안 및 인증 시나리오에 대 한 인증의 수직 확장 수 있습니다.
  
이 문서에서는 구성 하는 방법을 Office 365 개발/테스트 환경에 대 한 연결 된 인증 다음 그 결과 설명 합니다.
  
**그림 1: Office 365 개발/테스트 환경에 대 한 연결 된 인증**

![웹 응용 프로그램 프록시 서버가 Office 365에 대한 DirSync 개발/테스트 환경에 추가됨](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
그림 1에 표시 된 구성 이루어져 있습니다. 
  
- Office 365 e 5 평가판 구독을 만들 때에서 30 일이 지나면 만료는 합니다.
    
- 간소화 된 조직 인트라넷 (d c 1, a p p 1, CLIENT1, ADFS1, 및 PROXY1) Azure 가상 네트워크의 서브넷에 다섯 개의 가상 컴퓨터의 구성 되는 인터넷에 연결 합니다. Azure AD 연결 Office 365에 Windows Server AD 도메인의 계정 목록을 동기화 하는 a p p 1을 실행 합니다. PROXY1 들어오는 인증 요청을 받습니다. ADFS1 d c 1에 자격 증명의 유효성을 검사 하 고 보안 토큰을 발급 합니다.
    
이 개발/테스트 환경 설정에 다섯 단계로 가지가 있습니다.
  
1. DirSync를 사용한 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경 만들기
    
2. AD FS 서버 (ADFS1)를 만듭니다.
    
3. 웹 프록시 서버 (PROXY1)를 만듭니다.
    
4. 자체 서명 된 인증서를 만들고 ADFS1 및 PROXY1를 구성 합니다.
    
5. 페더레이션된 id에 대 한 Office 365를 구성 합니다.
    
Azure의 Office 365에 대 한 연결 된 인증의 프로덕션 배포를 진행 하려면 [Azure의 Office 365에 대 한 배포 고가용성 페더레이션된 인증](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)을 참조 합니다.
  
> [!NOTE]
> 이 개발/테스트 환경 Azure 평가판 구독을 구성할 수 없습니다. 
  
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a>1 단계: 디렉터리 동기화와 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경 만들기

디렉터리 동기화 서버 및 Office 365와 Windows Server AD 간의 동기화 된 id로 a p p 1으로 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경 만들기를 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md) 의 지침에 따라 d c 1에 대 한 계정입니다.
  
다음으로 새 공용 DNS 도메인 이름을 기준으로 현재 도메인 이름을 만들고 Office 365 구독을 추가 합니다. 이름을 사용 하는 것이 좋습니다 **테스트 실습.** \<공용 도메인 >. 예, 공용 도메인 이름이 contoso.com 이면 공용 도메인 이름 testlab.contoso.com를 추가 합니다.
  
DNS 공급자에서 올바른 DNS 레코드를 만들고 Office 365 평가판 구독에 도메인을 추가 하는 방법에 대 한 지침을 [사용자 추가 및 Office 365에 도메인을](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)참조 하십시오. 
  
구성 결과는 다음과 같습니다.
  
**Office 365 개발/테스트 환경에 대 한 그림 2: 디렉터리 동기화**

![DirSync를 사용하는 Office 365 개발/테스트 환경](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
그림 2는 Azure 가상 네트워크의 Office 365 및 CLIENT1, a p p 1을 및 d c 1에 가상 컴퓨터를 포함 하는 Office 365 개발/테스트 환경에 대 한 디렉터리 동기화를 보여줍니다.
  
## <a name="phase-2-create-the-ad-fs-server"></a>2 단계: AD FS 서버 만들기

AD FS 서버는 Office 365와 d c 1에서 호스팅되는 corp.contoso.com 도메인의 계정 간의 연결 된 인증을 제공 합니다.
  
ADFS1에 대 한 Azure 가상 컴퓨터를 만들려면 구독 및 자원 그룹 및 사용자 기본 구성에 대 한 Azure 위치의 이름을 입력 하 고 로컬 컴퓨터에서 이러한 명령을 Azure PowerShell 명령 프롬프트에서 다음 실행 합니다.
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> 클릭 [여기](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) 이 문서의 모든 PowerShell 명령을 포함 된 텍스트 파일을 가져오도록 합니다.
  
다음으로 ADFS1 로컬 관리자 계정 이름과 암호를 사용 하 여 ADFS1 가상 컴퓨터에 연결 하는 [Azure 포털](http://portal.azure.com) 을 사용 하 고 Windows PowerShell 명령 프롬프트를 엽니다.
  
ADFS1 및 d c 1 간의 이름 확인 및 네트워크 통신을 확인 하려면 **ping dc1.corp.contoso.com** 명령을 실행 하 고 응답을 4 번 남아 있지 않은지 확인 합니다.
  
다음으로, ADFS1에서 Windows PowerShell 프롬프트에 다음이 명령 사용 하 여 회사 도메인에 ADFS1 가상 컴퓨터에 참가 합니다.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

구성 결과는 다음과 같습니다.
  
**그림 3: AD FS 서버 추가 (영문)**

![AD FS 서버가 Office 365에 대한 DirSync 개발/테스트 환경에 추가됨](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
그림 3은 Office 365 개발/테스트 환경에 대 한 디렉터리 동기화를 ADFS1 서버 추가 보여줍니다.
  
## <a name="phase-3-create-the-web-proxy-server"></a>3 단계: 웹 프록시 서버를 만들기

PROXY1은 사용자 인증을 시도 하 고 ADFS1 간에 인증 메시지의 프록시를 제공 합니다.
  
PROXY1에 대 한 Azure 가상 컴퓨터를 만들려면 자원 그룹 및 Azure 위치의 이름을 입력 하 고 로컬 컴퓨터에서 이러한 명령을 Azure PowerShell 명령 프롬프트에서 다음 실행 합니다.
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> PROXY1은 PROXY1 가상 컴퓨터를 다시 시작 하는 경우, 그리고 그 포인트 바꾸어야 하는 공용 DNS 레코드를 만들어야 하므로 고정 공용 IP 주소를 할당 됩니다. 
  
다음으로, PROXY1의 개인 IP 주소 및 TCP 포트 443 인터넷에서 원하지 않는 인바운드 트래픽 허용 하는 회사 서브넷에 대 한 네트워크 보안 그룹에 규칙을 추가 합니다. Azure PowerShell 명령 프롬프트에서 로컬 컴퓨터에서 이러한 명령을 실행 합니다.
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

다음으로 [Azure 포털](http://portal.azure.com) 을 사용 하 여 PROXY1 로컬 관리자 계정 이름과 암호를 사용 하 여 PROXY1 가상 컴퓨터에 연결할 하 고 PROXY1에서 Windows PowerShell 명령 프롬프트를 엽니다.
  
PROXY1 및 d c 1 간의 이름 확인 및 네트워크 통신을 확인 하려면 **ping dc1.corp.contoso.com** 명령을 실행 하 고 응답을 4 번 남아 있지 않은지 확인 합니다.
  
다음으로, PROXY1에서 Windows PowerShell 프롬프트에 다음이 명령 사용 하 여 회사 도메인에 PROXY1 가상 컴퓨터에 참가 합니다.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

로컬 컴퓨터에서 이러한 Azure PowerShell 명령으로 PROXY1의 공용 IP 주소를 표시 합니다.
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

다음으로, 공용 DNS 공급자를 사용 하 고에 대 한 새 공용 DNS A 레코드를 만들려면 **fs.testlab.** \<DNS 도메인 이름을 > **쓰기 호스트** 명령에 의해 표시 되는 IP 주소를 확인 하는 합니다. **fs.testlab.** \<DNS 도메인 이름 >이 *페더레이션 서비스 FQDN으로* 참조 합니다.
  
다음으로 [Azure 포털](http://portal.azure.com) 을 사용 하 여는 회사를 사용 하 여 d c 1에 가상 컴퓨터에 연결할\\저장 된 관리자 수준 Windows PowerShell 명령 프롬프트에서 명령을 User1 자격 증명 하 고 다음을 실행 합니다.
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

이러한 명령은 페더레이션 서비스 Azure 가상 네트워크에서 가상 컴퓨터 ADFS1의 개인 IP 주소를 확인할 수 있는 FQDN에 대 한 DNS A 레코드를 만듭니다.
  
구성 결과는 다음과 같습니다.
  
**그림 4: 웹 응용 프로그램 프록시 서버 추가 (영문)**

![웹 응용 프로그램 프록시 서버가 Office 365에 대한 DirSync 개발/테스트 환경에 추가됨](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
그림 4 PROXY1 서버 추가 보여줍니다.
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>4 단계: 자체 서명 된 인증서를 만들고 ADFS1 및 PROXY1 구성

이 단계에서 자체 서명 된 디지털 인증서를 페더레이션 서비스 FQDN에 대 한 만들고 AD FS 팜으로 ADFS1 및 PROXY1를 구성 합니다.
  
먼저, [Azure 포털](http://portal.azure.com) 을 사용 하 여는 회사를 사용 하 여 d c 1에 가상 컴퓨터에 연결할\\User1 자격 증명 및 다음 열기를 관리자 수준 Windows PowerShell 명령 프롬프트입니다.
  
D c 1에서 Windows PowerShell 명령 프롬프트에서이 명령을 사용 하 여 AD FS 서비스 계정을 다음으로 만듭니다.
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

이 명령은 계정 암호를 입력 하 게 묻는 메모 합니다. 강력한 암호를 선택 하 고 안전한 위치에 기록 합니다. 이 단계와 5 단계에 대 한 할 수 있습니다.
  
[Azure 포털](http://portal.azure.com) 을 사용 하 여는 회사를 사용 하 여 ADFS1 가상 컴퓨터에 연결할\\User1 자격 증명입니다. ADFS1에서 관리자 수준 Windows PowerShell 명령 프롬프트를 열고, 페더레이션 서비스 FQDN 입력 하 고 자체 서명 된 인증서를 만들려면 다음이 명령을 실행 합니다.
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

다음으로 새 자체 서명 된 인증서를 파일로 저장 하려면 다음이 단계를 사용 합니다.
  
1. **시작**을 클릭 하 고 **mmc.exe**입력 한 다음 **Enter**키를 누릅니다.
    
2. 클릭 **파일 > 스냅인 추가/제거**합니다.
    
3. **추가 또는 제거 스냅인에서**사용 가능한 스냅인 목록에서 **인증서** 를 두번클릭, **컴퓨터 계정**을 클릭 하 고 ****을 클릭 합니다.
    
4. **컴퓨터 선택** **완료 날짜**를 클릭 한 다음 **확인**을 클릭 합니다.
    
5. 트리 창에서 엽니다 **인증서 (로컬 컴퓨터) > 개인 > 인증서**합니다.
    
6. 페더레이션 서비스 FQDN 사용 하 여 인증서를 마우스 오른쪽 단추로 클릭 하 고 **모든 작업**을 클릭 한 다음 **내보내기를**클릭 합니다.
    
7. **시작** 페이지에서 **다음**을 클릭 합니다.
    
8. **개인 키 내보내기** 페이지에서 **예**를 클릭 하 고 ****을 클릭 합니다.
    
9. **파일 내보내기 형식** 페이지에서 **모든 확장 된 속성 내보내기**를 클릭 하 고 ****을 클릭 합니다.
    
10. **보안** 페이지에서 **암호** 및 **암호** 에 암호를 입력 하 고 **암호 확인.**
    
11. **내보낼 파일** 페이지에서 **찾아보기**를 클릭 합니다.
    
12. 이동은 **c:\\인증서** **파일 이름** **SSL** 을 입력 하 고 다음을 클릭 하는 폴더를 **저장.**
    
13. **내보낼 파일** 페이지에서 **다음**을 클릭 합니다.
    
14. **인증서 내보내기 마법사 완료** 페이지에서 **마침**을 클릭 합니다. 대화 상자가 나타나면 **확인**을 클릭 합니다.
    
다음으로, ADFS1에서 Windows PowerShell 명령 프롬프트에서이 명령을 사용 하 여 AD FS 서비스를 설치 합니다.
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

설치를 완료 될 때까지 기다립니다.
  
다음, 다음이 단계와 AD FS 서비스를 구성 합니다.
  
1. **시작**을 클릭 한 다음 **서버 관리자** 아이콘을 클릭 합니다.
    
2. 서버 관리자의 트리 창에서 **AD FS**를 클릭 합니다.
    
3. 맨 위쪽에 있는 도구 모음에서 주황색 주의 기호를 클릭 하 고 **이 서버에서 페더레이션 서비스 구성**을 클릭 합니다.
    
4. Active Directory Federation Services 구성 마법사의 **시작** 페이지에서 **다음**을 클릭 합니다.
    
5. **AD DS에 연결** 페이지에서 **다음**을 클릭 합니다.
    
6. **서비스 속성 지정** 페이지 수행 합니다.
    
  - **SSL 인증서**대 한 아래쪽 화살표를 클릭 하 고 FQDN 페더레이션 서비스의 이름 사용 하 여 인증서를 클릭 합니다.
    
  - **페더레이션 서비스 표시 이름**가상의 조직 이름을 입력 합니다.
    
  - **다음**을 클릭합니다.
    
7. **서비스 계정 지정** 페이지에서 **계정 이름**에 대 한 **선택** 을 클릭 합니다.
    
8. **사용자 선택 또는 서비스 계정에서** **ADFS 서비스**를 입력 하 고 **이름 확인**을 클릭 한 다음 **확인**을 클릭 합니다.
    
9. **계정 암호**ADFS 서비스 계정에 대 한 암호를 입력 하 고 ****을 클릭 합니다.
    
10. **구성 데이터베이스 지정** 페이지에서 **다음**을 클릭 합니다.
    
11. **검토 옵션** 페이지에서 **다음**을 클릭 합니다.
    
12. **필수 확인** 페이지에서 **구성**을 클릭 합니다.
    
13. **결과** 페이지에서 **닫기를**클릭 합니다.
    
14. **시작**을 클릭 전원 아이콘을 클릭 **를 다시 시작**을 클릭 한 다음 **계속**을 클릭 합니다.
    
[Azure 포털](http://portal.azure.com)PROXY1는 회사와 연결\\User1 계정 자격 증명입니다.
  
다음으로, 다음이 단계를 사용 하 여 자체 서명 된 인증서를 설치 하 고 PROXY1를 구성 합니다.
  
1. **시작**을 클릭 하 고 **mmc.exe**입력 한 다음 **Enter**키를 누릅니다.
    
2. 클릭 **파일 > 스냅인 추가/제거**합니다.
    
3. **추가 또는 제거 스냅인에서**사용 가능한 스냅인 목록에서 **인증서** 를 두번클릭, **컴퓨터 계정**을 클릭 하 고 ****을 클릭 합니다.
    
4. **컴퓨터 선택** **완료 날짜**를 클릭 한 다음 **확인**을 클릭 합니다.
    
5. 트리 창에서 엽니다 **인증서 (로컬 컴퓨터) > 개인 > 인증서**합니다.
    
6. **개인**을 마우스 오른쪽 단추로 클릭 하 고 **모든 작업**을 클릭 한 다음 **가져오기**를 클릭 합니다.
    
7. **시작** 페이지에서 **다음**을 클릭 합니다.
    
8. **가져올 파일** 페이지에서 입력 ** \\ \\adfs1\\인증서\\ssl.pfx**, **다음**을 클릭 합니다.
    
9. **개인 키 보호** 페이지에서 **암호**인증서 암호를 입력 하 고 다음을 클릭 **다음.**
    
10. **인증서 저장소** 페이지에서 다음을 클릭 **다음.**
    
11. **완료** 페이지에서 **마침**을 클릭 합니다.
    
12. **인증서 저장소** 페이지에서 **다음**을 클릭 합니다.
    
13. 대화 상자가 나타나면 **확인**을 클릭 합니다.
    
14. 트리 창에서 **인증서** 를 클릭 합니다.
    
15. 인증서를 마우스 오른쪽 단추로 클릭 한 다음 **복사**를 클릭 합니다.
    
16. 트리 창에서 엽니다 **신뢰할 수 있는 루트 인증 기관 > 인증서**합니다.
    
17. 설치 된 인증서, 마우스 클릭의 목록 아래 마우스 포인터를 **붙여넣습니다**.
    
관리자 수준의 PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

설치를 완료 될 때까지 기다립니다.
  
다음이 단계를 사용 하 여 해당 페더레이션 서버로 ADFS1를 사용 하 여 웹 응용 프로그램 프록시 서비스를 구성 합니다.
  
1. **시작**을 클릭 한 다음 **서버 관리자**를 클릭 합니다.
    
2. 트리 창에서 **원격 액세스**를 클릭 합니다.
    
3. 맨 위쪽에 있는 도구 모음에서 주황색 주의 기호를 클릭 한 다음 **웹 응용 프로그램 프록시 마법사 열기**를 클릭 합니다.
    
4. 웹 응용 프로그램 프록시 구성 마법사의 **시작** 페이지에서 **다음**을 클릭 합니다.
    
5. **페더레이션 서버** 페이지 수행 합니다.
    
  - **페더레이션 서비스 이름**에 페더레이션 서비스 FQDN을 입력 합니다.
    
  - 형식은 **CORP\\User1** **사용자**이름에서입니다.
    
  - **암호**에 User1 계정에 대 한 암호를 입력 합니다.
    
  - **다음**을 클릭합니다.
    
6. **AD FS 프록시 인증서** 페이지에서 아래쪽 화살표를 클릭 하 고 페더레이션 서비스 FQDN 사용 하 여 인증서를 클릭 한 다음 **다음**을 클릭 합니다.
    
7. **확인** 페이지에서 **구성**을 클릭 합니다.
    
8. **결과** 페이지에서 **닫기를**클릭 합니다.
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a>단계 5: 페더레이션된 id에 대 한 Office 365 구성

[Azure 포털](http://portal.azure.com) 을 사용 하 여는 회사와 a p p 1 가상 컴퓨터에 연결할\\User1 계정 자격 증명입니다.
  
다음이 단계를 사용 하 여 Azure AD 연결 및 연결 된 인증에 대 한 Office 365 구독을 구성 합니다.
  
1. 바탕 화면에서 **Azure AD 연결**을 두번클릭 합니다.
    
2. **Azure AD 연결을 시작** 페이지에서 **구성**을 클릭 합니다.
    
3. **추가 작업** 페이지에서 **변경 사용자 로그인**을 클릭 하 고 ****을 클릭 합니다.
    
4. **Azure AD에 연결** 페이지에서 Office 365 전역 관리자 계정 이름과 암호를 입력 하 고 ****을 클릭 합니다.
    
5. **사용자 로그인** 페이지에서 **AD FS와의 페더레이션을 사용**을 클릭 하 고 ****을 클릭 합니다.
    
6. **AD FS 팜** 페이지에서 **기존 AD FS 팜 사용**을 클릭 하, **ADFS1** **서버 이름**입력 하 고 ****을 클릭 합니다.
    
7. 서버 자격 증명에 대 한 대화 상자가 나타나면는 회사의 자격 증명을 입력\\User1 계정으로 한 다음 **확인**을 클릭 합니다.
    
8. **도메인 관리자** 자격 증명 페이지에서 입력 **CORP\\User1** **사용자 이름** 및 **암호**계정 암호에 **다음**을 클릭 하 고 있습니다.
    
9. **AD FS 서비스 계정** 페이지에서 입력 **CORP\\ADFS 서비스** **도메인의 사용자 이름** 및 **도메인 사용자 암호**계정 암호에 **다음**을 클릭 하 고 있습니다.
    
10. **도메인** **Azure AD 도메인** 페이지에서 이전에 만든 하 고 1 단계에서에서 Office 365 구독에 추가 하는 도메인의 이름을 선택 하 고 ****을 클릭 합니다.
    
11. **구성 준비 완료** 페이지에서 **구성**을 클릭 합니다.
    
12. **설치 완료** 페이지에서 **확인**을 클릭 합니다.
    
    인트라넷 및 인터넷 모두 있는지 여부를 나타내는 메시지를 참조 해야 구성 확인 되었습니다.
    
13. **설치 완료** 페이지에서 **끝내기**를 클릭 합니다.
    
을 설명 하기 위해 해당 페더레이션된 인증 (영문)은 다음을 수행 합니다.
  
1. 로컬 컴퓨터에서 브라우저의 새 개인 인스턴스를 열고 [https://portal.office.com](https://portal.office.com)로 이동 합니다.
    
2. 로그인 자격 증명을 입력 **@ user1**\<1 단계에서에서 만든 도메인 >. 
    
    예를 들어 **testlab.contoso.com**테스트 도메인을 사용 하는 경우 **user1@testlab.contoso.com**을 입력 합니다. Tab 키 또는 자동으로 리디렉션됩니다를 Office 365를 허용 합니다.
    
    이제 **연결이 개인** 페이지를 표시 됩니다. 데스크톱 컴퓨터의 유효성을 검사 수 없는 ADFS1에 자체 서명 된 인증서를 설치 하기 때문에이 오류가 표시 됩니다. 연결 된 인증의 프로덕션 배포에서는 신뢰할 수 있는 인증 기관에서 인증서를 사용 하 고 사용자에 게 이렇게이 페이지를 볼 수 없습니다.
    
3. **연결이 개인** 페이지에서 **고급**클릭 하 고 다음을 클릭 **진행 \<페더레이션 서비스 FQDN >**합니다. 
    
4. 가상의 조직 이름 페이지에서 다음을 사용 하 여 로그인 합니다.
    
  - **CORP\\User1** 이름에 대 한
    
  - User1 계정에 대 한 암호
    
    **Microsoft Office** 홈페이지를 참조 해야 합니다.
    
이 절차에서는 Office 365 평가판 구독 d c 1에 호스트 되는 Windows Server AD corp.contoso.com 도메인와 페더레이션 되어있는지를 보여줍니다. 다음은 인증 프로세스를 위한 기본 사항입니다.
  
1. 로그인 계정 이름을 내에서 1 단계에서에서 만든 페더레이션된 도메인을 사용 하는 경우 Office 365에 페더레이션 브라우저를 리디렉션합니다 FQDN 및 PROXY1 서비스입니다.
    
2. PROXY1 로컬 컴퓨터의 가상의 회사 로그인 페이지를 보냅니다.
    
3. 회사를 보낼 때\\User1 및 암호를 PROXY1 것으로 전달 ADFS1 합니다.
    
4. 회사의 유효성을 검사 ADFS1\\User1 및 d c 1 사용 하 여 암호 보안 토큰을 로컬 컴퓨터에 게 보냅니다.
    
5. 로컬 컴퓨터에서 Office 365에 보안 토큰을 보냅니다.
    
6. Office 365의 보안 토큰 ADFS1 하 여 만든 및 액세스할 수 있도록 유효성을 검사 합니다.
    
이제 Office 365 평가판 구독에 연결 된 인증으로 구성 됩니다. 고급 인증 시나리오에 대 한이 개발/테스트 환경에 사용할 수 있습니다.
  
## <a name="next-step"></a>다음 단계

즉시 사용 가능성을 배포할 준비가 되 면 Azure에서 Office 365에 대 한 고가용성 연결 된 인증 [Azure의 Office 365에 대 한 배포 고가용성 연결 된 인증](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)을 참조 합니다.
  
## <a name="see-also"></a>See Also

[클라우드 채택 테스트 랩 가이드 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


