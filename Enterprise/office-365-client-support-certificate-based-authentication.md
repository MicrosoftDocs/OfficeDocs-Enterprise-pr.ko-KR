---
title: Microsoft 365 클라이언트 앱 지원-인증서 기반 인증
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
description: 이 문서에서는 인증서 기반 인증에 대 한 Microsoft 365 클라이언트 앱 지원에 대 한 세부 정보를 확인 합니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 759979ac7236ff4a6cf4c77ab52fff9b472b84ec
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606674"
---
# <a name="microsoft-365-client-app-support--certificate-based-authentication"></a>Microsoft 365 클라이언트 앱 지원-인증서 기반 인증

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

인증서 기반 인증을 사용 하면 Windows, Android 또는 iOS 장치에서 클라이언트 인증서를 사용 하 여 Azure Active Directory에 인증할 수 있습니다. 이 기능을 구성 하면 모바일 장치에서 특정 메일 및 Microsoft Office 응용 프로그램에 대 한 사용자 이름 및 암호 조합을 입력할 필요가 없습니다.

자세한 내용은 [인증서 기반 인증](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started)을 확인 하세요.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - Windows 10 데스크톱<sup>2</sup>
 - Windows 10 최신 앱
 - 웹 브라우저<sup>3</sup>
 - Android<sup>4</sup>
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

Microsoft 365의 플랫폼 지원에 대 한 자세한 내용은 [microsoft 365의 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.

## <a name="supported-clients"></a>지원되는 클라이언트

다음 클라이언트의 최신 버전에서는 인증서 기반 인증을 지원 합니다.

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Access 아이콘](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> 포털](https://azure.microsoft.com/features/azure-portal/) | ![회사 포털 아이콘](media/o365-microsoft-64x64.png) <br> [회사 <br> 포털](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 아이콘](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![에 지 아이콘](media/o365-edge-64x64.png) <br> [면](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Forms 아이콘](media/o365-forms-64x64.png) <br> [Forms​​](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com 아이콘](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) 
| ![Office 365 관리 아이콘](media/o365-o365admin-64x64.png) <br> [Microsoft 365 <br> 관리자](https://products.office.com/business/manage-office-365-admin-app) | ![렌즈 아이콘](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Planner 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps 아이콘](media/o365-powerapps-64x64.png) <br> [PowerApps<sup>3</sup>](https://powerapps.microsoft.com) | ![전원 자동화 아이콘](media/o365-flow-64x64.png) <br> [전원 <br> 자동화](https://flow.microsoft.com) | ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Project 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 아이콘](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![비즈니스용 Skype 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [<br>비즈니스용 Skype](https://www.skype.com/business/) | ![스티커 메모 아이콘](media/o365-stickynotes-64x64.png) <br> [스티커 메모](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| ![Stream 아이콘](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 아이콘](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams 아이콘](media/o365-teams-64x64.png) <br> [팀<sup>2</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) 
| ![Whiteboard 아이콘](media/o365-whiteboard-64x64.png) <br> [화이트 보드<sup>3</sup>,<sup>4</sup>](https://whiteboard.microsoft.com/) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>지원 되는 PowerShell 모듈

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 아이콘](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> Macos의 OneDrive에 대 한 지원이 곧 제공 될 예정입니다. <br>
> <sup>2</sup> Windows 데스크톱의 Yammer 지원 및 macos가 곧 제공 될 예정입니다. 곧 Windows 데스크톱의 팀에 대 한 지원이 제공 됩니다.<br>
> <sup>3</sup> 웹 앱에서 PowerApps 및 화이트 보드에 대 한 지원이 곧 제공 될 예정입니다. <br>
> <sup>4</sup> Android의 화이트 보드에 대 한 지원이 곧 제공 될 예정입니다.

## <a name="see-also"></a>기타 참고 항목

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
