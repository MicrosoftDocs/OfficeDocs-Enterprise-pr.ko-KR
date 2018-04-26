---
title: 온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: '요약: 크로스-프레미스 Azure를 구성 하는 방법을 설명 하 여 사이트 간 VPN 연결 Office 서버 작업 부하에 대 한 가상 네트워크입니다.'
ms.openlocfilehash: 818e709c8177c6533bfa02da00170bf7fdb5a0ac
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결

 **요약:** Office Server 작업용 프레미스 간 Azure Virtual Network 구성 방법을 알아봅니다.
  
크로스-프레미스 Azure 가상 네트워크 Azure 인프라 서비스에 서브넷 및 호스팅되는 가상 컴퓨터를 포함 하 여 네트워크 확장 (영문)를 온-프레미스 네트워크에 연결 됩니다. 이 연결에는 그 반대의 Azure에 가상 컴퓨터에 직접 액세스를 온-프레미스 네트워크에 컴퓨터 수 있습니다. 

예는 Azure 가상 컴퓨터에서 실행 하는 디렉터리 동기화 서버 계정에 대 한 변경 내용에 대 한 온-프레미스 도메인 컨트롤러를 쿼리하고 Office 365 구독에 이러한 변경 내용을 동기화 해야 합니다. 이 문서는 가상 크로스-프레미스 Azure를 설정 하는 방법을 보여주는 Azure 가상 컴퓨터 호스트를 준비 하는 사이트 마다 가상 사설망 (VPN) 연결을 사용 하 여 네트워크입니다.

## <a name="overview"></a>개요

Azure의 가상 시스템은 온-프레미스 환경에서 격리할 필요가 없습니다. Azure Virtual Machine을 온-프레미스 네트워크 리소스에 연결하려면 프레미스 간 Azure Virtual Network를 구성해야 합니다. 다음 다이어그램은 Azure의 가상 컴퓨터가 있는 프레미스 간 Azure Virtual Network를 배포하는 데 필요한 구성 요소를 표시합니다.
  
![사이트 간 VPN 연결을 통해 Microsoft Azure에 연결된 온-프레미스 네트워크](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
다이어그램에는 사이트 마다 VPN 연결 하 여 연결 된 두 네트워크: 온-프레미스 네트워크 및 Azure 가상 네트워크입니다. 사이트 마다 VPN 연결이 시작 됩니다.

- 두 끝점 간에 되어 주소 지정이 가능한 공용 인터넷에 있는입니다.
- 온-프레미스 네트워크의 VPN 장치 및 Azure 가상 네트워크에는 Azure VPN 게이트웨이가 종료 됩니다.

Azure 가상 네트워크 가상 컴퓨터를 호스트합니다. Azure 가상 네트워크의 가상 컴퓨터에서 시작 되는 네트워크 트래픽은 다음 온-프레미스 네트워크의 VPN 장치에 사이트 간 VPN 연결을 통해 트래픽을 전달 하는 VPN 게이트웨이로 전달를 가져옵니다. 온-프레미스 네트워크의 라우팅 인프라에는 다음 대상 트래픽을 전달합니다.

>[!Note]
>또한 조직에서 Microsoft의 네트워크 사이 직접 연결 인 [ExpressRoute](https://azure.microsoft.com/services/expressroute/)사용할 수 있습니다. 트래픽 ExpressRoute 통해 공용 인터넷을 통해 이동 하지 않습니다. 이 문서는 ExpressRoute의 사용을 설명 하지 않습니다.
>
  
Azure Virtual Network와 온-프레미스 네트워크 간에 VPN 연결을 설정하려면 다음 단계를 수행합니다. 
  
1. **온-프레미스:** 온-프레미스 VPN 장치를 가리키는 Azure Virtual Network의 주소 공간에 대한 온-프레미스 네트워크 경로를 정의하고 만듭니다.
    
2. **Microsoft Azure:** 사이트 마다 VPN 연결 Azure 가상 네트워크를 만듭니다. 
    
3. **온-프레미스:** 온-프레미스 하드웨어 또는 소프트웨어 VPN 장치를 구성하여 IPsec(인터넷 프로토콜 보안)을 사용하는 VPN 연결을 종료합니다.
    
사이트 간 VPN 연결을 설정한 후 Azure Virtual Machine을 가상 네트워크의 서브넷에 추가합니다.
  
## <a name="plan-your-azure-virtual-network"></a>Azure Virtual Network 계획
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>필수 구성 요소
<a name="Prerequisites"></a>

- Azure에 구독 합니다. Azure 구독에 대 한 정보를 [어떻게를 구입 Azure 페이지](https://azure.microsoft.com/pricing/purchase-options/)으로 이동 합니다.
    
- 가상 네트워크 및 서브넷에 할당할 수 있는 개인 IPv4 주소 공간. 이 주소 공간에는 현재와 미래에 필요한 가상 컴퓨터 수를 수용할만한 충분한 공간이 있어야 합니다.
    
- 온-프레미스 네트워크에서 사용할 수 있는 VPN 장치. 이 장치로 IPsec의 요구 사항을 지원하는 사이트 간 VPN 연결을 종료할 수 있습니다. 자세한 내용은 [사이트 간 가상 네트워크 연결용 VPN 장치 정보](https://go.microsoft.com/fwlink/p/?LinkId=393093)를 참조하세요.
    
- 라우팅 인프라에 대한 변경 내용. Azure Virtual Network의 주소 공간으로 라우팅된 트래픽이 사이트 간 VPN 연결을 호스트하는 VPN 장치로 전달되도록 라우팅 인프라를 변경해야 합니다.
    
- 온-프레미스 네트워크와 Azure Virtual Network에 연결된 컴퓨터에 인터넷으로의 액세스를 제공하는 웹 프록시.
    
### <a name="solution-architecture-design-assumptions"></a>솔루션 아키텍처 디자인 가정

다음 목록에는 이 솔루션 아키텍처에 대한 디자인 선택이 나타납니다. 
  
- 이 솔루션은 사이트 간 VPN 연결을 사용하는 단일 Azure Virtual Network를 사용합니다. Azure Virtual Network는 여러 가상 컴퓨터를 포함할 수 있는 단일 서브넷을 호스트합니다. 
    
- Windows Server 2016 또는 Windows Server 2012에서 RRAS(라우팅 및 원격 액세스 서비스)를 사용하여 온-프레미스 네트워크와 Azure Virtual Network 간의 IPsec 사이트 간 VPN 연결을 설정할 수 있습니다. Cisco 또는 Juniper Networks VPN 장치와 같은 다른 옵션을 사용할 수도 있습니다.
    
- 온-프레미스 네트워크에는 Windows Server AD(Active Directory), DNS(Domain Name System) 및 프록시 서버와 같은 네트워크 서비스가 아직 있을 수 있습니다. 사용자의 요구 사항에 따라 Azure Virtual Network에서 이러한 네트워크 리소스를 배치하는 것이 좋을 수도 있습니다.
    
하나 이상의 서브넷이 있는 기존 Azure Virtual Network의 경우 사용자의 요구 사항에 따라 필요한 가상 컴퓨터를 호스트할 추가 서브넷을 위한 남은 주소가 있는지 확인합니다. 추가 서브넷을 위한 남은 주소 공간이 없으면 자체 사이트 간 VPN 연결이 있는 추가 가상 네트워크를 만듭니다.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Azure Virtual Network에 대한 라우팅 인프라 변경 계획

Azure Virtual Network의 주소 공간을 대상으로 하는 트래픽을 사이트 간 VPN 연결을 호스트하는 온 - 프레미스 VPN 장치로 전달하도록 온-프레미스 라우팅 인프라를 구성해야 합니다.
  
라우팅 인프라를 업데이트하는 정확한 방법은 라우팅 정보를 관리하는 방법에 따라 달라지며 그 방법은 다음과 같습니다.
  
- 수동 구성에 따른 라우팅 테이블 업데이트.
    
- RIP(Routing Information Protocol) 또는 OSPF(최단 경로 우선 프로토콜)와 같은 라우팅 프로토콜을 기준으로 라우팅 테이블 업데이트.
    
라우팅 전문가와 상담하여 Azure Virtual Network를 대상으로 하는 트래픽이 온-프레미스 VPN 장치로 전달되는지 확인하세요.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>온-프레미스 VPN 장치의 트래픽용 방화벽 규칙 계획

주변 네트워크와 인터넷 사이에 방화벽이 있는 주변 네트워크에 VPN 장치가 있는 경우 사이트 간 VPN 연결을 허용하도록 다음 규칙에 맞게 방화벽을 구성해야 할 수도 있습니다.
  
- VPN 장치로 보내는 트래픽(인터넷에서 수신):
    
  - VPN 장치 및 IP 프로토콜 50의 대상 IP 주소
    
  - VPN 장치 및 UDP 대상 포트 500의 대상 IP 주소
    
  - VPN 장치 및 UDP 대상 포트 4500의 대상 IP 주소
    
- VPN 장치에서 받는 트래픽(인터넷으로 발신)
    
  - VPN 장치 및 IP 프로토콜 50의 원본 IP 주소
    
  - VPN 장치 및 UDP 원본 포트 500의 원본 IP 주소
    
  - VPN 장치 및 UDP 원본 포트 4500의 원본 IP 주소
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Azure Virtual Network의 개인 IP 주소 공간 계획

Azure Virtual Network의 개인 IP 주소 공간은 가상 네트워크를 호스트하기 위해 Azure에서 사용하는 주소와 Azure Virtual Machine에 충분한 주소가 있는 서브넷을 하나 이상 수용할 수 있어야 합니다.
  
서브넷에 필요한 주소 개수를 확인하려면 지금 필요한 가상 컴퓨터의 수를 계산하고 이후 증가량을 추정한 후 다음 테이블을 사용해서 서브넷의 크기를 확인합니다.
  
|**필요한 가상 컴퓨터의 수**|**필요한 호스트 비트 수**|**서브넷 크기**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Azure Virtual Network 구성용 계획 워크시트
<a name="worksheet"> </a>

Azure 가상 네트워크를 만들어서 가상 컴퓨터를 호스트하기 전에 다음 테이블에서 필요한 설정을 확인해야 합니다.
  
가상 네트워크 설정에 대해서는 테이블 V를 채웁니다.
  
 **테이블 V: 프레미스 간 가상 네트워크 구성**
  
|**항목**|**Configuration 요소**|**설명**|**값**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |가상 네트워크 이름  <br/> |Azure Virtual Network(예: DirSyncNet)에 할당할 이름입니다.  <br/> |![](./images/Common_Images/TableLine.png) |
|2.  <br/> |가상 네트워크 위치  <br/> |가상 네트워크가 포함될 Azure 데이터 센터입니다(예: 미국 서부).  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|3.  <br/> |VPN 장치 IP 주소  <br/> |인터넷에서 VPN 장치 인터페이스의 공용 IPv4 주소입니다. IT 부서에서 이 주소를 확인합니다.  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|4.  <br/> |가상 네트워크 주소 공간  <br/> |단일 개인 주소 접두사로 정의된 가상 네트워크의 주소 공간입니다. IT 부서에서 이 주소 공간을 확인합니다. 주소 공간은 CIDR(Classless Interdomain Routing) 형식이어야 하며 네트워크 접두사 형식이라고도 합니다. 예를 들어 10.24.64.0/20입니다.  <br/> |![](./images/Common_Images/TableLine.png) <br/> |
|5.  <br/> |IPsec 공유 키  <br/> |사이트 간 VPN 연결의 양측을 인증하는 데 사용되는 32자의 무작위 영숫자 문자열입니다. IT 또는 보안 부서에서 이 키 값을 확인한 다음 안전한 위치에 저장합니다. 또한, [IPsec 미리 공유한 키의 무작위 문자열 만들기](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)를 참조하세요.<br/> |![](./images/Common_Images/TableLine.png) <br/> |
   
이 솔루션의 서브넷에 대해서는 테이블 S를 채웁니다.
  
- 첫 서브넷의 경우 Azure 게이트웨이 서브넷의 28비트 주소 공간(/28 접두사 길이)을 결정합니다. 이 주소 공간을 확인하는 방법의 정보는 [Azure Virtual Network용 게이트웨이 서브넷 주소 공간 계산](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/)을 참조하세요.
    
- 두 번째 서브넷의 경우 식별 이름, 가상 네트워크 주소 공간을 기준으로 하는 단일 IP 주소 공간 및 설명이 포함된 용도를 지정합니다.
    
IT 부서에서 가상 네트워크 주소 공간의 이러한 주소 공간을 확인합니다. 두 주소 공간 모두 CIDR 형식이어야 합니다.
  
 **테이블 S: 가상 네트워크의 서브넷**
  
|**항목**|**서브넷 이름**|**서브넷 주소 공간**|**용도**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |Azure 게이트웨이에서 사용하는 서브넷입니다.  <br/> |
|2.  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
가상 네트워크의 가상 컴퓨터에서 사용할 온-프레미스 DNS 서버에 대해서는 테이블 D에 채웁니다. 각 DNS 서버에 식별 이름과 단일 IP 주소를 부여합니다. 식별 이름은 DNS 서버의 컴퓨터 이름 또는 호스트 이름과 일치하지 않아도 됩니다. 두 개의 빈 항목이 나열되어 있지만 추가할 수 있습니다. IT 부서에서 이 목록을 확인합니다.
  
 **테이블 D: 온-프레미스 DNS 서버**
  
|**항목**|**DNS 서버 식별 이름**|**DNS 서버 IP 주소**|
|:-----|:-----|:-----|
|1.  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|2.  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
사이트 간 VPN 연결을 통해 Azure Virtual Network에서 조직 네트워크로 패킷을 라우팅하려면 로컬 네트워크로 가상 네트워크를 구성해야 합니다. 이 로컬 네트워크에는 가상 네트워크의 가상 컴퓨터에 도달해야 하는 온-프레미스 네트워크의 모든 위치에 대한 주소 공간 목록(CIDR 형식)이 포함되어 있습니다. 온-프레미스 네트워크 또는 하위 집합의 모든 위치일 수 있습니다. 로컬 네트워크를 정의하는 주소 공간 목록은 고유해야 하며 이 가상 네트워크 또는 다른 프레미스 간 가상 네트워크에 사용되는 주소 공간과 중복되지 않아야 합니다.
  
로컬 네트워크 주소 공간의 집합에 대해서는 테이블 L을 채웁니다. 세 개의 빈 항목이 나열되지만 일반적으로 더 많이 필요합니다. IT 부서에서 이 목록을 확인합니다.
  
 **테이블 L: 로컬 네트워크의 주소 접두사**
  
|**항목**|**로컬 네트워크 주소 공간**|
|:-----|:-----|
|1.  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|2.  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|3.  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>배포 로드맵
<a name="DeploymentRoadmap"> </a>

다음 3단계를 통해 프레미스 간 가상 네트워크를 만들고 Azure에 가상 컴퓨터를 추가합니다.
  
- 1단계: 온-프레미스 네트워크 준비
    
- 2단계: Azure에 프레미스 간 가상 네트워크를 만들기
    
- 3단계(선택 사항): 가상 컴퓨터 추가
    
### <a name="phase-1-prepare-your-on-premises-network"></a>1단계: 온-프레미스 네트워크 준비
<a name="Phase1"></a>

가상 네트워크의 주소 공간을 대상으로 하는 트래픽을 온-프레미스 네트워크의 가장자리에 있는 라우터로 지정하고 궁극적으로 이를 배달하는 경로로 온 - 프레미스 네트워크를 구성해야 합니다. 네트워크 관리자와 상의하여 온-프레미스 네트워크의 라우팅 인프라에 경로를 추가하는 방법을 확인합니다.
  
구성 결과는 다음과 같습니다.
  
![온-프레미스 네트워크에는 VPN 장치 쪽을 가리키는 Virtual Network의 주소 공간에 대한 경로가 있어야 합니다.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>2단계: Azure에 프레미스 간 가상 네트워크 만들기
<a name="Phase2"></a>

먼저 Azure PowerShell 프롬프트를 엽니다. Azure PowerShell을 설치하지 않은 경우 [Azure PowerShell cmdlet으로 시작](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)을 참조하세요.
  
> [!NOTE]
> 이러한 명령은 Azure PowerShell 1.0 이상에서 사용할 수 있습니다. 이 문서의 PowerShell 명령을 모두 포함하는 텍스트 파일은 [여기](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19)를 클릭합니다. 
  
그런 다음 이 명령을 사용하여 Azure 계정에 로그인합니다.
  
```
Login-AzureRMAccount
```

다음 명령을 사용하여 구독 이름을 가져옵니다.
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

이러한 명령을 사용하여 Azure 구독을 설정합니다. <and> 문자를 포함하여 따옴표 안에 있는 모든 것을 올바른 구독 이름으로 바꿉니다.
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

다음으로 가상 네트워크에 새 리소스 그룹을 만듭니다. 고유한 리소스 그룹 이름을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

이러한 명령을 사용하여 새 리소스 그룹을 만듭니다.
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

리소스 관리자 기반 가상 컴퓨터에는 리소스 관리자 기반 저장소 계정이 있어야 합니다. 소문자와 숫자만 포함하는 저장소 계정의 고유한 이름을 전역으로 선택해야 합니다. 이 명령을 사용하여 기존 저장소 계정을 나열할 수 있습니다.
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

이 명령을 사용하여 제안된 저장소 계정 이름이 고유한지 테스트할 수 있습니다.
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

새 저장소 계정을 만들려면 이러한 명령을 실행합니다.
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

다음으로 Azure Virtual Network를 만듭니다.
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

구성 결과는 다음과 같습니다.
  
![Virtual Network가 온-프레미스 네트워크에 아직 연결되지 않았습니다.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
다음으로 이러한 명령을 사용하여 사이트 간 VPN 연결의 게이트웨이를 만듭니다.
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

구성 결과는 다음과 같습니다.
  
![이제 Virtual Network에 게이트웨이가 있습니다.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
계속해서 Azure VPN 게이트웨이에 연결할 온-프레미스 VPN 장치를 구성합니다. 자세한 내용은 [사이트 간 Azure Virtual Network 연결용 VPN 장치 정보](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)를 참조하세요.
  
VPN 장치를 구성하려면 다음 항목이 필요합니다.
  
- 가상 네트워크의 Azure VPN 게이트웨이의 공용 IPv4 주소. **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** 명령을 사용하여 주소를 표시합니다.
    
- 사이트 간 VPN 연결용 IPsec 미리 공유한 키(테이블 V - 항목 5 - 값 열).
    
구성 결과는 다음과 같습니다.
  
![Virtual Network가 온-프레미스 네트워크에 이제 연결되었습니다.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>3단계(선택 사항): 가상 머신 추가

Azure에서 필요한 가상 컴퓨터를 만듭니다. 자세한 내용은 [Azure 포털과 Windows 가상 컴퓨터 만들기](https://go.microsoft.com/fwlink/p/?LinkId=393098)를 참조 하십시오.
  
다음 설정을 사용합니다.
  
- **기초** 창에서 사용자 가상 네트워크와 동일한 구독과 리소스 그룹을 선택합니다. 사용자 이름과 암호를 안전한 위치에 기록합니다. 나중에 가상 컴퓨터에 로그인하려면 이러한 정보가 필요합니다.
    
- **크기** 창에서 적절한 크기를 선택합니다.
    
- **설정** 창의 **저장소** 섹션에서 가상 네트워크로 설정된 **표준** 저장소 유형과 저장소 계정을 선택합니다. **네트워크** 섹션에서 가상 네트워크 이름과 가상 컴퓨터를 호스트하는 서브넷(GatewaySubnet 제외)을 선택합니다. 다른 설정은 기본값을 그대로 사용합니다.
    
내부 DNS를 확인하여 가상 컴퓨터가 올바르게 DNS를 사용하고 있는지 확인합니다. 주소(A) 레코드가 새 가상 컴퓨터에 추가되어야 합니다. 인터넷에 액세스하려면 Azure Virtual Machine이 온-프레미스 네트워크의 프록시 서버에 구성되어야 합니다. 네트워크 관리자에게 이 서버에서 수행할 수 있는 추가 구성 단계를 문의합니다.
  
구성 결과는 다음과 같습니다.
  
![이제 Virtual Network는 온-프레미스 네트워크에서 액세스할 수 있는 가상 머신을 호스트합니다.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>다음 단계
  
[Microsoft Azure에서 Office 365 DirSync(디렉터리 동기화)를 배포합니다.](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)

