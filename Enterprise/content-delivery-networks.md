---
title: 콘텐츠 배달 네트워크
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
ms.audience: ITPro
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
description: 이 정보를 사용 하 여 cdns (콘텐츠 배달 네트워크) 및 Office 365에서이를 활용 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636099"
---
# <a name="content-delivery-networks"></a>콘텐츠 배달 네트워크

이 항목의 정보는 cdns (콘텐츠 배달 네트워크) 및 Office 365에서 사용 하는 방법을 파악 하는 데 도움이 됩니다.

cdns 도움말은 최종 사용자가 Office 365을 빠르고 안정적으로 유지 합니다. Office 365와 같은 클라우드 서비스는 다운로드 속도를 빠르게 하 고 대기 시간을 줄이기 위해 정적 자산을 브라우저에 더 가깝게 캐시 하려면 cdns를 사용 합니다. 공용 cdns를 사용 하면 javascript 파일, 아이콘 및 이미지 같은 일반 콘텐츠의 빠른 다운로드를 허용 하 고, 개인용 cdns는 비디오 및 SharePoint Online 문서 라이브러리와 같은 사용자 콘텐츠에 빠르게 액세스할 수 있는 안전한 액세스를 제공 합니다.
  
 **머리글을 다시** [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)
  
## <a name="what-exactly-is-a-cdn"></a>CDN은 정확히 어떤 것 입니까?

cdns는 대부분의 엔터프라이즈 클라우드 서비스에서 사용 됩니다. Office 365와 같은 클라우드 서비스에서는 수백만 명의 고객이 전자 메일 등의 독점 콘텐츠 및 아이콘 등의 일반 콘텐츠를 한 번에 다운로드할 수 있습니다. 이미지를 모든 사용자가 아이콘 처럼 사용 가능한 한 더 가까이 배치 하는 것이 보다 효율적입니다. 그러나이는 모든 클라우드 서비스가 모든 대도시 영역에이 일반 콘텐츠를 저장 하는 CDN 데이터 센터를 구축 하거나 전 세계 모든 주요 인터넷 허브에도 이상적이 지 않으므로 이러한 cdns 중 일부는 공유 됩니다.
  
cdns는 전용 또는 공용 일 수 있습니다. 사설 cdns는 단일 회사에서 소유 하 고 운영 하며 해당 회사의 응용 프로그램 및 서비스 에서만 사용할 수 있습니다. 공용 cdns는 여러 회사에 대 한 사용량을 임대 하는 회사에서 실행 됩니다. 찾은 위치에 따라 office 365가 소유 하 고 실행 하는 CDN, 공용 CDN 또는 두 가지 조합에서 사용자의 일반 이미지를 다운로드 하는 것이 가장 효율적일 수 있습니다. 사용 되는 CDN 유형에 관계 없이 데이터를 검색 하는 단계는 동일 합니다.
  
1. 클라이언트가 Office 365의 데이터를 요청 합니다.

2. Office 365에서는 데이터를 클라이언트로 직접 반환 하거나 클라이언트에 CDN으로 지시 합니다.

3. 데이터가 CDN에서 이미 캐시 된 경우 클라이언트는 인터넷에서 클라이언트에 가장 가까운 CDN 위치에서 해당 데이터를 직접 다운로드 합니다.

4. 데이터가 cdn에서 캐시 되지 않으면 cdn 노드가 Office 365에서 데이터를 요청 하 고 클라이언트에서 데이터를 다운로드 한 후 일정 시간 동안 데이터를 캐시 합니다.

cdns는 가장 가까운 Office 365 데이터 센터에서 파일 및 이미지를 가져오고 차례로 차례로 클라이언트에서 가장 가까운 CDN에서 파일과 이미지를 가져옵니다. 사용자가 Outlook Web App에서 전자 메일을 읽고 같은 클라우드 서비스에 액세스 하는 경우 사용자의 브라우저에서 Office 365 데이터 센터의 파일과 이미지를 검색 하려고 합니다. 파일을 배달 하는 데 소요 되는 시간과 대역폭을 소비 하는 대신 Office 365에서 CDN으로 브라우저를 리디렉션합니다. CDN은 가장 가까운 데이터 센터를 사용자의 브라우저에 출력 하 고 리디렉션을 사용 하 여 원본 이미지를 다운로드 합니다. 이 CDN 리디렉션은 빠르게 사용할 수 있으며 사용자가 다운로드 시간을 많이 절약 합니다.

## <a name="how-do-cdns-make-services-work-faster"></a>cdns에서 서비스가 더 빠르게 작동 하도록 설정 하는 방법은 무엇 인가요?

아이콘과 같은 일반적인 항목을 다운로드 하는 경우에는 전자 메일 이나 문서 같은 중요 한 개인 콘텐츠를 다운로드 하는 데 더 효율적으로 사용할 수 있는 네트워크 대역폭을 차지할 수 있습니다. Office 365에서는 cdns를 포함 하는 아키텍처를 사용 하기 때문에, 서버에서 클라이언트 컴퓨터에 더 가까이에 아이콘, 스크립트 및 기타 일반 콘텐츠를 다운로드 하 여 다운로드 속도를 높일 수 있습니다. 이는 Office 365 데이터 센터에 안전 하 게 저장 되는 개인 콘텐츠에 빠르게 액세스할 수 있음을 의미 합니다.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>cdns가 Office 365에서 가장 잘 작동 하도록 네트워크를 설정 하려면 어떻게 해야 하나요?

[Office 365에 대 한 네트워크 연결](network-connectivity.md)을 계획 하는 경우에는 cdns가 일반적으로 작동 하는 방식과 CDN 네트워크 트래픽을 관리 하는 방법을 이해 하는 것이 좋습니다.

Office 365 테 넌 트에 대해 CDN을 사용 하도록 설정 하는 경우에는 cdn을 통해 배포할 콘텐츠 원본 (cdns 컨텍스트의 **원본** ), 데이터 분류 또는 파일 형식을 제어 하는 정책을 설정 하는 것으로 시작 합니다. 지정 된 콘텐츠에 액세스 하는 사용자는 CDN에서 가장 가까운 파일 위치로 리디렉션됩니다. 따라서 [Office 365 끝점 관리](managing-office-365-endpoints.md) 에서 설명 하는 최상의 방법을 사용 하 여 네트워크 구성에서 중앙 프록시를 통해 cdn 트래픽을 라우팅하는 것이 아니라 클라이언트 브라우저가 cdn에 직접 액세스할 수 있도록 허용 하는 것이 좋습니다. 불필요 한 대기 시간을 소개 합니다.

## <a name="is-my-data-safe"></a>데이터를 안전 하 게 보호 하나요?

비즈니스를 실행 하는 데이터를 보호 하는 데 도움이 되는 정보를 제공 합니다. cdns에 저장 된 고객 관련 데이터는 전송 및 휴지에서 모두 암호화 됩니다.

> [!NOTE]
> CDN 공급자에는 Office 365 보안 센터에서 설명 하는 것과는 다른 개인 정보 보호 및 준수 표준이 포함 될 수 있습니다. CDN 서비스를 통해 캐시 된 데이터는 Microsoft DPT (데이터 처리 조건)를 준수 하지 않을 수 있으며 Office 365 보안 센터 규정 준수 경계를 벗어날 수 있습니다.

Office 365 CDN 공급자에 대 한 개인 정보 및 데이터 보호에 대 한 자세한 내용을 보려면 다음을 방문 하세요.  

+ [Microsoft 보안 센터](https://www.microsoft.com/trustcenter) 의 Office 365 개인 정보 및 데이터 보호에 대 한 자세한 정보
+ azure [보안 센터](https://azure.microsoft.com/en-us/overview/trusted-cloud/) 의 azure 개인정보 취급 방침 및 데이터 보호에 대해 자세히 알아보기
+ [akamai 개인](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp) 정보 보호 센터에서 akamai의 개인 정보 취급 방침 및 데이터 보호법 자세히 알아보기

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>이러한 모든 타사 서비스를 사용 하 여 네트워크를 보호 하려면 어떻게 해야 하나요?

광범위 한 파트너 서비스 집합을 사용 하면 office 365에서 가용성 요구 사항을 확장 및 충족할 수 있을 뿐만 아니라 office 365을 사용할 때의 사용자 환경도 향상 됩니다. 타사 서비스 Office 365 활용에는 인증서 해지 목록 두 가지가 모두 포함 됩니다. crl.microsoft.com, sa.symcb.com 및 cdns와 같이 합니다. (예: r3.res.outlook.com) 모든 CDN FQDN office 365는 office 365에 대 한 사용자 지정 FQDN을 사용 합니다. Office 365 요청의 fqdn으로 보낸 경우 CDN 공급자가 해당 위치의 fqdn과 기본 콘텐츠를 제어할 수 있습니다.
  
Microsoft 또는 office 365 데이터 센터에 대해 전송 되는 요청을 타사에 게 전송 되는 요청으로 분리 하려는 고객의 경우 [Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)에 대 한 지침이 작성 되었습니다.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Office 365에서 사용 하는 모든 cdns의 목록이 있는지 여부

Office 365에서 사용 하는 cdns는 항상 변경 될 수 있으며, 대부분의 경우 이벤트 1에 구성 된 CDN 파트너가 여러 개 있을 수 있습니다. 사용 중인 기본 cdns는 다음과 같습니다.

+ [Office 365 (특히 SharePoint Online 콘텐츠 용)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Akamai](https://www.akamai.com/us/en/cdn.jsp)

이러한 CDN 솔루션은 전 세계 보다 더 많은 코너까지 서비스의 범위를 향상 시킬 수 있습니다. 여기에 저장 되는 콘텐츠는 일반적인 Office 365 스크립트, 파일 및 이미지를 포함 합니다. 예를 들어 portal.office.com에 로그온 할 때 가장 가까운 CDN에서 이미지를 끌어 페이지 로드 시간을 단축할 수 있습니다. 다른 예로는 office 365 ProPlus에는 CDN에 설치 비트를 저장 하 여 최신 버전을 다운로드 하는 데 걸리는 시간을 단축 하는 것이 있습니다.

또한 cdns에 저장 되는 일부 독점 콘텐츠 (예: Office 365 용 비디오 파일)도 있습니다. 비디오를 업로드 한 후에는 파일이 암호화 된 다음 Azure Media Services를 사용 하 여 암호화 된 형식으로 저장 됩니다. Office 365 비디오 플레이어가 비디오를 검색 하는 경우 비디오를 다운로드 하는 데 걸리는 시간을 단축 하기 위해 다운로드 하기 전에 가장 가까운 CDN에 캐시 됩니다.

office 365 CDN을 사용 하는 방법에 대 한 자세한 내용은 [use the office 365 content delivery network with SharePoint Online](use-office-365-cdn-with-spo.md)을 참조 하세요.

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>cdns를 활용 하는 모든 fqdn의 목록이 있는지 여부

fqdn 목록은 시간에 따른 cdns 변경을 활용 하는 방법 이며, 게시 된 [Office 365 url 및 IP 주소 범위](https://go.microsoft.com/fwlink/p/?LinkID=293744) 페이지를 참조 하 여 cdns를 활용 하는 최신 fqdn을 최신 상태로 가져옵니다.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>자체 CDN을 사용 하 고 로컬 네트워크에서 콘텐츠를 캐싱할 수 있나요?

microsoft는 고객의 요구를 지원 하기 위한 새로운 방법을 지속적으로 찾고 있으며 현재 캐싱 프록시 솔루션 및 기타 온-프레미스 CDN 솔루션 사용을 조사 하 고 있습니다.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Office 365에 대 한 Azure express 경로를 사용 하 고 있습니까?

[office 365에 대 한 Azure express](azure-expressroute.md) 를 통해 공용 인터넷에서 분리 된 office 365 인프라에 전용으로 연결할 수 있습니다. 즉, 클라이언트는 대신 express에서 지 원하는 서비스 목록에 명시적으로 포함 되지 않은 cdns 및 기타 Microsoft 인프라에 연결 하기 위해 비-비트 연결을 통해 연결 해야 합니다. cdns를 대상으로 하는 요청 같은 특정 트래픽을 라우팅하는 방법에 대 한 자세한 내용은 [Office 365 네트워크 트래픽 관리](routing-with-expressroute.md)를 참조 하세요.
  
다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>참고 항목

[Office 365 끝점 관리](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[Office 365 URL 및 IP 주소 범위](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[SharePoint Online에서 Office 365 콘텐츠 배달 네트워크 사용](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft 보안 센터](https://www.microsoft.com/trustcenter)