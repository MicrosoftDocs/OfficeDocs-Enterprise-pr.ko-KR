---
title: "GDPR에 대한 Office 365 정보 보호 개요"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "GDPR에 대한 Office 365 정보 보호 개요를 확인합니다. 개인 데이터를 검색, 분류, 보호 및 모니터링하는 방법을 알아봅니다."
ms.openlocfilehash: b3af91608d545b221694b9e4a18db07b85d7541a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a>GDPR에 대한 Office 365 정보 보호 개요

이 솔루션은 Office 365 서비스에 저장되어 있는 중요한 데이터를 보호하는 방법을 설명하며 개인 데이터를 검색, 분류, 보호 및 모니터링하기 위한 규정된 권장 사항을 포함합니다. 이 솔루션에서는 GDPR(일반 데이터 보호 규정)을 예제로 사용하지만, 동일한 프로세스를 적용하여 여러 다른 규정을 준수할 수 있습니다.

GDPR은 개인 데이터의 수집, 저장, 처리 및 공유를 규제합니다. 개인 데이터는 EU(유럽 연합)에 거주하는 식별되었거나 식별 가능한 자연인과 관련된 데이터로서 GDPR에서 매우 광범위하게 정의됩니다.

문서 4 - 정의

> '개인 데이터'는 식별되었거나 식별 가능한 자연인(‘데이터 주체’)과 관련된 정보를 의미합니다. 식별 가능한 자연인은 직간접적으로, 특히 이름, 식별 번호, 위치 데이터, 온라인 식별자 또는 해당 자연인의 신체적, 생리적, 유전적, 정신적, 경제적, 문화적 또는 사회적 ID와 같은 식별자를 참조하여 식별될 수 있는 사람입니다.

이 솔루션은 조직에서 GDPR이 적용될 수 있는 Office 365dml 개인 데이터를 검색하고 보호하는 데 도움을 주기 위해 작성되었습니다. 이 솔루션은 GDPR 규정 준수에 대한 증거로 제공되지 않습니다. 조직에서는 자체 GDPR 규정 준수를 보장하고, 법률 및 규정 준수 팀의 자문을 구하거나 규정 준수에 특하된 제3자의 자문을 구하는 것이 좋습니다.

[GDPR 평가](https://www.gdprbenchmark.com)는 조직이 전반적인 준비 수준이 GDPR에 부합되는지 검토하는 데 도움을 주기 위해 무료로 사용할 수 있는 빠른 온라인 자체 평가 도구입니다(<http://aka.ms/gdprassessment>).

## <a name="assess-and-manage-your-compliance-risk"></a>규정 준수 위험 평가 및 관리

GDPR 규정을 준수하는 첫 번째 단계는 GDPR이 조직에 적용되는지, 적용된다면 적용 수준은 어떤지 평가하는 것입니다. 이러한 분석에는 조직이 처리하는 데이터와 데이터의 위치를 이해하는 작업이 포함됩니다.

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a>1단계 - 규정 준수 관리자를 사용하여 규정 요구 사항을 확인하고 진행 상황 추적

규정 준수 관리자는 조직이 GDPR을 비롯한 다양한 표준 규정을 준수하도록 하기 위해 감사 컨트롤을 추적, 구현 및 관리하기 위한 도구를 제공합니다.

![규정 준수 관리자를 사용하여 요구 사항 확인 및 진행 상황 추적](Media/Overview-image1.png)

자세한 내용은 [서비스 보안 포털에서 규정 준수 관리자 사용](https://support.office.com/ko-KR/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942)을 참조하세요. 

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a>2단계 - 콘텐츠 검색 및 중요한 정보 유형을 사용하여 및 개인 데이터 찾기 

작업 환경에서 GDPR이 적용되는 개인 데이터를 검색합니다. 중요한 정보 유형과 콘텐츠 검색을 사용하여 다음을 수행합니다.

-   개인 데이터가 있는 위치를 찾아 보고합니다.

-   중요한 데이터 유형 및 기타 쿼리를 최적화하여 사용자 환경의 모든 개인 데이터를 찾습니다.

![콘텐츠 검색 및 중요한 정보 유형을 사용하여 개인 데이터 찾기](Media/Overview-image2.png)

중요한 정보 유형은 자동화된 프로세스가 상태 서비스 번호 및 신용 카드 번호와 같은 특정 정보 유형을 인식하는 방법을 정의합니다. 이 문서에는 시작점으로 사용할 수 있는 정보 집합이 포함되어 있습니다. EU 국가의 개인 데이터의 경우 앞으로 좀 더 많은 중요한 정보 유형이 제공될 예정입니다.

자세한 내용은 [개인 데이터 검색 및 찾기](search-for-and-find-personal-data.md)를 참조하세요. 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a>Office 365 및 기타 SaaS 앱에서 개인 데이터 분류, 보호 및 모니터링

Office 365에서 정보 보호에 사용되는 기능 중 일부를 다른 SaaS 응용 프로그램에서 중요한 데이터를 보호하는 데도 사용할 수 있습니다.

![개인 데이터 분류, 보호 및 모니터링](Media/Overview-image3.png)

이 그림은 이 섹션의 나머지 부분을 나타냅니다(3-5단계).

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a>3단계 - 중요한 정보 유형 외에도 레이블을 사용할지 여부 결정

중요한 정보 유형은 분류의 한 형태입니다. 레이블도 구현하려는 경우에는 [개인 데이터에 대한 분류 스키마 설계](architect-a-classification-schema-for-personal-data.md)를 참조하세요. 레이블을 적용하려면 [Office 365의 개인 데이터에 레이블 적용](apply-labels-to-personal-data-in-office-365.md)을 참조하세요.

이 그림에서 보면 중요한 정보 유형 및 레이블이 Office 365 전반에서 작동합니다. 머지 않아 Cloud App Security에서 이러한 항목을 사용하여 Box 및 Salesforce 등의 기타 SaaS 앱에서 중요한 데이터를 찾을 수 있을 것입니다.

### <a name="step-4--protect-personal-data-in-office-365"></a>4단계 - Office 365에서 개인 데이터 보호 

개인 데이터의 보호는 Office 365 데이터 손실 방지 기능을 통해 시작됩니다. 전자 메일을 위한 Office 365 메시지 암호화를 포함하여 개인 데이터에 대한 액세스를 보호하는 데 권장되는 다른 몇 가지 기능도 있습니다.

이러한 보호 기능의 대상을 다음과 같은 특정 데이터 집합으로 지정할 수 있습니다.

-   사이트 및 라이브러리 수준 사용 권한

-   사이트 수준 외부 공유 정책

-   사이트 수준 장치 액세스 제어

Office 365 및 기타 클라우드 서비스에 대한 액세스 보호에는 다음이 포함됩니다.

-   EMS(Enterprise Mobility + Security)의 ID 및 장치 액세스 보호

-   권한이 부여된 액세스 관리

-   Windows 10 보안 기능

보호 적용에 대한 자세한 내용은 [Office 365에서 개인 데이터에 보호 적용](apply-protection-to-personal-data-in-office-365.md)을 참조하세요.

### <a name="step-5--monitor-for-leaks-of-personal-data"></a>5단계 - 개인 데이터 누수 모니터링

Office 365 데이터 손실 방지 보고서는 중요한 데이터의 모니터링 결과를 가장 자세히 제공합니다. Office 365 감사 로그를 사용하여 자동화된 경고를 설정하고 위반을 조사할 수 있습니다. Cloud App Security는 확인하여 모니터링하는 중요한 데이터 범위를 다른 SaaS 공급자로 확장합니다. 이러한 도구에 대한 자세한 내용은 [개인 데이터 침해 모니터링](monitor-for-leaks-of-personal-data.md)을 참조하세요.
