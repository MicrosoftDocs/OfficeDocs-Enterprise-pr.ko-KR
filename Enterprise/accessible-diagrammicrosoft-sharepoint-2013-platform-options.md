---
title: 액세스할 수 있는 다이어그램-Microsoft SharePoint 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: 이 문서에는 Microsoft SharePoint 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
ms.openlocfilehash: 1f0d2bf4e74c7e1d28aaa27c6f88dac04f02b4a9
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504321"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>액세스할 수 있는 다이어그램-Microsoft SharePoint 2013 플랫폼 옵션

**요약:** 이 문서에는 Microsoft SharePoint 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
  
비즈니스 의사 결정권자 (Bdm) 하 고 구축한 어떤 Office 365, Microsoft Azure 및 온-프레미스 배포 하는 방법에 대 한 알고 있어야 합니다. 
  
이 포스터에는 두 섹션이 포함 됩니다. 
  
- SharePoint 2013에 대 한 4 개의 서로 다른 배포의 비교: SharePoint 2013, Azure, 및 SharePoint 2013의 온-프레미스 배포의 온-프레미스 배포를 Office 365의 하이브리드 Office 365의 SharePoint 합니다. 
    
- Azure를 이동 하려면 세 일반적인 작업에 대 한 설명입니다. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>SharePoint 2013 플랫폼에 대 한 4 개의 서로 다른 배포의 비교

비교는 다음 영역에 관련 된 각 배포 옵션에 대 한 정보를 제공 합니다. 
  
- 다양 한 배포 기능에 대 한 개요 
    
- 각 유형의 배포 란에 가장 적합 한 
    
- 라이선스 요구 사항 
    
- 아키텍처 작업을 구현 하는 데 필요한 
    
- IT 전문가 용 책임 구현에 대 한 
    
### <a name="overview"></a>개요

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의에서 SharePoint 2013

효율성을 확보 하 고 Office 365 다중 테 넌 트 계획 된 비용에 대 한 최적화 합니다. 
  
함께 제공 되는 다이어그램에서는 계정 이름 및 암호는 온-프레미스 Active Directory 환경 및 Azure Active Directory 테 넌 트 간에 동기화 Azure Active Directory 보유자를를 SharePoint Online 보여줍니다. 
  
기능에 대해 설명 합니다. 
  
- (SaaS) 서비스로 소프트웨어입니다. 
    
- 다양 한 기능 집합이 항상 최신 상태로 유지 됩니다. 
    
- (다른 응용 프로그램과 함께 사용할 수 있음)는 Azure Active Directory 테 넌 트를 포함 합니다. 
    
- 디렉터리 통합 계정 이름 및 암호 Azure Active Directory 테 넌 트 및 온-프레미스 Active Directory 환경 간의 동기화를 포함 합니다. 
    
- Single sign-on 및 SSO ()는 요구 사항, Active Directory Federation Services (AD FS)을 구현할 수 있습니다. 
    
- 암호화와 인증 된 액세스 (포트 443)를 통해 인터넷을 통해 통신 클라이언트입니다. 
    
- 데이터 마이그레이션 인터넷을 통해 업로드할 수 있는 개로 제한 됩니다. 
    
- Office, SharePoint 및 SharePoint Designer 2013에 대 한 사용자 지정: 앱입니다. 
    
#### <a name="hybrid-with-office-365"></a>Office 365와 함께 하이브리드

SharePoint 2013의 온-프레미스 배포와 Office 365의 장점을 결합 합니다. 
  
함께 제공 된 다이어그램 Business Connectivity Services (BCS)를 사용 하 여 온-프레미스 SharePoint Server 2013 팜에 연결할 SharePoint Online을 사용한 Office 365를 보여줍니다. 
  
통합 하려면 다음 기능 중 어떤를 선택 합니다. 
  
SharePoint Search 
  
- 사용자가 두 환경에서의 검색 결과 볼 수 있습니다. 
    
- 엑스트라넷 사용자가 온-프레미스 Active Directory 계정을 사용 하 여 로그온 하 고 모든 사용 가능한 하이브리드 기능을 사용 하 여 원격으로 수입니다. 
    
BCS
  
SharePoint Online: 사용자가 모두 읽기를 수행 하 고 쓰기 작업 수입니다. BCS 서비스는 온-프레미스 SharePoint Server 2013 팜에 연결합니다. BCS 서비스에 구성 된 온-프레미스 팜 브로커 온-프레미스 OData 서비스 끝점에 대 한 연결 합니다. 
  
Duet Enterprise Online 
  
SharePoint Online에서 사용자 수 읽기 및 쓰기 수행할는 온-프레미스 SAP 시스템에 대 한 작업입니다. 
  
#### <a name="azure"></a>Azure

활용 클라우드 플랫폼 및 기능에 대 한 모든 권한을 유지 하면서 합니다. 
  
함께 제공 된 다이어그램은 두 클라우드 서비스, SharePoint 2013 팜 및 인터넷을 통해 사용자에 게 연결 또는 VPN 터널을 통해 온-프레미스 Active Directory에 연결 하는 DNS 통한 Windows Server Active Directory를 포함 하는 Azure를 보여줍니다. 
  
기능은 다음과 같습니다. 
  
-  Azure은 SharePoint 2013 팜을 호스팅하는 데 필요한 인프라 및 응용 프로그램 서비스를 제공 하는 플랫폼입니다.
    
- 인프라 서비스입니다. 
    
- SQL Server 및 SharePoint에 대 한 최상의 네이티브 클라우드 플랫폼입니다. 
    
- 컴퓨팅 리소스는 즉시 거의 없는 확정을 사용할 수 있습니다. 
    
- 데이터 센터 및 인프라는 대신 응용 프로그램에 초점을 맞춥니다. 
    
- 저렴 한 개발 및 테스트 환경입니다. 
    
- SharePoint 솔루션은 인터넷에서 액세스할 수 또는 사이트 마다 VPN 터널을 통해 기업 환경 에서만에서 액세스할 수 있는 수 있습니다. 
    
- 사용자 지정 제한 되지 않습니다. 
    
#### <a name="on-premises"></a>온-프레미스

소유 하 고 모든 작업입니다. 
  
함께 제공 되는 다이어그램에는 웹 서버, 응용 프로그램 서버 및 모든 데이터베이스 및 검색을 위한 전용된 응용 프로그램 서버와 통신 하는 Active Directory를 사용 하는 온-프레미스 환경을 보여줍니다. 
  
기능은 다음과 같습니다. 
  
- 용량 계획 및 크기 조정 합니다. 
    
- 서버 취득 하 고 설치 합니다. 
    
- 배포 합니다. 
    
- 수평 확장, 패치 및 작업 합니다. 
    
- 데이터를 백업 합니다. 
    
- 재해 복구 환경을 유지 관리 합니다. 
    
- 사용자 지정 제한 되지 않습니다. 
    
### <a name="deployment-type-is-best-for---"></a>배포 유형에 가장 적합 한 란...

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의에서 SharePoint 2013

- 외부 공유 및 공동 작업을 보호 합니다. (고유한 기능!) 
    
- 인트라넷-팀 사이트, 내 사이트 및 내부 공동 작업 합니다. 
    
- 저장소 및 클라우드에서 버전 관리를 문서화 합니다. 
    
- 기본 공용 웹사이트입니다. 
    
Office 365 전용 구독 계획 된 추가 기능: 
  
- 조직에 전용 이며 다른 조직과 공유 되지 않도록 하는 Microsoft 데이터 센터 장비입니다. 
    
- 각 고객 환경 물리적으로 별개의 네트워크에 상주합니다. 
    
- IPSec 보안 VPN 또는 고객 소유 개인 연결을 통한 클라이언트 통신 합니다. 2 단계 인증 선택 사항입니다. 
    
- ITAR 지원 계획 합니다. 
    
#### <a name="hybrid-with-office-365"></a>Office 365와 함께 하이브리드

- 외부 공유 및 공동 작업 익스트라넷 환경을 설정 하는 대신 Office 365를 사용 합니다. 
    
- 해당 파일을 원격으로 액세스 하는 사용자에 대 한 쉽게 수행할 수 있도록 하 여 클라우드 (비즈니스용 OneDrive)의 내 사이트를 이동 합니다. 
    
- Office 365에서 새 팀 사이트를 시작 합니다. 
    
- 온-프레미스 BCS SharePoint 환경에서 Office 365 사이트를 통합 합니다. 
    
#### <a name="azure"></a>Azure

- 인터넷 사이트에 대 한 SharePoint-공용 사이트를 연결 합니다. 고객 계정 및 인증에 대 한 Azure AD 활용 합니다. 
    
- 개발자, 테스트 및 준비 환경-신속 하 게 프로 비전 하 고 전체 환경 하므로 합니다. 
    
- 하이브리드 응용 프로그램-데이터 센터 및 클라우드에 걸쳐 있는 응용 프로그램입니다. 
    
- 재해 복구 환경-신속 하 게 재해를 복구 합니다. 급여에만 사용 합니다. 
    
- 상세 보고 또는 감사 필요로 하는 팜 합니다. 
    
- 웹 분석 합니다. 
    
- Rest (SQL 데이터베이스에서 데이터 암호화)에 데이터 암호화 합니다. 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Rest (SQL 데이터베이스에서 데이터 암호화)에 대 한 데이터 암호화

- 국내 팜 (때 데이터를 관할지 내에 상주 하는 데 필요한). 
    
- BI 데이터에 있어야 하는 복잡 한 BI 솔루션을 닫습니다. 
    
- 개인 클라우드 솔루션입니다. 
    
- 고도로 사용자 지정 된 솔루션입니다. 
    
- 타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Azure 인프라 서비스에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다. 
    
- Azure Active Directory (Office 365에 대 한 요구 사항) 하 여 Active Directory 계정 동기화를 차단 하는 정보 공개 제한 합니다. 
    
- 전체 플랫폼 및 솔루션의 제어를 선호 하는 조직입니다. 
    
### <a name="license-requirements"></a>라이선스 요구 사항

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의에서 SharePoint 2013

구독 모델입니다. 추가 라이센스 필요 합니다. 
  
#### <a name="hybrid-with-office-365"></a>Office 365와 함께 하이브리드

- Office 365-구독 모델입니다. 추가 라이센스 필요 합니다. 
    
- 온-프레미스-모든 온-프레미스 라이선스 적용 됩니다. 
    
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

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의에서 SharePoint 2013

- 디렉터리 통합을 계획 하 고 디자인 합니다. 두 옵션입니다. 온-프레미스 또는 Azure에서 옵션 중 하나를 배포할 수 있습니다: 암호 동기화 (64 비트 서버를 하나 필요). SSO (AD FS 및 다중 서버 필요). 
    
- 네트워크 용량 및 방화벽, 프록시 서버, 게이트웨이 통해 및 WAN 링크에서 사용 가능 여부를 확인 합니다. 
    
- Office 365 서비스 제품에 대 한 엔터프라이즈 보안을 제공 하려면 타사 SSL 인증서를 구입 합니다. 
    
- 테 넌 트 이름을 계획 하 고 사이트 모음 아키텍처 및 관리 방식 디자인 합니다. 
    
- SharePoint Online에 대 한 사용자 지정, 솔루션, 및 앱을 계획 합니다. 
    
- 인터넷 프로토콜 6 (IPv6)를 사용 하 여 Office 365에 연결 하는 경우를 결정 합니다. 일반적인 아닙니다. 
    
#### <a name="hybrid-with-office-365"></a>Office 365와 함께 하이브리드

Office 365와 온-프레미스 환경에 대 한 작업 외에도: 
  
- 원하는 하 고 하이브리드 토폴로지 선택 얼마나 많은 기능 통합을 결정 합니다. 이 모델 포스터를 참조: 하이브리드 토폴로지를 사용 해야 합니까? 
    
- 필요한 경우에 프록시 서버 장치를 사용할 수 결정 합니다. 
    
#### <a name="azure"></a>Azure

Azure 네트워크 환경을 디자인 합니다. 
  
- 가상 네트워크 서브넷을 포함 하 여 Azure 내에서 합니다. 
    
- 도메인 환경 및 온-프레미스 서버와의 통합 합니다. 
    
- IP 주소와 DNS 합니다. 
    
- 선호도 그룹 및 저장소 계정입니다. 
    
Azure의 SharePoint 환경 디자인 합니다. 
  
- SharePoint 팜 토폴로지 및 논리 아키텍처를 제공 합니다. 
    
-  Azure 가용성 집합과 업데이트 도메인입니다.
    
- 가상 컴퓨터 크기입니다. 
    
- 부하 분산 된 끝점입니다. 
    
- 외부의 끝점을 공용 인 경우 액세스 하는 것이 좋습니다. 
    
- 재해 복구 환경입니다. 
    
#### <a name="on-premises"></a>온-프레미스

기존 온-프레미스 환경에서 SharePoint 환경 디자인 합니다. 
  
- SharePoint 팜 토폴로지 및 논리 아키텍처를 제공 합니다. 
    
- 서버 하드웨어에 있습니다. 
    
- 가상 환경을 사용 하는 경우입니다. 
    
- 부하 분산 합니다. 
    
- AD DS 및 DNS와의 통합 합니다. 
    
- 재해 복구 환경입니다. 
    
### <a name="it-pro-responsibilities"></a>IT 전문가 책임

#### <a name="sharepoint-2013-in-office-365"></a>Office 365의에서 SharePoint 2013

- 사용자 워크스테이션이 Office 365 클라이언트 필수 구성 요소를 충족 해야 합니다. 
    
- 디렉터리 통합 계획을 구현 합니다. 
    
- 계획 하 고 내부 및 외부 DNS 레코드 및 라우팅을 구현 합니다. 
    
- 프록시 또는 Office 365 IP 주소 및 URL 요구 사항에 대 한 방화벽을 구성 합니다. 
    
- 페이지를 만들고 사이트 모음에 사용 권한을 할당 합니다. 
    
- SharePoint Online에 대 한 사용자 지정, 솔루션 및 앱을 구현 합니다. 
    
- 네트워크 가용성을 모니터링 하 고 가능한 병목 현상을 식별 합니다. 
    
#### <a name="hybrid-with-office-365"></a>Office 365와 함께 하이브리드

Office 365와 온-프레미스 환경에 대 한 작업 외에도: 
  
- 필요한 경우 프록시 서버 장치를 구성 합니다. 
    
- 하이브리드 id 관리 인프라 구성: SSO 및 두 환경 간에 서버를 인증 합니다. 
    
- 선택한 기능 통합을 구성: Search, BCS, Duet Enterprise Online 합니다. 
    
#### <a name="azure"></a>Azure

배포 하 고 Azure와 SharePoint 환경을 관리 합니다. 
  
- 구현 하 고 Azure 네트워크 환경에서 관리 합니다. 
    
- SharePoint 환경을 배포 합니다. 
    
- SharePoint 팜 서버를 업데이트 합니다. 
    
- 추가 또는 종료 가상 컴퓨터 필요에 따라 팜 사용률에 기반 합니다. 
    
- 필요에 따라 가상 컴퓨터 크기를 늘리거나 설정 합니다. 
    
- SharePoint 환경을 백업 합니다. 
    
- 재해 복구 환경 및 프로토콜을 구현 합니다. 
    
#### <a name="on-premises"></a>온-프레미스

배포 하 고-프레미스 환경에서 SharePoint를 관리 합니다. 
  
- 서버를 구축 합니다. 
    
- SharePoint 환경을 배포 합니다. 
    
- SharePoint 팜 서버를 업데이트 합니다. 
    
- 추가 또는 제거 팜 서버 필요에 따라 팜 사용률에 기반 합니다. 
    
- SharePoint 환경을 백업 합니다. 
    
- 재해 복구 환경 및 프로토콜을 구현 합니다. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Azure를 이동 하려면 세 일반적인 작업

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365와 Azure의 디렉터리 구성 요소

Azure의 Office 365 디렉터리 통합 구성 요소를 배포 주문형 가상 컴퓨터를 배포할 수 있으므로 훨씬 빠릅니다. 
  
#### <a name="directory-synchronization-server-only"></a>디렉터리 동기화 서버에만

온-프레미스 환경에서 64 비트 디렉터리 동기화 서버를 배포 하는 대신 Azure에 가상 컴퓨터를 대신 구축 합니다. 
  
함께 제공 되는 다이어그램에서는 계정 이름 및 암호는 온-프레미스 Active Directory 환경 및 Azure Active Directory 테 넌 트 간에 동기화 Azure Active Directory 보유자를를 SharePoint Online 보여줍니다. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>디렉터리 동기화 및 AD FS

이 옵션을 사용 하면 온-프레미스 인프라에 하드웨어를 추가 하지 않고 Office 365 페더레이션 id가 SSO ()를 지원할 수 있습니다. 또한 온-프레미스 Active Directory 환경에 사용할 수 없는 경우 복구를 제공 합니다. 
  
- 디렉터리 통합 구성 요소는 Azure에 상주합니다. 
    
- AD FS Azure에서 AD FS 프록시를 통해 인터넷에 게시 됩니다. 
    
- 모든 위치에서 연결 하는 사용자에 대 한 클라이언트 인증 트래픽 Azure에 배포 되는 프록시 하 고 AD FS 서버에서 처리 됩니다. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>공용 인터넷 사이트 및 고객 인증에 대 한 Azure AD

Azure의 인터넷 사이트를 배치 하 여 제안에 쉽게 확장할 수 있는 기능을 활용 합니다. Azure AD를 사용 하 여 고객 계정을 저장 합니다. 
  
#### <a name="azure-advantages-for-internet-sites"></a>인터넷 사이트에 대 한 azure 장점

- 팜 사용률에 기반 하는 가상 컴퓨터 수를 조정 하 여 필요한 리소스에 대해서만 지불 합니다. 
    
- 상세 보고 및 웹 분석을 추가 합니다. 
    
- 인프라를 구축 하는 것 보다 큰 사이트 개발 (영문)에 초점을 맞춥니다. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD 클라우드 서비스에 대 한 id 관리 및 액세스 제어 기능을 제공합니다. 기능은 디렉터리 데이터 및 사용자 로그온 프로세스, 인증 서비스 및 AD FS를 포함 하 여 identity 서비스의 핵심 집합에 대 한 클라우드 기반 저장소를 포함 합니다. Azure AD에 포함 된 id 서비스, 온-프레미스 Active Directory 배포와 쉽게 통합 및 타사 id 공급자를 완전히 지원 합니다. 
  
함께 제공 되는 다이어그램에는 영역 및 인터넷 사이트에 대 한 중요 한 인증의 구성을 보여줍니다. 다음 다이어그램은 Azure Active Directory 테 넌 트, 두 영역으로 Azure에 설치 된 SharePoint 팜을 포함 하는 보여줍니다. 
  
- 익명 사용자 및 인증 된 방문자와 네트워크 외부의 고객와 상호작용 하는 인터넷 영역 
    
- 크롤링 및 VPN 터널을 통해 온-프레미스 Active Directory 배포와 상호작용 하는 Windows 인증에 NTLM을 포함 하는 기본 영역입니다. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>온-프레미스 팜 + Azure의 재해 복구

비즈니스 요구 사항에 맞는 재해 복구 옵션을 선택 합니다. 재해 복구를 시작 하는 회사에 대 한 초급 옵션을 제공 하는 azure 및 고급 높은 복구 요구 사항이 있는 기업에 대 한 옵션입니다. 
  
#### <a name="cold-standby"></a>정지 대기

- 팜의 완벽 하 게, 작성 되었지만 가상 컴퓨터를 중지 합니다. (지불할만 때 실행 하는지!) 
    
- 유지 관리 하는 환경 포함 시간을-런타임, 패치, 업데이트 및 확인 (영문) 환경에서에서 가상 컴퓨터를 시작 합니다. 
    
- 재해 발생 시 전체 환경을 다시 시작 합니다. 
    
#### <a name="warm-standby"></a>웜 대기

- 이 실행 되 고 프로 비전 하는 소규모 팜 포함 됩니다. 
    
- 즉시 팜의 장애 조치 시 사용자를 지원할 수 있습니다. 
    
- 신속 하 게 사용자층에 전체 팜을 확장 합니다. 
    
#### <a name="hot-standby"></a>상시 대기

완벽 하 게 크기의 팜을 대기 모드에서 실행 되 고 프로 비전 된 됩니다. 
  
함께 제공 된 다이어그램 azure SharePoint 재해 복구 환경와 상호작용 하는 온-프레미스 팜을 보여줍니다. 온-프레미스 데이터베이스에 사용 하 여 SQL Server 로그 전달 VPN 터널 SharePoint 데이터베이스, 두 웹 프런트엔드 서버 및 두 SharePoint를 포함 하는 두 SQL 데이터베이스 서버를 포함 하는 SharePoint 재해 복구 환경에 액세스 응용 프로그램 서버입니다. 
  

