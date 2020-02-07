---
title: 액세스 가능한 다이어그램-SharePoint 용 Microsoft Azure 2013의 인터넷 사이트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
f1.keywords:
- NOCSH
description: 이 문서는 SharePoint 2013 용 Microsoft Azure의 인터넷 사이트 라는 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: a68c5f8a0e92c45e3c33caaca77be0d841aa6003
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843899"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>액세스 가능한 다이어그램-SharePoint 용 Microsoft Azure 2013의 인터넷 사이트

**요약:** 이 문서는 SharePoint 2013 용 Microsoft Azure의 인터넷 사이트 라는 액세스 가능한 텍스트 버전입니다.
  
이 포스터에서는 공용 연결 인터넷 사이트에서 클라우드 회복 력 및 고객 계정의 Azure AD를 활용 하는 방법을 설명 합니다. Azure에서 제공 하는 인터넷 사이트의 이점에 대해 설명 하는 6 가지 시나리오가 있습니다. 
  
- 팜 토폴로지를 디자인 하 고 크기를 조정 합니다. 
    
- Azure에 대 한 미세 조정 
    
- Active Directory 모델을 선택 합니다. 
    
- Id 관리, 영역 및 인증을 위한 디자인 
    
- 교차 사이트 게시용 사이트 및 Url을 디자인 합니다. 
    
- Azure 환경을 디자인 합니다. 
    
## <a name="design-and-size-the-farm-topology"></a>팜 토폴로지 디자인 및 크기 조정

TechNet의 SharePoint 2013에 대 한 토폴로지, 용량 및 성능 지침을 사용 하 여 팜 토폴로지를 디자인 합니다. 
  
디자인 한 팜이 용량 및 성능에 대 한 목표를 충족 하는지 확인 합니다. 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>예: 중간 규모 인터넷 사이트 팜 (초당 ~ 85 페이지 보기)

이 팜은 340만 항목을 포함 하는 모음에 최적화 된 내결함성 SharePoint 2013 search farm 토폴로지를 제공 합니다. 
  
예제 팜은 언어에 따라 초당 100-200 문서를 처리 하 고 초당 85 페이지 보기와 초당 100 쿼리를 수용 합니다. 
  
다음 다이어그램에는 세 가지 유형의 서버가 있는 중간 규모의 인터넷 사이트 팜이 나와 있습니다. 
  
- 웹 서버 
    
- 응용 프로그램 서버 
    
- 데이터베이스 서버 
    
#### <a name="web-servers"></a>웹 서버

웹 서버 섹션에는 호스트 A, 호스트 B 및 호스트 C의 세 가지 웹 서버가 있습니다. 각 웹 서버에는 분산 캐시, 사용자 프로필, 관리 되는 메타 데이터 및 쿼리 처리 기능이 포함 되어 있습니다. 각 서버에 있는 인덱스 파티션 복제 데이터베이스도 포함 됩니다. 
  
수평 확장 하려면 다음의 추가 28 페이지 보기를 허용 하는 동일한 기능을 사용 하 여 추가 웹 서버를 추가 합니다. 
  
#### <a name="application-servers"></a>응용 프로그램 서버

응용 프로그램 서버 섹션에는 3 개의 응용 프로그램 서버 (호스트 D, 호스트 E 및 호스트 F)가 있습니다. 호스트 D에는 크롤링, 관리, 분석 및 콘텐츠 처리 구성 요소가 포함 되어 있습니다. 호스트 E에는 크롤링, 관리 및 콘텐츠 처리 구성 요소가 포함 됩니다. 호스트 F에는 크롤링 및 콘텐츠 처리 구성 요소가 포함 되어 있습니다. 
  
수평 확장 하려면 크롤링 구성 요소가 포함 된 응용 프로그램 서버 한 대와 콘텐츠 처리 구성 요소를 추가 하 여 초당 추가 40 문서를 처리 합니다. 
  
#### <a name="database-servers"></a>데이터베이스 서버

데이터베이스 서버 섹션에는 호스트 G와 호스트 H의 두 서버가 있습니다. 데이터베이스 서버는 내결함성을 위한 쌍을 이룬 호스트에 있습니다. 
  
호스트 G에는 검색 관리 데이터베이스, 링크 데이터베이스, 두 개의 크롤링 데이터베이스, 분석 데이터베이스 및 기타 모든 SharePoint 데이터베이스를 비롯 한 모든 SharePoint 데이터베이스가 포함 됩니다. 호스트 H에는 SQL 클러스터링, 미러링 또는 SQL Server 2012 AlwaysOn을 사용 하 여 모든 데이터베이스의 중복 복사본을 포함 하 여 모든 SharePoint 데이터베이스가 포함 됩니다. 
  
## <a name="fine-tune-for-azure"></a>Azure에 대 한 미세 조정

Azure 플랫폼에서 가용성 집합에 맞게 SharePoint 팜을 미세 조정 해야 할 수 있습니다. 모든 구성 요소의 고가용성을 보장 하려면 서버 역할이 모두 동일 하 게 구성 되어 있는지 확인 합니다. 
  
다이어그램의 예제 토폴로지: 
  
- 웹 서버와 데이터베이스 서버는 동일 하 게 구성 됩니다. 
    
- 세 응용 프로그램 서버가 동일 하 게 구성 되지 않았습니다. 이러한 서버 역할을 사용 하려면 Azure의 가용성 집합에 대 한 미세 조정이 필요 합니다. 
    
### <a name="before"></a>Before

다이어그램 윗부분에는 Azure의 가용성 집합에 대해 미세 조정 되기 전에 SharePoint 팜이 표시 됩니다. 다이어그램에서 세 개의 호스트 응용 프로그램 서버가 동일 하 게 구성 되지 않았습니다. 구성 요소 수는 팜의 성능 및 용량 목표에 따라 결정 됩니다. 세 서버는 다음과 같이 구성 됩니다. 
  
- 호스트 D 응용 프로그램 서버는 크롤링, 관리, 분석 및 콘텐츠 처리 역할로 구성 됩니다. 
    
- 호스트 E 응용 프로그램 서버는 크롤링, 관리자 및 콘텐츠 처리 역할로 구성 됩니다. 
    
- 호스트 F 응용 프로그램 서버는 크롤링 및 콘텐츠 처리 역할로 구성 됩니다. 
    
### <a name="after"></a>마치면

이 다이어그램의 부분에는 Azure의 가용성 집합에 대해 미세 조정 된 SharePoint 팜이 나와 있습니다. Azure에 대해이 아키텍처를 조정 하기 위해 3 대의 모든 서버에서 네 개의 구성 요소를 복제 합니다. 이렇게 하면 성능 및 용량에 필요한 구성 요소의 수가 늘어납니다. 이러한 단점은 이러한 세 가지 가상 컴퓨터가 가용성 집합에 할당 될 때 Azure 플랫폼에 있는 네 가지 구성 요소의 고가용성을 보장 한다는 것입니다. 
  
세 서버는 모두 크롤링, 관리, 분석 및 콘텐츠 처리 역할을 갖도록 구성 됩니다. 
  
## <a name="choose-the-active-directory-model"></a>Active Directory 모델 선택

모든 SharePoint 솔루션에는 Windows AD DS (Active Directory 도메인 서비스)가 필요 합니다. 현재 Azure의 SharePoint 솔루션에는 두 가지 옵션이 있습니다. 
  
- 옵션 1: 전용 도메인-SharePoint 팜을 지원 하기 위해 Azure에 전용 및 격리 된 도메인을 배포할 수 있습니다. 이 옵션은 공용 인터넷 사이트에 적합 합니다. 
    
- 옵션 2: 사이트 간 VPN 연결을 통해 온-프레미스 도메인을 확장 합니다. 사이트 간 VPN 연결을 통해 온-프레미스 도메인을 확장 하면 사용자는 온-프레미스에 호스트 된 것 처럼 SharePoint 팜에 액세스 합니다. 기존 Active Directory 및 DNS 구현을 활용할 수 있습니다. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Id 관리, 영역 및 인증을 위한 디자인

### <a name="design-for-accounts-and-authentication"></a>계정 및 인증에 대 한 디자인

계정을 관리 하는 방법 및 사용 되는 인증 유형을 결정 합니다. 
  
#### <a name="accounts-for-site-developers-and-authors"></a>사이트 개발자 및 제작자를 위한 계정

- Azure의 도메인에 계정을 추가 합니다. 
    
- 온-프레미스 AD FS (Active Directory Federation Services)를 사용 하 여 내부 계정을 Azure의 도메인에 페더레이션 합니다. 
    
- 디자인에 사이트 간 VPN 연결이 포함 되어 있으면 내부 계정을 사용 합니다. 
    
#### <a name="accounts-for-customers"></a>고객을 위한 계정

- Azure Active Directory를 사용 합니다. 
    
- 다른 SAML 기반 공급자를 사용 합니다. 
    
### <a name="design-for-zones"></a>영역 디자인

SharePoint 2013에서 id 관리는 영역 및 인증 구성에 대 한 것입니다. 
  
이 디자인을 통해 다른 모든 계정과 고객 계정을 명확 하 게 분리할 수가 있습니다. 
  
- 고객 계정을 작성자 및 사이트 개발자를 위한 내부 계정과 완전히 다른 것으로 간주 하려면이 디자인을 사용 합니다. 
    
- 이 디자인을 사용 하 여 영역 정책을 사용 하 여 웹 응용 프로그램 내에서 고객 작업을 제한할 수 있습니다. 
    
- 이 디자인은 고객 계정 및 내부 계정에 대해 서로 다른 Url을 생성 합니다. 
    
이 예제의 특징은 다음과 같습니다. 
  
- 내부 계정의 기본 영역을 구성 합니다. 
    
- 고객 인증 액세스를 위한 엑스트라넷 영역을 구성 합니다. 고객 계정에 대해 Azure Active Directory (AD)를 사용 하거나 다른 SAML 기반 공급자를 사용 합니다. 
    
- 익명 액세스를 사용 하도록 인터넷 영역을 구성 합니다. 
    
인증 된 모든 사용자가 기본 영역을 사용 하도록 구성 되어 있는 두 영역 디자인을 사용 하지 마십시오. 
  
함께 제공 되는 다이어그램에서는 내부 및 고객 계정이 분리 된 3 영역 디자인을 보여 줍니다. 
  
방문자 및 고객은 두 영역 중 하나에서 웹 응용 프로그램을 통해 SharePoint 2013 팜의 Azure AD 테 넌 트에 액세스 합니다. 두 영역에는 다음이 포함 됩니다. 
  
- 영역: 익명 사용자의 인터넷 
    
- 영역: 인증 된 사용자에 대 한 엑스트라넷 
    
내부 계정이 있는 사용자는 Azure AD에 대 한 VPN 터널을 통해 온-프레미스 환경에서 AD DS 및 AD FS의 Azure Active Directory 테 넌 트에 액세스 합니다. 기본 영역은 Windows 인증 (NTLM)을 제공 합니다. 
  
### <a name="design-for-connecting-to-azure-ad"></a>Azure AD에 연결 하기 위한 디자인

 Azure AD는 클라우드 서비스에 대 한 id 관리 및 액세스 제어 기능을 제공 합니다. 기능에는 디렉터리 데이터를 위한 클라우드 기반 저장소와 사용자 로그온 프로세스, 인증 서비스 및 AD FS 등의 핵심 id 서비스가 포함 됩니다. Azure AD에 포함 된 id 서비스는 온-프레미스 AD DS 배포와 쉽게 통합 되며 타사 id 공급자를 완벽 하 게 지원 합니다.
  
함께 제공 되는 다이어그램에서는 다음과 같은 시나리오를 보여 줍니다. 
  
Azure Active Directory와 함께 SharePoint 2013을 통합 하는 경우에는 ACS (액세스 제어 서비스)가 다음과 같은 두 가지 용도로 사용 됩니다. 
  
-  Azure AD는 SAML 2.0을 사용 하며, SharePoint는 SAML 1.1 에서만 작동 합니다. ACS는 두 가지 형식을 모두 이해 하 고 SharePoint 및 Azure AD 간에 토큰 형식을 변환 하기 위한 중개 역할을 합니다.
    
- ACS는이 SAML 시나리오에 대해 id 공급자 STS (security token service)에 대 한 요구를 대체 합니다. 
    
자세한 내용은 TechNet 라이브러리에서 SharePoint 2013을 사용 하 여 Azure AD 구성를 참조 하세요. 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>교차 사이트 게시용 사이트 및 Url 디자인

게시 시나리오에는 하나의 웹 응용 프로그램 디자인을 사용 하는 것이 좋습니다. 
  
- 두 제작 사이트와 게시 사이트가 같은 웹 응용 프로그램에 있습니다. 
    
- 교차 사이트 게시는 자산을 게시 하는 데 사용 됩니다. 
    
경로 기반 및 호스트 이름으로 된 사이트 모음을 사용 합니다. 
  
- 루트 사이트 모음은 필수 사항입니다. 이 사이트를 경로 기반 사이트로 만듭니다. 
    
- 다른 모든 사이트 모음을 호스트 이름으로 된 사이트 모음으로 만듭니다. 
    
웹 응용 프로그램 및 루트 사이트 Url 
  
- 웹 응용 프로그램 URL에 내부 이름을 사용 합니다. 다른 이름이 지정 되지 않은 경우 SharePoint에서 로컬 컴퓨터 이름을 기본 이름으로 사용 합니다. 내부 네트워크 환경에 예약 된 도메인 이름을 사용할 수 있습니다. 
    
- SharePoint는 웹 응용 프로그램을 만들 때 비표준 포트 번호를 할당 합니다. 포트 80 또는 포트 443 대신이 포트 번호를 사용 합니다. 또는 다른 비표준 포트 번호를 사용 합니다. 
    
- 루트 사이트 모음에는 경로 기반 사이트 모음에 해당 하는 이름과 포트 번호를 사용 합니다. 
    
함께 제공 되는 다이어그램은 웹 응용 프로그램을 사용 하 여 사이트 모음과 상호 작용 하는 검색 같은 응용 프로그램 풀 서비스를 보여줍니다 다음과 같은 사이트 모음이 표시 됩니다. 
  
- (루트 사이트)에 https://internal:8000 있는 경로 기반 사이트 모음입니다. 
    
- 크롤링:와 같은 주소에 있는 호스트 이름으로 https://authoring.contoso.com:8000된 사이트 모음입니다. 
    
- 쿼리: 2 주소에 있는 별도의 호스트 이름이 지정 된 사이트 모음: 
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Azure 환경 디자인

이 예제 아키텍처에는 다음과 같은 요소가 포함 됩니다. 
  
- 사이트 간 VPN 연결은 선택 사항이 며 온-프레미스 Windows AD DS 및 DNS 환경을 Azure의 가상 네트워크로 확장 합니다. 
    
- 필요한 경우 Azure에서 전용 도메인을 사용 하 여 SharePoint 팜을 지원 합니다. 
    
- 서버는 역할에 따라 Azure 클라우드 서비스 간에 분할 됩니다. 
    
- 가용성 집합은 동일 하 게 구성 된 서버 역할의 고가용성을 보장 합니다. 
    
자세한 내용은 TechNet: Azure 아키텍처 for SharePoint 솔루션용의 다음 문서를 참조 하세요. 
  
함께 제공 되는 다이어그램에는 Azure virtual network와 연결 되는 온-프레미스 환경의 예가 나와 있습니다. 
  
Azure 환경의 선택적 요소인 온-프레미스 환경에는 다음과 같은 구성 요소가 포함 되어 있습니다. 
  
- Windows Server 2012 RRAS 
    
- AD DS 
    
- Windows Server 및 AD DS에서 활성 VPN 게이트웨이 서브넷으로의 VPN 게이트웨이 
    
Azure virtual network 환경에는 다음과 같은 구성 요소가 포함 됩니다. 
  
- 활성 VPN 게이트웨이 서브넷 (해당 하는 경우 온-프레미스 환경과 겹칩니다) 
    
- AD DS 및 DNS 가용성 집합을 포함 하는 클라우드 서비스 (서버 2 대) 
    
- 프런트 엔드 서버 가용성 집합 (SharePoint 서버 3 대) 및 앱 서버 가용성 집합 (3 개의 SharePoint 서버)이 포함 된 클라우드 서비스 
    
- 두 개의 데이터베이스 사용 가능 집합이 포함 된 클라우드 서비스 
    

