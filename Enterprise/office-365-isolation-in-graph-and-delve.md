---
title: Office Graph 및 Delve에서 office 365 테 넌 트 격리
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: '요약: Office Graph 및 Delve의 테 넌 트 격리에 대 한 설명입니다.'
ms.openlocfilehash: c9e054494e6d71d84a19350bc38e0d3981fede45
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844439"
---
# <a name="tenant-isolation-in-the-office-graph-and-delve"></a>Office Graph 및 Delve에서 테넌트 격리

## <a name="tenant-isolation-in-the-office-graph"></a>Office Graph의 테 넌 트 격리

[Office Graph](https://developer.microsoft.com) 는 Exchange Online, SharePoint Online, Yammer, 비즈니스용 Skype, Azure Active Directory 등을 비롯 한 office 365 서비스의 활동을 모델링 하며, 다른 Microsoft 서비스 또는 타사 서비스와 같은 외부 서비스에서 작업을 진행 합니다. Office Graph 구성 요소는 Office 365 전체에서 사용 됩니다. Office Graph는 콘텐츠 및 활동 모음과 전체 Office 제품군에서 발생 하는 간의 관계를 나타냅니다. 복잡 한 기계 학습 기법을 사용 하 여 사용자를 관련 콘텐츠, 대화 및 주변 사용자에 게 연결 합니다. 예를 들어 SharePoint Online의 테 넌 트 인덱스에는 Delve 쿼리를 제공 하는 데 사용 되는 Office Graph 색인이 있고, SharePoint Online의 분석 처리 엔진은 신호를 저장 하 고, 정보를 계산 하는 데 사용 되며, Exchange Online은 각 사용자의 받는 사람 캐시를 테 넌 트 분석에 입력 합니다.

Office Graph에는 사용자 및 문서와 같은 엔터프라이즈 개체와 이러한 개체 간의 관계 및 상호 작용에 대 한 정보가 포함 되어 있습니다. 관계와 상호 작용은 *가장자리로*표시 됩니다. Office 그래프가 같은 테 넌 시의 *노드* 간에만 있을 수 있도록 테 넌 트로 분할 됩니다. *노드* 는 URI (Uniform resource Identifier), 노드 유형, 액세스 제어 목록 및 *메타 데이터* 와 모서리를 포함 하는 패싯 집합이 포함 된 엔터티입니다. 각 노드에는 공통 정보 모델에서와 같이 *패싯에* 정렬 된 메타 데이터 및 가장자리가 연결 되어 있습니다. *메타 데이터* 는 office graph에서 검색, 필터링 또는 분석에 사용할 수 있는 노드에 저장 된 속성입니다. *패싯은* 노드의 메타 데이터 및 모서리에 대 한 논리적 컬렉션입니다. 각 패싯은 노드의 한 가지 측면을 나타냅니다. 

Office Graph에서는 모든 데이터를 단일 리포지토리로 가져오지 않습니다. 대신 다른 위치에 있는 데이터에 대 한 관계 및 메타 데이터를 저장 합니다. Office Graph는 여러 데이터 저장소와 처리 구성 요소로 구성 되어 있습니다.

- 테 넌 트 그래프 저장소는 효율적인 분석을 위해 최적화 된 대량 저장소를 제공 합니다.
- 활성 콘텐츠 캐시는 사용자 환경을 구동 하기 위해 활성 노드와 가장자리에 대 한 신속한 임의 액세스를 제공 합니다.
- 입력 라우터는 구성 요소에 테 넌 트 그래프에 대 한 변경 내용을 적용 하 고 내부 및 외부에 알립니다.

각 작업 부하 내의 분석은 테 넌 트 차원 계산과 관련 된 정보를 추론 하 여 테 넌 트 그래프로 푸시합니다. 테 넌 트의 모든 활동을 초과 하 여 행동 패턴에 대 한 통찰력을 생성 하는 것은 거주자 분석 이유입니다. 예를 들어 Exchange Online은 각 사용자의 사서함을 효율적으로 설명 하는 분석을 사용 하 여 각 사용자의 받는 사람 캐시를 계산 합니다. 이러한 사용자별 분석에서는 각 사용자의 *RecipientCache* 에 대 한 집합을 생성 하며, 그러면 각 사용자에 게 테 넌 트 그래프로 푸시됩니다. 이렇게 하면 가능한 한 원본 데이터에 가깝게 분석 처리의 대부분이 유지 됩니다.

## <a name="tenant-isolation-in-delve"></a>Delve의 테 넌 트 격리

앞에서 설명한 것 처럼 Office Graph는 사용자가 자신의 엔터프라이즈에서 현재 활동을 검색 하 고 공동으로 작업 하는 데 도움이 되 고, 작업 전반에 걸친 콘텐츠 및 활동에 대 한 이유를 분석 하기 위한 엔터티 중심 플랫폼을 제공 합니다. Office 365 이상입니다. Delve는 Office Graph에 의해 구동 되는 첫 번째 환경입니다.
Delve는 office Graph를 통해 office 365 및 Yammer Enterprise에서 Office 365 사용자에 게 콘텐츠를 제공 하는 Office 365 웹 환경입니다. 웹 환경에서는 데이터를 다른 보드로 표시 하며 각각에 게 자동 *경향* 또는 *내가 수정한*것과 같은 특정 항목을 제공 합니다. 각 보드는 문서에서 요약 텍스트와 그림을 표시 하는 여러 문서 카드로 구성 됩니다. 카드를 사용 하면 문서의 문서를 열거나 Yammer 페이지를 여는 등의 작업을 수행할 수 있습니다. Office 365 테 넌 트에서 각 사용자에 대해 가장 관련성이 높은 문서를 표시 하는 페이지와 Exchange Online 또는 비즈니스용 Skype를 호출 하 여 해당 사람과 상호 작용할 수 있는 아이콘이 있습니다. Delve는 Office Graph API를 기반으로 하기 때문에 해당 API의 테 넌 트 기반 격리에 의해 바인딩됩니다.