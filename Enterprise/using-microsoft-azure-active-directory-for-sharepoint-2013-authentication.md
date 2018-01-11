---
title: "SharePoint 2013 인증에 대 한 Microsoft Azure Active Directory를 사용 하 여"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "요약: Azure Active Directory를 사용 하 여 SharePoint Server 2013 사용자를 인증 하는 Azure 액세스 제어 서비스를 사용 하는 방법에 알아봅니다."
ms.openlocfilehash: 9025eb53f4d8e37403c48416f41adbe35fa9fa01
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="381bf-103">SharePoint 2013 인증에 대 한 Microsoft Azure Active Directory를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="381bf-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="381bf-104">**요약:** Azure Active Directory를 사용 하 여 SharePoint Server 2013 사용자를 인증 하는 Azure 액세스 제어 서비스를 사용 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="381bf-p101">다른 id 공급자를 사용 하 여 인증 하는 하 여 사용자를 관리 하기 쉽습니다 될 수 있습니다. 어떻게 편리 하 게 수 신뢰할 수 있지만 다른 사람을 관리 하는 id 공급자를 사용 하는 것이 좋습니다. 예, 한 가지 유형의 사용자가 액세스 하는 클라우드에서 SharePoint Server 2013에 대 한 인증 및 온-프레미스 환경에서 SharePoint 2013 사용자에 대 한 다른 있을 수 있습니다. Azure 액세스 제어 서비스를 사용 하면 이러한 선택 가능한 있습니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="381bf-p102">이 문서에서는 Azure 액세스 제어 서비스를 사용 하 여 온-프레미스 Active Directory 대신 Azure AD 사용한 SharePoint 2013 사용자를 인증 하는 방법을 설명 합니다. 이 구성에서 Azure AD SharePoint 2013에 대 한 신뢰할 수 있는 id 공급자를 됩니다. 이 구성 추가 하는 SharePoint 2013 설치 자체에서 사용 하는 Active Directory 인증 분리 하는 사용자 인증 방법입니다. 이 문서를 에서도 Ws-federation을 파악 해야 합니다. 자세한 내용은 [Ws-federation 이해를](https://go.microsoft.com/fwlink/p/?linkid=188052)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="381bf-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="381bf-114">다음 그림에서는이 구성에서 SharePoint 2013 사용자에 대 한 인증을 작동 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![Azure Active Directory로 인증된 사용자](images/SP_AzureAD.png)
  
<span data-ttu-id="381bf-116">이 문서에 사용 되는 예제는 Kirk Evans, Azure 최상의 센터에 대 한 Microsoft 설계자에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="381bf-117">SharePoint 2013 내게 필요한 옵션에 대 한 정보를 [SharePoint 2013에 대 한 내게 필요한 옵션](https://go.microsoft.com/fwlink/p/?LinkId=393123)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="381bf-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="381bf-118">구성 개요</span><span class="sxs-lookup"><span data-stu-id="381bf-118">Configuration overview</span></span>

<span data-ttu-id="381bf-119">SharePoint 2013 id 공급자로 Azure AD를 사용 하 여 환경을 설정 하는 이러한 일반적인 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="381bf-120">새 만들기 Azure AD 테 넌 트 및 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="381bf-121">Ws-federation id 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="381bf-122">신뢰 당사자 응용 프로그램으로 SharePoint를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="381bf-123">SSL을 사용 하 여 자체 서명 된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="381bf-124">클레임 기반 인증에 대 한 규칙 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="381bf-125">X.509 인증서를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="381bf-126">클레임 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="381bf-127">새 id 공급자에 대 한 SharePoint를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="381bf-128">사용 권한을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="381bf-129">새 공급자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="381bf-130">Azure AD 테 넌 트 및 네임 스페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="381bf-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="381bf-p103">새로 만들려면 다음 단계를 사용 하 여 Azure AD 테 넌 트 및 연결된 된 네임 스페이스입니다. 이 예제에서는 사용 하 여 네임 스페이스 "blueskyabove."</span><span class="sxs-lookup"><span data-stu-id="381bf-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="381bf-133">Azure 관리 포털에서 **Active Directory**클릭 하 고 새 프로그램을 만들 Azure AD 테 넌 트입니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="381bf-134">**액세스 제어 네임 스페이스**클릭 하 고 새 네임 스페이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="381bf-p104">아래쪽 모음에서 **관리** 를 클릭 합니다. 이 위치 열려야 https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="381bf-p105">Windows PowerShell을 엽니다. Windows PowerShell 용 Azure cmdlet을 설치 하기 위한 필수 구성 요소는 Microsoft 온라인 서비스 모듈에 대 한 Windows PowerShell을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="381bf-139">Windows PowerShell 명령 프롬프트에서 명령을 입력: `Connect-Msolservice`, 하 고 사용자의 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="381bf-140">Windows PowerShell 용 Azure cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell을 사용 하 여 Azure AD 관리](https://go.microsoft.com/fwlink/p/?LinkId=393124)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="381bf-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="381bf-141">Windows PowerShell 명령 프롬프트에서 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="381bf-142">다음 그림에서는 출력 결과를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-142">The following figure illustrates the output result.</span></span>
    
     ![서비스 사용자 이름 만들기](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="381bf-144">네임 스페이스에 WS 페더레이션 id 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="381bf-145">Blueskyabove 네임 스페이스에 새 WS 페더레이션 id 공급자를 추가 하려면 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="381bf-146">Azure 관리 포털에서 **Active Directory**로 이동 > **액세스 제어 네임 스페이스** **새 인스턴스 만들기**를 클릭 한 다음 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="381bf-147">Azure 액세스 제어 포털에서 **Id 공급자**를 클릭 > **추가**, 다음 그림에 나와있는 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Azure의 ID 공급자 대화 상자](images/Identity.jpg)
  
3. <span data-ttu-id="381bf-149">다음 그림에 나와있는 것 처럼 **WS 페더레이션 id 공급자**클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![ID 공급자 추가 설정](images/AddIdentity.jpg)
  
4. <span data-ttu-id="381bf-p106">표시 이름 및 로그온 링크 텍스트를 작성 한 다음 **저장**을 클릭 합니다. Ws-federation 메타 데이터 URL에 대 한 https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml를 입력 합니다. 다음 그림에서는 설정을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![페더레이션 ID 공급자](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="381bf-155">신뢰 당사자 응용 프로그램으로 SharePoint 추가</span><span class="sxs-lookup"><span data-stu-id="381bf-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="381bf-156">다음 단계를 사용 하 여 신뢰 당사자 응용 프로그램으로 SharePoint를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="381bf-157">신뢰 당사자 응용 프로그램 설정에 대 한 추가 정보에 대 한 [신뢰 당사자 응용 프로그램](https://go.microsoft.com/fwlink/p/?LinkId=393125)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="381bf-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="381bf-158">Azure 액세스 제어 포털에서 **신뢰 당사자 응용 프로그램**클릭 하 고 다음 그림에 나와있는 것 처럼 다음 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![신뢰 당사자 응용 프로그램 설정](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="381bf-160">SSL을 사용 하 여 자체 서명 된 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="381bf-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="381bf-161">다음 단계를 사용 하 여 SSL을 통한 보안 통신을 위해 사용 하 여 새, 자체 서명 된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="381bf-162">다음 그림에 나와있는 것 처럼 PublishingSite,으로 동일한 URL을 사용 하려면 SSL 포트 443 함께 사용 하 여 웹 응용 프로그램을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![응용 프로그램을 확장하기 위한 설정](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="381bf-164">IIS 관리자에서 **서버 인증서**를 두번클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="381bf-p107">**동작** 창에서 **자체 서명 된 인증서 만들기**를 클릭 합니다. **지정 인증서에 대 한 이름** 상자에 인증서에 대 한 친숙 한 이름을 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="381bf-167">**사이트 바인딩 편집** 대화 상자에서 호스트 이름은 친숙 한 이름을와 동일 하 게 다음 그림에 나와있는 것 처럼 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![자체 서명된 인증서 마법사](images/SelfSignedCert.jpg)
  
     ![바인딩 편집 상자의 호스트 이름](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="381bf-170">Azure 관리 포털에서 구성 하려는 가상 컴퓨터를 클릭 하 고 **끝점**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="381bf-171">**추가**클릭 하 고 다음을 클릭 **-->** (다음)에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="381bf-172">**이름**는 끝점에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="381bf-p108">**공용 포트** 및 **개인 포트**를 사용 하려는 포트 번호를 입력 하 고 완료를 확인 표시를 클릭 합니다. 이러한 번호는 다를 수 있습니다. 이 문서에서는에서는 사용 443, 다음 그림에 나와있는 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![Azure의 끝점 설정](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="381bf-177">Azure에 가상 컴퓨터에 끝점을 추가 하는 방법에 대 한 자세한 내용은 [가상 컴퓨터에 설정를 끝점 하는 방법](https://go.microsoft.com/fwlink/p/?LinkId=393126)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="381bf-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="381bf-178">다음 그림에 나와있는 것 처럼 액세스 제어 서비스 포털에서 신뢰 당사자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![신뢰 당사자 추가 응용 프로그램 설정](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="381bf-180">클레임 기반 인증에 대 한 규칙 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="381bf-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="381bf-181">다음 단계를 사용 하 여 제어 클레임 기반 인증을 새 규칙 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="381bf-182">왼쪽된 창에서 **규칙 그룹**클릭 한 다음 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="381bf-p109">규칙 그룹에 대 한 이름을 입력 하 고 **저장**을 클릭 한 다음 **생성**을 클릭 한 다음 합니다. 이 문서의 목적 우리는 사용 하 여 **기본 규칙 그룹 >for spvms.cloudapp.net**다음 그림에 나와있는 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![Azure의 규칙 그룹 설정](images/RuleGroup.jpg)
  
     ![생성을 선택한 이후의 규칙](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="381bf-187">규칙 그룹을 만드는 방법에 대 한 자세한 내용은 [규칙 그룹 및 규칙을](https://go.microsoft.com/fwlink/p/?LinkId=393128)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="381bf-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="381bf-p110">변경 하려는 규칙 그룹을 클릭 하 고을 변경 하려는 클레임 규칙을 클릭 합니다. 이 문서에서는 다음 그림과 같이 **upn**변수로 **이름** 를 전달 하는 그룹에 클레임 규칙을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![Azure 액세스 제어의 클레임 규칙](images/ClaimRules.jpg)
  
4. <span data-ttu-id="381bf-191">**Upn**라는 기존 클레임 규칙을 삭제 하 고 다음 그림과 같이 **이름에 UPN 클레임** 규칙을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![Azure 액세스 제어의 규칙 설정](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="381bf-193">X.509 인증서를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="381bf-194">토큰 서명을 사용 하 여 X.509 인증서를 구성 하려면 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="381bf-195">액세스 제어 서비스 창에서 **개발** **응용 프로그램의 통합**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="381bf-196">**끝점 참조**Azure 테 넌 트와 연결 된 **Federation.xml** 찾은 다음 브라우저의 주소 표시줄에는 위치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="381bf-197">**Federation.xml** 파일에서 **RoleDescriptor** 섹션을 찾아에서 정보를 복사 된 _<X509Certificate>_ 요소를 다음 그림에 나와있는 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![Federation.xml 파일의 X509 인증서 요소](images/X509Cert.jpg)
  
4. <span data-ttu-id="381bf-199">C: 드라이브의 루트에서\\, **인증서**라는 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="381bf-200">C: 폴더로 x509 인증서 정보를 저장\\인증서 파일 이름으로 **AcsTokenSigning.cer**합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="381bf-201">파일 이름 확장명이.cer 저장 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![X509Certificate 요소를 파일로 저장](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="381bf-203">Windows PowerShell을 사용 하 여 클레임 매핑 만들기</span><span class="sxs-lookup"><span data-stu-id="381bf-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="381bf-204">다음 단계를 사용 하 여 Windows PowerShell을 사용 하 여 클레임 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="381bf-205">다음 멤버 자격이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="381bf-206">SQL Server 인스턴스에 대 한 **securityadmin** 고정 서버 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="381bf-207">업데이트 되는 모든 데이터베이스에 대 한 **db_owner** 고정된 데이터베이스 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="381bf-208">Windows PowerShell cmdlet을 실행 하는 서버에서 administrators 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="381bf-209">관리자는 **Add-spshelladmin** cmdlet를 사용 하 여 SharePoint 2013 cmdlet을 사용 하 여 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="381bf-p111">권한이 없는 경우에 설치 관리자 또는 SQL Server 관리자 권한 요청에 문의 합니다. Windows PowerShell 사용 권한에 대 한 자세한 내용은 [Add-spshelladmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="381bf-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span></span> 
  
1. <span data-ttu-id="381bf-212">**시작** 메뉴에서 **모든 프로그램**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="381bf-213">**Microsoft SharePoint 2013 Products**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="381bf-214">**SharePoint 2013 관리 셸**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="381bf-215">Windows PowerShell 명령 프롬프트에서 클레임 매핑을 만들려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="381bf-216">새 id 공급자에 대 한 SharePoint 구성</span><span class="sxs-lookup"><span data-stu-id="381bf-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="381bf-217">Azure AD에 대 한 새 id 공급자에 SharePoint 설치를 구성 하려면 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="381bf-218">이 절차를 수행하는 사용자 계정이 Farm Administrators SharePoint 그룹의 구성원인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="381bf-219">중앙 관리의 홈페이지에서 **응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="381bf-220">**응용 프로그램 관리** 페이지의 **웹 응용 프로그램** 섹션에서 **웹 응용 프로그램 관리를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="381bf-221">적절한 웹 응용 프로그램을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="381bf-222">리본 메뉴에서 **인증 공급자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="381bf-p112">**영역**영역의 이름을 클릭 합니다. 예: **기본값**입니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="381bf-p113">**인증 편집** 페이지의 **클레임 인증 유형** 섹션에서 **신뢰할 수 있는 Id 공급자**선택 하 고이 문서의 목적을 위해 **ACS 공급자**는 하는 공급자의 이름을 클릭 합니다. **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="381bf-227">다음 그림에는 **신뢰할 수 있는 공급자** 설정을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![웹 앱의 신뢰할 수 있는 공급자 설정](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="381bf-229">사용 권한 설정</span><span class="sxs-lookup"><span data-stu-id="381bf-229">Set the permissions</span></span>

<span data-ttu-id="381bf-230">웹 응용 프로그램에 액세스 권한을 설정 하려면 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="381bf-231">중앙 관리의 홈페이지에서 **응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="381bf-232">**응용 프로그램 관리** 페이지의 **웹 응용 프로그램** 섹션에서 **웹 응용 프로그램 관리를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="381bf-233">적절 한 웹 응용 프로그램을 클릭 한 다음 **사용자 정책**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="381bf-234">**웹 응용 프로그램에 대 한 정책** **사용자 추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="381bf-235">**사용자 추가** 대화 상자에서 **영역**적절 한 영역을 클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="381bf-236">**사용자 추가** 대화 상자에서 typeuser2@blueskyabove.onmicrosoft.com (ACS 공급자).</span><span class="sxs-lookup"><span data-stu-id="381bf-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="381bf-237">**사용 권한** **모든 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="381bf-238">**마침**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="381bf-239">다음 그림에서는 기존 웹 응용 프로그램의 **사용자 추가** 섹션을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![기존 웹 앱에 사용자 추가](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="381bf-241">새 공급자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-241">Verify the new provider</span></span>

<span data-ttu-id="381bf-242">다음 단계를 사용 하 여 새 인증 공급자의 로그인 프롬프트에 나타나는지 확인 하 여 새 id 공급자가 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="381bf-243">다음 그림에 나와있는 것 처럼 **파란색 하늘 위에**라는 새 공급자를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![새 신뢰할 수 있는 공급자를 보여주는 로그인 대화 상자](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="381bf-245">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="381bf-245">Additional resources</span></span>

[<span data-ttu-id="381bf-246">Ws-federation 이해</span><span class="sxs-lookup"><span data-stu-id="381bf-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="381bf-247">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="381bf-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="381bf-248">토론 참여</span><span class="sxs-lookup"><span data-stu-id="381bf-248">Join the discussion</span></span>

|<span data-ttu-id="381bf-249">**문의처**</span><span class="sxs-lookup"><span data-stu-id="381bf-249">**Contact us**</span></span>|<span data-ttu-id="381bf-250">**설명**</span><span class="sxs-lookup"><span data-stu-id="381bf-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="381bf-251">**클라우드 채택 콘텐츠 합니까 필요 합니까?**</span><span class="sxs-lookup"><span data-stu-id="381bf-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="381bf-p114">여러 Microsoft 클라우드 플랫폼 및 서비스에 걸쳐 있는 클라우드 채택에 대 한 콘텐츠를 만듭니다. 보겠습니다 작업을 알 사용해 클라우드 채택 콘텐츠를 구상할 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)에 전자 메일을 발송 하 여 특정 콘텐츠를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="381bf-254">**클라우드 채택 토론에 참가**</span><span class="sxs-lookup"><span data-stu-id="381bf-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="381bf-p115">클라우드 기반 솔루션에 열정을 갖고 인 경우에는 클라우드 채택 자문 보드 (CAAB) Microsoft 콘텐츠 개발자, 업계 전문가는 전세계 어디에서 고객의 더 큰, 생생한 커뮤니티와 연결할에 참가 하는 것이 좋습니다. 참가, Microsoft 기술 커뮤니티의 [CAAB (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 의 구성원으로 자신을 추가 하 고 [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내주시기 합니다. 누구나 [CAAB 블로그 (영문)](https://blogs.technet.com/b/solutions_advisory_board/)에서 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원에 게 새 클라우드 채택 리소스 및 솔루션에 설명 하는 개인 웨 초대장을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="381bf-258">**여기에서 참조 하 여 아트 가져오기**</span><span class="sxs-lookup"><span data-stu-id="381bf-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="381bf-p116">이 문서에서 참조 하는 이미지의 편집 가능한 복사본을 원하는 귀하에 게 보내야 기꺼이 표시 됩니다. URL 및 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)는 이미지의 제목을 포함 하 여 요청을 전자 메일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="381bf-p116">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

