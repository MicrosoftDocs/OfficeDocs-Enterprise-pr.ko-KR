---
title: Microsoft 365 클라이언트 앱 지원-조건부 액세스
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- NOCSH
description: 조건부 액세스에 대 한 Microsoft 365 클라이언트 앱 지원 이해
ms.openlocfilehash: 6081af2ad3bca69978a10baabeae0a13d783f0ae
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998506"
---
# <a name="microsoft-365-client-app-support--conditional-access"></a>Microsoft 365 클라이언트 앱 지원-조건부 액세스

현대 작업의 경우 사용자는 어디에서 나 다양 한 장치 및 앱을 사용 하 여 조직의 리소스에 액세스할 수 있습니다. 따라서 리소스에 액세스할 수 있는 사용자에 대 한 포커스는 더 이상 부족 합니다. 조직에서는 또한 액세스 제어 인프라에서 리소스에 액세스 하는 방법과 위치를 지원 해야 합니다.

Azure Active Directory (Azure AD) 장치, 위치 및 다단계 인증 기반 조건부 액세스를 사용 하 여이 새로운 요구 사항을 충족할 수 있습니다. 조건부 액세스는 사용자 환경의 앱 액세스에 대한 제어할 수 있도록 해 주는 Azure AD의 기능입니다. 이 기능은 특정 조건을 기반으로 하며 중앙 위치에서 관리됩니다.

[Azure AD 조건부 액세스](https://docs.microsoft.com/azure/active-directory/conditional-access/)에 대해 자세히 알아보세요.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - Windows 10 Desktop
 - Windows 10 최신 앱
 - 웹 브라우저
 - Android
 - iOS
 - macOS<sup>1</sup>

Microsoft 365의 플랫폼 지원에 대 한 자세한 내용은 [microsoft 365의 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.

## <a name="supported-clients"></a>지원되는 클라이언트

다음 클라이언트의 최신 버전에서는 조건부 액세스를 지원 합니다.

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> 포털](https://azure.microsoft.com/features/azure-portal/) | ![Access 아이콘](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![회사 포털 아이콘](media/o365-microsoft-64x64.png) <br> [회사 <br> 포털](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Cortana 아이콘](media/o365-cortana-64x64.png) <br> [Cortana](https://www.microsoft.com/cortana) | ![Delve 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) 
| ![Dynamics 365 아이콘](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![에 지 아이콘](media/o365-edge-64x64.png) <br> [면](https://www.microsoft.com/windows/microsoft-edge) | ![Exchange 아이콘](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Forms 아이콘](media/o365-forms-64x64.png) <br> [Forms​​](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com 아이콘](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![렌즈 아이콘](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365 관리 아이콘](media/o365-o365admin-64x64.png) <br> [Microsoft 365 <br> 관리자](https://products.office.com/business/manage-office-365-admin-app) | ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps 아이콘](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![전원 자동화 아이콘](media/o365-flow-64x64.png) <br> [전원 <br> 자동화](https://flow.microsoft.com)
| ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Project 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 아이콘](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![비즈니스용 Skype 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [<br>비즈니스용 Skype](https://www.skype.com/business/) | ![스티커 메모 아이콘](media/o365-stickynotes-64x64.png) <br> [스티커 메모](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream 아이콘](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 아이콘](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams 아이콘](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) 
| ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>지원 되는 PowerShell 모듈

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 아이콘](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> Macos의 OneDrive에 대 한 지원이 곧 제공 될 예정입니다.

## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
