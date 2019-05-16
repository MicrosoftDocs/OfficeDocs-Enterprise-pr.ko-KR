---
title: SharePoint online에서 개체 캐시 사용
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 이 문서에서는 SharePoint Server 2013 온-프레미스 및 SharePoint Online에서 개체 캐시를 사용 하는 경우의 차이점에 대해 설명 합니다.
ms.openlocfilehash: 16805aee0c6c6828fc2bf81370046dfd0f1c5a70
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070544"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>SharePoint online에서 개체 캐시 사용

이 문서에서는 SharePoint Server 2013 온-프레미스 및 SharePoint Online에서 개체 캐시를 사용 하는 경우의 차이점에 대해 설명 합니다.
  
SharePoint Online 배포에서 개체 캐시에 의존 하는 것이 상당히 부정적으로 영향을 받습니다. SharePoint Online의 개체 캐시에 대 한 종속성은 페이지의 안정성을 줄입니다. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online 및 SharePoint Server 2013 개체 캐시의 작동 방식

SharePoint Server 2013이 온-프레미스에 호스트 되 면 고객에 게 개체 캐시를 호스트 하는 개인 프런트 엔드 웹 서버가 있는 것입니다. 즉, 캐시는 한 고객 전용으로 사용 가능 하며 개체 캐시에 할당 되는 메모리의 양에 의해서만 제한 됩니다. 온-프레미스 시나리오에서는 하나의 고객만 제공 되므로 프런트 엔드 웹 서버는 일반적으로 동일한 사이트에 대 한 요청을 수행 하 게 됩니다. 즉, 캐시가 빠르게 꽉 차서 사용자가 정기적으로 요청 하는 목록 쿼리 결과 및 SharePoint 개체의 전체 상태를 유지 합니다.
  
![온-프레미스 프런트 엔드 웹 서버에 대한 트래픽 및 로드 표시](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
따라서 사용자가 페이지를 두 번 방문 하면 페이지 로드 시간이 빨라집니다. 동일한 페이지를 네 번 이상 로드 한 후에는 페이지가 모든 프런트 엔드 웹 서버에 캐시 됩니다.
  
반면 SharePoint Online에는 더 많은 서버 뿐만 아니라 더 많은 사이트가 있습니다. 각 사용자는 캐시가 채워지지 않은 다른 프런트 엔드 웹 서버에 연결할 수 있습니다. 또는 캐시가 서버에 대해 채워지면 해당 프런트 엔드 웹 서버에 대 한 다음 사용자가 다른 사이트의 페이지를 요청 합니다. 또는 다음 사용자가 이전에 방문 했을 때와 동일한 페이지를 요청 하는 경우에도 해당 페이지가 캐시에 없는 다른 프런트 엔드 웹 서버에 로드 균형이 조정 됩니다. 이 마지막 경우에는 캐싱이 사용자에 게 도움이 되지 않습니다.
  
다음 그림에서 각 점은 사용자가 요청 하는 페이지와 캐시 되는 위치를 나타냅니다. 다양 한 색은 SaaS 인프라를 공유 하는 여러 고객을 나타냅니다.
  
![SharePoint Online의 개체 캐시 결과 표시](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
다이어그램에서 볼 수 있듯이 해당 페이지의 캐시 된 버전을 사용 하 여 특정 사용자가 서버를 방문 하는 것은 슬림 합니다. 또한 많은 사이트 간에 서버를 공유 하는 처리량이 많기 때문에 캐시에 사용 가능한 캐싱 공간이 충분 하기 때문에 캐시가 오래 지속 되지 않았습니다.
  
이러한 모든 이유로, 캐시 된 개체를 가져오는 사용자에 게 작업을 수행 하는 것은 SharePoint Online에서 품질 사용자 환경 및 페이지 로드 시간을 효과적으로 보장할 수 없습니다.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>SharePoint Online에서 성능을 향상 시키기 위해 개체 캐시에 의존할 수 없는 경우에는 어떤 작업을 대신 사용 하나요?

SharePoint Online의 캐싱에 의존해 서는 안 되므로, 개체 캐시를 사용 하는 SharePoint 사용자 지정에 대 한 대체 디자인 방식을 평가 해야 합니다. 즉, 사용자에 게 좋은 결과를 생성 하기 위해 개체 캐싱을 사용 하지 않는 성능 문제에 대 한 접근 방식을 사용 합니다. 이 작업은이 시리즈의 다른 문서에 설명 되어 있으며 다음을 포함 합니다.
  
- [SharePoint Online에 대 한 탐색 옵션](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online의 축소 및 묶음](minification-and-bundling-in-sharepoint-online.md)
    
- [콘텐츠 배달 네트워크 사용](using-content-delivery-networks-with-sharepoint-online.md)
    
- [SharePoint Online에서 이미지 및 JavaScript 로드 지연](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

