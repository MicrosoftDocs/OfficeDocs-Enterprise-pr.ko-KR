---
title: Office 365 개발/테스트 환경용 Advanced Threat Protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: '요약: Office 365 개발/테스트 환경의 Office 365 Advanced Threat Protection을 구성하고 보여 줍니다.'
ms.openlocfilehash: 274f8558d23714a73e0891500dac5d5e007b6be2
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162421"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="a54d6-103">Office 365 개발/테스트 환경용 Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="a54d6-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="a54d6-104">**요약:** Office 365 개발/테스트 환경의 Office 365 Advanced Threat Protection을 구성하고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="a54d6-105">Office 365 ATP(Advanced Threat Protection)는 EOP(Exchange Online Protection)의 기능으로 전자 메일에서 맬웨어를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-105">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span> <span data-ttu-id="a54d6-106">ATP를 사용 하 여 EAC (Exchange 관리 센터) 또는 보안 &amp; 및 준수 센터에서 사용자가 악성이 아닌 것으로 확인 된 전자 메일의 링크나 첨부 파일에만 액세스할 수 있도록 하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-106">With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious.</span></span> <span data-ttu-id="a54d6-107">자세한 내용은 [안전한 첨부 파일 및 안전한 링크를 위한 Advanced Threat Protection](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a54d6-107">For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="a54d6-108">이 문서의 지침을 사용하여 Office 365 평가판 구독의 ATP를 구성하고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="a54d6-109">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="a54d6-110">최소 요구 사항의 간단한 방식으로 ATP를 테스트 하려면 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2 단계 및 3 단계의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a54d6-111">시뮬레이트된 엔터프라이즈에서 ATP를 테스트 하려면 [Office 365 개발/테스트 환경에 대 한 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="a54d6-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a54d6-112">ATP 테스트에는 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-112">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="a54d6-113">이 기능은 나중에 일반적인 조직을 나타내는 환경에서 ATP를 테스트 하 고 시험해 볼 수 있도록 옵션으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-113">It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="a54d6-114">2 단계: Office 365의 기본 전자 메일 배달 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="a54d6-115">이 단계에서는 ATP 정책을 구성하기 전에 잠재적인 악성 전자 메일이 차단 또는 완화되지 않고 Office 365 사서함으로 배달될 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="a54d6-116">Internet Explorer를 열고 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)2 단계에서 만든 Outlook 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="a54d6-117">경량 Office 365 개발/테스트 환경을 사용하는 경우 Internet Explorer의 비공개 세션을 열고 로컬 컴퓨터에서 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="a54d6-118">시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 [Azure portal](https://portal.azure.com) 을 사용 하 여 client1 가상 컴퓨터에 연결한 다음, client1에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="a54d6-119">메모장을 실행하고 일부 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="a54d6-120">파일을 **getKeys.js**로 문서 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="a54d6-121">Internet Explorer의 Outlook 메일 탭에서 **새 전자 메일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="a54d6-122">**받는 사람**에 평가판 구독 Office 365 전역 관리자 이름의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="a54d6-123">제목에 **새 키**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="a54d6-124">본문에 **파일 전달**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="a54d6-125">**첨부**를 클릭하고 문서 폴더에서 **getKeys.js**를 두 번 클릭하고 **복사본으로 첨부**를 클릭한 다음 **보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="a54d6-126">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-126">Click **New**.</span></span>
    
10. <span data-ttu-id="a54d6-127">**받는 사람**에 평가판 구독 Office 365 전역 관리자 이름의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="a54d6-128">제목에 **새 여행 웹 사이트**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="a54d6-129">본문에 **이 사이트를 전달받았음**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="a54d6-130">본문에 **이 사이트** 텍스트를 선택하고 도구 모음에 하이퍼링크 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="a54d6-131">**URL**에 입력 **http://www.spamlink.contoso.com/** 하 고 **확인**을 클릭 한 다음 **보내기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="a54d6-132">전용 탐색 모드에서 별도의 Internet Explorer 인스턴스를 열고 Microsoft 365 관리 센터 ([https://admin.microsoft.com](https://admin.microsoft.com))로 이동한 후 전역 관리자 계정으로 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="a54d6-133">기본 포털 페이지에서 앱 타일을 클릭한 다음 **메일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="a54d6-134">받은 편지함에서 제목이 **새 키**인 메시지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="a54d6-135">정크 메일 폴더에서 제목 **새 여행 웹 사이트가**있는 메시지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-135">In the Junk Mail folder, click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="a54d6-136">메시지 내에서 **이 사이트** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-136">Within the message, click the **this site** link.</span></span> <span data-ttu-id="a54d6-137">"죄송 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-137">You should see a "Oops!</span></span> <span data-ttu-id="a54d6-138">Internet Explorer에서 spamlink.contoso.com를 찾을 수 없습니다. "</span><span class="sxs-lookup"><span data-stu-id="a54d6-138">Internet Explorer could not find spamlink.contoso.com."</span></span> <span data-ttu-id="a54d6-139">페이지.</span><span class="sxs-lookup"><span data-stu-id="a54d6-139">page.</span></span> <span data-ttu-id="a54d6-140">해당 위치에 웹 페이지가 없기 때문에이 결과가 올바른 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-140">This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="a54d6-p104">이러한 잠재적인 악성 전자 메일이 모두 배달되었습니다. **새 키** 전자 메일에 검색되지 않은 맬웨어가 포함될 수 있으며 사용자는 **새 여행 웹 사이트** 전자 메일의 잠재적인 악성 링크를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="a54d6-143">3단계: ATP의 안전한 첨부 파일 및 안전한 링크 정책 구성</span><span class="sxs-lookup"><span data-stu-id="a54d6-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="a54d6-144">이 단계에서는 안전한 첨부 파일 정책을 만들고 구성하여 잠재적인 악성 첨부 파일이 배달되지 않도록 하고 안전한 링크 정책을 통해 사용자가 잠재적으로 안전하지 않은 URL로 이동할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="a54d6-145">Internet Explorer의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="a54d6-146">왼쪽 창에서 **관리 센터**를 클릭한 다음 **Exchange**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="a54d6-147">Exchange 관리 센터 탭의 왼쪽 탐색 창에서 **고급 위협**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="a54d6-148">**안전한 첨부파일** 탭을 클릭한 다음 + 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="a54d6-149">**새 안전 첨부 파일 정책** 창의 **이름**에 **안전한 첨부 파일 정책 차단을**입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="a54d6-150">**안전한 첨부 파일 알 수 없는 맬웨어 응답**에서 **차단을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="a54d6-151">**검색에 첨부 파일 리디렉션**에서 **리디렉션 사용**을 클릭하고 Office 365 전역 관리자 계정의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="a54d6-152">**적용 대상**에서 아래쪽 화살표를 클릭한 다음 **받는 사람 도메인이 다음과 같음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-152">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="a54d6-153">창에서 조직 이름 (예: contoso.onmicrosoft.com)을 클릭 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-153">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="a54d6-154">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-154">Click **Save**.</span></span> <span data-ttu-id="a54d6-155">업데이트 후에는 새로운 및 사용 가능한 **안전한 첨부 파일 정책 블록이**표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-155">After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="a54d6-156">**안전한 링크** 탭을 클릭한 다음 + 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="a54d6-157">**새 안전한 링크 정책** 창의 **이름**에 **안전한 링크 정책**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="a54d6-158">**메시지에서 알려지지 않은 잠재적인 악성 URL에 대한 작업 선택**에서 **설정**을 클릭한 다음 **사용자가 원래 URL을 클릭하여 이동하도록 허용하지 않음**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="a54d6-159">**적용 대상**에서 아래쪽 화살표를 클릭한 다음 **받는 사람 도메인이 다음과 같음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-159">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="a54d6-160">창에서 조직 이름 (예: contoso.onmicrosoft.com)을 클릭 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-160">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="a54d6-p108">**저장**을 클릭합니다. 사용 가능한 새로운 **안전한 링크 정책**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="a54d6-163">4단계: 실행되는 ATP 표시</span><span class="sxs-lookup"><span data-stu-id="a54d6-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="a54d6-164">이 단계에서는 ATP에서 잠재적인 악성 전자 메일을 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="a54d6-165">2 단계에서 전자 메일을 보내는 데 사용한 Internet Explorer의 인스턴스에서 왼쪽 탐색 영역의 보낸 편지함을 클릭 합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="a54d6-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="a54d6-166">**새 키**제목의 전자 메일을 클릭 하 고 아래쪽 화살표 아이콘을 클릭 한 다음 **전달을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="a54d6-167">새 메시지의 경우 **받는 사람**에 평가판 구독 Office 365 전역 관리자 이름의 전자 메일 주소를 입력한 다음 **보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="a54d6-168">제목이 **새 여행 웹 사이트인**전자 메일을 클릭 하 고 아래쪽 화살표 아이콘을 클릭 한 다음 **전체 회신**을 클릭 하 고 **보내기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="a54d6-p109">3단계에서 ATP 정책을 구성하는 데 사용한 Internet Explorer의 인스턴스에서 Exchange 관리 센터 탭을 클릭하고 앱 타일을 클릭한 다음 **메일**을 클릭합니다. 받은 편지함에 다음과 같은 새 전자 메일 메시지가 두 개 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="a54d6-171">제목이 **FW: 새 키**인 메시지</span><span class="sxs-lookup"><span data-stu-id="a54d6-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="a54d6-172">제목이 **FW: 새 여행 웹 사이트**인 메시지</span><span class="sxs-lookup"><span data-stu-id="a54d6-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="a54d6-173">**Fw: 새 여행 웹 사이트** 라는 전자 메일 메시지를 열고 **이 사이트** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-173">Open the email message titled **Fw: New travel web site** and click the **this site** link.</span></span> <span data-ttu-id="a54d6-174">"이 웹 사이트가 악성으로 분류 되었습니다."가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-174">You should see a "This website has been classified as malicious."</span></span> <span data-ttu-id="a54d6-175">페이지.</span><span class="sxs-lookup"><span data-stu-id="a54d6-175">page.</span></span> <span data-ttu-id="a54d6-176">이는 ATP가 잠재적으로 악의적인 웹 사이트에 액세스할 수 없다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-176">This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="a54d6-177">Internet Explorer의 Exchange 관리 센터 탭의 왼쪽 탐색 창에서 **메일 흐름**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="a54d6-178">**메시지 추적** 탭을 클릭한 다음 **검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="a54d6-179">**메시지 추적 결과** 창에서 제목이 **새 키**인 메시지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-179">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**.</span></span> <span data-ttu-id="a54d6-180">이 메시지는 받은 편지 함으로 배달 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-180">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="a54d6-181">이 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-181">Close this window.</span></span>
    
10. <span data-ttu-id="a54d6-182">제목이 **새 여행 웹 사이트**인 메시지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-182">Double-click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="a54d6-183">이 메시지는 받은 편지 함으로 배달 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-183">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="a54d6-184">이 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-184">Close this window.</span></span>
    
11. <span data-ttu-id="a54d6-185">제목이 **FW: 새 키**인 메시지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-185">Double-click the message with the subject **Fw: Your new keys**.</span></span> <span data-ttu-id="a54d6-186">ATP에서이 메시지를 처리 한 후 받은 편지 함으로 배달 하는 방법을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="a54d6-186">Note how this message was processed by ATP and then delivered to the Inbox.</span></span> <span data-ttu-id="a54d6-187">이 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-187">Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="a54d6-188">안전한 첨부 파일 정책의 목적은 악성 코드에 대 한 첨부 파일 검색을 시작 하는 것 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-188">The purpose of the safe attachments policy was to begin scanning attachments for malicious code.</span></span> <span data-ttu-id="a54d6-189">GetKeys .js 첨부 파일이 악성으로 확인 되지 않았으므로 허용 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-189">The getKeys.js attachment was allowed because it was not determined to be malicious.</span></span> <span data-ttu-id="a54d6-190">이 단계에서는 ATP가 첨부 파일 검사를 수행 했는지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-190">This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="a54d6-191">제목이 **FW: 새 여행 웹 사이트**인 메시지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-191">Double-click the message with the subject **Fw: New travel web site**.</span></span> <span data-ttu-id="a54d6-192">이 메시지는 받은 편지 함으로 배달 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-192">Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="a54d6-193">이제 이 환경을 사용하여 새 정책을 만들고 ATP를 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="a54d6-194">[여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a54d6-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a54d6-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a54d6-195">See Also</span></span>

[<span data-ttu-id="a54d6-196">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="a54d6-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a54d6-197">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="a54d6-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="a54d6-198">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="a54d6-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a54d6-199">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="a54d6-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="a54d6-200">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="a54d6-200">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="a54d6-201">안전한 첨부 파일 및 안전한 링크를 위한 Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="a54d6-201">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


