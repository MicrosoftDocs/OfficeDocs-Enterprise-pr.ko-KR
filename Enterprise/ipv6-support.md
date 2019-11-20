---
title: Office 365 서비스의 IPv6 지원
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: '요약: Microsoft Office 365 구성 요소 및 Office 365 정부 제품의 IPv6 지원에 대해 설명 합니다.'
ms.openlocfilehash: 17938a6bd3544889c4afa38f27b11ea7f02e0f43
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745731"
---
# <a name="ipv6-support-in-office-365-services"></a>Office 365 서비스의 IPv6 지원

*이 문서는 Office 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*

Office 365은 IPv6 및 IPv4를 모두 지원 합니다. 그러나 IPv6에서 모든 Office 365 기능이 완전히 사용 하도록 설정 되는 것은 아닙니다. 즉, Office 365에 연결 하려면 IPv4 및 IPv6을 모두 사용 해야 합니다. Office 365에 대 한 아웃 바운드 트래픽을 필터링 하는 경우 Office 365에서 지 원하는 전체 IPv6 주소 목록은 [office 365 url 및 IP 주소 범위](urls-and-ip-address-ranges.md)문서에서 찾을 수 있습니다. 네트워크가 구성 되 고 적절 한 IPv6 주소가 허용 되 면 Microsoft 다운로드 센터에서 [Office 365 IPv6 테스트 계획](https://go.microsoft.com/fwlink/?LinkId=293447) 을 다운로드할 수 있습니다.
  
## <a name="ipv6-support-in-office-365-subscription-service"></a>Office 365 구독 서비스의 IPv6 지원

### <a name="exchange-online-and-ipv6"></a>Exchange Online 및 IPv6

Exchange Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 유선 및 무선 네트워크에서 모두 기본적으로 IPv6을 사용 하 게 됩니다. Exchange Online에 대 한 통신을 제어 하려면 [Office 365 url 및 ip 주소 범위](urls-and-ip-address-ranges.md)에서 ip 주소 범위를 사용 합니다.
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online 및 IPv6

 **Office 365 정부/G3/G4/K1** SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 IPv6 사용이 기본적으로 시도 됩니다.
  
 **공용 다중 테 넌 트 클라우드** Microsoft는 요청 시 SharePoint Online IPv6을 사용 하도록 설정 합니다. 조직의 DNS 인프라에 대 한 CIDR notated IP 주소를 제공 해야 합니다. 이 DNS 인프라는 테 넌 트에 대해 사용 하도록 설정 하기 위한 IPv6 용 다른 조직에서 공유할 수 없습니다. IPv6을 사용 하도록 설정한 후에는 SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 기본적으로 IPv6을 사용 합니다.
  
SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 유선 및 무선 네트워크에서 모두 기본적으로 IPv6을 사용 하 게 됩니다. SharePoint Online에 대 한 통신을 제어 하려면 [Office 365 url 및 ip 주소 범위](urls-and-ip-address-ranges.md)에서 ip 주소 범위를 사용 합니다.
  
 **Office 365 정부/G3/G4/K1** SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 IPv6 사용이 기본적으로 시도 됩니다.
  
### <a name="skype-for-business-and-ipv6"></a>비즈니스용 Skype 및 IPv6

알 수 없음 IPv6은 비즈니스용 Skype에서 지원 되지 않으며 더 이상 사용할 수 없습니다.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection 및 IPv6

전송 계층 보안 프로토콜을 통해 전송이 수행 되는 경우 EOP (Exchange Online Protection)에서 IPv6을 지원 합니다. EOP 범위에 대해 [Office 365 url 및 IP 주소 범위](urls-and-ip-address-ranges.md)를 사용 합니다.
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Office 365 정부 제품에 대 한 IPv6 지원

Office 365 정부에 대 한 IPv6 지원은 경영 부서나 기관에 대 한 정보 관리자를 위한 OMB (관리 및 예산) Memorandum 및 IPv6 (인터넷 프로토콜 버전 6)의 연방 정부 채택에 부합 합니다. ) memorandum. [정부용 Microsoft Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414) 는 분리 된 커뮤니티 클라우드에 미국 정부 데이터를 저장 하는 다중 테 넌 트 서비스입니다. 다른 Office 365 제공 기능과 마찬가지로, Exchange Online, 비즈니스용 Skype, SharePoint Online 및 Office Professional Plus를 포함 하는 생산성 및 공동 작업 서비스가 제공 됩니다. 

Microsoft Office 365 정부 제품은 2013 이상에만 적용 됩니다. Office 365 정부 제품에 대 한 자세한 내용은 [Microsoft 정부용 office 365 정부: US 정부 커뮤니티 클라우드](https://go.microsoft.com/fwlink/p/?LinkId=325414)를 참조 하세요. ITAR (무장 규정)의 국제 트래픽은 [미국 군수 목록 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)에 대 한 방어 관련 문서 및 서비스의 내보내기와 가져오기를 제어 하는 미국 정부 규정 집합입니다. 

기업에 대 한 microsoft Office 365에서는 연방 정보 보안이 필요한 미국 연방 기관에 대 한 보안, 개인 정보 보호 및 규정 준수 요구 사항을 지 원하는 Microsoft 생산성 솔루션에 대 한 전용 호스팅 서비스를 제공 합니다. FISMA (관리) 인증 및 상업용 엔터티가 ITAR에 적용 됩니다.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>IPv6 및 Office 365을 사용할 때 고려해 야 할 사항

IPv6을 사용 하지 않도록 설정 하지 않는 것이 좋습니다. 자세한 내용은이 [가이드 문서](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)를 참조 하십시오. 네트워크에서 사용 중인 IP 버전을 확인 하려면 다음을 고려 하십시오.
  
- 명령 프롬프트에 **IPConfig** 명령 표시에 "ipv6 주소" 또는 "임시 IPv6 주소" 라는 행이 포함 되어 있으면 사용자 환경에 i p v 6이 있는 것입니다.

- 모든 IPv6 주소가 "fe80"로 시작 하 고 "링크-로컬 IPv6 주소" 라는 행에 해당 하면 사용자 환경에 i p v 6이 없는 것입니다.

네트워크에 다음과 같은 사항이 적용 될 수 있습니다.
  
- 공용 구독 서비스는 IPv6을 통한 신용 카드를 사용한 구매를 지원 하지 않습니다. 정부에는 EA (엔터프라이즈 계약) 라이선스가 있기 때문에 GCC (정부 커뮤니티 클라우드) 라이센스가 적용 되지 않습니다.

- 일부 RMS (권한 관리 서비스) 시나리오는 IPv6에서 지원 되지 않습니다.

- BES (BlackBerry는 IPv6을 지원 하지 않기 때문에, IPv6은 BlackBerry®를 지원 하지 않습니다.

- Office 365에서 AD FS (Active Directory Federation Services)를 사용 하는 경우에는 IPv6을 사용 하 여 AD FS 네트워크 끝점을 Office 365에 보급 하는 것은 지원 되지 않습니다. Exchange Online을 사용 하는 경우 AD FS DNS 항목에 AAAA 레코드를 포함할 수 없습니다. 

다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>참고 항목

[IPv6 학습 로드맵](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 생존 가이드](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
