---
title: 액세스 가능한 다이어그램-Microsoft SharePoint 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- SPO_Content
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
f1.keywords:
- NOCSH
description: 이 문서는 Microsoft SharePoint 2013 플랫폼 옵션 이라는 그림의 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: 100645b8de8487497eca4a2581523818e18834b3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843879"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>액세스 가능한 다이어그램-Microsoft SharePoint 2013 플랫폼 옵션

**요약:** 이 문서는 Microsoft SharePoint 2013 플랫폼 옵션 이라는 그림의 액세스 가능한 텍스트 버전입니다.
  
Office 365, Microsoft Azure 및 온-프레미스 배포에 대해 알아야 할 BDMs (비즈니스 의사 결정권자) 및 설계자 
  
이 포스터에는 두 가지 섹션이 있습니다. 
  
- Sharepoint의 sharepoint 2013, Azure 및 온-프레미스 배포와 sharepoint 2013의 온-프레미스 배포를 포함 하는 office 365의 microsoft 365 하이브리드와 같은 네 가지 2013 배포를 비교 합니다. 
    
- Azure로 이동할 일반적인 3 가지 작업에 대 한 설명입니다. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>SharePoint 2013 플랫폼에 대해 서로 다른 네 가지 배포 비교

비교에서는 다음 영역과 관련 된 각 배포 옵션에 대 한 정보를 제공 합니다. 
  
- 다양 한 배포 기능에 대 한 개요 
    
- 각 유형의 배포에 가장 적합 한 사항 
    
- 라이선스 요구 사항 
    
- 구현에 필요한 아키텍처 작업 
    
- 구현에 필요한 IT 전문가 책임 
    
### <a name="overview"></a>개요

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의 SharePoint 2013

Office 365 다중 테 넌 트 요금제를 사용 하 여 비용을 효율적으로 확보 하 고 최적화 합니다. 
  
함께 제공 되는 다이어그램에서는 온-프레미스 Active Directory 환경과 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트를 사용 하 여 SharePoint Online을 보여 줍니다. 
  
기능 설명: 
  
- SaaS (Software as a Service)입니다. 
    
- 다양 한 기능 집합은 항상 최신 상태로 유지 됩니다. 
    
- Azure Active Directory 테 넌 트를 포함 합니다 (다른 응용 프로그램과 함께 사용 가능). 
    
- 디렉터리 통합에는 온-프레미스 Active Directory 환경과 Azure Active Directory 테 넌 트 사이에 계정 이름과 암호를 동기화 하는 작업이 포함 됩니다. 
    
- SSO (single sign-on)가 요구 되는 경우에는 AD FS (Active Directory Federation Services)를 구현할 수 있습니다. 
    
- 암호화 및 인증 된 액세스 (포트 443)를 통해 인터넷을 통한 클라이언트 통신 
    
- 데이터 마이그레이션은 인터넷을 통해 업로드할 수 있는 것으로 제한 됩니다. 
    
- 사용자 지정: Office, SharePoint 및 SharePoint Designer 2013 용 앱입니다. 
    
#### <a name="hybrid-with-office-365"></a>Office 365 하이브리드

Office 365의 혜택을 온-프레미스 SharePoint 2013 배포와 결합 합니다. 
  
함께 제공 되는 다이어그램은 BCS (Business Connectivity Services)를 사용 하 여 SharePoint Online과 함께 온-프레미스 SharePoint Server 2013 팜에 연결 하는 Office 365를 보여 줍니다. 
  
다음 중 통합 기능을 선택 합니다. 
  
SharePoint Search 
  
- 사용자는 두 환경의 검색 결과를 볼 수 있습니다. 
    
- 엑스트라넷 사용자는 온-프레미스 Active Directory 계정을 사용 하 여 원격으로 로그온 하 고 사용 가능한 모든 하이브리드 기능을 사용할 수 있습니다. 
    
BCS
  
SharePoint Online에서: 사용자는 읽기 및 쓰기 작업을 모두 수행할 수 있습니다. BCS 서비스가 온-프레미스 SharePoint Server 2013 팜에 연결 됩니다. 온-프레미스 팜에 구성 된 BCS 서비스가 온-프레미스 OData 서비스 끝점에 대 한 연결을 브로커 합니다. 
  
Duet Enterprise Online 
  
SharePoint Online에서 사용자는 온-프레미스 SAP 시스템에 대해 읽기 및 쓰기 작업을 수행할 수 있습니다. 
  
#### <a name="azure"></a>Azure

플랫폼 및 기능에 대 한 모든 권한을 유지 관리 하면서 클라우드를 활용 합니다. 
  
함께 제공 되는 다이어그램에는 두 개의 클라우드 서비스, SharePoint 2013 팜 및 인터넷을 통해 사용자에 게 DNS를 연결 하거나 VPN 터널을 통해 온-프레미스 Active Directory에 연결 하는 Windows Server Active Directory가 포함 된 Azure가 표시 됩니다. 
  
기능에는 다음이 포함 됩니다. 
  
-  Azure는 SharePoint 2013 팜을 호스트 하는 데 필요한 인프라 및 앱 서비스를 제공 하는 플랫폼입니다.
    
- 인프라 서비스 
    
- SQL Server 및 SharePoint에 대 한 최상의 네이티브 클라우드 플랫폼입니다. 
    
- 컴퓨팅 리소스는 확정 없이 즉시 사용할 수 있습니다. 
    
- 데이터 센터 및 인프라 대신 응용 프로그램에 집중 합니다. 
    
- 저렴 한 개발 및 테스트 환경 
    
- 인터넷에서 SharePoint 솔루션에 액세스 하거나 사이트 간 VPN 터널을 통해 회사 환경 에서만 액세스할 수 있습니다. 
    
- 사용자 지정 내용이 제한 되지 않습니다. 
    
#### <a name="on-premises"></a>온-프레미스

모든 것을 소유 하 고 있습니다. 
  
함께 제공 되는 다이어그램에서는 웹 서버, 응용 프로그램 서버 및 Active Directory와 함께 모든 데이터베이스 및 검색용 전용 응용 프로그램 서버와 통신 하는 온-프레미스 환경을 보여 줍니다. 
  
기능에는 다음이 포함 됩니다. 
  
- 용량 계획 및 크기 조정 
    
- 서버 인식 및 설정 
    
- 배포. 
    
- 수평 확장, 패치 및 작업 
    
- 데이터 백업 
    
- 재해 복구 환경 유지 관리 
    
- 사용자 지정 내용이 제한 되지 않습니다. 
    
### <a name="deployment-type-is-best-for---"></a>배포 유형은에 가장 적합 합니다. . .

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의 SharePoint 2013

- 외부 공유 및 공동 작업을 보호 합니다. (고유한 기능!) 
    
- 인트라넷-팀 사이트, 내 사이트 및 내부 공동 작업 
    
- 클라우드의 저장소 및 버전 관리를 문서화 합니다. 
    
- 기본 공용 웹 사이트 
    
Office 365 전용 구독 계획을 사용 하는 추가 기능: 
  
- 조직 전용 Microsoft 데이터 센터 장비 이며 다른 조직과 공유 하지 않습니다. 
    
- 각 고객 환경은 물리적으로 분리 된 네트워크에 있습니다. 
    
- IPSec 보안 VPN 또는 고객 소유 개인 연결을 통한 클라이언트 통신 2 단계 인증은 선택 사항입니다. 
    
- ITAR 지원 계획 
    
#### <a name="hybrid-with-office-365"></a>Office 365 하이브리드

- 엑스트라넷 환경을 설정 하는 대신 Office 365에서 외부 공유 및 공동 작업을 사용 합니다. 
    
- 사용자가 원격으로 자신의 파일에 쉽게 액세스할 수 있도록 내 사이트 (비즈니스용 OneDrive)를 클라우드로 이동 합니다. 
    
- Office 365에서 새 팀 사이트를 시작 합니다. 
    
- Office 365 사이트를 온-프레미스 BCS SharePoint 환경에 통합 합니다. 
    
#### <a name="azure"></a>Azure

- 인터넷 사이트용 SharePoint — 공용 사이트 고객 계정 및 인증에 대 한 Azure AD를 활용 합니다. 
    
- 개발자, 테스트 및 준비 환경-전체 환경을 빠르게 프로 비전 하 고 프로 비전 해제 합니다. 
    
- 하이브리드 응용 프로그램-데이터 센터와 클라우드를 확장 하는 응용 프로그램입니다. 
    
- 재해 복구 환경-재해 로부터 빠르게 복구 합니다. 사용을 위해 결제 합니다. 
    
- 상세 보고 또는 감사가 필요한 팜 
    
- Web analytics 
    
- 데이터 암호화 휴지 (SQL 데이터베이스에서 데이터가 암호화 됨) 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>데이터 암호화 휴지 (SQL 데이터베이스에서 데이터가 암호화 됨)

- 국내 팜 (데이터가 관할지 내에 있어야 하는 경우) 
    
- BI 데이터와 근접해 야 하는 복잡 한 BI 솔루션 
    
- 사설 클라우드 솔루션 
    
- 고도로 사용자 지정 된 솔루션 
    
- Azure 인프라 서비스에서 지원 되지 않는 하드웨어 및 소프트웨어에 의존 하는 타사 구성 요소를 사용 하는 레거시 솔루션 
    
- Azure Active Directory를 사용 하는 Active Directory 계정의 동기화를 방지 하는 개인 정보 제한 (Office 365에 대 한 요구 사항) 
    
- 전체 플랫폼과 솔루션의 제어를 선호 하는 조직 
    
### <a name="license-requirements"></a>라이선스 요구 사항

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의 SharePoint 2013

구독 모델 추가 라이선스가 필요 하지 않습니다. 
  
#### <a name="hybrid-with-office-365"></a>Office 365 하이브리드

- Office 365 — 구독 모델 추가 라이선스가 필요 하지 않습니다. 
    
- 온-프레미스-모든 온-프레미스 라이선스가 적용 됩니다. 
    
#### <a name="azure"></a>Azure

-  Azure 구독 (서버 운영 체제 포함)
    
- SQL Server 
    
- SharePoint 2013 서버 라이선스 
    
- SharePoint 2013 클라이언트 액세스 라이선스 
    
#### <a name="on-premises"></a>온-프레미스

- 서버 운영 체제 
    
- SQL Server 
    
- SharePoint 2013 서버 라이선스 
    
- SharePoint 2013 클라이언트 액세스 라이선스 
    
### <a name="architecture-tasks"></a>아키텍처 작업

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의 SharePoint 2013

- 디렉터리 통합을 계획 하 고 디자인 합니다. 두 가지 옵션 두 옵션 중 하나를 온-프레미스 또는 Azure: 암호 동기화 (1 64 비트 서버 필요)에 배포할 수 있습니다. SSO (AD FS 및 다중 서버 필요) 
    
- 방화벽, 프록시 서버, 게이트웨이 및 WAN 링크를 통해 네트워크 용량과 사용 가능 여부를 확인 합니다. 
    
- 타사 SSL 인증서를 취득 하 여 Office 365 서비스 제품에 대해 엔터프라이즈 보안을 제공 합니다. 
    
- 테 넌 트 이름을 계획 하 고 사이트 모음 아키텍처 및 거 버 넌 스를 디자인 합니다. 
    
- SharePoint Online에 대 한 사용자 지정, 솔루션 및 앱을 계획 합니다. 
    
- IPv6 (인터넷 프로토콜 6)을 사용 하 여 Office 365에 연결할지 여부를 결정 합니다. 이는 일반적인 것이 아닙니다. 
    
#### <a name="hybrid-with-office-365"></a>Office 365 하이브리드

Office 365 및 온-프레미스 환경 둘 다에 대 한 작업 외에도 다음을 수행 합니다. 
  
- 원하는 기능 통합 정도를 결정 하 고 하이브리드 토폴로지를 선택 합니다. 사용 해야 하는 하이브리드 토폴로지는 다음 모델 포스터를 참조 하세요. 
    
- 필요한 경우 사용할 프록시 서버 장치를 확인 합니다. 
    
#### <a name="azure"></a>Azure

Azure 네트워크 환경을 디자인 합니다. 
  
- 서브넷을 포함 하는 Azure 내의 가상 네트워크 
    
- 도메인 환경 및 온-프레미스 서버와의 통합 
    
- IP 주소 및 DNS 
    
- 선호도 그룹 및 저장소 계정 
    
Azure에서 SharePoint 환경 디자인: 
  
- SharePoint 팜 토폴로지 및 논리적 아키텍처 
    
-  Azure availability 도메인을 설정 하 고 업데이트 합니다.
    
- 가상 컴퓨터 크기 
    
- 부하 분산 된 끝점입니다. 
    
- 공용 액세스용 외부 끝점 (더 선호 되는 경우) 
    
- 재해 복구 환경 
    
#### <a name="on-premises"></a>온-프레미스

기존 온-프레미스 환경에서 SharePoint 환경을 디자인 합니다. 
  
- SharePoint 팜 토폴로지 및 논리적 아키텍처 
    
- 서버 하드웨어 
    
- 가상 환경 (사용 하는 경우) 
    
- 부하 분산 
    
- AD DS 및 DNS와의 통합 
    
- 재해 복구 환경 
    
### <a name="it-pro-responsibilities"></a>IT 전문가 책임

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의 SharePoint 2013

- 사용자 워크스테이션이 Office 365 클라이언트 필수 구성 요소를 충족 하는지 확인 합니다. 
    
- 디렉터리 통합 계획을 구현 합니다. 
    
- 내부 및 외부 DNS 레코드와 라우팅을 계획 하 고 구현 합니다. 
    
- Office 365 IP 주소 및 URL 요구 사항에 대 한 프록시나 방화벽을 구성 합니다. 
    
- 사이트 모음을 만들고 사용 권한을 할당 합니다. 
    
- SharePoint Online에 대 한 사용자 지정, 솔루션 및 앱을 구현 합니다. 
    
- 네트워크 가용성을 모니터링 하 고 가능한 병목 현상을 파악 합니다. 
    
#### <a name="hybrid-with-office-365"></a>Office 365 하이브리드

Office 365 및 온-프레미스 환경 둘 다에 대 한 작업 외에도 다음을 수행 합니다. 
  
- 필요한 경우 프록시 서버 장치를 구성 합니다. 
    
- 하이브리드 id 관리 인프라: SSO 및 두 환경 간의 서버 간 인증을 구성 합니다. 
    
- 검색, BCS, Duet Enterprise Online 등 선택한 기능의 통합을 구성 합니다. 
    
#### <a name="azure"></a>Azure

Azure 및 SharePoint 환경을 배포 및 관리 합니다. 
  
- Azure 네트워크 환경을 구현 하 고 관리 합니다. 
    
- SharePoint 환경을 배포 합니다. 
    
- SharePoint 팜 서버를 업데이트 합니다. 
    
- 팜 사용률에 따라 필요한 경우 가상 컴퓨터를 추가 하거나 종료 합니다. 
    
- 필요한 경우 가상 컴퓨터 크기를 늘리거나 줄이십시오. 
    
- SharePoint 환경을 백업 합니다. 
    
- 재해 복구 환경 및 프로토콜을 구현 합니다. 
    
#### <a name="on-premises"></a>온-프레미스

온-프레미스 환경에서 SharePoint를 배포 하 고 관리 합니다. 
  
- 서버 구축 
    
- SharePoint 환경을 배포 합니다. 
    
- SharePoint 팜 서버를 업데이트 합니다. 
    
- 팜 사용률에 따라 필요에 따라 팜 서버를 추가 하거나 제거 합니다. 
    
- SharePoint 환경을 백업 합니다. 
    
- 재해 복구 환경 및 프로토콜을 구현 합니다. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Azure로 이동할 일반적인 3 가지 작업

### <a name="office-365-plus-directory-components-in-azure"></a>Azure의 Office 365 plus 디렉터리 구성 요소

Azure에서 Office 365 디렉터리 통합 구성 요소를 배포 하는 것은 주문형으로 가상 컴퓨터를 배포할 수 있기 때문입니다. 
  
#### <a name="directory-synchronization-server-only"></a>디렉터리 동기화 서버 전용

온-프레미스 환경에 64 비트 디렉터리 동기화 서버를 배포 하는 대신 Azure에서 가상 컴퓨터를 프로 비전 합니다. 
  
함께 제공 되는 다이어그램에서는 온-프레미스 Active Directory 환경과 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트를 사용 하 여 SharePoint Online을 보여 줍니다. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>디렉터리 동기화 및 AD FS

이 옵션을 사용 하면 온-프레미스 인프라에 하드웨어를 추가 하지 않고 Office 365 페더레이션 id (SSO)를 지원할 수 있습니다. 또한 온-프레미스 Active Directory 환경을 사용할 수 없는 경우에도 복구 력을 제공 합니다. 
  
- 디렉터리 통합 구성 요소는 Azure에 있습니다. 
    
- AD FS는 Azure에서 AD FS 프록시를 통해 인터넷에 게시 됩니다. 
    
- 모든 위치에서 연결 하는 사용자에 대 한 클라이언트 인증 트래픽은 Azure에 배포 되는 AD FS 서버 및 프록시에서 처리 됩니다. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>고객 인증용 인터넷 사이트 및 Azure AD에 대 한 공용 연결

Azure에 인터넷 사이트를 배치 하 여 수요를 간편 하 게 확장할 수 있는 기능을 활용 합니다. Azure AD를 사용 하 여 고객 계정을 저장 합니다. 
  
#### <a name="azure-advantages-for-internet-sites"></a>인터넷 사이트용 Azure 혜택

- 팜 사용률을 기준으로 가상 컴퓨터 수를 확장 하 여 필요한 리소스에 대해서만 결제 합니다. 
    
- 상세 보고 및 web analytics 추가 
    
- 인프라를 구축 하는 것 보다는 훌륭한 사이트 개발에 집중 합니다. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD는 클라우드 서비스에 대 한 id 관리 및 액세스 제어 기능을 제공 합니다. 기능에는 디렉터리 데이터를 위한 클라우드 기반 저장소와 사용자 로그온 프로세스, 인증 서비스 및 AD FS 등의 핵심 id 서비스가 포함 됩니다. Azure AD에 포함 된 id 서비스는 온-프레미스 Active Directory 배포와 쉽게 통합 되며 타사 id 공급자를 완벽 하 게 지원 합니다. 
  
함께 제공 되는 다이어그램에서는 인터넷 연결 사이트에 중요 한 영역 및 인증의 구성을 보여 줍니다. 다음 다이어그램에는 두 개의 영역이 포함 된 Azure의 SharePoint 팜을 포함 하는 Azure Active Directory 테 넌 트가 나와 있습니다. 
  
- 익명 및 인증 된 방문자 및 네트워크 외부의 고객과 상호 작용 하는 인터넷 영역 
    
- VPN 터널을 통해 온-프레미스 Active Directory 배포와 상호 작용 하는 크롤링 및 Windows 인증에 대 한 NTLM이 포함 된 기본 영역입니다. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Azure의 온-프레미스 팜 및 재해 복구

비즈니스 요구 사항에 맞는 재해 복구 옵션을 선택 합니다. Azure는 복원 력이 높은 기업에 대 한 재해 복구 및 고급 옵션을 시작 하기 위한 회사에 대 한 항목 수준 옵션을 제공 합니다. 
  
#### <a name="cold-standby"></a>콜드 대기

- 팜이 완전히 구축 되었지만 가상 컴퓨터는 중지 됩니다. (실행 중인 경우에만 비용을 지불 하 고 있습니다.) 
    
- 환경 유지 관리에는 시간에 대 한 가상 컴퓨터 시작, 패치, 업데이트 및 환경 확인이 포함 됩니다. 
    
- 재해가 발생 한 경우 전체 환경을 시작 합니다. 
    
#### <a name="warm-standby"></a>웜 대기

- 여기에는 프로 비전 되어 실행 되는 소규모 팜이 포함 됩니다. 
    
- 팜은 장애 조치 (failover) 시 사용자에 게 즉시 서비스를 제공할 수 있습니다. 
    
- 전체 사용자 기반에 서비스를 제공 하기 위해 팜을 빠르게 수평 확장 합니다. 
    
#### <a name="hot-standby"></a>상시 대기

완전히 크기 있는 팜이 프로 비전 되 고 대기 모드에서 실행 되 고 있습니다. 
  
함께 제공 되는 다이어그램에는 Azure에서 SharePoint 재해 복구 환경과 상호 작용 하는 온-프레미스 팜이 나와 있습니다. 온-프레미스 데이터베이스는 VPN 터널을 통한 SQL Server 로그 전달을 사용 하 여 sharepoint 데이터베이스, 두 개의 웹 프런트 엔드 서버 및 두 개의 SharePoint를 포함 하는 두 개의 SQL 데이터베이스 서버를 포함 하는 SharePoint 재해 복구 환경에 액세스 합니다. 응용 프로그램 서버 
  

