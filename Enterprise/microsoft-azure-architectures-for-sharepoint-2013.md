---
title: SharePoint 2013용 Microsoft Azure 아키텍처
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: '요약: SharePoint 2013 솔루션을 Microsoft Azure 가상 컴퓨터에서 호스트할 수 있습니다. 적합 한 솔루션 유형과 Microsoft Azure를 설정 하 여이를 호스트 하는 방법에 대해 알아봅니다.'
ms.openlocfilehash: 7bc274098f961ccf9aa6aef05f595dfc6e116bec
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032293"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>SharePoint 2013용 Microsoft Azure 아키텍처

 **요약:** SharePoint 2013 솔루션은 Microsoft Azure 가상 컴퓨터에서 호스팅할 수 있습니다. 적합 한 솔루션 유형과 Microsoft Azure를 설정 하 여이를 호스트 하는 방법에 대해 알아봅니다.
  
Azure는 SharePoint Server 2013 솔루션을 호스트 하는 데 적합 한 환경입니다. 대부분의 경우 Office 365을 권장 하지만 Azure에서 호스트 되는 SharePoint Server 팜이 특정 솔루션에 적합 한 옵션 일 수 있습니다. 이 문서에서는 Azure 플랫폼에 적합 한 방식으로 SharePoint 솔루션을 설계 하는 방법을 설명 합니다. 다음 두 가지 특정 솔루션은 예제로 사용 됩니다.
  
- [Microsoft Azure에서 SharePoint Server 2013 재해 복구](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [SharePoint Server 2013을 사용하는 Microsoft Azure의 인터넷 사이트](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Azure 인프라 서비스용으로 권장 되는 SharePoint 솔루션

Azure 인프라 서비스는 SharePoint 솔루션을 호스팅하기 위한 뛰어난 옵션입니다. 다른 솔루션 보다이 플랫폼에 적합 한 몇 가지 솔루션이 있습니다. 다음 표에는 권장 해결 방법이 나와 있습니다.
  
|**솔루션**|**Azure에이 솔루션을 권장 하는 이유**|
|:-----|:-----|
|개발 및 테스트 환경  <br/> |이러한 환경을 손쉽게 만들고 관리할 수 있습니다.  <br/> |
|Azure에 대 한 온-프레미스 SharePoint 팜의 재해 복구  <br/> |**호스팅된 보조 데이터 센터** 다른 지역의 보조 데이터 센터에 투자 하는 대신 Azure를 사용 합니다. <br/> **저렴 한 재해 복구 환경** 온-프레미스 재해 복구 환경 보다 리소스를 줄이고 유지 관리 하 고 비용을 지불 합니다. 리소스 수는 콜드 대기, 웜 대기 또는 핫 대기 중에서 선택한 재해 복구 환경에 따라 달라 집니다. <br/> **보다 탄력적 플랫폼** 재해가 발생 하는 경우 복구 SharePoint 팜을 쉽게 확장 하 여 부하 요구 사항을 충족할 수 있습니다. 리소스가 더 이상 필요 하지 않은 경우에 확장 됩니다. <br/> [Microsoft Azure의 SharePoint Server 2013 재해 복구를](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)참조 하세요.  <br/> |
|Office 365에서 사용할 수 없는 기능 및 배율을 사용 하는 인터넷 연결 사이트  <br/> |**노력 집중** 인프라를 구축 하는 것 보다는 훌륭한 사이트 구축에 집중 합니다. <br/> **Azure에서 회복 력을 활용** 합니다. 새 서버를 추가 하 여 요청을 위한 팜의 크기를 조정 하 고 필요한 리소스만 지불 합니다. 동적 컴퓨터 할당이 지원 되지 않습니다 (자동 크기 조정). <br/> **Azure Active Directory (AD) 사용** 고객 계정에 대 한 Azure AD를 활용 합니다. <br/> **Office 365에서 사용할 수 없는 SharePoint 기능 추가** 상세 보고 및 web analytics 추가 <br/> [SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트를](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)참조 하세요.  <br/> |
|Office 365 또는 온-프레미스 환경을 지원 하기 위한 앱 팜  <br/> |온-프레미스 및 클라우드 환경을 모두 지원 하기 위해 Azure에서 **앱을 구축, 테스트 및 호스트** 합니다. <br/> 온-프레미스 환경에 대 한 새 하드웨어를 구입 하는 대신 Azure에서 **이 역할을 호스트** 합니다. <br/> |
   
인트라넷 및 공동 작업 솔루션 및 작업에 대 한 자세한 내용은 다음 옵션을 고려 하십시오.
  
- Office 365이 비즈니스 요구 사항을 충족 하는지 또는 솔루션의 일부일 수 있는지 확인 합니다. Office 365에서는 항상 최신 상태로 유지 되는 다양 한 기능 집합을 제공 합니다.
    
- Office 365이 모든 비즈니스 요구 사항을 충족 하지 않는 경우 MCS (Microsoft 컨설팅 서비스)에서 온-프레미스 SharePoint 2013의 표준 구현을 고려 합니다. 표준 아키텍처는 사용자 지정 된 것 보다 더 빠르고 저렴 하며 쉬운 해결책이 될 수 있습니다. 
    
- 표준 구현이 비즈니스 요구 사항을 충족 하지 않는 경우에는 사용자 지정 된 온-프레미스 솔루션을 고려해 야 합니다.
    
- 비즈니스 요구 사항에 따라 클라우드 플랫폼을 사용 하는 것이 중요 한 경우 Azure 인프라 서비스에서 호스트 되는 표준 또는 사용자 지정 된 SharePoint 2013 구현도 고려해 야 합니다. SharePoint 솔루션은 기본이 아닌 Microsoft 공용 클라우드 플랫폼 보다 Azure에서 더 쉽게 지원할 수 있습니다.
    
## <a name="before-you-design-the-azure-environment"></a>Azure 환경을 디자인 하기 전에

이 문서에서는 예제 SharePoint 토폴로지를 사용 하지만 이러한 디자인 개념을 모든 SharePoint 팜 토폴로지와 함께 사용할 수 있습니다. Azure 환경을 디자인 하기 전에 다음 토폴로지, 아키텍처, 용량 및 성능 지침을 사용 하 여 SharePoint 팜을 디자인 합니다.
  
- [SharePoint 2013 IT 전문가를 위한 아키텍처 디자인](http://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [SharePoint Server 2013에서 성능 및 용량 관리 계획](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>Active Directory 도메인 유형 확인

각 SharePoint Server 팜은 Active Directory를 사용 하 여 팜 설치를 위한 관리 계정을 제공 합니다. 현재 Azure의 SharePoint 솔루션에는 두 가지 옵션이 있습니다. 다음 표에 설명 되어 있습니다.
  
|**옵션**|**설명**|
|:-----|:-----|
|전용 도메인  <br/> |SharePoint 팜을 지원 하기 위해 Azure에 전용 및 격리 된 Active Directory 도메인을 배포할 수 있습니다. 이 옵션은 공용 인터넷 사이트에 적합 합니다.  <br/> |
|크로스-프레미스 연결을 통해 온-프레미스 도메인 확장  <br/> |크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 하면 사용자는 온-프레미스를 호스트 하는 것 처럼 인트라넷을 통해 SharePoint 팜에 액세스 합니다. 온-프레미스 Active Directory 및 DNS 구현을 활용할 수 있습니다.  <br/> 온-프레미스 팜에서 장애 조치 (failover) 하기 위해 Azure에서 재해 복구 환경을 구축 하려면 크로스-프레미스 연결이 필요 합니다.  <br/> |
   
이 문서에서는 크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 하기 위한 디자인 개념에 대해 설명 합니다. 솔루션에서 전용 도메인을 사용 하는 경우 크로스-프레미스 연결이 필요 하지 않습니다.
  
## <a name="design-the-virtual-network"></a>가상 네트워크 디자인

먼저 Azure에 가상 컴퓨터를 배치할 서브넷이 포함 된 가상 네트워크가 필요 합니다. 가상 네트워크에는 서브넷에 할당 하는 개인 IP 주소 공간이 필요 합니다.
  
크로스-프레미스 연결을 통해 온-프레미스 네트워크를 Azure로 확장 하는 경우 (재해 복구 환경에 필요한 경우) 조직 네트워크에서 아직 사용 되지 않은 개인 주소 공간을 선택 해야 합니다. 온-프레미스 환경 및 기타 Azure 가상 네트워크 
  
**그림 1: Azure의 가상 네트워크를 사용 하는 온-프레미스 환경**

![SharePoint 솔루션용 Microsoft Azure virtual network 디자인 Azure 게이트웨이에 대 한 서브넷 1 개 가상 컴퓨터에 대 한 서브넷 1 개](media/OPrrasconWA-AZarch.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- Azure의 가상 네트워크는 온-프레미스 환경에 나란히 표시 됩니다. 두 환경은 교차-프레미스 연결에 의해 아직 연결 되지 않으며, 사이트 간 VPN 연결 또는 Express 경로일 수 있습니다.
    
- 이 시점에서 가상 네트워크에는 서브넷과 다른 아키텍처 요소가 포함 되지 않습니다. 한 서브넷은 Azure gateway를 호스팅하고 다른 서브넷은 SharePoint 팜의 계층을 호스트 하 고, Active Directory 및 DNS를 추가로 사용 합니다.
    
## <a name="add-cross-premises-connectivity"></a>크로스-프레미스 연결 추가

다음 배포 단계는 크로스-프레미스 연결 (솔루션에 해당 되는 경우)을 만드는 것입니다. 크로스-프레미스 연결의 경우 Azure 게이트웨이는 별도의 게이트웨이 서브넷에 있으며 주소 공간을 만들고 할당 해야 합니다. 
  
크로스-프레미스 연결을 계획할 때는 Azure 게이트웨이와 온-프레미스 게이트웨이 장치에 대 한 연결을 정의 하 고 만듭니다.
  
**그림 2: Azure 게이트웨이와 온-프레미스 게이트웨이 장치를 사용 하 여 온-프레미스 환경 및 Azure 간의 사이트 간 연결 제공**

![사이트 간 VPN 연결 또는 Express 경로일 수 있는 크로스-프레미스 연결을 통해 Azure virtual network에 연결 된 온-프레미스 환경](media/AZarch-VPNgtwyconnct.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- 이전 다이어그램에 추가 하는 경우 온-프레미스 환경은 크로스-프레미스 연결 (사이트 간 VPN 연결 또는 Express 가능)에 의해 Azure virtual network에 연결 됩니다.
    
- Azure 게이트웨이가 게이트웨이 서브넷에 있습니다.
    
- 온-프레미스 환경에는 라우터 또는 VPN 서버와 같은 게이트웨이 장치가 포함 됩니다.
    
크로스-프레미스 가상 네트워크를 계획 하 고 만드는 방법에 대 한 자세한 내용은 온 [-프레미스 네트워크를 Microsoft Azure virtual network에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조 하십시오.
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>AD DS (Active Directory 도메인 서비스) 및 DNS 추가

Azure의 재해 복구에서는 Windows Server ad가 온-프레미스와 Azure 가상 컴퓨터 모두에 배포 되는 하이브리드 시나리오에서 Windows Server AD와 DNS를 배포 합니다.
  
**그림 3: 하이브리드 Active Directory 도메인 구성**

![Azure virtual network와 SharePoint 팜 서브넷에 배포 된 가상 컴퓨터는 복제 도메인 컨트롤러 및 DNS 서버입니다.](media/AZarch-HyADdomainConfig.png)
  
이 다이어그램에서는 두 개의 가상 컴퓨터를 Windows Server AD 및 DNS 서브넷에 추가 하 여 이전 다이어그램을 작성 합니다. 이러한 가상 컴퓨터는 복제 도메인 컨트롤러 및 DNS 서버입니다. 사용자는 온-프레미스 Windows Server AD 환경의 확장입니다. 
  
다음 표에는 Azure의 이러한 가상 컴퓨터에 대 한 구성 권장 사항이 나와 있습니다. Azure 환경이 온-프레미스 환경과 통신 하지 않는 전용 도메인에도이 기능을 사용 하 여 환경을 디자인 하는 시작 점으로 사용할 수도 있습니다.
  
|**항목**|**구성**|
|:-----|:-----|
|Azure의 가상 컴퓨터 크기  <br/> |표준 계층의 A1 또는 A2 크기  <br/> |
|운영 체제  <br/> |Windows Server 2012 R2  <br/> |
|Active Directory 역할  <br/> |글로벌 카탈로그 서버로 지정 된 AD DS 도메인 컨트롤러 이 구성을 사용 하면 크로스-프레미스 연결을 통해 송신 트래픽을 줄일 수 있습니다.  <br/> 변경 비율이 높은 다중 도메인 환경 (일반적이 아님)에서 복제 트래픽을 줄이기 위해 온-프레미스에서 도메인 컨트롤러를 Azure의 글로벌 카탈로그 서버와 동기화 하지 않도록 구성 합니다.  <br/> |
|DNS 역할  <br/> |도메인 컨트롤러에 DNS 서버 서비스를 설치 하 고 구성 합니다.  <br/> |
|데이터 디스크  <br/> |Active Directory 데이터베이스, 로그 및 SYSVOL을 추가 Azure 데이터 디스크에 배치 합니다. 이를 운영 체제 디스크 또는 Azure에서 제공 하는 임시 디스크에 배치 하지 마십시오.  <br/> |
|IP 주소  <br/> |고정 IP 주소를 사용 하 고 도메인 컨트롤러를 구성한 후에는 가상 네트워크의 가상 컴퓨터에 이러한 주소를 할당 하도록 가상 네트워크를 구성 합니다.  <br/> |
   
> [!IMPORTANT]
> Azure에서 Active Directory를 배포 하기 전에 [Azure 가상 컴퓨터에 Windows Server Active directory를 배포 하기 위한 지침](https://go.microsoft.com/fwlink/p/?linkid=392681)을 읽어 보십시오. 다음은 솔루션에 다른 아키텍처 또는 다른 구성 설정이 필요한 지를 결정 하는 데 도움이 되는 정보입니다. 
  
## <a name="add-the-sharepoint-farm"></a>SharePoint 팜 추가

SharePoint 팜의 가상 컴퓨터를 해당 서브넷의 계층에 배치 합니다.
  
**그림 4: SharePoint 가상 컴퓨터 배치**

![SharePoint 팜 서브넷 내의 Azure virtual network에 추가 된 데이터베이스 서버 및 SharePoint 서버 역할](media/AZarch-SPVMsinCloudSer.png)
  
이 다이어그램은 해당 계층에 SharePoint 팜 서버 역할을 추가 하 여 이전 다이어그램을 작성 합니다.
  
- SQL Server를 실행 하는 두 개의 데이터베이스 가상 컴퓨터에서 데이터베이스 계층을 만듭니다.
    
- 프런트 엔드 서버, 분산 캐시 서버 및 백 엔드 서버 계층 각각에 대해 SharePoint Server 2013을 실행 하는 두 개의 가상 컴퓨터가 있습니다.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>가용성 집합 및 장애 도메인에 대 한 서버 역할 디자인 및 미세 조정

장애 도메인은 역할 인스턴스가 실행 되는 하드웨어 그룹입니다. 동일한 장애 도메인 내의 가상 컴퓨터는 Azure 인프라에서 동시에 업데이트할 수 있습니다. 동일한 랙을 공유 하기 때문에 동시에 실패할 수도 있습니다. 동일한 오류 도메인에 두 대의 가상 컴퓨터가 있을 위험을 방지 하기 위해 가상 컴퓨터를 가용성 집합으로 구성 하 여 각 가상 컴퓨터가 서로 다른 오류 도메인에 있도록 할 수 있습니다. 세 개의 가상 컴퓨터가 가용성 집합으로 구성 된 경우 Azure는 두 개 이상의 가상 컴퓨터가 동일한 오류 도메인에 있는 것을 보장 합니다.
  
SharePoint 팜에 대 한 Azure 아키텍처를 디자인할 때는 가용성 집합에 포함 되도록 동일한 서버 역할을 구성 합니다. 이렇게 하면 가상 컴퓨터가 여러 장애 도메인에 분산 됩니다.
  
**그림 5: Azure 가용성 집합을 사용 하 여 SharePoint 팜 계층에 대 한 고가용성 제공**

![SharePoint 2013 솔루션용 Azure 인프라의 가용성 집합 구성](media/AZenv-WinAzureAvailSetsHA.png)
  
이 다이어그램은 Azure 인프라 내에서 가용성 집합의 구성을 호출 합니다. 다음의 각 역할은 별도의 가용성 집합을 공유 합니다.
  
- Active Directory 및 DNS
    
- 데이터베이스
    
- 백 엔드
    
- 캐시 배포
    
- 프런트 엔드
    
SharePoint 팜을 Azure 플랫폼에서 미세 조정 해야 할 수 있습니다. 모든 구성 요소의 고가용성을 보장 하려면 서버 역할이 모두 동일 하 게 구성 되어 있는지 확인 합니다.
  
다음은 특정 용량 및 성능 목표를 충족 하는 표준 인터넷 사이트 아키텍처를 보여 주는 예입니다. 이 예제는 다음과 같은 아키텍처 모델, 즉 [SharePoint Server 2013 용 인터넷 사이트 검색 아키텍처](https://go.microsoft.com/fwlink/p/?LinkId=261519)에 제공 됩니다.
  
**그림 6:3 계층 팜의 용량 및 성능 목표에 대 한 계획 예제**

![표준 SharePoint 2013 특정 용량 및 성능 목표를 충족 하는 구성 요소 할당이 포함 된 인터넷 사이트 아키텍처](media/AZarch-CapPerfexmpArch.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- 3 계층 팜 (웹 서버, 응용 프로그램 서버 및 데이터베이스 서버)이 표시 됩니다.
    
- 세 웹 서버는 여러 구성 요소와 동일한 방식으로 구성 됩니다.
    
- 두 데이터베이스 서버는 동일 하 게 구성 됩니다.
    
- 세 응용 프로그램 서버는 동일 하 게 구성 되지 않습니다. 이러한 서버 역할을 사용 하려면 Azure의 가용성 집합에 대 한 미세 조정이 필요 합니다.
    
응용 프로그램 서버 계층을 좀 더 자세히 살펴보겠습니다.
  
**그림 7: 미세 조정 이전의 응용 프로그램 서버 계층**

![Microsoft Azure 가용성 집합에 맞게 조정 하기 전 SharePoint Server 2013 응용 프로그램 서버 계층 예제](media/AZarch-AppServtierBefore.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- 응용 프로그램 계층에는 세 개의 서버가 포함 됩니다.
    
- 첫 번째 서버에는 네 개의 구성 요소가 포함 되어 있습니다.
    
- 두 번째 서버에는 세 개의 구성 요소가 포함 됩니다.
    
- 세 번째 서버에는 두 개의 구성 요소가 있습니다.
    
팜의 성능 및 용량 목표에 따라 구성 요소의 수를 결정 합니다. Azure에 대해이 아키텍처를 조정 하기 위해 3 대의 모든 서버에서 네 개의 구성 요소를 복제 합니다. 이렇게 하면 성능 및 용량에 필요한 구성 요소의 수가 늘어납니다. 이러한 단점은 이러한 세 가지 가상 컴퓨터가 가용성 집합에 할당 될 때 Azure 플랫폼에 있는 네 가지 구성 요소의 고가용성을 보장 한다는 것입니다.
  
**그림 8: 미세 조정 후 응용 프로그램 서버 계층**

![Microsoft Azure 가용성 집합에 맞게 조정한 후 SharePoint Server 2013 응용 프로그램 서버 계층 예제](media/AZarch-AppServtierAfter.png)
  
이 다이어그램에서는 동일한 4 개의 구성 요소와 동일 하 게 구성 된 3 개의 응용 프로그램 서버를 모두 보여 줍니다.
  
SharePoint 팜의 계층에 가용성 집합을 추가 하면 구현이 완료 됩니다.
  
**그림 9: Azure 인프라 서비스의 완료 된 SharePoint 팜**

![가상 네트워크, 크로스-프레미스 연결, 서브넷, Vm 및 가용성 집합이 있는 Azure 인프라 서비스의 SharePoint 2013 팜 예](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
이 다이어그램에서는 각 계층의 서버에 대 한 장애 도메인을 제공 하기 위한 가용성 집합과 함께 Azure 인프라 서비스에서 구현 되는 SharePoint 팜을 보여 줍니다.
  
**토론 참여**

|**연락처**|**설명**|
|:-----|:-----|
|**어떤 클라우드 채택 콘텐츠가 필요한가요?** <br/> |여러 Microsoft 클라우드 플랫폼 및 서비스에 적용되는 클라우드 채택 콘텐츠를 만들고 있습니다. 클라우드 채택 콘텐츠에 대한 의견을 제공하거나 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)으로 이메일을 보내서 특정 콘텐츠를 요청하세요.<br/> |
|**클라우드 채택 토론에 가입** <br/> |클라우드 기반 솔루션에 관심이 있다면 CAAB(클라우드 채택 자문 위원회)에 가입하여 Microsoft 콘텐츠 개발자, 산업 전문가 및 전 세계 고객으로 구성된 더 크고 활발한 커뮤니티에 연결할 수 있습니다. 참가 하려면 자신을 Microsoft 기술 커뮤니티의 [Caab (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 에 추가 하 고[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내 주세요. 모든 사용자가 [Caab 블로그에서](https://blogs.technet.com/b/solutions_advisory_board/)커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원은 새 클라우드 채택 리소스와 솔루션에 대해 설명하는 비공개 웹 세미나에 초대됩니다.  <br/> |
|**여기에 표시된 아트 받기** <br/> |이 문서에 표시된 아트의 편집 가능한 복사본을 원하시면 보내드리겠습니다. 아트의 URL과 제목을 적어서 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)으로 요청 이메일을 보내주세요.  <br/> |
   
## <a name="see-also"></a>참고 항목

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[SharePoint Server 2013을 사용하는 Microsoft Azure의 인터넷 사이트](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Microsoft Azure에서 SharePoint Server 2013 재해 복구](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


