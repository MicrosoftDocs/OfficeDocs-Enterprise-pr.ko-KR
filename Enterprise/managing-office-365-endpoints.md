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
ms.openlocfilehash: a1a658ff04bc7306cb953477798d3e32d894d695
ms.sourcegitcommit: 854653f927c9515024a1c9e0a86fd5f2fadb92f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "25359500"
---
# <a name="managing-office-365-endpoints"></a>Office 365 끝점 관리

## <a name="office-365-network-connectivity"></a>Office 365 네트워크 연결

 Office 365에 대 한 연결 높은 볼륨을 통해 사용자 옆에 있는 대기 시간이 적은 탈출 수행한 때 가장을 수행 하는 신뢰할 수 있는 네트워크 요청으로 구성 됩니다. 일부 Office 365 연결에서 연결을 최적화 이용할 수 있습니다. 
  
1. 방화벽 확인 Office 365 끝점에 대 한 연결에 대 한 목록 수 있도록 허용 합니다.
    
2. 프록시 인프라를 사용 하 여 와일드 카드 및 게시 되지 않은 대상에 인터넷 연결을 허용 합니다.
    
3. 최적의 경계 네트워크 구성 유지 관리 합니다.
    
4. [최상의 연결을 시작 하는 확인](https://aka.ms/o365perfprinciples)합니다.
    
5. 최상의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하려면 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md) 읽습니다. 
    
![방화벽 및 프록시를 통해 Office 365에 연결 합니다.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>업데이트 방화벽의 아웃 바운드 허용 목록

모든 신뢰할 수 있는 방화벽을 통해 직접 Office 365 네트워크 요청 보내기, 모든 추가 패킷 수준 검사를 무시 하거나 처리 하 여 네트워크를 최적화할 수 있습니다. 대기 시간에서 성능 저하 줄이고 경계 용량 요구 사항을 줄일 수 있습니다. 신뢰 하도록 요청 하는 네트워크를 선택 하는 것이 가장 편리 방법은 사용해 [미리 작성된 된 PAC 파일](managing-office-365-endpoints.md#pacfiles)을 사용 하는 것입니다. 
  
모든 IP 되도록 알면에 방화벽 블록 아웃 바운드 트래픽 및 Fqdn이 [XML 파일](https://go.microsoft.com/fwlink/?LinkId=533185) 에 **필요한** 로 표시 하는 경우에 허용 목록에 있습니다. 모든 서비스에는 일부 타사 서비스를 사용 해야 인식 합니다. 인증서 공급자의 경우 콘텐츠 배달 네트워크 DNS 공급자와 같은 이러한 타사 서비스에 대 한 IP 주소를 제공 하 고 등 하지 했습니다. 전체 Office 365 기능에 대 한 대상에 대 한 게시는 정보의 양을 관계 없이 Office 365에서 요청한 모든 대상에 연결할 수 있어야 합니다. 
  
이 기능을 사용 하 여 보내고 요청 되는 이러한 네트워크 요청을 현재 IP 주소를 해결 하는 작업을 할 수 있어야 합니다 다양 한 대상 게시 하는 IP 주소를 갖지 않습니다 또는 특정 정규화 된 도메인 이름 없이 와일드 카드 도메인으로 나열 된는 인터넷을 통해 네트워크 요청 합니다.
  
사용자를 대신 하 여 XML 파일을 구문 분석 하 고 방화벽을 통해 직접 라우팅할 하려는 서비스 또는 기능에 따라 자동으로 규칙을 업데이트 하는 방화벽을 사용 하 여 프로세스를 자동화 합니다. 커뮤니티에서 작성 된 Cisco XE 경로 또는 ACL 목록 구성, 일반 텍스트 또는 CSV 내보내기 옵션을 포함 하면 XML 구문 분석 하 여 [Azure 범위](https://azurerange.azurewebsites.net/) 도구를 사용할 수 있습니다. 
  
네트워크 대상에 대 한 긴 설명은 사용해 [기반 RSS 변경 로그를](https://go.microsoft.com/fwlink/p/?linkid=236301) 통해이 [참조 (영문) 사이트](urls-and-ip-address-ranges.md) 도 사용할 수 있는 이므로 변경 내용에 가입할 수 있습니다. 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>PAC 파일을 사용 하 여 아웃 바운드 경로 구성

Office 365와 연결 된 지만 제공 되는 IP 주소를 설치 하지 않은 네트워크 요청을 관리 하려면 PAC 또는 WPAD 파일을 사용 합니다. 프록시 또는 경계 장치를 통해 전송 되는 일반적인 네트워크 요청 추가 대기 시간을 발생 시킵니다. 프록시 인증 헤드가 가장 큰 세금, 하는 동안 신뢰도 조회 및 하려고 하면 패킷 검사 등의 다른 서비스는 사용자 환경의 성능이 저하 될 수 있습니다. 또한 이러한 경계 네트워크 장치는 모든 네트워크 요청을 처리 하는 데 충분 한 용량을 필요 합니다. 직접 Office 365 네트워크 요청에 대 한 프록시 또는 검사 인프라를 우회 하는 것이 좋습니다.
  
시작 지점으로 네트워크 트래픽을 프록시에 전송 됩니다 및 방화벽을 보내도록 하는 결정 하려면이 PAC 파일 중 하나를 사용 합니다. 라면 당사의 Office 365 컨설턴트 중 하나에서 [배포 PAC 파일](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) 에 대 한이 게시물을 읽을 PAC 또는 WPAD 파일의 새로운 기능입니다. 시작 지점으로 이러한를 검토 하 고 환경에 맞게 편집 하려고 합니다. 
  
 **PAC 파일 7/10/2018로 업데이트**합니다. 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1-PAC 파일:와 구분 알려진된 Office 365 FQDN에서 인터넷 Fqdn 필요 합니다.

첫번째 예제만 인터넷을 통해 끝점을 관리 하는 권장 되는 방법의 데모를은입니다. Office 365 대상 IP 주소를 게시 하 고 프록시에 나머지 네트워크 요청을 보냅니다 위치에 대 한 프록시를 무시 합니다.
  
코드 조각:

```javascript
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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2-PAC 파일: 인터넷 및 ExpressRoute를 통해 Office 365에 연결
<a name="bkmk_inet-aer"> </a>

두번째 예제는 ExpressRoute 및 인터넷 회로 사용할 수 있는 경우 연결을 관리 하는 권장 되는 방법의 데모입니다. ExpressRoute 보급 ExpressRoute 회로에 대상 및 인터넷에만 프록시에 대 한 대상 보급 보냅니다.
  
코드 조각:

```javascript
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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3-PAC 파일: 모든 Office 365 대상을 전체적으로 관리
<a name="bkmk_inet-direct"> </a>

세번째 단일 대상에 게 Office 365와 관련 된 모든 네트워크 요청을 보내는 예제입니다. 이 Office 365 네트워크 요청에 대 한 모든 검사를 무시 하도록 일반적으로 사용 하 고 있는 모든 게시 된 끝점 형식 하는 사용자 지정에 대 한 사용 하 여 PAC 형식에서 목록에서 제공 합니다.
  
코드 조각:

```javascript
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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>사용자 지정 스크립트를 사용 하거나 수동으로 직접 PAC 파일을 만들려면
<a name="pacfiles_manual"> </a>

구축 하는 경우 나가기를 공유 하려는 무언가 메모에 메모를 몇가지 추가 도구는 커뮤니티에서 다음과 같습니다. 이 문서에서 참조 되는 도구는 공식적으로 커뮤니티의 지원 없음 또는 Microsoft에 의해 유지 관리 하 고 필요에 따라 여기 제공 됩니다.
  
- Office 365 커뮤니티의 구성원에 의해 작성 하는 도구는 프로세스를 관리 하는데 가장 오래 된 커뮤니티 생성 도구입니다. [다운로드](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7)링크는 다음과 같습니다.
    
- 내보낼 수 있는 방화벽 규칙에 개념 증명: [Microsoft 클라우드 IP API](https://mscloudips.azurewebsites.net/)입니다.
    
- [IT Praktyk:에서 RSS 변환](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) 및 [XML 변환](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896)합니다.
    
- Peter Abele:에서 [다운로드](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3)합니다.
    
- 사용 하는 네트워크를 확인 하기 위해 네트워크 분석 요청 프록시 인프라가 무시 해야 합니다. 고객 프록시 사용 하지 않으려면 사용 되는 가장 일반적인 Fqdn 이러한 끝점에서 보내고 받는 네트워크 트래픽 볼륨으로 인해 다음을 포함 합니다.
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- 허용 된 대화 상대를 통과 하도록 요청을 허용 하도록 방화벽의 해당 항목을 포함 하는 방화벽에 직접 전송 되 고 네트워크 요청을 모두 확인 합니다.

## <a name="perimeter-network-integration"></a>경계 네트워크의 통합
<a name="BKMK_Perimeter"> </a>

Microsoft의 알고 WAN 세계에서 가장 큰 백본 중 하나입니다.
  
이것이이 대규모 네트워크는 Office 365 및 기타 클라우드 서비스는 전세계의 위치에 관계 없이 작업 기능을 사용 하면 true입니다. 다양 한 개인적으로 소유 진한 파이버와 클라우드 서비스를 사용 하 여 쉽게 수행할 수 있도록 모든 데이터 센터 및에 지 노드 간에 다중 Terabit 연결 경로 마일와 높은 대역폭, 낮은 대기 시간, 장애 조치 가능한 링크의이 네트워크 구성 됩니다.
  
다음과 같이 네트워크를 가능한 한 빨리이 네트워크에 연결 하 여 조직의 장치 할 수 있습니다. 넘는 2500 ISP 피어 링 관계를 가진 전역적으로 및 현재 상태의 70 포인트 우리를 네트워크에서 시작 해야 원활 하 게 수행 합니다. ISP의 피어 링 관계는는 가장 좋은 [방법은 다음 몇가지 예를](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) 정상 상태와 좋지 않습니다 하지 피어 링 손 장점과 단점을 이해 사용해 네트워크로의 확인 몇분 투자 면에 타격 수는 없습니다. 
  
최적으로 요청을 처리 하도록 Office 365 응용 프로그램 네트워크, 장비에 따라 네트워크에 있는 장치를 자동으로 구성 하거나 수동으로 수 있습니다. 최적으로 Office 365 네트워크 트래픽을 처리할 수 있도록 필요한 구성 변경 내용을 사용자 환경에 따라 달라 집니다. Office 365 네트워크 요청은 다음을 허용 하는 네트워크 구성에서 도움이 될 수 있습니다.
  
- 덜 중요 한 네트워크 트래픽 통한 우선순위입니다.
    
- 속도가 느린 WAN을 통해 backhauling를 방지 하기 위해 로컬 탈출을 라우팅하면 Microsoft 네트워크에서 사용할 수 있는 낮은 대기 시간을 활용 하는 동안 링크입니다. 고객 계약에 따라 [적절 한 내용은 다음과 같습니다](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) . 
    
- 가장 가까운 Microsoft 피어 링 위치에 도착 로컬 탈출 근처 DNS를 사용 하 여 로컬 탈출을 해제 하는 네트워크 요청을 확인 합니다.
    
- 상세 패킷 검사 또는 기타 위주의 네트워크 패킷 수직 확장의 대기 시간 요구 사항에 맞게 처리에서 제외 합니다.
    
현대 네트워크 장치에는 일반, 신뢰할 수 없는 인터넷 트래픽을 다르게 Office 365와 같은 신뢰할 수 있는 응용 프로그램에 대 한 네트워크 요청을 관리 하는 기능 포함 합니다. SD WAN 솔루션의 새로운 가로 방향으로 트래픽 및 경로 선택의 이러한 차별화도로 수행할 수 시간 가용성, 대기 시간 또는 다양 한 연결 경로의 성능에 대 한 포인터와 같은 네트워크의 변화 상태 인식 사용자와 클라우드 합니다.
  
네트워크 구성 계획에 대 한 추가 지침에 대 한 [네트워크 및 마이그레이션 Office 365에 대 한 계획](network-and-migration-planning.md), [성능 문제해결 Office 365에 대 한 계획](performance-troubleshooting-plan.md), 및 [Office 365에 대 한 배포 계획 검사 목록](deployment-planning-checklist.md) 을 참조 하십시오. 
  
### <a name="to-implement-this-scenario"></a>이 시나리오를 구현을:

사용할 수 있는 Office 365 URL 및 IP 정의 (사용자)에 대 한 로컬 낮은 오버 헤드를 용이 하 게 하는 XML에서 탈출 Office 365 트래픽에 대 한 네트워크의 다른 응용 프로그램을 기준으로 해당 우선순위를 관리 하 고 조정 하는 경우 네트워크 솔루션 또는 서비스 공급자를 통한 확인은 변화 하는 네트워크 환경에 따라 Microsoft 네트워크로 Office 365 연결에 대 한 네트워크 경로입니다. 일부 솔루션 다운로드 하 고 해당 스택이에서 Office 365 URL 및 IP Xml 정의 자동화 합니다.
  
항상 구현 된 솔루션 필요한 수준의 복구 기능, Office 365 트래픽에 대 한 네트워크 경로에 적절 한 지리적으로 분산 중복 있으며 페이지가 자동으로 게시 될 때 변경 내용을 Office 365 Url 및 Ip를 수용 해야 합니다.

## <a name="faq"></a>FAQ

연결에 대 한 관리자 질문과 대답:
  
### <a name="how-do-i-submit-a-question"></a>질문을 제출 하는 방법 합니까?

문서가 유용한 경우 나타내려면 맨 아래에 링크를 클릭 하 고 추가 질문을 제출 합니다. 피드백을 모니터링 하 고 가장 자주 묻는 질문에 여기 업데이트 합니다.
  
### <a name="when-is-the-xml-file-updated"></a>XML 파일을 업데이트 하는 경우

새 끝점 발표 된 때 방법이 일반적으로 30 + 일 버퍼가 유효 하 고 네트워크 요청을 이동 하는 것을 시작 하기 전에. 버퍼가 고객 되도록이 되어 파트너 기회를 시스템을 업데이트 합니다. FQDN과 IP 접두사 추가 및 제거 새 FQDN 될 XML 파일에서 사용 하기 전에 30 일 누구나 알림으로 동시에 XML 파일에서 처리 됩니다. 알림으로 동시에 XML에서 끝점을 제거 하는 경우 자신의 제거를 발표 하기 전에 제거 하는 끝점을 네트워크 요청을 보내는 중단 이후 않은 이미 사용 되는.
  
### <a name="how-can-i-be-notified-of-changes"></a>어떻게 합니까 알림을 받을 수 변경 합니까?
<a name="bkmk_changes"> </a>

Office 365 끝점은 30 일 통지와 각 달의 끝에 게시 됩니다. 필요에 따라 전혀 변경 달 두번 이상 또는 짧은 통지 기간을 사용 합니다. 끝점을 추가 하면 [RSS 피드](https://go.microsoft.com/fwlink/p/?linkid=236301) 에 나열 된 유효 날짜는 끝점으로 전송 됩니다 네트워크 요청 되는 날짜입니다. RSS의 새로운 기능 인 경우 [Outlook을 통해 구독](https://go.microsoft.com/fwlink/p/?LinkId=532416) 하거나 있습니다 하는 방법 [RSS 피드를 전자 메일로 전달 하는 업데이트는](https://go.microsoft.com/fwlink/p/?LinkId=532417)다음과 같습니다.
  
### <a name="how-do-i-read-the-rss-change-log"></a>RSS 변경 로그 어떻게 읽을 수 있습니까?
<a name="bkmk_changes"> </a>

RSS 피드를 구독 한 후 있습니다 구문 분석할 수 있는 정보는 사용자가 직접 또는 스크립트를 사용 합니다. 다음 표에서 형식 rss 피드 o 쉽게 합니다.
  
|**섹션**|**1 부**|**2 부**|**3 부**|**제 4 부**|**5 부**|**6 부**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**설명** <br/> |개수  <br/> |날짜를 끝점으로 보낼 수에 대 한 네트워크 요청을 얻을 수 있습니다.  <br/> |기능 또는 서비스 끝점에 대 한 기본 설명입니다.  <br/> |인터넷 외에 ExpressRoute 회로에서이 끝점에 연결할 수 있습니까?  <br/> |**Yes** -인터넷과 ExpressRoute에서이 끝점에 연결할 수 있습니다.  <br/> **No** -인터넷에서이 끝점에만 연결할 수 있습니다.  <br/> |대상 FQDN 또는 IP 범위 목록에 추가 되거나 제거 합니다.  <br/> |
|**예제** <br/> |1 /  <br/> |[효과적인 xx/xx/xxx 합니다.  <br/> |필수: \<설명\>합니다.  <br/> |ExpressRoute:  <br/> |\<예/아니요\>합니다.  <br/> |\<FQDN/IP\>],  <br/> |

몇 다른 참고 사항, 모든 항목에는 일반적인 집합이 구분 합니다.
  
- **/**-수 후
- 수에 대 한 항목을 나타내기 위해 **[** -
- **.** -항목의 고유한 각 구역 사이 사용 되는
- **],** -단일 항목의 끝을 나타내려면
- **].** -모든 항목의 끝을 표시 하려면

### <a name="how-do-i-determine-the-location-of-my-tenant"></a>테 넌 트의 위치를 확인 하려면 어떻게 해야 합니까?

 **테 넌 트 위치** 는 가장 사용해 [매핑할 데이터 센터를](https://o365datacentermap.azurewebsites.net/)사용 하 여 결정 됩니다.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>팔 I 피어 링 적절 하 게 microsoft?

 **Peering 위치** 는 [Microsoft와 피어 링](https://www.microsoft.com/peering)에 자세히 설명 되어있습니다.
  
넘는 2500 ISP 피어 링 관계를 가진 전역적으로 및 현재 상태의 70 포인트 우리를 네트워크에서 시작 해야 원활 하 게 수행 합니다. ISP의 피어 링 관계는는 가장 좋은 [방법은 다음 몇가지 예를](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) 정상 상태와 좋지 않습니다 하지 피어 링 손 장점과 단점을 이해 사용해 네트워크로의 확인 몇분 투자 면에 타격 수는 없습니다. 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>ExpressRoute을 통해 수락 하도록 IP 주소를 확인 하려면는 어떻게

 특정 Office 365 [BGP 커뮤니티](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)및 [Microsoft의 IP 범위](https://www.microsoft.com/download/details.aspx?id=53602) **수락 ExpressRoute 경로** 정의 합니다.
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>해야 하는 끝점을 확인 하려면 어떻게 해야 합니까?

정기적으로 새로운 기능 및 서비스에 추가 Office 365 제품군 연결 가로 확장 합니다. E3 또는 e 5 SKU에 가입한 끝점 목록에 대 한 생각 하는 간단한 방법은 한지는 제품군에 대 한 완전 한 기능을 활용할 수의 모든 해야 합니다. 이러한 Sku 중 하나에 가입 되지 않은 경우에 끝점 수 측면에서 최소한의는 다릅니다.
  
최상의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하 고 Office 365 끝점 범주에 대 한 자세한 정보를 보려면 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md) 을 읽습니다. 
  
아래 이미지에서 Office Online의 섹션에 있는 FQDN 테이블의 부분에서 예를 볼 수 있습니다. 행 기능 및 차이점 연결에 따라 구성 됩니다. 처음 두 행으로 표시 하는 끝점에서 Office Online는 사용 하 여 나타낼 Office 365 인증 및 Id 및 포털에 필요 하 고 섹션을 공유 합니다. 이러한 공유 서비스에 대 한 의존도 Office 365 내에서 서비스에 대 한 일반적인입니다. 클라이언트 컴퓨터에 연결할 수 있어야 하는 세번째 행 나타냅니다 \*. officeapps.live.com Office Online와 네번째 행을 사용 하 여 컴퓨터에 연결할 수도 있어야 나타냅니다 \*. Office Online을 사용 하 여 cdn.office.net 합니다.
  
두 행 3 및 Office Online을 사용 하는 데 필요한 4, 하는 경우에 대상은 다른 나타내기 위해 구분 된 했을 때:
  
1. \*. officeapps.live.com CDN를 나타내지 않는 경우,이 네임 스페이스에 대 한 의미 요청 Microsoft 데이터 센터에 직접 이동 됩니다.
2. \*. officeapps.live.com는 Microsoft Peering를 사용 하 여 ExpressRoute 회로에 액세스할 수 있습니다.
3. Office Online와 연결 된 IP 주소 및 \*. officeapps.live.com이이 링크를 수행 하 여 찾을 수 있습니다.
4. \*. cdn.office.net Akamai에서 호스트 CDN 나타냅니다,이 네임 스페이스에 대 한 의미 요청은 Akamai 데이터 센터에 들어갈 수 있습니다.
5. \*. cdn.office.net는 ExpressRoute 회로에 액세스할 수 없습니다.
6. Office Online와 연결 된 IP 주소 및 \*. cdn.office.net을 사용할 수 없습니다.

![끝점 페이지의 화면 캡처](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>게시 된 목록에 없는 IP 주소에 대 한 네트워크 요청을 참조 하 필요한에 대 한 액세스를 제공 합니다.
<a name="bkmk_MissingIP"> </a>

만 인터넷 이나 ExpressRoute를 통해 직접 라우팅할 해야 Office 365 서버에 대 한 IP 주소를 제공 합니다. 이 문서가 포괄적인 목록이 모든 IP 주소에 대 한 네트워크 요청을 볼 수 있습니다. Microsoft 및 제 3 자 소유, 게시 되지 않은, IP 주소에 대 한 네트워크 요청을 볼 수 있습니다. 이러한 IP 주소는 동적으로 생성 하거나 관리 변경 될 때 시기 적절 하 게 통지를 방지 하는 방법 (영문). 방화벽 수 없는 이러한 네트워크 요청에 대 한 Fqdn을 기준으로 액세스를 허용 하는 경우는 요청을 관리 하려면 PAC 또는 WPAD 파일을 사용 합니다.
  
Office 365에서 자세한 정보를 원하는 연관 된 IP 참조?
  
1. IP 주소는 [CIDR 계산기 (영문)를](http://jodies.de/ipcalc)사용 하 여 더 큰 게시 된 범위에 포함 되어 있는지 확인 합니다.
2. 파트너는 [whois 쿼리](https://dnsquery.org/)와 IP를 소유 하는 경우를 참조 합니다. Microsoft 소유 하 고 있으면는 내부 파트너 수 있습니다.
3. 인증서를 확인, 브라우저에서 사용 하 여 IP 주소에 연결 *HTTPS://\<IP_ADDRESS\> * , 어떤 도메인의 IP 주소와 연결 된 이해 하는 인증서에 나열 된 도메인을 확인 합니다. IP 주소를 소유 하는 Microsoft는 것이 발생 한 경우 Office 365 IP 주소 목록에 없는 가능성이 IP 주소에는 *MSOCDN.NET* 또는 게시 되는 IP 정보 없이 다른 Microsoft 도메인 등 Microsoft CDN와 관련이 있습니다. 도메인 인증서에는 하나 클레임 IP 주소를 나열 하는 위치를 찾으면을 수행 하는 경우 의견을 보내 주십시오.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>예: nsatc.net 또는 Microsoft 도메인 이름에 akadns.net 이름을 나타나는 이유는 무엇입니까?
<a name="bkmk_akamai"> </a>

Office 365 및 기타 Microsoft 서비스 Akamai MarkMonitor 등의 여러 타사 서비스를 사용 하 여 Office 365 환경을 개선 하기 위해. 최상의 경험 하 게 유지 하려면 가능한 경우는 변경할 수 있습니다 이러한 서비스 나중에. 이 과정에서 자주 제 3 자 갖고 있는 도메인, record 또는 IP 주소를 가리키는 CNAME 레코드를 게시 했습니다. 제 3 자 도메인 CDN, 등의 콘텐츠를 호스팅할 수 있습니다 또는 지리적 트래픽 관리 서비스와 같은 서비스를 호스트 될 수 있습니다. 이러한 제 3 자에 대 한 연결을 표시 하는 경우 리디렉션 또는 조회, 클라이언트에서 초기 요청 하지의 형태로 것입니다. 일부 고객은 이러한 형식의 조회 수 있도록 해야 하 고 리디렉션이 명시적으로 잠재적 Fqdn 제 3 자 서비스의 긴 목록을 사용할 수 있습니다를 추가 하지 않고 전달할 수 있습니다.
  
서비스의 목록은 언제 든 지 변경 될 수 있습니다. 현재 사용 중인 서비스 중 일부는 다음과 같습니다.
  
[MarkMonitor](https://www.markmonitor.com/) 를 포함 하는 요청을 참조 하는 경우 사용 중인 * \*. nsatc.net* 합니다. 이 서비스는 도메인 이름 보호 및 악의적인 동작 보호 하기 위해 모니터링을 제공 합니다.
  
[ExactTarget](https://www.marketingcloud.com/) 에 대 한 요청을 참조 하는 경우 사용 중인 * \*. exacttarget.com* 합니다. 이 서비스는 전자 메일 링크 관리 및 악의적인 동작에 대 한 모니터링을 제공 합니다.
  
[Akamai](https://www.akamai.com/) 사용 되 고 있는 때 다음 Fqdn 중 하나를 포함 하는 요청을 표시 합니다. 이 서비스는 지리적으로 분산 DNS 및 콘텐츠 배달 네트워크 서비스를 제공 합니다.
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>Office 365 끝점의 세 유형은 무엇입니까?
<a name="bkmk_akamai"> </a>

- DNS 조회 CDN 콘텐츠 검색 등의 기본 인터넷 서비스를 검색 하려면 제 3 자 서비스에 연결할 수 있습니다. OneNote 전자 필기장에서 YouTube 비디오를 통합 하는 등 통합 기능에 대 한 타사 서비스에 연결할 수도 있습니다.
- 보조 서비스 호스팅 및에 지 노드 컴퓨터에 가장 가까운 인터넷 위치에서 Microsoft의 글로벌 네트워크를 입력 하 여 네트워크 요청 수 있도록 하는 등 Microsoft가 실행에 연결할 수 있습니다. 공존할에서 세번째 가장 큰 네트워크로 연결 환경을 향상 됩니다. 다양 한 Office 365 서비스에서 사용 되는 Azure 미디어 서비스 등의 Microsoft Azure 서비스에 연결할 수도 있습니다.
- 고유 하 고 소유 데이터 거주 하는 비즈니스 온라인 서버에 대 한 Exchange Online 사서함 서버 또는 Skype와 같은 기본 Office 365 서비스에 연결할 수 있습니다. FQDN 또는 IP 주소 하 여 기본 Office 365 서비스에 연결할 수 있고 인터넷 또는 ExpressRoute 회로 사용 합니다. 제 3 자 및 인터넷 회로에 Fqdn을 사용 하 여 보조 서비스에만 연결할 수 있습니다.

다음 다이어그램은 이러한 서비스 영역 간의 차이 보여줍니다. 이 다이어그램에서 왼쪽 아래에서 고객 온-프레미스 네트워크에는 네트워크 연결 관리 지원 하기 위해 여러 네트워크 장치입니다. 그러면 다음과 같은 구성 기업 고객을 위한 공유 됩니다. 네트워크에만 클라이언트 컴퓨터와도 지원 되는 인터넷 사이 방화벽에 방화벽 허용 목록 규칙의 Fqdn 및 와일드 카드를 지원할 수를 확인 하려는 경우.
  
최상의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하 고 Office 365 끝점 범주에 대 한 자세한 정보를 보려면 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md) 을 읽습니다. 
  
![Office 365를 사용 하는 경우 네트워크 끝점의 세가지 다른 종류를 표시 합니다.](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>모든 타사 서비스를 사용 하지 않으려고 하거나 수 없음
<a name="bkmk_thirdparty"> </a>

Office 365가 인터넷을 통해 함수를 작성 하는 서비스 제품군, 안정성과 가용성 약속을 기반으로 사용할 수 있도록 하는 많은 표준 인터넷 서비스. 예, DNS, CRL, Cdn 등의 표준 인터넷 서비스는 대부분의 최신 인터넷 서비스를 사용 하 여 연결할 수 있어야 하는 것 처럼 Office 365를 사용 하 여 연결할 수 이어야 합니다.
  
이러한 기본 인터넷 서비스 외에도 다음과 같은 기능을 통합 하만 사용 되는 타사 서비스가 나와 있습니다. 예, Microsoft 팀 내에서 Giphy.com를 사용 하 여 원활 하 게 팀 내에서 Gif를 포함 하는 고객 수 있습니다. 마찬가지로, YouTube 및 Flickr 완벽 하 게 통합 비디오 및 이미지 인터넷에서 Office 클라이언트에 사용 되는 타사 서비스가 나와 있습니다. 통합을 위해 필요한 이러한 하는 동안 서비스의 핵심 기능 계속 끝점 액세스할 수 없을 경우 작동 것을 의미 하는 Office 365 끝점을 문서에 선택적으로 표시는 있습니다.
  
Office 365를 사용 하려고 하 고 액세스할 수 없는 제 3 자 서비스를 발견 하는 경우 [필수 또는이 문서에서 옵션을 표시 하는 모든 Fqdn 프록시 및 방화벽을 통해 허용 된 확인](urls-and-ip-address-ranges.md)합니다.
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>모든 보조 서비스를 사용 하 여 하지 않으려고 하거나 수 없음
<a name="bkmk_secondary"> </a>

보조 서비스는 Microsoft Office 365 컨트롤 내에 있는 하지 않습니다. 이들은 지 네트워크, Azure 미디어 서비스 및 콘텐츠 배달 네트워크 Azure 등입니다. 이러한은 Office 365를 사용 하 여 모든 필요 하 고 연결할 수 있어야 합니다.
  
Office 365를 사용 하려고 하 고 액세스할 수 없는 제 3 자 서비스를 발견 하는 경우 [필수 또는이 문서에서 옵션을 표시 하는 모든 Fqdn 프록시 및 방화벽을 통해 허용 된 확인](urls-and-ip-address-ranges.md)합니다.
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Microsoft의 소비자 서비스에 대 한 액세스를 차단 어떻게 합니까?
<a name="bkmk_consumer"> </a>

소비자 서비스에 대 한 액세스를 제한 해야 위험은 사용자가 자신의 차단 소비자 서비스에만 신뢰할 수 있는 방법은 *login.live.com* FQDN 대 한 액세스를 제한 하는 것입니다. 이 FQDN은 다양 한 MSDN, TechNet, 등의 비 소비자 서비스를 포함 하 여 서비스에서 사용 됩니다. 이 FQDN에 대 한 액세스를 제한도 이러한 서비스와 연결 된 네트워크 요청에 대 한 규칙에 대 한 예외를 포함할 필요가 늘어날 수 있습니다.
  
만으로는 Microsoft 고객 서비스에 대 한 액세스를 차단 차단 되지는 않습니다 기능 네트워크에 다른 사용자에 대 한는 Office 365 테 넌 트 또는 다른 서비스를 사용 하 여 exfiltrate 정보를 염두에 두어야 합니다.
  
## <a name="related-topics"></a>관련 항목

[Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)

[Microsoft Azure 데이터 센터 IP 범위](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 공용 IP 공간](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune에 대 한 네트워크 인프라 요구 사항](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Power BI 및 ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md)