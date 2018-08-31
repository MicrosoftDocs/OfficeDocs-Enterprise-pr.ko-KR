---
title: Office 365 독일 끝점 변경 로그
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid: MOE150
ms.assetid: 980041c9-7984-44b2-95f0-af66743543a1
ms.openlocfilehash: e77d6fc3b8136f39ed75ef21b0ff417a4ad6465a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542146"
---
# <a name="office-365-germany-endpoints-change-log"></a>Office 365 독일 끝점 변경 로그

*적용 대상: Office 365 관리*

## <a name="list-of-changes-to-the-endpoints-required-for-office-365-germany"></a>Office 365 독일에 필요한 끝점에 대 한 변경 목록

다음 표에 [Office 365 독일 끝점](office-365-germany-endpoints.md)을 변경 합니다.
  
|**날짜**|**변경**|
|:-----|:-----|
|1/24/2017  <br/> |문서의 초기 게시 합니다.  <br/> |
|2/28/2017  <br/> |3 Fqdn; 추가 (영문) 1 / [효과적인 4/1/2017 합니다. 필수: Office 365 포털 및 공유 합니다. ExpressRoute: 아니요 www.office.de], 2 / [효과적인 4/1/2017 합니다. 필수: Office 365 포털 및 공유 합니다. ExpressRoute: 아니요 office.de], 3 / [효과적인 4/1/2017 합니다. 필수: Office 365 포털 및 공유 합니다. ExpressRoute: 아니요 officehome.msocdn.de]. 참고: 추가 (영문) 추가 포털 Fqdn. 2 IP_Sets; 추가 (영문) 1 / [효과적인 4/1/2017 합니다. 필수: Office 365 포털 및 공유 합니다. ExpressRoute: 아니요 51.5.245.67/32], 2 / [효과적인 4/1/2017 합니다. 필수: Office 365 포털 및 공유 합니다. ExpressRoute: 아니요 51.4.227.178/32]. 참고 사항: 추가 포털 끝점을 추가 합니다. 2 IP_Sets; 추가 (영문) 1 / [효과적인 4/1/2017 합니다. 필수: Office 365 포털 및 공유 합니다. ExpressRoute: 아니요 2a01:4180:2001::92], 2 / [효과적인 4/1/2017 합니다. 필수: Office 365 포털 및 공유 합니다. ExpressRoute: 아니요 2a01:4180:2401::11f]. 참고 사항: 추가 포털 끝점을 추가 합니다.  <br/> |
|3/8/2017  <br/> |1 Fqdn; 추가 (영문) 1 / [효과적인 3/8/2017 합니다. 비즈니스용 OneDrive: 필요 합니다. ExpressRoute: 아니요 spoprod-a.akamaihd.net] 합니다. 참고 사항: 추가 CDN 끝점을 추가 합니다.  <br/> |
|3/31/2017  <br/> |3 Fqdn; 추가 (영문) 1 / [효과적인 5/1/2017 합니다. 필수: SharePoint Online 하이브리드 합니다. \*. search.production.de.azuretrafficmanager.de], 2 / [효과적인 5/1/2017 합니다. 필수: SharePoint Online 하이브리드 합니다. login.microsoftonline.de], 3 / [효과적인 5/1/2017 합니다. 필수: SharePoint Online 하이브리드 합니다. provisioningapi.microsoftonline.de]. 참고: 추가 (영문) Sharepoint 하이브리드 Fqdn입니다.  <br/> |
|6/1/2017  <br/> |2 Fqdn 추가 (영문) 효과적인 7/1/2017  <br/> shellprod.msocdn.de  <br/> r1.res.office365.com  <br/> |
|6/26/2017  <br/> |자동 검색을 대체\*. Autodiscover.outlook.de 및 자동 검색 outlook.office.de outlook.de 합니다.  <br/> |
|2017/9/29  <br/> |3 Fqdn; 추가 (영문) 1 / [효과적인 11/1/2017 합니다.  <br/> cegsignup.microsoft.de  <br/> negsignup.microsoft.de  <br/> \*. svc.ms  <br/> |
|1/16/2018  <br/> |1 Fqdn; 추가 (영문) 1 / [효과적인 2/1/2018 합니다. 필수: Office 365 포털 합니다. ExpressRoute: 아니요 webshell.suite.office.de]. 참고: Office 365 제품군 셸에 대 한 추가 FQDN을 추가 합니다. 4 IP_Sets; 추가 (영문) 1 / [효과적인 2/1/2018 합니다. 필수: Office 365 포털 합니다. ExpressRoute: 아니요 51.5.242.163/32], 2 / [효과적인 2/1/2018 합니다. 필수: Office 365 포털 합니다. ExpressRoute: 아니요 51.4.226.115/32], 3 / [효과적인 2/1/2018 합니다. 필수: Office 365 포털 합니다. ExpressRoute: 아니요 2a01:4180:2401::33b / 4 / [효과적인 2/1/2018 합니다. 필수: Office 365 포털 합니다. ExpressRoute: 아니요 2a01:4180:2001::234 / 참고: Office 365 제품군 셸에 대 한 추가 IP 주소를 추가 합니다.  <br/> |
|2/5/2018  <br/> |1 개 추가 1 FQDN / [효과적인 3/1/2018 합니다. 필수: 포털 및 공유 합니다. ExpressRoute: 예입니다. webshell.suite.office.de]. 참고: 포털 및 공유 Fqdn. 2 IP_Sets; 추가 (영문)에 대 한 URL을 추가 (영문) 1 / [효과적인 3/1/2018 합니다. 필수: 포털 및 공유 합니다. ExpressRoute: 예입니다. 51.5.242.163/32]., 2 / [효과적인 3/1/2018 합니다. 필수: 포털 및 공유 합니다. ExpressRoute: 예입니다. 51.4.226.115/32]입니다. 참고 사항: 포털에 대 한 접두사를 추가 하 고 공유 새로 추가 합니다. 2 IP_Sets; 추가 (영문) 1 / [효과적인 3/1/2018 합니다. 필수: 포털 및 공유 합니다. ExpressRoute: 예입니다. 2a01:4180:2401::33b 128 /]., 2 / [효과적인 3/1/2018 합니다. 필수: 포털 및 공유 합니다. ExpressRoute: 예입니다. 2a01:4180:2001::234 128 /]. 참고 사항: 포털에 대 한 접두사를 추가 하 고 공유 새로 추가 합니다. 1 IP_Sets; 추가 (영문) 1 / [효과적인 3/1/2018 합니다. 필수: Office Online 합니다. ExpressRoute: 예입니다. 51.18.16.0/23]입니다. 참고 사항: Office Online에 대 한 새 접두사를 추가 합니다.  <br/> |
|3/15/2018  <br/> |1 IP_Set; 추가 (영문) 1 / [효과적인 4/15/2018 합니다. 필수: Office 365 ProPlus 합니다. ExpressRoute: 아니요 51.18.0.0/21]. 참고 사항: Office 365 ProPlus 끝점을 추가 합니다.  <br/> |
|7/2/2018  <br/> |1 FQDN; 제거 1 / [효과적인 8/1/2018 합니다. 비즈니스용 OneDrive: 필요 합니다. ExpressRoute: 아니요 login.microsoftonline.de]. 참고: 비즈니스 끝점에 대 한 OneDrive를 제거 합니다. 11 Fqdn; 제거 1 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://excelps.osi.office.de/exlps/excelprint.svc/exlPrint], 2 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://wordps.osi.office.de/wrdps/wordprint.svc/wrdprint], 3 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://wordcs.osi.office.de/wordauto/wordautomation.svc/wordautomation], 4 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://wordcs.osi.office.de/wordauto/wordautomation.svc/rest], 5 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://pptps.osi.office.de/pptps/powerpointprint.svc/PptPrint], 6 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/PptAutomation], 7 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/rest], 8 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://ols.osi.office.de/], 9 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://ols.osi.office.de/olsc/OlsClient.svc/OlsClient], 10 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://excelcs.osi.office.de/xlauto/excelautomation.svc/XlAutomation], 11 / [효과적인 8/1/2018 합니다. 필수: Office Mobile입니다. ExpressRoute: 아니요 https://excelcs.osi.office.de/xlauto/excelautomation.svc/rest]. 참고 사항: Office 모바일 끝점을 제거 합니다.  <br/> |
   

