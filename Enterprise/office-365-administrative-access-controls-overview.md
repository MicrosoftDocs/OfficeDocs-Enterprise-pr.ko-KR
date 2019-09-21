---
title: Office 365 관리 액세스 권한 컨트롤
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: '요약: Office 365의 관리 액세스 제어 및 데이터 분류에 대 한 개요입니다.'
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067709"
---
# <a name="administrative-access-controls-in-office-365"></a>Office 365 관리 액세스 권한 컨트롤 

Microsoft는 Microsoft의 고객 콘텐츠에 대 한 액세스를 의도적으로 제한 하면서 대부분의 Office 365 운영을 자동화 하는 시스템 및 컨트롤에 크게 투자 했습니다. 서비스를 관리 하 고 소프트웨어가 서비스를 운영 하는 사람입니다. 이를 통해 Microsoft는 확장 시에 Office 365을 관리 하 고 고객 콘텐츠에 대 한 내부 위협의 위험을 관리할 수 있습니다.

기본적으로 Microsoft 엔지니어가 관리 권한을 보유 하 고 있으며 Office 365의 고객 콘텐츠에 대 한 액세스 권한이 제로입니다. 제한 된 기간 동안 Microsoft 엔지니어가 고객 콘텐츠에 대 한 액세스를 제한 하 고 감사 하 고 보안을 유지할 수 있습니다. 액세스는 서비스 작업에 필요한 경우에만 사용 되며 Microsoft의 선임 관리 구성원이 승인 하는 경우에만 가능 합니다. 고객 인증 키 저장소 사용이 허가 된 고객의 경우, 고객은 Office 365에서 호스트 되는 콘텐츠에 대 한 액세스 승인을 제공 합니다.

Microsoft는 다양 한 형태의 클라우드 전달을 사용 하 여 온라인 서비스를 제공 합니다.

- **공용 클라우드:** 여러 테 넌 트 버전의 Office 365, Azure 및 북미, 남미, 유럽, 아시아, 오스트레일리아 등에 호스트 되는 기타 서비스를 포함 합니다.
- **국가 클라우드:** 이전에 언급 한 것을 제외 하 고 미국 외부에서 운영 하는 모든 sovereign 클라우드에 및 타사에서 작동 하는 모든 클라우드 (중국에서 운영 하는 Office 365) 및 독일의 Office 365 (예: Microsoft에서 운영 하지만 독일어 데이터를 트러스티로 제공 되는 모델에서)을 포함 합니다. Deutsche Telekom, Microsoft의 고객 데이터 및 고객 데이터를 포함 하는 시스템에 대 한 액세스를 제어 하 고 모니터링 합니다.
- **정부 클라우드:** 미국 정부 고객에 게 제공 되는 Office 365 및 Azure 서비스를 포함 합니다.

이 문서에서 제공 하는 Office 365 서비스에는 다음이 포함 됩니다.

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [비즈니스용 OneDrive](https://docs.microsoft.com/OneDrive/onedrive)
- [비즈니스용 Skype](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a>Office 365 액세스 제어

액세스 제어를 위해 Microsoft는 Office 365 데이터를 고객 데이터 또는 기타 데이터 형식으로 분류 합니다.

### <a name="customer-data"></a>고객 데이터

고객 데이터는 Office 365 서비스를 사용할 때 또는 고객을 대신 하 여 제공 하는 모든 데이터입니다. 다음을 포함 하 여 Office 365 사용자가 직접 만들거나 업로드 한 고객 콘텐츠입니다.

- 전자 메일
- SharePoint Online 콘텐츠
- 인스턴트 메시지
- 일정 항목
- 문서
- Contacts
- EUII (최종 사용자 식별 정보) (사용자가 고유 하거나 개별 사용자에 게 linkable 하지만 고객 콘텐츠를 포함 하지 않는 데이터)

### <a name="other-types-of-data"></a>기타 데이터 형식

다른 데이터 형식에는 다음이 포함 됩니다.

- **계정 데이터:** 관리 데이터 (관리자가 서비스를 등록 하거나 구매할 때 제공 하는 정보) 및 지불 데이터 (신용 카드 정보와 같은 결제 방식 정보)를 포함 합니다.
- **조직 차원 식별이 가능한 정보:** 테 넌 트, 사용 현황 데이터를 식별 하 고 개별 사용자에 게 linkable 하는 데 사용 되거나 고객 콘텐츠에 포함 되지 않은 데이터를 포함 합니다.
- **시스템 메타 데이터:** 구성 설정, 시스템 상태, Microsoft IP 주소 및 구독 및 테 넌 트에 대 한 기술 정보가 포함 된 서비스 로그를 포함 합니다.

Microsoft는 고객 데이터 또는 액세스 제어 데이터에 대 한 승인 되지 않은 액세스를 사용 하지 않도록 액세스 제어 메커니즘을 설정 했습니다. 액세스 제어 데이터는 고객 콘텐츠 또는 EUII, Microsoft 암호, 보안 인증서 및 기타 인증 관련 데이터에 대 한 액세스를 포함 하 여 환경 내에서 다른 유형의 데이터 또는 기능에 대 한 액세스를 관리 합니다. 또한 액세스 제어 메커니즘은 Office 365 프로덕션 환경에 대 한 승인 되지 않은 물리적, 논리적 또는 원격 액세스를 보호 합니다.

Office 365에는 Microsoft에서 사용 하는 세 가지 종류의 access 컨트롤이 있습니다.

- 격리 컨트롤
- 인적 컨트롤
- 기술 컨트롤

이러한 컨트롤을 결합 하면 Office 365에서 악의적인 작업을 방지 하 고 검색할 수 있습니다. Microsoft에서 사용 하는 격리, 인력 및 기술 제어 외에도 customer에서 구현 하는 컨트롤의 네 번째 범주를 사용할 수 있습니다.

Office 365에서는 온-프레미스 환경에서 데이터를 관리 하는 것과 동일한 방식으로 데이터를 관리할 수 있습니다. Office 365 조직에 등록 하는 사람은 자동으로 전역 관리자가 됩니다. 전역 관리자는 관리 포털의 모든 기능에 액세스할 수 있으며 다음이 가능 합니다.

- 사용자 만들기 또는 편집
- 다른 사용자에 게 관리자 역할 할당
- 사용자 암호 다시 설정
- 사용자 라이선스 관리
- 도메인 관리
- 고객 Lockbox 요청 승인

각 조직에서는 최소 두 개의 관리자 계정을 구성 하는 것이 좋습니다. 대규모 엔터프라이즈 조직의 경우 다른 기능을 제공 하는 특수 한 관리자 계정을 사용 하는 것이 좋습니다.

관리자 역할 및 사용 권한을 할당 하는 방법에 대 한 자세한 내용은 [office 365의 관리자 역할 할당](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) 및 [office 365 관리자 역할 정보](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D)를 참조 하세요.

## <a name="related-links"></a>관련 링크

- [격리 컨트롤](office-365-isolation-controls.md)
- [인적 컨트롤](office-365-personnel-controls.md)
- [기술 컨트롤](office-365-technology-controls.md)
- [액세스 제어 모니터링 및 감사](office-365-monitoring-and-auditing-access-controls.md)
- [Yammer Enterprise 액세스 제어](office-365-yammer-enterprise-access-controls.md)