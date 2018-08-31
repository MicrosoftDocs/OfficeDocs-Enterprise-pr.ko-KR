---
title: Office 365 계정 관리 도구
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '사용 하 여 Office 365 사용자 관리 도구에 대해 알아보고 기능 사용 하 여 사용자 id를 관리 하는 방법에 따라 다릅니다. '
ms.openlocfilehash: 24a7dd72603b881ea0810d0712900bc78dc34a81
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541919"
---
# <a name="tools-to-manage-office-365-accounts"></a>Office 365 계정 관리 도구

구성에 따라 다양 한 방식으로 Office 365 사용자를 관리할 수 있습니다. Office 365 관리 센터에서 Windows PowerShell 프로그램 온-프레미스 디렉터리 또는 Azure Active Directory 관리 포털에서 사용자를 관리할 수 있습니다. Office 365를 구입 하는 즉시 관리 센터 및 Windows PowerShell 수 관리 하는데 사용할 계정입니다. 클라우드 id를 관리 하는 경우 조직에서 모든 사람 별도 사용자 ID와 암호를 Office 365에 있습니다. 온-프레미스 인프라와 통합 하 고 사용자 계정이 하려는 경우 Office 365와 동기화를 사용할 수 있습니다 Azure Active Directory에 연결 하 고 id의 동기화를 제공 하 고 필요에 따라 암호 동기화를 제공 하거나 전체 single sign-on 기능입니다.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>사용자 사용자 계정을 관리 하는 방식과 위치에 대 한 계획

Office 365에 대해 사용 하려는 id 모델에 따라 달라 집니다 위치와 방법을 사용자 계정을 관리할 수 있습니다. 두 전반적인 모델은 클라우드 인증 및 연결 된 인증입니다.
  
### <a name="cloud-authentication"></a>클라우드 인증

- [클라우드 인증](about-office-365-identity.md#cloud-authentication) -만들기 및 Office 365 관리 센터에서 사용자 관리, 사용자를 관리 하려면 Windows PowerShell 또는 Azure Active Directory을 사용할 수도 있습니다. 
    
- [암호 해시를 원활 하 게 single sign-on 동기화](about-office-365-identity.md) -Azure AD에서 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하는 가장 간단한 방법은 합니다. 암호 해시 동기화 (PHS)를 사용한 Office 365와 온-프레미스 Active Directory 사용자 계정 개체를 동기화 및 사용자가 온-프레미스를 관리 합니다. 
    
- 하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 직접 사용 하는 사용자의 유효성을 검사 하려면 Azure AD 인증 서비스에 대 한 간단한 암호 유효성을 제공 하는 [원활 하 게 single sign-on 통과 인증](about-office-365-identity.md) -사용자 온-프레미스 Active Directory 합니다. 
    
### <a name="federated-authentication"></a>연결 된 인증

- [페더레이션 인증 옵션](about-office-365-identity.md#federated-authentication-options) -대기업 조직 보다 복잡 한 인증 요구 사항에 대 한 주로 온-프레미스 디렉터리 개체는 Office 365와 동기화 되며 사용자 계정을 관리 되는 온-프레미스 합니다. 
    
- [타사 인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체를 Office 365로 동기화 될 수 및 리소스 액세스를 클라우드는 주로 타사 id 공급자 (IdP)에 의해 관리 됩니다. 
    
## <a name="managing-accounts"></a>계정 관리

어떤 방식으로 조직을 만들고 계정 관리를 결정할 때는 다음 사항을 고려 합니다.
  
- 디렉터리 동기화 소프트웨어를 Office 365와 온-프레미스 디렉터리 간의 id가 연결 하 여 온-프레미스 환경 내에서 서버에 설치 해야 합니다.
    
- SSO 옵션을 포함 하는 디렉터리 동기화 옵션을 온-프레미스 디렉터리 특성 표준을 충족 해야 합니다. [Office 365에 대 한 디렉터리 동기화를 통해 프로 비전 사용자에 게 준비](prepare-for-directory-synchronization.md)어떤 특성 디렉터리에서 사용 되 고 어떤 정리 (해당 되는 경우)가 필요의 세부 사항은 설명 합니다. 디렉터리 정리를 자동화 하려면 IdFix를 사용 하는 방법에 대 한 지침은 [Office 365 IdFix 도구를 실행 하 고 설치를](install-and-run-idfix.md) 참조 합니다. 
    
- Office 365 계정을 만들 하려는 하는 방법을 계획 합니다.
    
    다음 표에 서로 다른 계정 관리 도구를 나열합니다.
    
|**옵션**|**참고**|
|:-----|:-----|
|Office 365 관리 센터  <br/> |[사용자가 개별적으로 또는 대량으로 Office 365에 추가-관리 지원](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  추가 및 사용자 계정을 변경할 수 있는 간단한 웹 인터페이스를 제공 합니다.  <br/>  디렉터리 동기화를 사용 하는 경우 사용자를 변경 하는데 사용할 수 없습니다 (위치 및 라이선스 할당을 설정할 수 있습니다.).  <br/>  SSO 옵션에 사용할 수 없습니다.  <br/> |
|Windows PowerShell  <br/> |[Windows PowerShell로 Office 365 관리](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Windows PowerShell 스크립트를 사용 하 여 대량 사용자의 사용자를 추가할 수 있습니다.  <br/>  계정을 만드는 방법에 관계 없이 계정에 위치 및 라이선스를 할당 하려면 사용할 수 있습니다.  <br/> |
|대량 가져오기  <br/> |[Office 365에 여러 사용자를 동시에 추가 - 관리자 도움말](add-several-users-at-the-same-time.md) <br/>  Office 365로 사용자 그룹에 추가 하려면 CSV 파일을 가져올 수 있습니다.  <br/>  SSO 옵션에 사용할 수 없습니다.  <br/> |
|Azure Active Directory  <br/> |Office 365 구독을 Azure Active Directory의 무료 버전을 가져옵니다. 무료 버전을 사용 하 여 클라우드 사용자 및 사용자 지정 로그인 하 고 액세스 패널 페이지에 대 한 다시 설정 하는 셀프서비스 암호와 같은 기능을 수행할 수 있습니다. 향상 된 기능을 얻으려면, 기본 버전 또는 premium edition으로 업그레이드할 수 있습니다. 지원 되는 기능의 목록 [Azure Active Directory 버전](https://go.microsoft.com/fwlink/p/?LinkId=698465) 을 참조 하십시오.<br/> |
|디렉터리 동기화  <br/> |[Azure Active Directory를 사용 하면 온-프레미스 id가 통합 (영문)](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  디렉터리 동기화와 관계 없이 암호 동기화를 위한 [express 설정 사용 하 여 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkID=698537)을 사용 합니다.  <br/>  여러 포리스트 및 SSO 옵션에 대 한 [사용자 정의 설치의 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkId=698430)을 사용 합니다.  <br/>  SSO를 사용 하도록 설정 하는 인프라를 제공 합니다.  <br/>  다양 한 하이브리드 시나리오에 필요합니다.  <br/>  미리 구성된 마이그레이션  <br/>  하이브리드 Exchange  <br/>  온-프레미스 디렉터리의 보안 및 메일 사용 가능 그룹을 동기화합니다.  <br/> |
   
- 사용자 계정을 Office 365에 추가 하려는 방법에 관계 없이 위치를 지정 라이선스를 할당 하는 등의 여러 계정 기능을 관리 하 고 등을 지정 해야 합니다. Office 365 관리 센터에서 장기 이러한 기능을 관리할 수 있는 또는 [Office 365 powershell 사용자 계정을 만들](https://go.microsoft.com/fwlink/p/?LinkId=717083)수도 있습니다.
    
    추가 하 고 Office 365 관리 센터를 통해 모든 사용자를 관리 하려는 경우에 위치를 지정 및 Office 365 계정 만들기 (영문)와 같은 시간에 라이선스를 할당 합니다. 따라서 많은 하지 계획은 필요 합니다.
    
    > [!IMPORTANT]
    > 계정 소유자는 Office 365 포털 하지만 그를 볼 수 있음을 의미 (SharePoint Online으로, 예:) 라이선스를 할당 하지 않고 Office 365에서 계정 만들기 회사의 구독 내에서 서비스에 액세스할 수 없습니다. 위치 및 라이선스를 할당 한 후 서비스 또는 사용자에 게 할당 하는 서비스 계정이 복제 됩니다. 사용자는 자신의 계정으로 로그인 하 고 자신에 게 할당 하는 서비스를 사용 하 여 수 있습니다. 
  
## <a name="next-steps"></a>다음 단계

[온-프레미스 환경와 office 365의 통합](office-365-integration.md)
  
## <a name="see-also"></a>참고 항목

[Office 365에서 사용자 계정을 관리합니다](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

