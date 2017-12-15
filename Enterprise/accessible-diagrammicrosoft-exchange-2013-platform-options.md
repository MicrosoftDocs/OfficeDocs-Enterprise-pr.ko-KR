---
title: "액세스할 수 있는 다이어그램-Microsoft Exchange 2013 플랫폼 옵션"
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: "이 문서에는 기술 다이어그램에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다."
ms.openlocfilehash: d81fe9947feee64d1dd75278738262d10c802ecc
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>액세스할 수 있는 다이어그램-Microsoft Exchange 2013 플랫폼 옵션

**요약:** 이 문서에는 [기술 다이어그램](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
  
이 포스터 비즈니스 의사 결정권자 (Bdm) 하 고 구축한 필요한 정보를 Exchange Online 및 Exchange Server 배포에 대해 알고에 대해 설명 하 고 포함 합니다. 
  
- Exchange 2013에 대 한 4 개의 사용 가능한 플랫폼 옵션의 비교: Exchange Online (Office 365), Exchange 하이브리드 Exchange Server 온-프레미스, 및 Provider-Hosted 교환 합니다. 
    
- Exchange 2013의 세 신규 또는 업데이트 된 기능에 대 한 설명입니다. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Exchange 2013 플랫폼에 대 한 4 개의 서로 다른 배포의 비교

비교는 다음 영역에서 각 배포 옵션에 대 한 정보를 제공합니다. 
  
- 다양 한 배포 기능에 대 한 개요 
    
- 각 배포 옵션을 구현 하는의 이점 
    
- 라이선스 요구 사항 
    
- 필수 아키텍처 작업 
    
- 각 배포 옵션을 구현 하기 위한 IT Pro 책임 
    
### <a name="overview"></a>개요

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

효율성을 높이 하 고이 정보를 Office 365와 비용을 절감 합니다.
  
함께 제공 되는 다이어그램에서는 계정 이름 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경과 Azure Active Directory 테 넌 트 간에 암호를 동기화 하는 한 Azure Active Directory 테 넌 트를 Exchange Online 보여줍니다. Active Directory Federation Services (AD FS)는 single sign-on 필요 합니다. 
  
기능 및 기능을 설명 합니다.
  
- 서버 및 서버 소프트웨어의 작업은 Microsoft에서 처리 됩니다.
    
- Exchange Server 2013의 클라우드 기반 서비스로 풍부한 기능을 설정합니다.
    
- 항상 최신 상태로 유지 최신 기능을 사용 합니다.
    
- Exchange Online Protection (EOP) 백신-스팸 방지/맬웨어 방지 보호 기능에 대 한 포함 됩니다.
    
- 기본 제공 고가용성 99.9%와 서비스 수준 계약 (SLA).
    
- 디렉터리 동기화를 온-프레미스 Active Directory 도메인 서비스 (AD DS) 및 Azure Active Directory 테 넌 트 간에 암호를 포함 합니다. Active Directory Federation Services (AD FS)는 single sign-on 필요 합니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

Office 365의 이점을 활용 하 여 Exchange Server 온-프레미스를 유지 하면서 수 있습니다.
  
함께 제공 되는 다이어그램 Exchange Online과 여기에서 일부 사용자는 홈된 온-프레미스 하 고 일부 사용자가 온라인에 있는 Office 365를 보여줍니다. 또한 계정 이름 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경과 Azure Active Directory 테 넌 트 간에 암호를 동기화 하는 한 Azure Active Directory 테 넌 트를 보여줍니다.
  
기능 및 기능을 설명 합니다.
  
- 일부 사용자는 홈된 온-프레미스 하 고 일부 사용자가 온라인 상태에 있는 사용자가 동일한 전자 메일 주소 공간을 공유 합니다.
    
- 기존 Exchange 서버 인프라를 활용합니다.
    
- Exchange 온-프레미스에서 Exchange Online에 일정에 시간별로 마이그레이션하십시오.
    
- Lync Online 및 SharePoint Online을 포함 하 여 다른 Office 365 응용 프로그램과 통합 합니다.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

디자인 하 고 직접 Exchange Server 2013 인프라를 관리할 수 있습니다.
  
함께 제공 된 다이어그램은 사용자의 홈된 온-프레미스가 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경 사용 하 여 Exchange Server 인프라를 보여줍니다.
  
기능 및 기능을 설명 합니다.
  
- 가장 큰 수준의 제어 및 구성에 대 한 사용자 지정 합니다.
    
- 부하 분산 계층에서 세션 선호도 유지 관리에 대 한 종속성 없습니다.
    
- 간단한 고가용성 및 사이트 복구 데이터베이스 가용성 그룹 (Dag)를 사용 하 여 합니다.
    
- 훌륭한 사용자 환경을 유지 관리 하는데 도움이 되는 가용성을 관리 합니다.
    
- 기존 하드웨어 및 저장소 인프라를 활용 합니다.
    
#### <a name="provider-hosted-exchange"></a>Exchange 공급자 호스팅

Exchange Server 솔루션 공급자에 Exchange 서버 작업 부하를 아웃소싱 할 수 있습니다.
  
함께 제공 된 다이어그램을 운영 하 고 공급자에 의해 유지 관리 하는 Exchange Server 환경을 보여줍니다.
  
기능 및 기능을 설명 합니다.
  
- 서버 및 서버 소프트웨어의 작업은 공급자에 의해 처리 됩니다.
    
- 계획, 크기 조정, 배율 및 Exchange 서버 인프라의 유지 관리 공급자에 위임 됩니다.
    
- 유지 관리 서비스 공급자에 의해 처리 됩니다.
    
- Exchange 기능 집합은 공급자가 배포 된 소프트웨어 버전으로 제한 됩니다.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>각 배포 옵션을 구현 하는의 이점

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

이 배포 옵션은 가장 적합 합니다.
  
- 온-프레미스에 대 한 작업 비용 절감을 고려 하는 조직에서는 배포를 교환 합니다.
    
- SharePoint Online 및 Lync Online 같은 다른 Office 365 제품을 활용 하려는 조직에서는 합니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

이 배포 옵션은 가장 적합 합니다.
  
- Exchange 온-프레미스에서 Exchange Online로 마이그레이션을 원활 하 게 합니다.
    
- Branch office 인프라에 투자 하지 않고도 원격 사이트를 지원 합니다.
    
- 온-프레미스 상주 하는 데이터를 필요로 하는 자회사와 다국적 기업입니다.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

이 배포 옵션은 가장 적합 합니다.
  
- 고도로 사용자 지정 된 솔루션입니다.
    
- 타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Exchange Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.
    
- 조직에서는 온-프레미스 상주 하는 데이터를 필요로 하는 데이터 관리 규정을 제목입니다.
    
- 조직 전체 플랫폼 및 솔루션의 제어를 유지 하려면입니다.
    
#### <a name="provider-hosted-exchange"></a>Exchange 공급자 호스팅

이 배포 옵션은 가장 적합 합니다.
  
- Exchange 서버 기능을 필요는 없지만 해당 배포 및 유지 관리를 아웃소싱 할 하려고 하는 조직입니다.
    
- 개인 설정 된 지원 옵션 필요 하는 조직입니다.
    
- 사용자 지정 된 솔루션 및 공급자가 제공 하는 사용자 지정 응용 프로그램과 통합 합니다.
    
- 타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Exchange Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.
    
### <a name="license-requirements"></a>라이선스 요구 사항

다음 표에서 각 배포 옵션에 대 한 라이선스 요구 사항에 자세히 설명 합니다.
  
|**배포 옵션**|**라이선스 요구 사항**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |구독 모델  <br/> |
|Exchange 하이브리드  <br/> | Office 365-구독 모델 <br/>  온-프레미스-모든 온-프레미스 라이선스 적용 (Exchange Server 온-프레미스에 대 한 검토 라이선스) <br/>  하이브리드 서버 라이선스 * <br/> |
|Exchange Server 온-프레미스  <br/> | 서버 운영 체제 <br/>  Exchange 2013 서버 라이선스 <br/>  Exchange 2013 클라이언트 액세스 라이선스 <br/> |
|Exchange 공급자 호스팅  <br/> |비용을 기반으로 공급자와 계약  <br/> |
   
### <a name="architecture-tasks"></a>아키텍처 작업

이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 보여줍니다.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 계획 하 고 디렉터리 동기화를 디자인 합니다.
    
- 네트워크 용량 및 방화벽, 프록시 서버, 게이트웨이 통해 및 WAN 링크에서 연결을 확인 합니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

Office 365와 온-프레미스 환경에 대 한 아키텍처 작업 외에도:
  
- 환경에는 단일 기호 (+)를 제공 여부를 결정 합니다.
    
- 온-프레미스 조직을 통해 또는 Exchange Online Protection을 통한 인바운드 인터넷 메일을 라우팅하 여부를 결정 합니다.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

- Exchange 토폴로지를 디자인 합니다.
    
- 서버 하드웨어에 대 한 용량을 계획 합니다.
    
- 메시지 라우팅 토폴로지를 디자인 합니다.
    
- 클라이언트 액세스 서버에 대해 부하 분산을 디자인 합니다.
    
- 데이터베이스 가용성 그룹을 사용 하 여 고가용성을 위한 계획 합니다.
    
#### <a name="provider-hosted-exchange"></a>Exchange 공급자 호스팅

네트워크 용량 및 방화벽, 프록시 서버, 게이트웨이 통해 사용 가능 여부를 확인 하 고 WAN 링크에서 공급자에 사용할 수 있는 키를 누릅니다.
  
### <a name="it-pro-responsibilities"></a>IT 전문가 책임

이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 용 책임을 부여 합니다.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 디렉터리 동기화 계획을 구현 합니다.
    
- 계획 하 고 내부 및 외부 DNS 레코드 및 라우팅을 구현 합니다.
    
- 프록시 서버 또는 Office 365 IP 주소 및 URL 요구 사항에 대 한 방화벽을 구성 합니다.
    
- 사용자 계정 및 Exchange Online 설정을 관리 합니다.
    
#### <a name="exchange-hybrid"></a>Exchange 하이브리드

Office 365와 온-프레미스 환경에 대 한 IT 전문가 용 책임 외에도:
  
- (필요한 경우)에서 Active Directory Federation Services (AD FS)에 대 한 단일 기호 (+)를 구성 합니다.
    
- Exchange 2013 서버와 Office 365 간의 보안 통신에 대 한 Exchange 인증서를 구성 합니다.
    
- 원하는 인바운드 인터넷 메일 경로 대 한 DNS 레코드를 구성 합니다.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 온-프레미스

- Exchange 서비스에 대 한 필요한 인증서를 구성 합니다.
    
- 서버를 구축 합니다.
    
- Exchange 메시지 라우팅 토폴로지를 구현 합니다.
    
- 데이터베이스 가용성 그룹을 구현 합니다.
    
- 업데이트 하 고 Exchange 서버를 유지 관리 합니다.
    
- 사용률에 따라 추가 또는 필요에 따라 서버를 제거 합니다.
    
#### <a name="provider-hosted-exchange"></a>Exchange 공급자 호스팅

공급자의 책임에는 다음이 포함 됩니다.
  
- 시스템 및 서비스 유지 관리 합니다.
    
- 롤아웃 기능을 합니다.
    
- 데이터 보호 및 재해 복구 합니다.
    
조직에서 IT 직원의 책임을 만들고 사용자 계정 관리를 포함 합니다.
  
#### <a name="more-information"></a>추가 정보

Exchange Online (Office 365)에 대 한 자세한 내용은 다음 항목을 참조 합니다.
  
- [Exchange Online 서비스 설명](https://aka.ms/EXOSD)
    
- [TechNet 라이브러리의 Exchange Online](https://aka.ms/EXOTN)
    
- [Exchange Online 포털](https://aka.ms/EXO)
    
Exchange 하이브리드에 대 한 자세한 내용은 다음 항목을 참조 합니다.
  
- [Exchange 2013 하이브리드 배포](https://aka.ms/ExchangeHybrid)합니다. 하이브리드 서버 라이선스만 인지에 주의 해야 다음과 같은 시나리오에 필요한: Exchange 2013 하이브리드 서버 및 Exchange 2007 조직의 Exchange 2013 또는 Exchange 2010 하이브리드 서버와 함께 사용 하 여 Exchange 2010 조직입니다.
    
- [Office 365 로그인](https://aka.ms/HybridKey)
    
Exchange Server 온-프레미스에 대 한 자세한 내용은 다음 항목을 참조 합니다.
  
- [Exchange Server 2013 TechNet 라이브러리](https://aka.ms/Ex2013TN)
    
- [Exchange Server 2013 포털](https://aka.ms/Exchange2013)
    
- [Exchange Server 2013의 아키텍처](https://aka.ms/Ex2013SP1ArchPoster)
    
Provider-Hosted Exchange에 대 한 자세한 내용은 다음 항목을 참조 합니다.
  
[Exchange Server 2013 호스팅 및 다중 테 넌 시 솔루션 및 지침](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Exchange 2013의 세 신규 또는 업데이트 된 기능에 대 한 설명이

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) 계층 데이터 센터의 글로벌 네트워크를 통해 배포 되는 보호 기능을 제공 하 여 모든 배포에 대 한 스팸 방지 및 맬웨어 방지 보호 기능을 제공 합니다. 이 통해 메시징 환경 관리를 단순화할 수 있습니다. EOP Exchange Online 구독에 포함 되어 있지만 하이브리드 및 온-프레미스 배포를 위한도 활용할 수 있습니다.
  
함께 제공 되는 다이어그램에 대해 Exchange Online, Exchange 하이브리드 Exchange 온-프레미스 및 전역 네트워크에서 EOP 계층을 포함 하는 배포를 보여줍니다.
  
### <a name="exchange-server-deployment-assistant"></a>Exchange Server 배포 도우미

Exchange Server 배포 도우미는 현재 환경에 대 한 몇가지 질문을 요청 하 고 다음 다양 한 유형의 시나리오에 대 한 Exchange 서버를 배포 하는 데 도움이 되도록 사용자 지정 단계별 검사 목록을 생성 하는 웹 기반 도구입니다. 만들지 여부를 Exchange에 Exchange 2013의 이전 버전에서 마이그레이션할 Exchange Online으로 마이그레이션하거나 하이브리드 인프라를 계획 Exchange Server 배포 도우미 시나리오에 대 한 사용자 지정 된 배포 검사 목록입니다.
  
함께 제공 되 스크린샷에서 Exchange Server 배포 도우미를 사용 하 여 만든 예제 검사 목록입니다.
  
### <a name="integration-with-lync-and-sharepoint"></a>Lync 및 SharePoint와의 통합

Exchange Server 2013 Lync Server 2013 및 SharePoint Server 2013와 통합 하는 다양 한 기능을 포함 합니다. 함께 이러한 제품은 풍부한 기능 집합을 제공 하 고 조직 전체에서 공동 작업을 향상 시킵니다. 
  
함께 제공 되는 다이어그램 서버-서버 인증 포스터를 표시 하 고 포스터에 대 한 링크를 제공 합니다. 
  
- 보관, 보류 및 eDiscovery
    
- 사이트 사서함
    
- 통합 연락처 저장소
    
- 고해상도 사용자 사진
    
- Outlook 및 Outlook Web App의 Lync 현재 상태
    
- 서버 간 인증
    
- Voicemail
    
- 모임 녹음/녹화
    
- Exchange 작업 동기화
    
함께 제공 되는 다이어그램 Exchange Server 2013 SP1 아키텍처 포스터를 표시 하 고 포스터에 대 한 링크를 제공 합니다.
  

