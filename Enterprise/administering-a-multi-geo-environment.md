---
title: 다중 위치 환경 관리
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 다중 위치 환경의 SharePoint 및 OneDrive 서비스 관리에 대해 알아봅니다.
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>다중 위치 환경 관리

OneDrive 및 SharePoint 서비스가 다중 위치 환경에서 작동하는 방식을 살펴봅니다.

#### <a name="onedrive-administrator-experience"></a>OneDrive 관리자 환경

[OneDrive 관리 센터](https://admin.onedrive.com)의 왼쪽 탐색 영역에는 지리적 위치를 보고 관리할 수 있는 지리적 위치 지도를 표시하는 **지리적 위치** 탭이 있습니다. 이 페이지에서 테넌트에 대한 지리적 위치를 추가하거나 삭제합니다.

#### <a name="taxonomy"></a>분류

회사에 대한 중앙 위치에 마스터가 호스트된 상태로, 여러 지리적 위치의 엔터프라이즈 관리 메타데이터에 대해 통합된 [분류](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)를 지원합니다. 중앙 위치에서 전역 분류를 관리하고, 위치별 용어는 위성 지리적 위치의 불륨에만 추가하는 것이 좋습니다. 전역 분류는 위성 지리적 위치와 동기화됩니다.

#### <a name="sharing"></a>공유

관리자는 해당 위치 각각에 대해 공유 정책을 설정하고 관리할 수 있습니다. 각 지리적 위치의 OneDrive 사이트에는 해당 지역별 공유 설정만 적용됩니다. (예를 들어 중앙 위치에 대해 [외부 공유](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)를 허용한 경우 위성 위치에는 허용할 수 없으며, 그 반대의 경우도 마찬가지입니다.) 공유 설정은 지리적 위치 간에 공유 제한을 구성하는 것을 허용하지 않습니다.

OneDrive Multi-Geo의 경우, 공유 설정이 테넌트 전체에서 동기화되지 않으므로 각 지리적 위치에서 관리해야 합니다. 공유를 관리하려면 [OneDrive 관리 센터 공유 설정](https://admin.onedrive.com/?v=SharingSettings) 페이지를 참조하세요. 기본적으로 외부 공유는 각 위성 위치의 모든 사용자에게 허용됩니다.

#### <a name="user-profile-application"></a>사용자 프로필 응용 프로그램

각 지리적 위치에는 [사용자 프로필 응용 프로그램](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)이 있습니다. 각 사용자의 프로필 정보가 해당 지리적 위치에 호스트되며 해당 지리적 위치의 관리자가 사용할 수 있습니다.

사용자 지정 프로필 속성이 있으면 지리적 위치 간에 동일한 프로필 스키마를 사용하고 모든 지리적 위치에 또는 필요할 때 사용자 지정 프로필 속성을 채우는 것이 좋습니다. 프로그래밍 방식으로 사용자 프로필 데이터를 채우는 방법에 대한 지침을 보려면 [사용자 프로필 대량 업데이트 API](https://docs.microsoft.com/ko-KR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)를 참조하세요.

#### <a name="bcs-secure-store-apps"></a>BCS, 보안 저장소, 앱

BCS, 보안 저장소 및 앱은 모두 별도의 지리적 인스턴스를 유지하므로, SharePoint Online 관리자는 이러한 항목을 제공하려는 각 지리적 인스턴스에서 이러한 서비스를 관리하고 구성해야 합니다.

#### <a name="security-and-compliance-admin-center"></a>보안 및 준수 관리 센터

Multi-Geo 테넌트에 대해 하나의 중앙 준수 센터인 [Office 365 보안 및 준수 센터](https://protection.office.com/?rfr=AdminCenter\#/homepage)가 있습니다.

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>IP(정보 보호) DLP(데이터 손실 방지) 정책

보안 및 준수 센터에서 비즈니스용 OneDrive에 대한 IP DLP 정책을 설정하고 필요에 따라 정책 범위를 전체 테넌트 또는 해당 사용자로 지정할 수 있습니다. 예를 들어, 위성 위치의 OneDrive 사용자에 대한 정책을 선택하려는 경우 해당 정책을 특정 OneDrive에 적용하고 사용자의 OneDrive URL을 입력합니다. DLP 정책 생성에 대한 일반 지침을 보려면 [데이터 손실 방지 정책 개요](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조하세요.

DLP 정책은 각 지리적 위치에 적용할 수 있는지에 따라 자동으로 동기화됩니다.

지리적 위치에 모든 사용자에 대해 정보 보호 및 데이터 손실 방지 정책을 구현하는 방식은 UI에서 사용할 수 있는 옵션이 아니며, 대신 정책에 대해 적용 가능한 OneDrive 계정을 선택하거나 정책을 모든 OneDrive 계정에 전역적으로 적용해야 합니다.

#### <a name="ediscovery"></a>eDiscovery 

기본적으로 eDiscovery 관리자 또는 다중 위치 테넌트의 관리자는 해당 테넌트의 중앙 위치에서만 eDiscovery를 수행할 수 있습니다. 위성 위치에 대한 eDiscovery를 수행할 수 있는 기능을 지원하기 위해 "Region"이라는 새로운 준수 보안 필터 매개 변수를 PowerShell을 통해 사용할 수 있습니다.

Office 365 전역 관리자는 다른 사용자들이 eDiscovery를 수행할 수 있도록 하기 위해 eDiscovery 관리자 권한을 할당해야 하며, 해당 준수 보안 필터에서 “Region” 매개 변수를 할당하여 eDiscovery 수행 지역을 위성 위치로 지정해야 합니다. 그렇지 않으면 해당 위성 위치에 대해 eDiscovery가 수행되지 않습니다.

특정 지리적 위치에 대해 eDiscovery 관리자(manager) 또는 관리자(administrator) 역할이 설정되면 해당 eDiscovery 관리자(manager) 또는 관리자(administrator)만 해당 지리적 위치에 있는 SharePoint 사이트 및 OneDrive 사이트에 대해 eDiscovery 검색 작업을 수행할 수 있습니다. eDiscovery 관리자(manager) 또는 관리자(administrator)가 지정된 지역 외부의 SharePoint 또는 OneDrive 사이트를 검색하려고 하면 결과가 반환되지 않습니다. 또한 지역에 대한 eDiscovery 관리자(manager) 또는 관리자(administrator)가 내보내기를 트리거할 경우 데이터가 해당 지역의 Azure 인스턴스로 내보내집니다. 이를 통해 제어 경계 너머로 콘텐츠가 내보내지지 않게 되므로 조직은 준수 상태를 유지할 수 있습니다.

> [!NOTE]
> eDiscovery 관리자가 여러 SharePoint 지역에 걸쳐 검색해야 할 경우 OneDrive 또는 SharePoint 사이트가 있는 대체 지역을 지정하는 eDiscovery 관리자에 대해 다른 사용자 계정을 만들어야 합니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Multi-Geo 지원 지리적 위치</strong></th>
<th align="left"><strong>SharePoint 내보낸 데이터에 대한 eDiscovery가 이 Azure Blob 데이터 위치에서 수행</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">미국 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">유럽 데이터 센터</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">동남아시아 또는 동아시아 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">미국 데이터 센터</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">동남아시아 또는 동아시아 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">테넌트의 기본 데이터 위치</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">유럽 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">동남아시아 또는 동아시아 데이터 센터</td>
</tr>
</tbody>
</table>

지역에 대한 준수 보안 필터를 설정하려면

1.  Windows PowerShell을 엽니다.

2.  다음을 입력합니다.  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    예: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

추가 매개 변수 및 구문에 대해서는 [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 문서를 참조하세요.

#### <a name="audit-log-search"></a>감사 로그 검색

모든 지리적 위치에 대한 통합된 [감사 로그](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)를 Office 365 감사 로그 검색 페이지에서 사용할 수 있습니다. 여러 지역의 모든 감사 로그 항목을 볼 수 있습니다. 예를 들어, NAM 및 EUR 지역 사용자의 활동은 하나의 조직 보기에 표시되며, 기존 필터를 적용하여 특정 사용자 활동을 볼 수 있습니다.
