---
title: Microsoft 365에서 디렉터리 동기화 오류 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Microsoft 365 관리 센터에서 디렉터리 동기화 오류 및 가능한 수정 사항을 확인 하는 방법을 알아봅니다.
ms.openlocfilehash: 344cc71d192e6a73826c66c8bcbf8569d10e45d8
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605710"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Microsoft 365에서 디렉터리 동기화 오류 보기

Microsoft 365 관리 센터에서 디렉터리 동기화 오류를 볼 수 있습니다. 사용자 개체 오류만 표시 됩니다. PowerShell을 사용 하 여 오류를 보려면 [DirSyncProvisioningErrors를 사용 하 여 개체 확인](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)을 참조 하십시오.

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Microsoft 365 관리 센터에서 디렉터리 동기화 오류 보기

Microsoft 365 관리 센터에서 오류를 확인 하려면 다음을 수행 합니다.
  
1. 전역 관리자 계정으로 [Microsoft 365 관리 센터](https://admin.microsoft.com) 에 로그인 합니다. 
    
2. **홈** 페이지에서 **사용자 관리** 카드를 볼 수 있습니다. 
    
    ![Microsoft 365 관리 센터의 사용자 관리 카드](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. 카드에서 **AZURE AD Connect** 아래에 있는 **동기화 오류** 를 선택 하 여 **디렉터리 동기화 오류** 페이지에서 오류를 확인 합니다.   
    
    ![디렉터리 동기화 오류 페이지의 예](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. 오류에 대 한 정보 및 문제 해결 방법에 대 한 팁이 포함 된 세부 정보 창을 표시 하려면 오류를 선택 합니다.

   ![디렉터리 동기화 오류 세부 정보의 예](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
확인 후에는 [Microsoft 365에 대 한 디렉터리 동기화 문제 해결](fix-problems-with-directory-synchronization.md) 을 참조 하 여 식별 된 모든 문제를 해결 합니다.

