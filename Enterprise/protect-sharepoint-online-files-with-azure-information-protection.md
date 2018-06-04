---
title: Azure Information Protection을 사용한 SharePoint Online 파일 보호
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
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: '요약: Azure Information Protection을 적용하여 극비 SharePoint Online 팀 사이트의 파일을 보호합니다.'
ms.openlocfilehash: bab799a784cac579c92fb06ea17592d85fd59af2
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "19168502"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="83aa3-103">Azure Information Protection을 사용한 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="83aa3-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="83aa3-104">**요약:** Azure Information Protection을 적용하여 극비 SharePoint Online 팀 사이트의 파일을 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="83aa3-p101">이 문서의 단계를 사용하여 극비 SharePoint Online 팀 사이트에서 파일에 대해 암호화 및 사용 권한을 제공하도록 Azure Information Protection을 구성합니다. 암호화 및 사용 권한 보호 기능은 사이트에서 다운로드된 파일에 적용됩니다. 극비 SharePoint Online 팀 사이트에 대한 자세한 내용은 [보안 SharePoint Online 사이트 및 파일](secure-sharepoint-online-sites-and-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83aa3-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="83aa3-p102">Office 365에 저장된 파일에 Azure Information Protection 암호화가 적용되어 있으면 이 파일의 내용을 처리할 수 없습니다. 즉 공동 작성, eDiscovery, 검색, Delve 및 기타 공동 작업 기능이 작동하지 않습니다. DLP(데이터 손실 방지) 정책은 메타데이터(Office 365 레이블 포함)에만 작동할 수 있지만 파일의 내용(예: 파일 내의 신용 카드 번호)에는 작동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="83aa3-111">먼저 [Office 365 구독을 위해 Office 365 관리 센터에서 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)의 지침을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-111">First, follow the instructions in [Activate Azure RMS with the Office 365 admin center for your Office 365 subscription](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="83aa3-112">그런 다음, 극비 SharePoint Online 팀 사이트에 대한 보호 및 권한을 위한 새로운 범위 지정 정책 및 하위 레이블로 Azure Information Protection을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions for your highly confidential SharePoint Online team site by following these steps:</span></span>
  
1. <span data-ttu-id="83aa3-p103">보안 관리자 또는 회사 관리자 역할이 있는 계정으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83aa3-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="83aa3-115">브라우저의 별도 탭에서 Azure Portal([https://portal.azure.com](https://portal.azure.com))로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-115">In a separate tab of your browser, go to the Azure portal (https://portal.azure.com).</span></span>
    
3. <span data-ttu-id="83aa3-116">처음으로 Azure Information Protection을 구성하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83aa3-116">If this is the first time you are configuring Azure Information Protection, see [these instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="83aa3-117">목록 창에서 **모든 서비스**를 클릭하고 **정보**를 입력한 다음, **Azure Information Protection**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-117">In the list pane, click **More services**, type **information**, and click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="83aa3-118">**Azure Information Protection** 블레이드에서 **범위 지정 정책 > + 새 정책 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-118">On the **Azure Information protection** blade, click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="83aa3-119">**정책 이름**에 새 정책의 이름을 입력하고 **설명**에 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="83aa3-120">**이 정책을 가져올 사용자 또는 그룹을 선택합니다 > 사용자/그룹**을 클릭한 후 극비 SharePoint Online 팀 사이트에 대한 사이트 멤버 액세스 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="83aa3-121">**선택 > 확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="83aa3-122">**기밀** 레이블에서 생략 부호(…)를 클릭한 후 **하위 레이블 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="83aa3-123">**이름**에 하위 레이블의 이름을 입력하고 **설명**에 하위 레이블에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="83aa3-124">**이 레이블을 포함하는 문서 및 전자 메일에 대한 권한 설정**에서 **보호**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="83aa3-125">**보호** 섹션에서 **Azure(클라우드 키)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="83aa3-126">**보호** 블레이드의 **보호 설정** 아래에서 **+ 권한 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="83aa3-127">**권한 추가** 블레이드의 **사용자 및 그룹 지정** 아래에서 **+ 디렉터리 찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="83aa3-128">**AAD 사용자 및 그룹** 창에서 극비 SharePoint Online 팀 사이트에 대한 사이트 멤버 액세스 그룹을 선택하고 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and click **Select**.</span></span>
    
16. <span data-ttu-id="83aa3-129">**미리 설정에서 권한 선택** 아래에서 **콘텐츠 인쇄**, **복사 및 추출** 및 **전달** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-129">Under Choose permissions from the preset, clear the Print, Copy and extract content, and Forward check boxes.</span></span>
    
17. <span data-ttu-id="83aa3-130">**확인**를 두 번 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="83aa3-131">**하위 레이블** 블레이드에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="83aa3-132">새로운 범위 지정 정책 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="83aa3-133">**Azure Information Protection – 범위 지정 정책** 블레이드에서 **게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-133">On the **Azure Information Protection – Scoped policies** blade, click **Publish**, and then click Yes.</span></span>
    
<span data-ttu-id="83aa3-134">결과적으로 극비 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-134">This is the resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![격리된 SharePoint Online 팀 사이트에 대한 Azure Information Protection 레이블입니다.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="83aa3-136">이제 문서를 작성하고 Azure Information Protection 및 새로운 레이블을 사용하여 해당 문서를 보호할 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="83aa3-p104">사용자의 장치 또는 Windows 기반 컴퓨터 [Azure Information Protection 클라이언트](https://docs.microsoft.com/information-protection/rms-client/install-client-app)를 설치해야 합니다. 스크립트를 작성하여 설치를 자동화하거나 사용자가 클라이언트를 수동으로 설치할 수 있습니다. 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83aa3-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually.</span></span>
  
- [<span data-ttu-id="83aa3-140">Azure Information Protection의 클라이언트 측면</span><span class="sxs-lookup"><span data-stu-id="83aa3-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="83aa3-141">Azure Information Protection 클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="83aa3-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="83aa3-142">수동 설치를 위한 다운로드 페이지</span><span class="sxs-lookup"><span data-stu-id="83aa3-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="83aa3-p105">설치된 후 사용자가 Office 365 계정을 가진 Office 응용 프로그램(Microsoft Word )에서 실행한 다음 로그인할 수 있습니다. 새 **Information Protection** 표시줄에서 새 레이블이 선택할 수 있습니다. 극비 파일을 보호하려면 SharePoint Online 팀 사이트와 사용할 레이블을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="83aa3-146">극비 SharePoint Online 팀 사이트가 여러 개인 경우, 각 하위 레이블에 대한 권한을 특정 SharePoint Online 팀 사이트의 사이트 멤버 액세스 그룹으로 설정하고 위의 설정을 사용하여 하위 레이블이 포함된 Azure Information Protection 범위 지정 정책 여러 개를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83aa3-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="83aa3-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83aa3-147">See Also</span></span>

[<span data-ttu-id="83aa3-148">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="83aa3-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="83aa3-149">개발/테스트 환경의 보안 SharePoint Online 사이트</span><span class="sxs-lookup"><span data-stu-id="83aa3-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="83aa3-150">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="83aa3-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="83aa3-151">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="83aa3-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




