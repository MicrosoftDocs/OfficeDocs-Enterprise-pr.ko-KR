---
title: Office 365 연결 모니터링
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Office 365를 배포한 후에는 아래의 도구 및 기술 일부를 사용하여 Office 365 연결을 유지할 수 있습니다. 느린 네트워크에서 Office 365를 사용하기 위한 최상의 방법뿐만 아니라 공식적인 서비스 상태 및 연속성 지침을 이해할 수 있습니다. 또한 Office 365 관리자 앱을 이용하고 비즈니스용 Office 365 - 관리자 도움말을 북마크할 수도 있습니다.
ms.openlocfilehash: 5a0a6e217d0f74f6266bffa1bd6037427f14e7bd
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843709"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="54d70-105">Office 365 연결 모니터링</span><span class="sxs-lookup"><span data-stu-id="54d70-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="54d70-p102">Office 365를 배포한 후에는 아래의 도구 및 기술 일부를 사용하여 Office 365 연결을 유지할 수 있습니다. [느린 네트워크에서 Office 365를 사용하기 위한 최상의 방법](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)뿐만 아니라 공식적인 [서비스 상태 및 연속성](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) 지침을 이해할 수 있습니다. 또한 [Office 365 관리자 앱](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)을 이용하고 비즈니스용 [Office 365 - 관리자 도움말](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)을 북마크할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54d70-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="54d70-109">Office 365 연결 모니터링</span><span class="sxs-lookup"><span data-stu-id="54d70-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="54d70-110">**새 Office 365 끝점에 대한 알림 받기**</span><span class="sxs-lookup"><span data-stu-id="54d70-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="54d70-p103">[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)를 사용하는 경우 새 끝점을 게시할 때 알림을 받고자 하면 즐겨찾는 RSS 수집기를 사용하여 RSS 피드를 구독할 수 있습니다. 여기에서는 [Outlook을 통해 구독](https://go.microsoft.com/fwlink/p/?LinkId=532416)하는 방법 또는 [RSS 피드를 전자 메일로 전송하여 업데이트](https://go.microsoft.com/fwlink/p/?LinkId=532417)할 수 있는 방법을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="54d70-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="54d70-113">**System Center를 사용하여 Office 365를 모니터링 하기**</span><span class="sxs-lookup"><span data-stu-id="54d70-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="54d70-p104">Microsoft System Center를 사용하는 경우 [Office 365용 System Center 관리 팩](https://www.microsoft.com/download/details.aspx?id=43708)을 다운로드하여 Office 365 모니터링을 시작할 수 있습니다. 자세한 지침은 관리 팩 작업 가이드 또는이 블로그 게시물의 [System Center Operations Manager를 사용하여 Office365 모니터링](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54d70-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="54d70-116">**Azure ExpressRoute**의 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="54d70-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="54d70-117">Office 365용 Azure ExpressRoute를 사용하여 Office 365에 연결하는 경우 Azure의 [Azure 리소스 상태로 인한 문제 해결 시간을 단축](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)뿐만 아니라 Office 365 서비스 상태 대시보드도 사용하고 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54d70-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="54d70-118">**AD FS와 Azure Active Directory Connect Health 사용**</span><span class="sxs-lookup"><span data-stu-id="54d70-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="54d70-119">Office 365에서 Single Sign-On AD FS를 사용하는 경우 Azure AD Connect Health를 사용하여 [AD FS 인프라 모니터링](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54d70-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="54d70-120">**프로그래밍 방식으로 Office 365 모니터링**</span><span class="sxs-lookup"><span data-stu-id="54d70-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="54d70-121">[Office 365 관리 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)에 대한 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54d70-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="54d70-122">다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="54d70-122">Here's a short link you can use to come back: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="54d70-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54d70-123">See also</span></span>

[<span data-ttu-id="54d70-124">Office 365 Enterprise 서비스 및 응용 프로그램 구성</span><span class="sxs-lookup"><span data-stu-id="54d70-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="54d70-125">조직에서 Office 365 Enterprise를 사용할 수 있도록 준비</span><span class="sxs-lookup"><span data-stu-id="54d70-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="54d70-126">Office 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="54d70-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="54d70-127">온-프레미스 환경과 Office 365 통합</span><span class="sxs-lookup"><span data-stu-id="54d70-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="54d70-128">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="54d70-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
