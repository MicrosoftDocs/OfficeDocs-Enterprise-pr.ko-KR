---
title: Microsoft 365 클라우드 전용 id
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/09/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Microsoft 365 구독에서 클라우드 전용 id를 사용 하는 경우 사용자 및 그룹을 만드는 방법에 대해 설명 합니다.
ms.openlocfilehash: 0c2568d7be3f7a7b476d4cf918f00baf238da5ad
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230024"
---
# <a name="microsoft-365-cloud-only-identity"></a><span data-ttu-id="451cb-103">Microsoft 365 클라우드 전용 id</span><span class="sxs-lookup"><span data-stu-id="451cb-103">Microsoft 365 cloud-only identity</span></span>

<span data-ttu-id="451cb-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="451cb-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="451cb-105">클라우드 전용 id를 사용 하는 경우 모든 사용자, 그룹 및 연락처는 Microsoft 365 구독의 azure AD (azure Active Directory) 테 넌 트에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="451cb-106">다음은 클라우드 전용 id의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-106">Here are the basic components of cloud-only identity.</span></span>
 
![클라우드 전용 id의 기본 구성 요소](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="451cb-108">조직의 사용자 및 사용자 계정을 다양 한 방법으로 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="451cb-109">예를 들어 직원은 직원과 영구 상태를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="451cb-110">일부는 임시 상태인 공급 업체, 계약자 또는 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="451cb-111">일부는 사용자 계정이 없지만, 상호 작용 및 공동 작업을 지원 하기 위해 특정 서비스 및 리소스에 대 한 액세스 권한을 부여 해야 하는 외부 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="451cb-112">예시:</span><span class="sxs-lookup"><span data-stu-id="451cb-112">For example:</span></span>

- <span data-ttu-id="451cb-113">테넌트 계정은 클라우드 서비스에 대한 라이선스를 부여한 조직 내부의 사용자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="451cb-114">B2B 계정은 공동 작업에 참여하도록 초대한 조직 외부의 사용자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration</span></span>

<span data-ttu-id="451cb-115">조직의 사용자 유형을 재고 합니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-115">Take stock of the types of users in your organization.</span></span> <span data-ttu-id="451cb-116">그룹화 란?</span><span class="sxs-lookup"><span data-stu-id="451cb-116">What are the groupings?</span></span> <span data-ttu-id="451cb-117">예를 들어 조직에 대 한 높은 수준의 기능 또는 목적으로 사용자를 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-117">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="451cb-p104">또한 일부 클라우드 서비스는 사용자 계정 없이 조직 외부의 사용자와 공유될 수 있습니다. 이러한 사용자 그룹도 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="451cb-120">클라우드 환경을 관리 하는 여러 가지 용도로 Azure AD에서 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-120">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="451cb-121">예를 들어 Azure AD 그룹을 사용 하 여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-121">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="451cb-122">그룹 기반 라이선싱을 사용 하 여 구성원으로 추가 되는 즉시 사용자 계정에 Microsoft 365에 대 한 라이선스를 자동으로 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-122">Use group-based licensing to assign licenses for Microsoft 365 to your user accounts automatically as soon as they are added as members.</span></span>
- <span data-ttu-id="451cb-123">부서 이름과 같은 사용자 계정 특성에 따라 특정 그룹에 동적으로 사용자 계정을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-123">Add user accounts to specific groups dynamically based on user account attributes, such as department name.</span></span>
- <span data-ttu-id="451cb-124">SaaS (Software as a Service) 응용 프로그램에 대 한 사용자를 자동으로 프로 비전 하 고 MFA (multi-factor authentication) 및 기타 조건부 액세스 규칙을 사용 하 여 이러한 응용 프로그램에 대 한 액세스를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-124">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication (MFA) and other Conditional Access rules.</span></span>
- <span data-ttu-id="451cb-125">SharePoint Online 팀 사이트에 대 한 권한 및 액세스 수준 프로 비전</span><span class="sxs-lookup"><span data-stu-id="451cb-125">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="451cb-126">다음을 사용 하 여 새 ***사용자*** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-126">You create new ***users*** with:</span></span>

- [<span data-ttu-id="451cb-127">Microsoft 365 관리 센터</span><span class="sxs-lookup"><span data-stu-id="451cb-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="451cb-128">Microsoft 365 용 PowerShell</span><span class="sxs-lookup"><span data-stu-id="451cb-128">PowerShell for Microsoft 365</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="451cb-129">다음을 사용 하 여 새 ***그룹*** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="451cb-129">You create new ***groups*** with:</span></span>

- [<span data-ttu-id="451cb-130">Microsoft 365 관리 센터</span><span class="sxs-lookup"><span data-stu-id="451cb-130">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="451cb-131">Microsoft 365 용 PowerShell</span><span class="sxs-lookup"><span data-stu-id="451cb-131">PowerShell for Microsoft 365</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identity"></a><span data-ttu-id="451cb-132">클라우드 전용 id의 다음 단계</span><span class="sxs-lookup"><span data-stu-id="451cb-132">Next step for cloud-only identity</span></span>

[<span data-ttu-id="451cb-133">사용자 계정에 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="451cb-133">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
