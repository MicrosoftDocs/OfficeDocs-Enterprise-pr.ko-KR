---
title: Office 365 끝점 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
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
description: 일부 엔터프라이즈 네트워크에서는 일반 인터넷 위치에 대 한 액세스를 제한 하거나, 상당한 백 또는 네트워크 트래픽 처리를 포함 합니다. 이와 같은 네트워크의 컴퓨터가 office 365에 액세스할 수 있도록 하려면 네트워크 및 프록시 관리자가 office 365 끝점 목록을 구성 하는 fqdn, url 및 IP 주소 목록을 관리 해야 합니다. 네트워크 요청이 Office 365에 도달할 수 있도록 하려면 이러한 사항을 직접 경로, 프록시 바이패스 및/또는 방화벽 규칙 및 PAC 파일에 추가 해야 합니다.
ms.openlocfilehash: 469c1fa91fc2695c4175a4eccea26a0ffc46c52a
ms.sourcegitcommit: bc565081b64d374d43b1bf3bb3d92edaaa24e4c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2019
ms.locfileid: "30176748"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="dbfea-105">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="dbfea-105">Managing Office 365 endpoints</span></span>

<span data-ttu-id="dbfea-p102">여러 사무실 위치 및 연결 WAN이 있는 대부분의 엔터프라이즈 조직은 office 365 네트워크 연결에 대 한 구성을 필요로 합니다. 모든 추가 패킷 수준 검사 또는 처리를 무시 하 고 모든 신뢰할 수 있는 Office 365 네트워크 요청을 방화벽을 통해 직접 보내 네트워크를 최적화할 수 있습니다. 이렇게 하면 대기 시간 및 경계 용량 요구 사항이 줄어듭니다. Office 365 네트워크 트래픽은 사용자에 게 최적의 성능을 제공 하기 위한 첫 번째 단계 인지 확인 하는 것이 좋습니다. office 365 네트워크 연결에 대 한 자세한 내용은 [office 365 네트워크 연결 원리](office-365-network-connectivity-principles.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p102">Most enterprise organizations that have multiple office locations and a connecting WAN will need to need configuration for Office 365 network connectivity. You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces latency and your perimeter capacity requirements. Identifying Office 365 network traffic is the first step in providing optimal performance for your users. For more information about Office 365 network connectivity, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)</span></span>

<span data-ttu-id="dbfea-111">office [365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md) 를 사용 하 여 office 365 네트워크 끝점과 변경 사항에 액세스 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-111">Microsoft recommends you access the Office 365 network endpoints and changes to them using the [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md)</span></span>

<span data-ttu-id="dbfea-p103">중요 한 office 365 네트워크 트래픽을 관리 하는 방법에 관계 없이 office 365을 사용 하려면 인터넷에 연결 해야 합니다. 연결이 필요한 기타 네트워크 끝점은 [Office 365 IP 주소 및 URL 웹 서비스에 포함 되지 않은 추가 끝점](additional-office365-ip-addresses-and-urls.md) 에 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p103">Regardless of how you manage vital Office 365 network traffic, Office 365 requires Internet connectivity. Other network endpoints where connectivity is required are listed at [Additional endpoints not included in the Office 365 IP Address and URL Web service](additional-office365-ip-addresses-and-urls.md)</span></span>

<span data-ttu-id="dbfea-p104">Office 365 네트워크 끝점을 사용 하는 방법은 엔터프라이즈 조직 네트워크 아키텍처에 따라 달라 집니다. 이 문서에서는 엔터프라이즈 네트워크 아키텍처에서 Office 365 IP 주소 및 url과 통합할 수 있는 여러 가지 방법을 간략하게 설명 합니다. 신뢰할 네트워크 요청을 선택할 수 있는 가장 쉬운 방법은 각 사무실 위치에서 자동 Office 365 구성을 지 원하는 sdwan 장치를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p104">How you use the Office 365 network endpoints will depend on your enterprise organization network architecture. This article outlines several ways that enterprise network architectures can integrate with Office 365 IP addresses and URLs. The easiest way to choose which network requests to trust is to use SDWAN devices that support automated Office 365 configuration at each of your office locations.</span></span>

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a><span data-ttu-id="dbfea-117">중요 한 Office 365 네트워크 트래픽의 로컬 분기 송신을 위한 sdwan</span><span class="sxs-lookup"><span data-stu-id="dbfea-117">SDWAN for local branch egress of vital Office 365 network traffic</span></span>

<span data-ttu-id="dbfea-p105">각 지사 위치에서 office 365 for endpoints 범주에 대 한 트래픽을 라우팅하도록 구성 된 sdwan 장치를 제공 하거나, 범주를 Microsoft의 네트워크로 직접 최적화 하 고 허용할 수 있습니다. 온-프레미스 데이터 센터 트래픽, 일반 인터넷 웹 사이트 트래픽 및 Office에 대 한 트래픽 365 기본 범주 끝점을 포함 하는 기타 네트워크 트래픽은 더 많은 네트워크 경계를 가진 다른 위치로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p105">At each branch office location, you can provide an SDWAN device that is configured to route traffic for Office 365 Optimize category of endpoints, or Optimize and Allow categories, directly to Microsoft's network. Other network traffic including on-premises datacenter traffic, general Internet web sites traffic, and traffic to Office 365 Default category endpoints is sent to another location where you have a more substantial network perimeter.</span></span>

<span data-ttu-id="dbfea-p106">Microsoft는 sdwan 공급자와 협력 하 여 자동화 된 구성을 사용 하도록 설정 합니다. 자세한 내용은 [Office 365 네트워킹 파트너 프로그램](office-365-networking-partner-program.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p106">Microsoft is working with SDWAN providers to enable automated configuration. For more information, see [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span>

<span data-ttu-id="dbfea-122"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-122"></span></span>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a><span data-ttu-id="dbfea-123">중요 한 Office 365 트래픽을 직접 라우팅하기 위해 PAC 파일 사용</span><span class="sxs-lookup"><span data-stu-id="dbfea-123">Use a PAC file for direct routing of vital Office 365 traffic</span></span>

<span data-ttu-id="dbfea-p107">PAC 또는 WPAD 파일을 사용 하 여 Office 365에 연결 되어 있지만 IP 주소가 없는 네트워크 요청을 관리 합니다. 프록시 또는 경계 장치를 통해 전송 되는 일반적인 네트워크 요청에 대 한 대기 시간이 길어집니다. SSL 침입 및 검사에서는 가장 큰 대기 시간을 만들기 때문에 프록시 인증 및 신뢰도 조회와 같은 다른 서비스를 사용 하면 성능이 저하 되 고 사용자 환경이 잘못 될 수 있습니다. 또한 이러한 경계 네트워크 장치는 모든 네트워크 연결 요청을 처리 하기에 충분 한 용량을 필요로 합니다. 직접적인 Office 365 네트워크 요청에 대해 프록시 또는 검사 장치를 바이패스 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p107">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address. Typical network requests that are sent through a proxy or perimeter device increase latency. While SSL Break and Inspect creates the largest latency, other services such as proxy authentication and reputation lookup can cause poor performance and a bad user experience. Additionally, these perimeter network devices need enough capacity to process all of the network connection requests. We recommend bypassing your proxy or inspection devices for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="dbfea-p108">[powershell Gallery PacFile](https://www.powershellgallery.com/packages/Get-PacFile) 는 Office 365 IP 주소 및 URL 웹 서비스에서 최신 네트워크 끝점을 읽고 샘플 PAC 파일을 만드는 PowerShell 스크립트입니다. 기존 PAC 파일 관리와 통합 되도록 스크립트를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p108">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL Web service and creates a sample PAC file. You can modify the script so that it integrates with your existing PAC file management.</span></span>

![방화벽 및 프록시를 통해 Office 365에 연결](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

<span data-ttu-id="dbfea-132">**그림 1-간단한 엔터프라이즈 네트워크 경계**</span><span class="sxs-lookup"><span data-stu-id="dbfea-132">**Figure 1 - Simple enterprise network perimeter**</span></span>

<span data-ttu-id="dbfea-p109">PAC 파일은 그림 1의 포인트 1에 있는 웹 브라우저에 배포 됩니다. 중요 한 Office 365 네트워크 트래픽을 직접 송신 하기 위해 PAC 파일을 사용 하는 경우에는 네트워크 경계 방화벽에서 이러한 url 뒤에 오는 IP 주소에 대 한 연결도 허용 해야 합니다. 이 작업은 PAC 파일에 지정 된 것과 같은 Office 365 끝점 범주에 대 한 IP 주소를 가져오고 해당 주소를 기반으로 방화벽 acl을 만드는 방법으로 수행 됩니다. 방화벽은 그림 1의 포인트 3입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p109">The PAC file is deployed to web browsers at point 1 in Figure 1. When using a PAC file for direct egress of vital Office 365 network traffic, you also need to allow connectivity to the IP addresses behind these URLs on your network perimeter firewall. This is done by fetching the IP addresses for the same Office 365 endpoint categories as specified in the PAC file and creating firewall ACLs based on those addresses. The firewall is point 3 in Figure 1.</span></span>

<span data-ttu-id="dbfea-p110">별도로 범주 끝점을 최적화 하기 위해 직접 라우팅만 선택한 경우 프록시 서버에 보내는 모든 필수 허용 범주 끝점이 프록시 서버에 나열 되어야 더 이상 처리 되지 않습니다. 예를 들어 SSL 중단 및 검사 및 프록시 인증은 최적화 및 허용 범주 끝점과 모두 호환 되지 않습니다. 프록시 서버는 그림 1의 포인트 2입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p110">Separately if you choose to only do direct routing for the Optimize category endpoints, any required Allow category endpoints that you send to the proxy server will need to be listed in the proxy server to bypass further processing. For example, SSL break and Inspect and Proxy Authentication are incompatible with both the Optimize and Allow category endpoints. The proxy server is point 2 in Figure 1.</span></span>

<span data-ttu-id="dbfea-p111">일반적인 구성은 프록시 서버에 방문 하는 Office 365 네트워크 트래픽에 대 한 대상 IP 주소에 대 한 프록시 서버의 모든 아웃 바운드 트래픽을 처리 하지 않고 허용 하는 것입니다. SSL 중단 및 검사와 관련 된 문제에 대 한 자세한 내용은 [Office 365 트래픽에 타사 네트워크 장치 또는 솔루션 사용](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p111">The common configuration is to permit without processing all outbound traffic from the proxy server for the destination IP addresses for Office 365 network traffic that hits the proxy server. For information about issues with SSL Break and Inspect, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).</span></span>

<span data-ttu-id="dbfea-142">PacFile 스크립트는 두 가지 유형의 PAC 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-142">There are two types of PAC files that the Get-PacFile script will generate.</span></span>

|<span data-ttu-id="dbfea-143">**종류**</span><span class="sxs-lookup"><span data-stu-id="dbfea-143">**Type**</span></span>|<span data-ttu-id="dbfea-144">**설명**</span><span class="sxs-lookup"><span data-stu-id="dbfea-144">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="dbfea-145">**개**</span><span class="sxs-lookup"><span data-stu-id="dbfea-145">**1**</span></span> <br/> |<span data-ttu-id="dbfea-146">끝점 트래픽 다이렉트 및 다른 모든 항목을 프록시 서버로 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-146">Send Optimize endpoint traffic direct and everything else to the proxy server.</span></span> <br/> |
|<span data-ttu-id="dbfea-147">**2**</span><span class="sxs-lookup"><span data-stu-id="dbfea-147">**2**</span></span> <br/> |<span data-ttu-id="dbfea-p112">끝점 트래픽 직접 및 프록시 서버에 대 한 모든 작업을 최적화 하 고 허용 합니다. 이 유형을 사용 하 여 모든 지원 되는 모든 방법 Office 365 트래픽을가을 수 있는 네트워크 세그먼트 및 다른 모든 대상에 프록시 서버로 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p112">Send Optimize and Allow endpoint traffic direct and everything else to the proxy server. This type can also be used to send all supported ExpressRoute for Office 365 traffic to ExpressRoute network segments and everything else to the proxy server.</span></span> <br/> |

<span data-ttu-id="dbfea-150">다음은 PowerShell 스크립트를 호출 하는 간단한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-150">Here's a simple example of calling the PowerShell script:</span></span>

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

<span data-ttu-id="dbfea-151">스크립트에 전달할 수 있는 매개 변수에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-151">There are a number of parameters you can pass to the script:</span></span>

|<span data-ttu-id="dbfea-152">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="dbfea-152">**Parameter**</span></span>|<span data-ttu-id="dbfea-153">**설명**</span><span class="sxs-lookup"><span data-stu-id="dbfea-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="dbfea-154">**ClientRequestId**</span><span class="sxs-lookup"><span data-stu-id="dbfea-154">**ClientRequestId**</span></span> <br/> |<span data-ttu-id="dbfea-155">이는 필수 사항이 며 호출을 수행 하는 클라이언트 컴퓨터를 나타내는 웹 서비스에 전달 되는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-155">This is required and is a GUID passed to the web service that represents the client machine making the call.</span></span> <br/> |
|<span data-ttu-id="dbfea-156">**Instance**</span><span class="sxs-lookup"><span data-stu-id="dbfea-156">**Instance**</span></span> <br/> |<span data-ttu-id="dbfea-p113">기본적으로 국가별 설정에 해당 하는 Office 365 서비스 인스턴스입니다. 웹 서비스에도 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p113">The Office 365 service instance which defaults to Worldwide. Also passed to the web service.</span></span> <br/> |
|<span data-ttu-id="dbfea-159">**TenantName**</span><span class="sxs-lookup"><span data-stu-id="dbfea-159">**TenantName**</span></span> <br/> |<span data-ttu-id="dbfea-p114">Office 365 테 넌 트 이름입니다. 웹 서비스로 전달 되 고 일부 Office 365 url에서 교체 가능한 매개 변수로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p114">Your Office 365 tenant name. Passed to the web service and used as a replaceable parameter in some Office 365 URLs.</span></span> <br/> |
|<span data-ttu-id="dbfea-162">**유형**</span><span class="sxs-lookup"><span data-stu-id="dbfea-162">**Type**</span></span> <br/> |<span data-ttu-id="dbfea-163">생성 하려는 프록시 PAC 파일의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-163">The type of the proxy PAC file that you want to generate.</span></span> <br/> |

<span data-ttu-id="dbfea-164">다음은 추가 매개 변수를 사용 하 여 PowerShell 스크립트를 호출 하는 또 다른 예입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-164">Here's another example of calling the PowerShell script with additional parameters.</span></span>

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a><span data-ttu-id="dbfea-165">프록시 서버 바이패스 Office 365 네트워크 트래픽 처리</span><span class="sxs-lookup"><span data-stu-id="dbfea-165">Proxy server bypass processing of Office 365 network traffic</span></span>

<span data-ttu-id="dbfea-p115">직접 아웃 바운드 트래픽에 대해 PAC 파일을 사용 하지 않는 경우에도 프록시 서버를 구성 하 여 네트워크 경계에서 처리를 우회 하려고 합니다. 일부 프록시 서버 공급 업체에서는 [Office 365 네트워킹 파트너 프로그램](office-365-networking-partner-program.md)에 설명 된 것 처럼 자동화 된 구성을 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p115">Where PAC files are not used for direct outbound traffic, you still want to bypass processing on your network perimeter by configuring your proxy server. Some proxy server vendors have enabled automated configuration of this as described in the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span>

<span data-ttu-id="dbfea-p116">이 작업을 수동으로 수행 하는 경우 Office 365 IP 주소 및 URL 웹 서비스에서 최적화 및 허용 끝점 범주 데이터를 가져오고 이러한 항목에 대 한 처리를 우회 하도록 프록시 서버를 구성 해야 합니다. 최적화 및 허용 범주 끝점에 대해 SSL 중단 및 검사 및 프록시 인증을 방지 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p116">If you are doing this manually you will need to get the Optimize and Allow endpoint category data from the Office 365 IP Address and URL Web Service and configure your proxy server to bypass processing for these. It is important to avoid SSL Break and Inspect and Proxy Authentication for the Optimize and Allow category endpoints.</span></span>
  
<span data-ttu-id="dbfea-170"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-170"></span></span>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a><span data-ttu-id="dbfea-171">Office 365 IP 주소 및 url에 대 한 변경 관리</span><span class="sxs-lookup"><span data-stu-id="dbfea-171">Change management for Office 365 IP addresses and URLs</span></span>

<span data-ttu-id="dbfea-p117">네트워크 경계에 적합 한 구성을 선택 하는 것 외에도 Office 365 끝점에 대 한 변경 관리 프로세스를 채택 하는 것이 중요 합니다. 이러한 끝점은 정기적으로 변경 되며, 변경 사항을 관리 하지 않으면 새 IP 주소 또는 URL을 추가한 후 사용자가 차단 되거나 성능 저하로 인해 완료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p117">In addition to selecting appropriate configuration for your network perimeter, it is critical that you adopt a change management process for Office 365 endpoints. These endpoints change regularly and if you do not manage the changes, you can end up with users blocked or with poor performance after a new IP address or URL is added.</span></span>

<span data-ttu-id="dbfea-p118">Office 365 IP 주소 및 url에 대 한 변경 내용은 보통 매월 말일에 게시 됩니다. 운영, 지원 또는 보안 요구 사항으로 인해 변경 내용이 해당 일정 외부에 게시 되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p118">Changes to the Office 365 IP addresses and URLs are usually published near the last day of each month. Sometimes a change will be published outside of that schedule due to operational, support, or security requirements.</span></span>

<span data-ttu-id="dbfea-p119">IP 주소 또는 URL이 추가 되어 작업을 수행 해야 하는 변경 내용이 게시 되 면 해당 끝점에 Office 365 서비스가 있을 때까지 변경 내용을 게시할 때까지 30 일 동안 알림이 표시 됩니다. 이 알림 기간을 목표로 하기는 하지만 운영, 지원 또는 보안 요구 사항으로 인해 항상 가능 하지 않을 수 있습니다. 연결을 유지 하기 위해 즉시 작업을 수행 하지 않아도 되는 변경 사항 (예: 제거 된 IP 주소 또는 url 또는 덜 중요 한 변경)에는 사전 알림이 포함 되지 않습니다. 제공 되는 알림과 관계 없이 각 변경에 대해 예상 되는 서비스 활성 날짜가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p119">When a change is published that requires you to act because an IP address or URL was added, you should expect to receive 30 days notice from the time we publish the change until there is an Office 365 service on that endpoint. Although we aim for this notification period, it may not always be possible due to operational, support, or security requirements. Changes that do not require immediate action to maintain connectivity, such as removed IP addresses or URLs or less significant changes, do not include advance notification. Regardless of what notification is provided, we list the expected service active date for each change.</span></span>

### <a name="change-notification-using-the-web-service"></a><span data-ttu-id="dbfea-180">웹 서비스를 사용 하 여 알림 변경</span><span class="sxs-lookup"><span data-stu-id="dbfea-180">Change notification using the Web Service</span></span>

<span data-ttu-id="dbfea-p120">Office 365 IP 주소 및 URL 웹 서비스를 사용 하 여 변경 알림을 가져올 수 있습니다. Office 365에 연결 하는 데 사용 하는 끝점의 버전을 확인 하려면 한 시간 한 번 **/version** 웹 메서드를 호출 하는 것이 좋습니다. 사용 중인 버전과 비교 하 여이 버전이 변경 되는 경우에는 **/pndweb** 메서드에서 최신 끝점 데이터를 가져오고 필요에 따라 **/changes** 웹 메서드를 통해 차이를 가져와야 합니다. 찾은 버전을 변경 하지 않은 경우에는 **/tendpoints** 또는 **/dweb** 메서드를 호출 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p120">You can use the Office 365 IP Address and URL Web Service to get change notification. We recommend you call the **/version** web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the **/endpoints** web method and optionally get the differences from the **/changes** web method. It is not necessary to call the **/endpoints** or **/changes** web methods if there has not been any change to the version you found.</span></span>

<span data-ttu-id="dbfea-185">자세한 내용은 [Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbfea-185">For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-using-rss-feeds"></a><span data-ttu-id="dbfea-186">RSS 피드를 사용 하 여 알림 변경</span><span class="sxs-lookup"><span data-stu-id="dbfea-186">Change notification using RSS feeds</span></span>

<span data-ttu-id="dbfea-p121">Office 365 IP 주소 및 URL 웹 서비스는 Outlook에서 구독할 수 있는 RSS 피드를 제공 합니다. IP 주소 및 url에 대 한 각 Office 365 서비스 인스턴스별 페이지에는 RSS url에 대 한 링크가 있습니다. 자세한 내용은 [Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p121">The Office 365 IP Address and URL Web Service provides an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance-specific pages for the IP addresses and URLs. For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a><span data-ttu-id="dbfea-190">Microsoft 흐름을 사용 하 여 알림 및 승인 검토 변경</span><span class="sxs-lookup"><span data-stu-id="dbfea-190">Change notification and approval review using Microsoft Flow</span></span>

<span data-ttu-id="dbfea-p122">각 월별로 제공 되는 네트워크 끝점 변경에 대 한 수동 처리가 여전히 필요할 수 있다는 것을 이해 하 고 있습니다. Microsoft 흐름을 사용 하 여 전자 메일로 알리는 흐름을 만들고 Office 365 네트워크 끝점에 변경 내용이 있을 때 변경 내용에 대 한 승인 프로세스를 선택적으로 실행할 수 있습니다. 검토가 완료 되 면 흐름에서 방화벽 및 프록시 서버 관리 팀에 변경 내용을 자동으로 전자 메일로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p122">We understand that you might still require manual processing for network endpoint changes that come through each month. You can use Microsoft Flow to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.</span></span>

<span data-ttu-id="dbfea-194">microsoft flow 샘플과 템플릿에 대 한 자세한 내용은 [Office 365 IP 주소 및 url 변경에 대 한 전자 메일을 받으려면 microsoft flow 사용](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbfea-194">For information about a Microsoft Flow sample and template, see [Use Microsoft Flow to receive an email for changes to Office 365 IP addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span></span>
  
<span data-ttu-id="dbfea-195"><a name="FAQ"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-195"></span></span>
## <a name="office-365-network-endpoints-faq"></a><span data-ttu-id="dbfea-196">Office 365 네트워크 끝점 FAQ</span><span class="sxs-lookup"><span data-stu-id="dbfea-196">Office 365 network endpoints FAQ</span></span>

<span data-ttu-id="dbfea-197">Office 365 연결에 대 한 자주 묻는 관리자의 질문:</span><span class="sxs-lookup"><span data-stu-id="dbfea-197">Frequently-asked administrator questions about Office 365 connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="dbfea-198">질문을 제출 하려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="dbfea-198">How do I submit a question?</span></span>

<span data-ttu-id="dbfea-p123">아래쪽에 있는 링크를 클릭 하 여 기사가 도움이 되었는지 여부를 지정 하 고 추가 질문을 제출 합니다. 의견을 모니터링 하 고 여기에서 가장 자주 묻는 질문을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p123">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="dbfea-201">테 넌 트의 위치를 확인 하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="dbfea-201">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="dbfea-202">[데이터 센터 맵을](http://aka.ms/datamaps)사용 하 여 **테 넌 트 위치** 를 결정 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-202">**Tenant location** is best determined using our [datacenter map](http://aka.ms/datamaps).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="dbfea-203">Microsoft와의 피어 링이 적절 합니까?</span><span class="sxs-lookup"><span data-stu-id="dbfea-203">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="dbfea-204">**피어 링 위치** 는 [Microsoft와의 피어 링](https://www.microsoft.com/peering)에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-204">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="dbfea-p124">2500 개 이상의 ISP 피어 링 관계를 전역적으로 또는 70 지점에 연결 하는 경우 네트워크에서 우리에 게 가져오는 것이 원활 해야 합니다. ISP의 피어 링 관계가 가장 최적이 되도록 몇 분 정도의 시간이 소요 되는 것을 방지할 수는 있지만,이에 대 한 [몇 가지 예는](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) 네트워크에 대 한 좋은 피어 링 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p124">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) of good and not so good peering hand-offs to our network.</span></span>
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="dbfea-207">게시 된 목록에 없는 IP 주소에 대 한 네트워크 요청이 표시 됨, 액세스 권한을 제공 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="dbfea-207">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="dbfea-208"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-208"></span></span>

<span data-ttu-id="dbfea-p125">여기서는로 직접 라우팅하는 Office 365 서버에 대 한 IP 주소만 제공 합니다. 이는 네트워크 요청이 표시 되는 모든 IP 주소의 전체 목록이 아닙니다. Microsoft 및 타사 소유, 게시 되지 않은 IP 주소에 대 한 네트워크 요청이 표시 됩니다. 이러한 IP 주소는 변경 시 시기 적절 한 알림을 방지 하는 방식으로 동적으로 생성 되거나 관리 됩니다. 방화벽에서 이러한 네트워크 요청의 fqdn을 기반으로 액세스를 허용할 수 없으면 PAC 또는 WPAD 파일을 사용 하 여 요청을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p125">We only provide IP addresses for the Office 365 servers you should route directly to. This isn't a comprehensive list of all IP addresses you'll see network requests for. You will see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="dbfea-214">자세한 내용을 보려는 Office 365와 연결 된 IP를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbfea-214">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="dbfea-215">[CIDR 계산기](http://jodies.de/ipcalc)를 사용 하 여 IP 주소가 보다 큰 게시 범위에 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-215">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="dbfea-p126">파트너가 [whois 쿼리](https://dnsquery.org/)를 사용 하 여 IP를 소유 하는지 확인 합니다. 해당 Microsoft가 소유 하 고 있으면 내부 파트너가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p126">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="dbfea-p127">인증서 확인 브라우저에서 \*HTTPS://\<IP_ADDRESS\> \* 을 사용 하 여 ip 주소에 연결 하 고, 인증서에 나열 된 도메인을 확인 하 여 ip 주소와 연결 된 도메인을 파악 합니다. microsoft 소유의 ip 주소이 고 Office 365 IP 주소 목록이 아닌 경우 ip 주소는 *MSOCDN.NET* 또는 다른 microsoft 도메인과 같은 microsoft CDN에 ip 정보를 게시 하지 않은 상태로 연결 될 수 있습니다. 인증서에서 도메인을 찾는 경우 IP 주소를 나열 하는 것은 사용자에 게 알려 주세요.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p127">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

<span data-ttu-id="dbfea-221"><a name="bkmk_cname"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-221"></span></span>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a><span data-ttu-id="dbfea-p128">일부 Office 365 url은 DNS에서 레코드가 아닌 CNAME 레코드를 가리킵니다. CNAME 레코드를 사용 하 여 수행 해야 하는 작업</span><span class="sxs-lookup"><span data-stu-id="dbfea-p128">Some Office 365 URLs point to CNAME records instead of A records in the DNS. What do I have to do with the CNAME records?</span></span>

<span data-ttu-id="dbfea-p129">클라이언트 컴퓨터에는 클라우드 서비스에 연결 하는 데 필요한 IP 주소가 하나 이상 포함 된 DNS a 또는 AAAA 레코드가 필요 합니다. Office 365에 포함 된 일부 url은 A 또는 AAAA 레코드 대신 CNAME 레코드를 표시 합니다. 이러한 CNAME 레코드는 중개 레코드로, 체인에 여러 개 있을 수 있습니다. 항상 IP 주소에 대 한 A 또는 AAAA 레코드로 확인 됩니다. 예를 들어 궁극적으로 IP 주소 _IP_1_으로 확인 되는 다음과 같은 일련의 DNS 레코드를 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p129">Client computers need a DNS A or AAAA record that includes one or more IP Address(s) to connect to a cloud service. Some URLs included in Office 365 show CNAME records instead of A or AAAA records. These CNAME records are intermediary and there may be several in a chain. They will always eventually resolve to an A or AAAA record for an IP Address. For example, consider the following series of DNS records, which ultimately resolves to the IP address _IP_1_:</span></span>

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

<span data-ttu-id="dbfea-p130">이러한 CNAME 리디렉션은 DNS의 일반적인 부분이 며 클라이언트 컴퓨터에 투명 하며 프록시 서버에 대해 투명 합니다. 부하 분산, 콘텐츠 배달 네트워크, 고가용성 및 서비스 인시던트 완화에 사용 됩니다. Microsoft는 중개 CNAME 레코드를 게시 하지 않으며, 언제 든 지 변경 될 수 있으며, 프록시 서버에서 허용 되는 것으로 구성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p130">These CNAME redirects are a normal part of the DNS and are transparent to the client computer and transparent to proxy servers. They are used for load balancing, content delivery networks, high availability, and service incident mitigation. Microsoft does not publish the intermediary CNAME records, they are subject to change at any time, and you should not need to configure them as allowed in your proxy server.</span></span>

<span data-ttu-id="dbfea-p131">프록시 서버는 위의 예에서 serviceA.office.com이 고이 url이 office 365 게시에 포함 되어 있는 초기 URL의 유효성을 검사 합니다. 프록시 서버는 해당 URL의 DNS 확인을 IP 주소로 요청 하 고 IP_1를 다시 수신 합니다. 중간 CNAME 리디렉션 레코드의 유효성을 검사 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p131">A proxy server validates the initial URL which in the above example is serviceA.office.com and this URL would be included in Office 365 publishing. The proxy server requests DNS resolution of that URL to an IP Address and will receive back IP_1. It does not validate the intermediary CNAME redirection records.</span></span>

<span data-ttu-id="dbfea-p132">간접 Office 365 fqdn을 기반으로 하드 코드 된 구성 또는 허용 목록이 Microsoft에서 지원 하지 않는 것이 좋으며, 고객 연결 문제를 야기 하는 것으로 알려져 있습니다. CNAME 리디렉션에서 차단 되거나 Office 365 DNS 항목을 잘못 확인 하는 dns 솔루션은 dns 재귀를 사용 하도록 설정 된 dns 조건부 전달 (office 365 fqdn으로 범위가 지정 됨)을 통해 해결할 수 있습니다. 많은 타사 네트워크 경계 제품은 [office 365 IP 주소 및 URL 웹 서비스](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service)를 사용 하 여 권장 되는 office 365 끝점 허용 목록이을 구성에 기본적으로 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p132">Hard-coded configurations or whitelisting based on indirect Office 365 FQDNs is not recommended, not supported by Microsoft, and is known to cause customer connectivity issues. DNS solutions that block on CNAME redirection, or that otherwise incorrectly resolve Office 365 DNS entries, can be solved via DNS conditional forwarding (scoped to directly used Office 365 FQDNs) with DNS recursion enabled. Many third party network perimeter products natively integrate recommended Office 365 endpoint whitelisting in their configuration using the [Office 365 IP Address and URL Web service](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service).</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="dbfea-238">Microsoft 도메인 이름에 nsatc.net 또는 akadns.net와 같은 이름이 표시 되는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="dbfea-238">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="dbfea-239"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-239"></span></span>

<span data-ttu-id="dbfea-p133">office 365 및 기타 Microsoft 서비스에서는 Akamai 및 markmonitor와 같은 몇 가지 타사 서비스를 사용 하 여 Office 365 환경을 개선 합니다. 가능한 최상의 환경을 유지 하기 위해 나중에 이러한 서비스를 변경할 수 있습니다. 타사 도메인은 CDN 같은 콘텐츠를 호스팅하거나 지역 트래픽 관리 서비스와 같은 서비스를 호스팅할 수 있습니다. 현재 사용 중인 서비스 중 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p133">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="dbfea-p134">\* \*nsatc.net\* 를 포함 하는 요청을 볼 때 [markmonitor](https://www.markmonitor.com/) 가 사용 되 고 있습니다. 이 서비스는 도메인 이름 보호 및 모니터링을 제공 하 여 악의적인 동작 으로부터 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p134">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="dbfea-p135">\* \*exacttarget.com\* 에 대 한 요청을 볼 때 [ExactTarget](https://www.marketingcloud.com/) 가 사용 되 고 있습니다. 이 서비스는 악성 동작에 대 한 전자 메일 링크 관리 및 모니터링을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p135">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="dbfea-p136">다음 fqdn 중 하나를 포함 하는 요청이 표시 되 면 [Akamai](https://www.akamai.com/) 가 사용 중입니다. 이 서비스는 지리적 DNS 및 콘텐츠 배달 네트워크 서비스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p136">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a><span data-ttu-id="dbfea-250">Office 365에 대 한 최소 연결이 가능 해야 함</span><span class="sxs-lookup"><span data-stu-id="dbfea-250">I have to have the minimum connectivity possible for Office 365</span></span>
<span data-ttu-id="dbfea-251"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-251"></span></span>

<span data-ttu-id="dbfea-p137">Office 365은 인터넷을 통해 작동 하도록 구축 된 서비스 모음으로, 안정성 및 가용성 약속은 사용할 수 있는 다양 한 표준 인터넷 서비스를 기반으로 합니다. 예를 들어 DNS, CRL 및 cdns와 같은 표준 인터넷 서비스는 대부분의 최신 인터넷 서비스를 사용 하기 위해 연결할 수 있는 것 처럼 Office 365을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p137">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>

<span data-ttu-id="dbfea-p138">Office 365 제품군은 주요 서비스 지역으로 분류 되어 있습니다. 이러한 기능은 연결에 선택적으로 사용 하도록 설정할 수 있으며, all에 대 한 종속성 이며 항상 필요한 공통 영역이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p138">The Office 365 suite is broken down into major service areas. These can be selectively enabled for connectivity and there is a Common area which is a dependency for all and is always required.</span></span>

|<span data-ttu-id="dbfea-256">**서비스 영역**</span><span class="sxs-lookup"><span data-stu-id="dbfea-256">**Service Area**</span></span>|<span data-ttu-id="dbfea-257">**설명**</span><span class="sxs-lookup"><span data-stu-id="dbfea-257">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="dbfea-258">**Exchange**</span><span class="sxs-lookup"><span data-stu-id="dbfea-258">**Exchange**</span></span> <br/> |<span data-ttu-id="dbfea-259">exchange online 및 exchange online Protection</span><span class="sxs-lookup"><span data-stu-id="dbfea-259">Exchange Online and Exchange Online Protection</span></span> <br/> |
|<span data-ttu-id="dbfea-260">**SharePoint**</span><span class="sxs-lookup"><span data-stu-id="dbfea-260">**SharePoint**</span></span> <br/> |<span data-ttu-id="dbfea-261">SharePoint Online 및 비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="dbfea-261">SharePoint Online and OneDrive for Business</span></span> <br/> |
|<span data-ttu-id="dbfea-262">**비즈니스용 Skype Online 및 Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="dbfea-262">**Skype for Business Online and Microsoft Teams**</span></span> <br/> |<span data-ttu-id="dbfea-263">비즈니스용 Skype 및 Microsoft 팀</span><span class="sxs-lookup"><span data-stu-id="dbfea-263">Skype for Business and Microsoft Teams</span></span> <br/> |
|<span data-ttu-id="dbfea-264">**일반**</span><span class="sxs-lookup"><span data-stu-id="dbfea-264">**Common**</span></span> <br/> |<span data-ttu-id="dbfea-265">office 365 Pro Plus, office Online, Azure AD 및 기타 일반 네트워크 끝점</span><span class="sxs-lookup"><span data-stu-id="dbfea-265">Office 365 Pro Plus, Office Online, Azure AD and other common network endpoints</span></span> <br/> |

<span data-ttu-id="dbfea-p139">기본 인터넷 서비스 외에, 기능 통합에만 사용 되는 타사 서비스도 있습니다. 이러한 작업은 통합에 필요 하지만, 끝점에 액세스할 수 없는 경우 서비스의 핵심 기능이 계속 작동 하 게 된다는 것을 Office 365 endpoints 문서에 선택적으로 표시 합니다. 필요한 모든 네트워크 끝점은 필수 특성이 true로 설정 됩니다. 선택 사항인 모든 네트워크 끝점에는 필수 특성이 false로 설정 되 고, notes 특성은 연결이 차단 되는 경우 예상 되는 누락 된 기능을 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p139">In addition to basic internet services, there are third-party services that are only used to integrate functionality. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible. Any network endpoint which is required will have the required attribute set to true. Any network endpoint which is optional will have the required attribute set to false and the notes attribute will detail the missing functionality you should expect if connectivity is blocked.</span></span>
  
<span data-ttu-id="dbfea-270">Office 365을 사용 하려는 경우 타사 서비스를 찾을 수 없는 경우 [이 문서에 표시 된 모든 fqdn이 프록시 및 방화벽을 통해 허용 되는지 확인](urls-and-ip-address-ranges.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-270">If you're trying to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="dbfea-271">Microsoft의 소비자 서비스에 대 한 액세스를 차단 하는 방법</span><span class="sxs-lookup"><span data-stu-id="dbfea-271">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="dbfea-272"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="dbfea-272"></span></span>

<span data-ttu-id="dbfea-p140">소비자 서비스에 대 한 액세스를 제한 해야 하는 경우 사용자의 위험에 대 한 보안을 차단 하는 유일한 방법은 *login.live.com* FQDN에 대 한 액세스를 제한 하는 것입니다. 이 FQDN은 MSDN, TechNet 등의 소비자가 아닌 서비스를 포함 하는 광범위 한 서비스 집합에서 사용 됩니다. 이 FQDN은 microsoft 지원의 보안 파일 교환 프로그램 에서도 사용 되며 microsoft 제품에 대 한 문제 해결을 용이 하 게 하기 위해 파일을 전송 해야 합니다.  이 FQDN에 대 한 액세스를 제한 하면 이러한 서비스에 연결 된 네트워크 요청에 대 한 규칙에 대 한 예외도 포함 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-p140">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. This FQDN is also used by Microsoft Support's Secure File Exchange program and is necessary to transfer files to facilitate troubleshooting for Microsoft products.  Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="dbfea-277">Microsoft 소비자 서비스에 대 한 액세스를 차단 하더라도 Office 365 테 넌 트 또는 기타 서비스를 사용 하 여 네트워크의 누군가가 정보를 exfiltrate는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbfea-277">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="dbfea-278">관련 항목</span><span class="sxs-lookup"><span data-stu-id="dbfea-278">Related Topics</span></span>

[<span data-ttu-id="dbfea-279">Office 365 IP 주소 및 URL 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="dbfea-279">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="dbfea-280">Microsoft Azure 데이터 센터 IP 범위</span><span class="sxs-lookup"><span data-stu-id="dbfea-280">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="dbfea-281">Microsoft 공용 IP 공간</span><span class="sxs-lookup"><span data-stu-id="dbfea-281">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="dbfea-282">Microsoft Intune에 대 한 네트워크 인프라 요구 사항</span><span class="sxs-lookup"><span data-stu-id="dbfea-282">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="dbfea-283">express 경로 및 Power BI</span><span class="sxs-lookup"><span data-stu-id="dbfea-283">ExpressRoute and Power BI</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="dbfea-284">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="dbfea-284">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="dbfea-285">Office 365 연결에 대한 ExpressRoute 관리</span><span class="sxs-lookup"><span data-stu-id="dbfea-285">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="dbfea-286">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="dbfea-286">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
