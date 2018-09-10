---
title: Office 365 IP 주소 및 URL 웹 서비스
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
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
ms.openlocfilehash: 3abd6a0692ae4d66c76f8c0d65653b83646c6e23
ms.sourcegitcommit: d07feeba2e886febc6a57a5c33b0df02b3db5631
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "23830894"
---
# <a name="office-365-ip-address-and-url-web-service"></a>**Office 365 IP 주소 및 URL 웹 서비스**

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

자세한 내용은 다음을 참조하세요.

- [Office 365 기술 커뮤니티 포럼의 공지 사항 블로그 게시물](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [웹 서비스 사용에 대한 질문이 있는 경우 Office 365 기술 커뮤니티 포럼](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>**일반 매개 변수**

다음은 모든 웹 서비스 메서드에서 공통되는 매개 변수입니다.

- **format=CSV | JSON** - 쿼리 문자열 매개 변수입니다. 기본적으로 반환되는 데이터 형식은 JSON입니다. CSV(쉼표로 구분된 값) 형식으로 데이터를 반환하려면 이 선택적 매개 변수를 포함합니다.
- **ClientRequestId** - 쿼리 문자열 매개 변수입니다. 클라이언트 연결에 대해 생성하는 필수 GUID입니다. 웹 서비스를 호출하는 각 컴퓨터에 대해 GUID를 생성해야 합니다. 다음 예제에 표시되는 GUID는 향후 웹 서비스에서 차단될 수 있으므로 사용하지 않도록 합니다. GUID 형식은 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_입니다. 여기서 x는 16진수를 나타냅니다. GUID를 생성하려면 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 명령을 사용합니다.

## <a name="version-web-method"></a>**버전 웹 메서드**

Microsoft는 매월 말, 경우에 따라 운영 또는 지원 요구 때문에 주기 이외의 기간에 Office 365 IP 주소 및 FQDN 항목을 업데이트합니다. 게시딘 각 인스턴스에 대한 데이터에는 버전 번호가 할당됩니다. 버전 웹 메서드를 사용하여 각 Office 365 서비스 인스턴스의 최신 버전을 폴링할 수 있습니다. 버전을 매일 또는 적어도 시간별로 확인하는 것이 좋습니다. 새 버전은 각 월이 시작할 때 제공되도록 예정되어 있습니다. 경우에 따라 지원 인시던트, 보안 또는 기타 운영 요구 사항으로 인해 월 중간에 새 버전이 제공될 수 있습니다.

버전 웹 메서드에 대한 단일 매개 변수는 다음과 같습니다.

- **AllVersions=true** - 쿼리 문자열 매개 변수입니다. 기본적으로 반환되는 버전은 최신 버전입니다. 게시된 모든 버전을 요청하려면 이 선택적 매개 변수를 포함합니다.
- **Format=JSON** | **CSV** | **RSS** – JSON 및 CSV 형식 외에도, 버전 웹 메서드는 RSS도 지원합니다. 이 매개 변수를 allVersions=true 매개 변수와 함께 사용하여 Outlook 또는 기타 RSS 판독기에서 사용할 수 있는 RSS 피드를 요청할 수 있습니다.
- **Instance** - 경로 매개 변수입니다. 이 선택적 매개 변수는 버전을 반환할 인스턴스를 지정합니다. 생략하면 모든 인스턴스가 반환됩니다. 유효한 인스턴스는 Worldwide, China, Germany, USGovDoD, USGovGCCHigh입니다.

버전 웹 메서드의 결과는 단일 레코드 또는 레코드의 배열일 수 있습니다. 각 레코드의 요소는 다음과 같습니다.

- instance - Office 365 서비스 인스턴스의 짧은 이름입니다.
- latest - 지정된 인스턴스 끝점의 최신 버전입니다.
- versions - 지정된 인스턴스에 대한 모든 이전 버전 목록입니다. 이 요소는 AllVersions 매개 변수가 true인 경우에만 포함됩니다.

### <a name="examples"></a>**예제:**

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

[!IMPORTANT]
이러한 URI의 ClientRequestID 매개 변수에 대한 GUID는 예제에 불과합니다. 웹 서비스 URL을 사용해보려면 자체 GUID를 생성합니다. 이러한 예제에 표시되는 GUID는 앞으로 웹 서비스에 의해 차단될 수 있습니다.

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
...
```

## <a name="endpoints-web-method"></a>**끝점 웹 메서드**

끝점 웹 메서드는 Office 365 서비스를 구성하는 IP 주소 범위 및 URL에 대한 모든 레코드를 반환합니다. 끝점 웹 메서드의 최신 데이터는 네트워크 장치 구성에 사용되는 동안, 추가에 대해 제공된 사전 알림 때문에 게시되고 최대 30일 동안 캐시될 수 있습니다. 끝점 웹 메서드에 대한 매개 변수는 다음과 같습니다.

- **ServiceAreas** - 쿼리 문자열 매개 변수입니다. 쉼표로 구분된 서비스 영역 목록입니다. 유효한 항목은 Common, Exchange, SharePoint, Skype입니다. 일반적인 서비스 영역 항목은 다른 모든 서비스 영역에 대한 필수 구성 요소이기 때문에 웹 서비스에 항상 포함되어야 합니다. 이 매개 변수를 포함하지 않으면 모든 서비스 영역이 반환됩니다.
- **TenantName** - 쿼리 문자열 매개 변수입니다. Office 365 테넌트 이름입니다. 웹 서비스는 제공된 이름을 가져와 테넌트 이름을 포함하는 URL의 부분에 삽입합니다. 테넌트 이름을 제공하지 않으면 URL의 해당 부분에 와일드카드 문자(\*)가 표시됩니다.
- **NoIPv6** - 쿼리 문자열 매개 변수입니다. 네트워크에서 IPv6를 사용하지 않는 경우 출력에서 IPv6 주소를 제외하려면 이 매개 변수를 true로 설정합니다.
- **Instance** - 경로 매개 변수입니다. 이 필수 매개 변수는 끝점을 반환할 인스턴스를 지정합니다. 유효한 인스턴스는 Worldwide, China, Germany, USGovDoD, USGovGCCHigh입니다.

끝점 웹 메서드의 결과는 각 레코드가 끝점 집합을 나타내는 레코드 배열입니다. 각 레코드에 대한 요소는 다음과 같습니다.

- id - 끝점 집합의 변경이 불가능한 ID 번호입니다.
- serviceArea - 이 요소가 속하는 서비스 영역은 Common, Exchange, SharePoint 또는 Skype입니다.
- url - 끝점 집합에 대한 URL입니다. DNS 레코드의 JSON 배열입니다. 비워 두면 생략됩니다.
- tcpPorts - 끝점 집합에 대한 TCP 포트입니다. 모든 포트 요소는 쉼표로 구분된 포트 목록 또는 대시 문자(-)로 구분된 포트 범위로 서식이 지정됩니다. 포트는 해당 범주에 대한 해당 끝점 집합에 있는 모든 IP 주소 및 모든 URL에 적용됩니다. 비워 두면 생략됩니다.
- udpPorts - 이 끝점 집합의 IP 주소 범위에 대한 UDP 포트입니다. 비워 두면 생략됩니다.
- ips - 나열된 TCP 또는 UDP 포트와 연결된 이 끝점 집합과 연결된 IP 주소 범위입니다. IP 주소 범위의 JSON 배열입니다. 비워 두면 생략됩니다.
- category - 끝점 집합에 대한 연결 범주입니다. 유효한 값은 Optimize, Allow 및 Default입니다. 필수 항목입니다.
- expressRoute - 이 끝점 집합이 ExpressRoute를 통해 라우팅되는 경우 True 또는 False입니다.
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
...
```

추가 끝점 집합이 이 예제에는 포함되어 있지 않습니다.

예제 2 요청 URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

이 예제에서는 Exchange Online에 대한 Office 365 Worldwide 인스턴스의 끝점과 종속성만 가져옵니다.

예제 2의 출력은 결과에 SharePoint Online 또는 비즈니스용 Skype Online에 대한 끝점이 포함되지 않는다는 점을 제외하고 예제 1과 비슷합니다.

## <a name="changes-web-method"></a>변경 웹 메서드

변경 웹 메서드는 게시된 가장 최근 업데이트를 반환합니다. 일반적으로는 IP 주소 범위 및 URL에 대한 이전 달 변경 내용에 해당합니다. 처리할 가장 중요한 변경 내용은 방화벽 액세스 제어 목록에 IP 주소를 추가하지 못하기 때문에 새 URL 또는 IP 주소가 추가되는 경우 또는 프록시 서버 우회 목록에 대한 URL로 인해 해당 네트워크 장치 내부에서 Office 365 사용자의 작동이 중단될 수 있는 경우입니다. 운영 요구 사항에도 불구하고 이러한 중단이 발생하기 30일 전 알림에 _Add_ 작업이 추가됩니다.

변경 내용 웹 메서드에 대한 매개 변수입니다.

- **Version** - 필수 URL 경로 매개 변수입니다. 현재 구현했으며 해당 버전 이후의 변경 내용을 확인하려는 버전입니다. 형식은 _YYYYMMDDNN_입니다.

변경 웹 메서드의 결과는 각 레코드가 특정 끝점 버전의 변경을 나타내는 레코드 배열입니다. 각 레코드에 대한 요소는 다음과 같습니다.

- id - 변경 레코드의 변경이 불가능한 ID입니다.
- endpointSetId - 변경된 끝점 집합 레코드의 ID입니다. 필수 항목입니다.
- disposition - change, add 또는 remove일 수 있으며, 끝점 집합 레코드에 대해 수행된 변경을 설명합니다. 필수 항목입니다.
- version - 변경이 도입된 게시된 끝점 집합의 버전입니다. 버전 번호는 _YYYYMMDDNN_ 형식입니다. 여기서 NN은 하루 동안 게시되어야 하는 버전이 여러 개인 경우에 증가되는 자연수입니다.
- previous - 끝점 집합에서 변경된 요소의 이전 값을 자세히 설명하는 하위 구조입니다. 새로 추가된 끝점 집합에는 포함되지 않습니다. tcpPorts, udpPorts, ExpressRoute, category, required, notes가 포함됩니다.
- current - 끝점 집합에서 변경 요소의 업데이트된 값을 자세히 설명하는 하위 구조입니다. tcpPorts, udpPorts, ExpressRoute, category, required, notes가 포함됩니다.
- add - 끝점 집합 컬렉션에 추가할 항목을 자세히 설명하는 하위 구조입니다. 추가할 항목이 없으면 생략합니다.
  - effectiveDate - 서비스에서 추가가 적용될 날짜를 정의합니다.
  - ips - ips 배열에 추가할 항목입니다.
  - url - url 배열에 추가할 항목입니다.
- remove - 끝점 집합에서 제거할 항목을 자세히 설명하는 하위 구조입니다. 제거할 항목이 없으면 생략합니다.
  - ips- ips 배열에서 제거할 항목입니다.
  - url - url 배열에서 제거할 항목입니다.

### <a name="examples"></a>**예제:**

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
...
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

## <a name="example-powershell-script"></a>**예제 PowerShell 스크립트**

다음은 업데이트된 데이터에 대해 수행해야 하는 작업이 있는지 확인하기 위해 실행할 수 있는 PowerShell 스크립트입니다. 이 스크립트는 Office 365 Worldwide 인스턴스 끝점에 대한 버전 번호를 확인합니다. 변경 내용이 있는 경우 끝점을 다운로드하고 &quot;Allow&quot; 및 &quot;Optimize&quot; 범주 끝점을 필터링합니다. 또한 여러 호출에서 고유한 ClientRequestId를 사용하고 찾은 최신 버전을 임시 파일에 저장합니다. 이 스크립트를 1시간에 1회 호출하여 버전 업데이트를 확인해야 합니다.

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
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>**예제 Python 스크립트**

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

## <a name="web-service-interface-versioning"></a>**웹 서비스 인터페이스 버전 관리**

앞으로 이러한 웹 서비스 메서드의 매개 변수 또는 결과를 업데이트해야 할 수 있습니다. 이러한 웹 서비스의 일반 공급 버전이 게시된 후에 Microsoft는 웹 서비스에 대한 자료 업데이트 정보를 미리 알리기 위해 적절한 조치를 취할 것입니다. Microsoft에서 업데이트를 위해 웹 서비스를 사용하여 클라이언트를 변경해야 한다고 판단할 경우 웹 서비스의 이전 버전(하나 이전 버전)을 새 버전이 릴리스되고 12개월 이상 동안 사용할 수 있게 지원할 것입니다. 이 기간 동안 업그레이드하지 않는 고객은 웹 서비스 및 해당 메서드에 액세스하지 못할 수 있습니다. 고객은 웹 서비스 인터페이스 서명이 다음과 같이 변경될 경우 웹 서비스 클라이언트가 계속 작동되도록 해야 합니다.

- 이전 클라이언트가 제공할 필요가 없으며 이전 클라이언트가 수신하는 결과에 영향을 미치지 않는 새로운 선택적 매개 변수를 기존 웹 메서드에 추가
- 응답 REST 항목 또는 추가 열 중 하나에 있는 새로운 명명된 특성을 응답 CSV 에 추가
- 이전 클라이언트에서 호출하지 않는 새 이름의 새 웹 메서드 추가

## <a name="related-topics"></a>관련 항목
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md)

[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)

[Office 365에 대한 네트워크 연결](network-connectivity.md)
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)
  
[Office 365용 ExpressRoute 구현](implementing-expressroute.md)
  
[Office 365용 ExpressRoute 시나리오에서 BGP 커뮤니티 사용(미리 보기)](bgp-communities-in-expressroute.md)
  
[비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[비즈니스용 Skype Online의 네트워크 최적화](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[비즈니스용 Skype Online의 ExpressRoute 및 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute를 사용하는 호출 흐름](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
