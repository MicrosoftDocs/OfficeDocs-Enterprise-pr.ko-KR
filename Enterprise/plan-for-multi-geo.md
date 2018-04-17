---
title: 비즈니스 다중-지리적으로 분산 비즈니스용 OneDrive 계획
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 비즈니스 다중-지리적으로 분산, 다중-지리적으로 분산 작동 하는 방법 및 어떤 지리적 위치 데이터 저장소에서 사용할 수 있는 OneDrive을 소개 합니다.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>비즈니스 다중-지리적으로 분산 비즈니스용 OneDrive 계획

이 설명서는 자신의 SharePoint Online 테 넌 트 데이터 residency 요구를 충족 하기 위해 회사의 현재 상태에 따라 추가 지역 하기 위해 확장할 수 있도록 준비 하는 다국적 기업 (MNCs)의 관리자를 위한 설계 되었습니다.

OneDrive 다중-지리적으로 분산 구성에서 Office 365 테 넌 트 (기본 위치 라고도 함) 하는 중앙 위치 및 위성 지리적 위치를 하나 이상으로 구성 됩니다. 여러 지리적 위치에 걸쳐 있는 단일 테 넌 트입니다. OneDrive 다중-Geo의 지리적 위치를 포함 하 여 테 넌 트 정보를에서 Azure Active Directory (AAD) 마스터입니다. 

일부 주요 다중-지리적으로 분산 용어 구성의 기본 개념을 이해 하는데 도움이 되는 다음과 같습니다.

-   **테 넌 트** -일반적으로 연결 된 하나 이상의 도메인을 포함 하는 Office 365 클라우드 조직의 표현 (등 http://contoso.sharepoint.com)합니다. 

-   **지리적으로 분산 위치** -테 넌 트의 데이터 호스팅되는 지리적 위치입니다. 다중-지리적으로 분산 테 넌 트 예: 북미 및 유럽 둘 이상의 지리적 위치에 걸쳐 합니다.

-   **허용 된 데이터 위치 (ADL)** -을 테 넌 트에 구성 된 호스트 OneDrive와 SharePoint 데이터에 지리적 위치입니다.

-   **기본 설정 데이터 위치 (PDL)** -개별 사용자의 OneDrive 데이터가 저장 된 지리적 위치입니다. 관리자가 있는 테 넌 트에 대해 구성 된 허용 데이터 위치를 설정할 수 있습니다. OneDrive 사이트에 이미 있는 사용자에 대 한 PDL 변경 되는 경우 자신의 OneDrive 데이터 옮기지 않도록 새로운 지리적 위치에 자동으로 note 합니다. 자세한 내용은 [OneDrive 라이브러리를 다른 지리적 위치를 이동](move-onedrive-between-geo-locations.md) 을 참조 하십시오.

다중-지리적으로 분산을 사용 하도록 설정 4 개의 주요 단계를 수행 해야 합니다.

1.  _Office 365의 다중-지리적으로 분산 기능_ 서비스 계획을 추가 하려면 계정 팀과 함께 작동 합니다.

2.  원하는 대화 지리적 위치를 위성 및 테 넌 트에 추가 선택 합니다.

3.  원하는 위성 지리적 위치를 사용자의 기본 데이터 위치를 설정 합니다. 사용자에 대 한 새 OneDrive 사이트 구축, 될 때 해당 PDL를 프로 비전 됩니다.

4.  필요에 따라 기본 데이터 위치로 홈 위치에서 사용자의 기존 OneDrive 사이트를 마이그레이션하십시오.

이러한 각 단계에 대 한 자세한 내용은 [OneDrive 구성에 대 한 비즈니스 다중-지리적으로 분산을](multi-geo-tenant-configuration.md) 참조 하십시오.

> [!IMPORTANT]
> Note는 Office 365의 다중-지리적으로 분산 기능 성능 최적화 사례에 대 한 설계 되지 않았습니다, 데이터 residency 요구 사항을 충족 하도록 디자인 되었습니다. Office 365에 대 한 성능 최적화 하는 방법에 대 한 정보에 대 한 [네트워크 계획 및 성능 조정 Office 365에 대 한](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) 참조 또는 지원 그룹에 게 문의 합니다.

OneDrive 파일을 호스팅할 수 있는 위성 지리적 위치를 다음 위치 중 하나를 구성할 수 있습니다. 다중-지리적으로 분산을 계획할 때는 Office 365 테 넌 트에 추가 하려는 위치 목록을 확인 합니다. 필요한 경우 하나 또는 두 위성 위치로 시작 하 고 더 많은 지리적 위치를 점진적으로 확장 권장 합니다.

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
<td align="left">유럽 동쪽 중간 / / 아프리카</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">북미</td>
<td align="left">이름</td>
</tr>
<tr class="even">
<td align="left">오스트레일리아</td>
<td align="left">오스트레일리아</td>
</tr>
<tr class="odd">
<td align="left">캐나다</td>
<td align="left">수 있습니다.</td>
</tr>
<tr class="odd">
<td align="left">일본</td>
<td align="left">일본어</td>
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

예정 된 지리적 위치:
  
- 프랑스
- 인도

다중-지리적으로 분산을 구성 하는 경우에 Office 365로 마이그레이션하는 동안 온-프레미스 인프라를 통합 하 여 기회를 수행 하는 것이 좋습니다. 예, 싱가포르 및 말레이시아에서 온-프레미스 팜이 다음을 병합할 수 있습니다 APC 위성 위치에 데이터 residency 요구 사항을 사용 하면 그렇게 하면 제공 합니다.

## <a name="best-practices"></a>모범 사례

초기 테스트를 수행 하려면 Office 365의 테스트 사용자를 만드는 것이 좋습니다. 여기서 안내 일부 테스트 및 확인 단계가이 사용자와 온보드 프로덕션 사용자에 게 OneDrive 다중-지리적으로 분산 기능으로 진행 하기 전에 합니다.

테스트 사용자를 사용 하 여 테스트를 완료 한 후 새로운 지리적 위치에 OneDrive를 사용 하 여 처음에-IT 부서에서 아마도 파일럿 그룹-를 선택 합니다. 이 첫번째 그룹에 대 한 OneDrive 아직 없는 사용자를 선택 합니다. 이 초기 그룹에서 최대 5 개 까지만 사용자 것을 권장 합니다 하 고 점진적으로 일괄 처리 된 롤아웃 접근 방식에 따라를 확장 합니다.

각 사용자는 *기본 데이터 위치* (PDL) Office 365의 OneDrive를 프로 비전 하는 지리적으로 분산 위치에서 확인할 수 있도록 설정 해야 합니다. 사용자의 기본 데이터 위치는 선택한 위성 위치 나 중앙 위치 중 하 나와 일치 해야 합니다. PDL 필드는 필수가 아님을, 하는 동안 모든 사용자에 게는 PDL을 설정 하는 것 하는 것이 좋습니다. 다중-지리적으로 분산 논리에 따라 중앙 위치에는 PDL 없는 사용자의 작업 부하를 구축할 수 됩니다.   

사용자에 게 목록을 만들고 해당 사용자 계정 이름 (UPN) 하 고 적절 한 기본 설정된 데이터 위치에 대 한 위치 코드를 포함 합니다. 테스트 사용자 및 초기 파일럿 그룹을 시작 하 여 포함 됩니다. 구성 절차에 대 한이 목록에 필요 합니다.

사용자에 게는 온-프레미스 Active Directory (AD) 시스템에서을 Azure Active Directory (AAD)을 동기화 하는 경우에 Azure Active Directory 연결을 사용 하 여 동기화 된 사용자에 대 한 기본 설정된 데이터 위치를 설정 해야 합니다. Azure AD PowerShell을 사용 하 여 동기화 된 사용자에 대 한 기본 설정된 데이터 위치를 직접 구성할 수 없습니다. AD에서 PDL를 설정 하 고 동기화 하는 단계에 대해서는 설명 [Azure Active Directory 연결 동기화: Office 365 리소스에 대 한 기본 설정된 데이터 위치 구성](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)합니다.

지리적 다중 테 넌 트 관리에서 대부분의 SharePoint 및 OneDrive 설정으로 비 geo 다중 테 넌 다를 수 및 서비스는 다중-지리적으로 분산을 인식 합니다. 검토 하는 [다중-지리적으로 분산 환경 관리](administering-a-multi-geo-environment.md) 구성을 진행 하기 전에 것이 좋습니다.

다중-지리적으로 분산 환경에서 최종 사용자의 환경에 대 한 자세한 내용은 [multgeo 환경에서 사용자 경험](multi-geo-user-experience.md) 을 읽어보십시오.

OneDrive에 대 한 비즈니스 다중-지리적으로 분산 구성 시작 [OneDrive 구성에 대 한 비즈니스 다중-지리적으로 분산을](multi-geo-tenant-configuration.md)참조 하십시오.

(영문)의 기본 데이터 위치에서 사용자를 가져오는데 필요한 구성을 완료 했으면, [사용자의 OneDrive 라이브러리를](move-onedrive-between-geo-locations.md) 마이그레이션할 해야 합니다.
