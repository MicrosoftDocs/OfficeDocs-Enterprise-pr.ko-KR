---
title: Microsoft Cloud Identity for Enterprise Architects
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "요약: Microsoft 클라우드 서비스 및 플랫폼에 맞게 ID 솔루션을 디자인합니다."
ms.openlocfilehash: f581711345b043d61de503360d101fbcc09de82e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="45177-103">Microsoft Cloud Identity for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="45177-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="45177-104">**요약:** Microsoft 클라우드 서비스 및 플랫폼에 맞게 ID 솔루션을 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="45177-p101">이 문서에서는 Microsoft 클라우드 서비스 및 플랫폼을 사용하는 조직용으로 ID를 설계하는 과정과 관련하여 IT 설계자가 파악해야 하는 사항을 설명합니다. 이 문서를 5페이지로 이루어진 포스터로 표시한 후 타블로이드 형식으로 인쇄할 수도 있습니다(ledger 11 x 17 또는 A3).</span><span class="sxs-lookup"><span data-stu-id="45177-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="45177-107">[![Microsoft 클라우드 id 모델에 대 한 축소판 그림 이미지](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="45177-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="45177-108">![PDF 파일](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio 파일](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![다른 언어 버전으로 페이지 보기](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[기타 언어](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="45177-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="45177-109">또한 [Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md) 에 모델의 모든 및 표시를 통해 대 [Microsoft의 Enterprise 클라우드 로드맵: IT 의사 결정자를 위한 리소스](https://aka.ms/cloudarchitecture)합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="45177-p102">이 문서는 **엔터프라이즈 설계자에 대 한 Microsoft 클라우드 id** 포스터의 1 월 2016 버전을 반영합니다. 4 월 2016에 대 한 변경 내용을 또는 포스터의 이후 버전에는 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="45177-112">Microsoft 클라우드에 대한 ID 디자인</span><span class="sxs-lookup"><span data-stu-id="45177-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="45177-p103">ID를 Microsoft 클라우드와 통합하면 보다 폭넓은 서비스 및 클라우드 플랫폼 옵션에 액세스할 수 있습니다. 두 가지 기본 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="45177-p104">Microsoft Azure AD(Active Directory)와 통합할 수 있습니다. 여기에는 Microsoft 클라우드에 대한 ID 공급자인 Azure AD에 온-프레미스 계정을 동기화하는 과정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="45177-117">Microsoft Azure 인프라 서비스에서 실행되는 가상 컴퓨터로 온-프레미스 AD DS(Active Directory 도메인 서비스) 환경을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![클라우드에서 ID를 디자인하기 위한 옵션](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="45177-119">**그림 1: 클라우드에서 ID를 디자인하기 위한 옵션**</span><span class="sxs-lookup"><span data-stu-id="45177-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="45177-120">그림 1에서는 Azure AD가 Microsoft SaaS(Software as a Service) 서비스 및 Azure PaaS(Platform as a Service) 응용 프로그램에 대한 ID 공급자의 역할을 하는지와 LOB(기간 업무) 응용 프로그램에서 어떤 방식으로 온-프레미스 AD DS를 사용하는지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45177-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="45177-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="45177-121">Azure Active Directory</span></span>

<span data-ttu-id="45177-p105">Microsoft Azure AD는 Microsoft 클라우드 호스티드 ID 및 액세스 관리 서비스로, Microsoft 클라우드 서비스 및 플랫폼의 핵심에 있습니다. Azure AD와 통합하면 현재 계정 및 암호 집합을 사용하여 모든 Microsoft SaaS 서비스에 액세스할 수 있습니다. 또한 Azure PaaS 응용 프로그램용 클라우드 기반 ID 기능도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="45177-126">Azure AD는 엔터프라이즈 조직 또는 Azure IaaS(Infrastructure as a Service)에서 실행되는 Windows 기반 가상 시스템의 AD DS 온-프레미스 요구를 대신 충족하지는 못합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="45177-127">Azure AD에는 무료, 기본 및 프리미엄의 세 가지 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="45177-128">**무료**</span><span class="sxs-lookup"><span data-stu-id="45177-128">**Free**</span></span> <br/> |<span data-ttu-id="45177-129">**기본**</span><span class="sxs-lookup"><span data-stu-id="45177-129">**Basic**</span></span> <br/> |<span data-ttu-id="45177-130">**프리미엄**</span><span class="sxs-lookup"><span data-stu-id="45177-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="45177-131">사용자 계정 관리</span><span class="sxs-lookup"><span data-stu-id="45177-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="45177-132">온-프레미스 디렉터리와 동기화</span><span class="sxs-lookup"><span data-stu-id="45177-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="45177-133">Azure, Office 365 및 널리 사용되는 수천 가지 기타 SaaS 응용 프로그램(예: Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox 등)에서 Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="45177-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="45177-134">무료 버전에 포함된 모든 기능과 다음 기능 포함:</span><span class="sxs-lookup"><span data-stu-id="45177-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="45177-135">회사 브랜딩</span><span class="sxs-lookup"><span data-stu-id="45177-135">Company branding</span></span> <br/>  <span data-ttu-id="45177-136">그룹 기반 응용 프로그램 액세스</span><span class="sxs-lookup"><span data-stu-id="45177-136">Group-based application access</span></span> <br/>  <span data-ttu-id="45177-137">셀프 서비스 암호 재설정</span><span class="sxs-lookup"><span data-stu-id="45177-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="45177-138">99.9%의 엔터프라이즈 SLA</span><span class="sxs-lookup"><span data-stu-id="45177-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="45177-139">무료 및 기본 버전의 모든 기능과 다음 기능 포함:</span><span class="sxs-lookup"><span data-stu-id="45177-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="45177-140">셀프 서비스 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="45177-140">Self-service group management</span></span> <br/>  <span data-ttu-id="45177-141">고급 보안 보고서 및 알림</span><span class="sxs-lookup"><span data-stu-id="45177-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="45177-142">Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="45177-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="45177-143">온-프레미스 AD DS에 쓰기 저장하는 방식의 암호 재설정</span><span class="sxs-lookup"><span data-stu-id="45177-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="45177-144">Azure Connect AD 도구 양방향 동기화</span><span class="sxs-lookup"><span data-stu-id="45177-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="45177-145">Azure AD 응용 프로그램 프록시</span><span class="sxs-lookup"><span data-stu-id="45177-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="45177-146">MIM(Microsoft Forefront Identity Manager)</span><span class="sxs-lookup"><span data-stu-id="45177-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="45177-147">버전에 대한 자세한 내용은 [Azure Active Directory 버전](https://go.microsoft.com/fwlink/p/?LinkId=524280)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45177-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="45177-148">옵션 1: Azure Active Directory와의 통합</span><span class="sxs-lookup"><span data-stu-id="45177-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="45177-p106">대부분의 조직에서는 표준 개체 및 특성 집합을 Azure AD 테넌트와 동기화합니다. Azure AD Connect 도구는 온-프레미스 AD DS와 Azure AD 테넌트 간에 계정을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Azure AD와 통합](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="45177-152">**그림 2: Azure AD와 통합**</span><span class="sxs-lookup"><span data-stu-id="45177-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="45177-p107">그림 2에서는 Azure AD Connect 도구가 AD DS의 변경 내용을 가져온 후 Azure AD 테넌트로 보내는 방법을 보여 줍니다. 이 경우 Azure AD 테넌트는 필수적인 온-프레미스 디렉터리 콘텐츠의 클라우드 호스티드 복제본입니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="45177-p108">대부분의 조직에서는 AD DS를 온-프레미스 ID 공급자로 사용합니다. 다른 유형의 ID 공급자 온-프레미스(예: LDAP 사용)를 사용하고 Azure AD와 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="45177-157">옵션 2: AD DS를 Azure로 확장</span><span class="sxs-lookup"><span data-stu-id="45177-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="45177-p109">Azure 인프라 서비스에서 실행되는 가상 컴퓨터로 AD DS를 확장하면 Azure AD와 동기화할 경우와는 다른 솔루션 및 응용 프로그램 집합이 지원됩니다. 다음은 두 가지 지원 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="45177-160">NTLM 또는 Kerberos 인증을 요구하는 클라우드 기반 솔루션 또는 AD DS 도메인 가입 가상 컴퓨터가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="45177-161">여러 Microsoft 클라우드 서비스 및 플랫폼에 클라우드 서비스 및 응용 프로그램에 대한 추가 통합이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Azure로 AD DS 확장](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="45177-163">**그림 3: Azure로 AD DS 확장**</span><span class="sxs-lookup"><span data-stu-id="45177-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="45177-p110">그림 3에서는 온-프레미스 VPN 장치와 Azure VPN 게이트웨이를 통해 Azure Virtual Network에 연결된 AD DS 도메인 컨트롤러를 보여 줍니다. Azure Virtual Network에는 기간 업무 응용 프로그램 및 고유한 AD DS 도메인 컨트롤러 집합을 위한 서버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="45177-166">추가 정보</span><span class="sxs-lookup"><span data-stu-id="45177-166">More Information</span></span>

- [<span data-ttu-id="45177-167">편리한 Office 365와의 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="45177-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="45177-168">Infographic: 클라우드 ID 및 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="45177-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="45177-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="45177-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="45177-170">온-프레미스 AD DS 계정과 Microsoft Azure AD 통합</span><span class="sxs-lookup"><span data-stu-id="45177-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="45177-171">Azure AD와 온-프레미스 AD DS 계정을 동기화하면 사용자는 온-프레미스 AD DS 계정을 사용하여 다음에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="45177-172">모든 Microsoft SaaS 서비스(Office 365, Microsoft Intune 및 Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="45177-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="45177-173">Azure PaaS에서 실행되는 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="45177-174">다음 두 가지 방법으로 이러한 통합을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="45177-175">디렉터리 및 암호 동기화</span><span class="sxs-lookup"><span data-stu-id="45177-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="45177-176">페더레이션 및 Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="45177-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="45177-p111">필요에 맞는 가장 간단한 옵션부터 시작합니다. 필요에 따라 이러한 옵션 간을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="45177-179">엔터프라이즈급 조직에서는 클라우드 전용 계정(온-프레미스 AD DS와 통합되지 않은)을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="45177-180">디렉터리 및 암호 동기화</span><span class="sxs-lookup"><span data-stu-id="45177-180">Directory and password synchronization</span></span>

<span data-ttu-id="45177-181">이것은 가장 간단한 옵션이며 Azure AD Connect 도구를 실행하는 서버만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![디렉터리 및 암호 동기화 구성](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="45177-183">**그림 4: 디렉터리 및 암호 동기화 구성**</span><span class="sxs-lookup"><span data-stu-id="45177-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="45177-p112">그림 4에서는 AD DS 도메인 컨트롤러가 있는 온-프레미스 또는 사설 클라우드 데이터 센터를 보여 줍니다. Azure AD Connect 도구를 실행하는 서버는 계정 이름 목록을 Azure AD와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="45177-186">이 옵션을 사용하는 경우:</span><span class="sxs-lookup"><span data-stu-id="45177-186">With this option:</span></span>
  
- <span data-ttu-id="45177-p113">사용자 계정이 온-프레미스 AD DS(또는 다른 ID 공급자)에서 Azure AD 테넌트로 동기화됩니다. 온-프레미스 디렉터리는 계정에 대한 권한 있는 원본을 유지하며, 사용자는 이 디렉터리에서 모든 계정 변경 내용을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="45177-189">Azure AD는 Microsoft SaaS 기반 서비스 및 Azure PaaS 응용 프로그램에 대한 모든 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="45177-190">여러 AD DS 포리스트에 대한 동기화를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="45177-191">암호 동기화를 사용하는 경우:</span><span class="sxs-lookup"><span data-stu-id="45177-191">With password synchronization:</span></span>
  
- <span data-ttu-id="45177-192">클라우드 서비스에 액세스할 때 온-프레미스 리소스에 대해 사용하는 것과 동일한 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="45177-p114">사용자 암호는 절대 Azure AD에 일반 텍스트로 전송되지 않습니다. 대신 암호 해시가 사용됩니다. 암호화 방식으로는 암호 해시를 암호 해독하거나 리버스 엔지니어링하고 암호화되지 않은 암호를 획득할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="45177-196">MFA(Multi-Factor Authentication)를 사용하는 경우;</span><span class="sxs-lookup"><span data-stu-id="45177-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="45177-197">Office 365와 함께 제공되는 기본적인 MFA 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="45177-198">Azure PaaS 응용 프로그램 개발자는 Azure Multi-Factor Authentication 서비스를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="45177-199">디렉터리 동기화에서는 온-프레미스 MFA 솔루션과의 통합 기능이 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="45177-200">페더레이션 및 Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="45177-200">Federation and single sign-on</span></span>

<span data-ttu-id="45177-201">이 옵션을 사용하려면 추가 서버 및 인프라가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-201">This option requires additional servers and infrastructure.</span></span> 
  
![페더레이션된 인증에 필요한 서버](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="45177-203">**그림 5: 페더레이션된 인증에 필요한 서버**</span><span class="sxs-lookup"><span data-stu-id="45177-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="45177-p115">그림 5에서는 페더레이션된 인증을 위한 구성 요소 집합을 보여 줍니다. Azure AD는 웹 응용 프로그램 프록시에 연결하면 이 프록시는 AD FS(Active Directory Federation Services)에 인증 요청을 전달합니다. 그러면 서버는 평가 및 응답을 위해 AD DS 도메인 컨트롤러에 요청을 전달합니다. Azure AD Connect 도구를 실행하는 서버는 AD DS에서 Azure AD로 계정 이름 목록을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="45177-207">페더레이션은 다음과 같은 추가 엔터프라이즈 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="45177-208">Azure AD로 전송된 모든 인증 요청은 AD DS를 통해 온-프레미스 ID 공급자로 전달되고 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="45177-209">타사 ID 공급자에서도 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="45177-210">암호 해시 동기화는 페더레이션된 로그인에 대한 로그인 백업으로 작동합니다(예: 페더레이션 인증이 실패할 경우).</span><span class="sxs-lookup"><span data-stu-id="45177-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="45177-211">다음 경우에 페더레이션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-211">Use federation if:</span></span>
  
- <span data-ttu-id="45177-p116">Single Sign-On이 필요한 경우. Single Sign-On을 사용하면 클라우드 서비스에 액세스할 때 자격 증명(사용자 이름 또는 암호)을 입력하라는 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="45177-214">AD FS가 이미 배포된 경우</span><span class="sxs-lookup"><span data-stu-id="45177-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="45177-215">타사 ID 공급자를 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="45177-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="45177-216">Forefront Identity Manager 2010 R2를 사용하는 경우(암호 해시 동기화 지원 안 됨)</span><span class="sxs-lookup"><span data-stu-id="45177-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="45177-217">온-프레미스 통합 스마트 카드 또는 기타 MFA 솔루션이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="45177-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="45177-218">로그인 감사 및/또는 계정 비활성화 기능이 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="45177-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="45177-219">조직에서 네트워크 위치 또는 작업 시간에 따라 클라이언트 로그인을 제한해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="45177-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="45177-220">FIPS(Federal Information Processing Standard)를 준수해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="45177-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="45177-221">페더레이션 인증을 위해서는 인프라 온-프레미스에 더 많은 투자를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="45177-p117">온-프레미스 서버는 회사 방화벽을 통해 인터넷에 액세스할 수 있어야 합니다. 경계 네트워크에 배포된 웹 응용 프로그램 프록시 서버를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="45177-224">AD FS 서버, AD FS 프록시 또는 웹 응용 프로그램 프록시 서버/방화벽/부하 분산 장치용 하드웨어와 라이선스가 필요하며 관련 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="45177-225">사용자가 Office 365 및 기타 클라우드 응용 프로그램에 액세스할 수 있도록 하려면 가용성과 성능이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="45177-226">추가 정보</span><span class="sxs-lookup"><span data-stu-id="45177-226">More Information</span></span>

- [<span data-ttu-id="45177-227">편리한 Office 365와의 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="45177-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="45177-228">디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비</span><span class="sxs-lookup"><span data-stu-id="45177-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="45177-229">Office 365에 대한 다단계 인증 사용</span><span class="sxs-lookup"><span data-stu-id="45177-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="45177-230">Azure Multi-factor Authentication</span><span class="sxs-lookup"><span data-stu-id="45177-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="45177-231">TechEd 2014: 디렉터리 통합: Active Directory 및 Azure Active Directory를 사용하여 단일 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="45177-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="45177-232">AD DS를 Azure로 확장</span><span class="sxs-lookup"><span data-stu-id="45177-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="45177-233">Azure에 AD DS를 확장하는 것은 Azure 인프라 서비스의 가상 컴퓨터에서 실행되는 기간 업무 응용 프로그램을 지원하기 위한 첫 번째 단계로, 다음을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="45177-234">NTLM 또는 Kerberos 인증을 요구하는 클라우드 기반 솔루션 또는 AD DS 도메인 가입 가상 컴퓨터가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="45177-235">클라우드 서비스 및 응용 프로그램에 대한 추가 통합 지원을 언제든지 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Azure Virtual Network로 AD DS 확장](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="45177-237">**그림 6: Azure Virtual Network로 AD DS 확장**</span><span class="sxs-lookup"><span data-stu-id="45177-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="45177-p118">그림 6에서는 AD DS가 사이트 간 VPN 또는 ExpressRoute 연결을 사용하여 Azure Virtual Network에 연결된 온-프레미스 또는 사설 클라우드 데이터 센터를 보여 줍니다. Azure Virtual Network에는 기간 업무 응용 프로그램 및 고유한 AD DS 도메인 컨트롤러 집합을 위한 서버가 포함되어 있습니다. 이 구성은 온-프레미스 및 Azure 인프라 서비스의 AD DS 하이브리드 배포입니다. 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="45177-242">Azure Virtual Network</span><span class="sxs-lookup"><span data-stu-id="45177-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="45177-243">온-프레미스 VPN(가상 사설망) 장치 또는 라우터와 Azure VPN 게이트웨이 간 연결</span><span class="sxs-lookup"><span data-stu-id="45177-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="45177-244">가상 네트워크의 가상 컴퓨터에 대해 온-프레미스 IP 주소 범위 부분 사용</span><span class="sxs-lookup"><span data-stu-id="45177-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="45177-245">글로벌 카탈로그 서버로 지정된 가상 네트워크에서 하나 이상의 도메인 컨트롤러 배포(VPN 연결을 통한 송신 트래픽 감소)</span><span class="sxs-lookup"><span data-stu-id="45177-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="45177-246">이 ID 아키텍처는 Azure AD와의 동기화와 비교할 때 다양한 솔루션 및 응용 프로그램을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="45177-247">온-프레미스에서 Azure로의 연결 옵션</span><span class="sxs-lookup"><span data-stu-id="45177-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="45177-248">온-프레미스 네트워크를 Azure Virual Network에 연결하려면 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="45177-249">사이트 간 VPN 연결: 사이트 1~10개(다른 Azure Virual Network 포함)를 단일 Azure Virual Network에 연결 가능</span><span class="sxs-lookup"><span data-stu-id="45177-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="45177-p119">ExpressRoute: 파트너 네트워크 및 데이터 센터 서비스 공급자를 통해 이루어지는 Azure에 대한 안전한 사설 WAN 연결 ExpressRoute 연결은 향상된 안정성, 높은 대역폭 및 낮은 대기 시간을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="45177-252">추가 정보</span><span class="sxs-lookup"><span data-stu-id="45177-252">More Information</span></span>

- [<span data-ttu-id="45177-253">가상 네트워크에 대한 크로스-프레미스 연결</span><span class="sxs-lookup"><span data-stu-id="45177-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="45177-254">ExpressRoute 기술 개요</span><span class="sxs-lookup"><span data-stu-id="45177-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="45177-255">Azure Virtual Machine에서 Windows Server Active Directory를 배포하기 위한 지침</span><span class="sxs-lookup"><span data-stu-id="45177-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="45177-256">응용 프로그램과 클라우드 ID 통합</span><span class="sxs-lookup"><span data-stu-id="45177-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="45177-p120">클라우드에서 실행되는 응용 프로그램을 디자인하고 개발할 때 필요한 자격 증명 집합을 포함하여 인증 프로세스를 위한 일관된 사용자 환경을 구현하는 것에 중점을 두어야 합니다. 예를 들어 Azure AD 또는 확장된 AD DS에 대해 Windows 자격 증명을 사용할 경우 사용자는 빠르게 인증을 받고 작업에 집중할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![응용 프로그램과 클라우드 ID 통합](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="45177-260">**그림 7: 응용 프로그램과 클라우드 ID 통합**</span><span class="sxs-lookup"><span data-stu-id="45177-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="45177-261">그림 7에서는 클라우드 ID에 응용 프로그램을 통합하기 위한 세 가지 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45177-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="45177-262">Azure AD에 클라우드 호스티드 응용 프로그램을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="45177-p121">MSDN 문서 [Azure Active Directory에 응용 프로그램 통합](https://go.microsoft.com/fwlink/p/?LinkId=524303)을 참조하세요. 이렇게 하면 Azure AD를 사용하여 PaaS 응용 프로그램에서 인증을 받을 수 있으며 사용자나 관리자는 Office 365와 같은 클라우드 서비스에서 사용자 대신 콘텐츠에 액세스할 수 있는 권한을 응용 프로그램에 부여할 수도 있습니다. 자세한 내용과 코드 샘플은 MSDN 문서 [Azure Active Directory의 인증 시나리오](https://go.microsoft.com/fwlink/p/?LinkId=524304)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="45177-266">Windows Server 2012 R2의 AD DS, AD FS 또는 Azure AD로 보호되는 응용 프로그램에 액세스하기 위해 프로그래밍 방식의 인증이 필요한 응용 프로그램은 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="45177-267">[Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="45177-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="45177-268">ADAL(Active Directory 인증 라이브러리)</span><span class="sxs-lookup"><span data-stu-id="45177-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="45177-p122">Azure AD Graph API는 OAuth 및 OpenID Connect를 지원합니다. PaaS 응용 프로그램에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="45177-p123">Azure Virtual Network의 가상 시스템에서 실행되는 온-프레미스 응용 프로그램이나 LOB(기간 업무) 응용 프로그램이 Windows 인증(NTLM 또는 Kerberos)을 직접 사용하도록 구성합니다. 이 방식이 사용자에게는 최상의 환경이며, 서버 응용 프로그램 개발자의 구성 작업도 최소로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="45177-273">응용 프로그램 통합 예제</span><span class="sxs-lookup"><span data-stu-id="45177-273">Application integration example</span></span>

<span data-ttu-id="45177-p124">조직에서는 다른 응용 프로그램이 최신 판매 데이터를 얻을 수 있는 REST 끝점을 노출하는 ASP.NET 응용 프로그램을 빌드합니다. REST 끝점에 대한 액세스는 Azure AD를 통해 보호됩니다. ASP.NET 응용 프로그램이 요청된 데이터를 전송하려면 응용 프로그램에서 먼저 Azure AD에서 인증할 수 있는 자격 증명을 제공해야 합니다. 그러면 조직의 다른 개발자는 REST 끝점의 판매 데이터를 사용하는 자체 응용 프로그램을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="45177-p125">Azure AD를 인증하고 데이터를 검색하기 위해 ADAL에서는 사용자 인증 프로세스를 관리하고 응용 프로그램으로 액세스 토큰을 전달하여 판매 데이터에 액세스하는 데 사용하도록 할 수 있습니다. ADAL을 사용하면 토큰, OAuth 흐름 및 기타 요소를 가져와 구문 분석하는 복잡성이 초래됩니다. ADAL은 빠르게 변화하는 또 다른 기술 솔루션이므로 개발자는 NuGet에서 최신 버전을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="45177-281">Azure에 디렉터리 구성 요소 배포</span><span class="sxs-lookup"><span data-stu-id="45177-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="45177-p126">암호 동기화 또는 페더레이션 인증용 서버와 같은 디렉터리 구성 요소를 온-프레미스 데이터 센터가 아닌 Azure Virtual Network에 배포할 수 있습니다. Azure에 AD DS를 확장하려는 경우에 특히 이러한 방식의 이점을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="45177-284">Azure Virtual Network에 배치할 수 있는 디렉터리 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="45177-285">Azure AD Connect 도구</span><span class="sxs-lookup"><span data-stu-id="45177-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="45177-286">페더레이션 인증 구성 요소</span><span class="sxs-lookup"><span data-stu-id="45177-286">Federated authentication components</span></span>
    
- <span data-ttu-id="45177-287">독립 실행형 AD DS 환경</span><span class="sxs-lookup"><span data-stu-id="45177-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="45177-288">AD Connect 도구</span><span class="sxs-lookup"><span data-stu-id="45177-288">AD Connect tool</span></span>

<span data-ttu-id="45177-p127">Azure AD Connect 도구는 Azure Virtual Network의 클라우드에 호스트될 수 있습니다. Azure에 이러한 작업을 배포할 때의 다음과 같은 이점을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="45177-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="45177-291">보다 신속한 프로비저닝 가능/운영 비용 감소</span><span class="sxs-lookup"><span data-stu-id="45177-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="45177-292">가용성 개선</span><span class="sxs-lookup"><span data-stu-id="45177-292">Increased availability</span></span>
    
![Azure 인프라 서비스에서 실행되는 AD Connect 도구](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="45177-294">**그림 8: Azure에서 실행 중인 AD Connect 도구**</span><span class="sxs-lookup"><span data-stu-id="45177-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="45177-p128">그림 8에서는 Azure Virtual Network의 가상 시스템에서 실행되는 AD Connect 도구를 보여 줍니다. 이 도구는 온-프레미스 AD DS 도메인 컨트롤러에서 계정 변경 내용을 쿼리하고 해당 변경 내용을 Office 365로 전송합니다. 이 솔루션이 작동하는 항목:</span><span class="sxs-lookup"><span data-stu-id="45177-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="45177-297">Office 365 서비스</span><span class="sxs-lookup"><span data-stu-id="45177-297">Office 365 services.</span></span>
    
- <span data-ttu-id="45177-298">인터넷을 통해 사용할 수 있는 Azure PaaS 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="45177-299">사이트 간 VPN 또는 ExpressRoute 연결을 통해 온-프레미스 환경에서 사용할 수 있는 LOB(기간 업무) 응용 프로그램.</span><span class="sxs-lookup"><span data-stu-id="45177-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="45177-300">자세한 내용은 [Azure Active Directory에 온-프레미스 ID 통합](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="45177-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="45177-301">페더레이션 인증 인프라</span><span class="sxs-lookup"><span data-stu-id="45177-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="45177-302">온-프레미스에서 AD FS를 아직 배포하지 않았다면 이 작업을 Azure에 배포하는 경우의 이점을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="45177-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="45177-303">온-프레미스에 종속되지 않고 클라우드 서비스에 자율적으로 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="45177-304">온-프레미스에서 호스트되는 서버와 도구 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45177-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="45177-305">두 노드 장애 조치(failover) 클러스터에서 사이트 간 VPN 게이트웨이를 사용하여 Azure에 연결할 수 있습니다(새로운 기능).</span><span class="sxs-lookup"><span data-stu-id="45177-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="45177-306">ACL을 사용하여 웹 응용 프로그램 프록시 서버가 도메인 컨트롤러 또는 기타 서버와 직접 통신하지 않고 AD FS와만 통신할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Azure에 페더레이션된 인증 인프라 배포](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="45177-308">**그림 9: Azure에 페더레이션된 인증 인프라 배포**</span><span class="sxs-lookup"><span data-stu-id="45177-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="45177-p129">그림 9에서는 Azure Virtual Network에 있는 도메인 컨트롤러 집합을 사용하여 AD DS 정보를 복제하는 온-프레미스 도메인 컨트롤러 집합을 보여 줍니다. Azure Virtual Network의 서버에서 실행되는 Azure AD Connect 도구는 로컬 도메인 컨트롤러에서 변경 내용을 쿼리한 다음 해당 변경 내용을 Azure AD로 보냅니다. Microsoft SaaS 서비스, Azure PaaS 응용 프로그램 및 기타 클라우드 응용 프로그램에서 Azure AD로 들어오는 인증 요청은 외부 부하 분산 장치로 전달되며, 이 장치는 해당 요청을 웹 응용 프로그램 프록시 서버 집합으로 전달합니다. 웹 응용 프로그램 프록시 서버는 내부 부하 분산 장치로 요청을 전달하고, 이 장치는 해당 요청을 AD FS 서버 집합으로 전달합니다. 그러면 ADFS 서버는 해당 요청을 도메인 컨트롤러에 전달하여 전송 자격 증명이 유효한지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="45177-314">이 솔루션이 작동하는 항목:</span><span class="sxs-lookup"><span data-stu-id="45177-314">This solution works with:</span></span>
  
- <span data-ttu-id="45177-315">Kerberos가 필요한 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="45177-316">모든 Microsoft SaaS 서비스</span><span class="sxs-lookup"><span data-stu-id="45177-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="45177-317">Azure의 인터넷 연결 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="45177-318">조직의 AD DS에서 계정 집합의 인증을 요구하는 Azure IaaS 또는 PaaS의 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="45177-319">자세한 내용은 [Azure Active Directory에 온-프레미스 ID 통합](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="45177-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="45177-320">Azure Virtual Network의 독립 실행형 AD DS 환경</span><span class="sxs-lookup"><span data-stu-id="45177-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="45177-p130">온-프레미스 환경에 클라우드 응용 프로그램을 항상 통합해야 하는 것은 아닙니다. 예를 들어 Azure Virtual Network의 독립 실행형 AD DS 도메인은 인터넷 사이트와 같은 공용 응용 프로그램을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="45177-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![서버 기반 응용 프로그램을 위한 독립 실행형 AD DS 환경](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="45177-324">**그림 10: 서버 기반 응용 프로그램을 위한 독립 실행형 AD DS 환경**</span><span class="sxs-lookup"><span data-stu-id="45177-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="45177-p131">그림 10에서는 AD DS 서버 집합을 호스트하고, 응용 프로그램을 호스트하는 서버 집합을 AD DS 및 DNS 서비스에 제공하는 Azure Virtual Network를 보여 줍니다. 이 솔루션이 작동하는 항목:</span><span class="sxs-lookup"><span data-stu-id="45177-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="45177-327">인터넷 연결 웹 사이트 및 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="45177-328">NTLM 또는 Kerberos 인증을 수행해야 하는 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="45177-329">AD DS를 필요로 하는 Windows 기반 서버의 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="45177-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="45177-330">자세한 내용은 [Azure Active Directory에 온-프레미스 ID 통합](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="45177-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="45177-331">See Also</span><span class="sxs-lookup"><span data-stu-id="45177-331">See Also</span></span>

[<span data-ttu-id="45177-332">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="45177-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="45177-333">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="45177-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



