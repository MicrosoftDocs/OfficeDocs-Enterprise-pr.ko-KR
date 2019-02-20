---
title: Office 365와 Azure 통합
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 구독에는 Azure AD에 대 한 구독이 포함 되어 있습니다. 온-프레미스 환경에 대 한 암호 동기화 또는 single sign-on을 사용 하려면 Office 365와 Azure AD를 통합 합니다.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085477"
---
# <a name="azure-integration-with-office-365"></a>Office 365와 Azure 통합

Office 365에서는 azure Active Directory (azure AD)를 사용 하 여 백그라운드에서 사용자 id를 관리 합니다. office 365 구독에는 azure ad에 대 한 무료 구독이 포함 되어 있어 암호를 동기화 하거나 single sign-on을 온-프레미스 환경에 설정 하려는 경우 azure ad와 office 365를 통합할 수 있습니다. 계정을 보다 효율적으로 관리 하기 위해 고급 기능을 구입할 수도 있습니다.
  
Azure는 또한 Office 365 구독을 확장 및 사용자 지정 하는 데 사용할 수 있는 통합 앱 관리 등의 기타 기능을 제공 합니다.
  
Azure AD 배포 관리자는 다음과 같은 안내 설치 및 구성 환경에 사용할 수 있습니다.
 - [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync)
 - [AD FS 배포 관리자](https://aka.ms/adfsguidance)
 - [Azure RMS 배포 마법사](https://aka.ms/azuremsguidance)
 - [Azure AD Premium 설정 가이드](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD edition 및 Office 365 id 관리

Office 365에 대 한 유료 구독을 사용 하는 경우 Azure AD에 대 한 무료 구독도 제공 됩니다. Azure AD를 사용 하 여 사용자 및 그룹 계정을 만들고 관리할 수 있습니다. 이 구독을 활성화 하려면 일회용 등록을 완료 해야 합니다. 나중에 Office 365 관리 포털에서 Azure AD에 액세스할 수 있습니다. 자세한 내용은 [무료 Azure AD 구독 등록](https://go.microsoft.com/fwlink/p/?LinkId=617127)을 참조 하십시오. 
  
> [!TIP]
> 위의 지침에 따라 Office 365 구독에 제공 된 무료 Azure AD 구독을 등록 합니다. 등록을 위해 azure.microsoft.com로 직접 이동 하지 마세요. 또는 Office 365 용 무료 프로그램과는 별도의 microsoft azure 평가판 또는 유료 구독을 사용할 수 있습니다. 
  
무료 구독을 사용 하 여 온-프레미스 디렉터리와 동기화 하 고 single sign-on을 설정 하 고, Salesforce, DropBox 등의 다양 한 소프트웨어와 서비스 응용 프로그램을 동기화 할 수 있습니다.
  
향상 된 AD DS 기능, 양방향 동기화 및 기타 관리 기능을 사용 하려면 무료 구독을 유료 프리미엄 구독으로 업그레이드 하면 됩니다. 자세한 내용은 [Azure Active Directory 버전](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)을 참조 하세요.
  
office 365 및 azure AD에 대 한 자세한 내용은 [office 365 id 및 azure Active Directory 이해](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)를 참조 하세요.
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Office 365 테 넌 트의 기능 확장

|**기능**|**설명**|
|:-----|:-----|
|통합 앱  <br/> |개별 앱에 메일, 일정, 연락처, 사용자, 그룹, 파일 및 폴더와 같은 Office 365 데이터에 대 한 액세스 권한을 부여할 수 있습니다. 또한 전역 관리자 수준에서 이러한 앱에 권한을 부여 하 고 Azure AD에 앱을 등록 하 여 전체 회사에서 사용할 수 있도록 설정할 수도 있습니다. 자세한 내용은 [Office 365 관리자를 위한 통합 앱 및 Azure AD를](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)참조 하세요.<br/> [Azure AD 응용 프로그램 갤러리 및 single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604)도 참조 하세요.  <br/> |
|PowerApps  <br/> | Power apps는 SharePoint 목록 및 기타 데이터 앱과 같은 기존 데이터 원본에 연결할 수 있는 모바일 장치용으로 중요 한 앱입니다. 자세한 내용은 SharePoint Online 및 [PowerApps 페이지](https://powerapps.microsoft.com/) [에서 목록에 대 한 PowerApp 만들기](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) 를 참조 하세요.<br/> |
   
Microsoft Cloud 및 Office 365에 대 한 기타 리소스는 다음 리소스를 참조 하세요.
  
- [Microsoft Cloud ID for Enterprise Architects](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [Microsoft Azure에서 Office 365 DirSync(디렉터리 동기화)를 배포합니다.](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

자세한 내용은 [통합 앱 및 azure ad for Office 365 관리자](integrated-apps-and-azure-ads.md) 및 [azure ad application gallery 및 single sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)을 참고 하세요.

### <a name="power-apps"></a>파워 앱
Power apps는 SharePoint 목록 및 기타 데이터 앱과 같은 기존 데이터 원본에 연결할 수 있는 모바일 장치용으로 중요 한 앱입니다. 자세한 내용은 SharePoint Online 및 [PowerApps 페이지](https://powerapps.microsoft.com/) [에서 목록에 대 한 PowerApp 만들기](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) 를 참조 하세요.