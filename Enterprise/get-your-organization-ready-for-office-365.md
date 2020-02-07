---
title: Office 365 Enterprise 계획
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Office 365 엔터프라이즈 배포를 계획할 리소스에 대 한 액세스 권한을 확보 합니다.
ms.openlocfilehash: 31c0eb1e6867856abe59f57cb78ec828431d03fd
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840325"
---
# <a name="plan-for-office-365-enterprise"></a>Office 365 Enterprise 계획

엔터프라이즈 조직을 Office 365로 이동할 때는 IT 구축과 사용자 채택을 간소화 하는 주요 디자인 결정을 내리는 것이 중요 합니다. 

## <a name="planning-with-office-365-fasttrack"></a>Office 365 FastTrack 계획

Office [365에 대 한 Fasttrack](https://docs.microsoft.com/fasttrack/O365-fasttrack-benefit-for-office-365) 은 office 365 배포를 계획 하기 위한 Microsoft의 도움을 받을 수 있는 최상의 방법입니다. FastTrack은 가장 일반적인 디자인 고려 사항을 지원 하 고 방식에 따라 질문에 답할 수 있습니다. 

>[!Note]
>[Microsoft 파트너](https://www.microsoft.com/solution-providers/home)로부터 도움을 받을 수도 있습니다.
>

## <a name="do-it-yourself-planning-for-office-365"></a>Office 365에 대 한 직접 실행 계획

Office 365을 직접 계획 하려면 다음 영역에 대 한 계획 및 디자인 결정을 단계적으로 진행 합니다.

- Office 365 테넌트

  인터넷에 대 한 네트워크 연결, Office 365 id, 앱, 온-프레미스, Azure 및 기타 요소와의 통합에 대 한 계획을 포함 합니다. [여기](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)에서 시작 합니다.

- 클라이언트에 대 한 지원

  인증서 기반 인증, 모바일 장치 관리, 인증 옵션 및 테 넌 트 간 공동 작업을 포함 합니다. [여기](office-365-client-support-certificate-based-authentication.md)에서 시작 합니다.

- 하이브리드 최신 인증 지원

  주요 Office 365 작업의 하이브리드 구성을 사용 하는 경우 최신 인증을 계획 하는 방법을 제공 합니다. [여기](hybrid-modern-auth-overview.md)에서 시작 합니다.

- 이전 Office 클라이언트 및 서버

  Office 2007 및 Office 2010 클라이언트 및 서버 제품에 대 한 마이그레이션 정보가 포함 되어 있습니다. [여기](plan-upgrade-previous-versions-office.md)에서 시작 합니다.

>[!Note]
>[Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview) 구독에도이 프로세스를 사용할 수 있습니다.
>

Office 365 구독에 로그인 하 고 [office 365 서비스에 대 한 배포](deployment-advisors-for-office-365.md)관리자를 사용할 수도 있습니다.



<!--

This checklist will help your organization as you plan and prepare for a migration to Office 365. The phases and steps in the checklist are aligned with the guidance provided by the [Onboarding Center](https://go.microsoft.com/fwlink/?LinkId=517115). Feel free to adapt this checklist to your organization's needs.

Most organizations don't need to do anything to prepare for Office 365. It's an application on the web and people are able to use it as soon as they have an account. Other organizations have more locations, security practices, or other requirements that create the need for more planning. For enterprise-level organizations, follow the checklist items below to get started with Office 365.
  
If you want help getting Office 365 set up, [FastTrack](https://fasttrack.microsoft.com/office) is the easiest way to deploy Office 365, you can also sign in and use the [Deployment advisors for Office 365 services](deployment-advisors-for-office-365.md).
  
|**Choose one or more to get started:**||
|:-----|:-----|
| [System requirements for Office](https://products.office.com/office-system-requirements) |- Microsoft Office Professional, Office 365, Office 365 ProPlus, and each Office application for Windows, Mac, iOS, and Android all have specific system requirements. Ensure your hardware and software meet the minimum system requirements.|
|**Most** customers connect their on-premises directory to Office 365. Get a head start on directory preparation by [installing and running IdFix on your network](https://www.microsoft.com/download/details.aspx?id=36832). <br> Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium set up guide](https://aka.ms/aadpguidance) to get customized set up guidance. <br> |- Automated checks against your directory to [validate people's accounts will properly synchronize](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> - Recommends changes to directory objects and offers to automate the changes for you. <br> - [More details on using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Read** our [network performance guidance](https://aka.ms/tune) and use our tools to ensure you have the connectivity and performance configuration necessary to provide people with the best experience.  <br> | - Ensure you can connect to Office 365, if you filter or scan outbound traffic, you'll want to understand what [managing Office 365 endpoints](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) means for your organization.  <br>  - [Model and test your network capacity](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) or move to an [Azure ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) circuit for a more predictable experience.   |
|**Use** our [planning checklist](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) as a starting place for building your own deployment plan.  <br> | - In-depth overview of possible areas you'll need to plan for with links to reference or how-to information to help you plan. |
|**Use** the [Exchange Server Large Item Script](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) to find mail items that may be too large to migrate.  <br> | - Uses Exchange Web Services to impersonate, access, scan the mailbox for file sizes you specify, and dumps the results in a CSV file. Read the [detailed instructions on how to use the script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**Take** advantage of [Microsoft deployment experts](https://go.microsoft.com/fwlink/?LinkId=517115) who can help you from planning to helping everyone start using the new services and applications.  <br> Use the [Deployment wizards for Office 365 services](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) to get customized set up guidance.  <br> | - The Onboarding center works directly with customers and with partner organizations. Give them a call today. |
|**Use** the [templates and resources in the Office 365 success center](https://www.microsoft.com/fasttrack/resources) to share your deployment and onboarding plans with the people in your organization.  <br> | - Communication with everyone before, during, and after the transition to Office 365 is critical.  <br> - Use our templates, guides, and handouts to improve your communications. |
|**Read** the article [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.  <br> | - This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity. |
   
Want more resources to help you integrate Office 365 with your broader cloud strategy? Here are the [Microsoft cloud IT architecture resources](https://docs.microsoft.com/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## Want to talk with support?

We're here to help, [contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products.


--> 