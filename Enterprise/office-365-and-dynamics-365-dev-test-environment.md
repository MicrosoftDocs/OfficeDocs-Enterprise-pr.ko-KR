---
title: Office 365 및 Dynamics 365 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: '요약: 이 테스트 랩 가이드를 사용하여 Office 365 개발/테스트 환경에 Dynamics 365를 추가합니다.'
ms.openlocfilehash: 195e5ab4fd96d1f238c96d47cc7406a45e0e02b1
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915213"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 및 Dynamics 365 개발/테스트 환경

 **요약:** 이 테스트 랩 가이드를 사용하여 Office 365 개발/테스트 환경에 Dynamics 365를 추가합니다.
  
이 문서의 지침을 사용하여 Dynamics 365 평가판 구독을 Office 365 개발/테스트 환경과 동일한 조직에 추가하여 Office 365 및 Dynamics 365 개발/테스트 환경을 만듭니다.

![Office 365 및 Dynamics 365 개발/테스트 환경](media/o365-dynamics365-dev-test.png)
  
  
Dynamics 365 평가판 구독을 사용하여 Dynamics 365의 기능을 시연할 수 있습니다. 다음과 같은 해결 방법이 Dynamics 365 계획 1, Enterprise Edition 평가판에 함께 제공됩니다.
  
- [Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). 자동화 및 디지털 인텔리전스를 통해 영업 사원이 집중력을 유지하고 더욱 똑똑하게 업무를 수행할 수 있도록 도와 판매량을 늘립니다.
    
- [Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). 에이전트가 원활한 서비스를 제공하는 데 필요한 완벽한 정보와 디지털 인텔리전스를 제공하여 충성도를 얻습니다.
    
- [Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). 일정을 최적화하고 직원을 배치하며 예측 도구를 사용하여 이익을 늘려서 서비스 호출을 마스터합니다.
    
- [Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/ko-KR/dynamics365/project-service-automation). 프로젝트를 성공적으로 완료하고 생산적인 직원rhk 지능형 도구를 통해 수익성 있는 관계를 만듭니다.
    
Dynamics 365 평가판 구독에 대해 위 내용 중 하나 이상을 탐색할 수 있습니다.
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항과 경량 방식으로 Office 365 및 Dynamics 365를 테스트하려면 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 2, 3단계의 지침을 따릅니다.
  
시뮬레이트된 엔터프라이즈에서 Office 365 및 Dynamics 365를 테스트하려면 [Office 365 개발/테스트 환경에 대한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md) 지침을 따릅니다.

![Office 365 개발/테스트 환경](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> 이 문서의 구성에는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server AD 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 일반적인 조직을 나타내는 환경에서 Office 365 및 Dynamics 365를 실험할 수 있습니다. 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>2단계: Dynamics 365 평가판 구독 추가

이 단계에서는 Dynamics 365 평가판 구독을 등록하고 Office 365 평가판 구독과 동일한 조직에 추가합니다.
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Dynamics 365 평가판 구독 등록

1. 데스크톱 컴퓨터(경량) 또는 CLIENT1(시뮬레이트된 엔터프라이즈)의 브라우저에서 전역 관리자 계정의 자격 증명을 사용하여 [https://portal.office.com](https://portal.office.com)의 Office 365 포털에 로그인합니다.
    
2. **관리** 타일을 클릭합니다.
    
3. **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.
    
4. **구매 서비스** 페이지에서 **Dynamics 365 Plan 1 Enterprise Edition** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.
    
5. **주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.
    
6. **주문 접수** 페이지에서 **계속**을 클릭합니다.

![Office 365 및 Dynamics 365 개발/테스트 환경](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> Dynamics 365 Plan 1 Enterprise Edition 평가 기간은 30일입니다. 추가로 30일 동안 내역 구독을 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다. 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>3단계: Dynamics 365 라이선스 및 시스템 관리자 할당

이 단계에서는 전역 관리자, 사용자 2 및 사용자 3 계정에 Dynamics 365 라이선스를 할당하고 시스템 관리자로 지정합니다.
  
다음 단계를 사용하여 Dynamics 365 라이선스를 할당합니다.
  
1. **Office 관리 센터** 탭에서 **사용자 > 활성 사용자**를 클릭합니다.
    
2. 활성 사용자 목록에서 전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.
    
3. **제품 라이선스** 창에서 **Dynamics 365 Plan 1 Enterprise Edition**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 차례로 두 번 클릭합니다.
    
4. 사용자 2 및 사용자 3 계정에 대해 2, 3단계를 수행합니다.
    
5. **Office 관리 센터** 탭을 닫습니다.
    
다음 단계를 사용하여 사용자 2 및 사용자 3 계정을 Dynamics 365 시스템 관리자로 구성합니다.
  
1. **Microsoft Office 홈** 탭에서 **관리**를 클릭합니다.
    
2. **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **관리 센터**를 클릭하고 **Dynamics 365**를 클릭합니다.
    
    메뉴에 Dynamics 365가 표시되기 전에 Dynamics 365에서 프로비전이 완료될 때까지 기다려야 할 수 있습니다.
    
3. Dynamics 365 탭에서 **이러한 항목 모두**를 클릭한 후 **설치 완료**를 클릭합니다.
    
    설치가 완료될 때까지 기다립니다.
    
    설치가 완료되면 내역 구독에 포함된 샘플 데이터를 기준으로 하는 판매 활동 대시보드가 표시됩니다. 몇 분 정도 할애하여 **평가판 시작** 비디오를 시청하세요. 완료되면 비디오 창을 닫습니다.
    
4. 맨 위에 있는 도구 모음에서 **판매** 옆에 있는 아래쪽 화살표를 클릭하고 **설정**을 클릭한 후 **보안**을 클릭합니다.
    
5. **보안** 페이지에서 **사용자**를 클릭합니다.
    
6. 사용자 목록에서 **사용자 2**를 클릭합니다.
    
7. 도구 모음에서 **역할 관리**를 클릭합니다.
    
8. **역할 관리**에서 **시스템 관리자**를 클릭하고 **확인**을 클릭합니다.
    
9. 맨 위의 도구 모음에서 **보안**을 클릭합니다.
    
10. 사용자 3 계정에 대해 5-8단계를 반복합니다.
    
11. **사용자: 사용자3** 탭을 닫습니다.
    
> [!NOTE]
> Office 365 전역 관리자 계정에 Dynamics 365 시스템 관리자 역할이 자동으로 할당되었습니다. 
  
Office 365 및 Dynamics 365 개발/테스트 환경에는 다음이 포함됩니다.
  
- 사용자 계정 목록과 동일한 조직 및 동일한 Microsoft Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 Dynamics 365 평가판 구독
    
- 전역 엔터프라이즈 관리자, 사용자 2 및 사용자 3 계정이 Office 365 E5 Enterprise 및 Dynamics 365를 함께 사용하도록 설정되며, Dynamics 365 시스템 관리자가 됩니다.
    
## <a name="next-step"></a>다음 단계

[Office 365 및 Dynamics 365 개발/테스트 환경을 위한 Exchange Online 통합](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)을 사용하여 Exchange Online 사서함에서 Office 365 및 Dynamics 365가 함께 작동하는 방법을 구성한 다음 보여줍니다.
  
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365용 구독 관리(온라인)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Dynamics 365 관리](https://technet.microsoft.com/library/dn531101.aspx)


