---
title: Microsoft 365 연결 모니터링
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Microsoft 365을 배포한 후에는 아래의 일부 도구 및 기법을 사용 하 여 Microsoft 365 연결을 유지할 수 있습니다. 저속 네트워크에서 Microsoft 365을 사용 하기 위한 최상의 방법과 공식적인 서비스 상태 및 연속성 지침을 이해 하는 것이 좋습니다.
ms.openlocfilehash: aa47ff76f70e48285c6ca5f21ffdf30f1db52521
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571011"
---
# <a name="monitor-microsoft-365-connectivity"></a><span data-ttu-id="3b3be-104">Microsoft 365 연결 모니터링</span><span class="sxs-lookup"><span data-stu-id="3b3be-104">Monitor Microsoft 365 connectivity</span></span>

<span data-ttu-id="3b3be-105">Microsoft 365을 배포한 후에는 아래의 일부 도구 및 기법을 사용 하 여 Microsoft 365 연결을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-105">Once you've deployed Microsoft 365, you can maintain Microsoft 365 connectivity using some of the tools and techniques below.</span></span> <span data-ttu-id="3b3be-106">[저속 네트워크에서 Microsoft 365을 사용 하기 위한 최상의 방법과](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)공식적인 [서비스 상태 및 연속성](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) 지침을 이해 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-106">You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Microsoft 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span> <span data-ttu-id="3b3be-107">[Microsoft 365 admin 앱](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) 을 가져오고 [microsoft 365 For Business-admin 도움말](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)을 책갈피로도 할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-107">You'll also want to grab the [Microsoft 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Microsoft 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-microsoft-365-connectivity"></a><span data-ttu-id="3b3be-108">Microsoft 365 연결 모니터링</span><span class="sxs-lookup"><span data-stu-id="3b3be-108">Monitoring Microsoft 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="3b3be-109">**새 Microsoft 365 끝점에 대 한 알림 받기**</span><span class="sxs-lookup"><span data-stu-id="3b3be-109">**Getting notified of new Microsoft 365 endpoints**</span></span> <br/> |<span data-ttu-id="3b3be-110">[Microsoft 365 끝점을 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)하는 경우 새 끝점을 게시할 때 알림을 받으려면 즐겨찾기 rss 수집기를 사용 하 여 rss 피드를 구독 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-110">If you're [Managing Microsoft 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader.</span></span> <span data-ttu-id="3b3be-111">다음은 Outlook을 [통해 구독](https://go.microsoft.com/fwlink/p/?LinkId=532416) 하거나 [RSS 피드 업데이트를 전자 메일로 보낼](https://go.microsoft.com/fwlink/p/?LinkId=532417)수 있도록 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-111">Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>  <br/> |
|<span data-ttu-id="3b3be-112">**System Center를 사용 하 여 Microsoft 365 모니터링**</span><span class="sxs-lookup"><span data-stu-id="3b3be-112">**Use System Center to Monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="3b3be-113">Microsoft System Center를 사용 하는 경우 [에는 Office 365 용 System Center 관리 팩](https://www.microsoft.com/download/details.aspx?id=43708) 을 다운로드 하 여 microsoft 365 오늘 모니터링을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-113">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Microsoft 365 today.</span></span> <span data-ttu-id="3b3be-114">자세한 내용은 [System Center Operations Manager를 사용 하 여](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) 관리 팩 작업 가이드 또는이 블로그 게시물 Office365 모니터링을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3b3be-114">For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="3b3be-115">**Azure ExpressRoute**의 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="3b3be-115">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="3b3be-116">Microsoft 365에 대 한 Azure Express 경로를 사용 하 여 Microsoft 365에 연결 하는 경우 azure [리소스 상태에서 문제 해결 시간을 줄이기](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) 위해 Microsoft 365 서비스 상태 대시보드 및 azure를 모두 사용 하 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-116">If you are connecting to Microsoft 365 using Azure ExpressRoute for Microsoft 365, you'll want to ensure that you're using both the Microsoft 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="3b3be-117">**AD FS와 Azure Active Directory Connect Health 사용**</span><span class="sxs-lookup"><span data-stu-id="3b3be-117">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="3b3be-118">Microsoft 365을 사용 하 여 Single Sign-on 용 AD FS를 사용 하는 경우 [AZURE Ad Connect Health를 사용 하 여 AD fs 인프라를 모니터링](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3b3be-118">If you're using AD FS for Single Sign-On with Microsoft 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="3b3be-119">**프로그래밍 방식으로 Microsoft 365 모니터링**</span><span class="sxs-lookup"><span data-stu-id="3b3be-119">**Programmatically monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="3b3be-120">[Microsoft 365 관리 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)에 대 한 지침을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3b3be-120">Refer to our guidance on the [Microsoft 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="3b3be-121">다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="3b3be-121">Here's a short link you can use to come back: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3b3be-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b3be-122">See also</span></span>

[<span data-ttu-id="3b3be-123">Microsoft 365 Enterprise 서비스 및 응용 프로그램 구성</span><span class="sxs-lookup"><span data-stu-id="3b3be-123">Configure Microsoft 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="3b3be-124">조직이 Microsoft 365 Enterprise를 사용할 수 있도록 준비</span><span class="sxs-lookup"><span data-stu-id="3b3be-124">Get your organization ready for Microsoft 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="3b3be-125">Microsoft 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="3b3be-125">Network planning and performance tuning for Microsoft 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="3b3be-126">Microsoft 365 통합 온-프레미스 환경</span><span class="sxs-lookup"><span data-stu-id="3b3be-126">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="3b3be-127">Microsoft 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="3b3be-127">Managing Microsoft 365 endpoints</span></span>](managing-office-365-endpoints.md)
