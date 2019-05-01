---
title: Office 365 ID 및 Azure Active Directory 이해
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
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365에서 사용자 id가 관리 되는 방식을 알아봅니다.
ms.openlocfilehash: c9dff7e17e4c0dcceb7cdeab86c1acdd40e01205
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487765"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Office 365 ID 및 Azure Active Directory 이해

Office 365에서는 클라우드 기반 사용자 id 및 인증 서비스 azure Active Directory (azure AD)를 사용 하 여 사용자를 관리 합니다. 온-프레미스 조직과 Office 365 간에 id 관리를 구성 하는 방법을 선택 하는 것은 클라우드 인프라의 기초 중 하나입니다. 나중에이 구성을 변경 하기가 어려울 수 있으므로 조직의 요구에 가장 적합 한 작업을 결정 하는 옵션을 신중 하 게 고려해 야 합니다. Office 365에서 두 가지 기본 인증 모델을 선택 하 여 사용자 계정을 설정 및 관리할 수 있습니다. **클라우드 인증** 및 **페더레이션 인증**
  
이러한 인증 및 id 모델 중 어떤 것을 시작 하 고 실행 하는 데 사용할 것인지 신중히 고려해 야 합니다. 각 인증 및 id 옵션을 구현 및 유지 관리 하는 데 드는 시간, 기존 복잡성 및 비용에 대해 생각해 봅니다. 이러한 요인은 조직 마다 다릅니다. 그리고 배포에 사용 하려는 인증 및 id 모델을 선택 하는 데 도움이 되는 id 옵션의 주요 개념을 이해 해야 합니다.
  
## <a name="cloud-authentication"></a>클라우드 인증

온-프레미스에 기존 Active Directory 환경이 있거나 없는 경우에 따라 Office 365을 사용 하 여 사용자에 대 한 인증 및 id 서비스를 관리 하는 몇 가지 옵션을 사용할 수 있습니다.
  
### <a name="cloud-only"></a>클라우드 전용

클라우드 전용 모델을 사용 하는 경우에는 Office 365 에서만 사용자 계정을 관리할 수 있습니다. 온-프레미스 서버가 필요 하지 않습니다. 이 클라우드는 Azure AD에 의해 클라우드에서 모두 처리 됩니다. [Microsoft 365 관리 센터](https://admin.microsoft.com) 에서 또는 Windows PowerShell [PowerShell cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) 을 사용 하 여 사용자를 만들고 관리 하는 경우 Azure AD가 클라우드에서 완전히 처리 합니다. 일반적으로 다음과 같은 경우에는 클라우드 전용 모델을 사용 하는 것이 좋습니다. 
  
- 다른 온-프레미스 사용자 디렉터리는 없습니다.
    
- 매우 복잡 한 온-프레미스 디렉터리를 사용 하며 작업을 통합 하지 않을 수 있습니다.
    
- 기존 온-프레미스 디렉터리가 있지만 Office 365의 평가판 또는 파일럿을 실행 하려고 합니다. 나중에 온-프레미스 디렉터리에 연결할 준비가 되 면 클라우드 사용자를 온-프레미스 사용자에 게 일치 시킬 수 있습니다.
    
클라우드 id를 시작 하려면 [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)을 참조 하세요.
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>원활한 single sign-on을 사용한 암호 해시 동기화

Azure AD의 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하도록 설정 하는 가장 간단한 방법입니다. 암호 해시 동기화 (phs)를 사용 하 여 온-프레미스 Active Directory 사용자 계정 개체를 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다. 사용자는 온-프레미스 Active Directory에서 Azure AD로 동기화 되며, 사용자는 온 보와 클라우드에서 동일한 암호를 사용할 수 있습니다. 암호가 변경 되거나 온-프레미스에서 다시 설정 되 면 새 암호 해시가 Azure AD와 동기화 되어 사용자가 항상 클라우드 리소스 및 온-프레미스 리소스에 대해 동일한 암호를 사용할 수 있습니다. 암호가 azure ad로 전송 되지 않거나 azure ad에서 일반 텍스트로 저장 됩니다. id 보호와 같은 Azure AD의 일부 프리미엄 기능은 선택한 인증 방법에 관계 없이 phs를 요구 합니다. 원활한 single sign-on을 사용 하면 사용자가 회사 장치에 있고 회사 네트워크에 연결 되어 있을 때 Azure AD에 자동으로 로그인 됩니다.
  
[암호 해시 동기화](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) 및 [원활한 single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)선택에 대해 더 자세히 알아보세요.
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>원활한 single sign-on을 사용한 통과 인증

온-프레미스 Active Directory를 사용 하 여 사용자의 유효성을 직접 검사 하기 위해 하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하는 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 합니다. pta (통과 인증)를 사용 하는 경우 온-프레미스 Active Directory 사용자 계정 개체를 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다. 사용자는 온-프레미스 계정 및 암호를 사용 하 여 온-프레미스 및 Office 365 리소스와 응용 프로그램 모두에 로그인 할 수 있습니다. 이 구성은 암호 해시를 Office 365로 보내지 않고 온-프레미스 Active Directory에 대해 직접 사용자 암호의 유효성을 검사 합니다. 온-프레미스 사용자 계정 상태, 암호 정책 및 로그온 시간을 즉시 적용 해야 하는 보안 요구 사항이 있는 회사는이 인증 방법을 사용 합니다. 원활한 single sign-on을 사용 하면 사용자가 회사 장치에 있고 회사 네트워크에 연결 되어 있을 때 Azure AD에 자동으로 로그인 됩니다.
  
[통과 인증](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) 및 [원활한 single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)선택에 대해 자세히 알아보세요.
  
## <a name="federated-authentication-options"></a>페더레이션 인증 옵션

기존 Active Directory 환경이 온-프레미스에 있는 경우 페더레이션 인증을 사용 하 여 office 365에서 사용자에 대 한 인증 및 id 서비스를 관리 하는 방법을 포함 하 여 디렉터리와 사무실을 통합할 수 있습니다.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>AD FS (Active Directory Federation Services)와 페더레이션 된 id

인증 요구 사항이 보다 복잡 한 대규모 엔터프라이즈 조직의 경우 온-프레미스 디렉터리 개체는 Office 365와 동기화 되 고 사용자 계정은 온-프레미스에서 관리 됩니다. AD FS를 사용 하는 경우 사용자는 온-프레미스와 클라우드에서 동일한 암호를 사용 하며, Office 365를 사용할 수 있도록 다시 로그인 할 필요가 없습니다. 이 페더레이션 인증 모델은 스마트 카드 기반 인증 또는 타사 다단계 인증과 같은 추가 인증 요구 사항을 제공할 수 있으며, 일반적으로 조직에 인증 요구 사항이 있는 경우에 필요 합니다. Azure AD에서 기본적으로 지원 되지 않습니다.
  
자세한 내용은 [AD FS를 사용 하 여 페더레이션 id 선택을](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)참고 하세요.
  
### <a name="third-party-authentication-and-identity-providers"></a>타사 인증 및 id 공급자

온-프레미스 디렉터리 개체는 Office 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다. 조직에서 타사 페더레이션 솔루션을 사용 하는 경우 타사 페더레이션 솔루션이 Azure AD와 호환 되는 경우 Office 365에 대 한 해당 솔루션에 대 한 로그온을 구성할 수 있습니다.
  
자세한 내용은 [Azure AD 페더레이션 호환성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)을 확인 하세요.
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Office 365를 사용 하 여 id 및 인증 구성

[azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)를 사용 하 여 온-프레미스 디렉터리를 Office 365 및 azure ad와의 통합이 간소화 되었습니다. Azure AD connect는 디렉터리를 연결 하는 최상의 방법 이며, 조직에서 사용자를 클라우드로 동기화 하기 위한 권장 사항입니다.
  
azure ad advisor: [azure ad Connect advisor](https://aka.ms/aadconnectpwsync), [AD FS 배포 관리자](https://aka.ms/adfsguidance)및 [azure ad Premium 설치 가이드](https://aka.ms/aadpguidance)를 사용할 수도 있습니다.
  
## <a name="video-training"></a>동영상 교육

자세한 내용은 LinkedIn 학습을 통해 가져온 [Office 365: Azure AD Connect를 사용 하 여 id 관리](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)를 참조 하세요.
