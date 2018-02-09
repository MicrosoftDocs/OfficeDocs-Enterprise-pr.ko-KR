---
title: "SharePoint 2013에 대 한 Microsoft Azure 아키텍처"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: "요약: SharePoint 2013 솔루션은 Microsoft Azure 가상 컴퓨터에서 호스팅할 수 있습니다. 어떤 유형의 솔루션은 가장 잘 맞는 및 Microsoft Azure 하나는 호스트를 설정 하는 방법에 알아봅니다."
ms.openlocfilehash: 5156f3e8cabb3acabc7ad23a680a016c200c676e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>SharePoint 2013에 대 한 Microsoft Azure 아키텍처

 **요약:** SharePoint 2013 솔루션은 Microsoft Azure 가상 컴퓨터에서 호스팅할 수 있습니다. 어떤 유형의 솔루션은 가장 잘 맞는 및 Microsoft Azure 하나는 호스트를 설정 하는 방법에 알아봅니다.
  
Azure는 SharePoint Server 2013 솔루션을 호스팅하기 위한 좋은 환경입니다. 대부분의 경우에서 Office 365 좋지만 Azure에서 호스팅되는 SharePoint 서버 팜의 특정 솔루션에 대 한 적절 한 옵션이 될 수 있습니다. 이 문서에서는 SharePoint 솔루션 좋은 되도록 Azure 플랫폼에 맞게 설계 하는 방법을 설명 합니다. 다음 두 특정 솔루션은 예제로 사용 됩니다.
  
- [Microsoft Azure의 SharePoint Server 2013 재해 복구](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Azure 인프라 서비스에 대 한 권장 되는 SharePoint 솔루션

Azure 인프라 서비스에는 SharePoint 솔루션을 호스팅하기 위한 주목할 옵션입니다. 일부 솔루션은 다른 사용자 보다이 플랫폼에 대 한 보다 적합 합니다. 다음 표에서 권장 되는 솔루션을 보여줍니다.
  
|**해결 방법**|**이 솔루션은 Azure에 대 한 권장 되는 이유**|
|:-----|:-----|
|개발 및 테스트 환경  <br/> |만들고 이러한 환경을 관리 하기 쉽습니다.  <br/> |
|Azure로의 온-프레미스 SharePoint 팜 재해 복구  <br/> |**호스트 된 보조 데이터 센터** Azure를 사용 하 여 서로 다른 영역에 보조 데이터 센터에 투자 하는 대신 합니다. <br/> **저렴 재해 복구 환경** 유지 관리 하 고는 온-프레미스 재해 복구 환경 보다 적은 자원에 대 한 지불 합니다. 자원 수 있습니다를 선택 하는 재해 복구 환경에 따라 달라 집니다: 정지 대기, 웜 대기 또는 핫 대기 합니다.<br/> **보다 탄력적 플랫폼** 재해 발생 시 쉽게 확장 복구 SharePoint 팜의 부하 요구 사항을 충족 합니다. 리소스에는 필요 없는 경우의 수직 확장 합니다.<br/> [Microsoft Azure의 SharePoint Server 2013 재해 복구](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)를 참조 하십시오.  <br/> |
|기능 및 Office 365에서 사용할 수 없는 확장을 사용 하는 인터넷 사이트  <br/> |**자신의 노력** 인프라를 구축 하는 것 보다 큰 사이트 만들기 (영문)에 집중 합니다. <br/> **Azure에서 탄성을 활용** 새 서버를 추가 하 여 요청에 대 한 팜 크기를 조정 하 고 필요한 리소스에 대해서만 지불 합니다. 동적 컴퓨터 할당이 올바르지 않은 (자동 크기 조정)를 지원 합니다.<br/> **Azure Active Directory (AD)를 사용 하 여** 고객 계정에 대 한 Azure AD 활용 합니다. <br/> **Office 365에서 사용할 수 없는 SharePoint 추가 기능** 상세 보고 및 웹 분석을 추가 합니다. <br/> [SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)를 참조 하십시오.  <br/> |
|Office 365 또는 온-프레미스 환경을 지원 하도록 app 팜  <br/> |**빌드, 테스트 및 호스트 앱** Azure 지원 모두 온-프레미스 및 클라우드 환경입니다. <br/> Azure 온-프레미스 환경에 대 한 새 하드웨어를 구입 하는 대신에 **이 역할을 호스트** 을 선택 합니다. <br/> |
   
인트라넷 및 공동 작업 솔루션 및 작업을 다음 옵션을 고려 합니다.
  
- Office 365 비즈니스 요구 사항을 충족 또는 솔루션의 일부가 될 수를 확인 합니다. Office 365에는 항상 최신 상태로 유지 하는 다양 한 기능 집합을 제공 합니다.
    
- Office 365 모든 비즈니스 요구 사항을 충족 하지 않는, SharePoint 2013 온-프레미스에서 Microsoft Consulting Services (MCS) 표준 구현을 하는 것이 좋습니다. 표준 아키텍처를 사용자 지정 된 것 보다 지원할 수 있습니다, 가격이, 더 쉽고 빠르게 솔루션 될 수 있습니다. 
    
- 표준 구현도 비즈니스 요구 사항을 충족 하지 하는 경우 사용자 지정 된 온-프레미스 솔루션을 고려 합니다.
    
- 클라우드 플랫폼을 사용 하 여 비즈니스 요구 사항에 대 한 중요 한 경우 Azure 인프라 서비스에서 호스팅되는 SharePoint 2013의 표준 또는 사용자 지정 된 구현을 하는 것이 좋습니다. SharePoint 솔루션을 훨씬 쉽게 다른 기본이 아닌 Microsoft 공용 클라우드 플랫폼 보다 Azure에서 지원할 수 있습니다.
    
## <a name="before-you-design-the-azure-environment"></a>Azure 환경을 디자인 하기 전에

이 문서의 예제에서는 SharePoint 토폴로지를 사용 하는 동안에 모든 SharePoint 팜 토폴로지를 사용 하 여 이러한 디자인 개념을 사용할 수 있습니다. Azure 환경을 디자인 하기 전에 다음 토폴로지, 아키텍처, 용량 및 성능 지침을 사용 하 여 SharePoint 팜 디자인 수 있습니다:
  
- [SharePoint 2013 IT 전문가 위한 아키텍처 디자인](http://technet.microsoft.com/en-us/sharepoint/fp123594.aspx)
    
- [성능 및 SharePoint Server 2013의 용량 관리에 대 한 계획](http://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>Active Directory 도메인 유형 결정

각 SharePoint 서버 팜은 팜 설치에 대 한 관리 계정을 제공 하기 위해 Active Directory를 사용 합니다. 이 시간에서 Azure의 SharePoint 솔루션에 대 한 두 옵션이 있습니다. 이러한 옵션은 다음 표에 설명 되어있습니다.
  
|**옵션**|**설명**|
|:-----|:-----|
|전용된 도메인  <br/> |SharePoint 팜의 지원 하기 위해 Azure에 전용 및 격리 된 Active Directory 도메인을 배포할 수 있습니다. 공용 인터넷 사이트에 대 한 좋은 선택입니다.  <br/> |
|크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 합니다.  <br/> |크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 하면 마치 호스팅된 온-프레미스 것 처럼 사용자가 인트라넷을 통해 SharePoint 팜의 액세스 합니다. 온-프레미스 Active Directory 및 DNS 구현을 활용할 수 있습니다.  <br/> 크로스-프레미스 연결이 장애 조치 하 여 온-프레미스 팜에서 Azure의 재해 복구 환경을 구축 하기 위한 필요 합니다.  <br/> |
   
이 문서에 대 한 크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 하기 위한 디자인 개념 포함 됩니다. 솔루션 전용된 도메인을 사용 하는 경우 크로스-프레미스 연결이 필요는 없습니다.
  
## <a name="design-the-virtual-network"></a>가상 네트워크를 디자인 합니다.

먼저 가상 컴퓨터에서는 겁니다 서브넷을 포함 하는 Azure에 가상 네트워크를 해야 합니다. 가상 네트워크 서브넷에 할당 하는 중 일부는 개인 IP 주소 공간이 필요 합니다.
  
다른 위치를 포함할 수 있는 조직 네트워크에서에서 사용 하지 않은 개인 주소 공간을 선택 해야 Azure에 온-프레미스 네트워크 확장 하는 크로스-프레미스 연결 (재해 복구 환경에 필요)을 통해, 하는 경우 온-프레미스 환경 및 기타 Azure 가상 네트워크입니다. 
  
**Azure에 가상 네트워크를 사용 하는 그림 1: 온-프레미스 환경**

![SharePoint 솔루션에 대한 Microsoft Azure Virtual Network 디자인입니다. Azure Gateway에 대한 하나의 서브넷입니다. 가상 컴퓨터에 대한 하나의 서브넷입니다.](images/OPrrasconWA_AZarch.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- Azure에서 가상 네트워크는 온-프레미스 환경으로 수평적으로 그림이 합니다. 두 환경 사이트 마다 VPN 연결 또는 ExpressRoute 될 수 있는 크로스-프레미스 연결을 통해 아직 연결 되지 않습니다.
    
- 이 시점에서 가상 네트워크 서브넷 및 없는 다른 아키텍처 요소에만 포함합니다. 하나의 서브넷 Azure 게이트웨이 호스팅하고 다른 서브넷 SharePoint 팜에 있는 Active Directory 및 DNS에 대 한 추가 계층을 호스트 합니다.
    
## <a name="add-cross-premises-connectivity"></a>크로스-프레미스 연결 추가

다음 배포 단계 (이 솔루션에 적용 됨) 하는 경우 크로스-프레미스 연결을 만드는 것입니다. 크로스-프레미스 연결에 대 한 Azure 게이트웨이 별도 게이트웨이 서브넷에 있는 만들고 주소 공간을 할당 해야 합니다. 
  
크로스-프레미스 연결에 대 한 계획 하는 경우를 정의 하 고는 Azure 게이트웨이 만들고 온-프레미스 게이트웨이 장치를 연결 합니다.
  
**그림 2: Azure 게이트웨이와 온-프레미스 게이트웨이 장치를 사용 하 여 온-프레미스 환경 및 Azure 사이의 사이트 간 연결을 제공 하려면**

![크로스-프레미스 연결(사이트 간 VPN 연결 또는 Express 경로일 수 있음)에 의해 Azure Virtual Network에 연결된 온-프레미스 환경](images/AZarch_VPNgtwyconnct.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- 다이어그램에 추가 하는 이전, 온-프레미스 환경에 연결 되어 Azure 가상 네트워크 사이트 마다 VPN 연결 또는 ExpressRoute 될 수 있는 한 크로스-프레미스 연결 하 여 합니다.
    
- Azure는 게이트웨이 게이트웨이 서브넷에 있습니다.
    
- 온-프레미스 환경 라우터 또는 VPN 서버와 같은 게이트웨이 장치를 포함합니다.
    
크로스-프레미스 가상 네트워크 만들기 및 계획에 대 한 자세한 내용은 [Microsoft Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조 하십시오.
  
## <a name="add-windows-server-active-directory-ad-and-dns"></a>Windows Server Active Directory (AD)를 추가 하 고 DNS

Windows Server AD Azure의 재해 복구를 위한 배포 및 하이브리드 시나리오에서 Windows Server AD의 DNS 두 온-프레미스 배포 및 Azure 가상 컴퓨터에서 합니다.
  
**그림 3: 하이브리드 Active Directory 도메인 구성**

![Azure Virtual Network와 SharePoint 팜 서브넷에 배포된 두 가상 컴퓨터: 복제 도메인 컨트롤러 및 DNS 서버](images/AZarch_HyADdomainConfig.png)
  
이 다이어그램 두 가상 컴퓨터에 Windows Server AD 및 DNS 서브넷을 추가 하 여 이전 다이어그램에 구축 합니다. 이러한 가상 컴퓨터는 복제 도메인 컨트롤러 및 DNS 서버입니다. 온-프레미스 Windows Server AD 환경의 확장 됩니다. 
  
다음 표에서 Azure에 이러한 가상 컴퓨터에 대 한 구성 권장 사항을 제공 합니다. 시작 지점으로이 사용 하 여 사용자가 자신의 환경 디자인 (영문)에 대 한-온-프레미스 환경의 Azure 환경 하지 통신할 전용된 도메인에 대 한도입니다.
  
|**항목**|**구성**|
|:-----|:-----|
|Azure에 가상 컴퓨터 크기  <br/> |표준 계층에서 A1 또는 A2 크기  <br/> |
|운영 체제  <br/> |Windows Server 2012 R2  <br/> |
|Active Directory 역할  <br/> |AD DS 도메인 컨트롤러를 글로벌 카탈로그 서버로 지정 합니다. 이 구성은 크로스-프레미스 연결을 통해 탈출 트래픽을 줄입니다.  <br/> (공통 되지 않음) 변경 속도가 빠른 다중 도메인 환경에서 온-프레미스 복제 트래픽을 줄일 수 Azure에서 글로벌 카탈로그 서버와 동기화 할 필요가 도메인 컨트롤러를 구성 합니다.  <br/> |
|DNS 역할  <br/> |설치 하 고 도메인 컨트롤러에서 DNS 서버 서비스를 구성 합니다.  <br/> |
|데이터 디스크  <br/> |Active Directory 데이터베이스, 로그 및 SYSVOL Azure 추가 데이터 디스크에 배치 합니다. 이러한 운영 체제 디스크 또는 Azure에서 제공 하는 임시 디스크에 배치 하지 마십시오.  <br/> |
|IP 주소  <br/> |고정 IP 주소를 사용 하 고 도메인 컨트롤러를 구성한 후 이러한 주소는 가상 네트워크의 가상 컴퓨터를 할당 하 여 가상 네트워크를 구성 합니다.  <br/> |
   
> [!IMPORTANT]
> Azure의 Active Directory를 배포 하기 전에 [Windows Server Active Directory를 배포에 Azure 가상 컴퓨터에 대 한 지침](https://go.microsoft.com/fwlink/p/?linkid=392681)을 제공 합니다. 솔루션에 필요한 다른 아키텍처 또는 다른 구성 설정 하는 경우 이러한 도움말 결정 합니다. 
  
## <a name="add-the-sharepoint-farm"></a>SharePoint 팜 추가

적절 한 서브넷에 대 한 계층에는 SharePoint 팜에서의 가상 컴퓨터를 배치 합니다.
  
**SharePoint 가상 컴퓨터의 그림 4: 배치**

![SharePoint 팜 서브넷 내의 Azure Virtual Network에 추가된 데이터베이스 서버 및 SharePoint 서버 역할](images/AZarch_SPVMsinCloudSer.png)
  
이 다이어그램의 각 계층에서 SharePoint 팜 서버 역할을 추가 하 여 이전 다이어그램에서 만듭니다.
  
- SQL Server를 실행 하는 두 데이터베이스 가상 컴퓨터에서 데이터베이스 계층을 만듭니다.
    
- 각 다음 계층에 대 한 SharePoint Server 2013을 실행 하는 두 가상 컴퓨터: 프런트엔드 서버, 분산된 캐시 서버 및 백엔드 서버입니다.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>디자인 및 가용성 집합과 장애 도메인에 대 한 서버 역할을 미세 조정

장애 도메인은를 실행 하는 역할 인스턴스에서 하드웨어의 그룹입니다. Azure 인프라에 의해 동시에 같은 장애 도메인 내에서 가상 컴퓨터를 업데이트할 수 있습니다. 또는 동일한 랙을 공유 하기 때문에 동시에 실패할 수 있습니다. 동일한 장애 도메인에 가상 컴퓨터 두 대의 위험을 방지 하려면 다른 장애 도메인에서 각 가상 컴퓨터를 유지 하는 가용성 집합으로 가상 컴퓨터를 구성할 수 있습니다. 세 가상 컴퓨터 가용성 집합으로 구성 된 경우 동일한 장애 도메인에 있는 가상 컴퓨터의 2 개 이하의 Azure 보장 합니다.
  
SharePoint 팜에 대해 Azure 아키텍처를 디자인할 때 가용성 집합의 일부를 동일한 서버 역할을 구성 합니다. 이렇게 하면 가상 컴퓨터에 여러 장애 도메인 분산 되는 합니다.
  
**그림 5: SharePoint 팜 계층에 대 한 고가용성을 제공 하려면 사용 하 여 Azure 가용성 집합**

![SharePoint 2013 솔루션용 Azure 인프라의 가용성 집합 구성](images/AZenv_WinAzureAvailSetsHA.png)
  
이 다이어그램 Azure 인프라 내에서 가용성 집합의 구성이 호출합니다. 다음 역할의 각 별도 가용성 집합을 공유 합니다.
  
- Active Directory 및 DNS
    
- 데이터베이스
    
- 백엔드
    
- 캐시를 배포 합니다.
    
- 프런트 엔드
    
SharePoint 팜 해야할 것이 좋으며 Azure 플랫폼에서 조정 됩니다. 모든 구성 요소의 고가용성을 보장 하려면 확인 하는 서버 역할이 구성 되는 모두 동일 하 게 합니다.
  
다음은 특정 용량 및 성능 목표를 충족 하는 표준 인터넷 사이트 아키텍처를 표시 하는 예제입니다. 이 예제는 다음과 같은 아키텍처 모델에 자세히 볼: [SharePoint Server 2013 용 인터넷 사이트 검색 아키텍처](https://go.microsoft.com/fwlink/p/?LinkId=261519)입니다.
  
**그림 6: 3 계층 팜의 용량 및 성능 목표에 대 한 예제 계획**

![특정 용량 및 성능 목표를 충족하는 구성 요소 할당이 있는 표준 SharePoint 2013 인터넷 사이트 아키텍처](images/AZarch_CapPerfexmpArch.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- 3 계층 팜 표현 됩니다: 웹 서버, 응용 프로그램 서버 및 데이터베이스 서버입니다.
    
- 세 웹 서버는 여러 구성 요소와 동일 하 게 구성 됩니다.
    
- 두 데이터베이스 서버는 동일 하 게 구성 됩니다.
    
- 세 응용 프로그램 서버를 동일 하 게 구성 되지 않습니다. 이러한 서버 역할 Azure에서 설정 하는 가용성에 대 한 미세 조정에 필요 합니다.
    
응용 프로그램 서버 계층에 자세히 살펴보겠습니다.
  
**미세 조정 하기 전에 그림 7: 응용 프로그램 서버 계층**

![Microsoft Azure 가용성 집합에 맞게 조정하기 전 SharePoint Server 2013 응용 프로그램 서버 계층 예제](images/AZarch_AppServtierBefore.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- 세 서버 응용 프로그램 계층에 포함 됩니다.
    
- 첫번째 서버에는 4 개의 구성 요소가 포함 되어있습니다.
    
- 두번째 서버는 다음 세가지 구성 요소를 포함합니다.
    
- 세번째 서버 두 구성 요소를 포함합니다.
    
팜에 대 한 성능 및 용량 목표 하 여 구성 요소 수를 결정 합니다. 이 아키텍처 azure에 맞게 세 서버 모두 4 개의 구성 요소에 복제는 표시 됩니다. 이 성능 및 용량에 필요한 것 보다 세부적 구성 요소의 수를 늘립니다. 단점은이 디자인 때 이러한 세 가상 컴퓨터 가용성 집합에 할당 된 모든 구성 요소 4 개 Azure 플랫폼에서의 고가용성을 보장 하는 것입니다.
  
**그림 8: 응용 프로그램 서버 계층 미세 조정 후**

![Microsoft Azure 가용성 집합에 맞게 조정한 후 SharePoint Server 2013 응용 프로그램 서버 계층 예제](images/AZarch_AppServtierAfter.png)
  
이 다이어그램에서는 동일한 4 개의 구성 요소를 사용 하 여 동일 하 게 구성 하는 모든 세 응용 프로그램 서버를 보여줍니다.
  
SharePoint 팜에 있는 계층에 가용성 집합을 추가할는 구현 완료 됩니다.
  
**그림 9: 완료 된 SharePoint 팜에 있는 Azure 인프라 서비스**

![Virtual Network, 크로스-프레미스 연결, 서브넷, VM 및 가용성 집합이 있는 Azure 인프라 서비스의 SharePoint 2013 팜 예제](images/7256292f-bf11-485b-8917-41ba206153ee.png)
  
이 다이어그램에서는 각 계층의 서버에 대 한 장애 도메인을 제공 하려면 가용성 집합을 가진 Azure 인프라 서비스에서 구현 하는 SharePoint 팜을 보여줍니다.
  
**토론에 참가**

|**문의처**|**설명**|
|:-----|:-----|
|**클라우드 채택 콘텐츠 합니까 필요 합니까?** <br/> |여러 Microsoft 클라우드 플랫폼 및 서비스에 걸쳐 있는 클라우드 채택에 대 한 콘텐츠를 만듭니다. 보겠습니다 작업을 알 사용해 클라우드 채택 콘텐츠를 구상할 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)에 전자 메일을 발송 하 여 특정 콘텐츠를 요청 합니다.<br/> |
|**클라우드 채택 토론에 참가** <br/> |클라우드 기반 솔루션에 열정을 갖고 인 경우에는 클라우드 채택 자문 보드 (CAAB) Microsoft 콘텐츠 개발자, 업계 전문가는 전세계 어디에서 고객의 더 큰, 생생한 커뮤니티와 연결할에 참가 하는 것이 좋습니다. 참가, Microsoft 기술 커뮤니티의 [CAAB (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 의 구성원으로 자신을 추가 하 고[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내주시기 합니다. 누구나 [CAAB 블로그 (영문)](https://blogs.technet.com/b/solutions_advisory_board/)에서 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원에 게 새 클라우드 채택 리소스 및 솔루션에 설명 하는 개인 웨 초대장을 가져옵니다.<br/> |
|**여기에서 참조 하 여 아트 가져오기** <br/> |이 문서에서 참조 하는 이미지의 편집 가능한 복사본을 원하는 귀하에 게 보내야 기꺼이 표시 됩니다. URL 및 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)는 이미지의 제목을 포함 하 여 요청을 전자 메일로 보냅니다.<br/> |
   
## <a name="see-also"></a>참고 항목

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Microsoft Azure의 SharePoint Server 2013 재해 복구](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


