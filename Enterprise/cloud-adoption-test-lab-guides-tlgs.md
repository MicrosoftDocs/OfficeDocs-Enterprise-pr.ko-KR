---
title: TLG (테스트 랩 가이드)를 사용하여 Office 365 테스트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '요약: 이 TLG(테스트 랩 가이드)를 사용하여 Office 365의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.'
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302740"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a><span data-ttu-id="b65ee-103">TLG (테스트 랩 가이드)를 사용하여 Office 365 테스트</span><span class="sxs-lookup"><span data-stu-id="b65ee-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="b65ee-104">**요약:** 이 문서를 사용하여 Office 365의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365.</span></span>
  
<span data-ttu-id="b65ee-p101">TLG를 사용하면 Microsoft 제품을 빠르게 학습할 수 있습니다. 기술 또는 구성이 자신에게 적합한지 결정을 내리거나, 기술 또는 구성을 디자인, 계획하고, 사용자에게 선보이기 전에 먼저 평가해야 하는 경우에 유용합니다. "직접 구축 후 정상 작동 확인" 실습을 통해 새로운 제품 또는 솔루션의 배포 요구 사항을 이해할 수 있으므로 프로덕션에서 호스팅을 더욱 잘 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you and before you begin the design, planning, and rollout to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="b65ee-108">또한, TLG는 응용 프로그램의 개발 및 테스트를 위한 대표적 환경(개발/테스트 환경이라고도 함)을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a><span data-ttu-id="b65ee-110">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="b65ee-110">Office 365 dev/test environment</span></span>

<span data-ttu-id="b65ee-111">이러한 문서를 사용하여 Office 365 개발/테스트 환경을 구축하세요.</span><span class="sxs-lookup"><span data-stu-id="b65ee-111">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="b65ee-112">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="b65ee-112">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="b65ee-p102">Microsoft Azure 인프라 서비스에서 실행되는 단순화된 인트라넷을 생성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="b65ee-115">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="b65ee-115">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="b65ee-116">Office 365 Enterprise E5 평가판 구독을 만듭니다. 이는 컴퓨터에서 또는 Azure 인프라 서비스에서 실행되는 단순화된 인트라넷에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-116">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="b65ee-117">디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="b65ee-117">Directory synchronization</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b65ee-p103">암호 해시 동기화를 사용하여 디렉터리를 동기화하는 Azure AD Connect를 설치하고 구성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-p103">Install and configure Azure AD Connect for directory synchronization with password hash synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="b65ee-120">Office 365 개발/테스트 환경의 경우 이러한 문서를 사용하여 Office 365의 엔터프라이즈 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-120">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="b65ee-121">다단계 인증</span><span class="sxs-lookup"><span data-stu-id="b65ee-121">Multi-factor authentication</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b65ee-122">Office 365 구독 계정을 위해 스마트폰에 전송된 구독 텍스트 메시지를 사용하여 보조 인증을 구성하고 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-122">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="b65ee-123">페더레이션 ID</span><span class="sxs-lookup"><span data-stu-id="b65ee-123">Federated identity</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b65ee-124">AD DS(Active Directory Domain Services) 도메인의 계정을 사용하여 페더레이션된 인증을 구성하고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-124">Configure and demonstrate federated authentication with the accounts of an Active Directory Domain Services (AD DS) domain.</span></span>
    
- [<span data-ttu-id="b65ee-125">Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="b65ee-125">Advanced Threat Protection</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b65ee-126">전자 메일에서 맬웨어를 차단하는 EOP(Exchange Online Protection)의 기능인 Advanced Threat Protection을 구성하고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-126">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>

## <a name="simulated-cross-premises-devtest-environment"></a><span data-ttu-id="b65ee-127">시뮬레이션된 프레미스 간 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="b65ee-127">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="b65ee-128">하이브리드 클라우드 구성에서 Azure Virtual Network에 연결된 [시뮬레이션된 인트라넷](simulated-cross-premises-virtual-network-in-azure.md)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-128">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
## <a name="sharepoint-server-2016-devtest-environment"></a><span data-ttu-id="b65ee-129">SharePoint Server 2016 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="b65ee-129">SharePoint Server 2016 dev/test environment in Azure</span></span>

<span data-ttu-id="b65ee-130">Azure 인프라 서비스에 [단일 서버 SharePoint Server 2016 팜](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-130">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>

## <a name="microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="b65ee-131">Microsoft 365 Enterprise 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="b65ee-131">The Microsoft 365 Enterprise dev/test environment</span></span>

<span data-ttu-id="b65ee-132">[Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b65ee-132">Create dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) with these articles.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="b65ee-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b65ee-133">See Also</span></span>

[<span data-ttu-id="b65ee-134">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="b65ee-134">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="b65ee-135">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="b65ee-135">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="b65ee-136">Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델</span><span class="sxs-lookup"><span data-stu-id="b65ee-136">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="b65ee-137">하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="b65ee-137">Hybrid solutions</span></span>](hybrid-solutions.md)
