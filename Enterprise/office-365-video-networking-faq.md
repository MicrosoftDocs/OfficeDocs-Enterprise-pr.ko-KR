---
title: Office 365 비디오 네트워킹에 대 한 질문과 대답
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
audience: Admin
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
description: Office 365 비디오 리포지토리와 스트리밍 서비스는 조직 내에서 비디오를 간단 하 게 저장 하 고 스트리밍하는 작업을 수행 합니다. Office 365 비디오에 대 한 많은 유용한 정보가 있습니다. 이 네트워킹 FAQ는 대역폭 계획, 암호화 및 서비스가 CDNs (콘텐츠 배달 네트워크)를 활용 하는 방법에 대 한 가장 일반적인 질문에 대 한 답변을 제공 하도록 설계 되었습니다.
ms.openlocfilehash: 93f55e0c1e4d065e02a9cc41e5aaaab89b459a0d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069474"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Office 365 비디오 네트워킹에 대 한 질문과 대답

Office 365 비디오 리포지토리와 스트리밍 서비스는 조직 내에서 비디오를 간단 하 게 저장 하 고 스트리밍하는 작업을 수행 합니다. [Office 365 비디오에 대 한](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)많은 유용한 정보가 있습니다. 이 네트워킹 FAQ는 대역폭 계획, 암호화 및 서비스가 cdns ( [콘텐츠 배달 네트워크](content-delivery-networks.md) )를 활용 하는 방법에 대 한 가장 일반적인 질문에 대 한 답변을 제공 하도록 설계 되었습니다.
  
비디오를 업로드 하거나 재생할 때 수행 되는 작업을 완전히 이해 하지 못한 경우에는이 비디오를 함께 살펴보고 [Office 365 비디오에 업로드할 때 비디오 파일](https://www.youtube.com/watch?v=HXSZ0jYBKlM)을 확인 하세요.
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Office 365 비디오 대역폭 요구 사항은 무엇 인가요?

Office 365에 업로드할 수 있는 지원 되는 다양 한 [비디오 형식이](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) 있습니다. 각 비디오 파일은 재생을 위해 다양 한 비디오 품질을 사용 하 여 표준 형식으로 인코딩됩니다. Office 365 Video에서는 적응 비트 전송률 스트리밍을 사용 하 여 비디오 플레이어의 사용 가능한 네트워크 대역폭과 크기에 따라 가장 적합 한 비디오 재생 품질을 선택 합니다. 이를 위해 플레이어는 처음에는 가장 낮은 재생 품질을 요청 합니다. 그런 다음 서비스는 비디오 플레이어에 2 초 비디오 세그먼트를 전송 하기 시작 합니다. 그러면 플레이어에서 각 세그먼트가 배달 되는 속도에 따라 재생 품질이 높거나 낮게 설정할 수 있습니다.
  
적응 비트 전송률 스트리밍은 최소 중단 또는 버퍼링을 통해 비디오를 재생 하는 동안 백그라운드에서이 모든 시간을 사용 합니다. 비디오 재생 중에 비디오 플레이어에서 자동 재생 품질을 수동으로 재정의 하 여 특정 비디오 재생 품질을 선택할 수 있습니다.
  
다음은 각 비디오 재생 품질에 대 한 네트워크 요구 사항을 설명 하는 간단한 표입니다. 비디오를 재생 하는 데 필요한 사용자 당 최소 대역폭은 802Kbps입니다.
  
|||
|:-----|:-----|
|**재생 품질** <br/> |**네트워크 속도** <br/> |
|288p  <br/> |802Kbps  <br/> |
|360p  <br/> |1.2 Mbps  <br/> |
|576p  <br/> |2.5 Mbps  <br/> |
|720p  <br/> |3.8 Mbps  <br/> |

([맨 위로](office-365-video-networking-faq.md)이동)
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a>CDNs (콘텐츠 배달 네트워크)에서 비디오 재생을 지원 하나요?

동일한 지리적 위치에 있는 동일한 조직에서 여러 사용자가 동일한 비디오를 스트리밍하는 경우 CDNs는 해당 지역에 가까운 위치에 이러한 비디오의 복사본을 저장 합니다. 비디오가 저장 되거나 가장 가까운 위치에 캐시 되 면 각 사용자는 위치에 상관 없이 비디오를 더 멀리 떨어진 위치에서 스트리밍합니다. Office 365 Video는 Azure Media Services를 사용 하 여 Azure CDNs에 캐시 된 항목과 기간을 관리 합니다. Azure 미디어 서비스는 [AZURE CDN 위치](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) 중 하나를 사용 하 여 며칠 동안 비디오 조각과 매니페스트를 캐시할 수 있습니다. 조직의 사용자가 계속 해 서 캐시에 저장 되 면 캐시에 유지 됩니다. 며칠 동안 비디오에 액세스 하는 사람이 없는 경우에는 결국 비디오가 캐시에서 삭제 됩니다. 다음 번에 누군가 비디오 시청을 시도할 때 가장 가까운 CDN 위치에 다시 캐시 됩니다.
  
콘텐츠가 근처의 CDN에서 캐시 되는 동안 비디오를 시청 하려는 모든 사용자는 비디오가 더 가까이 있고, 대부분의 경우 홉의 수가 줄어듭니다. 이렇게 하면 비디오 재생 속도가 향상 됩니다. 그러나 비디오 재생을 위한 네트워크 요구 사항은 변경 되지 않습니다.
  
> [!NOTE]
> 용량 제한에 도달 하 여 3 일 전에 비디오를 제거할 수 있는 몇 가지 경우가 있습니다.
  
([맨 위로](office-365-video-networking-faq.md)이동)
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>보다 빠른 재생을 위해 비디오를 로컬로 캐시할 수 있나요?

예. Office 365에서는 로컬 CDN 또는 캐싱 프록시를 사용 하 여 비디오 또는 기타 Office 365 콘텐츠를 빠른 액세스를 위해 로컬 네트워크로 가져올 수 없습니다. 네트워크에서 로컬 캐싱 솔루션을 구현 하는 방법에는 여러 가지가 있으며, 가장 일반적인 방법은 콘텐츠를 로컬로 캐시 하는 프록시 솔루션을 사용 하는 것입니다. 프록시 또는 개인 CDN에서 비디오 조각 및 매니페스트를 캐시 하면 프록시 또는 개인 CDN을 통해 라우팅되는 파일에 대 한 후속 요청이 로컬 캐시에서 추출 되 고 인터넷 위치에서 추출 되지 않습니다. 이와 같은 솔루션을 계획 하는 동안 네트워크 대역폭, 용량 및 비디오 재생 병행성을 고려해 야 합니다.
  
([맨 위로](office-365-video-networking-faq.md)이동)
  
## <a name="how-videos-are-encrypted-and-secured"></a>비디오를 암호화 하 고 보호 하는 방법

Office 365 비디오에서는 데이터를 안전 하 고 개인적으로 유지 하는 것이 얼마나 중요 한지를 알고 있습니다. [Microsoft 보안 센터](https://products.office.com/business/office-365-trust-center-welcome) 는 콘텐츠의 개인 정보 및 보안에 대 한 약정을 설명 합니다. 비디오 재생을 사용 하면 속도가 매우 중요 한 환경을 경험할 수 있습니다. 그러나 exchange에서 속도를 높이기 위해 보안 또는 개인 정보를 손상 시 키 지는 않습니다. 속도, 보안 및 개인 정보를 처리 하는 방법은 다음과 같습니다.
  
사용자나 조직의 다른 사람이 새 비디오를 업로드 하면 해당 비디오는 트랜스 코딩 되 고, AES-128 암호화로 암호화 되며, Azure Media Services에 저장 됩니다. 즉, 비디오는 전송 및 휴지에서 모두 암호화 됩니다.
  
조직의 누군가가 새 비디오를 시청 하려고 하면 다음 단계를 수행 합니다.
  
1. SharePoint Online에 비디오를 볼 수 있는 권한이 있는지 확인 하세요.

2. SharePoint Online은 파일 사용 권한을 사용 하 여 사용자가 비디오를 시청할 수 있는지 여부를 결정 합니다.

3. 허용 되는 경우 SharePoint Online은 비디오 플레이어에 게 제공할 Azure에서 토큰을 검색 합니다.

4. 그런 다음 비디오 플레이어에서 토큰을 사용 하 여 Azure에서 암호 해독 키를 요청 합니다.

5. 암호 해독 키가 있으면 비디오 재생기에서 비디오를 스트리밍할 수 있습니다.

![O365 비디오 재생](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([맨 위로](office-365-video-networking-faq.md)이동)
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Office 365 동영상을 재생 하는 데 필요한 요구 사항은 무엇 인가요?

Office 365 비디오 지원 운영 체제 및 웹 브라우저는 [office 365 시스템 요구 사항](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)에 대 한 SharePoint Online 요구 사항과 동일 합니다. 보유 하 고 있는 운영 체제 및 웹 브라우저 구성에 따라 비디오 플레이어의 특정 요구 사항을 결정 해야 합니다. [비디오 재생 요구 사항](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)에 대 한 자세한 내용은 다음과 같습니다.
  
([맨 위로](office-365-video-networking-faq.md)이동)
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Office 365 비디오를 사용할 수 없음 (시작 해야 하는 경우)

Office 365의 연결 문제 해결 비디오에는 네트워크, ISP 및 Office 365 구성에 대 한 문제 해결이 포함 되어 있습니다. 시작 하는 첫 번째 위치는 서비스 상태 대시보드입니다. 이를 통해 Office 365 비디오에 문제가 있거나 그렇지 않을 수 있습니다. 여기에 모든 내용이 표시 되 면 도움이 되는 몇 가지 추가 리소스가 있습니다.
  
- [Office 365 비디오에 필요한 네트워크 끝점](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)에 연결할 수 있는지 확인 합니다.

- [Office 365 네트워크 문제 해결 가이드](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)를 사용 하 여 네트워크 연결을 확인 합니다.

- [저속 네트워크에서 Office 365 사용에 대 한 모범 사례](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)를 참조 하세요.

- [Office 365 비디오 구성에 대 한 도움말을 찾아봅니다](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([맨 위로](office-365-video-networking-faq.md)이동)
  
## <a name="office-365-video-resources"></a>Office 365 비디오 리소스

다음은 Office 365 비디오를 성공적으로 배포 및 사용 하는 데 도움이 되는 몇 가지 기타 리소스입니다.
  
[Office 365 비디오 구성에 대 한 도움말 찾기](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[Office 365 비디오에 맞추기](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Office 365 동영상에서 채널 만들기 및 관리](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Office 365 비디오 포털 관리](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Office 365 비디오에서 작동 하는 비디오 형식](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([맨 위로](office-365-video-networking-faq.md)이동)
  
다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
