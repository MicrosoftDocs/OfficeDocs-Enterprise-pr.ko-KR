---
title: Office 365 관리자를 위한 통합된 앱 및 Azure AD
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/19/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: O365 앱을 통합 하는 방법에 대해 알아봅니다 등록 되 고 Azure AD의 관리
ms.openlocfilehash: 6edf22261a40563227862908302d519a7edd6419
ms.sourcegitcommit: 7be23a03daeb42c156220efe7b2112938438ee82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2018
ms.locfileid: "26618874"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Office 365 관리자를 위한 통합된 앱 및 Azure AD

이 [기능을 통합 된 응용 프로그램 설정 또는 해제](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)를 방금 보다 통합된 앱을 관리 합니다. Office 365 REST Api의 등장, 사용자가 메일, 일정, 연락처, 사용자, 그룹, 파일 및 폴더와 같은 자신의 Office 365 데이터에 대 한 응용 프로그램 액세스를 부여할 수 있습니다. 기본적으로 사용자를 개별적으로 각 응용 프로그램에 사용 권한을 부여 해야 하지만 전역 관리자 수준에서 한번 앱 권한을 부여 하 고 응용 프로그램 시작 관리자를 통해 전체 조직에 제공 하려는 경우에이 수직 확장 하지 않습니다. 이 작업을 수행 Azure AD에 앱을 등록 해야 합니다. 다음과 같은 Azure AD에 응용 프로그램을 등록할 수 및 Office 365 조직에서 앱을 관리 하는데 도움이 되는 일부 배경 정보가 알고 있어야 하는 전에 수행 해야하는 단계를 수행 합니다. 이 문서는 이러한 리소스를 안내합니다.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Office 365 관리자를 위한 azure AD 리소스

Azure AD에서 Office 365 앱을 관리 하려면 먼저 다음 두 절차를 수행 해야 합니다.
  
|**필수 구성 요소**|**설명**|
|:-----|:-----|
|[무료 Azure Active Directory 구독에 등록](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Office 365에 모든 유료 구독 무료 구독 함께 Azure Active Directory를 제공합니다. 앱을 관리 하 고 사용자 및 그룹 계정을 만들고 관리 하 Azure AD를 사용할 수 있습니다. 이 구독 활성화 하 고 Azure 관리 포털에 액세스 하려면 일회성 등록 프로세스를 완료 해야 합니다. 그런 다음 Office 365 관리 센터에서 Azure AD로 이동할 수 있습니다.  <br/> |
|[통합 앱 설정 또는 해제](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |제 3 자 apps가 Office 365 정보에 액세스를 허용 하도록 사용자를 위한 및 Azure AD에 앱을 등록 하 통합 앱 설정 해야 합니다. 예, 타사 응용 프로그램을 사용 하 여 다른 사용자 경우 해당 앱을 요청할 수 있습니다. 권한에 대 한 비즈니스 폴더에 대 한 OneDrive에 있는 파일을 편집 하 고 자신의 일정에 액세스할 수 있습니다.  <br/> |
   
Office 365 응용 프로그램 관리를 사용 하면 Azure AD에서 앱에 대 한 지식을 해야 합니다. 이러한 문서는 필요한 배경을 사용 하면 도움이 됩니다.
  
|**배경 문서**|**설명**|
|:-----|:-----|
|[Office 365 응용 프로그램 시작 관리자를 충족 합니다.](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |응용 프로그램 시작 관리자의 새로운 기능에 없을 수 궁금할 것이 고 사용 하는 방법입니다. 응용 프로그램 시작 관리자는 어디에서 든 지 앱을 얻을 수 있도록 설계 된 Office 365에서 합니다.  <br/> |
|[추가, 업데이트 및 응용 프로그램을 제거](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |이 항목에서는 추가, 업데이트 하 고, 또는 Azure Active Directory에서 응용 프로그램을 제거 하는 방법을 보여줍니다. 다양 한 유형의 Azure AD와 통합 될 수 있는 응용 프로그램에 대해 배웁니다 및 api (영문), 웹 등 다른 리소스에 액세스할 수 있는 응용 프로그램을 구성 하는 방법입니다.  <br/> |
|[Office 365 응용 프로그램 시작 관리자에 표시 되는 앱을 포함](https://go.microsoft.com/fwlink/?LinkId=617138)합니다.  <br/> |쉽게 찾고 자신의 앱에 액세스 하는 사용자를 위한 Office 365에서 응용 프로그램 시작 관리자입니다. 이 문서에서는 사용자의 앱 아이콘에 표시 되 고도 Office 365 자격 증명을 사용 하 여 single sign on (SSO) 경험을 제공 하도록 앱을 얻을 수 개발자로 서 하는 방법에 설명 합니다.  <br/> |
|[Office 365 api (영문) 플랫폼 개요 (영문)](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Office 365 Api를 사용 하면 가장 관심 항목을 포함 하는 고객의 Office 365 데이터에 대 한 액세스를 제공할 수-자신의 메일, 일정, 연락처, 사용자 및 그룹, 파일 및 폴더입니다. Office 365 앱, Azure AD 간의 관계를 설명 하는이 문서의 좋은 다이어그램 방법이 및 응용 프로그램에 액세스 하는 데이터입니다.  <br/> |
|[Azure Active Directory에서 응용 프로그램 통합 (영문)](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Azure Active Directory 및 응용 프로그램을 등록, 등록 된 응용 프로그램 관련 된 개념을 이해 하 고 브랜딩 지침에 대 한 다중 테 넌 트 응용 프로그램에 설명 하는 방법과 통합 하는 응용 프로그램에 알아봅니다.  <br/> |
|[Azure Active Directory 통합 자습서](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |이 자습서의 목적은 타사 SaaS 응용 프로그램에 대 한 Azure AD SSO를 구성 하는 방법을 보여줍니다.  <br/> |
|[Azure AD에 대 한 인증 시나리오](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD 인증 개발자를 위한 업계 표준 프로토콜에 예: OAuth 2.0 및 OpenID 연결에 대 한 지원이 포함 된 서비스로 서 id를 제공 하 여 간소화 것은 물론 신속 하 게 코딩을 시작할 수 있도록 서로 다른 플랫폼에 대 한 소스 라이브러리를 엽니다. 이 문서에서는 Azure AD를 지원할 뿐 이며 시작 하는 방법을 설명 하는 다양 한 시나리오에 설명 합니다.  <br/> |
|[응용 프로그램 액세스](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD에는 서비스 (SaaS) 응용 프로그램;으로 쉽게 통합을 다양 한 오늘날의 인기 있는 소프트웨어를 사용할 수 있습니다. id 및 액세스 관리를 제공 배우고 해당 사용자에 대 한 액세스 패널은는 어떤 응용 프로그램 액세스를 검색할 수 있고 SSO를 사용 하 여 해당 응용 프로그램에 액세스할 수 있습니다. 이 문서에서는 Azure AD에 대 한 응용 프로그램 액세스 기능 향상 및 자신에 게 기여할 수 있는 방법에 대 한 자세한 내용은 사용할 수 있는 관련된 리소스에 대 한 링크를 제공 합니다.  <br/> |
|[Office 365 경험을 개인 설정](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |매일을 사용 하 여 추가 (영문) 또는 Office 365 응용 프로그램 시작 관리자에서 앱을 제거 하 여 앱에 대 한 빠른 액세스를 얻을 수 있습니다.  <br/> |
   

