---
title: Office 365를 사용 하 여 저속 네트워크에 연결 하는 것에 대 한 모범 사례
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
description: 않을까요 인터넷 연결 고속 항상 이었으며 하지 아래쪽 하는 경우? 아마도 그 날 상태가 됩니다. 하지만 동시에 다음과 같은 사항을 실제적인 balky 네트워크를 해결 하 고 여전히 일상적인 작업을 수행 하기 위해 할 수 있는.
ms.openlocfilehash: 52c3bde04aa58f9e24a49d2034e6b6433c44f21c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542165"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Office 365를 사용 하 여 저속 네트워크에 연결 하는 것에 대 한 모범 사례

않을까요 인터넷 연결 고속 항상 이었으며 하지 아래쪽 하는 경우? 아마도 그 날 상태가 됩니다. 하지만 동시에 다음과 같은 사항을 실제적인 balky 네트워크를 해결 하 고 여전히 일상적인 작업을 수행 하기 위해 할 수 있는. Office 365 클라우드 기반 서비스는 있지만, 오프 라인으로 콘텐츠를 사용 하 고 원활 하 게 동기화 하 여 변경 내용을 유지 하려면 다양 한 방법 제공 합니다. 게다가 경우에 따라 더 빠르게 응용 프로그램을 실행 하 고 사용자 인터페이스는 더 빠르게 응답 때문에 콘텐츠를 오프 라인으로 작업 하는 효율적입니다. 중요 한 점은이: Office 365의 장점 모두 제공 합니다. 활용 하는 방법은 다음과 같습니다. 
  
> [!TIP]
> 네트워크 연결이 어떻게 속도가 느림 (또는 fast) 보 시겠습니까? [OOKLA 속도 테스트](https://www.speedtest.net/) 또는 [네트워크 속도 테스트 응용 프로그램](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70)을 시도 합니다. 
     
## <a name="why-is-my-network-so-slow"></a>내 네트워크 아주 느린 이유는 무엇입니까?

자체 네트워크 성능에 대 한 제어를 설치 하지 않은 있지만 백그라운드에서 무슨 이해 하는데 도움이 됩니다. 인터넷은 매우 복잡 하지만 훨씬 더 나은 상황을 이해 하는데 도움이 되는 몇가지 개념입니다. 이 문서에서 모범 사례를 따르는 성능 문제를 해결 하는 데 도움이 및 불만 줄일 수 있습니다.
  
**네트워크 성능에 영향을 주는 주요 요인**

![네트워크 성능 요인](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **대역폭 및 대기 시간** 네트워크 성능의 가장 중요 한 두 측정값 대역폭 및 대기 시간에는: 
  
- 대역폭은 비트 / 초 단위로 지정 하는 처리량의 비율입니다. 클수록이 더 좋습니다. 대역폭 물 파이프와 비슷합니다. 파이프 클수록 넣을 수 있습니다 "를 통해" 자세한 물 합니다.
    
- 대기 시간은 장치로 서버 또는 서비스에서 가져올 콘텐츠에 대 한 걸리고 밀리초 단위로 측정 됩니다. 더 빠르게이 더 좋습니다. 다양 한 요인 낮은 대역폭, 성긴 연결 또는 전송 시간을 포함 하 여 대기 시간을 발생할 수 있습니다.
    
 **일반적인 문제** 대역폭 및 대기 시간 외에도 다른 네트워크 성능에 영향을 미칠 문제와 자주 예측할 수 없습니다. 네트워크 성능 하루 또는 실제 위치 시간에 따라 잡음이 수 있습니다. 네트워크 스파이크 자연 재해 또는 주요 공용 이벤트와 같은 인터넷을 사용 하는 특정 이벤트가 발생할 때 막히면 수 있습니다. 크기 및 복잡성 로드 되는 페이지의 수 및 전송 중인 파일의 크기를 관계가 직접 성능에 있습니다. Wi-fi 연결 일시적으로 저하 될 수 있습니다: 모든 사용자가 동시에 소리를 요청 하 여 수천 대규모 회의 모임을 폴링해야 하는 예입니다. 
  
 **위성 네트워크에 대 한 고려 사항** 위성 네트워크 지상파 네트워크 불가능 한 백 국가, 크루즈 ship, 또는 원격 공학용 영역 같은 경우에 유용 합니다. 이러한 네트워크 geosynchronous 파킹 된 통화는 적도 위에 22,000 마일에 배치 하는 위성에 의존 합니다. 그러나 전송을 실제로 90,000 마일 약으로 이동 하 고 위성 네트워크에 연결 되었습니다 (500ms 이상) 속도가 느린 대기 시간 보다 지상파 네트워크 (20 50ms). 조건 최고의 아래에서이 대기 시간을 알 수 없습니다 있지만 대용량 파일을 다운로드 하 고 스트리밍 비디오, 게임을 실행 하는 것에 대 한 것은 합니다. 다른 문제 "스런 나 및 (폭풍), 예:는 대용량 날씨 위성 전송을 일시적으로 중단할 수에서" 페이드 레인입니다.
  
## <a name="are-you-sure-its-the-network"></a>네트워크 인지 이십니까?

성능 문제가 발생 하면 때마다 먼저 장치 문제의 근본 원인이 없는 있는지 확인 합니다. 가지 큰 개선 하도록 할 수 있는 두 작업을 수행할 수 있습니다.
  
- 장치가 제대로 실행 되 고이 사용자의 컴퓨터에 없는 맬웨어 되어있는지 확인 합니다.
    
- 가능한 경우 더 많은 메모리를 구입 합니다. 가장 자주 간단 하 고는 메모리를 추가 장치에서 성능을 향상 시키기 위해 효과적인 방법입니다. 대용량 파일 및 비디오로 작업 하는 경우에 특히 유용 합니다.
    
자세한 내용은 [Windows 성능 및 유지 관리](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help) 하 고 [수정 하는 Windows 시스템 성능 문제](https://support.microsoft.com/mats/slow_windows_performance/)를 참조 하십시오.
   
## <a name="best-practices-for-using-your-browser"></a>브라우저를 사용 하기 위한 모범 사례

브라우저에서 Office 365에 해당 게이트웨이, 특히 로드 하는데 걸리는 시간와 성능에는 영향을 갖게 페이지 및 라운드 얼마나 자주 여행 office 365 서비스입니다. 
  
 **일반 브라우저**
  
다음은 추천 되는 브라우저에 대 한 일반적:
  
- 성능에 영향을 줄 수 있는 또는 정말 하지 않아도 브라우저 추가 기능을 사용 하지 않도록 설정 합니다.
    
- 임시 인터넷 파일에 대 한 캐시 크기를 늘립니다.
    
-  작업이 나 교육용 계정에 로그인 한, 되 면 브라우저 창을 열어 하루 동안 합니다. 다시 로그인 하지 않고 다른 탭과 windows를 열 수 있습니다. 다른 계정으로 로그인 해야 하는 경우 개인 검색을 사용 합니다. 
    
- 각 페이지에 다운로드 하 고 열기 되 면 계속 해 서 열기 탭을 사용 하 여 합니다. 탭 간에 이동 하 고 하루에서 나중에 페이지를 사용 하는 것이 쉽습니다. 해당 페이지에서 최신 데이터를 해야 하는 경우에 페이지를 새로 고칠 합니다.
    
- 페이지를 열려면 너무 오래 걸리는 것을 하는 경우 페이지 다운로드 (ESC 키를)를 중지 하 고 (f5 누름) 페이지를 새로 고쳐 합니다. 
    
-  가능한 경우 Office 365로 왕복을 줄입니다. 예, 대신 목록 또는 라이브러리를 통해 페이징, 사용 하 여 검색 대규모 라이브러리 및 사용자가 원하는 결과를 직접 목록에서 필터링에서 파일을 찾습니다. 또는 페이지 로드 시간을 최소화 하는 보기를 만듭니다. 자세한 내용은 [큰 목록 및 라이브러리 Office 365의 관리](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES)를 참조 하십시오.
    
- 비디오 성능이 저하 경우 비디오를 다운로드 하 고 장치에서 보기를 수 있습니다. 다운로드 링크를 사용할 수 있습니다 또는 비디오 링크를 마우스 오른쪽 단추로 클릭 하 고 **다른이름으로 대상 저장**을 선택 하는 작업을 할 수 있습니다. 
    
 **브라우저 전용**
  
특정 브라우저에 대 한 일부 제안 다음과 같습니다.
  
- **Internet Explorer** 이전 버전에 비해 성능이 상당히 향상 된 기능 또는 나중에 Internet Explorer 버전 11로 업그레이드 합니다. 자세한 내용은 [Internet Explorer 수정 문제 ](https://support.microsoft.com/mats/ie_performance_and_safety)를 참조 하십시오.
    
- **FireFox** 자세한 내용은 [Firefox 속도가 느림 또는 작동 중지](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging)를 참조 하십시오.
    
- **Safari** 자세한 내용은 [Apple-Safari를](https://www.apple.com/safari/)참조 하십시오.
    
- **크롬** 자세한 내용은 [크롬 도움말](https://support.google.com/chrome/?hl=en)을 참조 하십시오.
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Outlook 및 Outlook Web App를 사용 하기 위한 모범 사례

읽기, 쓰기, 및 전자 메일 구성 큰 일부인 모든 사람의 되는 시간입니다. Outlook 및 Outlook Web App (OWA) 모두 오프 라인 지원을 제공합니다. 스마트 전화기에서 전자 메일 응용 프로그램을 사용 하 여 다른 유용한 대체 됩니다. 요구 사항에 가장 잘 맞는 다음 옵션을 사용 합니다.
  
- 이전 버전에 비해 성능이 상당히 향상 된 기능 또는 나중에 Outlook 2013 s p 1로 업그레이드 합니다. 
    
-  Outlook Web App를 사용 하면 오프 라인에서 메시지, 연락처 및 일정 이벤트 다음에 OWA 때 업로드 되는 Office 365에 연결할 수를 만들 수 있습니다. 설정 및 오프 라인 모드에서 OWA를 사용 하는 방법에 대 한 자세한 내용은 [사용 하 여 Outlook Web App 오프 라인](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)을 참조 하십시오.
    
- Outlook을 사용 하는 자동으로 연결 가능 하면 항상 캐시 된 모드에서 작업할 수 있습니다. Outlook을 다운로드 하 여 전체 사서함 또는 그 중 일부만 있을 수 있습니다. 자세한 내용은 [캐시 된 Exchange 모드를 설정](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) 하 고 [Outlook에서 오프 라인으로 작업](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633)을 참조 하십시오. 
    
- Outlook을 오프 라인 모드 상태를 제공합니다. 이 스위치를 사용 하려면 먼저 설정 해야 캐시 된 모드를 하 여 사용자 계정에서 정보는 사용자의 컴퓨터에 복사 됩니다. 오프 라인 모드에서 Outlook에서 시도 보내기를 사용 하 여 연결 하 고 설정, 수신 또는 수동으로 설정한 경우 온라인으로 작업 하도록 합니다. 자세한 내용은 [데이터 연결 요금을 방지 하기 위해 오프 라인으로 작업](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [변경 보내기 및 받기 오프 라인으로 작업 하는 경우 설정](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)및 [온라인를 오프 라인으로 작업에서 스위치](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9)를 참조 하십시오. 
    
- 스마트폰을 설치한 경우에 전화 통신 회사의 네트워크를 통해 전자 메일 및 캘린더를 분류할 사용할 수 있습니다. 
    
> [!NOTE]
> 다음은 Outlook 또는 OWA를 사용 하는 경우에 대 한 일부 지침입니다. 디스크 공간 장치에 문제가 없는 경우 Outlook 기능의 전체 집합 있으며 최고 적용할 수 있는 방법입니다. 장치에 문제가 디스크 공간을 사용 하는 경우에 기능에 대 한 하위 집합에는 있지만 또한는 온라인 상황에 가장 잘 작동 하는 OWA를 사용 하 여 하는 것이 좋습니다. 물론 함께 잘 작동 하기 때문에 사용할 수 있습니다. 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>비즈니스용 OneDrive를 사용 하는 것에 대 한 모범 사례

비즈니스용 OneDrive은 온라인 및 오프 라인으로 프로그램 파일을 사용 하도록를 처음부터 설계 합니다. 설정한 것을 자동으로 하 고 안전 하 게 변경 내용에 대 한 동기화 발생 한 후 장소와 때마다 수 있도록. 네트워크가 느린 경우에 오프 라인 버전의 파일을 작업할 수 있습니다.
  
비즈니스 동기화 응용 프로그램에 대 한 OneDrive는 (Professional Plus 또는 Standard edition), Office 2013 및 Office 2013 응용 프로그램을 포함 하는 Office 365 구독을 사용할 수 있습니다. Office 2013를 설치 하지 않은 경우 할 수 있습니다 [다운로드](https://support.microsoft.com/kb/2903984) 비즈니스 동기화 응용 프로그램에 대 한 OneDrive 무료로 합니다. 이 app **탐색기에서 열기** 또는 **업로드** 명령을 사용 하는 것 보다 이기도 합니다. 자세한 내용은 [Office 365의 비즈니스 파일에 대 한 OneDrive와 동기화 하기 위해 컴퓨터를 설정](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16)을 참조 하십시오.
  
OneDrive 비즈니스 동기화 응용 프로그램을 사용 하기 위한 일부 추가 지침은 다음과 같습니다.
  
- 처음에 대 한 대규모 라이브러리를 동기화 하는 경우 예, 야 간에 시간을 해제 하는 동안 동기화를 시작 합니다. 
    
- 일시적으로 업데이트의 동기화를 중지 하는 [비즈니스 응용 프로그램에 대 한 onedrive 라이브러리의 동기화를 중지](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) 하는 기능을 사용할 수 있습니다. 그러나 큰 큐를 방지 하기 위해 한 번에 몇 시간 등의 짧은 기간 동안에 대 한이 기능을 사용 하 고 여러 사용자가 동일한 문서에서 작업 하는 경우 병합 충돌의 위험을 최소화 하기 위해 업데이트의 번호를 매깁니다. 
  
## <a name="best-practices-for-using-onenote"></a>OneNote를 사용 하기 위한 모범 사례

모든 SharePoint 팀 사이트에는 기본 제공 OneNote 전자 필기장 및 쉽게 만들 수 있습니다 직접 합니다. OneNote는 편리 하 게 작업을 완료할를 매일 해야하는 시기 적절 하 게 정보를 수집 합니다. 예, 많은 팀 주간 회의 프로젝트 정보, 아이디어, 계획 및 상황 보고서에 대 한 컬렉션 지점으로 OneNote를 사용 합니다. 듯 페이지, 섹션 및 탭을 사용 하 여이 서로 다른 정보를 구성할 수 있습니다.
  
하지만 OneNote의 장점은 데스크톱, 랩톱, 태블릿 또는 스마트폰 여부 거의 모든 장치에서 콘텐츠를 액세스할 수 있다는 점입니다. 및 저장 하거나 OneNote 하면 않기 때문에 동기화 하는 방법에 대 한 염려할 필요가 없습니다. 
  
자세한 내용은 [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/)를 참조 하십시오.
  
## <a name="best-practices-for-using-lync-online"></a>Lync Online을 사용 하기 위한 모범 사례

다음은 네트워크 속도가 느린 경우 Lync Online을 사용 하기 위한 일반적인 지침입니다.
  
- 저속 네트워크에서 제대로 작동 하기 때문에 가능 하면 항상 인스턴트 메시징을 사용 합니다.
    
- 가상 사설망 (VPN) 또는 원격 액세스 서비스 (RAS) 연결을 통해 전화 통화를 요청 하지 않습니다.
    
- 오디오 장치 승인 되 고 있는지 확인 하십시오. 자세한 내용은 [전화 및 Microsoft Lync에 대 한 정규화 된 장치를](https://technet.microsoft.com/en-us/office/dn788944)참조 하십시오.
    
-  PowerPoint를 사용 하 여 온라인 프레젠테이션을에서 크기 및 슬라이드의 복잡도 줄입니다. 자세한 내용은 [프레젠테이션의 성능 향상을 위한 팁](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949)을 참조 하십시오.
    
- 가능 하면 항상 프로그램 또는 데스크톱 대신 모니터를 공유 합니다. 자세한 내용은 [Lync에서 프로그램 또는 데스크톱 공유](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842)를 참조 하십시오.
    
- 모임 미리 PowerPoint 슬라이드를 공유 하는 대신 보낼 클라이언트 장치에서 슬라이드가 표시 되 게 참석자에 게 첨부 파일을 요청 합니다. 자세한 내용은 [Lync 모임 설정](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d)을 참조 하십시오.
    
-  비디오 성능이 매우 네트워크 성능에 따라 달라 집니다. 네트워크 속도가 느린 경우 비디오를 사용 하지 마십시오. 
    
자세한 내용은 [오디오 또는 Lync Online에서 비디오 품질 저하](https://support.microsoft.com/kb/2386655) 및 [Lync 2013의 업데이트 속도가 느린 화면](https://support.microsoft.com/kb/2958375)을 참조 하십시오.
  
## <a name="best-practices-for-using-sharepoint-lists"></a>SharePoint 목록에서 사용 하는 것에 대 한 모범 사례

"스크러빙", 분석, 또는 매우 편리 하 저속 네트워크의 영향을 최소화 하기 위해 데이터를 보고 목록 데이터를 오프 라인으로 작업 합니다. 하면 읽고 쓸 수 있는 대부분의 목록은 Microsoft Access 2013에서 자신에 게 연결 하 여 합니다. Excel 표 및 목록 간에 단방향 데이터 연결을 만들고 하는 Excel 테이블에 목록을 내보낼 수도 있습니다.
  
또한 액세스 서비스 기능이 활성화 된 경우 다음 작업할 수 있습니다 훨씬 더 많은 데이터는 목록 보기 임계값 보다 기본적으로 최대 50, 000 항목입니다. Access 2013 및 Excel 2013 자동으로 작은 일괄 처리에서 목록 데이터를 처리 하 고 데이터를 사용 하 고 서비스 성능에 부정적인 영향을 주지않고 목록 보기 임계값 보다 훨씬 더 많은 데이터를 사용 하는 기술 다시 조립 모두 다른 사용자가 있습니다. 
  
자세한 내용은 [큰 목록 및 라이브러리 Office 365의 관리](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784)에서 "보다 관리에 대 한 큰 목록" 섹션을 참조 합니다.
  
## <a name="best-practices-for-customizing-web-pages"></a>웹 페이지를 사용자 지정을 위한 최상의 방법

웹 페이지를 사용자 지정할 때 페이지와 함께 성능 저하를 실수로 발생할 수 있습니다. 다양 한 요인은 복잡성과 크기는 페이지, 목록 또는 라이브러리 항목 수에 처음 표시 되는 얼마나 많은 웹 파트가 추가 되어 및 페이지 코드 하는 방법의 예:는 영향을 줄 수 있습니다.
  
자세한 내용은 [SharePoint Online 조정 성능](https://technet.microsoft.com/library/f97c2f06-0426-443d-8a16-d98abb0da252#TuneSharePoint)을 참조 하십시오.
  
## <a name="best-practices-for-using-project-online"></a>Project Online을 사용 하기 위한 모범 사례

다음 지침 네트워크 성능을 향상 시킬 수 있습니다.
  
- Project Online 및 SharePoint Online 동기화 시간이 많이 소요 될 수 있는 필요 합니다. 프로젝트 팀 낮은 회전이 프로젝트를 게시 및 프로젝트 세부 정보 페이지 성능을 향상 시키기 위해 프로젝트 사이트 동기화 사용 하지 않도록 설정 합니다. 실제로 시스템을 사용 하 고 큰 그룹의 동기화 한 후 잠재적인 사용 권한 문제를 모니터링 해야 하는 리소스의 그룹을 Active Directory 동기화를 제한 합니다. 
    
- 조직에서 프로젝트 사이트를 사용 하는 경우 만들고 필요에 따라 하지 않고 자동으로 합니다. 첫번째 게시 환경을 속도가 향상 하 고 불필요 한 사이트 및 콘텐츠를 만드는 방지 합니다.
    
- 프로젝트 세부 정보 페이지 (PDP) 트리거 (영문)의 전체 프로젝트를 다시 계산 하 고 워크플로 작업을 모두 성능 집약적인 작업 수를 시작 수 있습니다. 동일한 PDP에서 동시에 두 업데이트 프로세스를 트리거를 방지 하려면 일정 필드 (시작 날짜, 완료 날짜, 상황 보고 날짜 및 현재 날짜) 및 비 예약 된 필드 (프로젝트 이름, 설명 및 소유자)를 업데이트 하지 마십시오. 
    
- 웹 파트 및 각 PDP에 표시 되는 사용자 정의 필드의 수를 줄입니다. 시간을 절약 하 고 부하를 개선 하는 업데이트 필요로 하는 유일한 필드가 전용된 PDP를 만듭니다. 
    
- OData를 사용 하 여 보고에 대 한 서버쪽 필터링을 사용 하 여 런타임에 쿼리 하는 데이터의 양을 제한 합니다.
    
자세한 내용은 [Project Online 조정 성능](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)을 참조 하십시오.
  
## <a name="whats-the-best-way-to-report-problems"></a>문제를 보고 하는 가장 좋은 방법은 무엇입니까?

페이지 로드 시간을 줄이는 디스크 I/O 다시 디자인을 개선 하는 대기 시간 데이터 센터에는 하드웨어 추가 (영문)의 최소 다운로드 전략을 사용 하 여 페이지 및 Microsoft 지속적으로 대역폭을 측정 하는 네트워크를 모니터링 하 여 Office 365의 전반적인 성능이 향상 하 고 더 많은 데이터 센터를 추가 합니다. 현재 상태를 검사 하 고 문제를 보고 하는 방법에 대 한 자세한 내용은 [서비스의 상태 보기](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx)를 참조 하십시오.
  
## <a name="see-also"></a>참고 항목

[Office 365의 네트워크 계획 및 성능 조정](network-planning-and-performance.md)
  
[Microsoft 가상 Academy 코스 (영문)-Office 365 성능 관리](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

