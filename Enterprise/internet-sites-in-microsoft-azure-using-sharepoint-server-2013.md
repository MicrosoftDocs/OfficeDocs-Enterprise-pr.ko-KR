---
title: SharePoint Server 2013을 사용하는 Microsoft Azure의 인터넷 사이트
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: '요약: SharePoint Server 2013를 사용 하는 인터넷 사이트는 Azure 인프라 서비스에서 호스트 되는 이점을 활용할 수 있습니다. 이 문서에서는이 솔루션을 디자인 하 고 구현 하기 위한 리소스를 제공 합니다.'
ms.openlocfilehash: 26578133709959964e2f8ab1d01b562a526febcb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487910"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="95132-104">SharePoint Server 2013을 사용하는 Microsoft Azure의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="95132-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="95132-105">**요약:** SharePoint Server 2013를 사용 하는 인터넷 사이트는 Azure 인프라 서비스에서 호스트 되는 혜택을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95132-105">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services.</span></span> <span data-ttu-id="95132-106">이 문서에서는이 솔루션을 디자인 하 고 구현 하기 위한 리소스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-106">This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="95132-107">인터넷 사이트용 Azure 인프라 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="95132-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="95132-108">Microsoft Azure는 SharePoint Server 2013을 기반으로 인터넷 사이트를 호스팅하기 위한 뛰어난 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-108">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013.</span></span> <span data-ttu-id="95132-109">장점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95132-109">Advantages include the following:</span></span>
  
- <span data-ttu-id="95132-110">인프라를 구축 하는 대신 훌륭한 사이트 개발에 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="95132-111">수평 확장 및에서의 수요에 따라 솔루션을 확장 하는 유연성</span><span class="sxs-lookup"><span data-stu-id="95132-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="95132-112">필요한 자원에 대해서만 결제 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="95132-113">고객 계정에 대 한 Azure Active Directory를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="95132-114">상세한 보고 및 분석 같은 Office 365에서 현재 사용할 수 없는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="95132-115">리소스</span><span class="sxs-lookup"><span data-stu-id="95132-115">Resources</span></span>

<span data-ttu-id="95132-116">다음 기술 그림 및 문서에서는 SharePoint Server 2013를 사용 하 여 Azure에서 인터넷 사이트를 디자인 하 고 구현 하는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="95132-117">**리소스**</span><span class="sxs-lookup"><span data-stu-id="95132-117">**Resource**</span></span>|<span data-ttu-id="95132-118">**추가 정보**</span><span class="sxs-lookup"><span data-stu-id="95132-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="95132-119">**Azure의 SharePoint Server 2013 인터넷 사이트**</span><span class="sxs-lookup"><span data-stu-id="95132-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="95132-120">[![SharePoint를 사용한 Azure의 인터넷 사이트 이미지](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="95132-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="95132-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="95132-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="95132-122">이 아키텍처 모델에서는 주요 디자인 작업과 Azure의 인터넷 사이트에 대 한 권장 아키텍처 선택 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="95132-123">**디자인 샘플: SharePoint Server 2013 용 Azure의 인터넷 사이트**</span><span class="sxs-lookup"><span data-stu-id="95132-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="95132-124">[![디자인 샘플 이미지: SharePoint 2013용 Microsoft Azure의 인터넷 사이트](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="95132-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="95132-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="95132-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="95132-126">이 디자인 샘플을 자체 아키텍처의 시작 점으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="95132-127">**[SharePoint 용 Microsoft Azure 아키텍처 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="95132-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="95132-128">이 문서에서는 SharePoint 솔루션을 호스트 하도록 Azure 아키텍처를 디자인 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="95132-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="95132-129">**토론 참여**</span><span class="sxs-lookup"><span data-stu-id="95132-129">**Join the discussion**</span></span>

|<span data-ttu-id="95132-130">**연락처**</span><span class="sxs-lookup"><span data-stu-id="95132-130">**Contact us**</span></span>|<span data-ttu-id="95132-131">**설명**</span><span class="sxs-lookup"><span data-stu-id="95132-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="95132-132">**어떤 클라우드 채택 콘텐츠가 필요한가요?**</span><span class="sxs-lookup"><span data-stu-id="95132-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="95132-p104">여러 Microsoft 클라우드 플랫폼 및 서비스에 적용되는 클라우드 채택 콘텐츠를 만들고 있습니다. 클라우드 채택 콘텐츠에 대한 의견을 제공하거나 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)으로 이메일을 보내서 특정 콘텐츠를 요청하세요.</span><span class="sxs-lookup"><span data-stu-id="95132-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="95132-135">**클라우드 채택 토론에 가입**</span><span class="sxs-lookup"><span data-stu-id="95132-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="95132-136">클라우드 기반 솔루션에 관심이 있다면 CAAB(클라우드 채택 자문 위원회)에 가입하여 Microsoft 콘텐츠 개발자, 산업 전문가 및 전 세계 고객으로 구성된 더 크고 활발한 커뮤니티에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95132-136">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe.</span></span> <span data-ttu-id="95132-137">참가 하려면 자신을 Microsoft 기술 커뮤니티의 [caab (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 에 추가 하 고[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내 주세요.</span><span class="sxs-lookup"><span data-stu-id="95132-137">To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!).</span></span> <span data-ttu-id="95132-138">모든 사용자가 [caab 블로그에서](https://blogs.technet.com/b/solutions_advisory_board/)커뮤니티 관련 콘텐츠를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95132-138">Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/).</span></span> <span data-ttu-id="95132-139">그러나 CAAB 구성원은 새 클라우드 채택 리소스와 솔루션에 대해 설명하는 비공개 웹 세미나에 초대됩니다.</span><span class="sxs-lookup"><span data-stu-id="95132-139">However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.</span></span>  <br/> |
|<span data-ttu-id="95132-140">**여기에 표시된 아트 받기**</span><span class="sxs-lookup"><span data-stu-id="95132-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="95132-p106">이 문서에 표시된 아트의 편집 가능한 복사본을 원하시면 보내드리겠습니다. 아트의 URL과 제목을 적어서 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)으로 요청 이메일을 보내주세요.  </span><span class="sxs-lookup"><span data-stu-id="95132-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="95132-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95132-143">See Also</span></span>

[<span data-ttu-id="95132-144">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="95132-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



