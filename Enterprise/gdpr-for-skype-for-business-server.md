---
title: 비즈니스용 Skype 서버 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 온-프레미스 비즈니스용 Skype 서버 및 Lync Server에서 GDPR 요구 사항을 해결하는 방법을 알아보세요.
ms.openlocfilehash: eac57a7044a5eeb828857c7aabd15c5ca1443c96
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-skype-for-business-server-and-lync-server"></a>비즈니스용 Skype 서버 및 Lync Server GDPR

대부분의 비즈니스용 Skype 서버 및 Lync Server 데이터는 Exchange Server에 저장됩니다. 여기에는 다음이 포함됩니다.

-   대화 기록

-   음성 메일 알림 및 대화 내용

-   모임 초대

[Exchange Server GDPR](gdpr-for-exchange-server.md)에 대해 설명하는 절차를 사용하여 GDPR 요청에 이러한 형식의 데이터를 찾고 내보내고 삭제합니다.

연락처 목록은 SQL Server 데이터베이스에 저장되며, 다음과 같은 방법으로 내보낼 수 있습니다.

-   최종 사용자가 그룹 머리글을 마우스 오른쪽 단추로 클릭하고 복사를 선택하여 연락처를 직접 내보낼 수 있습니다. 그러면 해당 그룹의 모든 연락처가 클립보드에 복사되고, 그 후에는 원하는 앱에 붙여넣을 수 있습니다.

-   [Export-CsUserData](https://docs.microsoft.com/ko-KR/powershell/module/skype/export-csuserdata) cmdlet을 사용하여 이 데이터를 내보낼 수 있습니다.

모임에 업로드된 콘텐츠(예: PowerPoint 파일 또는 유인물) 또는 모임에서 생성된 콘텐츠(화이트보드, 설문 조사 또는 질문 및 답변)는 파일러(filer)에 저장됩니다. 이는 최종 사용자가 만료되지 않은 한 모임에 다시 로그인하고 업로드된 콘텐츠를 다운로드하거나 생성된 콘텐츠의 경우 스크린샷을 찍을 경우 내보낼 수 있습니다.

Exchange 일정 및 연락처 목록 및 연락처 권한(가족, 동료 등)에 없는 MeetNow 모임은 사용자 데이터베이스에 있습니다. Lync Server 2013 이상에서는 [Export-CsUserData](https://docs.microsoft.com/ko-KR/powershell/module/skype/export-csuserdata) cmdlet을 사용하여 이 데이터를 내보낼 수 있습니다.
