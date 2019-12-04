---
title: 사용자 계정에 Office 365 라이선스 할당
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 사용자 계정에 개별적으로 또는 그룹 구성원을 기반으로 Office 365 라이선스를 할당 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 169f5a3c0bf75bf807c40338542e0ba15b79a1bc
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813386"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>사용자 계정에 Office 365 라이선스 할당

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

클라우드 전용 id 모델의 경우 만든 방법에 따라 사용자 계정에 Office 365 라이선스를 할당할 수 있습니다.

하이브리드 id 모델의 경우 AD DS (Active Directory 도메인 서비스) 사용자 계정이 처음으로 동기화 되 면 Office 365 라이선스가 자동으로 할당 되지 않습니다.

어느 경우 든 사용자가 전자 메일 및 Microsoft 팀과 같은 Office 365 서비스에 액세스할 수 있도록 사용자 계정에 라이선스를 할당 해야 합니다.

사용자 계정에 개별적으로 또는 자동으로 그룹 구성원 자격을 통해 라이선스를 할당할 수 있습니다.

개별 사용자 계정에 Office 365 라이선스를 할당 하려면 다음을 사용할 수 있습니다.

- [Microsoft 365 관리 센터](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

라이선스를 자동으로 할당 하려면 [AZURE AD에서 그룹 기반 라이선싱](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)을 참조 하십시오.

## <a name="next-steps"></a>다음 단계

라이선스가 할당 된 전체 사용자 계정 집합을 사용 하 여 다음 작업을 수행할 준비가 되었습니다.

- [보안 구현](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Office 365 ProPlus와 같은 클라이언트 소프트웨어 배포](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Office 365에서 모바일 장치 관리 설정](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [서비스 및 응용 프로그램 구성](configure-services-and-applications.md)
