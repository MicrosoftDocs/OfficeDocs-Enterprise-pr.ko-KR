---
title: SharePoint Online에서 콘텐츠 배달 네트워크 사용
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 요약:이 문서에서는 콘텐츠 배달 네트워크 (CDNs) 및이를 사용 하 여 SharePoint Online 성능을 향상 시키는 방법에 대해 설명 합니다.
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070584"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>SharePoint Online에서 콘텐츠 배달 네트워크 사용

 **요약:** 이 문서에서는 CDNs (콘텐츠 배달 네트워크) 및이를 사용 하 여 SharePoint Online 성능을 향상 시키는 방법에 대해 설명 합니다. 
  
오늘날의 웹 개발 커뮤니티에는 SharePoint 솔루션에 포함할 수 있는 여러 공용 라이브러리 (예: JavaScript 및 CSS 파일)가 있습니다. 이러한 대부분의 기능은 해당 ASP CDN에서 Microsoft가 호스트 합니다. 즉, 이러한 분산 서버에서 이러한 라이브러리를 참조 하 고 인터넷의 기본 제공 DNS 라우팅 시스템에서 가장 가까운 사용자의 서버를 찾을 수 있습니다. 이 문서의 예에서는 SharePoint Online server에서 인기 라이브러리 jQuery를 다운로드 하는 것과 ASP CDN 간의 시간 차이가 상당히 중요 한 정도를 보여 줍니다. 또한 사용자는 해당 파일을 다운로드할 필요가 없도록 로컬 컴퓨터에 이미 CDN 버전을 캐시 했을 수 있습니다. 사용자가 세계 전체에 분산 되어 있고 SharePoint Online 사이트를 호스트 하는 데이터 센터에서 멀리 떨어진 곳에 있는 경우에는이 작업이 중요할 수 있습니다.
  
SharePoint Online에 대 한 페이지를 만들 때 대기 시간은 사용자와 SharePoint Online 인스턴스의 위치 간 실제 거리에 따라 영향을 받을 수 있습니다. 이는 전 세계의 다른 지역에 있는 사용자가 해당 콘텐츠에 액세스할 수 있는 전역 현재 상태를 가진 조직에서 특히 중요 합니다. CDNs는 최종 사용자에 게 더 가깝게 다른 위치에 특정 인기 웹 자산을 호스트 하 여 이러한 상황을 완화 합니다.
  
CDN은 동일한 파일을 호스트 하는 서버에 대 한 전 세계 네트워크 이기 때문에, CDNs에 저장 된 파일의 인터넷 Url은 사용자에 게 가장 가까운 서버에서 파일을 사용 하도록 클라이언트 컴퓨터에서 해석 됩니다. 이렇게 하면 네트워크 라운드트립으로 인 한 지연이 크게 줄어듭니다.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>전역 대상 그룹을 위해 SharePoint Online 사이트를 호스트할 때의 어려움

SharePoint Online 사이트는 Office 365에 등록할 때 선택한 위치 (사용자가 지정)에 따라 데이터 센터에서 호스트 됩니다. 예를 들어 사이트가 미국에 있는 서버에 있고 사용자가 동아시아에서 사이트에 액세스 하는 경우, 데이터의 거리가 광섬유 케이블을 통과 하는 것으로 인해 대기 시간 문제가 발생할 수 있습니다.
  
기본 SharePoint 사용자 인터페이스에서 사용 되는 여러 정적 파일은 이미 Microsoft의 CDNs 네트워크에 호스트 되어 있습니다. 이렇게 하면 시간이 지남에 따라 성능이 향상 됩니다. 그러나 인기 JavaScript 및 CSS 자산을 사용 하는 경우 (예: JQuery, Modernizr, 부트스트랩 또는 ASP.NET Ajax) 무료로 사용할 수 있는 CDNs를 사용 하 여 이러한 파일의 로드 시간을 높일 수 있습니다.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>다운로드 속도를 개선 하기 위해 CDNs를 사용 하는 경우의 장점

CDNs를 사용 하면 다양 한 이유로 페이지 로드 시간을 개선할 수 있습니다. 한 가지 이유는 CDN과 사용자 사이의 거리가 SharePoint Online 인스턴스에 대 한 거리 보다 짧을 수 있기 때문입니다. 이러한 네트워크는 고도로 분산 되어 있으며 고가용성 및 응답 시간을 갖도록 설계 되었습니다. 또 다른 이유는 CDN과 함께 사용 하는 CSS 파일의 인기 라이브러리를 사용할 경우 사용자에 게 이미 라이브러리가 캐시 되어 있으므로 다운로드 하지 않아도 된다는 것입니다.
  
다음 스크린샷은 CDNs를 사용 하는 경우의 이점에 대해 설명 합니다. 이러한 스크린샷은 Internet Explorer 11 개발자 도구의 **네트워크** 탭에서 가져온 것입니다. 이러한 스크린샷은 인기 라이브러리 jQuery의 대기 시간을 보여 줍니다. 이 화면을 가져오려면 Internet Explorer에서 **F12** 키를 누르고 wi-fi 아이콘과 함께 인식 되는 기호에 해당 하는 **네트워크** 탭을 선택 합니다. 
  
![F12 네트워크의 스크린샷](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
이 스크린샷은 SharePoint Online 사이트의 마스터 페이지 갤러리에 업로드 된 라이브러리를 보여 줍니다. 라이브러리를 업로드 하는 데 걸리는 시간은 1.51 초입니다.
  
![1.51초의 로드 시간을 보여 주는 스크린샷](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
두 번째 스크린샷에서는 Microsoft의 CDN에서 제공 되는 것과 동일한 파일을 보여 줍니다. 이번에는 대기 시간이 약 496 밀리초입니다. 이 기능은 크게 개선 된 것으로, 초당 전체 시간이 페이지 콘텐츠를 다운로드 하는 데 걸리는 총 시간을 shaved 것을 보여 줍니다.
  
![469밀리초의 로드 시간을 보여 주는 스크린샷](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>SharePoint Server 2013에서 CDNs 사용

CDNs를 사용 하는 것은 SharePoint Online 컨텍스트에서만 적합 하며, SharePoint Server 2013에서는 피해 야 합니다. 이는 서버가 온-프레미스 또는 지리적으로 가까이 있는 경우 지리적 위치에 대 한 모든 이점이 true를 유지 하지 않기 때문입니다. 또한 서버가 호스트 되는 서버에 대 한 네트워크 연결이 있는 경우 인터넷에 연결 하지 않고 사이트를 사용할 수 있으므로 CDN 파일을 검색할 수 없습니다. 그렇지 않은 경우에는 사이트에 필요한 라이브러리 및 파일에 대해 사용 가능한 안정적인 경우 CDN을 사용 해야 합니다.
  
## <a name="popular-cdns-and-how-to-use-them"></a>인기 있는 CDNs 및 사용 방법

Microsoft의 Ajax CDN은 jQuery (및 기타 모든 라이브러리), ASP.NET Ajax, 부트스트랩, 녹아웃 .js 등을 비롯 한 대부분의 인기 있는 라이브러리를 제공 합니다.
  
이러한 스크립트를 프로젝트에 포함 하려면 해당 라이브러리에 대 한 참조를 프로젝트 자체에 포함 하지 말고 CDN 주소에 대 한 참조로 대체 하기만 하면 됩니다. 예를 들어 다음 코드를 사용 하 여 jQuery에 연결 합니다.
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

CDNs에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](content-delivery-networks.md)를 참조 하세요.
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>SharePoint에서 CDNs를 사용 하는 방법에 대 한 추가 항목

[Office 365 CDN에서 클라이언트 쪽 웹 파트 호스팅](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

