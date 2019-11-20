---
title: NAT 지원(Office 365)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: '요약: NAT (Network Address Translation)를 사용 하 여 조직 내에서 IP 주소당 사용할 수 있는 정확한 클라이언트 수를 대략적으로 결정 하는 방법에 대해 자세히 설명 합니다.'
ms.openlocfilehash: 5d252b059661fdd3bad1f86bf552f44b8a747d24
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747902"
---
# <a name="nat-support-with-office-365"></a>NAT 지원(Office 365)

*이 문서는 Office 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*

이전에는 네트워크 포트당 약 2000 클라이언트에서 IP 주소당 365에 사용 해야 하는 최대 Exchange 클라이언트 수를 제안 했습니다.
  
## <a name="why-use-nat"></a>NAT를 사용 하는 이유

NAT를 사용 하 여 회사 네트워크에 있는 수천 명의 사용자가 공용으로 라우팅할 수 있는 IP 주소를 몇 개 "공유" 할 수도 있습니다.
  
대부분의 회사 네트워크는 개인 (RFC1918) IP 주소 공간을 사용 합니다. 개인 주소 공간은 인터넷에서 할당 된 번호 기관 (IANA)에 의해 할당 되며 전역 인터넷으로 직접 라우팅 되지 않는 네트워크 에서만 사용 됩니다.
  
개인 IP 주소 공간에서 장치에 대 한 인터넷 액세스를 제공 하기 위해 조직은 NAT (network address translation) 또는 PAT (포트 주소 변환) 서비스를 제공 하는 방화벽과 같은 게이트웨이 기술을 사용 합니다. 이러한 게이트웨이는 내부 장치에서 인터넷으로의 트래픽 (Office 365 포함)을 공용으로 라우팅할 수 있는 하나 이상의 IP 주소에서 보내는 것으로 표시 합니다. 내부 장치에서의 각 아웃 바운드 연결은 공용 IP 주소의 다른 원본 TCP 포트로 변환 됩니다. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Office 365에서 여러 연결이 동시에 열리도록 해야 하는 이유는 무엇 인가요?

Outlook에서는 추가 기능, 공유 일정, 사서함 등이 있는 경우 8 개 이상의 연결을 열 수 있습니다. Windows 기반 NAT 장치에서는 최대 64000 개의 포트를 사용할 수 있으므로 포트를 모두 사용 하기 전에 IP 주소 뒤에 최대 8000 명의 사용자가 있을 수 있습니다. 고객이 NAT에 대해 비 Windows OS 기반 장치를 사용 하는 경우 사용할 수 있는 총 포트는 사용 중인 NAT 장치나 소프트웨어에 따라 달라 집니다. 이 시나리오에서 포트의 최대 수는 64000 보다 작을 수 있습니다. 포트를 사용 하는 경우에도 Windows 제한 4000 포트와 같은 다른 요인의 영향을 받으며, 사용할 수 있는 총 포트 수가 60, 000 개까지 줄어듭니다. Internet Explorer와 같이 동시에 연결할 수 있는 다른 응용 프로그램이 있을 수 있습니다. 추가 포트를 요구 합니다.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Office 365을 사용 하 여 단일 공용 IP 주소에서 지원 되는 최대 장치 계산

단일 공용 IP 주소에 포함 되는 최대 장치 수를 확인 하려면 네트워크 트래픽을 모니터링 하 여 클라이언트당 최대 포트 사용량을 확인 해야 합니다. 또한 포트 사용 (최소 4)에 대해 최대 인수를 사용 해야 합니다. 
  
 **다음 수식을 사용 하 여 IP 주소당 지원 되는 장치 수를 계산 합니다.**
  
단일 공용 IP 주소에서 지원 되는 최대 장치 수 = (64000-제한 된 포트)/(최대 포트 소비 + 피크 계수)
  
 **예를 들어 다음과 같은 경우를 예로 들 있습니다.**
  
- **제한 된 포트:** 운영 체제의 경우 4000

- **최대 포트 소비:** 장치당 6 개

- **최대 인수:** 4

그런 다음 단일 공용 IP 주소에서 지원 되는 최대 장치 수 = (64000-4000)/(6 + 4) = 6000
  
Office 365 호스팅 팩을 사용 하는 경우 Microsoft Office Outlook 2007 용 2011 년 9 월에 제공 되는 업데이트 또는 Microsoft Outlook 2010의 11 월 2011 또는 이후 업데이트에 포함 된 Outlook의 연결 수 (Office Outlook 2007 with Service Exchange에 대 한 팩 2 및 Outlook 2010)는 2 개까지 사용할 수 있습니다. 네트워크 사용량이 최대 수준으로 요구 되는 최소 및 최대 포트 수를 결정 하려면 여러 운영 체제, 사용자 동작 등의 요소를 고려해 야 합니다.
  
단일 공용 IP 주소에서 더 많은 장치를 지원 하려면 설명 된 단계에 따라 지원 가능한 최대 장치 수를 평가 합니다.
  
네트워크 트래픽을 모니터링 하 여 클라이언트당 최대 포트 사용량을 확인 합니다. 다음 데이터를 수집 해야 합니다.
  
- 여러 위치에서
    
- 여러 장치에서
    
- 여러 번에
    
이전 공식을 사용 하 여 환경에서 지원할 수 있는 IP 주소당 당 최대 사용자 개수를 계산 합니다.
  
클라이언트 부하를 추가 공용 IP 주소에 분산 하는 방법에는 여러 가지가 있습니다. 사용 가능한 전략은 회사 게이트웨이 솔루션의 기능에 따라 달라 집니다. 가장 간단한 방법은 사용자 주소 공간을 분할 하 고 각 게이트웨이에 여러 IP 주소를 정적으로 "할당" 하는 것입니다. 많은 게이트웨이 장치에서 제공 하는 또 다른 대안은 IP 주소 풀을 사용 하는 기능입니다. 주소 풀의 이점은 보다 동적이 고 사용자 기반이 증가 함에 따라 조정이 필요할 가능성이 더 낮습니다.
  
## <a name="see-also"></a>참고 항목

[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
