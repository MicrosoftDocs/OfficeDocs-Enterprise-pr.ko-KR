---
title: 하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: 현대 인증을 사용 하면 보다 안전한 사용자 인증 및 권한 부여 제공, 비즈니스 서버 온-프레미스 및 Exchange server 온-프레미스,으로 비즈니스 하이브리드에 대 한 분할 도메인 Skype 용 Skype에 사용할 수 있는 id 관리의 방법이 있습니다.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542259"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="b136d-103">하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="b136d-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="b136d-104">현대 인증을 사용 하면 보다 안전한 사용자 인증 및 권한 부여 제공, 비즈니스 서버 온-프레미스 및 Exchange server 온-프레미스,으로 비즈니스 하이브리드에 대 한 분할 도메인 Skype 용 Skype에 사용할 수 있는 id 관리의 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="b136d-p101">**중요 한** 현대 인증 (MA) 및 이유 하려고 할 때 회사 또는 조직에서 사용 하는 방법에 대 한 상세 하 시겠습니까? [이 문서](hybrid-modern-auth-overview.md) 에 대 한 개요를 확인 합니다. 여기서 설명 하는 MA와 비즈니스 토폴로지가 지원 됩니다에 대 한 어떤 Skype 알아두어야 할 하는 경우!</span><span class="sxs-lookup"><span data-stu-id="b136d-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="b136d-108">**시작 하기에 앞서**, I 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="b136d-109">현대 인증 \> MA</span><span class="sxs-lookup"><span data-stu-id="b136d-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="b136d-110">하이브리드 현대 인증 \> HMA</span><span class="sxs-lookup"><span data-stu-id="b136d-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="b136d-111">온-프레미스 exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="b136d-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="b136d-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="b136d-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="b136d-113">비즈니스 온-프레미스 용 Skype \> SFB</span><span class="sxs-lookup"><span data-stu-id="b136d-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="b136d-114">및 온라인 비즈니스에 대 한 Skype \> SFBO</span><span class="sxs-lookup"><span data-stu-id="b136d-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="b136d-115">또한, \*이 문서에 그래픽에 회색 **없는** 에 포함 되어 MA 관련 구성에 표시 된 요소를 의미 하는 ' 흐리게 표시 ' 또는 '흐리게 표시' 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="b136d-116">요약 읽기</span><span class="sxs-lookup"><span data-stu-id="b136d-116">Read the summary</span></span>

<span data-ttu-id="b136d-117">이 요약 실행 하는 동안 손실 그렇지 않은 경우 얻을 수 이며 프로세스에서의 현재 위치에 대 한 추적을 유지 하려면 전체 검사 목록에 대 한 좋은 단계에는 프로세스를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="b136d-118">먼저 모든 필수 구성 요소를 충족 하는지 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b136d-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="b136d-p102">많은 **필수 구성 요소** 이후 비즈니스 및 [p r e 필수 검사 목록에 대 한 개요 (영문) 문서를 참조](hybrid-modern-auth-overview.md)Exchange에 대 한 두 Skype에 대 한 일반적인 됩니다. 이 수행 *하기 전에* 이 문서의 단계 중 하나를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="b136d-121">파일 또는 OneNote에서 수행 해야 HMA 관련 정보를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="b136d-122">Turn ON 현대에 대 한 인증 EXO (아직 설정 되지 않은) 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="b136d-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="b136d-123">Turn ON 현대에 대 한 인증 SFBO (아직 설정 되지 않은) 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="b136d-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="b136d-124">Exchange 온-프레미스에 대 한 하이브리드 현대 인증을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="b136d-125">비즈니스 온-프레미스 용 Skype에 대 한 하이브리드 현대 인증을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="b136d-p103">다음이 단계를 켭니다 MA SFB, SFBO, EXCH, 및 EXO-즉, SFB 및 SFBO (EXCH/EXO에 대 한 종속성 포함)의 HMA 구성에 참여할 수 있는 모든 제품 note 합니다. 즉, 사용자가 홈으로 / 사서함 하이브리드 (EXO + SFBO, EXO + SFB, EXCH + SFBO, 또는 EXCH + SFB)의 모든 부분에서 만든, 하는 경우 완성 된 제품에는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![비즈니스 HMA 토폴로지에 대 한 혼합 6 Skype에 MA 모든 네가지 가능한 위치에 있습니다.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="b136d-p104">MA를 설정 하는 4 개의 서로 다른 곳을 볼 수 있듯이! 최상의 사용자 환경에 대 한 이러한 위치의 모든 4에 MA에서 설정 하는 것이 좋습니다. 이러한 모든 위치에서 MA을 켤 수 없는, 환경에 대해 필요한 수 있는 위치에만 MA 켤 수 있도록 하는 단계를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="b136d-132">지원 되는 토폴로지 [MA와 비즈니스를 위한 Skype에 대 한 지원 가능성 항목](https://technet.microsoft.com/en-us/library/mt803262.aspx) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b136d-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="b136d-p105">**중요 한** 시작 하기 전에 모든 필수 구성 요소를 충족 했을 때 있는지 다시 확인 합니다. 해당 정보를 찾을 수 [여기](hybrid-modern-auth-overview.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="b136d-135">필요한 모든 HMA 관련 정보를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="b136d-p106">현대 인증을 사용 하 여 [필수 구성 요소](hybrid-modern-auth-overview.md) 를 충족 하는 이중 확인 한 후 (참고 참조 위)를 진행 하는 단계에서 HMA를 구성 해야 정보를 저장할 파일을 만들어야 합니다. 이 문서에 사용 된 예:</span><span class="sxs-lookup"><span data-stu-id="b136d-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="b136d-138">**SIP/SMTP 도메인**</span><span class="sxs-lookup"><span data-stu-id="b136d-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="b136d-p107">예: contoso.com (Office 365와 페더레이션 되어있는지)</span><span class="sxs-lookup"><span data-stu-id="b136d-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="b136d-141">**테 넌 트 ID**</span><span class="sxs-lookup"><span data-stu-id="b136d-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="b136d-142">(Contoso.onmicrosoft.com 형식의 로그인) 할 때 Office 365 테 넌 트를 나타내는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="b136d-143">**SFB 2015 c u 5 웹 서비스 Url**</span><span class="sxs-lookup"><span data-stu-id="b136d-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="b136d-p108">배포 된 모든 SfB 2015 풀에 대 한 내부 및 외부 웹 서비스 URL을 할 수 있습니다. 이러한를 얻으려면 비즈니스 관리 셸의 Skype에서 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="b136d-146">Get-csservice WebServer | Select-object PoolFqdn, InternalFqdn, 외부 | FL</span><span class="sxs-lookup"><span data-stu-id="b136d-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="b136d-p109">예: 내부:https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b136d-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="b136d-p110">예: 외부:https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b136d-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="b136d-p111">Standard Edition 서버를 사용 하는 경우에 내부 URL 비게 됩니다. 이 경우 풀 fqdn을 사용 하 여 내부 URL에 대 한.</span><span class="sxs-lookup"><span data-stu-id="b136d-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="b136d-153">EXO에 대 한 최신 인증 설정</span><span class="sxs-lookup"><span data-stu-id="b136d-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="b136d-154">이 문서의 지침에 따라: [Exchange Online: 현대 인증에 대 한 테 넌 트를 설정 하는 방법.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="b136d-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="b136d-155">SFBO에 대 한 최신 인증 설정</span><span class="sxs-lookup"><span data-stu-id="b136d-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="b136d-156">이 문서의 지침에 따라: [비즈니스 온라인 용 Skype: 현대 인증에 대 한 테 넌 트를 사용 하도록 설정](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="b136d-157">Exchange 온-프레미스에 대 한 하이브리드 현대 인증 설정</span><span class="sxs-lookup"><span data-stu-id="b136d-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="b136d-158">이 문서의 지침에 따라: [Exchange Server 온-프레미스 하이브리드 현대 인증을 사용 하도록 구성 하는 방법](configure-exchange-server-for-hybrid-modern-authentication.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="b136d-159">비즈니스 온-프레미스 용 Skype에 대 한 하이브리드 현대 인증을 설정</span><span class="sxs-lookup"><span data-stu-id="b136d-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="b136d-160">온-프레미스 Azure AD에 Spn으로 서비스 Url을 웹 추가</span><span class="sxs-lookup"><span data-stu-id="b136d-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="b136d-161">이제 SFBO에서 서비스 계정으로 (수집 된 이전) Url을 추가 하려면 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="b136d-p112">**참고 사항** 서비스 사용자 이름 (Spn) 웹 서비스를 식별 하 고 서비스 권한이 부여 된 사용자를 대신 하 여에 작업을 수행할 수 있도록 (예: 계정 이름 또는 그룹) 보안 주체를 연결 합니다. 서버를 인증 하는 클라이언트에 포함된 된 Spn 정보 사용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="b136d-164">먼저, [이러한 지침](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0)과 함께 AAD에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="b136d-165">이 명령을 실행, 온-프레미스, SFB 웹 서비스 Url의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="b136d-166">Get-MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | -ExpandProperty ServicePrincipalNames를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="b136d-p113">AppPrincipalId '00000004'로 시작 하 고 지 합니다. 이 비즈니스 Online 용 Skype에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="b136d-169">됩니다 SE 및 WS URL를 포함 하지만 대개 00000004-0000-0ff1-ce00-000000000000로 시작 하는 Spn을 구성 하는이 명령의 출력을 메모해 두십시오 (및 나중에 비교에 대 한 스크린샷)를 수행 / 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="b136d-170">내부 **또는** 외부 온-프레미스에서 SFB Url 누락 된 경우 (예를들어 https://lyncwebint01.contoso.com 및 https://lyncwebext01.contoso.com) 이 목록에 해당 특정 레코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="b136d-171">아래 *예제에서는 Url* 추가 명령에 실제 Url 바꿉니다 해야!</span><span class="sxs-lookup"><span data-stu-id="b136d-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="b136d-172">$x get MsolServicePrincipal =-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="b136d-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="b136d-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="b136d-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="b136d-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="b136d-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="b136d-175">집합 MSOLServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000-ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="b136d-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="b136d-p114">마찬가지로 2 단계에서 Get MsolServicePrincipal 명령을 실행 하 고 출력을 통해을 찾고 추가 된 새 레코드를 확인 합니다. 목록 비교 / Spn (수도 있습니다 스크린샷 새 목록에 레코드에 대 한)의 새 목록에 앞에서 스크린샷. 성공한, 두 새 Url 목록에 표시 됩니다. 이 예제에서 이동, Spn 목록이 이제 포함 됩니다 특정 Url https://lyncweb01.contoso.com 및 https://autodiscover.contoso.com합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="b136d-180">EvoSTS 인증 서버 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="b136d-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="b136d-181">비즈니스 관리 셸의 Skype 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="b136d-182">New-csoauthserver-Identity evoSTS-MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true-유형 AzureAD</span><span class="sxs-lookup"><span data-stu-id="b136d-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="b136d-183">하이브리드 현대 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="b136d-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="b136d-p115">실제로 MA를 설정 하는 단계입니다. 클라이언트 인증 흐름을 변경 하지 않고 시간 보다 먼저 모든 이전 단계를 실행할 수 있습니다. 인증 흐름을 변경 하려면 준비가 되 면 비즈니스 관리 셸의 Skype에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="b136d-187">Set-csoauthconfiguration-ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="b136d-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="b136d-188">확인</span><span class="sxs-lookup"><span data-stu-id="b136d-188">Verify</span></span>

<span data-ttu-id="b136d-p116">HMA를 사용 하도록 설정 되 면 클라이언트의 다음 로그인 하는 새 인증 흐름을 사용 합니다. 참고 방금 HMA를 켜서는 다시 인증 하는 모든 클라이언트에 대 한 트리거하지 않습니다. 클라이언트를 다시 인증에 따라 인증 토큰 및/또는 인증서의 수명 동안 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="b136d-p117">활성화 한 후 HMA 제대로 작동 하는지 테스트, 테스트 SFB Windows 클라이언트에서 로그 아웃 하 고 '내 자격 증명 삭제'를 클릭 해야 합니다. 다시 로그인 합니다. 클라이언트 이제 현대 인증 흐름 사용 하 고 사용자의 로그인을 '회사 또는 학교'에 대 한 **Office 365** 프롬프트를 지금 포함 됩니다 계정, 배치 하기 바로 전에 클라이언트는 서버에 연결 하 고 로그인을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="b136d-p118">도 확인 해야 ' 구성 정보 ' Skype에 대 한 비즈니스 클라이언트에 대 한 ' OAuth 기관 '에 대 한. 이 작업을 수행 하 여 클라이언트 컴퓨터에서 비즈니스 아이콘은 Skype 마우스 오른쪽 단추로 Windows 알림 표시줄에 동시에 CTRL 키를 유지 합니다. 표시 되는 메뉴에서 구성 정보를 클릭 합니다. 바탕 화면에 표시 되는 'Skype 비즈니스 구성 정보에 대 한' 창에서 다음 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Lync 및 OAUTH 인증 기관 EWS의 현대 인증을 사용 하 여 비즈니스 클라이언트에 대 한 Skype의 구성 정보를 표시 https://login.windows.net/common/oauth2/authorize합니다.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="b136d-p119">또한 Outlook 클라이언트 (도: Windows 알림 트레이)에 대 한 아이콘 마우스 오른쪽 단추로 클릭 하는 동시에 CTRL 키를 누른 하 고 ' 연결 상태 '를 클릭 해야 합니다. Authn 유형의 대해 클라이언트의 SMTP 주소를 찾습니다 ' Bearer\*'를 사용 하 여 OAuth bearer 토큰을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="b136d-202">관련된 문서</span><span class="sxs-lookup"><span data-stu-id="b136d-202">Related articles</span></span>

<span data-ttu-id="b136d-203">[현대 인증 개요에 다시 연결](hybrid-modern-auth-overview.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="b136d-p120">비즈니스 클라이언트에 대 한 프로그램 Skype에 대 한 최신 인증 (ADAL)를 사용 하는 방법을 알고 해야 합니까? 단계 되어 있는데 [여기](https://technet.microsoft.com/en-us/library/mt710548.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="b136d-p121">Exchange 서버에 대해 표시 되는 대로 다음이 단계를 읽고 하 시겠습니까, 온-프레미스, SFB 없이 실행 하 시겠습니까? 이러한 단계는 여기에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b136d-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

