---
title: 조직 외부의 사용자와 공동 작업
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords: NOCSH
description: 조직 외부의 사용자와 공동 작업용 Microsoft 365을 구성 하는 방법을 알아봅니다.
ms.openlocfilehash: 4cfaabd04a1f66592ab558bdca964fb6a1042855
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549087"
---
# <a name="collaborating-with-people-outside-your-organization"></a><span data-ttu-id="a49b1-103">조직 외부의 사용자와 공동 작업</span><span class="sxs-lookup"><span data-stu-id="a49b1-103">Collaborating with people outside your organization</span></span>

<span data-ttu-id="a49b1-104">기본적으로 Microsoft 365에서 조직 외부의 사용자와 공유는 SharePoint 및 OneDrive에 대해 사용 하도록 설정 되지만 팀에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-104">By default, in Microsoft 365, sharing with people outside your organization is enabled for SharePoint and OneDrive, but disabled for Teams.</span></span> <span data-ttu-id="a49b1-105">많은 SharePoint 및 OneDrive 외부 공유 시나리오는 추가 구성 없이 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-105">Many SharePoint and OneDrive external sharing scenarios work without further configuration.</span></span> <span data-ttu-id="a49b1-106">사용 중인 시나리오에 대 한 설정을 확인 하거나 새로 사용 하도록 설정 하려면 다음 옵션 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-106">To confirm the settings for a scenario that you're using, or enable a new one, choose from the following options:</span></span>

- <span data-ttu-id="a49b1-107">[문서 공동 작업](collaborate-on-documents.md) -파일 및 폴더에서 조직 외부의 사용자 (게스트 및 인증 되지 않은 사용자 모두)와의 공유 및 공동 작업을 허용 하도록 Microsoft 365을 구성 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-107">[Collaborate on documents](collaborate-on-documents.md) - Learn how to configure Microsoft 365 to allow sharing and collaboration with people outside your organization (both guests and unauthenticated users) on files and folders.</span></span>
- <span data-ttu-id="a49b1-108">[사이트에서 공동 작업](collaborate-in-a-site.md) -Microsoft 365을 구성 하 여 SharePoint 사이트와 게스트 공유를 사용 하도록 설정 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-108">[Collaborate in a site](collaborate-in-a-site.md) - Learn how to configure Microsoft 365 to enable sharing SharePoint sites with guests.</span></span>
- <span data-ttu-id="a49b1-109">[팀으로 공동 작업](collaborate-as-a-team.md) -팀에서 게스트 공동 작업을 사용 하도록 Microsoft 365을 구성 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-109">[Collaborate as a team](collaborate-as-a-team.md) - Learn how to configure Microsoft 365 to enable guest collaboration in Teams.</span></span>

<span data-ttu-id="a49b1-110">Microsoft 365에서 제공 하는 게스트 공유 설정에 대 한 자세한 내용은 [microsoft 365 guest 공유 설정 참조](microsoft-365-guest-settings.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a49b1-110">For a comprehensive look at the guest sharing settings available across Microsoft 365, see [Microsoft 365 guest sharing settings reference](microsoft-365-guest-settings.md).</span></span>

## <a name="secure-your-environment"></a><span data-ttu-id="a49b1-111">환경 보안</span><span class="sxs-lookup"><span data-stu-id="a49b1-111">Secure your environment</span></span>

<span data-ttu-id="a49b1-112">조직 외부의 사용자와 공유 하는 데 사용 하려는 시나리오를 사용 하도록 설정한 경우 실수로 또는 고의적인 부적절 한 공유 로부터 콘텐츠를 보호 하는 데 도움이 되는 추가 보호책을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-112">Once you've enabled the scenario that you want to use for sharing with people outside your organization, consider additional safeguards to help protect your content from accidental or intentional inappropriate sharing.</span></span>

- <span data-ttu-id="a49b1-113">[인증 되지 않은 사용자와 파일 및 폴더를 공유 하는 최상의 방법](best-practices-anonymous-sharing.md) -인증 되지 않은 사용자와의 공유 모범 사례에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-113">[Best practices for sharing files and folders with unauthenticated users](best-practices-anonymous-sharing.md) - Learn about best practices for sharing with unauthenticated users.</span></span>
- <span data-ttu-id="a49b1-114">[실수로 인 한 노출을 제한](sharing-limit-accidental-exposure.md) -실수로 중요 한 콘텐츠를 조직 외부의 사용자와 공유 하는 기회를 줄이는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-114">[Limit accidental exposure](sharing-limit-accidental-exposure.md) - Learn how to reduce the chances of accidentally sharing sensitive content with people outside your organization.</span></span>
- <span data-ttu-id="a49b1-115">[보안 게스트 공유 환경 만들기](create-a-secure-guest-sharing-environment.md) -Microsoft 365에서 제공 하는 도구를 통해 조직 외부의 사용자와의 공유를 안전한 방식으로 수행 하 고 관리 요구 사항을 충족 하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-115">[Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md)) - Learn about the tools provided in Microsoft 365 to help ensure that sharing with people outside your organization is done in a safe and secure manner and meets your governance requirements.</span></span>

## <a name="collaborate-with-partner-companies"></a><span data-ttu-id="a49b1-116">파트너 회사와 공동 작업</span><span class="sxs-lookup"><span data-stu-id="a49b1-116">Collaborate with partner companies</span></span>

<span data-ttu-id="a49b1-117">다른 조직의 여러 게스트가 포함 된 대규모 프로젝트에서 작업 하는 경우 또는 게스트가 자주 변경 되는 공급 업체 관계가 있는 경우에는 Azure Active Directory에서 권한 관리를 사용 하 여 게스트 관리를 단순화할 수 있습니다. 파트너 회사 들이 해당 책임을 공유할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a49b1-117">When you're working on a large project that involves many guests from another organization, or if you have an ongoing vendor relationship in which guests are often changing, you can use entitlement management in Azure Active Directory to simplify guest management and allow the partner company to share in that responsibility.</span></span> <span data-ttu-id="a49b1-118">자세한 내용은 [관리 되는 게스트를 사용 하 여 B2B 엑스트라넷 만들기](b2b-extranet.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a49b1-118">See [Create a B2B extranet with managed guests](b2b-extranet.md) for details.</span></span>

## <a name="limit-sharing"></a><span data-ttu-id="a49b1-119">제한 공유</span><span class="sxs-lookup"><span data-stu-id="a49b1-119">Limit sharing</span></span>

<span data-ttu-id="a49b1-120">Microsoft 365의 일부 공유 기능이 거 버 넌 스 정책과 충돌 하는 경우 공유 제한 옵션에 대 한 자세한 내용은 [microsoft 365의 공유 제한](microsoft-365-limit-sharing.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a49b1-120">If some of the sharing features in Microsoft 365 conflict with your governance policies, see [Limit sharing in Microsoft 365](microsoft-365-limit-sharing.md) to learn about options for limiting sharing.</span></span>

## <a name="see-also"></a><span data-ttu-id="a49b1-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a49b1-121">See Also</span></span>

[<span data-ttu-id="a49b1-122">Microsoft 365의 파일 공동 작업 소개</span><span class="sxs-lookup"><span data-stu-id="a49b1-122">Intro to file collaboration in Microsoft 365</span></span>](https://docs.microsoft.com/sharepoint/intro-to-file-collaboration)

[<span data-ttu-id="a49b1-123">Microsoft 365을 사용 하 여 SharePoint의 파일 공동 작업 계획</span><span class="sxs-lookup"><span data-stu-id="a49b1-123">Plan file collaboration in SharePoint with Microsoft 365</span></span>](https://docs.microsoft.com/sharepoint/deploy-file-collaboration)
