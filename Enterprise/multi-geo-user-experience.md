---
title: Multgeo 환경에서 사용자 환경
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 다중-지리적으로 분산 환경에서 SharePoint와 OneDrive 사용자 환경에 알아봅니다.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>다중-지리적으로 분산 환경에서 사용자 환경

OneDrive 다중-지리적으로 분산 구성에서 참조 하는 사용자에 게는 다음과 같습니다.

#### <a name="users-onedrive-for-business-location"></a>비즈니스 위치에 대 한 사용자의 OneDrive

사용자는 자신의 OneDrive for Business의 기본 데이터 위치에 프로 비전을 갖게 됩니다. 사용자가 OneDrive URL (예: 이전 지리적 위치에서 책갈피) 잘못 된 지리적 위치를 포함 하는 탐색 하는 경우 자동으로 적절 한 지리적 위치에 OneDrive로 리디렉션됩니다 됩니다.

#### <a name="sharing"></a>공유

사용자 선택 경험의 지리적 위치에 관계 없이 모든 사용자를 표시합니다. 이 사용자를 동일한 지리적으로 분산 또는 테 넌 트의 지리적 위치의 다른 모든 다른 사용자와 공유할 수 있습니다. 콘텐츠에서 서로 다른 지리적으로 분산 위치 비즈니스에 대 한 사용자의 OneDrive에서 **공유 항목** 보기에서 볼 수 있으며 Single Sign-on 환경에서 호스팅되는 어떤 지리적 위치에 관계 없이 사용 하 여 액세스할 수 있습니다.

#### <a name="office-applications"></a>Office 응용 프로그램

Word, Excel 및 PowerPoint와 같은 office 응용 프로그램 로그인 할 때 비즈니스 지리적으로 분산-각 사용자에 대 한 위치에 대 한 올바른 OneDrive을 자동으로 검색 됩니다. 사용자가 자신의 onedrive 지리적으로 분산 특정 URL을 입력 필요가 없습니다.

#### <a name="onedrive-for-business-sync-client"></a>비즈니스용 OneDrive 비즈니스 동기화 클라이언트

비즈니스 동기화 클라이언트에 대 한 OneDrive (버전 17.3.6943.0625 이상)의 사용자에 대 한 비즈니스 지리적 위치에 대 한 올바른 OneDrive를 자동으로 검색 됩니다.

#### <a name="office-365-app-launcher"></a>Office 365 앱 시작 관리자

응용 프로그램 시작 관리자를 인식 다중 지리적 이며 각 타일 작업량의 적절 한 지리적 위치에 직접 보내도록 지정 합니다. OneDrive는 사용자의 OneDrive 라이브러리 호스팅되, SharePoint 타일은 위치를 가리키도록 모든 사용자에 게 중앙, 팀 사이트는 다음과 같은 호스팅됩니다 여전히으로 하는 동안 올바른 지리적 위치에 있는 점을 바둑판식으로 배열 합니다.

#### <a name="delve-user-profiles"></a>사용자 프로필을 굴

사용자 프로필 정보를 사용자의 지리적 위치에 마스터 됩니다. 사용자를 선택할 때는 자신의 전체 프로필 정보 표시는 사용자에 대 한 적절 한 지리적 위치에 연결 됩니다.

Delve를 해제 하는 다중-지리적으로 분산 인식 없는 SharePoint, 경험 클래식 프로필을 표시 됩니다.

#### <a name="delve"></a>Delve

Office 365에 있는 사용자가 위성 인스턴스에 대 한 다중 Geo 굴 Delve SharePoint 블로그 사이트에만 다른 지역에서 사용자가 작성 하는 SharePoint 블로그 게시물에 연결 하지는 제한 된 지원 됩니다.

#### <a name="search"></a>검색

각 지리적 위치에는 자체 검색 인덱스와 검색 센터에 있습니다. 사용자를 검색 하는 경우 쿼리 지리적 위치를 모두에 전송 되 고 반환 된 결과 병합 된 셀 및 사용자 가져옵니다 통합된 결과 하므로 순위를 지정한 다음. 사용자가 자신의 지리적 위치에 관계 없이 모든 지리적 위치에서 결과를 가져옵니다. 자세한 내용은 [OneDrive에 대 한 비즈니스 다중-지리적으로 분산에 대 한 검색 구성](configure-search-for-multi-geo.md) 을 참조 하십시오.

다음과 같은 검색 클라이언트가 지원 됩니다.

-   비즈니스용 OneDrive

-   Delve

-   SharePoint 홈

-   검색 센터

-   SharePoint 검색 API를 사용 하는 사용자 지정 검색 응용 프로그램

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS 및 Android 

OneDrive iOS 및 Android 모바일 앱 안내해 OneDrive 파일 및 해당 지리적 위치에 관계 없이 사용자와 공유 하는 파일입니다. OneDrive 모바일 응용 프로그램에서 검색에는 모든 지리적 위치에서 관련이 있는 결과 표시 됩니다. 이러한 응용 프로그램의 최신 버전을 다운로드 하십시오.

자세한 내용은 사용 [iOS에 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 및 [Android에 대 한 사용 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) 를 참조 하십시오.

#### <a name="teams-experience"></a>팀 환경

팀은 다중-지리적으로 분산을 인식 합니다. OneDrive 파일 및 최근에 본된 파일은 사용자의 지리적 위치에 관계 없이 표시 됩니다. @ 모든 지리적 위치에서 사용자와 멘 작동 합니다.
