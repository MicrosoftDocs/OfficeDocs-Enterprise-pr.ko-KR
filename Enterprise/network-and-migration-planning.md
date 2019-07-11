---
title: Office 365의 네트워크 및 마이그레이션 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 네트워크 계획 및 테스트에 대 한 정보 링크와 Office 365로의 마이그레이션에 대 한 링크가 포함 되어 있습니다.
ms.openlocfilehash: 572910f2104ecd90e78bcfe37b2b022ddb3893fa
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616783"
---
# <a name="network-and-migration-planning-for-office-365"></a>Office 365의 네트워크 및 마이그레이션 계획

이 문서에는 네트워크 계획 및 테스트에 대 한 정보와 Office 365로의 마이그레이션에 대 한 링크가 포함 되어 있습니다.
  
처음으로 배포 하거나 Office 365로 마이그레이션하기 전에 다음 항목의 정보를 사용 하 여 필요한 대역폭을 예상 하 고 테스트 하 여 Office 365로 배포 하거나 마이그레이션할 대역폭이 충분 한지 확인할 수 있습니다.

||
|:-----|
| 이 문서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)의 일부입니다.|

|||
|:-----|:-----|
|![엔터프라이즈 설계자 포스터 용 Microsoft 클라우드 네트워킹 참조](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Office 365 및 기타 Microsoft 클라우드 플랫폼 및 서비스에 대 한 네트워크를 최적화 하는 단계는 [Microsoft 클라우드 네트워킹 For 엔터프라이즈 설계자](https://aka.ms/cloudarchnetworking) 포스터를 참조 하세요. |
   
## <a name="estimate-network-bandwidth-requirements"></a>네트워크 대역폭 요구 사항 예상
<a name="EstimateBandwidthRequirements"> </a>

Office 365을 사용 하면 조직의 인터넷 회로 사용률이 향상 될 수 있습니다. 최대 일 수를 처리 하기 위해 20%의 용량을 남겨 두고 Office 365이 완전히 배포 되 면 현재 사용 가능한 대역폭의 양이 충분 한지를 확인 하는 것이 중요 합니다.
  
대역폭을 예상 하려면 다음 단계를 사용 합니다.
  
1. 각 인터넷 송신을 사용할 클라이언트 수를 평가 합니다. 다중 terabit 네트워크가 가능한 한 많은 연결을 처리 하도록 합니다. 
    
2. 클라이언트에서 사용할 수 있는 Office 365 서비스 및 기능을 결정 합니다. 다른 서비스 또는 사용 프로필을 가진 사용자 그룹을 사용할 수 있습니다.
    
3. 파일럿 클라이언트 그룹의 네트워크 사용을 측정 합니다. 파일럿 클라이언트가 각 지리적 위치 뿐 아니라 조직에 있는 각 사용자의 프로필을 대표 하는지 확인 합니다. [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)및 [비즈니스용 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551) 에 대 한 이전 계산기와 자신의 네트워크에서 수행한 [사례 연구](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) 에 대해 결과를 상호 확인할 수 있습니다. 
    
4. 파일럿 그룹의 측정값을 사용 하 여 전체 조직의 요구 사항을 추정 하 고 다시 테스트 하 여 네트워크를 변경 하기 전 까지의 추정치를 확인 합니다.
    
## <a name="test-your-existing-network"></a>기존 네트워크 테스트
<a name="calculators"> </a>

 **네트워크 도구** 인터넷 대역폭을 테스트 하 고 유효성을 검사 하 여 다운로드, 업로드 및 대기 시간 제한을 확인 합니다. 이러한 도구는 마이그레이션에 대 한 네트워크 기능 뿐 아니라 완벽 하 게 배포 된 후에도 결정 하는 데 도움이 됩니다. 
  
- [Microsoft Message analyzer](https://technet.microsoft.com/library/jj649776.aspx): 메시지 분석기는 네트워크 문제 해결을 위한 효과적인 도구입니다. 메시지 분석기는 프로토콜 기반 메시징 트래픽 및 시스템 메시지를 캡처, 표시 및 분석 합니다. 또한 메시지 분석기를 사용 하 여 로그 및 추적 파일에서 데이터를 가져오고, 집계 하 고, 분석할 수 있습니다.
    
- [Microsoft 원격 연결 분석기](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 환경에서 연결을 테스트 합니다.
    
- [Office 365 용 Microsoft 지원 및 복구 도우미](https://diagnostics.office.com/#/Download?env=SOC) 를 사용 하 여 Outlook 및 Office 365 문제를 해결 합니다. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>네트워크 계획을 위한 모범 사례 및 Office 365의 마이그레이션 성능 개선
<a name="BestPractices"> </a>

Office 365 환경을 개선 하는 방법에 대 한 자세한 내용을 보려면 이러한 모범 사례를 자세히 살펴보겠습니다.
  
1. 사용자를 즉시 활용할 수 있도록 하기 원하십니까? 네트워크가 너무 많이 사용 되지 않는 경우 SharePoint Online, Exchange Online, Lync Online 등 Office 365 사용에 대 한 팁을 보려면 [느린 네트워크에서 office 365을 사용할](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) 때 유용한 정보를 참조 하세요. 이 문서에서는 Office 365 환경을 최적화 하기 위해 TechNet 및 Support.office.com의 콘텐츠 로드에 대해 설명 하 고, 웹 페이지를 사용자 지정 하는 간편한 방법 및 최상의 Office 365 환경을 위한 Internet Explorer 설정을 설정 하는 방법에 대 한 정보를 제공 합니다. 
    
2. Office [365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 을 읽고 office 365 트래픽을 안전 하 게 관리 하 고 가능한 최적의 성능을 얻는 데 필요한 연결 원칙을 이해 합니다. 이 문서는 Office 365 네트워크 연결을 안전 하 게 최적화 하기 위한 가장 최근 지침을 이해 하는 데 도움이 됩니다. 
    
3. Windows 업데이트 일정을 신중 하 게 관리 하 여 메일 마이그레이션 성능을 향상 시킵니다. 클라이언트 컴퓨터를 일괄적으로 업데이트 하 고 네트워크 대역폭 사용을 조정 하기 위해 Office 365로 마이그레이션하기 전에 모든 클라이언트 컴퓨터가 업데이트 되는지 확인할 수 있습니다. 자세한 내용은 [최신 업데이트에 대 한 Office 365 데스크톱 수동 업데이트 및 구성을](https://support.microsoft.com/gp/office-2013-365-update)참조 하십시오.
    
4. Office 365 네트워크 트래픽은 신뢰할 수 있는 인터넷 서비스로 취급 되 고 일부 조직에서 신뢰할 수 없는 인터넷 서비스에 대 한 네트워크 트래픽을 수행 하는 일반적인 필터링 및 검색 기능을 많이 사용 하지 않을 때 가장 적합 합니다. 여기에는 일반적으로 프록시 사용자 인증 및 패킷 검사와 같은 아웃 바운드 처리를 제거 하 고 올바른 NAT (Network Address Translation)를 사용 하 여 인터넷에 대 한 로컬 송신을 보장 하 고 증가 된 대역폭 용량을 처리할 수 있는 충분 한 공간이 포함 됩니다 네트워크 요청 네트워크에서 신뢰할 수 있는 인터넷 서비스로 Office 365를 처리 하도록 네트워크를 구성 하는 방법에 대 한 추가 지침은 [office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)를 참조 하세요.
    
1. [Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)를 확인 합니다. Office 365로 들어오는 추가 트래픽으로 인해 아웃 바운드 프록시 연결이 증가 하 고 TLS/SSL을 통한 보안 트래픽이 증가 합니다.
    
2. 아웃 바운드 프록시에 사용자 인증이 필요한 경우 연결 속도가 느리거나 기능 손실이 발생할 수 있습니다. Office 365 도메인에 대 한 인증 요구 사항을 건너뛰면 이러한 오버 헤드를 줄일 수 있습니다.
    
3. 공유 일정 및 사서함의 수가 많은 경우 Outlook에서 Exchange로의 연결 수가 증가 하는 것을 확인할 수 있습니다. 예를 들어 Outlook 클라이언트는 사용 중인 각 공유 일정에 대해 최대 2 개의 추가 연결을 열 수 있습니다. 이러한 상황에서는 egress 프록시가 연결을 처리할 수 있도록 하거나 Outlook에 대 한 Office 365 연결에 프록시를 사용 하지 않도록 합니다.
    
4. 공용 IP 주소에 대해 지원 되는 최대 장치 수와 여러 IP 주소 간의 로드 균형을 조정 하는 방법을 결정 합니다. 자세한 내용은 [Office 365에서 NAT 지원](nat-support-with-office-365.md)를 참조 하세요.
    
5. 네트워크의 컴퓨터에서 나가는 아웃 바운드 연결을 조사 하는 경우, Office 365 도메인에 대 한이 필터링을 우회 하면 연결 및 성능이 향상 됩니다. 또한 아웃 바운드 검사를 우회 하면 단일 인터넷 송신이 필요 하지 않으며 Office 365에서 전송 된 네트워크 요청에 대해 로컬 인터넷 송신을 사용 하도록 설정 하기도 합니다.
    
6. 일부 고객이 내부 네트워크 설정을 발견 하면 성능에 영향을 줄 수 있습니다. MTU (최대 전송 단위) 크기, 네트워크 자동 협상, 자동 검색 및 인터넷에 대 한 하위 최적 경로와 같은 설정은 일반적인 모습입니다.
    
## <a name="network-planning-reference-for-office-365"></a>Office 365에 대 한 네트워크 계획 참조
<a name="NetReference"> </a>

이러한 항목에는 자세한 Office 365 네트워크 참조 정보가 포함 되어 있습니다.
  
- [Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [클라이언트 연결](client-connectivity.md)
    
- [콘텐츠 배달 네트워크](content-delivery-networks.md)
    
- [Office 365에 대한 외부 Domain Name System 레코드](external-domain-name-system-records.md)
    
- [Office 365 서비스의 IPv6 지원](ipv6-support.md)
    
- [Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples)
    
- [Office 365 비디오 네트워킹에 대 한 질문과 대답 (FAQ)](office-365-video-networking-faq.md)
    
- [Office 365 서비스에 연결되는 네트워크 장치 계획](plan-for-network-devices.md)
    
- [Office 365 서비스 배포 관리자](deployment-advisors-for-office-365.md)
 