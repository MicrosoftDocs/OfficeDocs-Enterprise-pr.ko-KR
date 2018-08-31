---
title: 중앙 집중화 배포 PowerShell cmdlet을 사용 하 여 추가 기능 관리
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 배포 PowerShell 중앙 집중화 cmdlet를 사용 하 여 배포 하 고 Office 365 조직에 대 한 Office 추가 기능을 관리 하는 데 도움이 됩니다.
ms.openlocfilehash: f15bd1048d9240a125a1ae8245c773d83c6c935d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541935"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="ae5f6-103">중앙 집중화 배포 PowerShell cmdlet을 사용 하 여 추가 기능 관리</span><span class="sxs-lookup"><span data-stu-id="ae5f6-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="ae5f6-p101">Office 365 관리자로 중앙 집중화 배포를 통해 사용자에 게 Office 추가 기능을 배포할 수 있습니다 ( [Office 365 관리 센터에서 Office 365 추가 기능 배포를 관리](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)참조)는 기능입니다. Office 365 관리 센터를 통해 Office 추가 기능을 배포 하는 것 외에도 Microsoft PowerShell를 사용할 수 있습니다. [다운로드](https://go.microsoft.com/fwlink/p/?linkid=850850) 는 Microsoft 다운로드 센터에서 배포 PowerShell 중앙 집중화 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="ae5f6-107">무슨 작업을 하고 싶으십니까?</span><span class="sxs-lookup"><span data-stu-id="ae5f6-107">What do you want to do?</span></span>

[<span data-ttu-id="ae5f6-108">관리 자격 증명을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="ae5f6-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="ae5f6-109">프로그램 추가 기능에서 매니페스트를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="ae5f6-110">Office 스토어에서 추가 기능을 업로드합니다</span><span class="sxs-lookup"><span data-stu-id="ae5f6-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="ae5f6-111">추가 기능에 대 한 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="ae5f6-112">켜기 또는의 프로그램 추가 기능을 해제합니다</span><span class="sxs-lookup"><span data-stu-id="ae5f6-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="ae5f6-113">추가 또는 추가 기능에서 사용자를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="ae5f6-114">추가 기능을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="ae5f6-115">추가 기능을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="ae5f6-116">각 cmdlet에 대 한 자세한 도움말을 보려면</span><span class="sxs-lookup"><span data-stu-id="ae5f6-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="ae5f6-117">관리 자격 증명을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="ae5f6-117">Connect using your admin credentials</span></span>
<span data-ttu-id="ae5f6-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-118"></span></span>

<span data-ttu-id="ae5f6-119">배포에 집중 cmdlet를 사용 하려면 먼저에 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="ae5f6-120">PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="ae5f6-p102">회사 관리자 자격 증명을 사용 하 여 PowerShell에 연결 합니다. 다음 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="ae5f6-p103">**자격 증명 입력** 페이지에서 Office 365 전역 관리자 자격 증명을 입력 합니다. 또는 cmdlet에 직접 자격 증명을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="ae5f6-125">PSCredential 개체를으로 회사를 지정 하는 다음 cmdlet 관리 자격 증명을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="ae5f6-126">PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Office 365 PowerShell 연결](https://go.microsoft.com/fwlink/p/?linkid=848585)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="ae5f6-127">프로그램 추가 기능에서 매니페스트를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-127">Upload an add-in manifest</span></span>
<span data-ttu-id="ae5f6-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-128"></span></span>

<span data-ttu-id="ae5f6-p104">프로그램 추가 기능에서 매니페스트 파일 위치 또는 URL 될 수 있는 경로에서 업로드 새로 만들기-OrganizationAdd-에 cmdlet을 실행 합니다. 다음 예제에서는 _ManifestPath_ 매개 변수의 값에 대 한 파일 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="ae5f6-p105">추가 기능을 업로드 하 고 할당 사용자 또는 그룹에 직접 _구성원_ 매개 변수를 사용 하 여 다음 예제와 같이를 새로 만들기-OrganizationAdd-에 cmdlet을 실행할 수도 있습니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="ae5f6-133">Office 스토어에서 추가 기능을 업로드합니다</span><span class="sxs-lookup"><span data-stu-id="ae5f6-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="ae5f6-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-134"></span></span>

<span data-ttu-id="ae5f6-135">Office 스토어에서 매니페스트를 업로드 하려면 새로 만들기 OrganizationAddIn cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="ae5f6-136">다음 예제에서는 새 OrganizationAddIn cmdlet은 미국, 대한민국 위치 및 콘텐츠 시장 용으로 추가 기능에 대 한 AssetId를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="ae5f6-p106">_AssetId_ 매개 변수의 값을 확인 하려면 숫자 앞에 오는 "WA"를 사용 하 여 추가 기능 AssetIds에 대 한 웹 페이지는 항상 시작 Office 저장소의 URL에서 복사할 수 있습니다. 예, 앞의 예제에서는 소스 WA104099688 AssetId 값에 대 한는 추가 기능에 대 한 Office 스토어 웹 페이지 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="ae5f6-p107">_Locale_ 매개 변수 및 _ContentMarket_ 매개 변수 값은 동일 하 고 국가/지역에서 추가 기능을 설치 하려는 나타냅니다. 형식은은 EN-US, fr-fr. 등입니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="ae5f6-143">Office 스토어에서 업로드 한 추가 기능 Office 스토어에서 사용할 수 있는 것은 최신 업데이트의 경우 다음과 같은 며칠 내에서 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="ae5f6-144">추가 기능에 대 한 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-144">Get details of an add-in</span></span>
<span data-ttu-id="ae5f6-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-145"></span></span>

<span data-ttu-id="ae5f6-146">아래와 같이 Get OrganizationAddIn cmdlet을 실행 하는 테 넌 트에 업로드 된 모든 추가 기능에 대 한 세부 정보를 가져올 포함 된 추가 기능에서 제품 id입니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="ae5f6-147">지정 하는 추가 기능에 대 한 세부 정보를 검색 하려는 _ProductId_ 매개 변수의 값을 가진 Get OrganizationAddIn cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="ae5f6-148">모든 추가 기능 및 할당 된 사용자 및 그룹의 전체 세부 정보를 얻으려면 다음 예제와 같이 Format-list cmdlet에 Get OrganizationAddIn cmdlet의 출력을 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="ae5f6-149">켜기 또는의 프로그램 추가 기능을 해제합니다</span><span class="sxs-lookup"><span data-stu-id="ae5f6-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="ae5f6-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-150"></span></span>

<span data-ttu-id="ae5f6-151">를 해제 하려면 추가 기능에서 사용자 및 그룹에 할당 된 액세스 권한이 더이상 되므로 _ProductId_ 매개 변수 및로 설정 하는 _Enabled_ 매개 변수 집합 OrganizationAddIn cmdlet을 실행 `$false`다음 예제와 같이, 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="ae5f6-152">추가 기능을 다시 설정 하려면로 설정 하는 _Enabled_ 매개 변수와 함께 동일한 cmdlet을 실행 `$true`합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="ae5f6-153">추가 또는 추가 기능에서 사용자를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="ae5f6-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-154"></span></span>

<span data-ttu-id="ae5f6-p108">추가 기능에 특정 사용자 및 그룹을 추가, _제품 Id_, _추가_및 _구성원_ 매개 변수와 함께 집합 OrganizationAddInAssignments cmdlet을 실행 합니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="ae5f6-157">사용자 및 그룹을 제거 하려면 _제거_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="ae5f6-158">추가 기능에서 테 넌 트에 있는 모든 사용자에 할당 하려면 값으로 설정 된 _AssignToEveryone_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 `$true`합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="ae5f6-159">모든 사용자에 게 추가 기능을 할당 하 고 이전에 할당 된 사용자 및 그룹으로 되돌리려면 하지,를 동일한 cmdlet을 실행 및 해당 값 설정 하 여 _AssignToEveryone_ 매개 변수를 해제 수 `$false`합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="ae5f6-160">추가 기능을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-160">Update an add-in</span></span>
<span data-ttu-id="ae5f6-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-161"></span></span>

<span data-ttu-id="ae5f6-162">매니페스트에서 추가 기능을 업데이트 하려면 다음 예제와 같이 _ProductId_, _ManifestPath_및 _로캘_ 매개 변수를 사용 하 여 집합 OrganizationAddIn cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="ae5f6-163">Office 스토어에서 업로드 한 추가 기능 Office 스토어에서 사용할 수 있는 것은 최신 업데이트의 경우 다음과 같은 며칠 내에서 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="ae5f6-164">추가 기능을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-164">Delete an add-in</span></span>
<span data-ttu-id="ae5f6-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-165"></span></span>

<span data-ttu-id="ae5f6-166">추가 기능을 삭제 하려면 다음 예제와 같이 _ProductId_ 매개 변수와 함께 제거 OrganizationAddIn cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="ae5f6-167">각 cmdlet에 대 한 자세한 도움말을 보려면</span><span class="sxs-lookup"><span data-stu-id="ae5f6-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="ae5f6-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="ae5f6-168"></span></span>

<span data-ttu-id="ae5f6-p109">Get-help cmdlet을 사용 하 여 각 cmdlet에 대 한 자세한 도움말을 살펴볼 수 있습니다. 예, 다음 cmdlet 제거 OrganizationAddIn cmdlet에 대 한 자세한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


