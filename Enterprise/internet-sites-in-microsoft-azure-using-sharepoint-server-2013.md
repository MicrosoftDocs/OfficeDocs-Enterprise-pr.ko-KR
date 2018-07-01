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
description: '요약: SharePoint Server 2013을 사용 하는 인터넷 사이트 Azure 인프라 서비스에서 호스트 되 여 활용 합니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하기 위한 리소스를 제공 합니다.'
ms.openlocfilehash: a2444cdf98e861530131d55ae80fc661f730ba57
ms.sourcegitcommit: 9f57825b10f20e3813732372541128ef187d52c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "20161791"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="4698e-104">SharePoint Server 2013을 사용하는 Microsoft Azure의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="4698e-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="4698e-p102">**요약:** SharePoint Server 2013을 사용 하는 인터넷 사이트 Azure 인프라 서비스에서 호스트 되 여 활용 합니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하기 위한 리소스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="4698e-107">인터넷 사이트를 위한 Azure 인프라 서비스를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="4698e-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="4698e-p103">Microsoft Azure SharePoint Server 2013에 따라 인터넷 사이트를 호스팅하기 위한 주목할 옵션을 제공 합니다. 장점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="4698e-110">인프라를 구축 하는 대신 뛰어난 사이트의 개발에 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="4698e-111">유연성에 및 조정 하 여 필요에 따라 기반 솔루션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="4698e-112">필요 하 고 사용 되는 리소스에 대해서만 지불 합니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="4698e-113">Azure Active Directory 사용자 계정에 대 한을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="4698e-114">상세 보고 및 분석 예: Office 365에서 현재 사용할 수 없는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="4698e-115">리소스</span><span class="sxs-lookup"><span data-stu-id="4698e-115">Resources</span></span>

<span data-ttu-id="4698e-116">기술에 대 한 다음 그림 및 문서를 디자인 하 고 SharePoint Server 2013을 사용 하 여 Azure의 인터넷 사이트를 구현 하는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="4698e-117">**리소스**</span><span class="sxs-lookup"><span data-stu-id="4698e-117">**Resource**</span></span>|<span data-ttu-id="4698e-118">**추가 정보**</span><span class="sxs-lookup"><span data-stu-id="4698e-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4698e-119">**Azure의 SharePoint Server 2013 인터넷 사이트**</span><span class="sxs-lookup"><span data-stu-id="4698e-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="4698e-120">[![SharePoint를 사용 하 여 Azure의 인터넷 사이트의 이미지](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="4698e-120">[![Image of Internet sites in Azure using SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="4698e-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552) \| [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="4698e-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="4698e-122">주요 디자인 활동을 간략하게 소개 하 고 Azure의 인터넷 사이트에 대 한 선택 하려는 아키텍처를 권장 하는이 아키텍처 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="4698e-123">**이 디자인 예제: SharePoint Server 2013에 대 한 Azure의 인터넷 사이트**</span><span class="sxs-lookup"><span data-stu-id="4698e-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="4698e-124">[![이 디자인 예제 이미지: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="4698e-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="4698e-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="4698e-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="4698e-126">시작 지점으로이 디자인 예제를 사용 하 여 자신의 아키텍처에 대 한.</span><span class="sxs-lookup"><span data-stu-id="4698e-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="4698e-127">**[SharePoint 2013용 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="4698e-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="4698e-128">이 문서에서는 호스트 SharePoint 솔루션을 Azure 아키텍처를 디자인 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="4698e-129">**토론 참여**</span><span class="sxs-lookup"><span data-stu-id="4698e-129">**Join the discussion**</span></span>

|<span data-ttu-id="4698e-130">**연락처**</span><span class="sxs-lookup"><span data-stu-id="4698e-130">**Contact us**</span></span>|<span data-ttu-id="4698e-131">**설명**</span><span class="sxs-lookup"><span data-stu-id="4698e-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4698e-132">**어떤 클라우드 채택 콘텐츠가 필요한가요?**</span><span class="sxs-lookup"><span data-stu-id="4698e-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="4698e-p104">여러 Microsoft 클라우드 플랫폼 및 서비스에 적용되는 클라우드 채택 콘텐츠를 만들고 있습니다. 클라우드 채택 콘텐츠에 대한 의견을 제공하거나 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)으로 이메일을 보내서 특정 콘텐츠를 요청하세요.  </span><span class="sxs-lookup"><span data-stu-id="4698e-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="4698e-135">**클라우드 채택 토론에 가입**</span><span class="sxs-lookup"><span data-stu-id="4698e-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="4698e-p105">클라우드 기반 솔루션에 열정을 갖고 인 경우에는 클라우드 채택 자문 보드 (CAAB) Microsoft 콘텐츠 개발자, 업계 전문가는 전세계 어디에서 고객의 더 큰, 생생한 커뮤니티와 연결할에 참가 하는 것이 좋습니다. 참가, Microsoft 기술 커뮤니티의 [CAAB (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 의 구성원으로 자신을 추가 하 고[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내주시기 합니다. 누구나 [CAAB 블로그 (영문)](https://blogs.technet.com/b/solutions_advisory_board/)에서 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원에 게 새 클라우드 채택 리소스 및 솔루션에 설명 하는 개인 웨 초대장을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4698e-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="4698e-140">**여기에 표시된 아트 받기**</span><span class="sxs-lookup"><span data-stu-id="4698e-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="4698e-p106">이 문서에 표시된 아트의 편집 가능한 복사본을 원하시면 보내드리겠습니다. 아트의 URL과 제목을 적어서 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)으로 요청 이메일을 보내주세요.  </span><span class="sxs-lookup"><span data-stu-id="4698e-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="4698e-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4698e-143">See Also</span></span>

[<span data-ttu-id="4698e-144">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="4698e-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



