---
title: Office 365 서비스의 IPv6 지원
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: '요약: IPv6 지원 Office 365 government 제품 및 Microsoft Office 365 구성 요소에 설명합니다.'
ms.openlocfilehash: 75ed1c8ffe96ed1b09aa8802e11ae195ad60a4f2
ms.sourcegitcommit: d165aef59fe9a9ef538e6756fb014909a7cf975b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2018
ms.locfileid: "27294468"
---
# <a name="ipv6-support-in-office-365-services"></a>Office 365 서비스의 IPv6 지원

 **요약**: Microsoft Office 365 구성 요소에서 및 Office 365 government 제품의 IPv6 지원에 설명 합니다.
  
Office 365 IPv6 및 IPv4; 모두를 지원합니다. 그러나 일부 Office 365 기능 i p v 6을 사용할 수 완벽 하 게 됩니다. 즉, Office 365에 연결 하려면 i p v 4와 i p v 6을 모두 사용 해야 합니다. Office 365에 아웃 바운드 트래픽을 필터링 하는 경우 [Office 365 Url 및 IP 주소 범위](https://go.microsoft.com/fwlink/?LinkId=293744)문서의 전체 목록은 Office 365에서 지원 되는 IPv6 주소를 확인할 수 있습니다. 네트워크를 구성 하 고 적절 한 IPv6 주소는 사용할 수를 다운로드할 수 있습니다는 [Office 365 IPv6 테스트 계획](https://go.microsoft.com/fwlink/?LinkId=293447) Microsoft 다운로드 센터에서.
  
||
|:-----|
| 이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Office 365 구독 서비스의 IPv6 지원

### <a name="exchange-online-and-ipv6"></a>Exchange Online 및 IPv6

Exchange Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우 i p v 6 유선 및 무선 네트워크에는 기본적으로 사용 합니다. Exchange Online에 대 한 통신을 제어 하려는 경우 [Office 365 Url 및 IP 주소 범위에서](https://go.microsoft.com/fwlink/?LinkId=293744)IP 주소 범위를 사용 합니다.
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online 및 IPv6

 **Office 365 Government G1/G3/G4/K1** SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우에 기본적으로 i p v 6을 사용 하 여 시도 합니다.
  
 **공용 다중 테 넌 트 클라우드** Microsoft 사용자의 요청에 SharePoint Online i p v 6을 사용 합니다. CIDR 표기 조직의 DNS 인프라에 대 한 IP 주소를 제공 해야 합니다. 테 넌 트에 대해 사용 하도록 설정 하려면 i p v 6에 대 한 다른 조직에서 이러한 DNS 인프라를 공유할 수 없는 것을 염두에 두십시오. SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우 i p v 6에 사용 하도록 설정, 후에 i p v 6을 사용 하 여 기본적으로 합니다.
  
SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우 i p v 6 유선 및 무선 네트워크에는 기본적으로 사용 합니다. SharePoint Online에 대 한 통신을 제어 하려는 경우 [Office 365 Url 및 IP 주소 범위에서](https://go.microsoft.com/fwlink/?LinkId=293744)IP 주소 범위를 사용 합니다.
  
 **Office 365 Government G1/G3/G4/K1** SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우에 기본적으로 i p v 6을 사용 하 여 시도 합니다.
  
### <a name="skype-for-business-and-ipv6"></a>비즈니스 및 i p v 6에 대 한 Skype

I p v 6은 비즈니스에 대 한 Skype에서 지원 되지 않으며 더이상 사용할 수 없습니다 주의 해야 합니다.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection 및 IPv6

Exchange Online Protection (EOP) 전송 계층 보안 프로토콜을 통해 전송 발생 하는 경우 i p v 6을 지원 합니다. EOP 범위에 대 한 [Office 365 Url 및 IP 주소 범위를](https://go.microsoft.com/fwlink/?LinkId=293744)사용 합니다.
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Office 365 Government 제품의 IPv6 지원

중역이 부서 및 기관,으로 연방 정부 채택의 인터넷 프로토콜 버전 6 (i p v 6의 수석 정보 관리 책임자에 대 한 Office의 관리 및 예산 (OMB) 매핑합니다 준수 government 제품에 대 한 office 365 IPv6 지원 ) 매핑합니다. [Microsoft Office 365 정부는](https://go.microsoft.com/fwlink/p/?LinkId=325414) 분리 된 커뮤니티 클라우드에서 미국 정부 데이터를 저장 하는 다중 테 넌 트 서비스입니다. 다른 Office 365 제품 처럼 비즈니스, SharePoint Online 및 Office Professional Plus Skype Exchange Online을 포함 하 여 생산성 및 공동 작업 서비스를 제공 합니다. Microsoft Office 365 government 제품 2013에 대해서만 하 고 나중에 적용 됩니다. Office 365 government 제품에 대 한 자세한 내용은 참조 [정부에 대 한 Office 365 발표: A 미국 정부 커뮤니티 클라우드](https://go.microsoft.com/fwlink/p/?LinkId=325414)합니다. 국제 팔 규정 (ITAR)에서 트래픽은 방어 관련 문서 및 서비스는 [미국, 대한민국 군수 목록 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)에서 가져오기 및 내보내기를 제어 하는 미국 정부 규정 집합입니다. 엔터프라이즈용 Microsoft Office 365 보안, 프라이버시 및 규정 준수 요구 사항에 대 한 지원 미국 연방 기관에서 연방 정보 보안 요구 하는 Microsoft 생산성 솔루션에 대 한 전용된 호스팅 서비스를 제공 합니다. 관리 (FISMA) 인증 및 상업용 엔터티 ITAR에 따라 달라 집니다.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>IPv6과 Office 365를 사용할 때 고려해야 할 사항

I p v 6을 해제 하지 않는 것이 좋습니다. 자세한 내용은 참조 [Microsoft Windows에 대 한 IPv6: 질문과 대답](https://go.microsoft.com/fwlink/p/?LinkId=325418)합니다. 네트워크에서 사용 중인 IP 버전을 확인 하려면 다음 사항을 고려 합니다.
  
- 명령 프롬프트에서 IPConfig 명령 표시 "IPv6 Address" 또는 "Temporary IPv6 Address" 라는 행을 포함 하는 경우 환경의의 i p v 6을가지고 있습니다.

- 모든 IPv6 주소가 "fe80"로 시작 하 "Link-local IPv6 Address" 라는 행에 해당 하는 경우 해당 환경에 i p v 6를 않아도 됩니다.

다음의 고려 사항이 사용자의 네트워크에 적용될 수 있습니다.
  
- 공용 구독 서비스는 IPv6을 통해 신용 카드로 구매할 수 없습니다. 하지만 정부에는 EA(기업 계약) 라이선스가 있으므로 GCC(정부 커뮤니티 클라우드)에는 이 고려 사항이 적용되지 않습니다.

- IPv6은 일부 RMS(Rights Management 서비스) 시나리오를 지원하지 않습니다.

- BlackBerry i p v 6이 지원 되지 않으므로 i p v 6 BlackBerry® Enterprise Server (BES)를 지원 하지 않습니다.

- Office 365와 Active Directory Federation Services (AD FS)를 사용 하는 경우 Office 365에 AD FS 네트워크 끝점 광고 i p v 6을 사용 하 여 지원 되지 않습니다. Exchange Online을 사용 하는 경우 AD FS DNS 항목에서 AAAA 레코드를 포함 되지 않습니다. 

다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>참고 항목

[Microsoft 기술 백서](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[TCP/IP v4 및 v6](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[IPv6 사용 가이드](https://go.microsoft.com/fwlink/p/?LinkID=237480)
