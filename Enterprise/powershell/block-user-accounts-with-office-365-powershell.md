---
title: 블록 사용자 계정 Office 365 PowerShell을 사용 하 여
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Office 365 PowerShell을 사용 하 여 Office 365 계정에 대 한 액세스를 차단 및 차단 해제 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 18c7cea2df2514d7402dfcfd894acc03ed69b1c9
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841695"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c8b5d-103">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="c8b5d-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c8b5d-104">Office 365 계정에 대 한 액세스를 차단 하면 사용자가 계정을 사용 하 여 Office 365 조직의 서비스 및 데이터에 로그인 하 고 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-104">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="c8b5d-105">Office 365 PowerShell을 사용 하 여 개별 및 여러 사용자 계정에 대 한 액세스를 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-105">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c8b5d-106">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="c8b5d-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c8b5d-107">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="c8b5d-108">개별 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="c8b5d-108">Block access to individual user accounts</span></span>

<span data-ttu-id="c8b5d-109">개별 사용자 계정을 차단 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-109">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="c8b5d-110">AzureAD cmdlet의-ObjectID 매개 변수는 사용자 보안 주체 이름이 라고도 하는 계정 로그인 이름 또는 계정의 개체 ID를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-110">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="c8b5d-111">이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-111">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="c8b5d-112">사용자 계정을 차단 해제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-112">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="c8b5d-113">사용자의 표시 이름을 기준으로 사용자 계정 UPN을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-113">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="c8b5d-114">이 예에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 UPN을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-114">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c8b5d-115">사용자의 표시 이름을 기준으로 계정을 차단 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-115">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="c8b5d-116">언제 든 지 다음 명령을 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-116">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="c8b5d-117">여러 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="c8b5d-117">Block access to multiple user accounts</span></span>

<span data-ttu-id="c8b5d-118">여러 사용자 계정에 대 한 액세스를 차단 하려면 다음과 같은 각 줄에 계정 로그인 이름이 하나씩 포함 된 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-118">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="c8b5d-119">다음 명령에서 예제 텍스트 파일은 C:\My Documents\accounts.txt입니다 .입니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-119">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="c8b5d-120">텍스트 파일의 경로 및 파일 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-120">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="c8b5d-121">텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-121">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="c8b5d-122">텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-122">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c8b5d-123">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="c8b5d-123">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c8b5d-124">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-124">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="c8b5d-125">개별 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="c8b5d-125">Block access to individual user accounts</span></span>

<span data-ttu-id="c8b5d-126">개별 사용자 계정에 대 한 액세스를 차단 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-126">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="c8b5d-127">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-127">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c8b5d-128">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-128">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="c8b5d-129">이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="c8b5d-130">사용자 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-130">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="c8b5d-131">언제 든 지 다음 명령을 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-131">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="c8b5d-132">여러 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="c8b5d-132">Block access to multiple user accounts</span></span>

<span data-ttu-id="c8b5d-133">먼저 다음과 같이 각 줄에 하나의 계정을 포함 하는 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-133">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="c8b5d-134">다음 명령에서 예제 텍스트 파일은 C:\My Documents\accounts.txt입니다 .입니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-134">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="c8b5d-135">텍스트 파일의 경로 및 파일 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-135">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="c8b5d-136">텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-136">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="c8b5d-137">텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b5d-137">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="c8b5d-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8b5d-138">See also</span></span>

[<span data-ttu-id="c8b5d-139">Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="c8b5d-139">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c8b5d-140">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="c8b5d-140">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c8b5d-141">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="c8b5d-141">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
