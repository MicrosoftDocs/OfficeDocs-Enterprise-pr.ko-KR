---
title: Office 365용 타사 SSL 인증서 계획
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: '요약: AD FS, Exchange Online 서비스 및 Exchange 웹 서비스를 사용 하는 Exchange 온-프레미스 및 하이브리드, SSO에 필요한 SSL 인증서에 대해 설명 합니다.'
ms.openlocfilehash: 92425793d616f642fb78331a965b1a4a2dff071f
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747690"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="695c2-103">Office 365용 타사 SSL 인증서 계획</span><span class="sxs-lookup"><span data-stu-id="695c2-103">Plan for third-party SSL certificates for Office 365</span></span>

<span data-ttu-id="695c2-104">*이 문서는 Office 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="695c2-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

 <span data-ttu-id="695c2-105">**요약:** AD FS, Exchange Online 서비스 및 Exchange 웹 서비스를 사용 하는 Exchange 온-프레미스 및 하이브리드, SSO에 필요한 SSL 인증서에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-105">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="695c2-106">클라이언트와 Office 365 환경 간의 통신을 암호화 하려면 인프라 서버에 타사 SSL (Secure sockets Layer) 인증서가 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-106">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="695c2-107">이 문서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-107">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="695c2-108">다음 Office 365 구성 요소에 대 한 인증서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-108">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="695c2-109">Exchange 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="695c2-109">Exchange on-premises</span></span>
    
- <span data-ttu-id="695c2-110">SSO (Active Directory Federation Services) 페더레이션 서버 및 AD FS 페더레이션 서버 프록시 모두에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-110">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="695c2-111">자동 검색, 외부에서 Outlook 사용, Exchange 웹 서비스 등의 exchange Online 서비스</span><span class="sxs-lookup"><span data-stu-id="695c2-111">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="695c2-112">Exchange 하이브리드 서버</span><span class="sxs-lookup"><span data-stu-id="695c2-112">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="695c2-113">Exchange 온-프레미스 용 인증서</span><span class="sxs-lookup"><span data-stu-id="695c2-113">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="695c2-114">디지털 인증서를 사용 하 여 온-프레미스 Exchange 조직과 Exchange Online 보안 간의 통신을 수행 하는 방법에 대 한 개요는 [인증서 요구 사항 이해](https://go.microsoft.com/fwlink/p/?LinkID=243657)TechNet 문서를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="695c2-114">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="695c2-115">Single Sign-on 용 인증서</span><span class="sxs-lookup"><span data-stu-id="695c2-115">Certificates for Single Sign-On</span></span>

<span data-ttu-id="695c2-116">강력한 보안이 포함 된 단순한 single sign-on 환경을 사용자에 게 제공 하기 위해 페더레이션 서버 또는 페더레이션 서버 프록시에 다음 표에 나와 있는 인증서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-116">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies.</span></span> <span data-ttu-id="695c2-117">아래 표에서는 AD FS (Active Directory Federation Services)에 대해 설명 하며 타사 [id 공급자를 사용 하](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)는 방법에 대 한 자세한 내용도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-117">The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="695c2-118">**인증서 유형**</span><span class="sxs-lookup"><span data-stu-id="695c2-118">**Certificate Type**</span></span> <br/> |<span data-ttu-id="695c2-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="695c2-119">**Description**</span></span> <br/> |<span data-ttu-id="695c2-120">**배포 하기 전에 알아야 할 사항**</span><span class="sxs-lookup"><span data-stu-id="695c2-120">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="695c2-121">**SSL 인증서 (서버 인증 인증서 라고도 함)**</span><span class="sxs-lookup"><span data-stu-id="695c2-121">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="695c2-122">페더레이션 서버, 클라이언트 및 페더레이션 서버 프록시 컴퓨터 간의 통신을 보호 하는 데 사용 되는 표준 SSL 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-122">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="695c2-123">AD FS에 SSL 인증서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-123">AD FS requires an SSL certificate.</span></span> <span data-ttu-id="695c2-124">기본적으로 AD FS는 IIS (인터넷 정보 서비스)의 기본 웹 사이트에 대해 구성 된 SSL 인증서를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-124">By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).</span></span>  <br/> <span data-ttu-id="695c2-125">이 SSL 인증서의 주체 이름은 배포 하는 각 AD FS 인스턴스에 대 한 FS (페더레이션 서비스) 이름을 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-125">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy.</span></span> <span data-ttu-id="695c2-126">회사 또는 조직의 이름을 Office 365에서 가장 잘 나타내는 새 CA (인증 기관) 인증서의 주체 이름을 선택 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-126">Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365.</span></span> <span data-ttu-id="695c2-127">이 이름은 인터넷 경로를 지정할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-127">This name must be Internet-routable.</span></span>  <br/><span data-ttu-id="695c2-128">**주의:** AD FS를 사용 하려면이 SSL 인증서에 점 없는 (약식 이름) 주체 이름이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-128">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="695c2-129">**권장 사항:** 이 인증서는 AD FS의 클라이언트에서 신뢰할 수 있어야 하므로 공용 (타사) CA 또는 공개적으로 신뢰할 수 있는 루트의 하위 CA에서 발급 한 SSL 인증서를 사용 하는 것이 좋습니다. 예를 들어 VeriSign 또는 Thawte를 들 있습니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-129">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="695c2-130">**토큰 서명 인증서**</span><span class="sxs-lookup"><span data-stu-id="695c2-130">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="695c2-131">페더레이션 서버에서 발급 하는 모든 토큰에 안전 하 게 서명을 하는 데 사용 되 고, Office 365에서 수락 하 고 유효성을 검사 하는 표준 x.509 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-131">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="695c2-132">토큰 서명 인증서에는 FS의 신뢰할 수 있는 루트에 연결 되는 개인 키가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-132">The token-signing certificate must contain a private key that chains to a trusted root in the FS.</span></span> <span data-ttu-id="695c2-133">기본적으로 AD FS는 자체 서명 된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-133">By default, AD FS creates a self-signed certificate.</span></span> <span data-ttu-id="695c2-134">그러나 조직의 요구 사항에 따라 AD FS 관리 스냅인을 사용 하 여이 인증서를 CA 발급 인증서로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-134">However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.</span></span>  <br/><span data-ttu-id="695c2-135">**주의:** 토큰 서명 인증서는 ADFS 안정성에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-135">**Caution:** The token-signing certificate is critical to the stability of the FS.</span></span> <span data-ttu-id="695c2-136">인증서가 변경 되 면 변경 내용을 Office 365에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-136">If the certificate is changed, Office 365 must be notified of the change.</span></span> <span data-ttu-id="695c2-137">알림이 제공 되지 않으면 사용자가 Office 365 서비스 제품에 로그인 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-137">If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="695c2-138">**권장 사항:** AD FS에서 생성 된 자체 서명 된 토큰 서명 인증서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-138">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS.</span></span> <span data-ttu-id="695c2-139">이렇게 하면 기본적으로이 인증서가 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-139">By doing so, it manages this certificate for you by default.</span></span> <span data-ttu-id="695c2-140">예를 들어이 인증서가 만료 되려고 하면 AD FS는 자체 서명 된 새 인증서를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-140">For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.</span></span>  <br/> |
   
<span data-ttu-id="695c2-141">페더레이션 서버 프록시에는 다음 표에 설명 된 인증서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-141">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="695c2-142">**인증서 유형**</span><span class="sxs-lookup"><span data-stu-id="695c2-142">**Certificate Type**</span></span> <br/> |<span data-ttu-id="695c2-143">**설명**</span><span class="sxs-lookup"><span data-stu-id="695c2-143">**Description**</span></span> <br/> |<span data-ttu-id="695c2-144">**배포 하기 전에 알아야 할 사항**</span><span class="sxs-lookup"><span data-stu-id="695c2-144">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="695c2-145">SSL 인증서</span><span class="sxs-lookup"><span data-stu-id="695c2-145">SSL certificate</span></span>  <br/> |<span data-ttu-id="695c2-146">페더레이션 서버, 페더레이션 서버 프록시 및 인터넷 클라이언트 컴퓨터 간의 통신을 보호 하는 데 사용 되는 표준 SSL 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-146">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="695c2-147">AD FS 페더레이션 서버 프록시 구성 마법사를 성공적으로 실행 하려면 먼저이 SSL 인증서를 IIS의 기본 웹 사이트에 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-147">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="695c2-148">이 인증서의 주체 이름은 회사 네트워크의 페더레이션 서버에 구성 된 SSL 인증서와 동일 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-148">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="695c2-149">**권장 사항:** 이 페더레이션 서버 프록시가 연결 되는 페더레이션 서버에 대해 구성 된 것과 동일한 서버 인증 인증서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-149">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="695c2-150">자동 검색, 외부에서 Outlook 사용 및 Active Directory 동기화를 위한 인증서</span><span class="sxs-lookup"><span data-stu-id="695c2-150">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="695c2-151">외부 연결 Exchange 2013, Exchange 2010, Exchange 2007 및 Exchange 2003 클라이언트 액세스 서버 (CASs)에는 자동 검색, 외부에서 Outlook 사용 및 Active Directory 동기화 서비스를 위한 보안 연결을 위한 타사 SSL 인증서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-151">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services.</span></span> <span data-ttu-id="695c2-152">이 인증서가 온-프레미스 환경에 이미 설치 되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-152">You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="695c2-153">Exchange 하이브리드 서버용 인증서</span><span class="sxs-lookup"><span data-stu-id="695c2-153">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="695c2-154">외부 연결 Exchange 하이브리드 서버에는 Exchange Online 서비스와의 보안 연결용 타사 SSL 인증서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-154">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service.</span></span> <span data-ttu-id="695c2-155">타사 SSL 공급자에서이 인증서를 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-155">You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="695c2-156">Office 365 인증서 체인</span><span class="sxs-lookup"><span data-stu-id="695c2-156">Office 365 Certificate Chains</span></span>

<span data-ttu-id="695c2-157">이 문서에서는 인프라에 설치 해야 할 수 있는 인증서에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="695c2-157">This article describes the certificates you may need to install on your infrastructure.</span></span> <span data-ttu-id="695c2-158">Office 365 서버에 설치 된 인증서에 대 한 자세한 내용은 [office 365 인증서 체인](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="695c2-158">For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="695c2-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="695c2-159">See also</span></span>

[<span data-ttu-id="695c2-160">Microsoft 365 Enterprise 개요</span><span class="sxs-lookup"><span data-stu-id="695c2-160">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
