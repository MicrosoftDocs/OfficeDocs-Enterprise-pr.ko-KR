---
title: 중앙 집중식 배포 PowerShell cmdlet을 사용하여 추가 기능 관리
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
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
description: 중앙 집중식 배포 PowerShell cmdlet을 사용 하 여 office 365 조 직 용 office 추가 기능을 배포 하 고 관리 하는 데 도움을 받을 수 있습니다.
ms.openlocfilehash: ec851fc85273e9f871c20d5075b16cb97472f975
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957639"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>중앙 집중식 배포 PowerShell cmdlet을 사용하여 추가 기능 관리

office 365 관리자는 중앙 집중식 배포 기능을 통해 사용자에 게 office 추가 기능을 배포할 수 있습니다 ( [office 365 관리 센터에서 office 추가 기능 배포](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)참조). office 365 관리 센터를 통해 office 추가 기능을 배포 하는 것 외에도 Microsoft PowerShell을 사용할 수 있습니다. [Windows PowerShell 용 O365 중앙화 된 추가 기능 배포 모듈](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)을 설치 합니다. 
    
## <a name="connect-using-your-admin-credentials"></a>관리자 자격 증명을 사용 하 여 연결

중앙 집중식 배포 cmdlet을 사용 하려면 먼저 로그인 해야 합니다.
  
1. PowerShell을 시작 합니다.
    
2. 회사 관리자 자격 증명을 사용 하 여 PowerShell에 연결 합니다. 다음 cmdlet을 실행 합니다.
    
  ```
  Connect-OrganizationAddInService
  ```

3. **자격 증명 입력** 페이지에서 Office 365 전역 관리자 자격 증명을 입력 합니다. 또는 cmdlet에 직접 자격 증명을 입력할 수 있습니다. 
    
    회사 관리자 자격 증명을 PSCredential 개체로 지정 하 여 다음 cmdlet을 실행 합니다.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)를 참조 하세요. 
  
## <a name="upload-an-add-in-manifest"></a>추가 기능 매니페스트 업로드

OrganizationAdd cmdlet을 실행 하 여 파일 위치나 URL이 될 수 있는 경로에서 추가 기능 매니페스트를 업로드 합니다. 다음 예제에서는 _ManifestPath_ 매개 변수 값에 대 한 파일 위치를 보여 줍니다. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

다음 예제와 같이 _Members_ 매개 변수를 사용 하 여 추가 기능을 업로드 하 고 사용자 또는 그룹에 직접 할당 하려면 OrganizationAdd cmdlet을 실행할 수도 있습니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Office 스토어에서 추가 기능 업로드

OrganizationAddIn cmdlet을 실행 하 여 Office 스토어에서 매니페스트를 업로드 합니다.
  
다음 예제에서는 OrganizationAddIn cmdlet은 미국 및 콘텐츠 시장의 추가 기능에 대 한 AssetId를 지정 합니다.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_AssetId_ 매개 변수의 값을 확인 하기 위해 추가 기능에 대 한 Office 스토어 웹 페이지의 URL에서이를 복사할 수 있습니다. AssetIds는 항상 "WA" 다음에 숫자를 사용 하 여 시작 합니다. 예를 들어 이전 예제에서 WA104099688의 AssetId 값에 대 한 원본은 추가 기능의 Office 스토어 웹 페이지 URL입니다 [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
_Locale_ 매개 변수와 _contentmarket_ 매개 변수의 값은 동일 하며 추가 기능을 설치 하려고 하는 국가/지역을 나타냅니다. 형식은 en-us, fr-fr입니다. 등이 있습니다. 
  
> [!NOTE]
> office 스토어에서 업로드 된 추가 기능은 office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다. 
  
## <a name="get-details-of-an-add-in"></a>추가 기능의 세부 정보 가져오기

아래와 같이 OrganizationAddIn cmdlet을 실행 하 여 테 넌 트에 업로드 된 모든 추가 기능에 대 한 세부 정보를 가져오고 추가 기능의 제품 ID를 포함 합니다.
  
```
Get-OrganizationAddIn
```

OrganizationAddIn cmdlet을 _ProductId_ 매개 변수의 값과 함께 실행 하 여 세부 정보를 검색할 추가 기능을 지정 합니다. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

할당 된 사용자 및 그룹의 모든 추가 기능에 대 한 세부 정보를 보려면 다음 예제와 같이 OrganizationAddIn cmdlet의 출력을 형식 목록 cmdlet에 파이프 합니다.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>추가 기능 설정 또는 해제

추가 기능을 해제 하 여 자신에 게 할당 된 사용자 및 그룹에 더 이상 액세스할 수 없도록 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 OrganizationAddIn cmdlet을 실행 하 고 `$false` _Enabled_ 매개 변수를로 설정 합니다.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

추가 기능을 다시 설정 하려면 _Enabled_ 매개 변수를 `$true`로 설정 하 여 동일한 cmdlet을 실행 합니다.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>추가 기능에서 사용자 추가 또는 제거

특정 추가 기능에 사용자 및 그룹을 추가 하려면 _ProductId_, _add_및 _Members_ 매개 변수를 사용 하 여 OrganizationAddInAssignments cmdlet을 실행 합니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

사용자 및 그룹을 제거 하려면 _remove_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

테 넌 트의 모든 사용자에 게 추가 기능을 할당 하려면 값이로 __ `$true`설정 된 다음 사용자 지정 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

모든 사용자에 게 추가 기능을 할당 하 고 이전에 할당 된 사용자 및 그룹으로 되돌리려면 같은 cmdlet을 실행 하 고 해당 값을로 `$false`설정 하 여 _모든 사람_ 지정 매개 변수를 해제할 수 있습니다.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>추가 기능 업데이트

매니페스트에서 추가 기능을 업데이트 하려면 다음 예제와 같이 _ProductId_, _ManifestPath_및 _Locale_ 매개 변수를 사용 하 여 OrganizationAddIn cmdlet을 실행 합니다. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> office 스토어에서 업로드 된 추가 기능은 office 스토어에서 사용할 수 있는 최신 업데이트 중 며칠 이내에 자동으로 업데이트 됩니다. 
  
## <a name="delete-an-add-in"></a>추가 기능 삭제

추가 기능을 삭제 하려면 다음 예제와 같이 _ProductId_ 매개 변수를 사용 하 여 OrganizationAddIn cmdlet을 실행 합니다. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>각 cmdlet에 대 한 자세한 도움말 보기

get-help cmdlet을 사용 하 여 각 cmdlet에 대 한 자세한 도움말을 확인할 수 있습니다. 예를 들어 다음 cmdlet은 OrganizationAddIn cmdlet에 대 한 자세한 정보를 제공 합니다.
  
```
Get-help Remove-OrganizationAddIn -Full
```


