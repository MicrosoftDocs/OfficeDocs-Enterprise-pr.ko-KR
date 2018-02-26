---
title: "Office 365의 개인 데이터에 레이블 적용"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "GDPR 보호 계획의 일부로 Office 레이블을 사용하는 방법을 알아봅니다."
ms.openlocfilehash: be09afa8efa19d48d6bed2ad818adbcaf2aafcda
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="apply-labels-to-personal-data-in-office-365"></a>Office 365의 개인 데이터에 레이블 적용

 Office 레이블을 GDPR 보호 계획의 일부로 사용하는 경우 이 항목을 사용하세요. 지금 바로 Office 365 보안 및 규정 준수 센터 및 Azure Information Protection에서 레이블을 만들 수 있습니다. 시간에 따라 이러한 기술이 통합된 레이블 및 분류 환경으로 집약되며, 더 많은 성과를 거둘 수 있을 것입니다.

Office 365에서 개인 데이터의 보호를 위해 레이블을 사용하는 경우 Office 레이블로 시작하는 것이 좋습니다. 고급 데이터 거버넌스를 사용하여 중요한 정보 유형 또는 기타 기준에 따라 레이블을 자동으로 적용할 수 있습니다. 데이터 손실 방지와 함께 Office 레이블을 사용하여 보호를 적용할 수 있습니다. eDiscovery 및 콘텐츠 검색에서도 레이블을 사용할 수 있습니다. 머지 않아 Cloud App Security와 함께 레이블 및 중요한 정보 유형을 사용하여 다른 SaaS 앱에 있는 개인 데이터를 모니터링할 수 있게 될 것입니다.

Azure Information Protection 레이블은 현재 온-프레미스 및 다른 클라우드 서비스와 공급자의 파일에 레이블을 적용하는 데 권장됩니다. 이러한 레이블은 데이터 보호를 위해 Azure RMS(Azure Rights Management) 암호화를 요구하는 Office 365의 파일(예: 영업 비밀 파일)에도 권장됩니다.

지금은 GDPR이 적용되는 데이터를 포함하는 Office 365의 파일에는 Azure Information Protection을 사용하여 Azure RMS 암호화를 적용하는 것이 권장되지 않습니다. Office 365 서비스는 현재 RMS로 암호화된 파일로 읽을 수 없습니다. 따라서 이 서비스는 이러한 파일에서 중요한 데이터를 찾을 수 없습니다.

Azure Information Protection 레이블은 Exchange Online의 메일에 적용할 수 있으며 Office 365 데이터 손실 방지에 작동합니다. 곧 통합된 분류 및 레이블링 엔진을 사용하여 전송 중인 전자 메일을 자동으로 레이블링하고 보호하는 것을 비롯하여 전자 메일 및 파일에 동일한 레이블을 사용할 수 있게 될 것입니다.

![Office 365 레이블 및 Azure Information Protection 레이블](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

이 그림의 내용

-   SharePoint Online 및 비즈니스용 OneDrive의 개인 데이터와 규제 및 영업 비밀 파일에 Office 365 레이블을 사용합니다.

-   규제 및 영업 비밀 파일, Exchange Online 전자 메일, 다른 SaaS 서비스의 파일, 온-프레미스 데이터 센터의 파일 및 기타 클라우드 공급자의 파일에 AIP(Azure Information Protection) 레이블을 사용합니다.

-   출시 예정: 두 가지 유형의 레이블이 통합된 분류 및 레이블링 환경에 집약될 예정입니다.

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a>정보 보호를 위해 Microsoft 365에서 Office 레이블 및 중요한 정보 유형 사용

다음 그림은 레이블 정책, 데이터 손실 방지 정책 및 Cloud App Security 정책에서 Office 레이블 및 중요한 정보 유형을 사용하는 방법을 보여 줍니다.

![Office 레이블 및 중요한 정보 유형](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

다음 표에서는 이해를 돕기 위해 그림과 동일한 예제를 제공합니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>분류 요소</strong></th>
<th align="left"><strong>정책 레이블 지정 - 2개 예제</strong></th>
<th align="left"><strong>데이터 손실 방지 정책 — 2개 예제</strong></th>
<th align="left"><strong>모든 SaaS 앱에 대한 Cloud App Security 정책 - 1개 예제</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Office 레이블 예제: 개인, 공용, 고객 데이터, HR 데이터, 기밀, 극비</td>
<td align="left"><p>다음 . . .</p>
<p>고객 데이터</p>
<p>. . . 레이블을 다음의 중요한 정보 유형과 일치하는 문서에 자동으로 적용 . . .</p>
<p>&lt;중요한 정보 유형 예제 목록&gt;</p></td>
<td align="left"><p>다음 . . .</p>
<p>&lt;보호 정의&gt;</p>
<p>. . . 보호를 다음 레이블의 문서에 적용 . . .</p>
<p>고객 데이터</p></td>
<td align="left"><p>승인된 SaaS 앱에서 다음 . . .</p>
<p>&lt;미리 정의된 PII 특성 -또는- 사용자 지정 식&gt;</p>
<p>. . . 특성을 가진 파일이 조직 외부에서 공유될 때 경고 발생</p></td>
</tr>
<tr class="even">
<td align="left">중요한 정보 유형. 예: 벨기에 국가 번호, 신용 카드 번호, 크로아티아 ID 카트 번호, 핀란드 국가 ID</td>
<td align="left"><p>사용자에 대해 다음 . . .</p>
<p>&lt;레이블 선택&gt;</p>
<p>. . . 레이블을 다음 위치에 수동으로 적용 . . .</p>
<p>&lt;모든 위치 또는 특정 위치 선택&gt;</p></td>
<td align="left"><p>다음 . . .</p>
<p>&lt;보호 정의&gt;</p>
<p>. . . 레이블을 다음의 중요한 정보 유형과 일치하는 문서에 자동으로 적용&gt;</p></td>
<td align="left">참고: Cloud App Security에 곧 제공될 특성에는 Office 365의 중요한 정보 유형과 Office 365 및 Azure Information Protection의 통합 레이블이 포함됩니다.</td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a>자동 적용 레이블 정책의 우선 순위 지정

GDPR이 적용되는 개인 데이터의 경우, 사용자 환경을 위해 조정한 중요한 정보 유형을 사용하여 레이블을 자동 적용하는 것이 좋습니다. 자동 적용 레이블 정책을 잘 디자인하고 테스트하여 의도한 대로 작동하는지 확인하는 것이 중요합니다.

자동 적용 정책이 만들어지는 순서와 사용자가 이러한 레이블을 적용하는지 여부도 결과에 영향을 미칩니다. 따라서 롤아웃을 신중하게 계획하는 것이 중요합니다. 알아야 할 사항은 다음과 같습니다.

### <a name="one-label-at-a-time"></a>한 번에 하나의 레이블 할당

문서에 하나의 레이블만 할당할 수 있습니다.

### <a name="older-auto-apply-policies-win"></a>오래된 정책이 먼저 자동으로 적용

자동 적용 레이블을 할당하는 규칙이 여러 개 있고 콘텐츠가 여러 규칙의 조건을 충족하는 경우, 가장 오래된 규칙에 대한 레이블이 할당됩니다. 이러한 이유로, 레이블 정책을 구성하기 전에 신중하게 계획하는 것이 중요합니다. 조직은 레이블 정책의 우선 순위를 변경해야 하는 경우 삭제한 후 다시 만들어야 합니다.

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a>수동 사용자 적용 레이블이 자동 적용 레이블보다 우선함

수동 사용자 적용 레이블은 자동 적용 레이블보다 우선합니다. 자동 적용 정책은 사용자가 이미 적용한 레이블을 대체할 수 없습니다. 사용자는 자동 적용된 레이블을 바꿀 수 있습니다.

### <a name="auto-assigned-labels-can-be-updated"></a>자동 할당 레이블을 업데이트할 수 있음

자동 할당 레이블은 최신 레이블 정책 또는 기존 정책의 업데이트로 업데이트될 수 있습니다.

레이블 구현 계획에 다음이 포함되어야 합니다.

-   자동 적용 정책이 만들어지는 순서에 우선 순위 지정

-   사용자가 수동으로 적용하기 위해 레이블을 롤아웃하기 전에 레이블이 자동으로 적용될 수 있는 충분한 시간 허용. 레이블이 조건과 일치하는 모든 콘텐츠에 적용되는 데는 최대 7일이 걸릴 수 있습니다.

### <a name="example-priority-for-creating-the-auto-apply-policies"></a>자동 적용 정책 만들기 우선 순위 예제

<table>
<thead>
<tr class="header">
<th align="left"><strong>레이블</strong></th>
<th align="left"><strong>자동 적용 정책을 만드는 우선 순위</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">인사 - 직원 데이터</td>
<td align="left">1</td>
</tr>
<tr class="even">
<td align="left">고객 데이터</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">극비</td>
<td align="left">3</td>
</tr>
<tr class="even">
<td align="left">인사 - 급여 데이터</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">기밀</td>
<td align="left">5</td>
</tr>
<tr class="even">
<td align="left">공용</td>
<td align="left">6</td>
</tr>
<tr class="odd">
<td align="left">개인</td>
<td align="left">자동 적용 정책 없음</td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a>레이블 만들기 및 레이블 정책 자동 적용

보안 및 규정 준수 센터에서 레이블 및 정책을 만듭니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>단계</strong></th>
<th align="left"><strong>설명</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>규정 준수 팀의 구성원에게 권한을 부여합니다.</p></td>
<td align="left"><p>레이블을 만드는 규정 준수 팀의 구성원에게는 의 보안 &amp; 규정 준수 센터를 사용할 수 있는 권한이 있어야 합니다. 보안 및 규정 준수 센터의 사용 권한으로 이동한 후, 규정 준수 관리자 그룹의 구성원을 수정합니다.</p>
<p><a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">사용자에게 Office 365 보안 &amp; 준수 센터에 대한 액세스 권한 부여</a>를 참조하세요.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Office 레이블을 만듭니다.</p></td>
<td align="left">보안 및 규정 준수 센터의 분류로 이동한 후 레이블을 선택하고 해당 환경에 대한 레이블을 만듭니다.</td>
</tr>
<tr class="odd">
<td align="left"><p>레이블에 대한 자동 적용 정책을 만듭니다.</p></td>
<td align="left">보안 및 규정 준수 센터에서 분류를 선택하고, 레이블 정책을 선택한 후 레이블을 자동 적용하기 위한 정책을 만듭니다. 이러한 정책을 우선 순위대로 만들어야 합니다.</td>
</tr>
</tbody>
</table>

다음 그림에서는 고객 데이터 레이블에 대한 자동 적용 레이블을 만드는 방법을 보여 줍니다.

![고객 데이터에 대한 레이블 만들기 및 적용](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

이 그림의 내용

-   "고객 데이터" 레이블이 만들어집니다.

-   GDPR에 대해 원하는 중요한 정보 유형인 벨기에 국가 번호, 신용 카드 번호, 크로아티아 ID 카트 번호, 핀란드 국가 ID가 나열됩니다.

-   자동 적용 정책을 만들고 정책에 추가하는 중요한 정보 유형 중 하나를 포함하는 모든 파일에 "고객 데이터" 레이블을 할당합니다.
