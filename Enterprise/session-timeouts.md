---
title: Office 365에 대 한 세션 제한 시간
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
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
description: 세션 제한 시간 securtiy로 Office 365 클라이언트 응용 프로그램에 대 한 액세스를 간편 하 게 균형을 조정 하는 데 사용 됩니다.
ms.openlocfilehash: 4ef50b876fd97e2de2449d324464b466243a6691
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378494"
---
# <a name="session-timeouts-for-office-365"></a>Office 365에 대 한 세션 제한 시간

세션 수명을 Office 365에 대 한 인증의 중요 한 부분 하며 보안 및 자격 증명에 대 한 사용자에 게 메시지 횟수 균형 조정에 중요 한 요소입니다.
  
## <a name="session-times-for-office-365-services"></a>Office 365 서비스에 대 한 세션 시간

Office 365 웹 앱 또는 모바일 응용 프로그램 중 하나에서 사용자를 인증 하는 경우에 세션 설정 됩니다. 세션 기간 동안 사용자가 다시 인증할 필요가 없습니다. 세션에는 탭을 확인 하는 브라우저를 닫을 때 또는 자신의 암호 다시 설정 된 경우 등의 다른 이유로 해당 인증 토큰 만료 될 때 사용자가 활성 상태인 없으면 만료 될 수 있습니다. Office 365 서비스는 서로 다른 세션 시간 초과 된 각 서비스의 일반적인를 사용 하 여 해당 합니다.
  
다음 표에 Office 365 서비스에 대 한 세션 수명:
  
|**Office 365 서비스**|**세션 제한 시간**|
|:-----|:-----|
|Office 365 관리 센터  <br/> |8 시간 마다 관리 센터에 대 한 자격 증명을 제공 하 라는 메시지가 표시 됩니다.  <br/> |
|SharePoint Online  <br/> |5 일 분의 비활성 사용자 까지도 **로그인 유지**자동을 선택합니다. 사용자 액세스 하는 경우 SharePoint Online 다시 후 이전 로그인에서 24 또는 그 이상의 시간 경과, 시간 제한 값을 5 일로 다시 설정 됩니다.<br/> |
|Outlook Web App  <br/> |6 시간입니다.  <br/> [Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet에서 _ActivityBasedAuthenticationTimeoutInterval_ 매개 변수를 사용 하 여이 값을 변경할 수 있습니다.  <br/> |
|Azure Active Directory  <br/> (사용 하도록 설정 하는 현대 인증을 통해 Office 2013 Windows 클라이언트에 사용 됨)  <br/> | 현대 인증 Azure Active Directory를 사용 하 여 Office 365 리소스에 대 한 사용자 액세스 권한을 부여 하려면 액세스 토큰에 refresh 토큰을 사용 합니다. 액세스 토큰 JSON 웹 토큰 인증에 성공한 후 제공 이며 1 시간 동안 유효 합니다. 긴 수명 새로고침 토큰도 제공 됩니다. 액세스 토큰에 만료 되는 경우 Office 클라이언트 유효한 새로고침 토큰을 사용 하 여 새 액세스 토큰을 얻는. 이 exchange 사용자의 초기 인증 유효 하도록 하는 경우 성공 합니다.  <br/>  90 일 동안 새로고침 토큰에 유효 있으며 연속 사용과 있을 수 있습니다 해지 될 때까지 유효 합니다.  <br/>  새로고침 토큰에 여러 이벤트에 의해 같은 무효화 될 수 있습니다.  <br/>  새로고침 토큰 발급 이후 사용자의 암호가 변경 되었습니다.  <br/>  관리자가 사용자가 액세스 하려는 리소스에 대 한 액세스를 제한 하는 조건부 액세스 정책을 적용할 수 있습니다.  <br/> |
|Android, iOS, 및 Windows 10에 대 한 모바일 앱을 SharePoint와 OneDrive  <br/> |액세스 토큰에 대 한 기본 수명은 1 시간입니다. 새로고침 토큰의 기본 최대 비활성 시간 90 일입니다.<br/> [토큰 및 토큰 수명은 구성 하는 방법에 대 한 자세한 내용은](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 새로 해지 하려면 토큰을 다시 설정할 수 있습니다는 사용자의 Office 365 암호  <br/> |
|Office 365 로그인와 yammer  <br/> |브라우저의 수명입니다. 사용자가 브라우저를 닫고 하 새 브라우저에서 Yammer에 액세스 하는 경우 Yammer를 다시 인증 하 Office 365를 사용 합니다. 사용자는 타사 브라우저를 캐시 쿠키를 사용 하는 경우 다시 브라우저를 다시 때 인증을 수행 하려면 필요 하지 않을 수 있습니다.<br/> > [!NOTE]>이 Office 365 로그인을 사용 하 여 Yammer에 대 한 네트워크에 대해서만 유효 합니다.           |
   

