---
title: 저속 네트워크에서의 Office 365 사용에 대 한 모범 사례
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
description: 인터넷 연결이 항상 빠른 속도로 작동 하지 않는 경우에는 유용 하지 않을까요? 해당 일이 곧 제공 될 예정입니다. 그러나이 경우에도 balky 네트워크를 해결 하기 위해 수행할 수 있는 실질적인 작업을 계속 해 서 수행 해야 합니다.
ms.openlocfilehash: 2287de562672f5ceb1ab32949168e8dfdeb31585
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490252"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>저속 네트워크에서의 Office 365 사용에 대 한 모범 사례

인터넷 연결이 항상 빠른 속도로 작동 하지 않는 경우에는 유용 하지 않을까요? 해당 일이 곧 제공 될 예정입니다. 그러나이 경우에도 balky 네트워크를 해결 하기 위해 수행할 수 있는 실질적인 작업을 계속 해 서 수행 해야 합니다. Office 365은 클라우드 기반 서비스 이지만 콘텐츠를 오프 라인으로 작업 하 고 변경 내용을 원활 하 게 유지 하는 다양 한 방법을 제공 합니다. 또한 응용 프로그램이 더 빠르게 실행 되 고 사용자 인터페이스가 응답 하기 때문에 콘텐츠를 오프 라인으로 작업 하는 것이 보다 효율적입니다. 이러한 점은 Office 365에서 제공 하는 두 가지 기능을 모두 활용 하는 것입니다. 이를 활용 하는 방법은 다음과 같습니다. 
  
> [!TIP]
> 네트워크 연결이 얼마나 느리거나 빠른 지 확인 하 고 싶으십니까? [OOKLA speed test](https://www.speedtest.net/) 또는 [Network 스피드 test 앱](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70)을 사용해 보십시오. 
     
## <a name="why-is-my-network-so-slow"></a>네트워크가 느리게 진행 되는 이유는 무엇 인가요?

네트워크 성능 자체를 제어할 수 있는 것은 아니지만, 내부적으로 진행 되 고 있는 작업을 파악 하는 데 도움이 됩니다. 인터넷은 enormously 복잡 하지만 상황을 훨씬 더 잘 이해 하는 데 도움이 되는 몇 가지 개념이 있습니다. 이 문서의 모범 사례를 수행 하면 성능 문제를 해결 하 고 발생 가능성을 줄일 수 있습니다.
  
**네트워크 성능에 영향을 주는 주요 요인**

![네트워크 성능 요인](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **대역폭 및 대기 시간** 네트워크 성능에 대 한 가장 중요 한 두 가지 기준은 대역폭과 대기 시간입니다. 
  
- 대역폭은 초당 비트 수로 측정 되는 처리량의 비율입니다. 더 큰 도움이 됩니다. 대역폭은 물 파이프와 같습니다. 파이프가 클수록이를 통해 "배치할 수 있는 물이 더 커집니다.
    
- 대기 시간은 콘텐츠가 서버 또는 서비스에서 장치로 가져오는 데 소요 되는 시간으로 밀리초 단위로 측정 됩니다. 속도가 더 빠릅니다. 대기 시간은 낮은 대역폭, 스파스 연결 또는 전송 시간을 비롯 한 여러 요인으로 인해 발생할 수 있습니다.
    
 **일반적인 문제** 대역폭 및 대기 시간 외에도 다른 문제는 네트워크 성능에 영향을 주므로 예측 불가능 한 경우가 많습니다. 네트워크 성능이 하루 시간 또는 실제 위치를 기반으로 fluctuate 수 있습니다. 네트워크는 자연 재해 또는 주요 공용 이벤트와 같이 인터넷을 사용 하는 특정 이벤트가 발생 하는 경우 clogged 될 수 있습니다. 로드 되는 페이지의 크기와 복잡도, 전송 되는 파일의 수와 크기에는 성능에 직접적인 관계가 있습니다. WiFi 연결이 일시적으로 저하 될 수 있습니다. 예를 들어, 모든 사용자에 게 동시에 tweet을 요청 하 여 수천 명의 대량 전화 회의를 폴링합니다. 
  
 **위성 네트워크에 대 한 고려 사항** 위성 네트워크는 해외 네트워크 (예: 뒷면 국가, 여객선 업체 배송 또는 원격 공학용 지역)가 적합 하지 않은 경우에 유용 합니다. 이러한 네트워크는 equator 위에 geosynchronous 궤도 22000 마일에 위치한 위성을 사용 합니다. 그러나 실제로 전송은 약 9만 마일으로 이동 하므로 위성 네트워크는 지상파 네트워크 (20 ~ 50ms) 보다 대기 시간이 더 느립니다 (500 ms 이상). 가장 좋은 조건에서는이 대기 시간이 표시 되지 않지만 대용량 파일을 다운로드 하 고 비디오를 스트리밍하 고 게임을 재생 하는 것이 좋습니다. 또 다른 문제는 thunderstorms 및 blizzards와 같은 고급 날씨로 인해 위성 전송을 일시적으로 중단할 수 있다는 것입니다.
  
## <a name="are-you-sure-its-the-network"></a>네트워크 임을 확인 하세요.

성능 문제가 발생할 때마다 먼저 장치가 문제의 근본적인 원인이 아닌지 확인 해야 합니다. 다음과 같은 두 가지 방법으로 크게 개선 될 수 있습니다.
  
- 장치가 제대로 작동 하 고 컴퓨터에 맬웨어가 있는지 확인 합니다.
    
- 가능한 경우 더 많은 메모리를 구입 합니다. 메모리를 추가 하는 것은 장치에서 성능을 개선 하는 가장 간단 하 고 효과적인 방법입니다. 큰 파일과 동영상을 사용할 때 특히 유용 합니다.
    
자세한 내용은 [windows 성능 및 유지 관리](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help) 및 [windows 시스템 성능 문제 수정을](https://support.microsoft.com/mats/slow_windows_performance/)참조 하세요.
   
## <a name="best-practices-for-using-your-browser"></a>브라우저 사용에 대 한 모범 사례

브라우저는 office 365의 게이트웨이입니다, 특히 페이지를 로드 하는 데 걸리는 시간과 office 365 서비스로의 라운드트립 빈도에 따라 성능에 영향을 줄 수 있습니다. 
  
 **일반적인 브라우저**
  
다음은 일반적인 브라우저에 대 한 몇 가지 제안입니다.
  
- 성능에 영향을 줄 수 있거나 실제로 필요 하지 않은 브라우저 추가 기능을 사용 하지 않도록 설정 합니다.
    
- 임시 인터넷 파일의 캐시 크기를 늘립니다.
    
-  회사 또는 학교 계정에 로그인 한 후에는 브라우저 창이 하루 종일 열린 상태로 유지 합니다. 다시 로그인 하지 않고도 다른 탭과 창을 열 수 있습니다. 다른 계정에 로그인 해야 하는 경우 전용 검색을 사용 합니다. 
    
- 각 페이지가 다운로드 되 고 열린 후 탭을 사용 하 여 열려 있는 상태로 유지 합니다. 탭 간을 탐색 하 고 나중에 해당 페이지를 사용 하는 것이 쉽습니다. 해당 페이지의 최신 데이터가 필요한 경우에만 페이지를 새로 고칩니다.
    
- 페이지를 여는 데 시간이 너무 오래 걸리는 경우에는 페이지 다운로드 (ESC 키를 누름)를 중지 하 고 F5 키를 눌러 페이지를 새로 고칩니다. 
    
-  가능한 경우에는 Office 365로의 라운드트립 속도를 낮춥니다. 예를 들어 목록 또는 라이브러리를 통한 페이징 대신, 검색을 사용 하 여 큰 라이브러리의 파일을 찾은 다음 목록에서 필터링 하 여 원하는 결과를 바로 가져올 수 있습니다. 또는 페이지 로드 시간을 최소화 하는 보기를 만듭니다. 자세한 내용은 [Office 365에서 큰 목록 및 라이브러리 관리](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES)를 참조 하세요.
    
- 비디오 성능이 낮을 경우 비디오를 다운로드 하 여 장치에서 시청할 수 있습니다. 다운로드 링크를 사용할 수 있거나, 비디오 링크를 마우스 오른쪽 단추로 클릭 하 고 다른 **이름으로 대상 저장**을 선택할 수 있습니다. 
    
 **브라우저 관련**
  
다음은 특정 브라우저에 대 한 몇 가지 제안입니다.
  
- **Internet Explorer** 이전 버전에 비해 상당한 성능 향상을 위해 Internet Explorer 버전 11 이상으로 업그레이드 합니다. 자세한 내용은 [Internet Explorer 문제 수정을 ](https://support.microsoft.com/mats/ie_performance_and_safety)참조 하십시오.
    
- **FireFox** 자세한 내용은 [Firefox 속도가 느리거나 작동 중지](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging)를 참조 하세요.
    
- **Safari** 자세한 내용은 [Apple-Safari](https://www.apple.com/safari/)를 참조 하세요.
    
- **Chrome** 자세한 내용은 [Chrome 도움말](https://support.google.com/chrome/?hl=en)을 참조 하십시오.
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>outlook 및 outlook Web App 사용에 대 한 모범 사례

모든 사용자가 전자 메일을 읽고 쓰고 구성 하는 과정은 매우 중요 합니다. outlook 및 OWA (outlook Web App)는 모두 오프 라인 지원을 제공 합니다. 다른 유용한 대안은 스마트 폰에서 전자 메일 앱을 사용 하는 것입니다. 요구 사항에 가장 잘 맞는 다음 옵션을 사용 합니다.
  
- 이전 버전에 비해 상당한 성능 향상을 위해 Outlook 2013 SP1 이상으로 업그레이드 합니다. 
    
-  Outlook Web App에서는 OWA가 다음에 Office 365에 연결할 수 있을 때 업로드 되는 오프 라인 메시지, 연락처 및 일정 이벤트를 만들 수 있습니다. OWA를 오프 라인 모드에서 설정 및 사용 하는 방법에 대 한 자세한 내용은 [오프 라인으로 Outlook Web App 사용](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)을 참조 하십시오.
    
- Outlook에서는 가능한 경우 자동으로 연결 되는 캐시 된 모드에서 작업할 수 있습니다. 전체 사서함 이나 일부만 다운로드 하도록 할 수 있습니다. 자세한 내용은 Outlook에서 [캐시 된 Exchange 모드 설정](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) 및 [오프 라인으로 작업](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633)을 참조 하세요. 
    
- Outlook 에서도 오프 라인 모드를 제공 합니다. 이를 사용 하려면 먼저 사용자 계정의 정보를 컴퓨터로 복사 하도록 캐시 된 모드를 설정 해야 합니다. 오프 라인 모드에서는 Outlook이 보내기 및 받기 설정을 사용 하 여 연결을 시도 하거나 온라인으로 작동 하도록 수동으로 설정 합니다. 자세한 내용은 오프 라인으로 [작업을 참조 하 여 데이터 연결 요금을 방지 하](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282)고, 오프 라인으로 [작업할 때 보내기 및 받기 설정을 변경](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)하 고, [오프 라인으로 작업을 온라인으로 전환](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9)합니다. 
    
- 스마트 전화가 있는 경우 전화 통신 회사 네트워크를 통해 전자 메일 및 일정을 분류 하는 데 사용할 수 있습니다. 
    
> [!NOTE]
> 다음은 Outlook 또는 OWA를 사용 하는 경우에 대 한 몇 가지 지침입니다. 장치에서 디스크 공간이 문제가 되지 않는 경우 Outlook에서는 전체 기능을 제공 하며 가장 적합 한 방식으로 작업할 수 있습니다. 장치에서 디스크 공간이 문제인 경우 기능 하위 집합이 있는 OWA를 사용 하는 것이 좋지만 온라인 상황에서 가장 잘 작동 합니다. 물론 제대로 작동 하기 때문에이 방법을 사용할 수 있습니다. 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>비즈니스용 OneDrive 사용에 대 한 모범 사례

비즈니스용 OneDrive는 온라인 및 오프 라인으로 파일에 대해 처음부터 작동 하도록 설계 되었습니다. 이를 설정 하 고 나면 변경 내용의 동기화가 자동으로 수행 되 고 언제 든 지, 모든 위치에서 안전 하 게 작동 합니다. 네트워크가 느린 경우 오프 라인 버전의 파일을 사용 하 여 작업할 수 있습니다.
  
비즈니스용 OneDrive 동기화 앱은 office 2013 (Professional Plus 또는 Standard edition) 또는 office 2013 응용 프로그램을 포함 하는 office 365 구독에서 사용할 수 있습니다. Office 2013이 없는 경우 비즈니스용 OneDrive 동기화 앱을 무료로 [다운로드할](https://support.microsoft.com/kb/2903984) 수 있습니다. 또한이 앱은 **탐색기에서 열기** 또는 **업로드** 명령을 사용 하는 것 보다 빠릅니다. 자세한 내용은 [Office 365에서 비즈니스용 OneDrive 파일을 동기화 하도록 컴퓨터 설정을](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16)참조 하세요.
  
비즈니스용 OneDrive 동기화 앱을 사용 하기 위한 몇 가지 추가 지침은 다음과 같습니다.
  
- 대규모 라이브러리를 처음으로 동기화 하는 경우에는 근무 외 시간 동안 동기화를 시작 합니다 (예: 야간). 
    
- [라이브러리를 비즈니스용 OneDrive 앱과의 동기화 중지](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) 기능을 사용 하 여 업데이트 동기화를 일시적으로 중지할 수 있습니다. 그러나 많은 수의 업데이트를 대기 시 가지 않고 여러 사용자가 같은 문서에서 작업할 경우 병합 충돌의 위험을 최소화 하기 위해 몇 시간에 한 번씩이 기능을 사용 하는 것이 좋습니다. 
  
## <a name="best-practices-for-using-onenote"></a>OneNote 사용에 대 한 모범 사례

모든 SharePoint 팀 사이트에는 기본적으로 제공 되는 OneNote 전자 필기장이 있으며 직접 만들 수 있습니다. OneNote를 통해 매일 필요한 정보를 수집 하 여 작업을 완료할 수 있습니다. 예를 들어 많은 팀은 주간 회의, 프로젝트 메모, 아이디어, 계획 및 상황 보고서의 컬렉션 포인트로 OneNote를 사용 합니다. 페이지, 섹션 및 탭을 사용 하 여 이러한 서로 다른 정보를 깔끔하게 구성할 수 있습니다.
  
그러나 OneNote의 장점은 데스크톱, 랩톱, 태블릿 또는 스마트폰에 관계 없이 거의 모든 장치에서 콘텐츠에 액세스할 수 있다는 것입니다. 또한 OneNote에서 사용자를 위해 저장 하거나 동기화 하는 경우를 걱정 하지 않아도 됩니다. 
  
자세한 내용은 [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/)를 참조 하세요.
  
## <a name="best-practices-for-using-lync-online"></a>Lync Online 사용에 대 한 모범 사례

다음은 네트워크 속도가 느린 경우 Lync Online을 사용 하기 위한 일반적인 지침입니다.
  
- 느린 네트워크에서 정상적으로 작동 하는 경우에는 항상 인스턴트 메시징을 사용 합니다.
    
- VPN (가상 사설망) 또는 RAS (원격 액세스 서비스) 연결을 통한 전화 통화를 방지 합니다.
    
- 오디오 장치가 승인 되었는지 확인 합니다. 자세한 내용은 [Microsoft Lync에 한정 된 전화 및 장치](https://technet.microsoft.com/en-us/office/dn788944)를 참조 하세요.
    
-  온라인 프레젠테이션에서 PowerPoint를 사용 하는 경우 슬라이드의 크기와 복잡도를 줄입니다. 자세한 내용은 [프레젠테이션의 성능을 향상 시키는 팁](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949)을 참조 하십시오.
    
- 가능한 경우 프로그램 또는 데스크톱 대신 모니터를 공유 합니다. 자세한 내용은 [Lync에서 데스크톱 또는 프로그램 공유](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842)를 참조 하세요.
    
- 참석자가 자신의 클라이언트 장치에서 슬라이드를 볼 때 공유 하는 대신 PowerPoint 슬라이드를 모임 요청 첨부 파일로 전송 합니다. 자세한 내용은 [Lync Meeting 설정](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d)항목을 참조 하십시오.
    
-  비디오 성능은 네트워크 성능에 따라 크게 좌우 됩니다. 네트워크가 느린 경우에는 비디오를 사용 하지 마십시오. 
    
자세한 내용은 lync [Online의 오디오 또는 비디오 품질 저하](https://support.microsoft.com/kb/2386655) 및 [lync 2013의 느린 화면 업데이트](https://support.microsoft.com/kb/2958375)를 참조 하세요.
  
## <a name="best-practices-for-using-sharepoint-lists"></a>SharePoint 목록을 사용 하는 최상의 방법

데이터를 오프 라인으로 "스크러빙", 분석 또는 보고 하 여 느린 네트워크의 영향을 최소화 하는 데 유용한 방법입니다. 연결 하 여 Microsoft Access 2013에서 대부분의 목록을 읽고 작성할 수 있습니다. excel 테이블과 목록 간에 단방향 데이터 연결을 만드는 목록을 excel 테이블로 내보낼 수도 있습니다.
  
또한 Access Services 기능이 활성화 되 면 목록 보기 임계값 보다 훨씬 더 많은 데이터를 사용할 수 있으며, 기본적으로 최대 5만 개의 항목이 사용 가능 합니다. Access 2013 및 Excel 2013에서는 목록 데이터를 작은 일괄 처리로 자동 처리 하 고 데이터를 다시 어셈블합니다. 목록 보기 임계값 보다 더 많은 데이터를 사용 하 여 작업을 수행 하 고 서비스 성능에 악영향을 미치지 않습니다. 기타 사용자입니다. 
  
자세한 내용은 [Office 365에서 대규모 목록 및 라이브러리 관리](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784)의 "큰 목록 관리에 대 한 자세한 내용" 섹션을 참조 하세요.
  
## <a name="best-practices-for-customizing-web-pages"></a>웹 페이지 사용자 지정을 위한 최상의 방법

웹 페이지를 사용자 지정 하면 페이지 성능이 잘못 될 수 있습니다. 페이지의 복잡성과 크기, 추가 되는 웹 파트의 수, 처음에 표시 되는 목록 또는 라이브러리 항목 수, 페이지를 코딩 하는 방법 등의 여러 요소에 영향을 줄 수 있습니다.
  
자세한 내용은 [SharePoint Online 성능 조정을](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance)참조 하세요.
  
## <a name="best-practices-for-using-project-online"></a>Project Online 사용에 대 한 모범 사례

다음 지침은 네트워크 성능을 향상 시키는 데 도움이 될 수 있습니다.
  
- Project Online 및 SharePoint Online에는 동기화가 필요 하며,이 경우 시간이 오래 걸릴 수 있습니다. 프로젝트 팀이 낮은 회전율을 갖는 경우 프로젝트 사이트 동기화를 사용 하지 않도록 설정 하 여 프로젝트 게시 및 프로젝트 세부 정보 페이지 성능을 개선 합니다. Active Directory 동기화를 실제로 시스템을 사용 하는 데 필요한 리소스 그룹으로 제한 하 고 대규모 그룹을 동기화 한 후에 발생할 수 있는 모든 권한 문제를 모니터링 합니다. 
    
- 조직에서 프로젝트 사이트를 사용 하는 경우에는 자동이 아니라 필요할 때 만듭니다. 이렇게 하면 첫 번째 게시 환경이 향상 되 고 불필요 한 사이트 및 콘텐츠가 생성 되지 않습니다.
    
- 프로젝트 세부 정보 페이지 (PDP)는 전체 프로젝트를 다시 계산 하 고 워크플로 작업을 시작할 수 있으며, 둘 다 성능 집약적인 작업을 수행할 수 있습니다. 동일한 PDP에서 두 개의 업데이트 프로세스를 동시에 트리거하지 않도록 하려면 달력 필드 (시작 날짜, 완료 날짜, 상황 보고 날짜 및 현재 날짜)와 예약 되지 않은 필드 (프로젝트 이름, 설명 및 소유자)를 업데이트 하지 않도록 합니다. 
    
- 각 PDP에 표시 되는 웹 파트 및 사용자 정의 필드 수를 줄입니다. 부하를 개선 하 고 시간을 절약 하기 위해 업데이트가 필요한 필드만 포함 된 전용 PDP를 만듭니다. 
    
- 보고에 OData를 사용 하는 경우 런타임에 서버 쪽 필터링을 사용 하 여 쿼리 하는 데이터의 양을 제한 합니다.
    
자세한 내용은 [Project Online 성능 조정을](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)참조 하세요.
  
## <a name="whats-the-best-way-to-report-problems"></a>문제를 보고 하는 가장 좋은 방법은 무엇 인가요?

Microsoft는 네트워크를 모니터링 하 고 대역폭과 대기 시간을 측정 하 고, 페이지 로드 시간을 높이 며, 디스크 i/o를 줄이고, 페이지를 최소 다운로드 전략을 사용 하 여 데이터 센터에 추가 하는 방법으로 Office 365의 전반적인 성과를 지속적으로 개선 하 고 있습니다. 더 많은 데이터 센터 추가 현재 상태 및 보고 문제를 확인 하는 방법에 대 한 자세한 내용은 [서비스의 상태 보기](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx)를 참조 하세요.
  
## <a name="see-also"></a>참고 항목

[Office 365의 네트워크 계획 및 성능 조정](network-planning-and-performance.md)
  
[Microsoft 가상 아카데미 강좌-Office 365 성능 관리](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

