---
title: Office 365 레이블 및 DLP를 사용하여 SharePoint Online 파일 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: '요약: 다양한 정보 보호 수준을 통해 SharePoint Online 팀 사이트에 Office 365 레이블 및 DLP(데이터 손실 방지) 정책을 적용합니다.'
ms.openlocfilehash: 52617e43f5c1bcb2ab958e751734a2f948ceba37
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="83b16-103">Office 365 레이블 및 DLP를 사용하여 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="83b16-103">Protect SharePoint Online files with Office 365 labels and Data Loss Prevention</span></span>

 <span data-ttu-id="83b16-104">**요약:** 다양한 정보 보호 수준을 통해 SharePoint Online 팀 사이트에 Office 365 레이블 및 DLP(데이터 손실 방지) 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="83b16-p101">이 문서의 단계를 사용하여 초기, 중요 및 극비 SharePoint Online 팀 사이트에 대한 Office 365 레이블 및 DLP 정책을 디자인하고 배포합니다. 이러한 3계층 보호에 대한 자세한 내용은 [SharePoint Online 사이트 및 파일 보호](secure-sharepoint-online-sites-and-files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83b16-p101">Use the steps in this article to design and deploy Office 365 labels and Data Loss Prevention (DLP) policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="83b16-107">SharePoint Online 사이트에 대한 Office 365 레이블</span><span class="sxs-lookup"><span data-stu-id="83b16-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="83b16-108">SharePoint Online 팀 사이트에 Office 365 레이블을 만들고 할당하는 경우 다음 세 가지 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-108">You must complete the following three phases when creating and assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="83b16-109">1단계: Office 365 레이블 이름 결정</span><span class="sxs-lookup"><span data-stu-id="83b16-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="83b16-p102">이 단계에서는 SharePoint Online 팀 사이트에 적용되는 네 가지 정보 보호 수준에 대한 Office 365 레이블의 이름을 결정합니다. 다음 표에는 각 수준에 권장되는 이름이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="83b16-112">**SharePoint Online 팀 사이트 보호 수준**</span><span class="sxs-lookup"><span data-stu-id="83b16-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="83b16-113">**레이블 이름**</span><span class="sxs-lookup"><span data-stu-id="83b16-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="83b16-114">초기 공용</span><span class="sxs-lookup"><span data-stu-id="83b16-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="83b16-115">내부 공용</span><span class="sxs-lookup"><span data-stu-id="83b16-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="83b16-116">초기 개인</span><span class="sxs-lookup"><span data-stu-id="83b16-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="83b16-117">개인</span><span class="sxs-lookup"><span data-stu-id="83b16-117">Private</span></span>  <br/> |
|<span data-ttu-id="83b16-118">중요</span><span class="sxs-lookup"><span data-stu-id="83b16-118">Sensitive</span></span>  <br/> |<span data-ttu-id="83b16-119">중요</span><span class="sxs-lookup"><span data-stu-id="83b16-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="83b16-120">극비</span><span class="sxs-lookup"><span data-stu-id="83b16-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="83b16-121">극비</span><span class="sxs-lookup"><span data-stu-id="83b16-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="83b16-122">2단계: Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="83b16-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="83b16-123">이 단계에서는 서로 다른 수준의 정보 보호를 위해 결정한 레이블을 만들어 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="83b16-124">레이블을 만들려면 Office 365 관리 센터 또는 Microsoft PowerShell을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="83b16-125">Office 365 관리 센터를 사용하여 Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="83b16-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="83b16-p103">보안 관리자 또는 회사 관리자 역할이 있는 계정으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83b16-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="83b16-128">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="83b16-129">브라우저의 새 **Office 관리 센터** 탭에서 **관리 센터 > 보안 및 준수**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-129">From the new Office Admin center tab of your browser, click Admin centers > Security & Compliance.</span></span>
    
4. <span data-ttu-id="83b16-130">브라우저의 새 **홈 - 보안 및 준수** 탭에서 **분류 > 레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-130">From the new Home – Security & Compliance tab of your browser, click Classifications > Labels.</span></span>
    
5. <span data-ttu-id="83b16-131">**홈 > 레이블** 창에서 **레이블 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="83b16-132">**레이블** 창에서 레이블 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-132">On the **Name your label** pane, type the name of the label, and click **Next**.</span></span>
    
7. <span data-ttu-id="83b16-133">**레이블 설정** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="83b16-134">**설정 검토** 창에서 **이 레이블 만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-134">On the **Review your settings** pane, click **Create this label**, and click **Close**.</span></span>
    
9. <span data-ttu-id="83b16-135">레이블을 추가하려면 5-8단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="83b16-136">PowerShell을 사용하여 Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="83b16-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="83b16-137">[원격 PowerShell을 사용하여 Office 365 보안 및 준수 센터에 연결하고](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) 보안 관리자 또는 회사 관리자 역할이 있는 계정의 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-137">Connect to the Office 365 Security & Compliance Center using remote PowerShell and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="83b16-138">레이블 이름 목록을 작성한 다음 PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="83b16-139">그리고 나서 다음 단계를 사용하여 새 Office 365 레이블을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="83b16-140">보안 및 준수 센터의 **홈 > 레이블** 창에서 **레이블 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-140">From the Home > Labels pane in the Security & Compliance Center, click Publish labels.</span></span>
    
2. <span data-ttu-id="83b16-141">**게시할 레이블 선택** 창에서 **게시할 레이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="83b16-142">**레이블 선택** 창에서 **추가**를 클릭하고 네 개의 레이블을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="83b16-143">**완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="83b16-144">**게시할 레이블 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="83b16-145">**위치 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="83b16-146">**정책 이름 지정** 창의 **이름**에서 레이블 집합 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and click **Next**.</span></span>
    
8. <span data-ttu-id="83b16-147">**설정 검토** 창에서 **레이블 게시**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-147">On the **Review your settings** pane, click **Publish labels**, and click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="83b16-148">3단계: SharePoint Online 사이트에 Office 365 레이블 적용</span><span class="sxs-lookup"><span data-stu-id="83b16-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="83b16-149">다음 단계에 따라 Office 365 레이블을 SharePoint Online 팀 사이트의 문서 폴더에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="83b16-150">브라우저의 **Microsoft Office 홈** 탭에서 **SharePoint** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="83b16-151">브라우저의 새 **SharePoint** 탭에서 할당된 Office 365 레이블이 필요한 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="83b16-152">브라우저의 새 SharePoint 사이트 탭에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="83b16-153">설정 아이콘을 클릭한 다음 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="83b16-154">**권한 및 관리** 아래에서 **Apply label to items in this library(이 라이브러리의 항목에 레이블 적용)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="83b16-155">**설정 - 레이블 적용**에서 적절한 레이블을 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-155">In **Settings-Apply Label**, select the appropriate label, and click **Save**.</span></span>
    
7. <span data-ttu-id="83b16-156">SharePoint Online 사이트의 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="83b16-157">3-8단계를 반복하여 추가 SharePoint Online 사이트에 Office 365 레이블을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="83b16-158">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-158">Here is your resulting configuration.</span></span>
  
![SharePoint Online 팀 사이트의 네 가지 유형에 대한 Office 365 레이블입니다.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="83b16-160">SharePoint Online 사이트에 대한 DLP 정책</span><span class="sxs-lookup"><span data-stu-id="83b16-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="83b16-161">다음 단계를 사용하여 사용자가 조직 외부의 중요 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자에게 알려주는 DLP 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="83b16-162">브라우저의 **Microsoft Office 홈** 탭에서 **보안 및 준수** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-162">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="83b16-163">브라우저의 새 **보안 및 준수** 탭에서 **데이터 손실 방지 > 정책**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-163">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="83b16-164">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="83b16-165">**서식 파일로 시작하거나 사용자 지정 정책 만들기** 창에서 **사용자 지정**, **다음**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
5. <span data-ttu-id="83b16-166">**정책 이름 지정** 창의 **이름**에서 중요 수준 DLP 정책의 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-166">In the Name your policy pane, type the name for the sensitive level DLP policy in Name, and click Next.</span></span>
    
6. <span data-ttu-id="83b16-167">**위치 선택** 창에서 **특정 위치 선택 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="83b16-168">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용하지 않도록 설정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and click **Next**.</span></span>
    
8. <span data-ttu-id="83b16-169">**보호할 중요 정보의 유형 사용자 지정** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="83b16-170">**보호할 콘텐츠 유형 선택** 창의 드롭다운 상자에서 **추가**, **레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and click **Labels**.</span></span>
    
10. <span data-ttu-id="83b16-171">**레이블** 창에서 **+ 추가**를 클릭하고, **중요** 레이블을 선택하고, **추가**를 클릭한 다음, **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and click **Done**.</span></span>
    
11. <span data-ttu-id="83b16-172">**보호할 콘텐츠 유형 선택** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="83b16-173">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="83b16-174">**중요한 정보를 발견하면 ** 창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="83b16-175">**Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="83b16-176">텍스트 상자에 다음을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="83b16-p104">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="83b16-180">또는 조직 외부의 파일을 공유하는 방법을 사용자에게 지시하는 사용자 고유의 정책 팁을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-180">Or type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="83b16-181">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="83b16-182">**중요한 정보를 감지하는 경우 어떻게 하시겠어요?** 창에서 **사용자의 공유를 차단하고 공유 콘텐츠에 대한 액세스를 제한** 확인란의 선택을 취소하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and click **Next**.</span></span>
    
18. <span data-ttu-id="83b16-183">**정책을 켤까요 아니면 먼저 테스트를 수행할까요?** 창에서 **예, 지금 켜겠습니다.** 를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes**, turn it on right away, and click **Next**.</span></span>
    
19. <span data-ttu-id="83b16-184">**설정 검토 창**에서 **만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-184">In the **Review your settings** pane, click **Create**, and click **Close**.</span></span>
    
<span data-ttu-id="83b16-185">결과적으로 중요 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![중요한 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="83b16-187">그리고 나서 다음 단계를 사용하여 사용자가 조직 외부의 극비 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자를 차단하는 DLP 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="83b16-188">브라우저의 **Microsoft Office 홈** 탭에서 **보안 및 준수** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-188">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="83b16-189">브라우저의 새 **보안 및 준수** 탭에서 **데이터 손실 방지 > 정책**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-189">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="83b16-190">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="83b16-191">**서식 파일로 시작하거나 사용자 지정 정책 만들기** 창에서 **사용자 지정**, **다음**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
5. <span data-ttu-id="83b16-192">**정책 이름 지정** 창의 **이름**에서 이름에 극비 수준 DLP 정책의 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and click **Next**.</span></span>
    
6. <span data-ttu-id="83b16-193">**위치 선택** 창에서 **특정 위치 선택 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="83b16-194">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용하지 않도록 설정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and click **Next**.</span></span>
    
8. <span data-ttu-id="83b16-195">**보호할 중요 정보의 유형 사용자 지정** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="83b16-196">**보호할 콘텐츠 유형 선택** 창의 드롭다운 상자에서 **추가**, **레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and click **Labels**.</span></span>
    
10. <span data-ttu-id="83b16-197">**레이블** 창에서 **+ 추가**를 클릭하고, **극비** 레이블을 선택하고, **추가**를 클릭한 다음, **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential label**, click **Add**, and click **Done**.</span></span>
    
11. <span data-ttu-id="83b16-198">**보호할 콘텐츠 유형 선택** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="83b16-199">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="83b16-200">**중요한 정보를 발견하면 ** 창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="83b16-201">**Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="83b16-202">텍스트 상자에 다음을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="83b16-p105">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="83b16-206">또는 조직 외부의 파일을 공유하는 방법을 사용자에게 지시하는 사용자 고유의 정책 팁을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-206">Or type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="83b16-207">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="83b16-208">**중요한 정보를 감지하는 경우 어떻게 하시겠어요?** 창에서 **재정의하려면 비즈니스 사유 필요**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and click **Next**.</span></span>
    
18. <span data-ttu-id="83b16-209">**정책을 켤까요 아니면 먼저 테스트를 수행할까요?** 창에서 **예, 지금 켜겠습니다.** 를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes**, turn it on right away, and click **Next**.</span></span>
    
19. <span data-ttu-id="83b16-210">**설정 검토 창**에서 **만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-210">In the **Review your settings** pane, click **Create**, and click **Close**.</span></span>
    
<span data-ttu-id="83b16-211">결과적으로 극비 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83b16-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![높은 수준의 기밀 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="83b16-213">다음 단계</span><span class="sxs-lookup"><span data-stu-id="83b16-213">Next step</span></span>

[<span data-ttu-id="83b16-214">Azure Information Protection을 사용한 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="83b16-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="83b16-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83b16-215">See Also</span></span>

[<span data-ttu-id="83b16-216">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="83b16-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="83b16-217">개발/테스트 환경의 SharePoint Online 사이트 보호</span><span class="sxs-lookup"><span data-stu-id="83b16-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="83b16-218">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="83b16-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="83b16-219">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="83b16-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


