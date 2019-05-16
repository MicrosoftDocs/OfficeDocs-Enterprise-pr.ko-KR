---
title: Office 365에 대 한 세션 제한 시간
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: 세션 시간 제한은 Office 365 클라이언트 앱에서 securtiy 및 접근성의 균형을 조정 하는 데 사용 됩니다.
ms.openlocfilehash: d43bc123de982f3ebf55f05f48e53debe7df036b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070854"
---
# <a name="session-timeouts-for-office-365"></a>Office 365에 대 한 세션 제한 시간

세션 수명은 Office 365 인증의 중요 한 부분이 며, 균형 조정 보안의 중요 한 구성 요소 이며 사용자에 게 자격 증명을 입력 하 라는 메시지가 표시 되는 횟수입니다.
  
## <a name="session-times-for-office-365-services"></a>Office 365 서비스의 세션 시간

사용자가 Office 365 웹 앱 또는 모바일 앱에서 인증 하는 경우 세션이 설정 됩니다. 세션을 진행 하는 동안에는 사용자가 다시 인증할 필요가 없습니다. 세션은 사용자가 비활성 상태일 때, 브라우저나 탭을 닫을 때, 또는 암호를 다시 설정 했을 때와 같은 다른 이유로 인해 인증 토큰이 만료 될 때 만료 될 수 있습니다. Office 365 서비스의 세션 시간 제한은 각 서비스의 일반적인 사용과 일치 합니다.
  
다음 표에는 Office 365 서비스의 세션 수명 목록이 나와 있습니다.
  
|**Office 365 서비스**|**세션 제한 시간**|
|:-----|:-----|
|Office 365 관리 센터  <br/> |관리자 센터에 대 한 자격 증명을 8 시간 마다 제공 하 라는 메시지가 표시 됩니다.  <br/> |
|SharePoint Online  <br/> |사용자가 **로그인 유지**를 선택 하기만 하면 5 일 동안 비활성 상태가 됩니다. 사용자가 24 시간 이상이 이전 로그인에서 전달 된 후에 SharePoint Online에 다시 액세스 하는 경우 시간 제한 값은 5 일로 다시 설정 됩니다.  <br/> |
|Outlook Web App  <br/> |6 시간  <br/> [Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) Cmdlet에서 _ActivityBasedAuthenticationTimeoutInterval_ 매개 변수를 사용 하 여이 값을 변경할 수 있습니다.  <br/> |
|Azure Active Directory  <br/> (최신 인증을 사용 하는 Office 2013 Windows 클라이언트에서 사용)  <br/> | 최신 인증은 액세스 토큰 및 새로 고침 토큰을 사용 하 여 Azure Active Directory를 사용 하는 Office 365 리소스에 대 한 사용자 액세스 권한을 부여 합니다. 액세스 토큰은 인증을 완료 한 후 제공 되는 JSON 웹 토큰이 며 1 시간 동안 유효 합니다. 수명이 긴 새로 고침 토큰도 제공 됩니다. 액세스 토큰이 만료 되 면 Office 클라이언트는 유효한 새로 고침 토큰을 사용 하 여 새 액세스 토큰을 가져옵니다. 사용자의 초기 인증이 여전히 유효한 경우이 exchange가 성공 합니다.  <br/>  새로 고침 토큰은 90 일 동안 유효 하며 지속적인 사용을 위해서는 해지할 때까지 유효 합니다.  <br/>  새로 고침 토큰은 다음과 같은 여러 가지 이벤트로 무효화 될 수 있습니다.  <br/>  새로 고침 토큰이 발급 된 이후 사용자의 암호가 변경 되었습니다.  <br/>  관리자는 사용자가 액세스 하려고 하는 리소스에 대 한 액세스를 제한 하는 조건부 액세스 정책을 적용할 수 있습니다.  <br/> |
|Android, iOS 및 Windows 10 용 SharePoint 및 OneDrive 모바일 앱  <br/> |액세스 토큰의 기본 수명은 1 시간입니다. 새로 고침 토큰의 기본 최대 비활성 시간은 90 일입니다.  <br/> [토큰 및 토큰 수명 구성 방법에 대 한 자세한 정보](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 새로 고침 토큰을 해지 하려면 사용자의 Office 365 암호를 다시 설정할 수 있습니다.  <br/> |
|Office 365 로그인이 포함 된 Yammer  <br/> |브라우저의 수명입니다. 사용자가 브라우저를 닫고 새 브라우저에서 Yammer에 액세스 하는 경우 Yammer는 Office 365를 사용 하 여이를 다시 인증 합니다. 사용자가 쿠키를 캐시 하는 타사 브라우저를 사용 하는 경우 브라우저를 다시 열 때 다시 인증 하지 않아도 될 수 있습니다.  <br/> > [!NOTE]> Yammer에 대 한 Office 365 로그인을 사용 하는 네트워크에만 유효 합니다.           |
   

