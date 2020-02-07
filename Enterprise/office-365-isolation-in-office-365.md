---
title: Office 365의 office 365 격리 및 액세스 제어
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
- SPO_Content
f1.keywords:
- NOCSH
description: '요약: Office 365의 다양 한 응용 프로그램 내에서 격리 및 액세스 제어에 대 한 설명입니다.'
ms.openlocfilehash: 2cf98480a2a3f5d202198c9056ecb46d281e1a3e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844409"
---
# <a name="isolation-and-access-control-in-office-365"></a>Office 365에서 격리 및 액세스 제어

Azure Active Directory 및 Office 365에서는 수십 개의 서비스, 수백 개의 엔터티, 수천 개의 관계 및 수백만 개의 특성을 포함 하는 고도로 복잡 한 데이터 모델을 사용 합니다. 높은 수준에서 Azure Active Directory 및 서비스 디렉터리는 상태 기반 복제 프로토콜을 사용 하 여 동기화 된 테 넌 트 및 받는 사람의 컨테이너입니다. Azure Active Directory 내에 보관 된 디렉터리 정보 외에도 각 서비스 작업에는 자체 디렉터리 서비스 인프라가 있습니다.
 
![Office 365 테 넌 트 데이터 동기화](media/office-365-isolation-tenant-data-sync.png)

이 모델 내에는 단일 디렉터리 데이터 원본이 없습니다. 특정 시스템은 개별 데이터를 소유 하지만 단일 시스템에는 모든 데이터가 저장 되지 않습니다. Office 365 서비스가이 데이터 모델의 Azure Active Directory와 공동으로 사용 됩니다. Azure Active Directory는 공유 데이터 (일반적으로 모든 서비스에서 사용 되는 작고 정적 데이터)에 대 한 "시스템 확정"입니다. Office 365 및 Azure Active Directory 내에서 사용 되는 페더레이션 모델은 데이터의 공유 보기를 제공 합니다.

Office 365에서는 실제 저장소 및 Azure 클라우드 저장소를 모두 사용 합니다. Exchange Online (Exchange Online Protection 포함) 및 비즈니스용 Skype는 고객 데이터에 대 한 자체 저장소를 사용 합니다. SharePoint Online은 SQL Server 저장소 및 Azure 저장소를 모두 사용 하므로, 저장소 수준에서 고객 데이터를 추가로 격리 해야 합니다.

## <a name="exchange-online"></a>Exchange Online

Exchange Online은 고객 데이터를 사서함에 저장 합니다. 사서함은 사서함 데이터베이스 라고 하는 ESE (Extensible Storage Engine)의 데이터베이스 내에서 호스팅됩니다. 여기에는 사용자 사서함, 연결 된 사서함, 공유 사서함 및 공용 폴더 사서함이 포함 됩니다. 사용자 사서함에는 대화 기록과 같은 저장 된 비즈니스용 Skype 콘텐츠가 포함 됩니다.

사용자 사서함 내용에는 다음이 포함 됩니다.

- 메일 및 전자 메일 첨부 파일
- 일정 및 약속 있음/없음 정보
- Contacts
- 작업
- Notes
- 그룹
- 유추 데이터

Exchange Online 내의 각 사서함 데이터베이스에는 여러 테 넌 트의 사서함이 포함 됩니다. 인증 코드는 테 넌 시에 포함 된 각 사서함을 보호 합니다. 기본적으로 할당 된 사용자만 사서함에 액세스할 수 있습니다. 사서함을 보안 하는 ACL (액세스 제어 목록)에 테 넌 트 수준에서 Azure Active Directory에 의해 인증 된 id가 포함 되어 있습니다. 각 테 넌 트에 대 한 사서함은 테 넌 트의 사용자만을 포함 하는, tenant의 인증 공급자에 대해 인증 된 id로 제한 됩니다. 테 넌 트의 콘텐츠를 테 넌 트 B의 사용자가 어떠한 방식으로도 가져올 수 없습니다.

## <a name="skype-for-business"></a>비즈니스용 Skype

비즈니스용 Skype에는 다음과 같은 다양 한 위치에 데이터가 저장 됩니다.

- 연결 끝점, 테 넌 트 Id, 다이얼 플랜, 로밍 설정, 현재 상태, 연락처 목록 등을 포함 하는 사용자 및 계정 정보는 비즈니스용 Skype Active Directory 서버 및 다양 한 비즈니스용 Skype 데이터베이스 서버에 저장 됩니다. 연락처 목록은 사용자가 두 제품을 사용할 수 있거나 사용자가 없는 경우 비즈니스용 Skype 서버를 사용 하도록 설정 된 경우 사용자의 Exchange Online 사서함에 저장 됩니다. 비즈니스용 Skype 데이터베이스 서버는 테 넌 트 별로 분할 되지 않지만 다중 테 넌 시 데이터 격리는 RBAC (역할 기반 액세스 제어)를 통해 적용 됩니다.
- 모임 콘텐츠 및 업로드 된 데이터는 DFS (분산 파일 시스템) 공유에 저장 됩니다. 사용 하도록 설정 된 경우 Exchange Online에이 콘텐츠를 보관할 수도 있습니다. DFS 공유는 테 넌 트 당 분할 되지 않습니다. 콘텐츠가 Acl을 사용 하 여 보호 되 고 다중 테 넌 시가 RBAC를 통해 적용 됩니다.
- 통화 기록, IM 세션, 응용 프로그램 공유, IM 기록 등과 같은 활동 기록은 Exchange Online에도 저장할 수 있지만 대부분의 통화 정보 레코드는 CDR (통화 정보 기록) 서버에 일시적으로 저장 됩니다. 콘텐츠는 테 넌 트 별로 분할 되지 않지만 다중 테 넌 시는 RBAC를 통해 적용 됩니다.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online에는 데이터 격리를 제공 하는 몇 가지 독립적인 메커니즘이 있습니다. 응용 프로그램 데이터베이스에서 개체를 추상화 된 코드로 저장 합니다. 예를 들어 사용자가 SharePoint Online에 파일을 업로드 하면 파일이 분해 되 고 응용 프로그램 코드로 변환 되며 여러 데이터베이스에 걸쳐 여러 테이블에 저장 됩니다.

사용자가 데이터를 포함 하는 저장소에 직접 액세스 하는 경우에는 콘텐츠를 SharePoint Online이 아닌 사람이 나 다른 시스템으로 해석할 수 없습니다. 이러한 메커니즘에는 보안 액세스 제어 및 속성이 포함 됩니다. 모든 SharePoint Online 리소스는 테 넌 시를 포함 하 여 인증 코드 및 RBAC 정책에 의해 보호 됩니다. 리소스를 보안 하는 ACL (액세스 제어 목록)에 테 넌 트 수준에서 인증 된 id가 포함 되어 있습니다. 테 넌 트에 대 한 SharePoint Online 데이터는 테 넌 트에 대 한 인증 공급자가 인증 한 id로만 제한 됩니다.

Acl 외에도 인증 공급자 (테 넌 트 별 Azure Active Directory)를 지정 하는 테 넌 트 수준 속성은 한 번 작성 되며 일단 설정 된 후에는 변경할 수 없습니다. 테 넌 트에 대해 authentication provider 테 넌 트 속성을 설정한 후에는 테 넌 트에 제공 된 Api를 사용 하 여 변경할 수 없습니다.

각 테 넌 트에 대해 고유한 *SubscriptionId* 가 사용 됩니다. 모든 고객 사이트는 테 넌 트에서 소유 하 고 테 넌 트에 고유한 *SubscriptionId* 를 할당 합니다. 사이트의 *SubscriptionId* 속성은 영구 기록 됩니다. 일단 테 넌 트에 할당 되 면 사이트를 다른 테 넌 트로 이동할 수 없습니다. *SubscriptionId* 는 인증 공급자에 대 한 보안 범위를 만드는 데 사용 되는 키 이며 테 넌 트에 연결 됩니다.

SharePoint Online에서는 콘텐츠 메타 데이터 저장소에 대해 SQL Server 및 Azure 저장소를 사용 합니다. 콘텐츠 저장소의 파티션 키는 SQL의 *SiteId* 입니다. SQL 쿼리를 실행 하는 경우 SharePoint Online은 테 넌 트 수준 *SubscriptionId* 확인의 일부로 확인 된 *SiteId* 를 사용 합니다.

SharePoint Online은 Microsoft Azure blob에 암호화 된 파일 콘텐츠를 저장 합니다. 각 SharePoint Online 팜에는 자체 Microsoft Azure 계정이 있으며 Azure에 저장 된 모든 blob는 SQL 콘텐츠 저장소에 저장 된 키를 사용 하 여 개별적으로 암호화 됩니다. 인증 계층에 의해 코드에 보호 되는 암호화 키가 최종 사용자에 게 직접 표시 되지 않습니다. SharePoint Online에는 HTTP 요청이 두 개 이상의 테 넌 트에 대 한 데이터를 읽거나 쓰는 시간을 검색 하는 실시간 모니터링이 있습니다. 요청 id *subscriptionid* 는 액세스 되는 리소스의 *subscriptionid* 에 따라 추적 됩니다. 여러 테 넌 트의 리소스에 액세스 하는 요청은 최종 사용자가 수행 하지 않아야 합니다. 다중 테 넌 트 환경의 서비스 요청은 유일한 예외입니다. 예를 들어 검색 크롤러는 전체 데이터베이스에 대 한 콘텐츠 변경 내용을 한 번에 가져옵니다. 이는 일반적으로 두 개 이상의 테 넌 트의 사이트를 단일 서비스 요청에 쿼리 하는 것과 관련 하 여 효율성을 이유로 수행 됩니다.
