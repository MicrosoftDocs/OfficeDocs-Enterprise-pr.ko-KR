---
title: Office 365 테넌트 간 공동 작업
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: 테 넌 트 및 조직에서 Office 365 공동 작업을 작동 하는 방법을 알아봅니다.
ms.openlocfilehash: e7823927b6e1987c27924bdae34cf439a50db296
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843629"
---
# <a name="office-365-inter-tenant-collaboration"></a>Office 365 테넌트 간 공동 작업

이 문서에서는 두 Office 365 테 넌 트 간에 공동 작업을 수행 하는 여러 가지 방법을 설명 합니다. Office 365 관리자를 위한 것입니다.
  
Fabrikam 및 Contoso 라는 두 조직에는 각각 비즈니스 테 넌 트에 대 한 Office 365이 있고 여러 프로젝트에서 공동 작업 하려는 경우를 가정해 보겠습니다. 일부는 제한 된 시간 동안 실행 되며 일부는 진행 중입니다. Fabrikam 및 Contoso에서 사용자와 팀이 안전한 방식으로 다른 Office 365 테 넌 트를 통해 보다 효율적으로 공동 작업을 수행할 수 있도록 하는 방법 Azure Active Directory B2B 공동 작업과 함께 제공 되는 Office 365에는 몇 가지 옵션이 있습니다. 이 문서에서는 Fabrikam 및 Contoso에서 고려할 수 있는 몇 가지 주요 시나리오에 대해 설명 합니다.
  
Office 365 테 넌 트 공동 작업 옵션에는 파일 및 대화에 대 한 중앙 위치 사용, 일정 공유, IM 사용, 통신을 위한 오디오/비디오 통화, 리소스 및 응용 프로그램에 대 한 액세스 보호 등이 포함 됩니다. 다음 표를 사용 하 여 솔루션을 선택 하 고 자세한 정보를 확인 하세요.
  
## <a name="exchange-online-collaboration-options"></a>Exchange Online 공동 작업 옵션

|**공유 목표**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|다른 Office 365 조직과 일정 공유  <br/> |관리자는 Exchange Online에서 다양 한 수준의 일정 액세스를 설정 하 여 기업이 다른 기업과 공동 작업을 할 수 있도록 하 고 사용자가 다른 사용자와 일정 (약속 있음/없음 정보)을 공유 하도록 할 수도 있습니다.  <br/> |[Exchange Online에서 공유](https://technet.microsoft.com/library/jj916670%28v=exchg.150%29.aspx) <br/> [Exchange Online의 조직 관계](https://technet.microsoft.com/library/jj916658%28v=exchg.150%29.aspx) <br/> [Exchange Online에서 조직 관계 만들기](https://technet.microsoft.com/library/jj916671%28v=exchg.150%29.aspx) <br/> [Exchange Online의 조직 관계 수정 및 관리](https://technet.microsoft.com/library/jj916659%28v=exchg.150%29.aspx) <br/> [Exchange Online에서 조직 관계 제거](https://technet.microsoft.com/library/jj916657%28v=exchg.150%29.aspx) <br/> [외부 사용자와 사이트 공유](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|사용자가 조직 외부의 사용자와 일정을 공유 하는 방법 제어  <br/> |관리자가 사용자 사서함에 공유 정책을 적용 하 여 공유할 수 있는 사람 및 부여 된 액세스 수준 제어  <br/> |[Exchange Online에서 정책 공유](https://technet.microsoft.com/library/jj916673%28v=exchg.150%29.aspx) <br/> [Exchange Online에서 공유 정책 만들기](https://technet.microsoft.com/library/jj916676%28v=exchg.150%29.aspx) <br/> [Exchange Online의 사서함에 공유 정책 적용](https://technet.microsoft.com/library/jj916672%28v=exchg.150%29.aspx) <br/> [Exchange Online에서 공유 정책 수정, 사용 안 함 또는 제거](https://technet.microsoft.com/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|보안 전자 메일 채널 구성 및 파트너 조직과의 메일 흐름 제어  <br/> |관리자는 커넥터를 만들어 파트너 조직 또는 서비스 공급자와의 메일 교환에 보안을 적용 합니다. 커넥터는 TLS (전송 계층 보안)를 통해 암호화를 적용 하 고, 파트너가 보낸 전자 메일을 보내는 도메인 이름 또는 IP 주소 범위에 대 한 제한도 허용 합니다.  <br/> |[Office 365의 전자 메일 연결 보안을 위해 Exchange Online에서 TLS를 사용하는 방법](https://technet.microsoft.com/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Exchange Online의 원격 도메인](https://technet.microsoft.com/library/jj966211%28v=exchg.150%29.aspx) <br/> [파트너 조직과의 보안 메일 흐름을 위한 커넥터 설정](https://technet.microsoft.com/library/dn751021%28v=exchg.150%29.aspx) <br/> [Exchange Online 및 Office 365에 대 한 메일 흐름 모범 사례 (개요)](https://technet.microsoft.com/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online 및 비즈니스용 OneDrive 공동 작업 옵션

|**목표 공유**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|외부 사용자와 사이트 및 문서 공유  <br/> |관리자가 테 넌 트 또는 Microsoft 계정 인증, 회사 또는 학교 계정 인증 또는 게스트 계정에 대 한 사이트 모음 수준에서 공유를 구성 합니다.  <br/> |[SharePoint Online 환경에 대해 외부 공유 관리](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Office 365 SharePoint Online 및 비즈니스용 OneDrive의 제한 된 도메인 공유](https://support.office.com/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [SharePoint Online을 B2B (business to business) 엑스트라넷 솔루션으로 사용](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|최종 사용자에 대 한 외부 공유 추적 및 제어  <br/> |비즈니스용 OneDrive 파일 소유자 및 SharePoint Online 최종 사용자 사이트 및 문서 공유를 구성 하 고 공유를 추적 하도록 알림을 설정 합니다.  <br/> |[비즈니스용 OneDrive에 대 한 외부 공유에 대 한 알림 구성](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Office 365에서 SharePoint 파일 또는 폴더 공유](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>비즈니스용 Skype 공동 작업 옵션

|**공유 목표**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|비즈니스용 skype Online-메신저 대화, 통화 및 현재 상태와 기타 비즈니스용 Skype 사용자  <br/> |관리자는 비즈니스용 Skype Online 사용자가 IM으로 사용 하도록 설정 하 고, 오디오/비디오 통화를 수행 하 고, 다른 Office 365 테 넌 트에서 사용자에 게 현재 상태를 볼 수 있습니다.  <br/> |[사용자가 외부 비즈니스용 Skype 사용자와 연락하도록 허용](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|비즈니스용 skype Online-IM, 통화 및 현재 상태를 Skype (소비자) 사용자와 함께 사용  <br/> |관리자는 비즈니스용 Skype 온라인 사용자가 IM을 사용 하도록 설정 하 고 전화를 걸고, Skype (소비자) 사용자에 게 현재 상태를 볼 수 있습니다.  <br/> |[비즈니스용 Skype 사용자가 Skype 대화 상대를 추가할 수 있도록 허용](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B 공동 작업 옵션

|**공유 목표**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|Azure AD B2B 공동 작업-조직의 디렉터리에 있는 그룹에 외부 사용자를 추가 하 여 콘텐츠 공유  <br/> |한 Office 365 테 넌 트에 대 한 전역 관리자는 다른 Office 365 테 넌 트의 사용자를 자신의 디렉터리에 참가 하도록 초대 하 고, 해당 사용자를 그룹에 추가 하 고, 그룹에 대 한 SharePoint 사이트 및 라이브러리와 같은 콘텐츠에 대 한 액세스 권한을 부여할 수 있습니다.  <br/> |[Azure AD B2B 공동 작업 미리 보기 란?](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B: 새로운 업데이트가 비즈니스에 collab 쉽게 수행 됩니다.](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Office 365 외부 공유 및 Azure Active Directory B2B 공동 작업](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B 공동 작업 API 및 사용자 지정](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD 및 Id 표시: Azure AD B2B 공동 작업 (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Office 365 공동 작업 옵션

|**공유 목표**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|Office 365 그룹-전자 메일, 일정, OneNote 및 공유 파일을 중앙 위치에 저장  <br/> |비즈니스 Essentials, 비즈니스 프리미엄, 교육 및 Enterprise E1, E3 및 E5 요금제에서 그룹을 지원 합니다. 한 Office 365 테 넌 트의 사용자는 그룹을 만들고 다른 Office 365 테 넌 트의 사용자를 게스트 사용자로 초대할 수 있습니다. Dynamics CRM에도 적용 됩니다.  <br/> |[Office 365 그룹에 대 한 자세한 정보](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Office 365 그룹의 게스트 액세스](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Office 365 그룹 배포](https://technet.microsoft.com/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Yammer 공동 작업 옵션

|**공유 목표**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|Yammer-엔터프라이즈 소셜 미디어를 통한 공동 작업  <br/> |외부 그룹을 만드는 기능이 Yammer 관리자에 의해 사용 하지 않도록 설정 된 경우 사용자는 외부 그룹을 만들어 대화를 통해 Yammer에서 공동 작업 하 고, 좋아요를 수행 하 고, 파일을 공유 하 고, 온라인으로 채팅을 수행할 수 있습니다.  <br/> |[Yammer의 외부 그룹 만들기 및 관리](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>팀 공동 작업 옵션

|**공유 목표**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|조직 외부의 사용자와 팀 공동 작업  <br/> |팀에서 외부 공동 작업을 사용 하도록 설정 하려면 Office 365 테 넌 트 초대를 위한 전역 관리자가 필요 합니다. 전역 관리자 및 팀 소유자는 이제 전자 메일 주소를 사용 하 여 모든 사용자에 게 팀 공동 작업을 초대할 수 있습니다.  <br/> 관리자는 또한 이미 테 넌 트에 있는 게스트를 관리 하 고 편집할 수 있습니다.  <br/> |[게스트 액세스 권한 부여](https://docs.microsoft.com/microsoftteams/teams-dependencies) <br/> [팀에서 게스트 액세스 설정 또는 해제](https://docs.microsoft.com/microsoftteams/set-up-guests) <br/> [PowerShell을 사용 하 여 게스트 액세스 제어](https://docs.microsoft.com/microsoftteams/guest-access-powershell) <br/> [게스트 액세스 검사 목록](https://docs.microsoft.com/microsoftteams/guest-access-checklist) <br/> [게스트 사용자 보기](https://docs.microsoft.com/microsoftteams/view-guests) <br/> [게스트 사용자 정보 편집](https://docs.microsoft.com/microsoftteams/edit-guests-information) <br/> |
|팀 소유자는 팀 내에서 게스트가 공동 작업을 수행 하는 방법을 초대 및 관리할 수 있습니다.  <br/> |팀 소유자는 팀 내에서 게스트에 대해 수행할 수 있는 작업에 대 한 추가 컨트롤을 보유 합니다.  <br/> |[게스트 추가](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [팀에 게스트 추가](https://docs.microsoft.com/microsoftteams/add-guests) <br/> [팀에서 게스트 액세스 관리](https://docs.microsoft.com/microsoftteams/manage-guests) <br/> [팀 또는 채널의 사용자 확인](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|다른 테 넌 트의 게스트는 팀의 콘텐츠를 보고 다른 구성원과 공동 작업을 수행할 수 있습니다.  <br/> |없음  <br/> |[게스트 액세스 환경](https://docs.microsoft.com/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Power BI 공동 작업 옵션

|**공유 목표**|**관리 작업**|**방법 정보**|
|:-----|:-----|:-----|
|Power BI에서는 외부 게스트 사용자가 링크를 통해 공유 되는 콘텐츠를 사용할 수 있습니다. 이렇게 하면 조직의 사용자가 조직 간에 안전한 방식으로 콘텐츠를 배포할 수 있습니다.<br/> | Power BI 관리자는 사용자가 외부 사용자를 초대 하 여 조직 내의 콘텐츠를 볼 수 있는지 여부를 제어할 수 있습니다. <br/> |[Azure AD B2B를 사용 하 여 외부 게스트 사용자에 게 Power BI 콘텐츠 배포](https://docs.microsoft.com/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Office 365 테 넌 트 간 공동 작업에 대해 염두에 두어야 하는 사항

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>사용자 계정, 라이선스, 구독 및 저장소 공유

각 조직은 자체 사용자 계정, id, 보안 그룹, 구독, 라이선스 및 저장소를 유지 관리 합니다. 사용자는 Office 365의 공동 작업 기능을 공유 정책 및 보안 설정과 함께 사용 하 여 회사 자산의 제어권을 유지 하면서 필요한 정보에 대 한 액세스를 제공 합니다.
  
- **사용자 계정:** 계정을 공유할 수 없으며 온-프레미스 Active Directory 디렉터리 서비스의 테 넌 트 또는 파티션 간에 계정을 복제할 수 없습니다. 
    
- **라이선스 &amp; 구독:** Office 365에서는 라이선스 요금제 (Sku 또는 Office 365 요금제 라고도 함)의 라이선스를 사용자에 게 해당 요금제에 대해 정의 된 Office 365 서비스에 대 한 액세스 권한을 부여 합니다. 
    
- **저장소:** Office 365 계획에서 SharePoint Online에 대 한 소프트웨어 경계와 제한은 사서함 저장 용량 제한과 별개로 관리 됩니다. 사서함 저장소 제한은 Exchange Online을 사용 하 여 설정 및 관리 됩니다. 두 시나리오에서 저장소는 상호 테 넌 트를 공유할 수 없습니다. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Office 365 테 넌 트에서 도메인 네임 스페이스를 공유할 수 있나요?

아니요. Fabrikam.com 또는 tailspintoys.com와 같은 베 니 티 도메인은 한 번에 하나의 테 넌 트 에서만 연결 하 여 사용할 수 있습니다. 각 테 넌 트에는 자체 네임 스페이스가 있어야 합니다. UPN, SMTP 및 SIP 네임 스페이스는 테 넌 트 간에 공유할 수 없습니다.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>하이브리드 구성 요소 및 Office 365 테 넌 트 간 공동 작업에 대 한 자세한 내용은 무엇 인가요?

Exchange 조직과 Azure AD Connect와 같은 온-프레미스 하이브리드 구성 요소는 여러 테 넌 트 간에 분할 될 수 없습니다.
  

