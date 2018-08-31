---
title: Exchange 2010 끝날 지원 로드맵
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 지원 거의 끝났습니다. 로드맵을 사용 하 여이 계획 가이드로 Exchange Online 또는 Exchange Server 온-프레미스의 최신 버전으로 업그레이드 하기 위한 준비 합니다.
ms.openlocfilehash: e655edcc38723acd622fc6abc62a00d3f3e36738
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915193"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 끝날 지원 로드맵

**2020 년 1 월 14**Exchange Server 2010 지원 종료에 도달 합니다. Office 365로 Exchange 2010 또는 Exchange 2016에서 마이그레이션을 시작한 이미 하지 않은 경우 지금 계획 수립 시작 시간을 됩니다. 
  
## <a name="what-does-end-of-support-mean"></a>지원 의미의 역할 끝 무엇입니까?

Exchange Server 같은 거의 모든 Microsoft 제품의 새로운 기능, 버그 수정, 보안 픽스 등에 제공 하는 동안 지원 주기를 있습니다. 이 수명 주기는 일반적으로 제품의 초기 릴리스 날짜 로부터 10 년 동안 지속 하 고이 주기 끝이 제품의 지원 종료 라고 합니다. Exchange 2010 2020, 년 1 월 14에서 지원의 끝에 도달 하면 Microsoft 제공 하지 않습니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원
    
- 검색 되는 및 안정성과 서버;의 유용성 영향을 줄 수 있는 문제에 대 한 버그 수정
    
- 검색 되는 하 고 서버를 공격에 취약 한 보안 위반 행위에 만들 수 있는 취약점에 대 한 보안 수정
    
- 표준 시간대를 업데이트합니다.
    
Exchange 2010의 설치 계속이 날짜 이후에 실행 됩니다. 그러나 위에 나열 된 변경으로 인해 좋습니다 마이그레이션하는 Exchange 2010에서 가능한 한 빨리.
  
Office 2010 서버 지원 종료를 거의 가득 차지 하는 방법에 대 한 자세한 내용은 [2010 서버와 클라이언트가 Office에서 업그레이드 하는데 도움이 되는 리소스](upgrade-from-office-2010-servers-and-products.md)를 참조 합니다.
  
## <a name="what-are-my-options"></a>내 옵션은 무엇입니까?

지원의 끝에 도달 Exchange 2010을 사용 하 여 옵션을 탐색 하 고 마이그레이션 계획을 준비 하는 훌륭한 시간입니다. 당신은 할 수 있어요:
  
- 하이브리드 마이그레이션; 또는 단독형, express를 사용 하 여 Office 365로 마이그레이션 
    
- 온-프레미스 서버에 최신 버전의 Exchange Exchange 2010 서버를 마이그레이션하십시오.
    
다음 섹션에서는 각 옵션을에 대 한 자세한 정보를 살펴봅니다.
  
### <a name="migrate-to-office-365"></a>Office 365로 마이그레이션

Office 365로 전자 메일 마이그레이션에 가장 하 고 이해 하기 쉬운 하는 옵션은 Exchange 2010 배포 사용을 중지 하는 데 도움이 됩니다. Office 365로의 마이그레이션와 같은 최신 기능에 오래 된 기술에서 단일 홉을 지정할 수 있습니다.
  
- 예: 보존 정책, 전체 및 소송 보존, 규정 준수 기능 전체 eDiscovery 등입니다.
    
- Microsoft 팀의;
    
- Power BI;
    
- 포커스가 받은 편지함;
    
- 분석; 굴
    
- 전자 메일, 일정, 연락처 및 등을 프로그래밍 방식 액세스를 위한 REST Api입니다.
    
Office 365도 새로운 기능 및 경험 첫번째를 가져오고 사용자와 함께 수 일반적으로 사용을 시작 귀하가 합니다. 새로운 기능 외에도 대 한 걱정 필요가 없습니다.
  
- 구입 및 하드웨어; 유지 관리
    
- 난방 및 서버; 냉각에 대 한 요금을 지불
    
- 보안, 제품 및 표준 시간대 픽스;에 최신 상태로 유지
    
- 저장소 및 규정 준수 요구 사항을;를 지원 하기 위한 소프트웨어 유지 관리
    
- 업그레이드를 새 버전의 Exchange-없이 이동 중일 항상 최신 버전의 Office 365의 Exchange 합니다.
    
#### <a name="how-should-i-migrate-to-office-365"></a>Office 365로 마이그레이션해야 합니다.는 방법

조직에 따라서는 몇 옵션 Office 365를 격리할 수 있습니다. 수 제공할 때 또는 이동 하는 사서함,으로 마이그레이션에 마지막으로, 원하는 기간 및 온-프레미스 설치 및 하는 동안 Office 365 간의 원활 하 게 통합 해야 하는지 여부와 같은 몇가지 사항을 고려해 야 하는 마이그레이션 옵션을 선택 하는 경우 마이그레이션입니다. 이 표에서 사용자가 마이그레이션 옵션 및 사용 방법을 결정 하는 가장 중요 한 요소를 보여줍니다.
  
|**마이그레이션 옵션**|**조직 크기**|**기간**|
|:-----|:-----|:-----|
|단독형 마이그레이션  <br/> |미만의 150 시트  <br/> |한 주 이내  <br/> |
|빠른 마이그레이션  <br/> |미만의 150 시트  <br/> |2 주 이내  <br/> |
|전체 하이브리드 마이그레이션  <br/> |150 개 이상의 시트  <br/> |몇 주 이상  <br/> |
   
다음 섹션에서는 이러한 방법에 대 한 개요를 제공합니다. [마이그레이션 경로 결정](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) 각 방법의 세부 정보를 확인할 수 있습니다. 
  
#### <a name="cutover-migration"></a>단독형 마이그레이션

단독형 마이그레이션 하나 페이지인 미리 선택 된 날짜 및 시간을 수를 마이그레이션하는 모든 사서함, 메일 그룹, 연락처 및 등을 Office 365; 모든 작업이 끝난 후에 있습니다 하겠습니다 온-프레미스 Exchange 서버를 종료 하 고 Office 365를 단독으로 사용 하 여 시작 합니다.
  
단독형 마이그레이션 메서드는 매우 많은 사서함을 설치 하지 않은 소규모 조직의 신속 하 게 Office 365로 가져올 하 고 일부는 다른 방법은의 복잡성을 처리 하지 않으려고 뛰어난 해야 합니다. 하지만 것도 다소 제한 한 주에 완료 해야 하기 때문에 있고 사용자를 자신의 Outlook 프로필을 다시 구성 해야 하기 때문에 있습니다. 단독형 마이그레이션 최대 2, 000 개에서 처리할 수 있는 하는 동안이 메서드와 함께 최대 150 사서함을 마이그레이션하는 것이 좋습니다. 150 개 이상의 사서함 마이그레이션 하려고 하면에 마감 하기 전에 모든 사서함을 전송 하는 시간에서 실행할 수 있습니다 하 고 IT 지원 담당자 나타날 수 너무 돕는 경우 사용자가 Outlook을 다시 구성 합니다.
  
단독형 마이그레이션을 수행 하는 방법에 대 한 생각을 하는 경우 다음은 생각 하는 몇가지 사항을 고려해 야 합니다.
  
- Office 365 TCP 포트 443;을 통해 외부에서 Outlook 사용을 사용 하 여 Exchange 2010 서버에 연결 해야 합니다.
    
- Office 365;로 모든 온-프레미스 사서함을 이동할
    
- 사용자의 사서함;의 콘텐츠를 읽을 수 있는 권한이 있는 온-프레미스 관리자 계정이 필요 합니다.
    
- Exchange 2010을 사용 하 여 Office 365 필요 서비스;에서 확인 된 도메인으로 추가 하려는 도메인을 허용
    
- 마이그레이션을 시작 하면 시간 사이 및 Office 365 및 온-프레미스 사서함 Office 365가 정기적으로 동기화 완료 단계를 시작 하는 경우 합니다. 이렇게 하면가 온-프레미스 사서함;에 남아 있는 전자 메일에 대 한 걱정 없이 마이그레이션 완료
    
- 사용자가 처음으로;에 대 한 각자의 사서함에 로그인 할 때 변경 하는데 필요한 해당 Office 365 계정의 새 임시 암호를 받게 됩니다.
    
- 마이그레이션할 각 사용자 사서함에 대 한 Exchange Online을 포함 하는 Office 365 라이선스가 필요 합니다.
    
- 사용자가 각각의 해당 장치에 새 Outlook 프로필을 설정 하 고 전자 메일을 다시 다운로드 해야 합니다. Outlook를 다운로드 하는 전자 메일의 양을 달라질 수 있습니다. 자세한 내용은 [오프 라인으로 유지 하려면 얼마나 많은 메일 변경](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)에 대 한 정보를 수행 합니다.
    
단독형 마이그레이션에 대 한 자세한 내용은,에 대 한 정보를 수행 합니다.
  
- [Office 365에 단독 전자 메일 마이그레이션에 대해 알고 하는데 필요한](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [전자 메일을 Office 365의 단독형 마이그레이션 수행](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="express-migration"></a>빠른 마이그레이션

Express 마이그레이션의 몇 백 사서함을 Office 365로 마이그레이션할 하 마이그레이션 2 주 내에 완료할 수 및 약속 있음/없음 일정 정보 공유와 같은 고급 하이브리드 마이그레이션 기능 중 하나 필요는 없습니다 하는 하나입니다.
  
Express 마이그레이션은를 자신의 사서함을 Office 365 마이그레이션 하지만 여전히 2 주 내에서 마이그레이션을 완료 하려면 더 많은 시간을 수행 해야 하는 조직에 적합 합니다. 복잡 한 문제 없이 고급 전체 하이브리드 마이그레이션의 일부 이점을 얻을 수 있습니다. 및 해당, 수, 사서함을 제어할 수 있습니다, 지정된 된 시간에 마이그레이션됩니다 사용자 이름 및 해당 온-프레미스 계정의 암호 사용 하 여 office 365 사서함을 만들어집니다. 및 단독형 마이그레이션와는 달리 사용자가 자신의 Outlook 프로필을 다시 필요 하지 않은 합니다.
  
미리 구성 된 마이그레이션을 수행 하는 방법에 대 한 생각 하면 몇가지 사항을 고려해 야 다음과 같습니다.
  
- Office 365 TCP 포트 443;을 통해 외부에서 Outlook 사용을 사용 하 여 Exchange 2010 서버에 연결 해야 합니다.
    
- 온-프레미스 Active Directory 서버와 Office 365; 간의 일회성 디렉터리 동기화를 수행 해야 합니다.
    
- 사용자가 동일한 사용자 이름 및 해당 사서함이 마이그레이션된; 때 사용한 암호를 사용 하 여 Office 365 사서함에 로그인 할 수 있습니다.
    
- 마이그레이션할 각 사용자 사서함에 대 한 Exchange Online을 포함 하는 Office 365 라이선스가 필요 합니다.
    
- 사용자 (오래 된 일부 Android 전화 새 프로필이 필요할) 해당 장치에는 대부분에 새 Outlook 프로필을 설정할 필요가 없습니다 하 고 다시 전자 메일을 다운로드 하려면 필요 하지 않습니다.
    
미리 구성 된 마이그레이션에 대 한 자세한 내용은 [신속 하 게 Office 365로 Exchange 사서함을 마이그레이션할 최소한의 하이브리드 사용에](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef) 대 한 정보를 수행 합니다.
  
#### <a name="full-hybrid"></a>전체 하이브리드

전체 하이브리드 마이그레이션에는 조직에 매우 많은 수의 사서함의 최대 수백, Office 365를 일부 또는 전부를 이동 하려는 장소와 하나입니다. 이러한 마이그레이션이 일반적으로 장기적인 이기 때문에 하이브리드 마이그레이션 수 있도록 합니다.
  
- Office 365의 온-프레미스 사용자가 사용자에 대 한 약속 있음/없음 일정 정보를 표시 하 고 그 반대의 경우도 마찬가지입니다.
    
- 온-프레미스 및 Office 365; 모두에서 받는 사람을 포함 하는 통합된 전체 주소 목록을 참조 하십시오.
    
- Office 365; 또는 온-프레미스 있는지 여부에 관계 없이 모든 사용자에 대 한 전체 Outlook 받는 사람 카드 보기
    
- 온-프레미스 Exchange 서버와 TLS 및 인증서;를 사용 하 여 Office 365 간의 전자 메일 보안 통신
    
- 수 있도록 internal로 온-프레미스 Exchange 서버와 Office 365 간에 보낸 메시지를 처리 합니다.
    
  - 제대로 평가 하 고 내부 메시지;를 대상으로 전송 및 규정 준수 에이전트에 의해 처리
    
  - 스팸 방지 필터를 통과 합니다.
    
전체 하이브리드 마이그레이션은 몇 개월 이상에 대해 하이브리드 구성에서 상태를 유지 하려면 것으로 예상 하는 조직에 가장 적합 합니다. 온라인 사서함 이동이를 사용 하 여이 섹션에서는 및 디렉터리 동기화, 더 나은 통합 된 규정 준수 기능 및 Office 365에서 사서함을 이동 하는 기능 앞부분에서 설명한 기능 얻을 수 있습니다. Office 365의 온-프레미스 조직 확장 됩니다.
  
전체 하이브리드 마이그레이션을 수행 하는 방법에 대 한 생각 하면 몇가지 사항을 고려해 야 다음과 같습니다.
  
- 전체 하이브리드 마이그레이션은 모든 유형의 조직에 적합 하지 않습니다. 전체 하이브리드 마이그레이션의 복잡성으로 인해 보다 작은 몇 백 사서함이 있는 조직에서는 작업량 및 비용 하나를 설정 하는 데 필요한 justify 혜택을 일반적으로 표시 되지 않습니다. 조직 처럼 소리이 하는 경우 라우팅하는 대신; Cutover 또는 미리 구성 된 마이그레이션을 고려 하는
    
- Office 365 TCP 포트 443;을 통해 외부에서 Outlook 사용을 사용 하는 Exchange 2010 서버에 연결 해야 합니다.
    
- Azure Active Directory에 연결 (AADConnect)를 사용 하 여 온-프레미스 Active Directory 서버와 Office 365; 간에 디렉터리 동기화를 설정 해야 합니다.
    
- 사용자는 동일한 사용자 이름 및 (Azure Active Directory 연결 암호 동기화 및/또는 Active Directory Federation Services와 필요)는 로컬 네트워크에 로그인 할 때 사용 하 여 암호를 사용 하 여 Office 365 사서함에 로그인 할 수 있게 됩니다.
    
- 마이그레이션할 각 사용자 사서함에 대 한 Exchange Online을 포함 하는 Office 365 라이선스가 필요 합니다.
    
- 사용자 (오래 된 일부 Android 전화 새 프로필이 필요할) 해당 장치에는 대부분에 새 Outlook 프로필을 설정할 필요가 없습니다 하 고 다시 전자 메일을 다운로드 하려면 필요 하지 않습니다.
    
적합 한 전체 하이브리드 마이그레이션 소리를, 수행 마이그레이션 도움이 되는 다음 리소스에 대 한 정보:
  
- [Exchange 배포 어시스턴트](https://aka.ms/exdeploy)
    
- [Exchange Server 하이브리드 배포](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [하이브리드 구성 마법사](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [하이브리드 구성 마법사 FAQ](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [하이브리드 배포 필수 구성 요소](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Exchange Server의 최신 버전으로 마이그레이션

강력 하 게 Office 365로 마이그레이션하는 방법으로 최상의 값 및 사용자 경험을 얻을 수 있는 하 라고 생각 되, 하는 동안는 또한 이해 일부 조직에서는 자신의 전자 메일 온-프레미스 유지 해야 합니다. 이 규정 요구 사항으로 인해 수, 데이터를 진행 하는 다른 국가, 이와 같은식으로에 있는 데이터 센터에 저장 되지 않습니다. 전자 메일에서 온-프레미스 유지 하려는 경우에 Exchange 2013 또는 Exchange 2016 Exchange 2010 환경을 마이그레이션할 수 있습니다.
  
Office 365로 마이그레이션할 수 없는 경우 Exchange 2016를 마이그레이션하는 것이 좋습니다. 모든 기능 및 이전 버전의 Exchange 포함 하는 고급 기능을 통해 Exchange 2016를 포함 하 고 (Office 365에만 사용할 수 있는 일부 기능 이지만) Office 365와 함께 사용할 수 있는 환경에서 가장 근접 하 게 일치 합니다. 제한 하면 했을 때 된 누락에이 문서는 몇을 확인해보세요.
  
|**Exchange 버전**|**기능**|
|:-----|:-----|
|Exchange 2013  <br/> | 세 서버 역할의 수를 줄이는 단순화 된 아키텍처 (사서함, 클라이언트 액세스, Edge 전송)  <br/>  데이터 손실 방지 정책 (DLP) 누수에서 중요 한 정보를 유지 하는  <br/>  크게 향상 된 Outlook Web App 환경  <br/> |
|Exchange 2016  <br/> | *Exchange 2013의 기능 및...*  <br/>  사서함 및 Edge 전송 방금 단순화 된 서버 역할 추가  <br/>  SharePoint와의 통합 함께 향상 된 DLP  <br/>  향상 된 데이터베이스 복구  <br/>  온라인 문서 공동 작업  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>마이그레이션해야 합니다. 버전

처음 가정 하면 Exchange 2016를 마이그레이션할지 하는 것이 좋습니다. 다음 가정이 확인 또는 Exchange 2016 발생 하지 않도록 하려면 다음 정보를 사용 합니다. 이유 중 하나 또는 다른 Exchange 2016를 마이그레이션할 수 없지만, 수행 같은 Exchange 2013을 처리 하 고 등입니다.
  
|**고려 사항**|**추가 정보**|
|:-----|:-----|
|지원 날짜의 끝  <br/> | Exchange 2010의 경우 다음과 같이 각 버전의 Exchange 지원 날짜의 끝을 있습니다.  <br/> **Exchange 2013** -년 4 월 2023  <br/> **Exchange 2016** -년 10 월 2025  <br/>  일찍 지원 날짜의 끝는 빠르게 다른 마이그레이션을 수행 하기 위해 필요 합니다. 4 월 2023은 생각 보다 훨씬 더 가깝게!<br/> |
|Exchange 2013 또는 2016에 대 한 마이그레이션 경로  <br/> |Exchange 2013으로 마이그레이션에 대 한 일반 단계는 다음과 같습니다.  <br/> 기존 Exchange 2010 조직 이동 서비스 및 Exchange 2013 또는 2016 이동 사서함을 다른 인프라 및 공용 폴더를 Exchange 2013 또는 2016 서비스 해제 남아 있는 Exchange 2010 서버에 Exchange 2013 또는 2016 설치 |
|버전 동시 사용  <br/> |Exchange 2013 또는 Exchange 2016으로 마이그레이션할 때 기존 Exchange 2010 조직에 두 버전을 설치할 수 있습니다. 이 옵션을 사용 하면 하나 이상의 Exchange 2013 또는 Exchange 2016 서버를 설치 하 고 마이그레이션을 수행할 수 있습니다.  <br/> |
|서버 하드웨어  <br/> | 서버 하드웨어 요구 사항 Exchange 2010에서 변경 되었습니다. 사용 하려는 하드웨어 호환 되는지 확인 해야 합니다. 여기에 각 버전에 대 한 하드웨어 요구 사항에 대 한 자세한 내용을 찾을 수 있습니다.<br/> [Exchange 2016 시스템 요구 사항](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 시스템 요구 사항](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/>  가 중요 한 Exchange 성능 향상는 컴퓨팅 향상 된 기능 및 새로운 서버에 저장 용량 가능성이 해야 같은 수의 사서함을 지원 하기 위해 적은 수의 서버를 찾을 수 있습니다.  <br/> |
|운영 체제 버전  <br/> | 각 버전에 대해 지원 되는 최소 운영 체제 버전 있습니다.  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/>  [Exchange 지원 가능성 행렬](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)에서 운영 체제 지원에 대 한 자세한 정보를 찾을 수 있습니다.  <br/> |
|Active Directory 포리스트 기능 수준  <br/> | 최소 지원 되는 Active Directory 포리스트 기능 수준 각 버전에 대 한 됩니다.  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/>  [Exchange 지원 가능성 행렬](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)에서 포리스트 기능 수준 지원에 대 한 자세한 정보를 찾을 수 있습니다.  <br/> |
|Office 클라이언트 버전  <br/> | 각 버전에 대 한 최소 지원 되는 Office 클라이언트 버전 있습니다.  <br/> **Exchange 2016** Office 2010 (최신 업데이트로)  <br/> **Exchange 2013** Office 2007 s p 3  <br/>  [Exchange 지원 가능성 행렬](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)에서 Office 클라이언트 지원에 대 한 자세한 정보를 찾을 수 있습니다.  <br/> |
   
#### <a name="how-do-i-migrate"></a>마이그레이션하는 방법은 무엇입니까?

전자 메일에서 온-프레미스를 유지 하려면 결정 하는 경우에 마이그레이션 도움이 되는 다음 리소스를 사용할 수 있습니다.
  
- [Exchange 배포 어시스턴트](https://aka.ms/exdeploy)
    
- Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx) 에 대 한 active Directory 스키마 변경 사항
    
- Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) 에 대 한 시스템 요구 사항
    
- Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx) 에 대 한 필수 구성 요소
    
## <a name="what-if-i-need-help"></a>경우에 어떻게 도움이 필요 합니까?

Office 365로 마이그레이션하는 경우,이 Microsoft FastTrack 서비스를 사용 하 여이 가능한 수도 있습니다. FastTrack 모범 사례, 도구 및 Office 365로 마이그레이션의 최대한 원활 하 게 확인 하는 리소스를 제공 합니다. 무엇 보다도, 계획에서 마이그레이션, 하면 안내 하 고 마지막 사서함에 이르는 모든 디자인 하는 실제 지원 엔지니어를 해야 합니다. FastTrack 하는 방법에 대 한 상세 [Microsoft FastTrack](https://fasttrack.microsoft.com/)에 대 한 정보를 수행 합니다.
  
실행 하면 모든 문제에 마이그레이션 하는 동안 Office 365로 하는 경우 FastTrack, 또는 Exchange Server의 최신 버전으로의 마이그레이션을 사용 하지 않는 것 도움이 필요 하세요. 다음은 일부 리소스를 사용할 수 있습니다.
  
- [기술 커뮤니티](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [고객 지원](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>관련 항목

[2010 서버와 클라이언트에서 Office를 업그레이드 하는데 도움이 되는 리소스](upgrade-from-office-2010-servers-and-products.md)
  
[Office 퇴직 그룹 (Microsoft 기술 커뮤니티)](https://go.microsoft.com/fwlink/?linkid=842065)
  

