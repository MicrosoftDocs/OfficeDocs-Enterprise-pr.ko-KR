---
title: Office 365 PowerShell을 사용한 사용자 계정 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: '요약: Office 365 PowerShell을 사용 하 여 다양 한 방식으로 사용자 계정을 보거나, 나열 하거나, 표시 합니다.'
ms.openlocfilehash: 28e6ec6936040c6bb84a49e354ae1ee5e9e9de44
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655840"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e62f9-103">Office 365 PowerShell을 사용한 사용자 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e62f9-104">Microsoft 365 관리 센터를 사용 하 여 Office 365 테 넌 트에 대 한 계정을 볼 수도 있지만 Office 365 PowerShell을 사용 하 여 관리 센터에서 수행할 수 없는 몇 가지 작업을 수행 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e62f9-105">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="e62f9-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e62f9-106">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="e62f9-107">모든 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-107">View all accounts</span></span>

<span data-ttu-id="e62f9-108">사용자 계정의 전체 목록을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="e62f9-109">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-109">You should see information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="e62f9-110">특정 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-110">View a specific account</span></span>

<span data-ttu-id="e62f9-111">특정 사용자 계정을 표시 하려면 UPN (사용자 계정 이름)이 라고도 하는 사용자 계정의 로그인 계정 이름을 입력 하 고 "<" 및 ">" 문자를 제거한 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="e62f9-112">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="e62f9-113">특정 계정에 대 한 추가 속성 값 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-113">View additional property values for a specific account</span></span>

<span data-ttu-id="e62f9-114">기본적으로 **AzureADUser** cmdlet은 계정의 ObjectID, DisplayName 및 UserPrincipalName 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="e62f9-115">표시할 속성 목록을 보다 신중 하 게 선택 하려면 **AzureADUser** cmdlet과 함께 **Select-Object** cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-115">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="e62f9-116">두 cmdlet을 결합 하기 위해 Azure Active Directory PowerShell for Graph에 설명 된 "파이프" 문자를 사용 하 여 한 명령 결과를 가져와 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="e62f9-117">다음은 모든 사용자 계정에 대해 DisplayName, 학과 및 UsageLocation를 표시 하는 명령 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="e62f9-118">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e62f9-119">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e62f9-120">사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-120">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="e62f9-121">사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-121">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e62f9-122">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e62f9-123">또 다른 예로, 다음 명령을 사용 하 여 특정 사용자 계정의 사용 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e62f9-124">공통 속성을 기준으로 일부 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-124">View some accounts based on a common property</span></span>

<span data-ttu-id="e62f9-125">표시할 계정 목록에 대해 좀 더 선택 하려면 **AzureADUser** cmdlet과 함께 **Where** cmdlet을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-125">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="e62f9-126">두 cmdlet을 결합 하기 위해 Azure Active Directory PowerShell for Graph에 설명 된 "파이프" 문자를 사용 하 여 한 명령 결과를 가져와 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="e62f9-127">다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e62f9-128">이 명령은 다음과 같은 그래프에 Azure Active Directory PowerShell을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="e62f9-129">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e62f9-130">사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-130">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="e62f9-131">중괄호 내에서이 명령은 Office 365 PowerShell에 UsageLocation 사용자 계정 속성 ( \*\* $ \_을 사용 하는 경우에만 계정 집합을 찾습니다. UsageLocation\*\* )이 지정 되지 않았습니다 ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e62f9-132">**UsageLocation** 속성은 사용자 계정에 연결 된 여러 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="e62f9-133">사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-133">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e62f9-134">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e62f9-135">예를 들어이 목록에서 **도시명** 은 사용자 계정 속성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-135">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="e62f9-136">즉, 다음 명령을 사용 하 여 London에 살아있는 사용자에 대 한 모든 사용자 계정을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-136">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e62f9-137">이러한 예에 표시 되는 **Where 개체** cmdlet의 구문은 **-object {$\_** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-137">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="e62f9-138">[사용자 계정 속성 이름] [비교 연산자] 가치 **}**. > [비교 연산자]는 equals의 경우- **eq** , **-ne** = 같지 않음,-a = 부등호, **-lt** for a,- **gt** = 보다 작음, 기타 보다 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="e62f9-139">[값]은 일반적으로 문자열 (문자, 숫자 및 기타 문자 시퀀스), 숫자 값 또는 지정 되지 않은 **$Null**> 자세한 내용을 보려면 [-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 를 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e62f9-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e62f9-140">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="e62f9-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e62f9-141">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="e62f9-142">모든 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-142">View all accounts</span></span>

<span data-ttu-id="e62f9-143">사용자 계정의 전체 목록을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="e62f9-144">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-144">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e62f9-145">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-145">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e62f9-146">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-146">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="e62f9-147">**Get-msoluser** cmdlet에도 매개 변수 집합이 있어 표시된 사용자 계정 집합을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-147">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="e62f9-148">예를 들어 Office 365에 추가 되었지만 아직 어떤 서비스를 사용 하도록 허가 되지 않은 사용자의 목록을 보려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-148">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="e62f9-149">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-149">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="e62f9-150">표시 되는 사용자 계정 집합을 필터링 하기 위한 추가 매개 변수에 대 한 자세한 내용은 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e62f9-150">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="e62f9-151">특정 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-151">View a specific account</span></span>

<span data-ttu-id="e62f9-152">특정 사용자 계정을 표시 하려면 UPN (사용자 계정 이름)이 라고도 하는 사용자 계정의 사용자 계정에 대 한 로그인 이름을 입력 하 고 "<" 및 ">" 문자를 제거한 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-152">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e62f9-153">공통 속성을 기준으로 일부 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-153">View some accounts based on a common property</span></span>

<span data-ttu-id="e62f9-154">표시할 계정 목록에 대해 좀 더 선택 하려면 **get-msoluser** cmdlet과 함께 **Where** cmdlet을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-154">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="e62f9-155">두 cmdlet을 결합 하려면 Office 365 PowerShell에 명령 결과를 가져와서 다음 명령으로 보내는 "파이프" 문자 "|"을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-155">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="e62f9-156">다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-156">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e62f9-157">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-157">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e62f9-158">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-158">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e62f9-159">사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-159">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="e62f9-160">중괄호 내에서이 명령은 Office 365 PowerShell에 UsageLocation 사용자 계정 속성 ( \*\* $ \_을 사용 하는 경우에만 계정 집합을 찾습니다. UsageLocation\*\* )이 지정 되지 않았습니다 ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-160">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e62f9-161">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-161">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="e62f9-162">**UsageLocation** 속성은 사용자 계정에 연결 된 여러 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-162">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="e62f9-163">사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-163">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e62f9-164">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-164">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e62f9-165">예를 들어이 목록에서 **도시명** 은 사용자 계정 속성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-165">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="e62f9-166">즉, 다음 명령을 사용 하 여 London에 살아있는 사용자에 대 한 모든 사용자 계정을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-166">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e62f9-167">이러한 예에 표시 되는 **Where 개체** cmdlet의 구문은 **-object {$\_** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-167">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="e62f9-168">[사용자 계정 속성 이름] [비교 연산자] 가치 **}**.</span><span class="sxs-lookup"><span data-stu-id="e62f9-168">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="e62f9-169">[비교 연산자]는 equals의 경우- **eq** , **-ne** : 같지 않음,-a = 부등호, **-** a = 보다 작음,- **gt** for = 및 기타입니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-169">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="e62f9-170">[값]은 일반적으로 문자열 (문자, 숫자 및 기타 문자의 시퀀스), 숫자 값 또는 **$Null** 지정 되지 않음에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-170">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="e62f9-171">자세한 내용은 [-Object](https://technet.microsoft.com/library/hh849715.aspx) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e62f9-171">See [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="e62f9-172">다음 명령을 사용 하 여 사용자 계정의 차단 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-172">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="e62f9-173">계정의 추가 속성 값 보기</span><span class="sxs-lookup"><span data-stu-id="e62f9-173">View additional property values for accounts</span></span>

<span data-ttu-id="e62f9-174">**Get-msoluser** cmdlet은 기본적으로 사용자 계정의 세 가지 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-174">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="e62f9-175">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="e62f9-175">UserPrincipalName</span></span>
    
- <span data-ttu-id="e62f9-176">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e62f9-176">DisplayName</span></span>
    
- <span data-ttu-id="e62f9-177">isLicensed</span><span class="sxs-lookup"><span data-stu-id="e62f9-177">isLicensed</span></span>
    
<span data-ttu-id="e62f9-178">사용자가 근무 하는 부서 및 Office 365 서비스를 사용 하는 국가/지역 같은 추가 속성이 필요한 경우 Get-msoluser **cmdlet과** 함께 **get-help** 를 실행 하 여 사용자 계정 속성의 목록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-178">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="e62f9-179">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-179">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e62f9-180">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e62f9-181">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e62f9-182">사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-182">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e62f9-183">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-183">You should see information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="e62f9-184">**Select-Object** cmdlet을 사용 하면 명령으로 표시할 속성을 선택 하 고 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-184">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="e62f9-185">사용자 계정의 모든 속성을 보려면 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-185">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e62f9-186">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-186">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e62f9-187">표시할 계정 목록을 보다 신중 하 게 선택 하기 위해, **여기서-Object** cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-187">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet.</span></span> <span data-ttu-id="e62f9-188">다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-188">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e62f9-189">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-189">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e62f9-190">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-190">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e62f9-191">사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** )을 사용 하 고 결과 정보를 다음 명령 ( **|** )로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-191">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="e62f9-192">중괄호 내에서 명령은 Office 365 PowerShell에 게 UsageLocation 사용자 계정 속성 ( \*\* $ \_을 갖는 계정 집합만 찾도록 지시 합니다. UsageLocation\*\* )이 지정 되지 않았습니다 ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-192">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="e62f9-193">사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e62f9-193">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e62f9-194">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-194">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="e62f9-195">디렉터리 동기화를 사용 하 여 Office 365 사용자를 만들고 관리 하는 경우 Office 365 사용자가 프로젝션 한 로컬 계정을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62f9-195">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="e62f9-196">다음은 Azure AD Connect가 ObjectGUID의 기본 소스 앵커를 사용 하도록 구성 된 것으로 가정 합니다 (원본 앵커 구성에 대 한 자세한 내용은 [AZURE Ad connect: Design 개념](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)참조) 및 Powershell 용 Active Directory 모듈이 설치 되어 있다고 가정 합니다 ( [RSAT 도구](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)참조).</span><span class="sxs-lookup"><span data-stu-id="e62f9-196">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="e62f9-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e62f9-197">See also</span></span>

[<span data-ttu-id="e62f9-198">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="e62f9-198">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e62f9-199">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="e62f9-199">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e62f9-200">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="e62f9-200">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

