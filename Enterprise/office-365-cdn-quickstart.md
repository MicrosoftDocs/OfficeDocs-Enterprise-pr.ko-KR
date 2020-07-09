---
title: Office 365 CDN (콘텐츠 배달 네트워크) 빠른 시작
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 CDN (콘텐츠 배달 네트워크) 빠른 시작
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561928"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 CDN (콘텐츠 배달 네트워크) 빠른 시작

기본 제공 **Office 365 CDN (콘텐츠 배달 네트워크** )을 사용 하 여 정적 자산 (이미지, JavaScript, 스타일 시트, woff 파일)을 호스트 하 여 SharePoint Online 페이지의 성능을 향상 시킬 수 있습니다. Office 365 CDN은 정적 자산을 요청하는 브라우저에 더 가깝게 캐싱하여 성능을 향상시켜 다운로드 속도를 높이고 대기 시간을 줄이는 데 기여합니다. 또한 Office 365 CDN은 향상 된 압축 및 HTTP 파이프라이닝을 위해 HTTP/2 프로토콜을 사용 합니다. Office 365 CDN 서비스는 SharePoint Online 구독의 일부로 포함되어 있습니다.

자세한 내용은 [Use The Office 365 CDN (Content Delivery Network) With SharePoint Online을](use-office-365-cdn-with-spo.md)참조 하세요.

>[!NOTE]
>Office 365 CDN은 프로덕션 (전 세계) 클라우드의 테 넌 트에만 사용할 수 있습니다. 미국 정부의 테 넌 트, 중국 및 독일 클라우드가 현재 Office 365 CDN을 지원 하지 않습니다.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>SharePoint 도구를 사용 하 여 CDN에 없는 항목을 식별 하는 페이지 진단

SharePoint 도구 브라우저 확장 **의 페이지 진단을** 사용 하 여 CDN 원본에 추가할 수 있는 sharepoint Online 페이지의 자산을 쉽게 나열할 수 있습니다.

**Sharepoint 용 페이지 진단 도구** 는 새 Microsoft Edge ( https://www.microsoft.com/edge) 및 sharepoint Online 최신 포털 및 클래식 게시 사이트 페이지 모두를 분석 하는 크롬 브라우저)에 대 한 브라우저 확장입니다. 이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다. Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](https://aka.ms/perftool)을 참조하세요.

SharePoint Online 페이지에서 SharePoint 용 페이지 진단 도구를 실행 하는 경우 **진단 테스트** 탭을 클릭 하 여 CDN에서 호스팅하지 않는 자산의 목록을 확인할 수 있습니다. 이러한 자산은 아래 스크린샷에 표시 된 대로 제목 **CDN (콘텐츠 배달 네트워크) 검사** 아래에 나열 됩니다.

![페이지 진단](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>페이지 진단 도구는 SharePoint Online에서만 사용할 수 있으며 SharePoint 시스템 페이지에서는 사용할 수 없습니다.

## <a name="cdn-overview"></a>CDN 개요

Office 365 CDN은 고속 글로벌 네트워크를 통해 이미지 및 javascript 파일 같은 자주 액세스 하는 개체를 배포 하 여 페이지 로드 시간을 줄이고 호스트 된 개체에 대 한 액세스 권한을 사용자에 게 제공 하 여 사용자의 성능을 최적화 하도록 디자인 되었습니다. CDN은 _근원_이라는 위치에서 자산을 페치합니다. 원본은 URL에서 액세스할 수 있는 SharePoint 사이트, 문서 라이브러리 또는 폴더가 될 수도 있습니다.

Office 365 CDN은 다음과 같은 두 가지 기본 형식으로 구분 됩니다.

- **공용 CDN** 은 JS (JavaScript), CSS (스타일 시트), 웹 글꼴 파일 (woff, WOFF2) 및 회사 로고와 같은 비 소유 이미지에 사용 하도록 설계 되었습니다.
- **PRIVATE CDN** 은 이미지 (PNG, JPG, JPEG 등)에 사용 하도록 설계 되었습니다.

조직의 공용 또는 개인 원본을 둘 다 사용할 수 있습니다. 대부분의 조직에서는 두 가지를 조합 하 여 구현 합니다. 공용 및 개인 옵션은 모두 비슷한 성능을 제공 하지만 각각에 고유한 특성 및 이점이 있습니다. 공용 및 개인 CDN 원본에 대 한 자세한 내용은 [각 출처를 public 또는 private로 지정](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)을 참조 하세요.

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>기본 구성으로 공용 및 개인 CDN을 사용 하도록 설정 하는 방법
테 넌 트 CDN 설정을 변경 하기 전에 조직의 준수, 보안 및 개인 정보 취급 방침을 충족 하는지 확인 해야 합니다.

보다 자세한 구성 설정에 대 한 자세한 내용을 설명 하거나 CDN을 이미 사용 하도록 설정한 상태에서 추가 위치 (원본)를 추가 하려면 [SharePoint Online 관리 셸을 사용 하 여 Office 365 CDN 설정 및 구성](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell) 섹션을 참조 하세요.

SharePoint Online 관리 셸을 사용 하 여 테 넌 트에 연결 합니다.

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

조직이 기본 구성으로 공용 및 개인 원본을 모두 사용 하도록 설정 하려면 다음 명령을 입력 합니다.

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

이러한 cmdlet의 출력은 다음과 같습니다.

![SPOTenantCdnEnabled의 출력](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>참고 항목

[SharePoint Online 용 페이지 진단 도구 사용](https://aka.ms/perftool)

[sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기](use-office-365-cdn-with-spo.md)

[콘텐츠 배달 네트워크](https://aka.ms/o365cdns)

[Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)

[SharePoint 성능 시리즈-Office 365 CDN 비디오 시리즈](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
