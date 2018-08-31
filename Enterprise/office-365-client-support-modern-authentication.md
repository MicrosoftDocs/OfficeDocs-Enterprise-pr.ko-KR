---
title: Office 365 클라이언트 응용 프로그램 지원-현대 인증
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
description: Office 365 현대 인증에 대 한 클라이언트 응용 프로그램을 지원 합니다.
ms.openlocfilehash: 6508724a1b4aa33cf41b260da1b49c9639138d0c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915173"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365 클라이언트 응용 프로그램 지원-현대 인증

서로 다른 플랫폼에 걸쳐 Active Directory 인증 라이브러리 ADAL 기반 로그인 Office 클라이언트 응용 프로그램에 대 한 Microsoft의 최신 인증 기능을 사용 하면 됩니다. 이 통해 다단계 인증 (MFA), 스마트 카드 및 인증서 기반 인증 등의 기능 로그인 합니다.

[다단계 인증](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) 및 [인증서 기반 인증](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)에 대 한 자세한 정보를 설명 합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

 - 10 Windows 바탕 화면
 - Windows 10 현대 앱
 - 웹 브라우저
 - Android
 - iOS
 - macOS

## <a name="supported-clients"></a>지원되는 클라이언트

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![굴 아이콘](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 아이콘](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![흐름 아이콘](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![양식 아이콘](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | 
| ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office 365 관리자 아이콘](media/o365-o365admin-64x64.png) <br> [Office 365 <br> 관리](https://products.office.com/business/manage-office-365-admin-app) | ![렌즈 아이콘](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![비즈니스 아이콘 비즈니스용 OneDrive](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote)
| ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![플래너 아이콘](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![프로젝트 아이콘](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) 
| ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype 비즈니스 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [용 Skype <br> 비즈니스](https://www.skype.com/business/) | ![StaffHub 아이콘](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![스트림 아이콘](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![아이콘 라](media/o365-sway-64x64.png) <br> [Sway](https://sway.com)
| ![팀 아이콘](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 아이콘](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)