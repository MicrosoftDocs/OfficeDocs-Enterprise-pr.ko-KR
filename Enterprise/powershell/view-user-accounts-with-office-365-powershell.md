---
title: Office 365 PowerShell을 사용한 사용자 계정 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: '요약: 보기, 목록, 또는 사용자 계정을 Office 365 powershell 다양 한 방식으로 표시 합니다.'
ms.openlocfilehash: f2743197456cc56f654e99e682108230420384c9
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123255"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b6400-103">Office 365 PowerShell을 사용한 사용자 계정 보기</span><span class="sxs-lookup"><span data-stu-id="b6400-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="b6400-104">**요약:** Office 365 powershell 다양 한 방식으로 사용자 계정을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="b6400-105">Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트에 대 한 계정을 볼 수 있지만 Office 365 PowerShell을 사용 하 여 수 및 Office 365 관리 센터 수 없는 일부 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="b6400-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b6400-106">Before you begin</span></span>

<span data-ttu-id="b6400-p101">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6400-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information-with-azure-active-directory-powershell-for-graph"></a><span data-ttu-id="b6400-109">Azure Active Directory powershell 그래프에 대 한 Office 365 사용자 계정 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-109">Display Office 365 user account information with Azure Active Directory PowerShell for Graph</span></span> 

<span data-ttu-id="b6400-110">다음 섹션에서는 사용자 계정 정보를 표시 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-110">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="b6400-111">모든 계정</span><span class="sxs-lookup"><span data-stu-id="b6400-111">All accounts</span></span>

<span data-ttu-id="b6400-112">사용자 계정의 전체 목록을 표시 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-112">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="b6400-113">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-113">You should see information similar to this:</span></span>
  
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

### <a name="a-specific-account"></a><span data-ttu-id="b6400-114">특정 계정</span><span class="sxs-lookup"><span data-stu-id="b6400-114">A specific account</span></span>

<span data-ttu-id="b6400-115">특정 사용자 계정으로 표시 하려면 사용자 계정의 사용자 계정 이름 (UPN)를 입력, 제거는 "<" 및 ">" 문자를 하 고이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-115">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="additional-property-values-for-a-specific-account"></a><span data-ttu-id="b6400-116">특정 계정에 대 한 추가 속성 값</span><span class="sxs-lookup"><span data-stu-id="b6400-116">Additional property values for a specific account</span></span>

<span data-ttu-id="b6400-117">기본적으로 **Get AzureADUser** cmdlet만 계정의 ObjectID, DisplayName 및 UserPrincipalName 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-117">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="b6400-p102">더 많은 수를 표시 하려면 속성의 목록에 대 한 선택적 사용할 수 있습니다 **Select-object** cmdlet은 **Get AzureADUser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 그래프를 하나의 명령의 결과 가져간에 다음 명령을 보낼 용 Azure Active Directory PowerShell에 지시 하는 합니다. 모든 사용자 계정에 대해 DisplayName, 부서 및 usagelocation이 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p102">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="b6400-121">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b6400-121">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b6400-122">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b6400-122">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6400-123">사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-123">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="b6400-p103">모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (\*)를 모두 표시 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p103">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b6400-126">다른 예로 다음 명령 사용 하 여 특정 사용자 계정의 사용 가능된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-126">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="b6400-127">일반 속성을 기준으로 일부 계정</span><span class="sxs-lookup"><span data-stu-id="b6400-127">Some accounts based on a common property</span></span>

<span data-ttu-id="b6400-p104">더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수 있습니다 **Where-object** cmdlet은 **Get AzureADUser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 그래프를 하나의 명령의 결과 가져간에 다음 명령을 보낼 용 Azure Active Directory PowerShell에 지시 하는 합니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p104">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b6400-131">이 명령은 PowerShell Azure Active Directory를 그래프에 대 한 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-131">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="b6400-132">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b6400-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6400-p105">지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** ). 중괄호 안에 명령은 지시만 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell ( \*\* $ \_합니다. Usagelocation이\*\* ) 지정 된 ( **-eq $Null** ) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p105">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b6400-p106">**Usagelocation이** 속성은 사용자 계정과 관련 된 많은 속성 중 하나입니다. 모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (\*)를 모두 표시 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p106">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b6400-p107">예,이 목록에서 **도시** 는 사용자 계정 속성의 이름입니다. 즉, 런던에 거주 하는 사용자에 대 한 사용자 계정을 모두 나열 하려면 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p107">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b6400-p108">이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**. > equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** [비교 연산자] 됩니다.  [값]은 일반적으로 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 숫자 값 또는 **$Null** 지정 되지 않은 대 한 > 자세한 내용은 [Where-object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6400-p108">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="display-office-365-user-account-information-with-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b6400-143">Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell을 사용한 Office 365 사용자 계정 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-143">Display Office 365 user account information with Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b6400-144">다음 섹션에서는 사용자 계정 정보를 표시 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-144">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="b6400-145">모든 계정</span><span class="sxs-lookup"><span data-stu-id="b6400-145">All accounts</span></span>

<span data-ttu-id="b6400-146">사용자 계정의 전체 목록을 표시 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-146">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="b6400-147">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-147">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b6400-p109">**Get-msoluser** cmdlet를 표시 하는 사용자 계정 집합을 필터링 매개 변수 집합을가지고 있습니다. 예, 허가 되지 않은 사용자 (Office 365에 추가 되었는지 하지만 서비스 중 하나를 사용 하 여 라이선스 아직 하지 않은 사용자)의 목록에 대 한이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p109">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="b6400-150">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-150">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b6400-151">표시를 필터링 할 추가 매개 변수에 대 한 자세한 내용은 표시 하는 사용자 계정 집합 [Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6400-151">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="a-specific-account"></a><span data-ttu-id="b6400-152">특정 계정</span><span class="sxs-lookup"><span data-stu-id="b6400-152">A specific account</span></span>

<span data-ttu-id="b6400-153">특정 사용자 계정으로 표시 하려면 사용자 계정의 사용자 계정 이름 (UPN)를 입력, 제거는 "<" 및 ">" 문자를 하 고이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-153">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="b6400-154">일반 속성을 기준으로 일부 계정</span><span class="sxs-lookup"><span data-stu-id="b6400-154">Some accounts based on a common property</span></span>

<span data-ttu-id="b6400-p110">더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수 있습니다 **Where-object** cmdlet은 **Get-msoluser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 하나의 명령의 결과 가져와서에 다음 명령을 보낼를 Office 365 PowerShell에 지시 하는 합니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p110">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b6400-158">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b6400-158">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b6400-159">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b6400-159">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6400-p111">지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** ). 중괄호 안에 명령은 지시만 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell ( \*\* $ \_합니다. Usagelocation이\*\* ) 지정 된 ( **-eq $Null** ) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b6400-162">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-162">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="b6400-p112">**Usagelocation이** 속성은 사용자 계정과 관련 된 많은 속성 중 하나입니다. 모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (\*)를 모두 표시 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p112">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b6400-p113">예,이 목록에서 **도시** 는 사용자 계정 속성의 이름입니다. 즉, 런던에 거주 하는 사용자에 대 한 사용자 계정을 모두 나열 하려면 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p113">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b6400-p114">이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**.  [비교 연산자]은 equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** 입니다.  [값]는 일반적으로 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 숫자 값 또는 **$Null** 지정 되지 않은 해야 합니다. 자세한 내용은 [Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6400-p114">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="b6400-173">다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-173">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="additional-property-values-for-accounts"></a><span data-ttu-id="b6400-174">계정에 대 한 추가 속성 값</span><span class="sxs-lookup"><span data-stu-id="b6400-174">Additional property values for accounts</span></span>

<span data-ttu-id="b6400-175">기본적으로 **Get-msoluser** cmdlet은 사용자 계정의 세 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-175">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="b6400-176">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="b6400-176">UserPrincipalName</span></span>
    
- <span data-ttu-id="b6400-177">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b6400-177">DisplayName</span></span>
    
- <span data-ttu-id="b6400-178">isLicensed</span><span class="sxs-lookup"><span data-stu-id="b6400-178">isLicensed</span></span>
    
<span data-ttu-id="b6400-p115">사용자에 대 한 작동 하는 부서 및 사용자 Office 365 서비스를 사용 하 여 있는 국가/지역 등의 추가 속성을 필요한 경우 사용자 계정 목록을 지정 하는 **Select-object** cmdlet과 함께에서 **Get-msoluser** 를 실행할 수 있습니다. 속성 수 있습니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p115">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b6400-181">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b6400-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b6400-182">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b6400-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6400-183">사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-183">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b6400-184">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-184">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="b6400-p116">**Select-object** cmdlet를 사용 하면 원하는 속성을 표시 하는 명령을 선택할 수 있습니다. 모든 사용자 계정에 대 한 속성을 보려면 모두를 표시 하는 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p116">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b6400-p117">더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수도 있습니다 **Where-object** cmdlet입니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p117">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b6400-190">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b6400-190">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b6400-191">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b6400-191">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6400-p118">지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** )에 다음 명령을 결과 정보를 보내고 ( **|** ). 중괄호 안에 명령은 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell 지시 됩니다 ( \*\* $ \_합니다. Usagelocation이\*\* ) 지정 된 ( **-eq $Null** ) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-p118">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="b6400-194">사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-194">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b6400-195">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6400-195">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="b6400-p119">디렉터리 동기화를 만들고 Office 365 사용자 관리를 사용 하는 경우에 Office 365 사용자에서 예상 된가 로컬 계정을 표시할 수 있습니다. 다음 Azure AD Connect가 ObjectGUID의 기본 소스 기준 위치를 사용 하도록 구성 된 것으로 가정 (원본 기준 위치를 구성 하는 방법에 자세한 내용은 참조 [Azure AD 연결: 개념 디자인](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) powershell에 대 한 Active Directory 모듈에 있다고 가정 하 고 된 설치 ( [RSAT 도구](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)참조).</span><span class="sxs-lookup"><span data-stu-id="b6400-p119">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="new-to-office-365"></a><span data-ttu-id="b6400-198">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="b6400-198">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="b6400-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6400-199">See also</span></span>

[<span data-ttu-id="b6400-200">사용자 계정 및 Office 365 PowerShell을 사용하여 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="b6400-200">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b6400-201">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="b6400-201">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b6400-202">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="b6400-202">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

