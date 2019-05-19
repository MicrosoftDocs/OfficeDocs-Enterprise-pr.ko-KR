---
title: Office 365 클라우드 전용 id
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Office 365 구독에서 클라우드 전용 id를 사용 하는 경우 사용자 및 그룹을 만드는 방법에 대해 설명 합니다.
ms.openlocfilehash: 7a2aaf7705378da3cbd91b415f07d10b6e039293
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164613"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="66da2-103">Office 365 클라우드 전용 id</span><span class="sxs-lookup"><span data-stu-id="66da2-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="66da2-104">클라우드 전용 id를 사용 하는 경우 모든 사용자, 그룹 및 연락처가 Office 365 구독의 azure AD (azure Active Directory) 테 넌 트에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-104">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="66da2-105">다음은 클라우드 전용 id의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-105">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="66da2-106">조직의 사용자 및 사용자 계정을 다양 한 방법으로 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-106">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="66da2-107">예를 들어 직원은 직원과 영구 상태를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-107">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="66da2-108">일부는 임시 상태인 공급 업체, 계약자 또는 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-108">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="66da2-109">일부는 사용자 계정이 없지만, 상호 작용 및 공동 작업을 지원 하기 위해 특정 서비스 및 리소스에 대 한 액세스 권한을 부여 해야 하는 외부 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-109">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="66da2-110">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-110">For example:</span></span>

- <span data-ttu-id="66da2-111">테넌트 계정은 클라우드 서비스에 대한 라이선스를 부여한 조직 내부의 사용자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-111">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="66da2-112">B2B (business to Business) 계정은 공동 작업에 참여 하도록 초대한 조직 외부의 사용자를 조직에 게 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-112">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="66da2-113">그룹화 란?</span><span class="sxs-lookup"><span data-stu-id="66da2-113">What are the groupings?</span></span> <span data-ttu-id="66da2-114">예를 들어 조직에 대 한 높은 수준의 기능 또는 목적으로 사용자를 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-114">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="66da2-p104">또한 일부 클라우드 서비스는 사용자 계정 없이 조직 외부의 사용자와 공유될 수 있습니다. 이러한 사용자 그룹도 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="66da2-117">클라우드 환경을 관리 하는 여러 가지 용도로 Azure AD에서 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-117">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="66da2-118">예를 들어 Azure AD 그룹을 사용 하 여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-118">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="66da2-119">그룹 기반 라이선싱을 사용 하 여 추가 하는 즉시 사용자 계정에 Office 365에 대 한 라이선스를 자동으로 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-119">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="66da2-120">부서와 같은 사용자 계정 특성에 따라 특정 그룹에 동적으로 사용자 계정 추가</span><span class="sxs-lookup"><span data-stu-id="66da2-120">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="66da2-121">Saas(Software as a Service) 응용 프로그램에 대해 사용자를 자동으로 프로비전하고 다단계 인증 및 기타 조건부 액세스 규칙을 사용하여 이러한 응용 프로그램에 대한 액세스 보호</span><span class="sxs-lookup"><span data-stu-id="66da2-121">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="66da2-122">SharePoint Online 팀 사이트에 대 한 권한 및 액세스 수준 프로 비전</span><span class="sxs-lookup"><span data-stu-id="66da2-122">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="66da2-123">다음을 사용 하 여 새 ***사용자*** 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-123">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="66da2-124">Microsoft 365 관리 센터</span><span class="sxs-lookup"><span data-stu-id="66da2-124">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="66da2-125">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="66da2-125">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="66da2-126">다음을 사용 하 여 새 ***그룹*** 을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66da2-126">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="66da2-127">Microsoft 365 관리 센터</span><span class="sxs-lookup"><span data-stu-id="66da2-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="66da2-128">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="66da2-128">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="66da2-129">클라우드 전용 id의 다음 단계</span><span class="sxs-lookup"><span data-stu-id="66da2-129">Next step for cloud-only identities</span></span>

[<span data-ttu-id="66da2-130">사용자 계정에 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="66da2-130">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
