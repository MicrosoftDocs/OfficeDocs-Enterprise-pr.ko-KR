---
title: 격리된 SharePoint Online 팀 사이트
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
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: '요약: 격리된 SharePoint Online 팀 사이트의 용도에 대해 알아봅니다.'
ms.openlocfilehash: 86aa5fb9fa4d4eb2f76e1e32a6fcd8bda7b29b76
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="a1816-103">격리된 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="a1816-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="a1816-104">**요약:** 격리된 SharePoint Online 팀 사이트의 용도에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="a1816-p101">SharePoint Online 팀 사이트는 Microsoft Office 365에서 노트, 문서, 기사, 일정 및 기타 리소스의 공동 작업 공간을 신속하게 만들 수 있는 편리한 방법입니다. SharePoint Online 팀 사이트는 Office 365 그룹을 기준으로 하며, 그룹 구성원의 개인 집합이나 전체 조직과 오픈해서 공동 작업할 수 있도록 하는 간편한 관리 모델을 제공합니다. 기본 SharePoint Online 팀 사이트는 Office 365 그룹 구성원이 다른 사용자를 초대하고 사용 권한 설정을 제어할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="a1816-p102">그러나 경우에 따라 하려는 그룹 멤버 자격 및 SharePoint에 의해만 관리 되는 사용 권한 수준, SharePoint Online을 통해 해당 사이트의 사용 권한을 제어 더욱 긴밀 하 게 됩니다 공동 작업에 대 한 SharePoint Online 팀 사이트 만들기 관리자가 있습니다. 오늘은이 있는 격리 된 사이트를 사용자는 사이트나 공동 작업, 해당 내용 보기 사이트 관리 하는 집합에 격리 됩니다. 다음에 대해 격리된 사이트가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="a1816-111">조직 내의 비밀 프로젝트</span><span class="sxs-lookup"><span data-stu-id="a1816-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="a1816-112">조직에서 고도로 민감하거나 중요한 지적 재산권이 포함된 위치</span><span class="sxs-lookup"><span data-stu-id="a1816-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="a1816-113">조직이 수행했거나 조직을 대상으로 이행된 법적 조치에 대한 리소스</span><span class="sxs-lookup"><span data-stu-id="a1816-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="a1816-114">약간의 중복된 측면이 있지만 대부분이 별도 비즈니스 엔터티로 존재하는 여러 조직 사이에서 Office 365 구독을 공유하려고 하는 경우</span><span class="sxs-lookup"><span data-stu-id="a1816-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="a1816-115">다음은 격리된 사이트에 대한 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="a1816-116">SharePoint Online 관리자만 사이트 관리를 수행할 수 있습니다. 이러한 사이트 관리에는 사이트에 액세스하기 위한 그룹 구성원 자격과 사용자 지정 권한 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="a1816-117">사이트의 구성원은 팀 사이트에 다른 구성원을 초대할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="a1816-p103">격리된 사이트의 구성원이 아닌 사용자는 사이트에 대한 액세스를 요청할 수 없습니다. 해당 사이트와 연결된 모든 URL에 액세스하려고 하면 액세스 거부됨 웹 페이지가 수신됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="a1816-p104">SharePoint Online 관리자가 중앙 집중식 액세스 제어 및 사용자 지정 권한을 요구하면 시간이 지나면서 사이트가 격리되는 문제가 발생합니다. 예를 들어, 현재 구성원은 의도적으로나 실수로 사이트의 구성원이 아닌 Office 365 구독 내의 다른 사용자를 초대하거나 해당 사용자에 대한 사용자 지정 권한을 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="a1816-122">격리된 사이트를 다음과 같은 기타 기능과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="a1816-123">사이트의 리소스를 암호화 상태로 유지하는 정보 권한 관리. 이 기능이 로컬로 다운로드되거나 전체 조직에서 사용할 수 있는 다른 사이트로 업로드된 경우도 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1816-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="a1816-124">사용자가 사이트의 리소스(예: 파일)를 전자 메일로 전송하지 못하게 하는 데이터 손실 방지</span><span class="sxs-lookup"><span data-stu-id="a1816-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="a1816-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a1816-125">Next steps</span></span>

<span data-ttu-id="a1816-126">평가판 구독에서 격리된 SharePoint Online 팀 사이트를 체험해보려면 [개발/테스트 환경에서 격리된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-site-dev-test-environment.md)의 단계별 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1816-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a1816-127">프로덕션 환경에 격리된 SharePoint Online 팀 사이트를 배포할 준비가 되면 [격리된 SharePoint Online 팀 사이트 디자인](design-an-isolated-sharepoint-online-team-site.md)에서 단계별 디자인 고려 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1816-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a1816-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1816-128">See Also</span></span>

<span data-ttu-id="a1816-129">[격리된 SharePoint Online 팀 사이트 디자인](design-an-isolated-sharepoint-online-team-site.md)</span><span class="sxs-lookup"><span data-stu-id="a1816-129">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
[<span data-ttu-id="a1816-130">격리된 SharePoint Online 팀 사이트 관리</span><span class="sxs-lookup"><span data-stu-id="a1816-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="a1816-131">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="a1816-131">Security solutions</span></span>](security-solutions.md)

<span data-ttu-id="a1816-132">[격리된 SharePoint Online 팀 사이트 배포](deploy-an-isolated-sharepoint-online-team-site.md)</span><span class="sxs-lookup"><span data-stu-id="a1816-132">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>


