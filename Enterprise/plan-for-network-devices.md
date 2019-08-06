---
title: Office 365 서비스에 연결되는 네트워크 장치 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: '요약: Office 365에 연결 하는 데 사용 되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대 한 고려 사항을 설명 합니다.'
ms.openlocfilehash: b6804e7922178a3b653b3767a33e02e2a382ef93
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722627"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Office 365 서비스에 연결되는 네트워크 장치 계획

 **요약**: Office 365에 연결 하는 데 사용 되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대 한 고려 사항을 설명 합니다.
  
일부 네트워크 하드웨어에서는 지원 되는 동시 세션 수에 제한이 있을 수 있습니다. 사용자가 2000 명 이상인 조직의 경우 네트워크 장치를 모니터링 하 여 추가 Office 365 서비스 트래픽을 처리할 수 있는지 확인 하는 것이 좋습니다. SNMP (Simple Network Management Protocol) 모니터링 소프트웨어를 통해이 작업을 수행할 수 있습니다.

||
|:-----|
| 이 문서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)의 일부입니다.|

온-프레미스 나가는 인터넷 프록시 설정도 클라이언트 응용 프로그램에 대 한 Office 365 서비스 연결에 영향을 줍니다. 또한 Microsoft 클라우드 서비스 Url 및 응용 프로그램에 대 한 연결을 허용 하도록 네트워크 프록시 장치를 구성 해야 합니다. 모든 조직은 서로 다릅니다. Microsoft가이 프로세스를 관리 하는 방법 및 구축 하는 대역폭의 양에 대 한 아이디어를 얻으려면 [사례 연구를 읽어보십시오](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
다음 비즈니스용 Skype 도움말 문서에는 비즈니스용 Skype 설정에 대 한 자세한 정보가 나와 있습니다.
  
- [관리자에 대 한 비즈니스용 Skype Online 로그인 오류 해결](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [온-프레미스 방화벽이 연결을 차단 하므로 비즈니스용 Skype에 연결할 수 없거나 특정 기능이 작동 하지 않습니다.](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> 이러한 설정 중 상당수는 비즈니스용 Skype에 따라 다르지만 네트워크 구성에 대 한 일반적인 지침은 모든 Office 365 서비스에 유용 합니다.
  
## <a name="determining-network-capacity"></a>네트워크 용량 확인

연결에 있는 모든 네트워크 장치에는 용량 제한이 있습니다. 이러한 장치에는 클라이언트 및 서버 네트워크 어댑터, 라우터, 스위치 및 허브를 상호 연결 하는 허브가 포함 됩니다. 적절 한 네트워크 용량을 통해 포화 상태인 것은 아닙니다. 네트워크 활동 모니터링은 모든 네트워크 장치의 실제 부하를 최대 용량 보다 작게 유지 하는 데 반드시 필요 합니다. 네트워크 용량은 프록시 장치 성능에 영향을 줍니다.
  
대부분의 경우 인터넷 연결 대역폭은 트래픽 크기에 대 한 제한을 설정 합니다. 인터넷 링크를 과도 하 게 사용 하 여 트래픽이 가장 많이 발생 하는 경우에는 성능이 저하 될 수 있습니다. 이 상황은 지점용 본사에서 느린 WAN (광역 네트워크) 링크를 통해 분기 사무실 프록시 서버 컴퓨터가 프록시 장치에 연결 되는 지점 시나리오에도 적용 됩니다.
  
네트워크 용량을 테스트 하려면 프록시 네트워크 인터페이스에서 네트워크 활동을 모니터링 합니다. 네트워크 인터페이스의 최대 대역폭 중 75% 이상이 면 적절 하지 않은 네트워크 인프라의 대역폭을 늘리는 것이 좋습니다. 또는 HTTP 압축과 같은 고급 기능을 사용 하는 것이 좋습니다.
  
## <a name="wan-accelerators"></a>WAN 가속기

조직에서 WAN (wide area network) 가속 프록시 기기를 사용 하는 경우에는 Office 365 서비스에 액세스할 때 문제가 발생할 수 있습니다. 사용자가 Office 365에 액세스할 때 일관 된 환경을 유지 하도록 네트워크 장치 또는 장치를 최적화 해야 할 수 있습니다. 예를 들어 Office 365 서비스는 일부 Office 365 콘텐츠 및 TCP 헤더를 암호화 합니다. 장치가 이러한 유형의 트래픽을 처리 하지 못할 수 있습니다.
  
[Office 365에서 WAN 최적화 컨트롤러 또는 트래픽/검사 장치를 사용 하는](https://support.microsoft.com/kb/2690045)방법에 대 한 지원 설명을 읽으십시오.
  
## <a name="hardware-and-software-load-balancing-devices"></a>하드웨어 및 소프트웨어 부하 분산 장치

조직에서 AD FS (Active Directory Federation Services) 서버 및/또는 Exchange 하이브리드 서버에 요청을 배포 하려면 HLB (하드웨어 부하 분산 장치) 또는 NLB (네트워크 부하 분산) 솔루션을 사용 해야 합니다. 부하 분산 장치는 온-프레미스 서버에 대 한 네트워크 트래픽을 제어 합니다. 이러한 서버는 single sign-on 및 Exchange 하이브리드 배포의 가용성을 보장 하는 데 매우 중요 합니다.
  
Windows Server에 기본 제공 되는 소프트웨어 기반 NLB 솔루션을 제공 합니다. Office 365는이 솔루션을 지원 하 여 부하 분산을 수행 합니다.
  
## <a name="firewalls-and-proxies"></a>방화벽과 프록시

Office 365에 연결 하기 위한 방화벽 및 프록시 구성에 대 한 자세한 내용, office [365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [office 365 네트워크 연결 평가](assessing-network-connectivity.md)및 [office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) 에 대 한 자세한 내용은 장치 및 회로에 대 한 자세한 내용을 참조 하세요. 영역의.
  
## <a name="see-also"></a>참고 항목

[Office 365 서비스 배포 관리자](deployment-advisors-for-office-365.md)
