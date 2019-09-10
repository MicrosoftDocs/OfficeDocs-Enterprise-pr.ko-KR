---
title: Office 365 클라이언트 앱 지원-Single Sign-on
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
description: Single sign-on에 대 한 Office 365 클라이언트 앱 지원
ms.openlocfilehash: e8f3aab27d898ebbc564a1815320bce72a151d35
ms.sourcegitcommit: b1a32e8df403143fb34eaddf116aed3595228c8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2019
ms.locfileid: "36817254"
---
# <a name="office-365-client-app-support--single-sign-on"></a>Office 365 클라이언트 앱 지원-Single Sign-on

SSO (Single sign-on)는 사용자가 Azure Active Directory (Azure AD)의 응용 프로그램에 로그온 할 때 보안 및 편의성을 추가 합니다. Single sign-on을 사용 하는 경우 사용자는 도메인에 가입 된 장치, 회사 리소스, SaaS (software as a service) 응용 프로그램 및 웹 응용 프로그램에 액세스 하기 위해 한 계정으로 한 번씩 로그인 합니다.

자세한 내용은 [single sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)을 참고 하세요.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - Windows 10 데스크톱<sup>2</sup>
 - Windows 10 최신 앱<sup>4</sup>
 - 웹 브라우저
 - Android<sup>3</sup>
 - iOS<sup>1</sup>
 - macOS

Office 365의 플랫폼 지원에 대 한 자세한 내용은 [office 365에 대 한 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.

## <a name="supported-clients"></a>지원되는 클라이언트

최신 버전의 다음 클라이언트는 single sign-on을 지원 합니다.

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![액세스 아이콘](media/o365-access-64x64.png) <br> [액세스](https://products.office.com/access) | ![회사 포털 아이콘](media/o365-microsoft-64x64.png) <br> [회사 <br> 포털<sup>3</sup>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![에 지 아이콘](media/o365-edge-64x64.png) <br> [면](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) 
| ![흐름 아이콘](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala<sup>1</sup>](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com 아이콘](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![렌즈 아이콘](media/o365-lens-64x64.png) <br> [Office Lens<sup>4</sup>](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote<sup>2</sup>](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI<sup>2</sup>](https://powerbi.microsoft.com)| ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![프로젝트 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 아이콘](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![비즈니스용 Skype 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [<br> 비즈니스용 Skype](https://www.skype.com/business/) | ![스티커 메모 아이콘](media/o365-stickynotes-64x64.png) <br> [스티커 메모](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| ![Sway 아이콘](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![팀 아이콘](media/o365-teams-64x64.png) <br> [팀<sup>2</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [수행할 작업](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![화이트 보드 아이콘](media/o365-whiteboard-64x64.png) <br> [화이트 보드<sup>3</sup>](https://whiteboard.microsoft.com/) 
| ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>지원 되는 PowerShell 모듈

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 아이콘](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> IOS의 Kaizala에 대 한 지원이 곧 제공 될 예정입니다. <br>
> <sup>2</sup> Windows 10 데스크톱의 OneNote, PowerBI, 팀 및 Yammer에 대 한 지원이 곧 제공 될 예정입니다. <br>
> <sup>3</sup> Android의 화이트 보드 지원 곧 제공 될 예정입니다. <br>
> <sup>4</sup> Windows 10 최신 앱의 Office Lens에 대 한 지원이 곧 제공 될 예정입니다. <br>
