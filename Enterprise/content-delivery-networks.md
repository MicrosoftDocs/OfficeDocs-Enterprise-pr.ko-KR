---
title: 콘텐츠 배달 네트워크
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
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
description: 이 정보를 사용 하 여 콘텐츠 배달 네트워크 (Cdn) 및 어떻게 Office 365 사용 되는지에 대해 설명 합니다. Cdn 최종 사용자를 위한 Office 365 빠르고 안정적을 유지 하는데 도움이 됩니다. Cdn와 Office 365 같은 클라우드 서비스 웹 클라이언트를 통해 서비스를 사용 하 여 때 사용자의 브라우저에 아이콘, 다음과 같은 일반 콘텐츠를 신속 하 게 다운로드 합니다.
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542169"
---
# <a name="content-delivery-networks"></a>콘텐츠 배달 네트워크

이 정보를 사용 하 여 콘텐츠 배달 네트워크 (Cdn) 및 어떻게 Office 365 사용 되는지에 대해 설명 합니다. Cdn 최종 사용자를 위한 Office 365 빠르고 안정적을 유지 하는데 도움이 됩니다. Cdn와 Office 365 같은 클라우드 서비스 웹 클라이언트를 통해 서비스를 사용 하 여 때 사용자의 브라우저에 아이콘, 다음과 같은 일반 콘텐츠를 신속 하 게 다운로드 합니다.
  
 **헤드 돌아가기** [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)합니다.
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>어떻게 해야 합니까 설정 내 네트워크 Office 365에 가장 적합 한 Cdn 있도록?

[Office 365에 대 한 네트워크 연결](network-connectivity.md)을 계획 하는 경우 Cdn 작동 하는 방법을 이해 하는 것이 유용 합니다. 필터링 할 수 없습니다는 Cdn에 대 한 연결 하 여 IP 주소를 이해 하는 것이 중요 이기도 합니다. Exchange Online과 같은 Office 365 내에서 서비스에 대 한 Ip 최상의 작업 목록을 제공 합니다. [끝점을 Office 365를 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)하기 위한 권장 사항에 대해 알아봅니다.
  
## <a name="how-do-cdns-make-services-work-faster"></a>CDN은 어떤 방식으로 서비스 작동 속도를 개선하나요?

아이콘 등의 일반적인 작업을 반복 해 서 다운로드 전자 메일 또는 문서와 같은 중요 한 개인 콘텐츠를 다운로드 하기 위해 더 잘 사용할 수 있는 네트워크 대역폭까지 걸릴 수 있습니다. Office 365 아키텍처를 사용 하기 때문에 Cdn, 아이콘, 스크립트를 포함 하는 및 다운로드를 더 빠르게 되도록 설정 하는 클라이언트 컴퓨터에 더 가깝게 서버에서 다른 일반 콘텐츠를 다운로드할 수 있습니다. 즉, Office 365 데이터 센터에 안전 하 게 저장 된 개인 콘텐츠에 대 한 빠른 액세스 합니다.
  
## <a name="what-exactly-is-a-cdn"></a>CDN이 정확히 무엇인가요?

Cdn은 대부분의 기업 클라우드 서비스에서 사용 됩니다. Office 365 같은 클라우드 서비스 수백만 혼합 독점 콘텐츠 (예: 전자 메일) 및 일반 콘텐츠 (예: 아이콘)을 한번에 다운로드 하는 고객의 경우 이미지 아이콘, 같은 모든 사용자가 사용 가능한 사용자의 컴퓨터에 근접 시키려면 효율적입니다. 아직, 이러한 Cdn 중 일부는 공유 하므로 모든 대도시 영역에서 또는 모든 주요 인터넷 허브는 전세계에이 일반 콘텐츠를 저장 하는 CDN 데이터 센터를 만들려는 모든 클라우드 서비스에 대 한 실제적인 없습니다.
  
Cdn 공용 또는 개인 될 수 있습니다. 개인 Cdn 소유 하 고 단일 회사에서 운영 하 고만 해당 회사의 응용 프로그램 및 서비스 사용할 수 있습니다. 공용 Cdn 여러 회사에 대 한 사용 현황 임대 기업에서 실행 됩니다. 여기서 인 위치에 따라 Office 365가 소유 하는 CDN 및 실행, 공용 CDN 또는 둘의 조합 하면 일반 이미지를 다운로드 하려면 Office 365에 대 한 가장 효율적인 수 있습니다. 어떤 유형의 CDN 사용 하는 것에 관계 없이 데이터를 검색 하는 단계는 동일 합니다.
  
1. Office 365에서 데이터를 요청 하는 클라이언트입니다.

2. Office 365 사용 클라이언트에 직접 데이터를 반환 하거나 CDN 클라이언트에 지시 합니다.

3. CDN에서 데이터가 이미 캐시, 클라이언트는 인터넷에서 클라이언트에 데이터 가장 가까운 CDN 위치에서 직접 다운로드 합니다.

4. CDN에서 데이터 캐시 되지 않습니다 CDN 노드 Office 365에서 데이터를 요청 하 고 클라이언트는 데이터를 다운로드 한 후에 시간 기간에 대 한 데이터의를 캐시 합니다.

Cdn 가져올 파일 및 가장 가까운 Office 365 데이터 센터에서 이미지 및 클라이언트에 가장 가까운 CDN에서 파일 및 이미지를 가져오는 차례로 합니다. 사용자가 Outlook Web App에서 전자 메일을 읽는 것 처럼 클라우드 서비스에 액세스 하는 사용자의 브라우저에서는 Office 365 데이터 센터에서 파일 및 이미지를 검색 하려고 합니다. 시간 및 파일을 제공 하는 대역폭을 소비 하는 대신 Office 365에서 CDN를 브라우저를 리디렉션합니다. CDN은 사용자의 브라우저에 가장 가까운 데이터 센터 파악 하 고 여기에서 일반 이미지를 다운로드 리디렉션을 사용 합니다. 이 CDN 리디렉션을 사용 하 여 빠른, 이며 사용자가 다운로드 시간을 많이 저장 합니다.
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Cdn를 활용 하는 모든 Fqdn 목록이 무엇 인가요?

Fqdn 목록과 이러한 시간이 지남에 따라 Cdn 변경을 활용 하는 방법을 사용해 Cdn를 활용 하는 최신 Fqdn에 최신 맞춘 게시 된 [Office 365 끝점 페이지](https://go.microsoft.com/fwlink/p/?LinkID=293744) 를 참조 하십시오.
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Office 365를 사용 하는 모든 Cdn 목록이 무엇 인가요?

Office 365에서 사용 되 고 있는 Cdn는 항상 하나를 사용할 수 있는 이벤트를 구성 하는 여러 CDN 파트너는 대부분의 경우에서 하 고 변경 될 수 있습니다. 사용 되 고 있는 가장 일반적인 두 Cdn는 [Akamai](https://www.akamai.com/us/en/cdn.jsp) 및 [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)입니다. 이러한 CDN 솔루션 갖추고 광범위 전세계의 더 많은 모서리 방향 서비스의 편의성을 향상 시켜줍니다. 저장 된 콘텐츠를 다음과 같은 일반적인 Office 365 스크립트, 파일 및 이미지를 포함 합니다. 예, portal.office.com에 로그온 할 때 페이지 로드 시간 속도를 가장 가까운 CDN에서 이미지를 가져오는 합니다. 다른 예로 Office 365 ProPlus Office의 최신 버전을 다운로드 하는데 걸리는 시간의 속도 CDN에서 설치 하는 비트를 저장 합니다. Office 365 비디오에 대 한 비디오 파일 등 Cdn에 저장 된 일부 독점 콘텐츠 이기도 합니다. 제공 되는 비디오를 업로드 한 후 파일이 암호화 되 고 Azure 미디어 서비스와 함께 암호화 된 형식으로 저장 됩니다. Office 365 비디오 플레이어 비디오를 검색 하는 경우 비디오를 다운로드 하는데 걸리는 시간 속도를 다운로드 하기 전에 가장 가까운 CDN에 캐시 먼저 됩니다.
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>Office 365 나만의 파일을 위해 사용할 수 있는 CDN 제공 합니까?

예! Office 365 구독에는 SharePoint Online 자산에 대 한 구체적으로 사용할 수 있는 Azure 별도로 CDN를 포함 합니다. Office 365 CDN를 사용 하는 방법에 대 한 자세한 내용은 [SharePoint Online을 사용 하 여 Office 365 콘텐츠 배달 네트워크를 사용 하 여](use-office-365-cdn-with-spo.md)을 참조 하십시오.
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>나만의 CDN 및 캐시 콘텐츠를 사용 하 여 로컬 네트워크 내에 수 있습니까?

고객 요구 사항을 지원 하기 위해 새로운 방법을 계속 해 서 찾고 하 고는 현재 살펴보기 (영문) 프록시 솔루션 및 기타 온-프레미스 CDN 솔루션 캐싱을 사용 합니다.
  
## <a name="is-my-data-safe"></a>데이터가 안전한가요?

비즈니스를 실행 하는 데이터를 보호 하는 것을 보장 하는 매우 주의 했습니다. 콘텐츠 배달 네트워크 파트너에 저장 된 항목을 암호화 합니다. 과 같은 [Office 365 비디오](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)또는 고객에 게 특정; 하지 예: Office 365 ProPlus 설치 파일입니다. 데이터 및 개인 정보를 보호 하기 위해이 심도 깊은 노력 하는 방법에 대 한 자세한 내용은 [Office 365 보안 센터](https://go.microsoft.com/fwlink/p/?LinkId=397383) 를 통해에서 헤드 합니다.
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>모든 이러한 타사 서비스를 사용 하 여 내 네트워크를 보호할 수는 방법

광범위 한 파트너 서비스 집합을 활용 하 여 Office 365를 확장 하 고 가용성 요구 사항을 충족으로 Office 365를 사용 하는 경우의 사용자 환경을 향상을 수 있습니다. Office 365 기술을 활용 하는 타사 서비스 포함 두 인증서 해지 목록입니다. 예: crl.microsoft.com 또는 sa.symcb.com, 및 Cdn; 같은 r3.res.outlook.com 합니다. 모든 CDN FQDN Office 365에서 사용 하는 Office 365에 대 한 사용자 지정 FQDN, Office 365의 요청에서 FQDN으로 전송 하려는 경우 보장할 수 있습니다는 우리가 FQDN 및 제어 내부 콘텐츠 해당 위치에 있습니다.
  
고객을 위한 하는 여전히 하려면 Microsoft 또는 Office 365 데이터 센터는 타사 사람에 게 보내는 요청에서 사람에 게 보내는 요청을 분리 하려는 [Office 365 관리 끝점](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)에 대 한 지침을 작성 했습니다.
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Office 365 용 Azure ExpressRoute를 사용 하 고, 작업 변경 하는?

[Office 365 용 azure ExpressRoute](azure-expressroute.md) 공용 인터넷에서 분리 되는 Office 365 인프라에 대 한 전용된 연결을 제공 합니다. 즉, 클라이언트 Cdn 및 ExpressRoute에서 지 원하는 서비스 목록에 명시적으로 포함 되지 않은 다른 Microsoft 인프라에 연결에 대 한 비 ExpressRoute 연결을 통해 연결 해야 합니다. Cdn 사람에 게 보내는 요청 등 특정 트래픽을 라우팅 하는 방법에 대 한 자세한 내용은 [Office 365 네트워크 트래픽 관리](routing-with-expressroute.md)를 참조 하십시오.
  
짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>참고 항목

[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
