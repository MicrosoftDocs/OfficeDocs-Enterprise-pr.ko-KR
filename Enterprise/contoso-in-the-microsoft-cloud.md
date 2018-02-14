---
title: "Microsoft 클라우드의 Contoso"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: c4a6d625-4938-42cc-87e1-56b7a13c63ef
description: "요약: 가상의 전형적인 글로벌 조직이 Microsoft 클라우드 서비스로 클라우드 포함 IT 인프라를 채택하는 방법"
ms.openlocfilehash: 314fc872e1c5d555b3e412b3ce709d70595aa23b
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="contoso-in-the-microsoft-cloud"></a><span data-ttu-id="cb2b7-103">Microsoft 클라우드의 Contoso</span><span class="sxs-lookup"><span data-stu-id="cb2b7-103">Contoso in the Microsoft Cloud</span></span>

 <span data-ttu-id="cb2b7-104">**요약:** 가상의 전형적인 글로벌 조직이 Microsoft 클라우드 서비스로 클라우드 포함 IT 인프라를 채택하는 방법</span><span class="sxs-lookup"><span data-stu-id="cb2b7-104">**Summary:** How a fictional but representative global organization is adopting a cloud-inclusive IT infrastructure with Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="cb2b7-p101">이 문서는 파리에 본사를 두고 있는 글로벌 제조 대기업인 Contoso Corporation이 클라우드 포함 IT 인프라를 수용하고, 네트워킹, ID 및 보안에 대한 주요 디자인 결정을 해결한 방법과 비즈니스 문제를 해결하기 위해 엔터프라이즈 클라우드 시나리오를 구현하는 방법을 설명하는 문서 모음으로 연결됩니다. 또한 비즈니스 문제를 해결하기 위해 엔터프라이즈 클라우드 시나리오를 이 정보는 11페이지로 이루어진 포스터로 표시한 후 타블로이드 형식으로 인쇄할 수도 있습니다(ledger 11 x 17 또는 A3).</span><span class="sxs-lookup"><span data-stu-id="cb2b7-p101">This article links you to a set of articles that describe how the Contoso Corporation, a global manufacturing conglomerate with its headquarters in Paris, is embracing a cloud-inclusive IT infrastructure and has addressed major design decisions for networking, identity, and security and how it is implementing enterprise cloud scenarios to address its business problems. You can also view this information as an 11-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="cb2b7-107">[![Microsoft 클라우드 포스터의 Contoso 축소판 이미지입니다.](images/Contoso_Poster/Thumbnail.png)](https://www.microsoft.com/download/details.aspx?id=54427)</span><span class="sxs-lookup"><span data-stu-id="cb2b7-107">[![Thumb image of the Contoso in the Microsoft Cloud poster.](images/Contoso_Poster/Thumbnail.png)](https://www.microsoft.com/download/details.aspx?id=54427)</span></span>
  
<span data-ttu-id="cb2b7-108">![PDF 파일](images/Common_Images/PDFIcon.png)[PDF](https://go.microsoft.com/fwlink/p/?linkid=842085)  | ![Visio 파일](images/Common_Images/VisioIcon.png)[Visio](https://go.microsoft.com/fwlink/p/?linkid=842086)  | ![다른 언어 버전으로 페이지 보기](images/Common_Images/GlobeIcon.png)[기타 언어](https://www.microsoft.com/download/details.aspx?id=54427)</span><span class="sxs-lookup"><span data-stu-id="cb2b7-108">![PDF file](images/Common_Images/PDFIcon.png)[PDF](https://go.microsoft.com/fwlink/p/?linkid=842085)  | ![Visio file](images/Common_Images/VisioIcon.png)[Visio](https://go.microsoft.com/fwlink/p/?linkid=842086)  | ![See a page with versions in additional languages](images/Common_Images/GlobeIcon.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54427)</span></span>
  
<span data-ttu-id="cb2b7-109">다음 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb2b7-109">See the following sections:</span></span>
  
- [<span data-ttu-id="cb2b7-110">하이브리드 클라우드 개요 (영문)</span><span class="sxs-lookup"><span data-stu-id="cb2b7-110">Hybrid cloud overview</span></span>](hybrid-cloud-overview.md)
    
    <span data-ttu-id="cb2b7-111">Contoso Corporation은 다국적 기업이자 10만 개가 넘는 제품의 제조, 판매 및 지원 업무를 처리하는 복합 기업입니다. </span><span class="sxs-lookup"><span data-stu-id="cb2b7-111">The Contoso Corporation is a global conglomerate manufacturing, sales, and support organization with over 100,000 products.</span></span>
    
- [<span data-ttu-id="cb2b7-112">Contoso의 IT 인프라 및 필요한</span><span class="sxs-lookup"><span data-stu-id="cb2b7-112">Contoso's IT infrastructure and needs</span></span>](contoso-it-infrastructure-and-needs.md)
    
    <span data-ttu-id="cb2b7-113">Contoso는 중앙 집중식 온-프레미스 IT 인프라에서 클라우드 기반 개인 생산성 작업, 응용 프로그램 및 하이브리드 시나리오를 통합 수행할 수 있는 클라우드 포함 인프라로의 전환을 진행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb2b7-113">Contoso is transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
    
- [<span data-ttu-id="cb2b7-114">Contoso Corporation에 대 한 네트워킹</span><span class="sxs-lookup"><span data-stu-id="cb2b7-114">Networking for the Contoso Corporation</span></span>](networking-for-the-contoso-corporation.md)
    
    <span data-ttu-id="cb2b7-115">클라우드 기반 서비스에 대한 최적의 성능을 위해 Contoso의 네트워크 엔지니어가 인터넷 에지 및 인터넷에서 트래픽을 최적화했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb2b7-115">For best performance to cloud-based services, Contoso's network engineers optimized traffic to their Internet edge and across the Internet.</span></span>
    
- [<span data-ttu-id="cb2b7-116">Contoso Corporation 프로그램 id</span><span class="sxs-lookup"><span data-stu-id="cb2b7-116">Identity for the Contoso Corporation</span></span>](identity-for-the-contoso-corporation.md)
    
    <span data-ttu-id="cb2b7-117">클라우드 솔루션에서 Contoso의 ID가 해당 온-프레미스 ID 공급자를 활용하고 기존의 신뢰할 수 있는 타사 ID 공급자와 함께 페더레이션 인증을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2b7-117">Contoso's identity in the cloud solution leverages their on-premises identity provider and includes federated authentication with their existing trusted, third-party identity providers.</span></span>
    
- [<span data-ttu-id="cb2b7-118">구독, 라이선스 및 Contoso Corporation에 대 한 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="cb2b7-118">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)
    
    <span data-ttu-id="cb2b7-119">Contoso가 Microsoft 클라우드 서비스에 액세스하기 위해 조직/구독/라이선스/사용자 계정 계층 구조를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2b7-119">Contoso uses the organization/subscriptions/licenses/user accounts hierarchy to access Microsoft's cloud offerings.</span></span>
    
- [<span data-ttu-id="cb2b7-120">Contoso Corporation에 대 한 보안</span><span class="sxs-lookup"><span data-stu-id="cb2b7-120">Security for the Contoso Corporation</span></span>](security-for-the-contoso-corporation.md)
    
    <span data-ttu-id="cb2b7-121">IT 인프라를 클라우드 포함 인프라로 전환할 때 Contoso가 온-프레미스 보안 요구 사항이 Microsoft 클라우드 서비스에서 지원 및 구현되었는지를 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb2b7-121">When transitioning their IT infrastructure to a cloud-inclusive one, Contoso made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
    
- [<span data-ttu-id="cb2b7-122">Contoso Corporation에 대 한 엔터프라이즈 시나리오</span><span class="sxs-lookup"><span data-stu-id="cb2b7-122">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
    
    <span data-ttu-id="cb2b7-123">Contoso에서 Microsoft 클라우드 서비스를 사용하여 비즈니스 요구 사항을 해결하는 방법을 확인</span><span class="sxs-lookup"><span data-stu-id="cb2b7-123">See how Contoso is addressing its business needs with Microsoft's cloud offerings.</span></span>
    
> [!NOTE]
> <span data-ttu-id="cb2b7-124">이러한 문서는 Microsoft 클라우드 포스터 Contoso의 **2017년 9월** 릴리스를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2b7-124">These articles reflect the **September 2017** release of the Contoso in the Microsoft Cloud poster.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cb2b7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb2b7-125">See Also</span></span>

[<span data-ttu-id="cb2b7-126">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="cb2b7-126">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="cb2b7-127">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="cb2b7-127">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



