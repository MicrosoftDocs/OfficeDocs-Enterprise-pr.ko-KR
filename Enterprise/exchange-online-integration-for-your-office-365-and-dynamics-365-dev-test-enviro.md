---
title: "Office 365 및 Dynamics 365 개발/테스트 환경을 위한 Exchange Online 통합"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "요약: 이 테스트 랩 가이드를 사용하여 Office 365 평가판 구독에서 Exchange Online용 Dynamic 365 통합을 사용하도록 설정할 수 있습니다."
ms.openlocfilehash: 4acfc4c676482131160ca82b5e8e405cca938cac
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Office 365 및 Dynamics 365 개발/테스트 환경을 위한 Exchange Online 통합

 **요약:** 이 테스트 랩 가이드를 사용하여 Office 365 평가판 구독에서 Exchange Online용 Dynamic 365 통합을 사용하도록 설정할 수 있습니다.
  
Microsoft Dynamics 365를 가장 잘 활용하는 방법은 모든 고객 통신을 한 곳에 저장하여 적합한 사용 권한을 가진 사용자라면 누구나 관련된 고객 레코드를 모두 볼 수 있도록 하는 것입니다. 예를 들어, 특정 연락처, 계정, 기회 및 케이스와 관련된 모든 전자 메일을 볼 수 있습니다.
  
Dynamics 365의 전자 메일 및 기타 메시징 레코드를 저장하려면 전자 메일 시스템을 Dynamics 365와 동기화해야 합니다. 서버 쪽 동기화는 전자 메일 동기화를 위한 가장 좋은 방법입니다.
  
이 테스트 랩 가이드를 사용하여 Exchange Online 및 Outlook Online 클라이언트가 Dynamics 365에 저장된 정보를 활용하는 방법을 구성하고 설명할 수 있습니다. 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>1단계: Office 365 및 Dynamics 365 개발/테스트 환경 구축

[Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)의 지침을 사용하여 Office 365 및 Dynamics 365 개발/테스트 환경의 경량 또는 시뮬레이트된 엔터프라이즈 버전 중 하나를 만들 수 있습니다.
  
> [!NOTE]
> 이 문서의 구성에는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server Active Directory(AD) 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 일반적인 조직을 나타내는 환경에서 Office 365 및 Dynamics 365를 실험할 수 있습니다. 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>2단계: Exchange Online에서 Dynamics 365 통합 구성 및 설명

다음 단계를 통해 Dynamics 365 및 Exchange Online 통합용 전역 관리자 사서함을 구성할 수 있습니다.
  
1. 브라우저의 개인 세션을 통해 [http://portal.office.com](http://portal.office.com)으로 이동한 다음 Office 365 전역 관리자 계정으로 로그인할 수 있습니다.
    
2. **Microsoft Office Home** 페이지에서 **메일** 타일을 클릭합니다.
    
3. 브라우저의 새 **메일** 탭에서 **새로 만들기**를 클릭하고 메시지 입력 상자 아래의 창 하단 구석에 내 템플릿 아이콘이 어떻게 표시되는지 확인하세요.
    
     ![Dynamics 365와 통합되지 않은 비어 있는 새 전자 메일 메시지입니다.](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. **취소**를 클릭하고 **메일** 탭을 열어 둡니다.
    
5. 브라우저에서 **Microsoft Office 탭**을 클릭한 다음 **관리** 타일을 클릭합니다.
    
6. **Office 관리 센터** 탭의 왼쪽 탐색 창에서 **관리 센터 > Dynamics 365**를 클릭합니다.
    
7. 브라우저의 새 **Dynamics 365** 탭에 있는 Dynamics 365 인스턴스 목록에서 **열기**를 클릭합니다.
    
8. 브라우저의 새 **관리** 탭에 있는 탐색 모음에서 **설정** 옆의 아래쪽 화살표를 클릭한 다음 **시스템**에서 **전자 메일 구성**을 클릭합니다.
    
9.  **전자 메일 구성** 페이지에서 **전자 메일 구성 설정**을 클릭합니다.
    
10. **시스템 설정** 대화 상자의 **전자 메일** 탭에서 **약속, 연락처 및 작업**을 **서버 쪽 동기화**로 변경한 다음 **확인**을 클릭합니다.
    
11. **전자 메일 구성** 페이지에서 **사서함**을 클릭합니다.
    
12. 왼쪽 확인 표시 열에서 Office 365 전역 관리자 이름을 선택하고 도구 모음에서 **기본 전자 메일 설정 적용**을 클릭한 다음 **확인**을 클릭합니다.
    
13. 도구 모음에서 **전자 메일 적용**을 클릭한 다음 **확인**을 클릭합니다.
    
14. 왼쪽 확인 표시 열에서 Office 365 전역 관리자 이름을 선택하고 도구 모음에서 **사서함 테스트 &amp; 사용**을 클릭한 다음 **확인**을 클릭합니다.
    
15. **메일** 탭을 클릭하고 전역 관리자가 테스트 메시지를 수신했는지 확인합니다.
    
16. 브라우저의 **사서함 내 활성 사서함** 탭으로 돌아가서 페이지를 새로 고칩니다. **수신 전자 메일 상태** 및 **발신 전자 메일 상태** 열은 전역 관리자 계정 이름에 대해 **성공**으로 설정되어 있어야 합니다. 테스트를 모두 완료하는 데 최대 15분이 소요될 수도 있습니다.
    
다음 단계를 통해 Outlook용 Dynamics 365 앱을 설치하고 전역 관리자 사서함 내에 Dynamics 365 기능을 설명할 수 있습니다.
  
1. 브라우저의 **사서함 내 활성 사서함** 탭에서 **설정** 옆의 아래쪽 화살표를 클릭한 다음 **시스템**에서 **Outlook용 Dynamics 365 앱**을 클릭합니다.
    
2. **Outlook용 Microsoft Dynamics 365 앱 시작하기** 페이지에서 전역 관리자 이름을 클릭한 다음 **앱을 Outlook에 추가**를 클릭합니다. **상태** 열이 **보류 중**으로 변경됩니다.
    
3. 상태가 **Outlook에 추가됨**으로 변경되기 전까지 페이지를 새로 고칩니다. 이 구성을 완료하는 데 최대 15분이 소요될 수 있습니다.
    
4. 브라우저에서 **메일** 탭을 클릭한 다음 브라우저를 닫습니다.
    
5. 브라우저에서 **Microsoft Office Home** 탭을 클릭한 다음 **메일** 타일을 클릭합니다.
    
6. 브라우저의 새 **메일** 탭에서 **새로 만들기**를 클릭합니다. 이제 메시지 입력 상자 아래의 창 하단 구석에 Dynamics 365 아이콘이 어떻게 표시되는지 확인하세요.
    
     ![Dynamics 365와 통합된 비어 있는 새 전자 메일 메시지로, 새 아이콘을 표시합니다.](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. Dynamics 365 아이콘을 클릭합니다. 이 전자 메일을 추적하거나 템플릿, 판매 문서 또는 기사에 액세스할 수 있는 **Dynamics 365** 창을 확인해야 합니다.
    
8. 전자 메일 메시지의 **받는 사람** 필드에서 **alex.y.wu@outlook.com**을 입력한 다음 **Dynamics 365** 창에서 **다시 시도**를 클릭합니다. **Dynamics 365** 창에서 **받는 사람** 섹션에 평가판 구독의 샘플 데이터와 함께 제공된 판매 응용 프로그램의 연락처인 Alex Wu에 대한 정보가 표시되어야 합니다.
    
     ![Dynamics 365에 저장된 판매 연락처에 대한 Dynamics 365 정보 창입니다.](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. **취소**를 클릭합니다.

> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.
    
## <a name="see-also"></a>참고 항목

[Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365용 구독 관리(온라인)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Dynamics 365 관리](https://technet.microsoft.com/library/dn531101.aspx)


