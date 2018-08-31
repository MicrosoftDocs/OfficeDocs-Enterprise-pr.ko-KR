---
title: Office 365에서 디렉터리 동기화 상태 보기
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 디렉터리 동기화를 비활성화 하는 방법에 알아봅니다. 또한 해당 상태를 볼 수 있습니다.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542217"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Office 365에서 디렉터리 동기화 상태 보기
온-프레미스 환경의 Office 365와 동기화 하 여 Azure AD와 온-프레미스 Active Directory 통합 했는지를 하는 경우에 사용자 동기화의 상태를 확인할 수 있습니다.
  
## <a name="view-directory-synchronization-status"></a>디렉터리 동기화 상태 보기
- Office 365 관리 센터에 로그인 하 고 홈 페이지에서 **디렉터리 동기화 상태** 를 선택 합니다. 
- 또는 **사용자** 에 게 이동할 수 있습니다 \> **현재 사용자가** **현재 사용자** 페이지에서 **더 많은** 선택 하 고 \> **디렉터리 동기화**합니다. **디렉터리 동기화** 창에서 **디렉터리 동기화 관리로 이동**을 선택 합니다.
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>디렉터리 동기화 관리 페이지에 대 한 정보

다음 표에서 페이지에 대 한 정보를 얻을 수 기능을 보여줍니다.
  
디렉터리 동기화에 문제가 있으면이 페이지는 오류가 나열 됩니다. 다른 오류가 발생할 수 있는 방법에 대 한 자세한 내용은 [Office 365에서 디렉터리 동기화 오류 식별을](identify-directory-synchronization-errors.md)참조 하십시오.
  
|**항목**|**이 대 한**|
|:-----|:-----|
|**도메인 확인** | 도메인 확인 한 경우 Office 365 테 넌 트의 수를 소유 합니다. |
|**확인 되지 않은 도메인** | 도메인에 추가 되었지만 확인할 수 없습니다. |
|**디렉터리 동기화를 사용 하도록 설정** |True 또는 false로 설정 합니다. 디렉터리 동기화를 사용할 수 있는지 여부를 지정 합니다. |
|**최신 디렉터리 동기화** | 디렉터리 동기화를 실행 하는 마지막 시간입니다. 표시 됩니다 경고 및 링크는 문제해결 도구 마지막 동기화 된 3 일이 경과 하는 경우. |
|**암호 동기화를 사용 하도록 설정** | True 또는 false로 설정 합니다. 사용해 온-프레미스 및 Office 365 테 넌 트 간에 암호 해시 동기화 해야 하는지 여부를 지정 합니다. |
|**마지막 암호 동기화** | 마지막으로 암호 해시 동기화를 실행 합니다. 표시 됩니다 경고 및 링크는 문제해결 도구 마지막 동기화 된 3 일이 경과 하는 경우. |
|**디렉터리 동기화 클라이언트 버전** | Azure AD 연결의 새 버전을 해제 된 경우에 다운로드 링크를 포함 합니다. |
|**IDFix 도구** | [IDFix](install-and-run-idfix.md), 로컬 Active Directory를 확인 하는 데 사용할 수 있는 도구에 링크를 다운로드 합니다. |
|**디렉터리 동기화 서비스 계정** | Office 365 디렉터리 동기화 서비스 계정 하의 이름을 표시합니다. |