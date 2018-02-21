---
title: "구독, 라이선스, 계정 및 Microsoft의 클라우드 서비스에 대 한 테 넌 트"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: "요약: Microsoft의 클라우드 서비스에서 조직, 구독, 라이선스, 사용자 계정 및 테 넌 트의 관계를 이해 합니다."
ms.openlocfilehash: a1bcc040d046e4e5674f16432aeffb0a34b9031b
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>구독, 라이선스, 계정 및 Microsoft의 클라우드 서비스에 대 한 테 넌 트

 **요약:** Microsoft의 클라우드 서비스에서 조직, 구독, 라이선스, 사용자 계정 및 테 넌 트의 관계를 이해 합니다.
  
Microsoft에서는 해당 클라우드 서비스 간에 id 및 대금 청구의 일관 된 사용에 대 한 조직, 구독, 라이선스 및 사용자 계정을의 계층 구조를 제공합니다.
  
- Microsoft Office 365
    
    [사업 계획 및 가격](https://products.office.com/business/compare-office-365-for-business-plans) 에 대 한 자세한 내용은 참조 하십시오.
    
- Microsoft Azure
    
    자세한 내용은 [Azure 가격](https://azure.microsoft.com/pricing/) 을 참조 하십시오.
    
- Microsoft Intune 및 엔터프라이즈 이동성 + 보안 (EMS)
    
    자세한 내용은 [Intune 가격](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) 을 참조 하십시오.
    
- Microsoft Dynamics 365
    
    자세한 내용은 [Dynamics 365 가격](https://dynamics.microsoft.com/) 을 참조 하십시오.
    
## <a name="elements-of-the-hierarchy"></a>계층 구조 요소

계층의 요소는 다음과 같습니다.
  
### <a name="organization"></a>조직

조직에서 일반적으로 contoso.com와 같은 공용 도메인 이름 시스템 (DNS) 도메인 이름으로 식별 되는 Microsoft 클라우드 서비스를 사용 하는 비즈니스 엔터티를 나타냅니다. 조직에는 구독에 대 한 컨테이너입니다.
  
### <a name="subscriptions"></a>구독

구독에는 하나를 사용 하 여 Microsoft와 계약 또는 Microsoft 클라우드 플랫폼 수를 늘리거나 요금을 계산 하는 작업에 대 한 서비스 사용자 단위 라이선스 요금 또는 클라우드 기반 리소스 사용에 따라 합니다. Microsoft의 소프트웨어를 서비스로 (SaaS)-(Office 365, Intune/EMS 및 Dynamics 365) 기반된 클라우드 서비스 요금을 사용자 단위 라이선스입니다. Microsoft의 플랫폼 서비스 (PaaS) 및 인프라 서비스 (IaaS) 클라우드 (Azure) 제품 제공물 클라우드 리소스 사용을 기반으로 합니다.
  
평가판 구독을 사용할 수도 있습니다 하지만 시간이 경과 된 후 특정 시간 또는 소비 요금 구독이 만료 됩니다. 평가판 구독을 유료 구독으로 변환할 수 있습니다.
  
조직에서는 Microsoft의 클라우드 서비스에 대 한 여러 구독을 가질 수 있습니다. 그림 1 예가 나와 있습니다.
  
**그림 1: 조직에 대 한 여러 구독의 예**

![Microsoft의 클라우드 서비스용 구독이 여러 개 있는 예제 조직입니다.](images/Subscriptions/Subscriptions_Fig1.png)

  
그림 1은 여러 Office 365 구독, Intune 구독, Dynamics 365 구독 및 여러 Azure 구독이 있는 단일 조직을 보여줍니다.
  
### <a name="licenses"></a>라이선스

Microsoft의 SaaS 클라우드 서비스에 대 한 라이선스 허용 클라우드 서비스를 사용 하 여 특정 사용자 계정을 제공 합니다. 구독의 일부로 고정된 월별 요금을 청구 됩니다. 관리자는 구독에 있는 개별 사용자 계정에 라이선스를 할당합니다. 그림 2의 예제에서는 Contoso Corporation에는 엔터프라이즈 e 5 기능 및 서비스를 사용 하 여 최대 100 개의 개별 사용자 계정에 허용 하는 100 라이선스는 Office 365 Enterprise E5 구독 합니다.
  
**조직에 대 한 SaaS 기반 구독 내 그림 2: 라이선스**

![Microsoft의 SaaS 기반 클라우드 서비스용 구독에 포함된 여러 라이선스 예제입니다.](images/Subscriptions/Subscriptions_Fig2.png)
  
Azure PaaS 기반 클라우드 서비스에 대 한 소프트웨어 라이선스 서비스 가격으로 작성 됩니다.
  
Azure IaaS 기반 가상 컴퓨터에 대 한 소프트웨어 또는 가상 컴퓨터 이미지에 설치 하는 응용 프로그램을 사용 하 여 추가 라이선스 필요할 수 있습니다. 일부 가상 시스템 이미지가 사용이 허가 된 버전의 소프트웨어를 설치 하 고 비용 서버에 대 한 분당 속도에 포함 됩니다. 예는 SQL Server 2014 및 SQL Server 2016에 대 한 가상 컴퓨터 이미지입니다. 
  
일부 가상 시스템 이미지 설치 하는 응용 프로그램의 평가판 버전 있고 평가판 기간 이후에도 사용 하기 위해 추가 소프트웨어 응용 프로그램 라이선스가 필요 합니다. 등 SharePoint Server 2016 평가판 가상 컴퓨터 이미지를 미리 설치 된 SharePoint Server 2016의 평가판 버전을 포함 합니다. SharePoint Server 2016를 사용 하 여 내역 만료 날짜 이후에 계속 하려면 Microsoft에서 SharePoint Server 2016 라이선스 및 클라이언트 라이선스를 구입 해야 합니다. 이러한 요금은 Azure 구독을 별도로 및 가상 컴퓨터를 실행 하려면 분당 속도 계속 적용 됩니다.
  
### <a name="user-accounts"></a>사용자 계정

Microsoft의 클라우드 서비스의 모든 사용자 계정은 사용자 계정 및 그룹을 포함 하는 Azure Active Directory (AD) 보유자를에 저장 됩니다. Azure AD 테 넌 트 Azure AD 연결, Windows 서버 기반 서비스를 사용 하 여 기존 Windows Server AD 계정을와 동기화 할 수 있습니다. 이 디렉터리 동기화 (DirSync) 이라고 합니다.
  
그림 3에는 일반적인 Azure AD 테 넌 트 조직의 계정이 포함 된를 사용 하 여 조직의 여러 구독의 예가 나와 있습니다.
  
**그림 3: 여러 구독 하는 조직의 동일한 Azure AD 테 넌 트를 사용 하는**

![모두 동일한 Azure 테넌트를 사용하는 여러 개의 구독이 있는 예제 조직입니다.](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a>테 넌 트

SaaS 클라우드 서비스에 대 한 테 넌 트 클라우드 서비스를 제공 하는 서버를 보관 하는 지역 위치입니다. 예, Contoso Corporation를 호스팅하는 Office 365, EMS, 및 Dynamics 365 테 넌 트 자신의 파리 본사에서 15, 000 작업자에 대 한 유럽 지역 선택 했습니다.
  
Azure PaaS 서비스와 Azure IaaS에서 호스팅되는 가상 컴퓨터 기반 작업 전세계 모든 Azure 데이터 센터의 테 넌 시를 가질 수 있습니다. Azure PaaS 응용 프로그램 또는 서비스 또는 IaaS 작업량의 요소를 만들 때 해당 위치 라고 Azure 데이터 센터를 지정 합니다.
  
Azure AD 테 넌 트는 계정 및 그룹을 포함 하는 Azure AD의 특정 인스턴스. Office 365, Dynamics 365 또는 Intune/EMS 유료 또는 평가판 구독에 포함 무료 Azure AD 테 넌 트입니다. 이 Azure AD 테 넌 트 다른 Azure 서비스를 포함 하지 않는 및 Azure에 평가판 또는 유료 구독으로 같지 않습니다.
  
### <a name="summary-of-the-hierarchy"></a>계층 구조 요약

빠른 다시 살펴보기 다음과 같습니다.
  
- 조직에 여러 구독이 있을 수 있습니다.
    
  - 구독에 여러 라이선스를 가질 수 있습니다.
    
  - 개별 사용자 계정에 라이선스를 할당할 수 있습니다.
    
  - Azure AD 테 넌 트에 저장 된 사용자 계정
    
조직, 구독, 라이선스 및 사용자 계정의 관계의 예는 다음과 같습니다.
  
- 공용 도메인 이름을 사용 하 여 식별 하는 조직입니다.
    
  - 사용자 라이선스는 Office 365 Enterprise E3 구독 합니다.
    
    사용자 라이선스는 Office 365 Enterprise E5 구독 합니다.
    
    사용자 라이선스에 EMS 구독 합니다.
    
    사용자 라이선스 Dynamics 365 구독 합니다.
    
    여러 Azure 구독 합니다.
    
  - 일반적인 Azure AD 테 넌 트에는 조직의 사용자 계정입니다.
    
구독을 제공 하는 여러 Microsoft 클라우드 동일한 Azure AD 테 넌 트 id 공급자를 공통으로 작동 하는 사용할 수 있습니다. 중앙 온-프레미스 Windows Server AD의 동기화 된 계정이 포함 된 Azure AD 테 넌 트 조직에 대 한 서비스 (IDaaS)으로 클라우드 기반 Id를 제공 합니다. 이 그림 4에 표시 됩니다.
  
**그림 4: 동기화 된 온-프레미스 계정 하 고 조직에 대 한 IDaaS**

![조직에 대한 IaaS(Identity as a Service) IDaaS입니다.](images/Subscriptions/Subscriptions_Fig4.png)
  
그림 4는 Microsoft의 SaaS 클라우드 서비스, Azure PaaS 응용 프로그램 및 Azure AD 도메인 서비스를 사용 하 여 Azure IaaS에 가상 컴퓨터에서 일반적인 Azure AD 테 넌 트를 활용 하는 방법을 보여줍니다. Azure AD 연결 Azure AD 테 넌 트와 온-프레미스 Windows Server AD 포리스트를 동기화합니다.
  
Microsoft의 클라우드 서비스에서 identity 통합 하는 방법에 대 한 자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 Id](https://aka.ms/cloudarchidentity)를 참조 하십시오.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>여러 Microsoft 클라우드 서비스에 대 한 구독을 결합

다음 표에서 이미 구독을 필요에 따라 여러 Microsoft 클라우드 서비스를 결합 하는 방법과 한 가지 유형의 (첫째 열을 아래로 레이블)를 제공 하 고 다른 클라우드를 위한 구독을 추가 하는 클라우드에 대 한 제공 (간에 이동 합니다. 열)입니다.
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |해당 없음  <br/> |Azure 포털에서 조직에 Azure에 구독을 추가 합니다.  <br/> |Office 365 포털에서 조직에 Intune/EMS 구독을 추가 합니다.  <br/> |Office 365 포털에서 조직에 Dynamics 365 구독을 추가 합니다.  <br/> |
|**Azure** <br/> |조직에 Office 365 구독을 추가 합니다.  <br/> |해당 없음  <br/> |조직에 Intune/EMS 구독을 추가 합니다.  <br/> |조직에 Dynamics 365 구독을 추가 합니다.  <br/> |
|**Intune/EMS** <br/> |조직에 Office 365 구독을 추가 합니다.  <br/> |Azure 포털에서 조직에 Azure에 구독을 추가 합니다.  <br/> |해당 없음  <br/> |조직에 Dynamics 365 구독을 추가 합니다.  <br/> |
|**Dynamics 365** <br/> |조직에 Office 365 구독을 추가 합니다.  <br/> |Azure 포털에서 조직에 Azure에 구독을 추가 합니다.  <br/> |조직에 Intune/EMS 구독을 추가 합니다.  <br/> |해당 없음  <br/> |
   
Office 365 관리 센터를 통해 Microsoft SaaS 기반 서비스에 대 한 조직에 구독을 추가 하는 간편한 방법이 됩니다.
  
1. 전역 관리자 계정과 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 한 다음 **관리**를 클릭 합니다.
    
2. **관리 센터** 홈페이지의 왼쪽된 탐색 모음에서 **대금 청구**및 **구매 서비스**를 클릭 합니다.
    
3. **구매 서비스** 페이지에서 새 구독을 구입 합니다.
    
Office 365 관리 센터 SaaS 기반 클라우드 서비스에 대 한 새 등록에 조직 및 Office 365 구독 Azure AD 테 넌 트를 할당합니다.
  
Office 365 구독으로 Azure AD 테 넌 트와 같은 조직에 Azure 구독을 추가:
  
1. Office 365 전역 관리자 계정 사용 하 여 Azure 포털 ([https://portal.azure.com](https://portal.azure.com))에 로그인 합니다.
    
2. 왼쪽 탐색 영역에서 **구독**을 클릭 하 고 **추가**클릭 합니다.
    
3. **추가 구독** 페이지에서 제공 하는 서비스를 선택 하 고 지불 정보 및 계약을 완료 합니다.
    
Azure 및 Office 365 구독을 별도로 구입 하 고 Azure 구독에서 Office 365 Azure AD 테 넌 트에 액세스 하는 경우 [는 Office 365 테 넌 트 Azure에 가입 연결](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)의 지침을 참조 합니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[하이브리드 솔루션](hybrid-solutions.md)
  
[구독, 라이선스 및 Contoso Corporation에 대 한 사용자 계정](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



