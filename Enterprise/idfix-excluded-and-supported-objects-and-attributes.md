---
title: IdFix 제외 및 지원 개체/특성
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 제외 되며 IdFix 도구에서 지원 되는 특성이 나와 있습니다.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542058"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 제외 및 지원 개체/특성
IdFix에서 관리하는 두 가지 규칙 집합은 다중 테넌트 및 전용/ITAR입니다. 현재 이 두 규칙 집합에는 검색에서 동일한 개체, 특성 및 특성 값이 제외됩니다. 이러한 방식이 향후 릴리스에서는 달라질 수 있습니다.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix에서 사용되는 다중 테넌트 및 전용 오류 제외
이 섹션에서는 개체, 특성 및 IdFix 대상 디렉터리의 해당 검색에서 제외 하는 값을 보여줍니다. 별표 (\*)은 다른 모든 문자에 대신 사용할 수 있는 와일드 카드.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>IdFix 검색 중에 제외되는 개체, 특성 및 값

|**제외**|**예제**|
|:-----|:-----|
|관리자\* |관리자 |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail 합니다. *GUID* |
|게스트\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms DS-KrbTgt 링크 |
|iusr_\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedname "\0ACNF:"|"\0ACNF: *GUID* " |
|개체에는 IsCriticalSystemObject 특성이 포함됩니다. |[특성 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)를 참조 하십시오. |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>IdFix에서 확인하는 다중 테넌트 및 전용 개체/특성
IdFix에서 오류를 확인 하는 특성을 ["IdFix 도구를 사용 하 여 Office 365와 동기화를 위한 디렉터리 특성 준비에](prepare-directory-attributes-for-synch-with-idfix.md)에서" 디렉터리 개체 및 특성 준비 섹션에 설명 되어있습니다.
  

