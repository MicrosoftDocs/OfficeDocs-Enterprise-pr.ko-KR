---
title: "Office 365 및 Dynamics 365 개발/테스트 환경을 위한 Exchange Online 통합"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "요약: 이 테스트 랩 가이드를 사용하여 Office 365 평가판 구독에서 Exchange Online용 Dynamic 365 통합을 사용하도록 설정할 수 있습니다."
ms.openlocfilehash: b297c3e461b5695b323c619145df64524989d58a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="53b61-103">Office 365 및 Dynamics 365 개발/테스트 환경을 위한 Exchange Online 통합</span><span class="sxs-lookup"><span data-stu-id="53b61-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="53b61-104">**요약:** 이 테스트 랩 가이드를 사용하여 Office 365 평가판 구독에서 Exchange Online용 Dynamic 365 통합을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="53b61-p101">Microsoft Dynamics 365를 가장 잘 활용하는 방법은 모든 고객 통신을 한 곳에 저장하여 적합한 사용 권한을 가진 사용자라면 누구나 관련된 고객 레코드를 모두 볼 수 있도록 하는 것입니다. 예를 들어, 특정 연락처, 계정, 기회 및 케이스와 관련된 모든 전자 메일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="53b61-p102">Dynamics 365의 전자 메일 및 기타 메시징 레코드를 저장하려면 전자 메일 시스템을 Dynamics 365와 동기화해야 합니다. 서버 쪽 동기화는 전자 메일 동기화를 위한 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="53b61-109">이 테스트 랩 가이드를 사용하여 Exchange Online 및 Outlook Online 클라이언트가 Dynamics 365에 저장된 정보를 활용하는 방법을 구성하고 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="53b61-110">1단계: Office 365 및 Dynamics 365 개발/테스트 환경 구축</span><span class="sxs-lookup"><span data-stu-id="53b61-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="53b61-111">[Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)의 지침을 사용하여 Office 365 및 Dynamics 365 개발/테스트 환경의 경량 또는 시뮬레이트된 엔터프라이즈 버전 중 하나를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="53b61-p103">이 문서의 구성에는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server Active Directory(AD) 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 일반적인 조직을 나타내는 환경에서 Office 365 및 Dynamics 365를 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="53b61-114">2단계: Exchange Online에서 Dynamics 365 통합 구성 및 설명</span><span class="sxs-lookup"><span data-stu-id="53b61-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="53b61-115">다음 단계를 통해 Dynamics 365 및 Exchange Online 통합용 전역 관리자 사서함을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="53b61-116">브라우저의 개인 세션을 통해 [(http://portal.office.com)]((http://portal.office.com))으로 이동한 다음 Office 365 전역 관리자 계정으로 로그인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-116">Using a private session of your browser, go to [(http://portal.office.com)]((http://portal.office.com)) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="53b61-117">**Microsoft Office Home** 페이지에서 **메일** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="53b61-118">브라우저의 새 **메일** 탭에서 **새로 만들기**를 클릭하고 메시지 입력 상자 아래의 창 하단 구석에 내 템플릿 아이콘이 어떻게 표시되는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="53b61-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![Dynamics 365와 통합되지 않은 비어 있는 새 전자 메일 메시지입니다.](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="53b61-120">**취소**를 클릭하고 **메일** 탭을 열어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="53b61-121">브라우저에서 **Microsoft Office 탭**을 클릭한 다음 **관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="53b61-122">**Office 관리 센터** 탭의 왼쪽 탐색 창에서 **관리 센터 > Dynamics 365**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="53b61-123">브라우저의 새 **Dynamics 365** 탭에 있는 Dynamics 365 인스턴스 목록에서 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="53b61-124">브라우저의 새 **관리** 탭에 있는 탐색 모음에서 **설정** 옆의 아래쪽 화살표를 클릭한 다음 **시스템**에서 **전자 메일 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="53b61-125">**전자 메일 구성** 페이지에서 **전자 메일 구성 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="53b61-126">**시스템 설정** 대화 상자의 **전자 메일** 탭에서 **약속, 연락처 및 작업**을 **서버 쪽 동기화**로 변경한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="53b61-127">**전자 메일 구성** 페이지에서 **사서함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="53b61-128">왼쪽 확인 표시 열에서 Office 365 전역 관리자 이름을 선택하고 도구 모음에서 **기본 전자 메일 설정 적용**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="53b61-129">도구 모음에서 **전자 메일 적용**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="53b61-130">왼쪽 확인 표시 열에서 Office 365 전역 관리자 이름을 선택하고 도구 모음에서 **사서함 테스트 &amp; 사용**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="53b61-131">**메일** 탭을 클릭하고 전역 관리자가 테스트 메시지를 수신했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="53b61-p104">브라우저의 **사서함 내 활성 사서함** 탭으로 돌아가서 페이지를 새로 고칩니다. **수신 전자 메일 상태** 및 **발신 전자 메일 상태** 열은 전역 관리자 계정 이름에 대해 **성공**으로 설정되어 있어야 합니다. 테스트를 모두 완료하는 데 최대 15분이 소요될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="53b61-135">다음 단계를 통해 Outlook용 Dynamics 365 앱을 설치하고 전역 관리자 사서함 내에 Dynamics 365 기능을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="53b61-136">브라우저의 **사서함 내 활성 사서함** 탭에서 **설정** 옆의 아래쪽 화살표를 클릭한 다음 **시스템**에서 **Outlook용 Dynamics 365 앱**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="53b61-p105">**Outlook용 Microsoft Dynamics 365 앱 시작하기** 페이지에서 전역 관리자 이름을 클릭한 다음 **앱을 Outlook에 추가**를 클릭합니다. **상태** 열이 **보류 중**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="53b61-p106">상태가 **Outlook에 추가됨**으로 변경되기 전까지 페이지를 새로 고칩니다. 이 구성을 완료하는 데 최대 15분이 소요될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="53b61-141">브라우저에서 **메일** 탭을 클릭한 다음 브라우저를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="53b61-142">브라우저에서 **Microsoft Office Home** 탭을 클릭한 다음 **메일** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="53b61-p107">브라우저의 새 **메일** 탭에서 **새로 만들기**를 클릭합니다. 이제 메시지 입력 상자 아래의 창 하단 구석에 Dynamics 365 아이콘이 어떻게 표시되는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="53b61-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![Dynamics 365와 통합된 비어 있는 새 전자 메일 메시지로, 새 아이콘을 표시합니다.](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="53b61-p108">Dynamics 365 아이콘을 클릭합니다. 이 전자 메일을 추적하거나 템플릿, 판매 문서 또는 기사에 액세스할 수 있는 **Dynamics 365** 창을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="53b61-p109">전자 메일 메시지의 **받는 사람** 필드에서 **alex.y.wu@outlook.com**을 입력한 다음 **Dynamics 365** 창에서 **다시 시도**를 클릭합니다. **Dynamics 365** 창에서 **받는 사람** 섹션에 평가판 구독의 샘플 데이터와 함께 제공된 판매 응용 프로그램의 연락처인 Alex Wu에 대한 정보가 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Dynamics 365에 저장된 판매 연락처에 대한 Dynamics 365 정보 창입니다.](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="53b61-151">**취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="53b61-152">[여기]((http://aka.ms/catlgstack))를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53b61-152">Click [here]((http://aka.ms/catlgstack)) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="53b61-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53b61-153">See Also</span></span>

[<span data-ttu-id="53b61-154">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="53b61-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="53b61-155">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="53b61-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="53b61-156">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="53b61-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="53b61-157">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="53b61-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="53b61-158">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="53b61-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

<span data-ttu-id="53b61-159">[Dynamics 365용 구독 관리(온라인)]((https://technet.microsoft.com/library/jj679903.aspx))</span><span class="sxs-lookup"><span data-stu-id="53b61-159">[Subscription Management for Dynamics 365 (online)]((https://technet.microsoft.com/library/jj679903.aspx))</span></span>
  
<span data-ttu-id="53b61-160">[Dynamics 365 관리]((https://technet.microsoft.com/library/dn531101.aspx))</span><span class="sxs-lookup"><span data-stu-id="53b61-160">[Administering Dynamics 365]((https://technet.microsoft.com/library/dn531101.aspx))</span></span>


