---
title: 액세스 가능한 다이어그램-Microsoft Exchange 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
f1.keywords:
- NOCSH
description: 이 문서는 기술 다이어그램에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 이라는 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: 56f77f7689270b60296848d41992652bf2068695
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844629"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>액세스 가능한 다이어그램-Microsoft Exchange 2013 플랫폼 옵션

**요약:** 이 문서는 [기술 다이어그램](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 이라는 액세스 가능한 텍스트 버전입니다.
  
이 포스터는 Exchange Online 및 Exchange Server 배포와 관련 하 여 다음과 같은 비즈니스 의사 결정권자 (BDMs) 및 설계자가 파악 해야 하는 사항에 대해 설명 합니다. 
  
- Exchange Online (Office 365), Exchange 하이브리드, Exchange Server 온-프레미스 및 공급자 호스트 Exchange 2013에 대해 사용 가능한 4 가지 플랫폼 옵션을 비교 합니다. 
    
- Exchange 2013에 새로 추가 되었거나 업데이트 된 기능에 대해 설명 합니다. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Exchange 2013 플랫폼에 대해 서로 다른 네 가지 배포 비교

비교에서는 다음 영역의 각 배포 옵션에 대 한 정보를 제공 합니다. 
  
- 다양 한 배포 기능에 대 한 개요 
    
- 각 배포 옵션을 구현할 때의 장점 
    
- 라이선스 요구 사항 
    
- 필수 아키텍처 작업 
    
- 각 배포 옵션을 구현 하는 IT 전문가 책임 
    
### <a name="overview"></a>개요

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Office 365의 효율성을 확보 하 고 비용을 절감할 수 있습니다.
  
함께 제공 되는 다이어그램에서는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트와의 Exchange Online을 보여 줍니다. Single sign-on에는 AD FS (Active Directory Federation Services)가 필요 합니다. 
  
기능에 대 한 설명:
  
- 서버 및 서버 소프트웨어의 작업은 Microsoft에서 처리 됩니다.
    
- Exchange Server 2013의 다양 한 기능 집합을 클라우드 기반 서비스로 사용 합니다.
    
- 최신 기능을 사용 하 여 항상 최신 상태로 유지 합니다.
    
- EOP (Exchange Online Protection)는 스팸 방지/맬웨어 방지 보호를 위해 포함 되어 있습니다.
    
- 99.9% SLA (서비스 수준 계약)를 사용한 기본 제공 고가용성
    
- 온-프레미스 AD DS (Active Directory 도메인 서비스) 및 Azure Active Directory 테 넌 트 간의 암호를 포함 하는 디렉터리 동기화 Single sign-on에는 AD FS (Active Directory Federation Services)가 필요 합니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

Exchange Server 온-프레미스를 유지 관리 하면서 Office 365의 이점을 활용할 수 있습니다.
  
함께 제공 되는 다이어그램에는 일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태에 있는 Office 365에서 Exchange Online이 표시 됩니다. 또한 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트도 표시 됩니다.
  
기능에 대 한 설명:
  
- 일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태이 고 사용자가 같은 전자 메일 주소 공간을 공유 하는 경우
    
- 기존 Exchange Server 인프라를 활용 합니다.
    
- 일정에 따라 시간에 따라 Exchange 온-프레미스에서 Exchange Online으로 마이그레이션
    
- Lync Online 및 SharePoint Online을 비롯 한 다른 Office 365 응용 프로그램과 통합 됩니다.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

고유한 Exchange Server 2013 인프라를 디자인 하 고 관리할 수 있습니다.
  
함께 제공 되는 다이어그램에서는 사용자가 온-프레미스에 있는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경을 사용 하는 Exchange Server 인프라를 보여 줍니다.
  
기능에 대 한 설명:
  
- 구성에 대 한 가장 적합 한 제어 및 사용자 지정 수준입니다.
    
- 부하 분산 계층에서 세션 선호도를 유지 관리 하는 방법에 대 한 종속성이 없습니다.
    
- Dag (데이터베이스 사용 가능 그룹)를 사용 하는 단순 고가용성 및 사이트 복구
    
- 뛰어난 사용자 환경을 유지 관리 하는 데 도움이 되는 관리 되는 가용성
    
- 기존 하드웨어 및 저장소 인프라를 활용 합니다.
    
#### <a name="provider-hosted-exchange"></a>공급자 호스팅 Exchange

Exchange 서버 작업을 Exchange Server 솔루션 공급자에 게 외주 시킬 수 있습니다.
  
함께 제공 되는 다이어그램에는 공급자가 운영 하 고 유지 관리 하는 Exchange Server 환경이 나와 있습니다.
  
기능에 대 한 설명:
  
- 서버 및 서버 소프트웨어의 작업은 공급자에 의해 처리 됩니다.
    
- Exchange Server 인프라에 대 한 계획, 크기 조정, 확장 및 유지 관리가 공급자에 게 위임 됩니다.
    
- 서비스 유지 관리는 공급자에 의해 처리 됩니다.
    
- Exchange 기능 집합은 공급자가 배포한 소프트웨어 버전으로 제한 됩니다.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>각 배포 옵션을 구현할 때의 장점

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.
  
- 온-프레미스 Exchange 배포에 대 한 운영 비용을 줄이기 위해 조직
    
- SharePoint Online 및 Lync Online과 같은 다른 Office 365 제품을 활용할 계획을 수립 하는 조직입니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.
  
- Exchange 온-프레미스에서 Exchange Online으로의 마이그레이션을 촉진 합니다.
    
- 지점 인프라에 대해 투자 하지 않고 원격 사이트를 지원 합니다.
    
- 데이터를 온-프레미스에 저장 해야 하는 자회사가 있는 다국적 기업
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.
  
- 고도로 사용자 지정 된 솔루션
    
- Exchange Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션
    
- 조직은 데이터를 온-프레미스에 배치 해야 하는 데이터 거 버 넌 스를 대상으로 합니다.
    
- 전체 플랫폼과 솔루션의 제어를 유지 하려는 조직
    
#### <a name="provider-hosted-exchange"></a>공급자 호스팅 Exchange

이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.
  
- Exchange Server 기능을 필요로 하지만 배포 및 유지 관리를 아웃소싱 하려는 조직
    
- 개인 설정 지원 옵션이 필요한 조직
    
- 공급자가 제공 하는 사용자 지정 응용 프로그램과의 솔루션 및 통합 사용자 지정
    
- Exchange Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션
    
### <a name="license-requirements"></a>라이선스 요구 사항

다음 표에서는 각 배포 옵션에 대 한 라이선스 요구 사항을 자세히 설명 합니다.
  
|**배포 옵션**|**라이선스 요구 사항**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |구독 모델  <br/> |
|Exchange 하이브리드  <br/> | Office 365-구독 모델 <br/>  온-프레미스-모든 온-프레미스 라이선스 적용 (온-프레미스의 교환 서버에 대 한 라이선스 검토) <br/>  하이브리드 서버 라이선스 * <br/> |
|Exchange Server 온-프레미스  <br/> | 서버 운영 체제 <br/>  Exchange 2013 서버 라이선스 <br/>  Exchange 2013 클라이언트 액세스 라이선스 <br/> |
|공급자 호스팅 Exchange  <br/> |공급자와의 계약에 따라 비용이 제공 됩니다.  <br/> |
   
### <a name="architecture-tasks"></a>아키텍처 작업

이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 소개 합니다.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 디렉터리 동기화를 계획 하 고 디자인 합니다.
    
- 방화벽, 프록시 서버, 게이트웨이 및 WAN 링크를 통해 네트워크 용량과 연결을 확인 합니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

Office 365 및 온-프레미스 환경 둘 다에 대 한 아키텍처 작업 외에도 다음을 수행 합니다.
  
- Single sign-on 환경을 제공할지 여부를 결정 합니다.
    
- 온-프레미스 조직을 통해 또는 Exchange Online Protection을 통해 인바운드 인터넷 메일을 라우트할 것인지 여부를 결정 합니다.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

- Exchange 토폴로지를 디자인 합니다.
    
- 서버 하드웨어에 대 한 용량을 계획 합니다.
    
- 메시지 라우팅 토폴로지를 디자인 합니다.
    
- 클라이언트 액세스 서버에 대 한 부하 분산을 디자인 합니다.
    
- 데이터베이스 사용 가능 그룹을 사용 하 여 고가용성을 계획 합니다.
    
#### <a name="provider-hosted-exchange"></a>공급자 호스팅 Exchange

공급자가 방화벽, 프록시 서버, 게이트웨이 및 WAN 링크를 통해 네트워크 용량 및 가용성을 사용할 수 있는지 확인 합니다.
  
### <a name="it-pro-responsibilities"></a>IT 전문가 책임

이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 책임을 소개 합니다.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 디렉터리 동기화 계획을 구현 합니다.
    
- 내부 및 외부 DNS 레코드와 라우팅을 계획 하 고 구현 합니다.
    
- Office 365 IP 주소 및 URL 요구 사항에 대 한 프록시 서버 또는 방화벽을 구성 합니다.
    
- 사용자 계정 및 Exchange Online 설정을 관리 합니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

Office 365 및 온-프레미스 환경 둘 다에 대 한 IT 전문가 책임 외에도 다음을 수행 하세요.
  
- 필요한 경우 AD FS (Active Directory Federation Services)를 single sign-on으로 구성 합니다.
    
- Exchange 2013 서버와 Office 365 간의 보안 통신을 위해 Exchange 인증서를 구성 합니다.
    
- 원하는 인바운드 인터넷 메일 경로에 대 한 DNS 레코드를 구성 합니다.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

- Exchange 서비스에 필요한 인증서를 구성 합니다.
    
- 서버를 구축 합니다.
    
- Exchange 메시지 라우팅 토폴로지를 구현 합니다.
    
- 데이터베이스 사용 가능 그룹을 구현 합니다.
    
- Exchange 서버를 업데이트 하 고 유지 관리 합니다.
    
- 사용률에 따라 필요한 경우 서버를 추가 또는 제거 합니다.
    
#### <a name="provider-hosted-exchange"></a>공급자 호스팅 Exchange

공급자의 책임은 다음과 같습니다.
  
- 시스템 및 서비스 유지 관리
    
- 기능 롤아웃
    
- 데이터 보호 및 재해 복구
    
조직에서 IT 직원의 책임은 사용자 계정 만들기 및 관리를 포함 합니다.
  
#### <a name="more-information"></a>추가 정보

Exchange Online (Office 365)에 대 한 자세한 내용은 다음을 참조 하십시오.
  
- [Exchange Online 서비스 설명](https://aka.ms/EXOSD)
    
- [TechNet의 Exchange Online 라이브러리](https://aka.ms/EXOTN)
    
- [Exchange Online 포털](https://aka.ms/EXO)
    
Exchange 하이브리드에 대 한 자세한 내용은 다음 항목을 참조 하십시오.
  
- [Exchange 2013 하이브리드 배포](https://aka.ms/ExchangeHybrid) Exchange 2013 하이브리드 서버 및 exchange 2007 조직이 Exchange 2013 또는 Exchange 2010 하이브리드 서버를 사용 하는 2010 경우에는 다음과 같은 시나리오에 하이브리드 서버 라이선스가 필요 하다는 것을 유의 해야 합니다.
    
- [Office 365 로그인](https://aka.ms/HybridKey)
    
Exchange Server 온-프레미스에 대 한 자세한 내용은 다음을 참조 하십시오.
  
- [TechNet의 Exchange Server 2013 라이브러리](https://aka.ms/Ex2013TN)
    
- [Exchange Server 2013 포털](https://aka.ms/Exchange2013)
    
- [Exchange Server 2013 아키텍처](https://aka.ms/Ex2013SP1ArchPoster)
    
공급자 호스트 Exchange에 대 한 자세한 내용은 다음 항목을 참조 하십시오.
  
[Exchange Server 2013 호스팅 및 다중 테 넌 시 솔루션 및 지침](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Exchange 2013의 세 가지 새로운 기능 또는 업데이트 된 기능의 설명

### <a name="exchange-online-protection"></a>Exchange Online Protection

EOP (Exchange Online Protection)는 데이터 센터의 전역 네트워크 전체에 배포 되는 보호 기능을 제공 하 여 모든 배포에 대 한 스팸 방지 및 맬웨어 방지 보호를 제공 합니다. 이를 통해 메시징 환경 관리를 단순화할 수 있습니다. EOP는 Exchange Online 구독에 포함 되어 있지만 하이브리드 및 온-프레미스 배포에도 사용할 수 있습니다.
  
함께 제공 되는 다이어그램은 전역 네트워크에 EOP 레이어를 포함 하는 Exchange Online, Exchange 하이브리드 및 Exchange 온-프레미스에 대 한 배포를 보여 줍니다.
  
### <a name="exchange-server-deployment-assistant"></a>Exchange Server 배포 도우미

Exchange Server 배포 도우미는 현재 환경에 대 한 몇 가지 질문을 한 다음, 다양 한 유형의 시나리오에 대해 Exchange Server를 배포 하는 데 도움이 되는 사용자 지정 단계별 검사 목록을 생성 하는 웹 기반 도구입니다. 이전 버전의 Exchange에서 Exchange 2013로 마이그레이션하거나 exchange Online으로 마이그레이션하거나 하이브리드 인프라를 계획 하는 경우 Exchange Server 배포 도우미는 시나리오에 대해 사용자 지정 된 배포 검사 목록을 만듭니다.
  
다음 스크린샷에는 Exchange Server 배포 도우미를 사용 하 여 만든 예제 검사 목록이 나와 있습니다.
  
### <a name="integration-with-lync-and-sharepoint"></a>Lync 및 SharePoint와의 통합

Exchange Server 2013에는 Lync Server 2013 및 SharePoint Server 2013과 통합 되는 많은 기능이 포함 되어 있습니다. 이러한 제품은 다양 한 기능을 제공 하며 조직 전체에서 공동 작업을 개선 합니다. 
  
함께 제공 되는 다이어그램은 서버 간 인증 포스터를 보여 주고 포스터 링크를 포함 합니다. 
  
- 보관, 유지 및 eDiscovery
    
- 사이트 사서함
    
- 통합 연락처 저장소
    
- 고해상도 사용자 사진
    
- Outlook 및 Outlook Web App에서 Lync 현재 상태
    
- 서버 간 인증
    
- Voicemail
    
- 모임 녹음/녹화
    
- Exchange 작업 동기화
    
함께 제공 되는 다이어그램에서는 Exchange Server 2013 SP1 아키텍처 포스터를 보여 주고 포스터 링크를 제공 합니다.
  

