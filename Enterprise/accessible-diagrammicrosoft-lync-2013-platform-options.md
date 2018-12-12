---
title: 액세스할 수 있는 다이어그램-Microsoft Lync 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 이 문서에는 기술 다이어그램에서 사용할 수 있는 Microsoft Lync 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504091"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>액세스할 수 있는 다이어그램-Microsoft Lync 2013 플랫폼 옵션

**요약:** 이 문서에는 [기술 다이어그램](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Lync 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
  
이 포스터 비즈니스 의사 결정권자 (Bdm) 하 고 구축한 알아야 내용 Lync Online (Office 365) 및 Lync Server 배포 하는 방법에 대 한 설명 하 고 포함 합니다.
  
- 4 개의 다양 한 배포 옵션 비교: Lync Online (Office 365), Lync Online/서버 하이브리드, Lync Server 및 Lync Server Provider-Hosted 합니다. 
    
- Lync 2013을 배포 하기 위한 두 예제 시나리오입니다.
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Lync 2013 플랫폼에 대 한 4 개의 서로 다른 배포의 비교

비교는 다음 영역에서 각 배포 옵션에 대 한 정보를 제공합니다. 
  
- 다양 한 배포 기능에 대 한 개요
    
- 각 배포 옵션을 구현 하는의 이점
    
- 라이선스 요구 사항
    
- 필수 아키텍처 작업
    
- 각 배포 옵션을 구현 하기 위한 IT Pro 책임
    
### <a name="overview"></a>개요

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

효율성을 확보 하 고이 정보를 Office 365 다중 테 넌 트 계획 된 비용에 대 한 최적화 합니다.
  
함께 제공 되는 다이어그램에서는 계정 이름 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경과 Azure Active Directory 테 넌 트 간에 암호를 동기화 하는 Azure Active Directory 보유자를를 Lync Online 보여줍니다. 
  
기능 및 기능을 설명 합니다.
  
- (SaaS) 서비스로 소프트웨어입니다.
    
- 서식 있는 집합은 항상 최신 상태로 유지 하는 기능입니다.
    
- 다른 응용 프로그램과 함께 사용할 수 있는 온라인 계정에 대 한 Azure Active Directory 보유자를 포함 합니다. 
    
- 디렉터리 통합 계정 이름 및 암호 Azure Active Directory 테 넌 트 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경 간의 동기화를 포함 합니다.
    
- Single sign-on 및 SSO ()는 요구 사항, Active Directory Federation Services (AD FS)를 구현 해야 합니다. 
    
- 인터넷을 통해 클라이언트 통신은 암호화 및 인증 합니다.
    
- 레거시 전화 장비 공용 전화망 (PSTN)을 연결 타사 공급자를 통해 사용할 수 있습니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/서버 하이브리드 (분할 도메인)

Lync 2013의 온-프레미스 배포와 Office 365의 혜택을 결합할 수 있습니다.
  
함께 제공 되는 다이어그램 여기에서 일부 사용자는 홈된 온-프레미스 하 고 일부 사용자가 온라인에 있는 온라인를 Lync를 사용 하 여 Office 365를 보여줍니다. 온-프레미스로 배포 된에 지 서버도 표시 됩니다.
  
기능 및 기능을 설명 합니다.
  
- 일부 사용자가 내부에 있는 및 일부 사용자가 온라인으로 있는 하지만 사용자는 동일한 SIP 도메인 (예: contoso.com)을 공유 합니다.
    
- PSTN에 대 한 연결을 포함 하 여 기존 Lync Server 2013 인프라를 활용 합니다.
    
- PSTN을 필요 하지 않은 경우에 새 Lync Online 사용자를 쉽게 추가 합니다.
    
- Lync 온-프레미스에서 Lync Online에 일정에 시간별로 마이그레이션하십시오.
    
- Exchange Online 및 SharePoint Online을 포함 하 여 다른 Office 365 응용 프로그램과 통합 합니다.
    
#### <a name="lync-server"></a>Lync Server

이 배포에서 소유 하 고 모든 작업입니다. 함께 제공 된 다이어그램은 사용자의 홈된 온-프레미스가 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경 사용 하는 Lync 서버 인프라를 보여줍니다.
  
기능 및 기능을 설명 합니다.
  
- 용량 계획 및 크기 조정 합니다.
    
- 서버 취득 하 고 설치 합니다.
    
- 배포 합니다.
    
- 수평 확장, 패치 및 작업 합니다.
    
- 데이터를 백업 합니다.
    
- 장애 조치 및 재해 복구를 유지 관리 합니다.
    
- Lync Server 2013 인프라가 PSTN에 연결 합니다.
    
- Private branch exchange (Pbx)와 같은 기존 전화 장비와의 통합 합니다.
    
#### <a name="provider-hosted-lync-server"></a>Lync 서버 공급자 호스팅

공급자에이 배포에 모든 작업을 담당합니다. 함께 제공 되는 다이어그램의 서버 및 온-프레미스 환경에 대 한 연결 된 장비를 비롯 하 여 공급자의 네트워크를 표시 합니다.
  
기능 및 기능을 설명 합니다.
  
- 용량 계획 및 크기 조정 합니다.
    
- 서버 취득 하 고 설치 합니다.
    
- 배포 합니다.
    
- 수평 확장, 패치 및 작업 합니다.
    
- 데이터를 백업 합니다.
    
- 장애 조치 및 재해 복구를 유지 관리 합니다.
    
- Private branch exchange (Pbx)와 같은 기존 전화 장비와의 통합 합니다.
    
- 또한 공급자는 다음과 같은 작업을 수행할 수 있습니다.
    
  - 귀하의 구내 (실선)에 대 한 연결을 사용 하 여 자신의 네트워크에서 해당 서버 및 장비를 설치 합니다.
    
  - 귀하의 구내 (점선)에서 해당 서버를 설치 합니다.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>각 배포 옵션을 구현 하는의 이점

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 온-프레미스 서버 또는 서버 소프트웨어의 없음 운영 부담이 있습니다.
    
- 클라우드 기반 서비스로 Lync Server 2013의 통신 기능입니다.
    
- Lync 현재 상태, 인스턴트 메시징, 오디오 및 비디오 풍부한 온라인 모임 및 광범위 한 웹 회의 기능을 호출 합니다.
    
- 지리적으로 분산 된 조직과 또는 주로 모바일 직원을 사용 합니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/서버 하이브리드 (분할 도메인)

- 원격 사용자와 비즈니스 파트너와의 통합에 대 한 Lync Online을 사용 합니다.
    
- Lync 온-프레미스에서 Lync Online로 마이그레이션을 용이 하 게 합니다.
    
- Branch office appliance를 사용 하지 않고 원격 사이트를 지원 합니다.
    
- 새 비즈니스 인수에 대 한 Lync 지원을 추가 (영문) 편리성 합니다.
    
#### <a name="lync-server"></a>Lync Server

- 개인 클라우드 솔루션입니다.
    
- 고도로 사용자 지정 된 솔루션입니다.
    
- 타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Lync Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.
    
- Office 365와 AD DS 계정 동기화를 차단 하는 정보 공개 제한 합니다.
    
- 전체 플랫폼 및 솔루션의 제어 하려고 하는 조직입니다.
    
- Lync Enterprise Voice와 PBX 대체 합니다.
    
#### <a name="provider-hosted-lync-server"></a>Lync 서버 공급자 호스팅

- Lync Server 기능을 사용할 하지만 해당 배포 및 유지 관리를 아웃소싱 할 하려는 하는 조직입니다.
    
- 공급자 기반 솔루션입니다.
    
- 고도로 사용자 지정 된 솔루션입니다.
    
- 타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Lync Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.
    
- Lync Enterprise Voice와 PBX 대체 합니다.
    
### <a name="license-requirements"></a>라이선스 요구 사항

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

구독 모델입니다.
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/서버 하이브리드 (분할 도메인)

- Office 365-구독 모델입니다. 추가 라이센스 필요 합니다. 
    
- 온-프레미스-모든 온-프레미스 라이선스 적용 됩니다. 
    
#### <a name="lync-server"></a>Lync Server

- 서버 운영 체제
    
- SQL Server
    
- Lync 2013 서버 라이선스
    
- Lync 2013 클라이언트 액세스 라이선스
    
#### <a name="provider-hosted-lync-server"></a>Lync 서버 공급자 호스팅

비용에 Lync 솔루션 공급자와 계약을 기반으로 합니다.
  
### <a name="architecture-tasks"></a>아키텍처 작업

이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 보여줍니다.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 디렉터리 동기화를 계획 하 고 디자인 합니다.
    
- 네트워크 용량 및 방화벽, 프록시 서버, 게이트웨이 통해 및 WAN 링크에서 사용 가능 여부를 확인 합니다.
    
- Office 365 서비스 제품에 대 한 엔터프라이즈 보안을 제공 하려면 타사 SSL 인증서를 구입 합니다.
    
- 인터넷 프로토콜 버전 6 (IPv6)와 함께 Office 365에 연결 하는 경우를 결정 합니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/서버 하이브리드 (분할 도메인)

Office 365와 온-프레미스 환경에 대 한 작업 외에도:
  
- 사용 하려는 얼마나 많은 기능 통합 온-프레미스 및 온라인 버전의 Exchange Server 및 SharePoint를 결정 합니다.
    
- 필요한 경우에 프록시 서버 장치를 사용 하 여 Office 365의 요청에 대 한가 결정 합니다.
    
#### <a name="lync-server"></a>Lync Server

기존 온-프레미스 환경에서 Lync 환경 디자인 합니다.
  
- 중앙에 대 한 Lync 토폴로지 및 지점입니다.
    
- 가상화를 포함 하 여 서버 하드웨어를 제공 합니다.
    
- Active Directory 도메인 서비스 (AD DS)와 통합 및 DNS 합니다.
    
- Lync server 풀에 대 한 분산을 로드 합니다.
    
- 장애 조치 및 재해 복구 합니다.
    
#### <a name="provider-hosted-lync-server"></a>Lync 서버 공급자 호스팅

- 클라우드 기반 설치를 위해 서비스 공급자의 네트워크에 대 한 연결을 결정 합니다.
    
- 온-프레미스 설치에 대 한 네트워크에 있는 공급자의 Lync 서버 배치를 결정 합니다.
    
- 두 형식에 대 한 AD DS와 PBX 장비와 통합을 결정 합니다.
    
### <a name="it-pro-responsibilities"></a>IT 전문가 책임

이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 용 책임을 부여 합니다.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

배포 하 고 Lync Online (Office 365)을 관리 합니다.
  
- 디렉터리 동기화 계획을 구현 합니다.
    
- 계획 하 고 내부 및 외부 DNS 레코드 및 라우팅을 구현 합니다.
    
- 프록시 또는 Office 365 IP 주소 및 URL 요구 사항에 대 한 방화벽을 구성 합니다.
    
- 사용자 계정 및 Lync Online 설정을 관리 합니다.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/서버 하이브리드 (분할 도메인)

Office 365와 온-프레미스 환경에 대 한 작업 외에도:
  
- 필요한 경우 프록시 서버 장치를 구성 합니다.
    
- 온-프레미스 및 온라인 버전의 Exchange Server 및 SharePoint의 기능 통합을 구성 합니다.
    
#### <a name="lync-server"></a>Lync Server

배포 하 고 온-프레미스 환경에서 Lync Server를 관리 합니다.
  
- 서버를 구축 합니다.
    
- Lync 토폴로지를 배포 합니다.
    
- Lync 서버를 업데이트 합니다.
    
- 서버 추가 또는 제거 토폴로지 필요에 따라 사용률에 기반 합니다.
    
- 장애 조치 및 재해 복구 환경을 구현 합니다.
    
#### <a name="provider-hosted-lync-server"></a>Lync 서버 공급자 호스팅

공급자와 함께 작동 합니다.
  
- 네트워크에 Lync Server를 통합 합니다.
    
- 다른 Microsoft 제품 또는 사용자 지정 솔루션 Lync Server를 통합 합니다.
    
- 공급자 서비스 수준 계약 (SLA)와 준수 하는지를 모니터링 합니다.
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Lync 2013을 배포 하기 위한 두 예제 시나리오

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Microsoft Azure의 디렉터리 동기화 구성 요소

Azure의 Office 365 디렉터리 동기화 구성 요소를 배포 보다 빠르게 주문형 가상 컴퓨터를 배포 하는 기능으로 인해 있습니다.
  
함께 제공 되는 다이어그램에서는 계정 이름 및 암호는 온-프레미스 Active Directory 환경 및 Azure Active Directory 테 넌 트 간에 동기화 Azure Active Directory 보유자를를 Lync Online 보여줍니다.
  
 **디렉터리 동기화 서버에 해당**합니다. 온-프레미스 환경에서 64 비트 디렉터리 동기화 서버를 배포 하는 대신 인터넷을 통해 Azure에 가상 컴퓨터를 구축 합니다.
  
 **디렉터리 동기화 + AD FS**합니다. 이 옵션을 사용 하면 온-프레미스 인프라에 하드웨어를 추가 하지 않고 Office 365 페더레이션 id가 SSO ()를 지원할 수 있습니다. 또한 온-프레미스 Active Directory 환경에 사용할 수 없는 경우 복구를 제공 합니다. 이 옵션의 기능은 다음과 같습니다.
  
- 디렉터리 통합 구성 요소를 Azure 가상 컴퓨터를 실행 합니다.
    
- AD FS Azure 가상 컴퓨터와를 실행 하는 AD FS 프록시를 통해 인터넷에 게시 됩니다.
    
- 모든 위치에서 연결 하는 사용자에 대 한 클라이언트 인증 트래픽 AD FS 서버 및 Azure 가상 컴퓨터도 배포 되는 프록시에 의해 처리 됩니다.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Exchange 및 Office 365의 SharePoint와 Lync 통합

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Exchange Online과 Lync Server 및 SharePoint Online

함께 제공 되는 다이어그램 Exchange Online 및 SharePoint Online을 사용 하 여 Office 365를 온-프레미스 Lync Server 2013 팜에 연결을 보여줍니다.
  
이 배포의 장점 수행할 수 있습니다.
  
- Lync Server 2013의 전체 기능 집합을 사용 합니다.
    
- Pbx와 같은 기존 온-프레미스 전화 장비를 활용 합니다.
    
- 온-프레미스 전자 메일 서버 및 저장소의 부담을 오프 로드 하는 전자 메일에 대 한 Exchange Online을 사용 합니다.
    
- 온-프레미스 SharePoint 서버를 유지 관리 부담을 오프 로드 하는 공동 작업을 위한 SharePoint Online을 사용 합니다.
    
- 사용 하 여 Lync, Exchange 및 SharePoint 기능을 비롯 하 여 UM (통합 메시징) Office 365의 통합.
    
#### <a name="exchange-server-with-lync-online"></a>Lync Online 포함 Exchange 서버

함께 제공 된 다이어그램 온-프레미스 Exchange 서버 팜에 연결 된 Lync Online을 사용 하 여 Office 365를 보여줍니다.
  
이 배포의 장점 수행할 수 있습니다.
  
- 기존 Exchange 인프라를 활용 합니다.
    
- 현재 상태, 인스턴트 메시징 및 회의 기능에 대 한 Lync Online을 사용 합니다.
    

