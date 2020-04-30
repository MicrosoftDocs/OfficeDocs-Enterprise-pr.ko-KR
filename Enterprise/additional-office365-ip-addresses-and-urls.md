---
title: Office 365 IP 주소 및 URL 웹 서비스에 포함되지 않은 추가 엔드포인트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/28/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: '요약: 새로운 엔드포인트 웹 서비스에는 특정 시나리오에 맞는 적은 수의 엔드포인트가 포함되어 있지 않습니다.'
hideEdit: true
ms.openlocfilehash: 303b3bb57ab3b29a9ad825a525793af6f476e784
ms.sourcegitcommit: eca49563fd99f08b7ee0bba01d122b0b96de07cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2020
ms.locfileid: "43930219"
---
# <a name="additional-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Office 365 IP 주소 및 URL 웹 서비스에 포함되지 않은 추가 엔드포인트

일부 네트워크 끝점은 이전에 게시되었으며 [Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)에 포함되어 있지 않습니다. 웹 서비스 범위는 엔터프라이즈 경계 네트워크에서 Office 365 사용자의 연결에 필요한 네트워크 끝점입니다. 현재는 다음 내용이 포함되어 있지 않습니다.

1. Microsoft 데이터 센터에서 고객 네트워크(인바운드 하이브리드 서버 네트워크 트래픽)로 연결 시 필요할 수 있는 네트워크 연결.
2. 고객 네트워크의 서버에서 엔터프라이즈 경계(아웃 바운드 서버 네트워크 트래픽) 전체에 네트워크 연결.
3. 한 사용자의 네트워크 연결 요구 사항에 대한 일반적이지 않은 시나리오.
4. DNS 확인 연결 요구 사항(아래 나열되지 않음).
5. Internet Explorer 또는 Microsoft Edge의 신뢰할 수 있는 사이트.

DNS 외에도 설명된 특정 시나리오가 필요하지 않는 경우 대부분의 고객에게 이러한 사항은 모두 선택 사항입니다.

|||||
|:-----|:-----|:-----|:-----|
| **행** | **용도** | **대상** | **유형** |
| 1  | PST 및 파일 수집를 위한 [서비스 가져오기](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) | 추가 요구 사항은 [서비스 가져오기](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)를 참조하세요. | 일반적이지 않은 아웃바운드 시나리오 |
| 2  | [Office 365용 Microsoft 고객 지원 및 복구 도우미](https://diagnostics.office.com/#/)  | https<span>://</span>autodiscover.outlook.com <BR> <span>https://</span>officecdn.microsoft.com <BR> <span>https://</span>api.diagnostics.office.com <BR> <span>https://</span>apibasic.diagnostics.office.com <BR> <span>https://</span>autodiscover-s.outlook.com <BR> <span>https://</span>cloudcheckenabler.azurewebsites.net <BR> <span>https://</span>dcs-staging.azure-api.net <BR> <span>https://</span>login.live.com <BR> <span>https://</span>login.microsoftonline.com <BR> <span>https://</span>login.windows.net <BR> <span>https://</span>o365diagtelemetry.trafficmanager.net <BR> <span>https://</span>odc.officeapps.live.com <BR> <span>https://</span>offcatedge.azureedge.net <BR> <span>https://</span>officeapps.live.com <BR> <span>https://</span>outlook.office365.com <BR> <span>https://</span>outlookdiagnostics.azureedge.net | 아웃바운드 서버 트래픽 |
| 3  | Azure AD Connect(w/SSO 옵션)-WinRM 및 원격 PowerShell | 고객 STS 환경(AD FS 서버 및 AD FS 프록시) \| TCP 포트 80 및 443 | 인바운드 서버 트래픽 |
| 4  | AD FS 프록시 서버와 같은 STS(페더레이션 고객만 해당) | 고객 STS(예: AD FS 프록시) \| 포트 TCP 443 또는 TCP 49443 w/ClientTLS | 인바운드 서버 트래픽 |
| 5  | [Exchange Online의 통합 메시징/SBC 통합](https://technet.microsoft.com/library/jj673565.aspx) | Session Border Controller 및 *. um.outlook.com간에 양방향 온-프레미스 | 아웃바운드 서버 전용 트래픽 |
| 6  | 사서함 마이그레이션. 온-프레미스 [Exchange 하이브리드](https://docs.microsoft.com/exchange/exchange-deployment-assistant)에서 Office 365로 사서함 마이그레이션을 시작하는 경우 Office 365에서 게시된 Exchange 웹 서비스(EWS)/사서함 복제 서비스(MRS) 서버에 연결합니다. 특정 원본 IP 범위에서 인바운드 연결을 제한하기 위해 Exchange Online 서버에서 사용하는 NAT IP 주소는 "Exchange Online"서비스 영역 아래의 [Office 365 URL 및 IP 범위](urls-and-ip-address-ranges.md)에 나열됩니다. OWA와 같은 게시된 EWS 끝점에 대한 액세스가 특정 원본 IP 범위에서 TCP 443 연결을 제한하기 전에 MRS 프록시가 별도의 FQDN 및 공용 IP 주소를 확인하는지 주의해야 합니다. | 고객 온-프레미스 EWS/MRS 프록시<br> TCP 포트 443 | 인바운드 서버 트래픽 |
| 7  | 약속 있음/없음 공유와 같은 [Exchange 하이브리드](https://docs.microsoft.com/exchange/exchange-deployment-assistant) 공존 기능 | 고객 온-프레미스 Exchange 서버 | 인바운드 서버 트래픽 |
| 8  | [Exchange 하이브리드](https://docs.microsoft.com/exchange/exchange-deployment-assistant) 프록시 인증 | 고객 온-프레미스 STS | 인바운드 서버 트래픽 |
| 9  | [Exchange 하이브리드 구성 마법사](https://docs.microsoft.com/exchange/hybrid-configuration-wizard)를 사용하여 [Exchange 하이브리드](https://docs.microsoft.com/exchange/exchange-deployment-assistant)를 구성하는 데 사용됩니다. <br> 참고 :이 끝점은 Exchange 하이브리드 구성에만 필요합니다  | TCP 포트 80 및 443의 domains.live.com. Exchange 2010 SP3 하이브리드 구성 마법사에서만 필요합니다.<BR> <BR> GCC High, DoD IP 주소: 40.118.209.192/32; 168.62.190.41/32 <BR> <BR> 전 세계 사용 및 & GCC: *.store.core.windows.net; asl.configure.office.com; mshrcstorageprod.blob.core.windows.net; tds.configure.office.com; mshybridservice.trafficmanager.net <BR>  | 아웃바운드 서버 전용 트래픽 |
| 10  | AutoDetect 서비스는 [Exchange 하이브리드](https://docs.microsoft.com/exchange/exchange-deployment-assistant) 시나리오에서 [iOS 및 Android용 Outlook을 통한 하이브리드 최신 인증](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)과 함께 사용됩니다. <BR> <BR> ```*.acompli.net``` <BR> <BR> ```*.outlookmobile.com``` <BR> <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | TCP 443의 고객 온-프레미스 Exchange 서버 | 인바운드 서버 트래픽 |
| 11  | Office 2016의 비즈니스용 Skype에는 UDP 포트를 사용하는 비디오 기반 화면 공유 기능이 포함되어 있습니다. Office 2013 이하의 이전 비즈니스용 Skype 클라이언트에서는 TCP 포트 443을 사용하는 RDP를 이용했었습니다. | 52.112.0.0/14에 열린 TCP 포트 443 | Office 2013 이전의 비즈니스용 Skype 이전 클라이언트 버전 |
| 12  | 비즈니스용 Skype Online에 대한 비즈니스용 Skype 하이브리드 온-프레미스 서버 연결 | 13.107.64.0/18, 52.112.0.0/14  <BR> UDP 포트 50,000~59,999 <BR>  TCP 포트 50,000~59,999; 5061 | 비즈니스용 Skype 온-프레미스 서버 아웃바운드 연결 |
| 13  | 온-프레미스 하이브리드 연결을 사용하는 클라우드 PSTN에는 온-프레미스 호스트에 열린 네트워크 연결이 필요합니다. 비즈니스용 Skype Online 하이브리드 구성에 대한 자세한 내용은  | [비즈니스용 Skype 서버 및 Office 365 간 하이브리드 연결 플랜](https://docs.microsoft.com/skypeforbusiness/hybrid/plan-hybrid-connectivity)을 참조하세요. | 비즈니스용 Skype 온-프레미스 하이브리드 인바운드 |
| 14  | **인증 및 ID FQDN** <br> 작동하려면 FQDN ```secure.aadcdn.microsoftonline-p.com```가 클라이언트의 Internet Explorer(IE) 또는 Edge의 신뢰할 수 있는 사이트 영역에 있어야 합니다. |  | 신뢰할 수 있는 사이트 |
| 15  |  **Microsoft Teams FQDN** <br> Internet Explorer 또는 Microsoft Edge를 사용하는 경우 먼저 제3자 쿠키를 사용하고 팀의 FQDN을 신뢰할 수 있는 사이트에 추가해야 합니다. 이는 14번째 줄에 나열된 제품군 전체의 FQDN, CDN 및 원격 분석 외에 추가되는 사항입니다. 자세한 내용은 [Microsoft Teams에 대한 알려진 문제점](https://docs.microsoft.com/microsoftteams/known-issues)을 참조하세요. |  | 신뢰할 수 있는 사이트 |
| 16  |  **SharePoint Online 및 비즈니스용 OneDrive FQDN** <br> FQDN의 '\< tenant>'가 있는 모든 '.sharepoint.com' FQDN은 클라이언트의 IE 또는 Microsoft Edge 신뢰할 수 있는 사이트 영역에 있어야 작동할 수 있습니다. 14번째 줄에 나열된 제품군 전체 FQDN, CDN 및 원격 측정 외에도 이러한 끝점을 추가해야 합니다. |  | 신뢰할 수 있는 사이트 |
| 17  | **Yammer**  <br> Yammer는 브라우저에서만 사용할 수 있으며 인증된 사용자는 프록시를 통해 전달되어야 합니다. 모든 Yammer FQDN은 클라이언트의 IE 또는 Edge의 신뢰할 수 있는 사이트 영역에 있어야 작동할 수 있습니다. |  | 신뢰할 수 있는 사이트 |
| 18  | [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/)를 사용하여 온프레미스 사용자 계정을 Azure AD에 동기화합니다. | [포트 및 프로토콜이 필요한 하이브리드 ID](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-ports), [Azure AD 연결 문제 해결](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity) 그리고 [Azure AD Connect Health 에이전트 설치](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints)를 참조합니다. | 아웃바운드 서버 전용 트래픽 |
| 19  | 온-프레미스 사용자 계정을 Azure AD에 동기화하기 위한 중국의 21 ViaNet과 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/) | \*.digicert.com:80 <BR> \*.verisign.com:80 <BR> \*.entrust.net:80 <BR> \*.chinacloudapi.cn:443 <BR> secure.aadcdn.partner.microsoftonline-p.cn:443 <BR>*.partner.microsoftonline.cn:443 <BR> <BR>[Azure AD 연결 수신 문제 해결](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity)을 참조하세요. | 아웃바운드 서버 전용 트래픽 |
| 20  | Microsoft Stream(Azure AD 사용자 토큰 필요) <BR> Office 365 월드와이드(GCC 포함) | \*.cloudapp.net <BR> \*.api.microsoftstream.com <BR> \*.notification.api.microsoftstream.com <BR> amp.azure.net <BR> api.microsoftstream.com <BR> az416426.vo.msecnd.net <BR> s0.assets-yammer.com <BR> vortex.data.microsoft.com <BR> web.microsoftstream.com <BR> TCP 포트 443  | 인바운드 서버 트래픽 |
| 21  | 다중 요소 인증 요청(서버 새로 설치 및 AD DS(Active Directory Domain Services)로 설정)에 MFA 서버를 사용하세요. | [Azure Multi-Factor Authentication Server 시작](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment)을 참조하세요.  | 아웃바운드 서버 전용 트래픽 |
| 22  | Microsoft Graph 변경 알림 | 개발자는[변경 알림](https://docs.microsoft.com/graph/webhooks?context=graph%2Fapi%2F1.0&view=graph-rest-1.0)을 활용하여 Microsoft Graph의 이벤트를 구독할 수 있습니다. | *.cloudapp.net<BR> 104.43.130.21, 137.116.169.230, 13.79.38.63, 104.214.39.228, 퍼블릭 클라우드: 168.63.250.205, 52.161.9.202, 40.68.103.62, 13.89.60.223, 23.100.95.104, 40.113.95.219, 104.214.32.10, 168.63.237.145, 52.161.110.176, 52.174.177.183 <BR> 미국 정부용 Microsoft Cloud: 52.244.231.173, 52.238.76.151, 52.244.250.211, 52.238.78.108 <BR> Microsoft Cloud Germany: 51.4.231.136, 51.5.243.223, 51.4.226.154, 51.5.244.215 <BR> 21Vianet로 운영되는 Microsoft Cloud China: 139.219.15.33, 42.159.154.223, 42.159.88.79, 42.159.155.77<BR> TCP 포트 443 <BR> 참고: 개발자는 구독을 만들 때 여러 포트를 지정할 수 있습니다.  | 인바운드 서버 트래픽 |
|||||

## <a name="related-topics"></a>관련 주제

[Office 365 끝점 관리](managing-office-365-endpoints.md)
  
[Office 365 연결 문제 해결](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[클라이언트 연결](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[콘텐츠 배달 네트워크](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure 데이터 센터 IP 범위](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 공용 IP 공간](https://www.microsoft.com/download/details.aspx?id=53602)
