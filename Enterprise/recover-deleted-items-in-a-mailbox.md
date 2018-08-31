---
title: 사용자 사서함에서 지운 편지함 복구 - 관리자 도움말
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: '이 문서는 관리자입니다. 않은 사용자 항목을 영구히 삭제 자신의 Outlook 사서함에서? 사용자는 다시가 하려는 있지만 복구할 수 없습니다. 수은 하지 않은 제거 된 경우 영구적으로 사용자의 사서함에서 제거 된 항목을 복구 합니다. '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541972"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="5184b-106">사용자 사서함에서 지운 편지함 복구 - 관리자 도움말</span><span class="sxs-lookup"><span data-stu-id="5184b-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="5184b-p102">**관리자를 위한이 문서는. 자신의 사서함에 있는 삭제 된 항목을 복구 하려고 합니까?** 다음 중 하나를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="5184b-109">Windows용 Outlook에서 삭제된 항목 복구</span><span class="sxs-lookup"><span data-stu-id="5184b-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="5184b-110">Outlook Web App에서 지운 편지함 또는 전자 메일 복구</span><span class="sxs-lookup"><span data-stu-id="5184b-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="5184b-111">웹에 있는 Outlook에서 삭제 된 전자 메일 메시지를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="5184b-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="5184b-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="5184b-p103">않은 사용자 항목을 영구히 삭제 자신의 Outlook 사서함에서? 사용자는 다시가 하려는 있지만 복구할 수 없습니다. 수은 하지 않은 제거 된 경우 영구적으로 사용자의 사서함에서 제거 된 항목을 복구 합니다. Exchange Online에서 원본 위치 eDiscovery 도구를 사용 하 여 삭제 된 전자 메일 및 기타 항목을 검색 하 여이 작업을 수행-연락처, 일정 약속 및 작업 같은 및-사용자의 사서함에 있습니다. 삭제 된 항목을 찾을 수 있으면 PST 파일 (Outlook 데이터 파일 라고도 함), 사용자가 사서함에 다시 항목을 복원 하려면 사용 하 여 수를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="5184b-p104">사용자의 사서함에서 삭제 된 항목을 복구 하는 중에 대 한 단계는 다음과 같습니다. 이 소요시간? 처음으로 복구 하려는 경우 얼마나 많은 항목에 따라 단계를 모두 완료 하는 데 20 또는 30 분 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5184b-p105">가 **Exchange 관리자** 또는 Office 365에서 **전역 관리자** 또는 조직 관리 역할 그룹의 구성원 Exchange Online에서 수이 문서의 단계를 수행 하려면 해야 합니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5184b-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="5184b-123">1 단계: eDiscovery 사용 권한을 직접 할당</span><span class="sxs-lookup"><span data-stu-id="5184b-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="5184b-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="5184b-124"></span></span>

<span data-ttu-id="5184b-p106">먼저 할당 하는 것 사용자가 직접 필요한 사용 권한을 Exchange 온라인 사용자의 사서함을 검색 하는 원본 위치 eDiscovery 도구를 사용할 수 있도록 합니다. 이 작업을 한번 수행 해야 합니다. 다른 사서함을 나중에 검색 해야하는 경우에이 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="5184b-128">[비즈니스를 위한 Office 365에 로그인 할 위치](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) 선택 하면 작업이 나 교육용 계정과 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="5184b-129">응용 프로그램 시작 관리자 아이콘을 선택 ![Office 365에 있는 응용 프로그램 시작 관리자 아이콘](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) 왼쪽 위에서에서 **관리**를 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="5184b-130">Office 365 관리 센터의 왼쪽 탐색 영역에서 **관리 센터**를 확장 하 고 **Exchange**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![관리 센터 목록](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="5184b-132">Exchange 관리 센터에서 **사용 권한**을 클릭 한 다음 **관리 역할**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="5184b-133">목록 보기에서 **검색 관리**선택 하 고 **편집**을 클릭 한 다음![편집 아이콘](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![EAC에서 검색 관리 역할 그룹에 추가 하는 사용자가 직접](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="5184b-135">**역할 그룹** **구성원**아래에서 **추가**클릭![추가 아이콘](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="5184b-136">**구성원 선택**는 이름 목록에서 자신을 선택 하 고 **추가**클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="5184b-p107">조직 관리 또는 TenantAdmins 등,의 구성원 이어야 하는 그룹을 추가할 수도 있습니다. 그룹에 추가 하면 다른 구성원 그룹의 원본 위치 eDiscovery 도구를 실행 하려면 필요한 권한은 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="5184b-139">**역할 그룹** **저장** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="5184b-140">Office 365에서 로그 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="5184b-141">새 사용 권한을 적용 되도록 다음 단계를 시작 하기 전에 로그 아웃 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="5184b-p108">검색 관리 역할 그룹의 구성원에는 중요 한 메시지 콘텐츠에 액세스할 수 있습니다. 조직에서 모든 사서함을 검색, 검색 결과 (및 기타 사서함 항목)를 미리 보거나, 결과 검색 사서함으로 복사 및 PST 파일로 검색 결과 내보내기 (영문)이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="5184b-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="5184b-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="5184b-145">삭제 된 항목에 대 한 사용자의 사서함을 검색 하는 2 단계:</span><span class="sxs-lookup"><span data-stu-id="5184b-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="5184b-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="5184b-146"></span></span>

<span data-ttu-id="5184b-p109">원본 위치 eDiscovery 검색을 실행 하면 검색 하는 사서함의 복구 가능한 항목 폴더의 검색에 자동으로 포함 됩니다. 복구 가능한 항목 폴더에서 영구적으로 삭제 된 항목 저장 된 위치 (영구적으로 제거)을 제거 하려는 자신이 때까지 사서함에서은입니다. 따라서 항목을 제거한 하지 않은 경우에 원본 위치 eDiscovery 도구를 사용 하 여 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="5184b-150">[비즈니스를 위한 Office 365에 로그인 할 위치](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) 선택 하면 작업이 나 교육용 계정과 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="5184b-151">응용 프로그램 시작 관리자 아이콘을 선택 ![Office 365에 있는 응용 프로그램 시작 관리자 아이콘](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) 왼쪽 위에서에서 **관리**를 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="5184b-152">Office 365 관리 센터의 왼쪽 탐색 영역에서 **관리**확장 한 다음 **Exchange**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="5184b-153">Exchange 관리 센터에서 **준수 관리**, 클릭 **원본 위치 eDiscovery &amp; 유지**, **새로 만들기**를 클릭 하 고![추가 아이콘](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![EAC의 규정 준수 관리 페이지에서 원본 위치 eDiscovery 클릭 및 유지](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="5184b-155">**이름 및 설명** 페이지에서 검색 (예: 전자 메일에 대 한 복구 중인 사용자의 이름), 선택적 설명 및 클릭에 대 한 이름을 입력 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="5184b-156">**사서함** 페이지에서 **지정 사서함 검색을**클릭 하 고 **추가**클릭 한 다음![추가 아이콘](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![특정 사서함을 검색 하려면 검색 하도록 지정 사서함을 클릭 합니다.](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="5184b-158">찾기 및에 대 한 삭제 된 전자 메일을 복구 하는 사용자의 이름을 선택, **추가**클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="5184b-159">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-159">Click **Next**.</span></span>
    
    <span data-ttu-id="5184b-p110">**검색 쿼리** 페이지가 표시 됩니다. 사용자의 사서함에서 누락 된 항목을 찾을 수 있는 검색 조건을 정의 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="5184b-162">**검색 쿼리** 페이지에서 다음 필드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="5184b-p111">**모든 콘텐츠를 포함 합니다.** 검색 결과에서 사용자의 사서함에 모든 콘텐츠를 포함 하려면이 옵션을 선택 합니다. 이 옵션을 선택 하는 경우에 추가 검색 조건을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="5184b-165">**필터 조건에 따라** 시작 하는 키워드를 포함 한 검색 조건을 지정 하 고 끝 날짜, 보낸사람 및 받는 사람 주소와 메시지 유형 하려면이 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![키워드, 날짜 범위, 받는 사람 및 메시지 유형 같은 기준에 따라 검색 작성](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="5184b-167">**필드**</span><span class="sxs-lookup"><span data-stu-id="5184b-167">**Field**</span></span>|<span data-ttu-id="5184b-168">**하려면이 옵션을 사용 하 여...**</span><span class="sxs-lookup"><span data-stu-id="5184b-168">**Use this to...**</span></span>|
|:-----|:-----|
|![분홍색 원에서 번호 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="5184b-170">키워드, 날짜 범위, 받는 사람 및 메시지 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![분홍색 원에 두 번호입니다.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="5184b-172">키워드 또는 구를, 메시지에 대 한 검색 하 고 **AND** 또는 **OR**같은 논리 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![분홍색 원에서 3 번호입니다.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="5184b-174">날짜 범위 내에서 보내거나 받은 메시지를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![분홍색 원에 4 번호입니다.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="5184b-176">받거나 특정인에 게 보낸 메시지를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![번호 매기기 5 분홍색 원입니다.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="5184b-178">모든 메시지 유형이 검색 하거나 특정 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="5184b-p112">**원본 위치 유지 설정** 페이지에서 검색을 시작 하려면 **완료** 를 클릭 합니다. 삭제 된 전자 메일을 복구 하는 사용자의 사서함을 보류 하 이유가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="5184b-181">검색을 시작 하면 Exchange의 예상 전체 크기 및 지정한 조건에 따라 검색에 의해 반환 되는 항목 수가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="5184b-p113">방금 만든 검색을 선택 하 고 **새로 고칠**을 클릭![새로고침](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) 세부 정보 창에 표시 되는 정보를 업데이트 합니다. **예측 성공** 의 상태를 검색 완료 되었음을 나타냅니다. Exchange에는 9 단계에서 지정한 검색 조건을 기준으로 검색 하 여 항목 (및 해당 크기)의 총 수를 예상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="5184b-p114">세부 정보 창에서 발견 된 항목을 볼 수 있는 **검색 결과 미리 보기를** 클릭 합니다. 항목을 찾는 식별 도움이 될 수 있습니다이 있습니다. 복구 하려는 항목을 찾을 수 있으면 검색 결과 PST 파일로 내보낼 4 단계로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![검색 결과를 복구 하려는 항목을 보려면 미리 보기를 클릭 합니다.](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="5184b-p115">원하는 내용을 찾을 수 없는 경우 수정할 수 있습니다 검색 조건을 검색을 선택 하 여 **편집**을 클릭 하면![편집 아이콘](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), 다음 **검색 쿼리**를 클릭 하 고 있습니다. 검색 조건을 변경 하 고 검색을 다시 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="5184b-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="5184b-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="5184b-192">(선택 사항) 3 단계: 검색 결과 검색 사서함으로 복사</span><span class="sxs-lookup"><span data-stu-id="5184b-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="5184b-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="5184b-193"></span></span>

<span data-ttu-id="5184b-p116">검색 결과 미리 보고 한 항목을 찾을 수 없는 경우 또는 사용자의 복구 가능한 항목 폴더에는 되는 항목을 참조 하려면 다음 검색 결과 (검색 사서함 라고 함) 특별 한 사서함에 복사한 후 t 웹에서 Outlook에서 해당 사서함을 엽니다. o는 실제 항목을 봅니다. 검색 결과 복사 하는 가장 좋은 이유 이므로 사용자의 복구 가능한 항목 폴더에서 항목을 볼 수 있습니다. 복구 하려는 항목 제거 하위 폴더에 있는 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="5184b-197">Exchange 관리 센터에서 **준수 관리** 로 이동 \> **원본 위치 eDiscovery &amp; 유지**합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="5184b-198">검색의 목록에서 2 단계에서에서 만든 검색을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="5184b-199">**검색**을 클릭![검색](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), 한 다음 드롭다운 목록에서 **검색 결과 복사를** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![검색을 클릭 한 다음 검색 결과 복사를 클릭 합니다.](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="5184b-201">**복사본 검색 결과** 페이지에서 **찾아보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![삭제 된 항목을 복구 하는 경우 옵션의 선택을 취소 하는 확인란을 그대로 둡니다.](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="5184b-203">**표시 이름**아래에서 **사서함 검색**클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![기본 검색 사서함을 검색 결과 복사](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="5184b-205">사서함 검색은 Office 365 조직에 자동으로 생성 된 기본 검색 사서함입니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="5184b-206">**복사본 검색 결과** 페이지에 다시 사서함 검색에 검색 결과 복사 하 여 프로세스를 시작 **복사** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![사서함 검색에 검색 결과 복사 하려면 복사를 클릭 합니다.](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="5184b-208">**새로고침**을 클릭![새로고침](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) 세부 정보 창에 표시 되는 복사 상태에 대 한 정보를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="5184b-209">복사가 완료 되 면 검색 결과 보려면 검색 검색 사서함을 열려면 **열기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![검색 결과 보려면 검색 검색 사서함으로 이동 하는 열기를 클릭 합니다.](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="5184b-p117">검색 검색 사서함에 복사 하는 검색 결과 원본 위치 eDiscovery 검색 이름이 같은 폴더에 배치 됩니다. 해당 폴더에 있는 항목을 표시 하는 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![사서함 검색;에서 검색 결과 제거 폴더의 항목을 관리 하 여 복구할 수 있습니다.](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="5184b-p118">검색을 실행 하는 경우에 사용자의 복구 가능한 항목 폴더 검색도 됩니다. 즉, 검색 결과에 포함 된 복구 가능한 항목 폴더에서 항목 검색 조건을 충족 하는 경우. 삭제 폴더의 항목은 사용자 (지운 편지함 폴더에서 항목을 삭제 하 여 또는 선택 하 고 **Shift + Delete**키를 눌러 여를 영구적으로 삭제 하는 항목. 사용자는 Outlook 또는 웹에 있는 Outlook에서 지운 편지함 복구 도구를 사용 하 여 삭제 폴더에서 항목을 복구할 수 있습니다. 제거 폴더의 항목은 지운 편지함 복구 도구를 사용 하 여 사용자를 제거 하는 항목 또는 사서함에 적용 된 정책에 의해 제거 된 자동으로 된 항목입니다. 두 경우 모두에서 관리자만 제거 폴더에서 항목을 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="5184b-p119">사용자는 복구 가능한 항목 도구를 사용 하 여 삭제 된 항목을 찾을 수 없는 하 고 해당 항목은 여전히 복구할 수 (있는지 것 하지 않은 영구적으로 제거 된 사서함에서 의미), 것은 것이 더 폴더에 있는 제거 합니다. 그렇다면 사용자에 대 한 복구 하려는 삭제 된 항목에 대 한 제거 폴더에서 검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="5184b-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="5184b-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="5184b-223">4 단계: 검색 결과 PST 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="5184b-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="5184b-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="5184b-224"></span></span>

<span data-ttu-id="5184b-p120">사용자에 대 한 복구 하려는 항목을 찾은 후 다음 단계를 PST 파일로 2 단계에서에서 실행 하는 검색에서 결과 내보내는입니다. 사용자가 사서함에 삭제 된 항목을 복원 하려면 다음 단계에서이 PST 파일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="5184b-227">Exchange 관리 센터에서 **준수 관리** 로 이동 \> **원본 위치 eDiscovery &amp; 유지**합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="5184b-228">검색의 목록에서 2 단계에서에서 만든 검색을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="5184b-229">**PST 파일로 내보내기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-229">Click **Export to a PST file**.</span></span>
    
    ![PST 파일로 내보내기를 클릭합니다](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="5184b-231">EDiscovery 내보내기 도구를 설치 하는 메시지가 표시 되 면 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="5184b-232">EDiscovery PST 내보내기 도구에서에서 PST 파일을 다운로드 하려는 위치를 지정 하려면 **찾아보기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![EDiscovery PST 내보내기 도구](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="5184b-234">중복 제거를 사용 하도록 설정 하 고 검색할 수 없는 항목을 포함 하는 옵션을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="5184b-235">사용자의 컴퓨터에 PST 파일을 다운로드 하려면 **시작** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="5184b-p121">내보내기 프로세스에 대 한 상태 정보를 표시 하는 **eDiscovery PST 내보내기 도구** 입니다. 내보내기가 완료 되 면 다운로드 한 위치에서 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="5184b-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="5184b-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="5184b-239">5 단계: 사용자의 사서함을 복구 된 항목 복원</span><span class="sxs-lookup"><span data-stu-id="5184b-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="5184b-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="5184b-240"></span></span>

<span data-ttu-id="5184b-p122">마지막 단계는 사용자의 사서함을 복구 된 항목을 복원 하는 4 단계에서 내보낸 PST 파일을 사용 하는 것입니다. 사용자에 게 PST 파일을 보낸 후이 단계의 나머지 부분에서는 PST 파일을 열고 다음는 복구 된 항목을 자신의 사서함에 있는 다른 폴더로 이동 하는 사용자에 의해 수행 됩니다. 단계별 지침은 보낼 수도 있습니다 사용자 링크를이 항목에: [Open Outlook 데이터 파일 (.pst) 및](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)합니다. 또는 [삭제 된 항목을 PST 파일을 사용 하 여 사서함 복원](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) 섹션에는 사용자 링크를 보낼 하 고 이러한 단계를 수행 하도록 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="5184b-245">**PST 파일을 사용자에 게 보내기**</span><span class="sxs-lookup"><span data-stu-id="5184b-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="5184b-p123">마지막 단계를 수행 하는 사용자에 게 4 단계에서 내보낸 PST 파일을 보내는 됩니다. 몇 가지 방법으로이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="5184b-p124">PST 파일을 전자 메일 메시지에 첨부 합니다. Outlook을 차단 PST 파일을 구성 하는 경우에 zip 파일 및 다음 메시지에 연결 해야 합니다. 다음은 방법:</span><span class="sxs-lookup"><span data-stu-id="5184b-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="5184b-251">Windows 탐색기나 파일 탐색기에서 PST 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="5184b-p125">파일을 마우스 오른쪽 단추로 클릭 한 다음 **보내기** 를 선택 \> **압축 (zip) 폴더**입니다. Windows 새 zip 파일을 만들고 PST 파일로 동일한 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="5184b-254">압축 된 PST 파일을 전자 메일 메시지에 첨부 하 고 파일 클릭 하 여 방금 후 압축을 수 있는 사용자에 게 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="5184b-255">PST 파일을 사용자에 액세스 하 고 검색할 수 있는 공유 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="5184b-256">다음 섹션의 단계는 사용자가 사서함에 삭제 된 항목을 복원 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="5184b-257">**PST 파일을 사용 하 여 사서함을 삭제 된 항목 복원**</span><span class="sxs-lookup"><span data-stu-id="5184b-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="5184b-p126">PST 파일을 사용 하 여 삭제 된 항목을 복원 하려면 Outlook 데스크톱 응용 프로그램을 사용 해야 합니다. Outlook Web App 또는 Outlook 웹에 있는 사용 하 여 PST 파일을 열 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="5184b-260">Outlook 2013 또는 Outlook 2016에서 **파일** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="5184b-261">클릭 **Open &amp; 내보내기**, 다음 **Outlook 데이터 파일 열기**를 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="5184b-262">전송 하는 관리자에 게 문의 하 여 PST 파일을 저장 한 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="5184b-263">PST를 선택한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="5184b-264">PST 파일로 Outlook의 왼쪽 탐색 모음에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![PST 파일로 Outlook의 왼쪽 탐색 모음에 표시 됩니다.](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="5184b-266">PST 파일을 확장 하 고 화살표를 클릭 하 고 복구 하려는 항목을 찾으려면 그 아래에 있는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![제거 폴더를 복구 하려는 항목에 대 한 있는지 확인](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="5184b-p127">복구 하려는 항목에 대 한 제거 폴더를 찾습니다. 이것은 제거할 숨겨진된 폴더 항목으로 이동 됩니다. 이것이 가능성이 복구 하는 관리자에 게 문의이 폴더에 있는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="5184b-271">복구 하 고 **이동** 를 클릭 한 다음 원하는 항목을 마우스 오른쪽 단추로 클릭 \> **다른 폴더**입니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![이동을 클릭 하 고 다른 폴더를 선택 합니다](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="5184b-273">항목 이동 하 고 사용자의 받은 편지함에 **받은 편지함**클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="5184b-274">**팁:** 다른 종류의 항목을 복구 하려면 다음 중 하나를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="5184b-275">일정 항목을 복구 하려면 마우스 오른쪽 단추로 클릭 하 고 **이동** 를 클릭 한 다음 \> **다른 폴더** \> **달력**입니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="5184b-276">대화 상대를 복구 하려면 마우스 오른쪽 단추로 클릭 하 고 **이동** 를 클릭 한 다음 \> **다른 폴더** \> **연락처**입니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="5184b-277">작업을 복구 하려면 마우스 오른쪽 단추로 클릭 하 고 **이동** 를 클릭 한 다음 \> **다른 폴더** \> **작업**합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![다른 종류의 항목을 이동할 폴더를 선택 합니다.](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="5184b-279">완료 되 면 삭제 된 항목 복구, 왼쪽 탐색 모음에서 PST 파일을 마우스 오른쪽 단추로 클릭 하 고 **"이름 닫기 PST 파일의" "를**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="5184b-280">Return to top</span><span class="sxs-lookup"><span data-stu-id="5184b-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="5184b-281">추가 정보</span><span class="sxs-lookup"><span data-stu-id="5184b-281">More information</span></span>
<span data-ttu-id="5184b-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="5184b-282"></span></span>

- <span data-ttu-id="5184b-p128">항목에 대 한 삭제 된 항목 보존 기간 기간이 만료 되지 않도록 하는 경우 영구적으로 삭제 된 항목을 복구 하는 사용자에 대 한 수도 있습니다. 발생할 수 있는 관리자도 복구 가능한 항목 폴더에 지정 된 시간 항목은 복구에 사용할 수입니다. 예, 30 일에 대 한 사용자의 지운 편지함 폴더에 보관 된 모든 항목을 삭제 하는 정책 및 사용자가 다른 14 일 최대에 대 한 복구 가능한 항목 폴더에서 항목을 복구할 수 있는 다른 정책 있을 수 있습니다. 그러나 두 일 후 여전히 수 있습니다를이 항목의 절차를 사용 하 여 사용자의 사서함에 있는 항목을 복구 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="5184b-p129">사용자는 지워진 하지 않은 경우 및 해당 항목에 대 한 삭제 된 항목 보존 기간 기간이 만료 되지 않도록 하는 경우 삭제 된 항목을 복구할 수 있습니다. 사용자가 자신의 사서함에서 삭제 된 항목을 복구를 위해 다음 항목 중 하나를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="5184b-289">Windows용 Outlook에서 삭제된 항목 복구</span><span class="sxs-lookup"><span data-stu-id="5184b-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="5184b-290">Outlook 2010의 삭제 된 항목을 복구</span><span class="sxs-lookup"><span data-stu-id="5184b-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="5184b-291">Outlook Web App에서 지운 편지함 또는 전자 메일 복구</span><span class="sxs-lookup"><span data-stu-id="5184b-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="5184b-292">웹에 있는 Outlook에서 삭제 된 전자 메일 메시지를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="5184b-293">Outlook에서 삭제 된 연락처를 복구 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="5184b-294">Outlook.com에서 삭제 된 전자 메일 메시지를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5184b-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="5184b-295">Return to top</span><span class="sxs-lookup"><span data-stu-id="5184b-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

