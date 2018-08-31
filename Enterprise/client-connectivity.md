---
title: 클라이언트 연결
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: '요약: 클라이언트 컴퓨터 및 Office 365 테넌트 데이터 센터의 위치에 따라 클라이언트 컴퓨터가 Office 365 테넌트에 연결되는 방식을 설명합니다.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223040"
---
# <a name="client-connectivity"></a>클라이언트 연결

 **요약:** 클라이언트 컴퓨터 및 Office 365 테넌트 데이터 센터의 위치에 따라 클라이언트 컴퓨터가 Office 365 테넌트에 연결되는 방식을 설명합니다.
  
Office 365 지진 또는 정전 등의 한 지역에서 주요 문제가 발생 하는 경우에 실행 하 고 서비스를 유지 하는 Microsoft 데이터 센터는 전세계에 있습니다. Office 365 테 넌 트에 연결할 때 클라이언트 연결에 게 표시할 적절 한 데이터 센터에 테 넌 트 호스트 되는 위치입니다. 테 넌 트를 호스팅할 수를 결정 하는 규칙은 Microsoft와 계약에 의해 정의 됩니다. 클라이언트에서 해당 데이터 센터 위치에서 데이터를 확보 하는 방법을 결정 하는 규칙 사용 중인 서비스의 아키텍처에 따라 달라 집니다.
  
예, Office 365 포털에 로그온 할 때 일반적으로 클라이언트에 게 가장 가까운 데이터 센터에 연결 하 고 서비스에 따라 이동 후 다음을 사용 합니다. 전자 메일을 실행 하는 경우 UI를 표시 하는 초기 연결을 가장 가까운 데이터 센터에서 계속 가져올 수 있지만 가장 가까운 데이터 센터와 테 넌 트의 전자 메일에는 내용을 표시 하려면 있는 위치는 데이터 센터 간의 두번째 연결을 열 수 있습니다. Microsoft fast 매우 빠른 데이터 센터에 datacenter 연결의 결과로 만들어진 세계에서 상위 10 개의 네트워크 중 하나는 작동 합니다.
  
문서를 읽고 나면 가능성이 알게 이유는 [Office 365 Url 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) 를 지정 하지 않고 센터당, 자신이 단순히 너무 상호 연결 하 고 최적 확인 하기 위해 각 장치 의존 합니다.
  
Office 365에 대 한 Azure ExpressRoute를 사용 하는 경우 대부분의 경우에서 사용자 연결 들어갈 수 개인 연결을 통해 Office 365로 여기에 설명 된 공용 연결 하는 대신 있습니다. 클라이언트에서 어떻게 연결 하는 방법에 대 한 원칙 여전히 정확 하 게 됩니다. [Office 365 용 Azure ExpressRoute](azure-expressroute.md)대 한 자세한 내용을 알아봅니다.
  
비즈니스 네트워크 요청에 대 한 Skype에서 더 자세히에 대 한 [미디어 품질 및 네트워크 연결 성능을 비즈니스 온라인 용 Skype에서](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)문서를 읽습니다.

||
|:-----|
| 이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.|

> [!NOTE]
> 안전 하 고 데이터 센터에서 개인 되기 때문에 고객 데이터를 관리 하는 매우 주의 했습니다. 개인정보 보호 관리 위해 취할 단계에 대 한 자세한 내용은 [보안 센터](https://go.microsoft.com/fwlink/?LinkID=397383)에 포함 됩니다.
  
## <a name="connecting-to-the-nearest-datacenter"></a>가장 가까운 데이터 센터에 연결

가장 일반적인 유형의 연결, 이며 Office 365 포털와 Exchange Online에서 사용 됩니다. 이 상황에서는 클라이언트를 Office 365에 연결 하려고 하는 경우 해당 컴퓨터의 DNS 쿼리 영역을 자신의 컴퓨터에서 들리는 세계를 확인 하 고 Office 365에서 가장 가까운 데이터 센터에 요청을 리디렉션합니다.
  
가장 가까운 데이터 센터에서 포털에 대 한 연결을 중지 하 고 클라이언트 컴퓨터에서 해당 위치에서 클라이언트의 테 넌 트에 대 한 정보로 제공 됩니다.
  
Exchange Online 이동 단계를 추가 합니다. 클라이언트 컴퓨터에서 가장 가까운 데이터 센터에 연결 되어, 되 면 해당 데이터 센터의 Exchange 서버에 연결 데이터 센터 테 넌 트 위치한 실제로에서 볼 수 있듯이 *이 작업을 어떻게 수행 섹션 작동* 아래입니다. 가장 가까운 데이터 센터 다음 프록시 서버는 Exchange Online 사서함 서버에 클라이언트 컴퓨터에서 요청 합니다. 이 전자 메일 및 일정 항목을 Microsoft 네트워크를 검색 하는 중요 한 역할을 이동 하 여 클라이언트 컴퓨터에 대 한 경험을 속도가 빨라집니다.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>표준 클라우드 서비스에 대 한이 작업을 어떻게 합니까?

이 연결 프로세스는 높은 트래픽이 대 한 표준와 같은 Office 365 검색에 유용한 웹 응용 프로그램입니다. 이 섹션에 대해 간략하게 설명 하 고는 하는 프로세스의 단계를 보여줍니다. 클라이언트 컴퓨터에서 테 넌 트 동일한 영역에 없을 때 연결 클라이언트에 연결 되는 서비스에 따라 훨씬 다르게 합니다.
  
 이 다이어그램에서는 표준 Office 365 구축을 사용 하 여 북미에서 테 넌 트와 고객을 보여줍니다. 이 시나리오에서는 요청을 만드는 유럽을 이동한 하 고 있는 사람의 해당 위치에서 Office 365를 사용 합니다.
  
1. 클라이언트 컴퓨터에서 Office 365와 연결 된 IP 주소에 대 한 로컬 DNS 서버를 묻습니다.

2. 클라이언트 컴퓨터의 로컬 DNS 서버가 Office 365와 연결 된 IP 주소에 대 한 Microsoft DNS 서버를 묻습니다.

3. Microsoft의 DNS 서버 (클라이언트의 DNS 서버 위치에 따라), 지역 서버 이름을 반환 하 고 1과 지역 Office 365 데이터 센터의 IP 주소를 확인 하는 2 단계를 반복 하는 클라이언트 컴퓨터에서 키를 누릅니다.

4. 클라이언트 컴퓨터에서 해당 지역 데이터 센터의 IP 주소에 연결합니다.

5. Exchange Online 서버 고객의 테 넌 트가 있는 활성 데이터 센터에 대 한 연결을 설정 합니다.

![가장 가까운 지역 데이터 센터](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>이 작업 sovereign에 대 한 제품을 클라우드 하는 방법

이 연결이 21 Vianet에서 운영 하는 Office 365와 같은 군주 클라우드 서비스에서 약간 다릅니다. Office 365의 군주 인스턴스에 테 넌 트 포털 연결은 허용 하는 가장 가까운 Office 365 서버는 테 넌 트가 있는 군주 영역 내에 있는 서버 수 있습니다. 마찬가지로, 고객 당사의 군주 클라우드 또는 표준 제품에서 SharePoint Online에 액세스 하는 테 넌 트가 있는 프런트엔드 서버에 연결 됩니다. 활성 데이터 센터에 연결을 참조 하십시오.
  
1. 클라이언트 컴퓨터에서 Office 365와 연결 된 IP 주소에 대 한 로컬 DNS 서버를 묻습니다.

2. 클라이언트 컴퓨터의 로컬 DNS 서버가 Office 365와 연결 된 IP 주소에 대 한 Microsoft DNS 서버를 묻습니다.

3. Microsoft의 DNS 서버 (클라이언트의 DNS 서버 위치에 따라), 지역 서버 이름을 반환 하 고 1과 지역 Office 365 데이터 센터의 IP 주소를 확인 하는 2 단계를 반복 하는 클라이언트 컴퓨터에서 키를 누릅니다.

4. 클라이언트 컴퓨터에서 해당 지역 데이터 센터의 IP 주소에 연결합니다.

5. Exchange Online 서버 고객의 테 넌 트가 있는 활성 데이터 센터에 대 한 연결을 설정 합니다.

![가장 가까운 지역 한국 데이터 센터](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>활성 데이터 센터에 연결

활성 데이터 센터에 연결 하 두꺼운 데이터 전송 작업에 대 한 설계 하 고 현재 SharePoint Online에서 사용 합니다. 이 상황에서는 클라이언트가 Office 365에 연결 하려고 하는 경우 해당 브라우저 리디렉션되면 활성 데이터 센터에 자신의 SharePoint Online 테 넌 트에 대 한 합니다.
  
## <a name="how-does-this-work"></a>작동 방식

클라이언트 컴퓨터가 다른 지역에서 SharePoint Online에 연결 하는 경우 연결이 활성 SharePoint Online 데이터 센터로 리디렉션됩니다. 이 시나리오에서는 고객 제공, 로컬 남아 있는 포털 연결 되 고 활성 데이터 센터에 전달 되 고 SharePoint Online 연결 하는 표준을 사용 중입니다.
  
1. 클라이언트 컴퓨터에서 Office 365와 연결 된 IP 주소에 대 한 로컬 DNS 서버를 묻습니다.

2. 클라이언트 컴퓨터의 로컬 DNS 서버가 Office 365와 연결 된 IP 주소에 대 한 Microsoft DNS 서버를 묻습니다.

3. Microsoft의 DNS 서버 (클라이언트의 Office 365 테 넌 트의 위치에 따라) 활성 SharePoint Online 데이터 센터의 서버 이름을 반환 하 고 1과 현재 Office 365 데이터 센터의 IP 주소를 확인 하는 2 단계를 반복 하는 클라이언트 컴퓨터에서 키를 누릅니다.

4. 클라이언트 컴퓨터에서 해당 활성 데이터 센터의 IP 주소에 연결합니다.

![활성 한국 데이터 센터](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>VPN(가상 사설망)을 통해 연결

이러한 종류의 연결 가상 사설망 (VPN) 클라이언트 컴퓨터에서 사용 되는 경우에 적용 됩니다. 실제로 Office 365 동작 변경 되지 않고 단순히 있기 때문에 대 한 VPN을 사용 하 고 Vpn 클라이언트 컴퓨터 성능이 저하 된 환경에서 Office 365 및 일반적으로 결과에 대 한 연결을 설정 하는 방법을 제어 하는 일반적으로 사용 되를 지금 설명 하는 것이 중요 합니다.
  
## <a name="how-does-this-work"></a>작동 방식

다른 지역에 회사 사무실에 대 한 VPN 연결을 설정 하는 클라이언트 컴퓨터, 사무실에 있는 DNS 서버는 클라이언트 컴퓨터의 위치에서 DNS 서버 대신 사용 됩니다. 대부분의 경우에서이 추가 연결 VPN 통해 Office 365 환경에서 떨어집니다. Office 365 서비스에 근접 한 최종 사용자에 게 가능한으로 고객 서비스 연결을 최적화 됩니다. Azure에 지 네트워크, 콘텐츠 배달 네트워크 및 클라이언트 컴퓨터에 근접 Office 365 서비스에 대 한 네트워크 요청을 만들 때 최적의 사용자 환경을 제공 하기 위해 Microsoft 네트워크에서 신뢰할 수 있는 네트워크 용량을 활용 하는 대부분의 서비스 가능한 합니다.
  
1. 클라이언트 컴퓨터에서 Office 365와 연결 된 IP 주소에 대 한 VPN DNS 서버를 묻습니다.

2. 클라이언트 컴퓨터의 VPN DNS 서버가 Office 365와 연결 된 IP 주소에 대 한 Microsoft DNS 서버를 묻습니다.

3. Microsoft의 DNS 서버 (VPN DNS 서버 위치에 따라) 지역 서버 이름, 반환 하 고 1과 지역 Office 365 데이터 센터의 IP 주소 정보를 얻을 수는 2 단계를 반복 하는 클라이언트 컴퓨터에서 키를 누릅니다.

4. 클라이언트 컴퓨터에서 가장 가까운 VPN 연결을를 설정한 회사 사무실에 있는 IP 주소를 데이터 센터에 연결 합니다.

![VPN 데이터 센터 연결](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>참고 항목

[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365에 대한 네트워크 연결](network-connectivity.md)
