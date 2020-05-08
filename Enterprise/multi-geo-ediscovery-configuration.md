---
title: Microsoft 365 Multi-Geo eDiscovery 구성
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Microsoft 365 Multi-Geo의 eDiscovery를 구성하는 방법을 알아봅니다.
ms.openlocfilehash: a956a38f00590161c04009b472a4a8a9d2e89d2b
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057958"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 Multi-Geo eDiscovery 구성

기본적으로 eDiscovery 관리자 또는 다중 위치 테넌트의 관리자는 해당 테넌트의 중앙 위치에서만 eDiscovery를 수행할 수 있습니다. 위성 위치에 대한 eDiscovery를 수행할 수 있는 기능을 지원하기 위해 "Region"이라는 새로운 준수 보안 필터 매개 변수를 PowerShell을 통해 사용할 수 있습니다.

Microsoft 365 전역 관리자는 다른 사용자들이 eDiscovery를 수행할 수 있도록 하기 위해 eDiscovery 관리자 권한을 할당해야 하며, 해당 준수 보안 필터에서 “Region” 매개 변수를 할당하여 eDiscovery 수행 지역을 위성 위치로 지정해야 합니다. 그렇지 않으면 해당 위성 위치에 대해 eDiscovery가 수행되지 않습니다.

특정 위성 위치에 대해 eDiscovery 관리자(manager) 또는 관리자(administrator) 역할이 설정되면 해당 eDiscovery 관리자(manager) 또는 관리자(administrator)만 해당 위성 위치에 있는 SharePoint 사이트 및 OneDrive 사이트에 대해 eDiscovery 검색 작업을 수행할 수 있습니다. eDiscovery 관리자(manager) 또는 관리자(administrator)가 지정된 위성 위치 외부의 SharePoint 또는 OneDrive 사이트를 검색하려고 하면 결과가 반환되지 않습니다. 또한 지역에 대한 eDiscovery 관리자(manager) 또는 관리자(administrator)가 내보내기를 트리거할 경우 데이터가 해당 지역의 Azure 인스턴스로 내보내집니다. 이를 통해 제어 경계 너머로 콘텐츠가 내보내지지 않게 되므로 조직은 준수 상태를 유지할 수 있습니다.

> [!NOTE]
> eDiscovery 관리자가 여러 SharePoint 위성 위치에 걸쳐 검색해야 할 경우 OneDrive 또는 SharePoint 사이트가 있는 대체 위성 위치를 지정하는 eDiscovery 관리자에 대해 다른 사용자 계정을 만들어야 합니다.

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

지역에 대한 준수 보안 필터를 설정하려면

1. [Microsoft 365 보안 및 준수 센터 PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)

2. 다음 구문을 사용합니다.

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   예시는 다음과 같습니다:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

추가 매개 변수 및 구문에 대해서는 [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesecurityfilter) 문서를 참조하세요.
