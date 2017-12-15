---
title: "Office 365 및 Dynamics 365 개발/테스트 환경에 대 한 Exchange Online 통합"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- mar17entnews
- Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "요약:이 테스트 랩 가이드를 사용 하 여 Office 365 평가판 구독에서 Exchange Online에 대 한 Dynamics 365 통합을 사용 하도록 설정 합니다."
ms.openlocfilehash: 9cecd13f0ffc3c2822ac6c66a3bde9c9e6a3c798
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="ffad0-103">Office 365 및 Dynamics 365 개발/테스트 환경에 대 한 Exchange Online 통합</span><span class="sxs-lookup"><span data-stu-id="ffad0-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="ffad0-104">**요약:** 이 테스트 랩 가이드를 사용 하 여 Office 365 평가판 구독에서 Exchange Online에 대 한 Dynamics 365 통합을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="ffad0-p101">Microsoft Dynamics 365 사용 하는 중요 한 적절 한 권한이 있는 모든 사용자의 모든 관련 고객 레코드를 볼 수 있도록 한 곳에서 모든 고객의 통신을 저장 하는 것입니다. 예, 특정 연락처, 계정, 기회, 또는 대/소문자와 관련 된 모든 전자 메일을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="ffad0-p102">Dynamics 365 전자 메일 및 기타 메시징 레코드를 저장 하려면 Dynamics 365 전자 메일 시스템을 동기화 해야 합니다. 서버쪽 동기화는 전자 메일 동기화를 위해 선택한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="ffad0-109">이 테스트 랩 가이드를 사용 하 여를 구성 하 여 Exchange Online 및 Outlook 온라인 클라이언트 수 활용 하는 방법을 Dynamics 365 저장 된 정보를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="ffad0-110">1 단계: Office 365 및 Dynamics 365 개발/테스트 환경 구축</span><span class="sxs-lookup"><span data-stu-id="ffad0-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="ffad0-111">Office 365 및 Dynamics 365 개발/테스트 환경의 경량 또는 시뮬레이션 된 enterprise 버전을 만들려면 [Office 365와 Dynamics 365 개발/테스트 환경에서](office-365-and-dynamics-365-dev-test-environment.md) 의 지침을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ffad0-p103">이 문서의 구성 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경에 원하지 않는 및 Windows Server Active Directory (AD) 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 일반적인 조직을 대표 하는 환경에서 Office 365와 Dynamics 365 테스트할 수 있도록 하는 옵션으로 여기</span><span class="sxs-lookup"><span data-stu-id="ffad0-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="ffad0-114">2 단계: 구성 및 Exchange Online Dynamics 365 통합을 시연</span><span class="sxs-lookup"><span data-stu-id="ffad0-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="ffad0-115">다음이 단계를 사용 하 여 Dynamics 365 및 Exchange Online의 통합에 대 한 전역 관리자의 사서함을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="ffad0-116">브라우저의 개인 세션을 사용 하 여, [http://portal.office.com](http://portal.office.com) 로 이동 하 고 프로그램 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-116">Using a private session of your browser, go to [http://portal.office.com](http://portal.office.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="ffad0-117">**Microsoft Office 홈** 페이지에서 **메일** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="ffad0-118">브라우저에서 새 **메일** 탭에서 **새로 만들기** 를 클릭 하 고 메시지를 입력 하는 것에 대 한 상자 아래에 있는 창의 아래쪽 모서리 내 서식 파일에 대 한 아이콘을 포함 하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![Dynamics 365와 통합되지 않은 비어 있는 새 전자 메일 메시지입니다.](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="ffad0-120">**취소** 를 클릭 하 고 **메일** 탭을 열어둡니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="ffad0-121">브라우저에서 **Microsoft Office Home** 탭을 클릭 하 고 **Admin** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="ffad0-122">**Office 관리 센터** 탭의 왼쪽 탐색 영역에서 클릭 **관리 센터 > Dynamics 365**합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="ffad0-123">Dynamics 365 인스턴스 목록에서 브라우저에서 새 **Dynamics 365** 탭에서 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="ffad0-124">탐색 모음에서 브라우저에서 새 **관리** 탭에서 **설정**옆에 있는 아래쪽 화살표를 클릭 하 고 **시스템**에서 **전자 메일 구성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="ffad0-125">**전자 메일 구성** 페이지에서 **전자 메일 구성 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="ffad0-126">**시스템 설정** 대화 상자에 **전자 메일** 탭에서 **서버쪽 동기화** **약속, 연락처 및 작업을** 변경 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="ffad0-127">**전자 메일 구성** 페이지에서 **사서함**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="ffad0-128">확인 표시가 왼쪽된 열에서 Office 365 전역 관리자 이름을 선택 하 고 도구 모음에서 **기본 전자 메일 설정 적용** 을 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="ffad0-129">도구 모음에서 **승인 전자 메일** 을 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="ffad0-130">확인 표시가 왼쪽된 열에서 Office 365 전역 관리자 이름을 선택, 클릭 **테스트 &amp; 사서함을 사용 하도록 설정** 도구에서 막대를 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="ffad0-131">열기 **메일** 탭을 클릭 하 고 전역 관리자 테스트 메시지를 수신 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="ffad0-p104">브라우저에서 **사서함 내 활성 사서함** 탭으로 돌아가서 페이지를 새로 고칠 합니다. **받는 전자 메일 상태** 및 **보내는 전자 메일 상태** 열 전역 관리자의 계정 이름에 대 한 **성공** 로 설정 해야 합니다. 두 테스트를 완료 하려면 최대 15 분까지 걸릴 수 있다는 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="ffad0-135">다음이 단계를 사용 하 여 Outlook Dynamics 365 응용 프로그램을 설치 하 고 전역 관리자의 사서함에서 Dynamics 365 기능 시연 하려면:</span><span class="sxs-lookup"><span data-stu-id="ffad0-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="ffad0-136">브라우저에서 **사서함 내 활성 사서함** 탭에서 **설정**옆에 있는 아래쪽 화살표를 클릭 하 고 **시스템**에서 **Outlook에 대 한 Dynamics 365 응용 프로그램** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="ffad0-p105">**Outlook 용 Microsoft Dynamics 365 응용 프로그램 시작** 페이지에서 전역 관리자 이름을 클릭 하 고 **Outlook에 앱 추가**클릭 합니다. **상태** 열에 **보류 중인**변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="ffad0-p106">**Outlook에 추가 된**상태가 변경 될 때까지 페이지를 새로 고칠 합니다. 이 구성을 완료 하려면 최대 15 분까지 걸릴 수 있다는 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="ffad0-141">브라우저에서 **메일** 탭에서 클릭 하 고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="ffad0-142">브라우저에서 **Microsoft Office Home** 탭을 클릭 하 고 **메일** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="ffad0-p107">브라우저에서 새 **메일** 탭에서 **새로 만들기**를 클릭 합니다. 이제 메시지를 입력 하는 것에 대 한 상자 아래에 있는 창의 아래쪽 모서리 Dynamics 365 대 한 아이콘을 포함 되어있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![Dynamics 365와 통합된 비어 있는 새 전자 메일 메시지로, 새 아이콘을 표시합니다.](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="ffad0-p108">Dynamics 365 아이콘을 클릭 합니다. 이 전자 메일 또는 access 서식 파일, 영업 홍보 자료 또는 문서를 추적할 수 있는 프로그램 **Dynamics 365** 창을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="ffad0-p109">**받는** 사람 필드에는 전자 메일 메시지를에서 **alex.y.wu@outlook.com**입력 하 고 **Dynamics 365** 창에서 **다시 시도** 클릭 합니다. Alex Wu, 평가판 구독에 대 한 예제 데이터와 함께 제공 된 판매 응용 프로그램에서 대화 상대에 정보로 **Dynamics 365** 창에서 **받는 사람에 게** 섹션에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Dynamics 365에 저장된 판매 연락처에 대한 Dynamics 365 정보 창입니다.](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="ffad0-151">**취소**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="ffad0-152">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 문서는 모든 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffad0-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="ffad0-153">See Also</span><span class="sxs-lookup"><span data-stu-id="ffad0-153">See Also</span></span>

[<span data-ttu-id="ffad0-154">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="ffad0-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="ffad0-155">클라우드 채택 테스트 랩 가이드 (Tlg)</span><span class="sxs-lookup"><span data-stu-id="ffad0-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="ffad0-156">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="ffad0-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="ffad0-157">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="ffad0-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="ffad0-158">Office 365 개발/테스트 환경에 대 한 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="ffad0-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="ffad0-159">Dynamics 365 (온라인)에 대 한 구독 관리</span><span class="sxs-lookup"><span data-stu-id="ffad0-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="ffad0-160">Dynamics 365 관리</span><span class="sxs-lookup"><span data-stu-id="ffad0-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


