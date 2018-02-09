---
title: "중요 한 기밀 사항이 자산에 대 한 SharePoint Online 팀 사이트 보호"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "요약: Contoso 중요 한 보호 및 기밀 사항이 SharePoint Online 팀 사이트에 대 한 더 쉽게을 구현 하는 방법 아직 보안 임원 및 해당 연구 (영문)에 대 한 공동 작업 가운데에 맞춥니다."
ms.openlocfilehash: c615280d39117f68515fb13d4ba83428d73e4fd3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a>중요 한 기밀 사항이 자산에 대 한 SharePoint Online 팀 사이트 보호

 **요약:** 어떻게 구현 Contoso 중요 한 보호 및 기밀 사항이 SharePoint Online 팀 임원 및 해당 하는 리서치 센터에 대 한 보안 하면서도 쉽게, 공동 작업을 위한 사이트입니다.
  
Contoso의 임원진 Office 365를 사용 하 고 임원 저장할 수에 관계 없이 공동 작업에 대 한 단일 위치에서 해당 파일을 저장 하려고 합니다. 마찬가지로, Contoso의 연구 부서-파리, 모스크바, 뉴욕, 베이징, 및 Bangalore 부서와-팀 간에 쉽게 액세스 하 고 더 개방 공동 작업에 대 한 클라우드로의 온-프레미스 디지털 자산을 전환 해야 합니다.
  
그러나 두이 경우 모두에서 이러한 리소스에 대 한 액세스를 보거나, IT 담당자가 관리 하는 사이트에 대 한 지속적인 사용 권한으로 변경할 수 있는 사용자의 하위 집합으로 제한 이어야 합니다. 또한 일부 자원은 실수로 또는 의도적으로 하는 경우에, 분산 암호화 해야 하며 보거나 해당 내용을 변경 하려면 액세스 권한이 없는 사용자에 게를 방지 하기 위해 사용 권한이.
  
Contoso의 보안 및 SharePoint 관리자의 IT 부서 중요 한 보호 하 고 매우 기밀 SharePoint Online 팀 사이트를 사용 하 여 그림 1에 표시 된 것과 같이 합니다.
  
**중요 한 보호 및 기밀 사항이 SharePoint Online 팀 사이트의 그림 1: 비교**

![중요한 보호 및 높은 수준의 기밀 SharePoint Online 팀 사이트](images/Contoso_Poster/SP_Solution.png)
  
자신의 임원 및 팀이 연구 (영문)에 대 한 보안 SharePoint Online 팀 사이트를 만들려면 다음이 단계를 사용 하는 Contoso 합니다.
  
1. **임원** 중요 한 SharePoint Online 팀 사이트 만들기
    
    새 팀 사이트 편집 SharePoint 사용 권한 수준 및 SharePoint 관리자 계정의 작은 집합을 사용 하 여 모든 권한 권한 수준 가진 소유자로 구성원으로 중역에 대 한 기존 Azure Active Directory (AD) 그룹을 사용합니다.
    
2. 임원 파일 마이그레이션
    
    새 임원 SharePoint Online 팀 사이트에 기존 온-프레미스 임원 파일 및 폴더를 이동 합니다.
    
3. **리서치** 기밀 사항이 SharePoint Online 팀 사이트 만들기
    
    새 팀 사이트의 모든 권한 권한 수준 가진 소유자로 편집 사용 권한 수준 및 SharePoint 관리자 계정의 작은 집합을 사용 하 여 구성원으로 Azure AD 연구 팀 그룹을 기존를 사용합니다. 파일 연구에 할당 하는 AIP 레이블 하면 암호화 된 연구 (영문) 그룹의 구성원만 열 수 있습니다.
    
4. 리서치 파일 마이그레이션
    
    연구 팀이 기존 온-프레미스 파일 및 폴더를 새 리서치 SharePoint Online 팀 사이트를 이동 합니다.
    
결과 두 공동 작업 사이트 액세스 보안 및 SharePoint 관리자에 의해 제어 조밀 하 게 됩니다. 기밀 AIP 매우 레이블이 있는 파일에 대 한 리서치 팀 사이트 외부 배포 되는 경우에 이러한 암호화 되 고 연구 팀 구성원에 의해 열 수 있습니다.
  
자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)참조 하십시오.
  
 데모, 개념 증명 또는 개발/테스트 하면이 설정, [개발/테스트 환경에서 SharePoint Online 보안 사이트](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)를 참조 합니다.
  
## <a name="see-also"></a>참고 항목

[Contoso Corporation에 대 한 엔터프라이즈 시나리오](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft 클라우드의 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[데이터베이스를 늘이기](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)




