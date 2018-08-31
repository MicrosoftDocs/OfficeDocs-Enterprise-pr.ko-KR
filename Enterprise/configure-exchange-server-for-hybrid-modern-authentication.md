---
title: 하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 하이브리드 현대 인증 (HMA)는 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.
ms.openlocfilehash: 871f03b8e776c694f7378f6905259d21516f7326
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542063"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="7e4eb-103">하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="7e4eb-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="7e4eb-104">하이브리드 현대 인증 (HMA)는 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="7e4eb-105">선택 참석자</span><span class="sxs-lookup"><span data-stu-id="7e4eb-105">FYI</span></span>

<span data-ttu-id="7e4eb-106">시작 하기 전에 다음을 호출 I:</span><span class="sxs-lookup"><span data-stu-id="7e4eb-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="7e4eb-107">하이브리드 현대 인증 \> HMA</span><span class="sxs-lookup"><span data-stu-id="7e4eb-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="7e4eb-108">온-프레미스 exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="7e4eb-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="7e4eb-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="7e4eb-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="7e4eb-110">또한 *이 문서는가 ' 흐리게 표시 ' 또는 '흐리게 표시' 즉, 회색으로 표시 된 요소 HMA 관련 구성에 포함 되지 않은 개체는 하는 경우에 그래픽은* 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="7e4eb-111">하이브리드 현대 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7e4eb-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="7e4eb-112">HMA 의미를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="7e4eb-113">시작 하기 전에 선행 조건 충족 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="7e4eb-p101">많은 **필수 구성 요소** 이후 비즈니스 및 Exchange, [하이브리드 현대 인증 개요와 함께 사용 하는 것에 대 한 필수 구성 요소 온-프레미스 비즈니스 및 Exchange 서버에 대 한 Skype](hybrid-modern-auth-overview.md)Skype 모두에 대 한 일반적인 됩니다. 이 문서의 단계 중 하나를 시작 하기 전에이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="7e4eb-116">추가 (영문) 온-프레미스 웹 서비스 Url (Spn) 서비스 사용자 이름으로 Azure AD에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="7e4eb-117">HMA를 사용할 수 있는 모든 가상 디렉터리를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="7e4eb-118">EvoSTS 인증 서버 개체를 확인 하는 기능</span><span class="sxs-lookup"><span data-stu-id="7e4eb-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="7e4eb-119">EXCH.에서 HMA를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7e4eb-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="7e4eb-p102">**참고 사항** Office의 버전 MA를 지원 합니까? [Office 2013 및 Office 2016 클라이언트 응용 프로그램에 대 한 인증 작동 방법 현대](modern-auth-for-office-2013-and-2016.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="7e4eb-122">모든는 p r e-요구 사항 충족 하는지 확인</span><span class="sxs-lookup"><span data-stu-id="7e4eb-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="7e4eb-p103">많은 필수 구성 요소는 일반적으로 비즈니스 및 Exchange에 대 한 두 Skype, 이후 [하이브리드 현대 인증 개요 및 사용 하 여 비즈니스 및 Exchange 서버에 대 한 온-프레미스 Skype 사용 하기 위한 필수 구성 요소를](hybrid-modern-auth-overview.md)검토 합니다. 이 수행 *하기 전에* 이 문서의 단계 중 하나를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="7e4eb-125">온-프레미스 Azure AD에 Spn으로 서비스 Url을 웹 추가</span><span class="sxs-lookup"><span data-stu-id="7e4eb-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="7e4eb-p104">Azure AD Spn. Spn은 클라이언트 컴퓨터 및 장치에서 인증 및 권한 부여 하는 동안 사용 되는 대로 온-프레미스 웹 서비스 Url을 할당 하는 명령을 실행 합니다. Azure Active Directory (AAD)를 온-프레미스에서 연결을 사용할 수 있는 모든 Url (내부 및 외부 네임 스페이스 포함) AAD에 등록 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="7e4eb-p105">먼저, AAD에 추가 하는 모든 Url을 수집 합니다. 이러한 명령을 온-프레미스를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
- <span data-ttu-id="7e4eb-131">Get-MapiVirtualDirectory | FL 서버\*url\*</span><span class="sxs-lookup"><span data-stu-id="7e4eb-131">Get-MapiVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="7e4eb-132">Get-webservicesvirtualdirectory | FL 서버\*url\*</span><span class="sxs-lookup"><span data-stu-id="7e4eb-132">Get-WebServicesVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="7e4eb-133">**Get-activesyncvirtualdirectory | FL 서버\*url\***</span><span class="sxs-lookup"><span data-stu-id="7e4eb-133">**Get-ActiveSyncVirtualDirectory | FL server,\*url\***</span></span>
    
- <span data-ttu-id="7e4eb-134">Get-oabvirtualdirectory | FL 서버\*url\*</span><span class="sxs-lookup"><span data-stu-id="7e4eb-134">Get-OABVirtualDirectory | FL server,\*url\*</span></span>
    
<span data-ttu-id="7e4eb-135">클라이언트가 수 AAD에서 HTTPS 서비스 사용자 이름으로 나열 된 연결할 Url을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-135">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="7e4eb-136">먼저, [이러한 지침](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell)과 함께 AAD에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-136">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>
    
2. <span data-ttu-id="7e4eb-137">Exchange에 대 한 관련된 Url에 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-137">For your Exchange related URLs, type the following command:</span></span>
    
- <span data-ttu-id="7e4eb-138">Get-MsolServicePrincipal-AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | -ExpandProperty ServicePrincipalNames를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-138">Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames</span></span>
    
<span data-ttu-id="7e4eb-p106">https:// 포함 되어야 하는이 명령의 출력을 메모해 두십시오 (및 나중에 비교에 대 한 스크린샷)를 수행 * 자동 검색 합니다. *사용자* .com * 및 https:// *mail.yourdomain.com* URL 대개 00000002-0000-0ff1-ce00-000000000000로 시작 하는 Spn을 구성 하지만 / 합니다. Https:// Url에서 온-프레미스 누락 된 경우이 목록에 해당 특정 레코드를 추가 하는 것이 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https:// *autodiscover. *yourdomain*  .com *  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="7e4eb-142">아래 명령을 사용 하 여 추가 해야이 목록에 내부 및 외부 MAPI/HTTP, EWS, ActiveSync, OAB 및 자동 검색 레코드 보이지 않으면 (이 예제에서는 Url은 '`mail.corp.contoso.com`'및'`owa.contoso.com`', **자신의 예제 Url을 교체** 했지만) :</span><span class="sxs-lookup"><span data-stu-id="7e4eb-142">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> </br>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="7e4eb-p107">마찬가지로 2 단계에서 Get MsolServicePrincipal 명령을 실행 하 고 출력을 통해을 찾고 추가 된 새 레코드를 확인 합니다. 목록 비교 / Spn (수도 있습니다 스크린샷 새 목록에 레코드에 대 한)의 새 목록에 앞에서 스크린샷. 성공한, 두 새 Url 목록에 표시 됩니다. 이 예제에서 이동, Spn 목록이 이제 포함 됩니다 특정 Url `https://mail.corp.contoso.com` 및 `https://owa.contoso.com`합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="7e4eb-147">가상 디렉터리는 제대로 구성 확인</span><span class="sxs-lookup"><span data-stu-id="7e4eb-147">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="7e4eb-148">이제 확인 OAuth에서 제대로 설정 되어 Exchange 모든 가상 디렉터리 Outlook에서 다음 명령을 실행 하 여 사용할 수:</span><span class="sxs-lookup"><span data-stu-id="7e4eb-148">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

<span data-ttu-id="7e4eb-149">이러한 VDirs의 각에서 검사 **OAuth** 있는지 확인 하려면 출력을 사용할지, 모양과 동일 하 게 다음과 같이 (이며 살펴보는 것 'OAuth');</span><span class="sxs-lookup"><span data-stu-id="7e4eb-149">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 
  
 <span data-ttu-id="7e4eb-150">**[PS] C:\Windows\system32\>Get MapiVirtualDirectory | fl 서버\*url\*,\*인증\***</span><span class="sxs-lookup"><span data-stu-id="7e4eb-150">**[PS] C:\Windows\system32\>Get-MapiVirtualDirectory | fl server,\*url\*,\*auth\***</span></span>
  
 <span data-ttu-id="7e4eb-151">**서버: EX1**</span><span class="sxs-lookup"><span data-stu-id="7e4eb-151">**Server : EX1**</span></span>
  
 <span data-ttu-id="7e4eb-152">**InternalUrl:`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="7e4eb-152">**InternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="7e4eb-153">**ExternalUrl:`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="7e4eb-153">**ExternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="7e4eb-154">**IISAuthenticationMethods: {Ntlm, OAuth, 협상}**</span><span class="sxs-lookup"><span data-stu-id="7e4eb-154">**IISAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="7e4eb-155">**InternalAuthenticationMethods: {Ntlm, OAuth, 협상}**</span><span class="sxs-lookup"><span data-stu-id="7e4eb-155">**InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="7e4eb-156">**ExternalAuthenticationMethods: {Ntlm, OAuth, 협상}**</span><span class="sxs-lookup"><span data-stu-id="7e4eb-156">**ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
<span data-ttu-id="7e4eb-157">OAuth 서버 및 4 개의 가상 디렉터리의 모든에서 누락 된 경우 계속 하기 전에 관련 명령을 사용 하 여 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-157">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="7e4eb-158">EvoSTS 인증 서버 개체가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-158">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="7e4eb-p108">이 마지막 명령에 대 한 온-프레미스 Exchange 관리 셸을 반환 합니다. 이제 evoSTS 인증 공급자에 대 한 온-프레미스에 항목이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
<span data-ttu-id="7e4eb-p109">사용자가 출력 한 AuthServer 이름 EvoSts의 표시 및 'Enabled' 상태 True 여야 합니다. 이 표시 되지 않으면를 다운로드 하 고 하이브리드 구성 마법사의 최신 버전을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="7e4eb-163">**중요 한** 환경에서 Exchange 2010을 실행 하는 경우에 EvoSTS 인증 공급자를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-163">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="7e4eb-164">HMA를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7e4eb-164">Enable HMA</span></span>

<span data-ttu-id="7e4eb-165">온-프레미스 Exchange 관리 셸에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-165">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="7e4eb-166">확인</span><span class="sxs-lookup"><span data-stu-id="7e4eb-166">Verify</span></span>

<span data-ttu-id="7e4eb-p110">HMA를 사용 하도록 설정 되 면 클라이언트의 다음 로그인 하는 새 인증 흐름을 사용 합니다. 참고 방금 HMA를 켜서는 다시 인증 하는 모든 클라이언트에 대 한 트리거하지 않습니다. 클라이언트를 다시 인증에 따라 인증 토큰 및/또는 인증서의 수명 동안 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="7e4eb-p111">또한 Outlook 클라이언트 (도: Windows 알림 트레이)에 대 한 아이콘 마우스 오른쪽 단추로 클릭 하는 동시에 CTRL 키를 누른 하 고 ' 연결 상태 '를 클릭 해야 합니다. 'Authn' 형식에 대해 클라이언트의 SMTP 주소를 찾습니다 ' Bearer\*'를 사용 하 여 OAuth bearer 토큰을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="7e4eb-p112">**참고 사항** HMA를 사용 하 여 비즈니스를 위한 Skype 구성 해야 합니까? 두 문서를 수행 해야: [지원 되는 토폴로지](https://technet.microsoft.com/en-us/library/mt803262.aspx)를 나열 하 고 하나 [구성 작업을 수행 하는 방법](configure-skype-for-business-for-hybrid-modern-authentication.md)을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="7e4eb-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://technet.microsoft.com/en-us/library/mt803262.aspx), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="7e4eb-174">관련 항목</span><span class="sxs-lookup"><span data-stu-id="7e4eb-174">Related topics</span></span>

[<span data-ttu-id="7e4eb-175">하이브리드 현대 인증 개요 및 온-프레미스 Skype를 사용 하 여 비즈니스 및 Exchange 서버에 대 한 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="7e4eb-175">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

