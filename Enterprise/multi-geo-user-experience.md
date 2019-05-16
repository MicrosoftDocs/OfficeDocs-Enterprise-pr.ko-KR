---
title: 다중 위치 환경의 사용자 작업 환경
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 다중 위치 환경의 SharePoint, OneDrive 및 Exchange 사용자 작업 환경에 대해 알아봅니다.
ms.openlocfilehash: d8be4376b551242a372c44e62020ff78823f4dba
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069914"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>다중 위치 환경의 사용자 작업 환경

OneDrive Multi-Geo 구성에 표시되는 내용은 다음과 같습니다.

## <a name="exchange-mailbox"></a>Exchange 사서함


사용자의 Exchange 사서함은 원하는 데이터 위치에 프로비저닝되고 PDL이 변경되면 자동으로 재배치됩니다. 사용자는 일반적으로 다중 지역 환경에서 사용자 환경을 변경하지 않고도 웹에서 Outlook 및 Outlook을 사용할 수 있습니다.

## <a name="hub-sites"></a>허브 사이트

SharePoint 허브 사이트는 직원의 콘텐츠 검색 및 참여를 향상시키는 한편 프로젝트, 부서 또는 지역을 완전하고 일관성있게 표현합니다. 다중 지역 환경에서 인공위성 위치의 사이트는 허브 사이트의 위치 정보와 상관없이 허브 사이트와 쉽게 연관될 수 있습니다. 사용자는 사이트의 지리적 위치에 관계없이 단일 검색 환경을 통해 허브에서 검색하고 결과를 얻을 수 있습니다.

## <a name="office-365-app-launcher"></a>Office 365 앱 시작 관리자

앱 시작 관리자는 다중 지역을 인식하고 각 타일을 작업 부하의 적절한 지리적 위치로 지정합니다. SharePoint 및 OneDrive 타일은 사용자가 제공한 지리적 위치에 해당하는 위치를 가리킵니다. 즉, 사용자가 중앙 위치에 OneDrive를 가지고 있고, SharePoint 타일이 중앙 위치의 SP Home을 가리키지만 해당 그룹 사이트는 PDL에 해당하는 위치에 프로비저닝됩니다. 

## <a name="office-applications"></a>Office 응용 프로그램

Word, Excel 및 PowerPoint와 같은 Office 응용 프로그램은 각 사용자가 로그인할 때 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다. 사용자는 OneDrive 또는 SharePoint 사이트에 대한 지역별 URL을 입력할 필요가 없습니다.

## <a name="onedrive-for-business-sync-client"></a>비즈니스용 OneDrive 동기화 클라이언트

비즈니스용 OneDrive 동기화 클라이언트(버전 17.3.6943.0625 이상)는 사용자의 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다. 동기화 클라이언트 지원에는 지리적 위치에 관계없이 그룹 기반 사이트를 동기화하는 기능이 포함됩니다. 참고로 Groove 동기화 클라이언트는 다중 지역에서 지원되지 않습니다. 

## <a name="onedrive-for-business-location"></a>비즈니스용 OneDrive 위치

비즈니스용 OneDrive는 기본 설정 데이터 위치에 프로비전됩니다. 사용자가 잘못된 지리적 위치(예: 이전 지리적 위치의 책갈피)가 포함된 OneDrive URL로 이동하면 자동으로 해당 지리적 위치의 OneDrive로 리디렉션됩니다.

## <a name="onedrive-ios-and-android"></a>OneDrive iOS 및 Android 

OneDrive iOS 및 Android 모바일 앱은 지리적 위치에 관계없이 OneDrive 파일 및 공유되는 파일을 표시합니다. OneDrive 모바일 앱에서 검색하면 모든 지리적 위치의 관련 결과가 표시됩니다. 이러한 앱의 최신 버전을 다운로드하세요.

자세한 내용은 [iOS의 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 및 [Android용 OneDrive 사용](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)을 참조하세요.

## <a name="onedrive-mobile-client"></a>OneDrive 모바일 클라이언트 

OneDrive Mobile Client는 다중 지역을 인식하며 모든 지리적 위치의 관련 컨텐츠 및 결과를 표시합니다.

## <a name="search"></a>검색

각 지리적 위치에는 자체의 검색 인덱스와 검색 센터가 있습니다. 사용자가 검색을 하면 쿼리가 모든 지리적 위치로 전송되고 반환된 결과는 병합된 후 순위가 지정되므로 사용자는 통합된 결과를 얻게 됩니다. 사용자가 자신의 지리적 위치에 관계없이 모든 지리적 위치에서 결과를 가져옵니다. 구체적인 내용에 대해서는 [비즈니스용 OneDrive Multi-Geo에 대한 검색 구성](configure-search-for-multi-geo.md)을 참조하세요.

다음과 같은 검색 클라이언트가 지원됩니다.

-   비즈니스용 OneDrive

-   Delve

-   SharePoint 홈

-   검색 센터

-   SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램

## <a name="sharepoint-home"></a>SharePoint 홈 

SharePoint Multi-Geo에서 SharePoint 홈은 비즈니스 위치에 대해 OneDrive가 결정한대로 사용자가 거주하는 위치에서 호스팅됩니다. 예를 들어, 사용자가 OneDrive를 유럽 위성 위치에서 호스팅하는 경우 SharePoint 홈은 유럽에서 렌더링됩니다. SharePoint 홈에는 지리적 위치와 상관없이 사용자와 관련된 모든 콘텐츠가 포함됩니다. 

**팔로우한 사이트, 사이트의 뉴스, 최근 사용 사이트, 자주 사용하는 사이트 및 추천 사이트**

사용자가 해당 콘텐츠에 대한 권한이 있는 한 콘텐츠가 호스팅되는 지역 위치에 관계 없이 이러한 모든 구성 요소가 사용자에게 표시됩니다. 

**기능 링크**

관리자는 각 지리적 위치에 맞게 SharePoint 홈의 주요 링크를 구성할 수 있습니다. 이를 통해 관리자는 각 지역의 SP Home에서 해당 지역의 사용자에게 적합한 링크를 표시할 수 있습니다. 

## <a name="sharepoint-mobile-client"></a>SharePoint 모바일 클라이언트
 

SharePoint Mobile Client는 다중 지역을 인식하며 모든 지리적 위치의 관련 컨텐츠 및 결과를 표시합니다.

## <a name="sharing"></a>공유

사용자 선택 기능은 지리적 위치에 관계없이 모든 사용자를 보여줍니다. 이를 통해 사용자는 동일한 지리적 위치 또는 다른 거주자의 지리적 위치에있는 다른 사용자와 공유 할 수 있습니다. 서로 다른 지리적 위치의 콘텐츠는 사용자의 비즈니스용 OneDrive의 **공유한 항목** 보기에 표시되며 호스팅되는 지리적 위치와 상관없이 Single Sign-On 환경으로 액세스할 수 있습니다.

## <a name="teams-experience"></a>팀 환경

Teams은 여러 지역 인식합니다. OneDrive 파일과 최근에 본 파일은 사용자의 위치 정보와 상관없이 표시됩니다. @는 모든 지리적 위치의 사용자와 작업합니다.

## <a name="user-profiles"></a>사용자 프로필

사용자 프로필 정보는 사용자의 지리적 위치에서 마스터됩니다. 사용자를 선택하면 해당 사용자의 해당 지리적 위치로 이동되며, 여기에서 전체 프로필 세부 정보를 볼 수 있습니다.

Delve를 끄면 SharePoint에서 다중 위치를 인식하지 않는 클래식 프로필 환경이 표시됩니다.


