---
title: 중앙 집중식 배포 PowerShell cmdlet을 사용하여 추가 기능 관리
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
- MET150
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 중앙 집중식 배포 PowerShell cmdlet을 사용 하 여 Office 365 조 직 용 Office 추가 기능을 배포 하 고 관리 하는 데 도움을 받을 수 있습니다.
ms.openlocfilehash: 3e3ca622f4c7a84d1fb267880ebf13cc56ad9373
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004501"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="7754e-103">중앙 집중식 배포 PowerShell cmdlet을 사용하여 추가 기능 관리</span><span class="sxs-lookup"><span data-stu-id="7754e-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="7754e-104">Office 365 관리자는 중앙 집중식 배포 기능을 통해 사용자에 게 Office 추가 기능을 배포할 수 있습니다 (관리 [센터에서 office 365 추가 기능의 배포 관리](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)참조).</span><span class="sxs-lookup"><span data-stu-id="7754e-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="7754e-105">관리 센터를 통해 Office 추가 기능을 배포 하는 것 외에도 Microsoft PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="7754e-106">Microsoft 다운로드 센터에서 중앙 집중식 배포 PowerShell cmdlet을 [다운로드](https://go.microsoft.com/fwlink/p/?linkid=850850) 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="7754e-107">무슨 작업을 하고 싶으십니까?</span><span class="sxs-lookup"><span data-stu-id="7754e-107">What do you want to do?</span></span>

[<span data-ttu-id="7754e-108">관리자 자격 증명을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="7754e-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="7754e-109">추가 기능 매니페스트 업로드</span><span class="sxs-lookup"><span data-stu-id="7754e-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="7754e-110">Office 스토어에서 추가 기능 업로드</span><span class="sxs-lookup"><span data-stu-id="7754e-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="7754e-111">추가 기능의 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="7754e-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="7754e-112">추가 기능 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="7754e-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="7754e-113">추가 기능에서 사용자 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="7754e-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="7754e-114">추가 기능 업데이트</span><span class="sxs-lookup"><span data-stu-id="7754e-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="7754e-115">추가 기능 삭제</span><span class="sxs-lookup"><span data-stu-id="7754e-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="7754e-116">각 cmdlet에 대 한 자세한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="7754e-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="7754e-117">관리자 자격 증명을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="7754e-117">Connect using your admin credentials</span></span>
<span data-ttu-id="7754e-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="7754e-119">중앙 집중식 배포 cmdlet을 사용 하려면 먼저 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="7754e-120">PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="7754e-121">회사 관리자 자격 증명을 사용 하 여 PowerShell에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="7754e-122">다음 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="7754e-123">**자격 증명 입력** 페이지에서 Office 365 전역 관리자 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="7754e-124">또는 cmdlet에 직접 자격 증명을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="7754e-125">회사 관리자 자격 증명을 PSCredential 개체로 지정 하 여 다음 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="7754e-126">PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Connect To Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7754e-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="7754e-127">추가 기능 매니페스트 업로드</span><span class="sxs-lookup"><span data-stu-id="7754e-127">Upload an add-in manifest</span></span>
<span data-ttu-id="7754e-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="7754e-129">OrganizationAdd cmdlet을 실행 하 여 파일 위치나 URL이 될 수 있는 경로에서 추가 기능 매니페스트를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="7754e-130">다음 예제에서는 _ManifestPath_ 매개 변수 값에 대 한 파일 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="7754e-131">다음 예제와 같이 _Members_ 매개 변수를 사용 하 여 추가 기능을 업로드 하 고 사용자 또는 그룹에 직접 할당 하려면 OrganizationAdd cmdlet을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="7754e-132">구성원의 전자 메일 주소를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="7754e-133">Office 스토어에서 추가 기능 업로드</span><span class="sxs-lookup"><span data-stu-id="7754e-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="7754e-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="7754e-135">OrganizationAddIn cmdlet을 실행 하 여 Office 스토어에서 매니페스트를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="7754e-136">다음 예제에서는 OrganizationAddIn cmdlet은 미국 및 콘텐츠 시장의 추가 기능에 대 한 AssetId를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="7754e-137">_AssetId_ 매개 변수의 값을 확인 하기 위해 추가 기능에 대 한 Office 스토어 웹 페이지의 URL에서이를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="7754e-138">AssetIds는 항상 "WA" 다음에 숫자를 사용 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="7754e-139">예를 들어 이전 예제에서 WA104099688의 AssetId 값에 대 한 원본은 추가 기능의 Office 스토어 웹 페이지 URL입니다 [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="7754e-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="7754e-140">_Locale_ 매개 변수와 _contentmarket_ 매개 변수의 값은 동일 하며 추가 기능을 설치 하려고 하는 국가/지역을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="7754e-141">형식은 en-us, fr-FR입니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="7754e-142">등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7754e-143">Office 스토어에서 업로드 된 추가 기능은 Office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="7754e-144">추가 기능의 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="7754e-144">Get details of an add-in</span></span>
<span data-ttu-id="7754e-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="7754e-146">아래와 같이 OrganizationAddIn cmdlet을 실행 하 여 테 넌 트에 업로드 된 모든 추가 기능에 대 한 세부 정보를 가져오고 추가 기능의 제품 ID를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="7754e-147">OrganizationAddIn cmdlet을 _ProductId_ 매개 변수의 값과 함께 실행 하 여 세부 정보를 검색할 추가 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="7754e-148">할당 된 사용자 및 그룹의 모든 추가 기능에 대 한 세부 정보를 보려면 다음 예제와 같이 OrganizationAddIn cmdlet의 출력을 형식 목록 cmdlet에 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="7754e-149">추가 기능 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="7754e-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="7754e-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="7754e-151">추가 기능을 해제 하 여 자신에 게 할당 된 사용자 및 그룹에 더 이상 액세스할 수 없도록 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 OrganizationAddIn cmdlet을 실행 하 고 `$false` _Enabled_ 매개 변수를로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="7754e-152">추가 기능을 다시 설정 하려면 _Enabled_ 매개 변수를 `$true`로 설정 하 여 동일한 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="7754e-153">추가 기능에서 사용자 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="7754e-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="7754e-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="7754e-155">특정 추가 기능에 사용자 및 그룹을 추가 하려면 _ProductId_, _add_및 _Members_ 매개 변수를 사용 하 여 OrganizationAddInAssignments cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="7754e-156">구성원의 전자 메일 주소를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="7754e-157">사용자 및 그룹을 제거 하려면 _remove_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="7754e-158">테 넌 트의 모든 사용자에 게 추가 기능을 할당 하려면 값이로 `$true`설정 된 다음 _사용자 지정 매개 변수_ 를 사용 하 여 동일한 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="7754e-159">모든 사용자에 게 추가 기능을 할당 하 고 이전에 할당 된 사용자 및 그룹으로 되돌리려면 같은 cmdlet을 실행 하 고 해당 값을로 `$false`설정 하 여 _모든 사람_ 지정 매개 변수를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="7754e-160">추가 기능 업데이트</span><span class="sxs-lookup"><span data-stu-id="7754e-160">Update an add-in</span></span>
<span data-ttu-id="7754e-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="7754e-162">매니페스트에서 추가 기능을 업데이트 하려면 다음 예제와 같이 _ProductId_, _ManifestPath_및 _Locale_ 매개 변수를 사용 하 여 OrganizationAddIn cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="7754e-163">Office 스토어에서 업로드 된 추가 기능은 Office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="7754e-164">추가 기능 삭제</span><span class="sxs-lookup"><span data-stu-id="7754e-164">Delete an add-in</span></span>
<span data-ttu-id="7754e-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="7754e-166">추가 기능을 삭제 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 OrganizationAddIn cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="7754e-167">각 cmdlet에 대 한 자세한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="7754e-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="7754e-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="7754e-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="7754e-169">Get-help cmdlet을 사용 하 여 각 cmdlet에 대 한 자세한 도움말을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="7754e-170">예를 들어 다음 cmdlet은 OrganizationAddIn cmdlet에 대 한 자세한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7754e-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


