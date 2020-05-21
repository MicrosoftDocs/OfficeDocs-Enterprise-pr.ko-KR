---
title: 하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법
ms.author: kvice
author: kelleyvice-msft
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
f1.keywords:
- NOCSH
description: 하이브리드 최신 인증 (HMA)은 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.
ms.openlocfilehash: c52eecbe57567276de94aac913b7b82db8c5e404
ms.sourcegitcommit: 72a4938f1372e7f3693b53bcabac0c5d18305a1d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44326445"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="5f783-103">하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="5f783-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="5f783-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="5f783-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="5f783-105">하이브리드 최신 인증 (HMA)은 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-105">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="5f783-106">선택적</span><span class="sxs-lookup"><span data-stu-id="5f783-106">FYI</span></span>

<span data-ttu-id="5f783-107">시작 하기 전에 다음을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-107">Before we begin, I call:</span></span>
  
- <span data-ttu-id="5f783-108">하이브리드 최신 인증 \> HMA</span><span class="sxs-lookup"><span data-stu-id="5f783-108">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="5f783-109">Exchange 온-프레미스 \> exch</span><span class="sxs-lookup"><span data-stu-id="5f783-109">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="5f783-110">Exchange Online \> exo</span><span class="sxs-lookup"><span data-stu-id="5f783-110">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="5f783-111">또한 *이 문서의 그래픽에 ' 흐리게 ' 또는 ' 희미하게 ' 개체를 사용 하 여 회색으로 표시 된 요소가 HMA 별 구성에 포함 되지 않음을 의미* 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-111">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="5f783-112">하이브리드 최신 인증 사용</span><span class="sxs-lookup"><span data-stu-id="5f783-112">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="5f783-113">HMA를 켜는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-113">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="5f783-114">시작 하기 전에 필수 구성 요소을 충족 하는지 확인해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="5f783-114">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="5f783-115">대부분의 **필수 구성 요소** 는 비즈니스용 Skype 및 Exchange, [하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 skype 및 exchange 서버에서 사용 하기 위한 필수 구성 요소](hybrid-modern-auth-overview.md)에 공통 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-115">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="5f783-116">이 문서에 나와 있는 단계를 시작 하기 전에이 작업을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5f783-116">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="5f783-117">Azure AD에서 온-프레미스 웹 서비스 Url을 Spn (서비스 사용자 이름)으로 추가</span><span class="sxs-lookup"><span data-stu-id="5f783-117">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="5f783-118">모든 가상 디렉터리가 HMA에 사용 되도록 설정</span><span class="sxs-lookup"><span data-stu-id="5f783-118">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="5f783-119">EvoSTS 인증 서버 개체 확인</span><span class="sxs-lookup"><span data-stu-id="5f783-119">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="5f783-120">EXCH에서 HMA를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="5f783-120">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="5f783-121">**참고 사항** Office에서 지원 되는 버전은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="5f783-121">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="5f783-122">[최신 인증이 Office 2013 및 office 2016 클라이언트 앱에 작동 하는 방식을](modern-auth-for-office-2013-and-2016.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5f783-122">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="5f783-123">모든 사전 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-123">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="5f783-124">비즈니스용 Skype 및 Exchange에 대 한 많은 필수 구성 요소가 공통적 이므로 [온-프레미스 비즈니스용 skype 및 exchange 서버에서 하이브리드 최신 인증 개요 및 필수 구성 요소를 사용 하](hybrid-modern-auth-overview.md)는 경우를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5f783-124">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="5f783-125">이 문서에 나와 있는 단계를 시작 *하기 전에* 이 작업을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5f783-125">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="5f783-126">Azure AD에서 온-프레미스 웹 서비스 Url을 Spn으로 추가</span><span class="sxs-lookup"><span data-stu-id="5f783-126">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="5f783-127">온-프레미스 웹 서비스 Url을 Azure AD Spn으로 할당 하는 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-127">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="5f783-128">인증 및 권한 부여 중에는 클라이언트 컴퓨터 및 장치에서 Spn을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-128">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="5f783-129">온-프레미스에서 Azure Active Directory (AAD)에 연결 하는 데 사용할 수 있는 모든 Url은 AAD (내부 및 외부 네임 스페이스가 모두 포함 됨)에 등록 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-129">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="5f783-130">먼저 AAD에서 추가 해야 하는 모든 Url을 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-130">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="5f783-131">온-프레미스에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-131">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="5f783-132">클라이언트가 연결할 수 있는 Url이 AAD에서 HTTPS 서비스 사용자 이름으로 나열 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-132">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="5f783-133">먼저 [다음 지침](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)을 사용 하 여 AAD에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-133">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="5f783-134">**참고 사항** 아래 명령을 사용할 수 있으려면이 페이지의 Connect-msolservice 옵션을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-134">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="5f783-135">Exchange 관련 Url에 대해 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-135">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="5f783-136">메모 작성 (및 이후 비교)이 명령의 출력은 https:// *autodiscover.yourdomain.com* 및 Https:// *mail.yourdomain.com* URL을 포함 해야 하지만 대부분 00000002-0000-0ff1-ce00-000000000000/로 시작 하는 spn으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-136">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="5f783-137">누락 된 https://Url이 있는 경우이 목록에 특정 레코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-137">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="5f783-138">이 목록에 내부 및 외부 MAPI/HTTP, EWS, ActiveSync, OAB 및 자동 검색 레코드가 표시 되지 않으면 아래 명령을 사용 하 여 추가 해야 합니다 (예: Url은 ' `mail.corp.contoso.com` ' 및 ' ' 임 `owa.contoso.com` ). **replace the example URLs with your own**</span><span class="sxs-lookup"><span data-stu-id="5f783-138">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="5f783-139">2 단계에서 (New-msolserviceprincipal 명령을 다시 실행 하 고 출력을 검토 하 여 새 레코드가 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-139">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="5f783-140">목록/스크린샷에서 새 Spn 목록을 비교 합니다 (레코드의 새 목록을 스크린샷 할 수도 있음).</span><span class="sxs-lookup"><span data-stu-id="5f783-140">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="5f783-141">성공적으로 완료 되 면 목록에 두 개의 새 Url이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-141">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="5f783-142">예를 들어, Spn 목록에는 이제 특정 Url과가 포함 됩니다 `https://mail.corp.contoso.com` `https://owa.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="5f783-142">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="5f783-143">가상 디렉터리가 올바르게 구성 되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="5f783-143">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="5f783-144">이제 다음 명령을 실행 하 여 Outlook에서 사용할 수 있는 모든 가상 디렉터리의 Exchange에서 OAuth가 제대로 사용 하도록 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-144">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="5f783-145">출력을 확인 하 여 이러한 각 VDirs에 **OAuth** 가 사용 되도록 설정 되어 있는지 확인 하 고,이에 대 한 자세한 내용은 ' OAuth '와 같이 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-145">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

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
  
<span data-ttu-id="5f783-146">모든 서버 및 4 개의 가상 디렉터리에서 OAuth가 누락 된 경우 계속 하기 전에 관련 명령을 사용 하 여이를 추가 해야 합니다 ([set-mapivirtualdirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-mapivirtualdirectory?view=exchange-ps), [get-webservicesvirtualdirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-webservicesvirtualdirectory?view=exchange-ps), [new-oabvirtualdirectory](https://docs.microsoft.com/powershell/module/exchange/email-addresses-and-address-books/set-oabvirtualdirectory?view=exchange-ps)및 [new-autodiscovervirtualdirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-autodiscovervirtualdirectory?view=exchange-ps)).</span><span class="sxs-lookup"><span data-stu-id="5f783-146">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding ([Set-MapiVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-mapivirtualdirectory?view=exchange-ps), [Set-WebServicesVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-webservicesvirtualdirectory?view=exchange-ps), [Set-OABVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/email-addresses-and-address-books/set-oabvirtualdirectory?view=exchange-ps), and [Set-AutodiscoverVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-autodiscovervirtualdirectory?view=exchange-ps)).</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="5f783-147">EvoSTS 인증 서버 개체가 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="5f783-147">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="5f783-148">이 마지막 명령에 대해 온-프레미스 Exchange 관리 셸로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-148">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="5f783-149">이제 온-프레미스에 evoSTS 인증 공급자에 대 한 항목이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-149">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="5f783-150">출력에는 EvoSts 이름의 AuthServer이 표시 되 고 ' Enabled ' 상태가 True 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-150">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="5f783-151">이 표시 되지 않으면 최신 버전의 하이브리드 구성 마법사를 다운로드 하 여 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-151">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="5f783-152">**중요** 환경에서 Exchange 2010을 실행 하는 경우 EvoSTS 인증 공급자가 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-152">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="5f783-153">HMA 사용</span><span class="sxs-lookup"><span data-stu-id="5f783-153">Enable HMA</span></span>

<span data-ttu-id="5f783-154">Exchange 관리 셸에서 온-프레미스에 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-154">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="5f783-155">지</span><span class="sxs-lookup"><span data-stu-id="5f783-155">Verify</span></span>

<span data-ttu-id="5f783-156">HMA를 사용 하도록 설정 하면 클라이언트의 다음 로그인은 새 인증 흐름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-156">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="5f783-157">HMA를 설정 하는 것 만으로도 클라이언트에 대 한 재인증이 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-157">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="5f783-158">클라이언트는 인증 토큰 및/또는 인증서의 수명에 따라 다시 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-158">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="5f783-159">또한 CTRL 키를 누른 상태로 Outlook 클라이언트 아이콘 (Windows 알림 트레이)을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 상태 '를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-159">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="5f783-160">\*OAuth에서 사용 되는 전달자 토큰을 나타내는 ' 전달자 ' 유형 (' 인증 ' 형식)에 대해 클라이언트의 SMTP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-160">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="5f783-161">**참고 사항** HMA를 사용 하 여 비즈니스용 Skype를 구성 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="5f783-161">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="5f783-162">[지원 되는 토폴로지](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)를 나열 하는 문서와 [구성을 수행](configure-skype-for-business-for-hybrid-modern-authentication.md)하는 방법을 보여 주는 두 개의 문서가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f783-162">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
 
## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a><span data-ttu-id="5f783-163">Android 및 iOS용 Outlook에서 하이브리드 최신 인증 사용</span><span class="sxs-lookup"><span data-stu-id="5f783-163">Using hybrid Modern Authentication with Outlook for iOS and Android</span></span>

<span data-ttu-id="5f783-164">TCP 443에서 Exchange server를 사용 하는 온-프레미스 고객의 경우 다음 IP 범위를 허용 목록. </span><span class="sxs-lookup"><span data-stu-id="5f783-164">If you are an on-premises customer using Exchange server on TCP 443, please whitelist the following IP ranges:  </span></span><BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> 
  

## <a name="related-topics"></a><span data-ttu-id="5f783-165">관련 항목</span><span class="sxs-lookup"><span data-stu-id="5f783-165">Related topics</span></span>

[<span data-ttu-id="5f783-166">하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 Skype와 Exchange 서버를 사용 하기 위한 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="5f783-166">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  
<span data-ttu-id="5f783-167">Outlook 사용자를 최신 인증으로 강제 적용</span><span class="sxs-lookup"><span data-stu-id="5f783-167">Force Outlook users to Modern Authentication</span></span>  
[<span data-ttu-id="5f783-168">Office 365 전용/ITAR에서 vNext로의 전환에 대 한 최신 인증 구성 요구 사항</span><span class="sxs-lookup"><span data-stu-id="5f783-168">Modern Authentication configuration requirements for transition from Office 365 dedicated/ITAR to vNext</span></span>](modern-authentication-configuration.md)
