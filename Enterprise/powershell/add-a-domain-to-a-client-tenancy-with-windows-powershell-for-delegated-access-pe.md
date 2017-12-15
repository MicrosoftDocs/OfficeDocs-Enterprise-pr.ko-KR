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
ms.custom: DecEntMigration
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "요약:는 Windows PowerShell을 사용 하는 대체 도메인 이름을 기존 고객 테 넌 트에 추가 하려면 Office 365에 대 한 합니다."
ms.openlocfilehash: 182750a5706dbb23c6207c6bd63334cbf2a2a795
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="e366e-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가</span><span class="sxs-lookup"><span data-stu-id="e366e-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="e366e-104">**요약:** Office 365에 대 한 Windows PowerShell을 사용 하 여 기존 고객 테 넌 트에는 대체 도메인 이름을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="e366e-105">만들 수 있으며 연결할 새 도메인 Windows PowerShell을 사용한 고객의 테 넌 시 Office 365 용 Office 365 관리 센터를 사용 하 여 보다 빠르게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Office 365 admin center.</span></span>
  
<span data-ttu-id="e366e-p101">위임 된 액세스 권한 (DAP) 파트너는 신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너입니다. 다른 회사 네트워크 또는 전화 통신 공급자 자주 됩니다. 이러한 번들를 고객에 게 자신의 서비스 제품으로 Office 365 구독 합니다. Office 365 구독을 판매 하는 경우 고객 테에서 thecustomer 테 자신이 관리할 수 있도록 하 고 보고서에 사용 권한은 관리할 대리 (AOBO)를 자동으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p101">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="e366e-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="e366e-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="e366e-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span><span class="sxs-lookup"><span data-stu-id="e366e-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span></span>
  
<span data-ttu-id="e366e-112">다음 정보도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-112">You also need the following information:</span></span>
  
- <span data-ttu-id="e366e-113">고객이 원하는 FQDN(정규화된 도메인 이름)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-113">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="e366e-114">고객의 **테**해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-114">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="e366e-p102">인터넷 도메인 이름 서비스 (DNS) 등록자, GoDaddy와 같은 FQDN 등록 해야 합니다. 공개적으로 도메인 이름 등록 하는 방법에 대 한 자세한 내용은 [도메인 이름을 구입 하는 방법](https://go.microsoft.com/fwlink/p/?LinkId=532541)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e366e-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="e366e-p103">TXT 레코드를 DNS 등록자에 대 한 등록 된 DNS 영역에 추가 하는 방법을 알아야 합니다. TXT 레코드를 추가 하는 방법에 대 한 자세한 내용은 [Office 365에 대 한 모든 DNS 호스팅 공급자에서 만들기 DNS 레코드](https://go.microsoft.com/fwlink/p/?LinkId=532542)를 참조 하십시오. 이러한 절차 하면 작동 하지 않으면 DNS 등록자에 대 한 절차를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p103">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="e366e-120">도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="e366e-120">Create domains</span></span>

 <span data-ttu-id="e366e-p104">고객이 가능성이 게 직접 요청할 기본 싶어하지 않기 때문에 자신의 테 넌 시와 연결할 추가 도메인을 만들 수 있습니다 <domain>. onmicrosoft.com 도메인 세계 자신의 회사 id를 나타내는 기본 것입니다. 이 절차에서는 고객의 테 넌 시와 관련 된 새 도메인 만들기 (영문) 조정과 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e366e-p105">일부 이러한 작업을 수행 하기에 구성 된 로그인 파트너 관리자 계정을 설정 해야 **완전 한 관리를** **지원 회사에 대 한 할당 관리 액세스** 에 대 한 관리자 계정에 대 한 세부 정보에서 볼 수 있는 설정의 Office 365 관리 센터입니다. 파트너 관리자 역할 관리에 대 한 자세한 내용은 참조 하십시오.[파트너: 위임 된 관리 제공](https://go.microsoft.com/fwlink/p/?LinkId=532435)합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p105">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Office 365 admin center. For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="e366e-125">Azure Active Directory에서 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="e366e-125">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="e366e-p106">이 명령은 Azure Active Directory에서 도메인 만들지만 공개적으로 등록 된 도메인과 연결 하지는 않습니다. 기업 위한 Microsoft Office 365에 공개적으로 등록 된 도메인의 소유를 증명 하는 경우를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p106">This command creates the domain in Azure Active Directory but does not associate it with the publically registered domain. That comes when you prove that you own the publically registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="e366e-128">DNS TXT 확인 레코드에 대한 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="e366e-128">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="e366e-p107">Office 365 TXT DNS 확인 레코드에 배치 하는 특정 데이터가 생성 됩니다. 데이터를 가져오려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p107">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="e366e-131">이는 다음과 같은 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-131">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="e366e-p108">공개적으로 등록된 DNS 영역에서 TXT 레코드를 만들려면 이 텍스트가 필요합니다. 텍스트를 복사하고 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p108">You will need this text to create the TXT record in the publically registered DNS zone. Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="e366e-134">TXT 레코드를 공개적으로 등록된 DNS 영역에 추가</span><span class="sxs-lookup"><span data-stu-id="e366e-134">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="e366e-p109">Office 365를 공개적으로 등록 된 도메인 이름에 게 전달 되는 트래픽을 수락를 시작 전에 소유 하 고 도메인에 대 한 관리자 권한이 확인 해야 합니다. 도메인의 TXT 레코드를 작성 하 여 도메인의 소유를 증명 합니다. TXT 레코드는 도메인에 아무 작업도 수행 하지 하 고 도메인의 대화 소유권이 설정 된 후 삭제할 수 있습니다. TXT 레코드를 만들려면 [Office 365에 대 한 모든 DNS 호스팅 공급자에서 만드는 DNS 레코드](https://go.microsoft.com/fwlink/p/?LinkId=532542)에 절차를 따릅니다. 이러한 절차 하면 작동 하지 않으면 DNS 등록자에 대 한 절차를 찾이 필요가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p109">Before Office 365 will start accepting traffic that is directed to the publically registered domain name, you must prove that you own and have administrator permissions to the domain. You prove you own the domain by creating a TXT record in the domain. A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established. To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="e366e-p110">Nslookup 통해 TXT 레코드의 성공적인 생성을 확인 합니다. 다음이 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p110">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="e366e-142">이는 다음과 같은 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-142">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="e366e-143">Office 365의 도메인 소유권 확인</span><span class="sxs-lookup"><span data-stu-id="e366e-143">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="e366e-p111">이 마지막 단계에서는 하면 유효성을 검사 Office 365에 공개적으로 등록 된 도메인의 소유를 합니다. 이 단계를 수행한 후 새 도메인 이름으로 라우팅되는 트래픽을 허용 하지 Office 365 시작 됩니다. 도메인 만들기 및 등록 프로세스를 완료 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-p111">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="e366e-147">이 명령은 출력을 반환하지 않으므로 이 작업을 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-147">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="e366e-148">그러면 다음과 같이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e366e-148">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="e366e-149">See also</span><span class="sxs-lookup"><span data-stu-id="e366e-149">See also</span></span>

#### 

[<span data-ttu-id="e366e-150">파트너에 대 한 도움말</span><span class="sxs-lookup"><span data-stu-id="e366e-150">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

