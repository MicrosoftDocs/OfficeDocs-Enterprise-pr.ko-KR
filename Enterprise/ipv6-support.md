---
title: Office 365 서비스의 IPv6 지원
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: '요약: Microsoft Office 365 구성 요소 및 Office 365 정부 제품의 IPv6 지원에 대해 설명 합니다.'
ms.openlocfilehash: 594f656f8342fa7eddeeea09779cbcf638ae1882
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998110"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="c08f2-103">Office 365 서비스의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="c08f2-103">IPv6 support in Office 365 services</span></span>

<span data-ttu-id="c08f2-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="c08f2-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c08f2-105">Office 365은 IPv6 및 IPv4를 모두 지원 합니다. 그러나 IPv6에서 모든 Office 365 기능이 완전히 사용 하도록 설정 되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-105">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6.</span></span> <span data-ttu-id="c08f2-106">즉, Office 365에 연결 하려면 IPv4 및 IPv6을 모두 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-106">This means that you must use both IPv4 and IPv6 to connect to Office 365.</span></span> <span data-ttu-id="c08f2-107">Office 365에 대 한 아웃 바운드 트래픽을 필터링 하는 경우 Office 365에서 지 원하는 전체 IPv6 주소 목록은 [office 365 url 및 IP 주소 범위](urls-and-ip-address-ranges.md)문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-107">If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span> <span data-ttu-id="c08f2-108">네트워크가 구성 되 고 적절 한 IPv6 주소가 허용 되 면 Microsoft 다운로드 센터에서 [Office 365 IPv6 테스트 계획](https://go.microsoft.com/fwlink/?LinkId=293447) 을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-108">After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="c08f2-109">Office 365 구독 서비스의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="c08f2-109">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="c08f2-110">Exchange Online 및 IPv6</span><span class="sxs-lookup"><span data-stu-id="c08f2-110">Exchange Online and IPv6</span></span>

<span data-ttu-id="c08f2-111">Exchange Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 유선 및 무선 네트워크에서 모두 기본적으로 IPv6을 사용 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-111">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="c08f2-112">Exchange Online에 대 한 통신을 제어 하려면 [Office 365 url 및 ip 주소 범위](urls-and-ip-address-ranges.md)에서 ip 주소 범위를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-112">If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="c08f2-113">SharePoint Online 및 IPv6</span><span class="sxs-lookup"><span data-stu-id="c08f2-113">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="c08f2-114">**Office 365 정부/G3/G4/K1** SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 IPv6 사용이 기본적으로 시도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-114">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="c08f2-115">**공용 다중 테 넌 트 클라우드** Microsoft는 요청 시 SharePoint Online IPv6을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-115">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request.</span></span> <span data-ttu-id="c08f2-116">조직의 DNS 인프라에 대 한 CIDR notated IP 주소를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-116">You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure.</span></span> <span data-ttu-id="c08f2-117">이 DNS 인프라는 테 넌 트에 대해 사용 하도록 설정 하기 위한 IPv6 용 다른 조직에서 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-117">Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant.</span></span> <span data-ttu-id="c08f2-118">IPv6을 사용 하도록 설정한 후에는 SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 기본적으로 IPv6을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-118">After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="c08f2-119">SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 유선 및 무선 네트워크에서 모두 기본적으로 IPv6을 사용 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-119">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="c08f2-120">SharePoint Online에 대 한 통신을 제어 하려면 [Office 365 url 및 ip 주소 범위](urls-and-ip-address-ranges.md)에서 ip 주소 범위를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-120">If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="c08f2-121">**Office 365 정부/G3/G4/K1** SharePoint Online에 연결 하는 데 사용 하는 프로그램이 i p v 6을 지 원하는 경우 IPv6 사용이 기본적으로 시도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-121">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="c08f2-122">비즈니스용 Skype 및 IPv6</span><span class="sxs-lookup"><span data-stu-id="c08f2-122">Skype for Business and IPv6</span></span>

<span data-ttu-id="c08f2-123">알 수 없음 IPv6은 비즈니스용 Skype에서 지원 되지 않으며 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-123">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="c08f2-124">Exchange Online Protection 및 IPv6</span><span class="sxs-lookup"><span data-stu-id="c08f2-124">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="c08f2-125">전송 계층 보안 프로토콜을 통해 전송이 수행 되는 경우 EOP (Exchange Online Protection)에서 IPv6을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-125">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol.</span></span> <span data-ttu-id="c08f2-126">EOP 범위에 대해 [Office 365 url 및 IP 주소 범위](urls-and-ip-address-ranges.md)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-126">For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="c08f2-127">Office 365 정부 제품에 대 한 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="c08f2-127">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="c08f2-128">Office 365 정부에 대 한 IPv6 지원은 경영 부서나 기관에 대 한 정보 관리자 및 IPv6 (인터넷 프로토콜 버전 6) Memorandum의 정부 뿐 아니라 OMB (관리 및 예산) Memorandum를 준수 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-128">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum.</span></span> <span data-ttu-id="c08f2-129">[정부용 Microsoft Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414) 는 분리 된 커뮤니티 클라우드에 미국 정부 데이터를 저장 하는 다중 테 넌 트 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-129">[Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud.</span></span> <span data-ttu-id="c08f2-130">다른 Office 365 제품과 마찬가지로 Exchange Online, 비즈니스용 Skype, SharePoint Online 및 Microsoft 365 앱 for enterprise의 생산성 및 공동 작업 서비스가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-130">Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Microsoft 365 Apps for enterprise.</span></span> 

<span data-ttu-id="c08f2-131">Microsoft Office 365 정부 제품은 2013 이상에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-131">The Microsoft Office 365 government offerings apply only for 2013 and later.</span></span> <span data-ttu-id="c08f2-132">Office 365 정부 제품에 대 한 자세한 내용은 [Microsoft 정부용 office 365 정부: US 정부 커뮤니티 클라우드](https://go.microsoft.com/fwlink/p/?LinkId=325414)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c08f2-132">For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414).</span></span> <span data-ttu-id="c08f2-133">ITAR (무장 규정)의 국제 트래픽은 [미국 군수 목록 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)에 대 한 방어 관련 문서 및 서비스의 내보내기와 가져오기를 제어 하는 미국 정부 규정 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-133">International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="c08f2-134">기업에 대 한 microsoft Office 365는 ITAR에 게 적용 되는 FISMA (연방 정보 보안 관리) 인증 및 상업적 엔터티가 필요한 보안, 개인 정보 보호 및 규정 준수 요구 사항을 지 원하는 Microsoft 생산성 솔루션에 대 한 전용 호스팅 서비스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-134">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="c08f2-135">IPv6 및 Office 365을 사용할 때 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="c08f2-135">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="c08f2-136">IPv6을 사용 하지 않도록 설정 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-136">We recommend that you do not disable IPv6.</span></span> <span data-ttu-id="c08f2-137">자세한 내용은이 [가이드 문서](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c08f2-137">For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users).</span></span> <span data-ttu-id="c08f2-138">네트워크에서 사용 중인 IP 버전을 확인 하려면 다음을 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c08f2-138">To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="c08f2-139">명령 프롬프트에 **IPConfig** 명령 표시에 "ipv6 주소" 또는 "임시 IPv6 주소" 라는 행이 포함 되어 있으면 사용자 환경에 i p v 6이 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-139">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="c08f2-140">모든 IPv6 주소가 "fe80"로 시작 하 고 "링크-로컬 IPv6 주소" 라는 행에 해당 하면 사용자 환경에 i p v 6이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-140">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="c08f2-141">네트워크에 다음과 같은 사항이 적용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-141">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="c08f2-142">공용 구독 서비스는 IPv6을 통한 신용 카드를 사용한 구매를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-142">The public subscription service does not support purchase by credit card over IPv6.</span></span> <span data-ttu-id="c08f2-143">정부에는 EA (엔터프라이즈 계약) 라이선스가 있기 때문에 GCC (정부 커뮤니티 클라우드) 라이센스가 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-143">This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="c08f2-144">일부 RMS (권한 관리 서비스) 시나리오는 IPv6에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-144">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="c08f2-145">BES (BlackBerry는 IPv6을 지원 하지 않기 때문에, IPv6은 BlackBerry®를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-145">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="c08f2-146">Office 365에서 AD FS (Active Directory Federation Services)를 사용 하는 경우에는 IPv6을 사용 하 여 AD FS 네트워크 끝점을 Office 365에 보급 하는 것은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-146">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported.</span></span> <span data-ttu-id="c08f2-147">Exchange Online을 사용 하는 경우 AD FS DNS 항목에 AAAA 레코드를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c08f2-147">You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="c08f2-148">다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="c08f2-148">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c08f2-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c08f2-149">See also</span></span>

<span data-ttu-id="c08f2-150">[IPv6 학습 로드맵](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="c08f2-150">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="c08f2-151">IPv6 생존 가이드</span><span class="sxs-lookup"><span data-stu-id="c08f2-151">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
