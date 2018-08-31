---
title: 온-프레미스 환경와 office 365의 통합
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Office 365에서 기존 디렉터리 서비스와 통합 하는 방법에 알아봅니다.
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542070"
---
# <a name="office-365-integration-with-on-premises-environments"></a>온-프레미스 환경와 office 365의 통합

비즈니스 서버 2015 또는 SharePoint Server 2013에 대 한 Office 365의 Exchange Server, Skype 온-프레미스 설치와 함께 기존 디렉터리 서비스와 통합할 수 있습니다.
  
 - 디렉터리 서비스와 통합 하는 경우 동기화 할 수 있으며 두 환경에 대 한 사용자 계정을 관리할 수 있습니다. 추가할 수도 있습니다 암호 해시 동기화 또는 single sign on (SSO) 사용자가 로그온 수 있도록 두 환경에서 온-프레미스 자격 증명 사용에 로그온 합니다.
 - 온-프레미스 서버 제품을 통합 하는 경우에 하이브리드 환경을 만듭니다. 하이브리드 환경에는 Office 365에 사용자 또는 정보를 마이그레이션 또는 일부 사용자 또는 일부 정보 온-프레미스 및 클라우드의 일부를 계속할 수 대로 데 도움이 됩니다. 하이브리드 환경에 대 한 자세한 내용은 [Office 365 하이브리드 클라우드 솔루션 개요](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)를 참조 하십시오.

사용자 지정 된 설치 지침에 대 한 Azure AD 문에 사용할 수도 있습니다.
- [Azure AD 연결 관리자](https://aka.ms/aadconnectpwsync)
- [AD FS 배포 관리자](https://aka.ms/adfsguidance)
- [Azure RMS 배포 마법사](https://aka.ms/azuremsguidance)
- [Azure AD 프리미엄 설치 지침](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>시작하기 전에
Office 365 및 온-프레미스 환경 통합 하기 전에 네트워크를 계획 하 [고 Office 365에 대 한 성능 조정](network-planning-and-performance.md)참석 해야할 수도 있습니다. Office 365에서 사용 가능한 [id 모델](about-office-365-identity.md) 을 이해 하려면 원하는 메시지가 표시 됩니다. 

[계정을 Office 365 사용자를 관리 하려면 여기서](manage-office-365-accounts.md) 목록은 Office 365의 사용자 및 계정 관리 하기 위해 사용할 수 있는 도구를 참조 하십시오. 
  
## <a name="integrate-office-365-with-directory-services"></a>Office 365의 디렉터리 서비스와 통합
온-프레미스 디렉터리에 있는 기존 사용자 계정을 Office 365와 환경 간의 오류나 차이점을 소개 하는 위험에서 이러한 계정을 모두를 다시 만듭니다 하려는 하지 않습니다. 디렉터리 동기화를 사용 하면 온라인 사용자 간의 이러한 계정이 미러와 온-프레미스 환경입니다. 디렉터리 동기화를 통해 사용자가 각 환경에 대 한 새로운 정보를 기억할 필요가 없습니다 하 고 만들거나 두번 계정을 업데이트할 필요가 없습니다. 디렉터리 동기화를 위한 [온-프레미스 디렉터리 준비](prepare-for-directory-synchronization.md) 를 해야 합니다, 그리고이 작업을 수동으로 수행 하거나 [IdFix 도구](install-and-run-idfix.md) (IdFix 도구에만 작동 하며 Active Directory)를 사용할 수 있습니다. 
  
![디렉터리 동기화를 사용 하 여 온-프레미스 및 온라인 사용자 계정 정보 동기화 유지](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
사용자가 온-프레미스 자격 증명을 사용 하 여 Office 365에 로그온 할 수 있도록, 하려는 경우에 SSO를 구성할 수 있습니다. SSO를와 Office 365 사용자 인증에 대 한 온-프레미스 환경을 신뢰 하도록 구성 됩니다.
  
![Single sign-on과 동일한 계정을 온-프레미스 및 온라인 환경 모두에서 사용할 수 있는](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
다른 사용자 계정 관리 기술 다음 표와 같이 사용자에 게 다른 경험을 제공 합니다.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**디렉터리 동기화와 관계 없이 암호 해시 동기화 또는 통과 인증**
사용자가 자신의 사용자 계정 (도메인 \ 사용자 이름)가 온-프레미스 환경에 로그온 합니다. Office 365로 전달 될 때 이러한 해야 다시 계정으로 로그온 자신의 작업이 나 교육용 (user@domain.com). 사용자 이름은 환경 모두에서 동일 합니다. 암호 해시 동기화 또는 통과 인증을 추가 하면 사용자는 두 환경에 대 한 동일한 암호를 다르지만 Office 365에 로그온 할 때 이러한 자격 증명을 다시 제공 해야 합니다. 암호 해시 동기화를 사용 하 여 디렉터리 동기화에 가장 일반적으로 사용 되는 디렉터리 동기화 시나리오입니다.

디렉터리 동기화를 설정 하려면 Azure Active Directory 연결을 사용 합니다. 자세한 내용은 [Office 365에 대 한 디렉터리 동기화를 설정](set-up-directory-synchronization.md)하 고 [express 설정 사용 하 여 사용 하 여 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkId=698537)을 읽어보십시오.

[Office 365에 대 한 디렉터리 동기화를 통해 사용자를 프로 비전을 준비 하](prepare-for-directory-synchronization.md) 고 [통합 (영문) Azure Active Directory와 온-프레미스를 식별](https://go.microsoft.com/fwlink/?LinkId=518101)하는 방법에 대 한 자세한 내용은.

### <a name="directory-synchronization-with-sso"></a>**SSO 사용 하 여 디렉터리 동기화**
사용자가 자신의 사용자 계정 사용 하 여 온-프레미스 환경에 로그온 합니다. Office 365로 전달 될 때 하거나 로그온 되어 자동으로 또는 온-프레미스 환경 (도메인 \ 사용자 이름)을 사용 하는지에 동일한 자격 증명을 사용 하 여 로그온 합니다.

SSO를 설정 하려면 Azure AD 연결 사용 합니다. 자세한 내용은 [사용자 지정 설정 사용 하 여 사용 하 여 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkID=698430)을 읽어보십시오.

[응용 프로그램 액세스 및 single sign-on 및 Azure Active Directory를 사용](https://go.microsoft.com/fwlink/p/?LinkId=698604)하는 방법에 대 한 자세한 내용은 합니다.

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure AD 연결 이전 버전의 디렉터리 동기화 및 Azure AD 동기화와 같은 identity 통합 도구를 대체합니다. 자세한 내용은 [Azure Active Directory를 사용 하 여 온-프레미스 id가 통합 (영문)을](https://go.microsoft.com/fwlink/p/?LinkId=527969)참조 하십시오. Azure Active Directory 동기화에서 Azure AD 연결을 업데이트 하려는 경우 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하십시오. [Microsoft Azure에서 Office 365 디렉터리 동기화 (DirSync)](https://go.microsoft.com/fwlink/?LinkId=517887)용으로 작성 된 솔루션 아키텍처를 참조 하십시오.