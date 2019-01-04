---
title: 블록 사용자 계정 Office 365 PowerShell을 사용 하 여
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Office 365 PowerShell을 사용 하 여 차단 하 고 Office 365 계정에 대 한 액세스를 차단 해제 하는 방법에 설명 합니다.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546479"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="32bc0-103">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="32bc0-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="32bc0-104">**요약:**  Office 365 PowerShell을 사용 하 여 차단 하 고 Office 365 계정에 대 한 액세스를 차단 해제 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="32bc0-p101">Office 365 계정에 대 한 액세스를 차단에 로그인 하 고 서비스 및 Office 365 조직에서 데이터에 액세스 하는 계정을 사용 하 여에서 시킬 수 없습니다. Office 365 PowerShell을 사용 하 여 여러 사용자 계정 및 개별에 대 한 액세스를 차단 하 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="32bc0-107">Azure Active Directory PowerShell을 사용 하 여 그래프 모듈에 대 한</span><span class="sxs-lookup"><span data-stu-id="32bc0-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="32bc0-108">첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="32bc0-109">개별 사용자 계정에 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="32bc0-109">Block access to individual user accounts</span></span>

<span data-ttu-id="32bc0-110">개별 사용자 계정 차단 하려면 다음 구문을 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="32bc0-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="32bc0-111">집합 AzureAD cmdlet의-ObjectID 매개 변수 중 하나는 계정 로그인 이름, 사용자 계정 이름 또는 계정 개체 id입니다.로도 알려져를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="32bc0-112">이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="32bc0-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="32bc0-113">사용자 계정을 차단 해제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="32bc0-114">UPN 사용자의 표시 이름에 따라 사용자 계정으로 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="32bc0-115">Caleb Sills 라는 사용자에 대 한 사용자 계정의 UPN을 표시 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="32bc0-116">사용자의 표시 이름에 따라 계정을 차단 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="32bc0-117">언제 든 지 다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="32bc0-118">여러 사용자 계정에 대 한 블록 액세스</span><span class="sxs-lookup"><span data-stu-id="32bc0-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="32bc0-119">여러 사용자 계정에 대 한 액세스를 차단 하려면 이름을 다음과 같이 각 줄에 로그인 한 계정을 포함 하는 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="32bc0-p102">다음 명령 예제 텍스트 파일 C:\My Documents\Accounts.txt를입니다. 텍스트 파일의 경로 파일 이름으로 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="32bc0-122">텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="32bc0-123">텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="32bc0-124">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="32bc0-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="32bc0-125">첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="32bc0-126">개별 사용자 계정에 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="32bc0-126">Block access to individual user accounts</span></span>

<span data-ttu-id="32bc0-127">개별 사용자 계정에 대 한 액세스를 차단 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="32bc0-128">이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="32bc0-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="32bc0-129">사용자 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="32bc0-130">언제 든 지 다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="32bc0-131">여러 사용자 계정에 대 한 블록 액세스</span><span class="sxs-lookup"><span data-stu-id="32bc0-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="32bc0-132">먼저, 다음과 같이 각 줄에 하나의 계정이 포함 된 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="32bc0-p103">다음 명령 예제 텍스트 파일 C:\My Documents\Accounts.txt를입니다. 텍스트 파일의 경로 파일 이름으로 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="32bc0-135">텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="32bc0-136">텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bc0-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="32bc0-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32bc0-137">See also</span></span>

[<span data-ttu-id="32bc0-138">Office 365 PowerShell을 사용하여 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="32bc0-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="32bc0-139">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="32bc0-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="32bc0-140">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="32bc0-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
