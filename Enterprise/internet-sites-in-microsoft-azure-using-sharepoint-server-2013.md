---
title: SharePoint Server 2013을 사용하는 Microsoft Azure의 인터넷 사이트
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: '요약: SharePoint Server 2013를 사용 하는 인터넷 사이트는 Azure 인프라 서비스에서 호스트 되는 이점을 활용할 수 있습니다. 이 문서에서는이 솔루션을 디자인 하 고 구현 하기 위한 리소스를 제공 합니다.'
ms.openlocfilehash: 7791da6954aea49b9292967fe32311c529bedc69
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845099"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="c0e9c-104">SharePoint Server 2013을 사용하는 Microsoft Azure의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="c0e9c-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="c0e9c-105">**요약:** SharePoint Server 2013를 사용 하는 인터넷 사이트는 Azure 인프라 서비스에서 호스트 되는 혜택을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-105">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services.</span></span> <span data-ttu-id="c0e9c-106">이 문서에서는이 솔루션을 디자인 하 고 구현 하기 위한 리소스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-106">This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="c0e9c-107">인터넷 사이트용 Azure 인프라 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="c0e9c-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="c0e9c-108">Microsoft Azure는 SharePoint Server 2013을 기반으로 인터넷 사이트를 호스팅하기 위한 뛰어난 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-108">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013.</span></span> <span data-ttu-id="c0e9c-109">장점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-109">Advantages include the following:</span></span>
  
- <span data-ttu-id="c0e9c-110">인프라를 구축 하는 대신 훌륭한 사이트 개발에 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="c0e9c-111">수평 확장 및에서의 수요에 따라 솔루션을 확장 하는 유연성</span><span class="sxs-lookup"><span data-stu-id="c0e9c-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="c0e9c-112">필요한 자원에 대해서만 결제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="c0e9c-113">고객 계정에 대 한 Azure Active Directory를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="c0e9c-114">상세한 보고 및 분석 같은 Office 365에서 현재 사용할 수 없는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="c0e9c-115">리소스</span><span class="sxs-lookup"><span data-stu-id="c0e9c-115">Resources</span></span>

<span data-ttu-id="c0e9c-116">다음 기술 그림 및 문서에서는 SharePoint Server 2013를 사용 하 여 Azure에서 인터넷 사이트를 디자인 하 고 구현 하는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="c0e9c-117">**리소스**</span><span class="sxs-lookup"><span data-stu-id="c0e9c-117">**Resource**</span></span>|<span data-ttu-id="c0e9c-118">**추가 정보**</span><span class="sxs-lookup"><span data-stu-id="c0e9c-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0e9c-119">**Azure의 SharePoint Server 2013 인터넷 사이트**</span><span class="sxs-lookup"><span data-stu-id="c0e9c-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="c0e9c-120">[![SharePoint를 사용한 Azure의 인터넷 사이트 이미지](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="c0e9c-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="c0e9c-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="c0e9c-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="c0e9c-122">이 아키텍처 모델에서는 주요 디자인 작업과 Azure의 인터넷 사이트에 대 한 권장 아키텍처 선택 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="c0e9c-123">**디자인 샘플: SharePoint Server 2013 용 Azure의 인터넷 사이트**</span><span class="sxs-lookup"><span data-stu-id="c0e9c-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="c0e9c-124">[![디자인 샘플 이미지: SharePoint 2013용 Microsoft Azure의 인터넷 사이트](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="c0e9c-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="c0e9c-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="c0e9c-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="c0e9c-126">이 디자인 샘플을 자체 아키텍처의 시작 점으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="c0e9c-127">**[SharePoint 용 Microsoft Azure 아키텍처 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="c0e9c-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="c0e9c-128">이 문서에서는 SharePoint 솔루션을 호스트 하도록 Azure 아키텍처를 디자인 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e9c-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="c0e9c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0e9c-129">See Also</span></span>

[<span data-ttu-id="c0e9c-130">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="c0e9c-130">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



