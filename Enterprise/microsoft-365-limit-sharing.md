---
title: Microsoft 365에서의 공유 제한
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.custom: ''
localization_priority: Priority
description: Microsoft 365에서 공유를 제한하는 방법에 대해 알아봅니다.
ms.openlocfilehash: dd2705aefd4f91c4ce8773019f94acf53afea6c8
ms.sourcegitcommit: 4f465f690c6563cfa9f6029d3e7e9e3cace96671
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41658802"
---
# <a name="limit-sharing-in-microsoft-365"></a>Microsoft 365에서의 공유 제한

내부 공유를 완전히 비활성화하거나 사이트에서 공유 버튼을 제거할 수는 없지만 조직의 요구를 충족시키기 위해 Microsoft 365에서 공유를 제한할 수 있는 다양한 방법이 있습니다.

파일 공유 방법은 아래 표에 나열되어 있습니다. 자세한 정보를 확인하려면 **공유 방법** 열에서 해당 링크를 클릭하세요.

|공유 방법|설명|제한 옵션|
|:-------------|:----------|:-------------|
|[Office 365 그룹 또는 팀](#office-365-group-or-team)|Microsoft Teams 팀 또는 Office 365 그룹에 대한 액세스 권한을 받은 사람들은 연결된 SharePoint 사이트의 파일에 대한 편집 권한을 갖습니다.|그룹 또는 팀이 비공개인 경우 팀에 대한 초대 공유는 승인을 위해 소유자에게 이동됩니다. 관리자는 게스트 액세스를 비활성화하여 조직 외부의 사람들이 액세스하지 못하게 할 수 있습니다.|
|[SharePoint 사이트](#sharepoint-site)|사람들은 소유자, 회원 또는 방문자에게 SharePoint 사이트에 대한 액세스 권한을 부여할 수 있으며 사이트의 파일에 대해 해당 수준의 액세스 권한을 갖습니다.|사이트 소유자만 사이트를 공유할 수 있도록 사이트 권한을 제한할 수 있습니다.|
|[특정 사용자와 공유](#sharing-with-specific-people)|편집 권한이 있는 사이트 구성원과 사용자는 *특정 사용자* 링크를 사용하여 파일 및 폴더에 직접 권한을 부여하거나 공유할 수 있습니다.|사이트 소유자만 파일 및 폴더를 공유할 수 있도록 사이트 권한을 제한할 수 있습니다. 이 경우 사이트 구성원의 직접 액세스 및 *특정 사용자* 링크 공유는 소유자에게 전달되어 승인을 받을 수 있습니다.|
|[SharePoint 게스트 공유](#sharepoint-guest-sharing)|SharePoint 사이트 소유자 및 구성원은 조직 외부의 사용자와 파일 및 폴더를 공유할 수 있습니다.|전체 조직 또는 개별 사이트에 대해 게스트 공유 기능을 비활성화할 수 있습니다.|
|[*조직 내부 사용자* 공유 링크](#people-in-your-organization-sharing-links)|SharePoint 사이트 소유자 및 구성원은 *조직 내 사용자* 링크를 사용하여 파일을 공유할 수 있으며, 이는 조직 내부의 모든 사람이 사용할 수 있습니다.|사이트 수준에서 *조직의 사용자* 링크를 비활성화할 수 있습니다.|
|[전자 메일](#email)|파일에 대한 액세스 권한이 있는 사용자는 전자 메일을 통해 파일을 다른 사용자에게 보낼 수 있습니다.|관리자는 민감도 레이블을 사용하여 파일이 권한 없는 사용자와 공유되지 않도록 파일을 암호화할 수 있습니다.|
|[다운로드 또는 파일 복사](#download-or-file-copy)|파일에 대한 액세스 권한이 있는 사용자는 파일을 다운로드하거나 복사하여 이를 Microsoft 365 범위 밖에 있는 다른 사용자와 공유할 수 있습니다.|관리자는 민감도 레이블을 사용하여 파일이 권한 없는 사용자와 공유되지 않도록 파일을 암호화할 수 있습니다.|

이 문서에 설명된 관리 컨트롤을 사용하여 조직의 공유를 제한할 수 있지만 Microsoft 365에서 제공되는 보안 및 규정 준수 기능을 사용하여 안전한 공유 환경을 만드는 것을 고려해 볼 것을 강력히 권장합니다. 자세한 내용은 [ Microsoft 365와 SharePoint의 파일 공동 작업](https://docs.microsoft.com/sharepoint/deploy-file-collaboration) 및 [엄격히 규제되는 데이터용 Teams](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario)을 참조하십시오.

조직에서 공유를 사용하는 방법을 이해하려면 [파일 및 폴더 공유에 대한 보고서를 실행하세요](https://docs.microsoft.com/sharepoint/sharing-reports).

## <a name="office-365-group-or-team"></a>Office 365 그룹 또는 팀

Office 365 그룹 또는 Microsoft Teams 팀에서 공유를 제한하려는 경우 그룹 또는 팀을 비공개로 설정하는 것이 중요합니다. 조직 내부 사용자는 언제든 지 공용 그룹이나 팀에 참석할 수 있습니다. 그룹이나 팀이 비공개가 아닌 이상, 조직 내에서 팀 또는 해당 파일의 공유를 제한할 수 있는 방법이 없습니다.

### <a name="guest-sharing"></a>게스트 공유

Teams에서 게스트 액세스를 방지하려는 경우 Teams 관리 센터에서 게스트 공유를 해제할 수 있습니다.

Teams에 대해 게스트 공유를 해제하려면
1. Teams 관리 센터에서 **조직 전체 설정**을 확장한 다음 **게스트 액세스**를 클릭합니다.
2. **Teams에서 게스트 액세스 허용**을 해제합니다.
3. **저장**을 클릭합니다.

Office 365 그룹에서 게스트 액세스를 방지하려는 경우 Microsoft 365 관리 센터에서 그룹 게스트 액세스 설정을 해제할 수 있습니다.

Office 365 그룹에서 게스트 공유를 해제하려면
1. Microsoft 365 관리 센터에서 **설정**을 클릭한 다음 **설정**을 클릭합니다.
2. **서비스** 탭에서 **Office 365 그룹**을 클릭합니다.
3. **조직 외부의 그룹 구성원이 그룹 콘텐츠에 액세스할 수 있도록 허용** 및 **그룹 소유자가 조직 외부의 사람을 그룹에 추가하도록 허용** 확인란을 선택 취소합니다.
4. **변경 내용 저장**을 클릭 합니다.

    ![Microsoft 365 관리 센터의 Office 365 그룹 공유 설정 스크린샷](media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> 특정 그룹이나 팀에 대한 게스트 공유를 방지하려는 경우 Microsoft PowerShell을 사용하여 이 작업을 수행할 수 있습니다. 자세한 내용은 [특정 그룹의 게스트 사용자 차단](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group)을 참조하십시오.

Azure Active Directory에서 도메인을 허용하거나 차단하여 게스트를 특정 도메인의 사용자로 제한할 수 있습니다. [Azure AD B2B를 SharePoint 및 OneDrive와 통합](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)을 활성화한 경우 이러한 설정은 SharePoint의 게스트 공유에도 영향을 줍니다.

지정된 도메인에서만 초대를 공유할 수 있도록 허용하려면
1. Azure Active Directory의 개요 페이지에서 **조직 관계**를 클릭합니다.
2. **설정**을 클릭합니다.
3. **공동 작업 제한 사항**에서 **지정된 도메인에 대한 초대 거부** 또는 **지정된 도메인에 대한 초대만 허용**을 선택한 다음 사용하려는 도메인을 입력하십시오.
4. **저장**을 클릭합니다.

    ![Azure Active Directory의 공동 작업 제한 설정 스크린샷](media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a>SharePoint 사이트

SharePoint 사이트 공유를 사이트 소유자에게만 제한할 수 있습니다. 이렇게 하면 사이트 구성원이 사이트를 공유할 수 없습니다. 사이트가 Office 365 그룹에 연결된 경우 그룹 구성원은 다른 사람을 그룹에 초대할 수 있으며 해당 사용자는 사이트에 액세스할 수 있음을 기억하십시오.

소유자에게로만 사이트 공유를 제한하려면
1. 사이트에서 톱니바퀴 아이콘을 클릭한 다음 **사이트 권한**을 클릭합니다.
2. **공유 설정**에서 **공유 설정 변경**을 클릭합니다.
3. **사이트 소유자 및 구성원, 편집 권한이 있는 사용자는 파일 및 폴더를 공유할 수 있지만 사이트는 오직 사이트 소유자만 공유**를 선택합니다.
4. **저장**을 클릭합니다.

    ![SharePoint 사이트의 공유 권한 설정의 스크린샷](media/sharepoint-site-sharing-permissions-level-two.png)

액세스 요청을 해제하여 사이트의 구성원이 아닌 사용자가 액세스를 요청하지 못하도록 할 수 있습니다.

액세스 요청을 해제하려면
1. 사이트에서 톱니바퀴 아이콘을 클릭한 다음 **사이트 권한**을 클릭합니다.
2. **공유 설정**에서 **공유 설정 변경**을 클릭합니다.
3. **액세스 요청 허용**을 해제한 다음, **저장**을 클릭합니다.

사이트에 대한 도메인을 허용하거나 차단하여 사이트 공유를 특정 도메인으로 제한할 수 있습니다.

사이트 공유를 도메인별로 제한하려면
1. SharePoint 관리 센터의 **사이트**에서 **활성 사이트**를 클릭하십시오.
2. 동기화할 사이트를 클릭합니다.
3. **정책** 탭의 **외부 공유**에서 **편집**을 클릭합니다.
4. **외부 공유에 대한 고급 설정**에서 **도메인별 공유 제한**을 선택합니다.
5. 허용하거나 차단할 도메인을 추가하고 **저장**을 클릭합니다.
6. **저장**을 클릭합니다.

    ![허용된 도메인 사이트 수준 설정 스크린샷](media/limit-site-sharing-by-domain.png)

## <a name="sharing-with-specific-people"></a>특정 사용자와 공유

사이트 또는 해당 콘텐츠의 공유를 제한하려는 경우 사이트 소유자만 파일, 폴더 및 사이트를 공유하도록 사이트를 구성할 수 있습니다. 이러한 내용이 구성되면 사이트 구성원이 *특정 사용자* 링크를 사용하여 파일 또는 폴더를 공유하려는 시도가 승인을 위해 사이트 소유자에게 전달됩니다.

사이트, 파일 및 폴더 공유를 소유자에게로만 제한하려면
1. 사이트에서 톱니바퀴 아이콘을 클릭한 다음 **사이트 권한**을 클릭합니다.
2. **공유 설정**에서 **공유 설정 변경**을 클릭합니다.
3. **오직 사이트 소유자만 파일, 폴더 및 사이트를 공유**를 선택합니다.
4. **저장**을 클릭합니다.

    ![SharePoint 사이트의 공유 권한 설정의 스크린샷](media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a>SharePoint 게스트 공유

조직 외부 사람과 SharePoint 또는 OneDrive 파일 및 폴더를 공유하지 못하게 하려면 전체 조직 또는 개별 사이트에 대한 게스트 공유를 해제할 수 있습니다.

조직에 대한 SharePoint 게스트 공유를 끄려면
1. SharePoint 관리 센터의 **정책**에서 **공유**를 클릭하십시오.
2. **외부 공유**에서 SharePoint 슬라이더를 아래쪽에 있는 **조직의 사용자에게만**으로 드래그합니다.
3. **저장**을 클릭합니다.

    ![SharePoint 조직 수준 공유 설정의 스크린샷](media/sharepoint-tenant-sharing-off.png)


사이트에 대해 게스트 공유를 해제하려면
1. SharePoint 관리 센터의 **사이트**에서 **활성 사이트**를 클릭하십시오.
2. 동기화할 사이트를 클릭합니다.
3. **정책** 탭의 **외부 공유**에서 **편집**을 클릭합니다.
4. **외부 공유**에서 **조직의 사용자에게만**을 선택한 다음 **저장**을 클릭합니다.

    ![SharePoint 사이트 수준 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings-off.png)

조직 외부의 사람들과의 공유를 허용하지만 모든 사람이 인증을 받도록 하려면 전체 조직 또는 개별 사이트에 대해 *모든 사용자*(익명 공유) 링크를 비활성화할 수 있습니다.

조직 수준에서 *모든 사용자* 링크를 해제하려면
1. SharePoint 관리 센터의 **정책**에서 **공유**를 클릭하십시오.
2. **외부 공유**에서 SharePoint 슬라이더를 아래쪽에 있는 **신규 및 기존 게스트**로 드래그합니다.
3. **저장**을 클릭합니다.

    ![SharePoint 사이트 수준 공유 설정 스크린샷](media/sharepoint-guest-sharing-new-and-existing-guests.png)

사이트에 대해 *Anyone* 링크를 해제하려면
1. SharePoint 관리 센터의 **사이트**에서 **활성 사이트**를 클릭하십시오.
2. 동기화할 사이트를 클릭합니다.
3. **정책** 탭의 **외부 공유**에서 **편집**을 클릭합니다.
4. **외부 공유**에서 OneDrive에 대한 **신규 및 기존 게스트**를 선택한 다음, **저장**을 클릭합니다.

    ![SharePoint 사이트 수준 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings-new-and-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a>*조직 내부 사용자* 공유 링크

기본적으로 사이트 회원은 *조직 내 사용자* 링크를 사용하여 조직의 다른 사람과 파일 및 폴더를 공유할 수 있습니다. PowerShell을 사용하여 *조직 내 사용자* 링크를 비활성화할 수 있습니다.

`Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks`

다음의 예를 참조하십시오.

`Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks`

## <a name="email"></a>전자 메일

암호화를 사용하여 전자 메일이 의도하지 않게 공유되는 것을 방지할 수 있습니다. 따라서 전자 메일이 전달되거나 허가되지 않은 사용자에게 공유되는 것을 방지할 수 있습니다. 민감도 레이블을 사용하여 전자 메일 암호화를 활성화할 수 있습니다. 자세한 내용은 [민감도 레이블에서 암호화를 사용하여 콘텐츠 액세스 제한](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)을 참조하세요.

## <a name="download-or-file-copy"></a>다운로드 또는 파일 복사

Microsoft 365의 파일 및 폴더에 대한 액세스 권한이 있는 사용자는 파일을 다운로드하고 외부 미디어에 복사할 수 있습니다. 원치 않는 파일이 공유되는 위험을 줄이기 위해 민감도 레이블을 사용하여 콘텐츠를 암호화할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Microsoft 365 게스트 공유 설정 참조](microsoft-365-guest-settings.md)