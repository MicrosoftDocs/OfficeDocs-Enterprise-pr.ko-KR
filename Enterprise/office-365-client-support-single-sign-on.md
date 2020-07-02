---
title: Microsoft 365 클라이언트 앱 지원-Single Sign-on
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: Microsoft 365 클라이언트 앱이 single sign-on을 지원 합니다.
ms.openlocfilehash: beb0ae405b9c365da0faa64e31a36f7b571ce1aa
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998516"
---
# <a name="microsoft-365-client-app-support--single-sign-on"></a>Microsoft 365 클라이언트 앱 지원-Single Sign-on

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

SSO (Single sign-on)는 사용자가 Azure Active Directory (Azure AD)의 응용 프로그램에 로그온 할 때 보안 및 편의성을 추가 합니다. Single sign-on을 사용 하는 경우 사용자는 도메인에 가입 된 장치, 회사 리소스, SaaS (software as a service) 응용 프로그램 및 웹 응용 프로그램에 액세스 하기 위해 한 계정으로 한 번씩 로그인 합니다.

자세한 내용은 [single sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)을 참고 하세요.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - Windows 10 데스크톱<sup>2</sup>
 - Windows 10 최신 앱
 - 웹 브라우저
 - Android<sup>3</sup>
 - iOS<sup>1</sup>
 - macOS<sup>4</sup>

Microsoft 365의 플랫폼 지원에 대 한 자세한 내용은 [microsoft 365의 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.

## <a name="supported-clients"></a>지원되는 클라이언트

최신 버전의 다음 클라이언트는 single sign-on을 지원 합니다.

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Access 아이콘](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![회사 포털 아이콘](media/o365-microsoft-64x64.png) <br> [회사 <br> 포털<sup>3, 4</sup>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![에 지 아이콘](media/o365-edge-64x64.png) <br> [에 지<sup>1</sup>](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) 
| ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala<sup>1</sup>](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com 아이콘](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![렌즈 아이콘](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote<sup>2</sup>](https://products.office.com/onenote) 
| ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook<sup>4</sup>](https://products.office.com/outlook) | ![Planner 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![전원 자동화 아이콘](media/o365-flow-64x64.png) <br> [전원 <br> 자동화](https://flow.microsoft.com) | ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI<sup>2</sup>](https://powerbi.microsoft.com)| ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Project 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 아이콘](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![스티커 메모 아이콘](media/o365-stickynotes-64x64.png) <br> [스티커 메모](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw)  | ![Sway 아이콘](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Teams 아이콘](media/o365-teams-64x64.png) <br> [팀<sup>2, 4</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Whiteboard 아이콘](media/o365-whiteboard-64x64.png) <br> [화이트 보드<sup>3</sup>](https://whiteboard.microsoft.com/) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>지원 되는 PowerShell 모듈

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 아이콘](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> IOS의 Edge 및 Kaizala에 대 한 지원이 곧 제공 될 예정입니다. <br>
> <sup>2</sup> Windows 10 데스크톱의 OneNote, PowerBI, 팀 및 Yammer에 대 한 지원이 곧 제공 될 예정입니다. <br>
> <sup>3</sup> Android의 화이트 보드 지원 곧 제공 될 예정입니다. <br>
> <sup>4</sup> Macos에서 Outlook, 팀 및 회사 포털에 대 한 지원이 곧 제공 될 예정입니다. <br>

## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
