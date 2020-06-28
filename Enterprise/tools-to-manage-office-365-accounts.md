---
title: Microsoft 365 계정을 관리 하기 위한 도구
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: 'Microsoft 365 사용자를 관리 하는 데 사용할 도구와 사용자 id를 관리 하는 방법에 따라 사용할 수 있는 작업에 대해 알아봅니다. '
ms.openlocfilehash: c382006fe8cb46342548b7533148e760c103bf50
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906220"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a>Microsoft 365 계정을 관리 하기 위한 도구

구성에 따라 다양 한 방식으로 Microsoft 365 사용자를 관리할 수 있습니다. [Microsoft 365 관리 센터](https://admin.microsoft.com), Windows PowerShell, 온-프레미스 디렉터리 또는 Azure Active directory 관리 포털에서 사용자를 관리할 수 있습니다.

Microsoft 365을 구입 하는 즉시 관리 센터 및 Windows PowerShell을 사용 하 여 계정을 관리할 수 있습니다. 조직의 모든 사용자가 클라우드 id를 관리할 때는 Microsoft 365 용으로 별도의 사용자 ID와 암호를 사용 합니다. 온-프레미스 인프라와 통합 하 고 사용자 계정이 Microsoft 365와 동기화 되어 있는 경우 Azure Active Directory Connect를 사용 하 여 id 동기화를 제공 하 고 필요에 따라 암호 동기화 또는 전체 single sign-on 기능을 제공할 수 있습니다.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>사용자 계정을 관리 하는 위치 및 방법 계획

사용자 계정을 관리할 수 있는 위치와 방법은 Microsoft 365 구독에 사용할 id 모델에 따라 달라 집니다. 이 두 모델은 모두 클라우드 인증 및 페더레이션 인증입니다.
  
### <a name="cloud-authentication"></a>클라우드 인증

- [Microsoft 365 Identity](about-office-365-identity.md) -관리 센터에서 사용자를 만들고 관리 하 고, Windows PowerShell 또는 Azure Active Directory를 사용 하 여 사용자를 관리할 수도 있습니다.
- [원활한 single sign-on을 사용한 암호 해시 동기화](about-office-365-identity.md) -Azure AD의 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하도록 설정 하는 가장 간단한 방법입니다. 암호 해시 동기화 (PHS)를 사용 하 여 온-프레미스 Active Directory 사용자 계정 개체를 Microsoft 365으로 동기화 하 고 온-프레미스 사용자를 관리 합니다. 
- [원활한 single sign-on을 통한 통과 인증](about-office-365-identity.md) -하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 하 여 온-프레미스 Active Directory와 직접 사용자 유효성을 검사 합니다. 

### <a name="federated-authentication"></a>페더레이션 인증

- [Microsoft 365 Identity](about-office-365-identity.md) -주로 인증 요구 사항이 더 복잡 한 대규모 엔터프라이즈 조직의 경우 온-프레미스 디렉터리 개체는 Microsoft 365와 동기화 되 고 사용자 계정은 온-프레미스에서 관리 됩니다. 
- 타사 [인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체는 Microsoft 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다. 

## <a name="managing-accounts"></a>계정 관리

조직에서 계정을 만들고 관리 하는 방법을 결정할 때는 다음 사항을 고려 하십시오.
  
- Microsoft 365와 온-프레미스 디렉터리 간에 id를 연결 하려면 온-프레미스 환경 내의 서버에 디렉터리 동기화 소프트웨어를 설치 해야 합니다.
- SSO 옵션을 비롯 한 디렉터리 동기화 옵션을 사용 하려면 온-프레미스 디렉터리 특성이 표준을 충족 해야 합니다. 디렉터리에서 사용 되는 특성 및 필요한 정리 (있는 경우)에 대 한 자세한 내용은 [Prepare to the users to a directory synchronization to The Microsoft 365를](prepare-for-directory-synchronization.md)참조 하십시오. IdFix를 사용 하 여 디렉터리 정리를 자동화 하는 방법에 대 한 지침은 [Microsoft 365 idfix 도구 다운로드 및 실행](install-and-run-idfix.md) 을 참조 하세요. 

## <a name="plan-how-you-are-going-to-create-microsoft-365-accounts"></a>Microsoft 365 계정을 만드는 방법 계획

다음 표에서는 다양 한 계정 관리 도구를 보여 줍니다.

|**옵션**|**참고**|
|:-----|:-----|
|**관리 센터** | - [Microsoft 365에 개별적으로 또는 대량으로 사용자 추가-관리자 도움말](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -사용자 계정을 추가 및 변경할 수 있는 간단한 웹 인터페이스를 제공 합니다. <br> -디렉터리 동기화가 사용 하도록 설정 된 경우 (위치 및 라이선스 할당을 설정할 수 있음) 사용자를 변경 하는 데 사용할 수 없습니다. <br> -SSO 옵션과 함께 사용할 수 없습니다. <br> |
|**Windows PowerShell** | - [Windows PowerShell을 사용 하 여 Microsoft 365 관리](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -Windows PowerShell 스크립트를 사용 하 여 사용자를 대량 사용자에 게 추가할 수 있습니다. <br> -계정을 만드는 방법에 관계 없이 계정에 위치 및 라이선스를 할당 하는 데 사용할 수 있습니다. <br> |
|**대량 가져오기** | - [Microsoft 365에 여러 사용자를 동시에 추가-관리자 도움말](add-several-users-at-the-same-time.md) <br> -CSV 파일을 가져와 Microsoft 365에 사용자 그룹을 추가할 수 있습니다. <br> -SSO 옵션과 함께 사용할 수 없습니다. <br> |
|**Azure Active Directory** | -Microsoft 365 구독을 사용 하 여 무료 버전의 Azure Active Directory를 다운로드할 수 있습니다. -클라우드 사용자에 대해 셀프 서비스 암호 재설정 및 무료 버전을 사용 하 여 로그인 및 액세스 패널 페이지의 사용자 지정과 같은 기능을 수행할 수 있습니다. <br> -향상 된 기능을 가져오려면 기본 버전 또는 premium edition으로 업그레이드할 수 있습니다. 지원 되는 기능 목록은 [Azure Active Directory edition](https://go.microsoft.com/fwlink/p/?LinkId=698465) 를 참조 하세요. <br> |
|**디렉터리 동기화** | - [Azure Active Directory에 온-프레미스 id 통합](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -암호 동기화 여부와 관계 없이 디렉터리 동기화의 경우 [빠른 설정으로 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698537)를 사용 합니다.  <br>  -다중 포리스트 및 SSO 옵션에 대해 [AZURE AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다. <br> -SSO를 사용 하도록 설정 하는 데 필요한 인프라를 제공 합니다. <br> -많은 하이브리드 시나리오에 필요 (단계적 마이그레이션, 하이브리드 Exchange) <br> -온-프레미스 디렉터리에서 보안 및 메일 사용이 가능한 그룹을 동기화 합니다. <br> |

사용자 계정을 Microsoft 365에 추가 하려는 방법에 관계 없이 라이선스 할당, 위치 지정 등 여러 가지 계정 기능을 관리 해야 합니다. 이러한 기능은 관리 센터에서 장기간 관리할 수 있거나 [Microsoft 365 PowerShell을 사용 하 여 사용자 계정을 만들](https://go.microsoft.com/fwlink/p/?LinkId=717083)수도 있습니다.

관리 센터를 통해 모든 사용자를 추가 하 고 관리 하는 경우 Microsoft 365 계정을 만드는 것과 동시에 위치를 지정 하 고 라이선스를 할당 합니다. 따라서 계획은 그다지 많지 않아도 됩니다.

> [!IMPORTANT]
> 라이선스 (예: SharePoint Online에)를 할당 하지 않고 Microsoft 365에서 계정을 만드는 것은 계정 소유자가 Microsoft 365 관리 센터를 볼 수 있지만 회사 구독 내의 어떤 서비스에도 액세스 하지 못하는 것을 의미 합니다. 위치 및 라이선스를 할당 한 후에는 할당 한 서비스에 계정이 복제 됩니다. 사용자는 자신의 계정에 로그인 하 고 할당 한 서비스를 사용할 수 있습니다.