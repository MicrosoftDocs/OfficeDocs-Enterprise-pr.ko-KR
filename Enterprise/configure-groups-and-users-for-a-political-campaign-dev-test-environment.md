---
title: "정치적 캠페인 개발/테스트 환경에 대 한 사용자 및 그룹 구성"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "요약: 사용자 및 그룹 정치적 캠페인 개발/테스트 환경에 대 한 Office 365 및 Enterprise 이동성 + (EMS) 보안 평가판 구독을 만듭니다."
ms.openlocfilehash: e876c8770651c3f23c06c9c499bdaabca52da353
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>정치적 캠페인 개발/테스트 환경에 대 한 사용자 및 그룹 구성

 **요약:** 정치적 캠페인 개발/테스트 환경에 대 한 그룹 사용자와 Office 365 및 Enterprise 이동성 + (EMS) 보안 평가판 구독을 만듭니다.
  
이 문서의 지침을 사용 하 여 간소화 된 사용자 계정 및 [정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 보안 지침 Microsoft](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) 솔루션에 대 한 그룹을 포함 하는 개발/테스트 환경을 만듭니다.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>1단계: Office 365 개발/테스트 환경 만들기

이 단계에서 Office 365 e 5 및 Enterprise 이동성 + 정치적 캠페인을 나타내는 가상의 조직에 대 한 보안 (EMS) e 5에 대 한 평가판 구독 얻을 수 있습니다.
  
먼저, [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)중 **2 단계** 지침을 따릅니다.
  
다음으로, EMS E5 평가판 구독에 등록 하 고 Office 365 평가판 구독와 같은 조직에 추가 합니다.
  
1. 평가판 구독의 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 필요한 경우에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. **Admin** 타일을 클릭 합니다.
    
3. 왼쪽 탐색 영역에서 브라우저에서 **Office 관리 센터** 탭을 클릭 **대금 청구 > 구매 서비스**합니다.
    
4. **서비스 구매** 페이지 **Enterprise 이동성 + 보안 e 5** 항목을 찾습니다. 마우스 포인터를 올려 하 고 **무료 평가판을 시작**을 클릭 합니다.
    
5. **주문 확인** 페이지에서 **지금 시도**클릭 합니다.
    
6. **순서 확인** 페이지에서 **계속**을 클릭 합니다.
    
다음으로, 전역 관리자 계정에 대 한 EMS E5 라이선스를 사용 하도록 설정 합니다.
  
1. 왼쪽 탐색 영역에서 브라우저에서 **Office 365 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.
    
2. 전역 관리자 계정을 클릭 하 고 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.
    
3. **제품 라이선스** 창에서 **엔터프라이즈 이동성 + 보안 e 5** **전환**에 대 한 제품 라이선스 설정, **저장** 을 클릭 하 고 두번 **닫기** 를 클릭 합니다.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>2 단계: 그룹 만들기 및 구성 하면 Azure Active Directory (AD)

이 단계에서 만들고 캠페인에 대 한 Azure AD 그룹을 구성 합니다.
  
먼저, Azure 포털과 일반적인 정치적 캠페인에 대 한 그룹의 집합을 만듭니다.
  
1. 브라우저에서 별도 탭에 있는 [https://portal.azure.com](https://portal.azure.com)에서 Azure 포털으로 이동 합니다. 필요한 경우 Office 365 E5 평가판 구독에 대 한 전역 관리자 계정의 자격 증명을 사용 하 여 로그인 합니다.
    
2. Azure 포털에서 클릭 **Azure Active Directory > 사용자 및 그룹 > 모든 그룹**합니다.
    
3. 이 목록에 각 그룹 이름에 대해 다음 단계를 수행 합니다.
    
  - 선임 및 전략적 직원
    
  - IT 담당자
    
  - 분석 직원
    
  - 일반 핵심 직원
    
  - 작업 담당자
    
  - 필드 직원
    
1. **모든 그룹** 블레이드에서 **+ 새 그룹을**클릭 합니다.
    
2. **사용자 이름에서**목록에서 그룹 이름을 입력 합니다.
    
3. **멤버 자격**에서 **동적 사용자** 를 선택 합니다.
    
4. **Office를 사용 하도록 설정 기능**에 대 한 **예** 를 클릭 합니다.
    
5. **추가 동적 쿼리**를 클릭 합니다.
    
6. **사용자를 추가할 위치**, **부서**를 선택 합니다.
    
7. 다음 필드에 **는**선택 합니다.
    
8. 다음 필드 목록에서 그룹 이름을 입력 합니다.
    
9. **추가 쿼리**클릭 한 다음 **만들기**를 클릭 합니다.
    
10. **사용자 및 그룹-모든 그룹을**클릭 합니다.
    
다음으로, 구성원은 Office 365 e 5 및 EMS E5 라이선스를 자동으로 할당 되도록 그룹을 구성 합니다.
  
1. Azure 포털에서 클릭 **Azure Active Directory > 라이선스 > 모든 제품**합니다.
    
2. 목록에서 **엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise e 5**를 선택한 다음 **할당 +**를 클릭 합니다.
    
3. **라이선스를 할당** 블레이드에서 **사용자 및 그룹을**클릭 합니다.
    
4. 그룹 목록에서 다음을 선택 합니다.
    
  - 분석 직원
    
  - 필드 직원
    
  - IT 담당자
    
  - 작업 담당자
    
  - 일반 핵심 직원
    
  - 선임 및 전략적 직원
    
5. **선택**을 클릭 하 고 **할당**을 클릭 합니다.
    
6. 브라우저에서 Azure 포털 탭을 닫습니다.
    
## <a name="phase-3-add-your-user-accounts"></a>3 단계: 사용자 계정 추가

이 단계에서 정치적 캠페인에 대 한 예제 사용자 계정을 추가 합니다.
  
첫째, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)있습니다.
  
다음으로, 조직 이름, 사용자 위치 및 공통 암호를 입력 한 다음 PowerShell 명령 프롬프트 또는 스크립트 ISE (통합 환경)에서 다음이 명령을 실행 합니다.
  
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
> 여기에 일반적인 암호 사용 자동화 및 개발/테스트 환경에 대 한 구성이 쉽기 때문입니다. 프로덕션 구독에 대 한 권장 되지 않습니다. 각 이러한 새 사용자 계정을 사용 하 여 서명 하 암호를 변경 하 라는 메시지가 표시 됩니다. 
  
동적 그룹 멤버 자격 및 라이선스 그룹 기반 올바르게 작동 하는지 확인 하려면 다음이 단계를 사용 합니다.
  
1. 브라우저의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
2. 브라우저의 새 **Office 관리 센터** 탭에서 **사용자**를 클릭 합니다.
    
3. 사용자의 목록에서 **후보**를 클릭 합니다.
    
4. **후보** 사용자 계정의 속성을 나열 하는 창에서 다음을 확인.
    
  - 해당 **그룹 구성원 자격**) (의 **수석 및 전략적 직원** 그룹의 구성원입니다.
    
  - **엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise E5** 라이선스 ( **제품 라이선스**)에 할당 된 것입니다.
    
5. **후보** 사용자 계정 창을 닫습니다.
    
## <a name="record-values-for-future-reference"></a>나중에 참조할 수에 대 한 레코드 값

Office 365 및 EMS 평가판 구독이 개발/테스트 환경에 대 한 작업에 대 한 이러한 값을 기록 합니다.
  
- 평가판 구독 조직 이름: ___ 
    
    예, contoso.onmicrosoft.com 형식의 평가판 구독 도메인 이름에 대 한 조직 이름은 "contoso"입니다.
    
- Office 365 전역 관리자 이름: ___.onmicrosoft.com
    
    안전한 위치에이 계정에 대 한 암호 및 다른 사용자 계정에 대 한 일반적인 초기 암호를 기록 합니다.
    
## <a name="next-step"></a>다음 단계

[정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기와](create-team-sites-in-a-political-campaign-dev-test-environment.md)이 개발/테스트 환경에서 SharePoint Online 팀 사이트의 서로 다른 네가지 형식의 작성 합니다.
  
## <a name="see-also"></a>참고 항목

[정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




