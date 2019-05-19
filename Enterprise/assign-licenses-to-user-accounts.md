---
title: 사용자 계정에 Office 365 라이선스 할당
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
description: 사용자 계정에 개별적으로 또는 그룹 구성원을 기반으로 Office 365 라이선스를 할당 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164603"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="e03e7-103">사용자 계정에 Office 365 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="e03e7-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="e03e7-104">클라우드 전용 id 모델의 경우 만든 방법에 따라 사용자 계정에 Office 365 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e03e7-104">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="e03e7-105">하이브리드 id 모델의 경우 AD DS (Active Directory 도메인 서비스) 사용자 계정이 처음으로 동기화 되 면 Office 365 라이선스가 자동으로 할당 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e03e7-105">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="e03e7-106">어느 경우 든 사용자가 전자 메일 및 Microsoft 팀과 같은 Office 365 서비스에 액세스할 수 있도록 사용자 계정에 라이선스를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e03e7-106">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="e03e7-107">사용자 계정에 개별적으로 또는 자동으로 그룹 구성원 자격을 통해 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e03e7-107">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="e03e7-108">개별 사용자 계정에 Office 365 라이선스를 할당 하려면 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e03e7-108">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="e03e7-109">Microsoft 365 관리 센터</span><span class="sxs-lookup"><span data-stu-id="e03e7-109">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="e03e7-110">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e03e7-110">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="e03e7-111">라이선스를 자동으로 할당 하려면 [AZURE AD에서 그룹 기반 라이선싱](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e03e7-111">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e03e7-112">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e03e7-112">Next steps</span></span>

<span data-ttu-id="e03e7-113">라이선스가 할당 된 전체 사용자 계정 집합을 사용 하 여 다음 작업을 수행할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e03e7-113">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="e03e7-114">Office 365 ProPlus와 같은 클라이언트 소프트웨어 배포</span><span class="sxs-lookup"><span data-stu-id="e03e7-114">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="e03e7-115">모바일 장치 관리 구성</span><span class="sxs-lookup"><span data-stu-id="e03e7-115">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="e03e7-116">서비스 및 응용 프로그램 구성</span><span class="sxs-lookup"><span data-stu-id="e03e7-116">Configure services and applications</span></span>](configure-services-and-applications.md)
