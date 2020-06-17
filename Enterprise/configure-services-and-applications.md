---
title: Microsoft 365 Enterprise 서비스 및 응용 프로그램 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: deployment
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 7cec08a5-97fd-4761-b23b-ef3d66519e30
f1.keywords:
- NOCSH
description: Microsoft 365 Enterprise 서비스 및 응용 프로그램 구성
ms.openlocfilehash: 915d4baa18705e813f6d11a35dff6208c26ab0d3
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735956"
---
# <a name="configure-microsoft-365-enterprise-services-and-applications"></a>Microsoft 365 Enterprise 서비스 및 응용 프로그램 구성

[기본적인 설치 지침은](https://docs.microsoft.com/microsoft-365/admin/setup/setup) Microsoft 365 서비스 및 응용 프로그램을 사용 하는 가장 짧은 시간에 모든 사용자에 게 제공 됩니다. 모든 사용자가 사용을 시작 하기 전에 구성 해야 하는 경우가 있습니다. 예를 들어 메일 라우팅, 파일 저장소 또는 공유 정책을 구성 하려는 경우 
  
Microsoft 365을 설정 하는 데 도움이 필요 하면 [microsoft 365 및 Office 365 서비스에 대 한](setup-guides-for-office-365.md) **[Fasttrack](https://www.microsoft.com/fasttrack/microsoft-365)** 또는 설치 가이드를 사용 합니다.
  
|**서비스 및 응용 프로그램**|**리소스**|
|:-----|:-----|
|**Microsoft 365 제품군** |- [Microsoft 365 로그인 페이지에 회사 브랜딩 추가](https://support.office.com/article/Add-your-company-branding-to-Office-365-Sign-In-Page-a1229cdb-ce19-4da5-90c7-2b9b146aef0a) <br> - [Microsoft 365 도움말 창에 사용자 지정 지원 센터 정보 추가](https://support.office.com/article/Add-customized-help-desk-info-to-the-Office-365-help-pane-9dd9b104-68f7-4d49-9a30-82561c7d79a3) <br> - [Microsoft Azure AD와 다른 응용 프로그램의 통합 추가](https://support.office.com/article/Integrated-Apps-and-Azure-AD-for-Office-365-administrators-cb2250e3-451e-416f-bf4e-363549652c2a).  <br> 그룹을 사용하여 전자 메일, 일정, 문서 및 채팅으로 공동 작업하는 방법에 대해 - [자세히 알아보기](https://support.office.com/Article/Learn-more-about-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br> - [Microsoft 365에서 모바일 장치 관리 활성화 및 사용](https://support.office.microsoft.com/article/Manage-mobile-devices-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd) <br> - [Microsoft 365 연결 모니터링](monitor-connectivity.md) |
|**전자 메일** <br> (Exchange Online) | - [Exchange 배포 도우미를 사용하여 Exchange Hybrid](https://technet.microsoft.com/exdeploy2013)로 마이그레이션할 준비 하기  <br> - [Exchange 마이그레이션 관리자](https://aka.ms/office365setup)를 사용하여 사용자 지정 설치 지침 확인  <br> - [Exchange Online Protection 설정](https://technet.microsoft.com/library/jj723153%28v=exchg.150%29.aspx) |
|**사이트** <br> (SharePoint Online) | - [SharePoint Server 2013](https://technet.microsoft.com/library/jj838715) 의 하이브리드 기능을 구성 합니다.<br> - [사이트 서식 파일을 만들고 사용](https://support.office.com/article/Create-and-use-site-templates-60371B0F-00E0-4C49-A844-34759EBDD989)하여 SharePoint Online의 모양과 느낌을 사용자 지정 <br> - [SharePoint Online 계획 가이드](https://support.office.com/article/SharePoint-Online-Planning-Guide-for-Office-365-for-business-d5089cdf-3fd2-4230-acbd-20ecda2f9bb8) 또는 [ SharePoint Online 배포 관리자](https://aka.ms/spoguidance)를 사용하여 추가 기능 계획 및 구성 <br> - [비디오 포털](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da) 관리 |
|**IM 및 온라인 모임** <br> (비즈니스용 Skype Online) | - [Lync Server 2013](https://technet.microsoft.com/library/jj204805) 또는 [비즈니스용 Skype 2015](https://technet.microsoft.com/library/jj205403) 에 대 한 하이브리드 기능을 구성 합니다.<br> - [비즈니스용 Skype Online 설정](https://support.office.com/article/Set-up-Skype-for-Business-Online-40296968-e779-4259-980b-c2de1c044c6e) 및 통화 라우팅, 전화 회의 및 공유와 같은 공통 기능 구성  <br> - [비즈니스용 Skype 배포 관리자](https://aka.ms/skypeguidance)를 사용하여 사용자 지정된 설정 지침 확인 |
| **파일 저장소 및 공유** <br> (비즈니스용 OneDrive 및 SharePoint Online) | - [Microsoft 365 파일 저장 및 공유 설정](https://support.office.com/article/7aa9cdc8-2245-4218-81ee-86fa7c35f1de#BKMK_WhatDif): 비즈니스용 OneDrive를 사용 하 여 파일을 저장 하 고 ShharePoint Online 팀 사이트를 사용 해야 하는 경우에 대해 알아봅니다. <br> - [파일 저장 및 공유 설정](https://support.office.com/article/7aa9cdc8-2245-4218-81ee-86fa7c35f1de#BKMK_MoveDocsVideo): 비즈니스용 OneDrive 및 SharePoint 팀 사이트에서 파일을 업로드 하는 것이 얼마나 쉬운지 알아보기 <br> - [파일 저장 및 공유 설정](https://support.office.com/article/7aa9cdc8-2245-4218-81ee-86fa7c35f1de#BKMK_Store): 비즈니스용 OneDrive 및 팀 사이트에 파일을 업로드 하기 위한 모든 단계를 가져옵니다. 파일 공유에 대 한 팁 알아보기 <br> - [비즈니스용 OneDrive 설정 가이드 ](https://aka.ms/OD4Bguidance)를 사용하여 사용자 지정된 지침 확인 |
|**Microsoft 365 응용 프로그램** | -Microsoft 365 관리자는 [Office 배포 가이드](https://docs.microsoft.com/deployoffice) 를 사용 하 여 엔터프라이즈 배포 또는 업그레이드를 위한 Microsoft 365 앱을 계획 하는 데 도움이 되는 도움말을 확인 해야 합니다.  <br> - [Microsoft 365 용 Power BI 관리 센터](https://support.office.com/article/Power-BI-for-Office-365-Admin-Center-Help-5e391ecb-500c-47a3-bd0f-a6173b541044) <br> - [Microsoft 365 관리자를 위한 Office Delve](https://support.office.com/article/Office-Delve-for-Office-365-admins-54f87a42-15a4-44b4-9df0-d36287d9531b) <br> - [Sway에 대한 질문과 대답(FAQ)](https://support.office.com/article/446380fa-25bf-47b2-996c-e12cb2f9d075) <br> - [Project Online 시작](https://support.office.com/article/Get-started-with-Project-Online-e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)  <br> - [Microsoft Intune 배포 관리자](https://aka.ms/intuneguidance) |
|**기업용 소셜** <br> (Yammer) | - [Microsoft 365와 함께 Yammer 사용](https://support.office.com/article/Plan-for-Yammer-integration-with-Office-365-4086681f-6de1-4d39-aa72-752b2af1cbd7)  <br> - [Yammer Enterprise 설정 가이드](https://aka.ms/yammerdeploy)를 사용하여 사용자 지정된 설정 확인 |
