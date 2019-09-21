---
title: 서비스 거부 공격에 대해 클라우드 서비스를 방어 하는 Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Microsoft가 해당 클라우드 서비스를 DoS (서비스 거부) 공격에 defends 하는 방법입니다.
ms.openlocfilehash: ad15349832c36a7dceae59503055606999a3193c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067685"
---
# <a name="defending-microsoft-cloud-services-against-denial-of-service-attacks"></a>서비스 거부 공격에 대해 Microsoft 클라우드 서비스 방어

## <a name="introduction"></a>소개
Microsoft 데이터 센터는 경계 펜스, 비디오 카메라, 보안 담당자 및 생체 인식, 스마트 카드 및 다단계 인증을 사용 하는 보안 entrances 포함 된 심층 방어 보안으로 보호 됩니다. 심층 방어 보안은 모든 기능의 모든 영역과 각 물리적 서버 단위를 통해 진행 됩니다. [Microsoft 클라우드 인프라 및 운영 그룹](https://www.microsoft.com/en-us/cloud-platform/global-datacenters) 은 클라우드 서비스에 대 한 핵심 인프라 및 기본 기술을 제공 합니다. 이 데이터 센터는 물리적 보안 및 안정성을 위한 업계 표준을 준수 하며, Microsoft 운영 담당자가 관리 하 고 모니터링 하 고 관리 합니다.

클라우드 서비스를 추가로 보호 하기 위해 Microsoft는 Microsoft Azure 지속적인 모니터링 및 침투 테스트 프로세스의 일부인 DDoS 방어 시스템을 제공 합니다. Azure DDoS 방어 시스템은 외부, 다른 Azure 테 넌 트 로부터의 공격에 대 한 견딜 수 있도록 설계 되었습니다. Azure는 SYN 쿠키, 속도 제한, 연결 제한 등의 표준 검색 및 완화 기술을 사용 하 여 DDoS 공격 으로부터 보호 합니다.

Microsoft의 클라우드 서비스는 여러 원본의 공격 위협을 받게 됩니다. 다양 한 DoS 위협을 완화 하 고 보호 하기 위해 DoS에서 기본 인프라를 보호 하는 기본 목표를 사용 하 여 확장성이 높고 동적인 Azure 기반 위협 감지 및 완화 시스템을 개발 및 구현 했습니다. 클라우드 서비스 고객에 대 한 서비스 중단을 방지 하 고 지원 합니다. Azure DoS 완화 시스템은 인바운드, 아웃 바운드 및 지역 간 트래픽을 보호 합니다.

OSI ( [Open Systems](https://docs.microsoft.com/windows-hardware/drivers/network/windows-network-architecture-and-the-osi-model) transport) 모델의 네트워크 (L3) 및 전송 (L4) 계층에서 대상에 대해 대부분의 DoS 공격이 시작 되었습니다. L3 및 L4 계층에서 지시 되는 공격은 네트워크 인터페이스 또는 서비스를 지나치게 빠르게 리소스에 대 한 공격 트래픽을 방지 하 고 합법적인 트래픽에 대응 하는 기능을 거부할 수 있도록 설계 되었습니다. 특히 L3 및 L4 공격은 네트워크 링크, 장치 또는 서비스의 용량을 포화 또는 응용 프로그램을 지 원하는 가상 컴퓨터 또는 서버에 대 한 Cpu를 지나치게 활용 하려고 시도 합니다.

L3 및 L4 공격 으로부터 보호 하기 위해 Microsoft는 이러한 계층을 보호 하 여 공격에 들어오는 인프라 및 고객 목표를 관리 하기 위한 솔루션을 설계, 개발 및 배포 했습니다. 인프라 보호를 사용 하면 한 고객에 게 제공 되는 공격 트래픽으로 인해 다른 고객의 네트워크 품질에 대 한 피해가 손상 되거나 감소 하지 않을 수 있습니다. 이 솔루션은 데이터 센터 라우터의 트래픽 샘플링 데이터를 사용 합니다. 이 데이터는 공격을 감지 하기 위해 네트워크 모니터링 서비스에 의해 분석 됩니다. 공격이 감지 되 면 자동 방어 메커니즘이 시작 됩니다.

## <a name="application-level-defenses"></a>응용 프로그램 수준 방어
Microsoft 엔지니어링 팀은 [Microsoft 운영 보안 보증](https://www.microsoft.com/en-us/SDL/OperationalSecurityAssurance) 에 의해 설정 된 엄격한 표준을 따라 고객 데이터를 보호 합니다. Microsoft의 클라우드 서비스는 응용 프로그램 수준 DoS 공격을 방지 하 고 완화할 뿐 아니라 매우 높은 부하를 지원 하도록 의도적으로 구축 되었습니다. Microsoft는 일부 작업 부하의 지역별 격리 및 제한 기능을 통해 여러 전역 데이터 센터에 서비스를 분산 하는 수평 확장 아키텍처를 구현 했습니다.

서비스의 초기 설치 중에 고객 관리자가 식별 하는 각 고객의 국가 또는 지역에 따라 해당 고객의 데이터에 대 한 기본 저장 위치가 결정 됩니다. 고객 데이터는 기본/백업 전략에 따라 중복 데이터 센터 간에 복제 됩니다. 기본 데이터 센터는 소프트웨어에서 실행 되는 모든 기본 고객 데이터와 함께 응용 프로그램 소프트웨어를 호스트 합니다. 백업 데이터 센터는 자동 장애 조치 (failover)를 제공 합니다. 기본 데이터 센터가 어떤 이유로 든 작동을 중단 하면 요청이 백업 데이터 센터의 소프트웨어 및 고객 데이터 복사본으로 리디렉션됩니다. 주어진 시간에는 기본 또는 백업 데이터 센터에서 고객 데이터를 처리할 수 있습니다. 데이터 센터 여러 개를 분산 하는 경우에는 한 데이터 센터가 공격에 대비 하 여 영향을 받는 화면 영역이 줄어듭니다 또한 영향을 받는 데이터 센터의 서비스를 보조 데이터 센터에 복구 메커니즘 중 하나로 빠르게 리디렉션할 수 있으며, 서비스를 복원한 후에는 해당 데이터 센터에 다시 리디렉션될 수도 있습니다.

개별 작업에는 리소스 사용률을 관리 하는 기본 제공 기능이 포함 되어 있습니다. 예를 들어 Exchange Online 및 SharePoint Online의 제한 메커니즘은 DoS 공격 으로부터 방어 하기 위한 다계층 접근 방식에 속합니다. Exchange Online 사용자에 대 한 제한은 최종 사용자가 사용 하는 리소스, 즉 리소스가 Active Directory, Exchange Online 정보 저장소 또는 다른 위치에 있는지에 따라 달라 집니다. 예산은 각 클라이언트에 할당 되어 사용자가 사용 하는 리소스를 제한 합니다. 사용자 활동 및 시스템 구성 요소에 대 한 Exchange Online 제한은 [작업 관리](http://technet.microsoft.com/en-us/library/jj150503(v=exchg.150).aspx)를 기반으로 합니다. Exchange Online 작업은 exchange online 시스템 리소스 관리를 위해 명시적으로 정의 된 Exchange 온라인 기능, 프로토콜 또는 서비스입니다. 각 Exchange Online 작업에는 사용자 요청이 나 백그라운드 작업을 수행 하기 위해 CPU, 사서함 데이터베이스 작업 또는 Active Directory 요청과 같은 시스템 리소스가 필요 합니다. Exchange Online 작업의 예로는 웹에서 Outlook, Exchange ActiveSync, 사서함 마이그레이션, 사서함 도우미 등이 있습니다. 테 넌 트 관리자는 Exchange 관리 셸을 사용 하 여 사용자에 대 한 Exchange 작업 관리 제한 설정을 관리할 수 있습니다. Exchange Online 내에서는 PowerShell, Exchange 웹 서비스, POP 및 IMAP, Exchange ActiveSync, 모바일 장치 연결, 받는 사람 등을 비롯 한 다양 한 형태의 제한이 구현 되었습니다. 온-프레미스 Exchange 배포 관리자는 제한 정책을 구성할 수 있지만, 관리자는 Exchange Online에 대 한 제한 정책을 구성할 수 없습니다.

SharePoint Online의 제한에 대 한 가장 일반적인 트리거는 너무 높은 빈도로 너무 많은 작업을 수행 하는 CSOM (클라이언트 쪽 개체 모델) 코드입니다. CSOM을 사용 하는 경우에는 단일 요청을 사용 하 여 여러 작업을 수행할 수 있으며,이는 사용 제한을 초과 하 여 사용자별 제한을 유발할 수 있습니다.

제한이 발생할 수 있는 작업에 관계 없이 사용자가 사용 제한을 초과 하면 SharePoint Online은 해당 사용자 계정에서 일반적으로 짧은 기간 동안 더 많은 요청을 제한 합니다. 사용자 제한이 적용 되는 동안에는 다음 기준에 따라 해당 사용자의 모든 작업이 제한 만료로 제한 됩니다.
- 사용자가 브라우저에서 직접 수행 하는 요청의 경우 SharePoint Online은 제한 정보 페이지로 리디렉션되어 요청이 실패 합니다.
- CSOM 호출을 비롯 한 다른 모든 요청에 대해 SharePoint Online은 HTTP 상태 코드 429 ("너무 많은 요청")을 반환 하며 요청이 실패 합니다.

문제가 되는 프로세스가 계속 해 서 사용 제한을 초과 하는 경우 SharePoint Online에서 프로세스를 완전히 차단 하 고 HTTP 상태 코드 503 ("서비스를 사용할 수 없음")을 반환할 수 있습니다.

## <a name="vulnerability-and-penetration-testing"></a>취약성 및 침투 테스트
Microsoft는 다양 한 [보안 기술 및 사례](https://www.microsoft.com/en-us/trustcenter/security/threatmanagement) 를 사용 하 여 클라우드 서비스에 대 한 맬웨어 방지 구성 요소 및 서비스를 사용 하는 것을 포함 하는 최신의 복잡 한 위협에 대해 [클라우드의 인프라](https://blogs.technet.microsoft.com/hybridcloud/2015/05/05/protecting-your-datacenter-and-cloud-from-emerging-threats/) 및 온-프레미스 네트워크 컴퓨터 (Vm) 및 기타 시스템 고급 위협 분석-네트워크, 시스템 및 사용자의 일반 사용 패턴을 모니터링 하 고, 시스템 학습을 통해 일반 및 일반 침투 테스트를 수행 하는 동작에 플래그를 지정 합니다.

[Microsoft 클라우드 통합 침투 테스트 프로그램](https://technet.microsoft.com/en-us/mt784683)에서 자체 침투 테스트를 수행 하 고 고객에 게 제공 하는 것 외에도,에 대 한 정기적인 취약성 평가를 수행 하는 타사 보안 전문가 에게도 참여 하 고 있습니다. 클라우드 서비스에 대 한 침투 테스트 Microsoft는 이러한 타사 보안 문제 평가에서 제공 하는 보고서를 [서비스 트러스트](https://aka.ms/STP) 및 [서비스 보증](https://aka.ms/ServiceAssurance) 포털에서 다운로드할 수 있도록 합니다.
