---
title: 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 독일 신규 데이터 센터 지역으로의 마이그레이션
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 07/09/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '요약: 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 독일 신규 데이터 센터 지역으로의 마이그레이션 이해 '
ms.openlocfilehash: 3270cb9cf51bc35e7eb7549a109b34c42dda16ff
ms.sourcegitcommit: d34edff71d0b3c8088ec27049f0fc3b6ce57f7e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "45092887"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 독일 신규 데이터 센터 지역으로의 마이그레이션


>[!Note]
>이 문서는 적격 독일/도이칠란드 Microsoft 클라우드 고객에게만 적용 됩니다.
>

## <a name="cloud-service-offerings-in-germany"></a>독일에서 제공되는 클라우드 서비스 

2018년 8월, 보다 원활한 고객의 디지털 변환을 위해 독일의 새로운 클라우드 지역에서 Azure, Office 365, Dynamics 365 및 Power Platform 등을 포함하는 통합 Microsoft 클라우드 서비스 계획을 발표했습니다.  2019년 8월, 독일의 신규 클라우드 지역 출범을 발표합니다.   Azure는 8월부터 Office 365는 12월부터 사용 가능합니다.   Dynamics 365 및 Power Platform은 2020 1분기부터 가능할 것으로 예상됩니다.   

신규 지역은 더 나은 유연성, 최신 인테리전트 클라우드 서비스, 글로벌 크라우드와의 완벽한 연결성 및 데이터 보존을 원하는 진화하는 독일 고객의 니즈를 충족하도록 설계되었습니다.

## <a name="moving-to-the-new-german-regions"></a>신규 독일 지역으로 이전 

기존 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드) 고객은 이제 Office 365, Dynamics 365 고객 참여 및 Power Platform BI 고객 마이그레이션을 시작할 수 있습니다.  첫 번째 단계는 Microsoft 주도 신규 독일 데이터 센터 지역으로의 [마이그레이션에 동의](https://aka.ms/office365germanymoveoptin)하는 것입니다. 

Microsoft 주도 방식에 동의하면 2020년에 마이그레이션 됩니다.  마이그레이션이 되면 핵심 고객 데이터 및 구독정보는 신규 독일 지역으로 이전됩니다.  

Microsoft 주도 방식에 동의하면 다음 서비스도 함께 마이그레이션됩니다.

- Azure Active Directory
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- 비즈니스용 OneDrive
- 비즈니스용 Skype Online

독일 Microsoft 클라우드에서 독일 데이터 센터 지역으로 마이그레이션하는 동안 기존의 비즈니스용 Skype Online 고객은 Microsoft Teams로 이동합니다. 자세한 내용은 [Microsoft Teams 업그레이드 시작하기](https://aka.ms/SkypeToTeams-Home)를 참조하세요.

- Office 365 그룹
- Dynamics 365 / Power Platform

이들 서비스의 마이그레이션의 필요 조건과 영향에 관한 내용은 [Dynamics 365 고객 참여](https://aka.ms/D365ceOptIn) 문서를 참조하세요.

Office 365 비디오가 2021년 3월 1일에 사용 중지됩니다. Office 365 테넌트를 새 독일어 데이터 센터 영역으로 마이그레이션하도록 선택하면 SharePoint Online 마이그레이션이 완료된 후에 Office 365 비디오가 지원되지 않습니다. [자세한 정보](https://docs.microsoft.com/stream/migrate-from-office-365#microsoft-cloud-deutschland-timeline)

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Office 365 서비스 신규 독일 데이터 센터 지역으로의 마이그레이션을 준비하는 방법 

첫 번째 단계는 Microsoft가 여러분의 구독 정보 및 독일/도이칠란드 Microsoft 클라우드 데이터를 Office 365 서비스의 신규 독일 데이터 센터로 마이그레이션 할 수 있도록 승인하는 것입니다.   방법은 [동의 절차를](ms-cloud-germany-migration-opt-in.md) 참조하세요. 

- 모든 고객은 신규 독일 데이터 센터 지역을 포함한 전 세계 [Office 365 URL 및 IP 주소](urls-and-ip-address-ranges.md)를 확인해야 합니다. 
- Office 365 플랫폼 서비스 설명서를 검토하고 독일 지역으로의 이전 후 어떤 기능과 서비스가 제공되는지 확인하세요.   
- 유료 구독을 마이그레이션 합니다.   평가판 구독은 마이그레이션할 수 없습니다.

고객 불편을 최소화 하기 위해 테넌트 마이그레이션은 백 엔드 서비스 작업으로 실행됩니다.    전반적인 마이그레이션 상태와 고객의 추가 작업 필요 여부는 메시지 센터를 통해 전달됩니다.   고객 관리 DNS 업데이트나 Exchange Hybrid 고객에 대한 하이브리드 설정 재구성 등을 위해 고객의 추가 작업이 필요할 수 있습니다. 

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Office 365 서비스 신규 독일 데이터 센터 지역으로 마이그레이션 하는 동안 고객 경험

테넌트 마이그레이션은 최종 고객 및 관리자에 게 최소의 영향을 미치도록 설계되었습니다.  하지만, 각 작업과 관련하여 다음 사항에 유의 하세요.   

### <a name="azure-active-directory"></a>Azure Active Directory

독일 Microsoft 클라우드 Office/Dynamics 구독은 Azure Active Directory (Azure AD) 재배치와 함께 독일 지역으로 전환됩니다.  그런 다음 신규 월드와이드 서비스 구독이 반영되도록 업데이트 됩니다.  구독을 이전하는 잠깐의 시간 동안 구독 변경이 차단됩니다. 

### <a name="exchange-online"></a>Exchange Online

Exchange Online Hybrid 고객은 전환 이전에 하이브리드 구성 마법사를 다시 실행 하여 독일 Microsoft 클라우드에 대한 온프레미스 구성을 업데이트 하고 월드와이드 서비스 정리시 HCW를 재실행 해야 합니다.  사용자 지정 도메인을 사용 하는 고객은 추가 DNS 업데이트가 요구될 수 있습니다. 

사서함은 백 엔드 프로세스로 마이그레이션되며, 사용자는 전환이 진행 되는 동안 독일 Microsoft 클라우드나 독일 지역에 있을 수 있으며, 동일한 Exchange 조직(GAL)에 있습니다. 

### <a name="exchange-online-protection"></a>Exchange Online Protection

백 엔드 Exchange Online Protection 기능은 신규 독일 지역으로 복사됩니다. 

### <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online 마이그레이션이 완료 되면 데이터 인덱스가 다시 작성 됩니다. 검색 인덱스에 종속 된 기능은 인덱스 재작성을 완료 하는 동안 영향을 받을 수 있습니다.

전환된 기존 sharepoint.de URL은 보존 됩니다.

### <a name="onedrive-for-business"></a>비즈니스용 OneDrive

비즈니스용 OneDrive 마이그레이션이 완료 되면 데이터 인덱스가 다시 작성 됩니다. 검색 인덱스에 종속 된 기능은 인덱스 재작성을 완료 하는 동안 영향을 받을 수 있습니다.

### <a name="skype-for-business-online"></a>비즈니스용 Skype Online

기존 비즈니스용 Skype Online 고객은 Microsoft 팀으로 이관 됩니다. 자세한 내용은 [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home)을 참조하세요. 

### <a name="office-365-video"></a>Office 365 비디오
Office 365 비디오의 콘텐츠는 SharePoint Online 마이그레이션의 일부로 마이그레이션됩니다. 그러나 Office 365 비디오는 만료되며 새 독일어 데이터 센터 영역으로 SharePoint Online의 마이그레이션이 완료된 후에 Office 365 비디오가 지원되지 않습니다. Office 365 비디오의 비디오는 SharePoint 마이그레이션 후에 Office 365 비디오 UI에서 재생되지 않습니다.

Microsoft Stream이 독일 Microsoft에 배포되는 것이 아니며 현재 새 독일 데이터 센터 지역에 Microsoft Stream을 배포하기 위한 시간 표시 막대는 없습니다. 따라서 해당 지역에는 Microsoft Stream에 대한 Office 365 비디오의 마이그레이션 도구를 제공하지 않습니다. 사용자의 콘텐츠를 보존하려면 2021년 3월 1일 이전에 콘텐츠를 직접 다운로드하거나 이동시켜야 합니다. [자세한 정보](https://docs.microsoft.com/stream/migrate-from-office-365#microsoft-cloud-deutschland-timeline)


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a>독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)와 Office 365 서비스 신규 독일 데이터 센터 지역과의 주요 차이 


|| 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드) | 신규 독일 데이터 센터 지역에서의 Office 365 서비스 |
|:-------|:-----|:-----|
| 하나의 Office 365 테넌트만으로도 구독 가능한 Microsoft 365 서비스 | 15 개 서비스 (REF 참조) | 29 개 서비스 (REF 참조) |
| 새로운 기능 | 새로운 기능은 제공하지 않습니다.  | 글로벌 Office 365 서비스와 동일한 새로운 기능이 제공됩니다.  |
| 데이터 트러스티 | 예 | 아니요 |
| 글로벌 365 테넌트와 협업  | 아니요 | 예 |
| 고객 데이터 보존 | 고객 데이터는 독일 데이터 센터에만 저장 됩니다. | Microsoft는 독일에서만 다음의 사용자 데이터를 저장합니다: Exchange Online 사서함 콘텐츠(전자 메일 본문, 일정, 전자 메일 첨부 파일), SharePoint Online 사이트 콘텐츠 및 사이트에 저장된 파일, 비즈니스용 OneDrive에 업로드 된 파일.  |
| 적용 약관  | [온라인 서비스 약관](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)[부록 포함](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [온라인 서비스 약관](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a>FAQ

### <a name="is-migration-required"></a>마이그레이션이 필수인가요? 

Office 365 테넌트의 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 신규 독일 데이터 센터 지역으로의 마이그레이션은 무료입니다.   신규 독일 데이터 센터 지역으로의 마이그레이션을 강력히 추천드립니다만 독일 Microsoft 클라우드에도 업데이트 등 계속해서 지원을 제공할 예정입니다.   

Office 365 서비스 신규 독일 데이터 센터 지역의 추가 혜택: 

- 경쟁력 있는 가격의 [Azure](https://azure.microsoft.com/pricing/calculator/),[Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 고객 참여](https://dynamics.microsoft.com/pricing/) 및 [Power BI](https://powerbi.microsoft.com/pricing/)를 제공 합니다. 
- 수많은 네트워크 엣지 사이트, Peering Location, 송신 지점이 있는 Microsoft 글로벌 네트워크에 연결되어 전세계 어디서나 강력한 사용자 환경을 제공합니다.  
- 독일 내 지역 고객 데이터 보관 요구사항을 충족하는데 도움을 줍니다.  
- 최신 버전 서비스 및 Microsoft 팀과 Office 365 Multi-Geo를 포함한 새로운 기능 등 글로벌 클라우드에 포함된 모든 기능이 제공됩니다.   [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](https://docs.microsoft.com/office365/enterprise/o365-data-locations) 및 [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability)의 지역별 상품을 비교하세요. 
- 고객의 준법 및 규정 요구 사항을 충족 할 수 있도록 모든 기능, 엔터프라이즈급 보안 및 종합 기능을 제공 합니다. 
- 기존 온라인 서비스 계약을 통해 사용 가능합니다. 

#### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>여러 Office 365 클라우드 서비스 간에 사용할 수 있는 서비스는 무엇인가요?

Microsoft Cloud Germany(Microsoft Cloud Deutschland) 클라우드 서비스를 통해 다음의 15가지 서비스를 사용할 수 있습니다.  Microsoft Cloud Germany에는 신규 서비스를 추가하지 않고 있습니다. 

1. Exchange Online
2. 고객 Lockbox (Exchange Online)
3. 그룹 (모던 그룹)
4. Delve 프로필
5. Exchange Online Protection
6. ATP (Advanced Threat Protection)
7. Advanced eDiscovery
8. 고급 데이터 관리
9. SharePoint Online
10. 고객 Lockbox (SharePoint Online)
11. 비즈니스용 OneDrive
12. 비즈니스용 Skype
13. Word Online, Excel Online, PowerPoint, OneNote, Visio Online
14. Office 365 Pro Plus
15. Outlook Mobile

현재 새로운 독일 데이터 센터 영역에서 Office 365 서비스의 일부로 29개의 서비스를 사용할 수 있습니다.  계속해서 글로벌 Office 365 서비스와 일관된 새로운 기능과 서비스가 제공될 것입니다. 

1. Exchange Online
2. 고객 Lockbox (Exchange Online)
3. 그룹 (모던 그룹)
4. Delve 프로필
5. MyAnalytics
6. Workplace Analytics
7. Exchange Online Protection
8. ATP (Advanced Threat Protection)
9. Advanced eDiscovery
10. 고급 보안 관리
11. 정보 권한 관리
12. 고급 데이터 관리
13. SharePoint Online
14. 고객 Lockbox (SharePoint Online)
15. 비즈니스용 OneDrive
16. Microsoft Stream
17. 비즈니스용 Skype(마이그레이션 진행 중에 Microsoft Teams로 전환) 
18. 클라우드 PBX
19. PSTN 회의
20. PSTN 통화
21. Microsoft Teams
22. 관리 보고서/사용 현황 보고서
23. Word Online, Excel Online, PowerPoint, OneNote 및 Visio Online
24. Planner
25. Sway
26. Office 365 Pro Plus
27. Outlook Mobile
28. EMS E3 (Azure Active Directory Premium P1 + Intune + 권한 관리 서비스)
29. Yammer Online

### <a name="when-will-migration-happen"></a>언제 마이그레이션 되나요? 

#### <a name="azure"></a>Azure 

지금 Azure 리소스를 다른 지역으로 [마이그레이션](https://docs.microsoft.com/azure/germany/germany-migration-main) 할 수 있습니다.  Office 365, Dynamics 365 및/또는 Power BI와 함께 Azure를 사용 하는 경우 다음 단계를 따르세요.

#### <a name="office-365"></a>Office 365

지금 Microsoft 주도 마이그레이션에 [동의 합니다](https://aka.ms/office365germanymoveoptin).  마이그레이션을 시작할 준비가 되면 Microsoft 365 관리 센터에서 [메시지 센터를](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) 통해 알려 드립니다. 

#### <a name="dynamics-365-and-power-bi"></a>Dynamics 365 및 Power BI

지금 [Dynamics 365 고객 참여](https://aka.ms/D365ceOptIn) 및 [Power BI](https://aka.ms/pbioptin)의 Microsoft 기반 마이그레이션에 동의 하세요.  마이그레이션을 시작할 준비가 되면 Microsoft 365 관리 센터에서 [메시지 센터를](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) 통해 알려 드립니다. 

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a>사용하고 있는 Office 서비스 가격이 변동되나요? 

예. Microsoft의 글로벌 클라우드 지역(신규 데이터 센터 지역 포함)의 가격은 일반적으로 더 저렴합니다. 

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>신규 지역으로 마이그레이션 할 때 도움이 필요하거나 문의 사항이 있으면 어떻게 해야 하나요? 

질문이 있는 경우에는 다음을 통해 연락하거나 파트너에게 문의 할 수 있습니다.

- Azure의 경우 Azure 포털에서 [새 지원 요청을](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) 제출하세요. 
- Office 365의 경우 "도움이 필요하신가요?"를 통해 문의 할 수 있습니다.  [Microsoft 365 관리 센터](https://portal.office.de/) 링크
- Office 365가 있는 Dynamics 365 고객 참여 및 Power BI 고객은 "도움이 필요하신가요?"를 통해 문의 할 수 있습니다.  [Microsoft 365 관리 센터](https://portal.office.de/) 링크 Dynamics 365 고객 참여 지원은 [여기](https://docs.microsoft.com/dynamics365/get-started/support/)를 이용하세요.  Power BI 지원은 [여기](https://powerbi.microsoft.com/support/)를 이용하세요. 

## <a name="more-information"></a>추가 정보

- [Microsoft Cloud Deutschland 마이그레이션 지원](https://aka.ms/germanymigrateassist)
- [마이그레이션에 대해 옵트인하는 방법](https://aka.ms/office365germanymoveoptin)
- [Dynamics 365 마이그레이션 프로그램 정보](https://aka.ms/D365ceOptIn)
- [Power BI 마이그레이션 프로그램 정보](https://aka.ms/pbioptin)
- [Office 365 URL 및 IP 주소 범위](https://aka.ms/o365endpoints)
- [Office 365 하이브리드 구성 마법사](https://aka.ms/HybridWizard)
- [Microsoft Teams 업그레이드 시작하기](https://aka.ms/SkypeToTeams-Home)
