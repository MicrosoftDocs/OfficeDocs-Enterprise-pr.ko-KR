---
title: 데이터 이동 일반 FAQ
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: 다음은 핵심 데이터를 새 데이터 센터 지역으로 이동 하는 방법에 대 한 일반적인 질문에 대 한 대답입니다.
ms.openlocfilehash: 9e391a1b43ef1a11d9da72b7f78ecf35fd084c90
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028892"
---
# <a name="data-move-general-faq"></a>데이터 이동 일반 FAQ

다음은 핵심 데이터를 새 데이터 센터 지역으로 이동 하는 방법에 대 한 일반적인 질문에 대 한 대답입니다.
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>이동을 요청할 수 있는 고객은 무엇입니까?
  
기존 Office 365 상업용 고객은 새 데이터 센터 지역에 적합 한 국가를 선택한 경우 이동을 요청할 수 있습니다.  이 프로그램은 Office 365 테 넌 트에 할당 된 적격 국가 코드가 있는 테 넌 트에만 해당 Office 365 데이터 센터 geo에 적합 한 작업을 위해 rest에서 핵심 고객 데이터를 마이그레이션합니다.  국가 자격 확인 [방법은 데이터 이동을 요청 하는 방법](request-your-data-move.md) 페이지를 참조 하세요.   

## <a name="how-do-we-define-core-customer-data"></a>핵심 고객 데이터를 정의 하려면 어떻게 해야 합니까?
 
핵심 고객 데이터는 [Microsoft Online Services 조항](https://go.microsoft.com/fwlink/p/?LinkID=249048)에 정의 된 고객 데이터의 하위 집합을 지칭 하는 용어입니다. 
- Exchange Online 사서함 콘텐츠 (전자 메일 본문, 일정 항목 및 전자 메일 첨부 파일 콘텐츠)
- SharePoint Online 사이트 콘텐츠 및 해당 사이트 내에 저장 된 파일
- 비즈니스용 OneDrive에 업로드 된 파일 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>내 테 넌 트의 핵심 고객 데이터가 새 geo의 나머지 위치에 저장 되도록 내 마이그레이션이 완료 되는 점은 무엇입니까?

Exchange Online과 SharePoint Online/비즈니스용 OneDrive 간의 공유 종속성으로 인해 모든 마이그레이션은 두 서비스가 마이그레이션될 때까지 완료 된 것으로 간주할 수 없습니다.  Exchange Online 및 SharePoint Online/비즈니스용 OneDrive는 서로 독립적으로 마이그레이션하는 경우가 많습니다.  각 서비스 마이그레이션이 완료 되 고 언제 든 지 관리자 센터에서 데이터 위치 카드를 확인 하 여 각 서비스에 대 한 rest 위치에서 핵심 고객 데이터를 확인할 수 있는 테 넌 트 관리자가 메시지 센터에서 인증을 받습니다.

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>테 넌 트가 자동으로 새 데이터 센터 지역으로 이동 됩니까?
 
테 넌 트 관리자는 두 가지 작업을 수행할 수 있습니다.

- 옵트인Office 365 Move 프로그램에 등록 하 고 서비스에서 주요 고객 데이터를 새 데이터 센터 지역으로 마이그레이션하기 위한 커밋된 마감 기한을 받습니다.프로그램 옵트인 방법에 대 한 지침은 [데이터 이동을 요청 하는 방법](request-your-data-move.md) 페이지를 참조 하세요.
- 아무 작업도 하지 않음.작업을 수행 하지 않으면 Microsoft에서 서비스 관리 및 최적화의 일환으로 시간에 따라 핵심 고객 데이터를 새로운 데이터 센터 지역으로 이동할 수 있습니다.데이터는 다른 geo가 아닌 새 데이터 센터 지역으로만 이동할 수 있습니다.이러한 서비스 관리 이동이 완료 되 면 메시지 센터를 통해 알려 드리겠습니다.

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>이동 중에 내 고객 데이터를 안전 하 게 보호 하 고 가동 중지 시간이 발생 하지 않도록 하려면 어떻게 해야 합니까?
  
데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 서비스 작업입니다. 영향을 받을 수 있는 기능은 [데이터 이동 중 및 후](during-and-after-your-data-move.md)에 나열 됩니다. 가용성을 위해 [Microsoft Online SERVICES SLA (서비스 수준 계약)](https://go.microsoft.com/fwlink/p/?LinkId=523897) 를 준수 하 고, 고객이 이동 중에 대비 하거나 모니터링 해야 하는 작업이 없습니다. 
  
모든 Office 365 서비스는 데이터 센터에서 동일한 버전이 실행되므로 일관된 기능이 보장될 수 있습니다. 서비스는 프로세스 전반에 걸쳐 완벽하게 지원됩니다.
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>서로 다른 온-os에 다른 서비스가 있는 경우의 영향은 무엇입니까?

일부 Office 365 서비스는 일부 기존 고객 및 이동 프로세스의 중심에 있는 고객을 위해 다른 지역에 있을 수 있습니다.  서비스는 서로 독립적으로 실행 되며,이 경우 사용자 환경에는 영향을 주지 않습니다.그러나 데이터 상주 목적으로 Exchange Online과 SharePoint Online/비즈니스용 OneDrive를 모두 동일한 데이터 센터 지역으로 마이그레이션할 때까지 테 넌 트 마이그레이션을 완료로 간주할 수 없습니다.
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>새 Office 365 고객은 새 데이터 센터 geos에서 자동으로 프로 비전 됩니까?
  
예. 새 데이터 센터 geo를 사용할 수 있게 되 면 새 지역에 등록 하는 동안 국가를 선택 하는 비즈니스 고객을 위한 새 Office 365는 새 데이터 센터 지리적으로 나머지 지역의 핵심 고객 데이터를 보관 합니다.
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>내 핵심 고객 데이터는 어디에 있나요?

테 넌 트 관리자는 언제 든 지 관리자 센터에서 데이터 위치 카드를 확인 하 여 각 서비스의 rest 위치에서 핵심 고객 데이터를 확인할 수 있습니다 (특히 테 넌 트의 경우).또한 [ office 365 대화형 데이터 센터](https://office.com/datamaps) 의 office 365 customer 데이터 센터의 위치를 새 테 넌 트의 rest 위치에 있는 현재 기본 핵심 고객 데이터에 대 한 참조로 게시 합니다.  Microsoft 365 관리 센터에서 조직 프로필의 데이터 위치 섹션을 통해 rest에서 고객 데이터의 위치를 확인할 수 있습니다.  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>이동을 요청할 수 있는 시기는 언제 입니까?
  
데이터 센터 지역에 대해 지원 되는 기간에 대 한 [정보 이동을 요청 하는 방법](request-your-data-move.md) 페이지를 참조 하세요.
  
## <a name="how-can-i-request-to-be-moved"></a>이동 요청을 확인 하려면 어떻게 해야 합니까?
  
적격 고객은 [Office 365 관리자 포털](https://portal.office.com/)에 페이지를 볼 수 있습니다. 이동을 요청 하는 방법에 대 한 지침은 [데이터 이동을 요청 하는 방법을](request-your-data-move.md) 참조 하세요. 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>이동을 요청 하 고 나 서 선택을 변경할 수 있습니까?
  
요청을 제출한 후에는 프로세스에서 사용자를 제거할 수 없습니다.
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>마감 시간 전에 이사를 요청 하지 않은 경우 어떻게 되나요?
  
 이 경우에는 예외 기준에 대 한 요청을 수락 하 여 테 넌 트에 이동을 완료 하기 위해 커밋된 마감 기한을 부여할 수 있습니다.  [Office 365 지원](https://go.microsoft.com/fwlink/p/?LinkID=522459) 서비스에 문의 하 여 요청을 받으십시오.  Microsoft에서 서비스 관리 및 최적화의 일환으로 남은 시간에 따라 핵심 고객 데이터를 새 데이터 센터 지역으로 이동할 수 있으므로, 일부 작업은 옵트인 요청이 없어도 신규 지역으로 이동할 수 있습니다.데이터는 다른 geo가 아닌 새 데이터 센터 지역으로만 이동할 수 있습니다.  이러한 서비스 관리 이동이 완료 되 면 메시지 센터를 통해 알려 드리겠습니다.
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>네트워크 성능을 개선 하기 위해 데이터를 이동 하려는 경우에는 어떻게 하나요?
  
Office 365 데이터 센터에 가까워진다고 해서 더 나은 네트워킹 성능이 보장되는 것은 아닙니다. 최종 사용자와 Office 365 서비스 간의 네트워크 성능에 영향을 미치는 요인 및 구성 요소는 많습니다. 이 및 성능 조정에 대 한 자세한 내용은 [Office 365의 네트워크 계획 및 성능 조정을](network-planning-and-performance.md)참조 하세요.
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>모든 서비스가 같은 날에 데이터를 이동 합니까?
 
각 서비스는 독립적으로 이동 되며 데이터를 서로 다른 시간에 이동할 수 있습니다.
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>데이터 이동 여부를 선택할 수 있습니까?
 
 Microsoft는 이동의 구체적 날짜나 기간을 알려드릴 수 없습니다.
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>데이터를 이동 하는 경우 공유할 수 있습니까?
  
데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 작업입니다. 전체적으로 운영되는 자동화 환경에서 데이터 이동을 수행할 때 수반되는 복잡성, 정밀도 및 규모 때문에 귀하의 테넌트 또는 다른 단일 테넌트에서 데이터 이동이 완료될 것으로 예상되는 시기를 알려드리기가 어렵습니다. 고객은 데이터 이동이 완료되었을 때 메시지 센터에서 관련 서비스별로 1번의 확인을 받게 됩니다. 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>사용자가 데이터를 이동 하는 동안 서비스에 액세스 하면 어떻게 되나요?

각 서비스에 대 한 데이터 이동 중에 제한 될 수 있는 전체 기능 목록에 대 한 [데이터 이동 중 및 후](during-and-after-your-data-move.md) 를 확인 합니다. 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>이동이 완료 되었는지 어떻게 알 수 있나요?
  
각 서비스 데이터의 이동이 완료 되었는지 확인 하는 Office 365 메시지 센터를 시청 합니다. 각 서비스의 데이터를 이동 하면 완료 알림을 게시 하 여 Exchange Online, SharePoint Online 및 비즈니스용 Skype Online에 대 한 세 가지 완료 알림을 받게 됩니다.  Microsoft 365 관리 센터에서 조직 프로필 아래의 데이터 위치 섹션을 통해 rest에서 고객 데이터의 위치를 확인할 수도 있습니다.  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Office 365 고객은 새 데이터 센터의 geos 중 하나에서, 등록을 마친 후 다른 국가를 선택 했습니다. 새 데이터 센터 지역으로 이동 하려면 어떻게 해야 합니까?

테 넌 트와 연결 된 등록 국가는 변경할 수 없습니다. 대신 새 구독을 사용 하 여 새 Office 365 테 넌 트를 만들고 사용자와 데이터를 새 테 넌 트로 수동으로 이동 해야 합니다.
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>Exchange Online 이동 중에 전자 메일 데이터를 Office 365로 마이그레이션하는 프로세스를 진행 하는 경우 어떻게 되나요?

이는 매우 일반적인 시나리오로, 완벽 하 게 지원 됩니다.  데이터 센터의 클라우드 마이그레이션은 클라우드 사서함 마이그레이션에 영향을 주지 않습니다.
  
 ## <a name="can-i-pilot-some-users"></a>일부 사용자를 파일럿 할 수 있습니까?
  
별도의 평가판 테 넌 트를 만들어 연결을 테스트할 수 있지만 평가판 테 넌 트를 기존 테 넌 트와 함께 조합 하 여 사용 하면 안 됩니다.

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Microsoft가 내 데이터를 이동 하는 것을 기다리지 않으려고 합니다. 방금 새 테 넌 트를 만들고 자신을 이동할 수 있나요?
  
그렇지만 Microsoft가 데이터 이동을 수행하는 것처럼 프로세스가 원활하지 않을 수 있습니다.
  
새 데이터 센터 geo를 사용할 수 있는 경우 새 테 넌 트를 만드는 경우 새 테 넌 트가 새 지역에서 호스팅됩니다. 이 새 테넌트는 이전 테넌트와 완전히 별도이며, 모든 사용자 사서함, 콘텐츠 사이트, 도메인 이름 및 다른 데이터를 이동하는 일은 사용자가 처리해야 합니다. 한 테넌트에서 다른 테넌트로 테넌트 이름을 이동할 수는 없습니다. Microsoft는 사용자의 모든 설정, 데이터 및 구독의 이동을 관리하므로 Microsoft에서 제공하는 이동 프로그램을 기다리는 것이 좋습니다.
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>이동할 준비가 되지 않아 특정 이동 날짜를 선택할 수 있나요?
  
아니요, 각 서비스의 핵심 고객 데이터가 이동 되는 시간을 변경할 수 없습니다.
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>내 고객 데이터가 이미 새 데이터 센터 지역으로 이동 되었습니다. 뒤로 이동할 수 있나요?
 
아니요, 이것이 가능 하지 않습니다. 새 지리적 데이터 센터로 이동한 고객은 다시 이동할 수 없습니다. 모든 지역에 있는 고객은 이전에 했던 것과 동일한 서비스 품질, 성능 및 보안 제어 기능을 경험할 수 있습니다.  [Office 365](https://aka.ms/multi-geo) 일부 고객은 추가 기능을 사용 하 여 단일 테 넌 트를 통해 여러 위성 지역를 만들고 데이터 상주 약정을 사용 하 여 사용자 데이터를 해당 지역로 이동할 수 있습니다.
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>새 데이터 센터에서 현재 데이터 센터가 있는 것과 동일한 버전의 Office 365 서비스를 사용 하 고 있습니까?

예.
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>새 데이터 센터에서 호스트 되는 Office 365 테 넌 트를 해당 국가의 외부 사용자가 사용할 수 있나요?
  
A. 예. Microsoft는 2700 전 세계의 35 국가에서 130 개 보다 많은 인터넷 연결을 사용 하는 대규모 글로벌 네트워크를 유지 관리 합니다. 사용자는 인터넷에 있는 모든 위치에서 데이터 센터에 액세스할 수 있습니다.

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>내 테 넌 트가 [Office 365 다중 지역](https://aka.ms/multi-geo)에 대해 구성 되어 있습니다.  Office 365 Move 프로그램에서 내 테 넌 트를 계속 해 서 등록 하 여 기본 지역을 변경 하 고 위성 지역에 있지 않은 모든 사용자를 새 기본 지역으로 이동할 수 있나요?

예, 테 넌 트가 등록할 수 있습니다.  현재 기본 지역에서 새 로컬 데이터 센터 지역으로 모든 EXO 사서함을 이동 합니다.  사용자가 원하는 대로 위성 지역 데이터 상주를 계속 사용할 수 있도록 다중 지역 위성 지역에 구성 된 EXO 사서함을 이동 하지 않습니다.  SharePoint Online 및 비즈니스용 OneDrive는 이동 프로그램의 일부로 새 데이터 센터 지역으로 마이그레이션할 수 없지만, 비즈니스용 OneDrive 공유가 다중 지리적 프로그램을 통해 원하는 지역으로 이동 하도록 구성할 수도 있습니다.
  
## <a name="related-topics"></a>관련 항목

[핵심 데이터를 새 Office 365 데이터 센터 지역으로 이동](moving-data-to-new-datacenter-geos.md)

[데이터 이동을 요청하는 방법](request-your-data-move.md)

[Office 365 다중 지역](https://aka.ms/multi-geo)

[Office 365 대화형 데이터 센터 맵](https://office.com/datamaps)

[Office 365 지원](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Microsoft Dynamics CRM Online에 대 한 새로운 데이터 센터 지역](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[지역별 Azure services](https://azure.microsoft.com/regions/)
