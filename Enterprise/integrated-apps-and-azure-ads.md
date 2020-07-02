---
title: Microsoft 365 관리자를 위한 통합 된 앱 및 Azure AD
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: O365 통합 앱이 Azure AD에서 등록 되 고 관리 되는 방법 알아보기
ms.openlocfilehash: 0cb3ac73230e0ddce62366af9019a12ea2b04d09
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998093"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Microsoft 365 관리자를 위한 통합 된 앱 및 Azure AD

통합 앱을 [설정 하거나 해제](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)하는 것 보다 통합 앱을 관리 하는 것이 더 많습니다. Microsoft 365 REST Api의 등장으로 사용자는 메일, 일정, 연락처, 사용자, 그룹, 파일 및 폴더와 같은 Microsoft 365 데이터에 대 한 액세스 권한을 앱에 부여할 수 있습니다. 기본적으로 사용자는 각 앱에 개별적으로 사용 권한을 부여 해야 하지만, 전역 관리자 수준에서 앱을 한 번 인증 하 고 앱 시작 관리자를 통해 전체 조직에 배포 하려는 경우에는 제대로 확장 되지 않습니다. 이 작업을 수행 하려면 Azure AD에 앱을 등록 해야 합니다. Azure AD에 앱을 등록 하 고 Microsoft 365 조직에서 앱을 관리 하는 데 도움이 되는 정보를 확인 하기 위해 수행 해야 하는 몇 가지 단계가 있습니다. 이 문서에서는 이러한 리소스를 안내 합니다.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Microsoft 365 관리자를 위한 Azure AD 리소스

Azure AD에서 Microsoft 365 앱을 관리 하려면 먼저 이러한 두 가지 절차를 수행 해야 합니다.
  
|**필수 구성 요소**|**Comments**|
|:-----|:-----|
|[무료 Azure Active Directory 구독 사용](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |Microsoft 365에 대 한 모든 유료 구독에는 Azure Active Directory (Azure AD)에 대 한 무료 구독이 제공 됩니다. Azure AD를 사용 하 여 앱을 관리 하 고 사용자 및 그룹 계정을 만들고 관리할 수 있습니다. Azure AD를 사용 하려면 Azure 포털로 이동 하 여 Microsoft 365 계정을 사용 하 여 로그인 하기만 하면 됩니다.  <br/> |
|[통합 앱 설정 또는 해제](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |타사 앱에서 Microsoft 365 정보에 액세스 하 고 Azure AD에 앱을 등록 하기 위해 통합 앱을 사용 하도록 설정 해야 합니다. 예를 들어 다른 사용자가 타사 앱을 사용 하는 경우 해당 앱은 자신의 일정에 액세스 하 고 비즈니스용 OneDrive 폴더에 있는 파일을 편집 하는 권한을 요청할 수 있습니다.  <br/> |
   
Microsoft 365 앱을 관리 하려면 Azure AD의 앱에 대 한 지식이 있어야 합니다. 이러한 문서는 필요한 배경을 제공 하는 데 도움이 됩니다.
  
|**배경 문서**|**Comments**|
|:-----|:-----|
|[Microsoft 365 앱 시작 관리자를 충족 합니다.](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |앱 시작 관리자를 처음 사용 하는 경우에는이 문서가 무엇 인지 궁금할 것 이며 사용할 수 있습니다. 앱 시작 관리자는 Microsoft 365의 모든 위치에서 앱을 가져올 수 있도록 디자인 되었습니다.  <br/> |
|[Office 365 관리 Api 개요](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |Microsoft 365 Api를 사용 하면 사용자가 관심 있는 항목 (메일, 일정, 연락처, 사용자 및 그룹, 파일, 폴더)을 포함 하 여 Microsoft 365 데이터에 대 한 액세스를 제공할 수 있습니다. 이 문서에서는 Microsoft 365 앱, Azure AD 및 앱이 액세스 하는 데이터 간의 관계를 보여 주는 적절 한 다이어그램을 제공 합니다.  <br/> |
|[Azure Active Directory에서 응용 프로그램 통합](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Azure AD와 통합 된 응용 프로그램 및 응용 프로그램을 등록 하 고, 등록 된 응용 프로그램의 개념을 이해 하 고, 다중 테 넌 트 응용 프로그램에 대 한 브랜딩 지침에 대해 알아봅니다.  <br/> |
|[앱 시작 관리자에 사용자 지정 타일 추가](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |Microsoft 365의 앱 시작 관리자를 사용 하면 사용자가 앱을 보다 쉽게 찾고 액세스할 수 있습니다. 이 문서에서는 개발자가 앱을 사용자의 앱 평가판에 표시 하 고 Microsoft 365 자격 증명을 사용 하 여 SSO (single sign-on) 환경에 제공 하는 방법에 대해 설명 합니다.  <br/> |
|[Azure Active Directory 통합 자습서](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |이 자습서의 목표는 타사 SaaS 응용 프로그램에 대해 Azure AD SSO를 구성 하는 방법을 보여 주기 위한 것입니다.  <br/> |
|[Azure AD에 대한 인증 시나리오](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD는 OAuth 2.0 및 OpenID Connect와 같은 업계 표준 프로토콜을 지원 하 고 코딩을 빠르게 시작 하는 데 도움이 되는 다양 한 플랫폼용으로 공개 된 원본 라이브러리를 제공 하 여 개발자를 위한 인증을 간소화 합니다. 이 문서는 Azure AD에서 지 원하는 다양 한 시나리오를 이해 하 고 시작 하는 방법을 보여 줍니다.  <br/> |
|[응용 프로그램 액세스](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD를 사용 하면 오늘날 인기 있는 소프트웨어 (SaaS) 응용 프로그램으로 간편 하 게 통합할 수 있습니다. id 및 액세스 관리를 제공 하 고, 사용자가 액세스 하는 응용 프로그램에 액세스할 수 있는 위치를 검색 하 고 SSO를 사용 하 여 응용 프로그램에 액세스 하는 데 사용할 수 있는 액세스 패널을 전달 합니다. 이 문서에서는 Azure AD에 대 한 응용 프로그램 액세스 향상 기능에 대해 자세히 알아보고 해당 리소스에 기여할 수 있는 방법을 설명 하는 관련 리소스로 연결 되는 링크를 제공 합니다.  <br/> |
|[Office 365 환경 개인 설정](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Microsoft 365 앱 시작 관리자에서 앱을 추가 또는 제거 하 여 매일 사용 하는 앱에 빠르게 액세스 하도록 할 수 있습니다.  <br/> |
   

