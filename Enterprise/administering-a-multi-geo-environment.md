---
title: 다중 위치 환경 관리
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: 다중 위치 환경의 SharePoint 및 OneDrive 서비스 관리에 대해 알아봅니다.
ms.openlocfilehash: a4e467edebbcfbb0288b698f3e7d5bcf589cdd69
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433529"
---
# <a name="administering-a-multi-geo-environment"></a>Multi-Geo 환경 관리

Microsoft 365 서비스가 다중 위치 환경에서 작동하는 방식을 살펴봅니다.

## <a name="audit-log-search"></a>감사 로그 검색

모든 위성 위치에 대한 통합 [감사 로그](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)는 Microsoft 365 감사 로그 검색 페이지에서 사용할 수 있습니다. 여러 지역의 모든 감사 로그 항목을 볼 수 있습니다. 예를 들어, NAM 및 EUR 지역 사용자의 활동은 하나의 조직 보기에 표시되며, 기존 필터를 적용하여 특정 사용자 활동을 볼 수 있습니다.

## <a name="bcs-secure-store-apps"></a>BCS, 보안 저장소, 앱

BCS, 보안 저장소 및 앱은 모두 각 위성 위치에서 별도의 인스턴스를 유지하므로, SharePoint Online 관리자는 이러한 서비스를 각 위성 위치와는 별도로 관리하고 구성해야 합니다.

## <a name="ediscovery"></a>eDiscovery 

기본적으로 eDiscovery Manager 또는 다중 지역 테넌트의 관리자는 해당 거주자의 중앙 위치에서만 eDiscovery를 수행할 수 있습니다. Microsoft 365 전역 관리자는 다른 사용자들이 eDiscovery를 수행할 수 있도록 하기 위해 eDiscovery 관리자 권한을 할당해야 하며, 해당 준수 보안 필터에서 “Region” 매개 변수를 할당하여 eDiscovery 수행 지역을 위성 위치로 지정해야 합니다. 그렇지 않으면 해당 위성 위치에 대해 eDiscovery가 수행되지 않습니다. 지역에 대한 준수 보안 필터를 구성하려면 [Microsoft 365 Multi-Geo eDiscovery의 구성](multi-geo-ediscovery-configuration.md)을 참조하세요.

## <a name="exchange-mailboxes"></a>Exchange 사서함

사용자의 Exchange 사서함은 PDL이 변경되면 자동으로 이동합니다. 새 사서함이 만들어지면 사용자의 PDL에 값이 설정되지 않은 경우 사용자의 PDL 또는 중앙 위치에 프로비저닝됩니다.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>IP(정보 보호) DLP(데이터 손실 방지) 정책

보안 및 적합성 센터에서 비즈니스, SharePoint 및 Exchange 용 OneDrive에 대한 IP DLP 정책을 설정하고 필요에 따라 전체 테넌트 또는 해당 사용자에게 정책의 범위를 지정할 수 있습니다. 예를 들어 위성 위치에 있는 사용자에 대한 정책을 선택하려면 특정 OneDrive에 정책을 적용하고 사용자의 OneDrive URL을 입력하도록 선택합니다. DLP 정책 생성에 대한 일반적인 지침은 [데이터 손실 방지 정책 개요](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조하세요.

DLP 정책은 각 지리적 위치에 적용할 수 있는지에 따라 자동으로 동기화됩니다.

지리적 위치에 모든 사용자에 대해 정보 보호 및 데이터 손실 방지 정책을 구현하는 방식은 UI에서 사용할 수 있는 옵션이 아니며, 대신 정책에 대해 적용 가능한 계정을 선택하거나 정책을 모든 계정에 전역적으로 적용해야 합니다.

## <a name="microsoft-flow"></a>Microsoft Flow

위성 위치에 대해 만들어진 흐름은 테넌트의 기본 지리적 위치에 있는 끝점을 사용합니다.  Microsoft Flow는 다중 지역 서비스가 아닙니다. 

## <a name="microsoft-powerapps"></a>Microsoft PowerApps

위성 위치에 대해 만들어진 PowerApp은 테넌트의 중앙 위치에 있는 끝점을 사용합니다. Microsoft PowerApps은 다중 지역 서비스가 아닙니다. 

## <a name="onedrive-administrator-experience"></a>OneDrive 관리자 환경

[OneDrive 관리 센터](https://admin.onedrive.com)의 왼쪽 탐색 영역에는 지리적 위치를 보고 관리할 수 있는 지리적 위치 지도를 표시하는 **지리적 위치** 탭이 있습니다. 이 페이지에서 테넌트에 대한 지리적 위치를 추가하거나 삭제합니다.

## <a name="security-and-compliance-admin-center"></a>보안 및 준수 관리 센터

Multi-Geo 테넌트에 대해 하나의 중앙 준수 센터인 [Microsoft 365 보안 및 준수 센터](https://protection.office.com/?rfr=AdminCenter\#/homepage)가 있습니다.

## <a name="sharepoint-storage-quota"></a>SharePoint 저장소 할당량

기본적으로 다중 지역 환경의 모든 지리적 위치는 사용 가능한 테넌트 저장소 할당량을 공유합니다.  특정 지리적 위치에 대해 특정 할당량을 할당하여 저장소 할당량을 관리할 수도 있습니다. 자세한 내용은 [다중 지역 환경에서 SharePoint 저장소 할당량](sharepoint-multi-geo-storage-quota.md)을 참조하세요.

## <a name="sharing"></a>공유

관리자는 각 위치에 대한 공유 정책을 설정하고 관리할 수 있습니다. 각 지리적 위치에 있는 OneDrive 및 SharePoint 사이트는 해당 지리적 특정 공유 설정만 사용합니다. (예를 들어, 중앙 위치에 대한 [외부 공유](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)는 허용하지만 위성 위치의 외부 공유나 그 반대에 대해서는 허용할 수 없습니다.) 공유 설정에서는 지리적 위치간에 공유 제한을 구성할 수 없습니다.

## <a name="taxonomy"></a>분류

우리는 지리적 위치에서 엔터프라이즈 관리 메타 데이터에 대한 통합 [분류](https://docs.microsoft.com/sharepoint/managed-metadata)를 지원하며 마스터는 회사의 중앙 위치에서 호스팅됩니다. 전역 분류를 중앙 위치에서 관리하고 위치 관련 용어만 위성 위치의 분류에 추가하는 것이 좋습니다. 전역 분류 용어는 위성 위치에 동기화됩니다.

자세한 내용 및 개발자 지침은 [다중 지역 테넌트의 메타 데이터 관리](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata)를 참조하세요.

## <a name="user-profile-application"></a>사용자 프로필 응용 프로그램

[사용자 프로필 응용 프로그램](https://docs.microsoft.com/sharepoint/manage-user-profiles)은 각 지리적 위치에 있습니다. 각 사용자의 프로필 정보는 지리적 위치에서 호스팅되며 해당 지리적 위치의 관리자가 사용할 수 있습니다.

사용자 정의 프로필 속성이 있으면 지리적 위치 간에 동일한 프로필 스키마를 사용하고 모든 지리적 위치에 또는 필요할 때 사용자 지정 프로필 속성을 채우는 것이 좋습니다. 프로그래밍 방식으로 사용자 프로필 데이터를 채우는 방법에 대한 지침은 [대량 사용자 프로필 업데이트 API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)를 참조하세요.

자세한 내용 및 개발자 지침은 [다중 지역 테넌트의 사용자 프로필 작업](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience)를 참조하세요.

## <a name="video-portal"></a>비디오 포털

다중 지역 테넌트의 경우 O365 비디오 포털은 기본 지역에서만 제공되며 모든 사용자는 해당 중앙 포털 URL로 리디렉션됩니다. 따라서 해당 지역의 RMS(원격 미디어 서비스)가 다음과 같이 중앙 위치를 기반으로 사용됩니다.

스트림은 현재 다음 지역에서 사용할 수 있습니다.

- 북아메리카, 미국에서 호스팅 됨. 
- 유럽
- 아시아 태평양

그러나 현재 Microsoft 365 비디오가 지원되는 다음 지역에서는 스트림을 아직 사용할 수 없으므로 이러한 로컬 인스턴스의 경우 지원되는 가장 가까운 지역에 있는 RMS를 사용합니다.

- 오스트레일리아
- 캐나다
- 인도
- 영국
