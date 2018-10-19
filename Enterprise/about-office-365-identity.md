---
title: Office 365 ID 및 Azure Active Directory 이해
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365에서 사용자 id를 관리 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 14d1ec8a3ebc4620a72f831c0ec80253f7b3072c
ms.sourcegitcommit: dcb57859ad40090cf70586ac350472eb0fc8d9c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2018
ms.locfileid: "25639637"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Office 365 ID 및 Azure Active Directory 이해

Office 365 클라우드 기반 사용자 id 및 인증 서비스 Azure Active Directory (Azure AD)를 사용 하 여 사용자를 관리 합니다. 온-프레미스 조직과 Office 365 간의 id 관리 구성 된 경우 선택은 클라우드 인프라의 기초 중 하나가 있는 초기 결정 합니다. 나중에이 구성을 변경 하는 것은 어려울 수 있습니다, 때문에 조직의 필요에 따라 가장 적합 한 기능을 결정 하는 옵션을 신중 하 게 고려 합니다. Office 365를 설정 하 고 사용자 계정; 관리의 두 기본 인증 모델 중에서 선택할 수 있습니다. **클라우드 인증** 및 **연결 된 인증**합니다.
  
해당 되어 실행 되 고 신중 하 게 준비를 사용 하 여 이러한 인증 및 id 모델 중 어떤를 고려 하는 것이 중요 합니다. 시간, 기존 복잡성 및 비용을 구현 하 고 각각의 인증 및 id 옵션을 유지 관리를 고려해 야 합니다. 이러한 요소는 조직 마다;에 대 한 서로 다른 및 배포에 사용 하려는 인증 및 id 모델을 선택할 수 있도록 지원 id 옵션에 대 한 주요 개념을 이해 해야 합니다.
  
## <a name="cloud-authentication"></a>클라우드 인증

여부에 따라 Office 365 사용자에 대 한 인증 및 id 서비스를 관리 하는 여러 옵션 있거나 기존 Active Directory 환경 온-프레미스를 설치 하지 않은 경우 해야 합니다.
  
### <a name="cloud-only"></a>클라우드 전용

클라우드 전용 모델을 사용 하면 사용자 계정을 Office 365에만 관리할 수 있습니다. 온-프레미스 서버 없음 요소가 필요 합니다. 모든 클라우드에서 의해 처리 될 Azure AD 합니다. 컨트롤을 만들고 Office 365 관리 센터에서 사용자 관리 또는 Windows PowerShell을 사용 하 여 [PowerShell cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) 및 id 및 인증에서에서 처리 되는 완전히 클라우드 Azure AD 하 여 합니다. 클라우드 전용 모델은 일반적으로 좋은 선택 경우: 
  
- 다른 온-프레미스 사용자 디렉터리에 없는 해야합니다.
    
- 매우 복잡 한 온-프레미스 디렉터리 있고와 통합 하는 작업을 방지 하기 위해를 세려면 합니다.
    
- 기존 온-프레미스 디렉터리를 되었지만 평가판 또는 Office 365의 파일럿을 실행 하려는 합니다. 나중에 온-프레미스 디렉터리에 연결할 준비가 되 면 온-프레미스 사용자에 게 클라우드 사용자를 일치 시킬 수 있습니다.
    
클라우드 id를 가진 시작 [비즈니스를 위한 Office 365 설정](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)을 참조 하십시오.
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>원활 하 게 single sign-on 암호 해시 동기화

Azure AD에서 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하는 가장 간단한 방법은 합니다. 암호 해시 동기화 (PHS)를 사용한 Office 365와 온-프레미스 Active Directory 사용자 계정 개체를 동기화 및 사용자가 온-프레미스를 관리 합니다. 사용자 암호 해시를 사용자가 동일한 암호 온-프레미스 및 클라우드에서 Azure AD를 온-프레미스 Active Directory에서 동기화 됩니다. 암호 변경 또는 온-프레미스를 다시 설정 하는 경우 사용자에 게 클라우드 리소스 및 온-프레미스 리소스에 대 한 동일한 암호를 항상 사용할 수 있도록 새 암호 해시 Azure AD에 동기화 됩니다. 암호는 되지 Azure AD 보내거나 일반 텍스트로 Azure AD에 저장 합니다. 일부 프리미엄 기능 Id 보호와 같은 Azure ad 인증 방법을 선택 하는 관계 없이 PHS 필요 합니다. 원활 하 게 single sign-on, 사용자는 자동으로 로그인을 통해 회사 장치에는 및 회사 네트워크에 연결 된 경우 Azure AD 합니다.
  
[암호 해시 동기화를 선택](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) 하 고 [원활 하 게 single sign on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)하는 방법에 대 한 자세한 내용은.
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>원활 하 게 single sign-on 통과 인증

하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 온-프레미스 Active Directory를 사용 하 여 직접 사용자의 유효성을 검사 하려면 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 합니다. 통과 인증 (설명)을 사용 하면 Office 365와 온-프레미스 Active Directory 사용자 계정 개체 동기화 및 사용자가 온-프레미스를 관리 합니다. 사용자가 온-프레미스 및 Office 365 리소스 및 온-프레미스 계정 및 암호를 사용 하는 응용 프로그램에 로그인 하도록 허용 합니다. 이 구성은 Office 365에 암호 해시를 보내지 않고 온-프레미스 Active Directory에 대해 직접 사용자 암호의 유효성을 검사 합니다. 온-프레미스 사용자 계정을 즉시 적용 하려면 보안 요구 사항이 있는 회사 상태, 암호 정책 및 로그온 시간에이 인증 방법을 사용 합니다. 원활 하 게 single sign-on, 사용자는 자동으로 로그인을 통해 회사 장치에는 및 회사 네트워크에 연결 된 경우 Azure AD 합니다.
  
[통과 인증을 선택](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) 하 고 [원활 하 게 single sign on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)하는 방법에 대 한 자세한 내용은.
  
## <a name="federated-authentication-options"></a>연결 된 인증 옵션

기존 Active Directory 환경 온-프레미스가 Office 365에서 사용자에 대 한 인증 및 id 서비스를 관리 하려면 연결 된 인증을 사용 하 여 Office 365 디렉터리와 통합할 수 있습니다.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Active Directory Federation Services (AD FS)와 페더레이션된 id

주로 보다 복잡 한 인증 요구 사항이 조직 대기업, 온-프레미스 디렉터리 개체는 Office 365와 동기화 되며 사용자 계정을 관리 되는 온-프레미스 합니다. AD FS, 사용자가 동일한 암호 온-프레미스 및 클라우드에서 Office 365를 사용 하 여 다시 로그인 갖지 않습니다. 이 연결 된 인증 모델 추가 인증 요구 사항, 예: 제 3 자 다단계 인증 또는 스마트 카드 기반 인증을 제공할 수 및는 조직에는 인증 요구 사항이 있는 경우 일반적으로 필요 Azure AD에서 지원 되지 않음.
  
[AD FS 사용한 페더레이션된 id를 선택](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)하는 방법에 대 한 자세한 내용은.
  
### <a name="third-party-authentication-and-identity-providers"></a>타사 인증 및 id 공급자

온-프레미스 디렉터리 개체를 Office 365로 동기화 될 수 및 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)에 의해 관리 됩니다. 조직에서 타사 페더레이션 솔루션을 사용 하는 경우 구성할 수 있습니다 로그온 해당 솔루션 Office 365에 대 한 타사 페더레이션 솔루션 Azure AD와 호환 되는 제공 합니다.
  
[Azure AD 페더레이션 호환성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)에 대해 알아봅니다.
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Office 365를 사용 하 여 id 및 인증 구성

Office 365 및 Azure AD와 온-프레미스 디렉터리 통합 (영문) [Azure AD 연결](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)된 간소화 되었습니다. Azure AD 연결 디렉터리에 연결 하는 가장 좋은 방법은 및 클라우드로 사용자를 동기화 할 조직에 대 한 Microsoft의 권장 됩니다.
  
Azure AD 문에 사용할 수도 있습니다: [Azure AD 연결 관리자](https://aka.ms/aadconnectpwsync), [AD FS 배포 관리자](https://aka.ms/adfsguidance), 및 [Azure AD 프리미엄 설치 가이드](https://aka.ms/aadpguidance)입니다.
  
## <a name="video-training"></a>비디오 교육

자세한 내용은 비디오 과정을 참조 하십시오. [Office 365: 관리 id가 사용 하 여 Azure AD 연결](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), LinkedIn 학습에 의해 제공자 합니다.
