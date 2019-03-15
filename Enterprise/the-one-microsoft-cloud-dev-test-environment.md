---
title: One Microsoft Cloud 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: '요약: 이 테스트 랩 가이드를 사용하여 모든 Microsoft의 클라우드 서비스가 포함된 개발/테스트 환경을 만듭니다.'
ms.openlocfilehash: 0ccea58e86f2e105704aac01ba4379c21a174e3a
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "30573662"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>One Microsoft Cloud 개발/테스트 환경

 **요약:** 이 테스트 랩 가이드를 사용하여 모든 Microsoft의 클라우드 서비스가 포함된 개발/테스트 환경을 만듭니다.
  
이 문서의 지침에 따라 Microsoft Azure 인프라 서비스에서 시뮬레이트된 인트라넷을 만든 후 Microsoft Office 365, Microsoft Enterprise Mobility + Security 및 Microsoft Dynamics 365 구독을 추가합니다. 그 결과 단일 개발/테스트 환경에서 모든 Microsoft 클라우드 서비스를 동시에 사용하는 간소화된 조직이 구현됩니다. 
  
![Azure, Office 365, EMS 및 Dynamics 365를 사용하는 One Microsoft 클라우드 개발/테스트 환경 3단계](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
구성 결과를 사용하여 다음을 수행할 수 있습니다.
  
- Azure AD(Azure Active Directory)에서 제공하는 공통 ID 인프라와 같은 통합을 Microsoft 클라우드 서비스에서 경험할 수 있습니다.
    
- 여러 Microsoft 클라우드 서비스를 포함하는 종단 간 시나리오를 평가합니다.
    
- 여러 Microsoft 클라우드 서비스를 사용하는 데모, 개념 증명 또는 개발/테스트 구성을 만듭니다.
    
- 전문성 개발을 위한 Microsoft 클라우드 기술을 구축합니다.
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>1단계: 시뮬레이트된 인트라넷 만들기 및 Office 365 추가

[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따릅니다.
  
그림 1은 Office 365와 온-프레미스 Windows Server AD(Active Directory) 포리스트의 Azure 인프라 서비스 및 디렉터리 동기화에서 실행되는 시뮬레이트된 인트라넷을 포함하는 구성 결과를 보여줍니다.
  
**그림 1: Office 365를 사용한 Azure의 시뮬레이트된 인트라넷**

![DirSync를 사용하는 Office 365 개발/테스트 환경](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> Azure 평가 기간은 30일입니다. Office 365 Enterprise E5 평가 구독 기간은 30일로, 추가로 30일 동안 연장될 수 있습니다. 영구 개발/테스트 환경의 경우 적은 수의 라이선스를 사용하여 새 유료 Azure 구독과 새 유료 Office 365 Enterprise E5 구독을 만듭니다. 
  
## <a name="phase-2-add-ems"></a>2단계: EMS 추가

이 단계에서는 EMS 평가판 구독을 등록하고 Office 365 평가판 구독과 동일한 조직에 추가합니다.
  
1. 데스크톱 컴퓨터 또는 CLIENT1의 브라우저에서 전역 관리자 계정의 자격 증명을 사용하여 [https://www.office.comhttps://portal.office.com](https://www.office.com)의 Office 365 포털에 로그인합니다.
    
2. **관리** 타일을 클릭합니다.
    
3. 브라우저의 **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.
    
4. 
            **구매 서비스** 페이지에서 **Enterprise Mobility + Security E5** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.
    
5. **주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.
    
6. **주문 접수** 페이지에서 **계속**을 클릭합니다.
    
> [!NOTE]
> Enterprise Mobility + Security E5 평가판 구독 기간은 90일입니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다. 
  
그런 다음, 모든 사용자 계정에 대해 Enterprise Mobility + Security E5 라이선스를 사용하도록 설정합니다.
  
1. 브라우저의 **Office 365 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **사용자 > 활성 사용자**를 차례로 클릭합니다.
    
2. 전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.
    
3. **제품 라이선스** 창에서 **Enterprise Mobility + Security E5**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 두 번 클릭합니다.
    
4. 다른 모든 계정(사용자 1, 사용자 2, 사용자 3, 사용자 4 및 사용자 5)에 대해 2-3단계를 수행합니다.
    
이제 개발/테스트 환경에는 다음이 구현됩니다.
  
- Azure 인프라 서비스에서 실행되는 시뮬레이트된 인트라넷
    
- 사용자 계정 목록과 동일한 조직 및 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 EMS 평가판 구독
    
- 모든 사용자 계정이 Office 365 E5 Enterprise 및 EMS를 사용하도록 설정
    
그림 2는 EMS를 추가하는 구성 결과를 보여줍니다.
  
**그림 2: Office 365 및 EMS를 사용한 Azure의 시뮬레이트된 인트라넷**

![Azure, Office 365 및 EMS를 사용하는 One Microsoft 클라우드 개발/테스트 환경 2단계](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>3단계: Dynamics 365 추가

이 단계에서는 Dynamics 365  평가판 구독을 등록하고 Office 365 및 EMS 평가판 구독과 동일한 조직에 추가합니다.
  
1. 데스크톱 컴퓨터 또는 CLIENT1의 브라우저에서 전역 관리자 계정의 자격 증명을 사용하여 [https://www.office.comhttps://portal.office.com](https://www.office.com)의 Office 365 포털에 로그인합니다.
    
2. **관리** 타일을 클릭합니다.
    
3. **Microsoft 365 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.
    
4. **구매 서비스** 페이지에서 **Dynamics 365 Plan 1 Enterprise Edition** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.
    
5. **주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.
    
6. **주문 접수** 페이지에서 **계속**을 클릭합니다.
    
> [!NOTE]
> Dynamics 365 Plan 1 Enterprise Edition 평가 기간은 30일입니다. 추가로 30일 동안 내역 구독을 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다. 
  
다음 단계에 따라 전역 관리자, 사용자 2 및 사용자 3 계정에 Dynamics 365 라이선스를 할당하고 시스템 관리자로 지정합니다.
  
1. **Microsoft 365 관리 센터** 탭에서 **사용자 > 활성 사용자**를 클릭합니다.
    
2. 활성 사용자 목록에서 전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.
    
3. **제품 라이선스** 창에서 **Dynamics 365 Plan 1 Enterprise Edition**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 차례로 두 번 클릭합니다.
    
4. 사용자 2 및 사용자 3 계정에 대해 2, 3단계를 수행합니다.
    
5. **Microsoft 365 관리 센터** 탭을 닫습니다.
    
다음 단계를 사용하여 사용자 2 및 사용자 3 계정을 Dynamics 365 시스템 관리자로 구성합니다.
  
1. 브라우저의 **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **관리 센터**를 클릭하고 **Dynamics 365**를 클릭합니다.
    
    메뉴에 Dynamics 365가 표시되기 전에 Dynamics 365에서 프로비전이 완료될 때까지 기다려야 할 수 있습니다.
    
2. Dynamics 365 탭에서 **이러한 항목 모두**를 클릭한 후 **설치 완료**를 클릭합니다.
    
    설치가 완료될 때까지 기다립니다.
    
    설치가 완료되면 평가판 구독에 포함된 샘플 데이터를 기반으로 하는 판매 활동 대시보드가 표시됩니다. 잠시만 시간을 내어 **평가판 시작** 비디오를 시청하세요. 완료되면 비디오 창을 닫습니다.
    
3. 맨 위에 있는 도구 모음에서 **판매** 옆에 있는 아래쪽 화살표를 클릭하고 **설정**을 클릭한 후 **보안**을 클릭합니다.
    
4. **보안** 페이지에서 **사용자**를 클릭합니다.
    
5. 사용자 목록에서 **사용자 2**를 클릭합니다.
    
6. 도구 모음에서 **역할 관리**를 클릭합니다.
    
7. **역할 관리**에서 **시스템 관리자**를 클릭하고 **확인**을 클릭합니다.
    
8. 맨 위의 도구 모음에서 **보안**을 클릭합니다.
    
9. 사용자 3 계정에 대해 5-8단계를 반복합니다.
    
10. **사용자: 사용자3** 탭을 닫습니다.
    
> [!NOTE]
> Office 365 전역 관리자 계정에 Dynamics 365 시스템 관리자 역할이 자동으로 할당되었습니다. 
  
이제 개발/테스트 환경에는 다음이 구현됩니다.
  
- Azure 인프라 서비스에서 실행되는 시뮬레이트된 인트라넷
    
- 사용자 계정 목록과 동일한 조직 및 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise, EMS 및 Dynamics 365 평가판 구독
    
- 모든 사용자 계정이 Office 365 E5 Enterprise 및 EMS를 사용하도록 설정
    
- 전역 엔터프라이즈 관리자, 사용자 2 및 사용자 3 계정이 Dynamics 365를 사용하도록 설정되며, Dynamics 365 시스템 관리자가 됩니다.
    
그림 3은 구성 결과를 보여줍니다.
  
**그림 3: Office 365, EMS 및 Dynamics 365를 사용한 Azure의 시뮬레이트된 인트라넷**

![Azure, Office 365, EMS 및 Dynamics 365를 사용하는 One Microsoft 클라우드 개발/테스트 환경 3단계](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>다음 단계

이제 One Microsoft 클라우드 개발/테스트 환경을 체험해볼 수 있습니다. 지원되는 몇 가지 환경은 다음과 같습니다.
  
- [Office 365용 EMS 응용 프로그램에서 MAM(모바일 응용 프로그램 관리) 정책 구성](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Office 365의 Exchange Online과 Dynamics 365 연락처와의 통합 예시](https://technet.microsoft.com/library/mt798313.aspx)
    
- [서버 기반 워크로드를 호스트하기 위해 Azure 인프라 서비스에서 시뮬레이트된 크로스-프레미스 네트워크 만들기](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)
  
[하이브리드 솔루션](hybrid-solutions.md)
  
[보안 솔루션](security-solutions.md)





