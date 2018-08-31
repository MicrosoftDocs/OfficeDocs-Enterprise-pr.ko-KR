---
title: SharePoint Online에 대한 이미지 최적화
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: SharePoint Online 웹 사이트에서 이미지 성능을 향상 시키기 위해 변환 및 스프라이트를 사용 하는 방법에 알아봅니다.
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541930"
---
# <a name="image-optimization-for-sharepoint-online"></a>SharePoint Online에 대한 이미지 최적화

웹 페이지 로드 속도 이미지, HTML, JavaScript, 및 CSS를 포함 하 여 페이지를 렌더링 하는 데 필요한 모든 구성 요소의 조합된 크기에 따라 달라 집니다. 이미지 보다 매력적 사이트를 만들 수 있는 뛰어난 방식 있지만 크기가 성능에 영향을 줄 수 있습니다. 압축 및 크기 조정, 및 스프라이트를 사용 하 여 사용 하 여 이미지를 최적화 하 여 매우 큰 이미지의 효과 오프셋할 수 있습니다. SharePoint 이미지 변환을 사용 하 여 단일 큰 이미지를 업로드할 수 있으며 다시 로드 하지 않고 다시 사용할 수 있도록 이미지의 섹션을 표시할 수도 있습니다.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>스프라이트를 사용하여 SharePoint Online의 이미지 로드 속도 향상

|||
|:-----|:-----|
| 이미지 sprite 많은 작은 이미지를 포함합니다. CSS를 사용 하 여 복합 절대 위치를 지정 된 페이지의 특정 부분에 표시할 이미지의 부분을 선택 합니다. 기본적으로, 여러 이미지를 로드 하는 대신 페이지 주위에 단일 이미지를 이동 하 고 확인 최종 사용자에 게 sprite 이미지의 필수 부분을 표시할 위치에 작은 창을 통해 해당 이미지의 작은 부분을 표시 합니다. SharePoint Online를 사용 하 여 스프라이트 sprite spcommon.png에는 다양 한 아이콘을 표시 합니다.  <br/>  기능 여기에서 설명 됩니다.  <br/>  이미지 압축  <br/>  이미지 최적화  <br/>  SharePoint 이미지 변환  <br/> |![Spcommon의 스크린샷](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
이렇게 하는 대신 여러 하나만 이미지를 다운로드 하 고 다음 캐시 및 해당 이미지를 다시 사용 하기 때문에 성능이 향상. 여러 이미지 대신 단일 이미지를 하 여 이미지를 캐시, 유지 되지 않습니다, 하는 경우에이 메서드는 페이지 로드 시간을 줄일 수 있는 서버에는 HTTP 요청의 총 수를 줄입니다. 이 실제로 이미지 번들 형태의 합니다. 이것이 매우 유용한 기술의 이미지를 변경 하지 자주, 예: 아이콘 위에 제공 되는 SharePoint 예제와 같이입니다. [웹 Essentials](http://vswebessentials.com/), Microsoft Visual Studio에서이 작업을 쉽게 달성 하기 위해 제 3 자, 공개 소스, 커뮤니티 기반 프로젝트를 사용 하는 방법을 할 수 있습니다. 자세한 내용은 [축소 하 고 SharePoint Online에서 묶음](https://go.microsoft.com/fwlink/?LinkId=708698)을 참조 하십시오.
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>SharePoint에서 이미지 압축 및 최적화를 사용하여 페이지 로드 속도 향상

이미지 압축 및 최적화는 사이트에서 사용하는 이미지의 파일 크기를 줄이는 방법입니다. 경우에 따라 이미지의 크기를 줄이는 가장 좋은 방법은 이미지를 사이트에서 볼 수 있는 최대 크기로 조정하는 것입니다. 기존의 크기보다 더 크게 이미지를 만들 필요는 없습니다. 이미지 편집기를 사용하여 이미지를 적합한 크기로 유지하는 것이 페이지의 크기를 줄일 수 있는 빠르고 쉬운 방법입니다.
  
이미지는 오른쪽 크기, 되 면 다음 단계에서는 이러한 이미지의 압축을 최적화 하는 것입니다. 다양 한 도구 압축 및 최적화, 사진 갤러리 및 타사 도구를 포함 하 여 사용 하 여 사용할 수 있습니다. 압축 하는 최종 사용자에 대 한 모든 식별할 수 있는 품질을 유지 하면서 최대한 활용 하는 파일 크기를 줄일 수입니다. 압축 된 파일은 여전히 좋은 찾습니다 되도록 고화질 디스플레이에 테스트 있는지 확인 하십시오.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>SharePoint 이미지 변환 기능을 사용하여 페이지 다운로드 속도 향상

이미지 변환은 SharePoint online 서로 다른 버전의 미리 정의 된 이미지 크기에 따라 이미지를 처리할 수 있도록 하는 기능입니다. 이것은 사용자가 생성 이미지 콘텐츠 또는 이미지 크기 너비와 높이 같은 사이트에서 CSS를 통해 해결 하는 경우에 특히 중요 합니다. CSS에 의해 수정 되는 이미지를 하는 경우에 전체 해상도 이미지는 여전히 로드 됩니다. 이 경우 이미지 변환을 사용 하 여 파일 크기를 줄일 수 있습니다.
  
> [!NOTE]
> 변환은 게시 사용 하는 경우에 SharePoint에 사용할 수 있습니다. 설정 아래에서 게시를 사용 하도록 설정할 수 \> 사이트 설정 \> 사이트 기능 관리 \> SharePoint Server 게시 합니다. 옵션은 그렇지 않은 경우 표시 되지 않습니다. 
  
이미지 변환 기능을 사용하면 정의한 가장 작은 너비 또는 높이를 가져온 다음, 고정된 가로 세로 비율에 따라 다른 크기가 자동으로 조정됩니다. 기본적으로 나머지 크기에 따라 중심으로부터 이미지가 잘립니다. 예를 들어 100px(너비). 50px(높이)인 변환을 정의하며 원래 이미지가 1000px(너비), 800px(높이)인 경우 800px 크기가 50px이 되고, 1000px(현재 62.5px)이 이미지의 중심으로부터 잘립니다.
  
이러한 단계는 비교적 간단하지만 이미지에서 변환을 사용하려면 이미지를 추가하기 전에 SharePoint 사이트에 변환이 미리 준비되어 있어야 합니다. 또한 SharePoint Server 게시 인프라(사이트 모음 수준) 및 SharePoint Server 게시(사이트 수준) 기능이 설정되어 있어야 합니다.
  
 **페이지 로드 속도 이미지 변환 추가**
  
1. 이 절차를 수행 하는 사용자 계정에 있는지, 여기에 최소한 사이트 모음의 최상위 사이트에 대 한 디자인 권한이 하 고 사이트를 웹 페이지로 게시 되는 확인 합니다.
    
2. 웹 브라우저에서 게시 사이트 모음의 최상위 사이트로 이동합니다.
    
3. **설정** 아이콘을 선택합니다. 
    
4. **사이트 설정** 페이지의 **디자인** 섹션에 기본 제공 이미지 변환이 표시됩니다. 
    
    기본 변환을 사용하거나 **이미지 변환**을 선택하여 새로 만들 수 있습니다. 
    
    ![이미지 변환의 스크린샷](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. **이미지 변환** 페이지에서 **새 항목 추가**를 선택합니다.
    
    ![새 항목 추가를 보여 주는 스크린샷](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. **새 이미지 변환** 페이지의 **이름** 상자에 변환의 이름을 입력합니다. 
    
7. **너비** 및 **높이** 텍스트 상자에 변환의 너비 및 높이를 픽셀 단위로 입력한 다음 **저장**을 선택합니다.
    
    ![이미지 변환 이름을 보여 주는 스크린샷](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>SharePoint에서 이미지 변환을 사용한 사용자 지정 자르기

기본적으로 이미지 변환의 이미지를 중앙에서 생성 됩니다. 사용 하려는 이미지의 부분 잘라서 개별 이미지에 대 한 이미지 변환을 조정할 수 있습니다. 변환 당는 개인별로 이미지를 자를 수 있습니다. 이미지 자르기 속도가 향상 페이지를 각 변환에 대 한 이미지의 버전을 만들려면 SharePoint의 blob 캐시를 사용 하 여 로드 됩니다. 이미지만 크기를 조정할 한번 이며 최종 사용자에 게 여러 번 처리 하기 위해 준비 다음 때문에 이러한 방식으로 서버 부하가 감소 됩니다. 자르려면 이미지 변환 하는 방법에 대 한 자세한 내용은 [이미지 변환 자르려면](https://go.microsoft.com/fwlink/p/?LinkId=525626)을 참조 하십시오.
  

