---
title: Office 365 클라이언트 앱 지원-조건부 액세스
ms.author: robmazz
author: robmazz
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
description: 조건부 액세스에 대 한 Office 365 클라이언트 앱 지원 이해
ms.openlocfilehash: 3212d15f2df68256fc80e4544fc7e61cdccc82c2
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517562"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 클라이언트 앱 지원-조건부 액세스

최신 작업을 수행 하는 사용자는 거의 모든 위치에서 다양 한 장치 및 앱을 사용 하 여 조직의 리소스에 액세스할 수 있습니다. 따라서 리소스에 액세스할 수 있는 사용자에 대 한 포커스는 더 이상 부족 합니다. 조직에서는 또한 액세스 제어 인프라에 리소스를 액세스 하는 방법과 위치를 지원 해야 합니다. Azure AD 장치, 위치 및 다단계 인증 기반 조건부 액세스를 사용 하 여이 새로운 요구 사항을 충족할 수 있습니다. 조건부 액세스는 환경의 앱에 대 한 액세스에 컨트롤을 적용할 수 있도록 하는 Azure Active Directory의 기능으로, 특정 조건을 기준으로 하며 중앙 위치에서 관리 됩니다.

자세한 내용은 [조건부 액세스](https://docs.microsoft.com/azure/active-directory/conditional-access/)를 확인 하세요.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - Windows 10 Desktop
 - Windows 10 최신 앱
 - 웹 브라우저
 - Android<sup>1</sup>
 - iOS
 - macos<sup>2</sup>

office 365의 플랫폼 지원에 대 한 자세한 내용은 [office 365에 대 한 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.

## <a name="supported-clients"></a>지원되는 클라이언트

다음 클라이언트의 최신 버전에서는 조건부 액세스를 지원 합니다.

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 아이콘](media/o365-azure-64x64.png) <br> [Azure AD <br> 포털 ](https://azure.microsoft.com/features/azure-portal/) | ![액세스 아이콘](media/o365-access-64x64.png) <br> [액세스](https://products.office.com/access) | ![Delve 아이콘](media/o365-delve-64x64.png) <br> [Delve<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Dynamics 365 아이콘](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![에 지 아이콘](media/o365-edge-64x64.png) <br> [면](https://www.microsoft.com/windows/microsoft-edge) 
| ![Exchange 아이콘](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![흐름 아이콘](media/o365-flow-64x64.png) <br> [흐름](https://flow.microsoft.com) | ![양식 아이콘](media/o365-forms-64x64.png) <br> [양식](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![렌즈 아이콘](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365 관리 아이콘](media/o365-o365admin-64x64.png) <br> [Office 365 <br> 관리자](https://products.office.com/business/manage-office-365-admin-app) | ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) |
| ![Planner 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![프로젝트 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 아이콘](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher)
| ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![비즈니스용 Skype 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [<br> 비즈니스용 Skype](https://www.skype.com/business/) | ![스티커 메모 아이콘](media/o365-stickynotes-64x64.png) <br> [스티커 메모](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![스트림 아이콘](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 아이콘](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![팀 아이콘](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> Android의 Delve에 대 한 지원이 곧 제공 될 예정입니다. <br>
> <sup>2</sup> macos의 OneDrive에 대 한 지원이 곧 제공 될 예정입니다.