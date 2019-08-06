---
title: Office 365 계정 관리 도구
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Office 365 사용자를 관리 하는 데 사용할 도구와 사용자 id를 관리 하는 방법에 따라 사용할 수 있는 작업에 대해 알아봅니다. '
ms.openlocfilehash: 3e29af9e3d01184f9edc386148de60897fb03e27
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490741"
---
# <a name="tools-to-manage-office-365-accounts"></a>Office 365 계정 관리 도구

구성에 따라 다양 한 방식으로 Office 365 사용자를 관리할 수 있습니다. [Microsoft 365 관리 센터](https://admin.microsoft.com), Windows PowerShell, 온-프레미스 디렉터리 또는 Azure Active directory 관리 포털에서 사용자를 관리할 수 있습니다. Office 365을 구입 하는 즉시 관리 센터 및 Windows PowerShell을 사용 하 여 계정을 관리할 수 있습니다. 조직의 모든 사용자가 클라우드 id를 관리할 때 Office 365에 대해 별도의 사용자 ID와 암호를 사용 합니다. 온-프레미스 인프라와 통합 하 고 사용자 계정이 Office 365와 동기화 되도록 하려면 Azure Active Directory Connect를 사용 하 여 id 동기화를 제공 하 고, 선택적으로 암호 동기화를 제공 하거나, 전체를 제공할 수 있습니다. single sign-on 기능
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>사용자 계정을 관리 하는 위치 및 방법 계획

사용자 계정을 관리할 수 있는 위치와 방법은 Office 365에 사용할 id 모델에 따라 달라 집니다. 이 두 모델은 모두 클라우드 인증 및 페더레이션 인증입니다.
  
### <a name="cloud-authentication"></a>클라우드 인증

- 클라우드 인증-관리 센터에서 사용자를 만들고 관리 하 고, Windows PowerShell 또는 Azure Active Directory를 사용 하 여 사용자를 관리할 수도 있습니다. 
    
- 원활한 single sign-on을 사용한 암호 해시 동기화-Azure AD의 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하도록 설정 하는 가장 간단한 방법입니다. 암호 해시 동기화 (PHS)를 사용 하 여 온-프레미스 Active Directory 사용자 계정 개체를 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다. 
    
- 원활한 single sign-on을 통한 통과 인증-하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 하 여 온-프레미스 활성에서 사용자의 유효성을 직접 검사 합니다. 디렉토리로. 
    
### <a name="federated-authentication"></a>페더레이션 인증

- 페더레이션 인증 옵션-주로 인증 요구 사항이 더 복잡 한 대규모 엔터프라이즈 조직의 경우 온-프레미스 디렉터리 개체는 Office 365와 동기화 되 고 사용자 계정은 온-프레미스에서 관리 됩니다. 
    
- 타사 [인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체는 Office 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다. 
    
## <a name="managing-accounts"></a>계정 관리

조직에서 계정을 만들고 관리 하는 방법을 결정할 때는 다음 사항을 고려 하십시오.
  
- Office 365와 온-프레미스 디렉터리 간에 id를 연결 하려면 온-프레미스 환경 내의 서버에 디렉터리 동기화 소프트웨어를 설치 해야 합니다.
    
- SSO 옵션을 비롯 한 디렉터리 동기화 옵션을 사용 하려면 온-프레미스 디렉터리 특성이 표준을 충족 해야 합니다. 디렉터리에서 사용 되는 특성에 대 한 구체적인 내용과 필요한 정리 (있는 경우)는 [Office 365에 대 한 디렉터리 동기화를 통한 사용자 프로 비전 준비](prepare-for-directory-synchronization.md)에서 설명 합니다. IdFix를 사용 하 여 디렉터리 정리를 자동화 하는 방법에 대 한 지침은 [Office 365 idfix 도구 다운로드 및 실행](install-and-run-idfix.md) 을 참조 하세요. 
    
- Office 365 계정을 만드는 방법을 계획 합니다.
    
    다음 표에서는 다양 한 계정 관리 도구를 보여 줍니다.
    
|**옵션**|**참고**|
|:-----|:-----|
|관리 센터  <br/> |[사용자를 개별적으로 또는 대량으로 Office 365에 추가-관리자 도움말](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  사용자 계정을 추가 및 변경할 수 있는 간단한 웹 인터페이스를 제공 합니다.  <br/>  디렉터리 동기화가 사용 하도록 설정 된 경우 (위치 및 라이선스 할당을 설정할 수 있음) 사용자를 변경 하는 데 사용할 수 없습니다.  <br/>  SSO 옵션과 함께 사용할 수 없습니다.  <br/> |
|Windows PowerShell  <br/> |[Windows PowerShell을 사용 하 여 Office 365 관리](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Windows PowerShell 스크립트를 사용 하 여 사용자를 대량 사용자에 게 추가할 수 있습니다.  <br/>  계정을 만드는 방법에 관계 없이 계정에 위치 및 라이선스를 할당 하는 데 사용할 수 있습니다.  <br/> |
|대량 가져오기  <br/> |[Office 365에 여러 사용자를 동시에 추가 - 관리자 도움말](add-several-users-at-the-same-time.md) <br/>  CSV 파일을 가져와서 Office 365에 사용자 그룹을 추가할 수 있도록 허용 합니다.  <br/>  SSO 옵션과 함께 사용할 수 없습니다.  <br/> |
|Azure Active Directory  <br/> |Office 365 구독을 사용 하 여 무료 버전의 Azure Active Directory를 사용할 수 있습니다. 클라우드 사용자에 대해 셀프 서비스 암호 재설정 및 무료 버전을 사용 하 여 로그인 및 액세스 패널 페이지의 사용자 지정과 같은 기능을 수행할 수 있습니다. 향상 된 기능을 얻으려면 기본 버전 또는 premium edition으로 업그레이드 하면 됩니다. 지원 되는 기능 목록은 [Azure Active Directory edition](https://go.microsoft.com/fwlink/p/?LinkId=698465) 를 참조 하세요.  <br/> |
|디렉터리 동기화  <br/> |[Azure Active Directory에 온-프레미스 id 통합](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  암호 동기화 여부와 관계 없이 디렉터리 동기화의 경우 [빠른 설정으로 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698537)를 사용 합니다.  <br/>  여러 포리스트와 SSO 옵션에 대해 [AZURE AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다.  <br/>  SSO를 사용 하도록 설정 하는 데 필요한 인프라를 제공 합니다.  <br/>  다양 한 하이브리드 시나리오에 필요 합니다.  <br/>  미리 구성된 마이그레이션  <br/>  하이브리드 Exchange  <br/>  온-프레미스 디렉터리의 보안 및 메일 사용 가능 그룹을 동기화 합니다.  <br/> |
   
- 사용자 계정을 Office 365에 추가 하려는 방법에 관계 없이 라이선스 할당, 위치 지정 등 여러 가지 계정 기능을 관리 해야 합니다. 이러한 기능은 관리 센터에서 장기간 관리할 수 있거나 [Office 365 PowerShell을 사용 하 여 사용자 계정을 만들](https://go.microsoft.com/fwlink/p/?LinkId=717083)수도 있습니다.
    
    관리 센터를 통해 모든 사용자를 추가 하 고 관리 하는 경우 Office 365 계정을 만드는 것과 동일한 시간에 위치를 지정 하 고 라이선스를 할당 합니다. 따라서 계획은 그다지 많지 않아도 됩니다.
    
    > [!IMPORTANT]
    > 라이선스 (예: SharePoint Online에)를 할당 하지 않고 Office 365에서 계정을 만드는 것은 계정 소유자가 Office 365 포털을 볼 수 있지만 회사 구독 내의 어떤 서비스에도 액세스 하지 못하는 것을 의미 합니다. 위치 및 라이선스를 할당 한 후에는 할당 한 서비스에 계정이 복제 됩니다. 사용자는 자신의 계정에 로그인 하 고 할당 한 서비스를 사용할 수 있습니다. 
  
## <a name="next-steps"></a>다음 단계

[온-프레미스 환경과 Office 365 통합](office-365-integration.md)
  
## <a name="see-also"></a>참고 항목

[Office 365에서 사용자 계정 관리](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

