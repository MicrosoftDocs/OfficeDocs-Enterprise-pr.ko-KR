---
title: Office 365 클라이언트 응용 프로그램 지원-조건부 액세스
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Office 365 클라이언트 응용 프로그램 지원 조건부 액세스에 대 한 이해
ms.openlocfilehash: 215b97daf532e22eb37618d66779378e37accb31
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915303"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 클라이언트 응용 프로그램 지원-조건부 액세스

현대 직장에서 사용자 거의 모든 곳에서 다양 한 장치 및 앱을 사용 하 여 조직의 리소스에 액세스할 수 있습니다. 따라서 방금 리소스에 액세스할 수 있는 사용자에 초점을 맞추고이 충분 한 아니다. 조직에 대 한 액세스 제어 인프라에는 리소스에 액세스 하는 방법과도 지원 해야 합니다. Azure AD 장치, 위치 및 다단계 인증 기반 조건부 액세스를 사용 하 여이 새로운 요구 사항을 충족할 수 있습니다. 조건부 액세스는 하면 컨트롤에 특정 조건에 따라 모든 사용자 환경에서 앱에 대 한 액세스를 적용할 수 있도록 하는 중앙 위치에서 관리 되는 Azure Active Directory의 기능입니다. 

[장치 기반](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [위치 기반](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations), 및 [MFA 기반](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) 조건부 액세스 하는 방법에 대 한 자세한 내용은.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - 10 Windows 바탕 화면
 - Windows 10 현대 앱
 - 웹 브라우저
 - Android
 - iOS
 - macOS<sup>1</sup>

## <a name="supported-clients"></a>지원되는 클라이언트

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![굴 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![흐름 아이콘](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![양식 아이콘](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 관리자 아이콘](media/o365-o365admin-64x64.png) <br> [Office 365 <br> 관리](https://products.office.com/business/manage-office-365-admin-app) | ![비즈니스 아이콘 비즈니스용 OneDrive](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![플래너 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![프로젝트 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype 비즈니스 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [용 Skype <br> 비즈니스](https://www.skype.com/business/) 
| ![StaffHub 아이콘](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![스트림 아이콘](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![아이콘 라](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![팀 아이콘](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> macOS 출시 예정에 SharePoint 앱을 지원 합니다.