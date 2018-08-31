---
title: SharePoint Online의 축소 및 묶음
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: 이 문서에서는 HTTP 요청의 수를 줄일 수 및 SharePoint Online에서 페이지를 로드 하는데 걸리는 시간을 줄이는 축소 하 고 웹 Essentials 사용 하 여 기법을 묶음을 사용 하는 방법에 설명 합니다.
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541895"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>SharePoint Online의 축소 및 묶음

이 문서에서는 HTTP 요청의 수를 줄일 수 및 SharePoint Online에서 페이지를 로드 하는데 걸리는 시간을 줄이는 축소 하 고 웹 Essentials 사용 하 여 기법을 묶음을 사용 하는 방법에 설명 합니다.
  
웹 사이트를 사용자 지정할 때 사용자 지정을 지원하도록 서버에 많은 파일을 더 추가할 수 있습니다. 불필요한 JavaScript, CSS 및 이미지를 추가하면 서버에 대한 HTTP 요청 수가 늘어나 웹 페이지를 표시하는 데 걸리는 시간이 늘어납니다. 동일한 형식의 파일이 여러 개 있는 경우 이러한 파일을 묶어 더 빠르게 다운로드할 수 있습니다.
  
JavaScript 및 CSS 파일에 대 한 공백, 필요 하지 않은 다른 문자를 제거 하 여 파일의 전체 크기를 줄일 여기서 축소를 호출 하는 방법을 사용할 수도 있습니다.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Web Essentials에서 JavaScript 및 CSS 파일 축소 및 묶음

Web Essentials와 같은 타사 소프트웨어를 사용하여 CSS 및 JavaScript 파일을 묶을 수 있습니다.
  
> [!IMPORTANT]
> 웹 Essentials 제 3 자, 공개 소스, 커뮤니티 기반 프로젝트입니다. 소프트웨어는 Visual Studio 2012 및 Visual Studio 2013을 확장 하 고 Microsoft에서 지원 되지 않습니다. 웹 Essentials를 다운로드 하려면에서 웹사이트를 방문 [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)합니다. 
  
Web Essentials는 묶음을 다음과 같은 두 가지 형태로 제공합니다.
  
- .bundle: CSS 및 JavaScript 파일용
    
- .sprite: 이미지용(Visual Studio 2013에서만 사용 가능)
    
다음과 같이 사용자 지정 마스터 페이지 내에서 참조되는 일부 브랜딩 요소와 기존 기능을 사용하는 경우 Web Essentials를 사용할 수 있습니다.
  
![사용자 지정 마스터 페이지의 브랜드 요소 스크린샷](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **웹 Essentials에서 TE000127218 및 CSS 번들을 만들려면**
  
1. Visual Studio의 솔루션 탐색기에서 묶음에 포함할 파일을 선택합니다.
    
2. 선택한 파일을 마우스 오른쪽 단추로 클릭 한 다음 **웹 Essentials** 를 선택 \> 상황에 맞는 메뉴에서 **만들기 JavaScript 번들 파일** 입니다. 예를 들어: 
    
    ![Web Essentials 메뉴 옵션을 보여 주는 스크린샷](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>CSS 및 JavaScript 파일 묶음 결과 보기

CSS 및 JavaScript 번들 파일을 만들 때 Web Essentials는 JavaScript 및 CSS 파일과 일부 기타 구성 정보를 식별하는 조리법 파일이라는 XML 파일을 만듭니다. 
  
![JavaScript 및 CSS 조리법 파일의 스크린샷](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
또한 minify 플래그가 묶음 조리법에 true로 설정되어 있으면 파일 크기를 줄인 후 함께 묶습니다. 즉, 축소된 새 버전의 JavaScript 파일이 만들어지고 마스터 페이지에 참조할 수 있게 됩니다.
  
![true로 설정된 minify 플래그의 스크린샷](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
웹 사이트에서 페이지를 로드할 때 Internet Explorer 11과 같은 웹 브라우저에서 개발자 도구를 사용하여 서버로 전송된 요청 수와 각 파일을 로드하는 데 걸린 시간을 확인할 수 있습니다.
  
다음 그림은 축소 전에 JavaScript 및 CSS 파일을 로드한 결과입니다.
  
![다운로드되는 80가지 항목을 보여 주는 스크린샷](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
CSS 및 JavaScript 파일을 함께 묶은 후에는 요청 수가 74로 감소했으며 각 원본 파일을 따로 다운로드할 때보다 시간이 약간 더 소요되었습니다.
  
![다운로드되는 74가지 항목을 보여 주는 스크린샷](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
묶은 후에 JavaScript 번들 파일의 크기는 815KB에서 365KB로 크게 감소했습니다.
  
![감소된 다운로드 크기를 보여 주는 스크린샷](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>이미지 스프라이트를 만들어 이미지 묶기

와 마찬가지로 JavaScript 및 CSS 파일 번들 어떻게 있습니다 수 많은 작은 아이콘 및 기타 일반적인 이미지 더 큰 sprite 시트를 결합 하 고 CSS를 사용 하 여 개별 이미지를 표시 합니다. 각 개별 이미지를 다운로드 하는 대신 사용자의 웹 브라우저 한번 sprite 시트를 다운로드 하 고 로컬 컴퓨터에 캐시 합니다. 이 다운로드 및 웹 서버에 대 한 왕복 횟수에 아래로 가공 하 여 페이지 부하 성능이 향상 됩니다.
  
 **Web Essentials에서 이미지 스프라이트를 만들려면**
  
1. Visual Studio의 솔루션 탐색기에서 묶음에 포함할 파일을 선택합니다.
    
2. 선택한 파일을 마우스 오른쪽 단추로 클릭 한 다음 **웹 Essentials** 를 선택 \> 상황에 맞는 메뉴에서 **만들기 이미지 sprite** 합니다. 예를 들어: 
    
    ![이미지 스프라이트를 만드는 방법을 보여 주는 스크린샷](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. 스프라이트 파일이 저장될 위치를 선택합니다. .sprite 파일은 스프라이트의 파일 및 설정을 설명하는 XML 파일입니다. 다음 그림은 스프라이트 PNG 파일 및 해당 .sprite XML 파일의 예를 보여 줍니다.
    
    ![스프라이트 파일의 스크린샷](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![스프라이트 XML 파일의 스크린샷](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

