---
title: 사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스를 사용 하지 않도록 설정
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 사용자 계정에 라이선스를 할당 하 고 Office 365 PowerShell을 사용 하 여 동시에 특정 서비스 계획을 사용 하지 않도록 설정 하는 방법에 알아봅니다.
ms.openlocfilehash: 7567d84490cdb3db7c149a51c4f2f04d39cad9ce
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스를 사용 하지 않도록 설정

**요약:**  사용자 계정에 라이선스를 할당 하 고 Office 365 PowerShell을 사용 하 여 동시에 특정 서비스 계획을 사용 하지 않도록 설정 하는 방법에 알아봅니다.
  
Office 365 구독 개별 서비스에 대 한 서비스 계획 함께 제공 됩니다. Office 365 관리자는 종종 사용자에 게 라이선스를 할당 하는 경우 특정 계획을 사용 하지 않도록 설정 해야 합니다. 이 문서의 지침을 개별 사용자 계정 또는 여러 사용자 계정에 대 한 PowerShell을 사용 하 여 특정 서비스 계획을 사용 하지 않도록 설정 하는 동안 Office 365 라이선스를 할당할 수 있습니다.
  
## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>구독 및 서비스 계획 하는 방법에 대 한 정보 수집

현재 구독을 참조 하려면이 명령을 실행 합니다.
  
```
Get-MsolAccountSku
```

표시에서 된 `Get-MsolAccountSku` 명령 합니다.
  
- **AccountSkuId** 은에서 조직에 대 한 구독 \<OrganizationName >:\<구독 > 형식입니다. \<OrganizationName > Office 365에 등록 하 고 조직에 대 한 고유함 때 제공한 값입니다. \<구독 > 값은 특정 구독에 사용 됩니다. 예, litwareinc:ENTERPRISEPACK에 대 한 조직 이름은 litwareinc, 하 고 구독 이름은 ENTERPRISEPACK (Office 365 Enterprise E3)입니다.
    
- **ActiveUnits** 는 구독에 대 한 구입한 라이선스의 수입니다.
    
- **WarningUnits** 는 하면 하지 않은 갱신 되 고 30 일의 유예 기간 후 만료 되는 구독에서 라이선스의 수입니다.
    
- **ConsumedUnits** 는 구독에 대 한 사용자에 게 할당 했을 때 라이선스의 수입니다.
    
라이선스 할당 하려는 사용자를 포함 하는 Office 365 구독에 대 한 AccountSkuId note 합니다. 또한 충분 한 라이선스를 할당 되었는지 확인 ( **ActiveUnits** 에서 **ConsumedUnits** 빼기).
  
이 명령은 모든 구독에서 사용할 수 있는 Office 365 서비스 계획에 대 한 자세한 내용을 보려면 다음을 실행 합니다.
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

이 명령의 디스플레이에서 사용자에 게 라이선스를 할당 하는 경우 사용 하지 않도록 설정 하려면 어떤 서비스 계획을 결정 합니다.
  
다음은 서비스 계획 및 해당가 Office 365 서비스의 일부 목록입니다.
  
|**서비스 계획**|**설명**|
|:-----|:-----|
|영향  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Office 365의 모바일 장치 관리  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |RMS(Azure 권한 관리)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office Professional Plus  <br/> |
|MCOSTANDARD  <br/> |비즈니스용 Skype 온라인  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Exchange Online 계획 2  <br/> |
   
만들었으므로 이제는 AccountSkuId 및 사용 하지 않으려면 서비스 계획, 라이선스에 대 한 개별 사용자 또는 여러 사용자에 게 할당할 수 있습니다.
  
## <a name="for-a-single-user"></a>단일 사용자에 대 한

단일 사용자에 대 한 사용자 계정, AccountSkuId, 및 서비스 계획의 목록을 사용 하지 않도록 설정 하 고 설명 텍스트를 제거 하려면 사용자 계정 이름에 입력 및 \< 및 > 문자입니다. 다음, PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

Belindan@contoso.com, contoso:ENTERPRISEPACK 라이선스에 대 한 명명 된 계정에 대 한 예제 명령 블록 되며 서비스 계획 사용 하지 않도록 설정 하는 RMS_S_ENTERPRISE, 영향, INTUNE_O365, 및 YAMMER_ENTERPRISE 여기:
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a>여러 사용자에 대 한

여러 사용자에 대 한이 관리 작업을 수행 하려면 UserPrincipalName 및 usagelocation이 필드를 포함 하는 쉼표로 구분 된 값 (CSV) 텍스트 파일을 만듭니다. 다음은 한 예가입니다.
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

다음으로 입력 및 출력 CSV 파일, SKU ID 계정 및 서비스 계획을 사용 하지 않으려면 목록이의 위치를 입력 하 고 명령을 입력 하 고 결과 PowerShell 명령 프롬프트에서.
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

이 PowerShell 명령 차단 합니다.
  
- 각 사용자의 사용자 계정 이름을 표시합니다.
    
- 각 사용자에 게 라이선스를 사용자 지정 하는 할당 합니다.
    
- 처리 된 모든 사용자와 CSV 파일을 만들고의 라이선스 상태를 표시 합니다.
    
## <a name="see-also"></a>참고 항목

[Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다.](disable-access-to-services-with-office-365-powershell.md)
  
[Office 365 powershell 영향에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-sway-with-office-365-powershell.md)
  
[사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)

