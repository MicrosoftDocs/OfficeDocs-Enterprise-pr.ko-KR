---
title: 비즈니스 다중-지리적으로 분산 테 넌 트 구성에 대 한 OneDrive
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: OneDrive에 대 한 비즈니스 다중-지리적으로 분산을 구성 하는 방법에 알아봅니다.
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>비즈니스 다중-지리적으로 분산 테 넌 트 구성에 대 한 OneDrive

OneDrive에 대 한 테 넌 트에 대 한 비즈니스 다중-지리적으로 분산을 구성 하기 전에 반드시 [OneDrive에 대 한 비즈니스 다중-지리적으로 분산에 대 한 계획](plan-for-multi-geo.md)을 읽어야 합니다. 이 문서의 단계를 수행 하려면 사용 하려는 위치와 해당 위치에 대 한 프로 비전 할 테스트 사용자 목록이 필요 합니다.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>테 넌 트에 Office 365 계획의 다중-지리적으로 분산 기능 추가

OneDrive에 대 한 비즈니스 다중-지리적으로 분산을 사용 하려면 _Office 365의 다중-지리적으로 분산 기능_ 계획을 해야 합니다. 이 계획 테 넌 트에 추가할 계정 팀과 함께 작동 합니다. 계정 팀 적절 한 라이선스 전문가와 연결 하 고 구성 하는 테 넌 트를 가져올 됩니다.

_Office 365의 다중-지리적으로 분산 기능_ 계획 하는 내용의 사용자 수준 서비스 계획입니다. Setellite 위치를 호스트 하려는 각 사용자에 게 라이선스가 필요 합니다. 위성 위치에서 사용자를 추가할 때는 시간에 따른 추가 라이선스를 추가할 수 있습니다.

_Office 365의 다중-지리적으로 분산 기능_ 계획 테 넌 트이 프로비저닝 되었으며, **지리적 위치** 탭 [OneDrive 관리 센터](https://admin.onedrive.com)에서 사용할 수 있게 됩니다.

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>테 넌 트에 데이터 위치 허용 (ADL)을 설정 합니다.

비즈니스용 OneDrive를 사용 하 여 저장할 SharePoint에 대해 허용 되는 데이터 위치 각 지리적 위치에 대 한 설정 해야 합니다. 사용 가능한 지리적 위치는 다음 표와에서 같습니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>위치</strong></th>
<th align="left"><strong>코드</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">북미</td>
<td align="left">이름</td>
</tr>
<tr class="even">
<td align="left">유럽 동쪽 중간 / / 아프리카</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">아시아 태평양</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">오스트레일리아</td>
<td align="left">오스트레일리아</td>
</tr>
<tr class="odd">
<td align="left">일본</td>
<td align="left">일본어</td>
</tr>
<tr class="even">
<td align="left">캐나다</td>
<td align="left">수 있습니다.</td>
</tr>
<tr class="odd">
<td align="left">영국</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">한국</td>
<td align="left">KOR</td>
</tr>
</tbody>
</table>

위성 지리적 위치를 추가 하려면

1. [OneDrive 관리 센터](https://admin.onedrive.com)를 엽니다.

2. **지리적으로 분산 위치** 탭으로 이동 합니다.

3. **위치 추가**클릭 합니다.

4. 을 추가할 위치를 선택 하 고 ****을 클릭 합니다.

5. 지리적으로 분산 위치와 함께 사용 하려는 도메인을 입력 하 고 **추가**클릭 합니다.

6. **닫기**를 클릭합니다.

위성 위치의 프로 비전 완료 되 면 전자 메일 확인을 메시지가 나타납니다. 새로운 지리적 위치 OneDrive 관리 센터의 **지리적 위치** 탭에서 지도에 파란색으로 표시 되 면 해당 지리적 위치에 사용자의 기본 데이터 위치를 설정 하려면 작업을 진행할 수 있습니다. 

> [!IMPORTANT]
> 새 위성 지리적 위치 기본 설정으로 설정 됩니다. 이렇게 하면 로컬 규정 준수 요구 사항에 따라 해당 지리적 위치를 구성할 수 있습니다.

## <a name="setting-users-preferred-data-location"></a>사용자의 기본 설정된 데이터의 위치 설정
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

필요한 데이터 위치를 사용 하도록 설정한 후에 적절 한 데이터 위치를 사용 하 여 사용자 계정을 업데이트할 수 있습니다. 기본 데이터 위치에 남아 있는 경우 해당 사용자 하는 경우에 모든 사용자에 대 한 기본 설정된 데이터 위치를 설정 하는 것이 좋습니다.

> [!TIP]
> 다중-지리적으로 분산 기능 광범위 한 조직에 배포 하기 전에 테스트 사용자 또는 소규모 사용자 그룹에 대 한 유효성 검사를 시작 하는 것이 좋습니다.

AAD에는 두 유형의 사용자 개체: 클라우드 사용자와 동기화 된 사용자만. 사용자 유형의 사용자에 대 한 적절 한 지침을 따르십시오.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>사용자의 기본 설정 데이터 위치 AD 연결을 사용 하 여 동기화 

Azure Active Directory (AAD)는 온-프레미스 Active Directory (AD) 시스템에서 회사의 사용자는 동기화 하는 경우 자신의 PreferredDataLocation은 AD에 입력 하 고 AAD와 동기화 해야 합니다. 과정에 따라 [Azure AD 연결 동기화: 변경 내용을 기본 구성으로](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) 기본 설정 구성 하려면 데이터 위치 동기화에서 온-프레미스 AD AAD 합니다.

표준 사용자 만들기 워크플로의 일부로 사용자의 기본 설정 된 데이터의 위치를 설정를 포함 하는 것이 좋습니다.

> [!IMPORTANT]
> 프로 비전 onedrive에 없는 새 사용자에 대 한 사용자의 PDL가 사용자가 비즈니스용 OneDrive에 로그인 하기 전에 전파 하는 변경 내용에 대 한 AAD에 동기화 됨 후 24 시간 이상 기다립니다. (기본 설정된 데이터를 설정 위치는 사용자가 자신의 OneDrive 비즈니스에 대 한 프로 비전 하려면 로그인 하기 전에 되도록 사용자의 새 OneDrive 올바른 위치에 프로 비전 할 됩니다.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>클라우드 사용자만 기본적으로 사용 되는 데이터 위치 설정 

회사의 사용자가 동기화 되지 않으면는 온-프레미스 Active Directory (AD) 시스템을 Azure Active Directory (AAD) 하는 경우 Office 365 또는 AAD를 만들 때 사용한 누구나 다음 PDL 설정 해야 AAD PowerShell을 사용 하 여 합니다.

이 섹션의 절차에는 [Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)필요합니다. 이미 설치 된 AAD PowerShell 하는 경우 최신 버전으로 업데이트를 확인 하십시오.

1.  Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 엽니다.

2.  실행 `Connect-MsolService` 테 넌 트에 대 한 전역 관리자 자격 증명을 입력 합니다.

3.  각 사용자에 대 한 기본 설정된 데이터 위치를 설정 하려면 [이와](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet을 사용 합니다. 예를 들어:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    기본 데이터 위치 Get-msoluser cmdlet을 사용 하 여 제대로 업데이트 되었는지 확인 하려면 확인할 수 있습니다. 예를 들어:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

표준 사용자 만들기 워크플로의 일부로 사용자의 기본 설정 된 데이터의 위치를 설정를 포함 하는 것이 좋습니다.

> [!IMPORTANT]
> 프로 비전 onedrive에 없는 새 사용자에 대 한 사용자의 PDL 전파 하는 사용자가 SharePoint OneDrive에 로그인 하기 전에 변경에 대해 설정 된 후 24 시간 이상 기다립니다. (기본 설정된 데이터를 설정 위치는 사용자가 자신의 OneDrive 비즈니스에 대 한 프로 비전 하려면 로그인 하기 전에 되도록 사용자의 새 OneDrive 올바른 위치에 프로 비전 할 됩니다.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive 프로 비전 및 PDL의 영향

사용자가 이미 테 넌 트에서 만든 OneDrive 사이트를 하는 경우 자신의 PDL 설정 자동으로 움직이지 않습니다가 기존 OneDrive 합니다. 사용자의 OneDrive를 이동 하려면 참조 [비즈니스 지리적으로 분산 이동에 대 한 OneDrive](move-onedrive-between-geo-locations.md) 하십시오 지리적 위치 간에 이동 OneDrive의 지시를 따릅니다.

사용자는 테 넌 트 내의 OneDrive 사이트가 없는 경우 OneDrive는 구축할 하 여 자신의 PDL 값에 따라에서 사용자에 대 한 PDL 회사의 허용 되는 데이터 위치 (ADLs) 중 하 나와 일치 하는 것으로 가정 합니다.

## <a name="configuring-multi-geo-search"></a>다중-지리적으로 분산 검색 구성

다중-지리적으로 분산 테 넌 트 어디에서 든 지 결과 반환 하도록 검색 쿼리를 허용 집계 검색 기능에는 테 넌 트 내의 합니다.

기본적으로 각 검색 인덱스의 관련 지리적 위치에 위치 하는 경우에 이러한 진입점에서 검색할 집계 결과 반환 합니다.

- 비즈니스용 OneDrive

- Delve

- SharePoint 홈

- 검색 센터

또한 SharePoint 검색 API를 사용 하 여 사용자 지정 검색 응용 프로그램에 대 한 다중-지리적으로 분산 검색 기능을 구성할 수 있습니다.

모든 제한 및 차이점을 포함 하는 지침에 대 한 [OneDrive에 대 한 비즈니스 다중-지리적으로 분산에 대 한 검색 구성](configure-search-for-multi-geo.md) 을 검토 하십시오.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>OneDrive 비즈니스 다중-지리적으로 분산 구성에 대 한 유효성 검사

다음은 광범위 하 게를 배포 하기 전에 OneDrive에 대 한 비즈니스 다중-지리적으로 분산 회사에 유효성 검사 계획에 포함 하는 것이 좋을 일부 기본 사용 사례입니다. 이러한 테스트 및 회사와 관련 된 모든 추가 사용 사례를 완료 한 후에 초기 파일럿 그룹에 사용자 추가 (영문) 이동 하려면 선택할 수 있습니다.

**비즈니스용 OneDrive**

Office 365 응용 프로그램 시작 관리자에서 OneDrive를 선택 하 고 확인 자동으로 사용자의 PDL에 따라 사용자에 대 한 적절 한 지리적 위치에 전달 됩니다. 비즈니스용 OneDrive 해당 위치에 프로 비전 하는 것을 시작 이제 해야 합니다. 일단 프로 비전된 try 업로드 하 고 일부 문서를 다운로드 합니다.

**OneDrive 모바일 응용 프로그램**

테스트 계정 자격 증명을 사용 하 여 OneDrive 모바일 앱에 로그인 합니다. 비즈니스 파일 비즈니스용 OneDrive를 볼 수 있는 하 고 이러한 모바일 장치에서 상호작용할 수를 확인 합니다.

**OneDrive 동기화 클라이언트**

OneDrive 동기화 클라이언트는 자동으로 로그인 할 때 비즈니스 지리적 위치에 대 한 OneDrive을 검색 하는지 확인 합니다. 동기화 클라이언트를 다운로드 해야 하는 경우에 OneDrive 라이브러리에서 **동기화** 클릭 수 있습니다.

**Office 응용 프로그램**

Word와 같은 Office 응용 프로그램에서 로그인 하 여 비즈니스용 OneDrive에 액세스할 수 있는지 확인 합니다. Office 응용 프로그램 및 선택 엽니다 "OneDrive- <TenantName>"입니다. Office는 OneDrive 위치를 검색 하 고 파일을 열 수를 표시 합니다.

**Sharing**

OneDrive 파일 공유를 시도 합니다. 사용자 선택에서는 설명의 지리적 위치에 관계 없이 모든 SharePoint online 사용자를 확인 합니다.
