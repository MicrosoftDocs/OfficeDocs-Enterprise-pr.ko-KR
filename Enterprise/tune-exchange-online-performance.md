---
title: Exchange Online 성능 조정
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 이 문서에서는 Exchange Online의 성능을 개선 하는 방법을 설명 하는 일반적인 팁과 기타 리소스에 대 한 링크를 제공 합니다.
ms.openlocfilehash: 4ef0276345a3d7f1c9aeba016824f9cb06c475cb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841085"
---
# <a name="tune-exchange-online-performance"></a>Exchange Online 성능 조정

이 문서에서는 특히 마이그레이션 앞에서 Exchange Online의 성능을 개선 하는 방법을 설명 하는 일반적인 팁과 기타 리소스에 대 한 링크를 제공 합니다. 이 문서는 [Office 365 프로젝트에 대 한 네트워크 계획 및 성능 조정](https://aka.ms/tune) 의 일부입니다.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Exchange Online 성능을 개선 하기 위해 고려해 야 할 사항

마이그레이션 속도를 개선 하 고 Exchange Online에 대 한 조직의 대역폭 제약 조건을 줄이려면 다음을 고려 하세요.
  
- **사서함 크기를 줄입니다.** 사서함 크기가 작을수록 마이그레이션 속도가 빨라집니다. 
    
- **Exchange 하이브리드 배포와 함께 사서함 이동 기능을 사용 합니다.** Exchange 하이브리드 배포, 오프 라인 메일 (형태의. OST 파일)은 Exchange Online으로 마이그레이션할 때 다시 다운로드할 필요가 없습니다. 이렇게 하면 다운로드 대역폭 요구 사항이 크게 줄어듭니다. 
    
- **인터넷 트래픽이 낮고 온-프레미스 Exchange가 사용 되는 기간 동안 사서함 이동이 발생 하도록 예약 합니다.** 이동이 진행 되는 동안 마이그레이션 요청은 사서함 복제 프록시로 제출 되며 즉시 수행 되지 않을 수 있습니다. 
    
- **웹용 Outlook에는 간결한 팝업을 사용 합니다.** 간결한 팝업에서는 서버에 일부 구성 요소를 렌더링 하 여 Microsoft Edge 또는 Internet Explorer에서 메모리를 많이 사용 하는 보다 작은 버전의 특정 전자 메일 메시지를 제공 합니다. 자세한 내용은 [간결한 팝업을 사용 하 여 메일 메시지를 읽을 때 사용 되는 메모리 줄이기](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)를 참조 하세요.


## <a name="general-advice"></a>일반 조언

- Outlook.office.com에 대 한 DNS 조회가 해당 위치에 대 한 논리적 입력 위치의 MS datacenter에 진입 하는지 확인 합니다.

- 사서함 캐싱을 조사 하 고 적절 한 옵션 (re)을 선택 합니다. 캐싱 기간, 공유 사서함 캐싱, et cetera).

- Outlook 데이터가 인터넷을 통과 하기 전에 VPN 연결 (중앙 사무소)을 전달 하지 않도록 합니다.

- 사서함 데이터가 폴더 및 항목 크기에 대 한 제한 사항을 준수 해야 합니다.
    
Exchange 마이그레이션 성능에 대 한 자세한 내용은 [Office 365 마이그레이션 성능 및 모범 사례](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)를 참조 하세요.
  

