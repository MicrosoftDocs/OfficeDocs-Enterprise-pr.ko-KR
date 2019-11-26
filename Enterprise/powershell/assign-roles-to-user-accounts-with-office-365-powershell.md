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
ms.openlocfilehash: 5af8c514cbe8d102716d2d6b45e8ebdbdb5b1507
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257447"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="eb254-103">Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="eb254-104">Office 365 PowerShell을 사용 하 여 사용자 계정에 쉽고 빠르게 역할을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="eb254-105">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="eb254-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="eb254-106">먼저 전역 관리자 계정을 사용 하 여 [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="eb254-107">다음으로, 역할에 추가 하려는 사용자 계정의 로그인 이름 (예: fredsm@contoso.com)을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="eb254-108">이를 UPN (사용자 계정 이름)이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="eb254-109">다음으로, 역할 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-109">Next, determine the name of the role.</span></span> <span data-ttu-id="eb254-110">이 [관리자 역할 권한 목록을 Azure Active Directory에서](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="eb254-111">이 문서의 참고 사항에 주의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="eb254-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="eb254-112">일부 역할 이름은 Azure AD PowerShell에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="eb254-113">예를 들어 Microsoft 365 관리 센터의 "SharePoint 관리자" 역할에는 Azure AD PowerShell에 대 한 "SharePoint Service 관리자" 라는 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="eb254-114">다음으로, 로그인 및 역할 이름을 입력 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="eb254-115">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-115">Here is an example of a completed command set:</span></span>
  
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

<span data-ttu-id="eb254-116">특정 역할에 대 한 사용자 이름 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="eb254-117">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="eb254-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="eb254-118">먼저 전역 관리자 계정을 사용 하 여 [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="eb254-119">단일 역할 변경의 경우</span><span class="sxs-lookup"><span data-stu-id="eb254-119">For a single role change</span></span>

<span data-ttu-id="eb254-120">특정 사용자 계정에 대 한 가장 일반적인 방법은 표시 이름 또는 전자 메일 이름 (로그인 이름 UPN (사용자 계정 이름))을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="eb254-121">사용자 계정의 표시 이름</span><span class="sxs-lookup"><span data-stu-id="eb254-121">Display names of user accounts</span></span>

<span data-ttu-id="eb254-122">사용자 계정의 표시 이름으로 작업 하는 데 사용 되는 경우 다음 사항을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="eb254-123">구성 하려는 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="eb254-124">사용자 계정을 지정 하려면 해당 표시 이름을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-124">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="eb254-125">전체 목록 계정을 가져오려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-125">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="eb254-126">이 명령은 표시 이름별로 정렬 된 사용자 계정의 표시 이름을 한 번에 하나씩 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-126">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="eb254-127">**Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-127">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="eb254-128">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-128">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="eb254-129">PowerShell Core에서는 이름에 **Msol** 이 포함 된 Windows powershell 모듈 및 cmdlet에 대 한 Microsoft Azure Active Directory 모듈을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="eb254-130">이러한 cmdlet을 계속 사용 하려면 Windows PowerShell에서 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="eb254-131">이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-131">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="eb254-132">할당 하려는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-132">The role you want to assign.</span></span>
    
    <span data-ttu-id="eb254-133">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-133">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="eb254-134">계정의 표시 이름과 역할 이름을 확인 한 후에는 다음 명령을 사용 하 여 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-134">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="eb254-135">명령을 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-135">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="eb254-136">**$DispName** 및 **$roleName** 변수의 경우 설명 텍스트를 해당 값으로 바꾸고, \< 및 > 문자를 제거 하 고, 따옴표를 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-136">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="eb254-137">수정 된 줄을 복사 하 여 Windows PowerShell 용 Windows Azure Active Directory 모듈 창에 붙여 넣어 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-137">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="eb254-138">또는 Windows PowerShell ISE (통합 스크립트 환경)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-138">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="eb254-139">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-139">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="eb254-140">사용자 계정의 로그인 이름</span><span class="sxs-lookup"><span data-stu-id="eb254-140">Sign-in names of user accounts</span></span>

<span data-ttu-id="eb254-141">사용자 계정의 로그인 이름 또는 Upn으로 작업 하는 데 사용 되는 경우 다음 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-141">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="eb254-142">사용자 계정의 UPN입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-142">The user account's UPN.</span></span>
    
    <span data-ttu-id="eb254-143">아직 UPN을 모르는 경우에는 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-143">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="eb254-144">이 명령은 UPN을 기준으로 한 번에 한 화면씩 정렬 하 여 사용자 계정의 UPN을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-144">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="eb254-145">**Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-145">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="eb254-146">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-146">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="eb254-147">이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-147">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="eb254-148">할당 하려는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-148">The role you want to assign.</span></span>
    
    <span data-ttu-id="eb254-149">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-149">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="eb254-150">계정의 UPN과 역할 이름을 한 후에는 다음 명령을 사용 하 여 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-150">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="eb254-151">명령을 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-151">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="eb254-152">**$UpnName** 및 **$roleName** 변수의 경우 설명 텍스트를 해당 값으로 바꾸고, \< 및 > 문자를 제거 하 고, 따옴표를 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-152">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="eb254-153">수정 된 줄을 복사 하 여 Windows PowerShell 용 Windows Azure Active Directory 모듈 창에 붙여 넣어 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-153">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="eb254-154">또는 Windows PowerShell ISE를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-154">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="eb254-155">다음은 완성 된 명령 집합의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-155">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="eb254-156">여러 역할 변경의 경우</span><span class="sxs-lookup"><span data-stu-id="eb254-156">For multiple role changes</span></span>

<span data-ttu-id="eb254-157">다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-157">Determine the following:</span></span>
  
- <span data-ttu-id="eb254-158">구성 하려는 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="eb254-158">Which user accounts that you want to configure.</span></span> <span data-ttu-id="eb254-159">이전 섹션의 방법을 사용 하 여 표시 이름 또는 Upn 집합을 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-159">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="eb254-160">각 사용자 계정에 할당 하려는 역할</span><span class="sxs-lookup"><span data-stu-id="eb254-160">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="eb254-161">사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-161">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="eb254-162">다음으로 표시 이름이 나 UPN 및 role name 필드가 있는 CSV (쉼표로 구분 된 값) 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-162">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="eb254-163">Microsoft Excel에서 쉽게이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-163">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="eb254-164">다음은 표시 이름에 대 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-164">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="eb254-165">다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="eb254-166">Upn의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-166">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="eb254-167">다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb254-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="eb254-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb254-168">See also</span></span>

- [<span data-ttu-id="eb254-169">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="eb254-169">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="eb254-170">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="eb254-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="eb254-171">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="eb254-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
