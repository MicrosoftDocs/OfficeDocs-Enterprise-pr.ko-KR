---
title: "격리 된 SharePoint Online 팀 사이트를 디자인 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "격리 된 SharePoint Online 팀 사이트에 대 한 디자인 프로세스를 통해 요약: 단계입니다."
ms.openlocfilehash: efd55ce780cf2951bfafd31215201459965c0e78
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>격리 된 SharePoint Online 팀 사이트를 디자인 합니다.

 **요약:** 격리 된 SharePoint Online 팀 사이트에 대 한 디자인 프로세스를 단계별로 실행 합니다.
  
이 문서는 격리 된 SharePoint Online 팀 사이트를 만들기 전에 내려야 주요 디자인 결정을 안내 합니다.
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>1 단계: SharePoint 그룹 및 권한 수준 결정

기본적으로 모든 SharePoint Online 팀 사이트는 다음과 같은 SharePoint 그룹을 사용 하 여 만든은:
  
- \<사이트 이름 > 구성원
    
- \<사이트 이름 > 방문자
    
- \<사이트 이름 > 소유자
    
이러한 그룹은 Office 365 및 Azure Active Directory (AD) 그룹에서 별도 하며 사이트의 리소스에 대 한 사용 권한을 할당 하는 것에 대 한 기초입니다.
  
사이트에서 수행 하는 SharePoint 그룹의 구성원 수를 결정 하는 특정 사용 권한 집합 사용 권한 수준입니다. 기본적으로 SharePoint Online 팀 사이트에 대 한 사용 권한 수준이 세: 편집, 읽기 및 모든 권한입니다. 다음 표에서 SharePoint 그룹 및 할당 된 사용 권한 수준을의 기본 상관 관계를 보여줍니다.
  
|**SharePoint 그룹**|**사용 권한 수준**|
|:-----|:-----|
|\<사이트 이름 > 구성원  <br/> |편집  <br/> |
|\<사이트 이름 > 방문자  <br/> |읽기  <br/> |
|\<사이트 이름 > 소유자  <br/> |모든 권한  <br/> |
   
 **모범 사례:** 추가 SharePoint 그룹 및 권한 수준을 만들 수 있습니다. 격리 된 SharePoint Online 사이트에 대 한 기본 SharePoint 그룹 및 권한 수준을 사용 하는 것이 좋습니다.
  
다음은 기본 SharePoint 그룹 및 권한 수준입니다.
  
![SharePoint Online 사이트에 대한 기본 SharePoint 그룹 및 사용 권한 수준입니다.](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>2 단계: 액세스 그룹과 사용자에 게 사용 권한 할당

자신의 사용자 계정 또는 Office 365 또는 Azure AD 그룹은 사용자 계정이 SharePoint 그룹에 구성원을 추가 하 여 사용자에 게 사용 권한을 할당할 수 있습니다. 추가 되 면 Office 365 사용자 계정 하거나 직접 또는 간접적으로 Office 365 또는 Azure AD 그룹의 구성원 자격을 통해, SharePoint 그룹에 연결 된 사용 권한 수준에 할당 됩니다.
  
기본 SharePoint 그룹을 예로 사용:
  
- 구성원은 ** \<사이트 이름 > 구성원** 모두 사용자 계정 및 그룹을 포함할 수 있는 SharePoint 그룹 **편집** 사용 권한 수준에 할당 된
    
- 구성원은 ** \<사이트 이름 > 방문자** 모두 사용자 계정 및 그룹을 포함할 수 있는 SharePoint 그룹에 **읽기** 권한 수준에 할당 된
    
- 구성원은 ** \<사이트 이름 > 소유자** 모두 사용자 계정 및 그룹을 포함할 수 있는 SharePoint 그룹에 **모든 권한** 사용 권한 수준에 할당 된
    
 **모범 사례:** 개별 사용자 계정을 통해 사용 권한을 관리할 수는 있지만 단일을 사용 하는 것이 좋습니다 Azure AD 그룹에서 액세스 하는 그룹을 대신 라고 합니다. 각 SharePoint 그룹에 대 한 계정 사용자의 목록을 관리 하지 않고 액세스 그룹의 구성원 자격을 통해 사용 권한 관리가 간편해 집니다.
  
Office 365 용 azure AD 그룹 Office 365 그룹 보다 서로 다릅니다. Azure AD 그룹 **보안** 로 해당 **형식** 을 설정 하 여 Office 관리 센터에 표시 하 고 전자 메일 주소를 갖지 않습니다. Azure AD 그룹 내에서 관리할 수 있습니다.
  
- Windows Server Active Directory (AD)
    
    다음은 온-프레미스 Windows Server AD 인프라에서 만든 및 Office 365 구독에 동기화 된 그룹입니다. Office 관리 센터에서 이러한 그룹 **Synched active directory와**의 **상태** 를 가집니다.
    
- Office 365
    
    다음은 Office 관리 센터, Azure 포털 또는 Microsoft PowerShell 중 하나를 사용 하 여 만든 그룹입니다. Office 관리 센터에서 이러한 그룹 **클라우드**의 **상태** 를 가집니다.
    
 **모범 사례:** Windows Server AD 온-프레미스를 사용 하 여 Office 365 구독와 동기화 하는 경우 사용자 및 Windows Server AD와 함께 그룹 관리를 수행 합니다.
  
격리 된 SharePoint Online 팀 사이트, 권장된 그룹 구조는 다음과 같습니다.
  
|**SharePoint 그룹**|**Azure AD 기반 액세스 그룹**|**사용 권한 수준**|
|:-----|:-----|:-----|
|\<사이트 이름 > 구성원  <br/> |\<사이트 이름 > 구성원  <br/> |편집  <br/> |
|\<사이트 이름 > 방문자  <br/> |\<사이트 이름 > 뷰어  <br/> |읽기  <br/> |
|\<사이트 이름 > 소유자  <br/> |\<사이트 이름 > 관리자  <br/> |모든 권한  <br/> |
   
 **모범 사례:** SharePoint 그룹의 구성원으로 Office 365 또는 Azure AD 그룹을 사용할 수 있지만 Azure AD 그룹을 사용 하는 것이 좋습니다. Azure AD 그룹, Windows Server AD 또는 Office 365를 통해 관리 되는 사용 권한을 할당 하려면 중첩 된 그룹을 사용 하 여 더 큰 유연성을 제공 합니다.
  
다음은 기본 SharePoint 그룹 Azure AD 기반 액세스 그룹을 사용 하도록 구성 합니다.
  
![기본 SharePoint Online 사이트 그룹의 구성원으로 액세스 그룹을 사용합니다.](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
세 액세스 그룹을 디자인할 때 다음 사항에 유의 해야 합니다.
  
- 일부 구성원만 있어야는 ** \<사이트 이름 > Admins** 액세스 그룹에서 해당 하는 소수의 팀 사이트를 관리 하는 SharePoint Online 관리자입니다.
    
- 대부분의 사이트 구성원은 ** \<사이트 이름 > 구성원** 또는 ** \<사이트 이름 > 뷰어** 그룹에 액세스 합니다. 때문에 사이트의 구성원은 ** \<사이트 이름 > 구성원** 액세스 그룹을 삭제 하거나 사이트의 리소스를 수정, 신중 하 게 해당 구성원을 고려 하는 기능이 있습니다. 확실에 있을 때 사이트 구성원을 추가할는 ** \<사이트 이름 > 뷰어** 액세스 그룹입니다.
    
SharePoint 그룹 및 ProjectX 라는 격리 된 사이트에 대 한 액세스 그룹의 예는 다음과 같습니다.
  
![SharePoint Online 사이트인 ProjectX의 액세스 그룹을 사용한 예입니다.](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a>3 단계: 사용 하 여 중첩 된 Azure AD 그룹

사용자 수가 적은 에서만, 프로젝트 사이트의 SharePoint 그룹에 추가 하는 Azure AD 기반 액세스 그룹의 한 수준 대부분의 시나리오 적합 합니다. 그러나 많은 수의 사용자와 해당 사용자를 포함 하는 경우 이미의 구성원 설정 Azure AD 그룹 보다 쉽게 권한을 할당할 수 있습니다 SharePoint 중첩 된 그룹 또는 다른 그룹 구성원으로 포함 된 그룹을 사용 하 여 합니다.
  
판매, 마케팅, 엔지니어링, 법률의 중역 간의 공동 작업을 위한 격리 된 SharePoint online 팀 사이트 만들기 및 지원 부서 및 해당 부서 이미 임원 사용자 계정 사용 하 여 자신의 그룹 하려는 예 구성원 이어야 합니다. 새 사이트 구성원에 대 한 새 그룹을 만들고 모든 임원 개별 사용자 계정에 배치 하는 대신 각 부서에 대 한 기존 임원 그룹 새 그룹에 배치 합니다.
  
 여러 조직 간에 Office 365 구독을 공유 하는 경우에 조직에 대 한 사이트를 격리에 대 한 그룹 구성원 자격의 단일 수준을 많은 수의 사용자 계정으로 인해 관리 하기가 어려울 될 수 있습니다. 사용할 수는 경우에 사용 권한을 관리 하는 조직 내에서 그룹을 포함 하는 각 조직에 대 한 Azure AD 그룹을 중첩 합니다.
  
사용 하 여 중첩 된 Azure AD 그룹:
  
1. 식별 하거나 사용자 계정이 포함 되며 해당 하는 사용자 계정을 구성원으로 추가 하는 Azure AD 그룹을 만듭니다.
    
2. 다른 Azure AD 그룹 포함 되며 해당 그룹 구성원으로 추가 하는 컨테이너 Azure AD 기반 액세스 그룹을 만듭니다.
    
3.  SharePoint 그룹 및 해당 사용 권한 수준을 식별 하는 적절 한 컨테이너 액세스 그룹에 대 한 액세스 수준을, 합니다.
    
> [!NOTE]
> 중첩 된 Office 365 그룹을 사용할 수 없습니다. 
  
중첩 된 Azure AD의 예가 ProjectX 멤버 액세스 그룹에 대 한 그룹과 다음과 같습니다.
  
![ProjectX 사이트의 구성원 액세스 그룹에 대해 중첩 액세스 그룹을 사용한 예입니다.](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
잠재 고객 연구 (영문), 엔지니어링 및 프로젝트에 사용자 계정을 모두 하기 때문에 팀 사이트 구성원이 될 하기 위한 것, 자신의 Azure AD 그룹 ProjectX 멤버 액세스 그룹을 추가 하면 더 쉽습니다.
  
## <a name="next-step"></a>다음 단계

만들고 프로덕션 환경에서 격리 된 사이트를 구성 준비가 되 면 [SharePoint Online 팀 사이트를 격리 된 배포](deploy-an-isolated-sharepoint-online-team-site.md)를 참조 합니다.
  
## <a name="see-also"></a>참고 항목

[격리 된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-sites.md)
  
[SharePoint Online 팀 사이트를 격리 관리](manage-an-isolated-sharepoint-online-team-site.md)
  
[보안 솔루션](security-solutions.md)

[SharePoint Online 팀 사이트를 격리를 배포 합니다.](deploy-an-isolated-sharepoint-online-team-site.md)



