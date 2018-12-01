---
title: Azure IaaS용 하이브리드 클라우드 시나리오
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: '요약: 경우 서비스로 (IaaS) Microsoft의 인프라에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다.'
ms.openlocfilehash: bb6611f51cc346273438e879d957597fe3299c58
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123245"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Azure IaaS용 하이브리드 클라우드 시나리오

 **요약:** 서비스로 (IaaS) Microsoft의 인프라에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다.
  
온-프레미스 컴퓨팅을 확장 하 고 id 인프라에서 실행 되는 IT 작업 부하를 호스트 하 여 클라우드로 크로스-프레미스 Azure 가상 네트워크 (VNets). 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Azure IaaS 하이브리드 시나리오 아키텍처

그림 1 Azure의 Microsoft IaaS 기반 하이브리드 시나리오의 아키텍처를 보여줍니다.
  
**Azure의 그림 1: Microsoft IaaS 기반 하이브리드 시나리오**

![Azure의 Microsoft IaaS 기반 하이브리드 시나리오](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
아키텍처의 각 레이어에:
  
- 앱 및 시나리오
    
    IT 작업은 일반적으로 다중 계층, 항상 사용 가능한 응용 프로그램은 Azure 가상 컴퓨터 (Vm)의 구성 합니다.
    
- ID
    
    로컬 인증에 대 한 Azure VNets에서 실행 하는 서버 집합에 Windows Server AD 도메인 컨트롤러와 같은 identity 서버를 추가 합니다.
    
- 네트워크
    
    Azure IaaS에 개인 피어 링으로 인터넷을 통해 사이트 간 VPN 연결 또는 ExpressRoute 연결 중 하나를 사용 합니다.
    
- 온-프레미스
    
    Azure에서 실행 하는 identity 서버와 동기화 되는 identity 서버가 포함 됩니다. Azure에서 실행 중인 Vm에 액세스할 수 있는, 저장소 및 시스템 관리 인프라와 같은 리소스를 포함할 수도 있습니다.
    
## <a name="dirsync-server-for-office-365"></a>Office 365에 대 한 디렉터리 동기화 서버

그림 2와 같이 Azure VNet에서 디렉터리 동기화 (DirSync) 서버를 실행 하는 것은 컴퓨팅 및 id 인프라가 클라우드로 확장 (영문)의 예입니다.
  
**Azure IaaS에서 Office 365에 대 한 그림 2: 디렉터리 동기화 서버**

![Azure IaaS의 Office 365 디렉터리 동기화 서버](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
그림 2의 온-프레미스 네트워크 프록시 서버 및 해당에 지에서 라우터를 사용 하 여 Windows Server AD 인프라를 호스팅합니다. 라우터는 Azure 게이트웨이 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure VNet의 가장자리에 연결합니다. 디렉터리 동기화 서버는 VNet 내부 Azure AD 연결을 실행합니다.
  
Office 365에 대 한 디렉터리 동기화 서버는 Office 365 구독의 Azure AD 테 넌 트의 Windows Server AD 계정 목록을 동기화합니다.
  
디렉터리 동기화 서버에는 Azure AD 연결을 실행 하는 Windows 기반 서버가입니다. 더 빠른 프로 비전을 위한 또는 조직에서 온-프레미스 서버 수를 줄이는 Azure IaaS에서 가상 네트워크 (VNet)에서 디렉터리 동기화 서버를 배포 합니다.
  
디렉터리 동기화 서버는 Windows Server AD 변경 내용에 대 한 폴링 하 고 Office 365 구독을 동기화 합니다.
  
자세한 내용은 [Microsoft Azure에서 Office 365 디렉터리 동기화 배포](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)를 참조 하십시오.
  
## <a name="line-of-business-lob-application"></a>기간 업무 (LOB) 응용 프로그램의 줄

그림 3 Azure IaaS에서 실행 중인 응용 프로그램 서버 기반 LOB 구성을 보여줍니다.
  
**Azure IaaS에서 그림 3: LOB 응용 프로그램**

![Azure IaaS의 서버 기반 LOB 응용 프로그램](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
그림 3에서는 온-프레미스 네트워크 id 인프라 및 사용자를 호스트합니다. 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure IaaS 게이트웨이에 연결 됩니다. Azure IaaS LOB 응용 프로그램의 서버를 포함 하는 가상 네트워크를 호스팅합니다.
  
Azure 데이터 센터 (위치)의 Azure VNet의 서브넷에 상주 하는 Azure Vm에서 실행 되는 LOB 응용 프로그램을 만들 수 있습니다.
  
사용자 VNets에 고유한 개인 주소 공간을 할당 하 고 온-프레미스를 업데이트 해야 기본적으로 Azure를 사용 하도록 온-프레미스 인프라를 확장 하는, 때문에 라우팅 테이블에 각 VNet에 연결 가능성을 확인 합니다.
  
연결 된 후에 온-프레미스 서버와 마찬가지로 시스템 관리 소프트웨어를 사용 하거나 원격 데스크톱 연결 이러한 Vm 관리할 수 있습니다.
  
공개적으로 노출 포트를 구성 하 여 이러한 Vm 액세스할 수도 있습니다 인터넷에서 모바일 또는 원격 사용자가 있습니다.
  
개념 증명 구성을 [Simulated 크로스-프레미스 Azure에 가상 네트워크를](simulated-cross-premises-virtual-network-in-azure.md)참조 하십시오.
  
Azure Vm에서 호스팅되는 LOB 응용 프로그램의 특성은 다음과 같습니다.
  
- 여러 계층
    
    계층화 된 방식을 사용 하는 일반적인 LOB 응용 프로그램입니다. 두 서버 집합이 직원 또는 고객에 대 한 액세스에 대 한 id, 데이터베이스 처리, 응용 프로그램 및 논리 처리 및 프런트엔드 웹 서버를 제공합니다. 
    
- 고가용성
    
    각 계층에서 여러 서버를 사용 하 여 고가용성을 제공 하는 일반적인 LOB 응용 프로그램입니다. Azure IaaS Azure 가용성 집합에는 서버에 대 한 99.9% 가동 시간 SLA를 제공합니다. 
    
- 부하 분산
    
    계층에서 여러 서버 간에 네트워크 트래픽 부하를 배포 하려면 인터넷 또는 내부 Azure 부하 분산 장치를 사용할 수 있습니다. 또는 Azure marketplace에서 제공 하는 전용된 부하 분산 장치 기기를 사용할 수 있습니다.
    
- 보안
    
    인터넷에서 들어오는 원치 않는 트래픽을에서 서버를 보호 하려면 Azure 네트워크 보안 그룹을 사용할 수 있습니다. 허용 하거나 서브넷 또는 개별 가상 컴퓨터의 네트워크 인터페이스에 대 한 트래픽을 거부를 정의할 수 있습니다.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure의 SharePoint Server 2016 팜

다중 계층의 예로, Azure의 가용성이 LOB 응용 프로그램 그림 4와 같이 SharePoint Server 2016 팜은 합니다.
  
**그림 4: 고가용성 SharePoint Server 2016의에서 팜 Azure IaaS**

![Azure IaaS에 팜 된 고가용성 SharePoint Server 2016 ](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
그림 4는 온-프레미스 네트워크 id 인프라 및 사용자를 호스트합니다. 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure IaaS 게이트웨이에 연결 됩니다. Azure VNet 프런트엔드 서버, 응용 프로그램 서버, SQL Server 클러스터 및 도메인 컨트롤러에 대 한 별도 계층을 포함 하는 SharePoint Server 2016 팜의 서버를 포함 합니다.
  
이 구성은 다음과 같은 특성이 LOB 응용 프로그램의 Azure에서: 
  
- 계층
    
    팜 내에서 다양 한 역할을 실행 하는 서버는 계층 만들고 각 계층에는 자체 서브넷입니다.
    
- 고가용성
    
    동일한 가용성 집합에 있는 계층의 모든 서버를 배치 하 고 각 계층에 둘 이상의 서버를 사용 하 여 수행 합니다.
    
- 부하 분산
    
    내부 Azure 부하 분산 장치에는 들어오는 클라이언트 웹 트래픽을 (s q l 1, SQL2 및 MN1) SQL Server 클러스터의 수신기 IP 주소와 프런트엔드 서버 (WEB1 및 w e b 2)에 배포 합니다.
    
- 보안
    
    각 서브넷에 대 한 네트워크 보안 그룹을 통해 허용 된 인바운드 및 아웃 바운드 트래픽을 구성할 수 있습니다.
    
성공적인 채택에 대 한이 경로 따릅니다.
  
1. 평가 및 테스트
    
    [Microsoft Azure의 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) Azure의 SharePoint Server 2016 실행의 장점을 이해를 참조 하십시오.
    
    [Azure 개발/테스트 환경에서 인트라넷 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) 시뮬레이션 된 개발/테스트 환경을 구축 하기를 참조 하십시오.
    
2. 디자인
    
    Azure IaaS 네트워킹, 계산, 및 저장소 요소를 호스팅할 팜 및 설정의 집합을 결정 하는 프로세스를 통해의 8 단계 [Azure의 SharePoint Server 2016 팜 디자인 (영문)을](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) 참조 하십시오.
    
3. 배포
    
    5 단계에서 끝-구성 고가용성 팜의 각 단계를 수행 하려면 [SharePoint Server 2016 Azure에서 SQL Server AlwaysOn 가용성 그룹으로 배포](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) 참조 하십시오.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Azure의 Office 365에 대 한 페더레이션된 id

Azure의 다중 계층, 항상 사용 가능한 LOB 응용 프로그램의 다른 예에는 Office 365에 대 한 페더레이션된 id입니다.
  
**그림 5: Azure IaaS에서 Office 365에 대 한 고가용성 페더레이션된 id 인프라를**

![고가용성 Office 365 페더레이션 Azure에서 인증 인프라](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
그림 5는 온-프레미스 네트워크 id 인프라 및 사용자를 호스트합니다. 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure IaaS 게이트웨이에 연결 됩니다. Azure VNet 웹 프록시 서버, Active Directory Federation Services (AD FS) 서버 및 Windows Server Active Directory (AD) 도메인 컨트롤러를 포함 합니다.
  
이 구성은 다음과 같은 특성이 LOB 응용 프로그램의 Azure에서:
  
- **계층:** 웹 프록시 서버, AD FS 서버 및 Windows Server AD 도메인 컨트롤러에 대 한 계층 있습니다.
    
- **메일 로드:** 웹 프록시를 받는 클라이언트 인증 요청을 분산 하는 외부 Azure 부하 분산 및 내부 Azure 부하 분산 장치를 AD FS 서버에 인증 요청을 분산 합니다.
    
성공적인 채택에 대 한이 경로 따릅니다.
  
1. 평가 및 테스트
    
    Office 365와 연결 된 인증에 대 한 시뮬레이션 된 개발/테스트 환경을 구축 하 [여 Office 365 개발/테스트 환경에 대 한 페더레이션 id](federated-identity-for-your-office-365-dev-test-environment.md) 참조 하십시오.
    
2. 배포
    
    5 단계에서 끝-구성 고가용성 AD FS 인프라의 각 단계를 수행 하 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.
    
    
## <a name="see-also"></a>참고 항목

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)


