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
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>추가 기능 설정 또는 해제

추가 기능을 해제 하 여 자신에 게 할당 된 사용자 및 그룹이 더 이상 액세스할 수 없도록 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 **OrganizationAddIn** cmdlet을 실행 하 고 _Enabled_ 매개 변수를로 `$false`설정 합니다. .
  
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

테 넌 트의 모든 사용자에 게 추가 기능을 할당 하려면 값이로 __ `$true`설정 된 다음 사용자 지정 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다.
  
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

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>조직에 대 한 Microsoft Store 추가 기능 사용자 지정

조직에 배포 하기 전에 추가 기능을 사용자 지정 해야 합니다. 버전 1.1 보다 오래 된 추가 기능은이 기능에서 지원 되지 않습니다. 

또한 다음과 같은 제한이 있습니다.
- 모든 Url은 절대적 (http 또는 https 포함) 이어야 하 고 유효 해야 합니다.
- *DisplayName* 은 125 자를 초과할 수 없습니다. 
- *DisplayName*, *리소스* 및 *appdomain* 에는 다음 문자가 포함 되지 않아야 합니다. 
 
    - \<
    -  \>
    -  ;
    -  =   

배포한 추가 기능을 사용자 지정 하려는 경우에는 관리 센터에서 제거 하 고, 배포 된 각 컴퓨터에서 제거 하는 단계에 대 한 [추가 기능을 로컬 캐시에서 제거](#remove-an-add-in-from-local-cache) 를 참조 하세요.

추가 기능을 사용자 지정 하려면 *ProductId* 를 매개 변수로 사용 하 여 **OrganizationAddInOverrides** cmdlet을 실행 하 고 덮어쓸 태그와 새 값을 입력 합니다. *ProductId* 를 가져오는 방법을 알아보려면이 문서에서 [추가 기능의 세부 정보 가져오기를](#get-details-of-an-add-in) 참조 하세요. 예를 들면 다음과 같습니다.

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
추가 기능의 여러 태그를 사용자 지정 하려면 명령줄에 해당 태그를 추가 합니다.

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> 한 추가 기능에 여러 사용자 지정 태그를 하나의 명령으로 적용 해야 합니다. 태그를 하나씩 사용자 지정 하는 경우 마지막 사용자 지정만 적용 됩니다. 또한 실수로 태그를 사용자 지정 하는 경우에는 모든 사용자 지정 내용을 제거 하 고 처음부터 다시 시작 해야 합니다.

### <a name="tags-you-can-customize"></a>사용자 지정할 수 있는 태그

| Tag                  | 설명          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| 관리 센터의 추가 기능 아이콘으로 사용 되는 이미지의 URL입니다. </br> |
| \<DisplayName>| 추가 기능의 제목 (관리 센터)입니다.|
| \<호스트>| 추가 기능을 지 원하는 앱 목록입니다.|
| \<> | 추가 기능이 연결 되는 원본 URL입니다.| 
| \<Appdomain> | 추가 기능이 연결할 수 있는 도메인의 목록입니다. | 
| \<SupportURL>| 사용자가 도움말 및 지원에 액세스 하는 데 사용할 수 있는 URL입니다. | 
| \<리소스>  | 이 태그에는 다양 한 크기의 제목, 도구 설명 및 아이콘을 비롯 한 다양 한 요소가 포함 됩니다.| 
|
### <a name="customize-resources-tag"></a>Resources 태그 사용자 지정

매니페스트의 <Resources> 태그에 있는 모든 요소를 동적으로 사용자 지정할 수 있습니다. 먼저 매니페스트를 확인 하 여 새 값을 할당 하려는 요소 id를 찾아야 합니다. 태그 <Resources> 는 다음과 같습니다.

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
이 경우 이미지의 요소 id는 "img16icon" 이며 이와 연결 된 값은 "http:<i></i>/site입니다. <i> </i>com/img. "

사용자 지정할 요소를 확인 한 후 Powershell에서 다음 명령을 사용 하 여 요소에 새 값을 할당 합니다.

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

필요한 경우 명령을 사용 하 여 여러 요소를 사용자 지정할 수 있습니다.

### <a name="remove-customization-from-an-add-in"></a>추가 기능에서 사용자 지정 제거

현재 사용자 지정 항목을 삭제 하는 데 사용할 수 있는 유일한 옵션은 한 번에 모두 삭제 하는 것입니다.

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>추가 기능 사용자 지정 보기

적용 된 사용자 지정 목록을 보려면 **OrganizationAddInOverrides** cmdlet을 실행 합니다. **OrganizationAddInOverrides** 를 *ProductId* 없이 실행 한 경우에는 재정의를 적용 한 모든 추가 기능의 목록이 반환 됩니다.  

```powershell
Get-OrganizationAddInOverrides 
```
ProductId를 지정 하면 해당 추가 기능에 적용 된 재정의 목록이 반환 됩니다. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>로컬 캐시에서 추가 기능 제거

추가 기능을 배포한 경우에는 각 컴퓨터의 캐시에서 제거 해야 사용자 지정할 수 있습니다. 추가 기능의 캐시를 다시 사용 하려면 다음을 수행 합니다.

1. C:\ "사용자" 폴더로 이동 합니다. 
1. 사용자 폴더로 이동 합니다.
1. AppData\Local\Microsoft\Office로 이동 하 여 해당 버전의 Office와 연결 된 폴더를 선택 합니다.
1. *Wef* 폴더에서 *매니페스트* 폴더를 삭제 합니다.

## <a name="get-detailed-help-for-each-cmdlet"></a>각 cmdlet에 대 한 자세한 도움말 보기

Get-help cmdlet을 사용 하 여 각 cmdlet에 대 한 자세한 도움말을 확인할 수 있습니다. 예를 들어 다음 cmdlet은 OrganizationAddIn cmdlet에 대 한 자세한 정보를 제공 합니다.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


