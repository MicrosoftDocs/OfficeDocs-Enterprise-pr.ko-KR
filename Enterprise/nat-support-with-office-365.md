---
title: Office 365의 NAT 지원
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: '요약: NAT(Network Address Translation)를 사용하여 조직 내에서 IP 주소당 사용할 수 있는 정확한 클라이언트 수를 예측하는 방법에 대한 세부 정보를 제공합니다.'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541892"
---
# <a name="nat-support-with-office-365"></a>Office 365의 NAT 지원

 **요약:** NAT(Network Address Translation)를 사용하여 조직 내에서 IP 주소당 사용할 수 있는 정확한 클라이언트 수를 예측하는 방법에 대한 세부 정보를 제공합니다. 
  
이전에 대 한 지침 IP 주소 당 사용 하 여 Office 365에 연결 해야 하는 Exchange 클라이언트의 최대 네트워크 포트 당 약 2, 000 클라이언트 했음을 제시 합니다.
  
## <a name="why-use-nat"></a>NAT를 사용하는 이유

NAT를 사용 하 여 다양 한 회사 네트워크에 있는 사용자 수 "공유" 몇 공개적으로 라우팅 가능한 IP 주소.
  
대부분의 회사 네트워크에서는 개인(RFC1918) IP 주소 공간을 사용합니다. 개인 주소 공간은 IANA(Internet Assigned Numbers Authority)를 통해 할당되며 글로벌 인터넷으로/인터넷에서 직접 라우팅되지 않는 네트워크 전용으로 사용됩니다.
  
개인 IP 주소 공간에서 장치에 대 한 인터넷 액세스를 제공 하려면 조직은 방화벽 및 네트워크 주소 변환 (NAT) 또는 포트 주소 변환 (PAT) 서비스를 제공 하는 프록시 같은 게이트웨이 기술을 사용 합니다. 이러한 게이트웨이 내부 트래픽을 확인 (Office 365 포함)의 인터넷 장치 하나 이상의 공개적으로 라우팅 가능한 IP 주소에서 들리는 수를 표시 합니다. 서로 다른 원본 TCP 포트는 공용 IP 주소에는 내부 장치에서 각 아웃 바운드 연결으로 변환합니다. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Office 365에 개방 됨 동시에 너무 많은 연결 시간이 필요한 이유?

Outlook에서는 추가 기능, 공유 일정, 사서함 등이 있는 경우 연결을 8개 이상 열 수도 있습니다. Windows 기반 NAT 장치에서 사용 가능한 최대 포트 수는 64,000개이므로, 포트가 소모될 때까지 각 IP 주소를 최대 8,000명의 사용자가 사용할 수 있습니다. 고객이 NAT에 대해 Windows OS를 기반으로 하지 않는 장치를 사용하는 경우 사용 가능한 총 포트 수는 사용 중인 NAT 장치 또는 소프트웨어에 따라 다릅니다. 이러한 경우 최대 포트 수는 64,000개보다 적을 수 있습니다. 포트 사용 가능성은 다른 요인에도 영향을 받는데, 예를 들어 자체 사용을 위해 포트 4,000개를 제한하는 Windows에서는 사용 가능한 총 포트 수가 60,000개로 줄어듭니다. 또한 동시에 연결이 가능하여 추가 포트가 필요한 Internet Explorer 등의 기타 응용 프로그램이 있을 수도 있습니다.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Office 365와 함께 단일 공용 IP 주소 뒤에 최대 지원 되는 장치 수 계산

단일 공용 IP 주소 뒤에 있는 장치의 최대 수를 확인 하려면 클라이언트 당 최대 포트 사용량을 확인 하려면 네트워크 트래픽을 모니터링 해야 합니다. 또한 포트 사용량 (최소 4)에 대 한 최대 계수를 사용할 해야 합니다. 
  
 **다음 수식을 사용 하 여 IP 주소 당 지원 되는 장치 수를 계산 합니다.**
  
단일 공용 IP 주소 뒤에 장치를 지원 되는 최대 = (64000-제한 된 포트) / (최대 포트 사용량 + 최대 계수)
  
 **예: true 인 다음 하는 경우:**
  
- 운영 체제에 대 한 **제한 된 포트:** 4000 
    
- 장치당 **최대 포트 사용량:** 6 
    
- **최대 계수:** 4 
    
그런 다음, 지원 되는 최대 장치 단일 공용 IP 주소 뒤에 = (64000 4000) / (6 + 4) = 6000
  
호스팅 팩, Microsoft Office Outlook 2007 용 2011 년 9 월 또는 Microsoft Outlook 2010 용 2011 년 11 월에서 업데이트 또는 이후의 업데이트, Outlook (두 Office Outlook 2007과 함께 서비스에서에서 연결 수에 포함 된 Office 365의 릴리스와 함께 2와 Outlook 2010 팩)를 Exchange 2 정도로 적은 수 있습니다. 다른 운영 체제, 포트는 최대에서 네트워크에 필요한 최소 및 최대 수를 결정 하는 등 사용자 동작에에서 영향을 주지 필요 합니다.
  
단일 공용 IP 주소 뒤에 더 많은 장치를 지원 하려면 장치 지원 될 수 있는 최대 수를 평가 단계를 수행 합니다.
  
클라이언트 당 최대 포트 사용량을 확인 하려면 네트워크 트래픽을 모니터링 합니다. 이 데이터를 수집 해야 합니다.
  
- 여러 위치에서
    
- 여러 장치에서
    
- 여러 번에 걸쳐
    
위의 수식을 사용하여 환경에서 지원할 수 있는 IP 주소당 최대 사용자 수를 계산합니다.
  
추가 공용 IP 주소를 클라이언트 부하 분산에 대 한 다양 한 방법이 있습니다. 사용 가능한 전략 회사 게이트웨이 솔루션의 기능에 따라 달라 집니다. 간단한 솔루션은 사용자 주소 공간을 분리 하 고 정적으로 "할당" 다양 한 IP 주소를 각 게이트웨이에 하는 것입니다. 다른 많은 게이트웨이 장치를 제공 하는 방법은 풀의 IP 주소를 사용 하는 기능입니다. 주소 풀의 장점은 훨씬 더 동적이 고 사용자 수가 늘어남에 따라 조정을 요구 하도록 되지 않을 것입니다.
  
## <a name="see-also"></a>참고 항목

[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

