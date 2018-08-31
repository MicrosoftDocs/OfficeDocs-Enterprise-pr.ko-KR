---
title: Office 365 서비스의 IPv6 지원
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: '요약: IPv6 지원 Office 365 government 제품 및 Microsoft Office 365 구성 요소에 설명합니다.'
ms.openlocfilehash: 74752988803728ef4c319e368150b90f7e5d2599
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223130"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="1ea8b-103">Office 365 서비스의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="1ea8b-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="1ea8b-104">**요약**: Microsoft Office 365 구성 요소에서 및 Office 365 government 제품의 IPv6 지원에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="1ea8b-p101">Office 365 IPv6 및 IPv4; 모두를 지원합니다. 그러나 일부 Office 365 기능 i p v 6을 사용할 수 완벽 하 게 됩니다. 즉, Office 365에 연결 하려면 i p v 4와 i p v 6을 모두 사용 해야 합니다. Office 365에 아웃 바운드 트래픽을 필터링 하는 경우 [Office 365 Url 및 IP 주소 범위](https://go.microsoft.com/fwlink/?LinkId=293744)문서의 전체 목록은 Office 365에서 지원 되는 IPv6 주소를 확인할 수 있습니다. 네트워크를 구성 하 고 적절 한 IPv6 주소는 사용할 수를 다운로드할 수 있습니다는 [Office 365 IPv6 테스트 계획](https://go.microsoft.com/fwlink/?LinkId=293447) Microsoft 다운로드 센터에서.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="1ea8b-109">이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="1ea8b-110">Office 365 구독 서비스의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="1ea8b-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="1ea8b-111">Exchange Online 및 IPv6</span><span class="sxs-lookup"><span data-stu-id="1ea8b-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="1ea8b-p102">Exchange Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우 i p v 6 유선 및 무선 네트워크에는 기본적으로 사용 합니다. Exchange Online에 대 한 통신을 제어 하려는 경우 [Office 365 Url 및 IP 주소 범위에서](https://go.microsoft.com/fwlink/?LinkId=293744)IP 주소 범위를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="1ea8b-114">SharePoint Online 및 IPv6</span><span class="sxs-lookup"><span data-stu-id="1ea8b-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="1ea8b-115">**Office 365 Government G1/G3/G4/K1** SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우에 기본적으로 i p v 6을 사용 하 여 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="1ea8b-p103">**공용 다중 테 넌 트 클라우드** Microsoft 사용자의 요청에 SharePoint Online i p v 6을 사용 합니다. CIDR 표기 조직의 DNS 인프라에 대 한 IP 주소를 제공 해야 합니다. 테 넌 트에 대해 사용 하도록 설정 하려면 i p v 6에 대 한 다른 조직에서 이러한 DNS 인프라를 공유할 수 없는 것을 염두에 두십시오. SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우 i p v 6에 사용 하도록 설정, 후에 i p v 6을 사용 하 여 기본적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="1ea8b-p104">SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우 i p v 6 유선 및 무선 네트워크에는 기본적으로 사용 합니다. SharePoint Online에 대 한 통신을 제어 하려는 경우 [Office 365 Url 및 IP 주소 범위에서](https://go.microsoft.com/fwlink/?LinkId=293744)IP 주소 범위를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
 <span data-ttu-id="1ea8b-122">**Office 365 Government G1/G3/G4/K1** SharePoint Online에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우에 기본적으로 i p v 6을 사용 하 여 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="1ea8b-123">비즈니스 및 i p v 6에 대 한 Skype</span><span class="sxs-lookup"><span data-stu-id="1ea8b-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="1ea8b-p105">Microsoft은 Skype 비즈니스에 대 한 i p v 6를 사용 하도록 설정 공용 다중 테 넌 트 클라우드 및 Office 365 Government G1/G3/G4/K1 구독에서 사용자의 요청에 있습니다. 것은 사용 하도록 설정한 후, 비즈니스를 위한 Skype에 연결 하는데 사용할 프로그램이 i p v 6을 지 원하는 경우, 기본적으로 i p v 6을 사용 합니다. 비즈니스를 위한 Skype에 대 한 통신을 제어 하려는 경우 [Office 365 Url 및 IP 주소 범위에서](https://go.microsoft.com/fwlink/?LinkId=293744)IP 주소 범위를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p105">Microsoft will enable IPv6 for Skype for Business at your request in the public multi-tenant cloud and in Office 365 Government G1/G3/G4/K1 subscriptions. After it's enabled, if the program that you use to connect to Skype for Business supports IPv6, it will use IPv6 by default. If you want to control communications to Skype for Business, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
<span data-ttu-id="1ea8b-127">I p v 6을 모든 지역에서 사용할 수 없으면 및 Microsoft를 지금은 테 넌 트에 대 한 활성화 수에 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-127">Please be aware IPv6 is not available in all regions and Microsoft may not be able to activate it for your Tenant at this time.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="1ea8b-128">Exchange Online Protection 및 IPv6</span><span class="sxs-lookup"><span data-stu-id="1ea8b-128">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="1ea8b-p106">Exchange Online Protection (EOP) 전송 계층 보안 프로토콜을 통해 전송 발생 하는 경우 i p v 6을 지원 합니다. EOP 범위에 대 한 [Office 365 Url 및 IP 주소 범위를](https://go.microsoft.com/fwlink/?LinkId=293744)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p106">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="1ea8b-131">Office 365 Government 제품의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="1ea8b-131">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="1ea8b-p107">중역이 부서 및 기관,으로 연방 정부 채택의 인터넷 프로토콜 버전 6 (i p v 6의 수석 정보 관리 책임자에 대 한 Office의 관리 및 예산 (OMB) 매핑합니다 준수 government 제품에 대 한 office 365 IPv6 지원 ) 매핑합니다. [Microsoft Office 365 정부는](https://go.microsoft.com/fwlink/p/?LinkId=325414) 분리 된 커뮤니티 클라우드에서 미국 정부 데이터를 저장 하는 다중 테 넌 트 서비스입니다. 다른 Office 365 제품 처럼 비즈니스, SharePoint Online 및 Office Professional Plus Skype Exchange Online을 포함 하 여 생산성 및 공동 작업 서비스를 제공 합니다. Microsoft Office 365 government 제품 2013에 대해서만 하 고 나중에 적용 됩니다. Office 365 government 제품에 대 한 자세한 내용은 참조 [정부에 대 한 Office 365 발표: A 미국 정부 커뮤니티 클라우드](https://go.microsoft.com/fwlink/p/?LinkId=325414)합니다. 국제 팔 규정 (ITAR)에서 트래픽은 방어 관련 문서 및 서비스는 [미국, 대한민국 군수 목록 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)에서 가져오기 및 내보내기를 제어 하는 미국 정부 규정 집합입니다. 엔터프라이즈용 Microsoft Office 365 보안, 프라이버시 및 규정 준수 요구 사항에 대 한 지원 미국 연방 기관에서 연방 정보 보안 요구 하는 Microsoft 생산성 솔루션에 대 한 전용된 호스팅 서비스를 제공 합니다. 관리 (FISMA) 인증 및 상업용 엔터티 ITAR에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p107">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus. The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="1ea8b-139">IPv6과 Office 365를 사용할 때 고려해야 할 사항</span><span class="sxs-lookup"><span data-stu-id="1ea8b-139">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="1ea8b-p108">I p v 6을 해제 하지 않는 것이 좋습니다. 자세한 내용은 참조 [Microsoft Windows에 대 한 IPv6: 질문과 대답](https://go.microsoft.com/fwlink/p/?LinkId=325418)합니다. 네트워크에서 사용 중인 IP 버전을 확인 하려면 다음 사항을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p108">We recommend that you do not disable IPv6. For more information, see [IPv6 for Microsoft Windows: Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=325418). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="1ea8b-143">명령 프롬프트에서 IPConfig 명령 표시 "IPv6 Address" 또는 "Temporary IPv6 Address" 라는 행을 포함 하는 경우 환경의의 i p v 6을가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-143">If the display of the IPConfig command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="1ea8b-144">모든 IPv6 주소가 "fe80"로 시작 하 "Link-local IPv6 Address" 라는 행에 해당 하는 경우 해당 환경에 i p v 6를 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-144">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="1ea8b-145">다음의 고려 사항이 사용자의 네트워크에 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-145">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="1ea8b-p109">공용 구독 서비스는 IPv6을 통해 신용 카드로 구매할 수 없습니다. 하지만 정부에는 EA(기업 계약) 라이선스가 있으므로 GCC(정부 커뮤니티 클라우드)에는 이 고려 사항이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="1ea8b-148">IPv6은 일부 RMS(Rights Management 서비스) 시나리오를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-148">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="1ea8b-149">BlackBerry i p v 6이 지원 되지 않으므로 i p v 6 BlackBerry® Enterprise Server (BES)를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea8b-149">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

<span data-ttu-id="1ea8b-150">짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="1ea8b-150">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1ea8b-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ea8b-151">See also</span></span>

[<span data-ttu-id="1ea8b-152">Microsoft 기술 백서</span><span class="sxs-lookup"><span data-stu-id="1ea8b-152">Microsoft Technology Position Paper</span></span>](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[<span data-ttu-id="1ea8b-153">TCP/IP v4 및 v6</span><span class="sxs-lookup"><span data-stu-id="1ea8b-153">TCP/IP v4 and v6</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[<span data-ttu-id="1ea8b-154">IPv6 사용 가이드</span><span class="sxs-lookup"><span data-stu-id="1ea8b-154">IPv6 Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=237480)
