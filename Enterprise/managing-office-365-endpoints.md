---
title: Office 365 끝점 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
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
description: 일부 네트워크는 Office 365에 액세스할 수 있는 이러한, 네트워크 및 프록시 관리자 Fqdn, Url의 목록을 관리할 필요가 및 있는 IP 주소와 동일 하 게 네트워크에 있는 컴퓨터에서 Office 365 끝점을 목록으로 구성 되도록 인터넷에 대 한 액세스를 제한 하도록 설계 되었습니다. 이러한 필요가 파일 확인 네트워크 요청을 프록시 또는 방화벽 규칙 및 PAC에 추가할 수는 Office 365에 연결할 수 있습니다.
ms.openlocfilehash: 0396174719adc7794a1d6bb4b1f950bfe4603996
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542040"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="c8173-104">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="c8173-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="c8173-105">Office 365 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="c8173-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="c8173-p102">Office 365에 대 한 연결 높은 볼륨을 통해 사용자 옆에 있는 대기 시간이 적은 탈출 수행한 때 가장을 수행 하는 신뢰할 수 있는 네트워크 요청으로 구성 됩니다. 일부 Office 365 연결에서 연결을 최적화 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="c8173-108">방화벽 확인 Office 365 끝점에 대 한 연결에 대 한 목록 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="c8173-109">프록시 인프라를 사용 하 여 와일드 카드 및 게시 되지 않은 대상에 인터넷 연결을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="c8173-110">최적의 경계 네트워크 구성 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="c8173-111">[최상의 연결을 시작 하는 확인](https://aka.ms/o365perfprinciples)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="c8173-112">최상의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하려면 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md) 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![방화벽 및 프록시를 통해 Office 365에 연결 합니다.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="c8173-114">업데이트 방화벽의 아웃 바운드 허용 목록</span><span class="sxs-lookup"><span data-stu-id="c8173-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="c8173-p103">모든 신뢰할 수 있는 방화벽을 통해 직접 Office 365 네트워크 요청 보내기, 모든 추가 패킷 수준 검사를 무시 하거나 처리 하 여 네트워크를 최적화할 수 있습니다. 대기 시간에서 성능 저하 줄이고 경계 용량 요구 사항을 줄일 수 있습니다. 신뢰 하도록 요청 하는 네트워크를 선택 하는 것이 가장 편리 방법은 위의 **프록시** 탭에 있는 미리 작성된 된 PAC 파일을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our pre-built PAC files on the **Proxies** tab above.</span></span> 
  
<span data-ttu-id="c8173-p104">모든 IP 되도록 알면에 방화벽 블록 아웃 바운드 트래픽 및 Fqdn이 [XML 파일](https://go.microsoft.com/fwlink/?LinkId=533185) 에 **필요한** 로 표시 하는 경우에 허용 목록에 있습니다. 모든 서비스에는 일부 타사 서비스를 사용 해야 인식 합니다. 인증서 공급자의 경우 콘텐츠 배달 네트워크 DNS 공급자와 같은 이러한 타사 서비스에 대 한 IP 주소를 제공 하 고 등 하지 했습니다. 전체 Office 365 기능에 대 한 대상에 대 한 게시는 정보의 양을 관계 없이 Office 365에서 요청한 모든 대상에 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="c8173-122">이 기능을 사용 하 여 보내고 요청 되는 이러한 네트워크 요청을 현재 IP 주소를 해결 하는 작업을 할 수 있어야 합니다 다양 한 대상 게시 하는 IP 주소를 갖지 않습니다 또는 특정 정규화 된 도메인 이름 없이 와일드 카드 도메인으로 나열 된는 인터넷을 통해 네트워크 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="c8173-p105">사용자를 대신 하 여 XML 파일을 구문 분석 하 고 방화벽을 통해 직접 라우팅할 하려는 서비스 또는 기능에 따라 자동으로 규칙을 업데이트 하는 방화벽을 사용 하 여 프로세스를 자동화 합니다. 커뮤니티에서 작성 된 Cisco XE 경로 또는 ACL 목록 구성, 일반 텍스트 또는 CSV 내보내기 옵션을 포함 하면 XML 구문 분석 하 여 [Azure 범위](https://azurerange.azurewebsites.net/) 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="c8173-125">네트워크 대상에 대 한 긴 설명은 사용해 [기반 RSS 변경 로그를](https://go.microsoft.com/fwlink/p/?linkid=236301) 통해이 [참조 (영문) 사이트](urls-and-ip-address-ranges.md) 도 사용할 수 있는 이므로 변경 내용에 가입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="c8173-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="c8173-127">PAC 파일을 사용 하 여 아웃 바운드 경로 구성</span><span class="sxs-lookup"><span data-stu-id="c8173-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="c8173-p106">Office 365와 연결 된 지만 제공 되는 IP 주소를 설치 하지 않은 네트워크 요청을 관리 하려면 PAC 또는 WPAD 파일을 사용 합니다. 프록시 또는 경계 장치를 통해 전송 되는 일반적인 네트워크 요청 추가 대기 시간을 발생 시킵니다. 프록시 인증 헤드가 가장 큰 세금, 하는 동안 신뢰도 조회 및 하려고 하면 패킷 검사 등의 다른 서비스는 사용자 환경의 성능이 저하 될 수 있습니다. 또한 이러한 경계 네트워크 장치는 모든 네트워크 요청을 처리 하는 데 충분 한 용량을 필요 합니다. 직접 Office 365 네트워크 요청에 대 한 프록시 또는 검사 인프라를 우회 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="c8173-p107">시작 지점으로 네트워크 트래픽을 프록시에 전송 됩니다 및 방화벽을 보내도록 하는 결정 하려면이 PAC 파일 중 하나를 사용 합니다. 라면 당사의 Office 365 컨설턴트 중 하나에서 [배포 PAC 파일](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) 에 대 한이 게시물을 읽을 PAC 또는 WPAD 파일의 새로운 기능입니다. 시작 지점으로 이러한를 검토 하 고 환경에 맞게 편집 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="c8173-136">**PAC 파일 7/10/2018로 업데이트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="c8173-137">#1-PAC 파일:와 구분 알려진된 Office 365 FQDN에서 인터넷 Fqdn 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="c8173-p108">첫번째 예제만 인터넷을 통해 끝점을 관리 하는 권장 되는 방법의 데모를은입니다. Office 365 대상 IP 주소를 게시 하 고 프록시에 나머지 네트워크 요청을 보냅니다 위치에 대 한 프록시를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="c8173-140">코드 조각:</span><span class="sxs-lookup"><span data-stu-id="c8173-140">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))
      
    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))
        
    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="c8173-141">#2-PAC 파일: 인터넷 및 ExpressRoute를 통해 Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="c8173-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="c8173-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-142"></span></span>

<span data-ttu-id="c8173-p109">두번째 예제는 ExpressRoute 및 인터넷 회로 사용할 수 있는 경우 연결을 관리 하는 권장 되는 방법의 데모입니다. ExpressRoute 보급 ExpressRoute 회로에 대상 및 인터넷에만 프록시에 대 한 대상 보급 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="c8173-145">코드 조각:</span><span class="sxs-lookup"><span data-stu-id="c8173-145">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="c8173-146">#3-PAC 파일: 모든 Office 365 대상을 전체적으로 관리</span><span class="sxs-lookup"><span data-stu-id="c8173-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="c8173-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-147"></span></span>

<span data-ttu-id="c8173-p110">세번째 단일 대상에 게 Office 365와 관련 된 모든 네트워크 요청을 보내는 예제입니다. 이 Office 365 네트워크 요청에 대 한 모든 검사를 무시 하도록 일반적으로 사용 하 고 있는 모든 게시 된 끝점 형식 하는 사용자 지정에 대 한 사용 하 여 PAC 형식에서 목록에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="c8173-150">코드 조각:</span><span class="sxs-lookup"><span data-stu-id="c8173-150">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="c8173-151">사용자 지정 스크립트를 사용 하거나 수동으로 직접 PAC 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c8173-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="c8173-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-152"></span></span>

<span data-ttu-id="c8173-p111">구축 하는 경우 나가기를 공유 하려는 무언가 메모에 메모를 몇가지 추가 도구는 커뮤니티에서 다음과 같습니다. 이 문서에서 참조 되는 도구는 공식적으로 커뮤니티의 지원 없음 또는 Microsoft에 의해 유지 관리 하 고 필요에 따라 여기 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="c8173-p112">Office 365 커뮤니티의 구성원에 의해 작성 하는 도구는 프로세스를 관리 하는데 가장 오래 된 커뮤니티 생성 도구입니다. [다운로드](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7)링크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="c8173-157">내보낼 수 있는 방화벽 규칙에 개념 증명: [Microsoft 클라우드 IP API](https://mscloudips.azurewebsites.net/)입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="c8173-158">[IT Praktyk:에서 RSS 변환](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) 및 [XML 변환](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="c8173-159">Peter Abele:에서 [다운로드](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="c8173-p113">사용 하는 네트워크를 확인 하기 위해 네트워크 분석 요청 프록시 인프라가 무시 해야 합니다. 고객 프록시 사용 하지 않으려면 사용 되는 가장 일반적인 Fqdn 이러한 끝점에서 보내고 받는 네트워크 트래픽 볼륨으로 인해 다음을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- <span data-ttu-id="c8173-162">허용 된 대화 상대를 통과 하도록 요청을 허용 하도록 방화벽의 해당 항목을 포함 하는 방화벽에 직접 전송 되 고 네트워크 요청을 모두 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>
    
## <a name="perimeter-network-integration"></a><span data-ttu-id="c8173-163">경계 네트워크의 통합</span><span class="sxs-lookup"><span data-stu-id="c8173-163">Perimeter network integration</span></span>
<span data-ttu-id="c8173-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-164"></span></span>

<span data-ttu-id="c8173-165">Microsoft의 알고 WAN 세계에서 가장 큰 백본 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="c8173-p114">이것이이 대규모 네트워크는 Office 365 및 기타 클라우드 서비스는 전세계의 위치에 관계 없이 작업 기능을 사용 하면 true입니다. 다양 한 개인적으로 소유 진한 파이버와 클라우드 서비스를 사용 하 여 쉽게 수행할 수 있도록 모든 데이터 센터 및에 지 노드 간에 다중 Terabit 연결 경로 마일와 높은 대역폭, 낮은 대기 시간, 장애 조치 가능한 링크의이 네트워크 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="c8173-p115">다음과 같이 네트워크를 가능한 한 빨리이 네트워크에 연결 하 여 조직의 장치 할 수 있습니다. 넘는 2500 ISP 피어 링 관계를 가진 전역적으로 및 현재 상태의 70 포인트 우리를 네트워크에서 시작 해야 원활 하 게 수행 합니다. ISP의 피어 링 관계는는 가장 좋은 [방법은 다음 몇가지 예를](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) 정상 상태와 좋지 않습니다 하지 피어 링 손 장점과 단점을 이해 사용해 네트워크로의 확인 몇분 투자 면에 타격 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="c8173-p116">최적으로 요청을 처리 하도록 Office 365 응용 프로그램 네트워크, 장비에 따라 네트워크에 있는 장치를 자동으로 구성 하거나 수동으로 수 있습니다. 최적으로 Office 365 네트워크 트래픽을 처리할 수 있도록 필요한 구성 변경 내용을 사용자 환경에 따라 달라 집니다. Office 365 네트워크 요청은 다음을 허용 하는 네트워크 구성에서 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="c8173-174">덜 중요 한 네트워크 트래픽 통한 우선순위입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="c8173-p117">속도가 느린 WAN을 통해 backhauling를 방지 하기 위해 로컬 탈출을 라우팅하면 Microsoft 네트워크에서 사용할 수 있는 낮은 대기 시간을 활용 하는 동안 링크입니다. 고객 계약에 따라 [적절 한 내용은 다음과 같습니다](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) .</span><span class="sxs-lookup"><span data-stu-id="c8173-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="c8173-177">가장 가까운 Microsoft 피어 링 위치에 도착 로컬 탈출 근처 DNS를 사용 하 여 로컬 탈출을 해제 하는 네트워크 요청을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="c8173-178">상세 패킷 검사 또는 기타 위주의 네트워크 패킷 수직 확장의 대기 시간 요구 사항에 맞게 처리에서 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="c8173-p118">현대 네트워크 장치에는 일반, 신뢰할 수 없는 인터넷 트래픽을 다르게 Office 365와 같은 신뢰할 수 있는 응용 프로그램에 대 한 네트워크 요청을 관리 하는 기능 포함 합니다. SD WAN 솔루션의 새로운 가로 방향으로 트래픽 및 경로 선택의 이러한 차별화도로 수행할 수 시간 가용성, 대기 시간 또는 다양 한 연결 경로의 성능에 대 한 포인터와 같은 네트워크의 변화 상태 인식 사용자와 클라우드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="c8173-181">네트워크 구성 계획에 대 한 추가 지침에 대 한 [네트워크 및 마이그레이션 Office 365에 대 한 계획](network-and-migration-planning.md), [성능 문제해결 Office 365에 대 한 계획](performance-troubleshooting-plan.md), 및 [Office 365에 대 한 배포 계획 검사 목록](deployment-planning-checklist.md) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8173-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="c8173-182">이 시나리오를 구현을:</span><span class="sxs-lookup"><span data-stu-id="c8173-182">To implement this scenario:</span></span>

<span data-ttu-id="c8173-p119">사용할 수 있는 Office 365 URL 및 IP 정의 (사용자)에 대 한 로컬 낮은 오버 헤드를 용이 하 게 하는 XML에서 탈출 Office 365 트래픽에 대 한 네트워크의 다른 응용 프로그램을 기준으로 해당 우선순위를 관리 하 고 조정 하는 경우 네트워크 솔루션 또는 서비스 공급자를 통한 확인은 변화 하는 네트워크 환경에 따라 Microsoft 네트워크로 Office 365 연결에 대 한 네트워크 경로입니다. 일부 솔루션 다운로드 하 고 해당 스택이에서 Office 365 URL 및 IP Xml 정의 자동화 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="c8173-185">항상 구현 된 솔루션 필요한 수준의 복구 기능, Office 365 트래픽에 대 한 네트워크 경로에 적절 한 지리적으로 분산 중복 있으며 페이지가 자동으로 게시 될 때 변경 내용을 Office 365 Url 및 Ip를 수용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>
  
## <a name="web-service"></a><span data-ttu-id="c8173-186">웹 서비스</span><span class="sxs-lookup"><span data-stu-id="c8173-186">Web service</span></span>
<span data-ttu-id="c8173-187"><a name="webservice"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-187"></span></span>

<span data-ttu-id="c8173-p120">새 웹 서비스를 보다 잘 식별 하 고 Office 365 네트워크 트래픽을 구분할 수 있도록 Office 365 끝점을 쉽게 평가 하 고 구성 하 고 최신 변경 내용으로 정보를 얻을 수 있습니다를 게시 합니다. (지금 미리 보기)에서이 새 웹 서비스 끝점을 [Office 365 Url 및 IP 주소 범위](urls-and-ip-address-ranges.md) 문서에 있는 해당 데이터의 XML 버전과 RSS와 함께 목록 대체 결국 합니다. 단계적 2018 년 10 월 2에서으로 정리 하는 끝점 데이터의 이러한 형식에 대 한 계획입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p120">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service (now in preview), will eventually replace the lists of endpoints in the [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) article, along with the RSS and XML versions of that data. These format of endpoint data are planned to be phased out on October 2, 2018.</span></span> 
  
<span data-ttu-id="c8173-191">고객 또는 네트워크 경계 장치 공급 업체는 Office 365 IP 주소와 FQDN 항목에 대 한 새로운 REST 기반 웹 서비스에 대해 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-191">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries.</span></span>
  
- <span data-ttu-id="c8173-192">최신 버전의 Office 365 Url 및 IP 주소 범위를 사용 하 여 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-192">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="c8173-193">Office 365 Url 및 방화벽 및 프록시 서버에 대 한 IP 주소 범위 페이지에서 데이터를 사용 하 여 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-193">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="c8173-194">최신 변경 내용, 사용 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-194">To get the latest changes, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
<span data-ttu-id="c8173-195">고객으로이 웹 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-195">As a customer, you can use this web service to:</span></span> 
  
- <span data-ttu-id="c8173-196">Office 365 끝점 데이터 받기 및 네트워킹 장치에 대 한 모든 서식을 수정 하 여 PowerShell 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-196">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
    
- <span data-ttu-id="c8173-197">이 정보를 사용 하 여 클라이언트 컴퓨터에 배포 하는 PAC 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-197">Use this information to update PAC files deployed to client computers.</span></span>
    
<span data-ttu-id="c8173-198">네트워크 경계 장치 공급 업체도이 웹 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-198">As a network perimeter device vendor, you can use this web service to:</span></span> 
  
- <span data-ttu-id="c8173-199">페이지를 만들고 자동화 된 구성에 대 한 목록을 다운로드 하려면 장치 소프트웨어를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-199">Create and test device software to download the list for automated configuration.</span></span> 
    
- <span data-ttu-id="c8173-200">현재 버전을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-200">Check for the current version.</span></span>
    
- <span data-ttu-id="c8173-201">현재 변경 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-201">Get the current changes.</span></span>
    
<span data-ttu-id="c8173-202">다음 섹션에서는 서비스는 일반적으로 사용할 수 있을 때까지 시간이 지남에 따라 변경 될 수 있습니다는이 웹 서비스의 미리 보기에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-202">The following sections describe the preview of this web service, which might change over time until the service is generally available.</span></span> 
  
<span data-ttu-id="c8173-203">웹 서비스에서 데이터를 최신 상태로 유지 하 고 하지 않으려는 추가로 변경 하는 웹 서비스 Url에는 또는 릴리스 이전에 출시가 웹 서비스의 데이터 스키마를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-203">The data on the web service is up to date and we are not planning to make further changes to the web service URLs or returned data schema before the general availability release of this web service.</span></span>
  
<span data-ttu-id="c8173-204">자세한 내용은 다음을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-204">For additional information, see:</span></span>
  
- [<span data-ttu-id="c8173-205">Office 365 기술 커뮤니티 포럼에 알림 블로그 게시물</span><span class="sxs-lookup"><span data-stu-id="c8173-205">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [<span data-ttu-id="c8173-206">웹 서비스의 사용에 대 한 질문에 대 한 office 365 기술 커뮤니티 포럼</span><span class="sxs-lookup"><span data-stu-id="c8173-206">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a><span data-ttu-id="c8173-207">일반 매개 변수</span><span class="sxs-lookup"><span data-stu-id="c8173-207">Common parameters</span></span>

<span data-ttu-id="c8173-208">이러한 매개 변수는 모든 웹 서비스 메서드가 간에 공통:</span><span class="sxs-lookup"><span data-stu-id="c8173-208">These parameters are common across all the web service methods:</span></span>
  
- <span data-ttu-id="c8173-p121">**형식 CSV = | JSON** -쿼리 문자열 매개 변수입니다. 기본적으로 반환 되는 데이터 형식은 JSON입니다. 쉼표로 구분 된 값 (CSV) 형식으로 데이터를 반환 하려면이 선택적 매개 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p121">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span> 
    
- <span data-ttu-id="c8173-p122">**ClientRequestId** -쿼리 문자열 매개 변수입니다. 클라이언트 세션 연결에 대 한 생성 하는 필수 GUID입니다. 웹 서비스를 호출 하는 각 클라이언트 컴퓨터에 대 한 GUID를 생성 해야 합니다. 자신이 차단 될 수는 웹 서비스에 의해 나중에 하기 때문에 다음 예제에 표시 된 Guid를 사용 하지 마십시오. GUID 형식이 xxxxxxxx-이며-이며-이며-xxxxxxxxxxxx, 여기서 x는 16 진수를 나타냅니다. GUID를 생성 하려면 [새로 만들기 Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p122">**ClientRequestId** - Query string parameter. A required GUID that you generate for client session association. You should generate a GUID for each client machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span> 
    
### <a name="version-web-method"></a><span data-ttu-id="c8173-218">버전 웹 메서드</span><span class="sxs-lookup"><span data-stu-id="c8173-218">Version web method</span></span>

<span data-ttu-id="c8173-p123">Microsoft Office 365 IP 주소 및 FQDN에 대 한 주기에서 필요에 따라 하 고 각 월의 끝에 항목을 업데이트 하는 운영 또는 요구를 지원 합니다. 게시 된 각 인스턴스에 대 한 데이터는 버전 번호를 할당 됩니다. 버전 웹 메서드를 사용 하면 각 Office 365 서비스 인스턴스에 대 한 최신 버전에 대 한를 폴링할 수 있습니다. 매일, 또는 가장, 매시간 버전을 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p123">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly.</span></span>
  
<span data-ttu-id="c8173-223">버전 웹 메서드에 대 한 매개 변수 하나 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-223">There is one parameter for the version web method:</span></span>
  
- <span data-ttu-id="c8173-p124">**AllVersions = true** -쿼리 문자열 매개 변수입니다. 기본적으로 반환 되는 버전에 최신 정보는 합니다. 모든 게시 된 버전을 요청 하려면이 선택적 매개 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p124">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span> 
    
- <span data-ttu-id="c8173-p125">**인스턴스** -Route 매개 변수입니다. 이 선택적 매개 변수에 대 한 버전을 반환 하려면 인스턴스를 지정 합니다. 를 생략 하면 인스턴스를 모두 반환 됩니다. 유효한 인스턴스는: 전세계, 중국, 독일, USGovDoD, USGovGCCHigh</span><span class="sxs-lookup"><span data-stu-id="c8173-p125">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh</span></span> 
    
<span data-ttu-id="c8173-p126">단일 레코드 또는 레코드의 배열에서 버전 웹 메서드 결과 수 있습니다. 각 레코드의 요소는.</span><span class="sxs-lookup"><span data-stu-id="c8173-p126">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>
  
- <span data-ttu-id="c8173-233">인스턴스-Office 365 서비스 인스턴스의 짧은 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-233">instance - The short name of the Office 365 service instance.</span></span>
    
- <span data-ttu-id="c8173-234">최신-지정 된 인스턴스의 끝점에 대 한 최신 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-234">latest - The latest version for endpoints of the specified instance.</span></span>
    
- <span data-ttu-id="c8173-p127">버전-지정 된 인스턴스에 대 한 모든 이전 버전의 목록입니다. 이 요소는만 AllVersions 매개 변수는 하는 경우를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p127">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>
   
#### <a name="examples"></a><span data-ttu-id="c8173-237">예제:</span><span class="sxs-lookup"><span data-stu-id="c8173-237">Examples:</span></span>
  
<span data-ttu-id="c8173-238">예제 1에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="c8173-238">Example 1 request URI: **<span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-p128">이 URI는 최신 버전의 각 Office 365 서비스 인스턴스를 반환합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="c8173-p128">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>
  
```
[
 {
  "instance": "Worldwide", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
] 
```

> [!IMPORTANT]
> <span data-ttu-id="c8173-p129">이러한 Uri에서 ClientRequestID 매개 변수에 대 한 GUID는 예제 일 뿐입니다. 웹을 시도 하려면 아웃 Uri 서비스, 사용자 고유의 GUID를 생성 합니다. 이 예제에 표시 된 guid가 나중에 웹 서비스에 의해 차단 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p129">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span> 
  
<span data-ttu-id="c8173-244">예제 2에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="c8173-244">Example 2 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-p130">이 URI는 최신 버전의 지정된 된 Office 365 서비스 인스턴스를 반환합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="c8173-p130">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="c8173-247">예제 3에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 =**</span><span class="sxs-lookup"><span data-stu-id="c8173-247">Example 3 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-p131">이 URI CSV 형식으로 출력을 보여줍니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="c8173-p131">This URI shows output in CSV format. Example result:</span></span>
  
```
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="c8173-250">예제 4에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 =**</span><span class="sxs-lookup"><span data-stu-id="c8173-250">Example 4 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-p132">이 URI는 Office 365 전세계 서비스 인스턴스에 대 한 게시 된 모든 이전 버전을 표시 합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="c8173-p132">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>
  
```
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

### <a name="endpoints-web-method"></a><span data-ttu-id="c8173-253">끝점 웹 메서드</span><span class="sxs-lookup"><span data-stu-id="c8173-253">Endpoints web method</span></span>

<span data-ttu-id="c8173-p133">끝점 웹 메서드를 사용 하는 Office 365 서비스를 구성 하는 Url 및 IP 주소 범위에 대 한 모든 레코드를 반환 합니다. 끝점 웹 메서드에 대 한 매개 변수는.</span><span class="sxs-lookup"><span data-stu-id="c8173-p133">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. Parameters for the endpoints web method are:</span></span>
  
- <span data-ttu-id="c8173-p134">**ServiceAreas** -쿼리 문자열 매개 변수입니다. 서비스 분야의 쉼표로 구분 된 목록입니다. 유효한 항목은 공통, Exchange, SharePoint, Skype 합니다. 일반적인 서비스 영역 항목은 다른 모든 서비스 분야에 대 한 필수 구성 요소 이기 때문에 웹 서비스는 항상 포함 시킵니다. 이 매개 변수를 포함 하지 않으면 모든 서비스 분야 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p134">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span> 
    
- <span data-ttu-id="c8173-p135">**TenantName** -쿼리 문자열 매개 변수입니다. Office 365 테 넌 트 이름입니다. 웹 서비스에 제공 된 이름을 가져와 테 넌 트 이름을 포함 하는 Url의 부분에 삽입 합니다. Url의 해당 부분 와일드 카드 문자는 테 넌 트 이름을 제공 하지 않으면, (\*).</span><span class="sxs-lookup"><span data-stu-id="c8173-p135">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span> 
    
- <span data-ttu-id="c8173-p136">**NoIPv6** -쿼리 문자열 매개 변수입니다. 하려면이 옵션을 true로 설정 제외 IPv6 주소는 출력에서 예, 네트워크에서 i p v 6을 사용 하지 않는 경우.</span><span class="sxs-lookup"><span data-stu-id="c8173-p136">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span> 
    
- <span data-ttu-id="c8173-p137">**인스턴스** -Route 매개 변수입니다. 이 필수 매개 변수에 대 한 끝점을 반환 하려면 인스턴스를 지정 합니다. 유효한 인스턴스는: 전세계, 중국, 독일, USGovDoD, USGovGCCHigh 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p137">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span> 
    
<span data-ttu-id="c8173-p138">적용 한 결과 끝점 웹 메서드를은 끝점 집합을 나타내는 각 레코드와 레코드의 배열입니다. 각 레코드에 대 한 요소는.</span><span class="sxs-lookup"><span data-stu-id="c8173-p138">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>
  
- <span data-ttu-id="c8173-272">id-끝점의 변경할 수 없는 id 번호를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-272">id - The immutable id number of the endpoint set.</span></span>
    
- <span data-ttu-id="c8173-273">serviceArea-이의 일부인 서비스 영역: 공통, Exchange, SharePoint, 또는 Skype 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-273">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
    
- <span data-ttu-id="c8173-p139">url-끝점에 대 한 Url을 설정합니다. DNS 레코드의 JSON 배열입니다. 비어 있는 경우를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p139">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
    
- <span data-ttu-id="c8173-p140">tcpPorts-끝점에 대 한 TCP 포트를 설정 합니다. 모든 요소를 포트의 포트 또는 대시 문자 (-)으로 구분 하 여 포트 범위를 쉼표로 구분 된 목록으로 서식이 지정 됩니다. 포트는 해당 범주에 대 한 끝점 설정 한다는 점에서 모든 IP 주소 및 Url을 모두에 적용 됩니다. 비어 있는 경우를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p140">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
    
- <span data-ttu-id="c8173-p141">udpPorts-UDP 포트는 ip 주소 범위가 끝점 집합에 있습니다. 비어 있는 경우를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p141">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
    
- <span data-ttu-id="c8173-p142">ip-나열 된 TCP 또는 UDP 포트와 연결 된 설정이 끝점과 연결 된 IP 주소 범위입니다. 비어 있는 경우를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p142">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. Omitted if blank.</span></span>
    
- <span data-ttu-id="c8173-p143">범주-끝점에 대 한 연결 범주를 설정합니다. 유효한 값은 최적화, 허용 및 기본 합니다. 필수.</span><span class="sxs-lookup"><span data-stu-id="c8173-p143">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. Required.</span></span>
    
- <span data-ttu-id="c8173-288">expressRoute-True 또는 False 이면이 끝점 집합 ExpressRoute를 통해 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-288">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
    
- <span data-ttu-id="c8173-p144">필수-이 끝점 집합을 지원 해야 하는 Office 365에 대 한 연결을 필요로 하는 경우 True입니다. False 인 경우 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p144">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. Omitted if false.</span></span>
    
- <span data-ttu-id="c8173-p145">선택 사항 끝점에 대 한 메모-이 설명 텍스트 포함 될 누락 된 IP 주소를 하는 경우 Office 365 기능 또는 Url이이 끝점 집합 네트워크 계층에서 액세스할 수 없습니다. 비어 있는 경우를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p145">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>
    
#### <a name="examples"></a><span data-ttu-id="c8173-293">예제:</span><span class="sxs-lookup"><span data-stu-id="c8173-293">Examples:</span></span>
  
<span data-ttu-id="c8173-294">예제 1에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="c8173-294">Example 1 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-p146">이 URI는 모든 작업에 대 한 Office 365 전세계 인스턴스에 대 한 모든 끝점을 가져옵니다. 예제 결과 출력의 일부를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p146">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>
  
```
[ 
 { 
  "id": 1, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.protection.outlook.com" 
   ], 
  "ips": 
   [ 
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32" 
   ], 
  "tcpPorts": "443", 
  "expressRoute": true, 
  "category": "Allow" 
 }, 
 { 
  "id": 2, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.mail.protection.outlook.com" 
   ],
...
```

<span data-ttu-id="c8173-297">이 예제에는 추가 끝점 집합 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-297">Additional endpoint sets are not included in this example.</span></span>
  
<span data-ttu-id="c8173-298">예제 2에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 =**</span><span class="sxs-lookup"><span data-stu-id="c8173-298">Example 2 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-299">이 예제에서는 Exchange Online 및 종속성만 Office 365 전세계 인스턴스에 대 한 끝점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-299">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>
  
<span data-ttu-id="c8173-300">예: 2 출력 결과 포함 되지 것입니다 끝점 SharePoint Online 또는 Skype에 대 한 온라인 비즈니스에 대 한 한다는 점을 제외 하면 예제 1에서는 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-300">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>
  
### <a name="changes-web-method"></a><span data-ttu-id="c8173-301">변경 된 웹 메서드</span><span class="sxs-lookup"><span data-stu-id="c8173-301">Changes web method</span></span>

<span data-ttu-id="c8173-p147">변경 내용을 웹 메서드를 사용 하는 게시 된 최신 업데이트를 반환 합니다. 이 일반적으로 Url 및 IP 주소 범위를 이전 달의 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p147">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c8173-304">데이터 변경 내용 API에서 미리 보기에서 정확 하 게 이며 있어야 테스트 및 개발을 위한 사용만 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-304">Data from the changes API is accurate in the preview and should be used for development and testing only.</span></span> 
  
<span data-ttu-id="c8173-305">변경 내용 웹 메서드에 대 한 매개 변수가입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-305">The parameter for the changes web method is:</span></span>
  
- <span data-ttu-id="c8173-p148">**버전** -필요한 URL 경로 매개 변수입니다. 현재 구현 하 고 해당 버전 이후 변경 된 내용을 확인 하려면 버전입니다. 형식은 YYYYMMDDNN입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p148">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is YYYYMMDDNN.</span></span> 
    
<span data-ttu-id="c8173-p149">변경 된 웹 메서드 결과 배열 하는 끝점의 특정 버전에서 변경 내용을 나타내는 각 레코드와 레코드입니다. 각 레코드에 대 한 요소는.</span><span class="sxs-lookup"><span data-stu-id="c8173-p149">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>
  
- <span data-ttu-id="c8173-311">id-변경 레코드의 변경할 수 없는 id입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-311">id - The immutable id of the change record.</span></span>
    
- <span data-ttu-id="c8173-p150">endpointSetId-끝점의 ID는 변경 된 레코드를 설정 합니다. 필수.</span><span class="sxs-lookup"><span data-stu-id="c8173-p150">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
    
- <span data-ttu-id="c8173-314">처리-이 변경, 추가, 또는 제거 될 수 및 않은 끝점 집합 레코드를 변경 내용에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-314">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
    
- <span data-ttu-id="c8173-p151">버전-게시 된 끝점의 버전 설정할 변경 도입 되었습니다. 하루에 게시 되어야 하는 데 필요한 여러 버전 YYYYMMDDNN, 여기서 NN은 없는 경우 증가 하는 자연 번호가 형식의 버전 번호는 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p151">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format YYYYMMDDNN, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
    
- <span data-ttu-id="c8173-p152">이전-끝점에서 변경 된 요소의 이전 값에 자세히 설명 하는 하위 구조를 설정 합니다. 이 새로 추가 된 끝점 집합에 대 한 포함 되지 않습니다. TcpPorts, udpPorts, 포함 ExpressRoute, 범주, 필요한, 메모 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p152">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="c8173-p153">현재-값이 업데이트는 endpoinset에서 변경 된 요소를 자세히 설명 하는 하위 구조입니다. TcpPorts, udpPorts, 포함 ExpressRoute, 범주, 필요한, 메모 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p153">current - A substructure detailing updated values of changes elements on the endpoinset. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="c8173-p154">추가-끝점에 추가 될 항목에 자세히 설명 하는 하위 구조 컬렉션을 설정 합니다. 추가 되지 경우 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p154">add - A sub structure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
    
  - <span data-ttu-id="c8173-324">effectiveDate-의 추가 서비스의 라이브 될 때 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-324">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
    
  - <span data-ttu-id="c8173-325">ip-ip 배열에 추가할 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-325">ips - Items to be added to the ips array.</span></span>
    
  - <span data-ttu-id="c8173-326">url-항목을 url 배열에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-326">urls- Items to be added to the urls array.</span></span>
    
- <span data-ttu-id="c8173-p155">제거-끝점에서 제거할 항목에 자세히 설명 하는 하위 구조를 설정 합니다. 없음 제거 경우 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p155">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
    
  - <span data-ttu-id="c8173-329">ip-ip 배열에서 제거할 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-329">ips - Items to be removed from the ips array.</span></span>
    
  - <span data-ttu-id="c8173-330">url 배열에서 제거할 url 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-330">urls- Items to be removed from the urls array.</span></span>
    
 <span data-ttu-id="c8173-331">**예제:**</span><span class="sxs-lookup"><span data-stu-id="c8173-331">**Examples:**</span></span>
  
<span data-ttu-id="c8173-332">예제 1에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="c8173-332">Example 1 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-p156">Office 365 전세계 서비스 인스턴스는 모든 이전 변경을 요청합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="c8173-p156">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>
  
```
[ 
 { 
  "id": 424, 
  "endpointSetId": 32, 
  "disposition": "Change", 
  "version": "2018062700", 
  "remove": 
   { 
    "urls": 
     [ 
      "*.api.skype.com", "skypegraph.skype.com" 
     ] 
   } 
 }, 
 { 
  "id": 426, 
  "endpointSetId": 31, 
  "disposition": "Change", 
  "version": "2018062700", 
  "add": 
   { 
    "effectiveDate": "20180609", 
    "ips": 
     [ 
      "51.140.203.190/32" 
     ]
   },
  "remove": 
   { 
    "ips": 
     [
...

```

<span data-ttu-id="c8173-335">예제 2에서는 요청 URI: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="c8173-335">Example 2 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="c8173-p157">변경 요청이 Office 365 전세계 인스턴스를 지정된 된 버전 이후의 합니다. 이 경우 지정 된 버전은 최신입니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="c8173-p157">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>
  
```
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]

```

### <a name="example-powershell-script"></a><span data-ttu-id="c8173-339">예제 PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="c8173-339">Example PowerShell Script</span></span>

<span data-ttu-id="c8173-p158">업데이트 된 데이터에 대 한 해야할 작업이 있는지를 실행할 수 있는 PowerShell 스크립트는 다음과 같습니다. 이 스크립트는 Office 365 전세계 인스턴스 끝점에 대 한 버전 번호를 확인합니다. 프로그램 변경 내용이 있을 때 끝점 및 "허용" 및 "최적화" 범주 끝점에 대 한 필터 다운로드 합니다. 또한 고유한 ClientRequestId를 사용 하 여 여러 통화 별 하 고 파일을 임시 파일에 있는 최신 버전을 저장 합니다. 버전 업데이트를 확인 하는 시간에 한번이 스크립트를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p158">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    
    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        
        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

### <a name="example-python-script"></a><span data-ttu-id="c8173-345">예제 Python 스크립트</span><span class="sxs-lookup"><span data-stu-id="c8173-345">Example Python Script</span></span>

<span data-ttu-id="c8173-p159">업데이트 된 데이터에 대 한 해야할 작업이 있는지를 실행할 수 있는 Windows 10에서 Python 3.6.3 사용 하 여 테스트는 Python 스크립트는 다음과 같습니다. 이 스크립트는 Office 365 전세계 인스턴스 끝점에 대 한 버전 번호를 확인합니다. 프로그램 변경 내용이 있을 때 끝점 및 "허용" 및 "최적화" 범주 끝점에 대 한 필터 다운로드 합니다. 또한 고유한 ClientRequestId를 사용 하 여 여러 통화 별 하 고 파일을 임시 파일에 있는 최신 버전을 저장 합니다. 버전 업데이트를 확인 하는 시간에 한번이 스크립트를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p159">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))
    
    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

### <a name="web-service-interface-versioning"></a><span data-ttu-id="c8173-351">웹 서비스 인터페이스 버전 관리</span><span class="sxs-lookup"><span data-stu-id="c8173-351">Web Service interface versioning</span></span>

<span data-ttu-id="c8173-p160">매개 변수 또는 이러한 웹 서비스 메서드에 대 한 결과에 대 한 업데이트를 나중에 필요할 수 있습니다. 이러한 웹 서비스의 출시 버전을 게시 한 후 Microsoft 웹 서비스에 대 한 재료 업데이트의 사전 통지를 제공 하는 합리적인 모든 조치를 확인 합니다. Microsoft는 업데이트는 웹 서비스를 사용 하는 클라이언트의 변경이 필요는 생각, 하는 경우 Microsoft에는 새 버전의 릴리스 이후 적어도 12 (12) 개월 동안 사용할 수 있는 웹 서비스의 이전 버전 (버전 다시) 유지 됩니다. 이 시간 동안을 업그레이드 하지 않는 고객 수 웹 서비스 및 해당 메서드에 액세스할 수 없습니다. 고객은 클라이언트가 웹 서비스의 웹 서비스 인터페이스 서명에 다음과 같이 변경 내용이 있는 경우 오류 없이 작업을 계속 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p160">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>
  
- <span data-ttu-id="c8173-357">이전 버전의 클라이언트에 의해 제공 될 필요가 없으므로 하 고 결과 영향을 주지는 기존 웹 메서드에 새 선택적 매개 변수를 추가 (영문) 이전 클라이언트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-357">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
    
- <span data-ttu-id="c8173-358">CSV에 대 한 응답에 응답 나머지 항목 또는 추가 열 중 하나에 새 명명 된 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-358">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
    
- <span data-ttu-id="c8173-359">이전 버전의 클라이언트에 의해 호출 하지는 새 이름으로 새 웹 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-359">Adding a new web method with a new name that is not called by the older clients.</span></span>
    
## <a name="faq"></a><span data-ttu-id="c8173-360">FAQ</span><span class="sxs-lookup"><span data-stu-id="c8173-360">FAQ</span></span>

<span data-ttu-id="c8173-361">연결에 대 한 관리자 질문과 대답:</span><span class="sxs-lookup"><span data-stu-id="c8173-361">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="c8173-362">질문을 제출 하는 방법 합니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-362">How do I submit a question?</span></span>

<span data-ttu-id="c8173-p161">문서가 유용한 경우 나타내려면 맨 아래에 링크를 클릭 하 고 추가 질문을 제출 합니다. 피드백을 모니터링 하 고 가장 자주 묻는 질문에 여기 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p161">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="c8173-365">XML 파일을 업데이트 하는 경우</span><span class="sxs-lookup"><span data-stu-id="c8173-365">When is the XML file updated?</span></span>

<span data-ttu-id="c8173-p162">새 끝점 발표 된 때 방법이 일반적으로 30 + 일 버퍼가 유효 하 고 네트워크 요청을 이동 하는 것을 시작 하기 전에. 버퍼가 고객 되도록이 되어 파트너 기회를 시스템을 업데이트 합니다. FQDN과 IP 접두사 추가 및 제거 새 FQDN 될 XML 파일에서 사용 하기 전에 30 일 누구나 알림으로 동시에 XML 파일에서 처리 됩니다. 알림으로 동시에 XML에서 끝점을 제거 하는 경우 자신의 제거를 발표 하기 전에 제거 하는 끝점을 네트워크 요청을 보내는 중단 이후 않은 이미 사용 되는.</span><span class="sxs-lookup"><span data-stu-id="c8173-p162">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="c8173-370">어떻게 합니까 알림을 받을 수 변경 합니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-370">How can I be notified of changes?</span></span>
<span data-ttu-id="c8173-371"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-371"></span></span>

<span data-ttu-id="c8173-p163">Office 365 끝점은 30 일 통지와 각 달의 끝에 게시 됩니다. 필요에 따라 전혀 변경 달 두번 이상 또는 짧은 통지 기간을 사용 합니다. 끝점을 추가 하면 [RSS 피드](https://go.microsoft.com/fwlink/p/?linkid=236301) 에 나열 된 유효 날짜는 끝점으로 전송 됩니다 네트워크 요청 되는 날짜입니다. RSS의 새로운 기능 인 경우 [Outlook을 통해 구독](https://go.microsoft.com/fwlink/p/?LinkId=532416) 하거나 있습니다 하는 방법 [RSS 피드를 전자 메일로 전달 하는 업데이트는](https://go.microsoft.com/fwlink/p/?LinkId=532417)다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p163">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="c8173-376">RSS 변경 로그 어떻게 읽을 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-376">How do I read the RSS change log?</span></span>
<span data-ttu-id="c8173-377"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-377"></span></span>

<span data-ttu-id="c8173-p164">RSS 피드를 구독 한 후 있습니다 구문 분석할 수 있는 정보는 사용자가 직접 또는 스크립트를 사용 합니다. 다음 표에서 형식 rss 피드 o 쉽게 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p164">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="c8173-380">**섹션**</span><span class="sxs-lookup"><span data-stu-id="c8173-380">**Section**</span></span>|<span data-ttu-id="c8173-381">**1 부**</span><span class="sxs-lookup"><span data-stu-id="c8173-381">**Part 1**</span></span>|<span data-ttu-id="c8173-382">**2 부**</span><span class="sxs-lookup"><span data-stu-id="c8173-382">**Part 2**</span></span>|<span data-ttu-id="c8173-383">**3 부**</span><span class="sxs-lookup"><span data-stu-id="c8173-383">**Part 3**</span></span>|<span data-ttu-id="c8173-384">**제 4 부**</span><span class="sxs-lookup"><span data-stu-id="c8173-384">**Part 4**</span></span>|<span data-ttu-id="c8173-385">**5 부**</span><span class="sxs-lookup"><span data-stu-id="c8173-385">**Part 5**</span></span>|<span data-ttu-id="c8173-386">**6 부**</span><span class="sxs-lookup"><span data-stu-id="c8173-386">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="c8173-387">**설명**</span><span class="sxs-lookup"><span data-stu-id="c8173-387">**Description**</span></span> <br/> |<span data-ttu-id="c8173-388">개수</span><span class="sxs-lookup"><span data-stu-id="c8173-388">Count</span></span>  <br/> |<span data-ttu-id="c8173-389">날짜를 끝점으로 보낼 수에 대 한 네트워크 요청을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-389">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="c8173-390">기능 또는 서비스 끝점에 대 한 기본 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-390">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="c8173-391">인터넷 외에 ExpressRoute 회로에서이 끝점에 연결할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-391">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="c8173-392">**Yes** -인터넷과 ExpressRoute에서이 끝점에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-392">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="c8173-393">**No** -인터넷에서이 끝점에만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-393">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="c8173-394">대상 FQDN 또는 IP 범위 목록에 추가 되거나 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-394">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="c8173-395">**예제**</span><span class="sxs-lookup"><span data-stu-id="c8173-395">**Example**</span></span> <br/> |<span data-ttu-id="c8173-396">1 /</span><span class="sxs-lookup"><span data-stu-id="c8173-396">1/</span></span>  <br/> |<span data-ttu-id="c8173-397">[효과적인 xx/xx/xxx 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-397">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="c8173-398">필수: \<설명\>합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-398">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="c8173-399">ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="c8173-399">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="c8173-400">\<예/아니요\>합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-400">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="c8173-401">\<FQDN/IP\>],</span><span class="sxs-lookup"><span data-stu-id="c8173-401">\<FQDN/IP\>],</span></span>  <br/> |
   
<span data-ttu-id="c8173-402">몇 다른 참고 사항, 모든 항목에는 일반적인 집합이 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-402">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="c8173-403">**/**-수 후</span><span class="sxs-lookup"><span data-stu-id="c8173-403">**/** - after the count</span></span> 
    
- <span data-ttu-id="c8173-404">수에 대 한 항목을 나타내기 위해 **[** -</span><span class="sxs-lookup"><span data-stu-id="c8173-404">**[** - to indicate the entry for the count</span></span> 
    
- <span data-ttu-id="c8173-p165">**.** -항목의 고유한 각 구역 사이 사용 되는</span><span class="sxs-lookup"><span data-stu-id="c8173-p165">**.** - used in between each distinct section of the entry</span></span> 
    
- <span data-ttu-id="c8173-407">**],** -단일 항목의 끝을 나타내려면</span><span class="sxs-lookup"><span data-stu-id="c8173-407">**],** - to indicate the end of a single entry</span></span> 
    
- <span data-ttu-id="c8173-p166">**].** -모든 항목의 끝을 표시 하려면</span><span class="sxs-lookup"><span data-stu-id="c8173-p166">**].** - To indicate the end of all the entries</span></span> 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="c8173-410">테 넌 트의 위치를 확인 하려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-410">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="c8173-411">**테 넌 트 위치** 는 가장 사용해 [매핑할 데이터 센터를](https://o365datacentermap.azurewebsites.net/)사용 하 여 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-411">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="c8173-412">팔 I 피어 링 적절 하 게 microsoft?</span><span class="sxs-lookup"><span data-stu-id="c8173-412">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="c8173-413">**Peering 위치** 는 [Microsoft와 피어 링](https://www.microsoft.com/peering)에 자세히 설명 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-413">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="c8173-p167">넘는 2500 ISP 피어 링 관계를 가진 전역적으로 및 현재 상태의 70 포인트 우리를 네트워크에서 시작 해야 원활 하 게 수행 합니다. ISP의 피어 링 관계는는 가장 좋은 [방법은 다음 몇가지 예를](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) 정상 상태와 좋지 않습니다 하지 피어 링 손 장점과 단점을 이해 사용해 네트워크로의 확인 몇분 투자 면에 타격 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p167">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="c8173-416">ExpressRoute을 통해 수락 하도록 IP 주소를 확인 하려면는 어떻게</span><span class="sxs-lookup"><span data-stu-id="c8173-416">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="c8173-417">특정 Office 365 [BGP 커뮤니티](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)및 [Microsoft의 IP 범위](https://www.microsoft.com/download/details.aspx?id=53602) **수락 ExpressRoute 경로** 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-417">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="c8173-418">해야 하는 끝점을 확인 하려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-418">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="c8173-p168">정기적으로 새로운 기능 및 서비스에 추가 Office 365 제품군 연결 가로 확장 합니다. E3 또는 e 5 SKU에 가입한 끝점 목록에 대 한 생각 하는 간단한 방법은 한지는 제품군에 대 한 완전 한 기능을 활용할 수의 모든 해야 합니다. 이러한 Sku 중 하나에 가입 되지 않은 경우에 끝점 수 측면에서 최소한의는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p168">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="c8173-422">최상의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하 고 Office 365 끝점 범주에 대 한 자세한 정보를 보려면 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md) 을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-422">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="c8173-p169">아래 이미지에서 Office Online의 섹션에 있는 FQDN 테이블의 부분에서 예를 볼 수 있습니다. 행 기능 및 차이점 연결에 따라 구성 됩니다. 처음 두 행으로 표시 하는 끝점에서 Office Online는 사용 하 여 나타낼 Office 365 인증 및 Id 및 포털에 필요 하 고 섹션을 공유 합니다. 이러한 공유 서비스에 대 한 의존도 Office 365 내에서 서비스에 대 한 일반적인입니다. 클라이언트 컴퓨터에 연결할 수 있어야 하는 세번째 행 나타냅니다 \*. officeapps.live.com Office Online와 네번째 행을 사용 하 여 컴퓨터에 연결할 수도 있어야 나타냅니다 \*. Office Online을 사용 하 여 cdn.office.net 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p169">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="c8173-428">두 행 3 및 Office Online을 사용 하는 데 필요한 4, 하는 경우에 대상은 다른 나타내기 위해 구분 된 했을 때:</span><span class="sxs-lookup"><span data-stu-id="c8173-428">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="c8173-429">\*. officeapps.live.com CDN를 나타내지 않는 경우,이 네임 스페이스에 대 한 의미 요청 Microsoft 데이터 센터에 직접 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-429">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
    
2. <span data-ttu-id="c8173-430">\*. officeapps.live.com는 Microsoft Peering를 사용 하 여 ExpressRoute 회로에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-430">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
    
3. <span data-ttu-id="c8173-431">Office Online와 연결 된 IP 주소 및 \*. officeapps.live.com이이 링크를 수행 하 여 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-431">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
    
4. <span data-ttu-id="c8173-432">\*. cdn.office.net Akamai에서 호스트 CDN 나타냅니다,이 네임 스페이스에 대 한 의미 요청은 Akamai 데이터 센터에 들어갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-432">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
    
5. <span data-ttu-id="c8173-433">\*. cdn.office.net는 ExpressRoute 회로에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-433">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
    
6. <span data-ttu-id="c8173-434">Office Online와 연결 된 IP 주소 및 \*. cdn.office.net을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-434">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>
    
![끝점 페이지의 화면 캡처](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="c8173-436">게시 된 목록에 없는 IP 주소에 대 한 네트워크 요청을 참조 하 필요한에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-436">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="c8173-437"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-437"></span></span>

<span data-ttu-id="c8173-p170">만 인터넷 이나 ExpressRoute를 통해 직접 라우팅할 해야 Office 365 서버에 대 한 IP 주소를 제공 합니다. 이 문서가 포괄적인 목록이 모든 IP 주소에 대 한 네트워크 요청을 볼 수 있습니다. Microsoft 및 제 3 자 소유, 게시 되지 않은, IP 주소에 대 한 네트워크 요청을 볼 수 있습니다. 이러한 IP 주소는 동적으로 생성 하거나 관리 변경 될 때 시기 적절 하 게 통지를 방지 하는 방법 (영문). 방화벽 수 없는 이러한 네트워크 요청에 대 한 Fqdn을 기준으로 액세스를 허용 하는 경우는 요청을 관리 하려면 PAC 또는 WPAD 파일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p170">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="c8173-443">Office 365에서 자세한 정보를 원하는 연관 된 IP 참조?</span><span class="sxs-lookup"><span data-stu-id="c8173-443">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="c8173-444">IP 주소는 [CIDR 계산기 (영문)를](http://jodies.de/ipcalc)사용 하 여 더 큰 게시 된 범위에 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-444">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
    
2. <span data-ttu-id="c8173-p171">파트너는 [whois 쿼리](https://dnsquery.org/)와 IP를 소유 하는 경우를 참조 합니다. Microsoft 소유 하 고 있으면는 내부 파트너 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p171">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
    
3. <span data-ttu-id="c8173-p172">인증서를 확인, 브라우저에서 사용 하 여 IP 주소에 연결 *HTTPS://\<IP_ADDRESS\> * , 어떤 도메인의 IP 주소와 연결 된 이해 하는 인증서에 나열 된 도메인을 확인 합니다. IP 주소를 소유 하는 Microsoft는 것이 발생 한 경우 Office 365 IP 주소 목록에 없는 가능성이 IP 주소에는 *MSOCDN.NET* 또는 게시 되는 IP 정보 없이 다른 Microsoft 도메인 등 Microsoft CDN와 관련이 있습니다. 도메인 인증서에는 하나 클레임 IP 주소를 나열 하는 위치를 찾으면을 수행 하는 경우 의견을 보내 주십시오.</span><span class="sxs-lookup"><span data-stu-id="c8173-p172">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span> 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="c8173-450">예: nsatc.net 또는 Microsoft 도메인 이름에 akadns.net 이름을 나타나는 이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-450">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="c8173-451"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-451"></span></span>

<span data-ttu-id="c8173-p173">Office 365 및 기타 Microsoft 서비스 Akamai MarkMonitor 등의 여러 타사 서비스를 사용 하 여 Office 365 환경을 개선 하기 위해. 최상의 경험 하 게 유지 하려면 가능한 경우는 변경할 수 있습니다 이러한 서비스 나중에. 이 과정에서 자주 제 3 자 갖고 있는 도메인, record 또는 IP 주소를 가리키는 CNAME 레코드를 게시 했습니다. 제 3 자 도메인 CDN, 등의 콘텐츠를 호스팅할 수 있습니다 또는 지리적 트래픽 관리 서비스와 같은 서비스를 호스트 될 수 있습니다. 이러한 제 3 자에 대 한 연결을 표시 하는 경우 리디렉션 또는 조회, 클라이언트에서 초기 요청 하지의 형태로 것입니다. 일부 고객은 이러한 형식의 조회 수 있도록 해야 하 고 리디렉션이 명시적으로 잠재적 Fqdn 제 3 자 서비스의 긴 목록을 사용할 수 있습니다를 추가 하지 않고 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p173">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="c8173-p174">서비스의 목록은 언제 든 지 변경 될 수 있습니다. 현재 사용 중인 서비스 중 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p174">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="c8173-p175">[MarkMonitor](https://www.markmonitor.com/) 를 포함 하는 요청을 참조 하는 경우 사용 중인 \* \*. nsatc.net\* 합니다. 이 서비스는 도메인 이름 보호 및 악의적인 동작 보호 하기 위해 모니터링을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p175">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span> 
  
<span data-ttu-id="c8173-p176">[ExactTarget](https://www.marketingcloud.com/) 에 대 한 요청을 참조 하는 경우 사용 중인 \* \*. exacttarget.com\* 합니다. 이 서비스는 전자 메일 링크 관리 및 악의적인 동작에 대 한 모니터링을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p176">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span> 
  
<span data-ttu-id="c8173-p177">[Akamai](https://www.akamai.com/) 사용 되 고 있는 때 다음 Fqdn 중 하나를 포함 하는 요청을 표시 합니다. 이 서비스는 지리적으로 분산 DNS 및 콘텐츠 배달 네트워크 서비스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p177">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span> 
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="c8173-466">Office 365 끝점의 세 유형은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-466">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="c8173-467"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-467"></span></span>

- <span data-ttu-id="c8173-p178">DNS 조회 CDN 콘텐츠 검색 등의 기본 인터넷 서비스를 검색 하려면 제 3 자 서비스에 연결할 수 있습니다. OneNote 전자 필기장에서 YouTube 비디오를 통합 하는 등 통합 기능에 대 한 타사 서비스에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p178">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
    
- <span data-ttu-id="c8173-p179">보조 서비스 호스팅 및에 지 노드 컴퓨터에 가장 가까운 인터넷 위치에서 Microsoft의 글로벌 네트워크를 입력 하 여 네트워크 요청 수 있도록 하는 등 Microsoft가 실행에 연결할 수 있습니다. 공존할에서 세번째 가장 큰 네트워크로 연결 환경을 향상 됩니다. 다양 한 Office 365 서비스에서 사용 되는 Azure 미디어 서비스 등의 Microsoft Azure 서비스에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p179">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
    
- <span data-ttu-id="c8173-p180">고유 하 고 소유 데이터 거주 하는 비즈니스 온라인 서버에 대 한 Exchange Online 사서함 서버 또는 Skype와 같은 기본 Office 365 서비스에 연결할 수 있습니다. FQDN 또는 IP 주소 하 여 기본 Office 365 서비스에 연결할 수 있고 인터넷 또는 ExpressRoute 회로 사용 합니다. 제 3 자 및 인터넷 회로에 Fqdn을 사용 하 여 보조 서비스에만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p180">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>
    
<span data-ttu-id="c8173-p181">다음 다이어그램은 이러한 서비스 영역 간의 차이 보여줍니다. 이 다이어그램에서 왼쪽 아래에서 고객 온-프레미스 네트워크에는 네트워크 연결 관리 지원 하기 위해 여러 네트워크 장치입니다. 그러면 다음과 같은 구성 기업 고객을 위한 공유 됩니다. 네트워크에만 클라이언트 컴퓨터와도 지원 되는 인터넷 사이 방화벽에 방화벽 허용 목록 규칙의 Fqdn 및 와일드 카드를 지원할 수를 확인 하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="c8173-p181">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="c8173-480">최상의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하 고 Office 365 끝점 범주에 대 한 자세한 정보를 보려면 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md) 을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-480">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![Office 365를 사용 하는 경우 네트워크 끝점의 세가지 다른 종류를 표시 합니다.](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="c8173-482">모든 타사 서비스를 사용 하지 않으려고 하거나 수 없음</span><span class="sxs-lookup"><span data-stu-id="c8173-482">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="c8173-483"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-483"></span></span>

<span data-ttu-id="c8173-p182">Office 365가 인터넷을 통해 함수를 작성 하는 서비스 제품군, 안정성과 가용성 약속을 기반으로 사용할 수 있도록 하는 많은 표준 인터넷 서비스. 예, DNS, CRL, Cdn 등의 표준 인터넷 서비스는 대부분의 최신 인터넷 서비스를 사용 하 여 연결할 수 있어야 하는 것 처럼 Office 365를 사용 하 여 연결할 수 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p182">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="c8173-p183">이러한 기본 인터넷 서비스 외에도 다음과 같은 기능을 통합 하만 사용 되는 타사 서비스가 나와 있습니다. 예, Microsoft 팀 내에서 Giphy.com를 사용 하 여 원활 하 게 팀 내에서 Gif를 포함 하는 고객 수 있습니다. 마찬가지로, YouTube 및 Flickr 완벽 하 게 통합 비디오 및 이미지 인터넷에서 Office 클라이언트에 사용 되는 타사 서비스가 나와 있습니다. 통합을 위해 필요한 이러한 하는 동안 서비스의 핵심 기능 계속 끝점 액세스할 수 없을 경우 작동 것을 의미 하는 Office 365 끝점을 문서에 선택적으로 표시는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p183">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="c8173-490">Office 365를 사용 하려고 하 고 액세스할 수 없는 제 3 자 서비스를 발견 하는 경우 [필수 또는이 문서에서 옵션을 표시 하는 모든 Fqdn 프록시 및 방화벽을 통해 허용 된 확인](urls-and-ip-address-ranges.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-490">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="c8173-491">모든 보조 서비스를 사용 하 여 하지 않으려고 하거나 수 없음</span><span class="sxs-lookup"><span data-stu-id="c8173-491">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="c8173-492"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-492"></span></span>

<span data-ttu-id="c8173-p184">보조 서비스는 Microsoft Office 365 컨트롤 내에 있는 하지 않습니다. 이들은 지 네트워크, Azure 미디어 서비스 및 콘텐츠 배달 네트워크 Azure 등입니다. 이러한은 Office 365를 사용 하 여 모든 필요 하 고 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p184">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="c8173-496">Office 365를 사용 하려고 하 고 액세스할 수 없는 제 3 자 서비스를 발견 하는 경우 [필수 또는이 문서에서 옵션을 표시 하는 모든 Fqdn 프록시 및 방화벽을 통해 허용 된 확인](urls-and-ip-address-ranges.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-496">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="c8173-497">Microsoft의 소비자 서비스에 대 한 액세스를 차단 어떻게 합니까?</span><span class="sxs-lookup"><span data-stu-id="c8173-497">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="c8173-498"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="c8173-498"></span></span>

<span data-ttu-id="c8173-p185">소비자 서비스에 대 한 액세스를 제한 해야 위험은 사용자가 자신의 차단 소비자 서비스에만 신뢰할 수 있는 방법은 *login.live.com* FQDN 대 한 액세스를 제한 하는 것입니다. 이 FQDN은 다양 한 MSDN, TechNet, 등의 비 소비자 서비스를 포함 하 여 서비스에서 사용 됩니다. 이 FQDN에 대 한 액세스를 제한도 이러한 서비스와 연결 된 네트워크 요청에 대 한 규칙에 대 한 예외를 포함할 필요가 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-p185">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span> 
  
<span data-ttu-id="c8173-502">만으로는 Microsoft 고객 서비스에 대 한 액세스를 차단 차단 되지는 않습니다 기능 네트워크에 다른 사용자에 대 한는 Office 365 테 넌 트 또는 다른 서비스를 사용 하 여 exfiltrate 정보를 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8173-502">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="c8173-503">관련 항목</span><span class="sxs-lookup"><span data-stu-id="c8173-503">Related Topics</span></span>

[<span data-ttu-id="c8173-504">Microsoft Azure 데이터 센터 IP 범위</span><span class="sxs-lookup"><span data-stu-id="c8173-504">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="c8173-505">Microsoft 공용 IP 공간</span><span class="sxs-lookup"><span data-stu-id="c8173-505">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="c8173-506">Microsoft Intune에 대 한 네트워크 인프라 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c8173-506">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="c8173-507">Power BI 및 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="c8173-507">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="c8173-508">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="c8173-508">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="c8173-509">Office 365 연결에 대한 ExpressRoute 관리</span><span class="sxs-lookup"><span data-stu-id="c8173-509">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="c8173-510">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="c8173-510">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
  

