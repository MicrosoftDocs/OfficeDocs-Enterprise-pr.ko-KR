---
title: Office 365 서비스에 연결되는 네트워크 장치 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
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
description: '요약: Office 365에 연결하는 데 사용되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대한 고려 사항을 설명합니다.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933125"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Office 365 서비스에 연결되는 네트워크 장치 계획

 **요약**: Office 365에 연결하는 데 사용되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대한 고려 사항을 설명합니다.
  
일부 네트워크 하드웨어 지원 되는 동시 세션 수에 제한이 가질 수 있습니다. 사용자 들이 2, 000 개 이상의 조직에서는 추가 Office 365 서비스 트래픽을 처리할 수 있는지 확인 하도록 네트워크 장치를 모니터링 하는 것이 좋습니다. 단순 네트워크 관리 프로토콜 (SNMP) 소프트웨어 모니터링은이 작업을 수행 하는 데 도움이 됩니다.

||
|:-----|
| 이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.|

온-프레미스 보내는 인터넷 프록시 설정 클라이언트 응용 프로그램에 대 한 Office 365 서비스에 대 한 연결에도 영향을 줍니다. Microsoft 클라우드 서비스 Url 및 응용 프로그램에 대 한 연결을 허용 하도록 네트워크 프록시 장치로 구성 해야 합니다. 모든 조직은 다릅니다. Microsoft는이 프로세스 및 대역폭을 관리 하는 방법에 대 한 아이디어를 가져오려면는 프로 비전, [사례 연구 읽기](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)합니다.
  
비즈니스 도움말 문서에 대 한 다음 Skype 비즈니스 설정에 대 한 Skype 하는 방법에 대 한 자세한 내용은 있습니다.
  
- [관리자를 위한 비즈니스 Online 로그인 오류에 대 한 문제해결 Skype](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [비즈니스, 용 Skype에 연결할 수 없거나 특정 기능이 작동 하지 않으면 온-프레미스 방화벽이 연결을 차단 하기 때문에](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> 이러한 설정의 대부분은 비즈니스 관련 용 Skype, 하는 동안 네트워크 구성에 대 한 일반적인 지침은 모든 Office 365 서비스에 유용 합니다.
  
## <a name="determining-network-capacity"></a>네트워크 용량 결정

연결에 있는 모든 네트워크 장치에는 용량 제한이 있습니다. 이러한 장치에는 장치들을 서로 연결하는 클라이언트 및 서버 네트워크 어댑터, 라우터, 스위치, 허브 등이 포함됩니다. 네트워크 용량이 충분하면 이러한 네트워크 장치가 포화 상태가 되지 않습니다. 네트워크 활동 모니터링은 모든 네트워크 장치의 실제 로드를 최대 용량 미만으로 유지하는 데 중요합니다. 네트워크 용량은 프록시 장치 성능에 영향을 줍니다. 네트워크 용량은 프록시 장치 성능에 영향을 줍니다.
  
대부분의 경우 인터넷 연결 대역폭 트래픽 양에 대 한도 설정합니다. 사용량이 가장 많은 트래픽 시간 동안 약한 성능은 잠재적인 인터넷 링크의 과도 하 게 사용 하 여 발생 합니다. 이 상황은 지점 시나리오의 경우, 느린 넓은 WAN (광역 네트워크) 링크를 통해 지점 프록시 서버 컴퓨터 분기의 본사에서 프록시 장치에 연결 된 위치에 적용 됩니다.
  
네트워크 용량을 테스트 하려면 프록시 네트워크 인터페이스에 대 한 네트워크 활동을 모니터링 합니다. 모든 네트워크 인터페이스의 최대 대역폭의 75% 보다 많은 경우에 적절 한 없는 네트워크 인프라의 대역폭을 늘리면 하는 것이 좋습니다. 또는 HTTP 압축 등의 고급 기능을 사용 하 여 것이 좋습니다.
  
## <a name="wan-accelerators"></a>WAN 가속기

조직 광역 네트워크 (WAN) 가속 프록시 장치를 사용 하는 경우에 Office 365 서비스에 액세스할 때 문제가 발생할 수 있습니다. 네트워크 장치 또는 Office 365에 액세스할 때 사용자에 게 일관 된 환경을 권한이 있는지 확인 하는 장치를 최적화 해야할 수 있습니다. 등 Office 365 서비스의 일부 Office 365 콘텐츠 및 TCP 헤더를 암호화 합니다. 장치 이러한 종류의 트래픽 처리할 수 있습니다.
  
[WAN 최적화 컨트롤러를 사용 하 여 또는 Office 365를 사용 하 여 트래픽을/검사 장치에](https://support.microsoft.com/kb/2690045)대 한 지원 정보를 보호 정책을 읽어보십시오.
  
## <a name="hardware-and-software-load-balancing-devices"></a>하드웨어 및 소프트웨어 부하 분산 장치

조직에서는 HLB(하드웨어 부하 분산 장치) 또는 NLB(네트워크 부하 분산) 솔루션을 사용하여 요청을 AD FS(Active Directory Federation Services) 서버 및/또는 Exchange 하이브리드 서버로 분산시켜야 합니다. 부하 분산 장치는 온-프레미스 서버에 대한 네트워크 트래픽을 제어합니다. Single Sign-On 및 Exchange 하이브리드 배포를 사용 가능한 상태로 유지하려면 이러한 서버가 반드시 필요합니다.
  
Windows 서버에 기본 제공 되는 소프트웨어 기반 NLB 솔루션을 제공 합니다. Office 365 부하 분산을 달성 하기 위해이 솔루션을 지원 합니다.
  
## <a name="firewalls-and-proxies"></a>방화벽 및 프록시

대 한 자세한 내용은 방화벽 및 프록시 장치 및 회로 선택 하는 방법에 대 한 자세한 내용은 [Office 365 관리 끝점](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Office 365에 대 한 네트워크 연결](network-connectivity.md)및 [Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) 읽고 Office 365에 연결을 구성 합니다.
  
## <a name="see-also"></a>참고 항목

[Office 365 서비스 배포 관리자](deployment-advisors-for-office-365.md)
