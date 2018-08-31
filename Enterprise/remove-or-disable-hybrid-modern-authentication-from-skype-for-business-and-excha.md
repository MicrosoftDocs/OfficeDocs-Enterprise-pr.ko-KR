---
title: 비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: 하이브리드 현대 인증 (HMA)는 현재 환경에 적합 하지 찾을에을 설정한 경우에 HMA를 해제할 수 있습니다. 이 문서에 설명 방법입니다.
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542151"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="1e2c9-104">비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="1e2c9-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="1e2c9-p102">하이브리드 현대 인증 (HMA)는 현재 환경에 적합 하지 찾을에을 설정한 경우에 HMA를 해제할 수 있습니다. 이 문서에 설명 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="1e2c9-107">이 문서는 누구 입니까?</span><span class="sxs-lookup"><span data-stu-id="1e2c9-107">Who is this article for?</span></span>

<span data-ttu-id="1e2c9-108">비즈니스 온라인 또는 온-프레미스, 및/또는 Exchange Online 또는 온-프레미스에 대 한 Skype에서 현대 인증을 사용 하도록 설정 하 고 HMA를 사용 하지 않도록 설정 해야 발견 했을 때, 하는 경우 이러한 단계 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>
  
 <span data-ttu-id="1e2c9-109">**중요 한** 비즈니스 온라인 또는 온-프레미스 용 Skype 하 고 있는 경우 ' [비즈니스 토폴로지 용 Skype 현대 인증을 지원](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 문서를 참조 하는 혼합 토폴로지 HMA 있고 시작 하기 전에 지원 되는 토폴로지를 살펴보는 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-109">**Important** See the ' [Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="1e2c9-110">하이브리드 현대 인증 (Exchange)를 사용 하지 않도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e2c9-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="1e2c9-111">**Exchange 온-프레미스**: Exchange 관리 셸을 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following command.</span></span> 
    
1. <span data-ttu-id="1e2c9-112">Set-organizationconfig-OAuth2ClientProfileEnabled $false</span><span class="sxs-lookup"><span data-stu-id="1e2c9-112">Set-OrganizationConfig -OAuth2ClientProfileEnabled $false</span></span>
    
2. <span data-ttu-id="1e2c9-113">Set-authserver-Identity evoSTS-IsDefaultAuthorizationEndpoint $false</span><span class="sxs-lookup"><span data-stu-id="1e2c9-113">Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false</span></span>
    
2. <span data-ttu-id="1e2c9-p103">**Exchange Online**: 원격 PowerShell 사용한 Exchange Online에 연결 합니다. E'로 *OAuth2ClientProfileEnabled* 플래그를 설정 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-p103">**Exchange Online**: Connect to Exchange Online with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false'.</span></span> 
    
1. <span data-ttu-id="1e2c9-116">Set-organizationconfig-OAuth2ClientProfileEnabled: $false</span><span class="sxs-lookup"><span data-stu-id="1e2c9-116">Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false</span></span>
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="1e2c9-117">하이브리드 현대 인증 (비즈니스용 Skype)를 사용 하지 않도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e2c9-117">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="1e2c9-118">**비즈니스 온-프레미스 용 Skype**: 비즈니스 관리 셸의 Skype에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-118">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell.</span></span>
    
1. <span data-ttu-id="1e2c9-119">Set-csoauthconfiguration ClientAuthorizationOAuthServerIdentity ""</span><span class="sxs-lookup"><span data-stu-id="1e2c9-119">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""</span></span>
    
2. <span data-ttu-id="1e2c9-p104">**온라인 비즈니스에 대 한 Skype**: 원격 PowerShell 사용한 온라인 비즈니스에 대 한 Skype에 연결 합니다. 현대 인증을 사용 하지 않도록 설정 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-p104">**Skype for Business Online**: Connect to Skype for Business Online with Remote PowerShell. Run the following command to disable Modern Authentication.</span></span> 
    
1. <span data-ttu-id="1e2c9-122">Set-csoauthconfiguration ClientAdalAuthOverride 허용 되지 않음</span><span class="sxs-lookup"><span data-stu-id="1e2c9-122">Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed</span></span>
    
<span data-ttu-id="1e2c9-123">[현대 인증 개요에 다시 연결](hybrid-modern-auth-overview.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e2c9-123">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

