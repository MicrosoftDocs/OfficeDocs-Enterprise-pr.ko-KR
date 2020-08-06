---
title: Microsoft 365 연결 모니터링
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
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
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Microsoft 365을 배포한 후에는 아래의 일부 도구 및 기법을 사용 하 여 Microsoft 365 연결을 유지할 수 있습니다. 저속 네트워크에서 Microsoft 365을 사용 하기 위한 최상의 방법과 공식적인 서비스 상태 및 연속성 지침을 이해 하는 것이 좋습니다.
ms.openlocfilehash: aa47ff76f70e48285c6ca5f21ffdf30f1db52521
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571011"
---
# <a name="monitor-microsoft-365-connectivity"></a>Microsoft 365 연결 모니터링

Microsoft 365을 배포한 후에는 아래의 일부 도구 및 기법을 사용 하 여 Microsoft 365 연결을 유지할 수 있습니다. [저속 네트워크에서 Microsoft 365을 사용 하기 위한 최상의 방법과](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)공식적인 [서비스 상태 및 연속성](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) 지침을 이해 하는 것이 좋습니다. [Microsoft 365 admin 앱](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) 을 가져오고 [microsoft 365 For Business-admin 도움말](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)을 책갈피로도 할 예정입니다.
  
## <a name="monitoring-microsoft-365-connectivity"></a>Microsoft 365 연결 모니터링

|||
|:-----|:-----|
|**새 Microsoft 365 끝점에 대 한 알림 받기** <br/> |[Microsoft 365 끝점을 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)하는 경우 새 끝점을 게시할 때 알림을 받으려면 즐겨찾기 rss 수집기를 사용 하 여 rss 피드를 구독 하면 됩니다. 다음은 Outlook을 [통해 구독](https://go.microsoft.com/fwlink/p/?LinkId=532416) 하거나 [RSS 피드 업데이트를 전자 메일로 보낼](https://go.microsoft.com/fwlink/p/?LinkId=532417)수 있도록 하는 방법입니다.  <br/> |
|**System Center를 사용 하 여 Microsoft 365 모니터링** <br/> |Microsoft System Center를 사용 하는 경우 [에는 Office 365 용 System Center 관리 팩](https://www.microsoft.com/download/details.aspx?id=43708) 을 다운로드 하 여 microsoft 365 오늘 모니터링을 시작할 수 있습니다. 자세한 내용은 [System Center Operations Manager를 사용 하 여](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) 관리 팩 작업 가이드 또는이 블로그 게시물 Office365 모니터링을 참조 하세요. <br/> |
|**Azure ExpressRoute**의 상태 모니터링 <br/> |Microsoft 365에 대 한 Azure Express 경로를 사용 하 여 Microsoft 365에 연결 하는 경우 azure [리소스 상태에서 문제 해결 시간을 줄이기](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) 위해 Microsoft 365 서비스 상태 대시보드 및 azure를 모두 사용 하 고 있는지 확인 해야 합니다. <br/> |
|**AD FS와 Azure Active Directory Connect Health 사용** <br/> |Microsoft 365을 사용 하 여 Single Sign-on 용 AD FS를 사용 하는 경우 [AZURE Ad Connect Health를 사용 하 여 AD fs 인프라를 모니터링](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)하는 것이 좋습니다.  <br/> |
|**프로그래밍 방식으로 Microsoft 365 모니터링** <br/> |[Microsoft 365 관리 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)에 대 한 지침을 참조 하세요.  <br/> |

다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 서비스 및 응용 프로그램 구성](configure-services-and-applications.md)
  
[조직이 Microsoft 365 Enterprise를 사용할 수 있도록 준비](get-your-organization-ready-for-office-365.md)
  
[Microsoft 365의 네트워크 계획 및 성능 조정](network-planning-and-performance.md)
  
[Microsoft 365 통합 온-프레미스 환경](office-365-integration.md)
  
[Microsoft 365 끝점 관리](managing-office-365-endpoints.md)
