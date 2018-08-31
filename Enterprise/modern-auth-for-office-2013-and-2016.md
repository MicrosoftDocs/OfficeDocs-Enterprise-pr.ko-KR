---
title: 최신 인증이 Office 2013 및 Office 2016 클라이언트 앱에 작동하는 방식
ms.author: sirkkuw
author: Sirkkuw
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
description: Office 365 현대 인증 다르게 Office 2013 및 2016 클라이언트 응용 프로그램에 대 한 작동 방식에 대해 알아봅니다.
ms.openlocfilehash: a9b6e2dabec9fb59f5fd7f60508dcbc6fe840cfb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542074"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>최신 인증이 Office 2013 및 Office 2016 클라이언트 앱에 작동하는 방식

온라인 비즈니스에 대 한 Exchange Online, SharePoint Online 및 Skype Office 365 테 넌 트에는 인증 구성에 따라 Office 2013 및 Office 2016 클라이언트 앱 현대 인증 기능을 사용할 방법을 알아보려면이 문서를 읽어보십시오.
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>Office 365 서비스에 대 한 최신 인증의 사용 가능 여부

Office 365 서비스에 대 한 최신 인증의 기본 상태는:
  
- **기본적으로 Exchange Online에 대 한 켜져 있습니다.** [사용 하거나 사용 하지 않도록 현대 인증 Exchange 온라인](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) 설정 또는 해제를 참조 하십시오. 
    
- SharePoint online **에서** 기본적으로 설정 합니다. 
    
- **Skype에 대 한 온라인 비즈니스에 대 한 기본적으로 켜져 있습니다.** [현대 인증에 대 한 온라인 비즈니스에 대 한 Skype 사용 ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)설정 또는 해제를 참조 하십시오.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office 클라이언트 응용 프로그램의 로그인 동작

Office 2013 클라이언트 앱 기본적으로 레거시 인증을 지원 합니다. 레거시 하거나 Microsoft Online 로그인 도우미 또는 기본 인증을 지원 자신이 것을 의미 합니다. 현대 인증 기능을 사용 하 여 이러한 클라이언트에 대 한 순서, 클라이언트의 Windows 설정 하는 레지스트리 키를 가집니다. 자세한 내용은 [Windows 장치에서 Office 2013에 대 한 최신 인증 사용](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)을 참조 하십시오.
  
비즈니스를 위한 Skype와 작동 방식에 대해 자세히 알아보려면 [현대 인증 (ADAL) 비즈니스를 위한 Skype 함께 사용 하는 방법](https://go.microsoft.com/fwlink/p/?LinkId=785431) 을 읽어봅니다. 
  
Office 2016 클라이언트는 기본적으로 현대 인증을 지원 하 고 아무 작업도 이러한 새 흐름을 사용 하 여 클라이언트에 필요한 키를 누릅니다. 그러나 레거시 인증을 사용 하 여 명시적 작업이 필요 합니다.
  
Office 2013 및 Office 2016 클라이언트 인증 현대 인증 켜져 여부에 따라 Office 365 서비스와 함께 작동 하는 방법을 보려면 다음 링크를 클릭 합니다.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [비즈니스용 Skype Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

다음 표에서 함께 또는 따로 현대 인증 Exchange Online에 연결할 때 Office 2013 또는 Office 2016 클라이언트 응용 프로그램에 대 한 인증 동작을 설명 합니다.
  
|Office 클라이언트 응용 프로그램 버전 * * *|이 매개 변수가 레지스트리 키? * * *|에 대 한 최신 인증? * * *|테 넌 트 (기본값)에 대 한 최신 인증 및 인증 동작 설정 * * *|테 넌 트 *에 대 한 최신 인증 및 인증 동작 해제|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버를 기본 인증이 사용 됩니다. 서버에서 테 넌 트 활성화 되지 않은 경우 현대 인증을 거부 합니다.  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버를 기본 인증이 사용 됩니다. 서버에서 테 넌 트 활성화 되지 않은 경우 현대 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버를 기본 인증이 사용 됩니다. 서버에서 테 넌 트 활성화 되지 않은 경우 현대 인증을 거부 합니다.  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버를 기본 인증이 사용 됩니다. 서버에서 테 넌 트 활성화 되지 않은 경우 현대 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |기본 인증  <br/> |기본 인증  <br/> |
|Office 2013  <br/> |아니요  <br/> |아니요  <br/> |기본 인증  <br/> |기본 인증  <br/> |
|Office 2013  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버를 기본 인증이 사용 됩니다. 서버에서 테 넌 트 활성화 되지 않은 경우 현대 인증을 거부 합니다.  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버를 기본 인증이 사용 됩니다. 서버에서 테 넌 트 활성화 되지 않은 경우 현대 인증을 거부 합니다.  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

다음 표에서 또는 현대 인증 되지 않은 SharePoint Online에 연결할 때 Office 2013 또는 Office 2016 클라이언트 응용 프로그램에 대 한 인증 동작을 설명 합니다.
  
|Office 클라이언트 응용 프로그램 버전 * * *|이 매개 변수가 레지스트리 키? * * *|에 대 한 최신 인증? * * *|테 넌 트 (기본값)에 대 한 최신 인증 및 인증 동작 설정 * * *|테 넌 트 *에 대 한 최신 인증 및 인증 동작 해제|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |현대 인증에만 해당 합니다.  <br/> |연결에 실패 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |현대 인증에만 해당 합니다.  <br/> |연결에 실패 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |
|Office 2013  <br/> |아니요  <br/> |아니요  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |
|Office 2013  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |현대 인증에만 해당 합니다.  <br/> |연결에 실패 합니다.  <br/> |
   
### <a name="skype-for-business-online"></a>비즈니스용 Skype 온라인
<a name="BK_SFBO"> </a>

다음 표에서에 연결할 때 Skype 온라인 비즈니스에 대 한 함께 또는 따로 현대 인증 2016 Office 클라이언트 응용 프로그램이 나 Office 2013에 대 한 인증 동작을 설명 합니다.
  
|Office 클라이언트 응용 프로그램 버전 * * *|이 매개 변수가 레지스트리 키? * * *|에 대 한 최신 인증? * * *|테 넌 트 *에 대 한 최신 인증 및 인증 동작 설정|테 넌 트 (기본값)에 대 한 최신 인증 및 인증 동작 해제 * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |아니요, 또는 EnableADAL = 1  <br/> |예  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버, Microsoft Online 로그인 도우미 사용 됩니다. 서버는 비즈니스 온라인 테 넌 트에 대 한 Skype 사용할 수 없는 경우 현대 인증을 거부 합니다.  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버, Microsoft Online 로그인 도우미 사용 됩니다. 서버는 비즈니스 온라인 테 넌 트에 대 한 Skype 사용할 수 없는 경우 현대 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버, Microsoft Online 로그인 도우미 사용 됩니다. 서버는 비즈니스 온라인 테 넌 트에 대 한 Skype 사용할 수 없는 경우 현대 인증을 거부 합니다.  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버, Microsoft Online 로그인 도우미 사용 됩니다. 서버는 비즈니스 온라인 테 넌 트에 대 한 Skype 사용할 수 없는 경우 현대 인증을 거부 합니다.  <br/> |
|Office 2016  <br/> |예, EnableADAL = 0  <br/> |아니요  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |
|Office 2013  <br/> |아니요  <br/> |아니요  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |
|Office 2013  <br/> |예, EnableADAL = 1  <br/> |예  <br/> |현대 인증 먼저 시도 됩니다. 현대 인증 연결을 거부 하는 서버, Microsoft Online 로그인 도우미 사용 됩니다. 서버는 비즈니스 온라인 테 넌 트에 대 한 Skype 사용할 수 없는 경우 현대 인증을 거부 합니다.  <br/> |Microsoft 온라인 로그인 도우미만 합니다.  <br/> |
   
## <a name="see-also"></a>참고 항목

[Office 클라이언트와 Office 365 현대 인증을 사용 하 여](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a)

