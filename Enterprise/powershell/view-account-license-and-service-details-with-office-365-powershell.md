---
title: Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
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
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기

**요약:** Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 설명 합니다.
  
Office 365에서 라이선스를 제공 계획 라이선스를 (또한 호출된 Sku 또는 Office 365 계획) 사용자가 이러한 계획에 대해 정의 된 Office 365 서비스에 액세스 권한을 부여 합니다. 그러나 사용자 자신에 게 현재 할당 된 라이선스에서 사용할 수 있는 모든 서비스에 대 한 액세스를 권한이 없는 합니다. Office 365 PowerShell을 사용 하 여 사용자 계정에서 서비스의 상태를 보려면 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에
<a name="RTT"> </a>

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- 명령을 사용 하 여 `Get-MsolAccountSku` 및 `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` 다음 정보를 찾을 수 있습니다.
    
  - 조직에서 사용할 수 있는 라이선스 계획.
    
  - 각 라이선스 계획에서 사용할 수 있는 서비스 및 서비스 나열 순서(인덱스 번호).
    
     계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.
    
- 명령을 사용 하 여 `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` (인덱스 번호)를 나열 된 자신이 하는 사용자 및 순서에 할당 된 라이선스를 찾을 수 있습니다.
    
- 사용 하는 경우는 **Get-MsolUser** cmdlet을 사용 하지 않고는 _All_ 매개 변수를 처음 500 개의 계정만 반환 됩니다.
    
<a name="ShortVersion"> </a>
## <a name="the-short-version-instructions-without-explanations"></a>간략 한 (설명 없이 지침)

사용자에 액세스할 수 있는 모든 Office 365 PowerShell 서비스를 보려면 다음 구문을 사용 합니다.
  
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

특정 서비스를 사용하거나 사용하지 않도록 허가된 모든 사용자를 찾으려면 다음 구문을 사용합니다.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

이러한 예제는 다음 정보를 사용합니다.
  
- 관심 있는 우리가 하는 Office 365 서비스에 대 한 액세스를 제공 하는 라이선스는 (의 인덱스 번호는 0) 하는 모든 사용자에 게 할당 된 첫번째 라이선스입니다.
    
- 관심 있는 우리는 Office 365 서비스를 Skype 비즈니스 온라인 및 Exchange Online에 대 한 됩니다. 라이선스 계획 연관 된 라이선스에 대 한 온라인 비즈니스에 대 한 Skype는 나열 된 6 서비스 (인덱스 번호는 5), Exchange Online은 9 서비스 및 (인덱스 번호는 8) 나열 합니다.
    
이 예제에서는 비즈니스 온라인 및 Exchange Online에 대 한 Skype에 대해 사용할 수 있는 모든 사용이 허가 된 사용자를 반환 합니다.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Skype 비즈니스 온라인 또는 Exchange Online에 대 한 사용 하도록 설정 되지 않은 모든 사용이 허가 된 사용자를 반환 하는이 예제입니다.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<a name="LongVersion"> </a>
## <a name="the-long-version-instructions-with-detailed-explanations"></a>긴 버전 (명령에 대 한 세부 정보)

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>사용자에 액세스할 수 있는 Office 365 PowerShell 서비스 찾기

가 분명 어떤 사용자가 Office 365 라이선스 발급 하 고 있는 사용자 하지 않은 알 수 있습니다. (자세한 내용은 [Office 365 powershell 사용이 허가 된 및 허가 되지 않은 사용자를 보려면](view-licensed-and-unlicensed-users-with-office-365-powershell.md) 문서 참조). 그러나 단순히 Office 365 라이선스를 가진 알 수 없는 아무것도 해당 사용자 수행할 수 있는 실제로 Office 365를 사용 하는 방법에 대 한 합니다. 수가 자신이 사용 하 여 Exchange Online 또는 Skype 온라인 비즈니스에 대 한? 이 사용자 SharePoint Online 액세스할 수 있습니까? 가 자신이 않은 Office Professional Plus에 액세스할 수 있습니까? 사용자가 이러한 서비스에 액세스할 가능성이 의미 단순히는 라이선스가 필요 합니다. 그러나 사용자에 게 사용할 수 있는 기능이 자신의 라이선스에서 사용할 수 있는 서비스에 따라 달라 집니다.
  
어떻게 확인할 수 있는 Office 365 기능을 사용자가 액세스할 수 있습니까? 이 하나에 다음과 비슷한 명령을 실행 해야할 사항은 다음과 같습니다.
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

이 명령은 BelindaN@litwareinc.com 계정에 대 한 정보를 반환 하려면 **Get-msoluser** cmdlet를 사용 합니다. 해당 정보를 반환한 후에, 되 면 다음 계정 데이터를 **Select-object** cmdlet에 파이프 하 고는 **Select-object** **라이선스** 속성의 값을 "확장" 하 게 합니다.
  
 `Select-Object -ExpandProperty Licenses`
  
왜 이렇게 할까요? 물론 **라이선스** 기본적으로 속성은 알려줍니다에서 Belinda 라이선스를 획득 한 라이선스 팩의 이름:
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

**라이선스** 속성을 "확장" 하면 더 많은 정보를 제공 합니다.
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

및 다음 **ServiceStatus** 속성을 확장 하 여을 얻을 수 더 많은 정보:
  
|서비스 계획 * * *|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |RMS(Azure 권한 관리)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |비즈니스용 Skype 온라인  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 계획 2  <br/> |
   
> [!NOTE]
> 너무 많은 입력 하는 것이를 알고 계십니까? 물론을 이해할 수 애매 한 Windows PowerShell을 하는 경우 대신 실행할 수 있습니다는 명령의 압축 된 버전: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
궁금할 경우에 수 "확장" **라이선스** 속성은 **라이선스** 는 다중값된 속성 때문에:은 여러 값을 저장할 수 있는 단일 속성입니다. 단순히 드릴 다운 하 여 속성 값을 확장 하 고는 결과가에서 이러한 추가 되는 값을 기본적으로 표시 되지 않습니다 화면에 표시 합니다.
  
> [!NOTE]
> 값이 다중값된 속성 인지를 알고 있는 어떻게 가정해는? 물론 사실을 확인 하려면 다음과 같은 명령을 실행 하를 시도: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> **get-member** cmdlet은 자체; 개체에 대 한 정보를 반환 합니다. 이 경우에 속성에 대 한 정보는 사용자 계정 개체를 구성 하는 값입니다. **라이선스** 속성에 대 한 말을 **Get-member** 다음과 같습니다: > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> 속성 정의 컬렉션에 대 한 자료 된다고 표시 되 면 (이 경우 `System.Collections.Generic.List`) 다중값된 속성을 사용 해야하는 경우 알고 있어야 합니다. 
  
따라서이 모든 의미 합니까? 답변을 먼저 살펴보겠습니다 다른 **Get-msoluser** cmdlet에 의해 반환 되는 정보:
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

한 보겠습니다 또한 이러한 이상한 이름의 서비스 계획이 실제로 나타내는 설명 하는 테이블에 대 한 정보를 수행 합니다.
  
|서비스 계획 * * *|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |RMS(Azure 권한 관리)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |비즈니스용 Skype 온라인  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 계획 2  <br/> |
   
모든 확실히 이해 하셨나요?  `MCOSTANDARD` 은 Skype에 대 한 내부 프로그래밍 이름을 방금 온라인 비즈니스에 대 한 동안 `OFFICESUSBCRIPTION` Office Professional Plus에 대 한 내부 프로그래밍 이름 뿐입니다. 분야에서 가장 직관적인 것 없는 하지만이 표 간편 하 게 유지으로 필요가 많은 문제를 사용할 때 Office 365 서비스 사용 (영문).
  
리더에 게: 아니 군요. **ProvisioningStatus** 로 설정 된 경우에 문서를 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)갸우뚱 처럼 `Success` 는 서비스 완벽 하 게 활성화 되었는지, 즉 예 하는 경우 `MCOSTANDARD` 로 설정 된 `Success` 즉, 사용자가 온라인 비즈니스에 대 한 Skype를 액세스할 수 있습니다. **ProvisioningStatus** 로 설정 된 경우 `PendingInput` 즉, Office 365 서비스 요청을 처리 하 고 계속 그러나 사용자 수 일반적으로 로그온 하 고 요청 처리를 완료 하는 동안 서비스에 액세스 합니다. ( `YAMMER_ENTERPRISE` 항상 같이 표시 됩니다. `PendingInput`, 상관 없습니다: 하는 Yammer에 로그온 한 사용자 중지 되지 않음).
  
> [!IMPORTANT]
> 사용자가 설치 및 활성화 하는 동안 사용 되는 새로운 Office Professional Plus 설치 수 `OFFICESUBSCRIPTION` 에 `PendingInput` 상태입니다.
  
이며, 관리할 수 있어야 하는 서비스로 설정 되어 `Disabled` 는 해당 서비스에는 사용자에 게 사용할 수 없다는 것을 의미 합니다.
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>특정 Office 365 PowerShell 서비스에 액세스할 수 있는 사용자 찾기

별도 문서에서는 Office 365 PowerShell을 사용 하 여 서비스에 대 한 사용자 액세스를 사용 하지 않도록 설정 하는 방법을 살펴보았습니다. (해당 문서, 누락 된 경우 참조 [Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-services-with-office-365-powershell.md)) 합니다. 그렇다면 대체 발생 하는: 인스턴스가 있는 *사용자* 를 결정 하는 방법이 있습니다 (즉, 둘 이상의 사용자)가 사용 하거나 사용 하지 않도록 설정 하는 서비스?
  
요청은 다른 사용자 굴뚝 된 것입니다. 그 대답 하기 위해 먼저 살펴보았습니다 문서 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스에](view-licenses-and-services-with-office-365-powershell.md) 에서만 사용할 수 있는 현재 라이선스 계획에 대 한 서비스의 표를 검토 보겠습니다 `litwareinc:ENTERPRISEPACK`:
  
|서비스 계획 * * *|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |RMS(Azure 권한 관리)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |비즈니스용 Skype 온라인  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 계획 2  <br/> |
   
서비스 계획은 제품;에 대 한 내부 프로그래밍 이름에 마찬가지 기억할 것 처럼 예, `OFFICESUBSCRIPTION`, 하나의 이름을,은 Office Professional Plus에 대 한 내부 프로그래밍 이름입니다. 하는 경우 `OFFICESUBSCRIPTION` 변수로 나타나는데 `SUCCESS` 사용자의 서비스 계획에 다음 즉, 사용자가 Office Professional Plus에 액세스할 수 있습니다. 하는 경우 `EXCHANGE_S_ENTERPRISE` 으로 나열 되어있는지 `DISABLED` 즉, 사용자를 Exchange Online 사용할 수 없습니다.
  
> [!IMPORTANT]
> 사용자가 설치 및 활성화 하는 동안 사용 되는 새로운 Office Professional Plus 설치 수 `OFFICESUBSCRIPTION` 에 `PendingInput` 상태입니다.
  
이제는 서비스에 표시 하는 순서는 매우 중요 시간입니다. Windows PowerShell 목록에서 각 항목에는 인덱스 번호를 할당합니다. 첫번째 항목은 0으로, 다음 항목은 1 등입니다. 결과 다음 표에서 설명 합니다.
  
|인덱스 번호 * * *|서비스 계획 * * *|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
볼 수 있듯이 `SWAY` 는 첫번째 서비스 나열 된 인덱스 번호 0을 할당을 가져옵니다.
  
> [!CAUTION]
> 이유 0과 1 하지? 이것은 프로그래밍 것입니다. 프로그래밍 언어에서 인덱스가 안내 얼마나 항목은 ""에서 오프셋 배열의 시작 합니다. 첫번째 항목은 *은* 해당 offset이 0 되므로 배열의 시작 부분입니다. 두번째 항목은 배열의 시작 부분에서 1 개 항목 이므로 해당 오프셋은 1.
  
예를 보겠습니다. Exchange Online에 대해 활성화 되지 않은 모든 사용이 허가 된 사용자의 목록 같은 경우를 가정해 보겠습니다. 다음 명령을 사용할 수 있는, 사항은 다음과 같습니다.
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

그러나 이것은 필요에 따라 복잡을 찾고 거의 명령 보겠습니다 작동 하는 방법에 대해 설명 하는 분 걸릴입니다. 이것은 실제로 두 부분으로 구성 명령 및 앞부분은 매우 간단: 모든 Office 365 사용자의 컬렉션을 반환 하려면 **Get-msoluser** cmdlet을 사용 하면 했습니다 (사용이 허가 된 및 허가 되지 않은):
  
```
Get-MsolUser
```

해당 정보는 **Where-object** cmdlet에 파이프 됩니다. **Where-object** 모든 사용자 계정을 통해 이동 하 고 다음 조건이 모두 충족 하는 이러한 계정을:
  
- **IsLicensed** 속성이 같음 ( `-eq`) `True` ( `$true`). 이렇게 하면 허가 되지 않은 사용자가 걸러내기 하 게 합니다.
    
- **라이선스 [0]의 값입니다. ServiceStatus [8]입니다. ProvisioningStatus** 속성이 같음 ( `-eq`) `Disabled`합니다. 즉시이 목적을 위해이 다루기가 속성 이름의 중요 한 부분 입니까:
    
     `ServiceStatus[8]`
    
    `[8]` Exchange Online에 대 한 인덱스 번호를 나타냅니다. (많음을 알고 에서만 몇분 이내 테이블을 보면). 비즈니스 Online 용 Skype에 대해 활성화 된 모든 사용자를 찾으려면 어떻게 해야 할까요? 물론 비즈니스 온라인 용 Skype에 대 한 인덱스 번호 이므로 5,이 구문을 사용 하면:
    
     `ServiceStatus[5]`
    
    이러한 식으로 적용됩니다.
    
    참고로, `Licenses[0]` 살펴보는 원합니다 라이선스 계획을 나타냅니다. 이 테스트 도메인만 하나의 라이선스 계획을 갖기 때문이 훨씬 문제가 되지 않습니다. 하지만 사용자가 서로 다른 두 라이선스 계획에서 라이선스를 할당 된가 였습니다 경우를 가정해 보겠습니다. 이 경우 `Licenses[0]` 첫번째 라이선스 계획은 나타냅니다 및 `Licenses[1]` 두번째 라이선스 계획을 표시 합니다.
    
    다음 명령을 실행하여 사용자에게 할당된 라이선스 및 나열 순서를 찾을 수 있습니다.
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

이 모든 것이 작동 하는 방법이 된 것을 볼 수 있습니다. Office Professional Plus의 인덱스 번호는 4; 따라서이 명령은 Office Professional Plus에 대해 활성화 되지 않은 모든 사용자의 목록을 반환 합니다.
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

및 Office Professional Plus에 대해 *활성화* 를 받은 사용자가 목록이 경우에 어떻게 할까요? 음, 프로그램 **ServiceStatus** 갖게 됩니다 다음 활성화 된 했을 때 경우 `PendingInput` 또는 `Success`; 즉, **servicestatus에 포함 된** 사용자 *같지* ( `-ne`) `Disabled`합니다. 즉, 이전 명령에서는 걸리고 아웃 스왑가 하기만 하면 모든는 `-eq` 에 대 한 연산자는 `-ne` 연산자:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

되었다는로 전환 되 면는 코드 싶은 않습니다 win 많은 장점은 컨 합니다. 및 사실 필요 하다는 메시지가, 코드를 더 많은 얻을 수 혼란 합니다. 예, 비즈니스 온라인 및 Exchange Online에 대 한 두 Skype에 대해 활성화 된 사용자를 확인 하려고 있다고 가정 합니다.
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

하지 않는다면 하지만 어떻게 gnarly 있는 형태에 대해 알아봅니다 하는 방법에 대 한 너무 많은: 중요 한 점은, 비교적 적은 노력이이 정보 검색할 수 있습니다. Office 365 관리 센터를 사용 하 여이 같은 정보를 가져올 수 없습니다. Yes 하지만,에서 이론적에서 실질적, no입니다. Office 365 관리 센터를 사용 하 여이 동일한 정보에서를 각 사용자에 대 한 라이선스 정보에서 한번에 한 명의 사용자를 확인 하 고 다음 수동으로 추적할 *X* 에 대해 활성화 되어 있던 사용자 및 사용자가 않았다면 필요가 것입니다. 작동을 제외 하면 솔직히: 10 또는 11 개 이상의 사용자가이 작업을 수행 하려는 하지 않습니다. 이것이 너무 방대 하 고 시간이 많이 걸리는입니다.
  
물론는 Windows PowerShell가 제공 하는 이유: 하는 등의 방대 하 고 시간이 많이 걸리는 작업에서 Windows PowerShell 하면 저장 하는데 도움이 됩니다.
  
Office 365 E5 구독에 대 한 해당 라이선스 및 servicestatus에 포함 된 색인으로 식별 되는 지정 된 서비스 집합에 대 한 서비스 정보를 보기 위한 명령의 예는 다음과 같습니다.
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

이 명령은 모든 사용자 및 서비스 (팀, Yammer, AD RMS, OfficePro, Skype, SharePoint, 및 Exchange)의 지정된 된 집합에 대 한 해당 서비스 상태를 보여주는 CSV 파일을 만듭니다.

>[!Note]
>서비스 목록에서 구독에서 얻을 수 있습니다는 `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` 명령 합니다. 출력을 0이 들어 있는 서비스 인덱스 번호 매기기 시작 합니다. 위 명령은 단지 예를 합니다. 시간에 따른 서비스에 대 한 인덱스 번호를 변경할 수 있습니다.
>

  
<a name="SeeAlso"> </a>
## <a name="see-also"></a>참고 항목

Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.
  
- [Office 365 PowerShell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
- [삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [블록 사용자 계정 Office 365 PowerShell을 사용 하 여](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [ConvertTo Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [형식 목록](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [선택 개체](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Office 365의 새로운 기능


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]