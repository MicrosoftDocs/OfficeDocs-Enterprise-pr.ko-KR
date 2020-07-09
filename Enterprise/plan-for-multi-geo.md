---
title: Microsoft 365 Business를 위한 계획
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
localization_priority: Priority
description: Microsoft 365 Multi-Geo, Multi-Geo 작동 방식 및 데이터 저장소에 사용할 수 있는 지리적 위치에 대해 알아봅니다.
ms.openlocfilehash: 8f06c43b9a622e06959ab12fa0e055c8653ca61c
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052461"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Microsoft 365 Business를 위한 계획

이 설명서는 데이터 상주 요구 사항을 충족해야 하는 회사의 현재 위치에 따라 추가적인 지역으로 Microsoft 365 테넌트를 확장하려고 준비하는 MNC(다국적 회사)의 관리자를 대상으로 작성되었습니다.

Multi-Geo 구성에서 Microsoft 365 테넌트는 중앙 위치와 하나 이상의 위성 위치로 구성됩니다. 이것은 여러 지리적 위치에 걸쳐 있는 단일 테넌트
입니다. 지리적 위치를 포함한 테넌트 정보는 Azure Active Directory(AAD)에서 관리합니다.

다음은 구성의 기본 개념을 이해하는 데 도움이 되는 몇 가지 핵심적인 다중 위치 용어입니다.

-   **테넌트** – Microsoft 365에서 일반적으로 하나 이상의 도메인에 연결되어 있는 조직을 나타내는 표현(예: https://contoso.sharepoint.com). 

-   **지리적 위치** – Microsoft 365 테넌트에서 데이터를 호스팅하는 데 사용할 수 있는 지리적 위치입니다.

-   **위성 위치** - Microsoft 365 테넌트에서 데이터를 호스팅하기 위해 구성한 추가 지리적 위치입니다. 다중 지역 테넌트는 북미 및 유럽과 같이 둘 이상의 지리적 위치에 걸쳐 있습니다.

-   **기본 데이터 위치(PDL)** - 개별 사용자의 Exchange 및 OneDrive 데이터가 저장되는 위치 정보입니다. 이는 관리자가 테넌트을 위해 구성된 지리적 위치 에 설정할 수 있습니다. OneDrive 사이트가 이미 있는 사용자의 PDL을 변경하면 OneDrive 데이터가 자동으로 새 지리적 위치로 이동되지 않습니다. 자세한 내용은 [OneDrive 라이브러리를 다른 지리적 위치로 이동](move-onedrive-between-geo-locations.md)을 참조하십시오. Exchange 사서함이있는 경우 사서함은 새 기본 설정 데이터 위치로 자동 이동됩니다.

Multi-Geo를 사용하려면 다음 4가지 주요 단계가 필요합니다.

1.  계정 팀과 협의하여 _Microsoft 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다.

2.  원하는 위성 위치를 선택하고 테넌트에 추가합니다.

3.  사용자가 선호하는 데이터 위치를 원하는 위성 위치로 설정하십시오. 새 OneDrive 사이트 또는 Exchange 사서함이 사용자에게 제공되면 PDL에 프로비저닝됩니다.

4.  필요에 따라 중앙 위치에 있는 사용자의 기존 OneDrive 사이트를 기본 설정 데이터 위치로 마이그레이션합니다. (Exchange 사서함은 사용자의 PDL을 설정할 때 자동으로 마이그레이션됩니다.)

이러한 각 단계에 대한 자세한 내용은 [Microsoft 365 Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하세요.

> [!IMPORTANT]
> 참고로, Microsoft 365 Multi-Geo는 성능 최적화를 위해 설계되지 않았고 데이터 상주 요구 사항을 충족하도록 설계되었습니다. Microsoft 365의 성능 최적화에 대한 자세한 내용은 [Microsoft 365의 네트워크 계획 및 성능 조정](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)을 참조하거나 지원 그룹에 문의하세요.

다음 위치 중 하나를 OneDrive 및 SharePoint 사이트를 호스팅 할 수있는 위성 위치로 구성하고 Exchange 사서함을 구성 할 수 있습니다. Multi-Geo를 계획할 때 Microsoft 365 테넌트에 추가 할 위치 목록을 만드십시오. 하나 또는 두 개의 위성 위치로 시작한 다음 필요한 경우 더 많은 지역 위치로 점진적으로 확장하는 것을 권장합니다.

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Microsoft 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.

## <a name="best-practices"></a>모범 사례

몇 가지 초기 테스트를 수행하기 위해 Microsoft 365에서 테스트 사용자를 만드는 것이 좋습니다. 온보드 프로덕션 사용자에게 Microsoft 365 Multi-Geo로 진행하기 전에 이 사용자와의 몇 가지 테스트 및 확인 단계를 거칩니다.

테스트 사용자와 테스트를 마친 후에는 IT 부서의 파일럿 그룹을 선택하여 새로운 지리적 위치에서 OneDrive 및 Exchange를 가장 먼저 사용할 수 있습니다. 이 첫 번째 그룹에서는 아직 OneDrive가 없는 사용자를 선택합니다. 이 초기 그룹에 5명 이하를 두고 일괄 공개 접근 방식을 따라 점차적으로 확장하는 것을 권장합니다.

Each user should have a *preferred data location* (PDL) set so that Microsoft 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.

Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.

사용자가 온 - 프레미스 Active Directory 시스템에서 Azure Active Directory로 동기화되는 경우 기본 데이터 위치를 Active Directory 특성으로 설정하고 Azure Active Directory Connect를 사용하여 동기화해야 합니다. Azure AD PowerShell을 사용하여 동기화된 사용자의 기본 데이터 위치를 직접 구성할 수 없습니다. Active Directory에서 PDL을 설정하고 동기화하는 단계는 [Azure Active Directory Connect 동기화: Microsoft 365 리소스의 기본 설정 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)에서 다룹니다.

The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.

다중 위치 환경의 최종 사용자 경험에 대한 자세한 내용은 [다중 위치 환경의 사용자 경험](multi-geo-user-experience.md)을 읽어보세요.

Microsoft 365 Multi-Geo 테넌시의 Teams 경험에 대한 자세한 내용은 [Microsoft 365 OneDrive 및 SharePoint Online Multi-Geo 지원 테넌시의 Teams 경험](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)을 참조하세요.

Microsoft 365 Multi-Geo를 구성을 시작하려면 [Microsoft 365 Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하세요.

구성을 완료한 경우 기본 설정 데이터 위치에서 작업할 때 필요하므로 [사용자의 OneDrive 라이브러리를 마이그레이션](move-onedrive-between-geo-locations.md)해야 합니다.
