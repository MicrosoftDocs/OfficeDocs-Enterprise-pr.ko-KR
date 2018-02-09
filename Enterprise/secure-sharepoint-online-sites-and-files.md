---
title: "SharePoint Online 사이트 및 파일의 보안"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "요약: SharePoint Online 및 Office 365에서 파일을 보호 하기 위해 구성 권장 합니다."
ms.openlocfilehash: 78e29b12bad2d9ba91524fecf4fa66b8729715ae
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>SharePoint Online 사이트 및 파일의 보안

 **요약:** SharePoint Online 및 Office 365에서 파일을 보호 하기 위해 구성 권장 사항입니다.
  
이 문서에서는 SharePoint Online 팀 사이트 및 공동 작업의 간편 하 게 균형잡힌 보안을 제공 하는 파일 보호를 구성 하기 위한 권장 사항을 제공 합니다. 이 문서에서는 가장 open 공유 정책 사용 하 여 조직 내에서 공용 사이트로 시작 하 여 4 개의 서로 다른 구성 정의 합니다. 각 추가 구성 보호를 의미 있는 단계를 나타냅니다 하지만 관련 된 사용자 집합에 액세스 하 고 리소스에 공동 작업을 수행 하는 기능 영역이 줄어듭니다. 시작 지점으로 이러한 지침을 사용 하 여 하 고 조정 하 여 조직의 요구 사항에 맞게 구성 합니다. 
  
이 문서에는 구성 데이터, id, 및 장치에 대 한 보호의 세 계층에 대 한 Microsoft의 권장 사항에 맞는:
  
- 초기 계획 보호
    
- 중요 한 보호
    
- 기밀 보호
    
이러한 계층 및 각 계층에 대 한 권장 하는 기능에 대 한 자세한 내용은 다음 리소스를 참조 합니다. 
  
- [Office 365용 ID 및 장치 보호](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Office 365의 파일 보호 솔루션](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>기능 개요 (영문)

SharePoint Online 팀 사이트에 대 한 권장 사항을 다양 한 Office 365 기능에 그립니다. 기밀 사항이 사이트에 대 한 Azure 정보 보호 기능을 사용 하는 것이 좋습니다. 엔터프라이즈 이동성 + 보안 (EMS)에 포함 됩니다. 
  
다음 그림에는 4 개의 SharePoint Online 팀 사이트에 대 한 권장된 구성을 보여줍니다.
  
![SharePoint 사이트에 대한 권장 구성](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
볼 수 있듯이:
  
- 초기 계획 보호 SharePoint Online 팀 사이트에 대 한 두 옵션을 포함-공용 사이트 및 개인 사이트입니다. 공용 사이트를 검색 하 고 조직에서 누구나 하 여 액세스할 수 있습니다. 개인 사이트 수만 검색 하 고 사이트의 구성원으로 액세스 합니다. 이러한 사이트 구성의 두 그룹 외부의 공유에 대 한 허용 합니다. 
    
- 중요 한 및 기밀 보호에 대 한 사이트는 특정 그룹의 구성원에만 제한 된 액세스 권한이 있는 개인 사이트입니다.
    
- Office 365 레이블 필요한 보호 수준 사용 하 여 데이터를 분류 하는 방법을 제공 합니다. 각 SharePoint Online 팀 사이트는 자동으로 레이블 문서 라이브러리의 파일 기본 레이블이 있는 사이트에 대 한 하도록 구성 됩니다. 에 해당 하는 4 개의 사이트 구성,이 예제의 레이블 되어 내부 공용, 개인, 민감한 기밀입니다. 사용자는 레이블을 변경할 수는 있지만이 구성 하면 모든 파일에는 기본 레이블 수신 합니다.
    
- 데이터 손실 방지 (DLP) 정책 경고 메시지를 표시 하거나 이러한 종류의 조직 외부의 파일 전송 하려고 할 때 사용자를 방지 하려면 및 높은 기밀 Office 365 구분 하지 않는 레이블에 대 한 구성 됩니다.
    
- 기밀 보호를 사용 하 여 구성 하는 사이트에 대 한 Azure 정보 보호 암호화 하 고 파일에 대 한 사용 권한을 부여 합니다.
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online 및 비즈니스용 OneDrive에 대 한 테 넌 트 수준 설정

SharePoint Online 및 비즈니스용 OneDrive 모든 사이트 및 사용자에 영향을 주는 테 넌 트 수준의 설정을 포함 합니다. 이러한 설정 중 일부를 보다 제한적인 사이트 수준 (있지만 작을 하지)에 조정할 수 있습니다. 이 섹션에서는 보안 및 공동 작업에 영향을 주는 테 넌 트 수준 설정에 설명 합니다. 
  
### <a name="sharing"></a>공유

이 솔루션에 대 한 다음 테 넌 트 수준의 설정을 것이 좋습니다.
  
- 기본 공유 정책을 모든 계정 유형, 익명 공유를 포함 하 여 모든 공유를 허용 하는 유지 합니다.
    
- 원하는 경우 만료 되 면에 대 한 익명 링크를 설정 합니다.
    
- 내부를 공유 하는 것에 대 한 기본 연결 종류를 변경 합니다. 이 조직 외부에 실수로 데이터 유출을 방지할 수 있습니다.
    
외부 공유를 허용 하도록 들릴 수, 하는 동안이 방법은 파일 공유 전자 메일에 파일 전송에 비해 보다 효율적으로 제어를 제공 합니다. SharePoint Online 및 Outlook 파일에 대해 보안 공동 작업을 위해 함께 작동 합니다. 
  
- 기본적으로 Outlook 전자 메일에 파일을 전송 하는 대신 파일에 대 한 링크를 공유 합니다. 
    
- SharePoint Online 및 비즈니스용 OneDrive 쉽게 내부와 조직 외부에 있는 참가자와 파일에 대 한 링크를 공유 하려면
    
외부 공유를 관리 하는데 컨트롤 수도 있습니다. 예, 다음을 수행할 수 있습니다.
  
- 익명 게스트 링크를 사용 하지 않도록 설정 합니다.
    
- 사이트에 대 한 사용자 액세스를 해지 합니다.
    
- 특정 사이트 또는 문서에 대 한 액세스 권한이 있는 사람을 참조 하십시오.
    
- 익명 공유 링크 (설정 테 넌 트) 만료를 설정 합니다.
    
- 조직 외부에 (설정 테 넌 트)를 공유할 수 있는 사람을 제한 합니다.
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>외부 공유 데이터 손실 방지 (DLP)와 함께 사용 하 여

외부 공유 하는 것이 없도록, 대체 도구 및 방법 비즈니스를 사용 하는 사용자를 찾을 수 필요 합니다. 중요 한 및 기밀 파일을 보호 하기 위해 DLP 정책을 사용 하 여 외부 공유를 결합 하는 것이 좋습니다.
  
### <a name="device-access-settings"></a>장치 액세스 설정

SharePoint Online 및 비즈니스용 OneDrive에 대 한 장치 액세스 설정을 통해 access 브라우저 전용으로 제한 되는지 확인 (파일을 다운로드할 수 없습니다.) 액세스를 차단 하는 경우 또는 합니다. 이러한 설정은 현재 최초 버전에 및 테 넌 트 수준을 적용 합니다. 사이트 수준에서 장치 액세스 정책을 구성 하는 기능을는 곧 제공 될 예정입니다. 이 솔루션에 대 한 하지 테 넌 트 수준에 적용 되는 장치 액세스 설정을 사용 하는 것이 좋습니다.
  
첫번째 릴리스에서 동안 장치 액세스 설정을 사용 하 여: [표준 또는 Office 365의 첫번째 릴리스 옵션을 설정](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)합니다.
  
### <a name="onedrive-for-business"></a>비즈니스용 OneDrive

비즈니스 사이트에 대 한 OneDrive에 대 한 기본 설정을 변경 하는 경우를 결정 하려면이 설정을 참고 하십시오. 현재, 공유 및 장치 액세스 설정 SharePoint Online 관리 센터에서 중복 생성 됩니다.와 환경 모두에 적용 합니다.
  
## <a name="sharepoint-team-site-configuration"></a>SharePoint 팀 사이트 구성

다음 표에서 각이 문서의 앞부분에서 설명한 팀 사이트에 대 한 구성을 요약 합니다. 시작 지점 권장 사항으로 이러한 구성을 사용 하 고 사이트 유형 및 구성 하 여 조직의 요구 사항에 맞게 조정 합니다. 모든 조직에서 모든 유형의 사이트 필요로 합니다. 소수의 조직의 기밀 보호가 필요합니다.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**초기 계획 보호 #1** <br/> |**초기 계획 보호 #2** <br/> |**중요 한 보호** <br/> |**기밀** <br/> |
|설명  <br/> |검색 및 조직 내에서 공동 작업을 엽니다.  <br/> |개인 사이트 및 공유 그룹 외부의 허용 되는 그룹입니다.  <br/> |특정 그룹 구성원에에서 의해 정의 되는 액세스 수준을 격리 된 사이트입니다. 사이트의 구성원에 게 공유는 사용할 수 있습니다. DLP 조직 외부의 파일을 보내려고 할 때 사용자에 게 경고 합니다.  <br/> |격리 된 사이트 + 파일 암호화 및 Azure 정보 보호를 사용 하 여 권한을 합니다. DLP 조직 외부의 파일을 전송 하는 것을 금지 합니다.  <br/> |
|공용 또는 개인 팀 사이트  <br/> |공용  <br/> |개인  <br/> |개인  <br/> |개인  <br/> |
|Access 사람은 누구 입니까?  <br/> |모든 대화 상대에 B2B 사용자와 게스트 사용자를 포함 하는 조직입니다.  <br/> |만 사이트의 구성원입니다. 다른 사용자에 게 액세스를 요청할 수 있습니다.  <br/> |만 사이트의 구성원입니다. 다른 사용자에 게 액세스를 요청할 수 있습니다.  <br/> |구성원에만 해당 합니다. 다른 사용자에 게 액세스 권한을 요청할 수는 없습니다.  <br/> |
|사이트 수준 공유 컨트롤  <br/> |누구나와 허용을 공유 합니다. 기본 설정 합니다.  <br/> |누구나와 허용을 공유 합니다. 기본 설정 합니다.  <br/> |구성원은 사이트에 대 한 액세스를 공유할 수 없습니다.  <br/> 비 구성원은 사이트에 대 한 액세스를 요청할 수 있지만 이러한 요청 할 경우 사이트 관리자가 반드시 필요 합니다.  <br/> |구성원은 사이트에 대 한 액세스를 공유할 수 없습니다.  <br/> 비 구성원 내용을 확인 하는 사이트에 대 한 액세스를 요청할 수 없습니다.  <br/> |
|사이트 수준 장치 액세스 제어  <br/> |없음 추가 컨트롤입니다.  <br/> |없음 추가 컨트롤입니다.  <br/> |사이트 수준 컨트롤은 곧 제공 될 예정, 사용자가 비준수 또는 비도메인 조인 된 장치에 파일을 다운로드할 수 없습니다. 이는 다른 모든 장치에서 브라우저에만 액세스할 수 있습니다.  <br/> |사이트 수준 컨트롤은 곧 제공 될 예정, 비준수 또는 비도메인 조인 된 장치에 파일의 다운로드를 차단 하는 합니다.  <br/> |
|Office 365 레이블  <br/> |내부 공용  <br/> |개인  <br/> |중요 한  <br/> |기밀  <br/> |
|DLP 정책  <br/> |||조직 외부의 대부분은 중요 하지도 레이블이 지정 된 파일을 보낼 때 사용자에 게 경고 합니다.  <br/> 신용 카드 번호 또는 기타 개인 데이터와 같은 중요 한 데이터 형식의 외부 공유를 차단 하려면 이러한 데이터 형식 (구성 하는 사용자 지정 데이터 형식을 포함)에 대 한 추가 DLP 정책을 구성할 수 있습니다.  <br/> |조직 외부의 같이 고도로 기밀 레이블이 지정 된 파일을 보낼 수 없도록 차단 합니다. 사용자가 사용 하 여 파일을 공유 하는 이러한 사용자를 포함 한 근거를 제공 하 여이 재정의 하도록 허용 합니다.  <br/> |
|Azure Information Protection  <br/> ||||Azure 정보 보호를 사용 하 여 자동으로 암호화 하 고 파일에 사용 권한을 부여 합니다. 자신이 유출 되는 경우이 보호 된 파일 이동 합니다.  <br/> Office 365 Azure 정보 보호를 사용 하 여 암호화 된 파일을 읽을 수 없습니다. 또한 DLP 정책 (레이블 포함) 메타 데이터를 포함 하지만 (예: 파일 내에서 신용 카드 번호) 이러한 파일의 내용이 아니라 포함 작동할 수 있습니다.  <br/> |
   
4 개의 서로 다른 유형의이 솔루션의 SharePoint Online 팀 사이트를 배포 하는 단계를 [보호의 세 계층에 대 한 배포 SharePoint Online 사이트](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)를 참조 하십시오. 개발/테스트 환경 만들기, [개발/테스트 환경에서 SharePoint Online 보안 사이트](secure-sharepoint-online-sites-in-a-dev-test-environment.md)를 참조 하는 단계입니다. 
  
## <a name="office-365-classification-and-labels"></a>Office 365 분류 및 레이블

Office 365 레이블을 사용 하 여 중요 한 데이터가 포함 된 환경에 대 한 것이 좋습니다. 하 고 나면 구성 하 고 Office 365 레이블을 게시 합니다.
  
- 해당 라이브러리의 모든 문서 기본 레이블을 받도록 기본 레이블 SharePoint Online 팀 사이트의 문서 라이브러리에 적용할 수 있습니다. 
    
- 적용할 수 있습니다 레이블 콘텐츠를 자동으로 특정 조건에 맞으면.
    
- Office 365 레이블을 기반으로 하는 DLP 정책을 적용할 수 있습니다.
    
- 조직의 사용자에 게 콘텐츠에 적용할 수 레이블을 수동으로 웹에서 Outlook에서 Outlook 2010 이상, 비즈니스, SharePoint Online 및 Office 365 그룹에 대 한 OneDrive 합니다. 사용자가 자주 알고 있는 가장 콘텐츠 유형은 사용 중인, 분류 하 고 적절 한 DLP 정책이 적용 된 수 있도록 합니다.
    
![SharePoint 사이트에 대한 권장 구성](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
볼 수 있듯이,이 솔루션은 다음 레이블 만들기 (영문)에 포함 됩니다.
  
- 기밀
    
- 중요 한
    
- 개인
    
- 내부 공용
    
이러한 레이블은 그림에서 권장 되는 사이트와이 문서의 앞부분에서 차트에 매핑됩니다. 이 솔루션의 대부분은 중요 하지과 매우 기밀로 표시 된 파일 누출 방지 하려면 DLP 정책을 구성 하는 것이 좋습니다.
  
이 솔루션에서 Office 365 레이블 및 DLP 정책을 구성 하는 단계를 [Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 보호 파일](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)을 참조 하십시오.
  
## <a name="azure-information-protection"></a>Azure Information Protection

Azure 정보 보호를 사용 하 여 레이블과 알립니다. 위치에 관계 없이 파일에 따라 보호를 적용 합니다. 이 솔루션에 대 한 암호화 하 고 가장 높은 수준의 보안으로 보호 하는 파일에 사용 권한을 부여 하는 범위가 지정 된 Azure 정보 보호 정책 및 기밀 사항이 레이블의 하위 레이블을 사용 하는 것이 좋습니다. 
  
Azure 정보 보호 암호화는 Office 365에 저장 된 파일에 적용 되 면 서비스 수 없는 이러한 파일의 내용을 처리할 수 있습니다. 공동 작성, eDiscovery, 검색, Delve, 및 기타 공동 작업 기능이 작동 하지 않습니다. DLP 정책 (Office 365 레이블을 포함) 메타 데이터 있지만 (예: 파일 내에서 신용 카드 번호) 이러한 파일의 내용이 아니라만 사용할 수 있습니다.
  
![Azure에서 Azure Information Protection을 구성하고 클라이언트 도구 모음에 레이블을 표시합니다.](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
볼 수 있듯이:
  
- Microsoft Azure 포털에서 Azure 정보 보호 정책 및 레이블을 구성합니다. 범위가 지정 된 Azure 정보 보호 정책의 하위 레이블을 구성 하는 것이 좋습니다.
    
- Azure 정보 보호를 Office 응용 프로그램의 **정보 보호** 막대로 표시를 표시합니다.
    
### <a name="adding-permissions-for-external-users"></a>외부 사용자에 대 한 사용 권한을 추가 (영문)

두 가지 방법으로 Azure 정보 보호를 사용 하 여 보호 된 파일에 대 한 액세스를 외부 사용자에 게 부여 합니다. 두이 경우 모두에서 외부 사용자에 게 Azure AD 계정이 있어야 합니다. 외부 사용자에 게 Azure AD를 사용 하는 조직 구성원 하지 않으면 이러한 얻을 수 Azure AD 계정을 개인으로이 등록 페이지를 사용 하 여: [https://aka.ms/aip-signup](https://aka.ms/aip-signup)합니다.
  
- 외부 사용자에 게 레이블에 대 한 보호를 구성 하는데 사용 되는 Azure AD 그룹 추가
    
     먼저 디렉터리의 B2B 사용자 계정을 추가 해야 합니다. [Azure 권한 관리 하 여 캐싱을 그룹 구성원](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)에 대 한 시간 정도 걸릴 수 있습니다. 이 메서드를 사용 하는 레이블 (짝수 보호 되는 파일 Azure AD 그룹에 사용자 추가 되기 전에)를 사용 하 여 보호 하는 모든 기존 파일 권한이 부여 됩니다.
    
- 외부 사용자에 게 레이블 보호에 직접 추가
    
     조직 (예: Fabrikam.com), (예: 조직 내에서 재무 그룹)는 Azure AD 그룹이 나 개별 사용자의 모든 사용자를 추가할 수 있습니다. 예, 레이블에 대 한 보호 조절기의 외부는 팀을 추가할 수 있습니다. 이 메서드를 사용 권한이 외부 엔터티 보호에 추가 된 후 레이블에 대해 보호 되는 파일에만 부여 됩니다.
    
### <a name="deploying-and-using-azure-information-protection"></a>배포 및 Azure 정보 보호를 사용 하 여

이 솔루션에 Azure 정보 보호를 구성 하는 단계를 [Azure 정보 보호와 SharePoint Online 보호 파일](protect-sharepoint-online-files-with-azure-information-protection.md)을 참조 하십시오.
  
## <a name="see-also"></a>참고 항목

[정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[보안 솔루션](security-solutions.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[개발/테스트 환경에서 SharePoint Online 사이트 보호](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



