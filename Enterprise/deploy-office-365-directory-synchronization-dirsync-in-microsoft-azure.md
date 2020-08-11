---
title: Microsoft Azure에서 Microsoft 365 디렉터리 동기화 배포
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: Azure의 가상 머신에 Azure AD Connect를 배포 하 여 온-프레미스 디렉터리와 Azure AD 테 넌 트 간의 계정을 동기화 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 2872e3d5d233d04885fadd3e422ec1d15284ac26
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605744"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="691a0-103">Microsoft Azure에서 Microsoft 365 디렉터리 동기화 배포</span><span class="sxs-lookup"><span data-stu-id="691a0-103">Deploy Microsoft 365 Directory Synchronization in Microsoft Azure</span></span>

<span data-ttu-id="691a0-104">Azure Active Directory (Azure AD) Connect (이전에는 디렉터리 동기화 도구, 디렉터리 동기화 도구 또는 DirSync.exe 도구로 알려짐)는 온-프레미스 AD DS (Active Directory 도메인 서비스) 사용자를 Microsoft 365 구독의 Azure AD 테 넌 트와 동기화 하기 위해 도메인에 가입 된 서버에 설치 하는 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-104">Azure Active Directory (Azure AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="691a0-105">Microsoft 365는 디렉터리 서비스에 Azure AD를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-105">Microsoft 365 uses Azure AD for its directory service.</span></span> <span data-ttu-id="691a0-106">Microsoft 365 구독에는 Azure AD 테 넌 트가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-106">Your Microsoft 365 subscription includes an Azure AD tenant.</span></span> <span data-ttu-id="691a0-107">Azure의 다른 SaaS 응용 프로그램 및 앱을 비롯 한 다른 클라우드 작업을 포함 하 여 조직의 id를 관리 하는 데도이 테 넌 트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-107">This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="691a0-108">온-프레미스 서버에 Azure AD Connect를 설치할 수 있으며, 다음과 같은 이유로 Azure의 가상 머신에 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-108">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="691a0-109">클라우드 기반 서비스를 더 빠르게 프로비저닝하고 구성하여 사용자가 서비스를 더 빠르게 사용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-109">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="691a0-110">Azure에서는 더 적은 노력으로 더 나은 사이트 가용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-110">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="691a0-111">조직의 온-프레미스 서버 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-111">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="691a0-p102">이 솔루션을 사용하려면 온-프레미스 네트워크와 Azure Virtual Network가 연결되어 있어야 합니다. 자세한 내용은 [온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-p102">This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="691a0-114">이 문서에서는 단일 포리스트의 단일 도메인을 동기화 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-114">This article describes synchronization of a single domain in a single forest.</span></span> <span data-ttu-id="691a0-115">Azure AD Connect는 Active Directory 포리스트의 모든 AD DS 도메인을 Microsoft 365와 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-115">Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="691a0-116">Microsoft 365과 동기화 할 Active Directory 포리스트가 여러 개 있는 경우에는 [Single Sign-on 시나리오를 사용 하 여 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=393091)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-116">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a><span data-ttu-id="691a0-117">Azure에서 Microsoft 365 디렉터리 동기화 배포 개요</span><span class="sxs-lookup"><span data-stu-id="691a0-117">Overview of deploying Microsoft 365 directory synchronization in Azure</span></span>

<span data-ttu-id="691a0-118">다음 다이어그램에서는 온-프레미스 AD DS 포리스트와 Microsoft 365 구독을 동기화 하는 Azure의 가상 컴퓨터 (디렉터리 동기화 서버)에서 실행 되는 Azure AD Connect를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-118">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to a Microsoft 365 subscription.</span></span>
  
![트래픽 흐름을 사용 하 여 온-프레미스 계정을 Microsoft 365 구독의 Azure AD 테 넌 트와 동기화 하는 Azure의 가상 컴퓨터에 있는 azure AD Connect 도구](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="691a0-p104">다이어그램에는 사이트 간 VPN 또는 ExpressRoute 연결로 연결되는 2개의 네트워크가 있습니다. AD DS 도메인 컨트롤러가 있는 온-프레미스 네트워크가 있고, [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)가 실행되는 가상 머신에 해당하는 디렉터리 동기화 서버를 포함하는 Azure Virtual Network가 있습니다. 디렉터리 동기화 서버에서 시작하는 다음과 같은 두 가지 주요 트래픽 흐름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="691a0-123">Azure AD Connect는 온-프레미스 네트워크의 도메인 컨트롤러에서 계정 및 암호 변경 내용을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-123">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="691a0-124">Azure AD Connect는 계정 및 암호에 대 한 변경 내용을 Microsoft 365 구독의 Azure AD 인스턴스에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-124">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Microsoft 365 subscription.</span></span> <span data-ttu-id="691a0-125">디렉터리 동기화 서버가 온-프레미스 네트워크의 확장 부분에 있기 때문에 이러한 변경 내용은 온-프레미스 네트워크의 프록시 서버를 통해 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-125">Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="691a0-126">이 솔루션은 단일 Active Directory 포리스트에서 단일 Active Directory 도메인의 동기화에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-126">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest.</span></span> <span data-ttu-id="691a0-127">Azure AD Connect는 Active Directory 포리스트의 모든 Active Directory 도메인을 Microsoft 365와 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-127">Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="691a0-128">Microsoft 365과 동기화 할 Active Directory 포리스트가 여러 개 있는 경우에는 [Single Sign-on 시나리오를 사용 하 여 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=393091)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-128">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="691a0-129">이 솔루션을 배포할 때는 다음과 같은 두 가지 주요 단계가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-129">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="691a0-p107">Azure Virtual Network를 만들고 온-프레미스 네트워크에 대한 사이트 간 VPN 연결을 설정합니다. 자세한 내용은 [온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="691a0-132">Azure의 도메인에 가입 된 가상 컴퓨터에 [AZURE Ad Connect](https://www.microsoft.com/download/details.aspx?id=47594) 를 설치한 다음 온-프레미스 AD DS를 Microsoft 365와 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-132">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Microsoft 365.</span></span> <span data-ttu-id="691a0-133">여기에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-133">This involves:</span></span>
    
    <span data-ttu-id="691a0-134">Azure AD Connect를 실행할 Azure Virtual Machine 만들기</span><span class="sxs-lookup"><span data-stu-id="691a0-134">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="691a0-135">[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="691a0-135">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="691a0-136">Azure AD Connect를 구성 하려면 Azure AD 관리자 계정 및 AD DS 엔터프라이즈 관리자 계정의 자격 증명 (사용자 이름 및 암호)이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-136">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account.</span></span> <span data-ttu-id="691a0-137">Azure AD Connect는 온-프레미스 AD DS 포리스트를 Microsoft 365와 동기화 하기 위해 즉시 및 지속적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-137">Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Microsoft 365.</span></span>
    
<span data-ttu-id="691a0-138">이 솔루션을 프로덕션 환경에 배포 하기 전에 [시뮬레이트된 엔터프라이즈 기반 구성](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) 의 지침을 사용 하 여이 구성을 개념 증명, 데모 또는 실험으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-138">Before you deploy this solution in production, you can use the instructions in [The simulated enterprise base configuration](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="691a0-139">Azure AD Connect 구성이 완료될 때 AD DS 엔터프라이즈 관리자 계정 자격 증명이 저장되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-139">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="691a0-140">이 솔루션은 단일 AD DS 포리스트를 Microsoft 365으로 동기화 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-140">This solution describes synchronizing a single AD DS forest to Microsoft 365.</span></span> <span data-ttu-id="691a0-141">이 문서에서 설명 하는 토폴로지는이 솔루션을 구현 하는 한 가지 방법만을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-141">The topology discussed in this article represents only one way to implement this solution.</span></span> <span data-ttu-id="691a0-142">조직의 토폴로지는 고유한 네트워크 요구 사항 및 보안 고려 사항에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-142">Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a><span data-ttu-id="691a0-143">Azure의 Microsoft 365에 대 한 디렉터리 동기화 서버 호스트 계획</span><span class="sxs-lookup"><span data-stu-id="691a0-143">Plan for hosting a directory sync server for Microsoft 365 in Azure</span></span>
<span data-ttu-id="691a0-144"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="691a0-144"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="691a0-145">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="691a0-145">Prerequisites</span></span>

<span data-ttu-id="691a0-146">시작하기 전에 이 솔루션에 대한 다음 필수 구성 요소를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-146">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="691a0-147">[Azure Virtual Network 계획](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)에서 관련 계획 콘텐츠를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-147">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="691a0-148">Azure Virtual Network 구성을 위한 모든 [필수 구성 요소](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)가 충족되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-148">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="691a0-149">Active Directory 통합 기능을 포함 하는 Microsoft 365 구독을 보유 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-149">Have a Microsoft 365 subscription that includes the Active Directory integration feature.</span></span> <span data-ttu-id="691a0-150">Microsoft 365 구독에 대 한 자세한 내용을 보려면 [microsoft 365 구독 페이지로](https://products.office.com/compare-all-microsoft-office-products?tab=2)이동 하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-150">For information about Microsoft 365 subscriptions, go to the [Microsoft 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="691a0-151">Azure AD Connect를 실행 하 여 온-프레미스 AD DS 포리스트와 Microsoft 365을 동기화 하는 하나의 Azure Virtual Machine을 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-151">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Microsoft 365.</span></span>
    
    <span data-ttu-id="691a0-152">AD DS 엔터프라이즈 관리자 계정 및 Azure AD 관리자 계정의 자격 증명(이름 및 암호)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-152">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="691a0-153">솔루션 아키텍처 디자인 가정</span><span class="sxs-lookup"><span data-stu-id="691a0-153">Solution architecture design assumptions</span></span>

<span data-ttu-id="691a0-154">다음 목록은 이 솔루션을 위한 디자인 선택 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-154">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="691a0-p112">이 솔루션은 사이트 간 VPN 연결을 사용하는 단일 Azure Virtual Network를 사용합니다. Azure Virtual Network는 Azure AD Connect를 실행하는 디렉터리 동기화 서버에 해당하는 하나의 서버가 포함된 단일 서브넷을 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p112">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="691a0-157">온-프레미스 네트워크에 도메인 컨트롤러 및 DNS 서버가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-157">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="691a0-p113">Azure AD Connect는 Single Sign-On 대신 암호 해시 동기화를 수행합니다. AD FS(Active Directory Federation Services) 인프라를 배포할 필요는 없습니다. 암호 해시 동기화 및 Single Sign-On 옵션에 대한 자세한 내용은 [Azure Active Directory 하이브리드 ID 솔루션에 적합한 인증 방법 선택](https://aka.ms/auth-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="691a0-p114">작업 환경에서 이 솔루션을 배포할 때 다음을 비롯한 추가 디자인 선택 옵션을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="691a0-163">기존 Azure Virtual Network에 기존 DNS 서버가 있는 경우 디렉터리 동기화 서버에서 이름 확인을 위해 온-프레미스 네트워크의 DNS 서버 대신, 기존 DNS 서버를 사용하도록 할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-163">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="691a0-p115">기존 Azure Virtual Network에 도메인 컨트롤러가 있는 경우 Active Directory 사이트 및 서비스를 구성하는 것이 더 나은 옵션인지 결정합니다. 디렉터리 동기화 서버는 온-프레미스 네트워크의 도메인 컨트롤러 대신, Azure Virtual Network의 도메인 컨트롤러에서 계정 및 암호 변경 내용을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="691a0-166">배포 로드맵</span><span class="sxs-lookup"><span data-stu-id="691a0-166">Deployment roadmap</span></span>

<span data-ttu-id="691a0-167">Azure의 가상 머신에 Azure AD Connect를 배포하는 과정은 다음 세 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-167">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="691a0-168">1단계: Azure Virtual Network 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="691a0-168">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="691a0-169">2단계: Azure Virtual Machine 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="691a0-169">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="691a0-170">3단계: Azure AD Connect 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="691a0-170">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="691a0-171">배포 후에는 Microsoft 365의 새 사용자 계정에 대 한 위치 및 라이선스도 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-171">After deployment, you must also assign locations and licenses for the new user accounts in Microsoft 365.</span></span>


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="691a0-172">1단계: Azure Virtual Network 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="691a0-172">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="691a0-173">Azure Virtual Network를 만들고 구성하려면 [ 온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)의 배포 로드맵에서 [1단계: 온-프레미스 네트워크 준비](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) 및 [2단계: Azure에 프레미스 간 가상 네트워크 만들기](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-173">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="691a0-174">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-174">This is your resulting configuration.</span></span>
  
![Azure에서 호스트 되는 Microsoft 365에 대 한 디렉터리 동기화 서버 1 단계](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="691a0-176">이 그림에서는 사이트 간 VPN 또는 ExpressRoute 연결을 통해 Azure Virtual Network에 연결된 온-프레미스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-176">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="691a0-177">2단계: Azure Virtual Machine 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="691a0-177">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="691a0-p116">[Azure Portal에서 첫 번째 Windows Virtual Machine 만들기](https://go.microsoft.com/fwlink/p/?LinkId=393098)의 지침에 따라 Azure에 가상 머신을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="691a0-p117">**기초** 창에서 사용자 가상 네트워크와 동일한 구독, 위치 및 리소스 그룹을 선택합니다. 사용자 이름과 암호를 안전한 위치에 기록합니다. 나중에 가상 컴퓨터에 연결하려면 이러한 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="691a0-183">**크기 선택** 창에서 **A2 표준** 크기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-183">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="691a0-p118">**설정** 창의 **저장소** 섹션에서 **표준** 저장소 유형을 선택합니다. **네트워크** 섹션에서 디렉터리 동기화 서버를 호스트하기 위한 가상 네트워크 및 서브넷 이름을 선택합니다(GatewaySubnet 제외). 다른 설정은 기본값을 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="691a0-187">내부 DNS를 확인하여 주소 (A) 레코드가 해당 IP 주소의 가상 머신에 대해 추가되었는지 검토함으로써 디렉터리 동기화 서버가 DNS를 올바르게 사용하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-187">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="691a0-p119">[가상 머신에 연결 및 로그온](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)의 지침을 사용하여 원격 데스크톱 연결을 통해 디렉터리 동기화 서버에 연결합니다. 로그인한 후에 가상 머신을 온-프레미스 AD DS 도메인에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p119">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="691a0-p120">Azure AD Connect가 인터넷 리소스에 액세스할 수 있게 하려면 온-프레미스 네트워크의 프록시 서버를 사용하도록 디렉터리 동기화 서버를 구성해야 합니다. 수행할 추가 구성 단계에 대해서는 네트워크 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="691a0-192">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-192">This is your resulting configuration.</span></span>
  
![Azure에서 호스트 되는 Microsoft 365에 대 한 디렉터리 동기화 서버 2 단계](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="691a0-194">이 그림은 크로스-프레미스 Azure Virtual Network의 디렉터리 동기화 서버 가상 머신을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-194">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="691a0-195">3단계: Azure AD Connect 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="691a0-195">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="691a0-196">다음 절차를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-196">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="691a0-p121">로컬 관리자 권한이 있는 AD DS 도메인 계정으로 원격 데스크톱 연결을 통해 디렉터리 동기화 서버에 연결합니다. [가상 머신에 연결 및 로그온](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="691a0-p121">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span></span>
    
2. <span data-ttu-id="691a0-199">디렉터리 동기화 서버에서 [Microsoft 365에 대 한 디렉터리 동기화 설정](set-up-directory-synchronization.md) 문서를 열고 암호 해시 동기화를 사용한 디렉터리 동기화에 대 한 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-199">From the directory sync server, open the [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="691a0-p122">설치 프로그램은 로컬 사용자 OU(조직 구성 단위)에 **AAD_xxxxxxxxxxxx** 계정을 만듭니다. 이 계정을 이동하거나 제거하면 안 됩니다. 이 경우 동기화가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="691a0-202">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-202">This is your resulting configuration.</span></span>
  
![Azure에서 호스트 되는 Microsoft 365에 대 한 디렉터리 동기화 서버 3 단계](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="691a0-204">이 그림은 크로스-프레미스 Azure Virtual Network에서 Azure AD Connect를 사용하는 디렉터리 동기화 서버를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-204">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a><span data-ttu-id="691a0-205">Microsoft 365에서 사용자에 게 위치 및 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="691a0-205">Assign locations and licenses to users in Microsoft 365</span></span>

<span data-ttu-id="691a0-206">Azure AD Connect는 온-프레미스 AD DS에서 Microsoft 365 구독에 계정을 추가 하지만, 사용자가 Microsoft 365에 로그인 하 여 해당 서비스를 사용 하도록 하려면 계정을 위치 및 라이선스와 함께 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-206">Azure AD Connect adds accounts to your Microsoft 365 subscription from the on-premises AD DS, but in order for users to sign in to Microsoft 365 and use its services, the accounts must be configured with a location and licenses.</span></span> <span data-ttu-id="691a0-207">다음 단계를 사용 하 여 해당 하는 사용자 계정에 대 한 라이선스를 추가 하 고 해당 위치를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-207">Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="691a0-208">[Microsoft 365 관리 센터](https://admin.microsoft.com)에 로그인 한 다음 **관리자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-208">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="691a0-209">왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-209">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="691a0-210">사용자 계정 목록에서 정품 인증하려는 사용자 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-210">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="691a0-211">사용자 페이지에서 **제품 라이선스**에 대해 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-211">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="691a0-212">**제품 라이선스** 페이지에서 **위치**로 사용자의 위치를 선택한 다음, 사용자를 위한 적절한 라이선스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-212">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="691a0-213">완료되면 **저장**을 클릭한 다음 **닫기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-213">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="691a0-214">추가 사용자가 있으면 3단계로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="691a0-214">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="691a0-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="691a0-215">See also</span></span>

[<span data-ttu-id="691a0-216">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="691a0-216">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="691a0-217">온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결</span><span class="sxs-lookup"><span data-stu-id="691a0-217">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="691a0-218">Azure AD Connect 다운로드</span><span class="sxs-lookup"><span data-stu-id="691a0-218">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="691a0-219">Microsoft 365에 대 한 디렉터리 동기화 설정</span><span class="sxs-lookup"><span data-stu-id="691a0-219">Set up directory synchronization for Microsoft 365</span></span>](set-up-directory-synchronization.md)
  
