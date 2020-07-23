---
title: PowerShell을 사용 하 여 Microsoft 365 사용자 계정에 역할 할당
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '요약: Microsoft 365 용 PowerShell을 사용 하 여 사용자 계정에 역할을 할당 합니다.'
ms.openlocfilehash: 2be491692c23b1f528612cc5c56e041553f80c48
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230874"
---
# <a name="assign-roles-to-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="44ee8-103">PowerShell을 사용 하 여 Microsoft 365 사용자 계정에 역할 할당</span><span class="sxs-lookup"><span data-stu-id="44ee8-103">Assign roles to Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="44ee8-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="44ee8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="44ee8-105">Microsoft 365 용 PowerShell을 사용 하 여 사용자 계정에 쉽고 빠르게 역할을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-105">You can quickly and easily assign roles to user accounts using PowerShell for Microsoft 365.</span></span>

>[!Note]
><span data-ttu-id="44ee8-106">Microsoft 365 관리 센터를 사용 하 여 사용자 계정에 역할을 할당 하려면 [다음 지침](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44ee8-106">To assign roles to user accounts with the Microsoft 365 admin center, see [these instructions](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="44ee8-107">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="44ee8-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="44ee8-108">먼저 전역 관리자 계정을 사용 하 여 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="44ee8-109">다음으로, 역할에 추가 하려는 사용자 계정의 로그인 이름 (예: fredsm@contoso.com)을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-109">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="44ee8-110">이를 UPN (사용자 계정 이름)이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-110">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="44ee8-111">다음으로, 역할 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-111">Next, determine the name of the role.</span></span> <span data-ttu-id="44ee8-112">이 [관리자 역할 권한 목록을 Azure Active Directory에서](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-112">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="44ee8-113">이 문서의 참고 사항에 주의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="44ee8-113">Pay attention to the notes in this article.</span></span> <span data-ttu-id="44ee8-114">일부 역할 이름은 Azure AD PowerShell에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-114">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="44ee8-115">예를 들어 Microsoft 365 관리 센터의 "SharePoint 관리자" 역할에는 Azure AD PowerShell에 대 한 "SharePoint Service 관리자" 라는 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-115">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="44ee8-116">다음으로, 로그인 및 역할 이름을 입력 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-116">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="44ee8-117">다음은 belindan@contoso.com 계정에 SharePoint 서비스 관리자 역할을 할당 하는 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-117">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="44ee8-118">특정 역할에 대 한 사용자 이름 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-118">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="44ee8-119">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="44ee8-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="44ee8-120">먼저 전역 관리자 계정을 사용 하 여 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-120">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="44ee8-121">단일 역할 변경의 경우</span><span class="sxs-lookup"><span data-stu-id="44ee8-121">For a single role change</span></span>

<span data-ttu-id="44ee8-122">특정 사용자 계정에 대 한 가장 일반적인 방법은 해당 표시 이름 또는 전자 메일 이름 (로그인 이름 또는 UPN (사용자 계정 이름))을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-122">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="44ee8-123">사용자 계정의 표시 이름</span><span class="sxs-lookup"><span data-stu-id="44ee8-123">Display names of user accounts</span></span>

<span data-ttu-id="44ee8-124">사용자 계정의 표시 이름으로 작업 하는 데 사용 되는 경우 다음 사항을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-124">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="44ee8-125">구성 하려는 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-125">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="44ee8-126">사용자 계정을 지정 하려면 해당 표시 이름을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-126">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="44ee8-127">전체 목록 계정을 가져오려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-127">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="44ee8-128">이 명령은 표시 이름별로 정렬 된 사용자 계정의 표시 이름을 한 번에 하나씩 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-128">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="44ee8-129">**Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-129">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="44ee8-130">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-130">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="44ee8-131">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-131">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="44ee8-132">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-132">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="44ee8-133">이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-133">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="44ee8-134">할당 하려는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-134">The role you want to assign.</span></span>
    
    <span data-ttu-id="44ee8-135">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-135">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="44ee8-136">계정의 표시 이름과 역할 이름을 확인 한 후에는 다음 명령을 사용 하 여 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-136">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="44ee8-137">명령을 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-137">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="44ee8-138">**$DispName** 및 **$roleName** 변수의 경우 설명 텍스트를 해당 값으로 바꾸고, 문자를 제거 \< and > 하 고, 따옴표를 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-138">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="44ee8-139">수정 된 줄을 복사 하 여 Windows PowerShell 용 Windows Azure Active Directory 모듈 창에 붙여 넣어 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-139">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="44ee8-140">또는 Windows PowerShell ISE (통합 스크립트 환경)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-140">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="44ee8-141">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-141">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="44ee8-142">사용자 계정의 로그인 이름</span><span class="sxs-lookup"><span data-stu-id="44ee8-142">Sign-in names of user accounts</span></span>

<span data-ttu-id="44ee8-143">사용자 계정의 로그인 이름 또는 Upn으로 작업 하는 데 사용 되는 경우 다음 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-143">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="44ee8-144">사용자 계정의 UPN입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-144">The user account's UPN.</span></span>
    
    <span data-ttu-id="44ee8-145">아직 UPN을 모르는 경우에는 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-145">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="44ee8-146">이 명령은 UPN을 기준으로 한 번에 한 화면씩 정렬 하 여 사용자 계정의 UPN을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-146">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="44ee8-147">**Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-147">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="44ee8-148">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-148">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="44ee8-149">이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-149">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="44ee8-150">할당 하려는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-150">The role you want to assign.</span></span>
    
    <span data-ttu-id="44ee8-151">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-151">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="44ee8-152">계정의 UPN과 역할 이름을 한 후에는 다음 명령을 사용 하 여 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-152">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="44ee8-153">명령을 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-153">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="44ee8-154">**$UpnName** 및 **$roleName** 변수의 경우 설명 텍스트를 해당 값으로 바꾸고, 문자를 제거 \< and > 하 고, 따옴표를 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-154">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="44ee8-155">수정 된 줄을 복사 하 여 Windows PowerShell 용 Windows Azure Active Directory 모듈 창에 붙여 넣어 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-155">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="44ee8-156">또는 Windows PowerShell ISE를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-156">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="44ee8-157">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-157">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="44ee8-158">여러 역할 변경</span><span class="sxs-lookup"><span data-stu-id="44ee8-158">Multiple role changes</span></span>

<span data-ttu-id="44ee8-159">여러 역할 변경의 경우 다음 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-159">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="44ee8-160">구성 하려는 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="44ee8-160">Which user accounts that you want to configure.</span></span> <span data-ttu-id="44ee8-161">이전 섹션의 방법을 사용 하 여 표시 이름 또는 Upn 집합을 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-161">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="44ee8-162">각 사용자 계정에 할당 하려는 역할</span><span class="sxs-lookup"><span data-stu-id="44ee8-162">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="44ee8-163">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-163">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="44ee8-164">다음으로 표시 이름이 나 UPN 및 role name 필드가 있는 CSV (쉼표로 구분 된 값) 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-164">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="44ee8-165">Microsoft Excel에서 쉽게이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-165">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="44ee8-166">다음은 표시 이름에 대 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-166">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="44ee8-167">다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="44ee8-168">Upn의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-168">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="44ee8-169">다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="44ee8-169">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="44ee8-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44ee8-170">See also</span></span>

- [<span data-ttu-id="44ee8-171">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="44ee8-171">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="44ee8-172">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="44ee8-172">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="44ee8-173">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="44ee8-173">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
