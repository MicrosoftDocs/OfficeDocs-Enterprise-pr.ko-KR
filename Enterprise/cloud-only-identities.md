---
title: Office 365 클라우드 전용 id
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Office 365 구독에서 클라우드 전용 id를 사용 하는 경우 사용자 및 그룹을 만드는 방법에 대해 설명 합니다.
ms.openlocfilehash: 0c066ca22f372c10b04c60f9bd44cf24300b6492
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844669"
---
# <a name="office-365-cloud-only-identities"></a>Office 365 클라우드 전용 id

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

클라우드 전용 id를 사용 하는 경우 모든 사용자, 그룹 및 연락처가 Office 365 구독의 azure AD (azure Active Directory) 테 넌 트에 저장 됩니다. 다음은 클라우드 전용 id의 기본 구성 요소입니다.
 
![클라우드 전용 id의 기본 구성 요소](./media/about-office-365-identity/cloud-only-identity.png)

조직의 사용자 및 사용자 계정을 다양 한 방법으로 분류할 수 있습니다. 예를 들어 직원은 직원과 영구 상태를 유지 합니다. 일부는 임시 상태인 공급 업체, 계약자 또는 파트너입니다. 일부는 사용자 계정이 없지만, 상호 작용 및 공동 작업을 지원 하기 위해 특정 서비스 및 리소스에 대 한 액세스 권한을 부여 해야 하는 외부 사용자입니다. 예시는 다음과 같습니다:

- 테넌트 계정은 클라우드 서비스에 대한 라이선스를 부여한 조직 내부의 사용자를 나타냅니다.

- B2B (business to Business) 계정은 공동 작업에 참여 하도록 초대한 조직 외부의 사용자를 조직에 게 표시 합니다. 그룹화 란? 예를 들어 조직에 대 한 높은 수준의 기능 또는 목적으로 사용자를 그룹화 할 수 있습니다.

또한 일부 클라우드 서비스는 사용자 계정 없이 조직 외부의 사용자와 공유될 수 있습니다. 이러한 사용자 그룹도 식별해야 합니다.

클라우드 환경을 관리 하는 여러 가지 용도로 Azure AD에서 그룹을 사용할 수 있습니다. 예를 들어 Azure AD 그룹을 사용 하 여 다음을 수행할 수 있습니다.

- 그룹 기반 라이선싱을 사용 하 여 추가 하는 즉시 사용자 계정에 Office 365에 대 한 라이선스를 자동으로 할당 합니다.
- 부서와 같은 사용자 계정 특성에 따라 특정 그룹에 동적으로 사용자 계정 추가
- Saas(Software as a Service) 응용 프로그램에 대해 사용자를 자동으로 프로비전하고 다단계 인증 및 기타 조건부 액세스 규칙을 사용하여 이러한 응용 프로그램에 대한 액세스 보호
- SharePoint Online 팀 사이트에 대 한 권한 및 액세스 수준 프로 비전

다음을 사용 하 여 새 ***사용자*** 를 만들 수 있습니다.

- [Microsoft 365 관리 센터](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

다음을 사용 하 여 새 ***그룹*** 을 만들 수 있습니다.

- [Microsoft 365 관리 센터](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a>클라우드 전용 id의 다음 단계

[사용자 계정에 라이선스 할당](assign-licenses-to-user-accounts.md)
