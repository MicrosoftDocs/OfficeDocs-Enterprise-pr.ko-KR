---
title: Office 365 끝점 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 엔터프라이즈 네트워크는 일부 일반 인터넷 위치에 대 한 액세스를 제한 하거나 많이 backhaul 또는 네트워크 트래픽 처리를 포함 합니다. 되도록 Office 365에 액세스할 수 있는 이러한, 네트워크 및 프록시 관리자 Fqdn, Url의 목록을 관리할 필요가 및 있는 IP 주소와 동일 하 게 네트워크에 있는 컴퓨터에서 Office 365 끝점 목록을 구성 합니다. 직접 경로, 프록시 바이패스 및/또는 방화벽 규칙 및 네트워크 요청은 Office 365에 연결할 수 있도록 PAC 파일에 추가 될 이러한 필요 합니다.
ms.openlocfilehash: a240e3deea512dacd70b377b3d47a7b6f49a235c
ms.sourcegitcommit: 7f1e19fb2d7a448a2dec73d8b2b4b82f851fb5f7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2018
ms.locfileid: "25697974"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="bad84-105">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="bad84-105">Managing Office 365 endpoints</span></span>

<span data-ttu-id="bad84-p102">여러 office 위치와 연결 WAN 있는 대부분의 기업 조직에서는 Office 365 네트워크 연결에 대 한 구성 해야 해야 합니다. 모든 신뢰할 수 있는 방화벽을 통해 직접 Office 365 네트워크 요청 보내기, 모든 추가 패킷 수준 검사를 무시 하거나 처리 하 여 네트워크를 최적화할 수 있습니다. 대기 시간 감소 하 고 경계 용량 요구 사항 감소 합니다. Office 365 사용자에 대 한 최적의 성능을 제공 하는 첫번째 단계는 Office 365 네트워크 트래픽을 식별 합니다. Office 365 네트워크 연결에 대 한 자세한 내용은 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bad84-p102">Most enterprise organizations that have multiple office locations and a connecting WAN will need to need to have configuration for Office 365 network connectivity. You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces latency and reduces your perimeter capacity requirements. Identifying Office 365 network traffic is the first step in providing optimal performance for your Office 365 users. For more information about Office 365 network connectivity, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)</span></span>

<span data-ttu-id="bad84-111">Office 365 네트워크 끝점 및는 [Office 365 IP 주소 및 웹 서비스 URL을](office-365-ip-web-service.md) 사용 하 여 자신에 게 변경 내용에 액세스 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-111">Microsoft recommends you access the Office 365 network endpoints and changes to them using the [Office 365 IP Address and URL Web Services](office-365-ip-web-service.md)</span></span>

<span data-ttu-id="bad84-p103">중요 한 Office 365 네트워크 트래픽, 관리 하는 방법에 관계 없이 Office 365에는 인터넷에 연결을 해야 합니다. [Office 365 IP 주소 및 URL 웹 서비스에 포함 되지 않은 추가 끝점](additional-office365-ip-addresses-and-urls.md) 에 나열 된 연결이 필요한 다른 네트워크 끝점</span><span class="sxs-lookup"><span data-stu-id="bad84-p103">Regardless of how you manage vital Office 365 network traffic, Office 365 requires Internet connectivity. Other network endpoints where connectivity is required are listed at [Additional endpoints not included in the Office 365 IP Address and URL Web service](additional-office365-ip-addresses-and-urls.md)</span></span>

<span data-ttu-id="bad84-p104">Office 365 네트워크 끝점을 사용 하는 방법을 위해 엔터프라이즈 조직 네트워크 아키텍처에 따라 달라 집니다. 이 문서에서는 엔터프라이즈 네트워크 아키텍처 Office 365 IP 주소 및 Url을 통합할 수 있는 여러 방법에 설명 합니다. 신뢰 하도록 요청 하는 네트워크를 선택 하는 것이 가장 편리 방법은 지 원하는 각 사무실 위치에 자동화 된 Office 365 구성 SDWAN 장치를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p104">How you use the Office 365 network endpoints will depend on your enterprise organization network architecture. This article outlines several ways that enterprise network architectures can integrate with Office 365 IP addresses and URLs. The easiest way to choose which network requests to trust is to use SDWAN devices that support automated Office 365 configuration at each of your office locations.</span></span> 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a><span data-ttu-id="bad84-117">중요 한 Office 365 네트워크 트래픽 로컬 분기 탈출에 대 한 SDWAN</span><span class="sxs-lookup"><span data-stu-id="bad84-117">SDWAN for local branch egress of vital Office 365 network traffic</span></span>

<span data-ttu-id="bad84-p105">각 지사 사무실 위치에서 Office 365 최적화 범주 또는 최적화에 대 한 경로 IP 주소로 구성 된 SDWAN 장치는 제공 수 있으며 Microsoft의 네트워크에 직접 범주 허용 수 있습니다. 온-프레미스 데이터 센터 트래픽, 일반 인터넷 웹사이트 트래픽 및 Office 365 기본 범주 트래픽을 포함 하 여 다른 네트워크 트래픽이 더 좋지 않은 네트워크 경계를가 있는 다른 위치로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p105">At each branch office location, you can provide an SDWAN device which is configured to route IP Addresses for Office 365 Optimize category, or Optimize and Allow categories, directly to Microsoft's network. Other network traffic including on-premises datacenter traffic, generic internet web sites traffic, and Office 365 Default category traffic is sent to another location where you have a more substantial network perimeter.</span></span> 

<span data-ttu-id="bad84-p106">Microsoft가 자동된 구성을 사용 하도록 설정 SDWAN 공급자와 함께 작동 합니다. 읽을 수는 [Office 365 네트워킹 파트너 프로그램](office-365-networking-partner-program.md) 에 대 한 추가</span><span class="sxs-lookup"><span data-stu-id="bad84-p106">Microsoft is working with SDWAN providers to enable automated configuration. You can read further about the [Office 365 Networking Partner Program](office-365-networking-partner-program.md)</span></span>

<span data-ttu-id="bad84-122"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="bad84-122"></span></span>
## <a name="use-of-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a><span data-ttu-id="bad84-123">중요 한 Office 365 트래픽의 직접 라우팅에 대 한 PAC 파일 사용</span><span class="sxs-lookup"><span data-stu-id="bad84-123">Use of a PAC file for direct routing of vital Office 365 traffic</span></span>

<span data-ttu-id="bad84-p107">Office 365와 연결 된 지만 제공 되는 IP 주소를 설치 하지 않은 네트워크 요청을 관리 하려면 PAC 또는 WPAD 파일을 사용 합니다. 프록시 또는 경계 장치를 통해 전송 되는 일반적인 네트워크 요청 추가 대기 시간을 발생 시킵니다. SSL 해제 되 고 Inspect 헤드가 가장 큰 세금, 하는 동안 프록시 인증 및 신뢰도 조회 등의 다른 서비스는 사용자 환경의 성능이 저하 될 수 있습니다. 또한 이러한 경계 네트워크 장치는 모든 네트워크 연결 요청을 처리 하는 데 충분 한 용량을 필요 합니다. 직접 Office 365 네트워크 요청에 대 한 프록시 또는 검사 인프라를 우회 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p107">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While SSL Break and Inspect incurs the largest tax, other services such as proxy authentication and reputation lookup can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network connection requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="bad84-129">[PowerShell 갤러리 Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) 은 하는 PowerShell 스크립트를 웹 서비스에서 최신 네트워크 끝점을 읽고 샘플 PAC 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-129">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the web services and creates a sample PAC file.</span></span> 

<span data-ttu-id="bad84-p108">이 스크립트를 다운로드 한 후에 PAC 파일을 생성 하는데 사용할 수 있습니다. 또한 하 여 기존 PAC 파일 관리와 통합 되는 스크립트를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p108">Once you download this script, you can use it to generate a PAC file. You can also modify the script so that it integrates with your existing PAC file management.</span></span> 

<span data-ttu-id="bad84-p109">![방화벽 및 프록시를 통해 Office 365에 연결 합니다. ](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png) 그림 1-단순 엔터프라이즈 네트워크 경계</span><span class="sxs-lookup"><span data-stu-id="bad84-p109">![Connecting to Office 365 through firewalls and proxies.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png) Figure 1 - Simple enterprise network perimeter</span></span>

<span data-ttu-id="bad84-p110">PAC 파일 그림 1에서 포인트 (1)에 컴퓨터에 배포 됩니다. 중요 한 Office 365 네트워크 트래픽을 직접 탈출에 대 한 PAC 파일을 사용할 때에도 네트워크 경계 방화벽에서 이러한 Url 뒤에 IP 주소에 대 한 연결을 허용 해야 합니다. 이 PAC 파일에 지정 된 Office 365의 동일한 끝점 범주에 대 한 IP 주소를 반입 하 여 작업은 수행 하 고 만드는 방화벽 Acl 주소를 기반으로 해당 합니다. 방화벽에는 그림 1의 (3)을 가리키도록 처럼 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p110">The PAC file is deployed to computers at point (1) in Figure 1. When using a PAC file for direct egress of vital Office 365 network traffic, you also need to allow connectivity to the IP addresses behind these URLs on your network perimeter firewall. This is done by fetching the IP addresses for the same Office 365 endpoint categories as specified in the PAC file and creating firewall ACLs based on those addresses. The firewall is shown as point (3) in Figure 1.</span></span> 

<span data-ttu-id="bad84-p111">수행가 프록시 서버를 보내는 범주 끝점 추가 처리를 무시 하도록 프록시 서버에 나열 해야 합니다 모든 필수 허용 최적화 범주 끝점에 대 한 경로 네트워크 트래픽에 대 한 라우팅를 직접만을 선택 하는 경우에 개별적으로 합니다. 예, SSL 나누기 및 Inspect 및 프록시 인증 최적화와 허용 범주 끝점와 호환 되지 않습니다. 프록시 서버는 그림 1에 점 (2)으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p111">Separately if you choose to only do direct routing for the route network traffic for the Optimize category endpoints, any required Allow category endpoints that you send to the proxy server will need to be listed in the proxy server to bypass further processing. For example, SSL break and Inspect and Proxy Authentication are incompatible with both the Optimize and Allow category endpoints. The proxy server is shown as point (2) in Figure 1.</span></span>

<span data-ttu-id="bad84-p112">일반적인 구성은 대상 IP 주소를 프록시 서버에 접속 하는 Office 365 네트워크 트래픽에 대 한 필요 없는 되도록 프록시 서버에서 모든 아웃 바운드 트래픽을 허용 하도록 하는 것입니다. SSL 중단 및 검사를 [사용 하 여 타사 네트워크 장치 또는 Office 365 트래픽 솔루션에서](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)사용 하 여 문제에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p112">The common configuration is to permit all outbound traffic from the proxy server such that destination IP addresses for Office 365 network traffic that hits the proxy server is not required. Read about issues with SSL Break and Inspect at [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).</span></span>

<span data-ttu-id="bad84-143">Get PacFile 스크립트를 생성 하는 PAC 파일에는 다음과 같은 두가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-143">There are two types of PAC files that the Get-PacFile script will generate.</span></span>

|<span data-ttu-id="bad84-144">**종류**</span><span class="sxs-lookup"><span data-stu-id="bad84-144">**Type**</span></span>|<span data-ttu-id="bad84-145">**설명**</span><span class="sxs-lookup"><span data-stu-id="bad84-145">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bad84-146">**1**</span><span class="sxs-lookup"><span data-stu-id="bad84-146">**1**</span></span> <br/> |<span data-ttu-id="bad84-147">프록시 서버에 직접 및 모든 다른 최적화 끝점 트래픽을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-147">Send Optimize endpoint traffic direct and all else to the proxy server.</span></span> <br/> |
|<span data-ttu-id="bad84-148">**2**</span><span class="sxs-lookup"><span data-stu-id="bad84-148">**2**</span></span> <br/> |<span data-ttu-id="bad84-p113">최적화를 보내고 직접 및 프록시 서버를 다른 모든 끝점 트래픽을 허용 합니다. 지원 되는 모든 ExpressRoute ExpressRoute 네트워크 세그먼트 및 프록시 서버를 다른 모든 Office 365 트래픽을 보낼도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p113">Send Optimize and Allow endpoint traffic direct and all else to the proxy server. Can also be used to send all supported ExpressRoute for Office 365 traffic to ExpressRoute network segments and all else to the proxy server.</span></span> <br/> |

<span data-ttu-id="bad84-151">PowerShell 스크립트를 호출의 간단한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-151">Here's a simple example of calling the PowerShell script:</span></span>

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

<span data-ttu-id="bad84-152">스크립트에 전달할 수 있는 매개 변수 수가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-152">There are a number of parameters you can pass to the script:</span></span>

|<span data-ttu-id="bad84-153">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="bad84-153">**Parameter**</span></span>|<span data-ttu-id="bad84-154">**설명**</span><span class="sxs-lookup"><span data-stu-id="bad84-154">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bad84-155">**ClientRequestId**</span><span class="sxs-lookup"><span data-stu-id="bad84-155">**ClientRequestId**</span></span> <br/> |<span data-ttu-id="bad84-156">이 명령은 필요 하 고 전화를 거는 클라이언트 컴퓨터를 나타내는 웹 서비스에 전달 하는 GUID</span><span class="sxs-lookup"><span data-stu-id="bad84-156">This is required and is a GUID passed to the web service that represents the client machine making the call</span></span> <br/> |
|<span data-ttu-id="bad84-157">**Instance**</span><span class="sxs-lookup"><span data-stu-id="bad84-157">**Instance**</span></span> <br/> |<span data-ttu-id="bad84-p114">Worldwide의 기본값은 하는 Office 365 서비스 인스턴스. 또한 웹 서비스로 전달</span><span class="sxs-lookup"><span data-stu-id="bad84-p114">The Office 365 service instance which defaults to Worldwide. Also passed to the web service</span></span> <br/> |
|<span data-ttu-id="bad84-160">**TenantName**</span><span class="sxs-lookup"><span data-stu-id="bad84-160">**TenantName**</span></span> <br/> |<span data-ttu-id="bad84-p115">Office 365 테 넌 트 이름입니다. 웹 서비스에 전달 되 고 일부 Office 365 Url의 대체 가능한 매개 변수로 사용</span><span class="sxs-lookup"><span data-stu-id="bad84-p115">Your Office 365 tenant name. Passed to the web service and used as a replaceable parameter in some Office 365 URLs</span></span> <br/> |
|<span data-ttu-id="bad84-163">**종류**</span><span class="sxs-lookup"><span data-stu-id="bad84-163">**Type**</span></span> <br/> |<span data-ttu-id="bad84-164">생성 하려는 프록시 PAC 파일의 형식</span><span class="sxs-lookup"><span data-stu-id="bad84-164">The type of the proxy PAC file that you want to generate</span></span> <br/> |

<span data-ttu-id="bad84-165">추가 매개 변수를 사용 하 여 PowerShell 스크립트를 호출의 다른 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-165">Here's another example of calling the PowerShell script with additional parameters:</span></span>

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a><span data-ttu-id="bad84-166">Office 365 네트워크 트래픽 처리를 무시 하는 프록시 서버</span><span class="sxs-lookup"><span data-stu-id="bad84-166">Proxy server bypass processing of Office 365 network traffic</span></span> 

<span data-ttu-id="bad84-p116">직접 아웃 바운드 트래픽에 대해 PAC 파일을 사용 하지 않는, 여기서 프록시 서버를 구성 하 여 네트워크 경계에서의 처리를 무시 하려는 계속 합니다. 일부 프록시 서버 공급 업체는 [Office 365 네트워킹 파트너 프로그램](office-365-networking-partner-program.md)에서 설명한 대로이 대 한 자동된 구성이 활성화 합니다. 이 작업을 수동으로 수행 중인 경우 최적화를 얻고 끝점 범주 끝점 데이터는 Office 365 IP 주소와 URL 웹 서비스에서 허용 하 고이 대 한 처리를 사용 하지 않도록 프록시 서버를 구성 해야 합니다. 것 최적화에 대 한 SSL 중단 하 고 검사 및 프록시 인증을 방지 하 고 범주 끝점을 허용 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p116">Where PAC files are not used for direct outbound traffic, you will still want to bypass processing on your network perimeter by configuring your proxy server. Some proxy server vendors have enabled automated configuration of this as described in the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). If you are doing this manually you will need to obtain the Optimize and Allow endpoint category endpoint data from the Office 365 IP Address and URL Web Services and configure your proxy server to bypass processing for these. It is important to avoid SSL Break and Inspect and Proxy Authentication for the Optimize and Allow category endpoints.</span></span> 
  
<span data-ttu-id="bad84-171"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="bad84-171"></span></span>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a><span data-ttu-id="bad84-172">Office 365 IP 주소 및 Url에 대 한 변경 관리</span><span class="sxs-lookup"><span data-stu-id="bad84-172">Change management for Office 365 IP Addresses and URLs</span></span>

<span data-ttu-id="bad84-p117">이 네트워크 경계에 대 한 적절 한 구성을 선택, 외에도 Office 365 끝점에 대 한 변경 관리 프로세스를 채택 하는 중요 합니다. 이러한 끝점을 정기적으로 변경 하 고 변경 내용을 관리 하지 않는 경우 차단 된 사용자와 결국 수 또는 새 IP 후 성능이 저하 된 주소 또는 URL 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p117">In addition to selecting appropriate configuration for your network perimeter, it is critical that you adopt a change management process for Office 365 endpoints. These endpoints change regularly and if you do not manage the changes you can end up with users blocked or with poor performance after a new IP address or URL is added.</span></span> 

<span data-ttu-id="bad84-p118">Office 365 IP 주소 및 Url을 변경 된 각 월의 마지막 날짜 근처 일반적으로 게시 됩니다. 경우에 따라 변경 해당 작동 하 여 일정, 지원, 또는 보안 요구 사항 외부 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p118">Changes to the Office 365 IP addresses and URLs are usually published near the last day of each month. Sometimes a change will be published outside of that schedule due to operational, support, or security requirements.</span></span>

<span data-ttu-id="bad84-p119">IP 주소 또는 URL 추가 되었으므로 조치를 취할 수 해야 변경 내용을 게시 하는 경우 해당 끝점에서 라이브 Office 365 서비스 없을 때까지 변경 내용을 게시는 시간에서 30 일 통지를 받을 예상할 수 있습니다. Microsoft는이 알림 기간에 대 한 것을 목표로, 하지만 해당 되지 않을 수 있습니다 항상 운영으로 인해 가능한, 지원, 또는 보안 요구 사항. 와 같은 연결을 유지 하기 위해 즉각적인 조치가 필요 하지 않은 변경 내용이 Url 또는 IP 주소를 제거 또는 크게 변경 덜 사전 알림을 포함 하지 마십시오. 어떤 알림을 제공 하는 것에 관계 없이 각 변경에 대 한 예상 되는 서비스가 현재 날짜를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p119">When a change is published that requires you to take action because an IP address or URL was added, you should expect to receive 30 days notice from the time we published the change until there is live Office 365 service on that endpoint. Although Microsoft aims for this notification period, it may not always be possible due to operational, support, or security requirements. Changes that do not require immediate action to maintain connectivity, such as removed IP Addresses or URLs or less significant changes, do not include advance notification. Regardless of what notification is provided, we will list the expected service active date for each change.</span></span>

### <a name="change-notification-using-web-services"></a><span data-ttu-id="bad84-181">웹 서비스를 사용 하 여 변경 알림</span><span class="sxs-lookup"><span data-stu-id="bad84-181">Change notification using web services</span></span>

<span data-ttu-id="bad84-p120">Office 365 IP 주소에 사용할 수 있으며 가져올 웹 서비스 URL 변경 알림입니다. Office 365에 연결 하는데 사용 되는 끝점의 버전을 확인 하려면 /version 웹 메서드를 사용 하는 한 시간에 한번 호출 하는 것이 좋습니다. 이 버전에 사용 되 고 있는 있는 버전을 비교할 때 변경 되 면 웹 메서드는 /endpoints에서 최신 끝점 데이터를 가져오고를 선택적으로 /changes에서 차이점을 웹 메서드 가져오는 해야 있습니다. /Endpoints 또는 /changes 웹 메서드를 호출 하면 다음과 같은 발견 하면 버전에 어떠한 변경 되지 않은 경우 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p120">You can use the Office 365 IP Address and URL Web Services to get change notification. We recommend you call the /version web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the /endpoints web method and optionally get the differences from the /changes web method. It is not necessary to call the /endpoints or /changes web methods if there has not been any change to the version you found.</span></span> 

<span data-ttu-id="bad84-186">자세한 내용은 [Office 365 IP 주소 및 URL 웹 서비스를](office-365-ip-web-service.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bad84-186">For more information, see [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-using-rss-feeds"></a><span data-ttu-id="bad84-187">RSS 피드를 사용 하 여 변경 알림</span><span class="sxs-lookup"><span data-stu-id="bad84-187">Change notification using RSS feeds</span></span>

<span data-ttu-id="bad84-p121">Office 365 IP 주소 및 웹 서비스 URL에는 Outlook에서 구독할 수 있는 RSS 피드를 제공 합니다. 각 IP 주소에 대 한 Office 365 서비스 인스턴스 특정 페이지에는 RSS Url 및 Url에 대 한 링크가 있습니다. RSS 피드는 [Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)설명 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p121">The Office 365 IP Address and URL Web Services provide an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance specific pages for the IP addresses and URLs. The RSS feed is further described in the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a><span data-ttu-id="bad84-191">Microsoft 흐름을 사용 하 여 변경 알림 및 승인 검토</span><span class="sxs-lookup"><span data-stu-id="bad84-191">Change notification and approval review using Microsoft Flow</span></span>

<span data-ttu-id="bad84-p122">이해 매달을 통해 제공 되는 네트워크 끝점 변경에 대 한 수동 처리를 필요로 계속 될 수 있습니다. 전자 메일로 알리는 하 고 필요에 따라 Office 365 네트워크 끝점 변경 내용이 있을 때 변경 내용에 대 한 승인 프로세스를 실행 하는 흐름을 만들려는 Microsoft 흐름을 사용할 수 있습니다. 검토를 완료 한 후에 자동으로 방화벽 및 프록시 서버 관리 팀에 변경 내용을 전자 메일 흐름을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p122">We understand that you might still require manual processing for network endpoint changes that come through each month. You can use Microsoft Flow to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.</span></span> 

<span data-ttu-id="bad84-195">Microsoft 흐름 예제 및 [사용 하 여 Microsoft Office 365 IP 주소 및 Url에 대 한 변경 내용에 대 한 전자 메일을 수신 하도록 흐름](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651) 에서 서식 파일에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="bad84-195">Read about the Microsoft Flow sample and template at [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span></span>
  
<span data-ttu-id="bad84-196"><a name="FAQ"> </a></span><span class="sxs-lookup"><span data-stu-id="bad84-196"></span></span>
## <a name="office-365-network-endpoints-faq"></a><span data-ttu-id="bad84-197">Office 365 네트워크 끝점 FAQ</span><span class="sxs-lookup"><span data-stu-id="bad84-197">Office 365 network endpoints FAQ</span></span>

<span data-ttu-id="bad84-198">Office 365 연결 하는 방법에 대 한 관리자 질문과 대답:</span><span class="sxs-lookup"><span data-stu-id="bad84-198">Frequently-asked administrator questions about Office 365 connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="bad84-199">질문을 제출 하는 방법 합니까?</span><span class="sxs-lookup"><span data-stu-id="bad84-199">How do I submit a question?</span></span>

<span data-ttu-id="bad84-p123">문서가 유용한 경우 나타내려면 맨 아래에 링크를 클릭 하 고 추가 질문을 제출 합니다. 피드백을 모니터링 하 고 가장 자주 묻는 질문에 여기 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p123">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="bad84-202">테 넌 트의 위치를 확인 하려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="bad84-202">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="bad84-203">**테 넌 트 위치** 는 가장 사용해 [매핑할 데이터 센터를](http://aka.ms/datamaps)사용 하 여 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-203">**Tenant location** is best determined using our [datacenter map](http://aka.ms/datamaps).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="bad84-204">팔 I 피어 링 적절 하 게 microsoft?</span><span class="sxs-lookup"><span data-stu-id="bad84-204">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="bad84-205">**Peering 위치** 는 [Microsoft와 피어 링](https://www.microsoft.com/peering)에 자세히 설명 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-205">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="bad84-p124">넘는 2500 ISP 피어 링 관계를 가진 전역적으로 및 현재 상태의 70 포인트 우리를 네트워크에서 시작 해야 원활 하 게 수행 합니다. ISP의 피어 링 관계는는 가장 좋은 [방법은 다음 몇가지 예를](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) 정상 상태와 좋지 않습니다 하지 피어 링 손 장점과 단점을 이해 사용해 네트워크로의 확인 몇분 투자 면에 타격 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p124">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="bad84-208">게시 된 목록에 없는 IP 주소에 대 한 네트워크 요청을 참조 하 필요한에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-208">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="bad84-209"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="bad84-209"></span></span>

<span data-ttu-id="bad84-p125">만에 직접 라우팅할 해야 Office 365 서버에 대 한 IP 주소를 제공 합니다. 이 문서가 포괄적인 목록이 모든 IP 주소에 대 한 네트워크 요청을 볼 수 있습니다. Microsoft 및 제 3 자 소유, 게시 되지 않은, IP 주소에 대 한 네트워크 요청을 볼 수 있습니다. 이러한 IP 주소는 동적으로 생성 하거나 관리 변경 될 때 시기 적절 하 게 통지를 방지 하는 방법 (영문). 방화벽 수 없는 이러한 네트워크 요청에 대 한 Fqdn을 기준으로 액세스를 허용 하는 경우는 요청을 관리 하려면 PAC 또는 WPAD 파일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p125">We only provide IP addresses for the Office 365 servers you should route directly to. This isn't a comprehensive list of all IP addresses you'll see network requests for. You will see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="bad84-215">Office 365에서 자세한 정보를 원하는 연관 된 IP 참조?</span><span class="sxs-lookup"><span data-stu-id="bad84-215">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="bad84-216">IP 주소는 [CIDR 계산기 (영문)를](http://jodies.de/ipcalc)사용 하 여 더 큰 게시 된 범위에 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-216">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="bad84-p126">파트너는 [whois 쿼리](https://dnsquery.org/)와 IP를 소유 하는 경우를 참조 합니다. Microsoft 소유 하 고 있으면는 내부 파트너 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p126">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="bad84-p127">인증서를 확인, 브라우저에서 사용 하 여 IP 주소에 연결 \*HTTPS://\<IP_ADDRESS\> \* , 어떤 도메인의 IP 주소와 연결 된 이해 하는 인증서에 나열 된 도메인을 확인 합니다. IP 주소를 소유 하는 Microsoft는 것이 발생 한 경우 Office 365 IP 주소 목록에 없는 가능성이 IP 주소에는 *MSOCDN.NET* 또는 게시 되는 IP 정보 없이 다른 Microsoft 도메인 등 Microsoft CDN와 관련이 있습니다. 도메인 인증서에는 하나 클레임 IP 주소를 나열 하는 위치를 찾으면을 수행 하는 경우 의견을 보내 주십시오.</span><span class="sxs-lookup"><span data-stu-id="bad84-p127">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="bad84-222">예: nsatc.net 또는 Microsoft 도메인 이름에 akadns.net 이름을 나타나는 이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="bad84-222">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="bad84-223"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="bad84-223"></span></span>

<span data-ttu-id="bad84-p128">Office 365 및 기타 Microsoft 서비스 Akamai MarkMonitor 등의 여러 타사 서비스를 사용 하 여 Office 365 환경을 개선 하기 위해. 최상의 경험 하 게 유지 하려면 가능한 경우는 변경할 수 있습니다 이러한 서비스 나중에. 이 과정에서 자주 제 3 자 갖고 있는 도메인, record 또는 IP 주소를 가리키는 CNAME 레코드를 게시 했습니다. 제 3 자 도메인 CDN, 등의 콘텐츠를 호스팅할 수 있습니다 또는 지리적 트래픽 관리 서비스와 같은 서비스를 호스트 될 수 있습니다. 이러한 제 3 자에 대 한 연결을 표시 하는 경우 리디렉션 또는 조회, 클라이언트에서 초기 요청 하지의 형태로 것입니다. 일부 고객은 이러한 형식의 조회 수 있도록 해야 하 고 리디렉션이 명시적으로 잠재적 Fqdn 제 3 자 서비스의 긴 목록을 사용할 수 있습니다를 추가 하지 않고 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p128">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="bad84-p129">서비스의 목록은 언제 든 지 변경 될 수 있습니다. 현재 사용 중인 서비스 중 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p129">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="bad84-p130">[MarkMonitor](https://www.markmonitor.com/) 를 포함 하는 요청을 참조 하는 경우 사용 중인 \* \*. nsatc.net\* 합니다. 이 서비스는 도메인 이름 보호 및 악의적인 동작 보호 하기 위해 모니터링을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p130">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="bad84-p131">[ExactTarget](https://www.marketingcloud.com/) 에 대 한 요청을 참조 하는 경우 사용 중인 \* \*. exacttarget.com\* 합니다. 이 서비스는 전자 메일 링크 관리 및 악의적인 동작에 대 한 모니터링을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p131">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="bad84-p132">[Akamai](https://www.akamai.com/) 사용 되 고 있는 때 다음 Fqdn 중 하나를 포함 하는 요청을 표시 합니다. 이 서비스는 지리적으로 분산 DNS 및 콘텐츠 배달 네트워크 서비스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p132">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a><span data-ttu-id="bad84-238">Office 365에 대 한 가능한 최소 연결을 설치 해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="bad84-238">I have to have the minimum connectivity possible for Office 365</span></span>
<span data-ttu-id="bad84-239"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="bad84-239"></span></span>

<span data-ttu-id="bad84-p133">Office 365가 인터넷을 통해 함수를 작성 하는 서비스 제품군, 안정성과 가용성 약속을 기반으로 사용할 수 있도록 하는 많은 표준 인터넷 서비스. 예, DNS, CRL, Cdn 등의 표준 인터넷 서비스는 대부분의 최신 인터넷 서비스를 사용 하 여 연결할 수 있어야 하는 것 처럼 Office 365를 사용 하 여 연결할 수 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p133">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>

<span data-ttu-id="bad84-p134">Office 365 제품군 주요 서비스 영역으로 분류 됩니다. 연결에 대 한 선택적으로 사용할 수 있는 이러한 이며 모두에 대 한 종속성 이며 항상 필요한 것은 공통 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p134">The Office 365 suite is broken down into major service areas. These can be selectively enabled for connectivity and there is a Common area which is a dependency for all and is always required.</span></span>

|<span data-ttu-id="bad84-244">**서비스 영역**</span><span class="sxs-lookup"><span data-stu-id="bad84-244">**Service Area**</span></span>|<span data-ttu-id="bad84-245">**설명**</span><span class="sxs-lookup"><span data-stu-id="bad84-245">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bad84-246">**Exchange**</span><span class="sxs-lookup"><span data-stu-id="bad84-246">**Exchange**</span></span> <br/> |<span data-ttu-id="bad84-247">Exchange Online 및 Exchange Online 보호</span><span class="sxs-lookup"><span data-stu-id="bad84-247">Exchange Online and Exchange Online Protection</span></span> <br/> |
|<span data-ttu-id="bad84-248">**SharePoint**</span><span class="sxs-lookup"><span data-stu-id="bad84-248">**SharePoint**</span></span> <br/> |<span data-ttu-id="bad84-249">SharePoint Online 및 비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="bad84-249">SharePoint Online and OneDrive for Business</span></span> <br/> |
|<span data-ttu-id="bad84-250">**Skype**</span><span class="sxs-lookup"><span data-stu-id="bad84-250">**Skype**</span></span> <br/> |<span data-ttu-id="bad84-251">비즈니스 및 팀이 Microsoft Skype</span><span class="sxs-lookup"><span data-stu-id="bad84-251">Skype for Business and Microsoft Teams</span></span> <br/> |
|<span data-ttu-id="bad84-252">**일반**</span><span class="sxs-lookup"><span data-stu-id="bad84-252">**Common**</span></span> <br/> |<span data-ttu-id="bad84-253">Office 365 Pro Plus, Office Online 속성, Azure AD와 다른 일반적인 네트워크 끝점</span><span class="sxs-lookup"><span data-stu-id="bad84-253">Office 365 Pro Plus, Office Online, Azure AD and other common network endpoints</span></span> <br/> |

<span data-ttu-id="bad84-p135">기본 인터넷 서비스 외에도 다음과 같은 기능을 통합 하만 사용 되는 타사 서비스가 나와 있습니다. 통합을 위해 필요한 이러한 하는 동안 서비스의 핵심 기능 계속 끝점 액세스할 수 없을 경우 작동 것을 의미 하는 Office 365 끝점을 문서에 선택적으로 표시는 있습니다. 필요한 모든 네트워크 끝점에 게 필요한 특성이 true로 설정 합니다. 선택 사항이 며 모든 네트워크 끝점은 필수 특성이 false로 설정 하 고 메모 특성이 연결을 차단 하는 경우를 예상할 수 누락 된 기능에 자세히 설명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p135">In addition to basic internet services, there are third-party services that are only used to integrate functionality. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible. Any network endpoint which is required will have the required attribute set to true. Any network endpoint which is optional will have the required attribute set to false and the notes attribute will detail the missing functionality you should expect if connectivity is blocked.</span></span>
  
<span data-ttu-id="bad84-258">Office 365를 사용 하려고 하 고 액세스할 수 없는 제 3 자 서비스를 발견 하는 경우 [필수 또는이 문서에서 옵션을 표시 하는 모든 Fqdn 프록시 및 방화벽을 통해 허용 된 확인](urls-and-ip-address-ranges.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-258">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="bad84-259">Microsoft의 소비자 서비스에 대 한 액세스를 차단 어떻게 합니까?</span><span class="sxs-lookup"><span data-stu-id="bad84-259">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="bad84-260"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="bad84-260"></span></span>

<span data-ttu-id="bad84-p136">소비자 서비스에 대 한 액세스를 제한 해야 위험은 사용자가 자신의 차단 소비자 서비스에만 신뢰할 수 있는 방법은 *login.live.com* FQDN 대 한 액세스를 제한 하는 것입니다. 이 FQDN은 다양 한 MSDN, TechNet, 등의 비 소비자 서비스를 포함 하 여 서비스에서 사용 됩니다. 이 FQDN에 대 한 액세스를 제한도 이러한 서비스와 연결 된 네트워크 요청에 대 한 규칙에 대 한 예외를 포함할 필요가 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-p136">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="bad84-264">만으로는 Microsoft 고객 서비스에 대 한 액세스를 차단 차단 되지는 않습니다 기능 네트워크에 다른 사용자에 대 한는 Office 365 테 넌 트 또는 다른 서비스를 사용 하 여 exfiltrate 정보를 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad84-264">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="bad84-265">관련 항목</span><span class="sxs-lookup"><span data-stu-id="bad84-265">Related Topics</span></span>

[<span data-ttu-id="bad84-266">Office 365 IP 주소 및 URL 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="bad84-266">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="bad84-267">Microsoft Azure 데이터 센터 IP 범위</span><span class="sxs-lookup"><span data-stu-id="bad84-267">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="bad84-268">Microsoft 공용 IP 공간</span><span class="sxs-lookup"><span data-stu-id="bad84-268">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="bad84-269">Microsoft Intune에 대 한 네트워크 인프라 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bad84-269">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="bad84-270">Power BI 및 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bad84-270">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="bad84-271">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="bad84-271">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="bad84-272">Office 365 연결에 대한 ExpressRoute 관리</span><span class="sxs-lookup"><span data-stu-id="bad84-272">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="bad84-273">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="bad84-273">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
