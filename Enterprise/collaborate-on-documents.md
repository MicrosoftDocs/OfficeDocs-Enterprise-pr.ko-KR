---
title: 게스트와 문서에서 공동 작업하기
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Normal
description: SharePoint 및 OneDrive에서 문서에 대 한 게스트와 공동 작업 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 20b97ed6e232385500e74adcaa11378252167c26
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886497"
---
# <a name="collaborate-with-guests-on-a-document"></a>게스트와 문서에서 공동 작업하기

SharePoint 또는 OneDrive에서 문서에 대 한 게스트와 공동 작업을 수행 해야 하는 경우 문서에 대 한 공유 링크를 보낼 수 있습니다. 이 문서에서는 조직의 필요에 따라 SharePoint 및 OneDrive에 대 한 공유 링크를 설정 하는 데 필요한 Microsoft 365 구성 단계를 안내 합니다.

## <a name="video-demonstration"></a>비디오 데모

이 비디오에서는이 문서에서 설명 하는 구성 단계를 보여 줍니다.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

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
6. 변경한 경우 **저장**을 클릭 합니다.

**공동 작업 제한** 섹션의 설정을 확인 합니다. 공동 작업 하려는 게스트의 도메인이 차단 되지 않았는지 확인 합니다.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 조직 수준 공유 설정

게스트가 SharePoint 또는 OneDrive의 문서에 액세스할 수 있도록 하려면 SharePoint 및 OneDrive 조직 수준 공유 설정에서 게스트와 공유 하는 것을 허용 해야 합니다.

SharePoint의 조직 수준 설정에 따라 개별 SharePoint 사이트에서 사용할 수 있는 설정이 결정 됩니다. 사이트 설정은 조직 수준 설정 보다는 더 이상 허용 되지 않습니다. OneDrive에 대 한 조직 수준 설정에 따라 사용자의 OneDrive 라이브러리에서 사용할 수 있는 공유 수준이 결정 됩니다.

SharePoint 및 OneDrive의 경우 인증 되지 않은 파일 및 폴더 공유를 허용 하려면 **모든 사용자**를 선택 합니다. 모든 게스트가 인증을 받도록 하려면 **신규 및 기존 게스트**를 선택 합니다. *모든사용자* 링크는 가장 간편하게 공유하는 방법입니다. 게스트가 인증 없이 링크를 열 수 있으며 다른 사용자에게 무료로 전달할 수 있습니다.

SharePoint의 경우 조직의 모든 사이트에서 필요한 가장 관대 한 설정을 선택 합니다.

![SharePoint 조직 수준 공유 설정의 스크린샷](media/sharepoint-organization-external-sharing-controls.png)


SharePoint 조직 수준 공유 설정을 설정 하려면

1. Microsoft 365 관리 센터의 왼쪽 탐색에 있는 **관리 센터**에서 **SharePoint**를 클릭 합니다.
2. 왼쪽 탐색 창의 SharePoint 관리 센터에서 **공유**를 클릭합니다.
3. SharePoint 또는 OneDrive에 대 한 외부 공유가 **모든 사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다. OneDrive 설정은 SharePoint 설정 보다 더 허용 되지 않습니다.
4. 변경한 경우 **저장**을 클릭 합니다.

## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint 조직 수준 기본 링크 설정

기본 파일 및 폴더 링크 설정에 따라 파일 또는 폴더를 공유할 때 기본적으로 사용자에 게 표시 되는 링크 옵션이 결정 됩니다. 원하는 경우 공유 하기 전에 다른 옵션 중 하나로 연결 유형을 변경할 수 있습니다.

이 설정은 OneDrive 뿐 아니라 조직의 SharePoint 사이트에도 영향을 미칩니다.

사용자가 파일 및 폴더를 공유할 때 기본적으로 선택 되는 링크 유형을 선택 합니다.

- **링크를 포함 하는 모든 사용자** 인증 되지 않은 파일 및 폴더 공유를 많이 수행 하려는 경우이 옵션을 선택 합니다. *모든* 링크를 허용 하지만 실수로 인증 되지 않은 공유가 발생 하는 것이 염려 되는 경우에는 다른 옵션 중 하나를 기본값으로 사용 하는 것이 좋습니다. 이 링크 형식은 **모든 사용자** 가 공유 하도록 설정한 경우에만 사용할 수 있습니다.
- **조직의 사용자만** 조직 내부 사용자와 파일 및 폴더 공유를 사용할 것으로 예상 되는 경우이 옵션을 선택 합니다.
- **특정 사용자** -게스트와 파일 및 폴더 공유를 많이 수행 해야 하는 경우이 옵션을 고려 하세요. 이 유형의 링크는 게스트에서 작동 하며 인증을 요구 합니다.
 
![SharePoint 조직 수준 파일 및 폴더 공유 설정 스크린샷](media/sharepoint-organization-files-folders-sharing-settings.png)


SharePoint 및 OneDrive 조직 수준 기본 링크 설정을 설정 하려면

1. SharePoint 관리 센터에서 공유 페이지로 이동 합니다.
2. **파일 및 폴더 링크**에서 사용 하려는 기본 공유 링크를 선택 합니다.
3. 변경한 경우 **저장**을 클릭 합니다.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 사이트 수준 공유 설정

SharePoint 사이트에 있는 파일 및 fodlers를 공유 하는 경우에는 해당 사이트에 대 한 사이트 수준 공유 설정도 확인 해야 합니다.

![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings.png)

사이트 수준 공유 설정을 설정 하려면
1. SharePoint 관리 센터의 왼쪽 탐색 창에서 **사이트** 를 확장 하 고 **활성 사이트**를 클릭 합니다.
2. 방금 만든 사이트를 선택 합니다.
3. 리본 메뉴에서 **공유**를 클릭 합니다.
4. 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.
5. 변경한 경우 **저장**을 클릭 합니다.

## <a name="invite-users"></a>사용자 초대

이제 게스트 공유 설정이 구성 되므로 사용자가 guest를 사용 하 여 파일 및 폴더를 공유할 수 있습니다. 자세한 내용은 [OneDrive 파일 및 폴더](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) 공유 및 [SharePoint 파일 또는 폴더 공유](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[인증 되지 않은 사용자와 파일 및 폴더를 공유 하기 위한 최상의 방법](best-practices-anonymous-sharing.md)

[게스트와 공유할 때 파일에 실수로 발생하는 노출을 제한](sharing-limit-accidental-exposure.md)