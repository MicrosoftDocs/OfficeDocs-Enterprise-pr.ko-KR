---
title: Office 365의 개인 데이터에 보호 적용
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: Office 365에서 DLP 정책을 사용하여 개인 데이터를 보호하는 방법을 알아봅니다.
ms.openlocfilehash: 80b0129ade12824ae5d6190042622ea55ac1d427
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915073"
---
# <a name="apply-protection-to-personal-data-in-office-365"></a>Office 365의 개인 데이터에 보호 적용

Office 365의 개인 정보 보호에는 데이터 손실 방지 기능을 사용하는 방식이 포함됩니다. Office 365 보안 및 규정 준수 센터의 DLP(데이터 손실 방지) 정책을 사용하여 Office 365 전체에서 중요한 정보를 식별, 모니터링하고 자동으로 보호할 수 있습니다.

이 항목에서는 DLP를 사용하여 개인 데이터를 보호하는 방법을 설명합니다. 이 항목에서는 SharePoint 라이브러리의 권한 설정 및 장치 액세스 정책 사용을 포함하여 GDPR 규정 준수를 위해 사용할 수 있는 기타 보호 기능도 나와 있습니다.

## <a name="apply-protection-using-data-loss-prevention-in-office-365"></a>Office 365에서 데이터 손실 방지를 사용하여 보호 적용

DLP를 사용하면 다음과 같은 작업을 수행할 수 있습니다.

-   여러 위치에서 중요한 정보를 식별합니다.

-   중요한 정보가 실수로 공유되지 않도록 합니다.

-   사용자가 자신의 워크플로를 중단하지 않고 규정 준수 상태를 유지하도록 하는 방법을 알도록 도와줄 수 있습니다.

-   DLP 정책과 일치하는 내용을 표시하는 DLP 보고서를 확인합니다.

자세한 내용은 [데이터 손실 방지 정책 개요](https://support.office.com/ko-KR/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조하세요.

![데이터 손실 방지 정책을 만들기 위한 옵션](Media/Apply-protection-to-personal-data-in-Office-365-image1.png)

이 그림에서는 DLP 정책을 만들기 위한 옵션을 보여 줍니다.

-   적용할 보호를 선택합니다. 보호에는 다음이 포함될 수 있습니다.

    -   사용자에 대한 정책 팁

    -   관리자에 대한 전자 메일 보고서

    -   외부/내부적 공유 방지

-   보호 적용 기준을 선택합니다. 이 유형의 콘텐츠를 포함하는 문서에 보호를 적용합니다. 중요한 정보 유형 및/또는 레이블을 사용하도록 정책을 구성할 수 있습니다.

### <a name="using-dlp-for-gdpr-compliance"></a>GDPR 규정 준수를 위해 DLP 사용

Office 365 DLP의 기본적인 사용 중 하나는 Office 365 환경에서 EU 데이터 주체와 관련된 개인 데이터를 식별하는 것입니다. Office 365 DLP는 SharePoint Online 및 비즈니스용 OneDrive에서 개인 데이터가 저장되는 위치나 개인 정보를 포함하는 사용자가 전자 메일을 전송하는 경우를 규정 준수 팀에 알릴 수 있습니다. 또한 DLP는 EU 거주자와 관련된 개인 정보로 작업하는 경우 정책 팁을 직원에게 제공할 수도 있습니다.

작업 환경에서 EU 거주자 데이터가 저장되는 위치와 직원이 해당 데이터를 처리하도록 허용된 방식을 교육하고 인식을 높이는 것도 Office 365 DLP의 한 가지 정보 보호 수준을 나타냅니다. 종종, 이 유형의 정보에 대한 액세스 권한이 이미 있는 직원에게는 일상 작업을 수행하기 위해 이러한 권한이 필요합니다. GDPR 준수를 지원하기 위해 DLP 정책을 적용해도 액세스 권한을 제한해야 할 필요는 없을 수 있습니다.

그러나 GDPR을 준수할 때 법적 및 정보 보안 관점에서 저장되는 개인 정보의 유형과 저장 위치, 해당 정보를 저장하고 처리하는 것이 법률적 타당성이 있는지에 대한 조직의 위험 기반 평가가 수행됩니다. 이러한 평가에 따라, 조직을 보호하고 GDPR을 준수하기 위한 정책을 구현하기 위해 EU 데이터 주체에 대한 개인 정보를 포함하는 문서에 대한 직원 액세스 권한을 제거해야 할 수 있습니다. 추가 보호가 필요한 경우 추가 DLP 보호를 구성할 수 있습니다.

다음 표에서는 DLP를 사용하여 보호를 강화하는 3가지 구성을 보여 줍니다. 첫 번째 구성인 인식은 시작점이자 GDPR의 최소 보호 수준으로 사용될 수 있습니다.

### <a name="example-protection-levels-that-can-be-configured-with-dlp-policies-and-used-for-gdpr-compliance"></a>DLP 정책을 사용하여 구성하고 GDPR 규정 준수에 사용할 수 있는 보호 수준 예제

<table>
<thead>
<tr class="header">
<th align="left"><strong>보호 수준</strong></th>
<th align="left"><strong>EU 데이터 주체와 관련된 개인 정보가 포함된 문서에 대한 DLP 구성</strong></th>
<th align="left"><strong>장점과 위험</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">인식</td>
<td align="left"><p>이 데이터가 SharePoint Online 및 비즈니스용 OneDrive의 문서에서 확인될 때 규정 준수 팀에게 전자 메일 알림을 보냅니다.</p>
<p>이 데이터가 들어 있는 문서에 액세스할 때 정책 팁을 사용자 지정한 후 SharePoint 및 비즈니스용 OneDrive의 직원에게 표시합니다.</p>
<p>이 데이터가 공유되는 경우를 감지하고 보고합니다.</p></td>
<td align="left"><p>이 데이터가 저장된 위치와 관련해서 직원은 물론 규정 준수 팀의 인식을 높입니다.</p>
<p>이 데이터를 포함하는 문서의 처리에 대한 회사 정책을 직원에게 교육합니다.</p>
<p>직원이 내부 또는 외부적으로 이 데이터를 공유하지 못하게 합니다.</p>
<p>공유 데이터에 대한 DLP 보고서를 검토하고 있는 보호를 강화해야 하는지 여부를 결정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td align="left">외부 공유 방지</td>
<td align="left"><p>콘텐츠가 외부 사용자와 공유되는 경우 SharePoint Online 및 비즈니스용 OneDrive에서 이 데이터를 포함하는 문서에 대한 액세스를 제한합니다.</p>
<p>이 데이터를 포함하는 문서가 첨부된 전자 메일을 외부 받는 사람에게 전송하지 않도록 합니다.</p>
<p>이 데이터가 공유되는 경우를 감지하고 보고합니다.</p></td>
<td align="left"><p>직원이 내부에서는 이 데이터를 사용할 수 있지만 외부적으로 공유하지 못하게 합니다.</p>
<p>공유 데이터에 대한 DLP 보고서를 내부적으로 검토하고 이 보호를 강화해야 하는지 여부를 결정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td align="left">내부 및 외부 공유 방지</td>
<td align="left"><p>콘텐츠가 내부 또는 외부적으로 공유되는 경우 SharePoint Online 및 비즈니스용 OneDrive에서 이 데이터를 포함하는 문서에 대한 액세스를 제한합니다.</p>
<p>이 데이터를 포함하는 전자 메일을 내부 및 외부 받는 사람 둘 다에게 전송하지는 않도록 합니다.</p></td>
<td align="left"><p>이 데이터의 내부 및 외부 공유 방지</p>
<p>직원이 이 데이터로 작업해야 하는 태스크를 완료하지 못할 수도 있습니다.</p>
<p>공유 데이터에 대한 DLP 보고서를 내부 또는 외부적으로 검토하고 최종 사용자 교육이 필요한지 여부를 결정할 수 있습니다.</p></td>
</tr>
</tbody>
</table>

참고: 보호 수준이 증가하면 정보에 액세스하는 사용자의 권한이 경우에 따라 줄어들며, 일상 태스크를 완료하기 위한 생산성이나 능력에 영향을 미칠 수 있습니다. 직원에게 영향을 미치는 정책을 구현하여 보호 수준을 높이는 작업은 일반적으로 최종 사용자 교육과 함께 진행됩니다. 사용자에게 새로운 보안 정책과 절차를 교육하여 좀 더 안전한 환경에서 지속적으로 생산성을 유지하도록 할 수 있습니다.

### <a name="example-dlp-policy-for-gdpr--awareness"></a>GDPR에 대한 DLP 정책 예제 — 인식 

이름: GDPR이 적용되는 개인 데이터에 대한 인식

설명: 직원에게 정책 팁을 표시하고, SharePoint Online 및 비즈니스용 OneDrive의 문서에서 이 데이터를 찾았을 때 규정 준수 팀에게 알리고, 이 데이터가 조직 외부에 공유될 경우를 감지하고 보고합니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>제어</strong></th>
<th align="left"><strong>설정</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">보호할 정보 선택</td>
<td align="left">사용자 지정 정책 템플릿을 선택합니다.</td>
</tr>
<tr class="even">
<td align="left">위치</td>
<td align="left">Office 365의 모든 위치</td>
</tr>
<tr class="odd">
<td align="left">포함된 콘텐츠 찾기</td>
<td align="left">'편집'을 클릭하고 사용자 환경에 맞게 조정된 모든 중요한 정보 유형을 추가합니다.</td>
</tr>
<tr class="even">
<td align="left">이 콘텐츠가 공유될 경우 감지</td>
<td align="left">이 확인란을 선택하고 '조직 외부의 사용자'를 선택합니다.</td>
</tr>
<tr class="odd">
<td align="left">정책 설정과 일치하는 콘텐츠가 있을 때 사용자에게 알림</td>
<td align="left"><p>이 확인란("사용자에게 정책 팁 표시 및 전자 메일 알림 전송")을 선택합니다.</p>
<p>'팁 및 전자 메일 사용자 지정'을 클릭하고 작업 환경에 맞게 업데이트합니다. <a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">전자 메일 알림 보내기 및 DLP 정책에 대한 정책 팁 표시</a> 문서에서 기본 알림을 참조하세요.</p></td>
</tr>
<tr class="even">
<td align="left">한 번에 특정 양의 중요한 정보가 공유되는 경우 감지</td>
<td align="left"><p>'공유 중인 콘텐츠에 다음이 포함될 때 감지: 동일한 중요한 정보 유형의 ___개 이상 인스턴스' - 1로 설정합니다.</p>
<p>'사고 보고서를 전자 메일로 전송' - 이 확인란을 선택합니다. '보고서에 포함할 내용 및 받는 사람 선택'을 클릭합니다. 규정 준수 팀을 추가해야 합니다.</p>
<p>'콘텐츠에 액세스할 수 있는 사용자 제한 및 정책 재정의’ - 사용자가 해당 정보에 액세스하도록 하면서 중요한 정보에 대한 알림을 수신하도록 하려면 이 확인란을 선택 취소합니다.</p></td>
</tr>
</tbody>
</table>

모든 위치에는 다음이 포함됩니다.

-   SharePoint Online

-   비즈니스용 OneDrive 계정

-   Exchange 사서함

현재 콘텐츠 검색 기능으로 전자 메일을 포함하는 중요한 정보 유형을 테스트할 수 없으므로, 각 정책의 중요한 정보 유형 부분에 대한 Exchange용 정책을 따로 만들고 이러한 정책의 롤아웃을 모니터링하는 것이 좋습니다.

## <a name="additional-protection-you-can-apply-to-protect-personal-data-in-office-365"></a>Office 365의 개인 데이터를 보호하기 위해 적용할 수 있는 추가 보호

중요한 정보 유형, 레이블 및 데이터 손실 보호 정책은 특정 데이터를 포함하는 문서를 식별하고 보호를 적용하는 데 도움을 줍니다. 그러나 이러한 보호는 데이터 액세스에 대해 설정된 적절한 권한, 손상되지 않은 계정의 사용자, 정상 상태의 장치에 따라 좌우됩니다.

다음 그림에서는 개인 데이터에 대한 액세스를 보호하기 위해 적용할 수 있는 추가 보호 기능을 자세히 보여 줍니다.

![개인 데이터에 대한 액세스를 보호하기 위한 추가 보호](Media/Apply-protection-to-personal-data-in-Office-365-image2.png)

다음 표에서는 이해를 돕기 위해 그림과 동일한 정보를 제공합니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>보호 범위</strong></th>
<th align="left"><strong>기능</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">문서 및 전자 메일 수준 보호(전송 중인 메일은 포함되지만, 현재, 휴지 상태의 사서함의 메일은 포함되지 않음)</td>
<td align="left"><p>중요한 정보 유형</p>
<p>Office 레이블</p>
<p>데이터 손실 방지 정책</p>
<p>전자 메일에 대한 Office 365 메시지 암호화</p></td>
</tr>
<tr class="even">
<td align="left">사이트 및 라이브러리 수준 보호(SharePoint Online 및 비즈니스용 OneDrive 사이트 포함)</td>
<td align="left"><p>SharePoint Online 및 비즈니스용 OneDrive 사이트와 라이브러리에 대한 권한</p>
<p>SharePoint Online 및 비즈니스용 OneDrive(사이트 수준)에 대한 외부 공유 정책</p>
<p>사이트 수준 장치 액세스 제어</p></td>
</tr>
<tr class="odd">
<td align="left">서비스 액세스 보호(Office 365의 모든 서비스에 대한 액세스 포함)</td>
<td align="left"><p>EMS(Enterprise Mobility + Security) 제품군의 ID 및 장치 액세스 보호</p>
<p>권한이 부여된 액세스 관리</p>
<p>Windows 10 보안 기능</p></td>
</tr>
</tbody>
</table>

이 문서의 나머지 부분에서는 이러한 각 보호 범주에 대한 추가 정보를 제공합니다.

### <a name="capabilities-that-are-ok-to-use-with-gdpr"></a>GDPR를 통해 사용이 허가된 기능

GDPR 규정 준수에 대해 구성된 환경에서 다음과 같은 기능을 사용할 수 있습니다. 이러한 기능은 GDPR 규정 준수를 위해 필요하지는 않지만 GDPR 준수와 관련된 데이터를 검색, 보호, 모니터링 및 보고하는 기능에 영향을 미치지 않으면서 사용할 수 있습니다.

고객 키 - 고객이 Office 365 내에서 휴지 상태의 데이터를 암호화하는 데 사용되는 암호화 키를 제공하고 제어할 수 있도록 합니다. 규정에 따라 자체 암호화 키를 관리해야 하는 고객에게만 권장됩니다.

고객 Lockbox - 고객 Lockbox를 사용하면 필요한 경우 사례별로 기술적 문제를 해결하기 위해 Microsoft 지원 엔지니어가 사용자의 데이터에 액세스하는 방식을 제어할 수 있습니다. 지원 엔지니어에게 사용자 데이터에 대한 액세스 권한을 부여할지 여부를 제어할 수 있습니다. 요청별로 만료 시간이 제공됩니다.

## <a name="site-and-library-level-protection"></a>사이트 및 라이브러리 수준 보호

### <a name="permissions-for-sharepoint-and-onedrive-for-business-libraries"></a>SharePoint 및 비즈니스용 OneDrive 라이브러리에 대한 사용 권한

SharePoint의 사용 권한을 사용하여 사용자에게 사이트 또는 해당 콘텐츠에 대한 액세스 권한을 제공하거나 액세스를 제한할 수 있습니다. 기본 SharePoint 그룹에 개별 사용자 또는 Azure Active Directory 그룹을 추가하거나 보다 세밀한 제어를 위해 사용자 지정 그룹을 만듭니다.

![모든 권한에서 보기 전용에 이르는 사용 권한 수준](Media/Apply-protection-to-personal-data-in-Office-365-image3.png)

이 그림에서는 모든 권한부터 보기 전용에 이르는 사용 권한 수준을 보여 줍니다. 다음 표에는 동일한 정보가 포함되어 있습니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>모든 권한</strong></th>
<th align="left"><strong>디자인</strong></th>
<th align="left"><strong>편집</strong></th>
<th align="left"><strong>참가</strong></th>
<th align="left"><strong>읽기</strong></th>
<th align="left"><strong>보기만</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">참가 + 승인 및 사용자 지정</td>
<td align="left">참가 + 목록 추가, 편집, 삭제(항목 나열 이상)</td>
<td align="left">항목과 문서 보기, 추가, 업데이트, 삭제</td>
<td align="left">보기 및 다운로드</td>
<td align="left">보기, 다운로드 없음</td>
</tr>
</tbody>
</table>

추가 정보:

-   [SharePoint의 권한 수준 이해](https://support.office.com/ko-KR/article/Understanding-permission-levels-in-SharePoint-87ecbb0e-6550-491a-8826-c075e4859848)

-   [SharePoint 그룹 이해](https://support.office.com/ko-KR/article/Understanding-SharePoint-groups-94d9b261-161e-4ace-829e-eca1c8cd2eb8)

### <a name="external-sharing-policies-for-sharepoint-and-onedrive-for-business-libraries"></a>SharePoint 및 비즈니스용 OneDrive 라이브러리에 대한 외부 공유 정책

대부분의 조직에서는 공동 작업을 지원하기 위해 외부 공유를 허용합니다. 테넌트 전체 설정이 구성되는 방식을 알아보세요. 그런 후 개인 데이터를 포함하는 사이트에 대한 외부 공유 설정을 검토하세요.

외부 사용자는 SharePoint Online 사이트 및 문서에 액세스하도록 초대를 받았으나 SharePoint Online 또는 Microsoft Office 365 구독에 대한 라이선스가 없는 조직 외부의 사람입니다.

외부 공유 정책은 SharePoint Online 및 비즈니스용 OneDrive 둘 다에 적용됩니다.

-   공유 정책을 구성하려면 SharePoint Online 관리자여야 합니다.

-   외부 사용자와 사이트 또는 문서를 공유하려면 사이트 소유자이거나 모든 권한이 있어야 합니다.

다음 표에서는 구성할 수 있는 제어를 요약해서 보여 줍니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>제어 범주</strong></th>
<th align="left"><strong>옵션</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">공유 유형</td>
<td align="left"><p>조직 외부의 공유 허용 안 함(개별 사이트 모음에 대해 설정 가능)</p>
<p>인증된 외부 사용자만 공유 허용(개별 사이트 모음에 대해서는 새로 허용 또는 기존으로 제한을 설정할 수 있음)*</p>
<p>익명 액세스 링크가 있는 외부 사용자의 공유 허용(개별 사이트 모음에 대해 설정 가능)</p>
<p>도메인을 사용하는 외부 공유 제한(허용 및 거부 목록)</p>
<p>기본 링크 유형(익명, 회사 공유 가능 또는 제한) 선택</p>
</td>
</tr>
<tr class="even">
<td align="left">외부 사용자가 수행할 수 있는 작업</td>
<td align="left"><p>외부 사용자가 소유하지 않는 파일, 폴더, 사이트를 공유하지 못하도록 금지</p>
<p>외부 사용자는 초대를 받은 동일한 계정을 사용하여 공유 초대를 수락해야 함</p></td>
</tr>
<tr class="odd">
<td align="left">알림</td>
<td align="left"><p>현재 비즈니스용 OneDrive에서만 사용 가능합니다. 다음 경우에 소유자에게 알립니다.</p>
- <p>사용자가 추가 외부 사용자를 공유 파일로 초대함</p>
- <p>외부 사용자가 파일 액세스 초대를 수락함</p>
- <p>익명 액세스 링크를 만들거나 변경함</p></td>
</tr>
</tbody>
</table>

추가 정보:

-   
  [SharePoint Online 환경에 대해 외부 공유 관리](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)

-   [조직 외부의 사용자와 사이트 또는 문서 공유](https://support.office.com/ko-KR/article/Share-sites-or-documents-with-people-outside-your-organization-80e49744-e30f-44db-8d51-16661b1d4232)

### <a name="site-level-device-access-policies"></a>사이트 수준 장치 액세스 제어

SharePoint Online 및 비즈니스용 OneDrive를 사용하여 사이트 수준에서 장치 액세스 정책을 구성할 수 있습니다. 이를 통해 중요한 데이터가 포함된 사이트에 대해 더 많은 보호를 구성할 수 있습니다.

사이트 수준 장치 액세스 정책을 사용하는 경우 테넌트 수준 정책과 Azure Active Directory, Intune 및 Intune 앱 관리에서 구성된 액세스 정책에 맞춰 조정해야 합니다.

SharePoint 및 비즈니스용 OneDrive에 대한 장치 액세스 정책은 구현하는 시나리오에 따라 Microsoft Intune 및 Azure Active Directory의 정책을 지원해야 합니다. 다음 표에서는 장치 액세스 정책으로 달성할 수 있는 목표를 요약해서 보여 주며 지원 정책이 필요한 제품을 나타냅니다.

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">특정 IP 주소 위치로부터의 액세스만 허용</th>
<th align="left">사용자가 도메인에 가입되지 않은 장치로 파일을 다운로드하지 못하도록 차단</th>
<th align="left">도메인에 가입되지 않은 장치에 대한 액세스 차단</th>
<th align="left">사용자가 호환되지 않는 장치로 파일을 다운로드하지 못하도록 차단</th>
<th align="left">호환되지 않는 장치에 대한 액세스 차단</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">SharePoint 관리 센터</td>
<td align="left">예</td>
<td align="left">예</td>
<td align="left">예</td>
<td align="left">예</td>
<td align="left">예</td>
</tr>
<tr class="even">
<td align="left">Azure Active Directory</td>
<td align="left"></td>
<td align="left">예</td>
<td align="left">예</td>
<td align="left">예</td>
<td align="left">예</td>
</tr>
<tr class="odd">
<td align="left">Microsoft Intune</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left">예</td>
<td align="left">예</td>
</tr>
</tbody>
</table>

자세한 내용: [SharePoint Online 관리 센터: 관리되지 않는 장치의 액세스 제어](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US)

## <a name="service-access-protection-for-identities-and-devices"></a>ID 및 장치에 대한 서비스 액세스 보호

서비스에 액세스하는 ID 및 장치에 대한 보호를 구성하는 것이 좋습니다. Office 365 서비스에 대한 액세스를 보호하기 위해 구성한 작업을 사용하여 다른 SaaS 서비스, PaaS 서비스 및 기타 클라우드 공급자의 앱에 대한 액세스도 보호할 수 있습니다.

ID 및 장치에 대한 액세스 보호는 ID가 손상되지 않고, 장치가 안전하고, 장치에서 액세스되는 조직 데이터가 격리 및 보호되도록 하는 보호 기준을 제공합니다.

권장 시작점 및 구성 지침에 대해서는 [정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](https://docs.microsoft.com/ko-KR/microsoft-365-enterprise/microsoft-security-guidance)을 참조하세요.

AD FS를 사용하는 하이브리드 ID 환경에 대해서는 [권장되는 보안 정책 및 구성](https://docs.microsoft.com/ko-KR/microsoft-365-enterprise/microsoft-security-guidance)을 참조하세요.

다음 그림에서는 클라우드 서비스(SaaS, PaaS), 계정 유형(테넌트 도메인 계정 및 B2B 계정), 서비스 액세스 기능이 관련디는 방식을 보여 줍니다. B2B 계정에 사용할 수 있는 기능을 이해하는 것도 중요합니다.

![클라우드 서비스, 계정 유형 및 액세스 기능](Media/Apply-protection-to-personal-data-in-Office-365-image4.png)

이해를 돕기 위해 이 섹션의 나머지 부분에서는 이 그림을 설명합니다.

### <a name="cloud-services"></a>클라우드 서비스

Azure Active Directory는 Amazon Web Services와 같은 타사 공급자를 비롯한 모든 클라우드 서비스에 대한 ID 액세스를 제공합니다. 이 그림에서는 Office 365를 "기타 SaaS 앱" 및 "PaaS 앱”을 보여 줍니다. Azure Active Directory에서 이러한 각 서비스로 연결되는 화살표는 이러한 모든 앱 유형에 대한 인증에 Azure Active Directory를 사용할 수 있음을 보여 줍니다.

### <a name="types-of-accounts"></a>계정 유형

테넌트 도메인 계정은 테넌트에 추가하고 직접 관리하는 계정입니다. B2B 계정은 공동 작업을 위해 초대하는 조직 외부의 사용자를 위한 계정입니다. 이러한 계정은 다른 Office 365 계정, 다른 조직 계정 또는 소비자 계정(예: Gmail)일 수 있습니다. 이 그림에서는 Azure Active Directory 내의 두 계정 유형을 보여 줍니다.

### <a name="capabilities"></a>기능

다음 표의 기능은 ID 및 장치를 보호합니다. 이 표에서는 B2B 계정에서도 사용할 수 있는 기능을 그림과 비슷하게 나타냅니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>기능</strong></th>
<th align="left"><strong>테넌트 도메인 계정 사용</strong></th>
<th align="left"><strong>Azure B2B 계정 사용(추가 라이선스 없음)</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">다단계 인증 및 조건부 액세스</td>
<td align="left">예</td>
<td align="left">예</td>
</tr>
<tr class="even">
<td align="left">Azure AD ID 보호</td>
<td align="left">예</td>
<td align="left">예</td>
</tr>
<tr class="odd">
<td align="left">Azure AD Privileged Identity Management</td>
<td align="left">예</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">MAM(모바일 응용 프로그램 관리)</td>
<td align="left">예</td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">장치 등록 및 관리</td>
<td align="left">예</td>
<td align="left">하나의 조직에서 하나의 장치만 관리할 수 있음</td>
</tr>
<tr class="even">
<td align="left">Windows 10 보안 기능(장치 규정 준수에 따른 조건부 액세스에서 장치 관리 요구)</td>
<td align="left">예</td>
<td align="left">예</td>
</tr>
</tbody>
</table>

필요한 경우 B2B 계정에 라이선스를 추가하여 사용자에게 이러한 추가 기능을 부 여함으로써 작업 환경의 개인 데이터에 대한 액세스를 보호할 수 있습니다.
