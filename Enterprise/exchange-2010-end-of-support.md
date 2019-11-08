---
title: Exchange 2010 지원 로드맵 종료
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 09/16/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010는 지원 종료에 거의 도달 했습니다. 이 계획 로드맵을 사용 하 여 Exchange Online으로의 업그레이드를 준비 하거나 Exchange Server 온-프레미스의 새 버전으로 업그레이드할 수 있습니다.
ms.openlocfilehash: 28dcead19c1af1b5a641cae8f9d649b22fb36c95
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028832"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 지원 로드맵 종료

**2020 년 10 월 13 일**에 Exchange Server 2010은 지원 종료에 도달 합니다. 아직 Exchange 2010에서 Office 365 또는 Exchange 2016로의 마이그레이션을 시작한 적이 없는 경우에는 계획을 시작 하는 데 걸리는 시간입니다.

## <a name="what-does-end-of-support-mean"></a>지원이 끝나는 것은 무엇을 의미 하나요?

Exchange 서버에는 거의 모든 Microsoft 제품과 마찬가지로 새로운 기능, 버그 수정, 보안 픽스 등을 제공 하는 지원 주기가 있습니다. 일반적으로이 수명 주기는 제품 초기 릴리스 날짜 로부터 10 년 동안 지속 되며이 주기의 끝은 제품의 지원 종료 라고 합니다.
Exchange 2010가 2020 년 10 월 13 일에 지원 종료에 도달 하면 더 이상 다음이 제공 되지 않습니다.

- 발생할 수 있는 문제에 대 한 기술 지원
- 검색 된 문제와 서버의 안정성 및 유용성에 영향을 줄 수 있는 문제에 대 한 버그 수정
- 검색 되 고 서버에서 보안 위반에 취약 해질 수 있는 취약성에 대 한 보안 수정 사항
- 표준 시간대 업데이트

이 날짜 후에도 Exchange 2010 설치가 계속 실행 됩니다. 그러나 위에 나열 된 변경 사항으로 인해 가능한 한 빨리 Exchange 2010에서 마이그레이션하는 것이 좋습니다.

지원 종료에 가까운 Office 2010 서버에 대 한 자세한 내용은 [office 2010 서버 및 클라이언트에서 업그레이드 하는 데 도움이](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)되는 리소스를 참조 하십시오.

## <a name="what-are-my-options"></a>내 옵션 이란?

Exchange 2010이 지원 종료에 도달 하면이를 통해 옵션을 살펴보고 마이그레이션 계획을 준비할 수 있습니다. 다음을 수행할 수 있습니다.

- Office 365로 전체 마이그레이션을 완료 합니다. 가공선, 최소 하이브리드 또는 전체 하이브리드 마이그레이션을 사용 하 여 사서함을 마이그레이션한 다음 온-프레미스 Exchange 서버와 Active Directory를 제거 합니다.
- 온-프레미스 서버에서 exchange 2010 서버를 Exchange 2016로 마이그레이션합니다.

> [!IMPORTANT]
> 조직에서 사서함을 Office 365로 마이그레이션하도록 결정 하지만, 온-프레미스 Active Directory에서 사용자 계정을 계속 관리 하기 위해 DirSync 또는 Azure AD Connect를 유지 하려는 경우에는 하나 이상의 Exchange 서버를 온-프레미스로 유지 해야 합니다. 마지막 Exchange 서버를 제거 하는 경우 exchange Online에서 Exchange 받는 사람을 변경할 수 없게 됩니다. 이는 기관 원본이 온-프레미스 Active Directory에 남아 있으며 변경 해야 하기 때문입니다. 이 시나리오에서는 다음과 같은 옵션을 사용할 수 있습니다.

- (**권장**) 사서함을 Office 365로 마이그레이션하고 2020 업그레이드할 수 있으면 Exchange 2010을 사용 하 여 Office 365에 연결 하 고 사서함을 마이그레이션합니다. 다음으로, Exchange 2016를 Exchange 2010로 마이그레이션하고 나머지 Exchange 2010 서버를 해제 합니다.
- 2020 년 10 월 13 일에 사서함 마이그레이션 및 온-프레미스 서버 업그레이드를 완료할 수 없는 경우 온-프레미스 Exchange 2010 서버를 먼저 Exchange 2016로 업그레이드 한 다음 Exchange 2016을 사용 하 여 Office 365에 연결 하 고 사서함을 마이그레이션합니다.

> [!NOTE]
> 다소 복잡 하 게 인해 온-프레미스 Exchange 2010 서버를 Exchange 2016로 마이그레이션하는 동안 사서함을 Office 365로 마이그레이션할 수도 있습니다.

다음은 Exchange Server 2010에 대 한 지원 종료를 방지 하기 위해 수행할 수 있는 세 가지 경로입니다.

![Exchange Server 2010 업그레이드 경로](./media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

다음 섹션에서는 각 옵션에 대해 자세히 알아봅니다.

## <a name="migrate-to-office-365"></a>Office 365로 마이그레이션

Exchange 2010 배포를 중지 하는 데 도움이 되는 가장 간단 하 고 간단한 옵션은 전자 메일을 Office 365로 마이그레이션하는 것입니다. Office 365로 마이그레이션하는 경우 이전 기술과의 단일 홉을 사용 하 여 다음과 같은 최신 기능을 사용할 수 있습니다.

- 보존 정책, 현재 위치, 소송 보존, 원본 위치 eDiscovery 등의 규정 준수 기능
- Microsoft 팀
- Power BI;
- 중요 받은 편지함;
- Delve 분석;

또한 Office 365은 새로운 기능과 환경을 먼저 제공 하며, 사용자는 일반적으로 바로 사용을 시작할 수 있습니다. 새 기능 외에도 다음에 대해 걱정할 필요가 없습니다.

- 하드웨어 구입 및 유지 관리
- 서버 과열 및 냉각에 대 한 비용 지불
- 보안, 제품 및 표준 시간대 수정 사항에 대해 최신 상태를 유지 합니다.
- 준수 요구 사항을 지원 하기 위해 저장소 및 소프트웨어 유지 관리
- 새 버전의 Exchange로 업그레이드-항상 Office 365에서 최신 Exchange 버전을 사용 하 고 있습니다.

### <a name="how-should-i-migrate-to-office-365"></a>Office 365로 마이그레이션하는 방법

조직에 따라 Office 365에 액세스 하는 데 도움이 되는 몇 가지 옵션을 사용할 수 있습니다. 마이그레이션 옵션을 선택할 때는 이동 해야 하는 좌석 또는 사서함 수, 마이그레이션에 소요 되는 시간, 온-프레미스 설치 및 Office 365 중에 원활한 통합이 필요한 지 여부 등 몇 가지 사항을 고려해 야 합니다. 마이그레이션 이 표에서는 마이그레이션 옵션 및 사용할 방법을 결정 하는 가장 중요 한 요소를 보여 줍니다.

| **마이그레이션 옵션**     | **조직 크기** | **기간**        |
|--------------------------|-----------------------|---------------------|
| 단독형 마이그레이션        | 좌석 150 개 미만  | 1 주 이내      |
| 최소 하이브리드 마이그레이션 | 좌석 150 개 미만  | 몇 주 이내 또는 그 밖의 경우 |
| 전체 하이브리드 마이그레이션    | 150 개 이상   | 몇 주 이상 |

다음 섹션에서는 이러한 방법의 개요를 제공 합니다. 자세한 내용은 [마이그레이션 경로를 결정](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) 하 여 각 방법에 대 한 세부 정보를 확인 하세요.

### <a name="cutover-migration"></a>단독형 마이그레이션

마이그레이션에 대 한 자세한 내용은 미리 선택 된 날짜 및 시간에 모든 사서함, 메일 그룹, 연락처 등을 Office 365로 마이그레이션하는 방법 중 하나입니다. 작업이 완료 되 면 온-프레미스 Exchange 서버를 종료 하 고 Office 365 사용을 독점적으로 시작 합니다.

간단한 마이그레이션 방법은 사서함이 너무 많고, Office 365에 빠르게 액세스 하 고, 다른 방법의 복잡성 중 일부를 처리 하지 않으려고 하는 소규모 조직의 경우에 적합 합니다. 그러나 한 주 이내에 완료 되 고 사용자가 자신의 Outlook 프로필을 다시 구성 해야 하므로 다소 제한 됩니다. 정리 마이그레이션에서 최대 2000 개의 사서함을 처리할 수 있지만이 방법을 사용 하는 경우 150 사서함을 마이그레이션하는 것이 좋습니다. 150 개 보다 많은 사서함을 마이그레이션하려는 경우 기한 전에 모든 사서함을 전송 하는 데 시간이 오래 걸릴 수 있으며 IT 지원 담당자가 Outlook을 다시 구성 하는 데 많은 도움을 받을 수 있습니다.

간단한 마이그레이션을 수행 하는 방법을 고려 하 고 있다면 다음 사항을 고려해 야 합니다.

- Office 365에서는 TCP 포트 443을 통해 외부에서 Outlook 사용을 통해 Exchange 2010 서버에 연결 해야 합니다.
- 모든 온-프레미스 사서함이 Office 365로 이동 됩니다.
- 사용자 사서함의 콘텐츠를 읽을 수 있는 권한이 있는 온-프레미스 관리자 계정이 필요 합니다.
- Office 365에서 사용 하려는 Exchange 2010 허용 도메인은 서비스에서 확인 된 도메인으로 추가 해야 합니다.
- 마이그레이션을 시작 하는 시간과 완료 단계를 시작할 때 사이에 Office 365에서는 주기적으로 Office 365 및 온-프레미스 사서함을 동기화 합니다. 이를 통해 온-프레미스 사서함에 남아 있는 전자 메일을 걱정 하지 않고 마이그레이션을 완료할 수 있습니다.
- 사용자가 처음으로 사서함에 로그인 할 때 변경 해야 하는 Office 365 계정에 대 한 새로운 임시 암호를 받게 됩니다.
- 마이그레이션하려는 각 사용자 사서함에 대해 Exchange Online을 포함 하는 Office 365 라이선스가 필요 합니다.
- 사용자가 각 장치에서 새 Outlook 프로필을 설정 하 고 전자 메일을 다시 다운로드 해야 합니다. Outlook에서 다운로드 하는 전자 메일의 양은 다를 수 있습니다. 자세한 내용은 [오프 라인으로 유지할 메일 양 변경](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1)정보를 확인 하세요.

간단한 마이그레이션에 대해 자세히 알아보려면 다음을 확인 하세요.

- [Office 365로의 전자 메일 마이그레이션에 대해 알아야 할 사항](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Office 365에 전자 메일을 간편 하 게 마이그레이션 수행](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>최소 하이브리드 마이그레이션

최소 하이브리드, 즉 빠른 마이그레이션은 Office 365로 마이그레이션할 사서함이 몇 개 있고, 몇 주 내에 마이그레이션을 완료할 수 있으며, 공유 약속 있음/없음 일정 정보와 같은 고급 하이브리드 마이그레이션 기능을 사용할 필요가 없는 것입니다.

최소 하이브리드 마이그레이션은 사서함을 Office 365로 마이그레이션하는 데 더 많은 시간을 기울여야 하지만 몇 주 내에 마이그레이션을 완료 하기 위한 계획을 수립 하는 데 있어 매우 유용 합니다. 복잡성이 많지 않은 경우에도 고급 전체 하이브리드 마이그레이션의 몇 가지 이점이 있습니다. 지정 된 시간에 마이그레이션되는 사서함의 수 및 최대 개수를 제어할 수 있습니다. Office 365 사서함은 온-프레미스 계정의 사용자 이름 및 암호를 사용 하 여 생성 됩니다. 또한 마이그레이션 위에 나오는 것과 달리 사용자는 Outlook 프로필을 다시 만들 필요가 없습니다.

최소한의 하이브리드 마이그레이션을 수행 하는 것이 생각 되는 경우 다음과 같은 몇 가지 사항을 고려해 야 합니다.

- 온-프레미스 Active Directory 서버와 Office 365 간에 일회성 디렉터리 동기화를 수행 해야 합니다.
- 사용자는 사서함이 마이그레이션될 때 사용 중인 것과 동일한 사용자 이름과 암호를 사용 하 여 Office 365 사서함에 로그인 할 수 있습니다.
- 마이그레이션하려는 각 사용자 사서함에 대해 Exchange Online을 포함 하는 Office 365 라이선스가 필요 합니다.
- 사용자가 대부분의 장치에서 새 Outlook 프로필을 설정할 필요는 없지만 일부 이전 Android 휴대폰에는 새 프로필이 필요할 수 있으므로 전자 메일을 다시 다운로드할 필요가 없습니다.

최소 하이브리드 마이그레이션에 대해 자세히 알아보려면 [최소한의 하이브리드 사용을 살펴보고 Exchange 사서함을 Office 365로 신속 하 게 마이그레이션해야](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef) 합니다.

### <a name="full-hybrid"></a>전체 하이브리드

전체 하이브리드 마이그레이션은 조직이 수백, 수천 개까지 사서함을 갖고 있으며 이러한 중 일부 또는 전체를 Office 365로 이동 하려는 경우를 예로 들 수 있습니다. 이러한 마이그레이션은 일반적으로 더 길기 때문에 하이브리드 마이그레이션을 사용 하면 다음과 같은 작업을 수행할 수 있습니다.

- 온-프레미스 사용자에 게 Office 365의 사용자에 대 한 약속 있음/없음 일정 정보를 표시 하 고 그 반대의 경우도 마찬가지입니다.
- 온-프레미스 및 Office 365 둘 다에 받는 사람이 포함 된 통합 전체 주소 목록을 확인 합니다.
- 온-프레미스에 있는지, 아니면 Office 365에 있든 관계 없이 모든 사용자에 대 한 전체 Outlook 받는 사람 카드를 볼 수 있습니다.
- TLS 및 인증서를 사용 하 여 온-프레미스 Exchange 서버와 Office 365 간의 보안 전자 메일 통신
- 온-프레미스 Exchange 서버와 Office 365 간에 전송 되는 메시지를 내부로 취급 하 여 다음과 같은 기능을 사용할 수 있습니다.
- 내부 메시지를 대상으로 하는 전송 및 준수 에이전트로 올바르게 평가 및 처리 해야 합니다.
- 스팸 방지 필터를 무시 합니다.

전체 하이브리드 마이그레이션은 여러 달 이상의 하이브리드 구성에 유지 해야 하는 조직에 가장 적합 합니다. 이 섹션의 앞부분에 나와 있는 기능 및 디렉터리 동기화, 향상 된 통합 준수 기능 및 온라인 사서함 이동을 사용 하 여 Office 365에서 사서함을 이동 하는 기능을 확인할 수 있습니다. Office 365은 온-프레미스 조직의 확장이 됩니다.

전체 하이브리드 마이그레이션을 수행 하는 방법을 고려할 때 고려해 야 할 몇 가지 사항은 다음과 같습니다.

- 전체 하이브리드 마이그레이션은 모든 유형의 조직에 적합 하지 않습니다. 전체 하이브리드 마이그레이션의 복잡도로 인해 사서함 수가 수백 개 미만인 조직은 일반적으로 작업을 설정 하는 데 필요한 노력과 비용을 정당화 하는 이점을 제공 하지 않습니다. 조직 처럼 생각 되는 경우에는 대신 하나 또는 최소한의 하이브리드 마이그레이션을 수행 하는 것이 좋습니다.
- 온-프레미스 Active Directory 서버와 Office 365 간에 Azure Active Directory Connect (AADConnect)를 사용 하 여 디렉터리 동기화를 설정 해야 합니다.
- 사용자는 로컬 네트워크에 로그인 할 때 사용 하는 것과 동일한 사용자 이름과 암호를 사용 하 여 Office 365 사서함에 로그인 할 수 있습니다 (암호 동기화 및/또는 Active Directory Federation Services를 사용 하는 Azure Active Directory Connect 필요).
- 마이그레이션하려는 각 사용자 사서함에 대해 Exchange Online을 포함 하는 Office 365 라이선스가 필요 합니다.
- 사용자가 대부분의 장치에서 새 Outlook 프로필을 설정할 필요는 없지만 일부 이전 Android 휴대폰에는 새 프로필이 필요할 수 있으므로 전자 메일을 다시 다운로드할 필요가 없습니다.

> [!IMPORTANT]
> 조직에서 사서함을 Office 365로 마이그레이션하도록 결정 하지만, 온-프레미스 Active Directory에서 사용자 계정을 계속 관리 하기 위해 DirSync 또는 Azure AD Connect를 유지 하려는 경우에는 하나 이상의 Exchange 서버를 온-프레미스로 유지 해야 합니다. 마지막 Exchange 서버를 제거 하는 경우 exchange Online에서 Exchange 받는 사람을 변경할 수 없게 됩니다. 이는 기관 원본이 온-프레미스 Active Directory에 남아 있으며 변경 해야 하기 때문입니다.

전체 하이브리드 마이그레이션이 적절 하 게 재생 되는 경우 마이그레이션에 도움이 되는 다음 리소스를 확인 하세요.

- [Exchange 배포 도우미](https://aka.ms/exdeploy)
- [Exchange Server 하이브리드 배포](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)
- [하이브리드 구성 마법사](https://technet.microsoft.com/library/hh529921%28v=exchg.150%29.aspx)
- [하이브리드 구성 마법사 FAQ](https://technet.microsoft.com/library/mt488940%28v=exchg.150%29.aspx)
- [하이브리드 배포 필수 구성 요소](https://technet.microsoft.com/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>새 버전의 Exchange Server 온-프레미스로 업그레이드

Office 365로 마이그레이션을 통해 최상의 가치와 사용자 환경을 얻을 수 있다고 확신 하지만 일부 조직에서는 일부 Exchange 서버를 온-프레미스로 유지 해야 한다는 것도 이해 하 고 있습니다. 이는 규정 요구 사항, 데이터가 다른 국가에 있는 데이터 센터에 저장 되지 않도록 하거나, 클라우드에서 충족할 수 없는 고유한 설정이 나 요구 사항이 있거나, Exchange가 필요한 경우에만 발생할 수 있다는 것입니다. 여전히 Active Directory 온-프레미스를 사용 하기 때문에 클라우드 사서함을 관리 합니다. Exchange 온-프레미스를 선택 하거나 유지 해야 하는 경우에는 Exchange 2010 환경을 exchange 2013 또는 Exchange 2016 이상으로 업그레이드 해야 하며, 지원 날짜 보다 끝나기 전에 Exchange 2010이 제거 되어 있어야 합니다.

최상의 환경을 위해 남은 온-프레미스 환경을 Exchange 2016으로 업그레이드 하는 것이 좋습니다. Exchange server 2010에서 Exchange Server 2016로 바로 이동 하려면 Exchange Server 2013을 설치 하지 않아도 됩니다.

Exchange 2016에는 이전 버전의 Exchange에 포함 된 모든 기능 및 향상 된 기능이 포함 되어 있으며, 일부 기능은 Office 365 에서만 사용할 수 있지만 Office 365에서 사용할 수 있는 환경과 가장 밀접 하 게 일치 합니다. 누락 된 항목 중 몇 가지만 확인 하세요.

| **Exchange 릴리스**                     | **기능**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | 간소화 된 아키텍처 서버 역할 수를 3 개 (사서함, 클라이언트 액세스, Edge 전송)로 줄이기                                                                                                                                        |
|                                          | 중요 한 정보의 누출을 방지 하는 데 도움이 되는 DLP (데이터 손실 방지 정책)                                                                                                                                                                |
|                                          | 대폭 향상 된 Outlook Web App 환경                                                                                                                                                                                                    |
| Exchange 2016                            | *Exchange 2013의 기능 및 ...*                                                                                                                                                                                                                   |
|                                          | 사서함 및 Edge 전송에만 해당 하는 보다 간단한 서버 역할                                                                                                                                                                                   |
|                                          | SharePoint와의 통합과 함께 DLP 개선                                                                                                                                                                                                  |
|                                          | 향상 된 데이터베이스 복구 기능                                                                                                                                                                                                                         |
|                                          | 온라인 문서 공동 작업                                                                                                                                                                                                                        |

| **있다는**                        | **추가 정보**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 지원 날짜 종료                     | Exchange 2010와 마찬가지로 각 Exchange 버전의 지원 종료 날짜는 다음과 같습니다.                                                                                                                                                                        |
|                                          | **Exchange 2013** -2023 년 4 월                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** -2025 년 10 월                                                                                                                                                                                                                     |
|                                          | 지원 날짜가 끝나면 이전에 다른 마이그레이션을 수행 해야 합니다. 4 월 2023은 생각 보다 훨씬 더 가깝습니다.                                                                                                                 |
| Exchange 2013 또는 2016의 마이그레이션 경로  | Exchange 2013 또는 Exchange 2016을 선택할 때 Exchange 2010에서 새 버전으로의 마이그레이션 경로는 동일 합니다.                                                                                                                              |
|                                          | 기존 Exchange 2010 조직에 Exchange 2013 또는 2016을 설치 하 고 Exchange 2013 또는 2016에 사서함 및 공용 폴더를 exchange 2013 또는 2016 서비스 해제 남은 Exchange 2010 서버로 이동 합니다.  |
| 버전 동시 사용                      | Exchange 2013 또는 Exchange 2016로 마이그레이션할 때 기존 Exchange 2010 조직에 두 버전을 모두 설치할 수 있습니다. 이를 통해 하나 이상의 Exchange 2013 또는 Exchange 2016 서버를 설치 하 고 마이그레이션을 수행할 수 있습니다.             |
| 서버 하드웨어                          | 서버 하드웨어 요구 사항이 Exchange 2010에서 변경 되었습니다. 사용할 하드웨어가 호환 되는지 확인 해야 합니다. 각 버전의 하드웨어 요구 사항에 대 한 자세한 내용은 여기에서 확인할 수 있습니다.                                      |
|                                          | [Exchange 2016 시스템 요구 사항](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Exchange 2013 시스템 요구 사항](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Exchange 성능이 크게 개선 되 고, 컴퓨팅 파워 및 저장 용량이 최신 서버에 더 많이 제공 되는 경우 동일한 사서함 수를 지원 하기 위한 서버 수가 더 적어집니다.                       |
| 운영 체제 버전                 | 각 버전에 대해 지원 되는 최소 운영 체제 버전은 다음과 같습니다.                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | 운영 체제 지원에 대 한 자세한 내용은 [Exchange 지원 가능성 매트릭스](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)를 확인할 수 있습니다.                                                                        |
| Active Directory 포리스트 기능 수준 | 각 버전에 대해 지원 되는 최소 Active Directory 포리스트 기능 수준은 다음과 같습니다.                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | [Exchange 지원 가능성 매트릭스](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)에서 포리스트 기능 수준 지원에 대 한 자세한 정보를 확인할 수 있습니다.                                                                 |
| Office 클라이언트 버전                   | 각 버전에 대해 지원 되는 최소 Office 클라이언트 버전은 다음과 같습니다.                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (최신 업데이트 포함)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Office 클라이언트 지원에 대 한 자세한 내용은 [Exchange 지원 가능성 매트릭스](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx)를 확인할 수 있습니다.                                                                           |

마이그레이션에 도움이 되는 다음 리소스를 사용할 수 있습니다.

- [Exchange 배포 도우미](https://aka.ms/exdeploy)
- Exchange [2016](https://technet.microsoft.com/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/bb738144%28v=exchg.150%29.aspx) 에 대 한 Active Directory 스키마 변경 사항
- Exchange [2016](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx) 에 대 한 시스템 요구 사항
- Exchange [2016](https://technet.microsoft.com/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/bb691354%28v=exchg.150%29.aspx) 의 필수 구성 요소

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 클라이언트 및 서버 및 Windows 7의 옵션 요약

Office 2010 클라이언트 및 서버 및 Windows 7의 업그레이드, 마이그레이션 및 클라우드 간 옵션에 대 한 자세한 요약을 보려면 [지원 종료 포스터](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf)를 참조 하세요.

![](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)

이 한 페이지 포스터는 Office 2010 클라이언트 및 서버 제품 및 Windows 7의 지원 종료를 방지 하기 위해 수행할 수 있는 다양 한 경로를 이해 하는 빠른 방법 이며, Microsoft 365 Enterprise의 기본 설정 경로 및 옵션을 통해 강조 표시 됩니다.

또한이 포스터를 [다운로드](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) 하 여 letter, legal 또는 tabloid (11 x 17) 형식으로 인쇄할 수 있습니다.
      
## <a name="what-if-i-need-help"></a>도움이 필요한 경우 어떻게 하나요?

Office 365로 마이그레이션하는 경우 Microsoft FastTrack 서비스를 사용할 수 있는 자격이 있을 수 있습니다. FastTrack은 Office 365로의 마이그레이션을 최대한 원활 하 게 수행할 수 있는 모범 사례, 도구 및 리소스를 제공 합니다. 무엇 보다도, 마지막 사서함 마이그레이션에 대 한 모든 방법을 계획 및 디자인에서 안내 하는 실제 지원 엔지니어가 제공 됩니다. FastTrack에 대해 자세히 알아보려면 [Microsoft FastTrack](https://fasttrack.microsoft.com/)을 확인 하세요.

Office 365로 마이그레이션하는 동안 문제가 발생 하 여 FastTrack를 사용 하지 않는 경우 또는 최신 버전의 Exchange Server로 마이그레이션하는 경우에는 다음 작업을 수행 하는 데 도움이 됩니다. 사용할 수 있는 몇 가지 리소스는 다음과 같습니다.

- [기술 커뮤니티](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [고객 지원](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-topics"></a>관련 항목

[Office 2010 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Office 사용 중지 그룹(Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
