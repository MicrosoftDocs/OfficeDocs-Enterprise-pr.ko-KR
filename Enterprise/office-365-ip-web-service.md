---
title: Office 365 IP 주소 및 URL 웹 서비스
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/7/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Office 365 네트워크 트래픽을 보다 잘 식별하고 차별화하기 위해 새로운 웹 서비스는 Office 365 끝점을 게시하여 변경 내용을 보다 쉽게 평가하고 구성하며 이러한 변경 내용으로 업데이트하여 최신 상태를 유지할 수 있도록 합니다.
ms.openlocfilehash: 35a34071a76e551cde8342566a912e4fd4d0100e
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/14/2019
ms.locfileid: "33976523"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 IP 주소 및 URL 웹 서비스

Office 365 네트워크 트래픽을 보다 잘 식별하고 차별화하기 위해 새로운 웹 서비스는 Office 365 끝점을 게시하여 변경 내용을 보다 쉽게 평가하고 구성하며 이러한 변경 내용으로 업데이트하여 최신 상태를 유지할 수 있도록 합니다. XML 형식은 2018년 10월 2일에 단계적으로 중단될 예정입니다.

고객 또는 네트워크 주변 장치 공급업체는 Office 365 IP 주소 및 FQDN 항목에 대한 새로운 REST 기반 웹 서비스를 구축할 수 있습니다. 다음 URL을 사용하여 웹 브라우저에서 직접 데이터에 액세스할 수 있습니다.

- 최신 버전의 Office 365 URL 및 IP 주소 범위에 대해서는 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)을 사용하세요.
- Office 365 URL 및 방화벽과 프록시 서버에 대한 IP 주소 범위 데이터에 대해서는 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)를 사용하세요.
- 웹 서비스를 처음 사용할 수 있던 2018년 7월 말 이후의 모든 최신 변경 내용을 가져오려면 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)를 사용하세요.

고객은 이 웹 서비스를 사용하여 다음을 수행할 수 있습니다.

- Office 365 끝점 데이터를 가져오고 네트워킹 장치에 대한 모든 서식을 수정하기 위한 PowerShell 스크립트를 업데이트합니다.
- 이 정보를 사용하여 클라이언트 컴퓨터에 배포된 PAC 파일을 업데이트합니다.

네트워크 주변 장치 공급업체는 이 웹 서비스를 사용하여 다음을 수행할 수 있습니다.

- 자동화된 구성 목록을 다운로드하기 위한 장치 소프트웨어를 만들고 테스트합니다.
- 현재 버전을 확인합니다.
- 현재 변경 내용을 가져옵니다.

> [!NOTE]
> Azure ExpressRoute를 사용하여 Office 365에 연결하는 경우 Azure ExpressRoute에서 지원되는 Office 365 서비스에 익숙해질 수 있또록 [Office 365용 Azure ExpressRoute](https://docs.microsoft.com/office365/enterprise/azure-expressroute)를 검토하십시오. 또한 [Office 365 URL 및 IP 주소 범위](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) 문서를 검토하여 Office 365 응용 프로그램의 네트워크 연결 중 인터넷 연결이 필요한 것은 무엇인지 확인하십시오. 이렇게 하면 주변 보안 장치를 보다 잘 구성하는 데 도움이 됩니다.

자세한 내용은 다음을 참조하세요.

- [Office 365 기술 커뮤니티 포럼의 공지 사항 블로그 게시물](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [웹 서비스 사용에 대한 질문이 있는 경우 Office 365 기술 커뮤니티 포럼](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>일반 매개 변수

다음은 모든 웹 서비스 메서드에서 공통되는 매개 변수입니다.

- **format=<JSON | CSV>** - 기본적으로 반환되는 데이터 형식은 JSON입니다. 이 선택적 매개 변수를 사용하여 쉼표로 구분된 값(CSV) 형식으로 데이터를 반환하십시오.
- **ClientRequestId =\<guid >** - 클라이언트 연결을 위해 생성해야 하는 필수 GUID입니다. 웹 서비스를 호출하는 각 시스템에 대한 GUID를 생성해야 합니다. 다음 예제에 표시된 GUID는 앞으로 웹 서비스에 의해 차단될 수 있으므로 사용하지 마십시오. GUID 형식은 _에서-xxxx-xxxx-xxxx-xxxxxxxxxxxx_이며 여기서 x는 16진수를 나타냅니다. GUID를 생성하려면 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 명령을 사용하십시오.

## <a name="version-web-method"></a>버전 웹 메서드

Microsoft는 매월 말, 경우에 따라 운영 또는 지원 요구 때문에 주기 이외의 기간에 Office 365 IP 주소 및 FQDN 항목을 업데이트합니다. 게시딘 각 인스턴스에 대한 데이터에는 버전 번호가 할당됩니다. 버전 웹 메서드를 사용하여 각 Office 365 서비스 인스턴스의 최신 버전을 폴링할 수 있습니다. 버전을 매일 또는 적어도 시간별로 확인하는 것이 좋습니다. 새 버전은 각 월이 시작할 때 제공되도록 예정되어 있습니다. 경우에 따라 지원 인시던트, 보안 또는 기타 운영 요구 사항으로 인해 월 중간에 새 버전이 제공될 수 있습니다.

버전 웹 메소드의 매개 변수는 다음과 같습니다.

- **AllVersions = < true | false >** -기본적으로 반환되는 버전은 최신 버전입니다. 이 선택적 매개 변수를 포함하여 웹 서비스가 처음 릴리스된 이후에 모든 게시된 버전을 요청하십시오.
- **형식 = < JSON | CSV | RSS >** -는 JSON 및 CSV 형식 외에도 버전 웹 방법으로도 지원 RSS 합니다. 이 선택적 매개 변수를 _AllVersions = true_ 매개 변수와 함께 사용하여 Outlook이나 다른 RSS 판독기에서 사용할 수 있는 RSS 피드를 요청할 수 있습니다.
- **인스턴스=<전세계 | 중국 | 독일 | USGovDoD | USGovGCCHigh> ** -이 선택적 매개 변수는 버전을 반환할 인스턴스를 지정합니다. 생략할 경우 모든 인스턴스가 반환됩니다. 유효한 인스턴스는 전세계, 중국, 독일, USGovDoD, USGovGCCHigh입니다.

버전 웹 메서드는 속도가 제한되지 않으며 429 HTTP 응답 코드를 반환하지 않습니다. 버전 웹 메서드에 대한 응답에는 1시간 동안의 데이터 캐시를 권장하는 cache-control 헤더가 포함되어 있습니다. 버전 웹 메서드의 결과는 단일 레코드 또는 레코드의 배열일 수 있습니다. 각 레코드의 요소는 다음과 같습니다.

- instance - Office 365 서비스 인스턴스의 짧은 이름입니다.
- latest - 지정된 인스턴스 끝점의 최신 버전입니다.
- versions - 지정된 인스턴스에 대한 모든 이전 버전 목록입니다. 이 요소는 AllVersions 매개 변수가 true인 경우에만 포함됩니다.

Microsoft Flow를 사용하여 IP 주소 및 URL에 대한 변경 내용을 이메일로 알림을 받을 수 있습니다. [Microsoft Flow를 사용하여 Office 365 IP 주소 및 Url에 대한 변경 내용을 이메일로 받기](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)를 참조하세요.

### <a name="examples"></a>예제:

예제 1 요청 URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

이 URI은 각 Office 365 서비스 인스턴스의 최신 버전을 반환합니다. 예제 결과:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> 이러한 URI의 ClientRequestID 매개 변수에 대한 GUID는 예제에 불과합니다. 웹 서비스 URL을 사용해보려면 자체 GUID를 생성합니다. 이러한 예제에 표시되는 GUID는 앞으로 웹 서비스에 의해 차단될 수 있습니다.

예제 2 요청 URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

이 URI은 지정된 Office 365 서비스 인스턴스의 최신 버전을 반환합니다. 예제 결과:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

예제 3 요청 URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

이 URI는 출력을 CSV 형식으로 표시합니다. 예제 결과:

```csv
instance,latest
Worldwide,2018063000
```

예제 4 요청 URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

이 URI는 Office 365 Worldwide 서비스 인스턴스에 대해 게시된 모든 이전 버전을 보여 줍니다. 예제 결과:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

예제 5 RSS 피드 URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

이 URI는 각 버전의 변경 내용 목록에 대한 링크를 포함하는 게시된 버전의 RSS 피드를 보여 줍니다. 예제 결과:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>엔드포인트 웹 메서드

엔드포인트 웹 메서드는 Office 365 서비스를 구성하는 IP 주소 범위 및 URL에 대한 모든 레코드를 반환합니다. 엔드포인트 웹 메서드의 최신 데이터를 네트워크 디바이스 구성에 사용해야 하지만, 추가를 위해 제공된 사전 통지로 인해 게시된 후 최대 30일 동안 데이터를 캐시할 수 있습니다. 버전 웹 메소드가 새 버전의 데이터를 사용할 수 있음을 나타내면 엔드 포인트 웹 메소드만 다시 호출할 것을 권장합니다.

엔드포인트 웹 메서드의 매개 변수는 다음과 같습니다.

- **ServiceAreas=<공통 | 교환 | SharePoint | Skype> ** - 쉼표로 구분 된 서비스 영역 목록입니다. 유효한 항목은 _공통_, _Exchange_, _SharePoint_ 및 _Skype_입니다. 공통 서비스 영역 항목은 다른 모든 서비스 영역의 전제 조건이므로 웹 서비스에 항상 포함됩니다. 이 매개 변수를 포함하지 않으면 모든 서비스 영역이 반환됩니다.
- **TenantName=<tenant_name >** - Office 365 테넌트 이름. 웹 서비스는 제공된 이름을 가져와 테넌트 이름이 포함된 URL의 일부에 삽입합니다. 테넌트 이름을 제공하지 않으면 URL의 해당 부분에 와일드 카드 문자(\*)가 있습니다.
- **NoIPv6=<true | false>** - 네트워크에서 IPv6를 사용하지 않는 경우 출력에서 IPv6 주소를 제외하려면 이 매개 변수를 true로 설정합니다.
- **인스턴스=<전세계 | 중국 | 독일 | USGovDoD | USGovGCCHigh> ** -이 필수 매개 변수는 엔드포인트을 반환할 인스턴스를 지정합니다. 유효한 인스턴스는 _전세계_, _중국_, _독일_, _USGovDoD_, _USGovGCCHigh_입니다.

엔드포인트 웹 메서드를 동일한 클라이언트 IP 주소에서 여러 번 호출하면 HTTP 응답 코드 429(너무 많은 요청)가 수신될 수 있습니다. 이것은 대부분의 사용자에게 표시되지 않습니다. 이 응답 코드를 받은 경우, 다시 요청을 반복하기까지 1시간을 기다리세요. 버전 웹 메서드가 사용 가능한 새 버전이 있음을 나타내면 엔드포인트 웹 메소드만 호출하도록 계획합니다.

끝점 웹 메서드의 결과는 각 레코드가 끝점 집합을 나타내는 레코드 배열입니다. 각 레코드에 대한 요소는 다음과 같습니다.

- id - 끝점 집합의 변경이 불가능한 ID 번호입니다.
- serviceArea - 이 요소가 속하는 서비스 영역은 Common, Exchange, SharePoint 또는 Skype입니다.
- url - 끝점 집합에 대한 URL입니다. DNS 레코드의 JSON 배열입니다. 비워 두면 생략됩니다.
- tcpPorts - 끝점 집합에 대한 TCP 포트입니다. 모든 포트 요소는 쉼표로 구분된 포트 목록 또는 대시 문자(-)로 구분된 포트 범위로 서식이 지정됩니다. 포트는 해당 범주에 대한 해당 끝점 집합에 있는 모든 IP 주소 및 모든 URL에 적용됩니다. 비워 두면 생략됩니다.
- udpPorts - 이 끝점 집합의 IP 주소 범위에 대한 UDP 포트입니다. 비워 두면 생략됩니다.
- ips - 나열된 TCP 또는 UDP 포트와 연결된 이 끝점 집합과 연결된 IP 주소 범위입니다. IP 주소 범위의 JSON 배열입니다. 비워 두면 생략됩니다.
- 범주 - 엔드포인트 집합의 연결 범주입니다. 유효한 값은 최적화, 허용 및 기본입니다. 엔드포인트 데이터를 사용하여 IP 주소 또는 URL의 범주를 검색하는 경우 쿼리가 여러 범주를 반환할 수 있습니다. 이러한 문제가 발생하는 이유로는 몇 가지가 있습니다. 이러한 문제가 발생하는 경우 최고 우선 순위 범주의 권장 사항을 따라야 합니다. 예를 들어 엔드포인트가 최적화와 허용 모두에서 나타나는 경우 최적화의 요구 사항을 따라야 합니다. 이는 필수입니다.
- expressRoute - 이 엔드포인트 집합이 ExpressRoute를 통해 라우팅되는 경우 True 또는 False입니다.
- required - Office 365에 대한 연결이 지원되기 위해 이 끝점 집합이 필요한 경우 True입니다. 이 끝점 집합이 선택 사항이면 False입니다.
- notes - 선택적 끝점의 경우 이 텍스트는 네트워크 계층에서 이 끝점 집합의 IP 주소나 URL에 액세스할 수 없는 경우 손실되는 Office 365 기능에 대해 설명합니다. 비워 두면 생략됩니다.

### <a name="examples"></a>예제:

예제 1 요청 URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

이 URI은 모든 워크로드에 대한 Office 365 Worldwide 인스턴스에 대한 모든 끝점을 가져옵니다. 출력 일부를 보여 주는 예제 결과는 다음과 같습니다.

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

추가 끝점 집합이 이 예제에는 포함되어 있지 않습니다.

예제 2 요청 URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

이 예제에서는 Exchange Online에 대한 Office 365 Worldwide 인스턴스의 끝점과 종속성만 가져옵니다.

예제 2의 출력은 결과에 SharePoint Online 또는 비즈니스용 Skype Online에 대한 끝점이 포함되지 않는다는 점을 제외하고 예제 1과 비슷합니다.

## <a name="changes-web-method"></a>변경 웹 메서드

변경 웹 메서드는 게시된 가장 최근 업데이트를 반환합니다. 일반적으로는 IP 주소 범위 및 URL에 대한 이전 달 변경 내용에 해당합니다. 처리할 가장 중요한 변경 내용은 방화벽 액세스 제어 목록에 IP 주소를 추가하지 못하기 때문에 새 URL 또는 IP 주소가 추가되는 경우 또는 프록시 서버 우회 목록에 대한 URL로 인해 해당 네트워크 장치 내부에서 Office 365 사용자의 작동이 중단될 수 있는 경우입니다. 운영 요구 사항에도 불구하고 이러한 중단이 발생하기 30일 전 알림에 _Add_ 작업이 추가됩니다.

변경 내용 웹 메서드에 대한 필수 매개 변수입니다.

- ** 버전 = \<YYYYMMDDNN>** - 필수 URL 경로 매개 변수입니다. 이 값은 현재 구현한 버전이어야 합니다. 웹 서비스는 해당 버전 이후의 변경 사항을 반환합니다. 형식은 _YYYYMMDD_입니다. 여기서 _NN_은 하루 동안 게시해야하는 여러 버전이 있는 경우 자연수 증가분이고 _00_은 해당 날짜의 첫 번째 업데이트를 나타냅니다. 웹 서비스는 _버전_ 매개 변수가 정확히 10 자리를 포함하도록 요구합니다.

변경 웹 메서드는 엔드 포인트 웹 메서드와 같은 방식으로 비율이 제한됩니다. 429 HTTP 응답 코드를 받은 경우, 다시 요청을 반복하기까지 1시간을 기다리세요.

변경 웹 메서드의 결과는 각 레코드가 특정 끝점 버전의 변경을 나타내는 레코드 배열입니다. 각 레코드에 대한 요소는 다음과 같습니다.

- id - 변경 레코드의 변경이 불가능한 ID입니다.
- endpointSetId - 변경된 끝점 집합 레코드의 ID입니다.
- disposition - change, add 또는 remove일 수 있으며, 끝점 세트 레코드에 대해 수행된 변경을 설명합니다.
- impact - 모든 변경이 모든 환경에서 동일하게 중요한 것은 아닙니다. 이 요소는 이 변경의 결과로 엔터프라이즈 네트워크 주변 환경에 대해 예상되는 영향을 설명합니다. 이 특성은 버전 **2018112800** 이상의 변경 레코드에만 포함됩니다. impact에 대한 옵션은 다음과 같습니다.
  - AddedIp - IP 주소가 Office 365에 추가되었으며 곧 서비스될 예정입니다. 이 옵션은 방화벽 또는 기타 계층 3 네트워크 주변 디바이스에서 수행해야 하는 변경을 나타냅니다. 사용을 시작하기 전에 이 옵션을 추가하지 않으면 중단이 발생할 수 있습니다.
  - AddedUrl - URL이 Office 365에 추가되었으며 곧 서비스에 게시됩니다. 이는 프록시 서버 또는 URL 파싱 네트워크 주변 장치에서 수행해야하는 변경 사항을 나타냅니다. 사용하기 전에 이것을 먼저 추가하지 않으면 중단이 발생할 수 있습니다.
  - AddedIpAndUrl - IP 주소 및 URL이 둘 다 추가되었습니다. 이 옵션은 방화벽 계층 3 디바이스 또는 프록시 서버나 URL 구문 분석 디바이스에서 수행해야 하는 변경을 나타냅니다. 사용을 시작하기 전에 이 옵션을 추가하지 않으면 중단이 발생할 수 있습니다.
  - RemovedIpOrUrl – 하나 이상의 IP 주소 또는 URL이 Office 365에서 제거되었습니다. 주변 디바이스에서 네트워크 끝점을 제거해야 하지만 이 작업을 반드시 수행해야 하는 마감일은 없습니다.
  - ChangedIsExpressRoute – ExpressRoute 지원 특성이 변경되었습니다. ExpressRoute을 사용하는 경우 구성에 따라 작업을 수행해야 할 수도 있습니다.
  - MovedIpOrUrl – 이 끝점 세트와 다른 끝점 세트 간에 IP 주소 또는 URL을 이동했습니다. 일반적으로 필요한 작업은 없습니다.
  - RemovedDuplicateIpOrUrl – 중복된 IP 주소 또는 URL을 제거했으나 Office 365에 여전히 게시됩니다. 일반적으로 필요한 작업은 없습니다.
  - OtherNonPriorityChanges – 메모 필드와 같이 다른 옵션보다 덜 중요한 항목이 변경되었습니다.
- version - 변경이 도입된 게시된 끝점 집합의 버전입니다. 버전 번호는 _YYYYMMDDNN_ 형식입니다. 여기서 NN은 하루 동안 게시되어야 하는 버전이 여러 개인 경우에 증가되는 자연수입니다.
- 이전 - 엔드포인트 집합에서 변경된 요소의 이전 값을 설명하는 하위 구조입니다. 새로 추가된 엔드포인트 집합에는 포함되지 않습니다. _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, 및 _notes_를 포함합니다.
- 현재 - 엔드포인트 집합의 변경 요소에 대한 업데이트된 값을 설명하는 하부 구조입니다. _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, 및 _notes_를 포함합니다.
- add - 끝점 집합 컬렉션에 추가할 항목을 자세히 설명하는 하위 구조입니다. 추가할 항목이 없으면 생략합니다.
  - effectiveDate - 서비스에서 추가가 적용될 날짜를 정의합니다.
  - ips - _ips_ 배열에 추가할 항목입니다.
  - url - _urls_ 배열에 추가할 항목입니다.
- remove - 끝점 집합에서 제거할 항목을 자세히 설명하는 하위 구조입니다. 제거할 항목이 없으면 생략합니다.
  - ips- _ips_ 배열에서 제거할 항목입니다.
  - urls -_urls_l 배열에서 제거할 항목입니다.

### <a name="examples"></a>예제:

예제 1 요청 URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Office 365 Worldwide 서비스 인스턴스에 대한 모든 이전 변경 내용을 요청합니다. 예제 결과:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

예제 2 요청 URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Office 365 Worldwide 인스턴스에 대한 지정된 버전 이후의 변경 내용을 요청합니다. 이 경우 지정된 버전은 최신 버전입니다. 예제 결과:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>예제 PowerShell 스크립트

다음은 업데이트 된 데이터에 대해 수행해야 하는 작업이 있는지 알아보기 위해 실행할 수 있는 PowerShell 스크립트입니다. 이 스크립트는 Office 365 Worldwide 인스턴스 엔드포인트의 버전 번호를 확인합니다. 변경이 있으면 "허용"및 "최적화" 범주 엔드포인트에 대한 엔드포인트와 필터를 다운로드합니다.. 또한 여러 호출에서 고유 한 _ClientRequestId_를 사용하고 임시 파일에 있는 최신 버전을 저장합니다. 한 시간에 한 번 이 스크립트를 호출하여 버전 업데이트를 확인해야 합니다.

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    $flatIp6s = $endpointSets | ForEach-Object {
    $endpointSet = $_
    $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
    # IPv6 strings have colons while IPv6 strings have dots
    $ip6s = $ips | Where-Object { $_ -like '*:*' }
    $ipCustomObjects = @()
    if ($endpointSet.category -in ("Optimize")) {
        $ipCustomObjects = $ip6s | ForEach-Object {
            [PSCustomObject]@{
                category = $endpointSet.category;
                ip = $_;
                tcpPorts = $endpointSet.tcpPorts;
                udpPorts = $endpointSet.udpPorts;
            }
        }
    }
    $ipCustomObjects
}
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>예제 Python 스크립트

다음은 업데이트된 데이터에 대해 수행해야 하는 작업이 있는지 확인하기 위해 실행할 수 있는 Windows 10의 Python 3.6.3으로 테스트된 Python 스크립트입니다. 이 스크립트는 Office 365 Worldwide 인스턴스 끝점에 대한 버전 번호를 확인합니다. 변경 내용이 있는 경우 끝점을 다운로드하고 _Allow_ 및 _Optimize_ 범주 끝점을 필터링합니다. 또한 여러 호출에서 고유한 ClientRequestId를 사용하고 찾은 최신 버전을 임시 파일에 저장합니다. 이 스크립트를 1시간에 1회 호출하여 버전 업데이트를 확인해야 합니다.

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>웹 서비스 인터페이스 버전 관리

앞으로 이러한 웹 서비스 메서드의 매개 변수 또는 결과를 업데이트해야 할 수 있습니다. 이러한 웹 서비스의 일반 공급 버전이 게시된 후에 Microsoft는 웹 서비스에 대한 자료 업데이트 정보를 미리 알리기 위해 적절한 조치를 취할 것입니다. Microsoft에서 업데이트를 위해 웹 서비스를 사용하여 클라이언트를 변경해야 한다고 판단할 경우 웹 서비스의 이전 버전(하나 이전 버전)을 새 버전이 릴리스되고 12개월 이상 동안 사용할 수 있게 지원할 것입니다. 이 기간 동안 업그레이드하지 않는 고객은 웹 서비스 및 해당 메서드에 액세스하지 못할 수 있습니다. 고객은 웹 서비스 인터페이스 서명이 다음과 같이 변경될 경우 웹 서비스 클라이언트가 계속 작동되도록 해야 합니다.

- 이전 클라이언트가 제공할 필요가 없으며 이전 클라이언트가 수신하는 결과에 영향을 미치지 않는 새로운 선택적 매개 변수를 기존 웹 메서드에 추가
- 응답 REST 항목 또는 추가 열 중 하나에 있는 새로운 명명된 특성을 응답 CSV 에 추가
- 이전 클라이언트에서 호출하지 않는 새 이름의 새 웹 메서드 추가

## <a name="office-365-endpoint-functions-module"></a>Office 365 엔드포인트 함수 모듈

Microsoft는 Office 365 서비스의 최신 URI를 가져오기 위해 REST 서비스를 호스팅하고 있습니다.  URI를 컬렉션으로 사용하려면 이 모듈을 몇 가지 유용한 cmdlet과 함께 사용할 수 있습니다.

### <a name="calling-the-rest-service"></a>REST 서비스를 호출

이 모듈을 사용하려면 하드 디스크 어딘가에서 모듈 파일 [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1)을 복사하여 다음 명령을 사용하여 직접 가져옵니다.

```powershell
    Import-Module O365EndpointFunctions.psm1
```

모듈을 가져온 후에는 REST 서비스를 호출할 수 있습니다. 이렇게 하면 현재 URI를 PowerShell에서 직접 처리할 수 있는 컬렉션이 반환됩니다. 다음 명령의 설명처럼 Office 365 테넌트의 이름을 입력해야 합니다.

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant]
```

#### <a name="parameters"></a>매개 변수 

- **tenantName** - Office 365 테넌트의 이름입니다. 이 매개 변수는 선택 사항입니다.
- **ForceLatest** - 이 스위치는 REST API가 항상 최신 URI의 전체 목록을 반환하도록 합니다.
- **Ipv6** -이 스위치는 IPv6 주소도 반환합니다. 기본값으로 IPv4만 반환 됩니다.

### <a name="examples"></a>예제

IPv6 주소를 포함한 모든 URI의 전체 목록을 반환

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

Exchange 온라인 서비스의 IP 주소만 반환

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a>프록시 PAC 파일 내보내기

이 모듈을 사용해 프록시 PAC 파일을 만들 수 있습니다. 이 예제에서는 먼저 엔드포인트를 가져오고 결과를 필터링하여 URL을 선택합니다. 이러한 URL은 명령을 통해 내보내기됩니다.  

```powershell
 Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a>관련 항목
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md)

[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)

[Office 365에 대한 네트워크 연결](network-connectivity.md)
  
[비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[비즈니스용 Skype Online의 네트워크 최적화](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
