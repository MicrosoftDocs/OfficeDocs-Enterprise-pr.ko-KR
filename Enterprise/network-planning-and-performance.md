---
title: Office 365의 네트워크 계획 및 성능 조정
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/23/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
description: Microsoft Office 365에 대 한 네트워크 대역폭 요구 사항을 계획 하는데 도움이 됩니다. 배포 하면 미세 조정 하려면 여기를 반환 하 고 Office 365 성능 문제를 해결 합니다.
ms.openlocfilehash: da8618381664a0ddf4d670cfbb2907236c468ac0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22915893"
---
# <a name="network-planning-and-performance-tuning-for-office-365"></a>Office 365의 네트워크 계획 및 성능 조정
를 처음으로 배포 하거나 Office 365로 마이그레이션 전에 정보 사용할 수 있습니다는 이러한 항목에 필요한 대역폭을 예측 하려면 다음 테스트 하 고를 배포 하거나 Office 365로 마이그레이션하는 대역폭이 충분 한지 확인 하십시오. 에 대 한 개요를 참조: [네트워크 및 마이그레이션 Office 365에 대 한 계획](network-and-migration-planning.md)합니다.
  
|||||
|:-----|:-----|:-----|:-----|
|**네트워크 계획** <br/> ![네트워크](media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |고속 연결 하 고 신속 하 게 로드 하는 페이지를 설정할지 여부  <br/> [최상의 연결 및 Office 365의 성능](https://aka.ms/o365perfprinciples) 읽기 <br/> [Office 365를 사용 하 여 성능을 최적화 하기 위해 이해 네트워크 연결](https://blogs.office.com/2015/03/04/understanding-network-connectivity-optimize-performance-office-365/) 개념을 이해 하려면 비디오 시청  <br/> |**네트워크를 측정합니다.** <br/> ![계산기](media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |[초기 계획 및 성능 기록을 사용 하 여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md) 및 [성능 문제해결 Office 365에 대 한 계획을](performance-troubleshooting-plan.md)읽습니다.  <br/> [기존 네트워크를 평가](network-and-migration-planning.md#calculators)하는 이러한 도구를 사용 합니다.  <br/> |
|**모범 사례** <br/> ![모범 사례](media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[네트워크 계획 및 Office 365에 대 한 마이그레이션 성능을 개선 하기 위한 모범 사례](network-and-migration-planning.md#BestPractices)입니다. 사용자에 게 즉시 도와 시작 싶으십니까? [저속 네트워크에서 Office 365를 사용 하는 것에 대 한 모범 사례](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)를 참조 하십시오.<br/> [Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 에 안전 하 게 Office 365 네트워크 연결을 최적화 하는 것에 대 한 최신 지침을 이해 하는데 도움이 됩니다.  <br/> |**참조 (영문)** <br/> ![책 또는 저널](media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |IP 주소 및 포트 목록 처럼는 정보가 필요 하십니까? [네트워크 계획 Office 365에 대 한 참조](network-and-migration-planning.md#NetReference)를 참조 합니다.<br/> |
|![Microsoft 클라우드 네트워킹 엔터프라이즈 설계자 포스터 (영문)에 대 한 참조](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |Office 365 및 기타 Microsoft 클라우드 플랫폼 및 서비스에 대 한 네트워크를 최적화 하는 단계를 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 네트워킹](https://aka.ms/cloudarchnetworking) 포스터를 참조 하십시오.  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-office-365"></a>Office 365의 성능 조정 및 문제 해결 리소스
<a name="apptuning"> </a>

Office 365 배포를 만든 후에이 섹션의 항목을 사용 하 여 성적을 최적화할 수 있습니다. 성능 저하를 발생 하는 경우 문제를 해결 하 이러한 항목을 사용할 수도 있습니다.
  
 **[Office 365 조정 성능](tune-office-365-performance.md)**: 네트워크 주소 변환 Office 365와 함께 사용 하는 방법에 대 한 정보를 [Office 365와의 NAT 지원](nat-support-with-office-365.md)을 참조 합니다. 또한 Paul Collinge로 [최적화 하 고 Office 365 네트워크 연결 문제를 해결 하는 상위 10 가지 팁](https://blogs.technet.com/b/onthewire/archive/2014/06/18/top-10-tips-for-optimising-amp-troubleshooting-your-office-365-network-connectivity.aspx) 를 살펴보겠습니다. 
  
 **[Exchange Online 조정 성능](tune-exchange-online-performance.md)**: Exchange Online 성능을 미세 조정 하는이 문서를 사용 합니다. 
  
 **[비즈니스 온라인 성능에 대 한 조정 Skype](tune-skype-for-business-online-performance.md)**: 이러한 문서를 사용 하 여 비즈니스 온라인 성능에 대 한 Skype 다시 조정 해야 합니다. 
  
 **[SharePoint Online 조정 성능](tune-sharepoint-online-performance.md)**: SharePoint Online 성능을 미세 조정 하는이 문서를 사용 합니다. 
  
 **[Project Online 조정 성능](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)**: Project Online 성능을 미세 조정 하려면이 문서를 사용 합니다. 
  

