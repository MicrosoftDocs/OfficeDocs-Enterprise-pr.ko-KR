---
title: Office 365 비즈니스용 Skype 데이터 삭제
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
description: 비즈니스용 Skype에서 데이터를 삭제 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: e6b0c6b29b43ad07ace8797c1d62240c72110163
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067678"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a><span data-ttu-id="50e2a-103">Office 365에서 비즈니스용 Skype 데이터 삭제</span><span class="sxs-lookup"><span data-stu-id="50e2a-103">Skype for Business Data Deletion in Office 365</span></span>

<span data-ttu-id="50e2a-104">비즈니스용 Skype를 사용 하면 모임에서 피어 투 피어 인스턴트 메시지, 단체 인스턴트 메시지 및 콘텐츠 업로드 활동을 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-104">Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings.</span></span> <span data-ttu-id="50e2a-105">보관 기능을 사용 하려면 Exchange가 필요 하며 전자 메일 및 비즈니스용 Skype 콘텐츠를 모두 보관 하는 사용자의 Exchange 사서함 원본 위치 유지 특성에 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-105">The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.</span></span>

<span data-ttu-id="50e2a-106">비즈니스용 Skype의 모든 보관은 해당 사용자에 대해 사용자 수준 보관 정책을 만들고 구성 하 고 적용 하 여 하나 이상의 특정 사용자 또는 사용자 그룹에 대해이 기능을 사용 하거나 사용 하지 않도록 설정 하므로 "사용자 수준 보관"으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-106">All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users.</span></span> <span data-ttu-id="50e2a-107">비즈니스용 Skype 관리 센터 내에서 보관 설정에 대 한 직접적인 제어 기능은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-107">There is no direct control of archiving settings from within the Skype for Business admin center.</span></span>

<span data-ttu-id="50e2a-108">비즈니스용 Skype에서는 다음과 같은 유형의 콘텐츠를 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-108">The following types of content are not archived in Skype for Business:</span></span> 
- <span data-ttu-id="50e2a-109">피어 투 피어 파일 전송</span><span class="sxs-lookup"><span data-stu-id="50e2a-109">Peer-to-peer file transfers</span></span>
- <span data-ttu-id="50e2a-110">피어 투 피어 인스턴스 메시지 및 회의에 대한 오디오/비디오</span><span class="sxs-lookup"><span data-stu-id="50e2a-110">Audio/video for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="50e2a-111">피어 투 피어 메신저 메시지 및 전화 회의 응용 프로그램 공유</span><span class="sxs-lookup"><span data-stu-id="50e2a-111">Application sharing for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="50e2a-112">회의 주석</span><span class="sxs-lookup"><span data-stu-id="50e2a-112">Conferencing annotations</span></span> 

## <a name="meeting-content-retention"></a><span data-ttu-id="50e2a-113">모임 콘텐츠 보존</span><span class="sxs-lookup"><span data-stu-id="50e2a-113">Meeting Content Retention</span></span>
<span data-ttu-id="50e2a-114">비즈니스용 Skype를 사용 하는 고객은 PowerPoint 프레젠테이션, OneNote 파일 및 기타 파일 같은 첨부 파일로 비즈니스용 Skype 모임에 콘텐츠를 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-114">Customers using Skype for Business can upload content to a Skype for Business meeting as attachments, such as PowerPoint presentations, OneNote files, and other files.</span></span> <span data-ttu-id="50e2a-115">모임에 업로드 된 콘텐츠의 보존 기간은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-115">The retention period for content that has been uploaded to a meeting is as follows:</span></span>
- <span data-ttu-id="50e2a-116">**일회성 모임** 콘텐츠는 마지막 사람이 모임에서 나간 시간부터 15 일 동안 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-116">**One-time meeting** - Content is retained for 15 days starting from when the last person leaves the meeting.</span></span>
- <span data-ttu-id="50e2a-117">**되풀이 모임** -지난 사용자가 마지막 모임 세션을 떠나는 15 일 후에 콘텐츠가 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-117">**Recurring meeting** - Content is retained for 15 days after the last person leaves the last session of the meeting.</span></span> <span data-ttu-id="50e2a-118">누군가가 15일 이내 동일한 모임 세션에 참여한 경우에는 보존 타이머가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-118">The retention timer resets if someone joins the same meeting session within 15 days.</span></span> <span data-ttu-id="50e2a-119">예를 들어 비즈니스용 Skype 모임이 1 년 동안 매주 발생 하도록 예약 되 고 첫 번째 인스턴스 중에 파일이 모임에 업로드 된다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-119">For example, assume a Skype for Business meeting is scheduled to occur on a weekly basis for one year, and a file is uploaded to the meeting during the first instance.</span></span> <span data-ttu-id="50e2a-120">한 명 이상의 사용자가 매주 모임 세션에 참가 하는 경우 해당 파일은 매달 비즈니스용 Skype 온라인 서버에 보관 되며 지난 사용자는 15 일 후에 해당 시리즈의 마지막 모임에 참가 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-120">If at least one person joins the meeting session every week, the file is retained in Skype for Business Online servers for the entire year plus 15 days after the last person leaves the last meeting of the series.</span></span>
- <span data-ttu-id="50e2a-121">모임 **시작 모임** -콘텐츠가 회의 종료 시간 이후 8 시간 동안 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-121">**Meet Now meeting** - Content is retained for 8 hours after the meeting end time.</span></span>

> [!NOTE]
> <span data-ttu-id="50e2a-122">사용자에 게 라이선스가 없거나 사용 하지 않는 경우 (예: **msrtcsip-gateways-userenabled** 가 *False*로 설정 된 경우) 모임 콘텐츠가 보존 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-122">If a user is unlicensed or disabled (e.g., if **msRTCSIP-userenabled** is set to *False*), and is then re-licensed or reenabled, meeting content is not retained.</span></span>

## <a name="meeting-expiration"></a><span data-ttu-id="50e2a-123">모임 만료</span><span class="sxs-lookup"><span data-stu-id="50e2a-123">Meeting Expiration</span></span>
<span data-ttu-id="50e2a-124">사용자는 모임이 종료된 후 특정 모임에 액세스할 수 있습니다(다음 만료 기간이 적용됨).</span><span class="sxs-lookup"><span data-stu-id="50e2a-124">Users can access a specific meeting after the meeting has ended, subject to the following expiration time periods:</span></span>
- <span data-ttu-id="50e2a-125">**일회성** 모임 모임은 예약 된 모임 종료 시간 14 일 후에 만료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-125">**One-time meeting** - Meeting expires 14 days after the scheduled meeting end time.</span></span>
- <span data-ttu-id="50e2a-126">**종료 날짜가 있는 되풀이 모임** -모임이 마지막 모임 항목의 예약 된 종료 시간 보다 14 일 후에 만료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-126">**Recurring meeting with end date** - Meeting expires 14 days after the scheduled end time of the last meeting occurrence.</span></span>
- <span data-ttu-id="50e2a-127">**모임 시작 모임이** 8 시간 후에 만료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-127">**Meet Now meeting** - Meeting expires after 8 hours.</span></span>

## <a name="whiteboard-collaboration"></a><span data-ttu-id="50e2a-128">화이트 보드 공동 작업</span><span class="sxs-lookup"><span data-stu-id="50e2a-128">Whiteboard Collaboration</span></span>
<span data-ttu-id="50e2a-129">화이트 보드에 작성된 주석은 모든 참가자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-129">Annotations made on whiteboards will be seen by all participants.</span></span> <span data-ttu-id="50e2a-130">화이트 보드를 저장할 때 화이트 보드와 모든 주석은 비즈니스용 Skype 서버에 저장 되며 관리자가 설정한 모임 콘텐츠 만료 정책에 따라 서버에 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-130">When saving a whiteboard, the whiteboard and all annotations will be stored on a Skype for Business server, and it will be retained on the server according to meeting content expiration policies set by the administrator.</span></span>

## <a name="audio-test-service"></a><span data-ttu-id="50e2a-131">오디오 테스트 서비스</span><span class="sxs-lookup"><span data-stu-id="50e2a-131">Audio Test Service</span></span>
<span data-ttu-id="50e2a-132">음성에 대 한 짧은 (약 5 초) 샘플은 오디오 테스트 서비스 통화 중에 녹음 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-132">A short (approximately 5 seconds) sample of your voice is recorded during the Audio Test Service call.</span></span> <span data-ttu-id="50e2a-133">음성 샘플은 녹음 품질에 따라 비즈니스용 Skype 통화의 사운드 품질을 확인 및/또는 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-133">The voice sample is used by you to check and/or verify the sound quality of your Skype for Business call based on the quality of the recording.</span></span> <span data-ttu-id="50e2a-134">오디오 테스트 서비스 호출이 끝나면 음성 샘플이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-134">When the Audio Test Service call ends, the voice sample is deleted.</span></span>

## <a name="persistent-group-chat"></a><span data-ttu-id="50e2a-135">영구 그룹 채팅</span><span class="sxs-lookup"><span data-stu-id="50e2a-135">Persistent Group Chat</span></span>
<span data-ttu-id="50e2a-136">영구 그룹 채팅은 그룹 채팅 대화의 콘텐츠를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-136">Persistent Group Chat stores the content of group chat conversations.</span></span> <span data-ttu-id="50e2a-137">이 정책 설정을 사용 하면 관리자가 보존 기간을 제어 하 고,이 정보가 저장 되는 서버, 규정 준수 또는 기타 목적을 위해 그룹 채팅 기록을 보관 하는 경우, 룸의 모든 속성을 관리/수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-137">If enabled, the administrator can control the retention period, the server on which this information is stored, if Group Chat history is archived for compliance or other purposes, and manage/modify any properties on a room.</span></span> <span data-ttu-id="50e2a-138">역할이 서로 다른 사용자에 게는 다음과 같이 영구 데이터에 대 한 액세스 권한이 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-138">Users with different roles have different access to the persisted data, as follows:</span></span>
- <span data-ttu-id="50e2a-139">관리자는 모든 대화방에서 이전 콘텐츠 (예: 특정 날짜 이전에 게시 된 콘텐츠)를 삭제 하 여 데이터베이스 크기가 크게 커지는 것을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-139">Administrators can delete older content (for example, content posted before a certain date) from any chat room to keep the size of the database from growing greatly.</span></span> <span data-ttu-id="50e2a-140">또는 지정 된 채팅방 (또는 적합 하지 않은 것으로 간주)에 적합 하지 않은 것으로 간주 되는 메시지를 제거 하거나 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-140">Or, they can remove or replace messages considered inappropriate for a given chat room (or considered unsuitable).</span></span>
- <span data-ttu-id="50e2a-141">메시지 작성자를 포함 하 여 최종 사용자는 채팅방의 콘텐츠를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-141">End-users, including message authors, cannot delete content from any chat room.</span></span>
- <span data-ttu-id="50e2a-142">채팅방 관리자는 대화방을 사용 하지 않도록 설정할 수 있지만 대화방을 삭제 하지는 못합니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-142">Chat room managers can disable rooms but cannot delete rooms.</span></span> <span data-ttu-id="50e2a-143">관리자만이 만들어진 채팅방을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50e2a-143">Only administrators can delete a chat room after it is created.</span></span>