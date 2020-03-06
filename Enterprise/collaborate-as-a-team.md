---
title: 게스트와 팀으로 공동 작업하기
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: 팀에서 게스트와 공동 작업 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 87635d6fd2196fd706d27fb68cbe24e51b723220
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549137"
---
# <a name="collaborate-with-guests-in-a-team"></a>게스트와 팀으로 공동 작업하기

여러 문서, 작업 및 대화에서 게스트와 공동 작업을 수행 해야 하는 경우 Microsoft 팀을 사용 하는 것이 좋습니다. 팀은 영구 채팅 및 통합 사용자 환경에서 사용자 지정 및 확장 가능한 공동 작업 도구 집합을 사용 하 여 Office 및 SharePoint에서 사용할 수 있는 모든 공동 작업 기능을 제공 합니다.

이 문서에서는 게스트와의 공동 작업을 위해 팀을 설정 하는 데 필요한 Microsoft 365 구성 단계를 안내 합니다.

## <a name="video-demonstration"></a>비디오 데모

이 비디오에서는이 문서에서 설명 하는 구성 단계를 보여 줍니다.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a>Azure 조직 관계 설정

Microsoft 365의 공유는 Azure Active Directory의 조직 관계 설정에 따라 최상위 수준에서 관리 됩니다. Azure AD에서 게스트 공유가 사용 하지 않도록 설정 되거나 제한 되 면 Microsoft 365에서 구성한 모든 공유 설정이 재정의 됩니다.

조직 관계 설정을 확인 하 여 게스트가 공유 하는 것이 차단 되지 않는지 확인 합니다.

![Azure Active Directory 조직 관계 설정 페이지 스크린샷](media/azure-ad-organizational-relationships-settings.png)

조직 관계 설정을 설정 하려면

1. Microsoft Azure에 로그인 [https://portal.azure.com](https://portal.azure.com)합니다.
2. 왼쪽 탐색 창에서 **Azure Active Directory**를 클릭 합니다.
3. **개요** 창에서 **조직 관계**를 클릭 합니다.
4. **조직 관계** 창에서 **설정을**클릭 합니다.
5. **Guest inviter 역할의 관리자 및 사용자가 초대** 를 하 고 **구성원은 초대** 를 할 수 있는지 확인 하 고 둘 다 **예**로 설정 합니다.
6. 변경한 내용이 있으면 **저장**을 클릭합니다.

**공동 작업 제한** 섹션의 설정을 확인 합니다. 공동 작업 하려는 게스트의 도메인이 차단 되지 않았는지 확인 합니다.

## <a name="teams-guest-access-settings"></a>팀 게스트 액세스 설정

팀에는 게스트 액세스에 대 한 마스터 온/오프 스위치가 있으며, 팀원 들이 어떤 게스트 작업을 수행할 수 있는지를 제어 하는 다양 한 설정을 사용할 수 있습니다. 게스트 액세스를 팀에서 작동 시키려면 마스터 스위치를 사용 하 여 **팀에서 게스트 액세스 허용** 이 **설정** 되어 있어야 합니다.

팀에서 게스트 액세스를 사용 하도록 설정 되어 있는지 확인 하 고 비즈니스 요구에 따라 게스트 설정을 조정 합니다. 이러한 설정은 모든 팀에 영향을 줍니다.

![Teams의 게스트 액세스 토글의 스크린샷](media/teams-guest-access-toggle-on.png)

팀 게스트 액세스 설정을 설정 하려면

1. 에서 [https://admin.microsoft.com](https://admin.microsoft.com)Microsoft 365 관리 센터에 로그인 합니다.
2. 왼쪽 탐색 영역에서 **모두 표시**를 클릭 합니다.
3. **관리 센터**에서 **팀**을 클릭 합니다.
4. 팀 관리 센터의 왼쪽 탐색 창에서 **조직 전체 설정을** 확장 하 고 **게스트 액세스**를 클릭 합니다.
5. **팀에서 게스트 액세스 허용** 이 설정 되어 있는지 확인 **합니다.**
6. 추가 게스트 설정을 원하는 대로 변경한 다음 **저장**을 클릭 합니다.

> [!NOTE]
> 팀 게스트 설정이 설정 된 후 활성 상태가 되는 데 최대 24 시간이 걸릴 수 있습니다.

## <a name="office-365-groups-guest-settings"></a>Office 365 그룹 게스트 설정

팀에서는 team 구성원에 게 Office 365 그룹을 사용 합니다. 팀에서 게스트 액세스를 작동 하려면 Office 365 그룹 게스트 설정이 설정 되어 있어야 합니다.

![Microsoft 365 관리 센터의 Office 365 그룹 게스트 설정 스크린샷](media/office-365-groups-guest-settings.png)

Office 365 그룹 게스트 설정을 설정 하려면

1. Microsoft 365 관리 센터의 왼쪽 탐색 영역에서 **설정을**확장 합니다.
2. **서비스 & 추가 기능**을 클릭 합니다.
3. 목록에서 **Office 365 그룹**을 클릭 합니다.
4. **조직 외부 구성원이 그룹 콘텐츠에 액세스** 하 고 그룹 **소유자가 조직 외부의 사람을 그룹에 추가** 하도록 허용 확인란을 모두 선택 했는지 확인 합니다.
5. 변경한 경우 **변경 내용 저장**을 클릭 합니다.


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 조직 수준 공유 설정

파일, 폴더 및 목록과 같은 팀 콘텐츠는 모두 SharePoint에 저장 됩니다. 게스트가 팀의 이러한 항목에 액세스할 수 있도록 하려면 SharePoint 조직 수준 공유 설정에서 게스트가 공유 하도록 허용 해야 합니다.

조직 수준 설정에 따라 팀에 연결 된 사이트를 포함 하 여 개별 사이트에서 사용할 수 있는 설정이 결정 됩니다. 사이트 설정은 조직 수준 설정 보다는 더 이상 허용 되지 않습니다.

인증 되지 않은 사용자와 파일 및 폴더 공유를 허용 하려면 **모든 사용자**를 선택 합니다. 모든 게스트가 인증을 받도록 하려면 **신규 및 기존 게스트**를 선택 합니다. 조직의 모든 사이트에 필요한 가장 관대 한 설정을 선택 합니다.

![SharePoint 조직 수준 공유 설정의 스크린샷](media/sharepoint-organization-external-sharing-controls.png)


SharePoint 조직 수준 공유 설정을 설정 하려면

1. Microsoft 365 관리 센터의 왼쪽 탐색에 있는 **관리 센터**에서 **SharePoint**를 클릭 합니다.
2. 왼쪽 탐색 창의 SharePoint 관리 센터에서 **공유**를 클릭합니다.
3. SharePoint 용 외부 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.
4. 변경한 내용이 있으면 **저장**을 클릭합니다.


## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint 조직 수준 기본 링크 설정

기본 파일 및 폴더 링크 설정에 따라 파일 또는 폴더를 공유할 때 기본적으로 사용자에 게 표시 되는 링크 옵션이 결정 됩니다. 원하는 경우 공유 하기 전에 다른 옵션 중 하나로 연결 유형을 변경할 수 있습니다.

이 설정은 조직의 모든 팀 및 SharePoint 사이트에 영향을 줍니다.

사용자가 파일 및 폴더를 공유할 때 기본적으로 선택 되는 링크 유형을 선택 합니다.

- **링크가 있는 모든 사용자** -파일 및 폴더의 인증 되지 않은 공유를 많이 사용 하는 경우이 옵션을 선택 합니다. *모든* 링크를 허용 하지만 실수로 인증 되지 않은 공유가 발생 하는 것이 염려 되는 경우에는 다른 옵션 중 하나를 기본값으로 사용 하는 것이 좋습니다. 이 링크 형식은 **모든 사용자** 가 공유 하도록 설정한 경우에만 사용할 수 있습니다.
- **조직의 사용자만** 조직 내부 사용자와 파일 및 폴더 공유를 사용할 것으로 예상 되는 경우이 옵션을 선택 합니다.
- **특정 사용자** -게스트와 파일 및 폴더 공유를 많이 수행 해야 하는 경우이 옵션을 고려 하세요. 이 유형의 링크는 게스트에서 작동 하며 인증을 요구 합니다.
 
![SharePoint 조직 수준 파일 및 폴더 공유 설정 스크린샷](media/sharepoint-organization-files-folders-sharing-settings.png)


SharePoint 조직 수준 기본 링크 설정을 설정 하려면

1. SharePoint 관리 센터에서 공유 페이지로 이동 합니다.
2. **파일 및 폴더 링크**에서 사용 하려는 기본 공유 링크를 선택 합니다.
3. 변경한 내용이 있으면 **저장**을 클릭합니다.

## <a name="create-a-team"></a>팀 만들기

다음 단계는 게스트와 공동 작업 하는 데 사용할 팀을 만드는 것입니다.

팀을 만들려면
1. 팀의 **팀** 탭에서 왼쪽 창의 아래쪽에 있는 **참가 또는 팀 만들기** 를 클릭 합니다.
2. **팀 만들기를**클릭 합니다.
3. **팀 구성 처음부터 새로 만들기**를 클릭 합니다.
4. **개인** 또는 **공개**를 선택 합니다.
5. 팀의 이름과 설명을 입력 하 고 **만들기**를 클릭 합니다.
6. **건너뛰기를**클릭 합니다.

나중에 사용자를 초대 합니다. 다음으로 팀과 연결 된 SharePoint 사이트에 대 한 사이트 수준 공유 설정을 확인 하는 것이 중요 합니다.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 사이트 수준 공유 설정

사이트 수준 공유 설정을 확인 하 여이 팀에 대해 원하는 액세스 유형을 허용 하는지 확인 합니다. 예를 들어 조직 수준 설정을 모든 **사용자**로 설정 했지만 모든 게스트가이 팀에 대해 인증을 받으려는 경우에는 사이트 수준 공유 설정이 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.

![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings.png)


사이트 수준 공유 설정을 설정 하려면
1. SharePoint 관리 센터의 왼쪽 탐색 창에서 **사이트**를 확장시키고 **Active 사이트**를 클릭합니다.
2. 방금 생성한 팀의 사이트를 선택합니다.
3. 리본 메뉴에서 **공유**를 클릭합니다.
4. 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.
5. 변경한 내용이 있으면 **저장**을 클릭합니다.

## <a name="invite-users"></a>사용자 초대

이제 게스트 공유 설정이 구성 되므로 팀에 내부 사용자 및 게스트를 추가할 수 있습니다. 

팀에 내부 사용자를 초대 하려면
1. 팀에서 **기타 옵션** (**\*\***)을 클릭 하 고 **구성원 추가**를 클릭 합니다.
2. 초대 하려는 사용자의 이름을 입력 합니다.
3. **추가**를 클릭한 다음 **닫기**를 클릭합니다.

팀에 게스트를 초대 하려면
1. 팀에서 **기타 옵션** (**\*\***)을 클릭 하 고 **구성원 추가**를 클릭 합니다.
2. 초대 하려는 게스트의 전자 메일 주소를 입력 합니다.
3. **게스트 정보 편집**을 클릭 합니다.
4. 게스트의 전체 이름을 입력 하 고 확인 표시를 클릭 합니다.
5. **추가**를 클릭한 다음 **닫기**를 클릭합니다.

## <a name="see-also"></a>참고 항목

[인증되지 않은 사용자와 파일 및 폴더를 공유하는 모범 사례](best-practices-anonymous-sharing.md)

[게스트와 공유할 때 파일에 실수로 발생하는 노출을 제한](sharing-limit-accidental-exposure.md)

[보안 게스트 공유 환경 만들기](create-a-secure-guest-sharing-environment.md)

[관리 대상 게스트와 B2B 엑스트라넷 작성](b2b-extranet.md)
