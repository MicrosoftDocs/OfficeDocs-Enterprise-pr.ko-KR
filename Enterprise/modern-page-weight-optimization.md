---
title: SharePoint Online 최신 사이트 페이지에서 페이지부하 최적화
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online 최신 사이트 페이지에서 페이지 부하를 최적화하는 방법을 학습하세요.
ms.openlocfilehash: 75bc6227cf77d355dcd6b3a4ce1afa9388b32c58
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078007"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>SharePoint Online 최신 사이트 페이지에서 페이지부하 최적화

SharePoint Online 최신 사이트 페이지에는 이미지, 텍스트, 탐색/명령 모음 아래의 콘텐츠 영역에 있는 개체와 페이지의 프레임 워크를 구성하는 기타 HTML 코드를 포함하여 페이지의 페이지 콘텐츠를 제공하는데 필요한 연재된 코드가 포함되어 있습니다.   페이지 부하는 이 HTML 코드에 대한 측정치며 페이지 로드 시간을 최적화하기 위해 제한되어 야 합니다.

이 문서는 최신 사이트 페이지에서 페이지 부하를 줄이는 방법을 이해하는데 도움을 줍니다.

>[!NOTE]
>SharePoint Online 최신 포털의 성능에 대한 자세한 내용은 [최신 SharePoint 환경의 성능](https://docs.microsoft.com/sharepoint/modern-experience-performance)을 참조하세요.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>SharePoint 용 페이지 진단 도구를 사용한 페이지 부하 분석

**Sharepoint 페이지 진단 도구**는 Chrome 및 [ Microsoft Edge 버전 77 이상](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)의 브라우저 확장으로서 Sharepoint 최신 및 클래식 게시 사이트 페이지를 분석하는데 사용할 수 있습니다.  이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다. Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](page-diagnostics-for-spo.md)을 참조하세요.

Sharepoint용 페이지 진단 도구를 사용하여 Sharepoint 사이트 페이지를 분석 시 _진단 테스트_ 창의 **500KB 미만의 페이지 부하** 결과에서 페이지에 대한 정보를 확인할 수 있습니다. 페이지 부하가 기준선 값 아래에 있으면 결과는 녹색이 되고, 페이지 부하가 기준선 값을 초과하는 경우 빨간색으로 표시됩니다.

잠정 결과는 다음과 같습니다:

- **주의 필요** (빨간색): 페이지 부하가 500KB를 초과
- **조치가 필요하지 않음** (녹색): 페이지 부하가 500KB 미만

**페이지 부하가 500KB 미만** 결과가 **주의 필요** 섹션에 표시되는 경우 클릭하여 세부 정보를 확인할 수 있습니다.

![SharePoint 결과에 대한 요청](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>페이지 부하 문제 수정

페이지 부하가 500KB를 초과하는 경우 웹 파트 수를 줄이고 페이지 콘텐츠를 적절한 수준으로 제한하여 전반적인 페이지 로드 시간을 개선할 수 있습니다.

페이지 부하 줄이기에 대한 일반적인 지침은 다음과 같습니다:

- 페이지 콘텐츠를 적정 분량으로 제한하고 관련 콘텐츠는 여러 페이지를 사용합니다.
- 큰 속성 백이 있는 웹 파트의 사용을 최소화합니다.
- 가능하면 비 대화형 롤업 보기를 사용합니다.
- 압축 이미지 형식을 사용하여 이미지 크기를 적절하게 조정하고 이미지가 CDN에서 다운로드 되는지 확인하여 이미지 크기를 최적화합니다.

다음의 문서에서 페이지 부하를 제한하는 방법에 대한 추가 지침을 확인할 수 있습니다.

- [SharePoint에서 페이지 성능 최적화](https://docs.microsoft.com/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

성능 문제를 개선하기 위해 페이지를 수정하기 전에 분석 결과에 페이지 로드 시간을 기록해 둡니다. 수정 후에 다시 도구를 실행하여 새 결과가 기준선 표준에 포함되는지 확인하고 새 페이지 로드 시간을 확인하여 개선이 되었는지 확인합니다.

![페이지 로드 시간 결과](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>페이지 로드 시간은 네트워크 부하, 하루 중 시간 및 기타 일시적인 조건과 같은 다양한 요인에 따라 다를 수 있습니다. 결과의 평균을 내는데 도움이 되도록 수정을 하기 전과 후에 페이지 로드 시간을 몇 번 정도 테스트해야 합니다.

## <a name="related-topics"></a>관련 항목

[SharePoint Online 성능 조정](tune-sharepoint-online-performance.md)

[Office 365 성능 조정](tune-office-365-performance.md)

[최신 SharePoint 환경의 성능](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)

[콘텐츠 배달 네트워크](content-delivery-networks.md)

[sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기](use-office-365-cdn-with-spo.md)
