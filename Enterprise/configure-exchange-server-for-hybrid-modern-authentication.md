---
title: 하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: 하이브리드 최신 인증 (HMA)은 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.
ms.openlocfilehash: 98a47f9527b3922767bfd8240790d7cfdeb14936
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068044"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="099d0-103">하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="099d0-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="099d0-104">하이브리드 최신 인증 (HMA)은 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="099d0-105">선택적</span><span class="sxs-lookup"><span data-stu-id="099d0-105">FYI</span></span>

<span data-ttu-id="099d0-106">시작 하기 전에 다음을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="099d0-107">하이브리드 최신 인증 \> HMA</span><span class="sxs-lookup"><span data-stu-id="099d0-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="099d0-108">Exchange 온-프레미스 \> exch</span><span class="sxs-lookup"><span data-stu-id="099d0-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="099d0-109">Exchange Online \> exo</span><span class="sxs-lookup"><span data-stu-id="099d0-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="099d0-110">또한 *이 문서의 그래픽에 ' 흐리게 ' 또는 ' 희미하게 ' 개체를 사용 하 여 회색으로 표시 된 요소가 HMA 별 구성에 포함 되지 않음을 의미* 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="099d0-111">하이브리드 최신 인증 사용</span><span class="sxs-lookup"><span data-stu-id="099d0-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="099d0-112">HMA를 켜는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="099d0-113">시작 하기 전에 필수 구성 요소을 충족 하는지 확인해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="099d0-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="099d0-114">대부분의 **필수 구성 요소** 는 비즈니스용 Skype 및 Exchange, [하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 skype 및 exchange 서버에서 사용 하기 위한 필수 구성 요소](hybrid-modern-auth-overview.md)에 공통 됩니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-114">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="099d0-115">이 문서에 나와 있는 단계를 시작 하기 전에이 작업을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="099d0-115">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="099d0-116">Azure AD에서 온-프레미스 웹 서비스 Url을 Spn (서비스 사용자 이름)으로 추가</span><span class="sxs-lookup"><span data-stu-id="099d0-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="099d0-117">모든 가상 디렉터리가 HMA에 사용 되도록 설정</span><span class="sxs-lookup"><span data-stu-id="099d0-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="099d0-118">EvoSTS 인증 서버 개체 확인</span><span class="sxs-lookup"><span data-stu-id="099d0-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="099d0-119">EXCH에서 HMA를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="099d0-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="099d0-120">**참고 사항** Office에서 지원 되는 버전은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="099d0-120">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="099d0-121">[최신 인증이 Office 2013 및 office 2016 클라이언트 앱에 작동 하는 방식을](modern-auth-for-office-2013-and-2016.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="099d0-121">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="099d0-122">모든 사전 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="099d0-123">비즈니스용 Skype 및 Exchange에 대 한 많은 필수 구성 요소가 공통적 이므로 [온-프레미스 비즈니스용 skype 및 exchange 서버에서 하이브리드 최신 인증 개요 및 필수 구성 요소를 사용 하](hybrid-modern-auth-overview.md)는 경우를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="099d0-123">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="099d0-124">이 문서에 나와 있는 단계를 시작 *하기 전에* 이 작업을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="099d0-124">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="099d0-125">Azure AD에서 온-프레미스 웹 서비스 Url을 Spn으로 추가</span><span class="sxs-lookup"><span data-stu-id="099d0-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="099d0-126">온-프레미스 웹 서비스 Url을 Azure AD Spn으로 할당 하는 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-126">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="099d0-127">인증 및 권한 부여 중에는 클라이언트 컴퓨터 및 장치에서 Spn을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-127">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="099d0-128">온-프레미스에서 Azure Active Directory (AAD)에 연결 하는 데 사용할 수 있는 모든 Url은 AAD (내부 및 외부 네임 스페이스가 모두 포함 됨)에 등록 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-128">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="099d0-129">먼저 AAD에서 추가 해야 하는 모든 Url을 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-129">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="099d0-130">온-프레미스에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-130">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="099d0-131">클라이언트가 연결할 수 있는 Url이 AAD에서 HTTPS 서비스 사용자 이름으로 나열 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="099d0-132">먼저 [다음 지침](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)을 사용 하 여 AAD에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="099d0-133">**참고 사항** 아래 명령을 사용할 수 있으려면이 페이지의 Connect-msolservice 옵션을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="099d0-134">Exchange 관련 Url에 대해 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="099d0-135">메모 작성 (및 이후 비교)이 명령의 출력에는 https:// *autodiscover.yourdomain.com* 및 Https:// *mail.yourdomain.com* URL이 포함 되어 있지만 대부분의 경우에 시작 하는 spn으로 구성 됩니다. 00000002-0000-0ff1-ce00-000000000000/.</span><span class="sxs-lookup"><span data-stu-id="099d0-135">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="099d0-136">누락 된 https://Url이 있는 경우이 목록에 특정 레코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-136">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="099d0-137">이 목록에 내부 및 외부 MAPI/HTTP, EWS, ActiveSync, OAB 및 자동 검색 레코드가 표시 되지 않으면 아래 명령을 사용 하 여 추가 해야 합니다 (예: Url은 '`mail.corp.contoso.com`' 및 '`owa.contoso.com`' 임). \*\*\*\* :</span><span class="sxs-lookup"><span data-stu-id="099d0-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="099d0-138">2 단계에서 (New-msolserviceprincipal 명령을 다시 실행 하 고 출력을 검토 하 여 새 레코드가 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-138">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="099d0-139">목록/스크린샷에서 새 Spn 목록을 비교 합니다 (레코드의 새 목록을 스크린샷 할 수도 있음).</span><span class="sxs-lookup"><span data-stu-id="099d0-139">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="099d0-140">성공적으로 완료 되 면 목록에 두 개의 새 Url이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-140">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="099d0-141">예를 들어, Spn 목록에는 이제 특정 Url `https://mail.corp.contoso.com` 과 `https://owa.contoso.com`가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-141">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="099d0-142">가상 디렉터리가 올바르게 구성 되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="099d0-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="099d0-143">이제 다음 명령을 실행 하 여 Outlook에서 사용할 수 있는 모든 가상 디렉터리의 Exchange에서 OAuth가 제대로 사용 하도록 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="099d0-144">출력을 확인 하 여 이러한 각 VDirs에 **OAuth** 가 사용 되도록 설정 되어 있는지 확인 하 고,이에 대 한 자세한 내용은 ' OAuth '와 같이 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="099d0-145">서버 및 4 개의 가상 디렉터리에서 OAuth가 누락 된 경우 계속 하기 전에 관련 명령을 사용 하 여이를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="099d0-146">EvoSTS 인증 서버 개체가 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="099d0-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="099d0-147">이 마지막 명령에 대해 온-프레미스 Exchange 관리 셸로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-147">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="099d0-148">이제 온-프레미스에 evoSTS 인증 공급자에 대 한 항목이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-148">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="099d0-149">출력에는 EvoSts 이름의 AuthServer이 표시 되 고 ' Enabled ' 상태가 True 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-149">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="099d0-150">이 표시 되지 않으면 최신 버전의 하이브리드 구성 마법사를 다운로드 하 여 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-150">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="099d0-151">**중요** 환경에서 Exchange 2010을 실행 하는 경우 EvoSTS 인증 공급자가 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="099d0-152">HMA 사용</span><span class="sxs-lookup"><span data-stu-id="099d0-152">Enable HMA</span></span>

<span data-ttu-id="099d0-153">Exchange 관리 셸에서 온-프레미스에 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="099d0-154">지</span><span class="sxs-lookup"><span data-stu-id="099d0-154">Verify</span></span>

<span data-ttu-id="099d0-155">HMA를 사용 하도록 설정 하면 클라이언트의 다음 로그인은 새 인증 흐름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-155">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="099d0-156">HMA를 설정 하는 것 만으로도 클라이언트에 대 한 재인증이 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-156">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="099d0-157">클라이언트는 인증 토큰 및/또는 인증서의 수명에 따라 다시 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-157">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="099d0-158">또한 CTRL 키를 누른 상태로 Outlook 클라이언트 아이콘 (Windows 알림 트레이)을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 상태 '를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-158">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="099d0-159">OAuth에서 사용 되는 전달자 토큰을 나타내는 ' 전달자\*' 유형 (' 인증 ' 형식)에 대해 클라이언트의 SMTP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-159">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="099d0-160">**참고 사항** HMA를 사용 하 여 비즈니스용 Skype를 구성 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="099d0-160">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="099d0-161">[지원 되는 토폴로지](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)를 나열 하는 문서와 [구성을 수행](configure-skype-for-business-for-hybrid-modern-authentication.md)하는 방법을 보여 주는 두 개의 문서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="099d0-161">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="099d0-162">관련 항목</span><span class="sxs-lookup"><span data-stu-id="099d0-162">Related topics</span></span>

[<span data-ttu-id="099d0-163">하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 Skype와 Exchange 서버를 사용 하기 위한 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="099d0-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

