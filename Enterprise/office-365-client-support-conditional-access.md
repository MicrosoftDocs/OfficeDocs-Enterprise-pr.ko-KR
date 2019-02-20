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
ms.openlocfilehash: 42dc6eaa5e144acb4b5b969b1414bf074ee35660
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085347"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 클라이언트 앱 지원-조건부 액세스

최신 작업을 수행 하는 사용자는 거의 모든 위치에서 다양 한 장치 및 앱을 사용 하 여 조직의 리소스에 액세스할 수 있습니다. 따라서 리소스에 액세스할 수 있는 사용자에 대 한 포커스는 더 이상 부족 합니다. 조직에서는 또한 액세스 제어 인프라에 리소스를 액세스 하는 방법과 위치를 지원 해야 합니다. Azure AD 장치, 위치 및 다단계 인증 기반 조건부 액세스를 사용 하 여이 새로운 요구 사항을 충족할 수 있습니다. 조건부 액세스는 환경의 앱에 대 한 액세스에 컨트롤을 적용할 수 있도록 하는 Azure Active Directory의 기능으로, 특정 조건을 기준으로 하며 중앙 위치에서 관리 됩니다. 

자세한 내용은 [조건부 액세스](https://docs.microsoft.com/azure/active-directory/conditional-access/)를 확인 하세요.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - Windows 10 Desktop
 - Windows 10 최신 앱
 - 웹 브라우저
 - Android
 - iOS
 - macOS

office 365의 플랫폼 지원에 대 한 자세한 내용은 [office 365에 대 한 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.

## <a name="supported-clients"></a>지원되는 클라이언트

다음 클라이언트의 최신 버전에서는 조건부 액세스를 지원 합니다.

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Delve 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![에 지 아이콘](media/o365-edge-64x64.png) <br> [Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![흐름 아이콘](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![양식 아이콘](media/o365-forms-64x64.png) <br> [양식](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) |
| ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office 365 관리 아이콘](media/o365-o365admin-64x64.png) <br> [Office 365 <br> 관리자](https://products.office.com/business/manage-office-365-admin-app) | ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) |
| ![Planner 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![프로젝트 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![비즈니스용 Skype 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [<br> 비즈니스용 Skype](https://www.skype.com/business/) | ![StaffHub 아이콘](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![스티커 메모 아이콘](media/o365-stickynotes-64x64.png) <br> [Sticky Notes](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![스트림 아이콘](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 아이콘](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![팀 아이콘](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)