---
title: 액세스 가능한 다이어그램-Microsoft Lync 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 이 문서는 기술 다이어그램에서 사용할 수 있는 Microsoft Lync 2013 Platform Options 라는 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: 4993ad90307973589da6dc5081d8c2875b44ce66
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068614"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>액세스 가능한 다이어그램-Microsoft Lync 2013 플랫폼 옵션

**요약:** 이 문서는 [기술 다이어그램](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Lync 2013 Platform Options 라는 액세스 가능한 텍스트 버전입니다.
  
이 포스터는 BDMs (비즈니스 의사 결정권자) 및 설계자가 Lync Online (Office 365) 및 Lync Server 배포에 대해 알아야 할 사항에 대해 설명 합니다.
  
- Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server 및 Provider Hosted Lync Server의 네 가지 서로 다른 배포 옵션을 비교 합니다. 
    
- Lync 2013 배포에 대 한 두 가지 예제 시나리오
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Lync 2013 플랫폼에 대해 네 가지 서로 다른 배포 비교

비교에서는 다음 영역의 각 배포 옵션에 대 한 정보를 제공 합니다. 
  
- 다양 한 배포 기능에 대 한 개요
    
- 각 배포 옵션을 구현할 때의 장점
    
- 라이선스 요구 사항
    
- 필수 아키텍처 작업
    
- 각 배포 옵션을 구현 하는 IT 전문가 책임
    
### <a name="overview"></a>개요

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Office 365 다중 테 넌 트 요금제를 사용 하 여 비용을 효율성과 최적화 합니다.
  
함께 제공 되는 다이어그램에는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트를 사용한 Lync Online이 나와 있습니다. 
  
기능에 대 한 설명:
  
- SaaS (Software as a Service)입니다.
    
- 항상 최신 상태로 유지 되는 다양 한 기능 집합
    
- 다른 응용 프로그램과 함께 사용할 수 있는 온라인 계정에 대 한 Azure Active Directory 테 넌 트를 포함 합니다. 
    
- 디렉터리 통합에는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 사이에 계정 이름과 암호를 동기화 하는 작업이 포함 됩니다.
    
- SSO (single sign-on)가 요구 되는 경우에는 AD FS (Active Directory Federation Services)를 구현 해야 합니다. 
    
- 인터넷을 통한 클라이언트 통신은 암호화 되 고 인증 됩니다.
    
- 레거시 전화 장비, PSTN (공중 전화망), 타사 공급자를 통해 연결을 사용할 수 있습니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (분할 도메인)

Office 365의 혜택을 온-프레미스 Lync 2013 배포와 결합할 수 있습니다.
  
함께 제공 되는 다이어그램에는 일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태에 있는 Office 365에서 Lync Online이 표시 됩니다. 온-프레미스에 배포 된에 지 서버도 표시 됩니다.
  
기능에 대 한 설명:
  
- 일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태 이지만, 사용자가 같은 SIP 도메인 (예: contoso.com)을 공유 하는 경우
    
- PSTN에 대 한 연결을 포함 하 여 기존 Lync Server 2013 인프라를 활용 합니다.
    
- PSTN이 필요 하지 않은 경우 새 Lync Online 사용자를 쉽게 추가할 수 있습니다.
    
- 일정에 따라 Lync 온-프레미스에서 Lync Online으로 마이그레이션
    
- Exchange Online 및 SharePoint Online을 비롯 한 다른 Office 365 응용 프로그램과 통합 됩니다.
    
#### <a name="lync-server"></a>Lync Server

이 배포에서는 모든 것을 소유 합니다. 함께 제공 되는 다이어그램에서는 사용자가 온-프레미스에 있는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경을 사용 하는 Lync Server 인프라를 보여 줍니다.
  
기능에 대 한 설명:
  
- 용량 계획 및 크기 조정
    
- 서버 인식 및 설정
    
- 배포.
    
- 수평 확장, 패치 및 작업
    
- 데이터 백업
    
- 장애 조치 (failover) 및 재해 복구 유지 관리
    
- Lync Server 2013 인프라를 PSTN에 연결 합니다.
    
- Pbx (private branch 교환의)와 같은 기존 전화 장비와의 통합
    
#### <a name="provider-hosted-lync-server"></a>공급자 호스트 Lync Server

이 배포에서 공급자는 모든 항목을 소유 합니다. 함께 제공 되는 다이어그램에서는 온-프레미스 환경에 대 한 연결을 사용 하 여 서버 및 장비를 포함 하는 공급자의 네트워크를 보여줍니다.
  
기능에 대 한 설명:
  
- 용량 계획 및 크기 조정
    
- 서버 인식 및 설정
    
- 배포.
    
- 수평 확장, 패치 및 작업
    
- 데이터 백업
    
- 장애 조치 (failover) 및 재해 복구 유지 관리
    
- Pbx (private branch 교환의)와 같은 기존 전화 장비와의 통합
    
- 또한 공급자는 다음과 같은 작업을 수행할 수 있습니다.
    
  - 온-프레미스 (실선) 연결을 사용 하 여 자체 네트워크에 서버 및 장비를 설치 합니다.
    
  - 온-프레미스 (점선)에 서버를 설치 합니다.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>각 배포 옵션을 구현할 때의 장점

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 온-프레미스 서버 또는 서버 소프트웨어의 작동 부담을 주지 않습니다.
    
- Lync Server 2013의 통신 기능은 클라우드 기반 서비스입니다.
    
- Lync 현재 상태, 인스턴트 메시징, 오디오 및 비디오 통화, 리치 온라인 모임, 다양 한 웹 회의 기능
    
- 지리적으로 분산 된 조직이 나 주로 모바일 직원과 함께 사용 됩니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (분할 도메인)

- 원격 사용자에 대해 Lync Online을 사용 하 고 비즈니스 파트너와 통합 합니다.
    
- Lync 온-프레미스에서 Lync Online으로 쉽게 마이그레이션할 수 있습니다.
    
- Branch office 어플라이언스를 사용 하지 않고 원격 사이트를 지원 합니다.
    
- 새로운 비즈니스 인수에 대 한 Lync 지원을 쉽게 추가할 수 있습니다.
    
#### <a name="lync-server"></a>Lync Server

- 사설 클라우드 솔루션
    
- 고도로 사용자 지정 된 솔루션
    
- Lync Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션
    
- Office 365와의 AD DS 계정을 동기화 하지 못하도록 하는 개인 정보 제한입니다.
    
- 전체 플랫폼과 솔루션의 제어를 원하는 조직
    
- Lync Enterprise Voice를 사용한 PBX 교체
    
#### <a name="provider-hosted-lync-server"></a>공급자 호스트 Lync Server

- Lync Server 기능을 관리 하지만 배포 및 유지 관리를 아웃소싱 하려는 조직
    
- 공급자 기반 솔루션
    
- 고도로 사용자 지정 된 솔루션
    
- Lync Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션
    
- Lync Enterprise Voice를 사용한 PBX 교체
    
### <a name="license-requirements"></a>라이선스 요구 사항

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

구독 모델
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (분할 도메인)

- Office 365 — 구독 모델 추가 라이선스가 필요 하지 않습니다. 
    
- 온-프레미스-모든 온-프레미스 라이선스가 적용 됩니다. 
    
#### <a name="lync-server"></a>Lync Server

- 서버 운영 체제
    
- SQL Server
    
- Lync 2013 서버 라이선스
    
- Lync 2013 클라이언트 액세스 라이선스
    
#### <a name="provider-hosted-lync-server"></a>공급자 호스트 Lync Server

비용은 Lync 솔루션 공급자와의 계약을 기반으로 합니다.
  
### <a name="architecture-tasks"></a>아키텍처 작업

이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 소개 합니다.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 디렉터리 동기화를 계획 및 디자인 합니다.
    
- 방화벽, 프록시 서버, 게이트웨이 및 WAN 링크를 통해 네트워크 용량과 사용 가능 여부를 확인 합니다.
    
- 타사 SSL 인증서를 취득 하 여 Office 365 서비스 제품에 대해 엔터프라이즈 보안을 제공 합니다.
    
- IPv6 (인터넷 프로토콜 버전 6)을 사용 하 여 Office 365에 연결할지 여부를 결정 합니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (분할 도메인)

Office 365 및 온-프레미스 환경 둘 다에 대 한 작업 외에도 다음을 수행 합니다.
  
- Exchange Server 및 SharePoint의 온-프레미스 및 온라인 버전에서 사용할 기능 통합 용량을 결정 합니다.
    
- 필요한 경우 Office 365의 요청에 사용할 프록시 서버 장치를 확인 합니다.
    
#### <a name="lync-server"></a>Lync Server

기존 온-프레미스 환경에서 Lync 환경을 디자인 합니다.
  
- 중앙 및 지사의 Lync 토폴로지
    
- 가상화를 비롯 한 서버 하드웨어
    
- AD DS (Active Directory 도메인 서비스) 및 DNS와의 통합
    
- Lync server 풀에 대 한 부하 분산
    
- 장애 조치 (Failover) 및 재해 복구
    
#### <a name="provider-hosted-lync-server"></a>공급자 호스트 Lync Server

- 클라우드 기반 설치의 경우 서비스 공급자의 네트워크에 대 한 연결을 확인 합니다.
    
- 온-프레미스 설치의 경우 네트워크에서 공급자의 Lync server 배치를 확인 합니다.
    
- 두 유형 모두에 대해 AD DS 및 PBX 장비와의 통합을 결정 합니다.
    
### <a name="it-pro-responsibilities"></a>IT 전문가 책임

이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 책임을 소개 합니다.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Lync Online 배포 및 관리 (Office 365):
  
- 디렉터리 동기화 계획을 구현 합니다.
    
- 내부 및 외부 DNS 레코드와 라우팅을 계획 하 고 구현 합니다.
    
- Office 365 IP 주소 및 URL 요구 사항에 맞게 프록시나 방화벽을 구성 합니다.
    
- 사용자 계정 및 Lync Online 설정을 관리 합니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (분할 도메인)

Office 365 및 온-프레미스 환경 둘 다에 대 한 작업 외에도 다음을 수행 합니다.
  
- 필요한 경우 프록시 서버 장치를 구성 합니다.
    
- 기능을 온-프레미스 및 온라인 버전의 Exchange Server 및 SharePoint와 통합을 구성 합니다.
    
#### <a name="lync-server"></a>Lync Server

온-프레미스 환경에서 Lync Server를 배포 하 고 관리 합니다.
  
- 서버를 구축 합니다.
    
- Lync 토폴로지를 배포 합니다.
    
- Lync server를 업데이트 합니다.
    
- 사용률에 따라 필요에 따라 토폴로지 서버를 추가 하거나 제거 합니다.
    
- 장애 조치 (failover) 및 재해 복구 환경을 구현 합니다.
    
#### <a name="provider-hosted-lync-server"></a>공급자 호스트 Lync Server

공급자와 협력 하 여 다음을 수행 합니다.
  
- Lync Server를 네트워크에 통합 합니다.
    
- Lync Server를 다른 Microsoft 제품 또는 사용자 지정 솔루션과 통합 합니다.
    
- SLA (서비스 수준 계약) 준수를 모니터링 합니다.
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Lync 2013 배포를 위한 두 가지 예제 시나리오

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Microsoft Azure의 디렉터리 동기화 구성 요소

요청 시 가상 컴퓨터를 배포 하는 기능으로 인해 Azure에서 Office 365 디렉터리 동기화 구성 요소를 배포 하는 것이 더 빠릅니다.
  
함께 제공 되는 다이어그램에는 온-프레미스 Active Directory 환경과 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트를 사용한 Lync Online이 나와 있습니다.
  
 **디렉터리 동기화 서버에만**해당 합니다. 온-프레미스 환경에 64 비트 디렉터리 동기화 서버를 배포 하는 대신, 인터넷을 통해 Azure에서 가상 컴퓨터를 프로 비전 합니다.
  
 **디렉터리 동기화 + AD FS** 이 옵션을 사용 하면 온-프레미스 인프라에 하드웨어를 추가 하지 않고 Office 365 페더레이션 id (SSO)를 지원할 수 있습니다. 또한 온-프레미스 Active Directory 환경을 사용할 수 없는 경우에도 복구 력을 제공 합니다. 이 옵션의 기능은 다음과 같습니다.
  
- 디렉터리 통합 구성 요소는 Azure 가상 컴퓨터로 실행 됩니다.
    
- Azure 가상 컴퓨터로 실행 되는 AD fs 프록시를 통해 AD FS가 인터넷에 게시 됩니다.
    
- 모든 위치에서 연결 하는 사용자에 대 한 클라이언트 인증 트래픽은 Azure 가상 컴퓨터로 배포 되는 AD FS 서버 및 프록시에서 처리 됩니다.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Office 365의 Exchange 및 SharePoint와의 Lync 통합

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Exchange Online 및 SharePoint Online을 사용 하는 Lync Server

함께 제공 되는 다이어그램에는 온-프레미스 Lync Server 2013 팜에 연결 된 Exchange Online 및 SharePoint Online의 Office 365이 나와 있습니다.
  
이 배포를 사용 하면 다음과 같은 이점이 있습니다.
  
- Lync Server 2013의 전체 기능 집합을 사용 합니다.
    
- Pbx와 같은 기존 온-프레미스 전화 장비를 활용 합니다.
    
- 전자 메일에 대 한 Exchange Online을 사용 하 여 온-프레미스 전자 메일 서버 및 저장소에 대 한 부담을 오프에서 로드 합니다.
    
- 공동 작업을 위해 SharePoint Online을 사용 하 여 온-프레미스 SharePoint 서버를 유지 관리 하는 부담을 해제 합니다.
    
- Office 365의 UM (통합 메시징)을 포함 하 여 Lync, Exchange 및 SharePoint 통합 기능을 사용 합니다.
    
#### <a name="exchange-server-with-lync-online"></a>Lync Online을 사용 하는 Exchange Server

함께 제공 되는 다이어그램에서는 온-프레미스 Exchange Server 팜에 Lync Online이 연결 된 Office 365를 보여 줍니다.
  
이 배포를 사용 하면 다음과 같은 이점이 있습니다.
  
- 기존 Exchange 인프라를 활용 합니다.
    
- 현재 상태, 인스턴트 메시징 및 회의 기능을 위해 Lync Online을 사용 합니다.
    

