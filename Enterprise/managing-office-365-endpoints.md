---
title: Office 365 끝점 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/11/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 일부 엔터프라이즈 네트워크에서는 일반 인터넷 위치에 대 한 액세스를 제한 하거나, 상당한 백 또는 네트워크 트래픽 처리를 포함 합니다. 이와 같은 네트워크의 컴퓨터가 office 365에 액세스할 수 있도록 하려면 네트워크 및 프록시 관리자가 office 365 끝점 목록을 구성 하는 fqdn, url 및 IP 주소 목록을 관리 해야 합니다. 네트워크 요청이 Office 365에 도달할 수 있도록 하려면 이러한 사항을 직접 경로, 프록시 바이패스 및/또는 방화벽 규칙 및 PAC 파일에 추가 해야 합니다.
ms.openlocfilehash: ed3a64ad3cd840987d105ae99a5ba5cbf41567e9
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2019
ms.locfileid: "30053002"
---
# <a name="managing-office-365-endpoints"></a>Office 365 끝점 관리

여러 사무실 위치 및 연결 WAN이 있는 대부분의 엔터프라이즈 조직은 office 365 네트워크 연결에 대 한 구성을 필요로 합니다. 모든 추가 패킷 수준 검사 또는 처리를 무시 하 고 모든 신뢰할 수 있는 Office 365 네트워크 요청을 방화벽을 통해 직접 보내 네트워크를 최적화할 수 있습니다. 이렇게 하면 대기 시간 및 경계 용량 요구 사항이 줄어듭니다. Office 365 네트워크 트래픽은 사용자에 게 최적의 성능을 제공 하기 위한 첫 번째 단계 인지 확인 하는 것이 좋습니다. office 365 네트워크 연결에 대 한 자세한 내용은 [office 365 네트워크 연결 원리](office-365-network-connectivity-principles.md) 를 참조 하세요.

office [365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md) 를 사용 하 여 office 365 네트워크 끝점과 변경 사항에 액세스 하는 것이 좋습니다.

중요 한 office 365 네트워크 트래픽을 관리 하는 방법에 관계 없이 office 365을 사용 하려면 인터넷에 연결 해야 합니다. 연결이 필요한 기타 네트워크 끝점은 [Office 365 IP 주소 및 URL 웹 서비스에 포함 되지 않은 추가 끝점](additional-office365-ip-addresses-and-urls.md) 에 나열 되어 있습니다.

Office 365 네트워크 끝점을 사용 하는 방법은 엔터프라이즈 조직 네트워크 아키텍처에 따라 달라 집니다. 이 문서에서는 엔터프라이즈 네트워크 아키텍처에서 Office 365 IP 주소 및 url과 통합할 수 있는 여러 가지 방법을 간략하게 설명 합니다. 신뢰할 네트워크 요청을 선택할 수 있는 가장 쉬운 방법은 각 사무실 위치에서 자동 Office 365 구성을 지 원하는 sdwan 장치를 사용 하는 것입니다. 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>중요 한 Office 365 네트워크 트래픽의 로컬 분기 송신을 위한 sdwan

각 지사 위치에서 office 365 for endpoints 범주에 대 한 트래픽을 라우팅하도록 구성 된 sdwan 장치를 제공 하거나, 범주를 Microsoft의 네트워크로 직접 최적화 하 고 허용할 수 있습니다. 온-프레미스 데이터 센터 트래픽, 일반 인터넷 웹 사이트 트래픽 및 Office에 대 한 트래픽 365 기본 범주 끝점을 포함 하는 기타 네트워크 트래픽은 더 많은 네트워크 경계를 가진 다른 위치로 전송 됩니다.

Microsoft는 sdwan 공급자와 협력 하 여 자동화 된 구성을 사용 하도록 설정 합니다. 자세한 내용은 [Office 365 네트워킹 파트너 프로그램](office-365-networking-partner-program.md)을 참조 하세요.

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>중요 한 Office 365 트래픽을 직접 라우팅하기 위해 PAC 파일 사용

PAC 또는 WPAD 파일을 사용 하 여 Office 365에 연결 되어 있지만 IP 주소가 없는 네트워크 요청을 관리 합니다. 프록시 또는 경계 장치를 통해 전송 되는 일반적인 네트워크 요청에 대 한 대기 시간이 길어집니다. SSL 침입 및 검사에서는 가장 큰 대기 시간을 만들기 때문에 프록시 인증 및 신뢰도 조회와 같은 다른 서비스를 사용 하면 성능이 저하 되 고 사용자 환경이 잘못 될 수 있습니다. 또한 이러한 경계 네트워크 장치는 모든 네트워크 연결 요청을 처리 하기에 충분 한 용량을 필요로 합니다. 직접적인 Office 365 네트워크 요청에 대해 프록시 또는 검사 장치를 바이패스 하는 것이 좋습니다.
  
[powershell Gallery PacFile](https://www.powershellgallery.com/packages/Get-PacFile) 는 Office 365 IP 주소 및 URL 웹 서비스에서 최신 네트워크 끝점을 읽고 샘플 PAC 파일을 만드는 PowerShell 스크립트입니다. 기존 PAC 파일 관리와 통합 되도록 스크립트를 수정할 수 있습니다. 

![방화벽 및 프록시를 통해 Office 365에 연결](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**그림 1-간단한 엔터프라이즈 네트워크 경계**

PAC 파일은 그림 1의 포인트 1에 있는 웹 브라우저에 배포 됩니다. 중요 한 Office 365 네트워크 트래픽을 직접 송신 하기 위해 PAC 파일을 사용 하는 경우에는 네트워크 경계 방화벽에서 이러한 url 뒤에 오는 IP 주소에 대 한 연결도 허용 해야 합니다. 이 작업은 PAC 파일에 지정 된 것과 같은 Office 365 끝점 범주에 대 한 IP 주소를 가져오고 해당 주소를 기반으로 방화벽 acl을 만드는 방법으로 수행 됩니다. 방화벽은 그림 1의 포인트 3입니다. 

별도로 범주 끝점을 최적화 하기 위해 직접 라우팅만 선택한 경우 프록시 서버에 보내는 모든 필수 허용 범주 끝점이 프록시 서버에 나열 되어야 더 이상 처리 되지 않습니다. 예를 들어 SSL 중단 및 검사 및 프록시 인증은 최적화 및 허용 범주 끝점과 모두 호환 되지 않습니다. 프록시 서버는 그림 1의 포인트 2입니다.

일반적인 구성은 프록시 서버에 방문 하는 Office 365 네트워크 트래픽에 대 한 대상 IP 주소에 대 한 프록시 서버의 모든 아웃 바운드 트래픽을 처리 하지 않고 허용 하는 것입니다. SSL 중단 및 검사와 관련 된 문제에 대 한 자세한 내용은 [Office 365 트래픽에 타사 네트워크 장치 또는 솔루션 사용](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)을 참조 하십시오.

PacFile 스크립트는 두 가지 유형의 PAC 파일을 생성 합니다.

|**종류**|**설명**|
|:-----|:-----|
|**개** <br/> |끝점 트래픽 다이렉트 및 다른 모든 항목을 프록시 서버로 최적화 합니다. <br/> |
|**2** <br/> |끝점 트래픽 직접 및 프록시 서버에 대 한 모든 작업을 최적화 하 고 허용 합니다. 이 유형을 사용 하 여 모든 지원 되는 모든 방법 Office 365 트래픽을가을 수 있는 네트워크 세그먼트 및 다른 모든 대상에 프록시 서버로 보낼 수도 있습니다. <br/> |

다음은 PowerShell 스크립트를 호출 하는 간단한 예입니다.

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

스크립트에 전달할 수 있는 매개 변수에는 여러 가지가 있습니다.

|**매개 변수**|**설명**|
|:-----|:-----|
|**ClientRequestId** <br/> |이는 필수 사항이 며 호출을 수행 하는 클라이언트 컴퓨터를 나타내는 웹 서비스에 전달 되는 GUID입니다. <br/> |
|**Instance** <br/> |기본적으로 국가별 설정에 해당 하는 Office 365 서비스 인스턴스입니다. 웹 서비스에도 전달 됩니다. <br/> |
|**TenantName** <br/> |Office 365 테 넌 트 이름입니다. 웹 서비스로 전달 되 고 일부 Office 365 url에서 교체 가능한 매개 변수로 사용 됩니다. <br/> |
|**유형** <br/> |생성 하려는 프록시 PAC 파일의 유형입니다. <br/> |

다음은 추가 매개 변수를 사용 하 여 PowerShell 스크립트를 호출 하는 또 다른 예입니다.

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>프록시 서버 바이패스 Office 365 네트워크 트래픽 처리 

직접 아웃 바운드 트래픽에 대해 PAC 파일을 사용 하지 않는 경우에도 프록시 서버를 구성 하 여 네트워크 경계에서 처리를 우회 하려고 합니다. 일부 프록시 서버 공급 업체에서는 [Office 365 네트워킹 파트너 프로그램](office-365-networking-partner-program.md)에 설명 된 것 처럼 자동화 된 구성을 사용 하도록 설정 했습니다. 

이 작업을 수동으로 수행 하는 경우 Office 365 IP 주소 및 URL 웹 서비스에서 최적화 및 허용 끝점 범주 데이터를 가져오고 이러한 항목에 대 한 처리를 우회 하도록 프록시 서버를 구성 해야 합니다. 최적화 및 허용 범주 끝점에 대해 SSL 중단 및 검사 및 프록시 인증을 방지 하는 것이 중요 합니다. 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 IP 주소 및 url에 대 한 변경 관리

네트워크 경계에 적합 한 구성을 선택 하는 것 외에도 Office 365 끝점에 대 한 변경 관리 프로세스를 채택 하는 것이 중요 합니다. 이러한 끝점은 정기적으로 변경 되며, 변경 사항을 관리 하지 않으면 새 IP 주소 또는 URL을 추가한 후 사용자가 차단 되거나 성능 저하로 인해 완료 될 수 있습니다. 

Office 365 IP 주소 및 url에 대 한 변경 내용은 보통 매월 말일에 게시 됩니다. 운영, 지원 또는 보안 요구 사항으로 인해 변경 내용이 해당 일정 외부에 게시 되는 경우가 있습니다.

IP 주소 또는 URL이 추가 되어 작업을 수행 해야 하는 변경 내용이 게시 되 면 해당 끝점에 Office 365 서비스가 있을 때까지 변경 내용을 게시할 때까지 30 일 동안 알림이 표시 됩니다. 이 알림 기간을 목표로 하기는 하지만 운영, 지원 또는 보안 요구 사항으로 인해 항상 가능 하지 않을 수 있습니다. 연결을 유지 하기 위해 즉시 작업을 수행 하지 않아도 되는 변경 사항 (예: 제거 된 IP 주소 또는 url 또는 덜 중요 한 변경)에는 사전 알림이 포함 되지 않습니다. 제공 되는 알림과 관계 없이 각 변경에 대해 예상 되는 서비스 활성 날짜가 나열 됩니다.

### <a name="change-notification-using-the-web-service"></a>웹 서비스를 사용 하 여 알림 변경

Office 365 IP 주소 및 URL 웹 서비스를 사용 하 여 변경 알림을 가져올 수 있습니다. Office 365에 연결 하는 데 사용 하는 끝점의 버전을 확인 하려면 한 시간 한 번 **/version** 웹 메서드를 호출 하는 것이 좋습니다. 사용 중인 버전과 비교 하 여이 버전이 변경 되는 경우에는 **/pndweb** 메서드에서 최신 끝점 데이터를 가져오고 필요에 따라 **/changes** 웹 메서드를 통해 차이를 가져와야 합니다. 찾은 버전을 변경 하지 않은 경우에는 **/tendpoints** 또는 **/dweb** 메서드를 호출 하지 않아도 됩니다. 

자세한 내용은 [Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)를 참조 하세요.

### <a name="change-notification-using-rss-feeds"></a>RSS 피드를 사용 하 여 알림 변경

Office 365 IP 주소 및 URL 웹 서비스는 Outlook에서 구독할 수 있는 RSS 피드를 제공 합니다. IP 주소 및 url에 대 한 각 Office 365 서비스 인스턴스별 페이지에는 RSS url에 대 한 링크가 있습니다. 자세한 내용은 [Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)를 참조 하세요.

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Microsoft 흐름을 사용 하 여 알림 및 승인 검토 변경

각 월별로 제공 되는 네트워크 끝점 변경에 대 한 수동 처리가 여전히 필요할 수 있다는 것을 이해 하 고 있습니다. Microsoft 흐름을 사용 하 여 전자 메일로 알리는 흐름을 만들고 Office 365 네트워크 끝점에 변경 내용이 있을 때 변경 내용에 대 한 승인 프로세스를 선택적으로 실행할 수 있습니다. 검토가 완료 되 면 흐름에서 방화벽 및 프록시 서버 관리 팀에 변경 내용을 자동으로 전자 메일로 보낼 수 있습니다. 

microsoft flow 샘플과 템플릿에 대 한 자세한 내용은 [Office 365 IP 주소 및 url 변경에 대 한 전자 메일을 받으려면 microsoft flow 사용](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651) 을 참조 하세요.
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 네트워크 끝점 FAQ

Office 365 연결에 대 한 자주 묻는 관리자의 질문:
  
### <a name="how-do-i-submit-a-question"></a>질문을 제출 하려면 어떻게 해야 합니까?

아래쪽에 있는 링크를 클릭 하 여 기사가 도움이 되었는지 여부를 지정 하 고 추가 질문을 제출 합니다. 의견을 모니터링 하 고 여기에서 가장 자주 묻는 질문을 업데이트 합니다.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>테 넌 트의 위치를 확인 하려면 어떻게 해야 하나요?

 [데이터 센터 맵을](http://aka.ms/datamaps)사용 하 여 **테 넌 트 위치** 를 결정 하는 것이 가장 좋습니다.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Microsoft와의 피어 링이 적절 합니까?

 **피어 링 위치** 는 [Microsoft와의 피어 링](https://www.microsoft.com/peering)에 자세히 설명 되어 있습니다.
  
2500 개 이상의 ISP 피어 링 관계를 전역적으로 또는 70 지점에 연결 하는 경우 네트워크에서 우리에 게 가져오는 것이 원활 해야 합니다. ISP의 피어 링 관계가 가장 최적이 되도록 몇 분 정도의 시간이 소요 되는 것을 방지할 수는 있지만,이에 대 한 [몇 가지 예는](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) 네트워크에 대 한 좋은 피어 링 모범 사례입니다. 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>게시 된 목록에 없는 IP 주소에 대 한 네트워크 요청이 표시 됨, 액세스 권한을 제공 해야 하나요?
<a name="bkmk_MissingIP"> </a>

여기서는로 직접 라우팅하는 Office 365 서버에 대 한 IP 주소만 제공 합니다. 이는 네트워크 요청이 표시 되는 모든 IP 주소의 전체 목록이 아닙니다. Microsoft 및 타사 소유, 게시 되지 않은 IP 주소에 대 한 네트워크 요청이 표시 됩니다. 이러한 IP 주소는 변경 시 시기 적절 한 알림을 방지 하는 방식으로 동적으로 생성 되거나 관리 됩니다. 방화벽에서 이러한 네트워크 요청의 fqdn을 기반으로 액세스를 허용할 수 없으면 PAC 또는 WPAD 파일을 사용 하 여 요청을 관리 합니다.
  
자세한 내용을 보려는 Office 365와 연결 된 IP를 확인 하세요.
  
1. [CIDR 계산기](http://jodies.de/ipcalc)를 사용 하 여 IP 주소가 보다 큰 게시 범위에 포함 되어 있는지 확인 합니다.
2. 파트너가 [whois 쿼리](https://dnsquery.org/)를 사용 하 여 IP를 소유 하는지 확인 합니다. 해당 Microsoft가 소유 하 고 있으면 내부 파트너가 될 수 있습니다.
3. 인증서 확인 브라우저에서 *HTTPS://\<IP_ADDRESS\> * 을 사용 하 여 ip 주소에 연결 하 고, 인증서에 나열 된 도메인을 확인 하 여 ip 주소와 연결 된 도메인을 파악 합니다. microsoft 소유의 ip 주소이 고 Office 365 IP 주소 목록이 아닌 경우 ip 주소는 *MSOCDN.NET* 또는 다른 microsoft 도메인과 같은 microsoft CDN에 ip 정보를 게시 하지 않은 상태로 연결 될 수 있습니다. 인증서에서 도메인을 찾는 경우 IP 주소를 나열 하는 것은 사용자에 게 알려 주세요.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Microsoft 도메인 이름에 nsatc.net 또는 akadns.net와 같은 이름이 표시 되는 이유는 무엇 인가요?
<a name="bkmk_akamai"> </a>

office 365 및 기타 Microsoft 서비스에서는 Akamai 및 markmonitor와 같은 몇 가지 타사 서비스를 사용 하 여 Office 365 환경을 개선 합니다. 가능한 최상의 환경을 유지 하기 위해 나중에 이러한 서비스를 변경할 수 있습니다. 이렇게 하면 타사 소유의 도메인, 레코드 또는 IP 주소를 가리키는 CNAME 레코드를 게시 하는 경우가 많습니다. 타사 도메인은 CDN 같은 콘텐츠를 호스팅하거나 지역 트래픽 관리 서비스와 같은 서비스를 호스팅할 수 있습니다. 이러한 제 3 자에 대 한 연결이 표시 되 면 해당 사용자는 클라이언트의 초기 요청이 아닌 리디렉션 또는 조회 형식입니다. 일부 고객은 타사 서비스가 사용할 수 있는 잠재적 fqdn의 긴 목록을 명시적으로 추가 하지 않고도이 형태의 참조와 리디렉션을 통과할 수 있도록 해야 합니다.
  
서비스 목록은 언제 든 지 변경 될 수 있습니다. 현재 사용 중인 서비스 중 일부는 다음과 같습니다.
  
* \*nsatc.net* 를 포함 하는 요청을 볼 때 [markmonitor](https://www.markmonitor.com/) 가 사용 되 고 있습니다. 이 서비스는 도메인 이름 보호 및 모니터링을 제공 하 여 악의적인 동작 으로부터 보호 합니다.
  
* \*exacttarget.com* 에 대 한 요청을 볼 때 [ExactTarget](https://www.marketingcloud.com/) 가 사용 되 고 있습니다. 이 서비스는 악성 동작에 대 한 전자 메일 링크 관리 및 모니터링을 제공 합니다.
  
다음 fqdn 중 하나를 포함 하는 요청이 표시 되 면 [Akamai](https://www.akamai.com/) 가 사용 중입니다. 이 서비스는 지리적 DNS 및 콘텐츠 배달 네트워크 서비스를 제공 합니다.
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Office 365에 대 한 최소 연결이 가능 해야 함
<a name="bkmk_thirdparty"> </a>

Office 365은 인터넷을 통해 작동 하도록 구축 된 서비스 모음으로, 안정성 및 가용성 약속은 사용할 수 있는 다양 한 표준 인터넷 서비스를 기반으로 합니다. 예를 들어 DNS, CRL 및 cdns와 같은 표준 인터넷 서비스는 대부분의 최신 인터넷 서비스를 사용 하기 위해 연결할 수 있는 것 처럼 Office 365을 사용할 수 있어야 합니다.

Office 365 제품군은 주요 서비스 지역으로 분류 되어 있습니다. 이러한 기능은 연결에 선택적으로 사용 하도록 설정할 수 있으며, all에 대 한 종속성 이며 항상 필요한 공통 영역이 있습니다.

|**서비스 영역**|**설명**|
|:-----|:-----|
|**Exchange** <br/> |exchange online 및 exchange online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online 및 비즈니스용 OneDrive <br/> |
|**비즈니스용 Skype Online 및 Microsoft Teams** <br/> |비즈니스용 Skype 및 Microsoft 팀 <br/> |
|**일반** <br/> |office 365 Pro Plus, office Online, Azure AD 및 기타 일반 네트워크 끝점 <br/> |

기본 인터넷 서비스 외에, 기능 통합에만 사용 되는 타사 서비스도 있습니다. 이러한 작업은 통합에 필요 하지만, 끝점에 액세스할 수 없는 경우 서비스의 핵심 기능이 계속 작동 하 게 된다는 것을 Office 365 endpoints 문서에 선택적으로 표시 합니다. 필요한 모든 네트워크 끝점은 필수 특성이 true로 설정 됩니다. 선택 사항인 모든 네트워크 끝점에는 필수 특성이 false로 설정 되 고, notes 특성은 연결이 차단 되는 경우 예상 되는 누락 된 기능을 자세히 설명 합니다.
  
Office 365을 사용 하려는 경우 타사 서비스를 찾을 수 없는 경우 [이 문서에 표시 된 모든 fqdn이 프록시 및 방화벽을 통해 허용 되는지 확인](urls-and-ip-address-ranges.md)해야 합니다.
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Microsoft의 소비자 서비스에 대 한 액세스를 차단 하는 방법
<a name="bkmk_consumer"> </a>

소비자 서비스에 대 한 액세스를 제한 해야 하는 경우 사용자의 위험에 대 한 보안을 차단 하는 유일한 방법은 *login.live.com* FQDN에 대 한 액세스를 제한 하는 것입니다. 이 FQDN은 MSDN, TechNet 등의 소비자가 아닌 서비스를 포함 하는 광범위 한 서비스 집합에서 사용 됩니다. 이 FQDN은 microsoft 지원의 보안 파일 교환 프로그램 에서도 사용 되며 microsoft 제품에 대 한 문제 해결을 용이 하 게 하기 위해 파일을 전송 해야 합니다.  이 FQDN에 대 한 액세스를 제한 하면 이러한 서비스에 연결 된 네트워크 요청에 대 한 규칙에 대 한 예외도 포함 해야 할 수도 있습니다.
  
Microsoft 소비자 서비스에 대 한 액세스를 차단 하더라도 Office 365 테 넌 트 또는 기타 서비스를 사용 하 여 네트워크의 누군가가 정보를 exfiltrate는 것을 방지할 수 있습니다.
  
## <a name="related-topics"></a>관련 항목

[Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)

[Microsoft Azure 데이터 센터 IP 범위](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 공용 IP 공간](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune에 대 한 네트워크 인프라 요구 사항](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[express 경로 및 Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md)
