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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: idfix 도구에서 제외 및 지원 되는 특성을 나열 합니다.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085087"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 제외 및 지원 개체/특성
IdFix에서 관리하는 두 가지 규칙 집합은 다중 테넌트 및 전용/ITAR입니다. 현재 이 두 규칙 집합에는 검색에서 동일한 개체, 특성 및 특성 값이 제외됩니다. 이러한 방식이 향후 릴리스에서는 달라질 수 있습니다.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix에서 사용되는 다중 테넌트 및 전용 오류 제외
이 섹션에는 idfix에서 디렉터리 검색에서 제외 되는 개체, 특성 및 값이 나열 됩니다. 별표 (\*)는 다른 문자를 대체할 수 있는 와일드 카드입니다.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>IdFix 검색 중에 제외되는 개체, 특성 및 값

|**제외**|**예**|
|:-----|:-----|
|Admini\* |관리자 |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|discoverysearchmailbox\*  |discoverysearchmailbox  |
|FederatedEmail\* |FederatedEmail *GUID* |
|체제\* ||
|httpconnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-링크 |
|iusr\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|지원\* ||
|SystemMailbox\* |systemmailbox { *GUID* }|
|wwioadmini\*  ||
|\*$ ||
|distinguishedName에는 "\0ACNF:"가 포함 되어 있습니다.|"\0ACNF: *GUID* " |
|개체에는 IsCriticalSystemObject 특성이 포함됩니다. |[특성 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)를 참조 하세요. |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>IdFix에서 확인하는 다중 테넌트 및 전용 개체/특성
idfix에서 오류를 확인 하는 특성은 [idfix 도구를 사용 하 여 Office 365 동기화를 위한 디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md)의 "디렉터리 개체 및 특성 준비" 섹션에 설명 되어 있습니다.
  

