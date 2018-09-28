---
title: SharePoint online에서 개체 캐시 사용
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 이 문서에서는 SharePoint Server 2013 온-프레미스 및 SharePoint Online에서 개체 캐시를 사용 하 여 간의 차이 설명 합니다.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 7cd210c44622ea2de5fb0e8e91c7be4839c80205
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2018
ms.locfileid: "24056167"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>SharePoint online에서 개체 캐시 사용

이 문서에서는 SharePoint Server 2013 온-프레미스 및 SharePoint Online에서 개체 캐시를 사용 하 여 간의 차이 설명 합니다.
  
SharePoint Online 배포에서 개체 캐시에 의존할 경우 큰 문제가 발생합니다. SharePoint Online에서 개체 캐시에 의존하면 페이지의 안정성이 떨어집니다. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online 및 SharePoint Server 2013 개체 캐시의 작동 방식

호스팅된 온-프레미스 SharePoint Server 2013을 사용 하는 경우 고객 개체 캐시를 호스트 하는 개인 프런트엔드 웹 서버에 있습니다. 즉, 캐시 한 고객 전용 하 고만 사용 가능 하 고 개체 캐시에 할당 된 메모리의 양을에 의해 제한 됩니다. 온-프레미스 시나리오에서 하나만 고객을 처리 하기 때문에 프런트엔드 웹 서버는 일반적으로 반복 해 동일한 사이트에 요청을 수행 하는 사용자를 가집니다. 즉, 캐시 전체 신속 하 게 가져옵니다 목록 쿼리 결과 주기적으로 사용자에 게 요청 하는 SharePoint 개체의 전체 유지 되도록 합니다.
  
![온-프레미스 프런트 엔드 웹 서버에 대한 트래픽 및 로드 표시](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
결과적으로 사용자가 페이지를 두 번째로 방문하면 페이지 로드 시간이 줄어듭니다. 같은 페이지가 최소 네 번 로드되면 페이지는 모든 프런트 엔드 웹 서버에서 캐시됩니다.
  
반면, SharePoint Online는 서버를 더 많은 하지만 더 많은 사이트에도 있습니다. 각 사용자 채워진 캐시를 갖고 있지 않은 다른 프런트엔드 웹 서버에 연결할 수 있습니다. 한 서버에 대 한 캐시는 자동으로 입력 아마도 또는 하지만 해당 프런트엔드 웹 서버에는 다음 사용자는 다른 사이트에서 페이지를 요청 합니다. 또는 다음 사용자가 같은 페이지에 자신의 이전 방문할 때를 요청 하는 경우에 해당 페이지의 캐시에 없는 다른 프런트엔드 웹 서버에 부하 분산 된 것이 있습니다. 이 지난 경우 캐싱 (영문) 되지 않습니다 사용자 전혀 도움이 됩니다.
  
다음 그림에서 각 점은 사용자가 요청을 하고 캐시되는 페이지를 나타냅니다. SaaS 인프라를 공유하여 사용하는 여러 다른 고객이 다른 색상으로 표시되어 있습니다.
  
![SharePoint Online의 개체 캐시 결과 표시](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
다이어그램에서 볼 수 있듯이 해당 페이지의 캐시 된 버전으로 서버를 방문 하는 특정된 사용자의 경우 가능성 많지 않습니다. 또한 큰 처리량과 서버 다 수의 사이트 간에 공유 되는 팩트,으로 인해 사용 가능한 캐싱 (영문)에 대 한 보다 공간에만 있기 때문에 긴 캐시 지속 되지 않습니다.
  
이러한 모든 이유로, 캐시된 개체를 가져오는 사용자에게 의존하는 방식은 SharePoint Online에서 좋은 사용자 환경과 적절한 페이지 로드 시간을 유지할 수 있는 효과적인 방법이 아닙니다.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>SharePoint Online에서 성능을 향상시키기 위해 개체 캐시에 의존할 수 없다면 대신 어떤 작업을 수행해야 합니까?

SharePoint Online에서 캐싱에 의존할 수 없다면 개체 캐시를 사용하는 SharePoint 사용자 지정을 위한 대체 디자인 접근 방식을 평가해야 합니다. 즉, 개체 캐싱에 의존하지 않으면서 사용자에게 적합한 결과를 줄 수 있는 성능 향상을 위한 접근 방법을 찾아야 합니다. 이 내용은 본 시리즈의 다른 일부 문서에 나와 있으며 다음 정보를 제공합니다.
  
- [SharePoint Online에 대한 탐색 옵션](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online의 축소 및 묶음](minification-and-bundling-in-sharepoint-online.md)
    
- [콘텐츠 배달 네트워크 사용](using-content-delivery-networks-with-sharepoint-online.md)
    
- [SharePoint Online에서 이미지 및 JavaScript 로드 지연](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

