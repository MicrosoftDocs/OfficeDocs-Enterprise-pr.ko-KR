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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 배포 PowerShell 중앙 집중화 cmdlet를 사용 하 여 배포 하 고 Office 365 조직에 대 한 Office 추가 기능을 관리 하는 데 도움이 됩니다.
ms.openlocfilehash: 6199ad2d37a11166155b898b52d52304836599d0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542154"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>중앙 집중화 배포 PowerShell cmdlet을 사용 하 여 추가 기능 관리

Office 365 관리자로 중앙 집중화 배포를 통해 사용자에 게 Office 추가 기능을 배포할 수 있습니다 ( [Office 365 관리 센터에서 배포 Office 추가 기능](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)을 참조)는 기능입니다. Office 365 관리 센터를 통해 Office 추가 기능을 배포 하는 것 외에도 Microsoft PowerShell를 사용할 수 있습니다. [다운로드](https://go.microsoft.com/fwlink/p/?linkid=850850) 는 Microsoft 다운로드 센터에서 배포 PowerShell 중앙 집중화 cmdlet입니다. 
    
## <a name="connect-using-your-admin-credentials"></a>관리 자격 증명을 사용 하 여 연결

배포에 집중 cmdlet를 사용 하려면 먼저에 로그인 해야 합니다.
  
1. PowerShell을 시작 합니다.
    
2. 회사 관리자 자격 증명을 사용 하 여 PowerShell에 연결 합니다. 다음 cmdlet을 실행 합니다.
    
  ```
  Connect-OrganizationAddInService
  ```

3. **자격 증명 입력** 페이지에서 Office 365 전역 관리자 자격 증명을 입력 합니다. 또는 cmdlet에 직접 자격 증명을 입력할 수 있습니다. 
    
    PSCredential 개체를으로 회사를 지정 하는 다음 cmdlet 관리 자격 증명을 실행 합니다.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Office 365 PowerShell 연결](https://go.microsoft.com/fwlink/p/?linkid=848585)을 참조 하십시오. 
  
## <a name="upload-an-add-in-manifest"></a>프로그램 추가 기능에서 매니페스트를 업로드 합니다.

프로그램 추가 기능에서 매니페스트 파일 위치 또는 URL 될 수 있는 경로에서 업로드 새로 만들기-OrganizationAdd-에 cmdlet을 실행 합니다. 다음 예제에서는 _ManifestPath_ 매개 변수의 값에 대 한 파일 위치를 표시합니다. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

추가 기능을 업로드 하 고 할당 사용자 또는 그룹에 직접 _구성원_ 매개 변수를 사용 하 여 다음 예제와 같이를 새로 만들기-OrganizationAdd-에 cmdlet을 실행할 수도 있습니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Office 스토어에서 추가 기능을 업로드합니다

Office 스토어에서 매니페스트를 업로드 하려면 새로 만들기 OrganizationAddIn cmdlet을 실행 합니다.
  
다음 예제에서는 새 OrganizationAddIn cmdlet은 미국, 대한민국 위치 및 콘텐츠 시장 용으로 추가 기능에 대 한 AssetId를 지정합니다.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_AssetId_ 매개 변수의 값을 확인 하려면 숫자 앞에 오는 "WA"를 사용 하 여 추가 기능 AssetIds에 대 한 웹 페이지는 항상 시작 Office 저장소의 URL에서 복사할 수 있습니다. 예, 앞의 예제에서는 소스 WA104099688 AssetId 값에 대 한는 추가 기능에 대 한 Office 스토어 웹 페이지 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)합니다.
  
_Locale_ 매개 변수 및 _ContentMarket_ 매개 변수 값은 동일 하 고 국가/지역에서 추가 기능을 설치 하려는 나타냅니다. 형식은은 EN-US, fr-fr. 등입니다. 
  
> [!NOTE]
> Office 스토어에서 업로드 한 추가 기능 Office 스토어에서 사용할 수 있는 것은 최신 업데이트의 경우 다음과 같은 며칠 내에서 자동으로 업데이트 됩니다. 
  
## <a name="get-details-of-an-add-in"></a>추가 기능에 대 한 정보를 봅니다.

아래와 같이 Get OrganizationAddIn cmdlet을 실행 하는 테 넌 트에 업로드 된 모든 추가 기능에 대 한 세부 정보를 가져올 포함 된 추가 기능에서 제품 id입니다.
  
```
Get-OrganizationAddIn
```

지정 하는 추가 기능에 대 한 세부 정보를 검색 하려는 _ProductId_ 매개 변수의 값을 가진 Get OrganizationAddIn cmdlet을 실행 합니다. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

모든 추가 기능 및 할당 된 사용자 및 그룹의 전체 세부 정보를 얻으려면 다음 예제와 같이 Format-list cmdlet에 Get OrganizationAddIn cmdlet의 출력을 파이프 합니다.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>켜기 또는의 프로그램 추가 기능을 해제합니다

를 해제 하려면 추가 기능에서 사용자 및 그룹에 할당 된 액세스 권한이 더이상 되므로 _ProductId_ 매개 변수 및로 설정 하는 _Enabled_ 매개 변수 집합 OrganizationAddIn cmdlet을 실행 `$false`다음 예제와 같이, 합니다.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

추가 기능을 다시 설정 하려면로 설정 하는 _Enabled_ 매개 변수와 함께 동일한 cmdlet을 실행 `$true`합니다.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>추가 또는 추가 기능에서 사용자를 제거 합니다.

추가 기능에 특정 사용자 및 그룹을 추가, _제품 Id_, _추가_및 _구성원_ 매개 변수와 함께 집합 OrganizationAddInAssignments cmdlet을 실행 합니다. 구성원의 전자 메일 주소를 쉼표로 구분 합니다. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

사용자 및 그룹을 제거 하려면 _제거_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 합니다. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

추가 기능에서 테 넌 트에 있는 모든 사용자에 할당 하려면 값으로 설정 된 _AssignToEveryone_ 매개 변수를 사용 하 여 동일한 cmdlet을 실행 `$true`합니다.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

모든 사용자에 게 추가 기능을 할당 하 고 이전에 할당 된 사용자 및 그룹으로 되돌리려면 하지,를 동일한 cmdlet을 실행 및 해당 값 설정 하 여 _AssignToEveryone_ 매개 변수를 해제 수 `$false`합니다.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>추가 기능을 업데이트 합니다.

매니페스트에서 추가 기능을 업데이트 하려면 다음 예제와 같이 _ProductId_, _ManifestPath_및 _로캘_ 매개 변수를 사용 하 여 집합 OrganizationAddIn cmdlet을 실행 합니다. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Office 스토어에서 업로드 한 추가 기능 Office 스토어에서 사용할 수 있는 것은 최신 업데이트의 경우 다음과 같은 며칠 내에서 자동으로 업데이트 됩니다. 
  
## <a name="delete-an-add-in"></a>추가 기능을 삭제 합니다.

추가 기능을 삭제 하려면 다음 예제와 같이 _ProductId_ 매개 변수와 함께 제거 OrganizationAddIn cmdlet을 실행 합니다. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>각 cmdlet에 대 한 자세한 도움말을 보려면

Get-help cmdlet을 사용 하 여 각 cmdlet에 대 한 자세한 도움말을 살펴볼 수 있습니다. 예, 다음 cmdlet 제거 OrganizationAddIn cmdlet에 대 한 자세한 정보를 제공 합니다.
  
```
Get-help Remove-OrganizationAddIn -Full
```


