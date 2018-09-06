---
title: 추가 Office 365 IP 주소 및 웹 서비스에 포함되지 않은 URL
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/22/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: '요약: 새로운 엔드 포인트 웹 서비스에는 특정 시나리오에 대한 적은 수의 엔드 포인트가 포함되지 않습니다.'
hideEdit: true
ms.openlocfilehash: b40fb1a40d2a815bfc6e02fa11204d10dde2af73
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22600512"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>추가 Office 365 IP 주소 및 웹 서비스에 포함되지 않은 URL

일부 네트워크 끝점은 이전에 게시되었으며 웹 서비스에 포함되지 않았습니다. 웹 서비스 범위는 엔터프라이즈 경계 네트워크에서 Office 365 최종 사용자의 연결에 필요한 네트워크 끝점입니다. 현재는 다음 내용이 포함되어 있지 않습니다.

1. Microsoft 데이터 센터에서 고객 네트워크(인바운드 하이브리드 서버 네트워크 트래픽)로 연결 시 필요할 수 있는 네트워크 연결
2. 고객 네트워크의 서버에서 엔터프라이즈 경계(아웃 바운드 서버 네트워크 트래픽) 전체에 네트워크 연결
3. 한 사용자의 네트워크 연결 요구 사항에 대한 일반적이지 않은 시나리오
4. DNS 확인 연결 요구 사항(아래 나열되지 않음)
5. Internet Explorer 또는 Microsoft Edge의 신뢰할 수 있는 사이트

DNS 외에도 설명된 특정 시나리오가 필요하지 않는 경우 대부분의 고객에게 이러한 사항은 모두 선택 사항입니다.

|||||
|:-----|:-----|:-----|:-----|
| **행** | **용도** | **대상** | **유형** |
| 1  | PST 및 파일 수집를 위한 [서비스 가져오기](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) | 추가 요구 사항은 [서비스 가져오기](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)를 참조하세요. | 일반적이지 않은 아웃바운드 시나리오 |
| 2  | [Microsoft 지원 및 Office 365 지원 및 복구 도우미](https://diagnostics.office.com/#/) - Single Sign-On 사용자 자격 증명의 유효성을 검사합니다. 원본:<br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | 온-프레미스 보안 토큰 서비스 | 인바운드 서버 트래픽 |
| 3  | Azure AD Connect(w/SSO 옵션)-WinRM 및 원격 PowerShell | 고객 STS 환경(AD FS 서버 및 AD FS 프록시) \| TCP 포트 80 및 443 | 인바운드 서버 트래픽 |
| 4  | AD FS 프록시 서버와 같은 STS(페더레이션 고객만 해당) | 고객 STS(예: AD FS 프록시) \| 포트 TCP 443 또는 TCP 49443 w/ClientTLS | 인바운드 서버 트래픽 |
| 5  | [Exchange Online의 통합 메시징/SBC 통합](https://technet.microsoft.com/library/jj673565.aspx) | Session Border Controller 및 *. um.outlook.com간에 양방향 온-프레미스 | 아웃바운드 서버 전용 트래픽 |
| 6  | 약속 있음/없음 공유와 같은 [Exchange Hybrid](https://docs.microsoft.com/exchange/exchange-deployment-assistant) 공존 기능 | 고객 온-프레미스 Exchange 서버 | 인바운드 서버 트래픽 |
| 7  | [Exchange 하이브리드](https://docs.microsoft.com/exchange/exchange-deployment-assistant) 프록시 인증 | 고객 온-프레미스 STS | 인바운드 서버 트래픽 |
| 8  | Exchange Hybrid 구성 마법사를 사용하여 [Exchange Hybrid](https://docs.microsoft.com/exchange/exchange-deployment-assistant)를 구성하는 데 사용됩니다. <br> 참고 :이 끝점은 Exchange 하이브리드 구성에만 필요합니다  | TCP 포트 80 및 443의 ```domains.live.com```는 Exchange 2010 SP3 하이브리드 구성 마법사에만 필요합니다. | 아웃바운드 서버 전용 트래픽 |
| 9  | **인증 및 ID FQDN** <br> 작동하려면 FQDN ```secure.aadcdn.microsoftonline-p.com```가 클라이언트의 Internet Explorer(IE) 또는 Edge의 신뢰할 수있는 사이트 영역에 있어야 합니다. |  | 신뢰할 수 있는 사이트 |
| 10  |  **Microsoft Teams FQDN** <br> Internet Explorer 또는 Microsoft Edge를 사용하는 경우 먼저 제3자 쿠키를 사용하고 팀의 FQDN을 신뢰할 수있는 사이트에 추가해야 합니다. 이는 위에 나열된 제품군 전체의 FQDN, CDN 및 원격 분석 외에 추가되는 사항입니다. 자세한 내용은 [Microsoft Teams대한 알려진 문제점](https://docs.microsoft.com/microsoftteams/known-issues)을 참조하세요. |  | 신뢰할 수 있는 사이트 |
| 11  |  **SharePoint Online 및 비즈니스용 OneDrive FQDN** <br> FQDN의 '\< tenant>'가있는 모든 '.sharepoint.com' FQDN은 클라이언트의 IE 또는 Microsoft Edge 신뢰할 수있는 사이트 영역에 있어야 작동할 수 있습니다. 위에 나열된 제품군 전체 FQDN, CDN 및 원격 측정 외에도 이러한 끝점을 추가해야 합니다. |  | 신뢰할 수 있는 사이트 |
| 12  | **Yammer**  <br> Yammer는 브라우저에서만 사용할 수 있으며 인증된 사용자는 프록시를 통해 전달되어야 합니다. 모든 Yammer FQDN은 클라이언트의 IE 또는 Edge의 신뢰할 수있는 사이트 영역에 있어야 작동할 수 있습니다. |  | 신뢰할 수 있는 사이트 |

## <a name="related-topics"></a>관련 항목

[Office 365 끝점 관리](managing-office-365-endpoints.md)
  
[Office 365 연결 문제 해결](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[클라이언트 연결](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[콘텐츠 배달 네트워크](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure 데이터 센터 IP 범위](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 공용 IP 공간](https://www.microsoft.com/download/details.aspx?id=53602)

