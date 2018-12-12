---
title: 액세스할 수 있는 다이어그램-SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: 이 문서는 SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트를 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503051"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>액세스할 수 있는 다이어그램-SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트

**요약:** 이 문서는 SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트를 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
  
이 포스터에 설명 합니다 클라우드 탄성 및 고객 계정에 대 한 Azure AD에서 어떻게 공용 인터넷 사이트 복리 후생 합니다. Azure에서 인터넷 사이트 활용 하는 방법을 설명 하는 6 개의 서로 다른 시나리오 가지가 있습니다. 
  
- 디자인 및 팜 토폴로지 크기를 조정 합니다. 
    
- Azure에 대 한 세부적으로 조정 합니다. 
    
- Active Directory 모델을 선택 합니다. 
    
- Id 관리, 영역 및 인증에 대 한 디자인 합니다. 
    
- 교차 사이트 게시에 대 한 사이트 및 Url을 디자인 합니다. 
    
- Azure 환경을 디자인 합니다. 
    
## <a name="design-and-size-the-farm-topology"></a>디자인 및 크기 조정 팜 토폴로지

팜 토폴로지를 디자인 하는 TechNet의 SharePoint 2013에 대 한 토폴로지, 용량 및 성능 지침을 사용 합니다. 
  
용량 및 성능 목표를 충족 하는 디자인 하는 팜 확인 합니다. 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>예: 중간 규모 인터넷 사이트 팜 (초당 ~ 85 페이지 보기)

이 팜의 3,400,000 항목이 포함 된 모음에 대해 최적화 된 내결함성 SharePoint 2013 검색 팜 토폴로지를 제공 합니다. 
  
예제 팜은 언어에 따라 초당 100-200 문서를 처리 하 고 초당 쿼리 수 두번째 및 100 당 85 페이지 보기를 수용 합니다. 
  
함께 제공 된 다이어그램은 다음과 같은 세가지 유형의 서버 포함 된 중간 규모 인터넷 사이트 팜을 보여줍니다. 
  
- 웹 서버 
    
- 응용 프로그램 서버 
    
- 데이터베이스 서버 
    
#### <a name="web-servers"></a>웹 서버

웹 서버 섹션에서 웹 서버 세대, 호스트 A, 호스트 B 및 없는 호스트 C. 각 웹 서버는 분산된 캐시, 사용자 프로필, 관리 되는 메타 데이터 및 쿼리 처리 기능을 포함 합니다. 각 서버에 있는 인덱스 파티션의 복제 데이터베이스도 포함 합니다. 
  
추가 28를 허용 하는 동일한 기능을 함께 추가 웹 서버를 추가, 확장할 초당 페이지를 봅니다. 
  
#### <a name="application-servers"></a>응용 프로그램 서버

응용 프로그램 서버 섹션에서 세가지 응용 프로그램 서버를 호스트 D 호스트 E 및 호스트 F. 호스트 D 크롤링, 관리, 분석 및 콘텐츠 처리 구성 요소를 포함 합니다. 호스트 E 크롤링, 관리자 및 콘텐츠 처리 구성 요소를 포함합니다. 호스트 F 크롤링 및 콘텐츠 처리 구성 요소를 포함합니다. 
  
수평 확장, 크롤링 구성 요소와 콘텐츠 처리 구성 요소 초당 추가 40 문서를 처리할 수 있는 하나의 응용 프로그램 서버를 추가 합니다. 
  
#### <a name="database-servers"></a>데이터베이스 서버

데이터베이스 서버 섹션에는 두 서버가 호스트 G 및 호스트 H. 데이터베이스 서버가 내결함성에 대 한 쌍으로 지정 된 호스트에 있습니다. 
  
호스트 G 검색 관리 데이터베이스, 링크 데이터베이스, 두 크롤링 데이터베이스, 분석 데이터베이스를 다른 모든 SharePoint 데이터베이스를 포함 하는 모든 SharePoint 데이터베이스를 포함 합니다. 호스트 H SQL 클러스터링, 미러링, 또는 SQL Server 2012 AlwaysOn을 사용 하 여 모든 데이터베이스의 중복 복사본을 포함 하 여 모든 SharePoint 데이터베이스를 포함 합니다. 
  
## <a name="fine-tune-for-azure"></a>Azure에 대 한 세부 조정

SharePoint 팜 Azure 플랫폼에서 가용성 집합에 대 한 미세 조정할 수 해야할 수 있습니다. 모든 구성 요소의 고가용성을 보장 하려면 서버 역할이 모두 동일 하 게 구성 되었는지 확인 합니다. 
  
다이어그램에 대 한 예제 토폴로지에서: 
  
- 웹 서버 및 데이터베이스 서버 구성 동일 하 게 됩니다. 
    
- 세 응용 프로그램 서버 동일 하 게 구성 되지 않습니다. 이러한 서버 역할 Azure에서 설정 하는 가용성에 대 한 미세 조정에 필요 합니다. 
    
### <a name="before"></a>Before

다이어그램의 위쪽 부분 Azure에서 설정 하는 SharePoint 팜 가용성에 대 한 세밀 된가 전에 표시 합니다. 이 다이어그램에서는 세 호스트 응용 프로그램 서버는 동일 하 게 구성 되지 않았습니다. 구성 요소의 수는 팜에 대 한 성능 및 용량 목표에 따라 결정 됩니다. 세 서버는 다음과 같이 구성 됩니다. 
  
- 크롤링, 관리, 분석 및 콘텐츠 처리 역할과 D 호스트 응용 프로그램 서버 구성 됩니다. 
    
- 크롤링, 관리자 및 콘텐츠 처리 역할과 E 호스트 응용 프로그램 서버 구성 됩니다. 
    
- 크롤링 및 콘텐츠 처리 역할과 F 호스트 응용 프로그램 서버 구성 됩니다. 
    
### <a name="after"></a>After

다이어그램의이 부분 Azure에서 설정 하는 SharePoint 팜 가용성에 대 한 세밀 된가 후 표시 합니다. 이 아키텍처 azure에 맞게 세 서버 모두 4 개의 구성 요소에 복제는 표시 됩니다. 이 성능 및 용량에 필요한 것 보다 세부적 구성 요소의 수를 늘립니다. 단점은이 디자인 때 이러한 세 가상 컴퓨터 가용성 집합에 할당 된 모든 구성 요소 4 개 Azure 플랫폼에서의 고가용성을 보장 하는 것입니다. 
  
세 서버에 구성 된 모든 크롤링, 관리, 분석 및 콘텐츠 처리 역할이 있는지 여부. 
  
## <a name="choose-the-active-directory-model"></a>Active Directory 모델을 선택 합니다.

모든 SharePoint 솔루션의 경우 Windows Active Directory 도메인 서비스 (AD DS) 필요합니다. 이 시간에서 Azure의 SharePoint 솔루션에 대 한 두 옵션이 있습니다. 
  
- 옵션 1: 전용된 도메인-SharePoint 팜의 지원 하기 위해 Azure에 전용 및 격리 된 도메인을 배포할 수 있습니다. 공용 인터넷 사이트에 대 한 좋은 선택입니다. 
    
- 옵션 2: 사이트 마다 VPN 연결을 통해 온-프레미스 도메인을 확장 합니다. 사이트 마다 VPN 연결을 통해 온-프레미스 도메인을 확장 하면 마치 호스팅된 온-프레미스 것 처럼 사용자가 SharePoint 팜에 액세스 합니다. 기존 Active Directory 및 DNS 구현을 활용할 수 있습니다. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Id 관리, 영역 및 인증에 대 한 디자인

### <a name="design-for-accounts-and-authentication"></a>계정 및 인증에 대 한 디자인

계정 관리 하는 방법 및 사용할 인증 유형을 결정 합니다. 
  
#### <a name="accounts-for-site-developers-and-authors"></a>사이트 개발자와 작성자에 대 한 계정

- Azure의 도메인에 계정을 추가 합니다. 
    
- 온-프레미스 Active Directory Federation Services (AD FS)를 사용 하 여 Azure에서 도메인을 내부 계정 페더레이션. 
    
- 디자인 사이트 마다 VPN 연결을 포함 하는 경우에 내부 계정을 사용 합니다. 
    
#### <a name="accounts-for-customers"></a>고객에 대 한 계정

- Azure Active Directory를 사용 합니다. 
    
- 다른 SAML 기반 공급자를 사용 합니다. 
    
### <a name="design-for-zones"></a>영역에 대 한 디자인

SharePoint 2013 id 관리 영역 및 인증의 구성으로 구분 됩니다. 
  
이 디자인 명확 하 게 분리 고객 계정의 다른 모든 계정에서 제공합니다. 
  
- 원할 경우 처리 하기 위해 고객 계정을 내부 계정에서 완전히 다른 작성자 및 사이트 개발자를 위한이 디자인을 사용 합니다. 
    
- 이 디자인을 사용 하 여 웹 응용 프로그램 내에서 고객의 작업을 제한 하려면 영역 정책을 사용할 수 있습니다. 
    
- 이 디자인 고객 계정과 내부 계정에 대 한 서로 다른 Url 만들어집니다. 
    
이 예제의 특징은 다음과 같습니다. 
  
- 내부 계정에 대 한 기본 영역을 구성 합니다. 
    
- 인증 된 사용자 액세스를 위한 익스트라넷 영역을 구성 합니다. Azure Active Directory (AD)를 사용 하 여 고객 계정에 대 한 또는 다른 SAML 기반 공급자를 사용 합니다. 
    
- 익명 액세스를 위한 인터넷 영역을 구성 합니다. 
    
기본 영역을 사용 하도록 구성 된 모든 인증 된 사용자는 두 영역 디자인을 사용 하지 마십시오. 
  
함께 제공 되는 다이어그램 빈칸이 내부의 세 영역 디자인 및 고객 계정을 보여줍니다. 
  
방문자 및 고객 Azure AD 테 넌 트 SharePoint 2013 팜에서 두 영역 중 하나에서 웹 응용 프로그램을 통해 액세스 합니다. 두 영역에는 다음이 포함 됩니다. 
  
- 익명 사용자에 대 한 영역: 인터넷 
    
- 영역: 인증 된 사용자에 대 한 엑스트라넷 
    
내부 계정 가진 사용자가 Azure AD를 AD DS와 VPN 터널을 통해 온-프레미스 환경에서 AD FS에서에서 Azure Active Directory 테 넌 트에 액세스 합니다. 기본 영역 Windows 인증 (NTLM)를 제공합니다. 
  
### <a name="design-for-connecting-to-azure-ad"></a>Azure AD에 연결 하기 위한 디자인

 Azure AD 클라우드 서비스에 대 한 id 관리 및 액세스 제어 기능을 제공합니다. 기능은 디렉터리 데이터 및 사용자 로그온 프로세스, 인증 서비스 및 AD FS를 포함 하 여 identity 서비스의 핵심 집합에 대 한 클라우드 기반 저장소를 포함 합니다. 온-프레미스와 쉽게 Azure AD에 포함 된 id 서비스 통합 AD DS 배포 및 지원 타사 id 공급자를 완벽 하 게 합니다.
  
함께 제공 된 다이어그램은 다음과 같은 시나리오를 보여줍니다. 
  
SharePoint 2013 Azure Active Directory를 통합 하는 경우는 Azure 서비스 ACS (액세스 제어)은 두 용도로 사용 됩니다. 
  
-  SAML 2.0을 사용 하 여 azure AD와 SharePoint SAML 1.1에 대해서만 작동 합니다. ACS 형식 모두를 인식 하 고 SharePoint와 Azure AD 사이의 토큰 형식을 변환 하는 중 계자 역할입니다.
    
- ACS는 id 공급자 보안 토큰 서비스 (IP STS)이 SAML 시나리오에 대 한 필요성을 대체합니다. 
    
자세한 내용은 TechNet 라이브러리의 SharePoint 2013과 함께 Azure AD 구성을 참조 하십시오. 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>사이트 디자인 및 교차 사이트 게시에 대 한 Url

하나의 웹 응용 프로그램 디자인 시나리오를 게시 하기 위한 것이 좋습니다. 
  
- 제작 및 게시 사이트 모두 동일한 웹 응용 프로그램에 있습니다. 
    
- 교차 사이트 게시를 사용 하 여 자산을 게시 합니다. 
    
경로 기반 및 호스트 이름이 지정 된 사이트 모음을 사용 합니다. 
  
- 루트 사이트 모음 요구 됩니다. 경로 기반 사이트와이 사이트를 만듭니다. 
    
- 호스트 이름이 지정 된 사이트 모음으로 다른 모든 사이트 모음을 만듭니다. 
    
웹 응용 프로그램 및 루트 사이트 Url 
  
- 웹 응용 프로그램 URL에 대 한 내부 이름을 사용 합니다. SharePoint는 다른 이름을 지정 하지 않으면 기본 이름으로 로컬 컴퓨터 이름을 사용 합니다. 내부 네트워크 환경에 대 한 예약 된 도메인 이름을 사용할 수 있습니다. 
    
- SharePoint 웹 응용 프로그램을 만들 때 비표준 포트 번호를 할당 합니다. 이 포트 번호를 사용 하 여 포트 80 또는 포트 443 대신 합니다. 또는 다른 하지만 비표준 포트 번호를 사용 합니다. 
    
- 경로 기반 사이트 모음인 루트 사이트 모음에 대 한 동일한 이름 및 포트 번호를 사용 합니다. 
    
함께 제공 된 다이어그램은 웹 응용 프로그램을 사용 하 여 사이트 모음과 상호작용 검색 등의 응용 프로그램 풀 서비스를 보여줍니다. 표시 된 사이트 모음에는 다음이 포함 됩니다. 
  
- Http://internal:8000 (루트 사이트)에 있는 경로 기반 사이트 모음입니다. 
    
- Https://authoring.contoso.com:8000와 같은 주소에 있는 크롤링: 호스트 이름이 지정 된 사이트 모음입니다. 
    
- 쿼리 수 있습니다: 2 별도 호스트 이름이 지정 된 사이트 모음에 있는 주소와 같은: 
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Azure 환경 디자인

이 예제에서는 아키텍처에는 다음 요소가 포함 됩니다. 
  
- 사이트 마다 VPN 연결은 선택 사항이 며 온-프레미스 AD DS 창과 DNS 환경 Azure에 가상 네트워크를 확장 합니다. 
    
- 필요에 따라 Azure의 전용된 도메인을 사용 하 여 SharePoint 팜을 지원 합니다. 
    
- 서버 역할에 따라 Azure 클라우드 서비스 간에 분할 됩니다. 
    
- 가용성 집합 동일 하 게 구성 된 서버 역할의 고가용성을 확인합니다. 
    
자세한 내용은 TechNet의 다음 문서를 참조: Azure Architectures for SharePoint 솔루션입니다. 
  
함께 제공 되는 다이어그램에는 Azure 가상 네트워크를 연결 하는 온-프레미스 환경의 예가 나와 있습니다. 
  
Azure 환경의 선택적 요소는 온-프레미스 환경에 포함 된 다음과 같은 요소가 있습니다. 
  
- Windows Server 2012 RRAS 
    
- AD DS 
    
- 현재 VPN 게이트웨이 서브넷에 Windows Server 및 AD DS에서 VPN 게이트웨이 
    
Azure 가상 네트워크 환경에는 다음 구성 요소가 포함 됩니다. 
  
- 현재 VPN 게이트웨이 서브넷 (해당 되는 경우 온-프레미스 환경에서 겹치는) 
    
- AD DS 및 DNS 사용 가능 여부를 포함 하는 클라우드 서비스 설정 (2 명의 서버) 
    
- 프런트엔드 서버 가용성을 포함 하는 클라우드 서비스 (세 SharePoint 서버)를 설정 하 고 응용 프로그램 서버 가용성 (세 SharePoint 서버)를 설정 합니다. 
    
- 두 데이터베이스 가용성을 포함 하는 클라우드 서비스 설정 
    

