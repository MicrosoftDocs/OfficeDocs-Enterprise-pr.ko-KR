---
title: "SharePoint Online 팀 사이트를 격리를 배포 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "요약: 새 격리 된 SharePoint Online 팀 사이트가 단계별 지침을 배포 합니다."
ms.openlocfilehash: 31a1f588aefccd9e2cb353af86d8aa0d598696af
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="86548-103">SharePoint Online 팀 사이트를 격리를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-103">Deploy an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="86548-104">**요약:** 새 격리 된 SharePoint Online 팀 사이트가 단계별 지침을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-104">**Summary:** Deploy a new isolated SharePoint Online team site with these step-by-step instructions.</span></span>
  
<span data-ttu-id="86548-p101">이 문서 만들기 (영문) 및 Microsoft Office 365에서 격리 된 SharePoint Online 팀 사이트를 구성 하기 위한 단계별 배포 가이드는. 이러한 단계 세 기본 SharePoint 그룹 및 각 액세스 수준에 대 한 단일 Azure Active Directory 기반 액세스 그룹과 해당 사용 권한 수준을 사용 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-p101">This article is a step-by-step deployment guide for creating and configuring an isolated SharePoint Online team site in Microsoft Office 365. These steps assume the use of the three default SharePoint groups and corresponding permission levels, with a single Azure Active Directory (AD)-based access group for each level of access.</span></span>
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a><span data-ttu-id="86548-107">1 단계: 만들기 및 팀 사이트 액세스 그룹 채우기</span><span class="sxs-lookup"><span data-stu-id="86548-107">Phase 1: Create and populate the team site access groups</span></span>

<span data-ttu-id="86548-108">이 단계에서 세개의 기본 SharePoint 그룹에 대 한 세 Azure AD 기반 액세스 그룹 만들고 적절 한 사용자 계정으로 채울 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-108">In this phase, you create the three Azure AD-based access groups for the three default SharePoint groups and populate them with the appropriate user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="86548-p102">다음 단계는 모든 필요한 사용자 계정이 이미 존재 하 고 적절 한 라이선스를 할당 된 가정 합니다. 그렇지 않은 경우 추가 하 고 1 단계를 진행 하기 전에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-p102">The following steps assume that all necessary user accounts already exist and are assigned the appropriate licenses. If not, please add them and assign licenses before proceeding to step 1.</span></span> 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a><span data-ttu-id="86548-111">1 단계: 사이트에 대 한 SharePoint Online 관리자를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-111">Step 1: List the SharePoint Online admins for the site</span></span>

<span data-ttu-id="86548-112">사용자 집합에 해당 하는 격리 된 팀 사이트에 대 한 SharePoint Online 관리자 계정을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-112">Determine the set of user accounts corresponding to the SharePoint Online admins for the isolated team site.</span></span>
  
<span data-ttu-id="86548-113">사용자 계정 및 그룹을 통해 Office 365를 관리 하는 Windows PowerShell을 사용 하려고 하는 경우 해당 사용자의 목록을 Upn (이름)를 만듭니다 (UPN 예제: belindan@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="86548-113">If you are managing user accounts and groups through Office 365 and want to use Windows PowerShell, make a list of their user principal names (UPNs) (example UPN: belindan@contoso.com).</span></span>
  
### <a name="step-2-list-the-members-for-the-site"></a><span data-ttu-id="86548-114">2 단계: 사이트에 대 한 멤버를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-114">Step 2: List the members for the site</span></span>

<span data-ttu-id="86548-115">사용자 계정에 해당 하는 공동 작업 사이트 내에 저장 된 리소스에 받는 사람이 격리 된 팀 사이트에 대 한 구성원의 집합을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-115">Determine the set of user accounts corresponding to the members for the isolated team site, those who will be collaborating on resources stored within the site.</span></span>
  
<span data-ttu-id="86548-p103">사용자 계정 및 그룹을 통해 Office 365를 관리 하는 PowerShell을 사용 하 여 원하는 하는 경우에 해당 Upn 목록이 확인 합니다. 사이트 구성원의 많은 경우 텍스트 파일에 Upn 목록이 저장 하 고 단일 PowerShell 명령을 사용 하 여 모든 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-p103">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
### <a name="step-3-list-the-viewers-for-the-site"></a><span data-ttu-id="86548-118">3 단계: 사이트에 대 한 뷰어를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-118">Step 3: List the viewers for the site</span></span>

<span data-ttu-id="86548-119">받는 사람이 수 없는 사이트에 저장 된 리소스를 보려면 하지만 하지 수정 하거나의 내용에 직접 공동 작업 격리 된 팀 사이트의 사용자에 게 해당 사용자 계정의 집합을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-119">Determine the set of user accounts corresponding to the viewers of the isolated team site, those who can view the resources stored in the site but not modify them or directly collaborate on their contents.</span></span>
  
<span data-ttu-id="86548-p104">사용자 계정 및 그룹을 통해 Office 365를 관리 하는 PowerShell을 사용 하 여 원하는 하는 경우에 해당 Upn 목록이 확인 합니다. 사이트 구성원의 많은 경우 텍스트 파일에 Upn 목록이 저장 하 고 단일 PowerShell 명령을 사용 하 여 모든 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-p104">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
<span data-ttu-id="86548-122">사이트에 대 한 뷰어 경영진, 법적 자문 위원 또는 inter-departmental 이해 관계자 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-122">Viewers for the site might include executive management, legal counsel, or inter-departmental stakeholders.</span></span>
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a><span data-ttu-id="86548-123">4 단계: Azure AD에서 해당 사이트에 대 한 세 액세스 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="86548-123">Step 4: Create the three access groups for the site in Azure AD</span></span>

<span data-ttu-id="86548-124">Azure AD에서 다음과 같은 액세스 그룹을 만들 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-124">You need to create the following access groups in Azure AD:</span></span>
  
- <span data-ttu-id="86548-125">(1 단계에서 목록 포함)이 표시 된 사이트 관리자</span><span class="sxs-lookup"><span data-stu-id="86548-125">Site admins (which will contain the list from step 1)</span></span>
    
- <span data-ttu-id="86548-126">(2 단계에서 목록 포함)이 표시 된 사이트 구성원</span><span class="sxs-lookup"><span data-stu-id="86548-126">Site members (which will contain the list from step 2)</span></span>
    
- <span data-ttu-id="86548-127">(3 단계에서 목록 포함)이 표시 된 사이트 뷰어</span><span class="sxs-lookup"><span data-stu-id="86548-127">Site viewers (which will contain the list from step 3)</span></span>
    
1. <span data-ttu-id="86548-128">브라우저에서 [https://portal.azure.com](https://portal.azure.com) 에서 Azure 포털로 이동 하 고 사용자 관리 관리자 또는 회사 관리자 역할을 가진 할당 된 계정의 자격 증명을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-128">In your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com) and sign in with the credentials of an account that has been assigned with User Management Admin or Company Administrator role.</span></span>
    
2. <span data-ttu-id="86548-129">Azure 포털에서 클릭 **Azure Active Directory > 사용자 및 그룹 > 모든 그룹**합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-129">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="86548-130">**모든 그룹** 블레이드에서 **+ 새 그룹을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-130">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="86548-131">**그룹** 블레이드에서:</span><span class="sxs-lookup"><span data-stu-id="86548-131">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="86548-132">**이름**에 그룹 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-132">Type the group name in **Name**.</span></span>
    
  - <span data-ttu-id="86548-133">**멤버 자격**에서 **할당** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-133">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="86548-134">**Office를 사용 하도록 설정 기능**에 대 한 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-134">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="86548-135">**만들기**클릭 한 다음 **그룹** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-135">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="86548-136">추가 그룹에 대해 3-5 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-136">Repeat steps 3-5 for your additional groups.</span></span>
    
> [!NOTE]
> <span data-ttu-id="86548-p105">사용 하도록 설정 하는 Office 기능을가지고 있습니다. 그룹을 만들 수는 Azure 포털을 사용 해야 합니다. SharePoint Online 격리 된 사이트는 나중에 사용 하도록 구성 파일을 암호화 하 고 특정 그룹에 권한 할당을 Azure 정보 보호 (AIP) 레이블이 있는 기밀 사항이 사이트로 허용 된 그룹 만들어져 있어야 Office 기능 사용할 수 있습니다. 가 만들어진 후 Azure AD 그룹의 Office 기능 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-p105">You need to use the Azure portal to create the groups so that they have Office features enabled. If a SharePoint Online isolated site is later configured as a Highly Confidential site with an Azure Information Protection (AIP) label to encrypt files and assign permission to specific groups, the permitted groups must have been created with Office features enabled. You cannot change the Office features setting of an Azure AD group after it has been created.</span></span> 
  
<span data-ttu-id="86548-140">세 개 사이트 액세스 그룹과 결과 구성에는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-140">Here is your resulting configuration with the three site access groups.</span></span>
  
![격리된 SharePoint Online 사이트 배포용 세 개의 액세스 그룹입니다.](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a><span data-ttu-id="86548-p106">5 단계입니다. Access 그룹에 사용자 계정 추가</span><span class="sxs-lookup"><span data-stu-id="86548-p106">Step 5. Add the user accounts to the access groups</span></span>

<span data-ttu-id="86548-144">이 단계에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-144">In this step, do the following:</span></span>
  
1. <span data-ttu-id="86548-145">사이트 관리자 액세스 그룹을 1 단계에서 사용자의 목록 추가</span><span class="sxs-lookup"><span data-stu-id="86548-145">Add the list of users from step 1 to the site admins access group</span></span>
    
2. <span data-ttu-id="86548-146">사이트 구성원 액세스 그룹에 2 단계에서 사용자의 목록 추가</span><span class="sxs-lookup"><span data-stu-id="86548-146">Add the list of users from step 2 to the site members access group</span></span>
    
3. <span data-ttu-id="86548-147">사이트 뷰어 액세스 그룹에 3 단계에서 사용자의 목록 추가</span><span class="sxs-lookup"><span data-stu-id="86548-147">Add the list of users from step 3 to the site viewers access group</span></span>
    
<span data-ttu-id="86548-148">사용자 계정 및 Windows Server AD 통해 그룹을 관리 하는 경우 일반 Windows Server AD 사용자 및 그룹 관리 절차를 사용 하 여 적절 한 액세스 그룹에 사용자를 추가 하 고 Office 365 구독와의 동기화를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="86548-148">If you are managing user accounts and groups through Windows Server AD, add users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="86548-p107">사용자 계정 및 그룹을 통해 Office 365를 관리 하는 경우에 Office 관리 센터 또는 PowerShell을 사용할 수 있습니다. 액세스 그룹 중 하나에 대 한 중복 그룹 이름이 Office 관리 센터를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-p107">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell. If you have duplicate group names for any of the access groups, you should use the Office Admin center.</span></span>
  
<span data-ttu-id="86548-151">Office 관리 센터에 대 한 사용자 계정 관리자 또는 회사 관리자 역할 할당 된 사용자 계정을 사용 하 여 로그인 하 고 적절 한 사용자 계정을 추가 하려면 그룹 및 그룹을 적절 한 액세스 그룹을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-151">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate user accounts and groups to the appropriate access groups.</span></span>
  
<span data-ttu-id="86548-152">Powershell, 첫번째 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-152">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="86548-153">다음으로, 다음 명령은 블록을 사용 하 여 access 그룹에 개별 사용자 계정을 추가 하려면:</span><span class="sxs-lookup"><span data-stu-id="86548-153">Next, use the following command block to add an individual user account to an access group:</span></span>
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="86548-154">모든 PowerShell 명령 및 Excel을 포함 하는 텍스트 파일에 대 한 PowerShell 명령에서 생성 하는 구성 워크시트에 따라 그룹 및 사용자 계정 이름, [격리 된 SharePoint Online 팀 사이트 배포 키트](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-154">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 
  
<span data-ttu-id="86548-155">텍스트 파일에 대 한 액세스 그룹 중 하나에 대 한 사용자 계정의 Upn을 저장 하는 경우에 한번에 추가 합니다 다음 PowerShell 명령 블록을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-155">If you stored the UPNs of user accounts for any of the access groups in a text file, you can use the following PowerShell command block to add them all at one time:</span></span>
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

<span data-ttu-id="86548-156">PowerShell에 대 한 다음 명령 블록을 사용 하 여 access 그룹에 개별 그룹을 추가 하려면:</span><span class="sxs-lookup"><span data-stu-id="86548-156">For PowerShell, use the following command block to add an individual group to an access group:</span></span>
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

<span data-ttu-id="86548-157">결과 다음과 같은 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-157">The results should be the following:</span></span>
  
- <span data-ttu-id="86548-158">사이트 관리자 사용자 계정 또는 그룹을 포함 하는 사이트 관리자 Azure AD 그룹</span><span class="sxs-lookup"><span data-stu-id="86548-158">The site admins Azure AD group contains the site admin user accounts or groups</span></span>
    
- <span data-ttu-id="86548-159">사이트 구성원 사용자 계정 또는 그룹을 포함 하는 사이트 구성원 Azure AD 그룹</span><span class="sxs-lookup"><span data-stu-id="86548-159">The site members Azure AD group contains the site member user accounts or groups</span></span>
    
- <span data-ttu-id="86548-160">사용자 계정 또는 사이트 콘텐츠를 볼 수만 있는 그룹을 포함 하는 사이트 Azure AD viewers 그룹</span><span class="sxs-lookup"><span data-stu-id="86548-160">The site viewers Azure AD group contains the user accounts or groups that can only view the site contents</span></span>
    
<span data-ttu-id="86548-161">각 액세스 그룹 Office 관리 센터 또는 다음 PowerShell 명령 블록에 대 한 그룹 구성원의 목록을 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-161">Validate the list of group members for each access group with the Office Admin center or with the following PowerShell command block:</span></span>
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

<span data-ttu-id="86548-162">사용자 계정 또는 그룹으로 채워진 세 사이트 액세스 그룹과 결과 구성에는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-162">Here is your resulting configuration with the three site access groups populated with user accounts or groups.</span></span>
  
![세 개의 액세스 그룹은 사용자 계정으로 채워집니다.](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a><span data-ttu-id="86548-164">2 단계: 만들기 및 격리 된 팀 사이트 구성</span><span class="sxs-lookup"><span data-stu-id="86548-164">Phase 2: Create and configure the isolated team site</span></span>

<span data-ttu-id="86548-165">이 단계에서 격리 된 SharePoint Online 사이트 만들고 새 Azure AD 기반 액세스 그룹을 사용 하 여 기본 SharePoint Online 사용 권한 수준에 대 한 사용 권한을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-165">In this phase, you create the isolated SharePoint Online site and configure the permissions for the default SharePoint Online permission levels to use your new Azure AD-based access groups.</span></span>
  
<span data-ttu-id="86548-166">먼저, 다음이 단계와 SharePoint Online 팀 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86548-166">First, create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="86548-p108">SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="86548-p108">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="86548-169">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-169">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="86548-170">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-170">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="86548-171">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-171">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="86548-172">**사이트 이름**팀 사이트에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-172">In **Site name**, type a name for the team site.</span></span> 
    
6. <span data-ttu-id="86548-173">**팀 사이트 설명** 에 사이트의 용도 대 한 선택적 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-173">In **Team site description,** type an optional description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="86548-174">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-174">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="86548-175">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-175">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="86548-176">다음으로 새 SharePoint Online 팀 사이트에서 사용 권한을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-176">Next, from the new SharePoint Online team site, configure permissions.</span></span>
  
1. <span data-ttu-id="86548-177">도구 모음에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-177">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
2. <span data-ttu-id="86548-178">**사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-178">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
3. <span data-ttu-id="86548-179">브라우저의 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-179">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
4. <span data-ttu-id="86548-180">**액세스 요청 설정** 대화 상자에서의 선택을 취소 **허용 액세스 요청** 및 **사이트 및 개별 파일 및 폴더 공유 허용 구성원** (되도록 세 확인란을 모두 선택 취소)를 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-180">In the **Access Requests Settings** dialog box, clear **Allow member to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
5. <span data-ttu-id="86548-181">브라우저의 **사용 권한** 탭을 클릭 ** \<사이트 이름 > 구성원** 목록에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-181">On the **Permissions** tab of your browser, click **\<site name> Members** in the list.</span></span>
    
6. <span data-ttu-id="86548-182">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-182">In **People and Groups**, click **New**.</span></span>
    
7. <span data-ttu-id="86548-183">**공유** 대화 상자에서 사이트 구성원 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-183">In the **Share** dialog box, type the name of the site members access group, select it, and then click **Share**.</span></span>
    
8. <span data-ttu-id="86548-184">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-184">Click the back button on your browser.</span></span>
    
9. <span data-ttu-id="86548-185">클릭 ** \<사이트 이름 > 소유자** 목록에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-185">Click **\<site name> Owners** in the list.</span></span>
    
10. <span data-ttu-id="86548-186">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-186">In **People and Groups**, click **New**.</span></span>
    
11. <span data-ttu-id="86548-187">**공유** 대화 상자에서 사이트 관리자 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-187">In the **Share** dialog box, type the name of the site admins access group, select it, and then click **Share**.</span></span>
    
12. <span data-ttu-id="86548-188">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-188">Click the back button on your browser.</span></span>
    
13. <span data-ttu-id="86548-189">클릭 ** \<사이트 이름 > 방문자** 목록에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-189">Click **\<site name> Visitors** in the list.</span></span>
    
14. <span data-ttu-id="86548-190">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-190">In **People and Groups**, click **New**.</span></span>
    
15. <span data-ttu-id="86548-191">**공유** 대화 상자에서 사이트 뷰어 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-191">In the **Share** dialog box, type the name of the site viewers access group, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="86548-192">브라우저의 **사용 권한** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-192">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="86548-193">이러한 사용 권한 설정의 결과:</span><span class="sxs-lookup"><span data-stu-id="86548-193">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="86548-194">** \<사이트 이름 > 소유자** SharePoint 그룹의 모든 구성원, **모든 권한** 권한 수준을 가진 사이트 관리자 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-194">The **\<site name> Owners** SharePoint group contains the site admins access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="86548-195">** \<사이트 이름 > 구성원** SharePoint 그룹 모두에는 구성원에 게 사용 권한 수준 **편집** 사이트 구성원 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-195">The **\<site name> Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="86548-196">** \<사이트 이름 > 방문자** SharePoint 그룹 모든 구성원에 **읽기** 권한 수준을 가진 사이트 뷰어 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-196">The **\<site name> Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="86548-197">다른 구성원을 초대 하는 구성원에 대 한 또는 비-구성원 액세스 요청에 대 한 기능을 사용 하는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-197">The ability for members to invite other members or for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="86548-198">사용자 계정으로 입력 되는 세가지 액세스 그룹이 나 Azure AD 그룹을 사용 하도록 구성 된 사이트에 대 한 세 SharePoint 그룹과 결과 구성에는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="86548-198">Here is your resulting configuration with the three SharePoint groups for the site configured to use the three access groups, which are populated with user accounts or Azure AD groups.</span></span>
  
![액세스 그룹 및 사용자 계정이 있는 격리된 SharePoint Online 사이트의 최종 구성입니다.](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
<span data-ttu-id="86548-200">및 액세스 그룹 중 하나에서 그룹 구성원 자격을 통해 사이트의 구성원 수 이제 공동 작업 사이트의 리소스를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-200">You and the members of the site, through group membership in one of the access groups, can now collaborate using the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="86548-201">다음 단계</span><span class="sxs-lookup"><span data-stu-id="86548-201">Next step</span></span>

<span data-ttu-id="86548-202">사이트 액세스 그룹 구성원 자격을 변경 하거나 사용자 지정 사용 권한으로 문서 폴더를 만들어 해야하는 경우 [Manage SharePoint Online 팀 사이트를 격리](manage-an-isolated-sharepoint-online-team-site.md)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-202">When you need to change site access group membership or create a document folder with custom permissions, see [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="86548-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86548-203">See Also</span></span>

[<span data-ttu-id="86548-204">격리 된 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="86548-204">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="86548-205">격리 된 SharePoint Online 팀 사이트를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="86548-205">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="86548-206">SharePoint Online 팀 사이트를 격리 관리</span><span class="sxs-lookup"><span data-stu-id="86548-206">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="86548-207">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="86548-207">Security solutions</span></span>](security-solutions.md)



