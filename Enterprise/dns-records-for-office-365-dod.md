---
title: Office 365 DoD용 DNS 레코드
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: '요약: Office 365 DoD의 DNS 레코드'
hideEdit: true
ms.openlocfilehash: d1f8c82224934f11eddbfa10c5dea7d15cc9e9a2
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339815"
---
# <a name="dns-records-for-office-365-dod"></a><span data-ttu-id="9db86-103">Office 365 DoD용 DNS 레코드</span><span class="sxs-lookup"><span data-stu-id="9db86-103">DNS records for Office 365 DoD</span></span>

<span data-ttu-id="9db86-104">*이 문서는 Office 365 DoD 및 Microsoft 365 DoD에 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="9db86-104">*This article applies to Office 365 DoD and Microsoft 365 DoD*</span></span>

<span data-ttu-id="9db86-105">Office 365 DoD에 대 한 온 보 딩의 일부로, SMTP 및 SIP 도메인을 온라인 서비스 테 넌 트에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-105">As part of onboarding to Office 365 DoD, you will need to add your SMTP and SIP domains to your Online Services tenant.</span></span>  <span data-ttu-id="9db86-106">Azure AD PowerShell에서 New-msoldomain cmdlet을 사용 하 여이 작업을 수행 하거나 [Azure 정부 포털](https://portal.azure.us) 을 사용 하 여 도메인을 추가 하 고 소유권을 증명 하는 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-106">You’ll do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.</span></span>

<span data-ttu-id="9db86-107">테 넌 트에 도메인을 추가 하 고 유효성을 검사 한 후에는 다음 지침을 사용 하 여 서비스에 대 한 적절 한 DNS 레코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-107">Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the services below.</span></span>  <span data-ttu-id="9db86-108">조직에서 인바운드 MX 레코드 및 모든 기존 Exchange 자동 검색 레코드와 관련 하 여 조직의 요구 사항에 맞게 아래 표를 수정 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-108">You may need to modify the below table to fit your organization’s needs with respect to the inbound MX record(s) and any existing Exchange Autodiscover record(s) you have in place.</span></span>  <span data-ttu-id="9db86-109">이러한 DNS 레코드를 메시징 팀에 조정 하 여 전자 메일이 중단 되거나 잘못 배달 되지 않도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-109">We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="9db86-110">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9db86-110">Exchange Online</span></span>

| <span data-ttu-id="9db86-111">종류</span><span class="sxs-lookup"><span data-stu-id="9db86-111">Type</span></span> | <span data-ttu-id="9db86-112">우선 순위</span><span class="sxs-lookup"><span data-stu-id="9db86-112">Priority</span></span> | <span data-ttu-id="9db86-113">호스트 이름</span><span class="sxs-lookup"><span data-stu-id="9db86-113">Host name</span></span> | <span data-ttu-id="9db86-114">주소 또는 값을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-114">Points to address or value</span></span> | <span data-ttu-id="9db86-115">TTL</span><span class="sxs-lookup"><span data-stu-id="9db86-115">TTL</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="9db86-116">MX</span><span class="sxs-lookup"><span data-stu-id="9db86-116">MX</span></span> | <span data-ttu-id="9db86-117">개</span><span class="sxs-lookup"><span data-stu-id="9db86-117">0</span></span> | @ | <span data-ttu-id="9db86-118">*tenant*mail.protection.office365.us (자세한 내용은 아래 참조)</span><span class="sxs-lookup"><span data-stu-id="9db86-118">*tenant*.mail.protection.office365.us (see below for additional details)</span></span> | <span data-ttu-id="9db86-119">1 Hour</span><span class="sxs-lookup"><span data-stu-id="9db86-119">1 Hour</span></span> |
| <span data-ttu-id="9db86-120">TXT</span><span class="sxs-lookup"><span data-stu-id="9db86-120">TXT</span></span> | - | @ | <span data-ttu-id="9db86-121">v = spf1에는 office365-all을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-121">v=spf1 include:spf.protection.office365.us -all</span></span> | <span data-ttu-id="9db86-122">1 Hour</span><span class="sxs-lookup"><span data-stu-id="9db86-122">1 Hour</span></span> |
| <span data-ttu-id="9db86-123">CNAME</span><span class="sxs-lookup"><span data-stu-id="9db86-123">CNAME</span></span> | - | <span data-ttu-id="9db86-124">autodiscover</span><span class="sxs-lookup"><span data-stu-id="9db86-124">autodiscover</span></span> | <span data-ttu-id="9db86-125">autodiscover-dod.office365.us</span><span class="sxs-lookup"><span data-stu-id="9db86-125">autodiscover-dod.office365.us</span></span> | <span data-ttu-id="9db86-126">1 Hour</span><span class="sxs-lookup"><span data-stu-id="9db86-126">1 Hour</span></span> |

### <a name="exchange-autodiscover-record"></a><span data-ttu-id="9db86-127">Exchange 자동 검색 레코드</span><span class="sxs-lookup"><span data-stu-id="9db86-127">Exchange Autodiscover record</span></span>

<span data-ttu-id="9db86-128">Exchange Server 온-프레미스를 사용 하는 경우 Exchange Online으로 마이그레이션하는 동안 기존 레코드를 그대로 두고 마이그레이션을 완료 한 후에 해당 레코드를 업데이트 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-128">If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you have completed your migration.</span></span>

### <a name="exchange-online-mx-record"></a><span data-ttu-id="9db86-129">Exchange Online MX 레코드</span><span class="sxs-lookup"><span data-stu-id="9db86-129">Exchange Online MX Record</span></span>

<span data-ttu-id="9db86-130">허용 도메인에 대 한 MX 레코드 값은 위에서 설명한 표준 *형식: mail.protection.office365.us*, *테 넌* 트를 기본 테 넌 트 이름의 첫 부분으로 교체 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-130">The MX record value for your accepted domains follows a standard format as noted above: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.</span></span>

<span data-ttu-id="9db86-131">예를 들어 테 넌 트 이름이 contoso.onmicrosoft.us 인 경우 MX 레코드의 값으로 **contoso.mail.protection.office365.us** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-131">For example, if your tenant name is contoso.onmicrosoft.us, you’d use **contoso.mail.protection.office365.us** as the value for your MX record.</span></span>

## <a name="skype-for-business-online"></a><span data-ttu-id="9db86-132">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="9db86-132">Skype for Business Online</span></span>

### <a name="cname-records"></a><span data-ttu-id="9db86-133">CNAME 레코드</span><span class="sxs-lookup"><span data-stu-id="9db86-133">CNAME records</span></span>

| <span data-ttu-id="9db86-134">유형</span><span class="sxs-lookup"><span data-stu-id="9db86-134">Type</span></span> | <span data-ttu-id="9db86-135">호스트 이름</span><span class="sxs-lookup"><span data-stu-id="9db86-135">Host name</span></span> | <span data-ttu-id="9db86-136">주소 또는 값을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-136">Points to address or value</span></span> | <span data-ttu-id="9db86-137">TTL</span><span class="sxs-lookup"><span data-stu-id="9db86-137">TTL</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="9db86-138">CNAME</span><span class="sxs-lookup"><span data-stu-id="9db86-138">CNAME</span></span> | <span data-ttu-id="9db86-139">sip</span><span class="sxs-lookup"><span data-stu-id="9db86-139">sip</span></span> | <span data-ttu-id="9db86-140">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="9db86-140">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="9db86-141">1 Hour</span><span class="sxs-lookup"><span data-stu-id="9db86-141">1 Hour</span></span> |
| <span data-ttu-id="9db86-142">CNAME</span><span class="sxs-lookup"><span data-stu-id="9db86-142">CNAME</span></span> | <span data-ttu-id="9db86-143">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="9db86-143">lyncdiscover</span></span> | <span data-ttu-id="9db86-144">webdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="9db86-144">webdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="9db86-145">1 Hour</span><span class="sxs-lookup"><span data-stu-id="9db86-145">1 Hour</span></span> | 

### <a name="srv-records"></a><span data-ttu-id="9db86-146">SRV 레코드</span><span class="sxs-lookup"><span data-stu-id="9db86-146">SRV records</span></span>

| <span data-ttu-id="9db86-147">유형</span><span class="sxs-lookup"><span data-stu-id="9db86-147">Type</span></span> | <span data-ttu-id="9db86-148">서비스</span><span class="sxs-lookup"><span data-stu-id="9db86-148">Service</span></span> | <span data-ttu-id="9db86-149">Protocol(프로토콜)</span><span class="sxs-lookup"><span data-stu-id="9db86-149">Protocol</span></span> | <span data-ttu-id="9db86-150">포트</span><span class="sxs-lookup"><span data-stu-id="9db86-150">Port</span></span> | <span data-ttu-id="9db86-151">가중치</span><span class="sxs-lookup"><span data-stu-id="9db86-151">Weight</span></span> | <span data-ttu-id="9db86-152">우선 순위</span><span class="sxs-lookup"><span data-stu-id="9db86-152">Priority</span></span> | <span data-ttu-id="9db86-153">이름</span><span class="sxs-lookup"><span data-stu-id="9db86-153">Name</span></span> | <span data-ttu-id="9db86-154">Target(대상)</span><span class="sxs-lookup"><span data-stu-id="9db86-154">Target</span></span> | <span data-ttu-id="9db86-155">TTL</span><span class="sxs-lookup"><span data-stu-id="9db86-155">TTL</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="9db86-156">SRV</span><span class="sxs-lookup"><span data-stu-id="9db86-156">SRV</span></span> | <span data-ttu-id="9db86-157">\_sip</span><span class="sxs-lookup"><span data-stu-id="9db86-157">\_sip</span></span> | <span data-ttu-id="9db86-158">\_ls</span><span class="sxs-lookup"><span data-stu-id="9db86-158">\_tls</span></span> | <span data-ttu-id="9db86-159">443</span><span class="sxs-lookup"><span data-stu-id="9db86-159">443</span></span> | <span data-ttu-id="9db86-160">1 </span><span class="sxs-lookup"><span data-stu-id="9db86-160">1</span></span> | <span data-ttu-id="9db86-161">100</span><span class="sxs-lookup"><span data-stu-id="9db86-161">100</span></span> | @ | <span data-ttu-id="9db86-162">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="9db86-162">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="9db86-163">1시간</span><span class="sxs-lookup"><span data-stu-id="9db86-163">1 Hour</span></span> |
| <span data-ttu-id="9db86-164">SRV</span><span class="sxs-lookup"><span data-stu-id="9db86-164">SRV</span></span> | <span data-ttu-id="9db86-165">\_sipfederationtls</span><span class="sxs-lookup"><span data-stu-id="9db86-165">\_sipfederationtls</span></span> | <span data-ttu-id="9db86-166">\_rdp-tcp</span><span class="sxs-lookup"><span data-stu-id="9db86-166">\_tcp</span></span> | <span data-ttu-id="9db86-167">5061</span><span class="sxs-lookup"><span data-stu-id="9db86-167">5061</span></span> | <span data-ttu-id="9db86-168">1 </span><span class="sxs-lookup"><span data-stu-id="9db86-168">1</span></span> | <span data-ttu-id="9db86-169">100</span><span class="sxs-lookup"><span data-stu-id="9db86-169">100</span></span> | @ | <span data-ttu-id="9db86-170">sipfed.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="9db86-170">sipfed.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="9db86-171">1 Hour</span><span class="sxs-lookup"><span data-stu-id="9db86-171">1 Hour</span></span> |

## <a name="additional-dns-records"></a><span data-ttu-id="9db86-172">추가 DNS 레코드</span><span class="sxs-lookup"><span data-stu-id="9db86-172">Additional DNS records</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9db86-173">DNS 영역에 기존 *msoid* CNAME 레코드가 있으면 지금 dns에서 레코드를 **제거** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-173">If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time.</span></span>  <span data-ttu-id="9db86-174">Msoid 레코드는 Microsoft 365 엔터프라이즈 앱 *(이전의 Office 365 ProPlus)* 과 호환 되지 않으며, 정품 인증에 성공 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="9db86-174">The msoid record is incompatible with Microsoft 365 Enterprise Apps *(formerly Office 365 ProPlus)* and will prevent activation from succeeding.</span></span>
