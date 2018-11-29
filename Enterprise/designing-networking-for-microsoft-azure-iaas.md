---
title: Microsoft Azure IaaS에 대한 네트워킹 디자인
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: '요약: Microsoft Azure IaaS에는 작업에 대해 최적화 된 네트워킹을 디자인 하는 방법을 이해 합니다.'
ms.openlocfilehash: d13c1d4b985c633b8336dc33253e1350a54b5a39
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872339"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>Microsoft Azure IaaS에 대한 네트워킹 디자인

 **요약:** Microsoft Azure IaaS에는 작업에 대해 최적화 된 네트워킹을 디자인 하는 방법을 이해 합니다.
  
Azure IaaS에서 호스팅되는 IT 작업 부하에 대 한 네트워킹 최적화 Azure 가상 네트워크 (VNets) 주소 공간, 라우팅, DNS 및 부하 분산에 대 한 이해를 해야 합니다.
  
## <a name="planning-steps-for-any-vnet"></a>모든 VNet에 대 한 계획 단계

모든 유형의 VNet에 대 한 다음이 단계를 수행 합니다.
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>1 단계: Microsoft 클라우드 서비스에 대 한 인트라넷을 준비 합니다.

[Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>2 단계: 인터넷 대역폭을 최적화 합니다.

[Microsoft SaaS에 대 한 네트워킹 디자인 (영문)](designing-networking-for-microsoft-saas.md)에서 **Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계** 섹션의 2-4 단계를 사용 하 여 인터넷 대역폭을 최적화 합니다.
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>3 단계: VNet의 형식을 확인 (클라우드 전용 또는 크로스-프레미스).

클라우드 전용 VNet는 온-프레미스 네트워크에 연결 합니다. 다음은 한 예입니다.
  
**그림 1:는 클라우드 전용 VNet**

![그림 1: Azure에 있는 클라우드 전용 Virtual Network](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
그림 1 클라우드 전용 VNet에서 가상 컴퓨터의 집합을 보여줍니다.
  
A 크로스-프레미스 VNet가을--사이트 마다 S2S ()는 Azure 게이트웨이 통해 온-프레미스 네트워크로 VPN 또는 ExpressRoute 연결 합니다. 다음은 한 예입니다.
  
**그림 2: 크로스-프레미스 VNet**

![그림 2: Azure의 크로스-프레미스 Virtual Network](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
그림 2는 온-프레미스 네트워크에 연결 되는 크로스-프레미스 VNet에서 가상 컴퓨터의 집합을 보여줍니다.
  
참조를 추가로이 문서에서 [크로스-프레미스 VNet에 대 한 계획 수립 단계](designing-networking-for-microsoft-azure-iaas.md#cross_prem) 섹션입니다.
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>4 단계:는 VNet의 주소 공간을 결정 합니다.

표 1은 다양 한 유형의 VNets에 대 한 주소 공간을 보여줍니다.
  
|**VNet의 유형**|**가상 네트워크 주소 공간**|
|:-----|:-----|
|클라우드 전용  <br/> |임의의 개인 주소 공간  <br/> |
|클라우드 전용 상호 연결  <br/> |임의의 개인 하지만 다른 겹치는 하지 VNets 연결  <br/> |
|크로스-프레미스  <br/> |개인, 하지만 하지 온-프레미스와 겹침  <br/> |
|상호 연결 된 크로스-프레미스  <br/> |개인, 하지만에 온-프레미스 및 기타 겹치는 하지 VNets 연결  <br/> |
   
 **표 1: 유형의 VNets 및 해당 하는 주소 공간**
  
가상 컴퓨터는 서브넷의 주소 공간에서 주소 구성은 DHCP가 할당 됩니다.
  
- 주소/서브넷 마스크
    
- 기본 게이트웨이
    
- DNS 서버 IP 주소
    
고정 IP 주소를 예약할 수 있습니다.
  
가상 컴퓨터도 할당할 수 공용 IP 주소를 개별적으로 또는 (클래식 배포 컴퓨터에만 해당)에 포함 된 클라우드 서비스에서.
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>5 단계:은 VNet 및 각 할당 된 주소 공간 내 서브넷을 결정 합니다.

서브넷에는 VNet, 게이트웨이 서브넷 및 가상 컴퓨터 호스팅 서브넷의는 다음과 같은 두가지 유형이 있습니다.
  
**그림 3: Azure에 있는 서브넷 두 종류**

![그림 3: Azure에 있는 서브넷 두 종류](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
그림 3에는 Azure 게이트웨이 및 가상 컴퓨터를 포함 하는 가상 컴퓨터 호스팅 서브넷 집합이 있는 게이트웨이 서브넷을 포함 하는 VNet 나와 있습니다.
  
Azure 게이트웨이 서브넷은 Azure 게이트웨이 두 가상 컴퓨터 호스트를 위해 Azure가 필요 합니다. 29 비트 접두사 길이 사용 하 여 주소 공간 지정 (예: 192.168.15.248/29). ExpressRoute를 사용 하 여 계획 하는 경우에 특히 28 비트 또는 더 작은 접두사 길이 것이 좋습니다.
  
Azure 게이트웨이 서브넷의 주소 공간을 결정 하기 위한 가장 좋은 방법은입니다.
  
1. 게이트웨이 서브넷의 크기를 결정 합니다.
    
2. VNet의 주소 공간에서 가변 비트를 0으로 게이트웨이 서브넷에 사용 되는 비트를 설정 하 고 나머지 비트를 1로 설정 합니다.
    
3. 8 진수를 변환 하 고 게이트웨이 서브넷의 크기를 설정 하는 접두사 길이와 주소 공간으로 표현 합니다.
    
이 메서드와 함께 게이트웨이 서브넷에 대 한 주소 공간 끝인지 항상 먼 VNet 주소 공간입니다.
  
다음은 게이트웨이 서브넷에 대 한 주소 접두사를 정의 하는 예제:은 VNet의 주소 공간은 10.119.0.0/16 합니다. 조직 처음 사이트 마다 VPN 연결을 사용할 수는 있지만 ExpressRoute 결국. 표 2 단계 및 네트워크 접두사 표기법 (CIDR) 게이트웨이 서브넷 주소 접두사를 결정 하는 결과 보여줍니다.

다음은 단계 및 게이트웨이 서브넷 주소 접두사를 결정 하는 예제입니다.

1. 게이트웨이 서브넷의 크기를 결정 합니다. 이 예제에 대 한 /28을 선택 했습니다.
2. 비트 VNet 주소 공간 (b)의 변수 부분에 0으로 설정 게이트웨이에 대 한 서브넷 비트 (G), 그렇지 않은 경우 1 (V) 합니다. 이 예제에 대 한는 VNet에 대 한 10.119.0.0/16 주소 공간을 사용 하는 것입니다.<br/>
<br/>10.119. bbbbbbbb 합니다. bbbbbbbb<br/>10.119입니다. VVVVVVVV 합니다. VVVVGGGG<br/>10.119입니다. 11111111 합니다. 11110000<br/><br/>
3. 10 진수 및 주소 공간으로 express 2 단계에서 결과 변환 합니다. 예제에 10.119 합니다. 11111111 합니다. 11110000 10.119.255.240, 이며 (이 예제에서는 28) 하 여 1 단계에서 접두사 길이, 결과 게이트웨이 서브넷 주소 접두사가 10.119.255.240/28 합니다.
  
자세한 내용은 [Azure 게이트웨이 서브넷에 대 한 주소 공간 계산기](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) 를 참조 하십시오.
  
서브넷 가상 컴퓨터를 호스팅하는 일반적인 역할 또는 응용 프로그램의 또는 서브넷 격리에 대 한 계층 등의 일반적인 온-프레미스 지침에 따라 수행할 수 있는 Azure 가상 컴퓨터를 배치 하는 위치입니다.
  
Azure의 처음 3 주소를 사용 하 여 각 서브넷에 있습니다. 따라서 Azure 서브넷에서 사용할 수 있는 주소 수가 2<sup>n</sup> -5, 여기서 n은 호스트 비트 수입니다. 표 3에서는 필요에 따라 비트를 호스트 하는 가상 컴퓨터를 필요한 수의 범위 및 해당 서브넷 크기입니다.
  
|**필요한 가상 컴퓨터**|**호스트 비트**|**서브넷 크기**|
|:-----|:-----|:-----|
|1-3  <br/> |3   <br/> |/29  <br/> |
|4-11  <br/> |4   <br/> |/28  <br/> |
|12-27  <br/> |5   <br/> |/27  <br/> |
|28-59  <br/> |6   <br/> |/26  <br/> |
|60-123  <br/> |7   <br/> |/25  <br/> |
   
 **표 3: 가상 컴퓨터 요구 사항 및 서브넷 크기에 따라**
  
서브넷 또는 VNet에 가상 컴퓨터의 최대 크기에 대 한 자세한 내용은 [네트워킹 제한](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)을 참조 하십시오.
  
자세한 내용은 [계획 및 디자인 Azure 가상 네트워크를](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)참조 하십시오.
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>6 단계: DNS 서버 구성 및 vm를 포함 하는 VNet에 게 할당 하려면 DNS 서버 주소를 확인 합니다.

Azure 가상 컴퓨터의 DHCP에 의해 DNS 서버 주소를 할당합니다. DNS 서버 수 있습니다.
  
- Azure에서 제공: 로컬 이름 등록 하 고 로컬 및 인터넷 이름 확인을 제공 합니다.
    
- 사용자에 의해 제공: 로컬 또는 인트라넷 이름 등록 하 고 인트라넷 또는 인터넷 이름 확인을 제공 합니다.
    
표 4에서는 각 유형의 VNet에 대 한 DNS 서버의 다양 한 구성을 보여줍니다.
    
|**VNet의 유형**|**DNS 서버**|
|:-----|:-----|
|클라우드 전용  <br/> |로컬 복사본과 인터넷 이름 확인에 대 한 azure 제공  <br/> 로컬 복사본과 인터넷 이름 확인 (DNS 전달)에 대 한 azure 가상 컴퓨터  <br/> |
|크로스-프레미스  <br/> |온-프레미스 로컬 복사본과 인트라넷 이름 확인을 위해  <br/> 로컬 복사본과 인트라넷 이름 확인 (DNS 복제 및 전달)에 대 한 azure 가상 컴퓨터  <br/> |
   
 **서로 다른 두 유형의 VNets에 대 한 표 4: DNS 서버 옵션**
  
자세한 내용은 [Vm 및 역할 인스턴스에 대 한 이름 확인](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)을 참조 하십시오.
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>7 단계: 부하 분산 구성 확인 (인터넷 또는 내부).

일부 경우에는 동일한 역할을 하는 서버 집합에 들어오는 트래픽을 배포 하려고 합니다. Azure IaaS가 인터넷에 대 한이 작업을 수행 하는 기본 제공 기능 및 내부 트래픽을 로드 합니다.
  
Azure 인터넷 부하 분산을 임의로 부하 분산 된 집합의 구성원에 게 인터넷에서 들어오는 원치 않는 트래픽을 분산 시킵니다.
  
**그림 4: Azure의 외부 부하 분산 장치**

![그림 4: Azure의 외부 부하 분산 장치](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
그림 4는 인바운드 NAT 규칙 또는 부하 분산 된 집합의 가상 컴퓨터의 집합에는 끝점에서 들어오는 트래픽을 분배 하는 Azure에는 외부 부하 분산 장치를 보여줍니다.
  
Azure 내부 부하 분산을 임의로 부하 분산 된 집합의 구성원에 게 인트라넷 컴퓨터 또는 다른 Azure Vm에서 임의의 들어오는 트래픽을 분산 시킵니다. 
  
**그림 5: Azure의 내부 부하 분산 장치**

![그림 5: Azure의 내부 부하 분산 장치](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
그림 5는 인바운드 NAT 규칙 또는 부하 분산 된 집합의 가상 컴퓨터의 집합에는 끝점에서 들어오는 트래픽을 분배 하는 Azure에는 내부 부하 분산 장치를 표시 합니다.
  
자세한 내용은 [Azure 부하 분산 장치](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)를 참조 하십시오.
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>8 단계: 가상 장비 및 사용자 정의 경로 사용을 결정 합니다.

사용자 VNet의 가상 기기에 대 한 트래픽 음성 메일로 착신 전환 해야하는 경우 서브넷에 하나 이상의 사용자 정의 경로 추가 해야할 수 있습니다.
  
**그림 6: Azure의 가상 어플라이언스 및 사용자 정의 경로**

![그림 6: Azure의 가상 어플라이언스 및 사용자 정의 경로](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
그림 6 크로스-프레미스 VNet 및 가상 기기를 가리키는 가상 컴퓨터 호스팅 서브넷에 할당 된 사용자 정의 경로 보여줍니다.
  
자세한 내용은 [사용자 정의 된 경로 및 IP 전달](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)을 참조 하십시오.
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>9 단계: 인터넷에서 컴퓨터 가상 컴퓨터에 연결 하는 방법을 결정 합니다.

여러 가지 방법으로 프록시 서버 또는 다른에 지 장치를 통해 조직 네트워크에서의 액세스를 포함 하는 프로그램 VNet에 가상 컴퓨터에 대 한 인터넷 액세스를 제공 합니다.
  
표 5 필터링 하거나 원치 않는 들어오는 트래픽을 검사 하기 위한 메서드를 나열 합니다.
  
|**방법**|**배포 모델**|
|:-----|:-----|
|1. 끝점 및 클라우드 서비스에 구성 된 Acl  <br/> |Classic  <br/> |
|2. 네트워크 보안 그룹  <br/> |리소스 관리자 및 클래식  <br/> |
|3. 인바운드 NAT 규칙과 인터넷 연결 부하 분산 장치  <br/> |자원 관리자  <br/> |
|4. 네트워크 보안 어플라이언스 (표시 되지 않음) Azure Marketplace에서  <br/> |리소스 관리자 및 클래식  <br/> |
   
 **표 5: 가상 컴퓨터 및 해당 Azure 배포 모델에 연결 하는 방법**
  
**그림 7: 인터넷을 통한 Azure 가상 컴퓨터에 연결**

![그림 7: 인터넷을 통한 Azure 가상 컴퓨터에 연결](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
그림 7 끝점을 사용 하 여 클라우드 서비스에서 가상 컴퓨터, 네트워크 보안 그룹을 사용 하 여 서브넷에 가상 컴퓨터 및 가상 컴퓨터에는 외부 부하 분산 장치 및 인바운드 규칙의 NAT 사용 하는 서브넷에 연결 하는 인터넷에 연결 된 컴퓨터를 보여줍니다.
  
추가 보안 기능을 제공 합니다.
  
- 원격 데스크톱 및 SSH 연결을 인증 하 고 암호화 하는 합니다.
    
- 인증 되 고 암호화 하는 원격 PowerShell 세션입니다.
    
- IPsec 전송 모드-종단간 암호화에 사용할 수 있습니다.
    
- 외부 및 내부 공격을 방지 하 여 azure DDOS 보호,
    
자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 보안](https://aka.ms/cloudarchsecurity) 및 [Azure 네트워크 보안](https://azure.microsoft.com/blog/azure-network-security/)을 참조 하십시오.
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>단계 10: 여러 VNets에 대 한 VNet-VNet 연결 토폴로지를 결정 합니다.

VNets 연결 하는 조직의 사이트에 사용 되는 것과 유사한 토폴로지를 사용 하 여 서로 연결할 수 있습니다.
  
데이지 체인 구성 시리즈에서 VNets를 연결합니다.
  
**그림 8: 데이지 체인에 대 한 구성을 VNets**

![그림 8: Azure Virtual Network에 대한 데이지 체인 구성](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
그림 8 연속적으로 연결 된 구성을 사용 하 여 계열에 있는 연결 된 다섯 개의 VNets를 표시 합니다.
  
여러 VNets 자체도 서로 게 연결 하는 중앙 VNets 집합에 연결 하는 허브 및 스포크 구성 합니다.
  
**그림 9: 허브 및 스포크에 대 한 구성을 VNets**

![그림 9: Azure Virtual Network를 위한 스포크 및 허브 구성](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
그림 9 두 VNets는 대화 상대와 두 다른 스포크 VNets에 연결 된 허브 6 VNets를 보여줍니다.
  
모든 VNet 서로 게 연결 하는 풀 메시 구성 합니다.
  
**그림 10: 전체 메쉬 VNets에 대 한 구성**

![그림 10: Azure Virtual Network를 위한 망 구성](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
그림 10 4 개의 VNets 6 VNet-VNet 연결의 합계를 사용 하 여, 서로 게 연결을 표시 합니다.
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>크로스-프레미스 VNet에 대 한 계획 단계
<a name="cross_prem"> </a>

크로스-프레미스 VNet에 대 한 다음이 단계를 수행 합니다.
  
> [!TIP]
> 시뮬레이션 된 크로스-프레미스 개발/테스트 환경을 만들려면 [Simulated 크로스-프레미스 Azure에 가상 네트워크를](simulated-cross-premises-virtual-network-in-azure.md)참조 하십시오. 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>1 단계: VNet (S2S VPN 또는 ExpressRoute)에 대 한 크로스-프레미스 연결을 확인 합니다.

표 6 다양 한 유형의 연결을 나열합니다.
  
|**연결 유형**|**용도**|
|:-----|:-----|
|사이트 (S2S) VPN  <br/> |단일 VNet에 (다른 VNets 포함)는 1 ~ 10 개의 사이트를 연결 합니다.  <br/> |
|ExpressRoute  <br/> |인터넷 Exchange 공급자 (IXP) 또는 네트워크 서비스 공급자 (NSP)를 통해 Azure에 안전 하 고 개인 링크입니다.  <br/> |
|지점 사이트 (P2S) VPN  <br/> |VNet 단일 컴퓨터에 연결 합니다.  <br/> |
|VNet 피어 링 또는 VNet VNet (V2V) VPN  <br/> |다른 VNet에는 VNet를 연결합니다.  <br/> |
   
 **표 6: 크로스-프레미스 VNets에 대 한 연결 유형**
  
최대 연결 수에 대 한 자세한 내용은 [네트워킹 제한](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)을 참조 하십시오.
  
VPN 장치에 대 한 자세한 내용은 [사이트 마다 가상 네트워크 연결에 대 한 VPN 장치](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)를 참조 하십시오.
  
피어 링 VNet 하는 방법에 대 한 자세한 내용은 [VNet 피어 링](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)을 참조 하십시오.
  
**그림 11: 크로스-프레미스 VNet에 연결 하 네가지 방법**

![그림 11: 크로스-프레미스 Azure Virtual Network에 연결하는 세 가지 방법 ](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
그림 11에는 다음과 같은 네가지 유형의 연결 된 VNet 나와: P2S 연결 하는 컴퓨터에서 온-프레미스 네트워크에서는 S2S VPN 연결는 온-프레미스 네트워크에서는 ExpressRoute 연결 및 다른 VNet에서 VNet-VNet 연결 합니다. 
  
다음과 같은 방법으로 VNet에서 Vm에 연결할 수 있습니다.
  
- 온-프레미스 네트워크 또는 인터넷에서 VNet Vm 관리
    
- 온-프레미스 네트워크에서 IT 작업량 액세스
    
- 추가 VNets 통해 네트워크의 확장을 필터링
    
연결에 대 한 보안은 다음에 의해 제공 됩니다.
  
- P2S는 Secure Socket 터널링 프로토콜 (SSTP)를 사용 하 여 
    
- AES256와 IPsec 터널 모드를 사용 하는 S2S 및 VNet-VNet VPN 연결
    
- ExpressRoute는 개인 WAN 연결
    
자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 보안](https://aka.ms/cloudarchsecurity) 및 [Azure 네트워크 보안](https://azure.microsoft.com/blog/azure-network-security/)을 참조 하십시오.
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>2 단계: 온-프레미스 VPN 장치 또는 라우터를 결정 합니다.

온-프레미스 VPN 장치 또는 라우터 역할을 합니다.
  
- IPsec 피어 Azure 게이트웨이에서 S2S VPN 연결을 종료 합니다.
    
- 개인 피어 링 ExpressRoute 연결에 대 한 BPG 피어 및 종료 지점입니다.
    
**그림 12: 온-프레미스 VPN 라우터 또는 장치**

![그림 12: 온-프레미스 VPN 라우터 또는 장치](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
그림 12는 온-프레미스 VPN 라우터 또는 장치에 연결 된 크로스-프레미스 VNet를 보여줍니다.
  
자세한 내용은 [대 한 VPN 게이트웨이](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)참조 하십시오.
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>3 단계:는 VNet의 주소 공간에 접속할 수 있도록 하려면 인트라넷에 경로 추가 합니다.

온-프레미스에서 라우팅 VNets에는 다음의 구성 됩니다.
  
1. VPN 장치를 향해 가리키는 VNet 주소 공간에 대 한 경로입니다.
    
2. S2S VPN 또는 ExpressRoute 연결을 통해 가리키는 VPN 장치에서 VNet 주소 공간에 대 한 경로
    
**그림 13: 온-프레미스 경로 VNet에 접속할 수 있도록 하는 데 필요한**

![그림 13: Azure VNet에 연결하는 데 필요한 온-프레미스 경로](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
그림 13 온-프레미스 라우터 및 VPN 라우터 또는 VNet의 주소 공간을 나타내는 장치에 필요한 라우팅 정보를 보여줍니다.
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>4 단계:에 대 한 ExpressRoute, 공급 업체에 문의 새 연결에 대 한 계획 합니다.

세 가지 방법으로 온-프레미스 네트워크 및 Microsoft 클라우드 간에 개인 피어 링와 ExpressRoute에 대 한 연결을 만들 수 있습니다.
  
- 클라우드 exchange에 함께 배치
    
- 지점간 이더넷 연결
    
- 모든-를-모든 (IP VPN) 네트워크
    
**그림 14: ExpressRoute를 사용 하 여 크로스-프레미스 VNet에 연결**

![그림 14: ExpressRoute를 사용해 크로스-프레미스 Azure Virtual Network에 연결](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
그림 14 크로스-프레미스 VNet 및 온-프레미스 라우터에서 Microsoft Azure로는 ExpressRoute 연결을 표시합니다.
  
자세한 내용은 [Microsoft 클라우드 연결에 대 한 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)을 참조 하십시오.
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>5 단계: Azure 게이트웨이에 대 한 로컬 네트워크 주소 공간을 결정 합니다.

Azure는 라우팅에 대 한는 온-프레미스 또는 다른 VNets는 VNet에서, 게이트웨이에 할당 된 로컬 네트워크 주소 공간에 일치 하는 Azure 게이트웨이 통해 트래픽을 전달 합니다.
  
**그림 15: 크로스-프레미스 VNet는 로컬 네트워크 주소 공간**

![그림 15: 크로스-프레미스 Azure Virtual Network에 대한 로컬 네트워크 주소 공간](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
그림 15 온-프레미스 네트워크에 연결할 수 있는 주소 공간을 나타내는 Azure 게이트웨이에서 크로스-프레미스 VNet 및 로컬 네트워크 주소 공간을 표시 합니다. 
  
다음과 같은 방법으로 로컬 네트워크 주소 공간을 정의할 수 있습니다.
  
- 옵션 1: 사용 (업데이트 필요할 수 새 서브넷을 추가 하는 경우) 또는 현재 필요한 주소 공간에 대 한 접두사 목록입니다.
    
- 옵션 2: 전체 온-프레미스 주소 공간 (업데이트 새 주소 공간을 추가 하는 경우에 필요).
    
Azure 게이트웨이 요약 된 경로 허용 하지 않으므로 VNet 주소 공간을 포함 하지 않는 되도록 옵션 2에 대 한 로컬 네트워크 주소 공간을 정의 해야 합니다.
  
**그림 16: 주소 공간 구멍 VNet 주소 공간에서 만든**

![그림 16: Virtual Network 공간에서 만든 주소 공간 구멍](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
그림 16 루트 공간을 사용 하는 주소 공간, 및 VNet 주소 공간 표시를 보여줍니다.
  
다음은 주소 공간 "구멍"는 VNet 하 여 만든 주위 로컬 네트워크 주소 공간에 대 한 접두사를 정의 하는 예제가입니다.
  
- 개인 주소 공간 (10.0.0.0/8, 172.16.0.0/12, 및 192.168.0.0/16)의 일부를 사용 하 여 자신의 온-프레미스 네트워크를 통해 조직 합니다. 이러한 옵션 2 및 10.100.100.0/24 자신의 VNet 주소 공간 했습니다.
    
표 7 단계 및이 예제에 대 한 로컬 네트워크 주소 공간을 정의 하는 접두사를 결과 보여줍니다.
  
|**단계**|**결과**|
|:-----|:-----|
|1. VNet 주소 공간에 대 한 루트 공간 없는 접두사를 나열 합니다.  <br/> |172.16.0.0/12 및 192.168.0.0/16  <br/> |
|2. 최대 8 진수를 변수 되지 않은 VNet 주소 공간에 사용 되는 마지막 8 진수가 제외한 겹치지 않는 접두사를 나열 합니다.  <br/> |10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 접두사, 10.100.0.0/16 건너뛰기)  <br/> |
|3. VNet 주소 공간을 사용 하는 마지막 옥텟 내에서 겹치지 않는 접두사를 나열 합니다.  <br/> |10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 접두사, 10.100.100.0/24 건너뛰기)  <br/> |
   
 **표 7: 예에서는 로컬 주소 네트워크 공간**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>6 단계: Azure에서 호스팅되는 DNS 서버와 DNS 복제를 위해 온-프레미스 DNS 서버를 구성 합니다.

온-프레미스 컴퓨터 Azure 기반 서버의 이름을 확인할 수 있고 Azure 기반 서버에는 온-프레미스 컴퓨터의 이름을 확인할 수를 확인, 다음을 구성 합니다.
  
- 온-프레미스 DNS 서버에 전달 하 여 VNet에서 DNS 서버
    
- DNS 서버 온-프레미스 간 및는 VNet에서 적절 한 영역의 DNS 복제
    
**그림 17: DNS 복제 및 크로스-프레미스 VNet에서 DNS 서버에 대 한 착신 전환**

![그림 17: 크로스-프레미스 Azure Virtual Network의 DNS 서버에 대한 DNS 복제 및 전달](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
그림 17은 VNet의 서브넷 및 온-프레미스 네트워크에 있는 DNS 서버와 크로스-프레미스 VNet를 표시합니다. DNS 복제 및 전달 두 DNS 서버 간에 구성 되었습니다.
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>7 단계: 강제 적용 된 터널링의 사용을 결정 합니다.

Azure 서브넷에 대 한 기본 시스템 경로 인터넷을 가리킵니다. 모든 가상 컴퓨터에서의 트래픽은 크로스-프레미스 연결을 통해 되도록 그 다음 홉 주소로 Azure 게이트웨이 사용 하는 기본 경로와 라우팅 테이블을 만듭니다. 다음은 서브넷과 경로 테이블을 연결합니다. 터널링 강제로으로 알려져 있습니다. 자세한 내용은 [Configure 강제 터널링](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)을 참조 하십시오.
  
**그림 18: 사용자 정의 경로 및 크로스-프레미스 VNet에 대 한 강제 적용 된 터널링**

![그림 18: 크로스-프레미스 Azure Virtual Network에 대한 강제 터널링 및 사용자 정의 경로](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
그림 18 Azure 게이트웨이를 가리키도록 설정 하는 서브넷에 대 한 사용자 정의 경로와 크로스-프레미스 VNet를 표시 합니다.
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure의 SharePoint Server 2016 팜
<a name="cross_prem"> </a>

인트라넷 Azure IaaS에서 호스팅되는 IT 작업의 예로 항상 사용 가능, 다중 계층 SharePoint Server 2016 팜에 있습니다.
  
**그림 19: Azure IaaS의 가용성이 인트라넷 SharePoint Server 2016 팜**

![Azure IaaS에 팜 된 고가용성 SharePoint Server 2016 ](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
그림 19 프런트엔드 및 데이터 계층에 대 한 내부 부하 분산 장치를 사용 하는 크로스-프레미스 VNet에 배포 된 SharePoint Server 2016 팜 9 명의 서버를 표시 합니다. 단계별 디자인 및 배포 지침을 비롯 한 자세한 내용은 [Microsoft Azure의 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)를 참조 하십시오.
  
> [!TIP]
> 시뮬레이션 된 크로스-프레미스 VNet에서 단일 서버 SharePoint Server 2016 팜을 만들려면 [Azure 개발/테스트 환경에서 인트라넷 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)를 참조 합니다. 
  
가상는 크로스-프레미스 Azure에 가상 컴퓨터에 배포 하는 IT 작업의 추가 예제를 보려면 네트워크 [Azure IaaS에 대 한 하이브리드 클라우드 시나리오](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)를 참조 하십시오.
  
## <a name="see-also"></a>참고 항목

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)


