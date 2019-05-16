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
ms.openlocfilehash: e1a99aef4f2045dcba8d7f3894ef82f9e7c36a15
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071104"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="189da-103">Office 365 PowerShell을 사용한 사용자 계정 보기</span><span class="sxs-lookup"><span data-stu-id="189da-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="189da-104">**요약:** Office 365 PowerShell을 사용 하 여 다양 한 방법으로 사용자 계정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="189da-105">Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트에 대 한 계정을 볼 수도 있지만 Office 365 PowerShell을 사용 하 고 Office 365 관리 센터에서 수행할 수 없는 작업도 수행 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="189da-106">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="189da-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="189da-107">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="189da-108">모든 계정 보기</span><span class="sxs-lookup"><span data-stu-id="189da-108">View all accounts</span></span>

<span data-ttu-id="189da-109">사용자 계정의 전체 목록을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="189da-110">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-110">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="189da-111">특정 계정 보기</span><span class="sxs-lookup"><span data-stu-id="189da-111">View a specific account</span></span>

<span data-ttu-id="189da-112">특정 사용자 계정을 표시 하려면 UPN (사용자 계정 이름)이 라고도 하는 사용자 계정의 로그인 계정 이름을 입력 하 고 "<" 및 ">" 문자를 제거한 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="189da-113">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="189da-114">특정 계정에 대 한 추가 속성 값 보기</span><span class="sxs-lookup"><span data-stu-id="189da-114">View additional property values for a specific account</span></span>

<span data-ttu-id="189da-115">기본적으로 **AzureADUser** cmdlet은 계정의 ObjectID, DisplayName 및 UserPrincipalName 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="189da-116">표시할 속성 목록을 보다 신중 하 게 선택 하려면 **AzureADUser** cmdlet과 함께 **Select-Object** cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-116">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="189da-117">두 cmdlet을 결합 하기 위해 Azure Active Directory PowerShell for Graph에 설명 된 "파이프" 문자를 사용 하 여 한 명령 결과를 가져와 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="189da-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="189da-118">다음은 모든 사용자 계정에 대해 DisplayName, 학과 및 UsageLocation를 표시 하는 명령 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="189da-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="189da-119">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="189da-120">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="189da-121">사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="189da-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="189da-122">사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-122">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="189da-123">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-123">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="189da-124">또 다른 예로, 다음 명령을 사용 하 여 특정 사용자 계정의 사용 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="189da-125">공통 속성을 기준으로 일부 계정 보기</span><span class="sxs-lookup"><span data-stu-id="189da-125">View some accounts based on a common property</span></span>

<span data-ttu-id="189da-126">표시할 계정 목록에 대해 좀 더 선택 하려면 **AzureADUser** cmdlet과 함께 **Where** cmdlet을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-126">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="189da-127">두 cmdlet을 결합 하기 위해 Azure Active Directory PowerShell for Graph에 설명 된 "파이프" 문자를 사용 하 여 한 명령 결과를 가져와 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="189da-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="189da-128">다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="189da-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="189da-129">이 명령은 다음과 같은 그래프에 Azure Active Directory PowerShell을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="189da-130">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="189da-131">사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="189da-131">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="189da-132">중괄호 내에서이 명령은 Office 365 PowerShell에 UsageLocation 사용자 계정 속성 ( \*\* $ \_을 사용 하는 경우에만 계정 집합을 찾습니다. UsageLocation\*\* )이 지정 되지 않았습니다 ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="189da-132">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="189da-133">**UsageLocation** 속성은 사용자 계정에 연결 된 여러 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="189da-134">사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-134">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="189da-135">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-135">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="189da-136">예를 들어이 목록에서 **도시명** 은 사용자 계정 속성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="189da-136">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="189da-137">즉, 다음 명령을 사용 하 여 London에 살아있는 사용자에 대 한 모든 사용자 계정을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-137">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="189da-138">이러한 예에 표시 되는 **Where 개체** cmdlet의 구문은 **-object {$\_** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-138">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="189da-139">[사용자 계정 속성 이름] [비교 연산자] 가치 **}**. > [비교 연산자]는 equals의 경우- **eq** , **-ne** = 같지 않음,-a = 부등호, **-lt** for a,- **gT** = 보다 작음, 기타 보다 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="189da-140">[값]은 일반적으로 문자열 (문자, 숫자 및 기타 문자의 시퀀스), 숫자 값 또는 **$Null** unspecified>에 대 한 자세한 내용은 [여기에서-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 를 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="189da-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="189da-141">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="189da-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="189da-142">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="189da-143">모든 계정 보기</span><span class="sxs-lookup"><span data-stu-id="189da-143">View all accounts</span></span>

<span data-ttu-id="189da-144">사용자 계정의 전체 목록을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="189da-145">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="189da-146">**Get-msoluser** cmdlet에도 매개 변수 집합이 있어 표시된 사용자 계정 집합을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-146">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="189da-147">예를 들어 Office 365에 추가 되었지만 아직 어떤 서비스를 사용 하도록 허가 되지 않은 사용자의 목록을 보려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-147">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="189da-148">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="189da-149">표시 되는 사용자 계정 집합을 필터링 하기 위한 추가 매개 변수에 대 한 자세한 내용은 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="189da-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="189da-150">특정 계정 보기</span><span class="sxs-lookup"><span data-stu-id="189da-150">View a specific account</span></span>

<span data-ttu-id="189da-151">특정 사용자 계정을 표시 하려면 UPN (사용자 계정 이름)이 라고도 하는 사용자 계정의 사용자 계정에 대 한 로그인 이름을 입력 하 고 "<" 및 ">" 문자를 제거한 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="189da-152">공통 속성을 기준으로 일부 계정 보기</span><span class="sxs-lookup"><span data-stu-id="189da-152">View some accounts based on a common property</span></span>

<span data-ttu-id="189da-153">표시할 계정 목록에 대해 좀 더 선택 하려면 **get-msoluser** cmdlet과 함께 **Where** cmdlet을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-153">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="189da-154">두 cmdlet을 결합 하려면 Office 365 PowerShell에 명령 결과를 가져와서 다음 명령으로 보내는 "파이프" 문자 "|"을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-154">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="189da-155">다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="189da-155">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="189da-156">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="189da-157">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="189da-158">사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="189da-158">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="189da-159">중괄호 내에서이 명령은 Office 365 PowerShell에 UsageLocation 사용자 계정 속성 ( \*\* $ \_을 사용 하는 경우에만 계정 집합을 찾습니다. UsageLocation\*\* )이 지정 되지 않았습니다 ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="189da-159">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="189da-160">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="189da-161">**UsageLocation** 속성은 사용자 계정에 연결 된 여러 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-161">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="189da-162">사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-162">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="189da-163">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-163">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="189da-164">예를 들어이 목록에서 **도시명** 은 사용자 계정 속성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="189da-164">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="189da-165">즉, 다음 명령을 사용 하 여 London에 살아있는 사용자에 대 한 모든 사용자 계정을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-165">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="189da-166">이러한 예에 표시 되는 **Where 개체** cmdlet의 구문은 **-object {$\_** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-166">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="189da-167">[사용자 계정 속성 이름] [비교 연산자] 가치 **}**.</span><span class="sxs-lookup"><span data-stu-id="189da-167">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="189da-168">[비교 연산자]는 equals의 경우- **eq** , **-ne** : 같지 않음,-a = 부등호, **-** a = 보다 작음,- **gt** for = 및 기타입니다.</span><span class="sxs-lookup"><span data-stu-id="189da-168">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="189da-169">[값]은 일반적으로 문자열 (문자, 숫자 및 기타 문자의 시퀀스), 숫자 값 또는 **$Null** 지정 되지 않음에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-169">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="189da-170">자세한 내용은 [-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="189da-170">See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="189da-171">다음 명령을 사용 하 여 사용자 계정의 차단 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="189da-172">계정의 추가 속성 값 보기</span><span class="sxs-lookup"><span data-stu-id="189da-172">View additional property values for accounts</span></span>

<span data-ttu-id="189da-173">**Get-msoluser** cmdlet은 기본적으로 사용자 계정의 세 가지 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="189da-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="189da-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="189da-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="189da-175">DisplayName</span></span>
    
- <span data-ttu-id="189da-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="189da-176">isLicensed</span></span>
    
<span data-ttu-id="189da-177">사용자가 근무 하는 부서 및 Office 365 서비스를 사용 하는 국가/지역 같은 추가 속성이 필요한 경우 Get-msoluser cmdlet과 함께 **get-help** 를 실행 하 여 사용자 계정 목록을 지정할 수 있습니다 \*\*\*\* . 물성.</span><span class="sxs-lookup"><span data-stu-id="189da-177">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="189da-178">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-178">Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="189da-179">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="189da-180">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="189da-181">사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="189da-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="189da-182">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="189da-183">**Select-Object** cmdlet을 사용 하면 명령으로 표시할 속성을 선택 하 고 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-183">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="189da-184">사용자 계정의 모든 속성을 보려면 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-184">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="189da-185">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-185">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="189da-186">표시할 계정 목록을 보다 신중 하 게 선택 하기 위해, **여기서-Object** cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-186">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet.</span></span> <span data-ttu-id="189da-187">다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="189da-187">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="189da-188">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="189da-189">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="189da-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="189da-190">사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** )을 사용 하 고 결과 정보를 다음 명령 ( **|** )로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="189da-190">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="189da-191">중괄호 내에서 명령은 Office 365 PowerShell에 게 UsageLocation 사용자 계정 속성 ( \*\* $ \_을 갖는 계정 집합만 찾도록 지시 합니다. UsageLocation\*\* )이 지정 되지 않았습니다 ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="189da-191">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="189da-192">사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="189da-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="189da-193">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="189da-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="189da-194">디렉터리 동기화를 사용 하 여 Office 365 사용자를 만들고 관리 하는 경우 Office 365 사용자가 프로젝션 한 로컬 계정을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189da-194">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="189da-195">다음은 Azure AD Connect가 ObjectGUID의 기본 원본 앵커를 사용 하도록 구성 된 것으로 가정 합니다 (원본 앵커 구성에 대 한 자세한 내용은 [AZURE Ad connect: Design 개념](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)참조) 및 Powershell 용 Active Directory 모듈에 대 한 것으로 가정 설치 된 경우 ( [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)참조):</span><span class="sxs-lookup"><span data-stu-id="189da-195">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="189da-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="189da-196">See also</span></span>

[<span data-ttu-id="189da-197">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="189da-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="189da-198">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="189da-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="189da-199">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="189da-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

