---
title: SharePoint Online의 축소 및 묶음
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: 이 문서에서는 웹 Essentials에서 축소 및 묶음 기법을 사용 하 여 HTTP 요청 수를 줄이고 SharePoint Online에서 페이지를 로드 하는 데 걸리는 시간을 줄이기 위한 방법을 설명 합니다.
ms.openlocfilehash: d73bc6cc86ea1ea4ecba5395f22a20befdc64b13
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070264"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>SharePoint Online의 축소 및 묶음

이 문서에서는 웹 Essentials에서 축소 및 묶음 기법을 사용 하 여 HTTP 요청 수를 줄이고 SharePoint Online에서 페이지를 로드 하는 데 걸리는 시간을 줄이기 위한 방법을 설명 합니다.
  
웹 사이트를 사용자 지정 하는 경우 사용자 지정을 지원 하기 위해 서버에 많은 수의 추가 파일을 추가할 수 있습니다. JavaScript, CSS 및 이미지를 추가 하면 서버에 대 한 HTTP 요청 수가 증가 하 여 웹 페이지를 표시 하는 데 소요 되는 시간이 길어집니다. 유형이 같은 파일이 여러 개 있는 경우 이러한 파일을 묶어 파일을 보다 빠르게 다운로드할 수 있습니다.
  
JavaScript 및 CSS 파일의 경우에는 공백 및 기타 필요 하지 않은 문자를 제거 하 여 전체 파일 크기를 줄이는 축소 방식으로 사용할 수도 있습니다.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Web Essentials를 사용 하 여 JavaScript 및 CSS 파일 축소 및 묶음

Web Essentials와 같은 타사 소프트웨어를 사용 하 여 CSS 및 JavaScript 파일을 묶을 수 있습니다.
  
> [!IMPORTANT]
> Web Essentials는 타사의 오픈 소스, 커뮤니티 기반 프로젝트입니다. 이 소프트웨어는 Visual Studio 2012 및 Visual Studio 2013의 확장 이며 Microsoft에서 지원 되지 않습니다. Web Essentials를 다운로드 하려면에서 [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)웹 사이트를 방문 하세요. 
  
Web Essentials에서는 다음과 같은 두 가지 형태의 번들을 제공 합니다.
  
- . 번들: CSS 및 JavaScript 파일용
    
- 스프라이트: 이미지 (Visual Studio 2013 에서만 사용 가능)
    
다음과 같이 사용자 지정 마스터 페이지 내에서 참조 되는 일부 브랜딩 요소와 기존 기능이 있는 경우 Web Essentials를 사용할 수 있습니다.
  
![사용자 지정 마스터 페이지의 브랜드 요소 스크린샷](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Web Essentials에서 TE000127218 및 CSS 번들을 만들려면**
  
1. Visual Studio의 솔루션 탐색기에서 번들에 포함할 파일을 선택 합니다.
    
2. 선택한 파일을 마우스 오른쪽 단추로 클릭 한 다음 상황에 맞는 메뉴에서 **Web Essentials** \> **Create JavaScript 번들 파일** 을 선택 합니다. 예를 들면 다음과 같습니다. 
    
    ![Web Essentials 메뉴 옵션을 보여 주는 스크린샷](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>번들 JavaScript 및 CSS 파일 묶음 결과 보기

JavaScript 및 CSS 번들을 만들 때 Web Essentials에서는 JavaScript 및 CSS 파일 뿐만 아니라 기타 구성 정보도 식별 하는 조리법 파일 이라는 XML 파일을 만듭니다. 
  
![JavaScript 및 CSS 조리법 파일의 스크린샷](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
또한 번들 레 서 피에서가 나 플래그를 true로 설정 하면 파일 크기가 축소 되 고 함께 번들로 제공 됩니다. 즉, 마스터 페이지에서 참조할 수 있는 새로운 버전의 JavaScript 파일이 생성 되었습니다.
  
![true로 설정된 minify 플래그의 스크린샷](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
웹 사이트에서 페이지를 로드할 때 Internet Explorer 11과 같은 웹 브라우저에서 개발자 도구를 사용 하 여 서버로 전송 된 요청 수와 각 파일을 로드 하는 데 걸린 시간을 확인할 수 있습니다.
  
다음 그림은 축소 전에 JavaScript 및 CSS 파일을 로드 한 결과입니다.
  
![다운로드되는 80가지 항목을 보여 주는 스크린샷](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
CSS 및 JavaScript 파일을 함께 묶음 한 후에는 요청 수가 74 개까지 손실 되 고 각 파일에 개별적으로 다운로드 하기 위한 원본 파일 보다 약간 더 오래 걸렸습니다.
  
![다운로드되는 74가지 항목을 보여 주는 스크린샷](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
번들을 만든 후 JavaScript 번들 파일은 815KB에서 365KB로 크게 줄어듭니다.
  
![감소된 다운로드 크기를 보여 주는 스크린샷](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>이미지 스프라이트를 만들어 이미지 묶음

JavaScript 및 CSS 파일을 묶는 방법과 마찬가지로, 여러 개의 작은 아이콘 및 기타 일반 이미지를 큰 스프라이트 시트에 결합 한 다음 CSS를 사용 하 여 개별 이미지를 표시할 수 있습니다. 사용자의 웹 브라우저에서 개별 이미지를 다운로드 하는 대신 스프라이트 시트를 한 번 다운로드 한 다음 로컬 컴퓨터에 캐시 합니다. 이를 통해 웹 서버로의 다운로드 및 라운드트립 횟수를 줄여서 페이지 로드 성능을 향상 시킬 수 있습니다.
  
 **Web Essentials에서 이미지 스프라이트를 만들려면**
  
1. Visual Studio의 솔루션 탐색기에서 번들에 포함할 파일을 선택 합니다.
    
2. 선택한 파일을 마우스 오른쪽 단추로 클릭 한 다음 상황에 맞는 메뉴에서 **Web Essentials** \> **만들기 이미지 스프라이트** 를 선택 합니다. 예를 들면 다음과 같습니다. 
    
    ![이미지 스프라이트를 만드는 방법을 보여 주는 스크린샷](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. 스프라이트 파일을 저장할 위치를 선택 합니다. Sprite 파일은 스프라이트의 설정 및 파일을 설명 하는 XML 파일입니다. 다음 그림에서는 스프라이트 PNG 파일 및 해당 스프라이트 XML 파일의 예를 보여 줍니다.
    
    ![스프라이트 파일의 스크린샷](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![스프라이트 XML 파일의 스크린샷](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

