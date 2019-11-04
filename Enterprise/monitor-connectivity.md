---
title: Office 365 연결 모니터링
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Office 365를 배포한 후에는 아래의 도구 및 기술 일부를 사용하여 Office 365 연결을 유지할 수 있습니다. 느린 네트워크에서 Office 365를 사용하기 위한 최상의 방법뿐만 아니라 공식적인 서비스 상태 및 연속성 지침을 이해할 수 있습니다. 또한 Office 365 관리자 앱을 이용하고 비즈니스용 Office 365 - 관리자 도움말을 북마크할 수도 있습니다.
ms.openlocfilehash: 385aef73173ea6bab421fae6d10622d7a8fe3c80
ms.sourcegitcommit: 9c39ba0c21fbe86343f825bb589a108ec5f176bf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2019
ms.locfileid: "37931696"
---
# <a name="monitor-office-365-connectivity"></a>Office 365 연결 모니터링

Office 365를 배포한 후에는 아래의 도구 및 기술 일부를 사용하여 Office 365 연결을 유지할 수 있습니다. [느린 네트워크에서 Office 365를 사용하기 위한 최상의 방법](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)뿐만 아니라 공식적인 [서비스 상태 및 연속성](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) 지침을 이해할 수 있습니다. 또한 [Office 365 관리자 앱](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)을 이용하고 비즈니스용 [Office 365 - 관리자 도움말](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)을 북마크할 수도 있습니다.
  
## <a name="monitoring-office-365-connectivity"></a>Office 365 연결 모니터링

|||
|:-----|:-----|
|**새 Office 365 끝점에 대한 알림 받기** <br/> |[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)를 사용하는 경우 새 끝점을 게시할 때 알림을 받고자 하면 즐겨찾는 RSS 수집기를 사용하여 RSS 피드를 구독할 수 있습니다. 여기에서는 [Outlook을 통해 구독](https://go.microsoft.com/fwlink/p/?LinkId=532416)하는 방법 또는 [RSS 피드를 전자 메일로 전송하여 업데이트](https://go.microsoft.com/fwlink/p/?LinkId=532417)할 수 있는 방법을 안내합니다.<br/> |
|**System Center를 사용하여 Office 365를 모니터링 하기** <br/> |Microsoft System Center를 사용하는 경우 [Office 365용 System Center 관리 팩](https://www.microsoft.com/download/details.aspx?id=43708)을 다운로드하여 Office 365 모니터링을 시작할 수 있습니다. 자세한 지침은 관리 팩 작업 가이드 또는이 블로그 게시물의 [System Center Operations Manager를 사용하여 Office365 모니터링](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)을 참조하세요. <br/> |
|**Azure ExpressRoute**의 상태 모니터링 <br/> |Office 365용 Azure ExpressRoute를 사용하여 Office 365에 연결하는 경우 Azure의 [Azure 리소스 상태로 인한 문제 해결 시간을 단축](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)뿐만 아니라 Office 365 서비스 상태 대시보드도 사용하고 있는지 확인해야 합니다. <br/> |
|**AD FS와 Azure Active Directory Connect Health 사용** <br/> |Office 365에서 Single Sign-On AD FS를 사용하는 경우 Azure AD Connect Health를 사용하여 [AD FS 인프라 모니터링](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)을 시작할 수 있습니다.  <br/> |
|**프로그래밍 방식으로 Office 365 모니터링** <br/> |[Office 365 관리 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)에 대한 지침을 참조하세요.  <br/> |

다음의 간단한 링크를 사용할 수 있습니다. [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>참고 항목

[Office 365 Enterprise 서비스 및 응용 프로그램 구성](configure-services-and-applications.md)
  
[조직에서 Office 365 Enterprise를 사용할 수 있도록 준비](get-your-organization-ready-for-office-365.md)
  
[Office 365의 네트워크 계획 및 성능 조정](network-planning-and-performance.md)
  
[온-프레미스 환경과 Office 365 통합](office-365-integration.md)
  
[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
