---
title: "Office 365 개발/테스트 환경용 Advanced Threat Protection"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "요약: 구성 및 Office 365 개발/테스트 환경에서 Office 365 고급 위협 보호 기능을 시연 합니다."
ms.openlocfilehash: 6266960287d06ffafdf7ed1f6690396fd4cda9d5
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="65adb-103">Office 365 개발/테스트 환경용 Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="65adb-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="65adb-104">**요약:** Office 365 개발/테스트 환경에서 Office 365 고급 위협 보호 시연 및 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="65adb-p101">Office 365 고급 위협 보호 (ATP) 기능의 Exchange Online Protection EOP ()는 데 도움이 되는 전자 메일에서 맬웨어를 유지 됩니다. ATP와 Exchange 관리 센터 (EAC) 또는 보안 정책을 만듭니다 &amp; 사용자에 게 링크 또는 하지 악의적으로 식별 되는 전자 메일에서 첨부 파일에 액세스할 수 있도록 하는 준수 센터입니다. 자세한 내용은 [안전한 첨부 파일 및 안전 링크에 대 한 고급 위협 보호](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="65adb-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="65adb-108">이 문서의 지침을 사용하여 Office 365 평가판 구독의 ATP를 구성하고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="65adb-109">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="65adb-110">최소 요구 사항을 경량 방식으로 ATP를 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="65adb-111">ATP 시뮬레이션 된 엔터프라이즈에서 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="65adb-p102">ATP 테스트에는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server AD 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 ATP를 테스트하고 일반적인 조직을 나타내는 환경에서 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="65adb-114">2 단계: Office 365의 기본 전자 메일 전달 동작을 시연</span><span class="sxs-lookup"><span data-stu-id="65adb-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="65adb-115">이 단계에서는 ATP 정책을 구성하기 전에 잠재적인 악성 전자 메일이 차단 또는 완화되지 않고 Office 365 사서함으로 배달될 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="65adb-116">Internet Explorer를 열고 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)중 2 단계에서에서 만든 Outlook 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="65adb-117">경량 Office 365 개발/테스트 환경을 사용하는 경우 Internet Explorer의 비공개 세션을 열고 로컬 컴퓨터에서 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="65adb-118">시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 [Azure 포털](https://portal.azure.com) 을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음 CLIENT1에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="65adb-119">메모장을 실행하고 일부 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="65adb-120">**GetKeys.js**로 문서 폴더에 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="65adb-121">Internet Explorer의 Outlook 메일 탭에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="65adb-122">(영문) **를**, 평가판 구독에 Office 365 전역 관리자 이름의 전자 메일 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="65adb-123">주제에 대 한 **새 키**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="65adb-124">본문에 **다음은 파일을**입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="65adb-125">**연결**, **getKeys.js** 문서 폴더에서를 두번클릭 하 고 **복사본으로 연결**클릭 **보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="65adb-126">**새**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-126">Click **New**.</span></span>
    
10. <span data-ttu-id="65adb-127">(영문) **를**, 평가판 구독에 Office 365 전역 관리자 이름의 전자 메일 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="65adb-128">주제에 대 한 **새로운 웹사이트 출장**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="65adb-129">본문에 **다른 사람이 전달한이 사이트를**입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="65adb-130">본문에 **이 사이트** 텍스트를 선택 하 고 도구 모음에서 하이퍼링크 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="65adb-131">**URL** **http://www.spamlink.contoso.com/**입력, **확인**을 클릭 하 고 **보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="65adb-132">개인 검색 모드에서 Internet Explorer의 별도 인스턴스를 열고 Office 365 포털 ([https://portal.office.com](https://portal.office.com))로 이동 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="65adb-133">주 포털 페이지에서 앱 타일을 클릭 하 고 **메일**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="65adb-134">받은 편지함에서 제목에 **새 키**와 메시지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="65adb-p103">정크 메일 폴더에서 **새로운 웹사이트 출장**주체와 메시지를 클릭 합니다. 메시지를 내에서 **이 사이트** 링크를 클릭 합니다. "Oops 나타나야 합니다.! Internet Explorer 찾을 수 없습니다 spamlink.contoso.com."페이지입니다. 해당 위치에 없는 웹 페이지 때문에 올바른 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="65adb-p104">이러한 위험할 수 있는 전자 메일을 모두 성공적으로 배달 된 알 수 있습니다. **새 키에** 전자 메일 검색 되지 않은 맬웨어를 포함 될 수 및 **새로운 웹사이트 출장을** 전자 메일에서 위험할 수 있는 링크를 클릭 하는 사용자가 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="65adb-143">3단계: ATP의 안전한 첨부 파일 및 안전한 링크 정책 구성</span><span class="sxs-lookup"><span data-stu-id="65adb-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="65adb-144">이 단계에서는 안전한 첨부 파일 정책을 만들고 구성하여 잠재적인 악성 첨부 파일이 배달되지 않도록 하고 안전한 링크 정책을 통해 사용자가 잠재적으로 안전하지 않은 URL로 이동할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="65adb-145">Internet Explorer의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="65adb-146">왼쪽 탐색 영역에서 **관리 센터**, 및 **Exchange**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="65adb-147">Exchange 관리 센터 탭의 왼쪽 탐색 영역에서 **고급 위협 요소**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="65adb-148">**안전한 첨부 파일** 탭을 클릭 하 고 더하기 기호를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="65adb-149">**이름** **새 안전한 첨부 파일 정책** 창에서 **안전한 첨부 파일 정책-블록을**입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="65adb-150">**알 수 없는 맬웨어 응답 안전한 첨부 파일**대 한 **차단**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="65adb-151">**검색에서 첨부 파일을 리디렉션**에에 대 한 **리디렉션 사용** 을 클릭 하 고 Office 365 전역 관리자 계정의 전자 메일 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="65adb-p105">**에 적용 되며**대 한 아래쪽 화살표를 클릭 하 고 **받는 사람 도메인은**를 클릭 합니다. 창에서 조직 이름 (예: contoso.onmicrosoft.com 형식)를 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="65adb-p106">**저장**을 클릭 합니다. 업데이트 된 후 새 나타납니다 및 **안전한 첨부 파일 정책-블록을**사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="65adb-156">**안전한 링크** 탭을 클릭 하 고 더하기 기호를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="65adb-157">**이름** **새 안전한 링크 정책** 창에서 **안전한 링크 정책**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="65adb-158">**메시지에 알 수 없는 위험할 수 있는 Url에 대 한 작업을 선택**하는 것에 대 한 **에서**클릭 하 고 **사용자가 클릭 하 여 원래 URL을을 허용 하지 않습니다**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="65adb-p107">**에 적용 되며**대 한 아래쪽 화살표를 클릭 하 고 **받는 사람 도메인은**를 클릭 합니다. 창에서 조직 이름 (예: contoso.onmicrosoft.com 형식)를 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="65adb-p108">**저장**을 클릭 합니다. 새 참조 해야 하 고이 정보를 **안전한 링크 정책**를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="65adb-163">4단계: 실행되는 ATP 표시</span><span class="sxs-lookup"><span data-stu-id="65adb-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="65adb-164">이 단계에서는 ATP에서 잠재적인 악성 전자 메일을 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="65adb-165">Internet Explorer의 왼쪽된 탐색 영역에서 2 단계에서에서 전자 메일을 보내는 데 사용 하는 인스턴스에서 클릭 **보낸편지함.**</span><span class="sxs-lookup"><span data-stu-id="65adb-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="65adb-166">**새 키**라는 제목의 전자 메일을 클릭 하 고 아래쪽 화살표 아이콘을 클릭 **전달**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="65adb-167">(영문) **를**, 새 메시지에 대 한 평가판 구독에 Office 365 전역 관리자 이름의 전자 메일 주소를 입력 하 고 **보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="65adb-168">**새로 만들기 출장 웹사이트**라는 제목의 전자 메일, 아래쪽 화살표 아이콘을 클릭 하 고 **전체 회신**을 클릭 **보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="65adb-p109">3 단계에서에서 ATP 정책을 구성 하는 사용 되는 Internet Explorer의 인스턴스에서 Exchange 관리 센터 탭을 클릭, 앱 타일을 클릭 하 고 **메일**을 클릭 합니다. 받은 편지함의 두 새 전자 메일 메시지를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="65adb-171">1 이라는 **펌웨어: 새 키**</span><span class="sxs-lookup"><span data-stu-id="65adb-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="65adb-172">1 이라는 **펌웨어: 새 출장 웹사이트**</span><span class="sxs-lookup"><span data-stu-id="65adb-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="65adb-p110">라는 제목의 전자 메일 메시지를 열고 **펌웨어: 새 출장 웹사이트** **이 사이트** 링크를 클릭 하 고 있습니다. "이이 웹사이트 분류 않은 악성 소프트웨어로." 페이지를 참조 해야 합니다. ATP 인해 없음을 하면 위험할 수 있는 웹사이트에 액세스 하지 못하도록 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="65adb-177">왼쪽 탐색 영역에서 Internet Explorer의 Exchange 관리 센터 탭에서 **메일 흐름**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="65adb-178">**메시지 추적** 탭을 클릭 하 고 **검색**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="65adb-p111">**메시지 추적 결과** 창에서 **새 키에**제목 포함 된 메시지를 두번클릭 합니다. 이 메시지가 받은 편지 함으로 배달 되었습니다. 이 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="65adb-p112">**새로 만들기 출장 웹사이트**제목 포함 된 메시지를 두번클릭 합니다. 이 메시지가 받은 편지 함으로 배달 되었습니다. 이 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="65adb-p113">제목 포함 된 메시지를 두번클릭 **펌웨어: 새 키에**합니다. 이 메시지 된 ATP에서 처리 하 고 다음 편지 함으로 배달 하는 방법을 note 합니다. 이 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="65adb-p114">안전한 첨부 파일 정책의 목적 악성 코드에 대 한 첨부 파일을 검색을 시작 했습니다. GetKeys.js 첨부 파일에는 악성 코드가 포함 될를 결정 하지 되었으므로 하도록 허용 되었습니다. 이 단계에서는 ATP 첨부 파일의 검색을 수행 않은 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="65adb-p115">제목 포함 된 메시지를 두번클릭 **펌웨어: 새 출장 웹사이트**합니다. 이 메시지는 받은 편지함에 성공적으로 배달 하는 내용의 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="65adb-193">이제 이 환경을 사용하여 새 정책을 만들고 ATP를 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="65adb-194">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="65adb-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="65adb-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65adb-195">See Also</span></span>

[<span data-ttu-id="65adb-196">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="65adb-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="65adb-197">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="65adb-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="65adb-198">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="65adb-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="65adb-199">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="65adb-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="65adb-200">Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안</span><span class="sxs-lookup"><span data-stu-id="65adb-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="65adb-201">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="65adb-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="65adb-202">안전한 첨부 파일 및 안전 링크에 대 한 고급 위협 보호</span><span class="sxs-lookup"><span data-stu-id="65adb-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


