---
title: 콘텐츠 배달 네트워크
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/22/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: 이 정보를 사용 하 여 Office 365에서 CDNs (콘텐츠 배달 네트워크)를 사용 하 여 성능을 개선 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 7b9ef7a3742dbbccbc052eca28469c4fb10cdae1
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029122"
---
# <a name="content-delivery-networks-cdns"></a>CDNs (콘텐츠 배달 네트워크)

CDNs 도움말은 최종 사용자가 Office 365을 빠르고 안정적으로 유지 합니다. Office 365와 같은 클라우드 서비스를 사용 하 여 정적 자산을 다운로드 속도를 빠르게 처리 하 고 인식 된 최종 사용자 대기 시간을 단축 하기 위해 브라우저에 좀 더 가깝게 고정 에셋을 캐시 합니다. 이 항목의 정보는 CDNs (콘텐츠 배달 네트워크) 및 Office 365에서 사용 하는 방법을 파악 하는 데 도움이 됩니다.

## <a name="what-exactly-is-a-cdn"></a>CDN은 정확히 어떤 것 입니까?

CDN은 고속 백본 네트워크로 연결 된 데이터 센터의 프록시 및 파일 서버로 구성 되는 지리적으로 분산 된 네트워크입니다. CDNs는 웹 사이트 또는 서비스의 지정 된 파일 및 개체 집합에 대 한 대기 시간 및 로드 시간을 줄이는 데 사용 됩니다. CDN에는 임의의 위치에서 들어오는 요청의 서비스를 최적으로 처리 하기 위한 수천 개의 끝점이 있을 수 있습니다.

CDNs는 일반적으로 javascript 파일, 아이콘 및 이미지 등의 웹 사이트 또는 서비스에 대 한 일반 콘텐츠의 신속한 다운로드를 제공 하는 데 사용 되며, SharePoint Online 문서 라이브러리의 파일, 스트리밍 미디어 파일 등의 사용자 콘텐츠에 대 한 개인 액세스를 제공할 수도 있습니다. 및 사용자 지정 코드

CDNs는 대부분의 엔터프라이즈 클라우드 서비스에서 사용 됩니다. Office 365와 같은 클라우드 서비스에서는 수백만 명의 고객이 전자 메일 등의 독점 콘텐츠 및 아이콘 등의 일반 콘텐츠를 한 번에 다운로드할 수 있습니다. 이미지를 모든 사용자가 아이콘 처럼 사용 가능한 한 더 가까이 배치 하는 것이 보다 효율적입니다. 모든 클라우드 서비스가 모든 대도시 영역에이 일반 콘텐츠를 저장 하는 CDN 데이터 센터를 구축 하거나 전 세계 모든 주요 인터넷 허브에도 해당 되지 않으므로, 이러한 CDNs 중 일부를 공유 하는 것은 실용적이 지 않습니다.

## <a name="how-do-cdns-make-services-work-faster"></a>CDNs에서 서비스가 더 빠르게 작동 하도록 설정 하는 방법은 무엇 인가요?

나중에 사이트 이미지 및 아이콘과 같은 공통 개체를 다운로드 하면 전자 메일 또는 문서와 같은 중요 한 개인 콘텐츠를 다운로드 하는 데 더 적합 한 네트워크 대역폭이 사용 될 수 있습니다. Office 365에서는 CDNs를 포함 하는 아키텍처를 사용 하기 때문에, 서버에서 클라이언트 컴퓨터에 더 가까이에 아이콘, 스크립트 및 기타 일반 콘텐츠를 다운로드 하 여 다운로드 속도를 높일 수 있습니다. 이는 Office 365 데이터 센터에 안전 하 게 저장 되는 개인 콘텐츠에 빠르게 액세스할 수 있음을 의미 합니다.

CDNs는 여러 가지 방법으로 클라우드 서비스 성능을 개선 하는 데 도움이 됩니다.

- CDNs 교대조는 네트워크 및 파일의 다운로드 부담을 클라우드 서비스에서 제외 하 고, 사용자 콘텐츠 및 기타 서비스를 제공 하기 위한 클라우드 서비스 리소스를 해제 하 여 정적 자산에 대 한 요청을 처리 해야 합니다.
- CDNs는 고성능 네트워크 및 파일 서버를 구현 하 고, [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) 와 같은 업데이트 된 네트워크 프로토콜을 고도로 효율적인 압축 및 요청 멀티플렉싱로 활용 하 여 낮은 대기 파일 액세스를 제공 하기 위한 목적으로 작성 되었습니다.
- CDN 네트워크는 많은 전역적으로 분산 된 끝점을 사용 하 여 콘텐츠를 사용자에 게 최대한 가깝게 사용할 수 있도록 합니다.

## <a name="the-office-365-cdn"></a>Office 365 CDN

기본 제공 Office 365 CDN (콘텐츠 배달 네트워크)을 사용 하면 Office 365 관리자가 정적 자산을 요청 하는 브라우저에 더 빠르게 캐싱하여 조직의 SharePoint Online 페이지 성능을 향상 시킬 수 있습니다. 다운로드 하 여 대기 시간을 줄입니다. Office 365 CDN은 압축 및 다운로드 속도 향상을 위해 [HTTP/2 프로토콜](https://en.wikipedia.org/wiki/HTTP/2) 을 사용 합니다.

> [!NOTE]
> Office 365 CDN은 **프로덕션** (전 세계) 클라우드의 테 넌 트에만 사용할 수 있습니다. 미국 정부의 테 넌 트, 중국 및 독일 클라우드가 현재 Office 365 CDN을 지원 하지 않습니다.

Office 365 CDN은 여러 위치, 즉 _출발지_에 정적 자산을 호스트하고 글로벌 고속 네트워크에서 제공할 수 있는 여러 CDN으로 구성됩니다. Office 365 CDN에서 호스팅하려는 콘텐츠의 종류에 따라 **공개** 출처, **비공개** 출처 또는 둘 다를 추가할 수 있습니다.

![Office 365 CDN 개념 다이어그램](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 개념 다이어그램")

Office 365 CDN 내의 **공개** 출처의 콘텐츠는 익명으로 액세스할 수 있으며 호스팅 된 자산에 대한 URL을 지닌 사람이면 누구나 액세스할 수 있습니다. 공개 출처의 콘텐츠에 대한 액세스는 익명이기 때문에 캐시 javascript 파일, 스크립트, 아이콘 및 이미지와 같은 중요하지 않은 일반 콘텐츠에만 사용할 수 있습니다. Office 365 CDN은 기본적으로 공개 출처의 Office 365 클라이언트 응용 프로그램 같은 일반 리소스를 다운로드하는 데 사용됩니다.

Office 365 CDN 내의 **비공개** 원본을 사용 하면 SharePoint Online 문서 라이브러리, 사이트 및 독점적인 이미지 등의 사용자 콘텐츠에 대 한 비공개 액세스를 제공 합니다. 비공개 출처의 콘텐츠에 대한 액세스는 동적으로 생성 된 토큰으로 보호되므로 원본 문서 라이브러리 또는 저장 위치에 대한 사용 권한을 가진 사용자만 액세스할 수 있습니다. Office 365 CDN의 비공개 출처는 SharePoint Online 콘텐츠에만 사용할 수 있으며 SharePoint Online 테넌트의 리디렉션을 통해 자산에만 액세스할 수 있습니다.

Office 365 CDN 서비스는 SharePoint Online 구독의 일부로 포함되어 있습니다.

Office 365 CDN을 사용 하는 방법에 대 한 자세한 내용은 [use The office 365 content delivery network With SharePoint Online](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)을 참조 하세요.

Office 365 CDN 사용에 대 한 개념 및 HOWTO 정보를 제공 하는 일련의 짧은 비디오를 시청 하려면 [SharePoint 개발자 패턴 및 모범 사례 YouTube 채널](https://aka.ms/sppnp-videos)을 방문 하세요.

## <a name="other-microsoft-cdns"></a>기타 Microsoft CDNs

Office 365 CDN에 포함 된 것은 아니지만 office 365 테 넌 트에서 이러한 CDNs를 사용 하 여 SharePoint 개발 라이브러리, 사용자 지정 코드 및 Office 365 CDN의 범위를 벗어난 기타 목적에 액세스할 수 있습니다.

### <a name="azure-cdn"></a>Azure CDN

**AZURE cdn** 을 사용 하 여 사용자 지정 웹 파트, 라이브러리 및 기타 리소스 자산을 호스팅하기 위한 자체 CDN 인스턴스를 배포할 수 있으며,이를 통해 cdn 저장소에 액세스 키를 적용 하 고 cdn 구성을 보다 강력 하 게 제어할 수도 있습니다. Azure CDN 사용은 무료이 아니며 Azure 구독이 필요 합니다.

Azure CDN 인스턴스를 구성 하는 방법에 대 한 자세한 내용은 [퀵 스타트: AZURE cdn과 azure storage 계정 통합](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn)을 참조 하세요.

Azure CDN을 사용 하 여 SharePoint 웹 파트를 호스팅하는 방법에 대 한 예제를 보려면 [sharepoint 클라이언트 쪽 웹 파트를 AZURE CDN에 배포](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn)를 참조 하세요.

Azure CDN PowerShell 모듈에 대 한 자세한 내용은 [PowerShell을 사용 하 여 AZURE Cdn 관리](https://docs.microsoft.com/azure/cdn/cdn-manage-powershell)를 참조 하세요.

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

Microsoft의 **AJAX CDN** 은 jQuery (및 다른 모든 라이브러리), ASP.NET Ajax, 부트스트랩, 녹아웃 .js 등을 비롯 한 다양 한 인기 개발 라이브러리를 제공 하는 읽기 전용 CDN입니다.
  
이러한 스크립트를 프로젝트에 포함 하려면 해당 라이브러리에 대 한 참조를 프로젝트 자체에 포함 하지 말고 CDN 주소에 대 한 참조로 대체 하기만 하면 됩니다. 예를 들어 다음 코드를 사용 하 여 jQuery에 연결 합니다.

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Microsoft Ajax CDN을 사용 하는 방법에 대 한 자세한 내용은 [Microsoft AJAX cdn](https://docs.microsoft.com/aspnet/ajax/cdn/overview)를 참조 하세요.

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Office 365에서 CDN의 콘텐츠를 사용 하는 방법

Office 365 테 넌 트에 대해 구성 하는 CDN에 관계 없이 기본 데이터 검색 프로세스는 동일 합니다.

1. 클라이언트 (브라우저 또는 Office 클라이언트 응용 프로그램)가 Office 365에서 데이터를 요청 합니다.

2. Office 365에서 클라이언트에 직접 데이터를 반환 하거나, 데이터가 CDN에 의해 호스트 되는 콘텐츠 집합의 일부인 경우 클라이언트를 CDN URL로 리디렉션합니다.

    a. 데이터가 이미 _공용_ 원점에 캐시 된 경우 클라이언트는 가장 가까운 CDN 위치에서 클라이언트로 직접 데이터를 다운로드 합니다.

    b. 데이터가 이미 _개인_ 원점에 캐시 되어 있는 경우 CDN 서비스는 원본에 대 한 Office 365 사용자 계정의 사용 권한을 확인 합니다. 사용 권한이 있는 경우 SharePoint Online은 CDN의 자산 경로 및 두 액세스 토큰으로 구성 된 사용자 지정 URL을 동적으로 생성 하 고 사용자 지정 URL을 클라이언트에 게 반환 합니다. 그러면 클라이언트는 사용자 지정 URL을 사용 하 여 가장 가까운 CDN 위치에서 클라이언트에 직접 데이터를 다운로드 합니다.

3. 데이터가 CDN에서 캐시 되지 않으면 CDN 노드가 Office 365에서 데이터를 요청 하 고 클라이언트에서 데이터를 다운로드 한 후 일정 시간 동안 데이터를 캐시 합니다.

CDN은 가장 가까운 데이터 센터를 사용자의 브라우저에 출력 하 고 리디렉션을 사용 하 여 요청 된 데이터를 다운로드 합니다. CDN 리디렉션은 빠르게 실행 되며 사용자가 다운로드 시간을 많이 절약할 수 있습니다.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>CDNs가 Office 365에서 가장 잘 작동 하도록 네트워크를 설정 하려면 어떻게 해야 하나요?

네트워크에서 클라이언트 간의 대기 시간을 최소화 하는 것은 최적의 성능을 보장 하기 위한 주요 고려 사항입니다. [Office 365 끝점 관리](managing-office-365-endpoints.md) 에서 설명 하는 최상의 방법을 사용 하 여 불필요 한 대기 시간이 발생 하지 않도록 네트워크 구성을 통해 클라이언트 브라우저가 중앙 프록시를 통해 cdn 트래픽을 라우팅하는 대신 cdn에 직접 액세스할 수 있도록 허용 합니다.

Office [365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 을 읽어 office 365 네트워크 성능 최적화의 개념을 파악할 수도 있습니다.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Office 365에서 사용 하는 모든 CDNs의 목록이 있는지 여부

Office 365에서 사용 하는 CDNs는 항상 변경 될 수 있으며, 대부분의 경우 이벤트 1에 구성 된 CDN 파트너가 여러 개 있을 수 있습니다. Office 365에서 사용 하는 기본 CDNs는 다음과 같습니다.

|CDN  |Company  |Usage  |링크  |
|---------|---------|---------|---------|
|Office 365 CDN     |Akamai         |공개 원본의 일반 자산, 개인 원본에 있는 SharePoint 사용자 콘텐츠         |[SharePoint Online에서 Office 365 콘텐츠 배달 네트워크 사용](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)         |
|Azure CDN     |Microsoft         |사용자 지정 코드, SharePoint Framework 솔루션         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN (읽기 전용)     |Microsoft         |Ajax, jQuery, ASP.NET, 부트스트랩, 녹아웃 .js 등의 공용 라이브러리         |[Microsoft Ajax CDN](https://docs.microsoft.com/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>CDN에서 제공 하는 성능 향상은 무엇 인가요?

Office 365에서 직접 다운로드 한 데이터와 특정 CDN에서 다운로드 한 데이터 (예: 테 넌 트에 대 한 위치, 가장 가까운 CDN 끝점, 수) 간의 특정 성능 차이를 측정 하는 데 관련 된 몇 가지 요인이 있습니다. CDN에서 처리 되는 페이지의 자산과 네트워크 대기 시간 및 대역폭에 대 한 일시적인 변경 그러나 간단한 A/B 테스트를 통해 특정 파일의 다운로드 시간 차이를 표시할 수 있습니다.

다음 스크린샷은 Office 365의 원시 파일 위치와 [Microsoft Ajax 콘텐츠 배달 네트워크](https://docs.microsoft.com/aspnet/ajax/cdn/overview)에서 호스트 되는 파일 간의 다운로드 속도 차이를 보여 줍니다. 이러한 스크린샷은 Internet Explorer 11 개발자 도구의 **네트워크** 탭에서 가져온 것입니다. 이러한 스크린샷은 인기 라이브러리 jQuery의 대기 시간을 보여 줍니다. 이 화면을 가져오려면 Internet Explorer에서 **F12** 키를 누르고 wi-fi 아이콘과 함께 인식 되는 기호에 해당 하는 **네트워크** 탭을 선택 합니다.
  
![F12 네트워크의 스크린샷](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
이 스크린샷은 SharePoint Online 사이트의 마스터 페이지 갤러리에 업로드 된 라이브러리를 보여 줍니다. 라이브러리를 업로드 하는 데 걸리는 시간은 1.51 초입니다.
  
![1.51초의 로드 시간을 보여 주는 스크린샷](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
두 번째 스크린샷에서는 Microsoft의 CDN에서 제공 되는 것과 동일한 파일을 보여 줍니다. 이번에는 대기 시간이 약 496 밀리초입니다. 이는 크게 개선 된 기능이 며, 개체를 다운로드 하는 데 걸리는 총 시간을 shaved 합니다.
  
![469밀리초의 로드 시간을 보여 주는 스크린샷](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>데이터를 안전 하 게 보호 하나요?

비즈니스를 실행 하는 데이터를 보호 하는 데는 세심 한 주의가 필요 합니다. Office 365 CDN에 저장 된 데이터는 전송 및 휴지에서 모두 암호화 되며 office 365 SharePoint CDN의 데이터에 대 한 액세스는 Office 365 사용자 권한 및 토큰 인증을 통해 보호 됩니다. Office 365 SharePoint CDN의 데이터 요청은 Office 365 테 넌 트에서 참조 (리디렉션) 해야 하며, 그렇지 않으면 인증 토큰이 생성 되지 않습니다.

데이터가 안전 하 게 유지 되도록 하려면 공용 CDN에 사용자 콘텐츠나 기타 중요 한 데이터를 저장 하지 않는 것이 좋습니다. 공용 CDN의 데이터에 대 한 액세스는 익명 이므로 공용 CDNs는 웹 스크립트 파일, 아이콘, 이미지 및 기타 중요 하지 않은 자산과 같은 일반 콘텐츠를 호스트 하는 경우에만 사용 해야 합니다.

> [!NOTE]
> 타사 CDN 공급자는 Office 365 보안 센터에서 설명 하는 약정 수준과는 다른 개인 정보 보호 및 준수 표준을 포함할 수 있습니다. CDN 서비스를 통해 캐시 된 데이터는 Microsoft DPT (데이터 처리 조건)를 준수 하지 않을 수 있으며 Office 365 보안 센터 규정 준수 경계를 벗어날 수 있습니다.

Office 365 CDN 공급자에 대 한 개인 정보 및 데이터 보호에 대 한 자세한 내용을 보려면 다음을 방문 하세요.  

- [Microsoft 보안 센터](https://www.microsoft.com/trustcenter) 의 Office 365 개인 정보 및 데이터 보호에 대 한 자세한 정보
- [Akamai 개인](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp) 정보 보호 센터에서 akamai의 개인 정보 취급 방침 및 데이터 보호법 자세히 알아보기
- Azure [보안 센터](https://azure.microsoft.com/overview/trusted-cloud/) 의 azure 개인정보 취급 방침 및 데이터 보호에 대해 자세히 알아보기

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>이러한 모든 타사 서비스를 사용 하 여 네트워크를 보호 하려면 어떻게 해야 하나요?

광범위 한 파트너 서비스 집합을 사용 하면 Office 365에서 가용성 요구 사항을 확장 및 충족할 수 있을 뿐만 아니라 Office 365을 사용할 때의 사용자 환경도 향상 됩니다. 타사 서비스 Office 365 활용에는 인증서 해지 목록 두 가지가 모두 포함 됩니다. crl.microsoft.com, sa.symcb.com 및 CDNs와 같이 합니다. (예: r3.res.outlook.com) Office 365에서 생성 되는 모든 CDN FQDN은 Office 365에 대 한 사용자 지정 FQDN입니다. Office 365 요청의 FQDN으로 보낸 경우 CDN 공급자가 해당 위치의 FQDN과 기본 콘텐츠를 제어할 수 있습니다.
  
Microsoft 또는 Office 365 데이터 센터에 대해 전송 되는 요청을 타사에 게 전송 되는 요청으로 분리 하려는 고객은 [Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)에 대 한 지침을 작성 해야 합니다.

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>CDNs를 활용 하는 모든 Fqdn의 목록이 있는지 여부

Fqdn 목록과 시간에 따른 CDNs 변경을 활용 하는 방법을 설명 합니다. , 게시 된 [Office 365 url 및 IP 주소 범위](https://go.microsoft.com/fwlink/p/?LinkID=293744) 페이지를 참조 하 여 cdns를 활용 하는 최신 fqdn을 최신으로 확인 하세요.

또한 [office 365 IP 주소 및 URL 웹 서비스](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service) 를 사용 하 여 현재 Office 365 URL 및 CSV 또는 JSON 형식의 IP 주소 범위를 요청할 수 있습니다.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>자체 CDN을 사용 하 고 로컬 네트워크에서 콘텐츠를 캐싱할 수 있나요?

Microsoft는 고객의 요구를 지원 하기 위한 새로운 방법을 지속적으로 찾고 있으며 현재 캐싱 프록시 솔루션 및 기타 온-프레미스 CDN 솔루션 사용을 조사 하 고 있습니다.

Office 365 CDN에 포함 된 것은 아니지만 **AZURE cdn** 을 사용 하 여 사용자 지정 웹 파트, 라이브러리 및 기타 리소스 자산을 호스팅할 수 있으며,이를 통해 cdn 저장소에 액세스 키를 적용 하 고 cdn 구성 보다 더 강력 하 게 제어할 수도 있습니다. Azure CDN 사용은 무료이 아니며 Azure 구독이 필요 합니다. Azure CDN 인스턴스를 구성 하는 방법에 대 한 자세한 내용은 [퀵 스타트: AZURE cdn과 azure storage 계정 통합](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn)을 참조 하세요.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Office 365에 대 한 Azure Express 경로를 사용 하 고 있습니까?

[Office 365에 대 한 Azure express](azure-expressroute.md) 를 통해 공용 인터넷에서 분리 된 office 365 인프라에 전용으로 연결할 수 있습니다. 즉, 클라이언트는 대신 express에서 지 원하는 서비스 목록에 명시적으로 포함 되지 않은 CDNs 및 기타 Microsoft 인프라에 연결 하기 위해 비-비트 연결을 통해 연결 해야 합니다. CDNs를 대상으로 하는 요청 같은 특정 트래픽을 라우팅하는 방법에 대 한 자세한 내용은 [Office 365 네트워크 트래픽 관리](routing-with-expressroute.md)를 참조 하세요.

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>온-프레미스에서 SharePoint Server에 CDNs를 사용할 수 있나요?

CDNs를 사용 하는 것은 SharePoint Online 컨텍스트에서 적합 하며 SharePoint Server에서는 피해 야 합니다. 이는 서버가 온-프레미스 또는 지리적으로 가까이 있는 경우 지리적 위치에 대 한 모든 이점이 true를 유지 하지 않기 때문입니다. 또한 서버가 호스트 되는 서버에 대 한 네트워크 연결이 있는 경우 인터넷에 연결 하지 않고 사이트를 사용할 수 있으므로 CDN 파일을 검색할 수 없습니다. 그렇지 않은 경우에는 사이트에 필요한 라이브러리 및 파일에 대해 사용 가능한 안정적인 경우 CDN을 사용 해야 합니다.
  
다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>참고 항목

[Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples)

[Office 365 네트워크 연결 평가](assessing-network-connectivity.md) 

[Office 365 끝점 관리](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints)

[Office 365 URL 및 IP 주소 범위](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[SharePoint Online에서 Office 365 콘텐츠 배달 네트워크 사용](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft 보안 센터](https://www.microsoft.com/trustcenter)

[Office 365 성능 조정](tune-office-365-performance.md)
