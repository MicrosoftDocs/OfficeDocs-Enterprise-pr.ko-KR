---
title: 게스트와 현장에서 공동 작업하기
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: SharePoint 사이트에서 게스트와 공동 작업 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 31e1365467729753cec358b4fb33462894cdcbb8
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261361"
---
# <a name="collaborate-with-guests-in-a-site"></a>게스트와 현장에서 공동 작업하기

여러 문서, 데이터 및 목록에서 게스트와 공동 작업을 수행 해야 하는 경우에는 SharePoint 사이트를 사용할 수 있습니다. 최신 SharePoint 사이트는 사이트 구성원 자격을 관리 하 고 공유 사서함 및 일정과 같은 추가 공동 작업 도구를 제공할 수 있는 Office 365 그룹에 연결 됩니다.

이 문서에서는 게스트가 포함 된 공동 작업을 위해 SharePoint 사이트를 설정 하는 데 필요한 Microsoft 365 구성 단계를 안내 합니다.

## <a name="video-demonstration"></a>비디오 데모

이 비디오에서는이 문서에서 설명 하는 구성 단계를 보여 줍니다.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

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

## <a name="office-365-groups-guest-settings"></a>Office 365 그룹 게스트 설정

최신 SharePoint 사이트에서는 Office 365 그룹을 사용 하 여 사이트 액세스를 제어 합니다. SharePoint 사이트에서 게스트 액세스를 작동 하려면 Office 365 그룹 게스트 설정이 설정 되어 있어야 합니다.

![Microsoft 365 관리 센터의 Office 365 그룹 게스트 설정 스크린샷](media/office-365-groups-guest-settings.png)

Office 365 그룹 게스트 설정을 설정 하려면

1. Microsoft 365 관리 센터의 왼쪽 탐색 영역에서 **설정을**확장 합니다.
2. **서비스 & 추가 기능**을 클릭 합니다.
3. 목록에서 **Office 365 그룹**을 클릭 합니다.
4. **조직 외부 구성원이 그룹 콘텐츠에 액세스** 하 고 그룹 **소유자가 조직 외부의 사람을 그룹에 추가** 하도록 허용 확인란을 모두 선택 했는지 확인 합니다.
5. 변경한 경우 **변경 내용 저장**을 클릭 합니다.


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 조직 수준 공유 설정

게스트가 SharePoint 사이트에 액세스할 수 있도록 하려면 SharePoint 조직 수준 공유 설정에서 guests 공유를 허용 해야 합니다.

조직 수준 설정에 따라 개별 사이트에 사용할 수 있는 설정이 결정 됩니다. 사이트 설정은 조직 수준 설정 보다는 더 이상 허용 되지 않습니다.

인증 되지 않은 파일 및 폴더 공유를 허용 하려면 **모든 사용자**를 선택 합니다. 조직 외부의 모든 사용자가 인증을 받아야 하는 것을 확인 하려면 **신규 및 기존 게스트**를 선택 합니다. 조직의 모든 사이트에 필요한 가장 관대 한 설정을 선택 합니다.

![SharePoint 조직 수준 공유 설정의 스크린샷](media/sharepoint-organization-external-sharing-controls.png)


SharePoint 조직 수준 공유 설정을 설정 하려면

1. Microsoft 365 관리 센터의 왼쪽 탐색에 있는 **관리 센터**에서 **SharePoint**를 클릭 합니다.
2. 왼쪽 탐색 창의 SharePoint 관리 센터에서 **공유**를 클릭합니다.
3. SharePoint 용 외부 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.
4. 변경한 내용이 있으면 **저장**을 클릭합니다.

## <a name="create-a-site"></a>사이트 만들기

다음 단계는 게스트와 공동 작업 하는 데 사용할 사이트를 만드는 것입니다.

사이트를 만들려면
1. SharePoint 관리 센터의 **사이트**아래에서 **활성 사이트**를 클릭 합니다.
2. **만들기**를 클릭합니다.
3. **팀 사이트**를 클릭 합니다.
4. 사이트 이름을 입력 하 고 그룹 소유자 (사이트 소유자)의 이름을 입력 합니다.
5. **고급 설정**에서이 사이트를 공용 또는 개인 사이트로 설정할 것인지 여부를 선택 합니다.
6. **다음**을 클릭합니다.
7. **마침**을 클릭합니다.

나중에 사용자를 초대 합니다. 다음으로이 사이트에 대 한 사이트 수준 공유 설정을 확인 하는 것이 중요 합니다.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 사이트 수준 공유 설정

사이트 수준 공유 설정을 확인 하 여 해당 사이트에 대해 원하는 액세스 유형을 허용 하는지 확인 합니다. 예를 들어 조직 수준 설정을 모든 **사용자**로 설정 했지만 모든 게스트가이 사이트에 대해 인증을 받으려는 경우에는 사이트 수준 공유 설정이 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.

사이트를 인증 되지 않은 사용자 (**사용자** 설정)와 공유할 수는 없지만 개별 파일 및 폴더를 사용할 수 있습니다.

![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings.png)

사이트 수준 공유 설정을 설정 하려면
1. SharePoint 관리 센터의 왼쪽 탐색 창에서 **사이트**를 확장시키고 **Active 사이트**를 클릭합니다.
2. 방금 만든 사이트를 선택 합니다.
3. 리본 메뉴에서 **공유**를 클릭합니다.
4. 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.
5. 변경한 내용이 있으면 **저장**을 클릭합니다.

## <a name="invite-users"></a>사용자 초대

게스트 공유 설정이 이제 구성 되므로 사이트에 내부 사용자 및 게스트를 추가할 수 있습니다. 사이트 액세스는 연결 된 Office 365 그룹을 통해 제어 되므로 사용자를 추가할 수 있습니다.

그룹에 내부 사용자를 초대 하려면
1. 사용자를 추가 하려는 사이트로 이동 합니다.
2. 오른쪽 위에 있는 **구성원** 을 클릭 합니다.
3. **구성원 추가**를 클릭합니다.
4. 사이트에 초대할 사용자의 이름 또는 전자 메일 주소를 입력 하 고 **저장**을 클릭 합니다.

게스트 사용자는 사이트에서 추가할 수 없습니다. 웹에서 Outlook을 사용 하 여 추가 해야 합니다.

그룹에 게스트를 초대 하려면
1. 웹용 Outlook의 **그룹**에서 구성원을 추가 하려는 그룹을 클릭 합니다.
2. 그룹 대화 상대 카드를 열고 **기타 옵션** (...)에서 **구성원 추가**를 클릭 합니다.
3. 초대 하려는 게스트의 전자 메일 주소를 입력 한 다음 **추가**를 클릭 합니다.
4. **닫기**를 클릭합니다.

## <a name="see-also"></a>참고 항목

[인증되지 않은 사용자와 파일 및 폴더를 공유하는 모범 사례](best-practices-anonymous-sharing.md)

[게스트와 공유할 때 파일에 실수로 발생하는 노출을 제한](sharing-limit-accidental-exposure.md)

[보안 게스트 공유 환경 만들기](create-a-secure-guest-sharing-environment.md)

[관리 되는 게스트를 사용 하 여 B2B 엑스트라넷 만들기](b2b-extranet.md)

