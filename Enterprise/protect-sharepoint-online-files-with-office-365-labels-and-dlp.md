---
title: Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 파일 보호
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
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: '요약: 다양 한 수준의 정보 보호와 SharePoint Online 팀 사이트에 대 한 Office 365 레이블 및 데이터 손실 방지 (DLP) 정책을 적용 합니다.'
ms.openlocfilehash: a6413ac556cf63cbe7491180d65b4425cd0dba3d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="c410a-103">Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="c410a-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="c410a-104">**요약:** 정보 보호의 다양 한 수준 사용 하 여 SharePoint Online 팀 사이트에 대 한 Office 365 레이블 및 데이터 손실 방지 (DLP) 정책을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="c410a-p101">이 문서의 단계를 사용 하 여 디자인 하 고 Office 365 레이블 및 초기 계획, 소문자를 구분 하 고 매우 기밀 SharePoint Online 팀 사이트에 대 한 DLP 정책 배포 합니다. 이러한 세 계층의 보호 하는 방법에 대 한 자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](secure-sharepoint-online-sites-and-files.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c410a-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="c410a-107">SharePoint Online 사이트에 대한 Office 365 레이블</span><span class="sxs-lookup"><span data-stu-id="c410a-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="c410a-108">만들기 (영문)을 세 단계로 되며 Office 365를 할당 한 다음 SharePoint Online 팀 사이트에 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-108">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="c410a-109">1단계: Office 365 레이블 이름 결정</span><span class="sxs-lookup"><span data-stu-id="c410a-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="c410a-p102">이 단계에서는 SharePoint Online 팀 사이트에 적용되는 네 가지 정보 보호 수준에 대한 Office 365 레이블의 이름을 결정합니다. 다음 표에는 각 수준에 권장되는 이름이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="c410a-112">**SharePoint Online 팀 사이트 보호 수준**</span><span class="sxs-lookup"><span data-stu-id="c410a-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="c410a-113">**레이블 이름**</span><span class="sxs-lookup"><span data-stu-id="c410a-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c410a-114">초기 공용</span><span class="sxs-lookup"><span data-stu-id="c410a-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="c410a-115">내부 공용</span><span class="sxs-lookup"><span data-stu-id="c410a-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="c410a-116">초기 개인</span><span class="sxs-lookup"><span data-stu-id="c410a-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="c410a-117">개인</span><span class="sxs-lookup"><span data-stu-id="c410a-117">Private</span></span>  <br/> |
|<span data-ttu-id="c410a-118">중요</span><span class="sxs-lookup"><span data-stu-id="c410a-118">Sensitive</span></span>  <br/> |<span data-ttu-id="c410a-119">중요</span><span class="sxs-lookup"><span data-stu-id="c410a-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="c410a-120">극비</span><span class="sxs-lookup"><span data-stu-id="c410a-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="c410a-121">극비</span><span class="sxs-lookup"><span data-stu-id="c410a-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="c410a-122">2단계: Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="c410a-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="c410a-123">이 단계에서는 서로 다른 수준의 정보 보호를 위해 결정한 레이블을 만들어 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="c410a-124">레이블을 만들려면 Office 365 관리 센터 또는 Microsoft PowerShell을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="c410a-125">Office 365 관리 센터를 사용 하 여 Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="c410a-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="c410a-p103">보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c410a-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c410a-128">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c410a-129">브라우저의 새 **Office 관리 센터** 탭을 클릭 **관리 센터 > 보안 &amp; 준수**합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-129">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="c410a-130">새에서 **홈-보안 &amp; 준수** 탭 클릭 하 여 브라우저의 **분류 > 레이블**합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-130">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="c410a-131">**홈 > 레이블** 창에서 **레이블 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="c410a-132">**이름에 레이블** 창에서 레이블의 이름을 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-132">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c410a-133">**레이블 설정** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="c410a-134">**설정 검토** 창에서 **이 레이블 만들기**를 클릭 하 고 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-134">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="c410a-135">레이블을 추가하려면 5-8단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="c410a-136">PowerShell을 사용한 Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="c410a-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="c410a-137">[Office 365 보안 연결 &amp; 원격 PowerShell을 사용 하 여 준수 센터](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) 하 고 보안 관리자 또는 회사 관리자 역할이 있는 계정의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-137">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="c410a-138">레이블 이름 목록을 작성한 다음 PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="c410a-139">그리고 나서 다음 단계를 사용하여 새 Office 365 레이블을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="c410a-140">**홈 > 레이블** 창 보안 &amp; 준수 센터 **게시 레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-140">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="c410a-141">**게시할 레이블 선택** 창에서 **게시할 레이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="c410a-142">**레이블 선택** 창에서 **추가**를 클릭하고 네 개의 레이블을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="c410a-143">**완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="c410a-144">**게시할 레이블 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="c410a-145">**위치 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="c410a-146">**이름 정책에 따라** 창에서 **이름**레이블 사용자 집합에 대 한 이름을 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c410a-147">**설정 검토** 창에서 **게시 레이블**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-147">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="c410a-148">3단계: SharePoint Online 사이트에 Office 365 레이블 적용</span><span class="sxs-lookup"><span data-stu-id="c410a-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="c410a-149">다음 단계에 따라 Office 365 레이블을 SharePoint Online 팀 사이트의 문서 폴더에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="c410a-150">브라우저의 **Microsoft Office 홈** 탭에서 **SharePoint** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="c410a-151">브라우저의 새 **SharePoint** 탭에서 할당된 Office 365 레이블이 필요한 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="c410a-152">브라우저의 새 SharePoint 사이트 탭에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="c410a-153">설정 아이콘을 클릭한 다음 **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="c410a-154">**권한 및 관리** 아래에서 **Apply label to items in this library(이 라이브러리의 항목에 레이블 적용)**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="c410a-155">**레이블 설정 적용**을 적절 한 레이블을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-155">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="c410a-156">SharePoint Online 사이트의 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="c410a-157">3-8단계를 반복하여 추가 SharePoint Online 사이트에 Office 365 레이블을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="c410a-158">결과적으로 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-158">Here is your resulting configuration.</span></span>
  
![SharePoint Online 팀 사이트의 네 가지 유형에 대한 Office 365 레이블입니다.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="c410a-160">SharePoint Online 사이트에 대한 DLP 정책</span><span class="sxs-lookup"><span data-stu-id="c410a-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="c410a-161">다음 단계를 사용하여 사용자가 조직 외부의 중요 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자에게 알려주는 DLP 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="c410a-162">브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-162">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="c410a-163">새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-163">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="c410a-164">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="c410a-165">**서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="c410a-166">**이름에 정책** 창에서 **이름**중요 한 수준 DLP 정책에 대 한 이름을 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-166">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c410a-167">**위치 선택** 창에서 **Let me choose specific locations(특정 위치 직접 선택)**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c410a-168">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c410a-169">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="c410a-170">**보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="c410a-171">**레이블** 창에서 **+ 기호 추가**클릭, **중요 한** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="c410a-172">**Choose the types of content to protect(보호할 콘텐츠 형식 선택)** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="c410a-173">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="c410a-174">**중요한 정보를 발견하면**  창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="c410a-175">**Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="c410a-176">텍스트 상자에 다음을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c410a-p104">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="c410a-180">또는 입력 하거나 조직 외부에 파일을 공유 하는 방법에 대 한 사용자가 지시 하는 정책 팁에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-180">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="c410a-181">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="c410a-182">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창에서 **공유, 다른 사람을 차단 하 고 공유 내용에 대 한 액세스를 제한** 확인란의 선택을 취소 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="c410a-183">**먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="c410a-184">**설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-184">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="c410a-185">결과적으로 중요 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![중요한 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="c410a-187">그리고 나서 다음 단계를 사용하여 사용자가 조직 외부의 극비 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자를 차단하는 DLP 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="c410a-188">브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-188">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="c410a-189">새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-189">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="c410a-190">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="c410a-191">**서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="c410a-192">**이름에 정책** 창에서 **이름**매우 중요 한 수준 DLP 정책에 대 한 이름을 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c410a-193">**위치 선택** 창에서 **Let me choose specific locations(특정 위치 직접 선택)**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c410a-194">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c410a-195">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="c410a-196">**보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="c410a-197">**레이블** 창에서 **+ 기호 추가**클릭, **기밀 사항이** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="c410a-198">**Choose the types of content to protect(보호할 콘텐츠 형식 선택)** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="c410a-199">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="c410a-200">**중요한 정보를 발견하면**  창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="c410a-201">**Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="c410a-202">텍스트 상자에 다음을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c410a-p105">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="c410a-206">또는 입력 하거나 조직 외부에 파일을 공유 하는 방법에 대 한 사용자가 지시 하는 정책 팁에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-206">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="c410a-207">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="c410a-208">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **, 업무 효율성을 재정의 하려면 필요**를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="c410a-209">**먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="c410a-210">**설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-210">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="c410a-211">결과적으로 극비 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c410a-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![높은 수준의 기밀 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="c410a-213">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c410a-213">Next step</span></span>

[<span data-ttu-id="c410a-214">Azure Information Protection을 사용한 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="c410a-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="c410a-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c410a-215">See Also</span></span>

[<span data-ttu-id="c410a-216">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="c410a-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="c410a-217">개발/테스트 환경의 SharePoint Online 사이트 보호</span><span class="sxs-lookup"><span data-stu-id="c410a-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="c410a-218">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="c410a-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="c410a-219">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="c410a-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


