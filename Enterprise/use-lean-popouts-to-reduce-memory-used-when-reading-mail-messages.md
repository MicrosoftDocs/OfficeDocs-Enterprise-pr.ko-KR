---
title: 간결한 팝업을 사용 하 여 메일 메시지를 읽을 때 사용 되는 메모리 줄이기
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: 이 문서에서는 웹용 Outlook에서 메시지 다운로드 성능을 개선 하기 위한 정보를 포함 합니다.
ms.openlocfilehash: a9070d9aefc8e4c223667848b4af5c06518de076
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616811"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>간결한 팝업을 사용 하 여 메일 메시지를 읽을 때 사용 되는 메모리 줄이기

이 문서에서는 웹용 Outlook에서 메시지 다운로드 성능을 개선 하기 위한 정보를 포함 합니다. 이 문서는 [Office 365 프로젝트에 대 한 네트워크 계획 및 성능 조정](https://aka.ms/tune) 의 일부입니다.
   
Office 365 전역 관리자는 Microsoft Edge 또는 Internet Explorer에서 비교적 작고 메모리를 많이 사용 하는 특정 전자 메일 메시지에 대 한 *간결한 팝업* 를 제공 하도록 웹에서 Outlook을 구성할 수 있습니다. 웹에서 Outlook에 대해 간결한 팝업를 구성 하면 성능을 최적화 하는 서버 쪽 렌더링 된 구성 요소가 로드 됩니다. 
  
> [!NOTE]
> 2018 년 3 월에 해당 하 여 팝업은 현재 IRM (정보 권한 관리)과 같은 사용 권한 제한을 지정 하는 메시지에는 사용할 수 없습니다. 
  
이러한 기능은 주 창에서 계속 작동 하지만 간결한 팝업에서는 사용할 수 없습니다.
  
- Outlook 추가 기능
    
- 비즈니스용 Skype 현재 상태
    
 **Office 365 조직 내의 모든 사용자에 대해 간결한 팝업를 구성 하려면**
  
1. [원격 PowerShell을 사용 하 여 Exchange Online에 연결](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )합니다.
    
2. 다음과 같이 LeanPopoutEnabled 매개 변수를 사용 하 여 [set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet을 실행 합니다. 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  예를 들어 조직의 모든 사용자에 대해 간결한 팝업을 사용 하도록 설정 하려면 다음을 수행 합니다.
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  조직의 모든 사용자에 대해 간결한 팝업을 사용 하지 않도록 설정 하려면
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


