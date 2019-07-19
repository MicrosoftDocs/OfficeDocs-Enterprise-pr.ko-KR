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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 중앙 집중식 배포 PowerShell cmdlet을 사용 하 여 Office 365 조 직 용 Office 추가 기능을 배포 하 고 관리 하는 데 도움을 받을 수 있습니다.
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791253"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="7b7f3-103">중앙 집중식 배포 PowerShell cmdlet을 사용하여 추가 기능 관리</span><span class="sxs-lookup"><span data-stu-id="7b7f3-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="7b7f3-104">Microsoft 365 글로벌 또는 Exchange 관리자로 서, 중앙 집중식 배포 기능을 통해 사용자에 게 Office 추가 기능을 배포할 수 있습니다 ( [관리 센터에서 Office 추가 기능 배포](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)참조).</span><span class="sxs-lookup"><span data-stu-id="7b7f3-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="7b7f3-105">365 Microsoft PowerShell을 사용 하 여 Office 추가 기능을 배포 하는 것 외에도</span><span class="sxs-lookup"><span data-stu-id="7b7f3-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="7b7f3-106">[Windows PowerShell 용 O365 중앙화 된 추가 기능 배포 모듈](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="7b7f3-107">모듈을 다운로드 한 후에는 일반 Windows PowerShell 창을 열고 다음 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="7b7f3-108">관리자 자격 증명을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="7b7f3-108">Connect using your admin credentials</span></span>

<span data-ttu-id="7b7f3-109">중앙 집중식 배포 cmdlet을 사용 하려면 먼저 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="7b7f3-110">PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="7b7f3-111">회사 관리자 자격 증명을 사용 하 여 PowerShell에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="7b7f3-112">다음 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="7b7f3-113">**자격 증명 입력** 페이지에서 Office 365 전역 관리자 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="7b7f3-114">또는 cmdlet에 직접 자격 증명을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="7b7f3-115">회사 관리자 자격 증명을 PSCredential 개체로 지정 하 여 다음 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="7b7f3-116">PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Connect To Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="7b7f3-117">추가 기능 매니페스트 업로드</span><span class="sxs-lookup"><span data-stu-id="7b7f3-117">Upload an add-in manifest</span></span>

<span data-ttu-id="7b7f3-118">**OrganizationAdd** cmdlet을 실행 하 여 파일 위치나 URL이 될 수 있는 경로에서 추가 기능 매니페스트를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="7b7f3-119">다음 예제에서는 _ManifestPath_ 매개 변수 값에 대 한 파일 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="7b7f3-120">다음 예제와 같이 _Members_ 매개 변수를 사용 하 여 추가 기능을 업로드 하 고 사용자 또는 그룹에 직접 할당 하려면 **OrganizationAdd** cmdlet을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="7b7f3-121">구성원의 전자 메일 주소를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="7b7f3-122">Office 스토어에서 추가 기능 업로드</span><span class="sxs-lookup"><span data-stu-id="7b7f3-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="7b7f3-123">**OrganizationAddIn** cmdlet을 실행 하 여 Office 스토어에서 매니페스트를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="7b7f3-124">다음 예제에서는 **OrganizationAddIn** Cmdlet은 미국 및 콘텐츠 시장의 추가 기능에 대 한 AssetId를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="7b7f3-125">_AssetId_ 매개 변수의 값을 확인 하기 위해 추가 기능에 대 한 Office 스토어 웹 페이지의 URL에서이를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="7b7f3-126">AssetIds는 항상 "WA" 다음에 숫자를 사용 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="7b7f3-127">예를 들어 이전 예제에서 WA104099688의 AssetId 값에 대 한 원본은 추가 기능의 Office 스토어 웹 페이지 URL입니다 [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="7b7f3-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="7b7f3-128">_Locale_ 매개 변수와 _contentmarket_ 매개 변수의 값은 동일 하며 추가 기능을 설치 하려고 하는 국가/지역을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="7b7f3-129">형식은 en-us, fr-FR입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="7b7f3-130">등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7b7f3-131">Office 스토어에서 업로드 된 추가 기능은 Office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="7b7f3-132">추가 기능의 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="7b7f3-132">Get details of an add-in</span></span>

<span data-ttu-id="7b7f3-133">아래와 같이 **OrganizationAddIn** cmdlet을 실행 하 여 테 넌 트에 업로드 된 모든 추가 기능에 대 한 세부 정보를 가져오고 추가 기능의 제품 ID를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="7b7f3-134">**OrganizationAddIn** Cmdlet을 _ProductId_ 매개 변수의 값과 함께 실행 하 여 세부 정보를 검색할 추가 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="7b7f3-135">할당 된 사용자 및 그룹의 모든 추가 기능에 대 한 세부 정보를 보려면 다음 예제와 같이 **OrganizationAddIn** cmdlet의 출력을 형식 목록 cmdlet에 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="7b7f3-136">추가 기능 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="7b7f3-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="7b7f3-137">추가 기능을 해제 하 여 자신에 게 할당 된 사용자 및 그룹이 더 이상 액세스할 수 없도록 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 **OrganizationAddIn** cmdlet을 실행 하 고 _Enabled_ 매개 변수를로 `$false`설정 합니다. .</span><span class="sxs-lookup"><span data-stu-id="7b7f3-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="7b7f3-138">추가 기능을 다시 설정 하려면 _Enabled_ 매개 변수를 `$true`로 설정 하 여 동일한 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="7b7f3-139">추가 기능에서 사용자 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="7b7f3-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="7b7f3-140">특정 추가 기능에 사용자 및 그룹을 추가 하려면 _ProductId_, _add_및 _Members_ 매개 변수를 사용 하 여 **OrganizationAddInAssignments** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="7b7f3-141">구성원의 전자 메일 주소를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="7b7f3-142">사용자 및 그룹을 제거 하려면 _remove_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="7b7f3-143">테 넌 트의 모든 사용자에 게 추가 기능을 할당 하려면 값이로 __ `$true`설정 된 다음 사용자 지정 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="7b7f3-144">모든 사용자에 게 추가 기능을 할당 하 고 이전에 할당 된 사용자 및 그룹으로 되돌리려면 같은 cmdlet을 실행 하 고 해당 값을로 `$false`설정 하 여 _모든 사람_ 지정 매개 변수를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="7b7f3-145">추가 기능 업데이트</span><span class="sxs-lookup"><span data-stu-id="7b7f3-145">Update an add-in</span></span>

<span data-ttu-id="7b7f3-146">매니페스트에서 추가 기능을 업데이트 하려면 다음 예제와 같이 _ProductId_, _ManifestPath_및 _Locale_ 매개 변수를 사용 하 여 **OrganizationAddIn** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="7b7f3-147">Office 스토어에서 업로드 된 추가 기능은 Office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="7b7f3-148">추가 기능 삭제</span><span class="sxs-lookup"><span data-stu-id="7b7f3-148">Delete an add-in</span></span>

<span data-ttu-id="7b7f3-149">추가 기능을 삭제 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 **OrganizationAddIn** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="7b7f3-150">조직에 대 한 Microsoft Store 추가 기능 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="7b7f3-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="7b7f3-151">조직에 배포 하기 전에 추가 기능을 사용자 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="7b7f3-152">버전 1.1 보다 오래 된 추가 기능은이 기능에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="7b7f3-153">또한 다음과 같은 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-153">Note also the following restrictions:</span></span>
- <span data-ttu-id="7b7f3-154">모든 Url은 절대적 (http 또는 https 포함) 이어야 하 고 유효 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-154">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="7b7f3-155">*DisplayName* 은 125 자를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-155">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="7b7f3-156">*DisplayName*, *리소스* 및 *appdomain* 에는 다음 문자가 포함 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-156">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="7b7f3-157">;</span><span class="sxs-lookup"><span data-stu-id="7b7f3-157"></span></span>
    -  =   

<span data-ttu-id="7b7f3-158">배포한 추가 기능을 사용자 지정 하려는 경우에는 관리 센터에서 제거 하 고, 배포 된 각 컴퓨터에서 제거 하는 단계에 대 한 [추가 기능을 로컬 캐시에서 제거](#remove-an-add-in-from-local-cache) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-158">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="7b7f3-159">추가 기능을 사용자 지정 하려면 *ProductId* 를 매개 변수로 사용 하 여 **OrganizationAddInOverrides** cmdlet을 실행 하 고 덮어쓸 태그와 새 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-159">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="7b7f3-160">*ProductId* 를 가져오는 방법을 알아보려면이 문서에서 [추가 기능의 세부 정보 가져오기를](#get-details-of-an-add-in) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-160">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="7b7f3-161">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-161">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
<span data-ttu-id="7b7f3-162">추가 기능의 여러 태그를 사용자 지정 하려면 명령줄에 해당 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-162">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="7b7f3-163">한 추가 기능에 여러 사용자 지정 태그를 하나의 명령으로 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-163">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="7b7f3-164">태그를 하나씩 사용자 지정 하는 경우 마지막 사용자 지정만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-164">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="7b7f3-165">또한 실수로 태그를 사용자 지정 하는 경우에는 모든 사용자 지정 내용을 제거 하 고 처음부터 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-165">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="7b7f3-166">사용자 지정할 수 있는 태그</span><span class="sxs-lookup"><span data-stu-id="7b7f3-166">Tags you can customize</span></span>

| <span data-ttu-id="7b7f3-167">Tag</span><span class="sxs-lookup"><span data-stu-id="7b7f3-167">Tag</span></span>                  | <span data-ttu-id="7b7f3-168">설명</span><span class="sxs-lookup"><span data-stu-id="7b7f3-168">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="7b7f3-169">\<IconURL></span><span class="sxs-lookup"><span data-stu-id="7b7f3-169">\<IconURL></span></span>   </br>| <span data-ttu-id="7b7f3-170">관리 센터의 추가 기능 아이콘으로 사용 되는 이미지의 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-170">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="7b7f3-171">\<DisplayName></span><span class="sxs-lookup"><span data-stu-id="7b7f3-171">\<DisplayName></span></span>| <span data-ttu-id="7b7f3-172">추가 기능의 제목 (관리 센터)입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-172">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="7b7f3-173">\<호스트></span><span class="sxs-lookup"><span data-stu-id="7b7f3-173">\<Hosts></span></span>| <span data-ttu-id="7b7f3-174">추가 기능을 지 원하는 앱 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-174">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="7b7f3-175">\<></span><span class="sxs-lookup"><span data-stu-id="7b7f3-175">\<SourceLocation></span></span> | <span data-ttu-id="7b7f3-176">추가 기능이 연결 되는 원본 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-176">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="7b7f3-177">\<Appdomain></span><span class="sxs-lookup"><span data-stu-id="7b7f3-177">\<AppDomains></span></span> | <span data-ttu-id="7b7f3-178">추가 기능이 연결할 수 있는 도메인의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-178">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="7b7f3-179">\<SupportURL></span><span class="sxs-lookup"><span data-stu-id="7b7f3-179">\<SupportURL></span></span>| <span data-ttu-id="7b7f3-180">사용자가 도움말 및 지원에 액세스 하는 데 사용할 수 있는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-180">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="7b7f3-181">\<리소스></span><span class="sxs-lookup"><span data-stu-id="7b7f3-181">\<Resources></span></span>  | <span data-ttu-id="7b7f3-182">이 태그에는 다양 한 크기의 제목, 도구 설명 및 아이콘을 비롯 한 다양 한 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-182">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="7b7f3-183">Resources 태그 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="7b7f3-183">Customize Resources tag</span></span>

<span data-ttu-id="7b7f3-184">매니페스트의 <Resources> 태그에 있는 모든 요소를 동적으로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-184">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="7b7f3-185">먼저 매니페스트를 확인 하 여 새 값을 할당 하려는 요소 id를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-185">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="7b7f3-186">태그 <Resources> 는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-186">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="7b7f3-187">이 경우 이미지의 요소 id는 "img16icon" 이며 이와 연결 된 값은 "http:<i></i>/site입니다. <i> </i>com/img. "</span><span class="sxs-lookup"><span data-stu-id="7b7f3-187">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="7b7f3-188">사용자 지정할 요소를 확인 한 후 Powershell에서 다음 명령을 사용 하 여 요소에 새 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-188">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="7b7f3-189">필요한 경우 명령을 사용 하 여 여러 요소를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-189">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="7b7f3-190">추가 기능에서 사용자 지정 제거</span><span class="sxs-lookup"><span data-stu-id="7b7f3-190">Remove customization from an add-in</span></span>

<span data-ttu-id="7b7f3-191">현재 사용자 지정 항목을 삭제 하는 데 사용할 수 있는 유일한 옵션은 한 번에 모두 삭제 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-191">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="7b7f3-192">추가 기능 사용자 지정 보기</span><span class="sxs-lookup"><span data-stu-id="7b7f3-192">View add-in customizations</span></span>

<span data-ttu-id="7b7f3-193">적용 된 사용자 지정 목록을 보려면 **OrganizationAddInOverrides** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-193">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="7b7f3-194">**OrganizationAddInOverrides** 를 *ProductId* 없이 실행 한 경우에는 재정의를 적용 한 모든 추가 기능의 목록이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-194">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="7b7f3-195">ProductId를 지정 하면 해당 추가 기능에 적용 된 재정의 목록이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-195">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="7b7f3-196">로컬 캐시에서 추가 기능 제거</span><span class="sxs-lookup"><span data-stu-id="7b7f3-196">Remove an add-in from local cache</span></span>

<span data-ttu-id="7b7f3-197">추가 기능을 배포한 경우에는 각 컴퓨터의 캐시에서 제거 해야 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-197">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="7b7f3-198">추가 기능의 캐시를 다시 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-198">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="7b7f3-199">C:\ "사용자" 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-199">Navigate to the “Users” folder in C:\</span></span> 
1. <span data-ttu-id="7b7f3-200">사용자 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-200">Go to your user folder</span></span>
1. <span data-ttu-id="7b7f3-201">AppData\Local\Microsoft\Office로 이동 하 여 해당 버전의 Office와 연결 된 폴더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-201">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="7b7f3-202">*Wef* 폴더에서 *매니페스트* 폴더를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-202">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="7b7f3-203">각 cmdlet에 대 한 자세한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="7b7f3-203">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="7b7f3-204">Get-help cmdlet을 사용 하 여 각 cmdlet에 대 한 자세한 도움말을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-204">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="7b7f3-205">예를 들어 다음 cmdlet은 OrganizationAddIn cmdlet에 대 한 자세한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b7f3-205">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


