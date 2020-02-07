---
title: 용량 계획 및 부하 테스트 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 이 문서에서는 허용 되지 않으므로 기존 부하 테스트를 수행 하지 않고 SharePoint Online에 배포 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: ca0ae008778cfd5d347d8b4f78b7db927b4e8f82
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844709"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>용량 계획 및 부하 테스트 SharePoint Online
이 문서에서는 SharePoint Online에서 부하 테스트가 허용 되지 않으므로 기존 부하 테스트 없이 SharePoint Online에 배포 하는 방법에 대해 설명 합니다. SharePoint Online은 클라우드 서비스 이며 부하 기능, 서비스의 전체 부하 균형은 Microsoft에 의해 관리 됩니다.
  
사이트 실행을 성공적으로 수행할 수 있도록 하기 위한 가장 좋은 방법은 [포털 시작 롤아웃 계획](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)에서 강조 표시 되는 기본 원칙, 사례 및 권장 사항을 따르는 것입니다.

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>SharePoint Online의 용량 계획 수행 방법 개요 
온-프레미스 배포를 통해 SharePoint Online의 주요 장점 중 하나는 배포 된 지역의 사용자에 대 한 최적화 뿐 아니라 클라우드의 회복 력입니다. 대규모 환경에서는 수백만 명의 사용자를 매일 처리할 수 있도록 설정 되어 있으므로, 팜 균형 조정 및 확장을 통해 용량을 효과적으로 처리 하는 것이 중요 합니다.
  
한 팜의 모든 테 넌 트에 대 한 증가는 종종 예측 불가능 하지만, 집계 된 요청의 합계는 시간에 따라 예측할 수 없습니다. SharePoint Online의 성장 추세를 파악 하 여 향후 확장이 계획 될 수 있습니다.
  
어떤 팜에서 든 효율적으로 용량을 사용 하 고 예기치 않은 성장을 처리 하기 위해 서비스의 다양 한 요소를 추적 하 고 모니터링 하는 자동화 기능을 제공 합니다. 여러 메트릭이 사용 되며,이는 기본 구성 요소의 CPU 부하 중 하나인 프런트 엔드 서버를 수직 확장 하는 신호로 사용 됩니다. 또한 시간에 따른 부하 및 증가에 따라 SQL 환경을 확장 하 고 단계 및 전파를 통해 해당 부하와 성장을 적절 하 게 배포할 수 있으므로 [단계별/물결 방식을 사용](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)하는 것이 좋습니다. 

용량은 하드웨어를 지속적으로 추가 하는 것 보다 더 많은 작업을 수행 하는 것이 아니라, 해당 용량을 관리 하 고 제어 하 여 유효한 부하 요청을 처리 하 고 있는지 확인할 수 있습니다. 고객은 권장 지침에 따라 최상의 환경을 유지 하는 것이 좋습니다. 또한 서비스에서 "악성 프로그램" 동작을 허용 하지 않도록 제한 패턴과 제어가 적절 하 게 구현 되었음을 의미 합니다. 의도적인 것이 전부는 아닐 수는 있지만 해당 동작의 영향을 제한 해야 합니다. 제한 및이를 방지 하는 방법에 대 한 자세한 내용은 [제한 지침](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) 문서를 참조 하세요.

## <a name="why-you-cannot-load-test-sharepoint-online"></a>테스트 SharePoint Online을 로드할 수 없는 이유
온-프레미스 환경에서는 부하 테스트를 사용 하 여 확장 가정의 유효성을 검사 하 고 팜의 중단 지점을 찾습니다. 부하에 따라 포화 

SharePoint Online을 사용 하는 경우에는 배율이 비교적 유체 이며 특정 추론을 기반으로 하 여 부하를 조정 하 고 제한 및 제어 하는 경우에는 다른 작업이 수행 되어야 합니다. 대규모의 다중 테 넌 트 환경에서는 동일한 팜의 모든 테 넌 트를 보호 해야 하므로 부하 테스트를 자동으로 제한 합니다. 그러나 현재 테스트를 수행 하는 경우 테스트를 실행 하는 동안 테스트 중에 확장을 변경 하거나 테스트 후에는 시간이 초과 될 수 있기 때문에 disappointing 및 잠재적으로 잘못 된 결과를 받게 됩니다. 확장 및 팜 균형 작업은 지속적으로 수행 됩니다.

여기서는 테스트 SharePoint를 서비스로 로드 하는 대신 권장 되는 방법에 중점을 둔 [채 정상적인 포털 지침을 만들고, 시작 하 고, 유지 관리](https://go.microsoft.com/fwlink/?linkid=2105838) 하는 방법을 따릅니다.
