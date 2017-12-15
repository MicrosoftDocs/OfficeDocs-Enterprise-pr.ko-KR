---
title: "Microsoft Azure에서 Office 365 디렉터리 동기화 (DirSync)를 배포 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: "요약: 온-프레미스 디렉터리 및 Office 365 구독 Azure AD 테 넌 트 사이 계정을 동기화 하는 Azure에 가상 컴퓨터에서 Azure AD 연결 (DirSync)를 배포 합니다."
ms.openlocfilehash: c6ee337c49092ac5d2b3d30a54fc33b3f3e2bb58
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure"></a>Microsoft Azure에서 Office 365 디렉터리 동기화 (DirSync)를 배포 합니다.

 **요약:** 온-프레미스 디렉터리 및 Office 365 구독 Azure AD 테 넌 트 사이 계정을 동기화 하는 Azure에 가상 컴퓨터에서 Azure AD 연결 (DirSync)를 배포 합니다.
  
Azure Active Directory (AD) 연결 (이전의 디렉터리 동기화 도구, 디렉터리 동기화 도구 또는 DirSync.exe 도구) 도메인에 가입 된 서버에 설치 하는 서버 기반 응용 프로그램은 온-프레미스 Windows 서버를 동기화 Office 365 구독 Azure Active Directory 테 넌 트에 active Directory 사용자입니다. 온-프레미스 서버의 Azure AD 연결을 설치할 수는 있지만 설치할 수 있습니다 또한 Azure에 가상 컴퓨터에 다음과 같은 이유로 합니다.
  
- 구축 및 클라우드 기반 서버를 속도 구성 하 여 서비스를 사용할 수 있도록 사용자에 게 빨리 수 있습니다.
    
- Azure 적은 노력으로 더 나은 사이트의 가용성을 제공 합니다.
    
- 조직에서 온-프레미스 서버 수를 줄일 수 있습니다.
    
> [!IMPORTANT]
> 이 솔루션을 사용 하려면 온-프레미스 네트워크 및 Azure 가상 네트워크 간의 연결을 해야 합니다. 자세한 내용은 [Microsoft Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조 하십시오. 
  
> [!IMPORTANT]
> 이 문서에서는 단일 포리스트에 단일 도메인의 동기화에 설명 합니다. Azure AD 연결 Office 365와 Active Directory 포리스트에 있는 모든 Windows Server AD 도메인을 동기화합니다. Office 365와 동기화 할 Active Directory 포리스트를 여러 경우 [Single Sign-on 시나리오를 사용 하는 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=393091)를 참조 하십시오. 
  
> [!NOTE]
> Office 365의 디렉터리 서비스에 대 한 Azure Active Directory (Azure AD)를 사용합니다. Office 365 구독은 Azure AD 테 넌 트를 포함합니다. 이 테 넌이 트 Azure의 다른 SaaS 응용 프로그램 및 응용 프로그램을 비롯 한 다른 클라우드 작업 부하와 조직의 id의 관리를 위한도 사용할 수 있습니다. 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a>Azure의 디렉터리 동기화를 Office 365 배포 개요
<a name="Overview"> </a>

다음 다이어그램에서는 anOffice 365 구독에는 온-프레미스 Windows Server AD 포리스트를 동기화 하는 Azure (디렉터리 동기화 서버)의 가상 컴퓨터에서 실행 중인 Azure AD 연결을 보여줍니다.
  
![트래픽 흐름을 사용하여 온-프레미스 계정을 Office 365 구독의 Azure AD 테넌트와 동기화하는 Azure의 가상 컴퓨터에 있는 Azure AD Connect 도구](images/CP_DirSyncOverview.png)
  
이 다이어그램에서는 사이트 마다 VPN 또는 ExpressRoute 연결 하 여 연결 된 두 네트워크 있습니다. 여기에서 Windows Server AD 도메인 컨트롤러 이동한 하는 가상 컴퓨터에 해당 하는 디렉터리 동기화 서버와 함께 Azure 가상 네트워크를 온-프레미스 네트워크가 [Azure AD 연결](https://www.microsoft.com/download/details.aspx?id=47594)을 실행 합니다. 디렉터리 동기화 서버에서 시작 되는 두가지 주요 트래픽 흐름 가지가 있습니다.
  
-  Azure AD 연결 계정 및 암호를 변경 내용에 대 한 온-프레미스 네트워크에서 도메인 컨트롤러를 쿼리합니다.
    
-  Azure AD 연결 계정 및 암호를 Office 365 구독 Azure AD 인스턴스는 변경 내용을 보냅니다. 온-프레미스 네트워크는 확장 된 부분에는 디렉터리 동기화 서버 이기 때문에 이러한 변경 내용은 온-프레미스 네트워크 프록시 서버를 통해 전송 됩니다.
    
> [!NOTE]
> 이 솔루션에서는 단일 Active Directory 포리스트에 단일 Active Directory 도메인의 동기화에 설명 합니다. Azure AD 연결 Office 365와 Active Directory 포리스트에 있는 모든 Active Directory 도메인을 동기화합니다. Office 365와 동기화 할 Active Directory 포리스트를 여러 경우 [Single Sign-on 시나리오를 사용 하는 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=393091)를 참조 하십시오. 
  
두 경우 모두 Azure 가상 컴퓨터에서 실행 중인 Azure AD 연결 하 여를 유발한 트래픽은 다음에 VPN 게이트웨이 장치에 사이트 마다 VPN 또는 ExpressRoute 연결을 통해 트래픽을 전달 하는 Azure에 가상 네트워크에 게이트웨이를 전달합니다 온-프레미스 네트워크입니다. 온-프레미스 네트워크의 라우팅 인프라에는 다음 도메인 컨트롤러 또는 프록시 서버와 같은 목적지로 트래픽을 전달합니다.
  
이 솔루션을 배포 하는 데는 두 주요 단계가 있습니다.
  
1. Azure 가상 네트워크를 만들고 온-프레미스 네트워크에 대 한 사이트 간 VPN 연결을 설정 합니다. 자세한 내용은 [Microsoft Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조 하십시오.
    
2. [Azure AD 연결](https://www.microsoft.com/download/details.aspx?id=47594) , Azure의 도메인에 가입 된 가상 컴퓨터에 설치 하 고 Office 365를 온-프레미스 Windows Server AD를 동기화 합니다. 이는 다음이 포함 됩니다.
    
    Azure 가상 컴퓨터를 사용 하 여 Azure AD 연결을 실행 하는를 만듭니다.
    
    설치 하 고 [Azure AD 연결](https://www.microsoft.com/download/details.aspx?id=47594)을 구성 합니다.
    
    Azure AD 연결을 구성 하려면 Azure AD 관리자 계정 및 Windows Server AD 엔터프라이즈 관리자 계정 자격 증명 (사용자 이름 및 암호) 필요 합니다. Azure AD 연결을 즉시 하 고 Office 365를 온-프레미스 Windows Server AD 포리스트를 동기화 하 고 지속적으로 실행 합니다.
    
프로덕션 환경에서이 솔루션을 배포 하기 전에 실험 또는 데모에 대 한 개념 증명으로이 구성을 설정 하려면 지침 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md) 에 사용 합니다.
  
> [!IMPORTANT]
> Azure AD 연결 구성에는 다음이 완료 되 면 저장 하지는 않습니다 Windows Server AD 엔터프라이즈 관리자 계정 자격 증명입니다. 
  
> [!NOTE]
> 이 솔루션에서는 Office 365를 단일 Windows Server AD 포리스트 동기화 (영문)에 대해 설명 합니다. 이 문서에서 설명 하는 토폴로지는이 솔루션을 구현 하는 방법은 하나 뿐를 나타냅니다. 조직의 토폴로지 고유한 네트워크 요구 사항 및 보안 고려 사항에 따라 다를 수 있습니다. 
  
## <a name="plan-for-hosting-a-dirsync-server-for-office-365-in-azure"></a>Azure의 Office 365에 대 한 디렉터리 동기화 서버를 호스트 하는 것에 대 한 계획
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>필수 구성 요소

시작 하기 전에이 솔루션에 대 한 다음과 같은 필수 구성 요소를 검토 합니다.
  
- [Azure 가상 네트워크를 계획](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)의 계획 관련된 콘텐츠를 검토 합니다.
    
- Azure 가상 네트워크를 구성 하기 위한 모든 [필수 구성 요소](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) 를 충족 하는지 확인 합니다.
    
- Active Directory 통합 기능을 포함 하는 Office 365 구독을 포함 합니다. Office 365 구독에 대 한 정보를 [Office 365 구독 페이지](https://go.microsoft.com/fwlink/p/?LinkId=394278)으로 이동 합니다.
    
- Office 365와 온-프레미스 Windows Server AD 포리스트에 동기화에 Azure AD 연결을 실행 하는 하나의 Azure 가상 컴퓨터를 프로 비전 합니다.
    
    Windows Server AD 엔터프라이즈 관리자 계정 및 Azure Active Directory 관리자 계정에 대 한 자격 증명 (이름 및 암호)이 있어야 합니다.
    
### <a name="solution-architecture-design-assumptions"></a>솔루션 아키텍처 디자인 가정

다음 목록에서는이 솔루션에 대 한 디자인 선택 사항에 설명 합니다.
  
- 이 솔루션 단일 Azure 가상 네트워크를 사용 하 여 사이트 간 VPN 연결을 사용 합니다. Azure 가상 네트워크 서버가 포함 된 단일 서브넷, Azure AD 연결을 실행 하는 디렉터리 동기화 서버를 호스트 합니다. 
    
- 온-프레미스 네트워크에서 도메인 컨트롤러와 DNS 서버 존재 합니다.
    
- Azure AD 연결 single sign-on 하는 대신 암호 동기화를 수행합니다. Active Directory Federation Services (AD FS) 인프라를 배포 필요가 없습니다. 암호 동기화 및 single sign-on 및 옵션에 대 한 자세한 내용은 [사용 하 여 디렉터리 통합 시나리오는 결정](https://go.microsoft.com/fwlink/p/?LinkId=393094)을 참조 합니다.
    
환경에서이 솔루션을 배포할 때 고려할 수 있는 추가 디자인 선택 사항이 있습니다. 이러한 기능은 다음과 같습니다.
  
- 기존 Azure 가상 네트워크에 있는 DNS 서버 기존, 온-프레미스 네트워크에 있는 DNS 서버 대신 이름 확인을 위해 사용 하 여 디렉터리 동기화 서버를 할지 여부를 확인 합니다.
    
- 기존 Azure 가상 네트워크의 도메인 컨트롤러가 경우 Active Directory 사이트를 구성 하는지 여부를 결정 하 고 서비스 하면 더 나은 옵션 될 수 있습니다. 디렉터리 동기화 서버 계정 및 암호 대신 온-프레미스 네트워크에서 도메인 컨트롤러의 변경 내용에 대 한 Azure 가상 네트워크의 도메인 컨트롤러를 쿼리할 수 있습니다.
    
## <a name="deployment-roadmap"></a>배포 로드맵
<a name="DeploymentRoadmap"> </a>

Azure AD 연결 Azure에 가상 컴퓨터에 배포 하는 작업은 세 단계로 구성 됩니다.
  
- 1 단계: 만들기 및 Azure 가상 네트워크를 구성 합니다.
    
- 2 단계: 만들기 및 Azure 가상 컴퓨터를 구성 합니다.
    
- 3 단계: 설치 하 고 Azure AD 연결 구성
    
배포 후에 위치 및 Office 365에서 새 사용자 계정에 대 한 라이선스를 할당 해야 합니다.
  
> [!TIP]
> 이 솔루션, Microsoft PowerPoint 및 Visio 형식, 다이어그램 및 Azure PowerShell을 생성 하는 Microsoft Excel 구성 통합 문서를 개발할 수 Azure PowerShell 블록의 모든 [디렉터리 동기화 서버 Azure 배포 키트에](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) 포함 사용자 설정에 대해 사용자 지정 명령 차단 됩니다.
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>1 단계: 만들기 및 Azure 가상 네트워크를 구성 합니다.

만들고 Azure 가상 네트워크를 구성 하려면 완료 [1 단계: 온-프레미스 네트워크 준비](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) 및 [2 단계: Azure에서 크로스-프레미스 가상 네트워크 만들기](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) [로드맵 배포에서에 온-프레미스 네트워크에 연결을 Microsoft Azure 가상 네트워크](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)합니다.
  
결과 구성입니다.
  
![Azure에서 호스트되는 Office 365의 DirSync 서버 1단계](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
이 그림에서는 사이트 마다 VPN 또는 ExpressRoute 연결을 통해 Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크를 보여줍니다.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>2 단계: 만들기 및 Azure 가상 컴퓨터를 구성 합니다.

[Azure 포털의 첫번째 Windows 가상 컴퓨터 만들기](https://go.microsoft.com/fwlink/p/?LinkId=393098)지침을 사용 하 여 Azure에 가상 컴퓨터를 만듭니다. 다음 설정이 사용 됩니다.
  
- **기본 (영문)** 창에서 가상 네트워크와 같은 구독, 위치 및 자원 그룹을 선택 합니다. 안전한 위치에 사용자 이름 및 암호를 기록 합니다. 가상 컴퓨터에 연결 하는 나중에이 주소가 필요 합니다.
    
- **크기를 선택** 창에서 **A2 표준** 크기를 선택 합니다.
    
- **설정** 창에서 **저장소** 섹션에서 **표준** 저장소 유형을 선택 합니다. **네트워크** 섹션에서 디렉터리 동기화 서버 (하지 GatewaySubnet)를 호스트 하는 것에 대 한 가상 네트워크 및 서브넷의 이름을 선택 합니다. 다른 모든 설정을 기본값으로 그대로 둡니다.
    
디렉터리 동기화 서버를 사용 하는지 확인 DNS 올바르게 내부 DNS를 확인 하 여 해당 IP 주소를 가진 가상 컴퓨터에 대 한 주소 (A) 레코드를이 추가 되었는지 있는지 확인 합니다. 
  
원격 데스크톱 연결을 사용 하 여 디렉터리 동기화 서버에 연결할 [에 가상 컴퓨터 및 로그인에 연결](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) 의 지침을 사용 합니다. 로그인 한 후 가상 컴퓨터를 온-프레미스 Windows Server AD 도메인에 가입 합니다.
  
인터넷 리소스에 대 한 액세스 권한을 얻으려고 Azure AD 연결에 대 한 온-프레미스 네트워크 프록시 서버를 사용 하 여 디렉터리 동기화 서버를 구성 해야 합니다. 수행 하려면 추가 구성 단계에 대 한 네트워크 관리자에 게 문의 해야 합니다.
  
결과 구성입니다.
  
![Azure에서 호스트되는 Office 365의 DirSync 서버 2단계](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
이 그림 디렉터리 동기화 서버 가상 컴퓨터에서 크로스-프레미스 Azure 가상 네트워크입니다.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>3 단계: 설치 하 고 Azure AD 연결 구성

다음 절차를 완료 합니다.
  
1. 로컬 관리자 권한이 있는 Windows Server AD 도메인 계정을 사용 하 여 원격 데스크톱 연결을 사용 하 여 디렉터리 동기화 서버에 연결 합니다. [가상 컴퓨터 및 로그인 시에 연결](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)을 참조 합니다.
    
2. 디렉터리 동기화 서버에서 [Office 365에서 디렉터리 동기화 설정](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) 문서 열고 암호 동기화를 사용 하 여 디렉터리 동기화에 대 한 지침을 따릅니다.
    
> [!CAUTION]
> 로컬 사용자 조직 구성 단위 (OU) **AAD_xxxxxxxxxxxx** 계정을 만듭니다. 이동 하지 않거나이 계정을 제거 또는 동기화에 실패 합니다.
  
결과 구성입니다.
  
![Azure에서 호스트되는 Office 365의 DirSync 서버 3단계](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
이 그림 Azure AD 연결 사용 하 여 디렉터리 동기화 서버에서 크로스-프레미스 Azure 가상 네트워크입니다.
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a>Office 365에서 사용자에 게 위치 및 라이선스 할당

온-프레미스 Windows Server AD에서 하지만 위치 및 라이선스를 사용 하 여 구성 해야 해당 서비스 계정을 사용 하 고 Office 365에 로그인 하는 사용자에서를 Office 365 구독의 계정을 추가 하는 azure AD 연결입니다. 다음이 단계를 사용 하 여 위치를 추가 하 고 적절 한 사용자 계정에 대 한 라이선스를 활성화 하려면:
  
1. [Office 365 포털 페이지](https://portal.office.com)로그인 한 다음 **관리**를 클릭 합니다.
    
2. 왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.
    
3. 사용자 계정 목록에서 활성화할 사용자 옆에 있는 확인란을 선택 합니다.
    
4. 사용자에 대 한 페이지에서 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.
    
5. **제품 라이센스** 페이지 **위치**대 한 사용자의 위치를 선택한 다음 사용자에 대 한 적절 한 라이센스를 사용 합니다.
    
6. 완료 되 면 **저장**을 클릭 한 다음 **닫기** 를 두 번 클릭 합니다.
    
7. 추가 사용자를 위한 3 단계로 이동 합니다.
    
## <a name="see-also"></a>See Also

<a name="DeploymentRoadmap"> </a>

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[다운로드 Azure AD 연결](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Office 365에서 디렉터리 동기화 설정](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[디렉터리 동기화 서버에서 Azure 배포 키트 (영문)](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



