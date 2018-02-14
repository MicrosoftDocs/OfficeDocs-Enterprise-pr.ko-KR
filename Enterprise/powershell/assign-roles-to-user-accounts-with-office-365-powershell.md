---
title: "Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "요약: Office 365 PowerShell 및 추가 MsolRoleMember cmdlet를 사용 하 여 사용자 계정에 역할을 할당 합니다."
ms.openlocfilehash: 97ecf29e10d14843322f3062ef16da14f16f7a2a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="4de2b-103">Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="4de2b-104">**요약:** Office 365 PowerShell 및 **추가 MsolRoleMember** cmdlet을 사용 하 여 사용자 계정에 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="4de2b-105">빠르고 쉽게 역할 할당할 수 있습니다를 역할 이름과 사용자 계정의 표시 이름을 확인 하 여 Office 365 PowerShell을 사용 하 여 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="4de2b-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4de2b-106">Before you begin</span></span>

<span data-ttu-id="4de2b-p101">이 항목의 절차에서는 전역 관리자 계정을 사용 하 여 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4de2b-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="4de2b-109">단일 역할 변경</span><span class="sxs-lookup"><span data-stu-id="4de2b-109">For a single role change</span></span>

<span data-ttu-id="4de2b-110">다음 사항을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-110">Determine the following:</span></span>
  
- <span data-ttu-id="4de2b-111">구성 하려는 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="4de2b-p102">사용자 계정을 지정 하려면 해당 표시 이름에 사항을 결정 해야 합니다. 전체 목록은 계정을 가져오려면이 명령을 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="4de2b-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4de2b-p103">이 명령은 한번에 한 화면 표시 이름별 정렬 하 여 사용자 계정의 표시 이름을 나열 합니다. **여기서** cmdlet을 사용 하 여 더 작은 집합 목록을 필터링 할 수 있습니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4de2b-117">이 명령은 "John"으로 시작 되는 표시 이름을 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="4de2b-118">할당 하려는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="4de2b-119">사용자 계정에 할당할 수 있는 사용 가능한 역할의 목록을 표시 하려면이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="4de2b-120">역할의 이름과 계정의 표시 이름의 확인 한 후에 계정에 역할을 할당 하려면 이러한 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="4de2b-p104">명령을 복사 하 고 메모장에 붙여넣습니다. **$DispName** 및 **$roleName** 변수에 대 한 설명 텍스트 해당 값으로 바꿉니다, 제거 된 \< 및 > 문자를 두고 따옴표를 입력 합니다. 수정 된 줄을 복사 하 고 실행 하 여 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 창에 붙여넣습니다. 또는 Windows PowerShell 스크립트 ISE (통합 환경)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="4de2b-125">완료 된 명령 집합의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="4de2b-126">여러 역할 변경에 대 한</span><span class="sxs-lookup"><span data-stu-id="4de2b-126">For multiple role changes</span></span>

<span data-ttu-id="4de2b-127">다음 사항을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-127">Determine the following:</span></span>
  
- <span data-ttu-id="4de2b-128">어떤 사용자 계정을 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="4de2b-p105">사용자 계정을 지정 하려면 해당 표시 이름에 사항을 결정 해야 합니다. 목록 계정을 가져오려면이 명령을 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="4de2b-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4de2b-p106">이 명령은 한번에 한 화면 표시 이름별 정렬 된 모든 사용자 계정의 표시 이름을 나열 합니다. **여기서** cmdlet을 사용 하 여 더 작은 집합 목록을 필터링 할 수 있습니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4de2b-134">이 명령은 "John"으로 시작 되는 표시 이름을 사용자 계정만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="4de2b-135">각 사용자 계정에 할당 하려는 되는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="4de2b-136">사용자 계정에 할당할 수 있는 사용 가능한 역할의 목록을 표시 하려면이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="4de2b-p107">다음으로, DisplayName 및 역할을 포함 하는 쉼표로 구분 된 값 (CSV) 텍스트 파일을 만들 필드 이름을 지정 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="4de2b-139">다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de2b-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="4de2b-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4de2b-140">See also</span></span>

#### 

[<span data-ttu-id="4de2b-141">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="4de2b-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4de2b-142">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="4de2b-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4de2b-143">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="4de2b-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="4de2b-144">추가 MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="4de2b-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

