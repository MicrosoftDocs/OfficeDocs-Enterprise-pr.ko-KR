---
title: sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Office 365 CDN (콘텐츠 배달 네트워크)을 사용 하 여 위치에 관계 없이 모든 사용자에 게 SharePoint Online 자산을 빠르게 배달 하는 방법에 대해 설명 하 고 콘텐츠에 액세스 하는 방법을 알아봅니다.
ms.openlocfilehash: ffb464b31a5f5a87a09334e2c5f7ae3c3027af65
ms.sourcegitcommit: 77a25920511c54d7d613f552bdff7ad14cdd8324
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2019
ms.locfileid: "36385196"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기

기본 제공 Office 365 Content Delivery Network(CDN)을 사용하여 정적 자산을 호스팅하여 SharePoint Online 페이지의 성능을 향상시킬 수 있습니다. Office 365 CDN은 정적 자산을 요청하는 브라우저에 더 가깝게 캐싱하여 성능을 향상시켜 다운로드 속도를 높이고 대기 시간을 줄이는 데 기여합니다. 또한 Office 365 CDN은 향상 된 압축 및 HTTP 파이프라이닝을 위해 [http/2 프로토콜](https://en.wikipedia.org/wiki/HTTP/2) 을 사용 합니다. Office 365 CDN 서비스는 SharePoint Online 구독의 일부로 포함되어 있습니다.

> [!NOTE]
> Office 365 CDN 사용에 대 한 제한 사항:
> + Office 365 CDN은 **프로덕션** (전 세계) 클라우드의 테 넌 트에만 사용할 수 있습니다. 미국 정부의 테 넌 트, 중국 및 독일 클라우드가 현재 Office 365 CDN을 지원 하지 않습니다.
> + Office 365 CDN에서는 현재 사용자 지정 또는 "베 니 티" 도메인을 사용 하 여 구성 된 테 넌 트를 지원 하지 않습니다. Office [365에 도메인 추가](https://docs.microsoft.com/en-us/office365/admin/setup/add-domain?view=o365-worldwide)항목에 나와 있는 지침을 사용 하 여 office 365 테 넌 트에서 구성 요소에 도메인을 추가한 경우에는 CDN의 콘텐츠에 액세스 하려고 할 때 OFFICE 365 CDN에서 오류를 반환 합니다.

Office 365 CDN은 여러 위치, 즉 _출발지_에 정적 자산을 호스트하고 글로벌 고속 네트워크에서 제공할 수 있는 여러 CDN으로 구성됩니다. Office 365 CDN에서 호스팅하려는 콘텐츠의 종류에 따라 **공개** 출처, **비공개** 출처 또는 둘 다를 추가할 수 있습니다. Public 및 private 원점과의 차이점에 대 한 자세한 내용은 [각 원점을 public 또는 private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) 중에서 선택 합니다 .를 참조 하세요.

![Office 365 CDN 개념 다이어그램] (media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 개념 다이어그램")

CDNs가 작동 하는 방식에 이미 익숙한 경우 테 넌 트에 Office 365 CDN을 사용 하도록 설정 하려면 몇 단계만 완료 하면 됩니다. 이 항목에서는 방법에 대해 설명 합니다. 정적 자산 호스팅을 시작 하는 방법에 대 한 자세한 내용을 확인 하세요.

> [!TIP]
> 특수 사용 시나리오에서는 Office 365와 함께 사용할 수 있는 Microsoft에서 호스팅하는 다른 CDNs가 있지만,이 항목에서는 Office 365 CDN 범위를 벗어나므로 여기서 설명 하지 않습니다. 자세한 내용은 [다른 Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns)를 참조 하세요.

 **[Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)으로 돌아갑니다.**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>SharePoint Online에서 Office 365 CDN 사용에 대 한 개요

조직에 대해 Office 365 CDN을 설정 하려면 다음 기본 단계를 수행 합니다.

- [Office 365 CDN 배포 계획](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - [CDN에서 호스트할 정적 자산을 결정](use-office-365-cdn-with-spo.md#CDNAssets)합니다.
  - [자산을 저장할 위치를 결정](use-office-365-cdn-with-spo.md#CDNStoreAssets)합니다. 이 위치는 SharePoint 사이트, 라이브러리 또는 폴더 일 수 있으며 _출처_라고 합니다.
  - [각 원본이 공용 또는 개인 인지 여부를 선택](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)합니다. 공용 및 개인 형식 둘 다의 원본을 여러 개 추가할 수 있습니다.

- PowerShell 또는 SharePoint Online CLI를 사용 하 여 CDN을 설정 하 고 구성 합니다.

  - [SharePoint Online 관리 셸을 사용 하 여 CDN을 설정 하 고 구성 합니다.](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [Office 365 CLI를 사용 하 여 CDN을 설정 하 고 구성 합니다.](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  이 단계를 완료 하면 다음이 수행 됩니다.

  - 조직에 CDN을 사용 하도록 설정 합니다.
  - 각 원점을 공용 또는 개인으로 식별 하는 출처를 추가 했습니다.

설치를 완료 한 후에는 시간에 따른 [Office 365 CDN을 관리할](use-office-365-cdn-with-spo.md#CDNManage) 수 있습니다.
  
- 자산 추가, 업데이트 및 제거
- 원본 추가 및 제거
- CDN 정책 구성
- 필요한 경우 CDN을 사용 하지 않도록 설정

마지막으로, [cdn 자산을 사용](use-office-365-cdn-with-spo.md#using-your-cdn-assets) 하 여 공용 및 개인 원본 모두에서 cdn 자산에 액세스 하는 방법에 대해 알아보세요.

일반적인 문제를 해결 하는 방법에 대 한 지침은 [Office 365 CDN 문제 해결](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 을 참조 하세요.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Office 365 CDN 배포 계획

Office 365 테 넌 트에 대 한 Office 365 CDN을 배포 하기 전에 계획 프로세스의 일부로 다음과 같은 요인을 고려해 야 합니다.

  - [CDN에서 호스트할 정적 자산 확인](use-office-365-cdn-with-spo.md#CDNAssets)
  - [자산을 저장할 위치 결정](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [각 출처를 public 또는 private로 설정할지를 선택 합니다.](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>CDN에서 호스트할 정적 자산 확인
<a name="CDNAssets"> </a>

일반적으로 CDNs는 _정적 자산_을 호스트 하거나 자주 변경 되지 않는 자산을 호스팅하는 데 가장 효과적입니다. 다음과 같은 조건 중 일부 또는 전부를 충족 하는 파일을 식별 하는 것이 좋습니다.

- 페이지 로드 시간에 큰 영향을 줄 수 있는 페이지 (스크립트 및 이미지 등)에 포함 된 정적 파일
- 실행 파일 및 설치 파일과 같은 큰 파일
- 스트리밍 미디어 파일
- 클라이언트 쪽 코드를 지 원하는 리소스 라이브러리

예를 들어 사이트 이미지 및 스크립트와 마찬가지로 반복적으로 요청 되는 작은 파일은 사이트 렌더링 성능을 크게 향상 시키고, CDN 원본에 추가 하는 경우 SharePoint Online 사이트의 부하를 점차적으로 줄일 수 있습니다. 설치 실행 파일이 나 비디오 파일과 같은 더 큰 파일을 CDN에서 다운로드 하거나 스트리밍할 수 있으므로, 자주 액세스 하지 않더라도 SharePoint Online 사이트에 대 한 부하를 긍정적으로 줄이는 것이 좋습니다.

파일을 기준으로 성능 향상은 가장 가까운 CDN 끝점에 대 한 클라이언트의 근접성, 로컬 네트워크의 일시적 조건 등의 다양 한 요인에 따라 달라 집니다. 많은 정적 파일은 매우 작으며 Office 365에서 1 초 이내에 다운로드할 수 있습니다. 그러나 웹 페이지에는 다운로드 시간이 누적 되는 여러 개의 포함 된 파일이 몇 초 동안 포함 될 수 있습니다. CDN에서 이러한 파일을 처리 하면 전체 페이지 로드 시간이 크게 줄어들 수 있습니다. [CDN에서 제공 하는 성능 향상은 무엇 인가요?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) 예를 참조 하세요.

### <a name="determine-where-you-want-to-store-your-assets"></a>자산을 저장할 위치 결정
<a name="CDNStoreAssets"> </a>

CDN은 _근원_이라는 위치에서 자산을 페치합니다. 원본은 URL에서 액세스할 수 있는 SharePoint 사이트, 문서 라이브러리 또는 폴더가 될 수도 있습니다. 조직의 원본을 지정할 때 유연성이 뛰어납니다. 예를 들어 모든 CDN 자산을 추가 하려는 원본이 여러 개 있거나 하나만 지정할 수 있습니다. 조직의 공용 또는 개인 원본을 둘 다 사용할 수 있습니다. 대부분의 조직에서는 두 가지를 조합 하 여 구현 합니다.

폴더 또는 문서 라이브러리와 같은 원본에 대 한 새 컨테이너를 만들고 CDN에서 사용 가능 하도록 설정할 파일을 추가할 수 있습니다. CDN에서 사용 하려는 특정 자산의 집합이 있고 CDN 자산 집합을 컨테이너의 해당 파일로 제한 하려는 경우에는이 방법이 좋은 방법입니다.

기존 사이트 모음, 사이트, 라이브러리 또는 폴더를 원본으로 구성 하 여 해당 컨테이너의 모든 적합 한 자산을 CDN에서 사용할 수 있도록 할 수도 있습니다. 기존 컨테이너를 원본으로 추가 하기 전에 익명 액세스 또는 권한 없는 사용자에 게 자산을 실수로 노출 하지 않도록 하기 위해 해당 콘텐츠 및 사용 권한을 알고 있는지 확인 하는 것이 중요 합니다.

Cdn에서 원본에 있는 콘텐츠를 제외 하도록 _cdn 정책을_ 정의할 수 있습니다. CDN 정책은 공용 또는 개인 원본에서 _파일 형식_ 및 _사이트 분류_와 같은 특성을 통해 자산을 제외 하 고, 정책에 지정 하는 cdntype (private 또는 public)의 모든 원본에 적용 됩니다. 예를 들어 여러 하위 사이트가 포함 된 사이트로 구성 된 개인 출처를 추가 하는 경우 해당 분류가 적용 된 사이트의 콘텐츠가 CDN에서 처리 되지 않도록 **비밀 우편** 으로 표시 된 사이트를 제외 하는 정책을 정의할 수 있습니다. 정책은 CDN에 추가한 _모든_ 개인 출처의 콘텐츠에 적용 됩니다.
  
원본 수가 많을 수록 CDN 서비스에서 요청을 처리 하는 데 소요 되는 시간에 더 많은 영향을 줍니다. 원본 수를 가능한 한 많이 제한 하는 것이 좋습니다.
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>각 출처를 public 또는 private로 설정할지를 선택 합니다.
<a name="CDNOriginChoosePublicPrivate"> </a>

출처를 식별할 때는 _공용_ 또는 _비공개로_설정할 지 여부를 지정 합니다. 공용 원본에서 CDN 자산에 대 한 액세스는 익명으로 진행 되며 개인 원본에 있는 CDN 콘텐츠는 보안을 강화 하기 위해 동적으로 생성 된 토큰에 의해 보호 됩니다. 선택 하는 옵션에 관계 없이 Microsoft는 CDN 자체를 관리 하는 경우 모든 사용자를 대상으로 합니다. 또한 CDN을 설정 하 고 원본을 식별 한 후 나중에 생각이 바뀔 수 있습니다.

공용 및 개인 옵션은 모두 비슷한 성능을 제공 하지만 각각에 고유한 특성 및 이점이 있습니다.

Office 365 CDN 내의 **공용** 원본에는 익명으로 액세스할 수 있으며 자산에 대 한 URL을 가진 모든 사용자가 호스트 된 자산에 액세스 하는 데 도움이 됩니다. 공개 출처의 콘텐츠에 대한 액세스는 익명이기 때문에 캐시 javascript 파일, 스크립트, 아이콘 및 이미지와 같은 중요하지 않은 일반 콘텐츠에만 사용할 수 있습니다.

Office 365 CDN의 **비공개** 출처는 SharePoint Online 문서 라이브러리, 사이트 및 비디오와 같은 미디어와 같은 사용자 콘텐츠에 대한 비공개 액세스를 제공합니다. 원본 문서 라이브러리나 저장 위치에 대 한 사용 권한이 있는 사용자만 액세스할 수 있도록 개인 원본의 콘텐츠에 대 한 액세스를 동적으로 생성 된 토큰으로 보호 합니다. Office 365 CDN의 비공개 출처는 SharePoint Online 콘텐츠에만 사용할 수 있으며, SharePoint Online 테 넌 트에서 리디렉션을 통해서만 개인 원본에 있는 자산에만 액세스할 수 있습니다.

비공개 원본의 자산에 대 한 CDN 액세스에 대 한 자세한 내용은 전용 원본 [에 자산 사용](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)에서 작업을 참조 하세요.

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>공개 원본에서의 자산 호스팅 특성 및 장점
  
- 공용 원본에 표시 되는 자산은 모든 사용자가 익명으로 액세스할 수 있습니다.
    > [!IMPORTANT]
    > 사용자 정보가 포함 된 리소스를 배치 하거나 조직에서 공용 원본으로 중요 한 것으로 간주 해서는 안 됩니다.
- 공개 원점에서 자산을 제거 하는 경우에는 해당 자산을 캐시에서 최대 30 일 동안 계속 사용할 수 있습니다. 그러나 15 분 내에 CDN의 자산에 대 한 링크가 무효화 됩니다.
- 공용 원점에 스타일 시트 (CSS 파일)를 호스트 하는 경우 코드 내에 상대 경로와 Uri를 사용할 수 있습니다. 즉, 배경 이미지 및 다른 개체를 호출 하는 자산의 위치를 기준으로 해당 위치를 참조할 수 있습니다.
- 공용 원본의 URL을 하드 코딩 하는 것은 좋지만, 이렇게 하지 않는 것이 좋습니다. 이는 CDN에 대 한 액세스를 사용할 수 없는 경우 URL이 SharePoint Online에서 조직에 자동으로 확인 되지 않으며 링크 및 기타 오류가 발생할 수 있기 때문입니다.
- 공용 원본에 대해 포함 되는 기본 파일 형식은 .css, eot, .gif, .ico, .jpeg, .jpg,. ttf 및. w o v,. p s v,. 추가 파일 형식을 지정할 수 있습니다.
- 지정한 사이트 분류에 의해 식별 된 자산을 제외 하도록 정책을 구성할 수 있습니다. 예를 들어, 허용 되는 파일 형식이 고 공용 원본에 있는 경우에도 "기밀" 또는 "제한"으로 표시 된 모든 자산을 제외 하도록 선택할 수 있습니다.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>전용 원본에서의 자산 호스팅의 특성 및 장점

- 비공개 출처는 SharePoint Online 자산에만 사용할 수 있습니다.
- 사용자는 컨테이너에 대 한 액세스 권한이 있는 경우에만 비공개 원본의 자산에 액세스할 수 있습니다. 이러한 자산에 대 한 익명 액세스는 차단 됩니다.
- 개인 원본에 있는 자산은 SharePoint Online 테 넌 트에서 참조 해야 합니다. 사설 CDN 자산에 직접 액세스할 수 없습니다.
- 비공개 원본에서 자산을 제거 하는 경우에는 자산을 캐시에서 한 시간까지 계속 사용할 수 있습니다. 그러나 자산의 제거 후 15 분 이내에 CDN의 자산에 대 한 링크가 무효화 됩니다.
- 전용 원본에 대해 포함 되는 기본 파일 형식은 .gif, .ico, .jpeg, .jpg, .js 및 .png입니다. 추가 파일 형식을 지정할 수 있습니다.
- 공용 출처와 마찬가지로 와일드 카드를 사용 하 여 폴더 또는 문서 라이브러리 내의 모든 자산을 포함 하는 경우에도 사용자가 지정한 사이트 분류에 의해 식별 된 자산을 제외 하도록 정책을 구성할 수 있습니다.

Office 365 CDN, 일반 CDN 개념 및 Office 365 테 넌 트에서 사용할 수 있는 기타 Microsoft CDNs를 사용 하는 이유에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](content-delivery-networks.md)를 참조 하세요.

### <a name="default-cdn-origins"></a>기본 CDN 원본

별도로 지정 하지 않으면 office 365에서 Office 365 CDN을 사용 하도록 설정할 때 기본 원본을 설정 합니다. 처음에 프로 비전 하지 않을 경우에는 설치를 완료 한 후 이러한 원본을 추가할 수 있습니다. 기본 원본에 대 한 설정을 건너뛰고이를 수행 하는 특별 한 이유가 있는 경우를 이해 하지 않으면 CDN을 사용 하도록 설정할 때이 설정의 생성을 허용 해야 합니다.
  
기본 개인 CDN 원본:
  
- \*/userphoto.aspx
- \*/cusets

기본 공용 CDN 원본:
  
- \*/masterpage
- \*/restyle 라이브러리
- \*/reclient자산과 자산

> [!NOTE]
> _clientsideassets_ 12 월 2017에 OFFICE 365 CDN 서비스에 추가 된 기본 공용 원본입니다. CDN에서 SharePoint Framework 솔루션이 작동 하려면이 원본이 있어야 합니다. Office 365 CDN을 12 월 2017 이전에 사용 하도록 설정 했거나 CDN을 사용 하도록 설정 했을 때 기본 원본 설치를 건너뛴 경우이 원본을 수동으로 추가할 수 있습니다. 자세한 내용은 [내 클라이언트 쪽 웹 파트 또는 SharePoint Framework 솔루션이 작동 하지 않는](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)경우를 참조 하세요.

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>SharePoint Online 관리 셸을 사용 하 여 Office 365 CDN을 설정 하 고 구성 합니다.
<a name="CDNSetupinPShell"> </a>

이 섹션의 절차를 수행 하려면 SharePoint Online 관리 셸을 사용 하 여 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [SharePoint Online PowerShell에 연결을](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)참조 하세요.
  
Sharepoint online 관리 셸을 사용 하 여 SharePoint Online에서 자산을 호스트 하도록 CDN을 설정 및 구성 하려면 다음 단계를 완료 합니다.
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>조직이 Office 365 CDN을 사용 하도록 설정

테 넌 트 CDN 설정을 변경 하기 전에 Office 365 테 넌 트에서 개인 CDN 구성의 현재 상태를 검색 해야 합니다. SharePoint Online 관리 셸을 사용 하 여 테 넌 트에 연결 합니다.

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

이제 **SPOTenantCdnEnabled** cmdlet을 사용 하 여 테 넌 트에서 CDN 상태 설정을 검색 합니다.

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

지정한 CdnType에 대 한 CDN의 상태가 화면에 출력 됩니다.

**SPOTenantCdnEnabled** cmdlet을 사용 하 여 조직에서 OFFICE 365 CDN을 사용 하도록 설정할 수 있습니다. 조직이 공용 원본, 전용 원본 또는 두 가지 모두를 한 번에 사용 하도록 설정할 수 있습니다. 또한이 기능을 사용 하도록 설정 하면 기본 원본 설정을 건너뛰도록 CDN을 구성할 수 있습니다. 이 항목의 설명에 따라 나중에 이러한 원본을 언제 든 지 추가할 수 있습니다.
  
SharePoint Online 용 Windows Powershell:

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

예를 들어 조직에서 공용 및 개인 원본을 둘 다 사용할 수 있도록 설정 하려면 다음 명령을 입력 합니다.

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

조직이 공용 및 개인 원본을 모두 사용할 수 있도록 설정 하 고 기본 원본을 설정 하지 않으려면 다음 명령을 입력 합니다.

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Office 365 CDN을 사용 하도록 설정 하는 경우 기본적으로 프로 비전 되는 원본에 대 한 정보 및 기본 원본 설정을 건너뛰는 경우 발생할 수 있는 영향에 대 한 자세한 내용은 [DEFAULT CDN 원본임](use-office-365-cdn-with-spo.md#default-cdn-origins) 을 참조 하십시오.

조직에서 공용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

조직에서 전용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

이 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)를 참조 하십시오.
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Office 365 CDN에 포함할 파일 형식 목록 변경 (선택 사항)
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> **SPOTenantCdnPolicy** cmdlet을 사용 하 여 파일 형식을 정의 하는 경우 현재 정의 된 목록을 덮어씁니다. 목록에 다른 파일 형식을 추가 하려면 먼저 cmdlet을 사용 하 여 이미 허용 된 파일 형식을 확인 하 여 새 파일과 함께 목록에 포함 시킵니다.
  
**SPOTenantCdnPolicy** cmdlet을 사용 하 여 CDN에서 공용 및 전용 원본으로 호스팅할 수 있는 정적 파일 형식을 정의 합니다. 기본적으로 일반 에셋 유형 (예: .css, .gif, .jpg, .js)을 사용할 수 있습니다.

SharePoint Online 용 Windows PowerShell:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

예를 들어 CDN에서 .css 및 .png 파일을 호스팅할 수 있도록 설정 하려면 다음 명령을 입력 합니다.

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

CDN에서 현재 허용 되는 파일 형식을 확인 하려면 **SPOTenantCdnPolicies** cmdlet을 사용 합니다.

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

이러한 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 및 [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)를 참조 하십시오.
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Office 365 CDN에서 제외 하려는 사이트 분류 목록 변경 (선택 사항)
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> **SPOTenantCdnPolicy** cmdlet을 사용 하 여 사이트 분류를 제외 하는 경우 현재 정의 된 목록을 덮어씁니다. 추가 사이트 분류를 제외 하려면 먼저 cmdlet을 사용 하 여 이미 제외 된 분류를 확인 한 다음 새 항목과 함께 추가 합니다.

**SPOTenantCdnPolicy** cmdlet을 사용 하 여 CDN을 통해 사용 하지 않도록 설정할 사이트 분류를 제외 합니다. 기본적으로 사이트 분류는 제외 되지 않습니다.

SharePoint Online 용 Windows PowerShell:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

현재 제한 된 사이트 분류를 확인 하려면 **SPOTenantCdnPolicies** cmdlet을 사용 합니다.

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

반환 되는 속성은 _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ 및 _excludeifnoscriptdisabled_입니다.

_IncludeFileExtensions_ 속성에는 CDN에서 처리할 파일 확장명 목록이 포함 됩니다.

> [!NOTE]
> 기본 파일 확장명은 public 및 private과 다릅니다.

_ExcludeRestrictedSiteClassifications_ 속성은 CDN에서 제외 하려는 사이트 분류를 포함 합니다. 예를 들어 해당 분류가 적용 된 사이트의 콘텐츠가 CDN에서 처리 되지 않도록 **비밀 우편** 으로 표시 된 사이트를 제외할 수 있습니다.

_Excludeifnoscriptdisabled_ 속성은 사이트 수준 _noscript_ 특성 설정에 따라 CDN에서 콘텐츠를 제외 합니다. 기본적으로 _최신_ 사이트에는 _Noscript_ 특성이 **사용** 으로 설정 되 고 _클래식_ 사이트에는 사용 **되지** 않습니다. 이것은 테 넌 트 설정에 따라 다릅니다.

이러한 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 및 [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)를 참조 하십시오.
  
### <a name="add-an-origin-for-your-assets"></a>자산에 대 한 근원 추가
<a name="Office365CDNforSPOOrigin"> </a>

**SPOTenantCdnOrigin** cmdlet을 사용 하면 원점을 정의할 수 있습니다. 여러 원본을 정의할 수 있습니다. 원점은 CDN에서 호스팅할 자산이 포함 된 SharePoint 라이브러리 또는 폴더를 가리키는 URL입니다.
  
> [!IMPORTANT]
> 사용자 정보가 포함 된 리소스를 배치 하거나 조직에서 공용 원본으로 중요 한 것으로 간주 해서는 안 됩니다.

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Path_ 값은 자산이 포함 된 라이브러리 또는 폴더에 대 한 상대 경로입니다. 상대 경로 외에도 와일드 카드를 사용할 수 있습니다. 원본 URL 앞에는 와일드 카드를 지원 합니다. 이를 통해 여러 사이트에 걸쳐 있는 원본을 만들 수 있습니다. 예를 들어 모든 사이트에 대 한 masterpages 폴더의 모든 자산을 CDN 내의 공용 근원으로 포함 하려면 다음 명령을 입력 합니다.

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- 와일드 카드 수정자 ***/** 는 경로의 시작 부분 에서만 사용할 수 있으며 지정 된 url의 모든 URL 세그먼트와 일치 합니다.
- 경로는 문서 라이브러리, 폴더 또는 사이트를 가리킬 수 있습니다. 예를 들어 경로 _*/site1_ 은 사이트 아래의 모든 문서 라이브러리와 일치 합니다.

특정 상대 경로를 사용 하 여 원본을 추가할 수 있습니다. 전체 경로를 사용 하 여 원점을 추가할 수는 없습니다.

이 예제에서는 특정 사이트에 siteassets 라이브러리의 개인 출처를 추가 합니다.

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

이 예제에서는 사이트 모음의 사이트 자산 라이브러리에 _folder1_ 폴더의 개인 출처를 추가 합니다.

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

경로에 공백이 있으면 경로를 큰따옴표로 묶고 URL 인코딩% 20로 공간을 바꿀 수 있습니다. 다음은 사이트 모음의 사이트 자산 라이브러리에서 _폴더 1_ 폴더의 개인 출처를 추가 하는 예제입니다.

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.

> [!NOTE]
> 비공개 원본의 경우 원본에서 공유 되는 자산은 CDN에서 액세스 하려면 먼저 주 버전을 게시 해야 합니다.
  
명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다. 최대 15 분까지 소요 될 수 있습니다.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>예: 마스터 페이지에 대 한 공용 원점과 SharePoint Online에 대 한 스타일 라이브러리에 대해 구성
<a name="ExamplePublicOrigin"> </a>

일반적으로 이러한 출처는 Office 365 CDN을 사용 하도록 설정 하면 기본적으로 설정 됩니다. 그러나 수동으로 사용 하도록 설정 하려는 경우 다음 단계를 수행 합니다.
  
- **SPOTenantCdnOrigin** cmdlet을 사용 하면 스타일 라이브러리를 공용 원점으로 정의할 수 있습니다.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- **SPOTenantCdnOrigin** cmdlet을 사용 하면 마스터 페이지를 공공 원점으로 정의할 수 있습니다.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.

명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다. 최대 15 분까지 소요 될 수 있습니다.

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>예: SharePoint Online에 대 한 사이트 자산, 사이트 페이지 및 게시 이미지에 대 한 개인 출처 구성
<a name="ExamplePrivateOrigin"> </a>

- **SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 자산 폴더를 전용 원본으로 정의할 수 있습니다.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- **SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 페이지 폴더를 전용 원본으로 정의할 수 있습니다.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- **SPOTenantCdnOrigin** cmdlet을 사용 하면 게시 이미지 폴더를 전용 원본으로 정의할 수 있습니다.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.

명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다. 최대 15 분까지 소요 될 수 있습니다.

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>예: SharePoint Online에 대 한 사이트 모음에 대 한 개인 원본 구성
<a name="ExamplePrivateOriginSiteCollection"> </a>

**SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 모음을 전용 원본으로 정의할 수 있습니다. 예를 들면 다음과 같습니다.

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.
  
명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다. SharePoint Online 테 넌 트가 CDN 서비스에 연결할 때 예상 되는 _구성 보류 중인_ 메시지가 표시 될 수 있습니다. 최대 15 분까지 소요 될 수 있습니다.

### <a name="manage-the-office-365-cdn"></a>Office 365 CDN 관리
<a name="CDNManage"> </a>

CDN을 설정한 후에는이 섹션에 설명 된 대로 콘텐츠를 업데이트 하거나 필요에 따라 변경 하 여 구성을 변경할 수 있습니다.
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Office 365 CDN에서 자산 추가, 업데이트 또는 제거
<a name="Office365CDNforSPOaddremoveasset"> </a>

설정 단계를 완료 한 후에는 새 자산을 추가 하 고 원할 때마다 기존 자산을 업데이트 하거나 제거할 수 있습니다. 폴더 또는 SharePoint 라이브러리에서 원본으로 식별 한 자산을 변경 하기만 하면 됩니다. 새 자산을 추가 하는 경우에는 CDN을 통해 즉시 사용할 수 있습니다. 그러나 자산을 업데이트 하는 경우 새 복사본을 전파 하 고 CDN에서 사용할 수 있게 되는 데 최대 15 분이 걸립니다.
  
원본 위치를 검색 해야 하는 경우 **SPOTenantCdnOrigins** cmdlet을 사용할 수 있습니다. 이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)를 참조 하십시오.
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Office 365 CDN에서 원본 제거
<a name="Office365CDNforSPORemoveOrigin"> </a>

원본으로 식별 한 폴더 또는 SharePoint 라이브러리에 대 한 액세스 권한을 제거할 수 있습니다. 이 작업을 수행 하려면 **SPOTenantCdnOrigin** cmdlet을 사용 합니다.

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)를 참조 하십시오.
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Office 365 CDN에서 원본 수정
<a name="Office365CDNforSPORemoveOrigin"> </a>

만든 출처는 수정할 수 없습니다. 대신 원점을 제거한 다음 새 원본을 추가 합니다. 자세한 내용은 [Office 365 CDN에서 출처를 제거](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) 하 고 [자산의 출처를 추가](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)하는 방법을 참조 하세요.
  
#### <a name="disable-the-office-365-cdn"></a>Office 365 CDN 사용 안 함
<a name="Office365CDNforSPODisable"> </a>

**SPOTenantCdnEnabled** cmdlet을 사용 하 여 조직에 CDN을 사용 하지 않도록 설정 합니다. CDN에 대 한 공용 및 전용 원본을 모두 사용 하는 경우에는 다음 예제와 같이 cmdlet을 두 번 실행 해야 합니다.
  
CDN에서 public 원본임을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

CDN에서 비공개 원본을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

이 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)를 참조 하십시오.

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>Office 365 CLI를 사용 하 여 Office 365 CDN을 설정 하 고 구성 합니다.
<a name="CDNSetupinCLI"> </a>

이 섹션의 절차에서는 [Office 365 CLI](https://aka.ms/o365cli)를 설치 해야 합니다. 다음으로, [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) 명령을 사용 하 여 SharePoint Online 테 넌 트에 연결 합니다.

Office 365 CLI를 사용 하 여 SharePoint Online에서 자산을 호스트 하도록 CDN을 설정 및 구성 하려면 다음 단계를 완료 합니다.

### <a name="enable-the-office-365-cdn"></a>Office 365 CDN 사용

[Spo CDN set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) 명령을 사용 하 여 테 넌 트에서 OFFICE 365 CDN의 상태를 관리할 수 있습니다.

테 넌 트에서 실행 되는 Office 365 공용 CDN을 사용 하도록 설정 하려면 다음을 수행 합니다.

```sh
spo cdn set --type Public --enabled true
```

Office 365 SharePoint CDN을 사용 하도록 설정 하려면 다음을 실행 합니다.

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Office 365 CDN의 현재 상태를 확인 합니다.

특정 유형의 Office 365 CDN을 사용 하거나 사용 하지 않도록 설정할지 여부를 확인 하려면 [spo CDN get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) 명령을 사용 합니다.

Office 365 공용 CDN이 사용 하도록 설정 되어 있는지 확인 하려면 다음을 실행 합니다.

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Office 365 CDN 원본 보기

현재 구성 된 Office 365 공용 CDN 원본을 실행 하려면 다음을 확인 합니다.

```sh
spo cdn origin list --type Public
```

Office 365 CDN을 사용 하도록 설정 하는 경우 기본적으로 프로 비전 되는 원본에 대 한 자세한 내용은 [DEFAULT CDN 원본을](use-office-365-cdn-with-spo.md#default-cdn-origins) 참조 하십시오.

### <a name="add-an-office-365-cdn-origin"></a>Office 365 CDN 원본 추가

> [!IMPORTANT]
> 조직에 중요 한 것으로 간주 되는 리소스를 공공 근원으로 구성 된 SharePoint 문서 라이브러리에 배치 해서는 안 됩니다.

[Spo cdn 원본 add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) 명령을 사용 하 여 cdn 원본을 정의 합니다. 여러 원본을 정의할 수 있습니다. 원점은 CDN에서 호스팅할 자산이 포함 된 SharePoint 라이브러리 또는 폴더를 가리키는 URL입니다.

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

여기서 `path` 은 자산이 포함 된 폴더에 대 한 상대 경로입니다. 상대 경로 외에도 와일드 카드를 사용할 수 있습니다.

모든 사이트의 **마스터 페이지 갤러리** 에 있는 모든 자산을 공용 원점으로 포함 하려면 다음을 실행 합니다.

```sh
spo cdn origin add --type Public --origin */masterpage
```

특정 사이트 모음에 대 한 개인 원점을 구성 하려면 다음을 실행 합니다.

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> CDN 원본을 추가한 후에는 CDN 서비스를 통해 파일을 검색 하는 데 최대 15 분까지 걸릴 수 있습니다. [Spo cdn 원본 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 명령을 사용 하 여 특정 원본이 이미 사용 하도록 설정 되었는지 여부를 확인할 수 있습니다.

### <a name="remove-an-office-365-cdn-origin"></a>Office 365 CDN 원본 제거

[Spo cdn 원본 제거](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) 명령을 사용 하 여 지정 된 cdn 유형에 대해 cdn 원본을 제거 합니다.

CDN 구성에서 공용 원점을 제거 하려면 다음을 실행 합니다.

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> CDN 원본을 제거 해도 해당 원본과 일치 하는 문서 라이브러리에 저장 된 파일에는 영향을 주지 않습니다. 이러한 자산이 SharePoint URL을 사용 하 여 참조 된 경우 SharePoint는 문서 라이브러리를 가리키는 원래 URL로 자동 전환 됩니다. 그러나 공용 CDN URL을 사용 하 여 자산이 참조 된 경우에는 원본을 제거 하면 링크가 끊어지고 수동으로 변경 해야 합니다.

### <a name="modify-an-office-365-cdn-origin"></a>Office 365 CDN 원본 수정

기존 CDN 원본을 수정할 수 없습니다. 대신 `spo cdn origin remove` 명령을 사용 하 여 이전에 정의 된 CDN 원본을 제거 하 고 `spo cdn origin add` 명령을 사용 하 여 새로 추가 해야 합니다.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Office 365 CDN에 포함할 파일 형식 변경

기본적으로 CDN에는 다음 파일 형식이 포함 됩니다. _.css, eot, .gif, .ico, .jpeg, .jpg_,. p s t,. w o v,. ttf,. CDN에 추가 파일 형식을 포함 해야 하는 경우에는 [spo cdn 정책 set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 명령을 사용 하 여 cdn 구성을 변경할 수 있습니다.

> [!NOTE]
> 파일 형식 목록을 변경할 때 현재 정의 된 목록을 덮어씁니다. 추가 파일 형식을 포함 하려면 먼저 [spo cdn 정책 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 명령을 사용 하 여 현재 구성 되어 있는 파일 형식을 확인 합니다.

공용 CDN에 포함 된 파일 형식의 기본 목록에 _JSON_ 파일 형식을 추가 하려면 다음을 실행 합니다.

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Office 365 CDN에서 제외 하려는 사이트 분류 목록 변경

[Spo cdn 정책 설정](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 명령을 사용 하 여 cdn을 통해 사용 하지 않으려는 사이트 분류를 제외 합니다. 기본적으로 사이트 분류는 제외 되지 않습니다.

> [!NOTE]
> 제외 된 사이트 분류 목록을 변경할 때 현재 정의 된 목록을 덮어씁니다. 추가 분류를 제외 하려면 먼저 [spo cdn 정책 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) 명령을 사용 하 여 현재 구성 된 분류를 확인 합니다.

_HBI_ 으로 분류 된 사이트를 공용 CDN에서 제외 하려면 다음을 실행 합니다.

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Office 365 CDN 사용 안 함

Office 365 CDN을 사용 하지 않도록 설정 `spo cdn set` 하려면 다음과 같이 명령을 사용 합니다.

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a>CDN 자산 사용

CDN 및 구성 된 원본 및 정책을 사용 하도록 설정 했으므로 이제 CDN 자산 사용을 시작할 수 있습니다.

이 섹션에서는 SharePoint에서 공용 및 사설 원본 모두에 대 한 요청을 CDN으로 리디렉션하는 SharePoint 페이지 및 콘텐츠에서 CDN Url을 사용 하는 방법을 이해 하는 데 도움이 됩니다.

- [CDN 자산에 대 한 링크 업데이트](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [공개 원본에서 에셋 사용](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [비공개 원본에서 에셋 사용](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

클라이언트 쪽 웹 파트 호스팅을 위해 CDN을 사용 하는 방법에 대 한 자세한 내용은 [Office 365 CDN (Hello World part 4)에서 클라이언트 쪽 웹 파트 호스트](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)항목을 참조 하십시오.

### <a name="updating-links-to-cdn-assets"></a>CDN 자산에 대 한 링크 업데이트

원본에 추가한 자산을 사용 하려면 원본의 파일 경로를 사용 하 여 원본 파일에 대 한 링크를 업데이트 하기만 하면 됩니다.

- 출처에 추가한 자산에 대 한 링크를 포함 하는 페이지 또는 콘텐츠를 편집 합니다. 또한 여러 방법 중 하나를 사용 하 여 지정 된 자산에 대 한 링크를 전역으로 검색 하 고 바꿀 수 있습니다.
- 원본의 자산에 대 한 각 링크에 대해 경로를 CDN 원본에 있는 파일의 경로로 바꿉니다. 상대 경로를 사용할 수 있습니다.
- 페이지 또는 콘텐츠를 저장 합니다.

예를 들어 문서 라이브러리 폴더 _/site/CDN_origins/public/_ 로 복사한 이미지 _/site/SiteAssets/images/image.png_을 고려해 보십시오. CDN 자산을 사용 하려면 이미지 파일 위치의 원래 경로를 원본 경로와 함께 바꿔 새 URL _/site/CDN_origins/public/image.png_합니다.

상대 경로 대신 자산에 대 한 전체 URL을 사용 하려면 다음과 같이 링크를 구성 합니다.

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> 일반적으로 CDN의 자산에 Url을 직접 하드 코딩 해서는 안 됩니다. 그러나 필요한 경우 공개 원본에서 자산에 대 한 Url을 수동으로 생성할 수 있습니다. 자세한 내용은 [공용 자산의 하드 코딩 CDN url](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets)을 참조 하세요.

CDN에서 자산이 제공 되 고 있는지 확인 하는 방법에 대 한 자세한 내용은 How the [Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 섹션의 ["cdn에서 자산이 제공 되 고 있는지 확인 하는 방법은 무엇입니까?"](use-office-365-cdn-with-spo.md#CDNConfirm) 를 참조 하십시오.

### <a name="using-assets-in-public-origins"></a>공개 원본에서 에셋 사용

SharePoint Online의 **게시 기능은** SHAREPOINT 대신 cdn 서비스에서 자산이 제공 되도록 공용 원본에 저장 된 자산의 url을 해당 cdn에 맞게 자동으로 다시 씁니다.

원본이 게시 기능이 사용 하도록 설정 된 사이트에 있고 CDN에 대해 오프 로드 하려는 자산이 다음 범주 중 하나에 포함 되어 있는 경우 SharePoint에서는 자산이 CDN에서 제외 된 경우에는 원본의 자산에 대 한 Url을 자동으로 다시 씁니다.  정책.

다음은 SharePoint 게시 기능에 의해 자동으로 다시 작성 되는 링크에 대 한 간략 한 설명입니다.

- 클래식 게시 페이지의 HTML 응답에 있는 IMG/LINK/CSS Url
  - 여기에는 페이지의 HTML 콘텐츠 내에서 제작자가 추가한 이미지가 포함 됩니다.
- 그림 라이브러리 슬라이드 쇼 웹 파트 이미지 Url
- RenderListDataAsStream (SPList REST API)의 이미지 필드 결과
  - 새 속성 _Imagefieldstotryrewritetocdnurls_ 을 사용 하 여 쉼표로 구분 된 필드 목록을 제공 합니다.
  - 하이퍼링크 필드 및 PublishingImage 필드 지원
- SharePoint 이미지 변환

다음 다이어그램에서는 SharePoint가 공용 원본의 자산을 포함 하는 페이지에 대 한 요청을 수신 하는 경우의 워크플로를 보여 줍니다.

![워크플로 다이어그램: 공용 원본의 Office 365 CDN 자산 검색] (media/O365-CDN/o365-cdn-public-steps-transparent.svg "워크플로: 공용 원본에서 Office 365 CDN 자산을 검색 하는 경우")

> [!TIP]
> 페이지의 특정 Url에 대해 자동 다시 쓰기를 사용 하지 않도록 설정 하려는 경우 페이지를 체크 아웃 하 고 쿼리 문자열 매개 변수를 추가할 수 있습니다. ** **사용 하지 않도록 설정할 각 링크의 끝에 NoAutoReWrites = true를 입력 합니다.

#### <a name="hardcoding-cdn-urls-for-public-assets"></a>공용 자산의 CDN Url을 하드 코딩 합니다.

공개 원점에 대해 _게시_ 기능을 사용할 수 없거나 자산이 cdn 서비스의 자동 재작성 기능에서 지 원하는 링크 형식 중 하나가 아닌 경우에는 자산의 cdn 위치에 대 한 url을 수동으로 구성 하 고 콘텐츠에 이러한 url을 사용할 수 있습니다.

> [!NOTE]
> URL의 마지막 섹션을 구성 하는 데 필요한 액세스 토큰이 리소스를 요청할 때 생성 되므로 비공개 원본의 자산에 CDN Url을 하드 제거할 수 없습니다.

공용 CDN 자산의 경우 URL 형식이 다음과 같이 표시 됩니다.

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**TenantHostName** 을 테 넌 트 이름으로 바꿉니다. 예제:

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a>비공개 원본에서 에셋 사용

비공개 원본에서 자산을 사용 하는 데에는 추가 구성이 필요 하지 않습니다. SharePoint Online은 개인 원본에 있는 자산의 Url을 자동으로 다시 씁니다. 이러한 자산에 대 한 요청은 항상 CDN에서 처리 됩니다. 자산을 요청 하는 경우에는 SharePoint Online에서 자동으로 생성 해야 하는 토큰이 포함 되기 때문에 이러한 Url에는 개인 원본에서 CDN 자산에 대 한 Url을 수동으로 빌드할 수 없습니다.

비공개 원본의 자산에 대 한 액세스는 원본에 대 한 사용자 권한 및 다음 섹션에서 설명 하는 주의 사항에 따라 동적으로 생성 된 토큰으로 보호 됩니다. 사용자에 게는 CDN에서 콘텐츠를 렌더링 하기 위한 **읽기** 이상의 원본 액세스 권한이 있어야 합니다.

다음 다이어그램에서는 SharePoint가 비공개 원본의 자산을 포함 하는 페이지에 대 한 요청을 수신 하는 경우의 워크플로를 보여 줍니다.

![워크플로 다이어그램: 비공개 원본의 Office 365 CDN 자산 검색] (media/O365-CDN/o365-cdn-private-steps-transparent.svg "워크플로: 비공개 원본의 Office 365 CDN 자산 검색")

#### <a name="token-based-authorization-in-private-origins"></a>전용 원본에서의 토큰 기반 권한 부여

Office 365 CDN의 비공개 원본에 있는 자산에 대 한 액세스는 SharePoint Online에서 생성 된 토큰에 의해 부여 됩니다. 원본에서 지정한 폴더나 라이브러리에 대 한 액세스 권한이 이미 있는 사용자에 게는 사용자가 자신의 사용 권한 수준에 따라 파일에 액세스할 수 있도록 허용 하는 토큰이 자동으로 부여 됩니다. 이러한 액세스 토큰은 토큰 재생 공격을 방지 하기 위해 생성 된 30 ~ 90 분에 유효 합니다.

액세스 토큰이 생성 되 면 SharePoint Online에서 클라이언트에 대 한 사용자 지정 URI 두 개 (edge 인증 __ 토큰)와 _oat_ (원본 인증 토큰)을 함께 반환 합니다. 각 토큰의 구조는 _< ' >__< ' 보안 서명 ' >' 만료 시간 '으로 지정 _됩니다. 예를 들면 다음과 같습니다.

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> 토큰을 소유 하는 모든 사용자가 CDN의 리소스에 액세스할 수 있습니다. 그러나 이러한 액세스 토큰을 포함 하는 Url은 HTTPS를 통해서만 공유 되므로 토큰이 만료 되기 전에 최종 사용자가 URL을 명시적으로 공유 하지 않으면 권한이 없는 사용자가 해당 자산에 액세스할 수 없습니다.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>비공개 원본에 있는 자산에 대해서는 항목 수준 권한이 지원 되지 않습니다.

SharePoint Online은 전용 원본에 있는 자산에 대 한 항목 수준 권한을 지원 하지 않는다는 점에 유의 해야 합니다. 예를 들어에 `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`있는 파일의 경우 사용자는 다음 조건에 해당 하는 파일에 대 한 유효한 액세스 권한을 갖습니다.

|사용자  |사용 권한  |유효한 액세스  |
|---------|---------|---------|
|사용자 1     |Folder1에 대 한 액세스 권한         |CDN에서 image1에 액세스할 수 있음         |
|사용자 2     |Folder1에 대 한 액세스 권한이 없음         |CDN에서 image1에 액세스할 수 없음         |
|사용자 3     |Folder1에 대 한 액세스 권한이 없지만 SharePoint Online에서 image1에 액세스할 수 있는 권한이 명시적으로 부여 됩니다.         |SharePoint Online에서 직접 자산 image1에 액세스할 수 있으 나 CDN에서 액세스 가능         |
|사용자 4     |Folder1에 대 한 액세스 권한이 있지만 SharePoint Online에서 image1에 대 한 액세스 권한이 명시적으로 거부 되었습니다.         |SharePoint Online에서 자산에 액세스할 수는 없지만 SharePoint Online에서 파일에 대 한 액세스가 거부 되더라도 CDN에서 자산에 액세스할 수 있습니다.         |

## <a name="troubleshooting-the-office-365-cdn"></a>Office 365 CDN 문제 해결
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>CDN에서 자산을 제공 하는지 확인 하려면 어떻게 해야 합니까?
<a name="CDNConfirm"> </a>

페이지에 CDN 자산의 링크를 추가한 후에는 해당 페이지로 이동 하 고 이미지를 렌더링 하 고 이미지 URL을 검토 한 후에 해당 페이지를 마우스 오른쪽 단추로 클릭 하 여 해당 자산이 CDN에서 처리 되 고 있는지 확인할 수 있습니다.

또한 브라우저의 개발자 도구를 사용 하 여 페이지에서 각 자산의 URL을 보거나 타사 네트워크 추적 도구를 사용할 수 있습니다.

> [!NOTE]
> Fiddler와 같은 네트워크 도구를 사용 하 여 SharePoint 페이지에서 자산을 렌더링 하지 않는 사용자의 자산을 테스트 하는 경우 URL이 SharePoint Online 테 넌 트의 `https://yourdomain.sharepoint.com`루트 URL 인 GET 요청에 참조 페이지 헤더 "참조 페이지"를 수동으로 추가 해야 합니다.

SharePoint Online에서 제공 되는 참조이 있어야 하므로 CDN Url을 웹 브라우저에서 직접 테스트할 수 없습니다. 그러나 SharePoint 페이지에 CDN 자산 URL을 추가한 다음 브라우저에서 페이지를 열면 CDN 자산이 페이지에 렌더링 된 것을 볼 수 있습니다.

Microsoft Edge 브라우저에서 개발자 도구를 사용 하는 방법에 대 한 자세한 내용은 [Microsoft Edge 개발자 도구](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide)를 참조 하세요.

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>새 원본의 자산을 사용할 수 없는 이유는 무엇 인가요?
새 원본의 자산은 CDN을 통해 등록이 전파 되 고 자산이 원본에서 CDN 저장소로 업로드 되는 시간을 차지 하므로 즉시 사용할 수 없습니다. CDN에서 자산을 사용할 수 있어야 하는 시간은 자산의 수와 파일 크기에 따라 달라 집니다.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>클라이언트 쪽 웹 파트 또는 SharePoint Framework 솔루션이 작동 하지 않는 경우

공용 원본에 대해 Office 365 CDN을 사용 하도록 설정 하면 CDN 서비스가 다음과 같은 기본 원본을 자동으로 만듭니다.

- */MASTERPAGE
- */VSTYLE 라이브러리
- */CLIENTSIDEASSETS

*/Clientsideassets 원본이 누락 되 면 SharePoint Framework 솔루션은 실패 하 고 경고 또는 오류 메시지는 생성 되지 않습니다. **$True**으로 설정 된 CDN 또는 원본이 수동으로 삭제 되었기 때문에이 __ 원본이 누락 될 수 있습니다.

다음 PowerShell 명령을 사용 하 여 */CLIENTSIDEASSETS 원본이 있는지 확인할 수 있습니다.

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

또는 Office 365 CLI를 통해 확인할 수 있습니다.

``` powershell
spo cdn origin list
```

PowerShell에서 원점을 추가 하려면:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Office 365 CLI에서 원점을 추가 하려면 다음을 수행 합니다.

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Office 365 CDN과 함께 작동 하는 데 필요한 PowerShell 모듈 및 CLI 셸에는 무엇 인가요?

**SharePoint Online 관리 셸** PowerShell 모듈 또는 **office 365 CLI**를 사용 하 여 office 365 CDN 작업을 선택할 수 있습니다.

- [SharePoint Online 관리 셸 시작](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [Office 365 CLI 설치](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>참고 항목

[콘텐츠 배달 네트워크](https://aka.ms/o365cdns)

[Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)

