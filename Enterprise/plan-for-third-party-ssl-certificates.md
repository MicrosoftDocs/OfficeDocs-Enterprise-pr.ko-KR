---
title: Office 365용 타사 SSL 인증서 계획
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
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
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: '요약: AD FS, Exchange Online 서비스 및 Exchange 웹 서비스를 사용하는 Exchange 온-프레미스 및 하이브리드와 SSO에 필요한 SSL 인증서를 설명합니다.'
ms.openlocfilehash: 1746cf5059ba83e225e4a2d55c8eebc082366362
ms.sourcegitcommit: bdd0083dc9dc62994de29421a1f4056ebe27f15f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "29952474"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="72963-103">Office 365용 타사 SSL 인증서 계획</span><span class="sxs-lookup"><span data-stu-id="72963-103">Plan for third-party SSL certificates for Office 365</span></span>

 <span data-ttu-id="72963-104">**요약:** Exchange 온-프레미스 및 하이브리드, AD FS를 사용 하 여 SSO에 필요한 SSL 인증서를 설명 Exchange Online 서비스 및 Exchange 웹 서비스.</span><span class="sxs-lookup"><span data-stu-id="72963-104">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="72963-105">클라이언트와 Office 365 환경 간의 통신을 암호화 하려면 인프라 서버에 타사 Secure Socket Layer (SSL) 인증서를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-105">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="72963-106">이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="72963-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="72963-107">인증서가 필요한 Office 365 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="72963-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="72963-108">Exchange 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="72963-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="72963-109">SSO(Single Sign-On). AD FS(Active Directory Federation Services) 페더레이션 서버 및 AD FS 페더레이션 서버 프록시에 모두 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="72963-110">자동 검색, 외부에서 Outlook 사용, 및 Exchange 웹 서비스 등의 Exchange Online 서비스</span><span class="sxs-lookup"><span data-stu-id="72963-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="72963-111">Exchange 혼성 서버</span><span class="sxs-lookup"><span data-stu-id="72963-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="72963-112">Exchange 온-프레미스용 인증서</span><span class="sxs-lookup"><span data-stu-id="72963-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="72963-113">디지털 인증서를 사용 하는 온-프레미스 Exchange 조직과 Exchange Online 간의 통신을 안전 하 게를 [인증서 요구 사항 이해](https://go.microsoft.com/fwlink/p/?LinkID=243657)TechNet 문서를 참조 하는 방법에 대 한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="72963-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="72963-114">Single Sign-On용 인증서</span><span class="sxs-lookup"><span data-stu-id="72963-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="72963-p101">단순한 single sign on 환경을 강력한 보안이 포함 된 사용자에 게을 제공 하려면 다음 표에 표시 된 인증서는 페더레이션 서버 또는 페더레이션 서버 프록시에 필요 합니다. 아래 표에 Active Directory Federation Services (AD FS)에 중점을 두고, 것 권한도 부여 [타사 id 공급자를 사용 하 여](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)대 한 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-p101">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies. The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="72963-117">**인증서 유형**</span><span class="sxs-lookup"><span data-stu-id="72963-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="72963-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="72963-118">**Description**</span></span> <br/> |<span data-ttu-id="72963-119">**배포하기 전에 알아야 할 내용**</span><span class="sxs-lookup"><span data-stu-id="72963-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="72963-120">**SSL 인증서(서버 인증 인증서라고도 함)**</span><span class="sxs-lookup"><span data-stu-id="72963-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="72963-121">페더레이션 서버, 클라이언트 및 페더레이션 서버 프록시 컴퓨터 간의 통신을 보호하는 데 사용되는 표준 SSL 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="72963-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="72963-p102">AD FS에는 SSL 인증서가 필요합니다. 기본적으로 AD FS 기본 웹사이트에서 인터넷 정보 서비스 (IIS)에 대해 구성 된 SSL 인증서를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-p102">AD FS requires an SSL certificate. By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).  </span></span><br/> <span data-ttu-id="72963-p103">이 SSL 인증서의 주체 이름은 배포 하는 AD FS의 각 인스턴스에 대 한 페더레이션 서비스 (FS) 이름을 결정 하는데 사용 됩니다. 모든 새 CA (인증 기관)에 대 한 주체 이름을 선택 하는 것이 좋습니다.-최고 회사 또는 조직의 Office 365로의 이름을 나타내는 인증서를 발급 합니다. 이 이름은 인터넷 라우팅 가능 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-p103">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy. Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365. This name must be Internet-routable.  </span></span><br/><span data-ttu-id="72963-127">**주의:** AD FS 하려면 점 없는 (약식 이름) 주체 이름이 SSL 인증서에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="72963-128">**권장 사항:** AD FS의 클라이언트에서이 인증서를 신뢰 해야, 때문에 공용 (타사) CA에서 또는 공개적으로 신뢰할 수 있는 루트;에 종속 되는 CA에서 발급 한 SSL 인증서를 사용 하는 것이 좋습니다. VeriSign, Thawte 등의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="72963-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="72963-129">**토큰 서명 인증서**</span><span class="sxs-lookup"><span data-stu-id="72963-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="72963-130">페더레이션 서버에서 발급 하며 해당 Office 365를 허용 하 고 유효성을 검사 하는 모든 토큰의 보안 서명에 사용 되는 표준 X.509 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="72963-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="72963-p104">토큰 서명 인증서는 FS에서 신뢰할 수 있는 루트에 연결 하는 개인 키를 포함 해야 합니다. 기본적으로 AD FS에는 자체 서명 된 인증서를 만듭니다. 그러나 조직의 필요에 따라 변경할 수 있습니다이 인증서를 CA에서 발급 한 인증서를 AD FS 관리 스냅인을 사용 하 여.</span><span class="sxs-lookup"><span data-stu-id="72963-p104">The token-signing certificate must contain a private key that chains to a trusted root in the FS. By default, AD FS creates a self-signed certificate. However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.  </span></span><br/><span data-ttu-id="72963-p105">**주의:** 토큰 서명 인증서가는 FS의 안정성과 중요 합니다. 인증서를 변경 하는 경우 Office 365 변경 알려야 합니다. 알림이 제공 되지 않은 경우 사용자가 Office 365 서비스 제품을 로그인 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72963-p105">**Caution:** The token-signing certificate is critical to the stability of the FS. If the certificate is changed, Office 365 must be notified of the change. If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="72963-p106">**권장 사항:** AD FS에서 생성 되는 자체 서명 된 토큰 서명 인증서를 사용 하는 것이 좋습니다. 이렇게 하 여 관리이 인증서 하면 기본적으로 합니다. 예,이 인증서가 만료 바로, AD FS 새로운 자체 서명 된 인증서를이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72963-p106">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS. By doing so, it manages this certificate for you by default. For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.  </span></span><br/> |
   
<span data-ttu-id="72963-140">페더레이션 서버 프록시의 경우 다음 표에서 설명하는 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="72963-141">**인증서 유형**</span><span class="sxs-lookup"><span data-stu-id="72963-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="72963-142">**설명**</span><span class="sxs-lookup"><span data-stu-id="72963-142">**Description**</span></span> <br/> |<span data-ttu-id="72963-143">**배포하기 전에 알아야 할 내용**</span><span class="sxs-lookup"><span data-stu-id="72963-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="72963-144">SSL 인증서</span><span class="sxs-lookup"><span data-stu-id="72963-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="72963-145">페더레이션 서버, 페더레이션 서버 프록시 및 인터넷 클라이언트 컴퓨터 간의 통신을 보호하는 데 사용되는 표준 SSL 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="72963-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="72963-146">이 SSL 인증서를 성공적으로 AD FS 페더레이션 서버 프록시 구성 마법사를 실행 하기 전에 IIS의 기본 웹사이트에 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="72963-147">이 인증서의 주체 이름은 회사 네트워크의 페더레이션 서버에 대해 구성된 SSL 인증서의 주체 이름과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="72963-148">**권장 사항:** 이 페더레이션 서버 프록시가 연결되는 페더레이션 서버에 대해 구성된 것과 같은 서버 인증 인증서를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="72963-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="72963-149">자동 검색, 외부에서 Outlook 사용 및 Active Directory 동기화에 대 한 인증서</span><span class="sxs-lookup"><span data-stu-id="72963-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="72963-p107">외부 연결 Exchange 2013, Exchange 2010, Exchange 2007 및 Exchange 2003 클라이언트 액세스 서버 (클래스) 자동 검색, 외부에서 Outlook 사용, 및 Active Directory 동기화 서비스에 대 한 보안 연결에 대 한 타사 SSL 인증서가 필요 합니다. 온-프레미스 환경에 설치 된이 인증서를 이미 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72963-p107">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services. You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="72963-152">Exchange 하이브리드 서버용 인증서</span><span class="sxs-lookup"><span data-stu-id="72963-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="72963-p108">외부 연결 Exchange 하이브리드 서버 또는 서버 타사 SSL 인증서를 Exchange Online 서비스와의 보안 연결에 필요합니다. 타사 SSL 공급자에서이 인증서를 가져오려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72963-p108">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service. You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="72963-155">Office 365 인증서 체인</span><span class="sxs-lookup"><span data-stu-id="72963-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="72963-p109">이 문서는 인프라에 설치 해야할 수 인증서를 설명 합니다. 이 Office 365 서버에 설치 된 인증서에 대 한 자세한 내용은 [Office 365 인증서 체인](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="72963-p109">This article describes the certificates you may need to install on your infrastructure. For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  

