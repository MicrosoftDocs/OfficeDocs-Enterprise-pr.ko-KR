---
title: Office 365 콘텐츠 배달 네트워크를 사용 하 여 SharePoint Online을 사용한
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: 위치 또는 콘텐츠를 액세스 하는 방식에 관계 없이 SharePoint Online 자산 모든 사용자에 게 배달 속도를 Office 365의 기본 제공 콘텐츠 배달 네트워크 (CDN)를 사용 하는 방법을 설명 합니다.
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541940"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>Office 365 콘텐츠 배달 네트워크를 사용 하 여 SharePoint Online을 사용한

SharePoint Online 페이지에 대 한 더 나은 성능을 제공 하기 위해 Office 365 콘텐츠 배달 네트워크 (CDN)의 정적 자산을 호스트할 수 있습니다. 정적 자산이 이미지, 비디오 및 오디오, 스타일 시트, 글꼴 및 JavaScript 파일 처럼 매우를 자주 변경 하지 않는 파일입니다. CDN 정적 자산을 요청 하는 브라우저에 더 가깝게를 캐시 하 여 지리적으로 분산 된 캐싱 프록시로 작동 합니다. 
  
Cdn이 작동 하는 방법에 익숙한 경우를 설정 하는 몇 단계를 완료 해야 합니다. 이 항목에서는 설명 방법입니다. Office 365 CDN 및 호스팅 정적 자산을 시작 하는 방법에 대 한 정보에 대 한에서 읽었습니다.
  
 **네트워크를 계획 하 [고 Office 365에 대 한 성능 조정](https://aka.ms/tune)헤드 백업합니다.**
  
## <a name="office-365-cdn-basics"></a>Office 365 CDN 기본 (영문)

Office 365 CDN 구독이 SharePoint Online의 일부로 포함 됩니다. 것에 대 한 추가 지불 필요가 없습니다. Office 365 두 개인에 대 한 지원 및 일반 액세스를 제공 하 고 여러 위치 또는 출처의 호스트 정적 자산 할 수 있습니다. Office 365 CDN Azure CDN 같지는 않습니다. CDN를 사용 하는 이유에 대 한 또는 일반 CDN 개념에 대 한 자세한 정보를 해야하는 경우 [콘텐츠 배달 네트워크](content-delivery-networks.md)를 참조 하십시오.
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>CDN 최종 사용자에 대 한 액세스를 부여 하는 방법

Office 365 CDN의 정적 자산에 대 한 개인 액세스는 SharePoint Online에서 생성 된 토큰에 의해 권한이 부여 됩니다. 이미 출처에 의해 지정 된 라이브러리 또는 폴더에 액세스할 수 있는 권한을 가진 사용자는 토큰에 자동으로 부여 됩니다. SharePoint Online은 CDN에 대 한 항목 수준 사용 권한의 지원 하지 않습니다.
  
예에 있는 파일에 대 한 `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, 다음을 제공 합니다.
  
- 1 사용자에 게 image1.jpg folder1에 대 한 액세스
    
- 사용자 2에는 folder1에 액세스할 수 없는 합니다.
    
- 사용자 3 folder1에 액세스할 수 없는 되지는 않지만 image1.jpg SharePoint Online을 통해 액세스할 수 있는 명시적 권한을 부여 됩니다.
    
- 사용자 4 folder1에 액세스할 수 있지만 image1.jpg에 대 한 액세스 명시적으로 거부 되었음을
    
다음은 다음은 true입니다.
  
- 사용자 1이 고 사용자 4 image1.jpg CDN을 통해 액세스할 수 없게 됩니다.
    
- 사용자 2와 사용자 3 image1.jpg CDN을 통해 액세스할 수 없게 되지 않습니다.
    
    그러나 사용자 3 계속 액세스할 수 자산 image1.jpg 직접 SharePoint Online을 통해 동안 사용자 4 SharePoint Online을 통해 자산에 액세스할 수 없습니다.
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>Office 365 CDN (영문)의 개요 (영문)

Office 365 CDN를 설정 하려면 다음 기본 단계를 수행 합니다.
  
- CDN 배포를 계획 하십시오.
    
  - Office 365 CDN에서를 호스트 하려는 정적 자산을 결정 합니다. 이러한 항목을 선택 하는 방법에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](content-delivery-networks.md)를 참조 하십시오.
    
  - [자산을 저장 하려면 확인](use-office-365-cdn-with-spo.md#CDNStoreAssets)합니다. 이 위치는 폴더 또는 SharePoint 라이브러리 이며 원점 라고 합니다.
    
  - 자산을 공개 또는 비공개로 유지 하는지 여부를 결정 합니다. 이 경우에 수행에 필요한 [각 출처를 공용 또는 개인으로 지정할지 여부를 선택](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)합니다. 원할 경우 일부 공용는 여러 출처를 포함할 수 하 고 일부는 개인 합니다.
    
- [설정 및 SharePoint Online 관리 셸을 사용 하 여 Office 365 CDN 구성](use-office-365-cdn-with-spo.md#CDNSetupinPShell)합니다. 이 단계를 완료 해야 합니다.
    
  - 조직에 대 한 CDN를 사용할 수 있습니다.
    
  - 프로그램 출처를 추가 합니다. 공용 또는 개인으로 각 출처를 식별 합니다.
    
한번, 설치 하 여 시간에 따른 [관리 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) 마친: 
  
- 추가, 업데이트 및 자산을 제거 합니다.
    
- 추가 (영문) 및 출처를 제거 합니다.
    
- CDN 정책 구성
    
- 필요한 경우 Office 365 CDN 사용 하지 않도록 설정
    
## <a name="determine-where-you-want-to-store-your-assets"></a>자산을 저장 하려면 확인

CDN 호출 하는 원본 위치에서 자산을 가져옵니다. Office 365에 대 한 원점 SharePoint 라이브러리 또는 URL에 액세스할 수 있는 폴더입니다. 조직에 대 한 출처를 지정 하는 경우 유연 하 게 있습니다. 예, 여러 출처 또는 모든 CDN 자산을 배치 하려는 하는 단일 출처를 지정할 수 있습니다. 조직에 대 한 공용 또는 개인 출처를 선택할 수 있습니다. 대부분의 조직에서는 둘의 조합을 구현 하려면 선택 합니다.
  
수백 개의 출처를 정의 하는 경우 가능성이 저하에 미칠 요청을 처리 하는데 걸리는 시간입니다. 약 100 개가 넘는 출처 있는 아키텍처를 다시 생각 하 게 사용할 수는 것이 좋습니다.
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>각 출처를 공용 또는 개인으로 지정할지 여부를 선택 합니다.

출처를 식별 하는 경우 공용 또는 개인 될 해야 하는지 여부를 지정할 수 있습니다. 어떤 옵션을 선택 하면에 관계 없이 Microsoft 자체 CDN의 관리를 수행할 때 하면 모든 쉬워집니다를 수행 합니다. 또한 변경할 수 있습니다 마음이 나중에 CDN 설정 했을 때 하 여 출처를 식별 한 후.
  
공용 및 개인 옵션은 향상 된 성능을 제공 했으나 각각 고유한 특성 및 장점이 있습니다.
  
 **특성 및 공용 출처의 자산 호스팅의 장점**
  
- 공용 출처에서 노출 자산 익명으로 모든 사용자가 액세스할 수 있습니다.
    
    > [!IMPORTANT]
    > 프로그램 CDN에서 공용 출처를 식별 하는 경우 리소스 것으로 간주 되 조직에 중요 한 공용 원본이 나 SharePoint 온라인 라이브러리에 두지 해야 합니다. 
  
- 자산을 캐시;에서 최대 30 일 동안 사용할 수 있도록 계속 될 수 있습니다 공용 원점에서 자산을 제거 하는 경우 그러나 15 분 이내 CDN에서 자산에 대 한 링크를 무효화 됩니다 했습니다.
    
- 공용 출처에 스타일 시트 (CSS 파일)를 호스트 하는 경우 코드 내에서 Uri 및 상대 경로 사용할 수 있습니다. 즉, 배경 이미지 및 메서드를 호출 하는 자산의 위치를 기준으로 다른 개체의 위치를 참조할 수 있습니다.
    
- 공용 출처의 URL, 하드 코딩 하는 동안 이렇게 하면 있으므로 권장 되지 않습니다. 이 대 한 설명 CDN에 대 한 액세스를 사용할 수 없게 하는 경우 URL SharePoint Online에서 조직에 자동으로 해결 되지 것입니다 되 고 되 끊어진된 링크 및 기타 오류가 발생할 수 있습니다.
    
- 공용 출처에 대 한 포함 된 기본 파일 형식은.css,.eot,.gif,.ico,.jpeg,.jpg,.js,.map,.png,.svg,.ttf, 및.woff 됩니다. 추가 파일 형식을 지정할 수 있습니다.
    
- 원할 경우 사용자가 지정한 사이트 분류 하 여 식별 된 자산을 제외 하는 정책을 구성할 수 있습니다. 예는 허용 되는 파일 형식 및 공용 출처에 있는 경우에 "confidential" 또는 "제한"으로 표시 되는 모든 자산을 제외 하도록 선택할 수 있습니다.
    
 **특성 및 개인 출처의 자산 호스팅의 장점**
  
- 이렇게 권한이 있는 경우 사용자가 개인 원점에서 자산을 액세스할만 수 있습니다. 이러한 자산에 대 한 익명 액세스 차단 됩니다.
    
- 자산을 캐시;에서 1 시간까지 사용할 수 있는 계속 될 수 있습니다 개인 원점에서 자산을 제거 하는 경우 그러나 15 분 이내 CDN에서 자산에 대 한 링크를 무효화 됩니다 했습니다.
    
- 개인 출처에 대 한 포함 된 기본 파일 형식에는.gif,.ico,.jpeg,.jpg,.js, 및.png 됩니다. 추가 파일 형식을 지정할 수 있습니다.
    
- 공용 출처와 마찬가지로 와일드 카드를 사용 하 여 폴더 또는 사이트 라이브러리 내의 모든 자산을 포함 하는 경우에를 지정 하는 사이트 분류 하 여 식별 된 자산을 제외 하는 정책을 구성할 수 있습니다.
    
## <a name="default-office-365-cdn-origins"></a>기본 Office 365 CDN 출처

별도로 지정 하지 않으면 Office 365 설정 하는 일부 기본 출처를 하면 Office 365 CDN를 사용 하도록 설정 하면 됩니다. 처음를 제외 하면 해당 하는 경우에 설치를 완료 한 후 이러한 출처를 추가할 수 있습니다.
  
기본 개인 출처:
  
- \*/userphoto.aspx
    
- \*/siteassets
    
기본 공용 출처:
  
- \*/masterpage
    
- \*/style 라이브러리
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>설정 및 SharePoint Online 관리 셸을 사용 하 여 Office 365 CDN 구성

이 항목의 절차를 사용 하면를 사용 하 여 SharePoint Online 관리 셸 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [SharePoint Online PowerShell 연결](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)을 참조 하십시오.
  
설정 및 SharePoint Online에서 정적 자산을 호스트 하는 Office 365 CDN를 구성 하려면 다음이 단계를 완료 합니다.
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>Office 365 CDN를 사용 하 여 조직에 사용 하도록 설정 하려면

**집합 SPOTenantCdnEnabled** cmdlet를 사용 하 여 Office 365 CDN를 사용 하 여 조직에 사용 하도록 설정 합니다. 공용 출처, 개인 출처 또는 CDN와 둘 모두를 사용 하 여 조직의 설정할 수 있습니다. Office 365 CDN를 사용 하도록 설정 하면 기본 출처의 설치를 건너뛸지를 구성할 수 있습니다. 항상 이러한 출처를 나중에이 항목의 설명에 따라 추가할 수 있습니다. 
  
SharePoint Online에 대 한 Windows powershell:
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

예, CDN와 공용 및 개인 출처를 사용 하 여 조직을 활성화 하려면 다음 명령을 입력 합니다.
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

조직 CDN 함께 공용 및 개인 출처를 사용 하지만 기본 출처를 건너뛸 수를 사용 하도록 설정 하려면 다음 명령을 입력 합니다.
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

CDN와 공용 출처를 사용 하 여 조직을 사용 하려면 다음 명령을 입력 합니다.
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

CDN와 개인 출처를 사용 하 여 조직을 사용 하려면 다음 명령을 입력 합니다.
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

이 cmdlet에 대 한 자세한 내용은 [집합 SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)을 참조 하십시오.
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>(선택 사항) Office 365 CDN에 포함할 파일 형식의 목록을 변경 하려면
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> **집합 SPOTenantCdnPolicy** cmdlet을 사용 하 여 파일 형식을 정의 하는 경우에 현재 정의 된 목록을 덮어씁니다. 추가 파일 형식 목록에 추가 하려는 경우 cmdlet은 먼저 찾는데 사용할 파일 형식을 이미 허용 되 고 새 항목과 함께 목록에 포함 합니다. 
  
CDN에서 공용 및 개인 출처에서 호스팅할 수 있는 정적 파일 형식 정의 **집합 SPOTenantCdnPolicy** cmdlet을 사용 합니다. 기본적으로 일반 자산 종류 예제.css,.gif,.jpg, 및.js 수 있습니다. 
  
SharePoint Online에 대 한 Windows powershell:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

파일 유형을 현재 CDN에 의해 걸러지고 남은 보려면 **Get SPOTenantCdnPolicies** cmdlet을 사용 합니다. 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

이러한 cmdlet에 대 한 자세한 내용은 [집합 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 및 [Get SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)를 참조 하십시오.
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>(선택 사항) Office 365 CDN에서 제외 하려는 사이트 분류의 목록을 변경 하려면
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> **집합 SPOTenantCdnPolicy** cmdlet을 사용 하 여 사이트 분류를 제외 하는 경우에 현재 정의 된 목록을 덮어씁니다. 사이트에 추가 분류 제외 하려는 경우 cmdlet을 사용 처음에 어떤 분류 이미 제외 확인 하 고 새 항목과 함께 추가 합니다. 
  
CDN을 통해 사용할 수 있도록 하려면 사이트 분류를 제외 하려면 **집합 SPOTenantCdnPolicy** cmdlet을 사용 합니다. 기본적으로 사이트 사용할 수 있는 분류 제외 되지 않습니다. 
  
SharePoint Online에 대 한 Windows powershell:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

어떤 사이트 분류는 현재 제한 된 참조를 **Get SPOTenantCdnPolicies** cmdlet을 사용 합니다. 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

이러한 cmdlet에 대 한 자세한 내용은 [집합 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 및 [Get SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)를 참조 하십시오.
  
### <a name="to-add-an-origin-for-your-assets"></a>자산에 대 한 출처를 추가 하려면
<a name="Office365CDNforSPOOrigin"> </a>

원점 정의 **추가 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 여러 출처를 정의할 수 있습니다. 출처는 SharePoint 라이브러리 또는 CDN에 의해 호스트 될 하려는 자산 들어 있는 폴더를 가리키는 URL입니다. 
  
> [!IMPORTANT]
> 프로그램 CDN에서 공용 출처를 식별 하는 경우 리소스 것으로 간주 되 조직에 중요 한 공용 원본이 나 SharePoint 온라인 라이브러리에 두지 해야 합니다. 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

여기서 경로 자산 포함 된 폴더의 경로입니다. 상대 경로 외에도 와일드 카드를 사용할 수 있습니다. 예를 포함 하려면 모든 자산 모든 사이트에 대 한 masterpages 폴더에서 CDN 내에서 공용 원점으로 다음 명령을 입력 합니다.
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

이 명령 및 구문에 대 한 자세한 내용은 [추가 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.
  
명령을 실행 했을 때, 되 면 시스템 데이터 센터 구성을 동기화 합니다. 이 수식의 계산 시간이 15 분.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>예: SharePoint Online에 대 한 마스터 페이지에 대 한 및 스타일 라이브러리에 대 한 공용 원본 구성
<a name="ExamplePublicOrigin"> </a>

일반적으로 이러한 출처는를 설정 하면 기본적으로 Office 365 CDN에 대 한 공용 출처를 사용 하도록 설정 하면 합니다. 그러나 수동으로 수 있도록 하려는 경우 다음이 단계를 수행 합니다.
  
- Office 365 CDN 내에서 공용 원점으로 스타일 라이브러리를 정의 하려면 **추가 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Office 365 CDN 내에서 공용 원점으로 마스터 페이지를 정의 하려면 **추가 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- 이 명령 및 구문에 대 한 자세한 내용은 [추가 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.
    
    명령을 실행 했을 때, 되 면 시스템 데이터 센터 구성을 동기화 합니다. 이 수식의 계산 시간이 15 분.
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>예: SharePoint Online에 대 한 사이트 자산, 사이트 페이지 및 게시 이미지의 개인 원본 구성
<a name="ExamplePrivateOrigin"> </a>

- Office 365 CDN 내 개인 원점으로 사이트 자산 폴더를 정의 하려면 **추가 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Office 365 CDN 내 개인 원점으로 사이트 페이지 폴더를 정의 하려면 **추가 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Office 365 CDN 내 개인 원점으로 게시 이미지 폴더를 정의 하려면 **추가 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    이 명령 및 구문에 대 한 자세한 내용은 [추가 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.
    
    명령을 실행 했을 때, 되 면 시스템 데이터 센터 구성을 동기화 합니다. 이 수식의 계산 시간이 15 분.
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>예: SharePoint Online에 대 한 사이트 모음에 대 한 개인 원본 구성
<a name="ExamplePrivateOriginSiteCollection"> </a>

Office 365 CDN 내 개인 원점으로 사이트 모음을 정의 하려면 **추가 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 예를 들어 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

이 명령 및 구문에 대 한 자세한 내용은 [추가 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.
  
명령을 실행 했을 때, 되 면 시스템 데이터 센터 구성을 동기화 합니다. 이 수식의 계산 시간이 15 분.
  
## <a name="manage-the-office-365-cdn"></a>Office 365 관리 CDN
<a name="CDNManage"> </a>

CDN 설정한 후 변경할 수 있습니다를 구성 요구 사항이 변경 됨, 또는 콘텐츠를 업데이트할 때이 섹션의 설명에 따라 합니다.
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>추가, 업데이트 하 고, 또는 Office 365 CDN에서 자산을 제거 하려면
<a name="Office365CDNforSPOaddremoveasset"> </a>

설치 단계를 완료 한 후 새 자산을 추가할 수 및 업데이트 하거나 원할 경우 언제 든 지 기존 자산을 제거 합니다. 폴더 또는 원점으로 식별 하는 SharePoint 라이브러리의 자산을 변경 것입니다. 새 자산을 추가 하는 경우 가능 하다는 CDN를 통해 즉시 합니다. 그러나 자산을 업데이트 하는 경우 전파 되 고 CDN에서 사용할 수 있게 하 고 새 복사본에 대 한 최대 15 분 걸립니다.
  
원점의 위치를 검색 해야하는 경우에 **Get SPOTenantCdnOrigins** cmdlet을 사용할 수 있습니다. 이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Get SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)을 참조 하십시오.
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>Office 365 CDN에서 한 출처를 제거 하려면
<a name="Office365CDNforSPORemoveOrigin"> </a>

필요한 경우에 폴더 또는 원점으로 식별 하는 SharePoint 라이브러리에 대 한 액세스를 제거할 수 있습니다. 이 작업을 수행 하려면 **제거 SPOTenantCdnOrigin** cmdlet을 사용 합니다. 이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [제거 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)을 참조 하십시오.
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>Office 365 CDN의 원점을 수정 하려면
<a name="Office365CDNforSPORemoveOrigin"> </a>

만들었고 원점을 수정할 수 없습니다. 대신, 출처를 제거 하 고 새를 추가 합니다. 자세한 내용은 [Office 365 CDN에서 원점을 제거 하](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) 고 [자산에 대 한 출처를 추가 하려면](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)을 참조 하십시오.
  
### <a name="to-disable-the-office-365-cdn"></a>Office 365 CDN를 사용 하지 않도록 설정 하려면
<a name="Office365CDNforSPODisable"> </a>

**집합 SPOTenantCdnEnabled** cmdlet을 사용 하면 조직에 대 한 CDN를 사용 하지 않도록 설정 합니다. 모두 공용 및 개인 출처 CDN를 사용 하도록 설정 하는 경우 다음 예제에 표시 된 대로 두번 cmdlet을 실행 해야 합니다. 
  
SharePoint Online 용 Windows Powershell에서 CDN에서 공용 출처 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

CDN에서 개인 출처의 사용을 사용 하지 않으려면 다음 명령을 입력 합니다.
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

이 cmdlet에 대 한 자세한 내용은 [집합 SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)을 참조 하십시오.
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Office 365 CDN 구성 문제해결
<a name="CDNManage"> </a>

끝점 즉시 되지 않습니다에 사용 하기 위해 사용할 수 있는 전체에 전파 되는데 CDN 등록을 위한 시간이 걸립니다. 구성 15 분이 걸립니다.
  

