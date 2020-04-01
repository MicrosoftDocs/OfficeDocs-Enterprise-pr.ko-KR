---
title: Office 365 네트워크 연결 위치 서비스 (미리 보기)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 네트워크 연결 위치 서비스 (미리 보기)
ms.openlocfilehash: 6deb964955689416219c5b9350ea150ecd4f3b7a
ms.sourcegitcommit: 44a0e9a134373eb0d1292761089a6557b01ac327
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "43081817"
---
# <a name="office-365-network-connectivity-location-services-preview"></a>Office 365 네트워크 연결 위치 서비스 (미리 보기)

Microsoft 365 관리 센터에는 이제 Office 365 테 넌 트에서 수집 되며 테 넌 트의 관리 사용자만 볼 수 있는 live performance 메트릭에 해당 하는 **네트워크 Insights 및 성능 권장 사항이**나와 있습니다. 조직 네트워크 연결은 네트워크 송신 위치를 통해 인터넷으로 연결 됩니다. Office 365 클라이언트 연결은이 경로를 사용 하 여 인터넷을 통해 Microsoft 서비스 전면 도어 서버로 연결 합니다. Office 위치를 확인 하는 것은 이러한 네트워크 통찰력을 표시할 수 있는 열쇠입니다.

## <a name="location-in-network-measurements"></a>네트워크 측정의 위치

조직의 관리자가이 기능에서 사용 하는 네트워크 측정값에 포함할 위치를 선택할 수 있습니다. 이렇게 하면 각 office가 있는 도시의 자동 검색이 가능해 집니다. 위치 정보는 정확 하지 않으며 300m로 난독 처리 되며 도시별로 분류 됩니다. Windows 디바이스에서 위치를 캡처하면 도구 트레이에 위치 하는 **사용** 중 아이콘이 표시 되 고 관리자가이를 사용자에 게 알릴 수 있습니다. 이 처리를 통해 위치는 회사 사무실 위치로 취급 되 고 개인 또는 장치의 위치는 아닙니다. 네트워크 insights는 이러한 검색 된 office 위치 도시에 표시 될 수 있습니다. 추천 값이 더 필요한 경우 관리자는 특정 office 위치 주소를 입력할 수 있으며 네트워크 insights가 대신 집계 됩니다. Office 위치를 300 미터 보다 더 가깝게 집계할 수 없습니다.

## <a name="location-in-the-microsoft-365-admin-center"></a>Microsoft 365 관리 센터의 위치

Microsoft 365 관리 센터에서 Bing 지도 컨트롤은 조직 사무실 위치를 표시 하 고 선택한 사무실 위치에 대 한 네트워크 경계 토폴로지를 표시 하는 데 사용 됩니다. 관리자가 office 위치에 대 한 특정 주소 세부 정보를 추가할 때 Bing 맵은 데이터를 보다 쉽게 입력할 수 있도록 주소를 제안 하는 데에도 사용 됩니다.

## <a name="terms-of-use"></a>사용 약관

Geocodes를 비롯 하 여 Bing 지도를 통해 제공 되는 모든 콘텐츠는 콘텐츠를 제공 하는 제품 내 에서만 사용할 수 있습니다. Microsoft 365 관리 센터 Location Services 기능을 사용 하 여 Bing 지도를 통해 제공 되는 고객은 _Bing 지도 최종 사용자의 사용 약관_ <https://go.microsoft.com/?linkid=9710837> 및에서 _microsoft 개인 정보 취급_ 방침을 사용할 수 있습니다.<https://go.microsoft.com/fwlink/?LinkID=248686.>

Bing 지도를 통해 제공 되는이 기능은 여기에서 지 원하는 **기술**에서도 지원 됩니다. Bing Maps에서 제공 하는 기술 _서비스 용어_ 에 따라 지원 되는 위치 서비스가 활용 됩니다 <https://legal.here.com/en-gb/terms>.
