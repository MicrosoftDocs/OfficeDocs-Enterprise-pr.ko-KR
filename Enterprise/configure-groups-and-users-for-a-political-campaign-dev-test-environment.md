---
title: 정치적 캠페인 개발/테스트 환경에 대해 그룹 및 사용자 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: '요약: 정치적 캠페인 개발/테스트 환경의 사용자 및 그룹을 사용하여 Office 365 및 EMS(Enterprise Mobility + Security) 평가판 구독을 만듭니다.'
ms.openlocfilehash: df737e3f745ba0fa4ab4752609e09e8af64ce6b0
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "19168512"
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>정치적 캠페인 개발/테스트 환경에 대해 그룹 및 사용자 구성

 **요약:** 정치적 캠페인 개발/테스트 환경의 사용자 및 그룹을 사용하여 Office 365 및 EMS(Enterprise Mobility + Security) 평가판 구독을 만듭니다.
  
이 문서의 절차에 따라 [정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) 솔루션을 위한 간소화된 사용자 계정 및 그룹을 포함하는 개발/테스트 환경을 만듭니다.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>1단계: Office 365 개발/테스트 환경 만들기

이 단계에서는 정치적 캠페인을 표방하는 가상의 조직을 위해 Office 365 E5 및 EMS(Enterprise Mobility + Security) E5에 대한 평가판 구독을 얻습니다.
  
먼저 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 **2단계**에 있는 지침을 따릅니다.
  
다음으로, EMS E5 평가판 구독을 등록하고 Office 365 평가판 구독과 동일한 조직에 추가합니다.
  
1. 필요한 경우 평가판 구독의 전역 관리자 계정 자격 증명으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.
    
2. **관리** 타일을 클릭합니다.
    
3. 브라우저의 **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.
    
4. 
            **구매 서비스** 페이지에서 **Enterprise Mobility + Security E5** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.
    
5. **주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.
    
6. **주문 접수** 페이지에서 **계속**을 클릭합니다.
    
그런 다음 전역 관리자 계정에 대해 EMS E5 라이선스를 사용하도록 설정합니다.
  
1. 브라우저의 **Office 365 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **사용자 > 활성 사용자**를 차례로 클릭합니다.
    
2. 전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.
    
3. **제품 라이선스** 창에서 **Enterprise Mobility + Security E5**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 두 번 클릭합니다.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>2단계: Azure AD(Active Directory) 그룹 만들기 및 구성

이 단계에서는 캡페인에 대한 Azure AD 그룹을 만들고 구성합니다.
  
먼저 Azure Portal을 사용하여 일반적인 정치적 캠페인에 대한 그룹 집합을 만듭니다.
  
1. 브라우저의 별도 탭에서 Azure Portal([https://portal.azure.com](https://portal.azure.com))로 이동합니다. 필요한 경우 Office 365 E5 평가판 구독에 대한 전역 관리자 계정의 자격 증명으로 로그인합니다.
    
2. Azure Portal에서 **Azure Active Directory > 사용자 및 그룹 > 모든 그룹**을 클릭합니다.
    
3. 이 목록의 각 그룹 이름에 대해 다음 단계를 수행합니다.
    
  - Senior and strategic staff
    
  - IT staff
    
  - Analytics staff
    
  - Regular core staff
    
  - Operations staff
    
  - Field staff
    
1. **모든 그룹** 블레이드에서 **+ 새 그룹**을 클릭합니다.
    
2. **이름**에 목록의 그룹 이름을 입력합니다.
    
3. **멤버 자격**에서 **동적 사용자**를 선택합니다.
    
4. **Office 기능 사용**에 **예**를 클릭합니다.
    
5. **동적 쿼리 추가**를 클릭합니다.
    
6. **사용자를 추가할 위치**에서 **부서**를 선택합니다.
    
7. 다음 필드에서 **같음**을 선택합니다.
    
8. 다음 필드에 목록의 그룹 이름을 입력합니다.
    
9. **쿼리 추가**를 클릭한 다음, **만들기**를 클릭합니다.
    
10. **사용자 및 그룹 - 모든 그룹**을 클릭합니다.
    
다음으로, 멤버에 Office 365 E5 및 EMS E5 라이선스가 자동으로 할당되도록 그룹을 구성합니다.
  
1. Azure Portal에서 **Azure Active Directory > 라이선스 > 모든 제품**을 차례로 클릭합니다.
    
2. 목록에서 **Enterprise Mobility + Security E5** 및 **Office 365 Enterprise E5**를 선택하고 **+ 할당**을 클릭합니다.
    
3. **라이선스 할당** 블레이드에서 **사용자 및 그룹**을 클릭합니다.
    
4. 그룹 목록에서 다음을 선택합니다.
    
  - Analytics staff
    
  - Field staff
    
  - IT staff
    
  - Operations staff
    
  - Regular core staff
    
  - Senior and strategic staff
    
5. **선택**을 클릭하고 **할당**을 클릭합니다.
    
6. 브라우저에서 Azure Portal 탭을 닫습니다.
    
## <a name="phase-3-add-your-user-accounts"></a>3단계: 사용자 계정 추가

이 단계에서는 정치적 캠페인에 대한 예제 사용자 계정을 추가합니다.
  
먼저 [Azure Active Directory V2 PowerShell 모듈에 연결](https://go.microsoft.com/fwlink/?linkid=842218)합니다.
  
다음으로 조직 이름, 사용자 위치 및 공통 암호를 입력합니다. PowerShell 명령 프롬프트 또는 ISE(Integrated Script Environment)에서 다음 명령을 실행합니다.
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> 여기서는 개발/테스트 환경의 자동화 및 편리한 구성을 위해 공통된 암호를 사용합니다. 프로덕션 구독에서는 이 방식이 권장되지 않습니다. 이러한 각각의 새 사용자 계정으로 로그인하면 암호를 변경하라는 메시지가 표시됩니다. 
  
다음 단계를 사용하여 동적 그룹 멤버 자격 및 그룹 기반 라이선스가 올바르게 작동하는지 확인합니다.
  
1. 브라우저의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭합니다.
    
2. 브라우저의 새 **Office 관리 센터** 탭에서 **사용자**를 클릭합니다.
    
3. 사용자 목록에서 **후보**를 클릭합니다.
    
4. **후보** 사용자 계정의 속성을 나열하는 창에서 다음을 확인합니다.
    
  - **Senior and strategic staff** 그룹의 멤버인지 여부(**그룹 멤버 자격**에서)
    
  - **Enterprise Mobility + Security E5** 및 **Office 365 Enterprise E5** 라이선스가 할당되었는지 여부(**제품 라이선스**에서)
    
5. **후보** 사용자 계정 창을 닫습니다.
    
## <a name="record-values-for-future-reference"></a>나중에 참조하기 위해 값 기록

이 개발/테스트 환경에 대해 Office 365 및 EMS 평가판 구독을 사용하려면 이러한 값을 기록해둡니다.
  
- 평가판 구독 조직 이름: ![](./images/Common_Images/TableLine.png) 
    
    예를 들어 평가판 구독 도메인 이름 contoso.onmicrosoft.com의 경우 조직 이름은 "contoso"입니다.
    
- Office 365 전역 관리자 이름: ![](./images/Common_Images/TableLine.png).onmicrosoft.com
    
    이 계정에 대한 암호와 다른 사용자 계정에 대한 일반적인 초기 암호를 안전한 위치에 기록해둡니다.
    
## <a name="next-step"></a>다음 단계

[정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기](create-team-sites-in-a-political-campaign-dev-test-environment.md)를 사용하여 이 개발/테스트 환경에서 4가지 다른 유형의 SharePoint Online 팀 사이트를 구축합니다.
  
## <a name="see-also"></a>참고 항목

[정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




