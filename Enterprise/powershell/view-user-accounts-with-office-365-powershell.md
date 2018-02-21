---
title: "Office 365 PowerShell을 사용한 사용자 계정 보기"
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "요약: 보기, 목록, 또는 사용자 계정을 Office 365 powershell 다양 한 방식으로 표시 합니다."
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fe36f-103">Office 365 PowerShell을 사용한 사용자 계정 보기</span><span class="sxs-lookup"><span data-stu-id="fe36f-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="fe36f-104">**요약:** 보기, 목록, 또는 사용자 계정을 Office 365 powershell 다양 한 방식으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="fe36f-105">Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트에 대 한 계정을 볼 수 있지만 Office 365 PowerShell을 사용 하 여 수 및 Office 365 관리 센터 수 없는 일부 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="fe36f-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fe36f-106">Before you begin</span></span>

<span data-ttu-id="fe36f-p101">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="fe36f-109">Office 365 사용자 계정 정보 표시</span><span class="sxs-lookup"><span data-stu-id="fe36f-109">Display Office 365 user account information</span></span>

<span data-ttu-id="fe36f-110">사용자 계정의 전체 목록을 표시 하려면 Office 365 PowerShell 명령 프롬프트 또는 PowerShell 스크립트 ISE (통합 환경)에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="fe36f-111">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-111">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="fe36f-p102">**Get-msoluser** cmdlet를 표시 하는 사용자 계정 집합을 필터링 매개 변수 집합을가지고 있습니다. 예, 허가 되지 않은 사용자 (Office 365에 추가 되었는지 하지만 서비스 중 하나를 사용 하 여 라이선스 아직 하지 않은 사용자)의 목록에 대 한이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="fe36f-114">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="fe36f-115">표시를 필터링 할 추가 매개 변수에 대 한 자세한 내용은 표시 하는 사용자 계정 집합 [Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe36f-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="fe36f-p103">더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수 있습니다 **Where-object** cmdlet은 **Get-msoluser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 하나의 명령의 결과 가져와서에 다음 명령을 보낼를 Office 365 PowerShell에 지시 하는 합니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="fe36f-119">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe36f-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fe36f-120">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fe36f-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fe36f-p104">지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** ). 중괄호 안에 명령은 지시만 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="fe36f-123">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="fe36f-p105">**Usagelocation이** 속성은 사용자 계정과 관련 된 많은 속성 중 하나입니다. 모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (\*)를 모두 표시 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="fe36f-p106">예,이 목록에서 **도시** 는 사용자 계정 속성의 이름입니다. 즉, 런던에 거주 하는 사용자에 대 한 사용자 계정을 모두 나열 하려면 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="fe36f-p107">이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**. > [비교 연산자]는 equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** > [값]는 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 일반적으로 숫자 값 또는 **$Null** 에 대 한 지정 되지 않은 > 자세한 내용은 [Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="fe36f-131">다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="fe36f-132">사용자 계정 속성을 선택하여 표시</span><span class="sxs-lookup"><span data-stu-id="fe36f-132">Select the user account properties to display</span></span>

<span data-ttu-id="fe36f-133">기본적으로 [Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet은 사용자 계정의 세 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="fe36f-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="fe36f-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="fe36f-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fe36f-135">DisplayName</span></span>
    
- <span data-ttu-id="fe36f-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="fe36f-136">isLicensed</span></span>
    
<span data-ttu-id="fe36f-p108">사용자에 대 한 작동 하는 부서 및 사용자 Office 365 서비스를 사용 하 여 있는 국가/지역 등의 추가 속성을 필요한 경우 사용자 계정 목록을 지정 하는 **Select-object** cmdlet과 함께에서 **Get-msoluser** 를 실행할 수 있습니다. 속성 수 있습니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="fe36f-139">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe36f-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fe36f-140">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fe36f-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fe36f-141">사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="fe36f-142">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-142">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

<span data-ttu-id="fe36f-p109">**Select-object** cmdlet을 사용 하는 속성을 표시 하는 명령을 선택할 수 있습니다. 모든 사용자 계정에 대 한 속성을 보려면 모두를 표시 하는 와일드 카드 문자 (\*)를 사용 하 여 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="fe36f-p110">더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수도 있습니다 **Where-object** cmdlet입니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="fe36f-148">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe36f-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fe36f-149">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fe36f-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fe36f-p111">지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** )에 다음 명령을 결과 정보를 보내고 ( **|** ). 중괄호 안에 명령은 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell 지시 됩니다 ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="fe36f-152">사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="fe36f-153">다음과 비슷한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="fe36f-154">Azure Active Directory V2 PowerShell 모듈을 사용 하 여 사용자 계정을 표시 하려면</span><span class="sxs-lookup"><span data-stu-id="fe36f-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="fe36f-p112">Azure Active Directory V2 PowerShell 모듈을 사용자 계정에 대 한 속성을 표시 하려면 [Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet을 사용 합니다. 하지만 먼저, 구독에 연결 해야 합니다. 지침,[Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="fe36f-158">Office 365 사용자 계정 정보 표시</span><span class="sxs-lookup"><span data-stu-id="fe36f-158">Display Office 365 user account information</span></span>

<span data-ttu-id="fe36f-159">사용자 계정의 전체 목록을 표시 하려면 Office 365 PowerShell 명령 프롬프트 또는 PowerShell 스크립트 ISE (통합 환경)에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="fe36f-160">기본적으로 **Get AzureADUser** cmdlet은 사용자 계정의 세 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="fe36f-161">ObjectID</span><span class="sxs-lookup"><span data-stu-id="fe36f-161">ObjectID</span></span>
    
- <span data-ttu-id="fe36f-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fe36f-162">DisplayName</span></span>
    
- <span data-ttu-id="fe36f-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="fe36f-163">UserPrincipalName</span></span>
    
<span data-ttu-id="fe36f-p113">더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수 있습니다 **Where-object** cmdlet은 **Get AzureADUser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 하나의 명령의 결과 가져와서에 다음 명령을 보낼를 Office 365 PowerShell에 지시 하는 합니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="fe36f-167">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe36f-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fe36f-168">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fe36f-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fe36f-p114">지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** ). 중괄호 안에 명령은 지시만 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="fe36f-p115">**Usagelocation이** 속성은 사용자 계정과 관련 된 많은 속성 중 하나입니다. 모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (\*)를 모두 표시 특정 사용자 계정 ( **더 많은** ) 한번에 한 페이지에 대 한 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="fe36f-p116">예, **도시** 는 사용자 계정 속성의 이름입니다. 즉, 런던에 거주 하는 사용자에 대 한 사용자 계정을 모두 나열 하려면 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="fe36f-p117">이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**. > [비교 연산자]는 equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** > [값]는 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 일반적으로 숫자 값 또는 **$Null** 에 대 한 지정 되지 않은 > 자세한 내용은[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="fe36f-178">사용자 계정 속성을 선택하여 표시</span><span class="sxs-lookup"><span data-stu-id="fe36f-178">Select the user account properties to display</span></span>

<span data-ttu-id="fe36f-p118">기본적으로 **Get AzureADUser** cmdlet은 사용자 계정의 ObjectID, DisplayName 및 UserPrincipalName 속성을 표시 합니다. 사용자에 대 한 작동 하는 부서 및 사용자 Office 365 서비스를 사용 하 여 있는 국가/지역 등의 추가 속성을 필요한 경우 사용자의 목록을 지정 하는 **Select-object** cmdlet과 함께에서 **Get AzureADUser** 를 실행할 수 있습니다. 계정 속성입니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="fe36f-182">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe36f-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fe36f-183">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fe36f-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fe36f-184">사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="fe36f-p119">더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수도 있습니다 **Where-object** cmdlet입니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="fe36f-187">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe36f-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fe36f-188">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fe36f-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fe36f-p120">지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** )에 다음 명령을 결과 정보를 보내고 ( **|** ). 중괄호 안에 명령은 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell 지시 됩니다 ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="fe36f-191">사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe36f-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="fe36f-192">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="fe36f-192">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="fe36f-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe36f-193">See also</span></span>

#### 

[<span data-ttu-id="fe36f-194">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="fe36f-194">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fe36f-195">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="fe36f-195">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fe36f-196">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="fe36f-196">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

