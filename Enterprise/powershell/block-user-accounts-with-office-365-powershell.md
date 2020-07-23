---
title: PowerShell을 사용 하 여 Microsoft 365 사용자 계정 차단
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: PowerShell을 사용 하 여 Microsoft 365 계정에 대 한 액세스를 차단 및 차단 해제 하는 방법을 설명 합니다.
ms.openlocfilehash: c18c0248c51096ab089b16b2e9e31eb0929de443
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230894"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="51339-103">PowerShell을 사용 하 여 Microsoft 365 사용자 계정 차단</span><span class="sxs-lookup"><span data-stu-id="51339-103">Block Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="51339-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="51339-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="51339-105">Microsoft 365 계정에 대 한 액세스를 차단 하면 사용자가 계정을 사용 하 여 Microsoft 365 조직의 서비스 및 데이터에 로그인 하 고 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51339-105">Blocking access to a Microsoft 365 account prevents anyone from using the account to sign in and access the services and data in your Microsoft 365 organization.</span></span> <span data-ttu-id="51339-106">PowerShell을 사용 하 여 개별 및 여러 사용자 계정에 대 한 액세스를 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51339-106">You can use PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="51339-107">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="51339-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="51339-108">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="51339-109">개별 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="51339-109">Block access to individual user accounts</span></span>

<span data-ttu-id="51339-110">개별 사용자 계정을 차단 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="51339-111">AzureAD cmdlet의-ObjectID 매개 변수는 사용자 보안 주체 이름이 라고도 하는 계정 로그인 이름 또는 계정의 개체 ID를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="51339-112">이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="51339-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="51339-113">사용자 계정을 차단 해제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="51339-114">사용자의 표시 이름을 기준으로 사용자 계정 UPN을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="51339-115">이 예에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 UPN을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="51339-116">사용자의 표시 이름을 기준으로 계정을 차단 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="51339-117">언제 든 지 다음 명령을 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51339-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="51339-118">여러 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="51339-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="51339-119">여러 사용자 계정에 대 한 액세스를 차단 하려면 다음과 같은 각 줄에 계정 로그인 이름이 하나씩 포함 된 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51339-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="51339-120">다음 명령에서는 예제 텍스트 파일을 C:\My Documents\Accounts.txt 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="51339-121">텍스트 파일의 경로 및 파일 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="51339-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="51339-122">텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="51339-123">텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="51339-124">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="51339-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="51339-125">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-125">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="51339-126">개별 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="51339-126">Block access to individual user accounts</span></span>

<span data-ttu-id="51339-127">개별 사용자 계정에 대 한 액세스를 차단 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="51339-128">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51339-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="51339-129">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="51339-130">이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="51339-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="51339-131">사용자 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="51339-132">언제 든 지 다음 명령을 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51339-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="51339-133">여러 사용자 계정에 대 한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="51339-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="51339-134">먼저 다음과 같이 각 줄에 하나의 계정을 포함 하는 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51339-134">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="51339-135">다음 명령에서는 예제 텍스트 파일을 C:\My Documents\Accounts.txt 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="51339-136">텍스트 파일의 경로 및 파일 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="51339-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="51339-137">텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="51339-138">텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51339-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="51339-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51339-139">See also</span></span>

[<span data-ttu-id="51339-140">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="51339-140">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="51339-141">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="51339-141">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="51339-142">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="51339-142">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
