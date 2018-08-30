---
title: SharePoint Server의 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 온-프레미스 SharePoint Server에서 GDPR 요구 사항을 해결하는 방법을 알아보세요.
ms.openlocfilehash: 392b83b080ea111a5be070e9b9383caefe05d0be
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240613"
---
# <a name="gdpr-for-sharepoint-server"></a>SharePoint Server의 GDPR

개인 정보 보호의 일환으로 다음을 권장합니다.

-   Azure Information Protection을 사용하여 데이터를 분류합니다.

-   최소 권한 구성에서 SharePoint Server를 실행합니다. 자세한 내용은 [SharePoint Server에서 최소 권한 관리 계획](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) 및 [SahrePoint Server의 보안](https://docs.microsoft.com/ko-KR/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server)을 참조하세요.

-   [서버에서 BitLocker 암호화를 사용하도록 설정합니다](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).

## <a name="user-generated-content"></a>사용자 생성 콘텐츠

SharePoint Server 사이트 및 라이브러리에 포함된 사용자 생성 콘텐츠에 대한 기본 권장 접근법은 다음과 같습니다.

-   Azure Information Protection을 사용하여 중요한 데이터를 레이블 지정합니다.

-   [SharePoint Server 검색](https://docs.microsoft.com/SharePoint/search/search) 및 [eDiscovery](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server)를 사용하여 중요한 데이터를 검색합니다.

파일 공유와 SharePoint 사이트 및 라이브러리에 대한 권장 접근법에는 다음 단계가 포함됩니다.

1.  **Azure Information Protection 스캐너를 설치하고 구성합니다.**

    -   사용할 중요한 데이터 형식을 결정합니다.

    -   사용할 SharePoint 사이트를 지정합니다.

2.  **검색 주기를 완료합니다.**

    -   검색 모드에서 스캐너를 실행하고 검색 결과의 유효성을 검사합니다.

    -   필요에 따라 조건 및 중요한 정보 유형을 최적화합니다.

    -   레이블 자동 적용의 예상된 영향을 평가합니다.

3.  **Azure Information Protection 스캐너를 실행하여 적격 문서에 레이블을 적용합니다**.

4.  **보호하려면:**

    a. Exchange 데이터 손실 방지 규칙을 구성하여 원하는 레이블로 문서를 보호합니다.

    b. 파일에 액세스할 수 있는 사용자를 제한할 수 있는 권한이 있는지 확인합니다.

    c. SharePoint의 경우 라이브러리에 IRM-보호를 사용합니다.

5.  **모니터링하려면 Windows Server 로그를 SIEM 도구와 통합합니다.**

    a. 데이터 주체 요청에 대한 개인 데이터를 찾으려면 검색 센터 또는 eDiscovery를 사용합니다.

레이블을 중요한 데이터에 적용할 때 보호로 구성되지 않는 레이블을 사용하는지 확인합니다. 보호에는 서비스가 파일의 중요한 데이터를 탐지하지 못하게 하는 암호화를 제공합니다.

Azure Information Protection 스캐너를 사용하여 개인 데이터를 찾고 레이블 지정하는 방법에 대한 자세한 내용은 http://aka.ms/gdprpartners)에서 [Microsoft GDPR 데이터 검색 도구 키트](http://aka.ms/gdprpartners)를 참조하세요.

조건을 위한 스캐너 구성 및 Office 365 DLP(데이터 손실 방지) 중요한 정보 유형의 사용에 대한 자세한 내용은 [Azure Information Protection의 자동 및 권장 분류를 위한 조건을 구성하는 방법](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification)을 참조하세요. 새 Office 365 중요한 정보 유형은 스캐너에서 즉시 사용할 수 없으며 사용자 지정 중요한 정보 유형은 스캐너에서 사용할 수 없습니다.

## <a name="removing-personal-information-from-office-files"></a>Office 파일에서 개인 정보 제거

SharePoint 문서 라이브러리에 저장된 Office 파일의 개인 정보(예: Word 문서의 메타데이터 또는 설명)를 수동으로 제거해야 합니다. 다음 단계를 따릅니다.

1.  SharePoint Server의 문서 복사본을 로컬 디스크에 다운도르합니다.

2.  SharePoint 문서 라이브러리에서 문서를 삭제 합니다.

3.  [문서를 검사하여 숨겨진 데이터 및 개인 정보 제거](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F)의 단계를 따릅니다.

4.  문서를 SharePoint 문서 라이브러리에 다시 업로드합니다.

## <a name="telemetry-and-log-files"></a>원격 분석 및 로그 파일

### <a name="uls-logs"></a>ULS 로그

SharePoint Server 트랙의 ULS(통합 로깅 서비스) 및 사용 현황 로깅은 다양한 시스템 기능을 추적하며 사용자 정보를 포함할 수 있습니다. ULS 로그 및 사용 현황 로그는 텍스트 파일이며 다양한 검색 도구를 사용하여 검색할 수 있습니다. [Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/ko-KR/powershell/module/sharepoint-server/merge-splogfile)은 팜의 여러 서버에 있는 ULS 로그의 레코드를 반환하는 방법을 제공합니다.

로그 보존 정책을 비즈니스 목적에 필요한 최소값으로 설정하는 것이 좋습니다. SharePoint Server에서 로깅을 구성하는 방법에 대한 자세한 내용은[ SharePoint Server에서 진단 로깅 구성](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)을 참조하세요.

일부 시스템 이벤트는 Windows 이벤트 로그에도 로깅됩니다.

### <a name="usage-database"></a>사용 현황 데이터베이스

SharePoint Server 사용 현황 데이터베이스(기본 이름 WSS_Logging)에는 ULS 로그에서 발견되는 정보의 하위 집합이 포함되어 있습니다. 데이터베이스에 있는 데이터의 최대 보존 기간은 30일입니다. 비즈니스 요구 사항에 따라 허용되는 최단 기간 동안 구성하는 것이 좋습니다. 자세한 내용은 [SharePoint Server에서 진단 로깅 구성](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)을 참조하세요.

## <a name="personal-information-and-search"></a>개인 정보 및 검색

검색 쿼리 기록 및 사용 현황 레코드에는 사용자 이름에 대한 참조가 포함되어 있습니다.

### <a name="query-history-and-favorite-queries"></a>쿼리 기록 및 즐겨찾기 쿼리

SharePoint Server에서 쿼리 기록 및 ‘즐겨찾기’ 쿼리는 자동으로 365일 후에 만료됩니다. 사용자가 조직을 떠나면 다음 단계를 사용하여 쿼리 기록에서 사용자 이름에 대한 참조를 제거할 수 있습니다.

다음 SQL 쿼리는 SharePoint Server에 적용되며 다음 작업을 수행할 수 있습니다.

-   사용자의 쿼리 기록 또는 즐겨찾기 쿼리 내보내기

-   쿼리 기록의 사용자 이름에 대한 참조 제거

#### <a name="export-a-users-queries-since-a-specific-date"></a>특정 날짜 후 사용자의 쿼리 내보내기 

@StartTime 후 @UserName에 의해 수행된 링크 스토어 쿼리 로그 테이블에서 쿼리를 내보내려면 다음 절차를 사용합니다.

```sql
[In dbo].[LinkStore_<ID>]:
CREATE PROCEDURE proc_MSS_GetQueryTermsForUser 
( 
    @UserName nvarchar(256), 
    @StartTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT searchTime, queryString 
    FROM 
        dbo.MSSQLogPageImpressionQuery 
    WITH 
        (NOLOCK) 
    WHERE 
        userName = @UserName AND 
        searchTime > @StartTime 
END 
GO 
```

#### <a name="export-a-users-queries-from-the-past-100-days"></a>지난 100일 동안의 사용자 쿼리 내보내기

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a>사용자의 즐겨찾기 쿼리 내보내기

<DateTime> 후 @UserName에 의해 수행된 검색 관리 DB 개인 결과 테이블에서 사용자의 즐겨찾기 쿼리를 내보내려면 다음 정차를 사용합니다.

```sql
In [dbo].[Search_<ID>]:
CREATE PROCEDURE proc_MSS_GetPersonalFavoriteQueries 
( 
    @UserName nvarchar(256), 
    @SearchTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT max(queries.SearchTime) as SearchTime, 
           max(queries.querystring) as queryString, 
           max(url.url) as URL 
    FROM MSSQLogOwner owners WITH(NOLOCK) 
    JOIN MSSQLogPersonalResults results WITH(NOLOCK) on owners.OwnerId = results.OwnerId 
    JOIN MSSQLogUrl url WITH(NOLOCK) on results.ClickedUrlId = url.urlId 
    JOIN MSSQLogPersonalQueries queries WITH(NOLOCK) on results.OwnerId = queries.OwnerId 
    WHERE queries.SearchTime > @SearchTime 
        AND queries.UserName = @UserName 
        GROUP BY queries.QueryString,url.url 
END 
GO 
```

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a>지난 100일 동안 사용자의 즐겨찾기 쿼리 내보내기 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a>X일보다 오래된 사용자 이름에 대한 참조 제거

다음 절차를 통해 링크 스토어 쿼리 로그 테이블에서 @Days보다 오래된 *모든* 사용자 이름에 대한 참조를 제거합니다. 이 절차는 @LastCleanupTime에 도달하기 전의 참조만 제거합니다.

```sql
In [dbo].[LinksStore_<ID>]:  
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a>X일보다 오래된 특정 사용자 이름에 대한 참조 제거

다음 절차를 사용하여 참조가 @Days일보다 오래된 링크 스토어 쿼리 로그 테이블에서 *특정* 사용자 이름에 대한 참조를 제거합니다. 절차는 @LastCleanupTime에 도달하기 전의 참조만 제거합니다.

```sql
In [dbo].[LinksStore_<ID>]:
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @UserName nvarchar(256),
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a>날짜와 지난 30일 동안의 쿼리 기록에 있는 모든 사용자 이름에 대한 참조 제거

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a>사용 현황 레코드 삭제

SharePoint Server는 3년 후 자동으로 사용 현황 레코드를 삭제합니다. 다음 절차를 사용해 이러한 레코드를 수동으로 삭제할 수 있습니다.

삭제된 문서와 연관된 모든 사용 현황 레코드를 삭제하려면: 

1.  최신 SharePoint 업데이트가 설치되어 있는지 확인합니다. 

2.  SharePoint 관리 셀을 시작합니다.

3.  사용 현황 분석 중지 및 지우기: 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  다시 시작하려면 분석을 기다립니다(24시간 정도 소요될 수 있음). 

5.  다음번 분석 실행 시 분석 보고 데이터베이스에서 모든 레코드를 덤프합니다. 항목이 많은 대용량 데이터베이스의 경우 이 전체 덤프는 시간이 다소 소요될 수 있습니다.

6.  10일 동안 기다립니다. 분석을 매일 실행하며 삭제된 문서와 연관된 레코드는 10번째 실행한 후 제거됩니다. 많은 레코드를 삭제해야 하는 경우 평소보다 시간이 더 소요될 수 있습니다. 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a>SharePoint Server 2010의 개인 정보 및 검색

#### <a name="fast-search-server-2010-for-sharepoint"></a>FAST Search Server 2010 for SharePoint 

인덱스에 파일을 저장하는 것 외에 FAST Search Server 2010 추가 기능은 SFixML이라는 중간 형식에 파일을 저장합니다. FiXML 파일은 기본적으로 매일 새벽 3시에서 5시 사이에 정기적으로 압축됩니다. 압축하면 FiXML 파일에서 삭제된 파일이 자동으로 제거됩니다. 삭제된 사용자 또는 문서에 속한 정보를 적절한 시기에 제거하려면 항상 압축을 사용할 수 있는지 확인합니다.

### <a name="hybrid-search"></a>하이브리드 검색 

하이브리드 검색 솔루션에 대한 권장 사항은 SharePoint Server 또는 SharePoint Online의 검색에 대한 권장 사항과 같습니다. 다음은 2가지 하이브리드 검색 솔루션입니다.

**클라우드 하이브리드 검색 솔루션** - SharePoint용 클라우드 하이브리드 검색 솔루션을 통해 Office 365의 검색 인덱스에서 온-프레미스 콘텐츠를 포함한 크롤링된 모든 콘텐츠를 인덱싱합니다. 사용자가 Office 365에서 검색 인덱스를 쿼리하면 온-프레미스 및 Office 365의 검색 결과를 모두 얻습니다. SharePoint Server 환경에서 문서가 삭제되면 Office 365의 검색 인덱스에서도 삭제됩니다. [클라우드 하이브리드 검색 솔루션](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) 및 [클라우드 하이브리드 검색에서 구성 요소 및 데이터베이스 상호 작용을 검색하는 방법](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint)을 자세히 읽어보면 GDPR이 하이브리드 환경에 미치는 영향을 더 잘 이해할 수 있습니다.

**하이브리드 페더레이션된 검색 솔루션** - 하이브리드 연결된 검색 솔루션을 사용하면 SharePoint Server의 인덱스와 Office 365의 인덱스를 둘 다 사용하게 됩니다. SharePoint Server 및 SharePoint Online Search 서비스는 둘 다 다른 환경의 검색 인덱스를 쿼리하고, 연결된 결과를 반환할 수 있습니다. 사용자가 검색센터에서 검색하면 검색 결과가 SharePoint Server의 검색 인덱스와 Office 365의 검색 인덱스에서 제공됩니다. [하이브리드 페더레이션된 검색 솔루션을 자세히 읽어보면](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) GDPR이 하이브리드 환경에 미치는 영향을 더 잘 이해할 수 있습니다.

## <a name="on-prem-to-cloud-migrations"></a>온-프레미스에서 클라우드 마이그레이션으로

데이터를 SharePoint Server에서 SharePoint Online으로 마이그레이션하는 동안 중복 데이터가 한 번에 두 위치에 모두 있을 수 있습니다. 마이그레이션 중간에 삭제해야 하는 데이터가 있는 경우 먼저 마이그레이션을 완료한 다음 두 위치에서 데이터를 삭제하는 것이 좋습니다. 어느 위치에서든 내보낼 데이터를 쿼리할 수 있습니다.

## <a name="user-profile-data"></a>사용자 프로필 데이터

사용자 프로필 서비스를 사용하면 다양한 외부 소스에서 프로필 데이터를 가져올 수 있습니다. 이러한 사용자 프로필 데이터에 대한 쿼리 및 업데이트는 데이터가 마스터된 시스템에서 처리해야 합니다. 외부 시스템을 업데이트하는 경우 SharePoint Server에서 사용자 프로필을 다시 동기화해야 합니다.

다음 기존 단계에 따라 SharePoint Server 사용자 프로필에서 사용자의 개인 정보를 제거합니다.

1.  SharePoint Server 사용자 프로필에 제공되는 외부 시스템에서 사용자 정보를 제거합니다. 디렉터리 동기화를 사용하는 경우 사용자는 온-프레미스 활성 디렉터리 환경에서 제거해야 합니다.

2.  SharePoint Server에서 [프로필 동기화](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually)를 실행합니다.

3.  SharePoint Server에서 프로필을 삭제합니다. 삭제를 완료하면 SharePoint Server는 30일 이내에 사용자 프로필 데이터베이스에서 프로필을 완전히 제거합니다. 사용자의 프로필 페이지 및 개인 사이트가 삭제됩니다.

사용자의 프로필을 삭제한 후에도 일부 제한된 정보(예: 사용자 ID)는 사용자가 방문한 사이트 모음에 기록될 수 있습니다. 주어진 사이트 모음에서 이 데이터를 삭제하도록 선택한 경우 CSOM을 사용하여 이 작업을 수행할 수 있습니다. 샘플 스크립트는 다음과 같이 제공됩니다.

```powershell
$username = "<admin@company.sharepoint.com>"
$password = "password"
$url = "<https://site.sharepoint.com>"
$securePassword = ConvertTo-SecureString $Password -AsPlainText -Force

# the path here may need to change if you used e.g. C:Lib.
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.dll"
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.Runtime.dll"

# connect/authenticate to SharePoint Online and get ClientContext object.
$clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($url)
$credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($username, $securePassword)
$clientContext.Credentials = $credentials
if (!$clientContext.ServerObjectIsNull.Value)
{
    Write-Host "Connected to SharePoint Online site: '$Url'" -ForegroundColor Green
}

# Get user
$user = $clientContext.Web.SiteUsers.GetByLoginName("i:0#.f|membership|user@company.sharepoint.com")

# Redact user
$user.Email = "Redacted"
$user.Title = "Redacted"
$user.Update()
$clientContext.Load($user)
$clientContext.ExecuteQuery()

# Get users
$users = $clientContext.Web.SiteUsers

# Remove user from site
$users.RemoveById($user.Id)
$clientContext.Load($users)
$clientContext.ExecuteQuery()
```