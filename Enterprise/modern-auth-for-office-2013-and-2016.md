---
title: Office 2013 및 Office 2016 클라이언트 앱에 대해 최신 인증이 작동하는 방법
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Microsoft 365 최신 인증이 Office 2013 및 2016 클라이언트 앱에 대해 다르게 작동 하는 방식을 알아봅니다.
ms.openlocfilehash: 469dd665a3f427db3e2ae3731945e53b900f05e9
ms.sourcegitcommit: 92bbb6d005d005952a9e2055661fcdccfdd0567b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "46533493"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>최신 인증이 Office 2013, Office 2016 및 Office 2019 클라이언트 앱에 작동 하는 방식

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

이 문서를 읽으면 Office 2013, Office 2016 및 Office 2019 클라이언트 앱이 Exchange Online, SharePoint Online 및 비즈니스용 Skype Online에 대 한 Microsoft 365 테 넌 트의 인증 구성에 따라 최신 인증 기능을 사용 하는 방법을 알아봅니다.

> [!NOTE]
> Office 2010 및 Office for Mac 2011와 같은 레거시 클라이언트 앱은 최신 인증을 지원 하지 않으며 기본 인증만 사용할 수 있습니다.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Microsoft 365 서비스에 대 한 최신 인증 가용성

Microsoft 365 서비스의 경우 최신 인증의 기본 상태는 다음과 같습니다.
  
- 기본적으로 Exchange **Online에 대해 설정 됩니다** . 기능을 설정 하거나 해제 하려면 [최신 인증 사용 또는 사용 안 함을](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) 참조 하세요. 
    
- 기본적으로 SharePoint **Online에 대해 설정 됩니다** . 
    
- 비즈니스용 Skype **Online에 기본적으로 설정 됩니다** . [최신 인증을 사용 ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)하지 않도록 설정 하려면 비즈니스용 Skype 온라인을 활성화 합니다 .를 참조 하세요.

> [!NOTE]
> 2017년 8월 1일 **이전**에 만든 테넌트의 경우 최신 인증은 Exchange Online 및 비즈니스용 Skype Online에 대해 기본적으로 설정이 **해제**되어 있습니다.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office 클라이언트 앱의 로그인 동작

Office 2013 클라이언트 앱은 기본적으로 레거시 인증을 지원 합니다. 레거시는 Microsoft 온라인 로그인 도우미 또는 기본 인증 중 하나를 지원 한다는 것을 의미 합니다. 이러한 클라이언트가 최신 인증 기능을 사용 하도록 하려면 Windows 클라이언트에 레지스트리 키가 설정 되어 있어야 합니다. 자세한 내용은 [Windows 장치에서 Office 2013에 대 한 최신 인증 사용](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)을 참조 하세요.

Microsoft Office 2013이 설치되었고 Windows를 실행 중인 장치(예: 노트북 및 태블릿)에 대해 최신 인증을 사용하려면 다음 레지스트리 키를 설정해야 합니다. 최신 인증을 사용할 각 장치에서 키를 설정해야 합니다.
  
|**레지스트리 키**|**유형**|**값** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |
  
비즈니스용 [skype와 함께 ADAL (최신 인증)을 사용](https://go.microsoft.com/fwlink/p/?LinkId=785431) 하 여 비즈니스용 skype에서 작동 하는 방식에 대해 알아봅니다. 
  
Office 2016 및 Office 2019 클라이언트는 기본적으로 최신 인증을 지원 하며, 이러한 새 흐름을 사용 하기 위해 클라이언트에 필요한 작업이 없습니다. 그러나 레거시 인증을 사용 하려면 명시적 작업을 수행 해야 합니다.
  
아래 링크를 클릭 하 여 Office 2013, Office 2016 및 Office 2019 클라이언트 인증이 최신 인증이 설정 되어 있는지 여부에 따라 Microsoft 365 services에서 작동 하는 방식을 확인 합니다.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [비즈니스용 Skype Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

다음 표에서는 최신 인증을 사용 하지 않고 Exchange Online에 연결할 때 Office 2013, Office 2016 및 Office 2019 클라이언트 앱의 인증 동작에 대해 설명 합니다.
  
|Office 클라이언트 응용 프로그램 버전 * * * *|레지스트리 키 유무 (? * * * *)|최신 인증은? * * * *|테 넌 트에 대 한 최신 인증이 설정 된 인증 동작 (기본값) * * * *|테 넌 트에 대 한 최신 인증을 끈 인증 동작 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |아니요 <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |예  <br/> |Outlook 2013, 2016 또는 2019에 최신 인증을 적용 합니다. <br/> [추가 정보](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Outlook 클라이언트 내에서 최신 인증을 적용 합니다.<br/> |
|Office 2019  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2019  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2019  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |기본 인증  <br/> |기본 인증  <br/> |
|Office 2016  <br/> |아니요 <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |예  <br/> |2013, 2016 또는 2019에 최신 인증을 적용 합니다. <br/> [추가 정보](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Outlook 클라이언트 내에서 최신 인증을 적용 합니다.<br/> |
|Office 2016  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |기본 인증  <br/> |기본 인증  <br/> |
|Office 2013  <br/> |아니요  <br/> |아니요  <br/> |기본 인증  <br/> |기본 인증  <br/> |
|Office 2013  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버가 최신 인증 연결을 거부 하면 기본 인증이 사용 됩니다. 테 넌 트가 사용 하도록 설정 되지 않은 경우 서버는 최신 인증을 거부 합니다.  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

다음 표에는 최신 인증을 사용 하 여 SharePoint Online에 연결 하는 경우 Office 2013, Office 2016 및 Office 2019 클라이언트 앱의 인증 동작이 나와 있습니다.
  
|Office 클라이언트 응용 프로그램 버전 * * * *|레지스트리 키 유무 (? * * * *)|최신 인증은? * * * *|테 넌 트에 대 한 최신 인증이 설정 된 인증 동작 (기본값) * * * *|테 넌 트에 대 한 최신 인증을 끈 인증 동작 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |최신 인증만  <br/> |연결 하지 못했습니다.  <br/> |
|Office 2019  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |최신 인증만  <br/> |연결 하지 못했습니다.  <br/> |
|Office 2019  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |
|Office 2016  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |최신 인증만  <br/> |연결 하지 못했습니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |최신 인증만  <br/> |연결 하지 못했습니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |
|Office 2013  <br/> |아니요  <br/> |아니요  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |
|Office 2013  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |최신 인증만  <br/> |연결 하지 못했습니다.  <br/> |
   
### <a name="skype-for-business-online"></a>비즈니스용 Skype Online
<a name="BK_SFBO"> </a>

다음 표에서는 최신 인증을 사용 하지 않고 온라인으로 비즈니스용 Skype Online에 연결할 때 Office 2013, Office 2016 및 Office 2019 클라이언트 앱의 인증 동작에 대해 설명 합니다.
  
|Office 클라이언트 응용 프로그램 버전 * * * *|레지스트리 키 유무 (? * * * *)|최신 인증은? * * * *|테 넌 트에 대 한 최신 인증이 설정 된 인증 동작 * * * *|테 넌 트에 대해 최신 인증을 끈 인증 동작 (기본값) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2019  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2019  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |
|Office 2016  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |
|Office 2013  <br/> |아니요  <br/> |아니요  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |
|Office 2013  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |가장 먼저 인증을 시도 합니다. 서버에서 최신 인증 연결을 거부 하는 경우 Microsoft Online 로그인 도우미가 사용 됩니다. 비즈니스용 Skype Online 테 넌 트를 사용할 수 없는 경우 서버는 최신 인증을 거부 합니다.  <br/> |Microsoft Online 로그인 도우미 전용입니다.  <br/> |
   
## <a name="see-also"></a>참고 항목

[Windows 장치에서 Office 2013를 사용하기 위한 최신 인증의 사용](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication)

[Microsoft 365에 대한 다단계 인증 사용](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365)

[다단계 인증을 사용 하 여 Microsoft 365에 로그인](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
