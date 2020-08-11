---
title: DAP 파트너에 대해 Windows PowerShell을 사용 하 여 클라이언트 테 넌 트에 도메인 추가
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: '요약: Microsoft 365 용 PowerShell을 사용 하 여 대체 도메인 이름을 기존 고객 테 넌 트에 추가 합니다.'
ms.openlocfilehash: 8b38caf72db57d5e80f0483062adb3bd2529672b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606484"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="6fc71-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가</span><span class="sxs-lookup"><span data-stu-id="6fc71-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

<span data-ttu-id="6fc71-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="6fc71-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="6fc71-105">Microsoft 365 관리 센터를 사용 하는 것 보다 더 빠른 Microsoft 365 PowerShell을 사용 하 여 고객의 테 넌 시에 새 도메인을 만들고 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-105">You can create and associate new domains with your customer's tenancy with PowerShell for Microsoft 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="6fc71-106">DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="6fc71-107">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="6fc71-108">Microsoft 365 구독을 고객에 게 서비스 제공으로 번들 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="6fc71-109">Microsoft 365 구독을 판매할 때 고객 테 넌 트에 대 한 관리 및 보고를 수행할 수 있도록 사용자에 게 테 넌 트에 대 한 "대신 (AOBO) 사용 권한을 자동으로 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="6fc71-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="6fc71-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="6fc71-111">이 항목의 절차를 수행 하려면 [PowerShell을 사용 하 여 Microsoft 365에 연결](connect-to-office-365-powershell.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-111">The procedures in this topic require you to connect to [Connect to Microsoft 365 with PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="6fc71-112">파트너 테넌트 관리자 자격 증명도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-112">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="6fc71-113">다음 정보도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-113">You also need the following information:</span></span>
  
- <span data-ttu-id="6fc71-114">고객이 원하는 FQDN(정규화된 도메인 이름)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-114">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="6fc71-115">고객의 **TenantId** 가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-115">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="6fc71-p102">FQDN은 GoDaddy 등의 DNS(인터넷 도메인 이름 서비스) 등록 기관으로 등록해야 합니다. 도메인 이름을 공개적으로 등록하는 방법에 대한 자세한 내용은 [도메인 이름 구입 방법](https://go.microsoft.com/fwlink/p/?LinkId=532541)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6fc71-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="6fc71-118">DNS 등록 기관에 대해 TXT 레코드를 등록된 DNS 영역에 추가하는 방법을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-118">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar.</span></span> <span data-ttu-id="6fc71-119">TXT 레코드를 추가 하는 방법에 대 한 자세한 내용은 [DNS 레코드를 추가 하 여 도메인 연결](https://go.microsoft.com/fwlink/p/?LinkId=532542)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6fc71-119">For more information on how to add a TXT record, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="6fc71-120">이러한 절차가 작동하지 않으면 DNS 등록 기관에 대한 절차를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-120">If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="6fc71-121">도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="6fc71-121">Create domains</span></span>

 <span data-ttu-id="6fc71-p104">고객이 기본<domain>.onmicrosoft.com도메인을 회사 ID로 표시할 기본 도메인으로 원하지 않으므로 테넌트와 연결할 추가 도메인 만들기를 문의할 수 있습니다. 이 절차를 통해 고객의 테넌트와 연관된 새 도메인 만들기가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6fc71-124">이러한 작업 중 일부를 수행 하려면 로그인 하는 파트너 관리자 계정을 Microsoft 365 관리 센터의 관리자 계정 세부 정보에 있는 지원 되는 **회사에 대 한 관리 액세스 권한 할당** 에 대 한 **전체 관리** 로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-124">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="6fc71-125">파트너 관리자 역할을 관리 하는 방법에 대 한 자세한 내용은 [파트너: 위임 된 관리 제공](https://go.microsoft.com/fwlink/p/?LinkId=532435)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6fc71-125">For more information on managing partner administrator roles, see [Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="6fc71-126">Azure Active Directory에서 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="6fc71-126">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="6fc71-127">이 명령은 Azure Active Directory에서 도메인을 만들지만 공개적으로 등록된 도메인으로 연결하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-127">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="6fc71-128">이는 공개적으로 등록 된 도메인을 기업에 대 한 Microsoft Microsoft 365에 소유 하 고 있음을 증명할 때 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-128">That comes when you prove that you own the publicly registered domain to Microsoft Microsoft 365 for enterprises.</span></span>
  
```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="6fc71-129">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="6fc71-130">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="6fc71-131">DNS TXT 확인 레코드에 대한 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="6fc71-131">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="6fc71-132">Microsoft 365는 DNS TXT 확인 레코드에 저장 해야 하는 특정 데이터를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-132">Microsoft 365 will generate the specific data that you need to place into the DNS TXT verification record.</span></span> <span data-ttu-id="6fc71-133">데이터를 가져오려면 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-133">To get the data, run this command.</span></span>
  
```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="6fc71-134">이는 다음과 같은 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-134">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="6fc71-135">공개적으로 등록된 DNS 영역에서 TXT 레코드를 만들려면 이 텍스트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-135">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="6fc71-136">텍스트를 복사하고 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-136">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="6fc71-137">TXT 레코드를 공개적으로 등록된 DNS 영역에 추가</span><span class="sxs-lookup"><span data-stu-id="6fc71-137">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="6fc71-138">Microsoft 365에서 공개적으로 등록 된 도메인 이름으로 향하는 트래픽을 수락 하기 전에 사용자가 소유 하 고 있으며 도메인에 대 한 관리자 권한이 있는지 입증 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-138">Before Microsoft 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="6fc71-139">도메인에서 TXT 레코드를 생성하여 도메인 소유를 증명합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-139">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="6fc71-140">TXT 레코드는 도메인에서 아무 작업도 수행하지 않으며 도메인 소유권이 설정되고 나면 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-140">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="6fc71-141">TXT 레코드를 만들려면 DNS 레코드 추가의 절차에 따라 [도메인을 연결](https://go.microsoft.com/fwlink/p/?LinkId=532542)합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-141">To create the TXT records, follow the procedures at [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="6fc71-142">이러한 절차가 작동하지 않으면 DNS 등록 기관에 대한 절차를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-142">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="6fc71-p111">nslookup을 통해 TXT 레코드가 만들어졌음을 확인합니다. 이 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-p111">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```console
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="6fc71-145">이는 다음과 같은 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-145">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a><span data-ttu-id="6fc71-146">Microsoft 365의 도메인 소유권 확인</span><span class="sxs-lookup"><span data-stu-id="6fc71-146">Validate domain ownership in Microsoft 365</span></span>

<span data-ttu-id="6fc71-147">이 마지막 단계에서는 아니라 공개적으로 등록 도메인을 소유 하 고 있음을 Microsoft 365에 대 한 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-147">In this last step, you validate to Microsoft 365 that you own the publically registered domain.</span></span> <span data-ttu-id="6fc71-148">이 단계를 수행한 후에는 Microsoft 365에서 새 도메인 이름으로 라우팅되는 트래픽을 수락 하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-148">After this step, Microsoft 365 will begin accepting traffic routed to the new domain name.</span></span> <span data-ttu-id="6fc71-149">도메인 만들기 및 등록 프로세스를 완료하려면 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-149">To complete the domain creation and registration process, run this command.</span></span> 
  
```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="6fc71-150">이 명령은 출력을 반환하지 않으므로 이 작업을 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-150">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="6fc71-151">그러면 다음과 같이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fc71-151">This will return something like this</span></span>

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

   
## <a name="see-also"></a><span data-ttu-id="6fc71-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6fc71-152">See also</span></span>

#### 

[<span data-ttu-id="6fc71-153">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="6fc71-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

