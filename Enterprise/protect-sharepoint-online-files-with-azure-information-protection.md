---
title: Azure Information Protection을 사용한 SharePoint Online 파일 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/08/2018
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
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: '요약: Azure Information Protection을 적용하여 극비 SharePoint Online 팀 사이트의 파일을 보호합니다.'
ms.openlocfilehash: 4ea6c1da8b39f22a56ba4f4d555518b671f07b70
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915313"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="adf1c-103">Azure Information Protection을 사용한 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="adf1c-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="adf1c-104">**요약:** Azure Information Protection을 적용하여 극비 SharePoint Online 팀 사이트의 파일을 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="adf1c-p101">이 문서의 단계를 사용하여 파일에 대해 암호화 및 사용 권한을 제공하도록 Azure Information Protection을 구성합니다. 이러한 파일은 극비 보호용으로 구성된 SharePoint 라이브러리에 추가되거나, 사이트에서 직접 파일을 열고 Azure Information Protection 클라이언트를 사용하여 암호화를 추가할 수 있습니다. 암호화 및 사용 권한 보호 기능은 사이트에서 다운로드된 파일에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="adf1c-p102">다음 단계는 이러한 사이트 내에서 SharePoint 사이트 및 파일에 대해 극비 보호를 구성하기 위한 보다 큰 솔루션의 일부입니다. 자세한 내용은 [SharePoint Online 사이트 및 파일 보호](secure-sharepoint-online-sites-and-files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="adf1c-111">SharePoint Online의 파일에 대해 Azure Information Protection을 사용하는 것이 모든 고객에게 권장되는 것은 아니지만 일부 파일에 대해 이러한 수준의 보호가 필요한 고객에게는 적절할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="adf1c-112">이 솔루션에 대한 몇 가지 중요 참고 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="adf1c-p103">Office 365에 저장된 파일에 Azure Information Protection 암호화가 적용되어 있으면 이 파일의 내용을 처리할 수 없습니다. 즉 공동 작성, eDiscovery, 검색, Delve 및 기타 공동 작업 기능이 작동하지 않습니다. DLP(데이터 손실 방지) 정책은 메타데이터(Office 365 레이블 포함)에만 작동할 수 있지만 파일의 내용(예: 파일 내의 신용 카드 번호)에는 작동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="adf1c-p104">이 솔루션을 사용하려면 Azure Information Protection의 보호를 적용하는 레이블을 선택해야 합니다. 파일을 인덱싱하고 조사하기 위해 SharePoint 기능 및 자동 암호화가 필요한 경우 SharePoint Online의 IRM(정보 권한 관리)을 사용하는 것이 좋습니다. IRM에 대해 SharePoint 라이브러리를 구성하면 편집을 위해 파일을 다운로드할 때 파일이 자동으로 암호화됩니다. SharePoint IRM에는 의사 결정에 영향을 줄 수 있는 제한 사항이 포함되어 있습니다. 자세한 내용은 [SharePoint 관리 센터에서 의 IRM(정보 권한 관리) 설정](https://support.office.com/ko-KR/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/ko-KR/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="adf1c-121">관리자 설정</span><span class="sxs-lookup"><span data-stu-id="adf1c-121">Admin setup</span></span>
<span data-ttu-id="adf1c-122">먼저 [Office 365 구독을 위해 Office 365 관리 센터에서 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)의 지침을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="adf1c-123">그런 다음, 극비 SharePoint Online 팀 사이트에 대한 보호 및 권한을 위한 새로운 범위 지정 정책 및 하위 레이블로 Azure Information Protection을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="adf1c-p105">보안 관리자 또는 회사 관리자 역할이 있는 계정으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="adf1c-126">브라우저의 별도 탭에서 Azure Portal([https://portal.azure.com](https://portal.azure.com))로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="adf1c-127">처음으로 Azure Information Protection을 구성하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adf1c-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>

4. <span data-ttu-id="adf1c-128">목록 창에서 **모든 서비스**를 클릭하고 **정보**를 입력한 다음, **Azure Information Protection**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>

5. <span data-ttu-id="adf1c-129">**레이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-129">Click **Labels**.</span></span>
    
6. <span data-ttu-id="adf1c-130">**기밀** 레이블을 마우스 오른쪽 단추로 클릭하고 **하위 레이블 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-130">Right-click the **Highly Confidential** label, and then click **Add a sub-label**.</span></span>
    
7. <span data-ttu-id="adf1c-131">**이름**에 하위 레이블의 이름을 입력하고 **설명**에 레이블에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-131">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
8. <span data-ttu-id="adf1c-132">**이 레이블을 포함하는 문서 및 전자 메일에 대한 권한 설정**에서 **보호**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-132">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
9. <span data-ttu-id="adf1c-133">**보호** 섹션에서 **Azure(클라우드 키)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-133">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
10. <span data-ttu-id="adf1c-134">**보호** 블레이드의 **보호 설정** 아래에서 **권한 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-134">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
11. <span data-ttu-id="adf1c-135">**권한 추가** 블레이드의 **사용자 및 그룹 지정** 아래에서 **디렉터리 찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-135">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
12. <span data-ttu-id="adf1c-136">**AAD 사용자 및 그룹** 창에서 극비 SharePoint Online 팀 사이트에 대한 사이트 멤버 액세스 그룹을 선택하고 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-136">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
13. <span data-ttu-id="adf1c-137">**미리 설정된 또는 설정된 사용자 지정에서 권한 선택**에서 **사용자 지정**을 클릭한 다음 **권한 보기**, **콘텐츠 편집**, **저장**, **회신** 및 **모두 회신** 확인란을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-137">Under **Choose permissions from the preset or set custom**, click **Custom**, and then click the **View Rights**, **Edit Content**, **Save**, **Reply**, and **Reply all** check boxes.</span></span>
    
14. <span data-ttu-id="adf1c-138">**확인**를 두 번 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-138">Click **OK** twice.</span></span>
    
15. <span data-ttu-id="adf1c-139">**하위 레이블** 블레이드에서 **저장**을 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-139">On the **Sub-label** blade, click **Save**, and then click **OK**.</span></span>

16. <span data-ttu-id="adf1c-140">**Azure Information Protection** 블레이드에서 **정책 > + 새 정책 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-140">On the **Azure Information protection** blade, click **Policies > + Add a new policy**.</span></span>
    
17. <span data-ttu-id="adf1c-141">**정책 이름**에 새 정책의 이름을 입력하고 **설명**에 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-141">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
18. <span data-ttu-id="adf1c-142">**이 정책을 가져올 사용자 또는 그룹을 선택합니다 > 사용자/그룹**을 클릭한 후 극비 SharePoint Online 팀 사이트에 대한 사이트 멤버 액세스 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-142">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span>
    
19. <span data-ttu-id="adf1c-143">**선택 > 확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-143">Click **Select > OK**.</span></span>

20. <span data-ttu-id="adf1c-p106">**레이블 추가 또는 제거**를 클릭합니다. **정책: 레이블 추가 또는 제거** 창에서 새 하위 레이블의 이름을 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p106">Click Add or remove labels. In the Policy: Add or remove labels pane, click CampaignStrategy, and then click OK.</span></span>   

21. <span data-ttu-id="adf1c-146">**저장**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-146">Click **Save**, and then click **OK**.</span></span>
 
##<a name="client-setup"></a><span data-ttu-id="adf1c-147">클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="adf1c-147">Client setup</span></span>
<span data-ttu-id="adf1c-148">이제 문서를 작성하고 Azure Information Protection 및 새로운 레이블을 사용하여 해당 문서를 보호할 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-148">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="adf1c-p107">사용자의 장치 또는 Windows 기반 컴퓨터 [Azure Information Protection 클라이언트](https://docs.microsoft.com/information-protection/rms-client/install-client-app)를 설치해야 합니다. 스크립트를 작성하여 설치를 자동화하거나 사용자가 클라이언트를 수동으로 설치할 수 있습니다. 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p107">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="adf1c-152">Azure Information Protection의 클라이언트 측면</span><span class="sxs-lookup"><span data-stu-id="adf1c-152">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="adf1c-153">Azure Information Protection 클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="adf1c-153">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="adf1c-154">수동 설치를 위한 다운로드 페이지</span><span class="sxs-lookup"><span data-stu-id="adf1c-154">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="adf1c-p108">설치된 후 사용자가 Office 365 계정을 가진 Office 응용 프로그램(Microsoft Word )에서 실행한 다음 로그인할 수 있습니다. 새 **Information Protection** 표시줄에서 새 레이블이 선택할 수 있습니다. 극비 파일을 보호하려면 SharePoint Online 팀 사이트와 사용할 레이블을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p108">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="adf1c-158">극비 SharePoint Online 팀 사이트가 여러 개인 경우, 각 하위 레이블에 대한 권한을 특정 SharePoint Online 팀 사이트의 사이트 멤버 액세스 그룹으로 설정하고 위의 설정을 사용하여 하위 레이블이 포함된 Azure Information Protection 범위 지정 정책 여러 개를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-158">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="adf1c-159">외부 사용자에 대한 권한 추가</span><span class="sxs-lookup"><span data-stu-id="adf1c-159">Adding permissions for external users</span></span>
<span data-ttu-id="adf1c-p109">Azure Information Protection으로 보호된 파일에 대한 액세스 권한을 외부 사용자에게 부여할 수 있는 두 가지 방법이 있습니다. 이 두 가지 방법에서는 모두 Azure AD 계정이 외부 사용자에게 있어야 합니다. 외부 사용자가 Azure AD를 사용하는 조직의 구성원이 아닌 경우 [https://aka.ms/aip-signup](https://aka.ms/aip-signup) 등록 페이지를 사용하여 Azure AD 계정을 개별로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p109">There are two ways you can grant external users access to files protected with Azure Information Protection. In both cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this signup page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="adf1c-p110">레이블 보호를 구성하는 데 사용되는 외부 사용자를 Azure AD 그룹에 추가합니다. 먼저 계정을 디렉터리에 B2B 사용자로 추가해야 합니다. [Azure Rights Management의 그룹 구성원 캐싱](https://docs.microsoft.com/ko-KR/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection) 작업에는 몇 시간 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p110">Add external users to an Azure AD group that is used to configure protection for a label. You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group memership caching by Azure Rights Management](https://docs.microsoft.com/ko-KR/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection).</span></span>  
 - <span data-ttu-id="adf1c-p111">레이블 보호에 외부 사용자를 직접 추가합니다. 조직(예: Fabrikam.com), Azure AD 그룹(조직 내의 재무 그룹) 또는 사용자의 모든 사용자를 추가할 수 있습니다. 예를 들어 조절기의 외부 팀을 레이블 보호에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adf1c-p111">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or user. For example, you can add an external team of regulators to the protection for a label.</span></span>

## <a name="see-also"></a><span data-ttu-id="adf1c-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="adf1c-169">See Also</span></span>

[<span data-ttu-id="adf1c-170">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="adf1c-170">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="adf1c-171">개발/테스트 환경의 보안 SharePoint Online 사이트</span><span class="sxs-lookup"><span data-stu-id="adf1c-171">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="adf1c-172">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="adf1c-172">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="adf1c-173">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="adf1c-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




