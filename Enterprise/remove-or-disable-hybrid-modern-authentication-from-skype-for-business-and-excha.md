---
title: 비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 현재 환경에 적합 하지 않은 것을 찾기 위해 HMA (Hybrid 현대 Authentication)만 사용 하도록 설정한 경우에는 HMA를 사용 하지 않도록 설정할 수 있습니다. 이 문서에서는 이러한 방법을 설명 합니다.
ms.openlocfilehash: ad9db5894670b49d2d9a1f385cd9f6acd43ea00f
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998207"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="94f8f-104">비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="94f8f-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="94f8f-105">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="94f8f-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="94f8f-106">현재 환경에 적합 하지 않은 것을 찾기 위해 HMA (Hybrid 현대 Authentication)만 사용 하도록 설정한 경우에는 HMA를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-106">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="94f8f-107">이 문서에서는 이러한 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-107">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="94f8f-108">이 문서는 누구에 게 있나요?</span><span class="sxs-lookup"><span data-stu-id="94f8f-108">Who is this article for?</span></span>

<span data-ttu-id="94f8f-109">비즈니스용 Skype Online 또는 온-프레미스 및/또는 Exchange Online 또는 온-프레미스에서 최신 인증을 사용 하도록 설정한 경우 HMA를 사용 하지 않도록 설정 해야 하는 경우 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-109">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94f8f-110">비즈니스용 Skype Online 또는 온-프레미스에 있는 경우 '[최신 인증과 함께 지원 되는 비즈니스용 skype 토폴로지](https://technet.microsoft.com/library/mt803262.aspx)' 문서를 참조 하 고, 혼합 된 토폴로지 HMA를 사용 하며, 시작 하기 전에 지원 되는 토폴로지를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-110">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="94f8f-111">하이브리드 최신 인증을 사용 하지 않도록 설정 하는 방법 (Exchange)</span><span class="sxs-lookup"><span data-stu-id="94f8f-111">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="94f8f-112">**Exchange 온-프레미스**: Exchange 관리 셸을 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-112">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="94f8f-113">**Exchange online**: 원격 PowerShell을 사용 [하 여 exchange online에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-113">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="94f8f-114">다음 명령을 실행 하 여 *OAuth2ClientProfileEnabled* 플래그를 ' f a l i e '로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-114">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="94f8f-115">하이브리드 최신 인증을 사용 하지 않도록 설정 하는 방법 (비즈니스용 Skype)</span><span class="sxs-lookup"><span data-stu-id="94f8f-115">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="94f8f-116">비즈니스용 **Skype 온-프레미스**: 비즈니스용 Skype 관리 셸에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-116">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="94f8f-117">비즈니스용 **Skype online**: 원격 PowerShell을 사용 [하 여 비즈니스용 skype online에 연결](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-117">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="94f8f-118">다음 명령을 실행 하 여 최신 인증을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-118">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="94f8f-119">[최신 인증 개요에 다시 연결](hybrid-modern-auth-overview.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="94f8f-119">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

