---
title: 비즈니스용 OneDrive Multi-Geo 테넌트 구성
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: 비즈니스용 OneDrive Multi-Geo를 구성하는 방법을 알아봅니다.
ms.openlocfilehash: 561025efc38199f3a92e228d5414a28df6eb12f0
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549969"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>비즈니스용 OneDrive Multi-Geo 테넌트 구성

비즈니스용 OneDrive Multi-Geo에 대한 테넌트를 구성하기 전에 [비즈니스용 OneDrive Multi-Geo 계획](plan-for-multi-geo.md)을 읽어야 합니다. 이 문서에 나와 있는 단계를 수행하려면 사용하도록 설정하려는 위치와 해당 위치에 대해 프로비전할 테스트 사용자 목록이 필요합니다.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>테넌트에 Office 365 요금제의 Multi-Geo 기능 추가

비즈니스용 OneDrive Multi-Geo를 사용하려면 _Office 365의 Multi-Geo 기능_ 요금제가 필요합니다. 계정 팀과 공조하여 테넌트에 이 요금제를 추가합니다. 계정 팀은 귀하를 적절한 라이선스 전문가에게 연결하여 테넌트가 구성될 수 있게 해드릴 것입니다.

_Office 365의 Multi-Geo 기능_ 요금제는 사용자 수준 서비스 요금제입니다. 따라서 위성 위치에 호스트하려는 각 사용자를 위해 라이선스가 필요합니다. 시간에 따라 위성 위치에 사용자를 추가하면서 라이선스를 더 추가할 수 있습니다.

테넌트가 _Office 365의 Multi-Geo 기능_ 요금제로 프로비전되면 [OneDrive 관리 센터](https://admin.onedrive.com)에서 **지리적 위치** 탭을 사용할 수 있게 됩니다.

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>ADL(허용 데이터 위치)을 테넌트로 설정

비즈니스용 OneDrive를 사용하려는 각 지리적 위치에 대해 SharePoint의 허용 데이터 위치를 설정해야 합니다. 사용 가능한 지리적 위치는 다음 표에 나와 있습니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>위치</strong></th>
<th align="left"><strong>코드</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">아시아 태평양</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">오스트레일리아</td>
<td align="left">AUS</td>
</tr>
<tr class="even">
<td align="left">캐나다</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">유럽/중동/아프리카</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
<td align="left">프랑스</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">일본</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">한국</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">북미</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">영국</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

위성 지리적 위치를 추가하려면

1. [OneDrive 관리 센터](https://admin.onedrive.com)를 엽니다.

2. **지리적 위치** 탭으로 이동합니다.

3. **위치 추가**를 클릭합니다.

4. 추가하려는 위치를 선택한 후 **다음**을 클릭합니다.

5. 지리적 위치에서 사용할 도메인을 입력한 후 **추가**를 클릭합니다.

6. **닫기**를 클릭합니다.

테넌트의 크기에 따라 프로비전하는 데 몇 시간에서 72시간까지 걸릴 수 있습니다. 위성 위치의 프로비전이 완료되면 전자 메일 확인이 수신됩니다. 새 지리적 위치가 OneDrive 관리 센터의 **지리적 위치** 탭의 지도에 파란색으로 표시되면 사용자의 기본 설정 데이터 위치를 해당 지리적 위치로 설정할 수 있습니다. 

> [!IMPORTANT]
> 이 경우 해당 지리적 위치를 로컬 준수 요구에 적합하게 구성할 수 있습니다.

## <a name="setting-users-preferred-data-location"></a>사용자의 기본 설정 데이터 위치 지정
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

필요한 데이터 위치를 사용하도록 설정한 경우, 해당 데이터 위치를 사용하도록 사용자 계정을 업데이트할 수 있습니다. 해당 사용자가 기본 데이터 위치에 있더라도, 모든 사용자의 기본 설정 데이터 위치를 지정하는 것이 좋습니다.

> [!TIP]
> Multi-Geo 기능을 보다 광범위한 조직으로 롤아웃하기 전에 테스트 사용자 또는 소규모의 사용자 그룹을 사용하여 유효성 검사를 시작하는 것이 좋습니다.

AAD에는 두 가지 유형의 사용자 개체인, 클라우드 전용 사용자와 동기화된 사용자가 있습니다. 사용자 유형에 적합한 지침을 따르세요.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>AD Connect를 사용하여 사용자의 기본 설정 데이터 위치 동기화 

회사의 사용자가 온-프레미스 AD (Active Directory) 시스템에서 AAD(Azure Active Directory)로 동기화되면 해당 PreferredDataLocation이 AD에 입력되고 AAD와 동기화됩니다. [Azure AD Connect 동기화: 기본 구성 변경](https://docs.microsoft.com/ko-KR/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)의 프로세스에 따라 온-프레미스 AD에서 AAD로의 기본 설정 데이터 위치 동기화를 구성합니다.

표준 사용자 만들기 워크플로의 일환으로, 사용자의 기본 설정 데이터 위치를 설정하는 것이 좋습니다.

> [!IMPORTANT]
> OneDrive가 프로비전되지 않은 새로운 사용자의 경우, 사용자의 PDL이 AAD와 동기화된 후에 변경 내용이 전파될 수 있게 24시간 넘게 기다렸다가 사용자가 비즈니스용 OneDrive에 로그인하도록 합니다. 사용자가 로그인하여 비즈니스용 OneDrive를 프로비전하기 전에 기본 설정 데이터 위치를 지정하면 사용자의 새 OneDrive가 올바른 위치에 프로비전됩니다.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>클라우드 전용 사용자를 위한 기본 설정 데이터 위치 지정 

회사의 사용자가 온-프레미스 AD(Active Directory) 시스템에서 AAD(Azure Active Directory)로 동기화되지 않을 경우, 즉 Office 365 또는 AAD에서 생성될 경우 AAD PowerShell을 사용하여 PDL을 설정해야 합니다.

이 섹션의 절차를 수행하려면 [Windows PowerShell용 Microsoft Azure Active Directory 모듈](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)이 필요합니다. AAD PowerShell이 이미 설치된 경우 최신 버전으로 업데이트해야 합니다.

1.  Windows PowerShell용 Microsoft Azure Active Directory 모듈을 엽니다.

2.  `Connect-MsolService`를 실행하고 테넌트에 대한 전역 관리자 자격 증명을 입력합니다.

3.  [Set-MsolUser](https://docs.microsoft.com/ko-KR/powershell/msonline/v1/set-msoluser) cmdlet을 사용하여 각 사용자에 대한 기본 설정 데이터 위치를 지정합니다. 예를 들면 다음과 같습니다.

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Get-MsolUser cmdlet을 사용하여 기본 데이터 위치가 적절히 업데이트되었는지 확인할 수 있습니다. 예를 들면 다음과 같습니다.

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

표준 사용자 만들기 워크플로의 일환으로, 사용자의 기본 설정 데이터 위치를 설정하는 것이 좋습니다.

> [!IMPORTANT]
> OneDrive가 프로비전되지 않은 새로운 사용자의 경우, 사용자의 PDL이 설정된 후에 변경 내용이 전파될 수 있게 24시간 넘게 기다렸다가 사용자가 SharePoint OneDrive에 로그인하도록 합니다. 사용자가 로그인하여 비즈니스용 OneDrive를 프로비전하기 전에 기본 설정 데이터 위치를 지정하면 사용자의 새 OneDrive가 올바른 위치에 프로비전됩니다.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive 프로비전 및 PDL의 영향

사용자의 OneDrive 사이트가 이미 테넌트에 만들어진 경우 해당 PDL을 설정해도 기존 OneDrive가 자동으로 이동되지 않습니다. 사용자의 OneDrive를 이동하려면 [비즈니스용 OneDrive 지리적 이동](move-onedrive-between-geo-locations.md)을 참조하세요. 또한 두 지리적 위치 간의 OneDrive 이동 지침을 따르세요.

테넌트 내에 OneDrive 사이트가 없으면 해당 사용자의 PDL이 회사의 ADL(허용 데이터 위치) 중 하나와 일치한다고 가정할 경우 해당 PDL 값에 따라 OneDrive가 프로비전됩니다.

## <a name="configuring-multi-geo-search"></a>Multi-Geo 검색 구성

Multi-Geo 테넌트에는 검색 쿼리가 테넌트 내의 어디에서든지 결과를 반환할 수 있도록 하는 집계 검색 기능이 제공됩니다.

기본적으로 각 검색 인덱스가 관련 지리적 위치 내에 있더라도, 이러한 진입점에서 검색을 수행하면 집계 결과가 반환됩니다.

- 비즈니스용 OneDrive

- Delve

- SharePoint 홈

- 검색 센터

또한 SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램에 대해 Multi-Geo 검색 기능을 구성할 수 있습니다.

제한 사항 및 차이점을 비롯한 지침을 보려면 [비즈니스용 OneDrive Multi-Geo 검색 구성](configure-search-for-multi-geo.md)을 검토하세요.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>비즈니스용 OneDrive Multi-Geo 구성 유효성 검사

다음은 비즈니스용 OneDrive Multi-Geo를 회사에 광범위하게 롤아웃하기 전에 유효성 검사 계획에 포함할 수 있는 몇 가지 기본적인 사용 사례입니다. 이러한 테스트와 회사에 적합한 추가 사용 사례를 완료하고 나면 초기 파일럿 그룹에 사용자를 추가하는 작업을 계속하도록 선택할 수 있습니다.

**비즈니스용 OneDrive**

Office 365 앱 시작 관리자에서 OneDrive를 선택하고, 사용자의 PDL에 따라 사용자에 대해 적절한 지리적 위치로 자동으로 이동되는지 확인합니다. 비즈니스용 OneDrive는 해당 위치에서 프로비전을 시작합니다. 프로비전이 끝나면 일부 문서를 업로드 및 다운로드해보세요.

**OneDrive 모바일 앱**

테스트 계정 자격 증명을 사용하여 OneDrive 모바일 앱에 로그인합니다. 비즈니스용 OneDrive 파일을 볼 수 있고, 모바일 장치에서 해당 파일과 상호 작용할 수 있는지 확인합니다.

**OneDrive 동기화 클라이언트**

OneDrive 동기화 클라이언트가 로그인 시 비즈니스용 OneDrive 지리적 위치를 자동으로 감지하는지 확인합니다. 동기화 클라이언트를 다운로드해야 할 경우 OneDrive 라이브러리에서 **동기화**를 클릭할 수 있습니다.

**Office 응용 프로그램**

Word와 같은 Office 응용 프로그램에서 로그인하여 비즈니스용 OneDrive에 액세스할 수 있는지 확인합니다. Office 응용 프로그램을 열고 "OneDrive- <TenantName>"을 선택합니다. Office에서 사용자의 OneDrive 위치가 감지되고 열 수 있는 파일이 표시됩니다.

**공유**

OneDrive 파일을 공유해 보세요. 사용자 선택 기능에는 모든 SharePoint Online 사용자가 해당 지리적 위치에 관계없이 표시됩니다.
