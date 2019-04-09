---
title: Office 365 클라이언트 앱 지원-최신 인증
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: 최신 인증을 위해 Office 365 클라이언트 앱을 지원 합니다.
ms.openlocfilehash: 997f2238fd654d267ef4f915571874bbda5e0ee6
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517572"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365 클라이언트 앱 지원-최신 인증

Microsoft의 최신 인증 기능은 서로 다른 플랫폼에서 Office 클라이언트 앱에 대해 ADAL (Active Directory 인증 라이브러리) 기반 로그인을 사용 하도록 설정 합니다. 이를 통해 MFA (multi-factor Authentication), 스마트 카드 및 인증서 기반 인증과 같은 로그인 기능을 사용할 수 있습니다.

[multi-factor authentication](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) 및 [인증서 기반 인증](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)에 대해 자세히 알아보세요.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - Windows 10 Desktop
 - Windows 10 최신 앱
 - 웹 브라우저
 - Android
 - iOS
 - macOS

office 365의 플랫폼 지원에 대 한 자세한 내용은 [office 365에 대 한 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.

## <a name="supported-clients"></a>지원되는 클라이언트

다음 클라이언트의 최신 버전은 최신 인증을 지원 합니다.

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![액세스 아이콘](media/o365-access-64x64.png) <br> [액세스](https://products.office.com/access) | ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> 포털 ](https://azure.microsoft.com/features/azure-portal/) | ![회사 포털 아이콘](media/o365-microsoft-64x64.png) <br> [회사 <br> 포털 ](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 아이콘](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![에 지 아이콘](media/o365-edge-64x64.png) <br> [면](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![흐름 아이콘](media/o365-flow-64x64.png) <br> [흐름](https://flow.microsoft.com) | ![양식 아이콘](media/o365-forms-64x64.png) <br> [양식](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 관리 아이콘](media/o365-o365admin-64x64.png) <br> [Office 365 <br> 관리자](https://products.office.com/business/manage-office-365-admin-app) | ![렌즈 아이콘](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Planner 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![프로젝트 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![비즈니스용 Skype 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [<br> 비즈니스용 Skype](https://www.skype.com/business/) | ![StaffHub 아이콘](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)| ![스티커 메모 아이콘](media/o365-stickynotes-64x64.png) <br> [스티커 메모](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![스트림 아이콘](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 아이콘](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![팀 아이콘](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) 
| ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer <br> 알림](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>지원 되는 PowerShell 모듈

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 아이콘](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)