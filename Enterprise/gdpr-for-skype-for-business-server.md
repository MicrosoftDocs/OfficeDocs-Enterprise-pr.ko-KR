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
# <a name="gdpr-for-skype-for-business-server-and-lync-server"></a><span data-ttu-id="fb105-103">비즈니스용 Skype 서버 및 Lync Server GDPR</span><span class="sxs-lookup"><span data-stu-id="fb105-103">GDPR for Skype for Business Server and Lync Server</span></span>

<span data-ttu-id="fb105-p101">대부분의 비즈니스용 Skype 서버 및 Lync Server 데이터는 Exchange Server에 저장됩니다. 여기에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb105-p101">Most Skype for Business Server and Lync Server data is stored in Exchange Server. This includes:</span></span>

-   <span data-ttu-id="fb105-106">대화 기록</span><span class="sxs-lookup"><span data-stu-id="fb105-106">Conversation History</span></span>

-   <span data-ttu-id="fb105-107">음성 메일 알림 및 대화 내용</span><span class="sxs-lookup"><span data-stu-id="fb105-107">Voicemail notifications and transcriptions</span></span>

-   <span data-ttu-id="fb105-108">모임 초대</span><span class="sxs-lookup"><span data-stu-id="fb105-108">Meeting invites</span></span>

<span data-ttu-id="fb105-109">[Exchange Server GDPR](gdpr-for-exchange-server.md)에 대해 설명하는 절차를 사용하여 GDPR 요청에 이러한 형식의 데이터를 찾고 내보내고 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="fb105-109">Use the procedures outlined for [GDPR for Exchange Server](gdpr-for-exchange-server.md) to find, export, or delete these types of data for GDPR requests.</span></span>

<span data-ttu-id="fb105-p102">연락처 목록은 SQL Server 데이터베이스에 저장되며, 다음과 같은 방법으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb105-p102">Contact lists are stored in the SQL Server database. They can be exported in the following ways:</span></span>

-   <span data-ttu-id="fb105-p103">최종 사용자가 그룹 머리글을 마우스 오른쪽 단추로 클릭하고 복사를 선택하여 연락처를 직접 내보낼 수 있습니다. 그러면 해당 그룹의 모든 연락처가 클립보드에 복사되고, 그 후에는 원하는 앱에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb105-p103">End users themselves can export the contacts by right clicking the group header and selecting Copy. This will copy all the contacts in that group into the clipboard, which can then be pasted into any app.</span></span>

-   <span data-ttu-id="fb105-114">[Export-CsUserData](https://docs.microsoft.com/ko-KR/powershell/module/skype/export-csuserdata) cmdlet을 사용하여 이 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb105-114">You can use the [Export-CsUserData](https://docs.microsoft.com/ko-KR/powershell/module/skype/export-csuserdata) cmdlet to export this data.</span></span>

<span data-ttu-id="fb105-p104">모임에 업로드된 콘텐츠(예: PowerPoint 파일 또는 유인물) 또는 모임에서 생성된 콘텐츠(화이트보드, 설문 조사 또는 질문 및 답변)는 파일러(filer)에 저장됩니다. 이는 최종 사용자가 만료되지 않은 한 모임에 다시 로그인하고 업로드된 콘텐츠를 다운로드하거나 생성된 콘텐츠의 경우 스크린샷을 찍을 경우 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb105-p104">Content uploaded into meetings (such as PowerPoint files or handouts) or content generated in a meeting (such as whiteboard, polls, or Q/A) is stored in the filer. This can also be exported if end users log back into any meeting that has not expired and download any uploaded content or take screenshots in the case of generated content.</span></span>

<span data-ttu-id="fb105-p105">Exchange 일정 및 연락처 목록 및 연락처 권한(가족, 동료 등)에 없는 MeetNow 모임은 사용자 데이터베이스에 있습니다. Lync Server 2013 이상에서는 [Export-CsUserData](https://docs.microsoft.com/ko-KR/powershell/module/skype/export-csuserdata) cmdlet을 사용하여 이 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb105-p105">MeetNow meetings that are not in the Exchange Calendar and Contact List and contact rights (family, co-worker, etc.) are in the User Database. In Lync Server 2013 and later, you can use the [Export-CsUserData](https://docs.microsoft.com/ko-KR/powershell/module/skype/export-csuserdata) cmdlet to export this data.</span></span>
