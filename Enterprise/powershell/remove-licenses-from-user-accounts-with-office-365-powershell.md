---
title: "Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다."
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Office 365 PowerShell을 사용 하 여 사용자에 게 이전에 할당 된 Office 365 라이선스를 제거 하는 방법에 설명 합니다."
ms.openlocfilehash: c02d5a6cac029ce9beb8077da98418734d935ded
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.

**요약:** Office 365 PowerShell을 사용 하 여 사용자에 게 이전에 할당 된 Office 365 라이선스를 제거 하는 방법에 설명 합니다.
  
## <a name="before-you-begin"></a>시작하기 전에

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- 조직에서 라이선스 계획 ( **AccountSkuID** ) 정보를 보려면 다음 항목을 참조 합니다.
    
  - [라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기](view-account-license-and-service-details-with-office-365-powershell.md)
    
- _-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.
    
## <a name="the-short-version-instructions-without-explanations"></a>간략 한 (설명 없이 지침)
<a name="ShortVersion"> </a>

이 여기서도 바라지 나 불필요 한 설명을 하지 않고 절차를 제공합니다. 질문이 있거나 자세한 내용을 확인 하려면 해당 항목의 나머지 부분을 읽을 수 있습니다.
  
기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` BelindaN@litwareinc.com 사용자 계정에서 라이선스를 (Office 365 Enterprise E3).
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

기존 사용이 허가 된 사용자 그룹에서 라이센스를 제거 하려면 다음 방법 중 하나를 사용.
  
- **기존 계정 특성을 기준으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

제거 하는이 예제는 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) 모든 accounts에서 사용자를 위한 라이선스 미국에서 Sales 부서에 있습니다.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **특정 계정 목록 사용** 이 작업을 수행 하려면 다음 단계를 수행 합니다.
    
1. 만들고 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 저장 합니다.
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 다음 구문을 사용합니다.
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` C:\My Documents\Accounts.txt 텍스트 파일에 정의 된 사용자 계정에서 라이선스를 (Office 365 Enterprise E3).
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

모든 기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` 에서 모든 기존 (Office 365 Enterprise E3) 라이선스 사용이 허가 된 사용자 계정입니다.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>긴 버전 (명령에 대 한 세부 정보)
<a name="LongVersion"> </a>

Nothing으로, 지속 되 고 Office 365 라이선스를 포함 하는: 일찍 또는 늦게 올 것 시간 사용자 계정에서 라이선스를 제거 해야 합니다. 엔터프라이즈 무선 전화 통신 사용자 나가기; 것 엔터프라이즈 무선 전화 통신 사용자가 더 이상는 운영 체제 버전; 위의-물론 있는데 분명 임의 개수의 사용자 라이선스를 제거 하는 이유는 이유
  
들어가기 전에 추가 된 잘 하는데 필요 라이선스를 제거 하는 것이 중요 것, 라이선스를 제거: 라이선스 제거와 동일한 작업 없는 라이선스에서 모든 서비스를 사용 하지 않도록 설정 합니다. 예에서는 모든 Office 365 라이선스;를 사용 한다고 가정 즉, 우리는 사용할 수 있는 한 어떠한 라이선스를 제공 합니다. 사용 하지 않으려면 모든 서비스 라고 표시, Belinda Newman의 계정에서 [Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-services-with-office-365-powershell.md) 의 절차를 수행 하기로 결정 합니다. 얼마나 많은 라이선스를 제공 하는 것이 할까요는 갖습니다를 보면 사용 가능한? 이와: 0입니다. 예, 해당 항목의 절차를 *사용 하지 않도록 설정* Belinda 라이선스에는 서비스는 모두 하지만 해제 하지 것입니다 (즉, 삭제) 자체 라이선스입니다. 라이선스 계속 유효 수 있으며 여전히 Belinda Newman에 게 할당 됩니다. 대화 상대가 방금 수 없습니다를 사용 하 여 해당 라이선스 모든 Office 365 서비스에 액세스 합니다.
  
중요 한 이며: 사용자에 게 서 라이선스를 제거 하려는 경우 실제로 *제거* 를 라이선스을 수행 해야 합니다. 모든 서비스 하지 않도록 설정 된 사용자 로그온 하는 Office 365에서에서 있지만 자신의 라이선스 확보 되지 않습니다. 현재이 1 이면 _RemoveLicenses_ 매개 변수를 사용 하 여 실제로 Belinda에 이전에 할당 된 라이선스를 제거 하는 명령은 다음과 비슷한 명령을 실행 해야 사용자에 게 할당 된 라이선스를 회수 하려면:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

해당 명령을 실행 하 고 Belinda Newman Office 365를 사용 하 여 라이선스 더이상 됩니다.
  
> [!NOTE]
> 볼 수 있듯이, 제거할 라이선스의 이름을 지정 하면 _RemoveLicenses_ 매개 변수를 사용 합니다. 확실 하지 않은 경우 다음과 같은 명령을 실행 하는 사용자에 게 라이선스를 할당 하는 라이선스 계획 사용 되었습니다.`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
라이선스가 실제로 제거되었는지 확인하려면 Get-MsolUser를 사용하여 문제의 사용자 계정을 확인합니다.
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

모든 계획을 제공 하기 위해,으로 Belinda의 **isLicensed** 속성 설정 이제 됩니다 `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

사용자 계정을 삭제 하 여 라이선스를 확보 하는 다른 방법은 됩니다. 자세한 내용은 [삭제 하 고 사용자 계정을 Office 365 powershell 복원](delete-and-restore-user-accounts-with-office-365-powershell.md)을 참조 하십시오.
  
## <a name="see-also"></a>참고 항목

Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.
  
- [Office 365 PowerShell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
- [삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [블록 사용자 계정 Office 365 PowerShell을 사용 하 여](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Office 365의 새로운 기능

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

