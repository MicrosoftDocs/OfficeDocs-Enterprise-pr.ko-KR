---
title: Exchange Server GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 온-프레미스 Exchange Server에서 GDPR 요구 사항을 해결하는 방법을 알아보세요.
ms.openlocfilehash: cf6d670134bd4aab60b97cd9f55e69a21ce06b19
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-exchange-server"></a>Exchange Server GDPR

개인 정보 보호의 일환으로 다음을 권장합니다.

-   Exchange Server에서 [보존 태그 및 정책](https://technet.microsoft.com/library/dd297955(v=exchg.160).aspx)을 사용하여 이메일 수명 주기 정책을 구현합니다.

-   [정보 권한 관리](https://technet.microsoft.com/library/dd638140(v=exchg.160).aspx)를 배포하여 Exchange Server에 저장된 정보에 액세스할 수 있는 사용자를 제한합니다.

-   서버에서 [BitLocker 암호화](https://blogs.technet.microsoft.com/exchange/2015/10/20/enabling-bitlocker-on-exchange-servers/)를 사용하도록 설정합니다.

## <a name="identifying-in-scope-content"></a>범위 내 콘텐츠 식별

Exchange는 최종 사용자가 생성한 콘텐츠용으로 사서함과 공용 폴더라는 두 개의 기본 저장소 리포지토리를 사용합니다. 개별 사용자의 사서함에 저장된 콘텐츠는 해당 사용자에게 고유하게 연결되며 Exchange 내에서 기본 리포지토리를 나타냅니다. 사용자 사서함에 저장된 데이터는 Outlook, 웹용 Outlook(전 Outlook Web App), Exchange ActiveSync, 비즈니스용 Skype 클라이언트 및 POP, IMAP 또는 EWS(Exchange 웹 서비스)를 사용하여 Exchange 서버에 연결하는 기타 타사 도구를 통해 만든 콘텐츠를 포함합니다. 이러한 항목의 예는 다음과 같습니다. 메시지, 일정 항목(모임 및 약속), 연락처, 메모, 작업. 개별 사용자의 사서함을 삭제하면 사서함의 컨텍스트에서 사용자가 생성하거나 사용자에게 바로 보낸 콘텐츠가 제거됩니다. EAC(Exchange 관리 센터) 또는 Exchange 관리 셸에서 [Remove-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/remove-mailbox?view=exchange-ps) cmdlet을 사용하여 사용자 사서함을 삭제할 수 있습니다.
참고: 이 옵션을 사용하는 경우 데이터를 복구할 수 없으므로 Remove-Mailbox cmdlet의 Permanent 매개 변수는 주의해서 사용해야 합니다.

Exchange는 공통 사서함에 저장되어 있는 콘텐츠를 보내고 받는 액세스를 한 명 이상의 사용자에게 허용하는 공유 사서함도 제공합니다. 공유 사서함은 단일 계정과 연결되어 있지 않은 고유 엔터티입니다. 대신, 여러 사용자에게 공유 사서함에서 이메일 콘텐츠를 보내고 받고 검토할 액세스 권한이 부여됩니다. 공유 사서함은 Exchange 관리 센터 및 일반 사용자 사서함을 관리하는 데 사용되는 동일한 cmdlet을 사용하여 관리됩니다. 사서함에서 개별 메시지를 제거해야 하는 경우 Exchange 버전에 따라 사용할 수 있는 여러 가지 옵션이 있습니다. Exchange Server 2010 및 2013에서 사용할 수 있는 [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/search-mailbox?view=exchange-ps)와 DeleteContent 매개 변수를 사용하여 사서함에서 메시지를 식별하고 제거할 수 있습니다. Exchange Server 2016 이상에서는 [New-ComplianceSearch](https://technet.microsoft.com/library/ff459253(v=exchg.160).aspx) 기능을 사용해야 합니다.

공용 폴더는 특정 사용자와 연결되지 않은 공유 저장소 구현입니다. 대신, 사용자에게는 콘텐츠를 생성할 공용 폴더에 대한 액세스 권한이 부여됩니다. 공용 폴더의 실제 구현은 Exchange 버전에 따라 달라집니다(Exchange Server 2010은 Exchange Server 2013 이상과는 다른 구현을 사용). 공용 폴더의 콘텐츠를 관리하는 도구는 제한되어 있습니다. 클라이언트 도구(예: Outlook)는 공용 폴더의 콘텐츠를 관리하는 기본 메커니즘입니다. 공용 폴더 개체를 관리하는 cmdlet은 있지만 개별 콘텐츠 항목을 관리하는 cmdlet은 없습니다. 개별 공용 폴더 항목을 관리하려면 EWS(Exchange 웹 서비스) 또는 기타 타사 도구를 활용하는 사용자 지정 스크립트가 필요할 가능성이 큽니다.

기본 요구 사항은 개별 사용자 사서함 콘텐츠를 관리하는 사항일 가능성이 큽니다. 이 요구 사항은 사서함을 관리하는 데 정기적으로 사용하는 그래픽 또는 cmdlet 기반 도구를 통해 쉽게 해결할 수 있습니다. 여러 사서함 또는 리소스를 종류에서 콘텐츠를 처리해야 하는 경우, Exchange 내에서 범위 내 콘텐츠를 식별하는 기본 메커니즘은 [eDiscovery](https://technet.microsoft.com/library/dd298021(v=exchg.160).aspx)입니다.

## <a name="deleted-item-retention"></a>삭제된 항목 보존

사서함에서 (전체 사서함 또는 공용 폴더 리소스 자체가 아닌) 개별 메시지 또는 항목을 삭제할 때, 해당 콘텐츠는 사서함 데이터베이스 또는 공용 폴더 데이터베이스의 DeletedItemRetention 매개 변수 값에 따라 복구 가능한 형식으로 보존됩니다. 기본값은 14일이지만 Exchange 관리자가 이 값을 구성할 수 있습니다.

## <a name="removing-soft-deleted-and-disconnected-mailboxes"></a>일시 삭제되고 연결이 끊긴 사서함 제거

Exchange 사서함을 사용하지 않도록 설정하거나 삭제하거나 데이터베이스(예: 부하 분산의 일부로) 간에 이동하는 경우, 사서함은 작업에 따라 사용되지 않거나 일시 삭제되거나 연결이 끊긴 상태로 지정됩니다. 사서함이 이러한 상태인 경우, Exchange는 사서함 데이터베이스에 지정된 MailboxRetention 매개 변수의 현재 값에 따라 사서함(콘텐츠를 포함)을 유지합니다. 기본값은 30일이지만 Exchange 관리자가 이 값을 구성할 수 있습니다. [Remove-StoreMailbox](https://docs.microsoft.com/powershell/module/exchange/mailbox-databases-and-servers/remove-storemailbox?view=exchange-ps) cmdlet을 사용하여 보존 기간이 자연적으로 만료되기 전에 사서함과 연결된 모든 데이터를 영구적으로 제거하도록 Exchange를 강제로 적용합니다.

> [!IMPORTANT]
> Remove-StoreMailbox cmdlet은 대상 사서함의 복구할 수 없는 데이터 손실로 이어질 수 있으므로 주의해서 사용해야 합니다. 

## <a name="on-prem-to-cloud-migrations"></a>온-프레미스에서 클라우드 마이그레이션으로

Exchange Server에서 Exchange Online으로 데이터를 마이그레이션하는 동안, 마이그레이션한 데이터는 Exchange 관리자가 복구 가능한 형식으로 원본 온-프레미스 Exchange Server에 있을 수 있습니다. 기본적으로 이 데이터는 데이터베이스에서 30일 이내에 자동으로 제거됩니다(위의 일시 제거되고 연결이 끊긴 사서함 제거 섹션 참조).

## <a name="automatic-data-collection-reported-to-microsoft-by-exchange-server"></a>Exchange Server에서 Microsoft에 자동 데이터 수집 보고

온-프레미스 환경에 배포된 Exchange Server는 Microsoft에 어떤 유형의 자동화된 보고 또는 최종 사용자 데이터 캡처도 제공하지 않습니다. Windows 운영 체제에서 Watson 충돌 덤프 보고를 사용하도록 설정된 Exchange Server는 충돌 보고서가 생성되는 시점에 제한된 메모리 콘텐츠를 받을 수 있습니다.
