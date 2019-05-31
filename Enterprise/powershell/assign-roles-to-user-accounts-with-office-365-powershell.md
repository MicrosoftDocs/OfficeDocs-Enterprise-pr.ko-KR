---
title: Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '요약: Office 365 PowerShell을 사용 하 여 사용자 계정에 역할을 할당 합니다.'
ms.openlocfilehash: d06b305c348d014ce526448d7f8401c26f4d1c47
ms.sourcegitcommit: 3100813cd7dff8b27b1a30a6d6ed5a7c4765c60f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "34586984"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="964ba-103">Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="964ba-104">Office 365 PowerShell을 사용 하 여 사용자 계정에 쉽고 빠르게 역할을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="964ba-105">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="964ba-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="964ba-106">먼저 전역 관리자 계정을 사용 하 여 [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="964ba-107">다음으로, 역할에 추가 하려는 사용자 계정의 로그인 이름 (예: fredsm@contoso.com)을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="964ba-108">이를 UPN (사용자 계정 이름)이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="964ba-109">다음으로, 역할 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-109">Next, determine the name of the role.</span></span> <span data-ttu-id="964ba-110">이 [관리자 역할 권한 목록을 Azure Active Directory에서](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="964ba-111">이 문서의 참고 사항에 주의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="964ba-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="964ba-112">일부 역할 이름은 Azure AD PowerShell에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="964ba-113">예를 들어 Microsoft 365 관리 센터의 "SharePoint 관리자" 역할에는 Azure AD PowerShell에 대 한 "SharePoint Service 관리자" 라는 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="964ba-114">다음으로, 로그인 및 역할 이름을 입력 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
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

<span data-ttu-id="964ba-115">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-115">Here is an example of a completed command set:</span></span>
  
```
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

<span data-ttu-id="964ba-116">특정 역할에 대 한 사용자 이름 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="964ba-117">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="964ba-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="964ba-118">먼저 전역 관리자 계정을 사용 하 여 [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="964ba-119">단일 역할 변경의 경우</span><span class="sxs-lookup"><span data-stu-id="964ba-119">For a single role change</span></span>

<span data-ttu-id="964ba-120">특정 사용자 계정에 대 한 가장 일반적인 방법은 표시 이름 또는 전자 메일 이름 (로그인 이름 UPN (사용자 계정 이름))을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="964ba-121">사용자 계정의 표시 이름</span><span class="sxs-lookup"><span data-stu-id="964ba-121">Display names of user accounts</span></span>

<span data-ttu-id="964ba-122">사용자 계정의 표시 이름으로 작업 하는 데 사용 되는 경우 다음 사항을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="964ba-123">구성 하려는 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="964ba-124">사용자 계정을 지정 하려면 해당 표시 이름을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-124">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="964ba-125">전체 목록 계정을 가져오려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-125">To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="964ba-126">이 명령은 표시 이름별로 정렬 된 사용자 계정의 표시 이름을 한 번에 하나씩 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-126">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="964ba-127">**Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-127">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="964ba-128">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-128">Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="964ba-129">이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-129">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="964ba-130">할당 하려는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-130">The role you want to assign.</span></span>
    
    <span data-ttu-id="964ba-131">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-131">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="964ba-132">계정의 표시 이름과 역할 이름을 확인 한 후에는 다음 명령을 사용 하 여 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-132">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="964ba-133">명령을 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-133">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="964ba-134">**$DispName** 및 **$roleName** 변수의 경우 설명 텍스트를 해당 값으로 바꾸고, \< 및 > 문자를 제거 하 고, 따옴표를 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-134">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="964ba-135">수정 된 줄을 복사 하 여 Windows PowerShell 용 Windows Azure Active Directory 모듈 창에 붙여 넣어 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-135">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="964ba-136">또는 Windows PowerShell ISE (통합 스크립트 환경)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-136">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="964ba-137">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-137">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="964ba-138">사용자 계정의 로그인 이름</span><span class="sxs-lookup"><span data-stu-id="964ba-138">Sign-in names of user accounts</span></span>

<span data-ttu-id="964ba-139">사용자 계정의 로그인 이름 또는 Upn으로 작업 하는 데 사용 되는 경우 다음 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-139">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="964ba-140">사용자 계정의 UPN입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-140">The user account's UPN.</span></span>
    
    <span data-ttu-id="964ba-141">아직 UPN을 모르는 경우에는 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-141">If you don't already know the UPN, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="964ba-142">이 명령은 UPN을 기준으로 한 번에 한 화면씩 정렬 하 여 사용자 계정의 UPN을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-142">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="964ba-143">**Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-143">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="964ba-144">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-144">Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="964ba-145">이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-145">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="964ba-146">할당 하려는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-146">The role you want to assign.</span></span>
    
    <span data-ttu-id="964ba-147">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-147">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="964ba-148">계정의 UPN과 역할 이름을 한 후에는 다음 명령을 사용 하 여 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-148">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="964ba-149">명령을 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-149">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="964ba-150">**$UpnName** 및 **$roleName** 변수의 경우 설명 텍스트를 해당 값으로 바꾸고, \< 및 > 문자를 제거 하 고, 따옴표를 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-150">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="964ba-151">수정 된 줄을 복사 하 여 Windows PowerShell 용 Windows Azure Active Directory 모듈 창에 붙여 넣어 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-151">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="964ba-152">또는 Windows PowerShell ISE를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-152">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="964ba-153">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-153">Here is an example of a completed command set:</span></span>
  
```
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="964ba-154">여러 역할 변경의 경우</span><span class="sxs-lookup"><span data-stu-id="964ba-154">For multiple role changes</span></span>

<span data-ttu-id="964ba-155">다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-155">Determine the following:</span></span>
  
- <span data-ttu-id="964ba-156">구성 하려는 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="964ba-156">Which user accounts that you want to configure.</span></span> <span data-ttu-id="964ba-157">이전 섹션의 방법을 사용 하 여 표시 이름 또는 Upn 집합을 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-157">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="964ba-158">각 사용자 계정에 할당 하려는 역할</span><span class="sxs-lookup"><span data-stu-id="964ba-158">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="964ba-159">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-159">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="964ba-160">다음으로 표시 이름이 나 UPN 및 role name 필드가 있는 CSV (쉼표로 구분 된 값) 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-160">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="964ba-161">Microsoft Excel에서 쉽게이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-161">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="964ba-162">다음은 표시 이름에 대 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-162">Here is an example for display names:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="964ba-163">다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-163">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="964ba-164">Upn의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-164">Here is an example for UPNs:</span></span>
  
```
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="964ba-165">다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="964ba-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="964ba-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="964ba-166">See also</span></span>

- [<span data-ttu-id="964ba-167">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="964ba-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="964ba-168">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="964ba-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="964ba-169">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="964ba-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
