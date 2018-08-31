---
title: 질문과 대답 네트워킹 office 365 비디오
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Office 365 비디오 리포지토리와 스트리밍 서비스를 보다 손쉽게 저장 하 고 조직 내에서 비디오를 스트리밍합니다. Office 365 비디오;에 대 한 유용한 정보 많이 이 네트워킹 FAQ는 암호화 및 서비스 콘텐츠 배달 네트워크 (Cdn)를 활용 하는 방법을 계획 하는 대역폭 주위 가장 일반적인 질문에 대답 하도록 설계 되었습니다.
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541979"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>질문과 대답 네트워킹 office 365 비디오

Office 365 비디오 리포지토리와 스트리밍 서비스를 보다 손쉽게 저장 하 고 조직 내에서 비디오를 스트리밍합니다. [Office 365 비디오에 대 한 정보](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)뛰어난; 많이 이 네트워킹 FAQ는 암호화 및 서비스 [콘텐츠 배달 네트워크 (Cdn)를](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)활용 하는 방법을 계획 하는 대역폭 주위 가장 일반적인 질문에 대답 하도록 설계 되었습니다.
  
이미에 비디오를 업로드할 때 수행 하는 작업의 철저 하 게 이해할 수 있습니다 또는 재생,이 비디오에 대 한 정보를 포함 하지는 배치 함께 [Office 365 비디오에 업로드 하는 경우 비디오 파일을 수행 하는 작업](https://www.youtube.com/watch?v=HXSZ0jYBKlM)입니다.
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Office 365 비디오 대역폭 요구 사항은 무엇입니까?

수많은 [지원 되는 비디오 형식](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) Office 365에 업로드 될 수 있습니다. 다음 각 비디오 파일 재생에 대 한 여러 다른 비디오 품질와 표준 형식으로 인코딩됩니다. Office 365 비디오 스트리밍 비디오 플레이어의 크기와 사용 가능한 네트워크 대역폭에 따라 최상의 비디오 재생 품질을 선택 하는 환경에 적합 한 비트 전송률을 사용 합니다. 이 작업을 수행 하려면 플레이어 처음 가장 낮은 재생 품질을 요청 합니다. 다음 서비스는 비디오 플레이어를 2 초 비디오 세그먼트를 보낼 시작 합니다. 플레이어 수를 기반으로 각 세그먼트 배달 되는 얼마나 빨리 높거나 낮게 재생 품질을 요청 합니다.
  
환경에 적합 한 비트 전송률 스트리밍이 작업을 수행 모든 백그라운드에서 최소한의 중단 또는 버퍼링와 비디오를 재생 하는 동안 합니다. 비디오 재생 하는 동안 비디오 플레이어를 수동으로 특정 비디오 재생 품질을 선택 하는 자동 재생 품질을 재정의 하려면 뷰어를 허용 합니다.
  
빠른 테이블에서는 각 비디오 재생 품질에 대 한 네트워크 요구 사항에 설명 하는 다음과 같습니다. 비디오를 재생 하는 데 필요한 사용자 당 최소 대역폭은 802 Kbps입니다.
  
|||
|:-----|:-----|
|**재생 품질** <br/> |**네트워크 속도** <br/> |
|288 p  <br/> |802 k b p s  <br/> |
|360 p  <br/> |1.2 Mbps  <br/> |
|576 p  <br/> |2.5 Mbps  <br/> |
|720p  <br/> |3.8 Mbps  <br/> |

([맨위로 이동](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>Cdn 비디오 재생을 통해 방법을

동일한 지리적 위치 내에서 같은 조직에서 여러 사용자는 동일한 비디오 스트리밍의 경우, Cdn 해당 지리적 영역에 더 가깝게 위치에 이러한 비디오의 복사본을 저장 합니다. 비디오, 저장 또는 가장 가까운 위치에 캐시 된 각 사용자 위치를 추가 하는 대신 자신에 게 가장 가까운 위치에서 비디오를 자리 비움으로 스트리밍합니다. Office 365 비디오 Azure Media 서비스를 사용 하 여 어떤 캐싱되 Azure Cdn에서 및 방법에 대 한 긴 관리. Azure 미디어 서비스 [Azure CDN 위치](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) 중 하나를 사용 하 여 비디오 조각 및 며칠에 대 한 매니페스트를 캐시 수 있습니다. 조직의 사용자에 게 계속 제공 되는 캐시 된 비디오를 시청 하는 경우 캐시 유지할 표시 됩니다. 며칠 비디오에 대 한 비디오 결국 없는 하나의 액세스 하는 경우 드롭 캐시에서 삭제할 수 있습니다. 다음 비디오를 시청 하 려 것은 다시 한번 캐시 시간 가장 가까운 CDN 위치에 합니다.
  
콘텐츠 하는 동안 비디오를 시청 하려고 하는 모든 사람 근처 CDN 혜택 되 가깝게, 비디오 및 홉, 자리 비움 덜 대부분의 경우에 캐시 됩니다. 이렇게 하면 비디오 재생 속도를; 향상 됩니다. 그러나 비디오를 재생 하려면 네트워크 요구 사항은 바뀌지 않습니다.
  
> [!NOTE]
> 중인에 도달 하면, 3 일에 도달 했습니다 전에 비디오 제거 될 수 있습니다를 사용해 용량 제한 등 경우도 있습니다.
  
([맨위로 이동](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>더 빠른 재생에 대 한 로컬에서 제공 되는 비디오를 캐시할 수 있습니까?

예입니다. Office 365 로컬 CDN 또는 캐싱 프록시를 사용 하 여 가져올 비디오 또는 다른 Office 365 콘텐츠 빠른 액세스에 대 한 로컬 네트워크에서 차단 되지 않습니다. 네트워크에서 로컬 캐싱 솔루션을 구현 하는 여러가지 방법으로, 가장 일반적인 방법은 콘텐츠를 로컬로 캐시 하는 프록시 솔루션을 사용 하는 것입니다. 프록시 또는 개인 CDN가 비디오 조각 및 매니페스트 캐시, 되 면 프록시 또는 개인 CDN를 통해 라우팅되며 이러한 파일에 대 한 이후 요청, 로컬 캐시에서 가져온를 업데이트 하 고 인터넷의 특정 위치에서 추출 되지 됩니다. 다음과 같은 솔루션의 계획 하는 동안 네트워크 대역폭, 용량 및 비디오 재생 동시성을 고려 합니다.
  
([맨위로 이동](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>방법 비디오 암호화 하 고 보호 하는?

Office 365 비디오 안전 하 고 개인 데이터를 유지 하는 얼마나 중요 한지 알 수 있습니다. [Office 365 보안 센터](https://products.office.com/business/office-365-trust-center-cloud-computing-security) 개인정보 및 콘텐츠의 보안을 위한 노력을 설명합니다. 비디오 재생 속도 환경을 향상 시키면서;에 대 한 중요 한 그러나 보안 또는 속도 위해 exchange에서 정보 공개는 손상을 주지 않도록 합니다. 속도, 보안 및 개인정보 보호 방법 수용는 다음과 같습니다.
  
하면 사용자나 관리자가 조직에서 새로운 비디오 업로드, 해당 비디오 코드 변환 된, AES 128 암호화를 사용 하 여 암호화 하 고 Azure 미디어 서비스에 저장 됩니다. 즉,에서 전송 및 나머지 부분에서 제공 되는 비디오 암호화 됩니다.
  
새 비디오를 시청 하려고 하면 조직에서 다른 사용자 할 때은 다음이 단계를 따릅니다.
  
1. SharePoint Online 비디오를 볼 수 있는 권한이 있는지 확인 합니다.

2. SharePoint Online 사용 하 여 파일 사용 권한을 결정 사용자 비디오 시청 수 있습니다.

3. 허용 되는 경우 SharePoint Online 토큰에서에서 검색 Azure에 비디오 플레이어를 제공 합니다.

4. 다음 비디오 플레이어 토큰을 사용 하 여 Azure에서 암호 해독 키를 요청 해야 합니다.

5. 손에서 암호 해독 키를 사용 하는 비디오 플레이어는 비디오 스트림 수 있습니다.

![O365 비디오 재생](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([맨위로 이동](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Office 365 비디오 재생에 대 한 요구 사항은 무엇입니까?

Office 365 비디오 지원 되는 운영 체제 및 웹 브라우저는 [Office 365 시스템 요구 사항](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)에서 SharePoint Online 요구와 동일 합니다. 운영 체제 및 웹에 따라 브라우저 구성 해야 비디오 플레이어의 특정 요구를 결정 합니다. [비디오 재생 요구 사항](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)에 대 한 자세한 내용은 다음과 같습니다.
  
([맨위로 이동](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Office 365 비디오 작동 하려면 어디서부터 시작 해야를 가져올 수 없습니다.

Office 365 비디오에 대 한 연결 문제를 해결 네트워크, 사용자 ISP(s) 및 Office 365의 구성 문제를 해결 해야 합니다. 시작 하려면 먼저 서비스 상태 대시보드는입니다. 이 여부에 문제가 발생 하면 Office 365 비디오를 안내 합니다. 모든 보이면 다음과 같은 경우 하는데 도움이 되는 일부 추가 리소스 다음과 같습니다.
  
- [Office 365 비디오에 필요한 네트워크 끝점](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)에 연결할 수 있는지 확인 하십시오.

- 이 [가이드의 문제를 해결 하는 Office 365 네트워크](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)를 사용 하 여 네트워크 연결을 확인 합니다.

- 이 [저속 네트워크에서 Office 365를 사용 하는 것에 대 한 모범 사례](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)를 참조 하십시오.

- [Office 365 비디오 구성에 대 한 도움말](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)을 찾아보십시오.

([맨위로 이동](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Office 365 비디오 리소스

항목을 평가 하 고는 질문에 응답 하는 경우 또는 대답 여전히 찾는 경우 알려주시면에 대 한 설명을 그대로 둡니다. 성공적으로 배포 하 고 Office 365 비디오를 사용할 수 있도록이 다른 리소스 중 일부는 다음과 같습니다.
  
[Office 365 비디오 구성에 대 한 도움말을 찾습니다](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).
  
[Office 365 비디오를 충족 합니다.](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[만들기 및 Office 365 비디오에서 채널 관리](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Office 365 비디오 포털 관리](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Office 365 비디오에서 작동 하는 비디오 형식](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([맨위로 이동](office-365-video-networking-faq.md))
  
짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
