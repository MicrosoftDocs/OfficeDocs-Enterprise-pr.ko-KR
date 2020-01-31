---
title: 중앙 집중식 배포 PowerShell cmdlet을 사용하여 추가 기능 관리
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2020
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
ms.openlocfilehash: 0577a4d69d7b6d32164e66613a9d38a71d9766e4
ms.sourcegitcommit: 3ed7b1eacf009581a9897524c181afa3e555ad3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/28/2020
ms.locfileid: "41570875"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>중앙 집중식 배포 PowerShell cmdlet을 사용하여 추가 기능 관리

Microsoft 365 글로벌 또는 Exchange 관리자로 서, 중앙 집중식 배포 기능을 통해 사용자에 게 Office 추가 기능을 배포할 수 있습니다 ( [관리 센터에서 Office 추가 기능 배포](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)참조). 365 Microsoft PowerShell을 사용 하 여 Office 추가 기능을 배포 하는 것 외에도 [Windows PowerShell 용 O365 중앙화 된 추가 기능 배포 모듈](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)을 설치 합니다. 

모듈을 다운로드 한 후에는 일반 Windows PowerShell 창을 열고 다음 cmdlet을 실행 합니다.

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>관리자 자격 증명을 사용 하 여 연결

중앙 집중식 배포 cmdlet을 사용 하려면 먼저 로그인 해야 합니다.
  
1. PowerShell을 시작 합니다.
    
2. 회사 관리자 자격 증명을 사용 하 여 PowerShell에 연결 합니다. 다음 cmdlet을 실행 합니다.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. **자격 증명 입력** 페이지에서 Office 365 전역 관리자 자격 증명을 입력 합니다. 또는 cmdlet에 직접 자격 증명을 입력할 수 있습니다. 
    
    회사 관리자 자격 증명을 PSCredential 개체로 지정 하 여 다음 cmdlet을 실행 합니다.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Connect To Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)를 참조 하세요. 
  
## <a name="upload-an-add-in-manifest"></a>추가 기능 매니페스트 업로드

**OrganizationAdd** cmdlet을 실행 하 여 파일 위치나 URL이 될 수 있는 경로에서 추가 기능 매니페스트를 업로드 합니다. 다음 예제에서는 _ManifestPath_ 매개 변수 값에 대 한 파일 위치를 보여 줍니다. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

다음 예제와 같이 _Members_ 매개 변수를 사용 하 여 추가 기능을 업로드 하 고 사용자 또는 그룹에 직접 할당 하려면 **OrganizationAdd** cmdlet을 실행할 수도 있습니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Office 스토어에서 추가 기능 업로드

**OrganizationAddIn** cmdlet을 실행 하 여 Office 스토어에서 매니페스트를 업로드 합니다.
  
다음 예제에서는 **OrganizationAddIn** Cmdlet은 미국 및 콘텐츠 시장의 추가 기능에 대 한 AssetId를 지정 합니다.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_AssetId_ 매개 변수의 값을 확인 하기 위해 추가 기능에 대 한 Office 스토어 웹 페이지의 URL에서이를 복사할 수 있습니다. AssetIds는 항상 "WA" 다음에 숫자를 사용 하 여 시작 합니다. 예를 들어 이전 예제에서 WA104099688의 AssetId 값에 대 한 원본은 추가 기능의 Office 스토어 웹 페이지 URL입니다 [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
_Locale_ 매개 변수와 _contentmarket_ 매개 변수의 값은 동일 하며 추가 기능을 설치 하려고 하는 국가/지역을 나타냅니다. 형식은 en-us, fr-FR입니다. 등이 있습니다. 
  
> [!NOTE]
> Office 스토어에서 업로드 된 추가 기능은 Office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다. 
  
## <a name="get-details-of-an-add-in"></a>추가 기능의 세부 정보 가져오기

아래와 같이 **OrganizationAddIn** cmdlet을 실행 하 여 테 넌 트에 업로드 된 모든 추가 기능에 대 한 세부 정보를 가져오고 추가 기능의 제품 ID를 포함 합니다.
  
```powershell
Get-OrganizationAddIn
```

**OrganizationAddIn** Cmdlet을 _ProductId_ 매개 변수의 값과 함께 실행 하 여 세부 정보를 검색할 추가 기능을 지정 합니다. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

할당 된 사용자 및 그룹의 모든 추가 기능에 대 한 세부 정보를 보려면 다음 예제와 같이 **OrganizationAddIn** cmdlet의 출력을 형식 목록 cmdlet에 파이프 합니다.
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>추가 기능 설정 또는 해제

추가 기능을 해제 하 여 자신에 게 할당 된 사용자 및 그룹에 더 이상 액세스할 수 없도록 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 **OrganizationAddIn** cmdlet을 실행 하 고 `$false` _Enabled_ 매개 변수를로 설정 합니다.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

추가 기능을 다시 설정 하려면 _Enabled_ 매개 변수를 `$true`로 설정 하 여 동일한 cmdlet을 실행 합니다.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>추가 기능에서 사용자 추가 또는 제거

특정 추가 기능에 사용자 및 그룹을 추가 하려면 _ProductId_, _add_및 _Members_ 매개 변수를 사용 하 여 **OrganizationAddInAssignments** cmdlet을 실행 합니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

사용자 및 그룹을 제거 하려면 _remove_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

테 넌 트의 모든 사용자에 게 추가 기능을 할당 하려면 값이로 `$true`설정 된 다음 _사용자 지정 매개 변수_ 를 사용 하 여 동일한 cmdlet을 실행 합니다.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

모든 사용자에 게 추가 기능을 할당 하 고 이전에 할당 된 사용자 및 그룹으로 되돌리려면 같은 cmdlet을 실행 하 고 해당 값을로 `$false`설정 하 여 _모든 사람_ 지정 매개 변수를 해제할 수 있습니다.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>추가 기능 업데이트

매니페스트에서 추가 기능을 업데이트 하려면 다음 예제와 같이 _ProductId_, _ManifestPath_및 _Locale_ 매개 변수를 사용 하 여 **OrganizationAddIn** cmdlet을 실행 합니다. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Office 스토어에서 업로드 된 추가 기능은 Office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다. 
  
## <a name="delete-an-add-in"></a>추가 기능 삭제

추가 기능을 삭제 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 **OrganizationAddIn** cmdlet을 실행 합니다. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature. 

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters 
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters: 
 
    - \<
    -  \>
    -  ;
    -  =   

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in’s icon (in admin center). </br> |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.| 
| \<AppDomains> | A list of domains that the add-in can connect with. | 
| \<SupportURL>| The URL users can use to access help and support. | 
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.| 
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.  

```powershell
Get-OrganizationAddInOverrides 
```
If ProductId is specified, then a list of overrides applied to that add-in is returned. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remive an add-in from cache:

1. Navigate to the “Users” folder in C:\ 
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>각 cmdlet에 대 한 자세한 도움말 보기

Get-help cmdlet을 사용 하 여 각 cmdlet에 대 한 자세한 도움말을 확인할 수 있습니다. 예를 들어 다음 cmdlet은 OrganizationAddIn cmdlet에 대 한 자세한 정보를 제공 합니다.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


