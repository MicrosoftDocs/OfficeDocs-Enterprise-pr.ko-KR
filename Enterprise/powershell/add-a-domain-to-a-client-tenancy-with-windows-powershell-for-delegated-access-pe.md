---
title: "DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "요약:Office 365에 대한 Windows PowerShell을 사용하여 대체 도메인 이름을 기존 고객 테넌트에 추가합니다."
ms.openlocfilehash: f99039ffa9f921b33829767a08f33db500a5d2ed
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="e4800-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가</span><span class="sxs-lookup"><span data-stu-id="e4800-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="e4800-104">**요약:** Office 365에 대한 Windows PowerShell을 사용하여 대체 도메인 이름을 기존 고객 테넌트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="e4800-105">Office 365 관리 센터를 사용하는 것보다 빠른Office 365용 Windows PowerShell이 포함된 고객의 테넌트로 새로운 도메인을 만들고 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Office 365 admin center.</span></span>
  
<span data-ttu-id="e4800-p101">DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. 이러한 공급자는 서비스와 Office 365 구독을 통합해서 고객에게 제공합니다. Office 365 구독을 판매하는 경우 고객 테넌트에 대한 AOBO(관리 위임자) 권한이 자동으로 부여되므로 고객 테넌트를 관리하고 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p101">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="e4800-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="e4800-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="e4800-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span><span class="sxs-lookup"><span data-stu-id="e4800-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span></span>
  
<span data-ttu-id="e4800-112">다음 정보도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-112">You also need the following information:</span></span>
  
- <span data-ttu-id="e4800-113">고객이 원하는 FQDN(정규화된 도메인 이름)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-113">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="e4800-114">고객의 **TenantId** 가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-114">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="e4800-p102">FQDN은 GoDaddy 등의 DNS(인터넷 도메인 이름 서비스) 등록 기관으로 등록해야 합니다. 도메인 이름을 공개적으로 등록하는 방법에 대한 자세한 내용은 [도메인 이름 구입 방법](https://go.microsoft.com/fwlink/p/?LinkId=532541)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4800-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="e4800-p103">DNS 등록 기관에 대해 TXT 레코드를 등록된 DNS 영역에 추가하는 방법을 알아야 합니다. TXT 레코드 추가 방법에 대한 자세한 내용은 [원하는 DNS 호스팅 공급자에서 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=532542)를 참조하세요. 이러한 절차가 작동하지 않으면 DNS 등록 기관에 대한 절차를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p103">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="e4800-120">도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="e4800-120">Create domains</span></span>

 <span data-ttu-id="e4800-p104">고객이 기본<domain>.onmicrosoft.com도메인을 회사 ID로 표시할 기본 도메인으로 원하지 않으므로 테넌트와 연결할 추가 도메인 만들기를 문의할 수 있습니다. 이 절차를 통해 고객의 테넌트와 연관된 새 도메인 만들기가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e4800-p105">이러한 일부 작업을 수행하려면 로그인한 파트너 관리자 계정이 Office 365 관리 센터에서 관리 계정의 세부 정보에서 찾을 수 있는 **지원 회사에 대한 할당 관리 액세스**의 **전체 관리**로 설정되어야 합니다. 파트너 관리자 역할 관리에 대한 자세한 내용은 [파트너: 위임된 관리 제안](https://go.microsoft.com/fwlink/p/?LinkId=532435)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4800-p105">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Office 365 admin center. For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="e4800-125">Azure Active Directory에서 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="e4800-125">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="e4800-p106">이 명령은 Azure Active Directory에서 도메인을 만들지만 공개적으로 등록된 도메인으로 연결하지는 않습니다. Microsoft Office 365 엔터프라이즈 에디션에 대해 공개적으로 등록된 도메인을 소유하고 있다고 증명될 때 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p106">This command creates the domain in Azure Active Directory but does not associate it with the publically registered domain. That comes when you prove that you own the publically registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="e4800-128">DNS TXT 확인 레코드에 대한 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="e4800-128">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="e4800-p107">Office 365는 DNS TXT 확인 레코드에 배치해야 하는 특정 데이터를 생성합니다. 데이터를 가져오려면 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p107">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="e4800-131">이는 다음과 같은 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-131">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="e4800-p108">공개적으로 등록된 DNS 영역에서 TXT 레코드를 만들려면 이 텍스트가 필요합니다. 텍스트를 복사하고 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p108">You will need this text to create the TXT record in the publically registered DNS zone. Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="e4800-134">TXT 레코드를 공개적으로 등록된 DNS 영역에 추가</span><span class="sxs-lookup"><span data-stu-id="e4800-134">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="e4800-p109">Office 365가 공개적으로 등록된 도메인 이름으로 연결된 트래픽을 수락하려면 해당 도메인에 대한 관리자 권한을 소유하고 있음을 증명해야 합니다. 도메인에서 TXT 레코드를 생성하여 도메인 소유를 증명합니다. TXT 레코드는 도메인에서 아무 작업도 수행하지 않으며 도메인 소유권이 설정되고 나면 삭제할 수 있습니다. TXT 레코드를 만들려면 [원하는 DNS 호스팅 공급자에서 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=532542)의 절차를 따릅니다. 이러한 절차가 작동하지 않으면 DNS 등록 기관에 대한 절차를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p109">Before Office 365 will start accepting traffic that is directed to the publically registered domain name, you must prove that you own and have administrator permissions to the domain. You prove you own the domain by creating a TXT record in the domain. A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established. To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="e4800-p110">nslookup을 통해 TXT 레코드가 만들어졌음을 확인합니다. 이 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p110">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="e4800-142">이는 다음과 같은 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-142">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="e4800-143">Office 365에서 도메인 소유권 확인</span><span class="sxs-lookup"><span data-stu-id="e4800-143">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="e4800-p111">이 마지막 단계에서 공개적으로 등록된 도메인을 소유하는 Office 365를 확인합니다. 이 단계를 수행한 후 Office 365에서는 새 도메인 이름에 라우팅된 트래픽 수락을 시작합니다. 도메인 만들기 및 등록 프로세스를 완료하려면 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-p111">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="e4800-147">이 명령은 출력을 반환하지 않으므로 이 작업을 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-147">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="e4800-148">그러면 다음과 같이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4800-148">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="e4800-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4800-149">See also</span></span>

#### 

[<span data-ttu-id="e4800-150">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="e4800-150">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

