---
title: Microsoft 클라우드 제품용 구독, 라이선스, 계정 및 테넌트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
ms.custom:
- seo-marvel-apr2020
- Ent_Architecture
description: Microsoft의 클라우드 제품에서 조직, 구독, 라이선스, 사용자 계정 및 테넌트의 관계를 이해합니다.
ms.openlocfilehash: 7546d4b24c66946e287aa51deb2d1f1896045322
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603670"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Microsoft 클라우드 제품용 구독, 라이선스, 계정 및 테넌트

Microsoft는 해당 클라우드 제품 간에 일관된 ID 사용 및 요금 청구를 위해 조직, 구독, 라이선스 및 사용자 계정을 포함하는 계층 구조를 제공합니다.
  
- Microsoft 365 및 Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>계층 구조의 요소

다음은 계층 구조의 요소입니다.
  
### <a name="organization"></a>조직

조직은 Microsoft 클라우드 서비스를 사용하는 비즈니스 엔터티를 나타내며, 일반적으로 하나 이상의 공용 DNS(Domain Name System) 도메인 이름(예: contoso.com)으로 식별됩니다. 조직은 구독을 위한 컨테이너입니다.
  
### <a name="subscriptions"></a>구독

구독은 하나 혹은 이상의 Microsoft 클라우드 플랫폼 또는 서비스를 사용하기 위한 Microsoft와의 약정이며 사용자 단위 라이선스 요금이나 클라우드 기반 리소스 소비량을 기준으로 요금이 부과됩니다. 

- Microsoft의 서비스로서의 소프트웨어 (SaaS) 기반 클라우드 서비스(Microsoft 365 및 Dynamics 365)는 사용자 단위 라이선스 요금을 부과합니다. 
- Microsoft의 서비스로서의 플랫폼 (PaaS) 및 서비스로서의 인프라 (IaaS) 클라우드 서비스는 (Azure) 클라우드 리소스 소비량을 기반으로 요금을 부과합니다.
 
평가판 구독을 사용할 수도 있지만, 일정 기간이 지나거나 이용 요금이 다 사용된 후에는 구독이 만료됩니다. 평가판 구독을 유료 구독으로 변환할 수 있습니다.
  
조직은 다수의 Microsoft의 클라우드 서비스를 구독할 수 있습니다. 그림 1에서는 여러 개의 Microsoft 365 구독, Dynamics 365 구독 및 여러 개의 Azure 구독이 있는 단일 조직을 보여줍니다.

**그림 1: 여러 개의 조직용 구독 예**

![Microsoft의 클라우드 서비스용 구독이 여러 개 있는 예제 조직입니다.](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>라이선스

Microsoft의 SaaS 클라우드 제품의 경우 라이선스를 통해 특정 사용자 계정이 클라우드 서비스를 사용할 수 있도록 해줍니다. 구독의 일부로서 구독자에게 고정 월별 요금이 청구됩니다. 관리자는 구독의 개별 사용자 계정에 라이선스를 할당합니다. 예를 들어, 그림 2에서 Contoso Corporation는 Microsoft 365 E5를 구독하고 100개의 라이선스를 보유하고 있어 최대 100개의 개별 사용자 계정을 사용하여 Microsoft 365 E5의 기능 및 서비스를 사용할 수 있습니다.
  
**그림 2: 조직을 위한 SaaS 기반 구독에 포함된 라이선스**

![Microsoft의 SaaS 기반 클라우드 서비스용 구독에 포함된 여러 라이선스 예제입니다.](media/Subscriptions/Subscriptions-Fig2.png)
  
Azure PaaS 기반 클라우드 서비스의 경우 소프트웨어 라이선스가 서비스 가격에 기본적으로 포함됩니다.
  
Azure IaaS 기반 가상 머신의 경우 가상 머신 이미지에 설치되어 있는 소프트웨어 또는 이미지를 사용하기 위한 추가 라이선스가 필요할 수도 있습니다. 일부 가상 머신 이미지는 설치된 소프트웨어의 라이선스 버전을 가지며 서버에 대한 분당 요금에 해당 요금이 포함됩니다. 제공된 예제는 SQL Server 2014 및 SQL Server 2016에 대한 가상 머신 이미지입니다. 
  
일부 가상 머신 이미지에는 평가판 버전의 응용 프로그램이 설치되어 있고 평가 기간 이후에도 사용하려면 추가 소프트웨어 응용 프로그램 라이선스가 필요합니다. 예를 들어, SharePoint Server 2016 평가판 가상 머신 이미지에는 사전 설치된 SharePoint Server 2016 평가판이 포함되어 있습니다. 평가판 만료일 이후에도 SharePoint Server 2016을 계속 사용하려면 Microsoft에서 SharePoint Server 2016 라이선스 및 클라이언트 라이선스를 구입해야 합니다. 이러한 청구 금액은 Azure 구독과는 별개이며, 가상 머신을 실행하는 분당 요금은 여전히 부과됩니다.
  
### <a name="user-accounts"></a>사용자 계정

모든 Microsoft 클라우드 서비스의 사용자 계정은 사용자 계정 및 그룹이 포함되어 있는 Azure AD (Azure 액티브 디렉터리) 테넌트에 저장됩니다. Azure AD 테넌트는 Windows server 기반의 서비스인 Azure AD Connect를 사용하여 기존의 AD DS (액티브 디렉터리 도메인 서비스) 계정과 동기화될 수 있습니다. 이를 디렉터리 동기화라고 합니다.
  
그림 3은 조직 계정이 포함된 일반적인 Azure 테넌트를 사용하는 조직의 여러 구독 예를 보여줍니다.
  
**그림 3: 동일한 Azure 테넌트를 사용하는 조직의 여러 구독**

![모두 동일한 Azure 테넌트를 사용하는 여러 개의 구독이 있는 예제 조직입니다.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>테넌트

SaaS 클라우드 제공품의 경우 테넌트는 클라우드 서비스를 제공하는 서버가 있는 지역 위치입니다. 예를 들어, Contoso Corporation은 유럽 지역을 선택하여 파리 본사에 있는 15,000명의 작업자를 위해 Microsoft 365, EMS 및 Dynamics 365 테넌트를 호스트했습니다.
  
Azure IaaS에 호스트된 Azure PaaS 서비스 및 가상 머신 기반 워크로드는 전 세계의 모든 Azure 데이터 센터에서 테넌시를 둘 수 있습니다. Azure PaaS 앱 또는 서비스를 만들 때는 위치로 사용되고, IaaS 워크로드의 요소로도 알려진 Azure 데이터 센터를 지정할 수 있습니다.
  
Azure AD 테넌트는 계정 및 그룹을 포함하는 Azure AD의 특정 인스턴스를 말합니다. Microsoft 365 또는 Dynamics 365의 유료 또는 평가판 구독에는 무료 Azure AD 테넌트가 포함됩니다. Azure AD 테넌트는 다른 Azure 서비스를 포함하지 않으며 Azure 평가판 또는 유료 구독과 다릅니다.
  
### <a name="summary-of-the-hierarchy"></a>계층 구조의 요약

간단한 설명은 다음과 같습니다.
  
- 하나의 조직에 구독이 여러 개일 수 있습니다.
    
  - 하나의 구독에 라이선스가 여러 개 있을 수 있습니다.
    
  - 라이선스를 개별 사용자 계정에 할당할 수 있습니다.
    
  - 사용자 계정은 Azure AD테넌트에 저장됩니다.
    
조직, 구독, 라이선스 및 사용자 계정의 관계를 보여주는 예제는 다음과 같습니다.
  
- 공용 도메인 이름으로 식별되는 조직
    
  - 사용자 라이선스가 있는 Microsoft 365 E3 구독
    
    사용자 라이선스가 있는 Microsoft 365 E5 구독
    
    사용자 라이선스가 있는 Dynamics 365 구독
    
    여러 Azure 구독
    
  - 일반적인 Azure AD 테넌트에 있는 조직의 사용자 계정
    
다수의 Microsoft 클라우드 서비스의 구독은 공통 ID제공자 역할을 하는 동일한 Azure AD 테넌트를 사용할 수 있습니다. 온-프레미스 AD DS의 동기화된 계정을 포함하는 중앙 Azure AD 테넌트는 조직에 클라우드 기반의 서비스로서의 ID (IDaaS)를 제공합니다. 
  
**그림 4: 조직에 대한 동기화된 온-프레미스 계정 및 IDaaS**

![조직에 대한 IDaaS(Identity as a Service)입니다.](media/Subscriptions/Subscriptions-Fig4.png)
  
그림 4는 일반적인 Azure AD 테넌트가 Azure AD Domains Services를 사용하는 Microsoft의 SaaS 클라우드 서비스, Azure PaaS 앱 및 Azure IaaS의 가상 머신에서 사용되는 방법을 보여 줍니다. Azure AD Connect는 온-프레미스 AD DS(Active Directory Domain Services) 포리스트를 Azure AD 테넌트와 동기화합니다.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>여러 Microsoft 클라우드 서비스에 대한 구독 결합

다음 표에서는 한 가지 유형의 클라우드 서비스에 대한 구독이 이미 있고(첫 번째 열 아래쪽에 레이블 참조), 다른 클라우드 서비스에 대한 구독을 추가하는 경우(열 가로 방향으로) 여러 Microsoft 클라우드 서비스를 결합하는 방법을 설명합니다.
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |해당 없음  <br/> |Azure Portal에서 조직에 Azure 구독을 추가합니다.  <br/> |Microsoft 365 관리 센터에서 조직에 Dynamics 365 구독을 추가합니다.  <br/> |
|**Azure** <br/> |조직에 Microsoft 365 구독을 추가합니다.  <br/> |해당 없음  <br/> |조직에 Dynamics 365 구독을 추가합니다.  <br/> |
|**Dynamics 365** <br/> |조직에 Microsoft 365 구독을 추가합니다.  <br/> |Azure Portal에서 조직에 Azure 구독을 추가합니다.  <br/> |해당 없음  <br/> |
   
관리 센터를 사용하면 Microsoft SaaS 기반 서비스를 위해 조직에 구독을 쉽게 추가할 수 있습니다.
  
1. 글로벌 관리자 계정을 사용하여 Microsoft 365 관리 센터([https://admin.microsoft.com](https://admin.microsoft.com))에 로그인합니다.
    
2. **관리 센터** 홈페이지의 왼쪽 탐색 창에서 **청구**를 클릭하고 **서비스 구매**를 클릭합니다.
    
3. **서비스 구매** 페이지에서 새 구독을 구입합니다.
    
관리 센터는 SaaS 기반 클라우드 서비스에 대한 새 구독에 Microsoft 365 구독의 조직 및 Azure 테넌트를 할당합니다.
  
Microsoft 365 구독과 동일한 조직 및 Azure 테넌트를 갖는 Azure 구독을 추가하려면
  
1. Microsoft 365 전역 관리자 계정을 사용하여 Azure Portal 포털([https://portal.azure.com](https://portal.azure.com))에 로그인합니다.
    
2. 왼쪽 탐색 모음에서 **구독**을 클릭하고 **추가**를 클릭합니다.
    
3. **구독 추가** 페이지에서 서비스를 선택하고 결제 정보 및 계약을 완료합니다.
    
Azure 및 Microsoft 365 구독으로 따로 구입했으며 Azure 구독에서 Microsoft 365 Azure AD 테넌트에 액세스하려는 경우 [Azure Active Directory 테넌트에 기존의 Azure 구독을 추가](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)의 지침을 참조하세요.
 
## <a name="see-also"></a>기타 참고 항목

[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)
  
[Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[하이브리드 솔루션](hybrid-solutions.md)

## <a name="next-step"></a>다음 단계

[Microsoft 365 네트워크 연결 평가](assessing-network-connectivity.md)
  
