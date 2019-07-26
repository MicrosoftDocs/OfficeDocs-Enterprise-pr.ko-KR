---
title: 핵심 데이터를 새 Office 365 데이터 센터 지역으로 이동
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 07/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: 새 데이터 센터? 지속적인 고객 요구 및 사용 증가를 지원 하기 위해 용량을 추가 하 고 리소스를 계산 합니다. 또한 새 데이터 센터 지역는 핵심 고객 데이터에 대 한 상주 데이터를 제공 합니다. 핵심 고객 데이터는 Microsoft Online Services 약관 (전자 메일 본문, 일정 항목 및 전자 메일 첨부 파일의 콘텐츠)과 SharePoint Online 사이트 콘텐츠 및 파일에 정의 된 고객 데이터의 하위 집합을 참조 하는 용어입니다. 해당 사이트 내에 저장 되 고 파일을 비즈니스용 OneDrive로 업로드 합니다.
ms.openlocfilehash: df52b50f6e291a80aeb7b8d783937d225bfb6e29
ms.sourcegitcommit: 842ac51577317dfc8d2adc46d09b4d735f29bc4f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2019
ms.locfileid: "35907641"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>핵심 데이터를 새 Office 365 데이터 센터 지역으로 이동

Office 365 for business 서비스용 새 데이터 센터 지역가 계속 해 서 열립니다. 이러한 새 데이터 센터 지역는 지속적인 고객 요구 및 사용 증가를 지원 하기 위해 용량을 추가 하 고 리소스를 계산 합니다. 또한 새 데이터 센터 지역는 핵심 고객 데이터에 대 한 상주 데이터를 제공 합니다. 

핵심 고객 데이터는 [Microsoft Online Services 조항](https://go.microsoft.com/fwlink/p/?LinkID=249048)에 정의 된 고객 데이터의 하위 집합을 지칭 하는 용어입니다. 
- Exchange Online 사서함 콘텐츠 (전자 메일 본문, 일정 항목 및 전자 메일 첨부 파일 콘텐츠)
- SharePoint Online 사이트 콘텐츠 및 해당 사이트 내에 저장 된 파일
- 비즈니스용 OneDrive에 업로드 된 파일 
  
핵심 고객 데이터가 기존 데이터 센터 지역에 이미 저장되어 있는 기존 고객은 새 데이터 센터 지역의 시작에 영향을 받지 않습니다. Microsoft는 새 데이터 센터 지역에 고유한 기능 또는 규정 준수 인증을 도입하지 않습니다. 두 지역 중 어떤 지역의 고객이든 이전과 동일한 서비스 품질, 성능 및 보안 제어를 경험할 수 있습니다. 아래 표에 나열 된 기존 고객은 rest에서 조직의 핵심 고객 데이터를 새 데이터 센터 지역으로 초기 마이그레이션을 요청 하는 옵션을 제공 합니다.
  
|청구 주소가 있는 고객 * * * *|이전 데이터 센터 지역 * * * *|새 데이터 센터 지역 * * * *|다음 이후 지역 사용 가능 * * * * * * * *|
|:-----|:-----|:-----|:-----|
|일본 * * * *| 아시아/태평양 | 일본 | 2014년 12월 |
|오스트레일리아, 뉴질랜드, 피지 * * * *| 아시아/태평양 | 오스트레일리아 | 2015년 3월 |
|인도 * * * *| 아시아/태평양 | 인도 | 2015년 10월 |
|캐나다 * * * *| 북미 | 캐나다 | 2016년 5월 |
|영국 * * * *| 유럽 | 영국 | 2016년 9월 |
|대한민국 * * * * * *| 아시아/태평양 | 대한민국 | 2017년 4월 |
|프랑스 * * * *| 유럽 | 프랑스 | 2018년 3월 |
|아랍에미리트 * * * *| 유럽 | 아랍에미리트 | 2019 년 6 월 |
|남아프리카 * * * *| 유럽 | 남아프리카 공화국 | 7 월 2019 일 |
  
새 데이터 센터 지역이 사용 가능해진 이후에 만들어진 신규 고객 또는 Office 365 테넌트의 경우 휴지 상태의 핵심 고객 데이터가 새 데이터 센터 지역에 자동으로 저장됩니다.
  
전체 데이터 센터 geos, 데이터 센터 및 나머지 고객 데이터 위치는 [대화형 데이터 센터 맵의](https://office.com/datamaps)일부로 사용할 수 있습니다. 
  
## <a name="data-residency-option"></a>데이터 상주 옵션

위 표에 나열된 데이터 센터 지역에 해당되는 기존 Office 365 고객에게는 데이터 상주 옵션이 제공됩니다. 이 옵션을 사용 하 여 데이터 상주 요구 사항을 충족 하는 고객은 나머지 조직의 핵심 고객 데이터를 새 데이터 센터 지역으로 초기에 마이그레이션할 수 있습니다.  Microsoft는 등록 창에서 초기 마이그레이션을 요청 하는 모든 적격 고객에 게 커밋된 마감 기한을 제공 합니다.  Geo 등록 창에 대 한 자세한 내용과 프로그램에 등록 하는 단계에 대 한 자세한 내용은 [데이터 이동 요청 방법을](request-your-data-move.md) 검토 하십시오.  데이터 이동은 요청 기간이 완료되고 24개월까지 소요될 수 있습니다.

작업을 수행 하지 않으면 Microsoft에서 서비스 관리 및 최적화의 일환으로 남은 시간에 따라 핵심 고객 데이터를 새 데이터 센터 지역으로 이동할 수 있습니다.핵심 고객 데이터는 다른 geo가 아닌 새 데이터 센터 지역으로만 이동할 수 있습니다.이 서비스 관리 이동이 완료 되 고 관리 센터의 데이터 위치를 업데이트 하면 메시지 센터를 통해 테 넌 트 관리자에 게 알립니다.
   
Microsoft는 새 데이터 센터 지역에 고유한 기능 또는 규정 준수 인증을 도입하지 않습니다.
    
전체적으로 운영되는 자동화 환경에서 데이터 이동을 수행할 때 수반되는 복잡성, 정밀도 및 규모 때문에 귀하의 테넌트 또는 다른 단일 테넌트에서 데이터 이동이 완료될 것으로 예상되는 시기를 알려드리기가 어렵습니다. 고객은 데이터 이동이 완료되었을 때 메시지 센터에서 관련 서비스별로 1번의 확인을 받게 됩니다. 
    
데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 서비스 작업입니다. 영향을 받을 수 있는 기능은 [During and after your data move](during-and-after-your-data-move.md) 페이지에 나와 있습니다. 가용성을 위해 [Microsoft Online SERVICES SLA (서비스 수준 계약)](https://go.microsoft.com/fwlink/p/?LinkId=523897) 를 준수 하 고, 고객이 이동 중에 대비 하거나 모니터링 해야 하는 작업이 없습니다. 서비스 유지 관리에 대한 알림은 필요한 경우에 수행됩니다. 

데이터를 새 데이터 센터 지역으로 이동 하는 것은 고객에 게 추가 비용 없이 완료 됩니다.
    
## <a name="related-topics"></a>관련 항목 
 
[데이터 이동을 요청하는 방법](request-your-data-move.md)
    
[데이터 이동 일반 FAQ](data-move-faq.md)
  
[Microsoft Dynamics CRM Online에 대 한 새로운 데이터 센터 지역](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[지역별 Azure services](https://azure.microsoft.com/en-us/regions/)
