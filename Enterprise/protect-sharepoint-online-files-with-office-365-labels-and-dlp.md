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
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: '요약: 다양한 정보 보호 수준을 통해 SharePoint Online 팀 사이트에 Office 365 레이블 및 DLP(데이터 손실 방지) 정책을 적용합니다.'
ms.openlocfilehash: 1e83f8c08dde55c22b7b9e8e6f9fe966c9fe9c02
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915783"
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="d9c87-103">Office 365 레이블 및 DLP를 사용하여 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="d9c87-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="d9c87-104">**요약:** 다양한 정보 보호 수준을 통해 SharePoint Online 팀 사이트에 Office 365 레이블 및 DLP(데이터 손실 방지) 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="d9c87-p101">이 문서의 단계를 사용하여 초기, 중요 및 극비 SharePoint Online 팀 사이트에 대한 Office 365 레이블 및 DLP 정책을 디자인하고 배포합니다. 이러한 3계층 보호에 대한 자세한 내용은 [SharePoint Online 사이트 및 파일 보호](secure-sharepoint-online-sites-and-files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="how-this-works"></a><span data-ttu-id="d9c87-107">작동 방식</span><span class="sxs-lookup"><span data-stu-id="d9c87-107">How this works</span></span>
1. <span data-ttu-id="d9c87-p102">원하는 레이블을 만들고 게시합니다. 레이블을 게시하는 데 최대 12시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p102">Create the desired labels and publish these. It can take up to 12 hours for these to be published.</span></span>
2. <span data-ttu-id="d9c87-110">원하는 SharePoint 사이트에서 문서 라이브러리 설정을 편집하여 레이블을 라이브러리의 항목에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-110">For the desired SharePoint sites, edit the document library settings to apply a label to items in the library.</span></span>
3. <span data-ttu-id="d9c87-111">레이블을 기반으로 작업을 수행하는 Create DLP 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-111">Create DLP policies to take action based on the labels.</span></span>

<span data-ttu-id="d9c87-p103">사용자가 라이브러리에 문서를 추가하면 문서에 기본적으로 레이블이 할당됩니다. 필요한 경우 사용자는 레이블을 변경할 수 있습니다. 사용자가 조직 외부에서 문서를 공유하면 레이블이 할당되어있는지 DLP가 체크하고 레이블이 DLP 정책에 일치하면 작업을 수행합니다l. 이러한 유형의 정책이 구성되면 DLP는 신용카드 번호가 포함된 파일 보호와 같은 다른 정책이 일치하는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p103">When users add a document to the library, the document will receive the assigned label by default. Users can change the label,if needed. When a user shares a document outside the organization, DLP will check to see if a label is assigned and take action if a DLP policy matches the label. DLP will look for other policy matches as well, such as protecting files with credit card numbers if this type of policy is configured.</span></span> 

## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="d9c87-116">SharePoint Online 사이트에 대한 Office 365 레이블</span><span class="sxs-lookup"><span data-stu-id="d9c87-116">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="d9c87-117">SharePoint Online 팀 사이트에 Office 365 레이블을 만들고 할당하는 경우 다음 세 가지 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-117">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="d9c87-118">1단계: Office 365 레이블 이름 결정</span><span class="sxs-lookup"><span data-stu-id="d9c87-118">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="d9c87-p104">이 단계에서는 SharePoint Online 팀 사이트에 적용되는 네 가지 정보 보호 수준에 대한 Office 365 레이블의 이름을 결정합니다. 다음 표에는 각 수준에 권장되는 이름이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p104">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="d9c87-121">**SharePoint Online 팀 사이트 보호 수준**</span><span class="sxs-lookup"><span data-stu-id="d9c87-121">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="d9c87-122">**레이블 이름**</span><span class="sxs-lookup"><span data-stu-id="d9c87-122">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d9c87-123">초기 공용</span><span class="sxs-lookup"><span data-stu-id="d9c87-123">Baseline-Public</span></span>  <br/> |<span data-ttu-id="d9c87-124">내부 공용</span><span class="sxs-lookup"><span data-stu-id="d9c87-124">Internal public</span></span>  <br/> |
|<span data-ttu-id="d9c87-125">초기 개인</span><span class="sxs-lookup"><span data-stu-id="d9c87-125">Baseline-Private</span></span>  <br/> |<span data-ttu-id="d9c87-126">개인</span><span class="sxs-lookup"><span data-stu-id="d9c87-126">Private</span></span>  <br/> |
|<span data-ttu-id="d9c87-127">중요</span><span class="sxs-lookup"><span data-stu-id="d9c87-127">Sensitive</span></span>  <br/> |<span data-ttu-id="d9c87-128">중요</span><span class="sxs-lookup"><span data-stu-id="d9c87-128">Sensitive</span></span>  <br/> |
|<span data-ttu-id="d9c87-129">극비</span><span class="sxs-lookup"><span data-stu-id="d9c87-129">Highly Confidential</span></span>  <br/> |<span data-ttu-id="d9c87-130">극비</span><span class="sxs-lookup"><span data-stu-id="d9c87-130">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="d9c87-131">2단계: Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="d9c87-131">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="d9c87-132">이 단계에서는 서로 다른 수준의 정보 보호를 위해 결정한 레이블을 만들어 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-132">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="d9c87-133">레이블을 만들려면 Office 365 관리 센터 또는 Microsoft PowerShell을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-133">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="d9c87-134">Office 365 관리 센터를 사용하여 Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="d9c87-134">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="d9c87-p105">보안 관리자 또는 회사 관리자 역할이 있는 계정으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d9c87-137">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-137">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="d9c87-138">브라우저의 새 **Office 관리 센터** 탭에서 **관리 센터 > 보안 및 준수**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-138">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="d9c87-139">브라우저의 새 **홈 - 보안 및 준수** 탭에서 **분류 > 레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-139">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="d9c87-140">**홈 > 레이블** 창에서 **레이블 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-140">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="d9c87-141">**레이블** 창에서 레이블 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-141">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d9c87-142">**레이블 설정** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-142">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="d9c87-143">**설정 검토** 창에서 **이 레이블 만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-143">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="d9c87-144">레이블을 추가하려면 5-8단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-144">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="d9c87-145">PowerShell을 사용하여 Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="d9c87-145">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="d9c87-146">[원격 PowerShell을 사용하여 Office 365 보안 및 준수 센터에 연결하고](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) 보안 관리자 또는 회사 관리자 역할이 있는 계정의 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-146">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="d9c87-147">레이블 이름 목록을 작성한 다음 PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-147">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="d9c87-148">그리고 나서 다음 단계를 사용하여 새 Office 365 레이블을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-148">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="d9c87-149">보안 및 준수 센터의 **홈 > 레이블** 창에서 **레이블 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-149">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="d9c87-150">**게시할 레이블 선택** 창에서 **게시할 레이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-150">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="d9c87-151">**레이블 선택** 창에서 **추가**를 클릭하고 네 개의 레이블을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-151">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="d9c87-152">**완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-152">Click **Done**.</span></span>
    
5. <span data-ttu-id="d9c87-153">**게시할 레이블 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-153">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="d9c87-154">**위치 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-154">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="d9c87-155">**정책 이름 지정** 창의 **이름**에서 레이블 집합 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-155">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d9c87-156">**설정 검토** 창에서 **레이블 게시**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-156">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="d9c87-157">3단계: SharePoint Online 사이트에 Office 365 레이블 적용</span><span class="sxs-lookup"><span data-stu-id="d9c87-157">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="d9c87-158">다음 단계에 따라 Office 365 레이블을 SharePoint Online 팀 사이트의 문서 폴더에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-158">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="d9c87-159">브라우저의 **Microsoft Office 홈** 탭에서 **SharePoint** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-159">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="d9c87-160">브라우저의 새 **SharePoint** 탭에서 할당된 Office 365 레이블이 필요한 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-160">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="d9c87-161">브라우저의 새 SharePoint 사이트 탭에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-161">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="d9c87-162">설정 아이콘을 클릭한 다음 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-162">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="d9c87-163">**권한 및 관리** 아래에서 **Apply label to items in this library(이 라이브러리의 항목에 레이블 적용)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-163">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="d9c87-164">**설정 - 레이블 적용**에서 적절한 레이블을 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-164">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="d9c87-165">SharePoint Online 사이트의 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-165">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="d9c87-166">3-8단계를 반복하여 추가 SharePoint Online 사이트에 Office 365 레이블을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-166">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="d9c87-167">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-167">Here is your resulting configuration.</span></span>
  
![SharePoint Online 팀 사이트의 네 가지 유형에 대한 Office 365 레이블입니다.](media/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="d9c87-169">SharePoint Online 사이트에 대한 DLP 정책</span><span class="sxs-lookup"><span data-stu-id="d9c87-169">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="d9c87-170">다음 단계를 사용하여 사용자가 조직 외부의 중요 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자에게 알려주는 DLP 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-170">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="d9c87-171">브라우저의 **Microsoft Office 홈** 탭에서 **보안 및 준수** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-171">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="d9c87-172">브라우저의 새 **보안 및 준수** 탭에서 **데이터 손실 방지 > 정책**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-172">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="d9c87-173">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-173">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="d9c87-174">**서식 파일로 시작하거나 사용자 지정 정책 만들기** 창에서 **사용자 지정**, **다음**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-174">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="d9c87-175">**정책 이름 지정** 창의 **이름**에서 중요 수준 DLP 정책의 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-175">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d9c87-176">**위치 선택** 창에서 **특정 위치 선택 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-176">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d9c87-177">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용하지 않도록 설정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-177">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d9c87-178">**보호할 중요 정보의 유형 사용자 지정** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-178">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="d9c87-179">**보호할 콘텐츠 유형 선택** 창의 드롭다운 상자에서 **추가**, **레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-179">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="d9c87-180">**레이블** 창에서 **+ 추가**를 클릭하고, **중요** 레이블을 선택하고, **추가**를 클릭한 다음, **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-180">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="d9c87-181">**보호할 콘텐츠 유형 선택** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-181">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="d9c87-182">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-182">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="d9c87-183">**중요한 정보를 발견하면 ** 창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-183">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="d9c87-184">**정책 팁 및 전자 메일 알림 사용자 지정** 창에서 **정책 팁 텍스트 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-184">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="d9c87-185">Azure Information Protection에서 극비 파일을 보호하도록 구현했는지에 따라 텍스트 상자에 다음 팁 중 하나를 입력하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-185">In the text box, type or paste in one of the following tips, depending on if you implemented Azure Information Protection to protect highly confidential files:</span></span>
    
  - <span data-ttu-id="d9c87-p106">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p106">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
  - <span data-ttu-id="d9c87-p107">극비 파일은 암호화를 통해 보호됩니다. IT 부서에서 사용 권한을 부여받은 외부 사용자만 극비 파일을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p107">Highly confidential files are protected with encryption. Only external users who are granted permissions to these files by your IT department can read them.</span></span>
    
    <span data-ttu-id="d9c87-p108">또는 조직 외부의 파일을 공유하는 방법을 사용자에게 지시하는 사용자 고유의 정책 팁을 입력하거나 붙여넣습니다. Azure Information Protection으로 보호된 파일에 외부 사용자 권한을 부여하는 방법에 대한 자세한 정보는 외부 사용자에 대한 권한 추가를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p108">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization. For more information on giving external users permissions to files protected wiht Azure Information Protection, see Adding permissions for external users.</span></span>
    
16. <span data-ttu-id="d9c87-193">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-193">Click **OK**.</span></span>
    
17. <span data-ttu-id="d9c87-194">**중요한 정보를 감지하는 경우 어떻게 하시겠어요?** 창에서 **사용자의 공유를 차단하고 공유 콘텐츠에 대한 액세스를 제한** 확인란의 선택을 취소하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-194">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="d9c87-195">**정책을 켤까요 아니면 먼저 테스트를 수행할까요?** 창에서 **예, 지금 켜겠습니다.** 를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-195">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d9c87-196">**설정 검토 창**에서 **만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-196">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="d9c87-197">결과적으로 중요 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-197">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![중요한 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](media/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="d9c87-199">그리고 나서 다음 단계를 사용하여 사용자가 조직 외부의 극비 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자를 차단하는 DLP 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-199">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="d9c87-200">브라우저의 **Microsoft Office 홈** 탭에서 **보안 및 준수** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-200">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="d9c87-201">브라우저의 새 **보안 및 준수** 탭에서 **데이터 손실 방지 > 정책**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-201">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="d9c87-202">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-202">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="d9c87-203">**서식 파일로 시작하거나 사용자 지정 정책 만들기** 창에서 **사용자 지정**, **다음**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-203">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="d9c87-204">**정책 이름 지정** 창의 **이름**에서 이름에 극비 수준 DLP 정책의 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-204">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d9c87-205">**위치 선택** 창에서 **특정 위치 선택 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-205">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d9c87-206">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용하지 않도록 설정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-206">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d9c87-207">**보호할 중요 정보의 유형 사용자 지정** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-207">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="d9c87-208">**보호할 콘텐츠 유형 선택** 창의 드롭다운 상자에서 **추가**, **레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-208">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="d9c87-209">**레이블** 창에서 **+ 추가**를 클릭하고, **극비** 레이블을 선택하고, **추가**를 클릭한 다음, **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-209">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="d9c87-210">**보호할 콘텐츠 유형 선택** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-210">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="d9c87-211">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-211">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="d9c87-212">**중요한 정보를 발견하면 ** 창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-212">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="d9c87-213">**Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-213">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="d9c87-214">텍스트 상자에 다음을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-214">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="d9c87-p109">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-p109">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="d9c87-218">또는 조직 외부의 파일을 공유하는 방법을 사용자에게 지시하는 사용자 고유의 정책 팁을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-218">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="d9c87-219">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="d9c87-220">**중요한 정보를 감지하는 경우 어떻게 하시겠어요?** 창에서 **재정의하려면 비즈니스 사유 필요**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-220">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="d9c87-221">**정책을 켤까요 아니면 먼저 테스트를 수행할까요?** 창에서 **예, 지금 켜겠습니다.** 를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d9c87-222">**설정 검토 창**에서 **만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="d9c87-223">결과적으로 극비 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c87-223">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![높은 수준의 기밀 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](media/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="d9c87-225">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d9c87-225">Next step</span></span>

[<span data-ttu-id="d9c87-226">Azure Information Protection을 사용한 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="d9c87-226">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="d9c87-227">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9c87-227">See Also</span></span>

[<span data-ttu-id="d9c87-228">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="d9c87-228">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="d9c87-229">개발/테스트 환경의 보안 SharePoint Online 사이트</span><span class="sxs-lookup"><span data-stu-id="d9c87-229">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="d9c87-230">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="d9c87-230">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="d9c87-231">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="d9c87-231">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


