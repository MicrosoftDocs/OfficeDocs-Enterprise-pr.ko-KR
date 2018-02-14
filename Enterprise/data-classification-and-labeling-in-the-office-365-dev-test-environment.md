---
title: "데이터 분류 및 Office 365 개발/테스트 환경에서 레이블 지정"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "요약: 구성 및 시연 데이터 분류 하 고 Azure 정보 보호 (AIP) 클라이언트를 사용 하 여 Office 365 개발/테스트 환경에서 레이블을 지정 합니다."
ms.openlocfilehash: 7243acecca0dd4c39ff6ef2aecd25091f25f2f53
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>데이터 분류 및 Office 365 개발/테스트 환경에서 레이블 지정

 **요약:** 구성 및 시연 데이터 분류 하 고 Azure 정보 보호 (AIP) 클라이언트를 사용 하 여 Office 365 개발/테스트 환경에서 레이블을 지정 합니다.
  
Azure 정보 보호 클라이언트를 사용 하면 Office 365의 SharePoint Online 폴더에 업로드 하기 전에 문서를 분류할 수 있습니다. 이 문서의 지침을 함께 Azure 정보 보호 클라이언트를 설치 및 데이터 분류를 시연 합니다. 자세한 내용은 [Azure 정보 보호](https://www.microsoft.com/cloud-platform/azure-information-protection)를 참조 하십시오.
  
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>1 단계: Office 365 개발/테스트 환경을 구축합니다

[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)에 대 한 지침을 따릅니다.
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>2 단계: Azure 정보 보호 평가판 구독 추가

이 단계에서 Office 365 개발/테스트 환경에 Azure 정보 보호를 추가 하 고 사용자 계정에 대해 사용 하도록 설정 합니다. [Office 365와 EMS 개발/테스트 환경을](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)구성한 경우이 단계를 건너뜁니다. Enterprise 이동성 제품군 평가판 구독 Azure 정보 보호 라이선스를 포함합니다.
  
먼저, Azure 정보 보호 평가판 구독에 등록 합니다.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Azure 정보 보호 평가판 구독에 등록

1. Internet Explorer 또는 브라우저에서 [http://portal.office.com](http://portal.office.com) 로 이동 하 고 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.
    
2. **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
3. Office 365 관리자 탭의 왼쪽된 탐색 영역에서 클릭 **대금 청구 > 구매 서비스**합니다.
    
4. **서비스 구매** 페이지 **Azure 정보 보호 프리미엄 P2** 항목을 찾습니다. 마우스 포인터로 하 고 **무료 평가판을 시작**을 클릭 합니다.
    
5. **주문 확인** 페이지에서 **지금 시도**클릭 합니다.
    
6. **순서 확인** 페이지에서 **계속**을 클릭 합니다.
    
다음으로 모든 사용자 계정에 대 한 정보 보호 Azure 라이선스 사용 하도록 설정 합니다.
  
1. Office 365 관리 센터 탭에서 **사용자**를 클릭 합니다.
    
2.  사용자 계정 목록에서 전역 관리자 계정에 선택한 다음 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.
    
3. **Azure 정보 보호 프리미엄 P2** **전환**에 대 한 제품 라이선스를 설정 하 고 **저장** 을 클릭 한 다음 **닫기** 를 두 번 클릭 합니다.
    
4. 다른 사용자 계정 (사용자 1-사용자 5)에 대 한 2와 3 단계를 반복 합니다.
    
Office 365 개발/테스트 환경을 현재가지고 있습니다.
  
- Office 365 e 5 Enterprise 및 Azure 정보 보호 평가판 구독 합니다.
    
- 사용자 계정을 모두 Office 365 e 5 엔터프라이즈와 Azure 정보 보호를 사용 하 여 사용할 수 있습니다.
    
## <a name="phase-3-demonstrate-data-classification"></a>3 단계: 데이터 분류를 시연

이 단계에서 Azure 정보 보호 클라이언트와 기본 Azure 정보 보호 정책 구성 요소를 사용 하 여 데이터 분류를 보여줍니다.
  
시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우에 CLIENT1에서 먼저 Office 2016를 설치 해야 합니다.
  
1. 브라우저를 사용 하 고 [Azure 포털](http://portal.azure.com)로 이동 합니다.
    
2. 클릭 **리소스 그룹 >** [자원 그룹 이름] **> CLIENT1 > 연결**합니다.
    
3. CLIENT1에서 Internet Explorer를 실행, [http://portal.office.com](http://portal.office.com)Office 포털을 이동 하 고 User5 계정 이름과 암호를 사용 하 여 로그인 합니다.
    
4. **Microsoft Office 홈** 탭에서 **Office 2016 설치**를 클릭 합니다.
    
5. 메시지가 표시 되 고 클릭 하 여 **Yes** 사용자 계정 컨트롤 대화 상자가 나타나면 다운로드를 실행 합니다. Office를 설치 될 때까지 기다립니다. 완료 되 면 두번 **닫기를** 클릭 합니다.
    
다음으로 Azure 정보 보호 클라이언트를 설치 합니다.
  
1. 사용자가 브라우저 또는 Internet Explorer에서 [Microsoft Azure 정보 보호 다운로드 페이지](https://www.microsoft.com/download/details.aspx?id=53018)로 이동 합니다.
    
  - Office 365 개발/테스트 환경의 경량 버전을 사용 하는 경우 로컬 컴퓨터에서 브라우저를 사용 합니다.
    
  - 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 CLIENT1에서 Internet Explorer를 실행 합니다.
    
2. **Microsoft Azure 정보 보호** 다운로드 페이지에서 **다운로드**를 클릭 하 고 **AzInfoProtection.exe**차례로 **다음**을 클릭 합니다.
    
3. 대화 상자가 나타나면 AzInfoProtection.exe를 실행 합니다.
    
4. **Azure 정보 보호 설치** 클라이언트 상자에서 **동의 함**를클릭하고 **예** 사용자 계정 컨트롤 대화 상자가 나타나면 클릭 합니다.
    
5. **성공적으로 완료** 상자에서 클릭 **닫기.**
    
다음으로, 문서 분류를 보여줄 있습니다.
  
1. 작업 표시줄에서 **Word** 아이콘을 클릭 합니다.
    
2. 대화 상자가 나타나면 User5 계정 이름과 암호를 사용 하 여 로그인 합니다.
    
3. CLIENT1에서 Office 2016에서 방금 설치한는 **가장 먼저 수행할 작업 첫번째** 상자, **수락**을 클릭 합니다.
    
4. **새 문서**를 클릭 합니다. 
    
    **홈** 탭과 문서 분류의 행에서 리본 메뉴의 **보호** 섹션을 note 합니다.
    
5. 빈 문서에서 텍스트를 입력 합니다.
    
6. 클릭 **파일 > 저장** **BeforeAIP**이름을 입력 한 다음 **확인**을 클릭 합니다. 
    
7. 문서 클래스의 행을 **비밀**대 한 아래쪽 화살표를 클릭 하 고 **모든 회사**를 클릭 한 다음 합니다.
    
8. 클릭 **파일 > 다른이름으로** **AfterAIP**이름을 입력 한 다음 **확인**을 클릭 합니다.
    
9. 작업 표시줄에서 **파일 탐색기** 를 클릭 한 다음 **문서** 폴더를 엽니다.
    
    Note **BeforeAIP** 및 **AfterAIP** 문서의 다른 파일 크기입니다. AfterAIP 문서는 분류 정보를 제공 하기 때문에 큽니다.
    
다음으로 모든 사용자가 지원 사이트 모음에 액세스 허용 합니다.
  
1. **Microsoft Office 홈** 탭에서 **SharePoint**를 클릭 합니다.
    
2. **SharePoint** 탭에서 **지원 사이트 모음**을 클릭 합니다.
    
3. 오른쪽 위에 있는 **설정** 아이콘을 클릭 하 고 **공유 대상을**클릭 합니다.
    
4. **공유 '지원 사이트 모음'** **고급**을 클릭 합니다.
    
5. SharePoint 그룹의 목록에서 **지원 사이트 모음 구성원을**클릭 합니다.
    
6. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
7. **'지원 사이트 모음' 공유** **모든 사용자**를 입력 하 고 **외부 사용자를 제외한 모든 사용자**를 클릭 한 다음이 클릭 한 다음 **공유.**
    
8. **사용자 및 그룹** 탭을 닫습니다.
    
다음으로 User5 계정을 사용 하 여 로그인 하 고 지원 사이트 모음의 문서 폴더를 AIP 암호로 보호 된 문서를 업로드 합니다.
  
1. 오른쪽 위에 있는 **Microsoft Office 홈** 탭에서 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [Http://portal.office.com](http://portal.office.com)로 이동 합니다.
    
3. 에 * * Office 365 로그인 * * 페이지 User5 계정 이름을 클릭 하 고 로그인 합니다.
    
4. **Microsoft Office 홈** 탭에서 클릭 **SharePoint > 사이트 모음을 지원**합니다.
    
5. **문서**, **업로드**를 클릭 하 고 **AfterAIP** 문서를 클릭 한 다음 **열기**를 클릭 합니다.
    
    지원 사이트 모음의 문서 폴더에 AfterAIP.docx이 표시 됩니다.
    
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 및 EMS 개발/테스트 환경](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure 정보 보호](https://www.microsoft.com/cloud-platform/azure-information-protection)


