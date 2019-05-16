---
title: Microsoft Azure IaaS에 대한 네트워킹 디자인
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: '요약: Microsoft Azure IaaS에서 작업을 위한 최적화 된 네트워킹을 디자인 하는 방법을 알아봅니다.'
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068134"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>Microsoft Azure IaaS에 대한 네트워킹 디자인

 **요약:** Microsoft Azure IaaS에서 작업을 위해 최적화 된 네트워킹을 디자인 하는 방법을 이해 합니다.
  
네트워킹 최적화 Azure IaaS에서 호스트 되는 작업에 대해 Azure virtual network (Vnet), 주소 공간, 라우팅, DNS 및 부하 분산을 이해 해야 합니다.
  
## <a name="planning-steps-for-any-vnet"></a>VNet에 대 한 단계 계획

모든 유형의 VNet에 대해 다음 단계를 수행 합니다.
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>1 단계: 인트라넷에서 Microsoft 클라우드 서비스를 준비 합니다.

[Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 있는 **microsoft 클라우드 서비스용 네트워크 섹션을 준비 하는 단계** 를 진행 합니다.
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>2 단계: 인터넷 대역폭을 최적화 합니다.

[Microsoft saas에 대 한 네트워킹 디자인](designing-networking-for-microsoft-saas.md)에서 **microsoft saas 서비스용 네트워크 준비** 섹션의 단계 2-4을 사용 하 여 인터넷 대역폭을 최적화 합니다.
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>3 단계: VNet 유형 (클라우드 전용 또는 크로스-프레미스)을 확인 합니다.

클라우드 전용 VNet은 온-프레미스 네트워크에 연결 되지 않습니다. 예제는 다음과 같습니다.
  
**그림 1: 클라우드 전용 VNet**

![그림 1: Azure의 클라우드 전용 가상 네트워크](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
그림 1은 클라우드 전용 VNet에 있는 가상 컴퓨터 집합을 보여 줍니다.
  
크로스-프레미스 VNet에는 Azure 게이트웨이를 통한 온-프레미스 네트워크에 대 한 S2S (사이트 간) VPN 또는 Express 간 연결이 있습니다. 예제는 다음과 같습니다.
  
**그림 2: 크로스-프레미스 VNet**

![그림 2: Azure의 크로스-프레미스 가상 네트워크](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
그림 2에서는 온-프레미스 네트워크에 연결 된 크로스-프레미스 VNet의 가상 컴퓨터 집합을 보여 줍니다.
  
이 문서에 있는 [크로스-프레미스 VNet에 대 한 추가 계획 단계](designing-networking-for-microsoft-azure-iaas.md#cross_prem) 를 참조 하세요.
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>4 단계: VNet의 주소 공간을 확인 합니다.

표 1에는 다양 한 유형의 Vnet에 대 한 주소 공간이 나와 있습니다.
  
|**VNet 유형**|**가상 네트워크 주소 공간**|
|:-----|:-----|
|클라우드 전용  <br/> |임의의 개인 주소 공간  <br/> |
|상호 연결 된 클라우드 전용  <br/> |임의 전용 이지만 연결 된 다른 Vnet와 겹치지 않음  <br/> |
|크로스-프레미스  <br/> |비공개, 온-프레미스와 겹치지 않음  <br/> |
|상호 연결 된 크로스-프레미스  <br/> |비공개, 온-프레미스 및 기타 연결 된 Vnet와 겹치지 않음  <br/> |
   
 **표 1: Vnet의 유형 및 해당 하는 주소 공간**
  
DHCP를 통해 서브넷의 주소 공간에서 가상 컴퓨터에 주소 구성이 할당 됩니다.
  
- 주소/서브넷 마스크
    
- 기본 게이트웨이
    
- DNS 서버 IP 주소
    
고정 IP 주소를 예약할 수도 있습니다.
  
또한 가상 컴퓨터에는 개별적으로 또는 포함 하는 클라우드 서비스에서 공용 IP 주소를 할당할 수 있습니다 (클래식 배포 시스템에만 해당).
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>5 단계: VNet 내의 서브넷과 각에 할당 된 주소 공간을 확인 합니다.

VNet에는 게이트웨이 서브넷과 가상 컴퓨터 호스팅 서브넷의 두 가지 서브넷 유형이 있습니다.
  
**그림 3: Azure의 두 가지 서브넷 유형**

![그림 3: Azure의 두 가지 서브넷 유형](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
그림 3은 Azure 게이트웨이가 있는 게이트웨이 서브넷과 가상 컴퓨터를 포함 하는 가상 컴퓨터 호스팅 서브넷 집합을 포함 하는 VNet을 보여 줍니다.
  
Azure는 azure 게이트웨이 서브넷의 가상 컴퓨터 두 개를 호스트 하는 데 필요 합니다. 최소 29 비트 접두사 길이를 사용 하 여 주소 공간을 지정 합니다 (예: 192.168.15.248/29). 특히 Express를 사용할 계획인 경우 27 비트 또는 더 작은 접두사 길이를 사용 하는 것이 좋습니다.
  
Azure 게이트웨이 서브넷의 주소 공간을 확인 하는 가장 좋은 방법은 다음과 같습니다.
  
1. 게이트웨이 서브넷의 크기를 결정 합니다.
    
2. VNet의 주소 공간에 있는 변수 비트에서 게이트웨이 서브넷에 사용 되는 비트를 0으로 설정 하 고 나머지 비트를 1로 설정 합니다.
    
3. 접두사 길이가 게이트웨이 서브넷 크기로 설정 된 주소 공간으로 10 진수 및 express로 변환 합니다.
    
이 방법을 사용 하는 경우 게이트웨이 서브넷의 주소 공간은 항상 VNet 주소 공간의 가장 끝에 있습니다.
  
다음은 게이트웨이 서브넷의 주소 접두사를 정의 하는 예입니다. VNet의 주소 공간은 10.119.0.0/16입니다. 조직에서는 처음에 사이트 간 VPN 연결을 사용 하지만 결국에는이를 기반으로 합니다. 표 2는 네트워크 접두사 표기법 (CIDR이 라고도 함)에서 게이트웨이 서브넷 주소 접두사를 확인 한 단계 및 결과를 보여 줍니다.

게이트웨이 서브넷 주소 접두사를 결정 하는 단계와 예는 다음과 같습니다.

1. 게이트웨이 서브넷의 크기를 결정 합니다. 이 예에서는/28을 선택 했습니다.
2. VNet 주소 공간 (b)의 변수 부분에 있는 비트를 G (게이트웨이 서브넷 비트)에 대해 0으로, 그렇지 않으면 1 (V)로 설정 합니다. 이 예에서는 VNet에 대해 10.119.0.0/16 주소 공간을 사용 하 고 있습니다.
<br/>
<br/>10.119 bbbbbbbb bbbbbbbb
<br/>10.119 VVVVVVV VVVVGGGG
<br/>10.119 11111111 1111만
<br/><br/>
3. 2 단계에서 10 진수 및 express로 결과를 주소 공간으로 변환 합니다. 이 예에서는 10.119를 사용할 것입니다. 11111111 1111만은 10.119.255.240이 고 1 단계의 접두사 길이를 포함 하 여, 결과 게이트웨이 서브넷 주소 접두사는 10.119.255.240/28입니다.
  
자세한 내용은 [Azure 게이트웨이 서브넷의 주소 공간 계산기](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) 를 참조 하세요.
  
가상 컴퓨터 호스팅 서브넷은 응용 프로그램의 공통 역할 또는 계층, 즉 서브넷 격리와 같은 일반적인 온-프레미스 지침에 따라 수행할 수 있는 Azure 가상 컴퓨터를 배치 하는 위치입니다.
  
Azure에서는 각 서브넷에서 처음 3 개의 주소를 사용 합니다. 따라서 Azure 서브넷에서 가능한 주소 수는 2<sup>n</sup> -5 이며 여기에서 n은 호스트 비트의 수입니다. 표 3에서는 필요한 가상 컴퓨터의 범위, 필요한 호스트 수 및 해당 서브넷 크기를 보여 줍니다.
  
|**필요한 가상 컴퓨터**|**호스트 비트**|**서브넷 크기**|
|:-----|:-----|:-----|
|1-3  <br/> |3(sp3)  <br/> |/29  <br/> |
|4-11  <br/> |1-4  <br/> |/28  <br/> |
|12-27  <br/> |2-5  <br/> |/27  <br/> |
|28-59  <br/> |번  <br/> |/26  <br/> |
|60-123  <br/> |연중  <br/> |/25  <br/> |
   
 **표 3: 가상 컴퓨터 요구 사항 및 해당 서브넷 크기**
  
서브넷 또는 VNet에 있는 가상 컴퓨터의 최대 크기에 대 한 자세한 내용은 [네트워킹 제한을](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)참조 하세요.
  
자세한 내용은 [Azure Virtual Network 계획 및 디자인](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)을 참조 하세요.
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>6 단계: VNet의 Vm에 할당할 DNS 서버의 주소와 DNS 서버 구성을 확인 합니다.

Azure는 가상 컴퓨터에 DHCP를 통해 DNS 서버의 주소를 할당 합니다. DNS 서버는 다음이 될 수 있습니다.
  
- Azure에서 제공: 로컬 이름 등록 및 로컬 및 인터넷 이름 확인을 제공 합니다.
    
- 제공: 로컬 또는 인트라넷 이름 등록 및 인트라넷 또는 인터넷 이름 확인을 제공 합니다.
    
표 4에서는 각 VNet 유형에 대 한 DNS 서버의 다양 한 구성을 보여 줍니다.
    
|**VNet 유형**|**DNS 서버**|
|:-----|:-----|
|클라우드 전용  <br/> |Azure-로컬 및 인터넷 이름 확인에 대해 제공 됩니다.  <br/> 로컬 및 인터넷 이름 확인을 위한 Azure 가상 컴퓨터 (DNS 전달)  <br/> |
|크로스-프레미스  <br/> |로컬 및 인트라넷 이름 확인을 위해 온-프레미스  <br/> 로컬 및 인트라넷 이름 확인에 대 한 Azure 가상 컴퓨터 (DNS 복제 및 전달)  <br/> |
   
 **표 4: 서로 다른 두 가지 유형의 Vnet DNS 서버 옵션**
  
자세한 내용은 [vm 및 역할 인스턴스에 대 한 이름 확인](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)을 참조 하십시오.
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>7 단계: 부하 분산 구성 (인터넷 연결 또는 내부)을 확인 합니다.

경우에 따라 같은 역할을 가진 서버 집합에 들어오는 트래픽을 분산 하려고 합니다. Azure IaaS에는 인터넷 연결 및 내부 트래픽 부하에 대해이 작업을 수행 하기 위한 기본 제공 기능이 있습니다.
  
Azure 인터넷 연결 부하 분산은 원치 않는 들어오는 트래픽을 인터넷에서 부하 분산 된 집합의 구성원으로 임의로 분산 합니다.
  
**그림 4: Azure의 외부 부하 분산 장치**

![그림 4: Azure의 외부 부하 분산 장치](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
그림 4에서는 인바운드 NAT 규칙 또는 끝점에 들어오는 트래픽을 부하 분산 집합에 있는 가상 컴퓨터 집합에 분산 하는 Azure의 외부 부하 분산 장치를 보여 줍니다.
  
Azure 내부 부하 분산은 다른 Azure Vm 또는 인트라넷 컴퓨터에서 들어오는 원치 않는 트래픽을 부하 분산 된 집합의 구성원으로 임의로 배포 합니다. 
  
**그림 5: Azure의 내부 부하 분산 장치**

![그림 5: Azure의 내부 부하 분산 장치](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
그림 5에서는 인바운드 NAT 규칙 또는 끝점에 들어오는 트래픽을 부하 분산 집합에 있는 가상 컴퓨터 집합에 분산 하는 Azure의 내부 부하 분산 장치를 보여 줍니다.
  
자세한 내용은 [Azure 부하 분산 장치](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)를 참조 하세요.
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>8 단계: 가상 어플라이언스 및 사용자 정의 경로 사용을 확인 합니다.

VNet의 가상 기기로 트래픽을 전달 해야 하는 경우에는 하나 이상의 사용자 정의 경로를 서브넷에 추가 해야 할 수 있습니다.
  
**그림 6: Azure의 가상 어플라이언스 및 사용자 정의 경로**

![그림 6: Azure의 가상 어플라이언스 및 사용자 정의 경로](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
그림 6에서는 가상 어플라이언스를 가리키는 가상 컴퓨터 호스팅 서브넷에 할당 되는 크로스-프레미스 VNet 및 사용자 정의 경로를 보여 줍니다.
  
자세한 내용은 [사용자 정의 경로 및 IP 전달을](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)참조 하십시오.
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>9 단계: 인터넷의 컴퓨터가 가상 컴퓨터에 연결 하는 방법을 결정 합니다.

VNet의 가상 컴퓨터에 대 한 인터넷 액세스를 제공 하는 방법에는 여러 가지가 있으며, 프록시 서버나 기타에 지 장치를 통해 조직 네트워크에 대 한 액세스를 포함 합니다.
  
표 5에는 원치 않는 들어오는 트래픽을 필터링 하거나 검사 하는 방법이 나열 되어 있습니다.
  
|**방법**|**배포 모델**|
|:-----|:-----|
|1. 클라우드 서비스에 구성 된 끝점 및 Acl  <br/> |기존  <br/> |
|2. 네트워크 보안 그룹  <br/> |자원 관리자 및 클래식  <br/> |
|3. 인바운드 NAT 규칙을 사용 하는 인터넷 연결 부하 분산 장치  <br/> |자원 관리자  <br/> |
|4. Azure Marketplace의 네트워크 보안 어플라이언스 (표시 되지 않음)  <br/> |자원 관리자 및 클래식  <br/> |
   
 **표 5: 가상 컴퓨터 및 해당 Azure 배포 모델에 연결 하는 방법**
  
**그림 7: 인터넷을 통한 Azure 가상 컴퓨터에 연결**

![그림 7: 인터넷을 통한 Azure 가상 컴퓨터에 연결](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
그림 7은 끝점, 네트워크 보안 그룹을 사용 하는 서브넷의 가상 컴퓨터 및 외부 부하 분산 장치 및 인바운드 NAT 규칙을 사용 하 여 서브넷의 가상 컴퓨터를 사용 하 여 클라우드 서비스의 가상 컴퓨터에 연결 하는 인터넷 연결 컴퓨터를 보여 줍니다.
  
추가 보안은 다음에 의해 제공 됩니다.
  
- 원격 데스크톱 및 SSH 연결 (인증 및 암호화 됨)
    
- 원격 PowerShell 세션 (인증 및 암호화 됨)
    
- IPsec 전송 모드-종단 간 암호화에 사용할 수 있습니다.
    
- 외부 및 내부 공격을 방지 하는 Azure DDOS protection
    
자세한 내용은 [Microsoft Cloud Security For Enterprise 설계자](https://aka.ms/cloudarchsecurity) 및 [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/)를 참조 하세요.
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>10 단계: 여러 Vnet에 대해 VNet-VNet 연결 토폴로지를 확인 합니다.

조직의 사이트를 연결 하는 데 사용 되는 것과 비슷한 토폴로지를 사용 하 여 Vnet를 서로 연결할 수 있습니다.
  
데이지 체인 구성은 일련의 Vnet 연결 합니다.
  
**그림 8: Vnet에 대 한 데이지 체인 구성**

![그림 8: Azure 가상 네트워크에 대 한 데이지 체인 구성](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
그림 8은 데이지 체인 구성을 사용 하 여 시리즈에 연결 된 5 개의 Vnet를 보여줍니다.
  
스포크 및 허브 구성은 서로 연결 되어 있는 중앙 Vnet 집합에 여러 Vnet를 연결 합니다.
  
**그림 9: Vnet에 대 한 스포크 및 허브 구성**

![그림 9: Azure 가상 네트워크에 대 한 스포크 및 허브 구성](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
그림 9에서는 여섯 개의 Vnet, 두 Vnet는 서로 연결 되는 허브, 그리고 다른 두 spoke Vnet를 보여 줍니다.
  
전체 메시 구성은 모든 VNet을 서로 연결 합니다.
  
**그림 10: Vnet에 대 한 풀 메시 구성**

![그림 10: Azure 가상 네트워크에 대 한 메시 구성](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
그림 10은 총 6 개의 VNet-VNet 연결을 사용 하 여 서로 연결 된 네 가지 Vnet를 보여줍니다.
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>크로스-프레미스 VNet에 대 한 계획 단계
<a name="cross_prem"> </a>

크로스-프레미스 VNet에 대해 다음 단계를 수행 합니다.
  
> [!TIP]
> 시뮬레이션 된 크로스-프레미스 개발/테스트 환경을 만들려면 [Azure에서 시뮬레이트된 크로스-프레미스 가상 네트워크](simulated-cross-premises-virtual-network-in-azure.md)를 참조 하세요. 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>1 단계: VNet (S2S VPN 또는 Express)에 대 한 크로스-프레미스 연결을 확인 합니다.

표 6에는 다양 한 유형의 연결이 나와 있습니다.
  
|**연결 유형**|**용도**|
|:-----|:-----|
|S2S (사이트 간) VPN  <br/> |1-10 사이트 (다른 Vnet 포함)를 단일 VNet에 연결 합니다.  <br/> |
|ExpressRoute  <br/> |IXP (인터넷 Exchange 공급자) 또는 NSP (네트워크 서비스 공급자)를 통해 Azure에 대 한 안전한 사설 링크입니다.  <br/> |
|지점 간 (P2S) VPN  <br/> |단일 컴퓨터를 VNet에 연결 합니다.  <br/> |
|VNet 피어 링 또는 VNet-VNet (V2V) VPN  <br/> |VNet을 다른 VNet에 연결 합니다.  <br/> |
   
 **표 6: 크로스-프레미스 Vnet 연결 유형**
  
최대 연결 수에 대 한 자세한 내용은 [네트워킹 제한을](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)참조 하세요.
  
VPN 장치에 대 한 자세한 내용은 [사이트 간 가상 네트워크 연결에 대 한 vpn 장치](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)를 참조 하세요.
  
VNet 피어 링에 대 한 자세한 내용은 [vnet 피어 링](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)를 참조 하세요.
  
**그림 11: 크로스-프레미스 VNet에 연결 하는 네 가지 방법**

![그림 11: 크로스-프레미스 Azure virtual network에 연결 하는 세 가지 방법](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
그림 11은 컴퓨터의 P2S 연결, 온-프레미스 네트워크의 S2S VPN 연결, 온-프레미스 네트워크 로부터의 간 연결, 다른 VNet에서의 VNet-VNet 연결과 같은 네 가지 유형의 연결이 포함 된 VNet을 보여 줍니다. 
  
다음과 같은 방법으로 VNet의 Vm에 연결할 수 있습니다.
  
- 온-프레미스 네트워크 또는 인터넷에서 VNet Vm 관리
    
- 온-프레미스 네트워크에서의 IT 워크 로드 액세스
    
- 추가 Vnet를 통한 네트워크 확장
    
연결에 대 한 보안은 다음을 통해 제공 됩니다.
  
- P2S는 SSTP (Secure Socket Tunneling Protocol)를 사용 합니다. 
    
- S2S 및 VNet과 vnet 간 VPN 연결에서는 AES256과 함께 IPsec 터널 모드를 사용 합니다.
    
- Express는 사설 WAN 연결
    
자세한 내용은 [Microsoft Cloud Security For Enterprise 설계자](https://aka.ms/cloudarchsecurity) 및 [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/)를 참조 하세요.
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>2 단계: 온-프레미스 VPN 장치 또는 라우터를 확인 합니다.

온-프레미스 VPN 장치 또는 라우터는 다음과 같이 작동 합니다.
  
- IPsec 피어-Azure 게이트웨이에서 S2S VPN 연결을 종료 합니다.
    
- 개인 피어 링 Express 연결에 대 한 BPG 피어 및 종료 지점입니다.
    
**그림 12: 온-프레미스 VPN 라우터 또는 장치**

![그림 12: 온-프레미스 VPN 라우터 또는 장치](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
그림 12에서는 온-프레미스 VPN 라우터 또는 장치에 연결 된 크로스-프레미스 VNet을 보여 줍니다.
  
자세한 내용은 [ABOUT VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)를 참조 하십시오.
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>3 단계: 인트라넷에 경로를 추가 하 여 VNet의 주소 공간에 연결할 수 있도록 합니다.

온-프레미스에서 Vnet로의 라우팅은 다음으로 구성 됩니다.
  
1. VPN 장치를 가리키는 VNet 주소 공간에 대 한 경로입니다.
    
2. VPN 장치에서 S2S VPN 또는 Express 연결을 가리키는 VNet 주소 공간에 대 한 경로
    
**그림 13: VNet에 연결할 수 있도록 하는 데 필요한 온-프레미스 경로**

![그림 13: Azure VNet에 연결할 수 있도록 설정 하는 데 필요한 온-프레미스 경로](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
그림 13은 온-프레미스 라우터에서 필요한 라우팅 정보 및 VNet의 주소 공간을 나타내는 VPN 라우터 또는 장치를 보여 줍니다.
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>4 단계: Express에서 공급자와의 새 연결을 계획 합니다.

온-프레미스 네트워크와 Microsoft 클라우드 사이에는 다음과 같은 세 가지 방법으로 개인 피어 링을 통한 간 연결을 만들 수 있습니다.
  
- 클라우드 exchange에 배치
    
- 지점 간 이더넷 연결
    
- 임의 (IP VPN) 네트워크
    
**그림 14: Express를 사용 하 여 크로스-프레미스 VNet에 연결**

![그림 14: Express를 사용 하 여 크로스-프레미스 Azure virtual network에 연결](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
그림 14에서는 온-프레미스 라우터에서 Microsoft Azure로의 크로스-프레미스 VNet 및 간 연결을 보여 줍니다.
  
자세한 내용은 [Microsoft 클라우드 연결용 express](expressroute-for-microsoft-cloud-connectivity.md)를 참조 하세요.
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>5 단계: Azure 게이트웨이의 로컬 네트워크 주소 공간을 확인 합니다.

온-프레미스 또는 VNet에서 다른 Vnet에 대 한 라우팅에서 Azure는 게이트웨이에 할당 된 로컬 네트워크 주소 공간과 일치 하는 Azure 게이트웨이 간에 트래픽을 전달 합니다.
  
**그림 15: 크로스-프레미스 VNet에 대 한 로컬 네트워크 주소 공간**

![그림 15: 크로스-프레미스 Azure virtual network에 대 한 로컬 네트워크 주소 공간](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
그림 15에서는 온-프레미스 네트워크에서 연결 가능한 주소 공간을 나타내는 Azure 게이트웨이의 크로스-프레미스 VNet과 로컬 네트워크 주소 공간을 보여 줍니다. 
  
다음과 같은 방법으로 로컬 네트워크 주소 공간을 정의할 수 있습니다.
  
- 옵션 1: 현재 필요 하거나 사용 중인 주소 공간의 접두사 목록 (새 서브넷을 추가할 때 업데이트가 필요할 수 있음)
    
- 옵션 2: 전체 온-프레미스 주소 공간 (새 주소 공간을 추가 하는 경우에만 필요 함)
    
Azure 게이트웨이가 요약 된 경로를 허용 하지 않으므로 옵션 2에 대 한 로컬 네트워크 주소 공간을 정의 하 여 VNet 주소 공간을 포함 하지 않도록 해야 합니다.
  
**그림 16: VNet 주소 공간에 의해 생성 되는 주소 공간 구멍**

![그림 16: 가상 네트워크 주소 공간에 의해 생성 되는 주소 공간 구멍](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
그림 16은 루트 공간과 VNet 주소 공간을 사용 하 여 주소 공간을 나타냅니다.
  
다음은 VNet에서 만든 주소 공간 "구멍" 주변의 로컬 네트워크 주소 공간에 대 한 접두사를 정의 하는 예입니다.
  
- 조직에서는 온-프레미스 네트워크에서 개인 주소 공간 일부 (10.0.0.0/8, 172.16.0.0/12 및 192.168.0.0/16)를 사용 합니다. 옵션 2와 10.100.100.0/24를 VNet 주소 공간으로 선택 합니다.
    
표 7에는이 예의 로컬 네트워크 주소 공간을 정의 하는 단계 및 결과 접두사가 나와 있습니다.
  
|**단계**|**결과**|
|:-----|:-----|
|1. VNet 주소 공간에 대 한 루트 공간이 아닌 접두사를 나열 합니다.  <br/> |172.16.0.0/12 및 192.168.0.0/16  <br/> |
|2.8 진수 가변 접두사에 대 한 겹치지 않는 접두 번호를 VNet 주소 공간에 나열 합니다.  <br/> |10.0.0.0/16, 10.1.0.0/16 10.99.0.0/16, 10.101.0.0/16 10.254.0.0/16, 10.255.0.0/16 (255 접두사, 10.100.0.0/16 건너뜀)  <br/> |
|3. VNet 주소 공간의 마지막으로 사용한 옥텟에 겹치지 않는 접두사를 나열 합니다.  <br/> |10.100.0.0/24, 10.100.1.0/24 ... 10.100.99.0/24, 10.100.101.0/24 ... 10.100.254.0/24, 10.100.0.255.0/24 (255 접두사, 10.100.100.0/24 건너뛰기)  <br/> |
   
 **표 7: 예 로컬 주소 네트워크 공간**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>6 단계: Azure에 호스트 되는 DNS 서버를 사용 하 여 DNS 복제를 위한 온-프레미스 DNS 서버를 구성 합니다.

온-프레미스 컴퓨터가 Azure 기반 서버 이름을 확인 하 고 Azure 기반 서버가 온-프레미스 컴퓨터의 이름을 확인할 수 있도록 하려면 다음을 구성 합니다.
  
- 온-프레미스 DNS 서버에 전달 하는 데 사용 되는 VNet의 DNS 서버
    
- 온-프레미스와 VNet에 있는 DNS 서버 간의 적절 한 영역에 대 한 DNS 복제
    
**그림 17: 크로스-프레미스 VNet의 DNS 서버에 대 한 DNS 복제 및 전달**

![그림 17: 크로스-프레미스 Azure virtual network의 DNS 서버에 대 한 DNS 복제 및 전달](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
그림 17에서는 온-프레미스 네트워크의 DNS 서버와 VNet의 서브넷에 있는 크로스-프레미스 VNet을 보여 줍니다. 두 DNS 서버 간에 DNS 복제 및 전달이 구성 되어 있습니다.
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>7 단계: 강제 터널링 사용을 확인 합니다.

Azure 서브넷의 기본 시스템 경로는 인터넷을 가리킵니다. 가상 컴퓨터의 모든 트래픽이 크로스-프레미스 연결에서 이동 되도록 하려면 Azure 게이트웨이를 다음 홉 주소로 사용 하는 기본 경로를 사용 하 여 라우팅 테이블을 만듭니다. 그런 다음 경로 테이블을 서브넷과 연결 합니다. 이를 강제 터널링 이라고 합니다. 자세한 내용은 [강제 터널링 구성을](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)참조 하십시오.
  
**그림 18: 크로스-프레미스 VNet에 대 한 강제 터널링 및 사용자 정의 경로**

![그림 18: 크로스-프레미스 Azure virtual network에 대 한 강제 터널링 및 사용자 정의 경로](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
그림 18은 Azure 게이트웨이를 가리키는 서브넷에 대 한 사용자 정의 경로가 있는 크로스-프레미스 VNet을 보여 줍니다.
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure의 SharePoint Server 2016 팜
<a name="cross_prem"> </a>

Azure IaaS에서 호스트 되는 인트라넷 IT 작업의 예로는 가용성이 높은 다중 계층 SharePoint Server 2016 팜이 있습니다.
  
**그림 19: Azure IaaS에서 사용 가능한 고가용성 인트라넷 SharePoint Server 2016 팜**

![Azure IaaS의 고가용성 SharePoint Server 2016 팜](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
그림 19에서는 프런트 엔드 및 데이터 계층에 대 한 내부 부하 분산 장치를 사용 하는 크로스-프레미스 VNet에 배포 된 SharePoint Server 2016 팜의 9 개 서버를 보여 줍니다. 단계별 디자인 및 배포 지침을 비롯 한 자세한 내용은 [Microsoft Azure의 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)를 참조 하세요.
  
> [!TIP]
> 시뮬레이트된 크로스-프레미스 VNet에 단일 서버 SharePoint Server 2016 팜을 만들려면 [Azure 개발/테스트 환경의 인트라넷 SharePoint server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)를 참조 하세요. 
  
크로스-프레미스 Azure 가상 네트워크의 가상 컴퓨터에 배포 된 IT 워크 로드에 대 한 추가 예제를 보려면 [Azure IaaS 용 하이브리드 클라우드 시나리오](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)를 참조 하세요.
  
## <a name="see-also"></a>참고 항목

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)


