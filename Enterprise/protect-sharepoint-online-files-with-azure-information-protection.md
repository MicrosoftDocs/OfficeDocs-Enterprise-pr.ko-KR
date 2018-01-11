---
title: "Azure 정보 보호와 SharePoint Online 파일 보호"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "요약: Azure 정보 보호 기밀 사항이 SharePoint Online 팀 사이트의 파일을 보호 하기 위해 적용 됩니다."
ms.openlocfilehash: 03a10c5d856c4c5518f18b9d02ffe76f2c8d2e7a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="e3ff7-103">Azure 정보 보호와 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="e3ff7-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="e3ff7-104">**요약:** 기밀 사항이 SharePoint Online 팀 사이트의 파일을 보호 하기 위해 Azure 정보 보호 기능을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="e3ff7-p101">이 문서의 단계를 사용 하 여 암호화 및 기밀 사항이 SharePoint Online 팀 사이트의 파일에 대 한 사용 권한을 제공 하는 Azure 정보 보호 기능을 구성 합니다. 암호화 및 사용 권한 보호의 사이트에서 다운로드 하는 경우에 파일을 함께 이동 합니다. 기밀 사항이 SharePoint Online 팀 사이트에 대 한 자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](secure-sharepoint-online-sites-and-files.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e3ff7-p102">Azure 정보 보호 암호화는 Office 365에 저장 된 파일에 적용 되 면 서비스에는 이러한 파일의 내용을 처리할 수 없습니다. 공동 작성, eDiscovery, 검색, Delve, 및 기타 공동 작업 기능이 작동 하지 않습니다. 데이터 손실 방지 (DLP) 정책 (Office 365 레이블을 포함) 메타 데이터 있지만 (예: 파일 내에서 신용 카드 번호) 이러한 파일의 내용이 아니라만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="e3ff7-111">먼저, Office 365 구독에 대 한 [Office 365 관리 센터와 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 의 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="e3ff7-112">다음으로 새 범위가 지정 된 정책 및 보호 및 기밀 사항이 SharePoint Online 팀 사이트의 사용 권한을 하위 레이블을 사용 하 여 Azure 정보 보호를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="e3ff7-p103">보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e3ff7-115">브라우저의 별도 탭에서 Azure 포털 ([https://portal.azure.com](https://portal.azure.com))로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-115">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="e3ff7-116">처음으로 Azure 정보 보호를 구성 하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="e3ff7-117">목록 창에서 **서비스를 더**, **정보**를 입력 한 다음 **Azure 정보 보호**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="e3ff7-118">**Azure 정보 보호** 블레이드에서를 클릭 **정책 범위 > 새 정책을 추가 +**합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="e3ff7-119">새 정책에 대 한 이름을 **정책 이름** 및 **설명**에 대 한 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="e3ff7-120">클릭 **있는 사용자 또는 그룹에이 정책을 가져오려면 선택 > 사용자/그룹**, 다음 선택 사이트 구성원은 매우 중요 한 SharePoint Online 팀 사이트에 대 한 그룹에 액세스 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="e3ff7-121">클릭 **선택 > 확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="e3ff7-122">**기밀 사항이** 레이블에 대 한 줄임표 (...)를 클릭 하 고 **하위 레이블 추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="e3ff7-123">**이름** 및 **설명**의 레이블 내에 대 한 설명을 하위 레이블에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="e3ff7-124">**문서 및이 레이블이 포함 된 전자 메일에 대 한 사용 권한 설정**에서 **암호로 보호**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="e3ff7-125">**보호** 섹션에서 **Azure (클라우드 키)를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="e3ff7-126">**보호** 블레이드 **보호 설정**아래에서 **+ 추가 사용 권한을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="e3ff7-127">**추가 사용 권한** 블레이드 **지정 사용자 및 그룹을**에서 **디렉터리 찾아보기 +**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="e3ff7-128">**AAD 사용자 및 그룹** 창에서 매우 중요 한 SharePoint Online 팀 사이트에 대 한 사이트 구성원 액세스 그룹을 선택 하 고 **선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="e3ff7-129">**사전 설정에서 사용 권한을 선택**아래에서 **인쇄**, **복사 및 콘텐츠 추출**및 **앞으로** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="e3ff7-130">두 번 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="e3ff7-131">**하위 레이블** 블레이드에서 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="e3ff7-132">새 범위가 지정 된 정책 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="e3ff7-133">**Azure 정보 보호-범위가 지정 된 정책** 블레이드에서 **게시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="e3ff7-134">기밀 사항이 SharePoint Online 팀 사이트에 대 한 결과 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![격리된 SharePoint Online 팀 사이트에 대한 Azure Information Protection 레이블입니다.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="e3ff7-136">이제 시작할 준비가 문서 만들기 (영문) 및 Azure 정보 보호 및 새 레이블을 사용 하 여이 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="e3ff7-p104">장치 또는 Windows 기반 컴퓨터에서 [Azure 정보 보호 클라이언트 설치](https://docs.microsoft.com/information-protection/rms-client/install-client-app) 를 수행 해야 합니다. 스크립트 하 고, 설치를 자동화 또는 사용자가 클라이언트를 수동으로 설치할 수 있습니다. 다음 리소스를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="e3ff7-140">Azure 정보 보호의 클라이언트쪽</span><span class="sxs-lookup"><span data-stu-id="e3ff7-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="e3ff7-141">Azure 정보 보호 클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="e3ff7-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="e3ff7-142">수동 설치에 대 한 페이지를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="e3ff7-p105">설치 되 면 사용자에 게를 실행 하 고 로그인 자신의 Office 365 계정 (예: Microsoft Word) Office 응용 프로그램에서 합니다. 새 **정보 보호** 모음을 사용자가 새 레이블을 선택할 수 있습니다. SharePoint Online 팀 사이트와 그 기밀 파일을 보호 하기 위해 사용 하 여 레이블을 지정 하는 프로그램 사용자에 게 있는지 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e3ff7-146">각 하위 레이블의 사이트 구성원 액세스 그룹 설정에 대 한 사용 권한 가진 위의 설정을 사용 하 여 여러 범위 Azure 정보 보호 정책의 만들어 하위 레이블이 있는 해야 여러 매우 중요 한 SharePoint Online 팀 사이트를 사용 하는 경우는 특정 SharePoint Online 팀 사이트입니다.</span><span class="sxs-lookup"><span data-stu-id="e3ff7-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="e3ff7-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3ff7-147">See Also</span></span>

[<span data-ttu-id="e3ff7-148">SharePoint Online 사이트 및 파일의 보안</span><span class="sxs-lookup"><span data-stu-id="e3ff7-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="e3ff7-149">개발/테스트 환경에서 SharePoint Online 사이트 보호</span><span class="sxs-lookup"><span data-stu-id="e3ff7-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="e3ff7-150">정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="e3ff7-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="e3ff7-151">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="e3ff7-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




