---
title: 비즈니스용 OneDrive Multi-Geo 계획
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
description: 비즈니스용 OneDrive Multi-Geo, 다중 위치 작동 방식 및 데이터 저장소에 사용할 수 있는 지리적 위치에 대해 알아봅니다.
ms.openlocfilehash: 54efc6092338e505ef44344f9c3d3a7efe9ae498
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>비즈니스용 OneDrive Multi-Geo 계획

이 설명서는 데이터 상주 요구 사항을 충족해야 하는 회사 현재 상황에 따라 추가적인 지역으로 SharePoint Online 테넌트를 확장하려고 준비하는 MNC(다국적 회사)의 관리자를 대상으로 작성되었습니다.

OneDrive Multi-Geo 구성에서 Office 365 테넌트는 하나의 중앙 위치(기본 위치라고도 함)와 하나 이상의 위성 지리적 위치로 구성됩니다. 이 테넌트는 여러 지리적 위치에 걸쳐 있는 단일 테넌트입니다. OneDrive Multi-Geo에서 지리적 위치를 포함하는 테넌트 정보는 AAD(Azure Active Directory)에서 마스터됩니다. 

다음은 구성의 기본 개념을 이해하는 데 도움이 되는 몇 가지 핵심적인 다중 위치 용어입니다.

-   **테넌트** – Office 365 클라우드에서 일반적으로 하나 이상의 도메인에 연결되어 있는 조직을 나타내는 표현입니다(예: http://contoso.sharepoint.com)). 

-   **지리적 위치** – 테넌트의 데이터가 호스트되는 지리적 위치입니다. 다중 위치 테넌트는 둘 이상의 지리적 위치(예: 북미 및 유럽)에 걸쳐 있습니다.

-   **ADL(허용된 데이터 위치)** – 테넌트가 OneDrive 및 SharePoint 데이터를 호스트하도록 구성된 지리적 위치입니다.

-   **PDL(기본 설정 데이터 위치)** - 개별 사용자의 OneDrive 데이터가 저장되는 지리적 위치입니다. 관리자는 이 위치를 테넌트에 대해 구성된 허용된 데이터 위치로 설정할 수 있습니다. OneDrive 사이트가 이미 있는 사용자의 PDL을 변경하는 경우 해당 OneDrive 데이터가 자동으로 새 지리적 위치로 이동되지 않습니다. 자세한 내용은 [OneDrive 라이브러리를 다른 지리적 위치로 이동](move-onedrive-between-geo-locations.md)을 참조하세요.

Multi-Geo를 사용하려면 다음 4가지 주요 단계가 필요합니다.

1.  계정 팀과 협의하여 추가 하려면 계정 팀에서 작업 하는 _Office 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다.

2.  원하는 위성 지리적 위치를 선택하고 테넌트에 추가합니다.

3.  사용자의 기본 설정 데이터 위치를 원하는 위성 지리적 위치로 설정합니다. 사용자에 대해 새 OneDrive 사이트가 프로비전될 경우 해당 PDL로 프로비전됩니다.

4.  필요에 따라 홈 위치에 있는 사용자의 기존 OneDrive 사이트를 기본 설정 데이터 위치로 마이그레이션합니다.

이러한 각 단계에 대한 자세한 내용은 [비즈니스용 OneDrive Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하세요.

> [!IMPORTANT]
> Office 365의 Multi-Geo 기능은 성능 최적화 사례에 맞게 디자인되지 않았으며, 데이터 상주 요구 사항을 충족하도록 디자인되었습니다. Office 365의 성능 최적화에 대한 내용은 [Office 365의 네트워크 계획 및 성능 조정](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)을 참조하거나 지원 그룹에 문의하세요.

다음 위치를 OneDrive 파일을 호스트할 수 있는 위성 지리적 위치로 구성할 수 있습니다. 다중 위치를 계획할 때는 Office 365 테넌트에 추가하려는 위치 목록을 만듭니다. 한두 개의 위성 위치에서 시작한 후 필요에 따라 더 많은 지리적 위치로 점차적으로 확장하는 것이 좋습니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>위치</strong></th>
<th align="left"><strong>코드</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">아시아 태평양</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">유럽/중동/아프리카</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">북미</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">오스트레일리아</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">캐나다</td>
<td align="left">CAN</td>
</tr>
<tr class="odd">
<td align="left">일본</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">한국</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">영국</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

예정된 지리적 위치:
  
- 프랑스
- 인도

다중 위치를 구성할 경우 Office 365로 마이그레이션하는 동안 온-프레미스 인프라를 통합할 기회를 고려하는 것이 좋습니다. 예를 들어, 싱가포르 및 말레이시아에 온-프레미스 팜이 있는 경우, 데이터 상주 요구에 맞을 경우 APC 위성 위치로 통합할 수 있습니다.

## <a name="best-practices"></a>모범 사례

Office 365에 초기 테스트를 수행하기 위한 테스트 사용자를 만드는 것이 좋습니다. 프로덕션 사용자를 OneDrive Multi-Geo 기능에 등록하기 전에 이 사용자로 일부 테스트 및 확인 단계를 진행하게 됩니다.

테스트 사용자로 테스트를 완료한 후 IT 부서에서 새 지리적 위치에서 최초로 OneDrive를 사용할 파일럿 그룹을 선택합니다. 이 첫 번째 그룹으로 OneDrive가 아직 없는 사용자를 선택합니다. 이 초기 그룹에는 5명 이하의 사용자를 포함한 후 일괄 롤아웃 방식에 따라 서서히 확장하는 것이 좋습니다.

Office 365에서 해당 OneDrive를 프로비전할 지리적 위치를 결정할 수 있도록 각 사용자에게는 PDL(*기본 설정 데이터 위치*)이 설정되어 있어야 합니다. 사용자의 기본 설정 데이터 위치는 선택한 위성 위치 중 하나 또는 사용자의 중앙 위치와 일치해야 합니다. PDL 필드는 필수는 아니지만 모든 사용자에 대해 PDL을 설정하는 것이 좋습니다. PDL이 없는 사용자의 워크로드는 Multi-Geo 논리에 따라 중앙 위치에 프로비전됩니다.   

사용자 목록을 만들고, 해당 UPN(사용자 주체 이름)과 해당 기본 설정 데이터 위치에 대한 위치 코드를 포함합니다. 시작할 테스트 사용자와 초기 파일럿 그룹을 포함합니다. 구성 절차를 위해 이 목록이 필요합니다.

사용자가 온-프레미스 AD(Active Directory) 시스템에서 AAD(Azure Active Directory)로 동기화되면 Azure Active Directory Connect를 사용하여 동기화된 사용자에 대한 기본 설정 데이터 위치를 설정해야 합니다. Azure AD PowerShell을 사용하여 동기화된 사용자의 기본 설정 데이터 위치를 직접 구성할 수는 없습니다. AD에서 PDL를 설정하고 동기화하는 단계는 [Azure Active Directory Connect 동기화: Office 365 리소스에 대한 기본 설정 데이터 위치 구성](https://docs.microsoft.com/ko-KR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)에 나와 있습니다.

SharePoint 및 OneDrive 설정과 서비스가 다중 위치를 인식하므로 다중 위치 테넌트의 관리는 다중 위치가 아닌 테넌트의 관리와 다를 수 있습니다. 구성을 계속하기 전에 [다중 위치 환경 관리](administering-a-multi-geo-environment.md)를 검토하는 것이 좋습니다.

다중 위치 환경의 최종 사용자 경험에 대한 자세한 내용은 [다중 위치 환경의 사용자 경험](multi-geo-user-experience.md)을 읽어보세요.

비즈니스용 OneDrive Multi-Geo 구성을 시작하려면 [비즈니스용 OneDrive Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하세요.

구성을 완료한 경우 기본 설정 데이터 위치에서 작업할 때 필요하므로 [사용자의 OneDrive 라이브러리를 마이그레이션](move-onedrive-between-geo-locations.md)해야 합니다.
