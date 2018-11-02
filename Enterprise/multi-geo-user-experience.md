---
title: 다중 위치 환경의 사용자 작업 환경
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 다중 위치 환경의 SharePoint 및 OneDrive 사용자 작업 환경에 대해 알아봅니다.
ms.openlocfilehash: 951efb636ce00f59393f624687d44a406fcf3fc0
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849834"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>다중 위치 환경의 사용자 작업 환경

OneDrive Multi-Geo 구성에 표시되는 내용은 다음과 같습니다.

#### <a name="users-onedrive-for-business-location"></a>사용자의 비즈니스용 OneDrive 위치

비즈니스용 OneDrive는 기본 설정 데이터 위치에 프로비전됩니다. 사용자가 잘못된 지리적 위치(예: 이전 지리적 위치의 책갈피)가 포함된 OneDrive URL로 이동하면 자동으로 해당 지리적 위치의 OneDrive로 리디렉션됩니다.

#### <a name="sharing"></a>공유

사용자 선택 환경에는 지리적 위치에 관계 없이 모든 사용자가 표시됩니다. 따라서 사용자는 같은 지역 또는 테넌트 지리적 위치의 다른 지역에 있는 다른 사용자와 공유할 수 있습니다. 다른 지리적 위치의 콘텐츠가 비즈니스용 OneDrive의 **공유한 항목** 보기에 표시되며, 호스트된 지리적 위치에 관계없이 Single-Sign-On 환경에서 액세스될 수 있습니다.

#### <a name="office-applications"></a>Office 응용 프로그램

Word, Excel 및 PowerPoint와 같은 Office 응용 프로그램은 각 사용자가 로그인할 때 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다. 따라서 사용자는 해당 OneDrive에 대한 지역별 URL을 입력할 필요가 없습니다.

#### <a name="onedrive-for-business-sync-client"></a>비즈니스용 OneDrive 동기화 클라이언트

비즈니스용 OneDrive 동기화 클라이언트(버전 17.3.6943.0625 이상)는 사용자의 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다.

#### <a name="office-365-app-launcher"></a>Office 365 앱 시작 관리자

앱 시작 관리자는 다중 위치를 인식하며, 각 타일을 워크로드의 해당 지리적 위치에 연결합니다. OneDrive 타일은 사용자의 OneDrive 라이브러리가 호스트된 올바른 지리적 위치를 가리키지만, SharePoint 타일은 모든 사용자를 팀 사이트가 호스트된 중앙 위치에 연결되도록 합니다.

#### <a name="delve-user-profiles"></a>Delve 사용자 프로필

사용자 프로필 정보는 사용자의 지리적 위치에서 마스터됩니다. 사용자를 선택하면 해당 사용자의 해당 지리적 위치로 이동되며, 여기에서 전체 프로필 세부 정보를 볼 수 있습니다.

Delve를 끄면 SharePoint에서 다중 위치를 인식하지 않는 클래식 프로필 환경이 표시됩니다.

#### <a name="delve"></a>Delve

위성 인스턴스에 있는 Office 365 사용자의 경우, Delve가 다른 지역의 사용자가 쓴 SharePoint 블로그 게시물에는 연결되지 않고, 해당 SharePoint 블로그 사이트에만 연결된다는 점을 제외하고, Delve Multi-Geo가 지원됩니다.

#### <a name="search"></a>검색

각 지리적 위치에는 자체의 검색 인덱스와 검색 센터가 있습니다. 사용자가 검색을 하면 쿼리가 모든 지리적 위치로 전송되고 반환된 결과는 병합된 후 순위가 지정되므로 사용자는 통합된 결과를 얻게 됩니다. 사용자가 자신의 지리적 위치에 관계없이 모든 지리적 위치에서 결과를 가져옵니다. 구체적인 내용에 대해서는 [비즈니스용 OneDrive Multi-Geo에 대한 검색 구성](configure-search-for-multi-geo.md)을 참조하세요.

다음과 같은 검색 클라이언트가 지원됩니다.

-   비즈니스용 OneDrive

-   Delve

-   SharePoint 홈

-   검색 센터

-   SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS 및 Android 

OneDrive iOS 및 Android 모바일 앱은 지리적 위치에 관계없이 OneDrive 파일 및 공유되는 파일을 표시합니다. OneDrive 모바일 앱에서 검색하면 모든 지리적 위치의 관련 결과가 표시됩니다. 이러한 앱의 최신 버전을 다운로드하세요.

자세한 내용은 [iOS의 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 및 [Android용 OneDrive 사용](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)을 참조하세요.

#### <a name="teams-experience"></a>팀 환경

팀은 다중 위치를 인식합니다. OneDrive 파일 및 최근에 본 파일은 사용자의 지리적 위치에 관계 없이 표시됩니다. @ 멘션은 모든 지리적 위치의 사용자에게 적용됩니다.
