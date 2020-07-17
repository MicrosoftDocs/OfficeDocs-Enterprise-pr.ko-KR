---
title: 하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 최신 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법 이며 비즈니스용 Skype 서버 온-프레미스 및 Exchange server 온-프레미스 및 비즈니스용 Skype 하이브리드에 사용할 수 있습니다.
ms.openlocfilehash: 6415fe374f63093b44ebacc125dc40c9ea70e898
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052511"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="74a6e-103">하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="74a6e-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="74a6e-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="74a6e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="74a6e-105">최신 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법 이며 비즈니스용 Skype 서버 온-프레미스 및 Exchange server 온-프레미스 및 비즈니스용 Skype 하이브리드에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-105">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, and split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="74a6e-106">**중요** 최신 인증 (MA)에 대 한 자세한 내용과 회사나 조직에서이를 사용 하는 데 도움이 될 수 있는 이유를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="74a6e-106">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="74a6e-107">[이 문서](hybrid-modern-auth-overview.md) 에서 개요를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-107">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="74a6e-108">MA에서 어떤 비즈니스용 Skype 토폴로지가 지원 되는지 파악 해야 하는 경우 여기에서 문서화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-108">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span>
  
 <span data-ttu-id="74a6e-109">**시작 하기 전에**다음과 같은 용어를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-109">**Before we begin**, I use these terms:</span></span>
  
- <span data-ttu-id="74a6e-110">최신 인증 (MA)</span><span class="sxs-lookup"><span data-stu-id="74a6e-110">Modern Authentication (MA)</span></span>

- <span data-ttu-id="74a6e-111">하이브리드 최신 인증 (HMA)</span><span class="sxs-lookup"><span data-stu-id="74a6e-111">Hybrid Modern Authentication (HMA)</span></span>

- <span data-ttu-id="74a6e-112">Exchange 온-프레미스 (EXCH)</span><span class="sxs-lookup"><span data-stu-id="74a6e-112">Exchange on-premises (EXCH)</span></span>

- <span data-ttu-id="74a6e-113">Exchange Online (EXO)</span><span class="sxs-lookup"><span data-stu-id="74a6e-113">Exchange Online (EXO)</span></span>

- <span data-ttu-id="74a6e-114">비즈니스용 Skype 온-프레미스 (SFB)</span><span class="sxs-lookup"><span data-stu-id="74a6e-114">Skype for Business on-premises (SFB)</span></span>

- <span data-ttu-id="74a6e-115">비즈니스용 Skype Online (SFBO)</span><span class="sxs-lookup"><span data-stu-id="74a6e-115">Skype for Business Online (SFBO)</span></span>

<span data-ttu-id="74a6e-116">또한이 문서의 그래픽에 회색 또는 희미하게 표시 되는 개체가 있는 경우에도 해당 요소는 s m a 구성에 포함 **되지 않습니다** .</span><span class="sxs-lookup"><span data-stu-id="74a6e-116">Also, if a graphic in this article has an object that's grayed-out or dimmed that means the element shown in gray **isn't** included in MA-specific configuration.</span></span>
  
## <a name="read-the-summary"></a><span data-ttu-id="74a6e-117">요약 읽기</span><span class="sxs-lookup"><span data-stu-id="74a6e-117">Read the summary</span></span>

<span data-ttu-id="74a6e-118">이 요약은 프로세스를 실행 하는 동안 손실 될 수 있는 단계로, 전체 검사 목록에서 프로세스를 진행 하는 위치를 추적 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-118">This summary breaks down the process into steps that might otherwise get lost during the execution, and is good for an overall checklist to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="74a6e-119">먼저 모든 필수 구성 요소를 충족 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-119">First, make sure you meet all the prerequisites.</span></span>

1. <span data-ttu-id="74a6e-120">비즈니스용 Skype 및 Exchange에 대 한 대부분의 **필수 구성 요소** 는 일반적인 것 이므로, [사전 필수 검사 목록에 대 한 개요 문서를 참조](hybrid-modern-auth-overview.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="74a6e-120">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="74a6e-121">이 문서에 나와 있는 단계를 시작 *하기 전에* 이 작업을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="74a6e-121">Do this  *before*  you begin any of the steps in this article.</span></span>

1. <span data-ttu-id="74a6e-122">파일 또는 OneNote에서 필요한 HMA 관련 정보를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-122">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>

1. <span data-ttu-id="74a6e-123">EXO에 대 한 최신 인증을 사용 하도록 설정 합니다 (아직 설정 되지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="74a6e-123">Turn ON Modern Authentication for EXO (if it isn't already turned on).</span></span>

1. <span data-ttu-id="74a6e-124">SFBO에 대 한 최신 인증을 설정 합니다 (아직 설정 되지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="74a6e-124">Turn ON Modern Authentication for SFBO (if it isn't already turned on).</span></span>

1. <span data-ttu-id="74a6e-125">Exchange 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-125">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>

1. <span data-ttu-id="74a6e-126">비즈니스용 Skype 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-126">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>

<span data-ttu-id="74a6e-127">이러한 단계는 SFB, SFBO, EXCH 및 EXCH에 대해 MA를 설정 하 고, SFB 및 SFBO의 HMA 구성에 참여할 수 있는 모든 제품 (EXCH/EXCH에 대 한 종속성 포함) 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-127">These steps turn on MA for SFB, SFBO, EXCH, and EXO - that is, all the products that can participate in an HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="74a6e-128">즉, 사용자에 게 하이브리드 (EXO + SFBO, EXO + SFB, EXO + SFBO 또는 EXO + SFB) 중 어떤 부분 에서도 만들어진 사서함이 있는 경우 완성 된 제품은 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-128">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![혼합 6 비즈니스용 Skype HMA 토폴로지의 경우 네 가지 가능한 위치 모두에서 MA가 설정 됩니다.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="74a6e-130">여기에서 볼 수 있듯이 MA를 켜는 네 가지 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-130">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="74a6e-131">최상의 사용자 환경을 위해서는 이러한 모든 위치에서 MA를 켜는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-131">For the best user experience, we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="74a6e-132">이러한 모든 위치에서 MA를 설정할 수 없는 경우 환경에 필요한 위치 에서만 MA를 설정 하도록 단계를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-132">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="74a6e-133">지원 되는 토폴로지의 [MA가 있는 비즈니스용 Skype에 대 한 지원 가능성 항목](https://technet.microsoft.com/library/mt803262.aspx) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="74a6e-133">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span>
  
 <span data-ttu-id="74a6e-134">**중요** 시작 하기 전에 모든 필수 구성 요소가 충족 되었는지 다시 한 번 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-134">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="74a6e-135">이 정보는 [여기](hybrid-modern-auth-overview.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-135">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="74a6e-136">필요한 모든 HMA 관련 정보 수집</span><span class="sxs-lookup"><span data-stu-id="74a6e-136">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="74a6e-137">최신 인증을 사용 하기 위한 [필수 구성 요소](hybrid-modern-auth-overview.md) (위의 참고 사항 참조)를 두 번 확인 한 후 앞 단계에서 HMA를 구성 하는 데 필요한 정보를 저장할 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-137">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="74a6e-138">이 문서에서 사용 되는 예:</span><span class="sxs-lookup"><span data-stu-id="74a6e-138">Examples used in this article:</span></span>
  
- <span data-ttu-id="74a6e-139">**SIP/SMTP 도메인**</span><span class="sxs-lookup"><span data-stu-id="74a6e-139">**SIP/SMTP domain**</span></span>

  - <span data-ttu-id="74a6e-140">Ex.</span><span class="sxs-lookup"><span data-stu-id="74a6e-140">Ex.</span></span> <span data-ttu-id="74a6e-141">contoso.com (Office 365에 페더레이션 됨)</span><span class="sxs-lookup"><span data-stu-id="74a6e-141">contoso.com (is federated with Office 365)</span></span>

- <span data-ttu-id="74a6e-142">**테 넌 트 ID**</span><span class="sxs-lookup"><span data-stu-id="74a6e-142">**Tenant ID**</span></span>

  - <span data-ttu-id="74a6e-143">Office 365 테 넌 트를 나타내는 GUID (contoso.onmicrosoft.com의 로그인)입니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-143">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>

- <span data-ttu-id="74a6e-144">**SFB 2015 CU5 웹 서비스 Url**</span><span class="sxs-lookup"><span data-stu-id="74a6e-144">**SFB 2015 CU5 Web Service URLs**</span></span>

<span data-ttu-id="74a6e-145">배포 된 모든 SfB 2015 풀에 대 한 내부 및 외부 웹 서비스 Url이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-145">you'll need internal and external web service URLs for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="74a6e-146">이러한 사항을 가져오려면 비즈니스용 Skype 관리 셸에서 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-146">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="74a6e-147">Ex.</span><span class="sxs-lookup"><span data-stu-id="74a6e-147">Ex.</span></span> <span data-ttu-id="74a6e-148">내https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="74a6e-148">Internal: https://lyncwebint01.contoso.com</span></span>

- <span data-ttu-id="74a6e-149">Ex.</span><span class="sxs-lookup"><span data-stu-id="74a6e-149">Ex.</span></span> <span data-ttu-id="74a6e-150">외부로https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="74a6e-150">External: https://lyncwebext01.contoso.com</span></span>

<span data-ttu-id="74a6e-151">Standard Edition 서버를 사용 하는 경우 내부 URL은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-151">If you're using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="74a6e-152">이 경우 내부 URL에 대 한 풀 fqdn을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-152">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="74a6e-153">EXO에 대 한 최신 인증 설정</span><span class="sxs-lookup"><span data-stu-id="74a6e-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="74a6e-154">[Exchange Online: 최신 인증용으로 테 넌 트를 사용 하도록 설정 하는 방법에 대 한](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx) 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="74a6e-155">SFBO에 대 한 최신 인증 설정</span><span class="sxs-lookup"><span data-stu-id="74a6e-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="74a6e-156">[비즈니스용 Skype Online: 최신 인증용으로 테 넌 트를 사용 하도록 설정](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="74a6e-157">Exchange 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="74a6e-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="74a6e-158">여기서 설명 하는 지침에 따라 [하이브리드 최신 인증을 사용 하도록 Exchange Server 온-프레미스를 구성 하는 방법을 설명](configure-exchange-server-for-hybrid-modern-authentication.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="74a6e-159">비즈니스용 Skype 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="74a6e-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a><span data-ttu-id="74a6e-160">Azure Active Directory에서 온-프레미스 웹 서비스 Url을 Spn으로 추가</span><span class="sxs-lookup"><span data-stu-id="74a6e-160">Add on-premises web service URLs as SPNs in Azure Active Directory</span></span>

<span data-ttu-id="74a6e-161">이제 SFBO에서 서비스 주체로 이전에 수집한 Url을 추가 하기 위한 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="74a6e-162">**참고 사항** Spn (서비스 사용자 이름)은 웹 서비스를 식별 하 고이를 보안 주체 (예: 계정 이름 또는 그룹)와 연결 하 여 인증 된 사용자를 대신 하 여 서비스를 수행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-162">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="74a6e-163">서버에 인증 하는 클라이언트는 Spn에 포함 된 정보를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-163">Clients authenticating to a server make use of information that's contained in SPNs.</span></span>
  
1. <span data-ttu-id="74a6e-164">먼저 [다음 지침](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)을 사용 하 여 Azure Active Directory (azure AD)에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-164">First, connect to Azure Active Directory (Azure AD) with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>

2. <span data-ttu-id="74a6e-165">온-프레미스에서이 명령을 실행 하 여 SFB 웹 서비스 Url의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="74a6e-166">AppPrincipalId는로 시작 `00000004` 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-166">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="74a6e-167">이는 비즈니스용 Skype Online에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-167">This corresponds to Skype for Business Online.</span></span>

   <span data-ttu-id="74a6e-168">메모 작성 및 현재 상태 URL을 포함 하는이 명령의 출력이 며, 대부분은로 시작 하는 Spn으로 구성 됩니다 `00000004-0000-0ff1-ce00-000000000000/` .</span><span class="sxs-lookup"><span data-stu-id="74a6e-168">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. <span data-ttu-id="74a6e-169">예를 들어 온-프레미스의 내부 **또는** 외부 SFB url이 없는 경우에는 https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) 이 목록에 특정 레코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-169">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span>

    <span data-ttu-id="74a6e-170">아래의 *예제 url* 을 추가 명령에 있는 실제 url로 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-170">Be sure to replace  *the example URLs* below with your actual URLs in the Add commands!</span></span>
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="74a6e-171">2 단계에서 **(new-msolserviceprincipal** 명령을 다시 실행 하 고 출력을 검토 하 여 새 레코드가 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-171">Verify your new records were added by running the **Get-MsolServicePrincipal** command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="74a6e-172">목록 또는 스크린샷을 새 Spn 목록 앞에 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-172">Compare the list or screenshot from before to the new list of SPNs.</span></span> <span data-ttu-id="74a6e-173">레코드에 대 한 새 목록을 스크린샷 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-173">You might also screenshot the new list for your records.</span></span> <span data-ttu-id="74a6e-174">성공적으로 완료 되 면 목록에 두 개의 새 Url이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-174">If you were successful, you'll see the two new URLs in the list.</span></span> <span data-ttu-id="74a6e-175">예를 들어, Spn 목록에는 이제 특정 Url과가 포함 됩니다 https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com/ .</span><span class="sxs-lookup"><span data-stu-id="74a6e-175">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>

### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="74a6e-176">EvoSTS 인증 서버 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="74a6e-176">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="74a6e-177">비즈니스용 Skype 관리 셸에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-177">Run the following command in the Skype for Business Management Shell.</span></span>
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="74a6e-178">하이브리드 최신 인증 사용</span><span class="sxs-lookup"><span data-stu-id="74a6e-178">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="74a6e-179">실제로 MA를 설정 하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-179">This is the step that actually turns on MA.</span></span> <span data-ttu-id="74a6e-180">클라이언트 인증 흐름을 변경 하지 않고 앞의 모든 단계를 미리 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-180">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="74a6e-181">인증 흐름을 변경할 준비가 되 면 비즈니스용 Skype 관리 셸에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-181">When you're ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a><span data-ttu-id="74a6e-182">지</span><span class="sxs-lookup"><span data-stu-id="74a6e-182">Verify</span></span>

<span data-ttu-id="74a6e-183">HMA를 사용 하도록 설정 하면 클라이언트의 다음 로그인은 새 인증 흐름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-183">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="74a6e-184">HMA를 설정 하면 모든 클라이언트에 대 한 재인증이 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-184">Note that just turning on HMA won't trigger a reauthentication for any client.</span></span> <span data-ttu-id="74a6e-185">클라이언트는 인증 토큰 및/또는 인증서의 수명에 따라 다시 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-185">The clients reauthenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="74a6e-186">해당 HMA가 사용 하도록 설정한 후에 작동 하는지 테스트 하려면 테스트 SFB Windows 클라이언트에서 로그 아웃 하 고 ' 내 자격 증명 삭제 '를 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-186">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="74a6e-187">다시 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-187">Sign in again.</span></span> <span data-ttu-id="74a6e-188">이제 클라이언트에서 최신 인증 흐름을 사용 하 고 있으며, 클라이언트가 서버에 연결 하 여 로그인 하기 바로 전에 확인 된 ' 회사 또는 학교 ' 계정에 대 한 **Office 365** 프롬프트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-188">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span>
  
<span data-ttu-id="74a6e-189">' OAuth 기관 '에 대 한 비즈니스용 Skype 클라이언트의 ' 구성 정보 '도 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-189">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="74a6e-190">클라이언트 컴퓨터에서이 작업을 수행 하려면 CTRL 키를 누른 상태에서 Windows 알림 트레이에서 비즈니스용 Skype 아이콘을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-190">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="74a6e-191">나타나는 메뉴에서 **구성 정보** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-191">Click **Configuration Information** in the menu that appears.</span></span> <span data-ttu-id="74a6e-192">바탕 화면에 표시 되는 ' 비즈니스용 Skype 구성 정보 ' 창에서 다음을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-192">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![최신 인증을 사용 하는 비즈니스용 Skype 클라이언트의 구성 정보에는의 Lync 및 EWS OAUTH 인증 기관 URL이 표시 https://login.windows.net/common/oauth2/authorize 됩니다.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="74a6e-194">또한 CTRL 키를 누른 상태로 Outlook 클라이언트 (Windows 알림 트레이)에 대 한 아이콘을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 상태 '를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-194">You should also hold down the CTRL key at the same time you right-click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="74a6e-195">\*OAuth에서 사용 되는 전달자 토큰을 나타내는 ' 전달자 ' 유형의 인증 유형에 대해 클라이언트의 SMTP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-195">Look for the client's SMTP address against an AuthN type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="74a6e-196">관련 문서</span><span class="sxs-lookup"><span data-stu-id="74a6e-196">Related articles</span></span>

<span data-ttu-id="74a6e-197">[최신 인증 개요에 다시 연결](hybrid-modern-auth-overview.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-197">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md).</span></span>
  
<span data-ttu-id="74a6e-198">비즈니스용 Skype 클라이언트에 대해 ADAL (최신 인증)을 사용 하는 방법을 알고 있어야 하나요?</span><span class="sxs-lookup"><span data-stu-id="74a6e-198">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="74a6e-199">[여기](https://technet.microsoft.com/library/mt710548.aspx)에는 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a6e-199">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
