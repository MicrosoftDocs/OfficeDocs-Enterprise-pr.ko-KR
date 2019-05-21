---
title: Office 365 id 모델 및 Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: 421002825842201fa754b4c5579dc04fde37eeaf
ms.sourcegitcommit: 2a7177c666dce3c00462b97463a6855e9e3a81f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "34249466"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a>Office 365 id 모델 및 Azure Active Directory

Office 365에서는 office 365 구독에 포함 되어 있는 Azure Active Directory (Azure AD), 클라우드 기반 사용자 id 및 인증 서비스를 사용 하 여 office 365에 대 한 id 및 인증을 관리 합니다. 조직에 대 한 Office 365 사용자 액세스 및 사용 권한을 관리 하려면 id 인프라를 올바르게 구성 하는 것이 중요 합니다.

시작 하기 전에이 비디오에서 Office 365 및 Microsoft 365에 대 한 id 모델 및 인증에 대 한 개요를 시청 하세요.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

첫 번째 계획 선택은 Office 365 id 모델입니다.

## <a name="office-365-identity-models"></a>Office 365 id 모델

사용자 계정을 계획 하려면 먼저 Microsoft 365에서 두 가지 id 모델을 이해 해야 합니다. 조직의 id는 클라우드에서만 유지 관리할 수 있으며, 사용자가 Microsoft 365 클라우드 서비스에 액세스할 때 온-프레미스 AD DS (Active Directory 도메인 서비스) id를 유지 관리 하 고 인증에 사용할 수 있습니다.  

다음은 두 가지 유형의 id와 가장 적합 한 일치 및 장점입니다.

|||
|:-------|:-----|:-----|
|  | **클라우드 전용 id** | **하이브리드 id** |
| **정의** | 사용자 계정이 Microsoft 365 구독의 azure AD (Active Directory) 테 넌 트에만 있습니다. | 사용자 계정이 AD DS에 있고 복사본은 Microsoft 365 구독의 Azure AD 테 넌 트에도 있습니다. 또한 Azure AD의 사용자 계정에는 사용자 계정 암호의 해시 된 버전을 포함할 수 있습니다. |
| **Microsoft 365에서 사용자 자격 증명을 인증 하는 방법** | Microsoft 365 구독의 Azure AD 테 넌 트는 클라우드 id 계정을 사용 하 여 인증을 수행 합니다. | Microsoft 365 구독에 대 한 Azure AD 테 넌 트가 인증 프로세스를 처리 하거나 사용자를 다른 id 공급자로 리디렉션합니다. |
| **최적 시나리오** | 온-프레미스 AD DS가 없거나 필요 하지 않은 조직 | AD DS 또는 다른 id 공급자를 사용 하는 조직 |
| **가장 큰 혜택** | 간편 하 게 사용할 수 있습니다. 추가 디렉터리 도구 또는 서버가 필요 하지 않습니다. | 사용자는 온-프레미스 또는 클라우드 기반 리소스에 액세스할 때 동일한 자격 증명을 사용할 수 있습니다. |
||||

## <a name="cloud-only-identity"></a>클라우드 전용 id

클라우드 전용 id는 Azure AD에만 있는 사용자 계정을 사용 합니다. 클라우드 id는 일반적으로 온-프레미스 서버가 없거나 AD DS를 사용 하 여 로컬 id를 관리 하지 않는 소규모 조직에서 사용 됩니다. 

다음은 클라우드 전용 id의 기본 구성 요소입니다.
 
![](./media/about-office-365-identity/cloud-only-identity.png)

온-프레미스 및 원격 (온라인)은 모두 Azure AD 사용자 계정 및 암호를 사용 하 여 Office 365 클라우드 서비스에 액세스 합니다. Azure AD는 저장 된 사용자 계정 및 암호를 기반으로 사용자 자격 증명을 인증 합니다.

### <a name="administration"></a>관리
사용자 계정은 Azure AD에만 저장 되므로 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 [Microsoft 365 관리 센터](https://admin.microsoft.com) 및 Windows PowerShell과 같은 도구를 사용 하 여 클라우드 id를 관리 합니다. 

## <a name="hybrid-identity"></a>하이브리드 id

하이브리드 id는 온-프레미스 AD DS에서 시작 되 고 Microsoft 365 구독의 Azure AD 테 넌 트에 복사본을 포함 하는 계정을 사용 합니다. 그러나 대부분의 변경 내용은 단방향 으로만 흐릅니다. AD DS 사용자 계정에 대해 수행한 변경 내용이 Azure AD에서 해당 복사본에 동기화 됩니다. 그러나 새 사용자 계정과 같은 Azure AD의 클라우드 기반 계정에 대 한 변경 내용은 AD DS와 동기화 되지 않습니다.

Azure AD Connect는 진행 중인 계정 동기화를 제공 합니다. 이 도구는 온-프레미스 서버에서 실행 되 고, AD DS의 변경 내용을 확인 하 고, 해당 변경 내용을 Azure AD로 전달 합니다. Azure AD Connect는 동기화 되는 계정 및 해시 된 버전의 사용자 암호를 동기화 (암호 해시 동기화 (PHS)) 할지 여부를 필터링 하는 기능을 제공 합니다.

하이브리드 id를 구현 하는 경우 온-프레미스 AD DS가 계정 정보에 대 한 신뢰할 수 있는 원본입니다. 즉, 관리 작업을 주로 온-프레미스로 수행한 다음 Azure AD와 동기화 합니다. 

하이브리드 id의 구성 요소는 다음과 같습니다.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD 테 넌 트에는 AD DS 계정의 복사본이 있습니다. 이 구성에서 Microsoft 365 클라우드 서비스에 액세스 하는 온-프레미스 및 원격 사용자 둘 다 Azure AD에 대해 인증을 수행 합니다.

>[!Note]
>하이브리드 id에 대해 사용자 계정을 동기화 하려면 항상 Azure AD Connect를 사용 해야 합니다. 라이선스 할당 및 그룹 관리, 사용 권한 구성 및 사용자 계정을 포함 하는 기타 관리 작업을 수행 하려면 Azure AD에서 동기화 된 사용자 계정이 필요 합니다.
>

### <a name="administration"></a>관리

원본 및 신뢰할 수 있는 사용자 계정이 온-프레미스 AD DS에 저장 되기 때문에 Active Directory 사용자 및 컴퓨터 도구와 같은 도구를 사용 하 여 AD DS와 동일한 도구로 id를 관리 합니다. 

Microsoft 365 관리 센터 또는 Windows PowerShell을 사용 하 여 Azure AD에서 동기화 된 사용자 계정을 관리 하지는 않습니다.

## <a name="next-step"></a>다음 단계

클라우드 전용 id 모델이 필요한 경우 [클라우드 전용](cloud-only-identities.md)id를 참조 하세요.

하이브리드 id 모델이 필요한 경우 [디렉터리 동기화](plan-for-directory-synchronization.md)를 참조 하세요.
  

## <a name="video-training"></a>동영상 교육

LinkedIn 학습을 통해 가져온 [Office 365: AZURE AD Connect를 사용 하 여 Id 관리](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)코스를 참조 하세요.
