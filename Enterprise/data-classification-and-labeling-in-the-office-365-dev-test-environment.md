---
title: Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: '요약: Office 365 개발/테스트 환경에서 Azure Information Protection (AIP) 클라이언트를 사용 하 여 데이터 분류 및 레이블을 구성 하 고 보여 줍니다.'
ms.openlocfilehash: f16fd41aaa454a3f038fd23c890bbf48be2c3e66
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028902"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정

 **요약:** Office 365 개발/테스트 환경에서 Azure Information Protection (AIP) 클라이언트를 사용 하 여 데이터 분류 및 레이블을 구성 하 고 보여 줍니다.
  
Azure Information Protection 클라이언트를 사용 하 여 문서를 Office 365의 SharePoint Online 폴더에 업로드 하기 전에 분류할 수 있습니다. 이 문서의 지침을 사용 하 여 Azure Information Protection 클라이언트를 설치 하 고 데이터 분류를 보여 줍니다. 자세한 내용은 [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)을 참조 하세요.
  
> [!TIP]
> [여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>1 단계: Office 365 개발/테스트 환경 구축

[Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)지침을 따릅니다.
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>2 단계: Azure Information Protection 평가판 구독 추가

이 단계에서는 Azure Information Protection을 Office 365 개발/테스트 환경에 추가 하 고 사용자 계정에 대해 사용 하도록 설정 합니다. [Office 365 및 EMS 개발/테스트 환경을](https://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)구성한 경우에는이 단계를 건너뛰십시오. Enterprise Mobility Suite 평가판 구독에는 Azure Information Protection 라이선스가 포함 됩니다.
  
먼저 Azure Information Protection 평가판 구독에 등록 합니다.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Azure Information Protection 평가판 구독 등록

1. Internet Explorer 또는 브라우저에서 Office 365 전역 관리자 [https://admin.microsoft.com](https://admin.microsoft.com) 계정으로 이동 하 여 로그인 합니다.
    
2. **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
3. Office 365 관리 탭의 왼쪽 탐색 창에서 **결제 > 서비스 구입**을 클릭 합니다.
    
4. **서비스 구매** 페이지에서 **Azure Information Protection Premium P2** 항목을 찾습니다. 마우스를 해당 사용자에 게 가리키고 **무료 평가판 시작**을 클릭 합니다.
    
5. **주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.
    
6. **주문 접수** 페이지에서 **계속**을 클릭합니다.
    
다음으로 모든 사용자 계정에 대해 Azure Information Protection 라이선스를 사용 하도록 설정 합니다.
  
1. Microsoft 365 관리 센터 탭에서 **사용자**를 클릭 합니다.
    
2.  사용자 계정 목록에서 전역 관리자 계정을 선택 하 고 **제품 라이선스**에 대해 **편집** 을 클릭 합니다.
    
3. **Azure Information Protection Premium P2** 에 대 한 제품 라이선스를 **사용 하도록 설정 하 고** **저장을** 클릭 한 후 **닫기를** 두 번 클릭 합니다.
    
4. 다른 사용자 계정에 대해 2-3 단계를 반복 합니다 (사용자 1-사용자 5).
    
지금까지 Office 365 개발/테스트 환경에는 다음이 포함 되어 있습니다.
  
- Office 365 E5 Enterprise 및 Azure Information Protection 평가판 구독
    
- 모든 사용자 계정을 사용 하 여 Office 365 E5 Enterprise 및 Azure Information Protection을 모두 사용할 수 있습니다.
    
## <a name="phase-3-demonstrate-data-classification"></a>3 단계: 데이터 분류 시연

이 단계에서는 Azure Information Protection 클라이언트 및 기본 Azure Information Protection 정책을 사용 하 여 데이터 분류를 보여 줍니다.
  
시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 먼저 CLIENT1에 Office 2016을 설치 해야 합니다.
  
1. 브라우저를 사용 하 여 [Azure 포털로](https://portal.azure.com)이동 합니다.
    
2. **리소스 그룹 >** [리소스 그룹 이름]> 클릭 하 여 **CLIENT1 > 연결**합니다.
    
3. CLIENT1에서 Internet Explorer를 실행 하 고에서 Office 포털로 [https://admin.microsoft.com](https://admin.microsoft.com)이동한 다음 User5 계정 이름 및 암호를 사용 하 여 로그인 합니다.
    
4. **Microsoft Office 홈** 탭에서 **Office 2016 설치**를 클릭합니다.
    
5. 메시지가 표시 되 면 다운로드를 실행 하 고 사용자 계정 컨트롤에 따라 메시지가 표시 되 면 **예** 를 클릭 합니다. Office가 설치 될 때까지 기다립니다. 완료 되 면 **닫기를** 두 번 클릭 합니다.
    
다음으로 Azure Information Protection 클라이언트를 설치 합니다.
  
1. 브라우저나 Internet Explorer에서 [Microsoft Azure Information Protection 다운로드 페이지로](https://www.microsoft.com/download/details.aspx?id=53018)이동 합니다.
    
  - 간단한 버전의 Office 365 개발/테스트 환경을 사용 하는 경우 로컬 컴퓨터에서 브라우저를 사용 합니다.
    
  - 시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우에는 CLIENT1에서 Internet Explorer를 실행 합니다.
    
2. **Microsoft Azure Information Protection** 다운로드 페이지에서 **다운로드**를 클릭 하 고 **Azinfoprotection.exe**을 클릭 한 후 **다음**을 클릭 합니다.
    
3. 메시지가 표시 되 면 Azinfoprotection.exe를 실행 합니다.
    
4. **Azure Information Protection 클라이언트 설치** 상자에서 **I agree (동의**)를 클릭 한 다음 사용자 계정 컨트롤에 따라 확인 메시지가 표시 되 면 **예** 를 클릭 합니다.
    
5. **성공적으로 완료 됨** 상자에서 **닫기를 클릭 합니다.**
    
다음으로 문서 분류를 보여 줍니다.
  
1. 작업 표시줄에서 **Word** 아이콘을 클릭 합니다.
    
2. 메시지가 표시 되 면 User5 계정 이름 및 암호를 사용 하 여 로그인 합니다.
    
3. CLIENT1에 Office 2016을 설치한 경우 첫 번째 **작업** 상자에서 **수락**을 클릭 합니다.
    
4. **새 문서**를 클릭 합니다. 
    
    **홈** 탭에 있는 리본 메뉴의 **보호** 구역과 문서 분류의 행을 확인 합니다.
    
5. 새 문서에서 텍스트를 입력 합니다.
    
6. **파일 > 저장**을 클릭 하 고 **BeforeAIP**이름을 입력 한 다음 **확인**을 클릭 합니다. 
    
7. 문서 클래스의 행에서 **Secret**의 아래쪽 화살표를 클릭 하 고 **모든 회사**를 클릭 합니다.
    
8. **파일 > 다른 이름으로 저장**을 클릭 하 고 **afteraip**를 입력 한 다음 **확인**을 클릭 합니다.
    
9. 작업 표시줄에서 **파일 탐색기** 를 클릭 한 다음 **문서** 폴더를 엽니다.
    
    **BeforeAIP** 및 **afteraip** 문서의 다양 한 파일 크기를 확인 합니다. 이 문서에는 분류 정보가 있기 때문에 AfterAIP 문서가 더 커집니다.
    
다음으로, 모든 사용자가 지원 사이트 모음에 액세스할 수 있도록 합니다.
  
1. **Microsoft Office 홈** 탭에서 **SharePoint**를 클릭 합니다.
    
2. **SharePoint** 탭에서 **사이트 모음 지원을**클릭 합니다.
    
3. 오른쪽 위에 있는 **설정** 아이콘을 클릭 한 다음 **공유를**클릭 합니다.
    
4. **공유 ' 지원 사이트 모음 '** 에서 **고급**을 클릭 합니다.
    
5. SharePoint 그룹 목록에서 **사이트 모음 구성원 지원을**클릭 합니다.
    
6. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.
    
7. **공유 ' 지원 사이트 모음 '** 에 **모든 사람**을 입력 하 고 **외부 사용자를 제외한 모든 사람**을 클릭 한 다음 공유를 클릭 **합니다.**
    
8. **사용자 및 그룹** 탭을 닫습니다.
    
다음으로, User5 계정으로 로그인 하 고 AIP로 보호 된 문서를 지원 사이트 모음의 문서 폴더에 업로드 합니다.
  
1. **Microsoft Office 홈** 탭의 오른쪽 위에서 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.
    
3. **Office 365 로그인** 페이지에서 User5 계정 이름을 클릭 하 고 로그인 합니다.
    
4. **Microsoft Office 홈** 탭에서 **SharePoint > 지원 사이트 모음**을 클릭 합니다.
    
5. **문서**, **업로드**, **afteraip** 문서를 차례로 클릭 한 다음 **열기**를 클릭 합니다.
    
    지원 사이트 모음의 문서 폴더에 AfterAIP가 표시 됩니다.
    
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 및 EMS 개발/테스트 환경](https://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


