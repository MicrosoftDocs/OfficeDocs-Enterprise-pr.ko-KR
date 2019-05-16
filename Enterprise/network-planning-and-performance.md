---
title: Office 365의 네트워크 계획 및 성능 조정
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
description: Microsoft Office 365에 대 한 네트워크 대역폭 요구 사항을 계획 하는 데 도움이 됩니다. 배포한 후에는 여기로 돌아와서 Office 365 성능 문제를 미세 하 게 조정 합니다.
ms.openlocfilehash: 3497ab5ec006011cefd6e09db323847c97999a34
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069894"
---
# <a name="network-planning-and-performance-tuning-for-office-365"></a>Office 365의 네트워크 계획 및 성능 조정
처음으로 배포 하거나 Office 365로 마이그레이션하기 전에 다음 항목의 정보를 사용 하 여 필요한 대역폭을 예상 하 고 테스트 하 여 Office 365로 배포 하거나 마이그레이션할 대역폭이 충분 한지 확인할 수 있습니다. 개요는 [Office 365의 네트워크 및 마이그레이션 계획](network-and-migration-planning.md)을 참조 하십시오.
  
|||||
|:-----|:-----|:-----|:-----|
|**네트워크 계획** <br/> ![네트워크](media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |빠른 연결 및 페이지를 빠르게 로드 하 고 싶으십니까?  <br/> [Office 365에서 최적의 연결성 및 성능을 확인 하기](https://aka.ms/o365perfprinciples) 위해 읽어 보기 <br/> [Office 365 네트워크 연결 개요](https://docs.microsoft.com/en-us/office365/enterprise/office-365-networking-overview) 를 읽고 개념을 이해 합니다.  <br/> |**네트워크 측정** <br/> ![계산](media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |Office 365의 초기 계획 및 성능 관련 내역 및 [성능 문제 해결 계획](performance-troubleshooting-plan.md)을 [사용 하 여 office 365 성능 튜닝](performance-tuning-using-baselines-and-history.md) 을 읽어 봅니다.  <br/> 이러한 도구를 사용 하 여 [기존 네트워크를 평가](network-and-migration-planning.md#calculators)합니다.  <br/> |
|**엔터프라이즈에서 Office 365 ProPlus를 배포하는 모범 사례 가이드** <br/> ![모범 사례](media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[네트워크 계획을 위한 모범 사례 및 Office 365의 마이그레이션 성능 개선](network-and-migration-planning.md#BestPractices) 사용자를 즉시 활용할 수 있도록 하기 원하십니까? [저속 네트워크에서 Office 365 사용에 대 한 모범 사례](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)를 참조 하세요.  <br/> [Office 365 네트워크 연결 원리](https://aka.ms/o365networkingprinciples) 는 office 365 네트워크 연결을 안전 하 게 최적화 하기 위한 가장 최근 지침을 이해 하는 데 도움이 됩니다.  <br/> |**참조** <br/> ![책 또는 업무 일지](media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |IP 주소 및 포트 목록과 같은 세부 정보를 원하십니까? [Office 365에 대 한 네트워크 계획 참조](network-and-migration-planning.md#NetReference)를 참조 하세요.  <br/> |
|![엔터프라이즈 설계자 포스터 용 Microsoft 클라우드 네트워킹 참조](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |Office 365 및 기타 Microsoft 클라우드 플랫폼 및 서비스에 대 한 네트워크를 최적화 하는 단계는 [Microsoft 클라우드 네트워킹 For 엔터프라이즈 설계자](https://aka.ms/cloudarchnetworking) 포스터를 참조 하세요.  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-office-365"></a>Office 365의 성능 조정 및 문제 해결 리소스
<a name="apptuning"> </a>

Office 365을 배포한 후에는이 섹션의 항목을 사용 하 여 성능을 최적화할 수 있습니다. 성능 저하가 발생 하는 경우 이러한 항목을 사용 하 여 문제를 해결할 수도 있습니다.
  
 **[Office 365 성능 조정](tune-office-365-performance.md)**: office 365에서 네트워크 주소 변환을 사용 하는 방법에 대 한 자세한 내용은 [NAT support with office 365](nat-support-with-office-365.md)을 참조 하십시오. 또한 Paul Collinge에서 [Office 365 네트워크 연결을 최적화 하 고 문제를 해결 하기 위한 주요 10 가지 팁](https://blogs.technet.com/b/onthewire/archive/2014/06/18/top-10-tips-for-optimising-amp-troubleshooting-your-office-365-network-connectivity.aspx) 을 살펴봅니다. 
  
 **[Exchange online 성능 조정](tune-exchange-online-performance.md)**: 이러한 문서를 사용 하 여 exchange online 성능을 세부적으로 조정 합니다. 
  
 비즈니스용 **[Skype 온라인 성능 조정](tune-skype-for-business-online-performance.md)**: 비즈니스용 skype 온라인 성능을 미세 조정 하려면 다음 문서를 사용 하세요. 
  
 **[Sharepoint online 성능 조정](tune-sharepoint-online-performance.md)**: 이러한 문서를 사용 하 여 sharepoint online 성능을 세부적으로 조정 합니다. 
  
 **[Project online 성능 조정](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)**:이 문서를 사용 하 여 project online 성능을 세부적으로 조정할 수 있습니다. 
  

