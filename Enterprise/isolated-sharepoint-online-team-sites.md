---
title: "격리 된 SharePoint Online 팀 사이트"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: "요약: 격리 된 SharePoint Online 팀 사이트에 대 한 사용 하는 방법에 대 한 설명입니다."
ms.openlocfilehash: 3de60bb19498d9f84c18e51181a3fedda9846bdf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="aa63b-103">격리 된 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="aa63b-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="aa63b-104">**요약:** 격리 된 SharePoint Online 팀 사이트에 대 한 사용에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="aa63b-p101">SharePoint Online 팀 사이트는 쉽게 신속 하 게 Microsoft Office 365의 메모, 문서, 문서, 일정, 및 기타 리소스의 공동 작업을 위한 공간을 만들 수 있습니다. SharePoint Online 팀 사이트는 그룹을 기반으로 Office 365 및 그룹 구성원 또는 전체 조직의 개인 설정 된 open 공동 작업을 허용 하도록 간소화 된 관리 모델을 포함 합니다. 기본 SharePoint Online 팀 사이트에는 다른 사용자를 초대 하 고 사용 권한 설정을 제어 하는 Office 365 그룹의 구성원 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="aa63b-p102">그러나 일부 경우에 만들려는 SharePoint Online 팀 사이트를 공동 작업에 대 한 그룹 구성원 자격 및만 SharePoint가 관리 하는 사용 권한 수준, SharePoint Online을 통해 해당 사이트의 사용 권한을 제어 더 밀접 하 게 됩니다. 관리자가 됩니다. 이 격리는 또는 공동 작업의 내용을 보고 사이트를 관리 하는 사용자 집합에 있는 격리 된 사이트를 호출 합니다. 다음에 대 한 격리 하는 사이트를 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="aa63b-111">조직 내에서 비밀 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="aa63b-112">조직에 대 한 매우 중요 한 또는 중요 한 지적 재산에 대 한 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="aa63b-113">조직 또는 종속 되는에서 수행 하는 법적 작업에 대 한 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="aa63b-114">Office 365를 공유 하려면 일부 있는 여러 조직 간에 구독 겹칠 때는, 있지만 대부분의 경우 별도 비즈니스 엔터티로 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="aa63b-115">격리 된 사이트의 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="aa63b-116">SharePoint Online 관리자만 사이트 및 사용자 지정 사용 권한 구성에 대 한 액세스에 대 한 그룹 구성원 자격을 포함 하는 사이트 관리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="aa63b-117">사이트의 구성원은 팀 사이트에 다른 구성원을 초대할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="aa63b-p103">격리 된 사이트의 구성원이 아닌 사용자는 사이트에 대 한 액세스를 요청할 수 없습니다. 사이트에 연결 된 모든 URL에 액세스 하려고 할 때 웹 페이지를 거부 하는 액세스를 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="aa63b-p104">중앙 집중화 된 액세스 제어 및 SharePoint Online 관리자가 사용자 지정 사용 권한 요구의 단점은 시간에 따른 사이트 남아 격리 된 것입니다. 예, 현재 구성원 수는 없습니다, 그리고 의도적으로 또는 실수로, 초대 또는 사이트의 구성원이 아니어야가 Office 365 구독 내의 다른 사용자에 대 한 사용자 지정 권한을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="aa63b-122">격리 하는 사이트와 같은 다른 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="aa63b-123">정보 권한 관리 상태로 유지 하는 사이트의 리소스를 로컬로 다운로드 하는 경우에 암호화 및 전체 조직에 사용할 수 있는 다른 사이트에 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="aa63b-124">예: 파일, 전자 메일에는 사이트의 리소스를 보내지 못하게 하려면 데이터 손실 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="aa63b-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="aa63b-125">Next steps</span></span>

<span data-ttu-id="aa63b-126">평가판 구독에서 격리 된 SharePoint Online 팀 사이트를 실행 하려면 [격리 된 SharePoint Online 팀 사이트 개발/테스트 환경](isolated-sharepoint-online-team-site-dev-test-environment.md)에 대 한 단계별 지침을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="aa63b-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="aa63b-127">프로덕션 환경에서 격리 된 SharePoint Online 팀 사이트를 배포할 준비가 되 면 [디자인 한 격리 된 SharePoint Online 팀 사이트에](design-an-isolated-sharepoint-online-team-site.md)대 한 단계별 디자인 고려 사항을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="aa63b-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aa63b-128">See Also</span><span class="sxs-lookup"><span data-stu-id="aa63b-128">See Also</span></span>

[<span data-ttu-id="aa63b-129">격리 된 SharePoint Online 팀 사이트를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-129">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="aa63b-130">SharePoint Online 팀 사이트를 격리 관리</span><span class="sxs-lookup"><span data-stu-id="aa63b-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="aa63b-131">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="aa63b-131">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="aa63b-132">SharePoint Online 팀 사이트를 격리를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa63b-132">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)


