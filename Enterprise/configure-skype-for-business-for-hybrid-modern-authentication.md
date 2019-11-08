---
title: 하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: 최신 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법으로, 비즈니스용 skype 서버 온-프레미스 및 Exchange server 온-프레미스에서 사용 가능 하 고, 하이브리드의 wmi for Business 비즈니스를 사용할 수 있습니다.
ms.openlocfilehash: 17079ab5e47e2e739780d3df4a9a523edccda14f
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029132"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="7e265-103">하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="7e265-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="7e265-104">최신 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법으로, 비즈니스용 skype 서버 온-프레미스 및 Exchange server 온-프레미스에서 사용 가능 하 고, 하이브리드의 wmi for Business 비즈니스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="7e265-105">**중요** 최신 인증 (MA)에 대 한 자세한 내용과 회사나 조직에서이를 사용 하는 데 도움이 될 수 있는 이유를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="7e265-105">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="7e265-106">[이 문서](hybrid-modern-auth-overview.md) 에서 개요를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-106">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="7e265-107">MA에서 어떤 비즈니스용 Skype 토폴로지가 지원 되는지 파악 해야 하는 경우 여기에서 문서화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-107">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="7e265-108">**시작 하기 전에**다음을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="7e265-109">최신 인증 \> MA</span><span class="sxs-lookup"><span data-stu-id="7e265-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="7e265-110">하이브리드 최신 인증 \> HMA</span><span class="sxs-lookup"><span data-stu-id="7e265-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="7e265-111">Exchange 온-프레미스 \> exch</span><span class="sxs-lookup"><span data-stu-id="7e265-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="7e265-112">Exchange Online \> exo</span><span class="sxs-lookup"><span data-stu-id="7e265-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="7e265-113">비즈니스용 Skype 온-프레미스 \> SFB</span><span class="sxs-lookup"><span data-stu-id="7e265-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="7e265-114">및 비즈니스용 Skype Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="7e265-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="7e265-115">또한이 문서의 그래픽에 ' 흐리게 ' 또는 ' 희미하게 ' 개체를 사용 하는 경우에는 회색으로 표시 된 요소가 MA 한정 구성에 포함 되어 **있지** 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="7e265-116">요약 읽기</span><span class="sxs-lookup"><span data-stu-id="7e265-116">Read the summary</span></span>

<span data-ttu-id="7e265-117">이 요약은 프로세스를 실행 하는 동안 손실 될 수 있는 단계에 boils 프로세스를 진행 하는 위치를 추적 하기 위해 전체 검사를 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="7e265-118">먼저 모든 필수 구성 요소를 충족 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="7e265-119">비즈니스용 Skype 및 Exchange에 대 한 대부분의 **필수 구성 요소** 는 일반적인 것 이므로, [사전 필수 검사 목록에 대 한 개요 문서를 참조](hybrid-modern-auth-overview.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="7e265-119">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="7e265-120">이 문서에 나와 있는 단계를 시작 *하기 전에* 이 작업을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7e265-120">Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="7e265-121">파일 또는 OneNote에서 필요한 HMA 관련 정보를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="7e265-122">EXO에 대 한 최신 인증을 사용 하도록 설정 합니다 (아직 설정 되지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="7e265-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="7e265-123">SFBO에 대 한 최신 인증을 사용 하도록 설정 합니다 (아직 설정 되지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="7e265-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="7e265-124">Exchange 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="7e265-125">비즈니스용 Skype 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="7e265-126">참고 이러한 단계는 SFB, SFBO, EXCH 및 EXCH에 대해 MA를 설정 하며, 즉 SFB 및 SFBO의 HMA 구성에 참여할 수 있는 모든 제품 (EXCH/EXCH에 대 한 종속성 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-126">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="7e265-127">즉, 사용자에 게 하이브리드 (EXO + SFBO, EXO + SFB, EXO + SFBO 또는 EXO + SFB) 중 어떤 부분 에서도 만들어진 사서함이 있는 경우 완성 된 제품은 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-127">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![혼합 6 비즈니스용 Skype HMA 토폴로지의 경우 네 가지 가능한 위치 모두에서 MA가 설정 됩니다.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="7e265-129">여기에서 볼 수 있듯이 MA를 켜는 네 가지 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-129">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="7e265-130">최상의 사용자 환경에서는 이러한 네 가지 위치 모두에 MA를 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-130">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="7e265-131">이러한 모든 위치에서 MA를 설정할 수 없는 경우 환경에 필요한 위치 에서만 MA를 설정 하도록 단계를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-131">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="7e265-132">지원 되는 토폴로지의 [MA가 있는 비즈니스용 Skype에 대 한 지원 가능성 항목](https://technet.microsoft.com/library/mt803262.aspx) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7e265-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="7e265-133">**중요** 시작 하기 전에 모든 필수 구성 요소가 충족 되었는지 다시 한 번 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-133">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="7e265-134">이 정보는 [여기](hybrid-modern-auth-overview.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-134">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="7e265-135">필요한 모든 HMA 관련 정보 수집</span><span class="sxs-lookup"><span data-stu-id="7e265-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="7e265-136">최신 인증을 사용 하기 위한 [필수 구성 요소](hybrid-modern-auth-overview.md) (위의 참고 사항 참조)를 두 번 확인 한 후 앞 단계에서 HMA를 구성 하는 데 필요한 정보를 저장할 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-136">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="7e265-137">이 문서에서 사용 되는 예:</span><span class="sxs-lookup"><span data-stu-id="7e265-137">Examples used in this article:</span></span> 
  
- <span data-ttu-id="7e265-138">**SIP/SMTP 도메인**</span><span class="sxs-lookup"><span data-stu-id="7e265-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="7e265-139">Ex.</span><span class="sxs-lookup"><span data-stu-id="7e265-139">Ex.</span></span> <span data-ttu-id="7e265-140">contoso.com (Office 365에 페더레이션 됨)</span><span class="sxs-lookup"><span data-stu-id="7e265-140">contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="7e265-141">**테 넌 트 ID**</span><span class="sxs-lookup"><span data-stu-id="7e265-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="7e265-142">Office 365 테 넌 트를 나타내는 GUID (contoso.onmicrosoft.com의 로그인)입니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="7e265-143">**SFB 2015 CU5 웹 서비스 Url**</span><span class="sxs-lookup"><span data-stu-id="7e265-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="7e265-144">모든 SfB 2015 풀에 배포 된 내부 및 외부 웹 서비스 URL이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-144">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="7e265-145">이러한 사항을 가져오려면 비즈니스용 Skype 관리 셸에서 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-145">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="7e265-146">Ex.</span><span class="sxs-lookup"><span data-stu-id="7e265-146">Ex.</span></span> <span data-ttu-id="7e265-147">내https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="7e265-147">Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="7e265-148">Ex.</span><span class="sxs-lookup"><span data-stu-id="7e265-148">Ex.</span></span> <span data-ttu-id="7e265-149">외부로https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="7e265-149">External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="7e265-150">Standard Edition 서버를 사용 하는 경우 내부 URL은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-150">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="7e265-151">이 경우 내부 URL에 대 한 풀 fqdn을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-151">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="7e265-152">EXO에 대 한 최신 인증 설정</span><span class="sxs-lookup"><span data-stu-id="7e265-152">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="7e265-153">[Exchange Online: 최신 인증용으로 테 넌 트를 사용 하도록 설정 하는 방법에 대 한](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx) 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-153">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="7e265-154">SFBO에 대 한 최신 인증 설정</span><span class="sxs-lookup"><span data-stu-id="7e265-154">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="7e265-155">[비즈니스용 Skype Online: 최신 인증용으로 테 넌 트를 사용 하도록 설정](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-155">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="7e265-156">Exchange 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7e265-156">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="7e265-157">여기서 설명 하는 지침에 따라 [하이브리드 최신 인증을 사용 하도록 Exchange Server 온-프레미스를 구성 하는 방법을 설명](configure-exchange-server-for-hybrid-modern-authentication.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-157">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="7e265-158">비즈니스용 Skype 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7e265-158">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="7e265-159">Azure AD에서 온-프레미스 웹 서비스 Url을 Spn으로 추가</span><span class="sxs-lookup"><span data-stu-id="7e265-159">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="7e265-160">이제 SFBO에서 서비스 주체로 이전에 수집한 Url을 추가 하기 위한 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-160">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="7e265-161">**참고 사항** Spn (서비스 사용자 이름)은 웹 서비스를 식별 하 고이를 보안 주체 (예: 계정 이름 또는 그룹)와 연결 하 여 인증 된 사용자를 대신 하 여 서비스를 수행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-161">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="7e265-162">서버에 인증 하는 클라이언트는 Spn에 포함 된 정보를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-162">Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="7e265-163">먼저 [다음 지침](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)을 사용 하 여 AAD에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-163">First, connect to AAD with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>
    
2. <span data-ttu-id="7e265-164">온-프레미스에서이 명령을 실행 하 여 SFB 웹 서비스 Url의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-164">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="7e265-165">AppPrincipalId는로 `00000004`시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-165">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="7e265-166">이는 비즈니스용 Skype Online에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-166">This corresponds to Skype for Business Online.</span></span>
    
   <span data-ttu-id="7e265-167">메모 작성 및 현재 상태 URL을 포함 하는이 명령의 출력이 며, 대부분은로 `00000004-0000-0ff1-ce00-000000000000/`시작 하는 spn으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-167">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. <span data-ttu-id="7e265-168">https://lyncwebint01.contoso.com 예 https://lyncwebext01.contoso.com) 를 들어 온-프레미스의 내부 **또는** 외부 SFB url이 없는 경우에는이 목록에 특정 레코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-168">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="7e265-169">아래의 *예제 url* 을 추가 명령에 있는 실제 url로 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-169">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="7e265-170">2 단계에서 (New-msolserviceprincipal 명령을 다시 실행 하 고 출력을 검토 하 여 새 레코드가 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-170">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="7e265-171">목록/스크린샷에서 새 Spn 목록을 비교 합니다 (레코드의 새 목록을 스크린샷 할 수도 있음).</span><span class="sxs-lookup"><span data-stu-id="7e265-171">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="7e265-172">성공적으로 완료 되 면 목록에 두 개의 새 Url이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-172">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="7e265-173">예를 들어, Spn 목록에는 이제 특정 Url https://lyncwebint01.contoso.com 과 https://lyncwebext01.contoso.com/가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-173">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="7e265-174">EvoSTS 인증 서버 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="7e265-174">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="7e265-175">비즈니스용 Skype 관리 셸에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-175">Run the following command in the Skype for Business Management Shell.</span></span>
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="7e265-176">하이브리드 최신 인증 사용</span><span class="sxs-lookup"><span data-stu-id="7e265-176">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="7e265-177">실제로 MA를 설정 하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-177">This is the step that actually turns MA on.</span></span> <span data-ttu-id="7e265-178">클라이언트 인증 흐름을 변경 하지 않고 앞의 모든 단계를 미리 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-178">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="7e265-179">인증 흐름을 변경할 준비가 되 면 비즈니스용 Skype 관리 셸에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-179">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a><span data-ttu-id="7e265-180">지</span><span class="sxs-lookup"><span data-stu-id="7e265-180">Verify</span></span>

<span data-ttu-id="7e265-181">HMA를 사용 하도록 설정 하면 클라이언트의 다음 로그인은 새 인증 흐름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-181">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="7e265-182">HMA를 설정 하는 것 만으로도 클라이언트에 대 한 재인증이 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-182">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="7e265-183">클라이언트는 인증 토큰 및/또는 인증서의 수명에 따라 다시 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-183">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="7e265-184">해당 HMA가 사용 하도록 설정한 후에 작동 하는지 테스트 하려면 테스트 SFB Windows 클라이언트에서 로그 아웃 하 고 ' 내 자격 증명 삭제 '를 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-184">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="7e265-185">다시 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-185">Sign in again.</span></span> <span data-ttu-id="7e265-186">이제 클라이언트에서 최신 인증 흐름을 사용 하 고 있으며, 클라이언트가 서버에 연결 하 여 로그인 하기 바로 전에 확인 된 ' 회사 또는 학교 ' 계정에 대 한 **Office 365** 프롬프트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-186">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="7e265-187">' OAuth 기관 '에 대 한 비즈니스용 Skype 클라이언트의 ' 구성 정보 '도 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-187">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="7e265-188">클라이언트 컴퓨터에서이 작업을 수행 하려면 CTRL 키를 누른 상태에서 Windows 알림 트레이에서 비즈니스용 Skype 아이콘을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-188">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="7e265-189">나타나는 메뉴에서 구성 정보를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-189">Click Configuration Information in the menu that appears.</span></span> <span data-ttu-id="7e265-190">바탕 화면에 표시 되는 ' 비즈니스용 Skype 구성 정보 ' 창에서 다음을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-190">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![최신 인증을 사용 하는 비즈니스용 Skype 클라이언트의 구성 정보에는의 https://login.windows.net/common/oauth2/authorizeLYNC 및 EWS OAUTH 인증 기관 URL이 표시 됩니다.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="7e265-192">또한 CTRL 키를 누른 상태로 Outlook 클라이언트 아이콘 (Windows 알림 트레이)을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 상태 '를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-192">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="7e265-193">OAuth에서 사용 되는 전달자 토큰을 나타내는 ' 전달자\*' 유형의 인증 유형에 대해 클라이언트의 SMTP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-193">Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="7e265-194">관련 문서</span><span class="sxs-lookup"><span data-stu-id="7e265-194">Related articles</span></span>

<span data-ttu-id="7e265-195">[최신 인증 개요에 다시 연결](hybrid-modern-auth-overview.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-195">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="7e265-196">비즈니스용 Skype 클라이언트에 대해 ADAL (최신 인증)을 사용 하는 방법을 알고 있어야 하나요?</span><span class="sxs-lookup"><span data-stu-id="7e265-196">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="7e265-197">[여기](https://technet.microsoft.com/library/mt710548.aspx)에는 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-197">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="7e265-198">SFB 없이 실행 되는 Exchange Server 온-프레미스에 대해 이러한 단계를 읽어 보 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="7e265-198">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB?</span></span> <span data-ttu-id="7e265-199">이러한 단계는 여기에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e265-199">Those steps are available here.</span></span>
  

