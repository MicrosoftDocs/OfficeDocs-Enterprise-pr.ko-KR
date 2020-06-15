---
title: IdFix 제외 및 지원 개체/특성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: IdFix 도구에서 제외 및 지원 되는 특성을 나열 합니다.
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711578"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 제외 및 지원 개체/특성

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

IdFix에서 유지 관리 되는 두 가지 규칙 집합은 다음과 같습니다. 다중 테 넌 트 및 전용/ITAR 이때 두 규칙 집합은 동일한 개체, 특성 및 특성 값을 해당 검색에서 제외 합니다. 이는 이후 릴리스에서 변경 될 수 있습니다.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix에서 사용 되는 다중 테 넌 트 및 전용 오류 제외
이 섹션에는 IdFix에서 디렉터리 검색에서 제외 되는 개체, 특성 및 값이 나열 됩니다. 별표 ( \* )는 다른 문자를 대체할 수 있는 와일드 카드입니다.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>IdFix 검색 중에 제외 되는 개체, 특성 및 값

|**배타적**|**예**|
|:-----|:-----|
|Admini\* |관리자 |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|체제\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-링크 |
|iusr_\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName에는 "\0ACNF:"가 포함 되어 있습니다.|"\0ACNF: *GUID* " |
|IsCriticalSystemObject 특성을 포함 하는 개체 |[특성 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)를 참조 하세요. |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>IdFix에서 확인 하는 다중 테 넌 트 및 전용 개체 및 특성
IdFix에서 오류를 확인 하는 특성에 대해서는 [idfix 도구를 사용 하 여 Microsoft 365과 동기화 하기 위한 Prepare 디렉터리 특성](prepare-directory-attributes-for-synch-with-idfix.md)의 "디렉터리 개체 및 특성 준비" 섹션에 설명 되어 있습니다.
  

