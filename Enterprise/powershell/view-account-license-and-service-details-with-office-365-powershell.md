---
title: Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 설명 합니다.
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213955"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기

**요약:** Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 설명 합니다.
  
Office 365에서 라이선스를 제공 계획 라이선스를 (또한 호출된 Sku 또는 Office 365 계획) 사용자가 이러한 계획에 대해 정의 된 Office 365 서비스에 액세스 권한을 부여 합니다. 그러나 사용자 자신에 게 현재 할당 된 라이선스에서 사용할 수 있는 모든 서비스에 대 한 액세스를 권한이 없는 합니다. Office 365 PowerShell을 사용 하 여 사용자 계정에서 서비스의 상태를 보려면 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- 명령을 사용 하 여 `Get-MsolAccountSku` 및 `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` 다음 정보를 찾을 수 있습니다.
    
  - 조직에서 사용할 수 있는 라이선스 계획.
    
  - 각 라이선스 계획에서 사용할 수 있는 서비스 및 서비스 나열 순서(인덱스 번호).
    
     계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.
    
- 명령을 사용 하 여 `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` (인덱스 번호)를 나열 된 자신이 하는 사용자 및 순서에 할당 된 라이선스를 찾을 수 있습니다.
    
- 사용 하는 경우는 **Get-MsolUser** cmdlet을 사용 하지 않고는 _All_ 매개 변수를 처음 500 개의 계정만 반환 됩니다.
    

## <a name="to-view-services-for-a-user-account"></a>사용자 계정에 대 한 서비스를 보려면

사용자에 액세스할 수 있는 모든 Office 365 서비스를 보려면 다음 구문을 사용 합니다.
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

이 예제에서는 BelindaN@litwareinc.com 사용자가 액세스할 수 있는 서비스입니다. 이 사용자 계정에 할당 된 모든 라이선스와 연결 된 서비스를 보여줍니다.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

이 예제에서는 사용자 BelindaN@litwareinc.com이 계정에 할당된 첫 번째 라이선스(인덱스 번호: 0)에서 액세스할 수 있는 서비스를 표시합니다.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

*여러 라이선스*할당 된 사용자에 대 한 모든 서비스를 보려면 다음 구문을 사용 합니다.

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>참고 항목

Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.
  
- [Office 365 PowerShell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
- [삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [블록 사용자 계정 Office 365 PowerShell을 사용 하 여](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [ConvertTo Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [선택 개체](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Office 365의 새로운 기능


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]