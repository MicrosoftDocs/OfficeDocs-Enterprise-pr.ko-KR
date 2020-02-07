---
title: Microsoft Azure에서 Office 365 디렉터리 동기화 배포
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: '요약: Azure의 가상 머신에 Azure AD Connect를 배포하여 온-프레미스 디렉터리 및 Office 365 구독의 Azure 테넌트 간에 계정을 동기화합니다.'
ms.openlocfilehash: 0c92771788d932127c0afaf5724e89ce11298a32
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840545"
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="99065-103">Microsoft Azure에서 Office 365 디렉터리 동기화 배포</span><span class="sxs-lookup"><span data-stu-id="99065-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="99065-104">**요약:** Azure 인프라 서비스의 가상 머신에 Azure AD Connect를 배포하여 온-프레미스 디렉터리 및 Office 365 구독의 Azure 테넌트 간에 계정을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure infrastructure services to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="99065-p101">Azure AD(Active Directory) Connect(이전 명칭은 디렉터리 동기화 도구 또는 DirSync.exe 도구)는 도메인에 가입한 서버에 설치하는 응용 프로그램으로, 온-프레미스 Active Directory Domain Services(AD DS) 사용자를 Office 365 구독의 Azure AD 테넌트에 동기화합니다. Office 365는 디렉터리 서비스를 위해 Azure AD(Active Directory)를 사용합니다. Office 365 구독은 Azure AD 테넌트를 포함합니다. 이 테넌트는 Azure의 기타 SaaS 응용 프로그램 및 앱을 포함한 기타 클라우드 워크로드로 조직의 ID를 관리하기 위해 사용될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Office 365 subscription. Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="99065-109">온-프레미스 서버에 Azure AD Connect를 설치할 수 있으며, 다음과 같은 이유로 Azure의 가상 머신에 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-109">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="99065-110">클라우드 기반 서비스를 더 빠르게 프로비저닝하고 구성하여 사용자가 서비스를 더 빠르게 사용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-110">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="99065-111">Azure에서는 더 적은 노력으로 더 나은 사이트 가용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-111">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="99065-112">조직의 온-프레미스 서버 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-112">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="99065-p102">이 솔루션을 사용하려면 온-프레미스 네트워크와 Azure Virtual Network가 연결되어 있어야 합니다. 자세한 내용은 [온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p102">This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="99065-p103">이 문서는 단일 포리스트의 단일 도메인 동기화에 대해 설명합니다. Azure AD Connect는 Active Directory 포리스트의 모든 AD DS 도메인을 Office 365와 동기화합니다. Office 365와 동기화할 Active Directory 포리스트가 여러 개 있으면 [Single Sign-On과 다중 포리스트 디렉터리 동기화 시나리오](https://go.microsoft.com/fwlink/p/?LinkId=393091)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="99065-118">Azure에서 Office 365 디렉터리 동기화 배포 개요</span><span class="sxs-lookup"><span data-stu-id="99065-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>

<span data-ttu-id="99065-119">다음 다이어그램에서는 온-프레미스 AD DS 포리스트를 Office 365 구독과 동기화하는 Azure의 가상 머신(디렉터리 동기화 서버)에서 실행되는 Azure AD Connect를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="99065-119">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to an Office 365 subscription.</span></span>
  
![트래픽 흐름을 사용하여 온-프레미스 계정을 Office 365 구독의 Azure AD 테넌트와 동기화하는 Azure의 가상 컴퓨터에 있는 Azure AD Connect 도구](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="99065-p104">다이어그램에는 사이트 간 VPN 또는 ExpressRoute 연결로 연결되는 2개의 네트워크가 있습니다. AD DS 도메인 컨트롤러가 있는 온-프레미스 네트워크가 있고, [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)가 실행되는 가상 머신에 해당하는 디렉터리 동기화 서버를 포함하는 Azure Virtual Network가 있습니다. 디렉터리 동기화 서버에서 시작하는 다음과 같은 두 가지 주요 트래픽 흐름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="99065-124">Azure AD Connect는 온-프레미스 네트워크의 도메인 컨트롤러에서 계정 및 암호 변경 내용을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-124">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="99065-p105">Azure AD Connect는 계정 및 암호 변경 내용을 Office 365 구독의 Azure AD 인스턴스로 보냅니다. 디렉터리 동기화 서버가 온-프레미스 네트워크의 확장된 영역에 있기 때문에 이러한 변경 내용은 온-프레미스 네트워크의 프록시 서버를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p105">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="99065-p106">이 솔루션은 단일 포리스트의 단일 Active Directory 포리스트에서 단일 Active Directory 도메인의 동기화에 대해 설명합니다. Azure AD Connect는 Active Directory 포리스트의 모든 Active Directory 도메인을 Office 365와 동기화합니다. Office 365와 동기화할 Active Directory 포리스트가 여러 개 있으면 [Single Sign-On과 다중 포리스트 디렉터리 동기화 시나리오](https://go.microsoft.com/fwlink/p/?LinkId=393091)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p106">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="99065-130">이 솔루션을 배포할 때는 다음과 같은 두 가지 주요 단계가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="99065-130">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="99065-p107">Azure Virtual Network를 만들고 온-프레미스 네트워크에 대한 사이트 간 VPN 연결을 설정합니다. 자세한 내용은 [온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="99065-p108">[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)를 Azure의 도메인 가입 가상 머신에 설치한 후 온-프레미스 AD DS를 Office 365와 동기화합니다. 이 과정에서 다음 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p108">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Office 365. This involves:</span></span>
    
    <span data-ttu-id="99065-135">Azure AD Connect를 실행할 Azure Virtual Machine 만들기</span><span class="sxs-lookup"><span data-stu-id="99065-135">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="99065-136">[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="99065-136">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="99065-p109">Azure AD Connect를 구성하려면 Azure AD 관리자 계정 및 AD DS 엔터프라이즈 관리자 계정의 자격 증명(사용자 이름 및 암호)이 필요합니다. Azure AD Connect 즉시 실행되며 계속해서 온-프레미스 AD DS 포리스트를 Office 365와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p109">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Office 365.</span></span>
    
<span data-ttu-id="99065-139">이 솔루션을 프로덕션 환경에 배포하기 전에 [Office 365 개발/테스트 환경에 대한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 사용하여 이 구성을 개념 증명, 데모 또는 실험용으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-139">Before you deploy this solution in production, you can use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="99065-140">Azure AD Connect 구성이 완료될 때 AD DS 엔터프라이즈 관리자 계정 자격 증명이 저장되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-140">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="99065-p110">이 솔루션에서는 단일 AD DS 포리스트를 Office 365와 동기화하는 방법을 설명합니다. 이 문서에 나오는 토폴로지는 이 솔루션을 구현하는 방법 중 하나에 불과합니다. 조직의 토폴로지는 고유한 네트워크 요구 사항 및 보안 고려 사항에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p110">This solution describes synchronizing a single AD DS forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="99065-144">Azure의 Office 365에 대한 디렉터리 동기화 서버 호스트 계획</span><span class="sxs-lookup"><span data-stu-id="99065-144">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="99065-145"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="99065-145"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="99065-146">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="99065-146">Prerequisites</span></span>

<span data-ttu-id="99065-147">시작하기 전에 이 솔루션에 대한 다음 필수 구성 요소를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-147">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="99065-148">[Azure Virtual Network 계획](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)에서 관련 계획 콘텐츠를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-148">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="99065-149">Azure Virtual Network 구성을 위한 모든 [필수 구성 요소](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)가 충족되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-149">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="99065-p111">Active Directory 통합 기능을 포함하는 Office 365 구독이 있어야 합니다. Office 365 구독에 대한 내용은 [Office 365 구독 페이지](https://products.office.com/compare-all-microsoft-office-products?tab=2)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p111">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="99065-152">Azure AD Connect를 실행하여 온-프레미스 AD DS 포리스트를 Office 365와 동기화하는 하나의 Azure Virtual Machine을 프로비저닝합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-152">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Office 365.</span></span>
    
    <span data-ttu-id="99065-153">AD DS 엔터프라이즈 관리자 계정 및 Azure AD 관리자 계정의 자격 증명(이름 및 암호)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-153">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="99065-154">솔루션 아키텍처 디자인 가정</span><span class="sxs-lookup"><span data-stu-id="99065-154">Solution architecture design assumptions</span></span>

<span data-ttu-id="99065-155">다음 목록은 이 솔루션을 위한 디자인 선택 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-155">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="99065-p112">이 솔루션은 사이트 간 VPN 연결을 사용하는 단일 Azure Virtual Network를 사용합니다. Azure Virtual Network는 Azure AD Connect를 실행하는 디렉터리 동기화 서버에 해당하는 하나의 서버가 포함된 단일 서브넷을 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p112">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="99065-158">온-프레미스 네트워크에 도메인 컨트롤러 및 DNS 서버가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-158">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="99065-p113">Azure AD Connect는 Single Sign-On 대신 암호 해시 동기화를 수행합니다. AD FS(Active Directory Federation Services) 인프라를 배포할 필요는 없습니다. 암호 해시 동기화 및 Single Sign-On 옵션에 대한 자세한 내용은 [Azure Active Directory 하이브리드 ID 솔루션에 적합한 인증 방법 선택](https://aka.ms/auth-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="99065-p114">작업 환경에서 이 솔루션을 배포할 때 다음을 비롯한 추가 디자인 선택 옵션을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="99065-164">기존 Azure Virtual Network에 기존 DNS 서버가 있는 경우 디렉터리 동기화 서버에서 이름 확인을 위해 온-프레미스 네트워크의 DNS 서버 대신, 기존 DNS 서버를 사용하도록 할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-164">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="99065-p115">기존 Azure Virtual Network에 도메인 컨트롤러가 있는 경우 Active Directory 사이트 및 서비스를 구성하는 것이 더 나은 옵션인지 결정합니다. 디렉터리 동기화 서버는 온-프레미스 네트워크의 도메인 컨트롤러 대신, Azure Virtual Network의 도메인 컨트롤러에서 계정 및 암호 변경 내용을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="99065-167">배포 로드맵</span><span class="sxs-lookup"><span data-stu-id="99065-167">Deployment roadmap</span></span>

<span data-ttu-id="99065-168">Azure의 가상 머신에 Azure AD Connect를 배포하는 과정은 다음 세 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="99065-168">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="99065-169">1단계: Azure Virtual Network 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="99065-169">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="99065-170">2단계: Azure Virtual Machine 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="99065-170">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="99065-171">3단계: Azure AD Connect 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="99065-171">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="99065-172">배포 후 Office 365에서 새 사용자 계정에 위치 및 라이선스를 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-172">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="99065-173">1단계: Azure Virtual Network 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="99065-173">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="99065-174">Azure Virtual Network를 만들고 구성하려면 [ 온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)의 배포 로드맵에서 [1단계: 온-프레미스 네트워크 준비](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) 및 [2단계: Azure에 프레미스 간 가상 네트워크 만들기](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-174">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="99065-175">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-175">This is your resulting configuration.</span></span>
  
![Azure에서 호스트되는 Office 365의 디렉터리 동기화 서버 1단계](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="99065-177">이 그림에서는 사이트 간 VPN 또는 ExpressRoute 연결을 통해 Azure Virtual Network에 연결된 온-프레미스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="99065-177">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="99065-178">2단계: Azure Virtual Machine 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="99065-178">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="99065-p116">[Azure Portal에서 첫 번째 Windows Virtual Machine 만들기](https://go.microsoft.com/fwlink/p/?LinkId=393098)의 지침에 따라 Azure에 가상 머신을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="99065-p117">**기초** 창에서 사용자 가상 네트워크와 동일한 구독, 위치 및 리소스 그룹을 선택합니다. 사용자 이름과 암호를 안전한 위치에 기록합니다. 나중에 가상 컴퓨터에 연결하려면 이러한 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="99065-184">**크기 선택** 창에서 **A2 표준** 크기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-184">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="99065-p118">**설정** 창의 **저장소** 섹션에서 **표준** 저장소 유형을 선택합니다. **네트워크** 섹션에서 디렉터리 동기화 서버를 호스트하기 위한 가상 네트워크 및 서브넷 이름을 선택합니다(GatewaySubnet 제외). 다른 설정은 기본값을 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="99065-188">내부 DNS를 확인하여 주소 (A) 레코드가 해당 IP 주소의 가상 머신에 대해 추가되었는지 검토함으로써 디렉터리 동기화 서버가 DNS를 올바르게 사용하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-188">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="99065-p119">[가상 머신에 연결 및 로그온](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)의 지침을 사용하여 원격 데스크톱 연결을 통해 디렉터리 동기화 서버에 연결합니다. 로그인한 후에 가상 머신을 온-프레미스 AD DS 도메인에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p119">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="99065-p120">Azure AD Connect가 인터넷 리소스에 액세스할 수 있게 하려면 온-프레미스 네트워크의 프록시 서버를 사용하도록 디렉터리 동기화 서버를 구성해야 합니다. 수행할 추가 구성 단계에 대해서는 네트워크 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="99065-193">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-193">This is your resulting configuration.</span></span>
  
![Azure에서 호스트되는 Office 365의 디렉터리 동기화 서버 2단계](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="99065-195">이 그림은 크로스-프레미스 Azure Virtual Network의 디렉터리 동기화 서버 가상 머신을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="99065-195">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="99065-196">3단계: Azure AD Connect 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="99065-196">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="99065-197">다음 절차를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-197">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="99065-p121">로컬 관리자 권한이 있는 AD DS 도메인 계정으로 원격 데스크톱 연결을 통해 디렉터리 동기화 서버에 연결합니다. [가상 머신에 연결 및 로그온](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p121">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span></span>
    
2. <span data-ttu-id="99065-200">디렉터리 동기화 서버에서 [Office 365의 디렉터리 동기화 설정](set-up-directory-synchronization.md) 문서를 열고 암호 해시 동기화를 사용한 디렉터리 동기화에 대한 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="99065-200">From the directory sync server, open the [Set up directory synchronization for Office 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="99065-p122">설치 프로그램은 로컬 사용자 OU(조직 구성 단위)에 **AAD_xxxxxxxxxxxx** 계정을 만듭니다. 이 계정을 이동하거나 제거하면 안 됩니다. 이 경우 동기화가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="99065-203">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99065-203">This is your resulting configuration.</span></span>
  
![Azure에서 호스트되는 Office 365의 디렉터리 동기화 서버 3단계](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="99065-205">이 그림은 크로스-프레미스 Azure Virtual Network에서 Azure AD Connect를 사용하는 디렉터리 동기화 서버를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="99065-205">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="99065-206">Office 365에서 사용자에게 위치 및 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="99065-206">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="99065-p123">Azure AD Connect는 온-프레미스 AD DS에서 Office 365 구독에 계정을 추가하지만, 사용자가 Office 365에 로그인하고 해당 서비스를 사용하려면 계정의 위치 및 라이선스를 구성해야 합니다. 다음 단계에 따라 해당 사용자 계정에 대한 위치를 추가하고 라이선스를 활성화하세요.</span><span class="sxs-lookup"><span data-stu-id="99065-p123">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises AD DS, but in order for users to sign in to Office 365 and use its services, the accounts must be configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="99065-209">[Office 365 포털 페이지](https://www.office.com)에 로그인한 다음 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-209">Sign in to the [Office 365 portal page](https://www.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="99065-210">왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-210">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="99065-211">사용자 계정 목록에서 정품 인증하려는 사용자 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-211">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="99065-212">사용자 페이지에서 **제품 라이선스**에 대해 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-212">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="99065-213">**제품 라이선스** 페이지에서 **위치**로 사용자의 위치를 선택한 다음, 사용자를 위한 적절한 라이선스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-213">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="99065-214">완료되면 **저장**을 클릭한 다음 **닫기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99065-214">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="99065-215">추가 사용자가 있으면 3단계로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="99065-215">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="99065-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99065-216">See also</span></span>

[<span data-ttu-id="99065-217">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="99065-217">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="99065-218">온-프레미스 네트워크를 Microsoft Azure Virtual Network에 연결</span><span class="sxs-lookup"><span data-stu-id="99065-218">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="99065-219">Azure AD Connect 다운로드</span><span class="sxs-lookup"><span data-stu-id="99065-219">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="99065-220">Office 365의 디렉터리 동기화 설정</span><span class="sxs-lookup"><span data-stu-id="99065-220">Set up directory synchronization for Office 365</span></span>](set-up-directory-synchronization.md)
  
