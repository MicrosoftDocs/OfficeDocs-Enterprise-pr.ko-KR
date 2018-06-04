---
title: 클라우드 채택 TLG(테스트 랩 가이드)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '요약: 이러한 클라우드 채택 TLG(테스트 랩 가이드)를 사용하여 Office 365, EMS(Enterprise Mobility + Security), Dynamics 365, Office Server 제품의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.'
ms.openlocfilehash: 1ca74f7fdb83cf730c4f6d003c9f9e325299f33d
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193678"
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="2c646-103">클라우드 채택 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="2c646-103">Cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="2c646-104">**요약:** 이러한 클라우드 채택 TLG(테스트 랩 가이드)를 사용하여 Office 365, EMS(Enterprise Mobility + Security), Dynamics 365, Office Server 제품의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365, Enterprise Mobility + Security (EMS), Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="2c646-p101">TLG를 사용하면 Microsoft 제품을 빠르게 학습할 수 있습니다. 기술 또는 구성이 자신에게 적합한지 결정을 내리거나 기술 또는 구성을 사용자에게 선보이기 전에 먼저 평가해야 하는 경우에 유용합니다. "직접 구축 후 정상 작동 확인" 실습을 통해 새로운 제품 또는 솔루션의 배포 요구 사항을 이해할 수 있으므로 프로덕션에서 호스팅을 더욱 잘 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="2c646-108">또한, TLG는 응용 프로그램의 개발 및 테스트를 위한 대표적 환경(개발/테스트 환경이라고도 함)을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="2c646-110">본격적으로 시작하기 전에 다음의 추가 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c646-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="2c646-111">Microsoft Virtual Academy 세션 [클라우드 채택 테스트 랩 가이드로 Microsoft 클라우드 경험하기](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 )를 보세요(22분밖에 소요되지 않습니다).</span><span class="sxs-lookup"><span data-stu-id="2c646-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="2c646-112">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="2c646-113">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-113">Office 365 dev/test environment</span></span>

<span data-ttu-id="2c646-114">이러한 문서를 사용하여 Office 365 개발/테스트 환경을 구축하세요.</span><span class="sxs-lookup"><span data-stu-id="2c646-114">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="2c646-115">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-115">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="2c646-p102">Microsoft Azure 인프라 서비스에서 실행되는 단순화된 인트라넷을 생성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="2c646-118">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-118">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-119">Office 365 Enterprise E5 평가판 구독을 만듭니다. 이는 컴퓨터에서 또는 Azure 인프라 서비스에서 실행되는 단순화된 인트라넷에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-119">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="2c646-120">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="2c646-120">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-p103">암호 동기화를 사용하여 디렉터리를 동기화하는 Azure AD Connect를 설치하고 구성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="2c646-123">Office 365 개발/테스트 환경의 경우 이러한 문서를 사용하여 Office 365의 엔터프라이즈 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-123">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="2c646-124">Office 365 개발/테스트 환경용 다단계 인증</span><span class="sxs-lookup"><span data-stu-id="2c646-124">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-125">Office 365 구독 계정을 위해 스마트폰에 전송된 구독 텍스트 메시지를 사용하여 보조 인증을 구성하고 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-125">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="2c646-126">Office 365 개발/테스트 환경용 페더레이션된 ID</span><span class="sxs-lookup"><span data-stu-id="2c646-126">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-127">Windows Server Active Directory 도메인의 계정을 사용하여 페더레이션된 인증을 구성하고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-127">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="2c646-128">Office 365 개발/테스트 환경용 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="2c646-128">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-129">Office 365 구독에서의 의심스러운 활동을 모니터링하고 알려주는 정책을 만들 수 있는 Office 365 Cloud App Security를 구성하고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-129">Configure and demonstrate Office 365 Cloud App Security, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="2c646-130">Office 365 개발/테스트 환경용 Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="2c646-130">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-131">전자 메일에서 맬웨어를 차단하는 EOP(Exchange Online Protection)의 기능인 Advanced Threat Protection을 구성하고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-131">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="2c646-132">Office 365 개발/테스트 환경용 고급 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="2c646-132">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-133">Office 365에 저장된 전자 메일, 문서 등의 데이터를 빠르게 찾고 분석하도록 예제 데이터를 추가하고 Advanced eDiscovery를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-133">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="2c646-134">Office 365 개발/테스트 환경용 중요 파일 보호</span><span class="sxs-lookup"><span data-stu-id="2c646-134">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-135">실수로 문서를 잘못된 폴더에 게시한다 하더라도 Office 365 정보 권한 관리를 사용하여 중요한 문서의 데이터를 보호할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-135">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="2c646-136">Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="2c646-136">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-137">Azure Information Protection(AIP) 클라이언트를 사용하여 다양한 수준의 보안으로 문서를 분류하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-137">Demonstrate how the Azure Information Protection (AIP) client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="2c646-138">개발/테스트 환경에서 격리된 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="2c646-138">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="2c646-139">중요하거나 극비 사항인 리소스를 위해 조직의 나머지와 분리된 SharePoint Online Group 사이트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-139">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="2c646-140">Microsoft 365 Enterprise 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-140">The Microsoft 365 Enterprise dev/test environment</span></span>

<span data-ttu-id="2c646-141">다음 문서의 시나리오를 따라 [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/)용 개발/테스트 환경을 만들어보세요.</span><span class="sxs-lookup"><span data-stu-id="2c646-141">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) scenarios with these articles:</span></span>
  
- [<span data-ttu-id="2c646-142">Microsoft 365 Enterprise 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-142">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="2c646-143">Office 365 E5, EMS E5 및 Windows 10 Enterprise를 실행하는 컴퓨터를 포함한 초기 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-143">Create the initial environment that includes Office 365 E5, EMS E5, and a computer running Windows 10 Enterprise.</span></span>
    
- [<span data-ttu-id="2c646-144">Microsoft 365 Enterprise 개발/테스트 환경용 MAM(모바일 응용 프로그램 관리) 정책</span><span class="sxs-lookup"><span data-stu-id="2c646-144">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="2c646-145">사용자 그룹과 iOS 및 Android 장치용 MAM(모바일 응용 프로그램 관리) 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-145">Create user groups and mobile application management (MAM) policies for ioS and Android devices.</span></span>
    
- [<span data-ttu-id="2c646-146">Microsoft Enterprise 365 개발/테스트 환경에서 iOS 및 Android 장치 등록</span><span class="sxs-lookup"><span data-stu-id="2c646-146">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    <span data-ttu-id="2c646-147">iOS 또는 Android 장치를 등록하고 원격으로 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-147">Enroll iOS or Android devices and manage them remotely.</span></span>
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="2c646-148">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-148">Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="2c646-149">이러한 문서를 사용하여 Dynamics 365 평가판 구독을 추가하고 Office 365 및 Dynamics 365 통합 기능 및 시나리오를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-149">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="2c646-150">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-150">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="2c646-151">Dynamics 365 평가판 구독과 Dynamics 365 라이선스 및 권한을 사용자 계정에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-151">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="2c646-152">Office 365 및 Dynamics 365 개발/테스트 환경용 Exchange Online 통합</span><span class="sxs-lookup"><span data-stu-id="2c646-152">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="2c646-153">Office 365 및 Dynamics 365가 Exchange Online 사서함에서 함께 작동하는 방식을 구성한 다음 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-153">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="2c646-154">One Microsoft Cloud 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-154">The One Microsoft Cloud dev/test environment</span></span>

<span data-ttu-id="2c646-p104">Microsoft의 모든 클라우드 서비스(Office 365, Azure, EMS, 및 Dynamics 365)를 포함하여 개발/테스트 환경을 만들어보세요. 단계별 지침에 대해서는 [One Microsoft Cloud 개발/테스트 환경](the-one-microsoft-cloud-dev-test-environment.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c646-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="2c646-157">시뮬레이션된 프레미스 간 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-157">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="2c646-158">이러한 문서를 사용하여 Azure Virtual Network, 시뮬레이션된 온-프레미스 네트워크 등의 프레미스 간 개발/테스트 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-158">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="2c646-159">시뮬레이트된 Azure의 크로스-프레미스 가상 네트워크</span><span class="sxs-lookup"><span data-stu-id="2c646-159">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="2c646-160">하이브리드 클라우드 구성에서 Azure Virtual Network에 연결된 시뮬레이션된 인트라넷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-160">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="2c646-161">Azure 개발/테스트 환경의 인트라넷 SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="2c646-161">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="2c646-162">Azure Virtual Network에 단일 서버 SharePoint Server 2016 팜을 만들고 시뮬레이션된 온-프레미스 네트워크의 연결 및 관리를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-162">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="2c646-163">추가 클라우드 기반 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-163">Additional cloud-based dev/test environments</span></span>

<span data-ttu-id="2c646-164">다음은 Azure 인프라 서비스에서 만들 수 있는 추가적인 클라우드 기반 개발/테스트 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-164">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="2c646-165">Azure의 SharePoint Server 2016 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-165">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="2c646-166">Azure 인프라 서비스에 단일 서버 SharePoint Server 2016 팜을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-166">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="2c646-167">Azure의 Exchange 2016 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-167">Exchange 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="2c646-168">Azure 인프라 서비스에 단일 Exchange 2016 서버를 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-168">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="2c646-169">Azure의 SharePoint Server 2013 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="2c646-169">SharePoint Server 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="2c646-170">Azure 인프라 서비스에 기본 및 고가용성 SharePoint Server 2013 팜을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="2c646-170">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
<span data-ttu-id="2c646-171">**토론 참여**</span><span class="sxs-lookup"><span data-stu-id="2c646-171">**Join the discussion**</span></span>

|<span data-ttu-id="2c646-172">**연락처**</span><span class="sxs-lookup"><span data-stu-id="2c646-172">**Contact us**</span></span>|<span data-ttu-id="2c646-173">**설명**</span><span class="sxs-lookup"><span data-stu-id="2c646-173">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2c646-174">**어떤 클라우드 채택 콘텐츠가 필요한가요?**</span><span class="sxs-lookup"><span data-stu-id="2c646-174">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="2c646-p105">여러 Microsoft 클라우드 플랫폼 및 서비스에 적용되는 클라우드 채택 콘텐츠를 만들고 있습니다. 클라우드 채택 콘텐츠에 대한 의견을 제공하거나 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)으로 이메일을 보내서 특정 콘텐츠를 요청하세요.  </span><span class="sxs-lookup"><span data-stu-id="2c646-p105">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="2c646-177">**클라우드 채택 토론에 가입**</span><span class="sxs-lookup"><span data-stu-id="2c646-177">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="2c646-p106">클라우드 기반 솔루션에 관심이 있다면 CAAB(클라우드 채택 자문 위원회)에 가입하여 Microsoft 콘텐츠 개발자, 산업 전문가 및 전 세계 고객으로 구성된 더 크고 활발한 커뮤니티에 연결할 수 있습니다. 참가하려면 Microsoft 기술 커뮤니티의 [CAAB(Cloud Adoption Advisory Board) 영역](https://aka.ms/caab)에 본인을 회원으로 추가하고 [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 간단한 이메일을 보내주세요. [CAAB 블로그](https://blogs.technet.com/b/solutions_advisory_board/)에서는 누구나 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원은 새 클라우드 채택 리소스와 솔루션에 대해 설명하는 비공개 웹 세미나에 초대됩니다.  </span><span class="sxs-lookup"><span data-stu-id="2c646-p106">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="2c646-181">**여기에 표시된 아트 받기**</span><span class="sxs-lookup"><span data-stu-id="2c646-181">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="2c646-p107">이 문서에 표시된 아트의 편집 가능한 복사본을 원하시면 보내드리겠습니다. 아트의 URL과 제목을 적어서 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)으로 요청 이메일을 보내주세요.  </span><span class="sxs-lookup"><span data-stu-id="2c646-p107">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="2c646-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c646-184">See Also</span></span>

<span data-ttu-id="2c646-185"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="2c646-185"></span></span>

[<span data-ttu-id="2c646-186">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="2c646-186">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="2c646-187">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="2c646-187">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="2c646-188">Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델</span><span class="sxs-lookup"><span data-stu-id="2c646-188">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="2c646-189">하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="2c646-189">Hybrid solutions</span></span>](hybrid-solutions.md)


