---
title: 하이브리드 현대 인증 개요 및 온-프레미스 Skype를 사용 하 여 비즈니스 및 Exchange 서버에 대 한 필수 구성 요소
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 10/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: '현대 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법입니다. 비즈니스 서버 온-프레미스 및 Exchange server 온-프레미스,으로 비즈니스 하이브리드에 대 한 분할 도메인 Skype 용 Skype의 하이브리드 배포에 사용할 수 있는 것입니다. 이 문서 링크를 제공 하 고 관련된 클라이언트 (예: Outlook 및 Skype 클라이언트) 정보 중 일부에 필수 구성 요소를 설치/사용 안함 현대 인증에 대 한 문서 관련 합니다.'
ms.openlocfilehash: c10e5660d43ccce50497fccfd9d830d31ac07d55
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371112"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="41e06-106">하이브리드 현대 인증 개요 및 온-프레미스 Skype를 사용 하 여 비즈니스 및 Exchange 서버에 대 한 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="41e06-106">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="41e06-p102">현대 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법입니다. 물론에 대 한 비즈니스 서버 온-프레미스 및 Exchange server 온-프레미스, 비즈니스 하이브리드에 대 한 분할 도메인 Skype Skype의 Office 365 하이브리드 배포에 사용할 수 있는 것입니다. 이 문서 링크를 제공 하 고 관련된 클라이언트 (예: Outlook 및 Skype 클라이언트) 정보 중 일부에 필수 구성 요소를 설치/사용 안함 현대 인증에 대 한 문서 관련 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p102">Modern Authentication is a method of identity management that offers more secure user authentication and authorization. It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids. This article links to related docs about prerequisites, setup/disabling Modern Authentication, and to some of the related client (ex. Outlook and Skype clients) information.</span></span> 
  
- [<span data-ttu-id="41e06-111">현대 인증 이란?</span><span class="sxs-lookup"><span data-stu-id="41e06-111">What is Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [<span data-ttu-id="41e06-112">현대 인증을 사용 하는 경우 변경 사항은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="41e06-112">What changes when I use Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [<span data-ttu-id="41e06-113">온-프레미스 환경의 현대 인증 상태 확인</span><span class="sxs-lookup"><span data-stu-id="41e06-113">Check the Modern Authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [<span data-ttu-id="41e06-114">현대 인증 필수 구성 요소를 충족 하면?</span><span class="sxs-lookup"><span data-stu-id="41e06-114">Do you meet Modern Authentication prerequisites?</span></span>](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [<span data-ttu-id="41e06-115">시작 하기 전에 시 필요한 사항</span><span class="sxs-lookup"><span data-stu-id="41e06-115">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [<span data-ttu-id="41e06-116">현대 인증 Url 목록</span><span class="sxs-lookup"><span data-stu-id="41e06-116">List of Modern Authentication URLs</span></span>](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a><span data-ttu-id="41e06-117">현대 인증 이란?</span><span class="sxs-lookup"><span data-stu-id="41e06-117">What is Modern Authentication?</span></span>
<span data-ttu-id="41e06-118"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="41e06-118"></span></span>

<span data-ttu-id="41e06-119">(예: 랩톱 또는 휴대폰) 클라이언트와 서버 간의 통신에 대 한 음성 채팅을 하는 경우 Microsoft 구를 '현대 인증'를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-119">When talking about communication between a client (for example, your laptop or your phone) and a server, Microsoft uses the phrase 'Modern authentication'.</span></span>
  
<span data-ttu-id="41e06-p103">현대 인증은 인증 및 권한 부여 방법으로 액세스 정책에 이미 익숙한 있을 사용 하는 일부 보안 조치의 조합에 대 한 포괄적인 용어입니다. 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p103">Modern authentication is an umbrella term for a combination of authentication and authorization methods, as well as some security measures that rely on access policies that you may already be familiar with. It includes:</span></span>
  
- <span data-ttu-id="41e06-122">**인증 방법**: 다중 요소 인증 클라이언트 인증서 기반 인증 및 Active Directory 인증 라이브러리 ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-122">**Authentication methods**: Multi-factor Authentication; Client Certificate-based authentication; and the Active Directory Authentication Library ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).</span></span>
    
- <span data-ttu-id="41e06-123">**권한 부여 방법**: OAuth (Open Authorization)의 Microsoft의 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-123">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth).</span></span> 
    
- <span data-ttu-id="41e06-124">**조건부 액세스 정책**: 모바일 응용 프로그램 관리 (MAM) 및 Azure Active Directory 조건부 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-124">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory Conditional Access.</span></span> 
    
<span data-ttu-id="41e06-125">현대 인증 된 사용자 id를 관리 관리자에 게 제공, 사용 하 여 리소스 보안을 제공 하 고 두 온-프레미스 (Exchange와 비즈니스를 위한 Skype)에 id 관리의 보안을 강화 메서드를 제공 하는 경우 Exchange 하이브리드 다양 한 도구 및 비즈니스 하이브리드/분할 도메인 시나리오에 대 한 Skype 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-125">Managing user identities with Modern Authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="41e06-p104">Skype 비즈니스를 위한 Exchange와의 밀접 하 게 작동 하기 때문에 사용자에 게는 표시 하는 비즈니스 클라이언트에 대 한 로그인 동작 Skype Exchange의 현대 인증 상태에 따라 영향 됩니다에 유의 합니다. 이 비즈니스 분할 도메인 하이브리드에 대 한 Skype 있는 경우에 적용 됩니다. 또한 현대 인증 사용을 지 원하는 비즈니스 하이브리드에 대 한 Skype 유형의 흔히 이라고 ' 분할 도메인 ' (비즈니스 온라인 용 Skype와 비즈니스에서-prem, 용 Skype가 분할 도메인 및 사용자가 두 위치에 있는).</span><span class="sxs-lookup"><span data-stu-id="41e06-p104">Be aware that because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will be effected by the Modern Authentication status of Exchange. This will also apply if you have a Skype for Business split-domain hybrid. Also, the type of Skype for Business Hybrid that supports the use of Modern Authentication is often called a 'split-domain' (in a split-domain, you have both Skype for Business Online and Skype for Business on-prem, and users are homed in both locations).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="41e06-p105">않은 있습니다 한다는 것을 알, 2017 년 8 월 기준 온라인 비즈니스를 위한 Skype를 포함 하 고 온라인 교환 하는 모든 새 Office 365 테 넌은 기본적으로 사용 하도록 설정 하는 현대 인증? 기존 테 넌 트 기본 MA 상태로 변경을 갖지 않도록 하지만 모든 새 테 넌 트 자동으로 확장된 기능 집합을 identity 위에 나열 된 참조를 지원 합니다. 비즈니스를 위한 Skype에 대 한 MA 상태를 온라인 확인 하려면 전역 관리자 자격 증명을 가진 비즈니스 온라인 PowerShell 용 Skype를 사용할 수 있습니다. 실행 `Get-CsOAuthConfiguration` -ClientADALAuthOverride의 출력을 확인 합니다. -ClientADALAuthOverride은 '허용 되는 경우' 현대 인증 켜져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p105">Did you know that, as of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have Modern Authentication enabled by default? Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above. To check your MA status for Skype for Business online, you can use Skype for Business online PowerShell with Global Admin credentials. Run `Get-CsOAuthConfiguration` to check the output of -ClientADALAuthOverride. If -ClientADALAuthOverride is 'Allowed' your Modern Authentication is on.</span></span> 
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="41e06-134">현대 인증을 사용 하는 경우 변경 사항은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="41e06-134">What changes when I use Modern Authentication?</span></span>
<span data-ttu-id="41e06-135"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="41e06-135"></span></span>

<span data-ttu-id="41e06-p106">온-프레미스 Skype와 현대 인증을 사용 하 여 비즈니스 또는 Exchange 서버에 대 한 때 넌 아직도 *인증* 사용자가 온-프레미스, 하지만 *권한 부여* 의 story 리소스 (예: 파일 또는 전자 메일) 변경 내용에 대 한 액세스 합니다. EvoSTS (보안 토큰 서비스 Azure AD에서 사용 하는)에서 MA 결과 구성 하는 동안 수행 하는 단계 클라이언트 및 서버 통신 하는 방법에 대 한 최신 인증은 하지만이 인해, 비즈니스 및 Exchange server 온-프레미스 용 Skype에 대 한 인증 서버로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p106">When using Modern Authentication with on-premises Skype for Business or Exchange server, you're still  *authenticating*  users on-premises, but the story of  *authorizing*  their access to resources (like files or emails) changes. This is why, though Modern Authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span> 
  
<span data-ttu-id="41e06-p107">EvoSTS 하 여 변경 내용을 사용 하면 온-프레미스 클라이언트, 권한 부여에 대 한 OAuth (토큰 발급) 기능을 활용 하는 서버 및 클라우드 (예: 다단계 인증)의 일반적인 온-프레미스 사용 하 여 보안 메서드를 사용 하면 수 있습니다. 또한는 evoSTS 요청의 일부로 자신의 암호를 제공 하지 않고 리소스에 대 한 액세스를 요청할 수 있도록 하는 토큰을 발급 합니다. 사용자가 있는 위치에 관계 없이 (의 온라인 또는 온-프레미스), 필요한 리소스를 호스팅하는 어느 위치에 관계 없이 EvoSTS 될 핵심 요소인 현대 인증을 구성한 후에 사용자 및 클라이언트의 권한을 부여 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p107">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication). Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request. No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once Modern Authentication is configured.</span></span>
  
<span data-ttu-id="41e06-p108">I 의미의 예는 다음과 같습니다. Skype 비즈니스 클라이언트에 대 한 사용자를 대신 하 여 일정 정보를 보려면 Exchange 서버에 액세스 하는 경우에 Active Directory 인증 라이브러리 (ADAL)을 사용 하 여 되도록 합니다. ADAL 코드 라이브러리 하도록 디렉터리의 보안된 리소스를 OAuth 보안 토큰을 사용 하는 클라이언트 응용 프로그램에 사용할 수 있도록 설정 합니다. 클레임을 확인 하 고 토큰 (암호 대신), 리소스에 대 한 사용자 액세스 권한을 부여 하려면 exchange OAuth와 ADAL 작동 합니다. 과거에 인증 기관에서 이와 같은-사용자 클레임의 유효성을 검사 하 고 필요한 토큰을 발급 하는 방법을 알고 있는 서버--트랜잭션 되었을 수 있습니다는 보안 토큰 서비스 온-프레미스, 또는 Active Directory Federation Services도 합니다. 그러나 현대 인증 클라우드에서 Azure Active Directory (Azure AD)와 해당 기관 중앙 집중화합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p108">Here's an example of what I mean. If Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so. ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens. ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource. In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services. However, Modern Authentication centralizes that authority with Azure Active Directory (Azure AD) in the Cloud.</span></span>
  
<span data-ttu-id="41e06-147">즉, 하는 경우에 Exchange 서버와 Skype 비즈니스 환경을 완전히 수에 대 한 온-프레미스, 권한을 부여 하는 서버는 온라인 상태 이며, 온-프레미스 환경을 만들고 사무실에 대 한 연결을 유지 관리할 수 있어야 합니다. 클라우드 (및 해당 디렉터리도 구독을 사용 하는 Azure Active Directory 인스턴스)에 365 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-147">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure Active Directory instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="41e06-p109">기능 변경 되지 않습니다. 분할 도메인 하이브리드 또는 비즈니스 및 Exchange server 온-프레미스 용 Skype를 사용 하 든 모든 사용자에 게 *온-프레미스* 를 먼저 인증 해야 합니다. 하이브리드 구현 하는 현대 인증, Lyncdiscovery 및 자동 검색 온-프레미스 서버를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p109">What doesn't change? Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate  *on-premises*  . In a hybrid implementation of Modern Authentication, Lyncdiscovery and Autodiscovery point to your on-premises server.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="41e06-151">MA에 대해서는 지원 되는 비즈니스 토폴로지에 대 한 특정 Skype 알아야 하는 경우 [오른쪽 여기서 설명](https://technet.microsoft.com/en-us/library/mt803262.aspx)하는 것이입니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-151">If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/en-us/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="41e06-152">온-프레미스 환경의 현대 인증 상태 확인</span><span class="sxs-lookup"><span data-stu-id="41e06-152">Check the Modern Authentication status of your on-premises environment</span></span>
<span data-ttu-id="41e06-153"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="41e06-153"></span></span>

<span data-ttu-id="41e06-p110">서비스 OAuth/S2S을 활용 하는 경우 사용 되는 인증 서버를 변경 하는 현대 인증, 때문에 비즈니스 및 Exchange 환경에 대 한 사용자 Skype에 대 한 최신 인증이 설정 또는 해제 하는 경우 알고 해야 합니다. 실행 하 여 온-프레미스, 비즈니스 서버에 대 한 Exchange 또는 Skype 상태를 확인할 수 있습니다는 `Get-CSOAuthConfiguration` PowerShell에 명령 합니다. 명령이 빈 'OAuthServers' 속성을 반환 하는 경우 최신 인증 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p110">Because Modern Authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if Modern Authentication is On or Off for your Skype for Business and Exchange environment. You can check the status on your Exchange or Skype for Business servers, on premises, by running the `Get-CSOAuthConfiguration` command in PowerShell. If the command returns an empty 'OAuthServers' property, then Modern Authentication is disabled.</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="41e06-157">현대 인증 필수 구성 요소를 충족 하면?</span><span class="sxs-lookup"><span data-stu-id="41e06-157">Do you meet Modern Authentication prerequisites?</span></span>

<span data-ttu-id="41e06-158">확인 하 고 계속 하기 전에 대화 목록 오프 이러한 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-158">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="41e06-159">**비즈니스 관련 용 Skype**</span><span class="sxs-lookup"><span data-stu-id="41e06-159">**Skype for Business specific**</span></span>
    
  - <span data-ttu-id="41e06-160">모든 서버에는 SFB 서버 2015 c u 5 있어야 합니다. 이상</span><span class="sxs-lookup"><span data-stu-id="41e06-160">All servers must have SFB Server 2015 CU5 or later</span></span>
    
  - <span data-ttu-id="41e06-161">**예외** -지속 가능성 분기 기기 (SBA) (Lync 2013 기준) 현재 버전에 있을 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="41e06-161">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span> 
    
  - <span data-ttu-id="41e06-162">SIP 도메인이 Office 365에서 페더레이션 도메인으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-162">Your SIP domain is added as a Federated domain in Office 365</span></span>
    
  - <span data-ttu-id="41e06-163">모든 SFB 프런트엔드 인터넷을 통해 Office 365 인증 Url (TCP 443)로 아웃 바운드 연결 되어 있어야 하 고 Office 365 Url 및 IP 행 56 및 [의 ''Microsoft 365 일반적인 및 Office Online 섹션의 125에 나열 된 잘 알려진 인증서 루트 Crl (TCP 80) 주소 범위](urls-and-ip-address-ranges.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-163">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 56 and 125 of the 'Microsoft 365 Common and Office Online' section of [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
    
 <span data-ttu-id="41e06-164">**참고 사항** 인터넷 액세스를 위한 프록시 서버를 사용 하는 비즈니스 프런트엔드 서버에 대 한 사용자 Skype, 하는 경우 각 프런트엔드에 대 한 web.config 파일의 구성 섹션에서 사용 되는 프록시 서버 IP와 포트 번호를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-164">**Note** If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span> 
  
- <span data-ttu-id="41e06-165">비즈니스 서버 2015\Web Components\Web에 대 한 C:\Program Files\Skype ticket\int\web.config</span><span class="sxs-lookup"><span data-stu-id="41e06-165">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
    
- <span data-ttu-id="41e06-166">비즈니스 서버 2015\Web Components\Web에 대 한 C:\Program Files\Skype ticket\ext\web.config</span><span class="sxs-lookup"><span data-stu-id="41e06-166">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> <span data-ttu-id="41e06-167">RSS [Office 365 Url 및 IP 주소 범위를](urls-and-ip-address-ranges.md) 필요한 Url의 최신 목록을와 최신 정보에 대 한 피드를 구독 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-167">Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) to stay current with the latest listings of required URLs.</span></span> 
  
- <span data-ttu-id="41e06-168">**특정 Exchange 서버**</span><span class="sxs-lookup"><span data-stu-id="41e06-168">**Exchange Server specific**</span></span>
    
  - <span data-ttu-id="41e06-169">Exchange server 2013 CU19 중 하나를 사용 하는 위로, 또는 Exchange server 2016 CU8 및 up 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-169">You're using either Exchange server 2013 CU19 and up, or Exchange server 2016 CU8 and up.</span></span>
    
  - <span data-ttu-id="41e06-170">환경에 없는 Exchange server 2010 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-170">There is no Exchange server 2010 in the environment.</span></span>
    
  - <span data-ttu-id="41e06-p111">SSL 오프 로딩 구성 되지 않았습니다. SSL 종료 하 고 다시 암호화가 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p111">SSL Offloading is not configured. SSL termination and re-encryption is supported.</span></span>
    
  - <span data-ttu-id="41e06-173">서버에서 인터넷에 연결할 수 있도록 하는 프록시 서버 인프라를 이용 하는 환경, 이벤트에서 모든 Exchange 서버 [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) 속성에 정의 된 프록시 서버에 있는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-173">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
    
- <span data-ttu-id="41e06-174">**Exchange 클라이언트와 프로토콜 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="41e06-174">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="41e06-175">다음 클라이언트 현대 인증을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-175">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="41e06-176">**클라이언트**</span><span class="sxs-lookup"><span data-stu-id="41e06-176">**Clients**</span></span>|<span data-ttu-id="41e06-177">**기본 프로토콜**</span><span class="sxs-lookup"><span data-stu-id="41e06-177">**Primary Protocol**</span></span>|<span data-ttu-id="41e06-178">**참고**</span><span class="sxs-lookup"><span data-stu-id="41e06-178">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="41e06-179">Outlook 2013 및 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="41e06-179">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="41e06-180">HTTP를 통한 MAPI</span><span class="sxs-lookup"><span data-stu-id="41e06-180">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="41e06-181">이러한 클라이언트 (일반적으로 사용 하거나 새 설치 하 고 위의 Exchange 2013 서비스 팩 1의 경우에 True); 함께 현대 인증을 활용 하기 위해 Exchange 내에서 HTTP 통한 MAPI는 사용할 수 있어야 자세한 내용은 [Office 2013 및 Office 2016 클라이언트 응용 프로그램에 대 한 인증 작동 방법을 현대](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="41e06-181">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).</span></span>  <br/> <span data-ttu-id="41e06-182">Outlook;의 최소 필요한 빌드를 실행 하는 확인 [Windows Installer (MSI)을 사용 하는 Outlook의 버전에 대 한 최신 업데이트](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="41e06-182">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="41e06-183">Mac용 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="41e06-183">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="41e06-184">Exchange Web Services</span><span class="sxs-lookup"><span data-stu-id="41e06-184">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="41e06-185">iOS 및 Android용 Outlook</span><span class="sxs-lookup"><span data-stu-id="41e06-185">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="41e06-186">자세한 정보를 [사용 하 여 하이브리드 iOS와 Android에 대 한 Outlook 사용 하 여 최신 인증을](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="41e06-186">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="41e06-187">Exchange ActiveSync 클라이언트 (예: iOS11 메일)</span><span class="sxs-lookup"><span data-stu-id="41e06-187">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="41e06-188">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="41e06-188">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="41e06-189">현대 인증을 지 원하는 Exchange ActiveSync 클라이언트에 대 한 기본 인증에서 현대 인증으로 전환 하기 위해 프로필을 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-189">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="41e06-190">**일반 필수 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="41e06-190">**General prerequisites**</span></span>
    
  - <span data-ttu-id="41e06-191">ADFS를 사용 하는 경우 Windows 2012 R2 ADFS 3.0 있어야 이상인 페더레이션에 대 한</span><span class="sxs-lookup"><span data-stu-id="41e06-191">If you use ADFS, you should have Windows 2012 R2 ADFS 3.0 and above for federation</span></span>
    
  - <span data-ttu-id="41e06-192">Identity 구성을 AAD 연결 하 여 지원 되는 형식 중 하나는 (암호 해시 동기화, 통과 인증 온-프레미스 STS Office 365에서 지 원하는와 같은 et cetera.)</span><span class="sxs-lookup"><span data-stu-id="41e06-192">Your identity configurations are any of the types supported by AAD Connect (such as password hash sync, pass-through authentication, on-premises STS supported by Office 365, et cetera.)</span></span>
    
  - <span data-ttu-id="41e06-193">AAD 연결 구성 및 사용자 복제 및 동기화에 대 한 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-193">You have AAD Connect configured and functioning for user replication and sync.</span></span>
    
  - <span data-ttu-id="41e06-194">해당 하이브리드 온-프레미스 및 Office 365 간의 작동 확인:</span><span class="sxs-lookup"><span data-stu-id="41e06-194">You have verified that hybrid is working between your on-premises and Office 365:</span></span>
    
  - <span data-ttu-id="41e06-195">Exchange 하이브리드에 대 한 공식적으로 지원 문을 이라는 현재 CU 또는 현재 CU-1 중 하나를 사용 하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-195">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    
  - <span data-ttu-id="41e06-196">(현대 인증을 사용 하는 것이 원하는 경우 확인 하이브리드 테스트 사용자와 온-프레미스 테스트 사용자를 홈으로 지정 된 Office 365의 비즈니스 데스크톱 클라이언트 (Skype와 현대 인증을 사용할 경우)에 대 한 Skype와 Microsoft Outlook에 로그인 할 수 있습니다. Exchange)입니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-196">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use Modern Authentication with Skype) and Microsoft Outlook (if you want so use Modern Authentication with Exchange).</span></span>
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="41e06-197">시작 하기 전에 시 필요한 사항</span><span class="sxs-lookup"><span data-stu-id="41e06-197">What else do I need to know before I begin?</span></span>
<span data-ttu-id="41e06-198"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="41e06-198"></span></span>

1. <span data-ttu-id="41e06-p112">온-프레미스 서버에 대 한 모든 시나리오와 관련 현대 인증 온-프레미스 설정 (사실에 대 한 비즈니스를 위한 Skype 지원 되는 토폴로지 목록이 방법이) 인증 및 권한 부여 하는 일을 담당 하는 서버에 있는 Microsoft 클라우드 (있도록 AAD의 보안 토큰 서비스), 'evoSTS' 라는), Azure Active Directory (AAD) Url 또는 비즈니스 또는 Exchange에 대 한 두 Skype의 온-프레미스 설치에서 사용 하는 네임 스페이스에 대 한 업데이트 하 고 있습니다. 따라서 온-프레미스 서버 Microsoft 클라우드 의존 관계 적용 됩니다. 이 작업을 수행 '하이브리드 인증' 구성 간주 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p112">All the scenarios for on-premises servers involve setting up Modern Authentication on-premises (in fact, for Skype for Business there is a list of Supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (AAD's security token service, called 'evoSTS'), and updating Azure Active Directory (AAD) about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange. Therefore, on-premises servers take on a Microsoft Cloud dependency. Taking this action could be considered configuring 'hybrid auth'.</span></span>
    
2. <span data-ttu-id="41e06-p113">이 문서 링크 아웃 다른 사용자에 게 선택 하는데 도움이 되는 지원 되는 (비즈니스용 Skype에만 필요), 현대 인증 토폴로지 및 사용 방법 해당 개요 설치 단계에서 문서 또는 Exchange 온-프레미스에 대 한 최신 인증을 사용 하지 않도록 설정 하는 단계 비즈니스 온-프레미스 용 Skype 하 고 있습니다. 좋아하는 홈-기반 서버 환경에서 현대 인증을 사용 하기 위한 필요 하려고 하는 경우 브라우저에서이 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="41e06-p113">This article links out to others that will help you choose supported Modern Authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable Modern Authentication, for Exchange on-premises and Skype for Business on-premises. Favourite this page in your browser if you're going to need a home-base for using Modern Authentication in your server environment.</span></span>
    
## <a name="list-of-modern-authentication-urls"></a><span data-ttu-id="41e06-204">현대 인증 Url 목록</span><span class="sxs-lookup"><span data-stu-id="41e06-204">List of Modern Authentication URLs</span></span>
<span data-ttu-id="41e06-205"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="41e06-205"></span></span>

- [<span data-ttu-id="41e06-206">Exchange Server 온-프레미스 현대 인증을 사용 하도록 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="41e06-206">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="41e06-207">현대 인증을 지원 되는 비즈니스 토폴로지 용 Skype</span><span class="sxs-lookup"><span data-stu-id="41e06-207">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [<span data-ttu-id="41e06-208">현대 인증을 사용 하 여 비즈니스 온-프레미스 용 Skype를 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="41e06-208">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="41e06-209">비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="41e06-209">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

