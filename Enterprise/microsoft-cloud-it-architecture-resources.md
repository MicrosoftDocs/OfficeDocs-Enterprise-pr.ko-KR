---
title: Microsoft 클라우드 IT 아키텍처 리소스
ms.author: bcarter
author: brendacarter
manager: laurawi
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 28986107-e2fb-4116-bfdd-f66d751a7c16
search.appverid:
- MET150
description: "Summary: Learn core cloud architecture concepts for Microsoft identity, security, networking, and hybrid. Review prescriptive recommendations for protecting files, identities, and devices when using Microsoft's cloud."
ms.openlocfilehash: c1d41fa4ca098a913c7fea039765f916614c7f9c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997905"
---
# <a name="microsoft-cloud-it-architecture-resources"></a>Microsoft 클라우드 IT 아키텍처 리소스

이러한 아키텍처 도구 및 포스터는 microsoft 클라우드 서비스에 대 한 정보를 제공 합니다 (예를 들어 Windows 365, 창 10, Azure Active Directory, Microsoft Intune, Microsoft Dynamics 365 및 하이브리드 온-프레미스 및 클라우드 솔루션 포함). IT 의사 결정권자와 설계자는 이러한 리소스를 사용하여 작업에 이상적인 솔루션을 결정하고 ID 및 보안과 같은 핵심 인프라 구성 요소에 대한 의사 결정을 내릴 수 있습니다. 
  
<!--**[Microsoft's Enterprise Cloud Roadmap](microsoft-cloud-it-architecture-resources.md#roadmap)** (Sway) -->
    
- **[Microsoft Cloud for Enterprise Architects 시리즈](microsoft-cloud-it-architecture-resources.md#cloudarch)** 
    <!-- [Microsoft Cloud Services and Platform Options](microsoft-cloud-it-architecture-resources.md#platformoptions) -->
    - [Microsoft Cloud Identity for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#identity)
    - [Microsoft Cloud Security for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#security)
    - [Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#networking)
    - [Microsoft Hybrid Cloud for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#hybrid)
    - [일반적인 공격 및 조직을 보호하는 Microsoft 기능](#common-attacks-and-microsoft-capabilities-that-protect-your-organization)
    - [Microsoft 365 Enterprise 기본 인프라](#m365foundationinfra)
    - [Microsoft 클라우드 테넌트간 마이그레이션에 대한 아키텍처 접근 방식](#architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations)
    
- **[Microsoft 365 Enterprise 솔루션 시리즈](microsoft-cloud-it-architecture-resources.md#BKMK_o365solutions)**:
    - [IT 설계자용 Microsoft 365의 Microsoft Teams 및 관련 생산성 서비스](#microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects)
    - [IT 설계자용 Microsoft 365의 그룹](#groups-in-microsoft-365-for-it-architects)
    - [다중 영역 조직에 대한 보안 및 정보 보호](#security-and-information-protection-for-multi-region-organizations)
    - [Office 365용 ID 및 디바이스 보호](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    - [Office 365의 파일 보호 솔루션](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    - [GDPR에 대한 Office 365 정보 보호](#office-365-information-protection-for-gdpr)
    - [정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](#microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations)
    - [Microsoft 전화 통신 솔루션](#microsoft-telephony-solutions) 
    
Let us know what you think! Send us email at [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 

<!--
<a name="roadmap"></a>
## Microsoft's Enterprise Cloud Roadmap

See the posters, icon sets, community venues, and other resources that describe the industry's most complete cloud solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumbnail for Enterprise Cloud Roadmap](media/c8b293b9-5992-4d29-b579-a6bbbd59d8d6.png)          ](https://aka.ms/cloudarchitecture) <br/> [Microsoft's Enterprise Cloud Roadmap](https://aka.ms/cloudarchitecture) (https://aka.ms/cloudarchitecture) <br/> |Swipe through this Sway experience for the resources that describe the industry's most complete cloud solution.  <br/> |
-->
  
<a name="cloudarch">
</a>
## Microsoft Cloud for Enterprise Architects 시리즈

이러한 클라우드 아키텍처 포스터는 microsoft 365, Azure Active Directory, Microsoft Intune, Microsoft Dynamics CRM Online 및 하이브리드 온-프레미스 및 클라우드 솔루션을 포함 하 여 Microsoft 클라우드 서비스에 대 한 정보를 제공 합니다. IT 의사 결정권자와 설계자는 이러한 리소스를 사용하여 작업에 이상적인 솔루션을 결정하고 ID 및 보안과 같은 핵심 인프라 구성 요소에 대한 의사 결정을 내릴 수 있습니다.

<!--  
<a name="platformoptions"></a>
### Microsoft Cloud Services and Platform Options

Learn key differences between Microsoft cloud services and platform offerings. Find the best fit for your solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumb image of cloud architecture model with service options](media/ff5c74e2-afc6-40c1-9292-cc4cb128cdd1.png)          ](https://www.microsoft.com/download/details.aspx?id=54432) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524731)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=524732)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=54432) <br/> | This model describes: <ul><li>  Software as a Service (SaaS) offerings, including Microsoft 365 </li><li>  Platform as a Service (PaaS) features in Microsoft Azure </li><li>  Infrastructure as a Service (IaaS) features in Microsoft Azure </li><li>  Private cloud datacenter capabilities using Windows Server and System Center </li><li>  Learn how Microsoft's own IT department is migrating to these cloud services and building its hybrid cloud. </li></ul><br/>|
-->

   
<a name="identity">

</a>
### Microsoft Cloud Identity for Enterprise Architects

Microsoft 클라우드 서비스 및 플랫폼을 사용하는 조직용으로 ID를 설계하는 과정과 관련하여 IT 설계자가 파악해야 하는 사항
  
|**항목**|**설명**|
|:-----|:-----|
|[![Microsoft Cloud ID 모델용 축소판 이미지](media/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png)          ](https://www.microsoft.com/download/details.aspx?id=54431) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586)  \| [Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd)           \| [추가 언어](https://www.microsoft.com/download/details.aspx?id=54431) <br/> | 이 모델에는 다음이 포함됩니다. <ul><li>Microsoft 클라우드를 사용하는 ID 소개 </li><li>Azure AD IDaaS 기능 </li><li>온-프레미스 Active Directory 도메인 서비스 계정을 Microsoft Azure Active Directory와 통합 </li><li>Azure에 디렉터리 구성 요소 추가 </li><li>Azure IaaS의 작업을 위한 도메인 서비스 옵션 </li></ul><br/>|
   
<a name="security"></a>
### <a name="microsoft-cloud-security-for-enterprise-architects"></a>Microsoft Cloud Security for Enterprise Architects

Microsoft 클라우드 서비스 및 플랫폼의 보안과 관련하여 IT 설계자가 파악해야 하는 사항
  
|**항목**|**설명**|
|:-----|:-----|
|[![Microsoft 클라우드 보안 모델용 축소판 이미지](media/5dc26f80-8888-4572-8ed9-a120d711e0f0.png)          ](https://www.microsoft.com/download/details.aspx?id=48121) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842070)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=842071)  \| [추가 언어](https://www.microsoft.com/download/details.aspx?id=48121) <br/> | 이 모델에는 다음이 포함됩니다. <ul><li>보안 서비스 및 플랫폼 제공에서 Microsoft의 역할</li><li>보안 위험을 완화하기 위한 고객의 책임</li><li>최상위 보안 인증 </li><li>Microsoft 컨설팅 서비스에서 제공하는 보안 제품 </ul><br/>|
   
<a name="networking"></a>
### <a name="microsoft-cloud-networking-for-enterprise-architects"></a>Microsoft Cloud Networking for Enterprise Architects

Microsoft 클라우드 서비스 및 플랫폼의 네트워킹과 관련하여 IT 설계자가 파악해야 하는 사항
  
|**항목**|**설명**|
|:-----|:-----|
|[![Microsoft 클라우드 네트워킹 모델의 축소판 이미지](media/95e8ab6a-b4d0-4836-acc1-b0b77ebf46e6.png)](media/Network-Poster/MSFT_cloud_architecture_networking.pdf) <br/> [PDF](media/Network-Poster/MSFT_cloud_architecture_networking.pdf)  \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Network-Poster/MSFT_cloud_architecture_networking.vsdx) <br/> | 이 모델에는 다음이 포함됩니다. <ul><li> 클라우드 연결을 위해 네트워크 확장 </li><li> Microsoft 클라우드 연결의 공통 요소 </li><li> Microsoft 클라우드 연결을 위한 ExpressRoute </li><li> Microsoft SaaS, Azure PaaS, Azure IaaS를 위한 네트워킹 디자인 </li></ul><br/>  <br/>|

<a name="hybrid"></a>
### <a name="microsoft-hybrid-cloud-for-enterprise-architects"></a>Microsoft Hybrid Cloud for Enterprise Architects

Microsoft 서비스 및 플랫폼용 하이브리드 클라우드와 관련하여 IT 설계자가 파악해야 하는 사항
  
|**항목**|**설명**|
|:-----|:-----|
|[![Microsoft 하이브리드 클라우드 모델의 축소판 이미지](media/9989c71e-f6a0-4dbe-906c-43e67b3ce537.png)](media/Hybrid-Poster/MSFT_cloud_architecture_hybrid.pdf) <br/> [PDF](media/Hybrid-Poster/MSFT_cloud_architecture_hybrid.pdf)  \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Hybrid-Poster/MSFT_cloud_architecture_hybrid.vsdx)  | 이 모델에는 다음이 포함됩니다. <ul><li> Microsoft 클라우드 서비스(SaaS, Azure PaaS, Azure IaaS) 및 공통 요소 </li><li> Microsoft 클라우드 서비스를 위한 하이브리드 클라우드 아키텍처 </li><li> Microsoft SaaS (Microsoft 365), Azure PaaS 및 Azure IaaS에 대 한 하이브리드 클라우드 시나리오 </li></ul><br/>|
   
<a name="attacks"></a>
### <a name="common-attacks-and-microsoft-capabilities-that-protect-your-organization"></a>일반적인 공격 및 조직을 보호하는 Microsoft 기능
가장 일반적인 사이버 공격과 Microsoft가 모든 공격 단계에서 조직을 지원하는 방식을 자세히 알아봅니다. 

|**항목**|**설명**|
|:-----|:-----|
|[![일반적인 공격의 축소판 그림 포스터입니다. ](media/common%20attacks-thumb3.png)](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) <br/> [PDF](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) \| [Visio](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.vsdx) <br/> | 이 포스터에서는 일반적인 공격의 경로를 보여 주고, 각 공격 단계에서 공격자를 중지하는 데 도움이 되는 기능에 대해 설명합니다. <br/>|

<a name="m365foundationinfra"></a>
### <a name="microsoft-365-enterprise-foundation-infrastructure"></a>Microsoft 365 Enterprise 기본 인프라

배포를 시작하려면 Microsoft 365 Enterprise의 [기본 인프라](https://docs.microsoft.com/microsoft-365/enterprise/deploy-foundation-infrastructure)에 대한 간략한 보기를 확인하세요.
  
|**항목**|**설명**|
|:-----|:-----|
|[![Microsoft 365 Enterprise 기본 인프라 포스터의 축소판 이미지](media/Microsoft365EnterpriseFoundInfra-thumb.png)](https://aka.ms/m365efoundinfraposter) <br/> [온라인으로](https://aka.ms/m365efoundinfraposter) \| [PDF 보기](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/deploy-foundation-infrastructure/Microsoft365EnterpriseFoundInfra.pdf) <br/> | 이 포스터는 목표, 기능 및 도구, 디자인 결정, 구성 결과, 온 보딩, 지속적인 모니터링 및 업데이트 측면에서 기초 인프라의 각 단계를 요약합니다. <br/>| 

### <a name="architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations"></a>Microsoft 클라우드 테넌트간 마이그레이션에 대한 아키텍처 접근 방식 
이 시리즈에서는 합병, 인수, 매각 및 기타 시나리오를 통해 새로운 클라우드 테넌트로 마이그레이션 할 수 있는 몇 가지 아키텍처 접근 방식에 대해 설명합니다. 이 항목에는 계획을 위한 시작점 지침을 제공합니다.

|**항목**|**설명**|
|:-----|:-----|
|[![Teams 논리 아키텍처 포스터의 축소판 그림 이미지](downloads/msft-tenant-to-tenant-migration-thumb.png)](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) <br/> [PDF](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/Microsoft-365-tenant-to-tenant-migration.vsdx)     |이 모델에는 다음이 포함됩니다. <ul><li>아키텍처 접근 방식에 대한 비즈니스 시나리오 매핑</li><li>디자인 고려 사항</li><li>단일 이벤트 마이그레이션 흐름</li><li>단계적 마이그레이션 흐름</li><li>테넌트 이동 또는 분할 흐름</li></ul>|

<a name="BKMK_o365solutions"></a>
## <a name="microsoft-365-enterprise-solution-series"></a>Microsoft 365 Enterprise 솔루션 시리즈

Microsoft 365 Enterprise 솔루션 시리즈는 Microsoft 365의 기능을 구현하기 위한 지침을 기술 중심으로 설명합니다.

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>IT 설계자용 Microsoft 365의 Microsoft Teams 및 관련 생산성 서비스
Microsoft Teams로 시장을 선도하는 Microsoft 365 생산성 서비스의 논리적 아키텍처입니다.

|**항목**|**설명**|
|:-----|:-----|
|[![Teams 논리 아키텍처 포스터의 축소판 그림 이미지](downloads/msft-teams-logical-architecture-thumb.png)](downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)     |Microsoft는 생산성 서비스 제품군을 제공하여 데이터 관리, 보안 및 규정 준수 기능이 포함된 공동 작업 환경을 제공합니다. <br/> <br/>이 일러스트레이션 시리즈는 엔터프라이즈 설계자를 위해 Microsoft Teams로 시장을 선도하는 생산성 서비스의 논리 아키텍처를 보여줍니다.|


### <a name="groups-in-microsoft-365-for-it-architects"></a>IT 설계자용 Microsoft 365의 그룹
IT 설계자가 Microsoft 365의 그룹에 대해 알아야 하는 점

|**항목**|**설명**|
|:-----|:-----|
|[![그룹 인포그래픽용 축소판 이미지](downloads/msft-m365-groups-architecture-thumb.png)](downloads/msft-m365-groups.pdf) <br/> [PDF](downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) |이러한 일러스트레이션은 다양한 그룹의 종류, 그룹을 만들고 관리하는 방법, 몇 가지 관리 권장 사항에 대해 자세한 설명을 제공합니다.|

### <a name="security-and-information-protection-for-multi-region-organizations"></a>다중 영역 조직에 대한 보안 및 정보 보호
단일 Microsoft 365 테넌트가 있는 다중 영역 조직에 대한 보안 및 정보 보호

|**항목**|**설명**|
|:-----|:-----|
|[![다중 영역 인포그래픽의 축소판 이미지](media/multi-region-single-tenant-security-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-security-info-protect-multi-region.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-security-info-protect-multi-region.pdf) \| [Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-security-info-protect-multi-region.vsdx) |글로벌 조직에 단일 Microsoft 365 테넌트의 사용은 많은 이유로 최선의 선택과 경험이 될 것입니다. 하지만 많은 설계자들이 다양한 영역에 걸쳐 보안 및 정보 보호 목적을 충족하기 위한 방법을 고심하고 있습니다. 이 항목의 집합은 권장 사항을 제공합니다. |


   
<a name="BKMK_O365IDP"></a>
### <a name="identity-and-device-protection-for-office-365"></a>Office 365용 ID 및 장치 보호

Azure AD 애플리케이션 프록시를 사용하여 게시한 온-프레미스 응용 프로그램, Office 365 및 다른 SaaS 서비스에 액세스하는 ID 및 디바이스를 보호하기 위해 권장되는 기능입니다.
  
|**항목**|**설명**|
|:-----|:-----|
|[![모델 포스터: Office 365 및 기타 SaaS 응용 프로그램용 ID 및 장치 보호](media/c1cfb31b-5150-45ff-b46c-3a237e9f5581.png)          ](https://www.microsoft.com/download/details.aspx?id=55032) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=841656)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657)  \| [추가 언어](https://www.microsoft.com/download/details.aspx?id=55032) <br/> |It's important to use consistent levels of protection across your data, identities, and devices. This document shows you which capabilities are comparable with more information on capabilities to protect identities and devices.  <br/> |
   
<a name="BKMK_O365fileprotect"></a>
### <a name="file-protection-solutions-in-office-365"></a>Office 365의 파일 보호 솔루션

세 가지 다른 민감도 수준에 따라 Office 365에서 파일을 보호하기 위해 권장되는 기능입니다.
  
|**항목**|**설명**|
|:-----|:-----|
|[![Office 365 미니 포스터 집합의 파일 보호 솔루션에 대한 미리 보기](media/24be68b5-d852-4fdb-94ad-94491a19edd8.png)          ](https://www.microsoft.com/download/details.aspx?id=55523) <br/> [PDF](https://go.microsoft.com/fwlink/?linkid=2004320)  \| [Visio](https://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.vsdx) <br/> |It's important to use consistent levels of protection across your data, identities, and devices. This document shows you which capabilities are comparable with more information on capabilities to protect files in Office 365.  <br/> |
   

### <a name="office-365-information-protection-for-gdpr"></a>GDPR에 대한 Office 365 정보 보호

Prescriptive recommendations for discovering, classifying, protecting, and monitoring personal data. This solution uses General Data Protection Regulation (GDPR) as an example, but you can apply the same process to achieve compliance with many other regulations.

|**항목**|**설명**|
|:-----|:-----|
|![GDPR에 대한 Office 365 정보 보호 간략 설명](media/o365infoprotectforgdpr-thumb.png)  <br/> [PDF](https://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.pdf) \| [Visio](https://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.vsdx)    |기사 형식으로이 콘텐츠를 보려면 [ GDPR에 대한 Office 365 정보 보호](https://docs.microsoft.com/Office365/SecurityCompliance/office-365-information-protection-for-gdpr)를 참조하십시오.      |

### <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a>정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침 

This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment.


|**항목**|**설명**|
|:-----|:-----|
|**정치적 캠페인을 위한 Microsoft 보안 지침** <br/> [![미니 포스터 집합에 대한 미리 보기입니다.](media/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf) <br/> [PDF](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)  \| [Visio](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.vsdx) <br/> |This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.  <br/> |
|**비영리 조직을 위한 Microsoft 보안 지침** <br/> [![다운로드 가능한 파일에 대한 미리 보기 이미지](media/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf) <br/> [PDF](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)  \| [Visio](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.vsdx) <br/> |This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.  <br/> |

This guidance includes Test Lab Guides. For more information, see [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](https://docs.microsoft.com/Office365/SecurityCompliance/microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o).

### <a name="microsoft-telephony-solutions"></a>Microsoft 전화 통신 솔루션

Microsoft supports several options as you begin your journey to Teams in the Microsoft cloud. This poster helps you decide which Microsoft telephony solution (Phone System in the cloud or Enterprise Voice on-premises) is right for users in your organization, and how your organization can connect to the Public Switched Telephone Network (PSTN).

![Microsoft 전화 통신 솔루션 포스터 간략 설명](media/microsoft-telephony-solutions-thumb.png) <br/>
[PDF](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.pdf) | [Visio](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.vsdx) 

자세한 내용은이 포스터에 대한 문서인 [Microsoft 전화 통신 솔루션](https://docs.microsoft.com/SkypeForBusiness/hybrid/msft-telephony-solutions)을 참조하세요.
  
## <a name="see-also"></a>참고 항목

[Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Microsoft 365 Enterprise 테스트 랩 가이드](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)
  
[하이브리드 솔루션](hybrid-solutions.md)

