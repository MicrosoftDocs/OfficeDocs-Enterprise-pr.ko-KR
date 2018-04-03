---
title: 다중-지리적으로 분산 환경 관리
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 다중-지리적으로 분산 환경에서 SharePoint와 OneDrive 서비스를 관리 하는 방법에 대 한 설명 합니다.
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>다중-지리적으로 분산 환경 관리

OneDrive 및 SharePoint services 다중-지리적으로 분산 환경에서 작동 하는 방법에 대 한 정보는 다음과 같습니다.

#### <a name="onedrive-administrator-experience"></a>OneDrive 관리자 환경

[OneDrive 관리 센터](https://admin.onedrive.com) 의 왼쪽 탐색 영역 확인 하 고 지리적 위치를 관리할 수 있는 기능 지리적으로 분산-위치를 매핑할 **지리적 위치** 탭을 있습니다. 이 페이지를 사용 하 여 추가 하거나 테 넌 트에 대 한 지리적 위치를 삭제 합니다.

#### <a name="taxonomy"></a>분류

지원 통합된 [분류](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) 엔터프라이즈 관리 되는 메타 데이터에 대 한 여러 지리적 위치에 걸친 회사에 대 한 중앙 위치에서 호스트 되는 마스터와 합니다. 중앙 위치에서 사용자 글로벌 분류를 관리 하 고 위성 지리적 위치 분류에만 위치 관련 용어를 추가할 것이 좋습니다. 글로벌 분류 용어는 위성 지리적 위치를 동기화 합니다.

#### <a name="sharing"></a>공유

관리자가 설정 하 고 각각의 위치에 대 한 공유 정책을 관리할 수 있습니다. OneDrive 사이트 각 지리적 위치에만 해당 지리적으로 분산 특정 공유 설정을 제한이 됩니다. 예, 허용할 수 있습니다 [외부 공유](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) 하면 중앙 위치에 대 한 하지만 위성 위치 하거나 그 반대 방향에 대 한 하지 않습니다. OneDrive 다중-Geo에 대 한 테 넌 트 간에 동기화 되지 않음으로 각 지리적 위치에 공유 설정을 관리 해야 합니다.

공유 방문 [공유 설정을 OneDrive 관리 센터](https://admin.onedrive.com/?v=SharingSettings) 페이지를 관리 합니다. 기본적으로 외부 공유 각 위성 위치에서 모든 사용자와 사용할 수 있습니다.

#### <a name="user-profile-application"></a>사용자 프로필 응용 프로그램

[사용자 프로필 응용 프로그램](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) 각 지리적 위치에 있습니다. 각 사용자의 프로필 정보는 자신의 지리적 위치 및 해당 지리적 위치에 대 한 관리자에 게 사용할 수 있는 호스팅됩니다.

사용자 지정 프로필 속성을 사용 하는 경우 다음 동일한 프로필 스키마를 사용 하 여 지역 하 고 모든 지리적 위치에서 사용자 지정 프로필 속성을 채우는 것이 좋습니다 이나 필요한 곳입니다.

#### <a name="bcs-secure-store-apps"></a>BCS, 보안 저장소 응용 프로그램

BCS, Secure Store 및 앱은 모든는 별도 지리적으로 분산 인스턴스, SharePoint Online 관리자가 관리 하 고 자신이 원하는 위치에 존재 하도록 각 지리적으로 분산 인스턴스에서 이러한 서비스를 구성 해야 하므로 합니다.

#### <a name="security-and-compliance-admin-center"></a>보안 및 규정 준수 관리 센터

다중-지리적으로 분산 테 넌 트에 대 한 하나의 중앙 준수 센터는: [Office 365 보안 및 규정 준수 센터](https://protection.office.com/?rfr=AdminCenter\#/homepage)입니다.

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>정보 보호 (IP) 데이터 손실 방지 (DLP) 정책

정책을 설정할 수 있습니다 IP DLP 비즈니스용 OneDrive에 대 한 보안 및 규정 준수 센터의 전체 테 넌 트 또는 해당 사용자에 게 필요에 따라 정책 범위를 지정 합니다. 예: 특정 OneDrive에 정책을 적용 하 고 사용자를 입력 하려면 선택의 OneDrive url 위성 위치에 OneDrive 사용자에 대 한 정책을 선택 하려는 경우. DLP 정책 만들기 (영문)에 대 한 일반적인 지침에 대 한 [데이터 손실 방지 정책 개요](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) 를 참고 하십시오.

DLP 정책 각 지리적 위치에 적용할 수 있는지에 따라 자동으로 동기화 됩니다.

UI에서 사용할 수 있는 옵션이 아님을 지리적 위치에 모든 사용자에 게 정보 보호 및 데이터 손실 방지 정책 구현, 정책에 대해 적용 가능한 OneDrive 계정을 선택 하거나 모든 OneDrive 계정에는 정책을 전역적으로 적용 해야 대신 합니다.

#### <a name="ediscovery"></a>eDiscovery 

기본적으로 관리자 또는 지리적 다중 테 넌 트의 관리자가 eDiscovery eDiscovery 해당 테 넌 트의 중앙 위치에만 수행할 수 있게 됩니다. 위성 위치에 대 한 eDiscovery를 수행 하는 기능을 지원 하기 위해 "Region" 이라는 새 준수 보안 필터 매개 변수는 PowerShell을 통해 사용할 수 있습니다.

Office 365 전역 관리자가 다른 사용자가 eDiscovery를 수행 하 고 위성으로 eDiscovery를 수행 하기 위한 영역을 지정 하는 적용 가능한 준수 보안 필터에 "Region" 매개 변수를 할당할 수 있도록 eDiscovery 관리자 권한을 할당 해야 합니다. 위치, 그렇지 않은 경우 없음 eDiscovery 위성 위치에 대해 수행 됩니다.

EDiscovery 관리자 또는 관리자 역할은 특정 지리적 위치에 대해 설정 되 면 eDiscovery 관리자 또는 관리자가 SharePoint 사이트 및 해당 지리적 위치에 있는 OneDrive 사이트에 대해 eDiscovery 검색 작업을 수행할 수만. eDiscovery 관리자 또는 관리자가 지정한 영역 외부의 OneDrive 또는 SharePoint 사이트를 검색 하려고 시도 하 고, 하는 경우에 결과가 없으면 반환 됩니다. 또한 한 영역에 대 한 관리자 또는 관리자가 eDiscovery 내보내기를 트리거하는 경우 데이터 Azure 인스턴스의 해당 영역을 내보냅니다. 이렇게 하면 조직이 제어 테두리 간에 내보낼 콘텐츠를 허용 하지 않도록 하 여 준수 유지할 수 있습니다.

> [!NOTE]
> EDiscovery 여러 SharePoint 지역에서 검색 하는 관리자에 대 한 필요한 경우 다른 사용자 계정 eDiscovery 대체 지역을 OneDrive 또는 SharePoint 사이트의 위치를 지정 하는 관리자에 대 한 만들 해야 합니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>다중-지리적으로 분산 지리적 위치를 지원</strong></th>
<th align="left"><strong>SharePoint 내보낸 데이터에 대 한 eDiscovery이 Azure Blob 데이터 위치 포함 될...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>이름</strong></td>
<td align="left">미국 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">유럽 데이터 센터</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">사용할 수 없는 동쪽 또는 동쪽 아시아 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>수 있습니다.</strong></td>
<td align="left">미국 데이터 센터</td>
</tr>
<tr class="odd">
<td align="left"><strong>오스트레일리아</strong></td>
<td align="left">사용할 수 없는 동쪽 또는 동쪽 아시아 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">테 넌 트의 기본 데이터 위치</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">유럽 데이터 센터</td>
</tr>
<tr class="even">
<td align="left"><strong>일본어</strong></td>
<td align="left">사용할 수 없는 동쪽 또는 동쪽 아시아 데이터 센터</td>
</tr>
</tbody>
</table>

지역에 대 한 준수 보안 필터를 설정 합니다.

1.  개방형 Windows PowerShell

2.  맨 위에  
    $s 새로 PSSession-ConfigurationName Microsoft.Exchange =-ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -$cred 자격 증명-기본 인증 AllowRedirection-SessionOption (새로 만들기 PSSessionOption SkipCACheck 서버의-SkipRevocationCheck)

    $를 Import-pssession $s AllowClobber =  

3.  **새 ComplianceSecurityFilter** **-작업** 모든 **-FilterName** EnterTheNameYouWantToAssign **-지역** EnterTheRegionParameter **-사용자가** EnterTheUserPrincipalName

    예: **새 ComplianceSecurityFilter-작업** 모든 **-FilterName** NAMEDISCOVERYMANAGERS **-지역** 이름 **-사용자가** adwood@contosodemosx.onmicrosoft.com

추가 매개 변수 및 구문에 대 한 [새로운 ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 문서를 참조 하십시오.

#### <a name="audit-log-search"></a>감사 로그 검색

한 통합 [감사 로그에](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) 대 한 모든 지리적 위치 하는 것은 Office 365 감사 로그 검색 페이지에서 사용할 수 있습니다. Geos 별에서 모든 감사 로그 항목을 볼 수 있습니다, 등 이름 및 EUR 지리적으로 분산 사용자의 활동 하나의 org 보기에 표시 됩니다 하 고 특정 사용자의 작업을 표시 하는 기존 필터를 적용할 수 있습니다.
