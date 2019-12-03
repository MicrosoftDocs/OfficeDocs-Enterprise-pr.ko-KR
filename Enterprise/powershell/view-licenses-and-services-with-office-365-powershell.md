---
title: 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Office 365 PowerShell을 사용 하 여 Office 365 조직에서 사용할 수 있는 라이선스 계획, 서비스 및 라이선스에 대 한 정보를 확인 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: b8a0bb1845f3c0db5aa47cea0c2f6e5e580c804f
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655850"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.

모든 Office 365 구독은 다음과 같은 요소로 구성 되어 있습니다.

- **라이선스 계획** 이러한 계획은 라이선스 요금제 또는 Office 365 요금제 라고도 합니다. 라이선스 계획은 사용자에 게 제공 되는 Office 365 서비스를 정의 합니다. Office 365 구독에는 여러 라이선싱 계획이 포함 될 수 있습니다. 라이선스 계획의 예로는 Office 365 Enterprise E3을 들 수 있습니다.
    
- **서비스** 이러한 계획은 서비스 계획이 라고도 합니다. 서비스는 각 라이선스 계획에서 사용할 수 있는 Office 365 제품, 기능 및 기능 (예: Exchange Online 및 Office Professional Plus)입니다. 사용자는 다양 한 서비스에 대 한 액세스 권한을 부여 하는 다른 라이센스 계획에서 할당 된 여러 개의 라이센스를 가질 수 있습니다.
    
- **라이선스** 각 라이선스 계획에는 구매한 라이선스 수가 포함 됩니다. 라이선스 계획에 정의 된 Office 365 서비스를 사용할 수 있도록 사용자에 게 라이선스를 할당 합니다. 모든 사용자 계정에는 라이선스 요금제가 하나 이상 있어야 Office 365에 로그온 하 고 서비스를 사용할 수 있습니다.
    
Office 365 PowerShell을 사용 하 여 Office 365 조직의 사용 가능한 라이선스 계획, 라이선스 및 서비스에 대 한 세부 정보를 볼 수 있습니다. 서로 다른 Office 365 구독에서 사용할 수 있는 제품, 기능 및 서비스에 대 한 자세한 내용은 [office 365 계획 옵션](https://go.microsoft.com/fwlink/p/?LinkId=691147)을 참조 하세요.


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  
현재 라이선스 계획 및 각 계획에 사용 가능한 라이선스에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

결과에는 다음 정보가 포함됩니다.
  
- **SkuPartNumber:** 조직에 사용할 수 있는 라이선스 계획을 표시 합니다. 예를 `ENTERPRISEPACK` 들어 Office 365 Enterprise e 3의 라이선스 계획 이름을 사용할 수 있습니다.
    
- **Enabled:** 특정 라이선스 계획을 위해 구매한 라이선스 수입니다.
    
- **ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 한 라이선스 수입니다.
    
모든 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 먼저 라이선스 계획 목록을 표시 합니다.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

다음으로, 라이선스 계획 정보를 변수에 저장 합니다.

```powershell
$licenses = Get-AzureADSubscribedSku
```

다음으로, 특정 라이선스 계획에서 서비스를 표시 합니다.

```powershell
$licenses[<index>].ServicePlans
```

\<index>는 `Get-AzureADSubscribedSku | Select SkuPartNumber` 명령 표시에서 1을 뺀 값으로 라이선스 계획의 행 번호를 지정 하는 정수입니다.

예를 들어 다음과 같이 `Get-AzureADSubscribedSku | Select SkuPartNumber` 명령을 표시 하는 경우를 예로 들 수 있습니다.

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

그런 다음 ENTERPRISEPREMIUM 라이선스 계획에 대 한 서비스를 표시 하는 명령은 다음과 같습니다.

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM은 세 번째 행입니다. 따라서 인덱스 값은 (3-1) 또는 2입니다.

라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

>[!Note]
>이 항목에서 설명하는 절차를 자동화하는 PowerShell 스크립트를 사용할 수 있습니다. 특히이 스크립트를 사용 하면 Sway를 포함 하 여 Office 365 조직에서 서비스를 확인 하 고 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)를 참조하세요.
>
    
현재 라이선스 계획 및 각 계획에 사용 가능한 라이선스에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

결과에는 다음 정보가 포함됩니다.
  
- **AccountSkuId:** 구문을 `<CompanyName>:<LicensingPlan>`사용 하 여 조직에 사용할 수 있는 라이선스 계획을 표시 합니다.  _<CompanyName>_ 은 Office 365에서 등록할 때 입력 한 값 이며 조직에서 고유 합니다. _<LicensingPlan>_ 값은 모든 사용자에 대해 동일 합니다. 예를 들어이 값 `litwareinc:ENTERPRISEPACK`에서 회사 이름은 `litwareinc`및 라이선스 계획 이름 `ENTERPRISEPACK`(Office 365 Enterprise e 3의 시스템 이름)입니다.
    
- **Activeunits:** 특정 라이선스 계획을 위해 구매한 라이선스 수입니다.
    
- **WarningUnits:** 갱신 하지 않고 30 일 유예 기간 이후에 만료 되는 라이선스 요금제의 라이선스 수입니다.
    
- **ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 한 라이선스 수입니다.
    
모든 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

다음 표에서는 가장 일반적인 서비스에 대 한 Office 365 서비스 계획 및 해당 이름을 보여 줍니다. 서비스 계획 목록이 다를 수도 있습니다. 
  
|**서비스 계획**|**설명**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |RMS(Azure 권한 관리)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |비즈니스용 Skype Online  <br/> |
| `SHAREPOINTWAC` <br/> |사무실  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 계획 2  <br/> |
   
라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.

특정 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 구문을 사용 합니다.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

이 예에서는 litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3) 라이선스 계획에서 사용할 수 있는 Office 365 서비스를 표시 합니다.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Office 365의 새로운 기능

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>참고 항목

[Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
