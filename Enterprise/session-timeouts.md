---
title: Microsoft 365에 대 한 세션 시간 제한
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: Microsoft 365 클라이언트 앱에서 세션 시간 제한을 사용 하 여 보안을 조정 하 고 액세스 용이성을 결정 하는 방법을 알아봅니다.
ms.openlocfilehash: 72146ca49e07bf3641982bc880897456699d0877
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605220"
---
# <a name="session-timeouts-for-microsoft-365"></a><span data-ttu-id="c1a87-103">Microsoft 365에 대 한 세션 시간 제한</span><span class="sxs-lookup"><span data-stu-id="c1a87-103">Session timeouts for Microsoft 365</span></span>

<span data-ttu-id="c1a87-104">세션 수명은 Microsoft 365 인증의 중요 한 부분이 며, 균형 조정 보안의 중요 한 구성 요소 이며 사용자에 게 자격 증명을 입력 하 라는 메시지가 표시 되는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-104">Session lifetimes are an important part of authentication for Microsoft 365 and are an important component in balancing security and the number of times users are prompted for their credentials.</span></span>
  
## <a name="session-times-for-microsoft-365-services"></a><span data-ttu-id="c1a87-105">Microsoft 365 서비스의 세션 시간</span><span class="sxs-lookup"><span data-stu-id="c1a87-105">Session times for Microsoft 365 services</span></span>

<span data-ttu-id="c1a87-106">사용자가 Microsoft 365 웹 앱 또는 모바일 앱에서 인증 하는 경우 세션이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-106">When users authenticate in any of the Microsoft 365 web apps or mobile apps, a session is established.</span></span> <span data-ttu-id="c1a87-107">세션을 진행 하는 동안에는 사용자가 다시 인증할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-107">For the duration of the session, users won't need to re-authenticate.</span></span> <span data-ttu-id="c1a87-108">세션은 사용자가 비활성 상태일 때, 브라우저나 탭을 닫을 때, 또는 암호를 다시 설정 했을 때와 같은 다른 이유로 인해 인증 토큰이 만료 될 때 만료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-108">Sessions can expire when users are inactive, when they close the browser or tab, or when their authentication token expires for other reasons such as when their password has been reset.</span></span> <span data-ttu-id="c1a87-109">Microsoft 365 서비스의 세션 시간 제한은 각 서비스의 일반적인 사용과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-109">The Microsoft 365 services have different session timeouts to correspond with the typical use of each service.</span></span>
  
<span data-ttu-id="c1a87-110">다음 표에는 Microsoft 365 서비스의 세션 수명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-110">The following table lists the session lifetimes for Microsoft 365 services:</span></span>
  
|<span data-ttu-id="c1a87-111">**Microsoft 365 서비스**</span><span class="sxs-lookup"><span data-stu-id="c1a87-111">**Microsoft 365 service**</span></span>|<span data-ttu-id="c1a87-112">**세션 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="c1a87-112">**Session timeout**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c1a87-113">Microsoft 365 관리 센터</span><span class="sxs-lookup"><span data-stu-id="c1a87-113">Microsoft 365 admin center</span></span>  <br/> |<span data-ttu-id="c1a87-114">관리자 센터에 대 한 자격 증명을 8 시간 마다 제공 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-114">You are asked to provide credentials for the admin center every 8 hours.</span></span>  <br/> |
|<span data-ttu-id="c1a87-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c1a87-115">SharePoint Online</span></span>  <br/> |<span data-ttu-id="c1a87-116">사용자가 **로그인 유지**를 선택 하기만 하면 5 일 동안 비활성 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-116">5 days of inactivity as long as the users chooses **Keep me signed in**.</span></span> <span data-ttu-id="c1a87-117">사용자가 24 시간 이상이 이전 로그인에서 전달 된 후에 SharePoint Online에 다시 액세스 하는 경우 시간 제한 값은 5 일로 다시 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-117">If the user accesses SharePoint Online again after 24 or more hours have passed from the previous sign-in, the timeout value is reset to 5 days.</span></span>  <br/> |
|<span data-ttu-id="c1a87-118">Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="c1a87-118">Outlook Web App</span></span>  <br/> |<span data-ttu-id="c1a87-119">6 시간</span><span class="sxs-lookup"><span data-stu-id="c1a87-119">6 hours.</span></span>  <br/> <span data-ttu-id="c1a87-120">[Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) Cmdlet에서 _ActivityBasedAuthenticationTimeoutInterval_ 매개 변수를 사용 하 여이 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-120">You can change this value by using the  _ActivityBasedAuthenticationTimeoutInterval_ parameter in the [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet.</span></span>  <br/> |
|<span data-ttu-id="c1a87-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c1a87-121">Azure Active Directory</span></span>  <br/> <span data-ttu-id="c1a87-122">(최신 인증을 사용 하는 Office 2013 Windows 클라이언트에서 사용)</span><span class="sxs-lookup"><span data-stu-id="c1a87-122">(Used by Office 2013 Windows clients with modern authentication enabled)</span></span>  <br/> | <span data-ttu-id="c1a87-123">최신 인증은 액세스 토큰 및 새로 고침 토큰을 사용 하 여 Azure Active Directory를 사용 하는 Microsoft 365 리소스에 대 한 사용자 액세스 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-123">Modern authentication uses access tokens and refresh tokens to grant user access to Microsoft 365 resources using Azure Active Directory.</span></span> <span data-ttu-id="c1a87-124">액세스 토큰은 인증을 완료 한 후 제공 되는 JSON 웹 토큰이 며 1 시간 동안 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-124">An access token is a JSON Web Token provided after a successful authentication and is valid for 1 hour.</span></span> <span data-ttu-id="c1a87-125">수명이 긴 새로 고침 토큰도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-125">A refresh token with a longer lifetime is also provided.</span></span> <span data-ttu-id="c1a87-126">액세스 토큰이 만료 되 면 Office 클라이언트는 유효한 새로 고침 토큰을 사용 하 여 새 액세스 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-126">When access tokens expire, Office clients use a valid refresh token to obtain a new access token.</span></span> <span data-ttu-id="c1a87-127">사용자의 초기 인증이 여전히 유효한 경우이 exchange가 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-127">This exchange succeeds if the user's initial authentication is still valid.</span></span>  <br/>  <span data-ttu-id="c1a87-128">새로 고침 토큰은 90 일 동안 유효 하며 지속적인 사용을 위해서는 해지할 때까지 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-128">Refresh tokens are valid for 90 days, and with continuous use, they can be valid until revoked.</span></span>  <br/>  <span data-ttu-id="c1a87-129">새로 고침 토큰은 다음과 같은 여러 가지 이벤트로 무효화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-129">Refresh tokens can be invalidated by several events such as :</span></span>  <br/>  <span data-ttu-id="c1a87-130">새로 고침 토큰이 발급 된 이후 사용자의 암호가 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-130">User's password has changed since the refresh token was issued.</span></span>  <br/>  <span data-ttu-id="c1a87-131">관리자는 사용자가 액세스 하려고 하는 리소스에 대 한 액세스를 제한 하는 조건부 액세스 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-131">An administrator can apply conditional access policies which restrict access to the resource the user is trying to access.</span></span>  <br/> |
|<span data-ttu-id="c1a87-132">Android, iOS 및 Windows 10 용 SharePoint 및 OneDrive 모바일 앱</span><span class="sxs-lookup"><span data-stu-id="c1a87-132">SharePoint and OneDrive mobile apps for Android, iOS, and Windows 10</span></span>  <br/> |<span data-ttu-id="c1a87-133">액세스 토큰의 기본 수명은 1 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-133">The default lifetime for the access token is 1 hour.</span></span> <span data-ttu-id="c1a87-134">새로 고침 토큰의 기본 최대 비활성 시간은 90 일입니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-134">The default max inactive time of the refresh token is 90 days.</span></span>  <br/> [<span data-ttu-id="c1a87-135">토큰 및 토큰 수명 구성 방법에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="c1a87-135">Learn more about tokens and how to configure token lifetimes</span></span>](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> <span data-ttu-id="c1a87-136">새로 고침 토큰을 해지 하려면 사용자의 Microsoft 365 암호를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-136">To revoke the refresh token, you can reset the user's Microsoft 365 password</span></span>  <br/> |
|<span data-ttu-id="c1a87-137">Microsoft 365 로그인이 포함 된 Yammer</span><span class="sxs-lookup"><span data-stu-id="c1a87-137">Yammer with Microsoft 365 Sign-In</span></span>  <br/> |<span data-ttu-id="c1a87-138">브라우저의 수명입니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-138">Lifetime of the browser.</span></span> <span data-ttu-id="c1a87-139">사용자가 브라우저를 닫고 새 브라우저에서 Yammer에 액세스 하는 경우 Yammer는 Microsoft 365를 사용 하 여이를 다시 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-139">If users close the browser and access Yammer in a new browser, Yammer will re-authenticate them with Microsoft 365.</span></span> <span data-ttu-id="c1a87-140">사용자가 쿠키를 캐시 하는 타사 브라우저를 사용 하는 경우 브라우저를 다시 열 때 다시 인증 하지 않아도 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-140">If users use third-party browsers that cache cookies, they may not need to re-authenticate when they reopen the browser.</span></span>  <br/> <span data-ttu-id="c1a87-141">> [!NOTE]> Yammer에 대해 Microsoft 365 로그인을 사용 하는 네트워크에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a87-141">> [!NOTE]> This is valid only for networks using Microsoft 365 Sign-In for Yammer.</span></span>           |
   

