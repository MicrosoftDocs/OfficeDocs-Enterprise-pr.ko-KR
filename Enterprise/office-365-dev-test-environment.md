---
title: Office 365 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
ms.audience: ITPro
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
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: '요약: 이 테스트 랩 가이드를 사용하여 평가 또는 개발/테스트를 위한 Office 365 평가판 구독을 만듭니다.'
ms.openlocfilehash: a49ba10ab9ddded36f21ca9cc92f0482cbe7a4fb
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038034"
---
# <a name="office-365-devtest-environment"></a>Office 365 개발/테스트 환경

 **요약:** 이 테스트 랩 가이드를 사용하여 평가 또는 개발/테스트를 위한 Office 365 평가판 구독을 만듭니다.
  
Office 365 평가판 구독을 사용하여 응용 프로그램에 대한 Office 365 개발/테스트 환경을 만들거나 Office 365의 기능과 특성을 구현해볼 수 있습니다. 다음 두 버전을 사용할 수 있습니다.
  
- 경량 Office 365 개발/테스트 환경은 주 컴퓨터에서 액세스하는 Office 365 평가판 구독으로 구성됩니다.
    
    기능을 빠르게 구현해보려면 이 환경을 사용합니다. 경량 Office 365 개발/테스트 환경에서는 이 문서의 2, 3단계만 완료합니다.
    
- 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경은 Office 365 평가판 구독과 인터넷에 연결되며 Microsoft Azure 인프라 서비스에 호스트된 간소화된 조직 인트라넷으로 구성됩니다. 이 구성은 Microsoft 클라우드에서 완전히 작성할 수 있습니다.
    
    인터넷에 연결된 전형적인 조직 네트워크와 유사한 환경에서 기능이나 앱을 구현해보거나, 이러한 유형의 환경이 필요한 기능을 사용하려면 이 환경을 사용합니다. 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경에서는 이 문서의 1, 2 및 3단계를 완료합니다.
    
> [!NOTE]
> 30일 간의 Office 365 평가판 구독 기간이 끝난 후에도 이 환경에 필요할 수 있는 특정 값을 기록해 두려면 이 문서를 인쇄할 수 있습니다. 추가로 30일 동안 내역 구독을 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다. 
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>1단계: Azure에서 기본 구성 만들기

[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)의 지침을 따릅니다.
  
Azure 구독이 필요합니다. 이 구성을 위해 [Azure 무료 평가판](https://azure.microsoft.com/pricing/free-trial/)을 사용할 수 있습니다. MSDN 또는 Visual Studio 구독이 있는 경우 [Visual Studio 구독자를 위한 월별 Azure 크레딧](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)을 참조하세요.
  
구성 결과는 다음과 같습니다.
  
![Azure의 기본 구성 개발/테스트 환경](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
이 구성은 Azure Virtual Network의 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신으로 이루어집니다.
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>2단계: Office 365 평가판 구독 만들기

Office 365 E5 평가판 구독을 시작하려면 먼저 가상의 회사 이름 및 새 Microsoft 계정이 필요합니다.
  
1. 회사 이름으로 Microsoft 샘플 콘텐츠에 사용되는 가상의 회사인 Contoso의 변형을 사용하는 것이 좋지만 필수는 아닙니다. 여기에 가상의 회사 이름을 기록하세요. ![](./media/Common-Images/TableLine.png)
    
2. 새 Microsoft 계정을 등록하려면으로 [https://outlook.com](https://outlook.com)으로 이동한 후 새 전자 메일 계정 및 주소를 사용하여 계정을 만듭니다. 이 계정을 사용하여 Office 365에 등록합니다.
    
  - 여기에 새 계정의 이름과 성을 기록합니다. ![](./media/Common-Images/TableLine.png)
    
  - 여기서 새 전자 메일 계정 주소를 기록합니다. ![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Office 365 E5 평가판 구독 등록

1. 경량 Office 365 개발/테스트 환경의 경우 컴퓨터에서 인터넷 브라우저를 열고 [https://aka.ms/e5trial](https://aka.ms/e5trial)로 이동합니다. 
    
    시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경의 경우 Azure Portal에서 CORP\User1 계정을 사용하여 CLIENT1에 연결합니다.

    시작 화면에서 Microsoft Edge를 실행하고 [https://aka.ms/e5trial](https://aka.ms/e5trial)로 이동합니다.
    
2. **반갑습니다. 자기소개 정보를 제공해 주세요.** 페이지에서 다음을 지정합니다.
    
  - 사용자의 실제 위치
    
  - 새 Microsoft 계정의 이름 및 성
    
  - 새 전자 메일 계정 주소
    
  - 회사 전화 번호
    
  - 가상의 회사 이름
    
  - 250-999명의 사용자로 구성된 조직 규모
    
3. **마지막 단계만 남음**을 클릭합니다.
    
4. **사용자 ID 만들기** 페이지에서 새 전자 메일 주소를 기준으로 하는 사용자 이름을 입력하고 @ 기호를 입력한 후 가상의 회사를 입력하고(이름에서 모든 공백 제거), 이 새 Office 365 계정에 대한 암호를 입력합니다(두 번).
    
    입력한 암호를 안전한 위치에 기록해둡니다.
    
    **조직 이름**으로 지칭될 가상의 회사 이름을 여기에 기록합니다. ![](./media/Common-Images/TableLine.png)
    
5. **내 계정 만들기**를 클릭합니다.
    
6. **자동 가입 방지를 위한 절차입니다.** 페이지에서 문자 입력이 가능한 휴대폰의 전화 번호를 입력하고 **문자 메시지 받기**를 클릭합니다.
    
7. 받은 문자 메시지의 확인 코드를 입력하고 **다음**을 클릭합니다.
    
8. 여기에 로그인 페이지 URL을 기록합니다(선택 후 복사). ![](./media/Common-Images/TableLine.png)
    
9. 여기에 사용자 ID를 기록합니다(선택 후 복사). ![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    이 값은 **Office 365 전역 관리자 이름**으로 사용됩니다.
    
10. **준비가 되었습니다.** 가 표시되면 클릭합니다.
    
11. 다음 페이지에서 Office 365 설정이 완료되고 모든 타일을 사용할 수 있게 될 때까지 기다립니다.
    
Office Online 서비스 및 Microsoft 365 관리 센터에 액세스할 수 있는 기본 Office 365 포털 페이지가 표시됩니다.
  
시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경의 경우 결과 구성은 다음과 같습니다.
  
![Office 365 개발/테스트 환경](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
이 구성은 다음으로 이루어집니다. 
  
- Azure Virtual Network의 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신
    
- Office 365 E5 평가판 구독
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>3단계: Office 365 평가판 구독 구성

이 단계에서는 추가 사용자로 Office 365 구독을 구성하고 Office 365 E5 라이선스를 할당합니다.
  
[Office 365 PowerShell에 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module)의 지침을 사용하여 그래프 모듈용 Azure Active Directory PowerShell을 사용하여 Office 365 구독에 연결합니다.
  
- 사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)
    
- CLIENT1 가상 컴퓨터(시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경)
    
 Windows PowerShell 자격 증명 요청 대화 상자에서 Office 365 전역 관리자 이름(예: jdoe@contosotoycompany.onmicrosoft.com)과 암호를 입력합니다.
  
조직 이름(예 : contosotoycompany), 위치에 대한 2 자리 국가 코드, 공통 계정 암호를 입력 한 다음 PowerShell 프롬프트에서 다음 명령을 실행합니다.

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a>4단계: 3개의 새로운 SharePoint Online 팀 사이트 만들기(선택 사항)

이 단계에서는 SharePoint Online 팀 사이트의 집합을 구성합니다.
  
1. [SharePoint Online 관리 셸](https://go.microsoft.com/fwlink/p/?LinkId=255251)(x64 버전)을 설치합니다.
    
2. **시작**을 클릭하고 **sharepoint**를 입력한 후 **SharePoint Online 관리 셸**을 클릭합니다.
    
3. 조직 이름(예: contosotoycompany)을 입력하고 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행하여 SharePoint Online 서비스에 연결합니다.
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. **Microsoft SharePoint Online 관리 셸** 대화 상자에서 Office 365 전역 관리자 이름(예: jdoe@contosotoycompany.onmicrosoft.com) 및 암호를 입력하고 **로그인**을 클릭합니다.
    
5. 3개의 새로운 팀 사이트(판매, 프로덕션 및 지원)를 만들려면 Office 365 전역 관리자 이름을 입력하고 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행합니다.
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. 이러한 새 사이트의 URL을 나열하려면 다음 명령을 실행합니다.
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. Internet Explorer에서 프로덕션 사이트의 URL을 입력하여 프로덕션 부서에 대한 기본 SharePoint Online 팀 사이트를 표시합니다..
    
## <a name="record-values-for-future-reference"></a>나중에 참조하기 위해 값 기록

이 테스트 환경에서 추가 테스트 랩 가이드를 사용하거나 배포하려면 다음 값을 기록해둡니다.
  
- Office 365 전역 관리자 이름: ![](./media/Common-Images/TableLine.png).onmicrosoft.com(2단계의 9번째 작업 단계)
    
    이 계정의 암호도 안전한 위치에 적어둡니다.
    
- 평가판 구독 조 직 이름: ![](./media/Common-Images/TableLine.png)(4단계의 2번째 작업 단계)
    
- 사용자 2, 사용자 3, 사용자 4, 사용자 5에 대한 계정을 나열하려면 Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    여기에 계정 이름을 기록합니다.
    
  - 사용자 2 계정 이름: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - 사용자 3 계정 이름: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - 사용자 4 계정 이름: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - 사용자 5 계정 이름: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    해당 계정의 암호도 안전한 위치에 적어둡니다.
    
- (선택 사항) 판매, 프로덕션 및 지원 팀 사이트에 대한 URL을 나열하려면 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행합니다.
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - 프로덕션 사이트 URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production
    
  - 판매 사이트 URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales
    
  - 지원 사이트 URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support
    
## <a name="next-steps"></a>다음 단계

Office 365 개발/테스트 환경에서 다음 문서를 사용하세요.
  
- [Office 365 개발/테스트 환경에 대한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Office 365 개발/테스트 환경용 Multi-Factor Authentication](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Office 365 개발/테스트 환경용 페더레이션된 ID](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Office 365 개발/테스트 환경용 Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Office 365 개발/테스트 환경용 Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [Office 365 개발/테스트 환경용 고급 eDiscovery](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Office 365 개발/테스트 환경용 중요 파일 보호](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [개발/테스트 환경에서 격리된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
추가 Microsoft 클라우드 서비스를 포함하도록 Office 365 개발/테스트 환경을 확장합니다.
  
- [Microsoft 365 Enterprise 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>참고 항목

- [클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
- [Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)
  
- [클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


