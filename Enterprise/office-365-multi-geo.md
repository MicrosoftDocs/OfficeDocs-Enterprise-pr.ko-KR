---
title: Office 365 Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Office 365 Multi-Geo로 여러 지리적 지역으로 Office 365 범위를 확장합니다.
ms.openlocfilehash: eb5c28131b7ac629d9acc607c777756b8825549c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491952"
---
# <a name="office-365-multi-geo"></a>Office 365 Multi-Geo

Office 365 Multi-Geo를 사용하면 Office 365 범위를 기존 지사의 여러 지리적 지역 및 / 또는 국가로 확장할 수 있습니다. Microsoft 계정 팀에 연락하여 다국적 기업용 Office 365 Multi-Geo에 가입합니다.
  
Office 365 Multi-Geo를 사용하여 데이터 상주 요구 사항을 충족하기 위해 선택한 지리적 위치에서 미사용 데이터를 프로비저닝 및 저장하고, 동시에 귀하의 전 세계 작업자들이 최신 생산선 환경을 활용하도록 할 수 있습니다.

#### <a name="video-introducing-office-365-multi-geo"></a>비디오: Office 365 Multi-Geo 소개

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

Multi-Geo 환경에서 Office 365 테넌트는 중앙 위치(Office 365 구독이 원래 제공되는 위치)와 하나 이상의 위성 위치로 구성됩니다. Multi-Geo 테넌트의 경우 지리적 위치, 그룹 및 사용자 정보에 대한 정보는 Azure Active Directory(AAD)에서 관리됩니다. 테넌트 정보가 중앙에서 관리되고 각 지리적 위치와 동기화되기 때문에 회사의 모든 사람과 관련된 공유 및 경험은 전역 세계적으로 인식됩니다.

![SharePoint 관리 센터의 Multi-Geo 지도 스크린샷](media/multi-geo-world-map.png)

Office 365 Multi-Geo는 주로 성능 최적화를 위해 설계되지 않았고 데이터 거주 요구 사항을 충족하도록 설계되었습니다. Office 365의 성능 최적화에 대한 자세한 내용은 [Office 365의 네트워크 계획 및 성능 조정](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)을 참조하거나 지원 그룹에 문의하세요.

## <a name="terminology"></a>용어

다음은 Office 365 Multi-Geo를 설명하는 데 사용되는 주요 용어입니다.

- **중앙 위치** - 테넌트가 원래 프로비저닝된 지리적 위치
- **지역 관리자** - 하나 이상의 지정된 위성 위치를 관리할 수 있는 관리자
- **지역 코드** - 주어직 지리적 위치에 대한 세 자리 코드
- **지리적 위치** – Exchange 우편함 및 OneDrive 및 SharePoint 사이트를 포함하여 데이터를 호스팅하기 위해 Multi-Geo 테넌트에서 사용할 수있는 지리적 위치
- **선호 하는 데이터 위치 (PDL)** - 사용자가 Exchange 사서함과 OneDrive를 프로비저닝하는 위치를 나타내는 관리자가 설정한 사용자 속성 또한 PDL은 사용자가 만든 SharePoint 사이트가 프로비저닝되는 위치를 결정합니다.
- **위성 위치** - 지리적 인식 Office 365 작업(SharePoint, OneDrive 및 Exchange)이 Multi-Geo 테넌트에서 활성화된 지리적 위치입니다.
- **테넌트** – Office 365에서 일반적으로 하나 이상의 도메인에 연결되어 있는 조직을 나타내는 표현입니다(예: contoso.com).

## <a name="office-365-multi-geo-availability"></a>Office 365 Multi-Geo 사용 가능 여부

Office 365 Multi-Geo는 현재 다음 지역 및 국가에서 제공됩니다.

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a>시작하기

Multi-Geo를 시작하려면 이러한 단계를 따르세요.

1. 계정 팀과 협의하여 _Office 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다. 계정 팀이 필요한 라이센스 수를 추가할 수 있도록 안내합니다. 현재 Multi-Geo 기능은 Office 365 구독을 2,500개 이상 보유한 고객에게 제공됩니다.

   Office 365 Multi-Geo를 사용하려면 먼저 Microsoft에서 Multi-Geo 지원을 위해 Exchange Online 테넌트를 구성해야 합니다. 이 일회성 구성 프로세스는 *Office 365의 Multi-Geo 기능* 서비스 계획을 주문하고 테넌트에 라이선스가 표시된 후에 실행됩니다. Multi-Geo 라이선스가 적용되면 [Office 365 메시지 센터](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093)에서 알림을 받게 되며 Office 365 Multi-Geo 기능을 구성하고 사용하기 시작할 수 있습니다.

2. [Multi-Geo 환경 계획](plan-for-multi-geo.md)을 읽으세요.

3. [Multi-Geo 환경 관리](administering-a-multi-geo-environment.md) 및 [사용자가 환경을 경험하는 방법](multi-geo-user-experience.md)에 대해 알아봅니다.

4. Office 365 Multi-Geo를 설치할 준비가 되면 [Multi-Geo의 테넌트를 구성합니다.](multi-geo-tenant-configuration.md)

5. [검색 설정](configure-search-for-multi-geo.md)

## <a name="see-also"></a>참고 항목

[Exchange Online 및 OneDrive의 Multi-Geo](https://Aka.ms/GoMultiGeo)

[OneDrive 및 SharePoint Online의 Multi-Geo 기능](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[Exchange Online의 Multi-Geo 기능](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)
