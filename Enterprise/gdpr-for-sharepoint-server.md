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
# <a name="gdpr-for-sharepoint-server"></a><span data-ttu-id="8b0d9-103">SharePoint Server의 GDPR</span><span class="sxs-lookup"><span data-stu-id="8b0d9-103">GDPR for SharePoint Server</span></span>

<span data-ttu-id="8b0d9-104">개인 정보 보호의 일환으로 다음을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-104">As part of safeguarding personal information, we recommend the following:</span></span>

-   <span data-ttu-id="8b0d9-105">Azure Information Protection을 사용하여 데이터를 분류합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-105">Classify your data, using Azure Information Protection.</span></span>

-   <span data-ttu-id="8b0d9-p101">최소 권한 구성에서 SharePoint Server를 실행합니다. 자세한 내용은 [SharePoint Server에서 최소 권한 관리 계획](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) 및 [SahrePoint Server의 보안](https://docs.microsoft.com/ko-KR/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p101">Run SharePoint Server in a least-privileged configuration. See [Plan for least-privileged administration in SharePoint Server](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) and [Security for SharePoint Server](https://docs.microsoft.com/ko-KR/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server) for more information.</span></span>

-   <span data-ttu-id="8b0d9-108">[서버에서 BitLocker 암호화를 사용하도록 설정합니다](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).</span><span class="sxs-lookup"><span data-stu-id="8b0d9-108">[Enable BitLocker encryption on your servers](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).</span></span>

## <a name="user-generated-content"></a><span data-ttu-id="8b0d9-109">사용자 생성 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="8b0d9-109">User Generated content</span></span>

<span data-ttu-id="8b0d9-110">SharePoint Server 사이트 및 라이브러리에 포함된 사용자 생성 콘텐츠에 대한 기본 권장 접근법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-110">The basic recommended approach for user generated content contained in SharePoint Server sites and libraries is:</span></span>

-   <span data-ttu-id="8b0d9-111">Azure Information Protection을 사용하여 중요한 데이터를 레이블 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-111">Use Azure Information Protection to label sensitive data.</span></span>

-   <span data-ttu-id="8b0d9-112">[SharePoint Server 검색](https://docs.microsoft.com/SharePoint/search/search) 및 [eDiscovery](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server)를 사용하여 중요한 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-112">Use [SharePoint Server search](https://docs.microsoft.com/SharePoint/search/search) and [eDiscovery](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server) to retrieve sensitive data.</span></span>

<span data-ttu-id="8b0d9-113">파일 공유와 SharePoint 사이트 및 라이브러리에 대한 권장 접근법에는 다음 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-113">The recommended approach for files shares and SharePoint sites and libraries includes these steps:</span></span>

1.  <span data-ttu-id="8b0d9-114">**Azure Information Protection 스캐너를 설치하고 구성합니다.**</span><span class="sxs-lookup"><span data-stu-id="8b0d9-114">**Install and configure Azure Information Protection scanner.**</span></span>

    -   <span data-ttu-id="8b0d9-115">사용할 중요한 데이터 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-115">Decide which sensitive data types to use.</span></span>

    -   <span data-ttu-id="8b0d9-116">사용할 SharePoint 사이트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-116">Specify which SharePoint sites to use.</span></span>

2.  <span data-ttu-id="8b0d9-117">**검색 주기를 완료합니다.**</span><span class="sxs-lookup"><span data-stu-id="8b0d9-117">**Complete a discovery cycle.**</span></span>

    -   <span data-ttu-id="8b0d9-118">검색 모드에서 스캐너를 실행하고 검색 결과의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-118">Run the scanner in discovery mode and validate the findings.</span></span>

    -   <span data-ttu-id="8b0d9-119">필요에 따라 조건 및 중요한 정보 유형을 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-119">If needed, optimize the conditions and sensitive information types.</span></span>

    -   <span data-ttu-id="8b0d9-120">레이블 자동 적용의 예상된 영향을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-120">Assess the expected impact of automatically applying labels.</span></span>

3.  <span data-ttu-id="8b0d9-121">**Azure Information Protection 스캐너를 실행하여 적격 문서에 레이블을 적용합니다**.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-121">**Run the Azure Information Protection scanner to apply labels to qualifying documents**.</span></span>

4.  <span data-ttu-id="8b0d9-122">**보호하려면:**</span><span class="sxs-lookup"><span data-stu-id="8b0d9-122">**For protection:**</span></span>

    <span data-ttu-id="8b0d9-p102">a. Exchange 데이터 손실 방지 규칙을 구성하여 원하는 레이블로 문서를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p102">a.  Configure Exchange data loss prevention rules to protect documents with the desired label.</span></span>

    <span data-ttu-id="8b0d9-p103">b. 파일에 액세스할 수 있는 사용자를 제한할 수 있는 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p103">b.  Be sure permissions to limit who can access files.</span></span>

    <span data-ttu-id="8b0d9-p104">c. SharePoint의 경우 라이브러리에 IRM-보호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p104">c.  For SharePoint, use IRM-protection for libraries.</span></span>

5.  <span data-ttu-id="8b0d9-129">**모니터링하려면 Windows Server 로그를 SIEM 도구와 통합합니다.**</span><span class="sxs-lookup"><span data-stu-id="8b0d9-129">**For monitoring, integrate Windows Server logs with a SIEM tool.**</span></span>

    <span data-ttu-id="8b0d9-p105">a. 데이터 주체 요청에 대한 개인 데이터를 찾으려면 검색 센터 또는 eDiscovery를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p105">a.  To find personal data for data subject requests, use Search Center or eDiscovery.</span></span>

<span data-ttu-id="8b0d9-p106">레이블을 중요한 데이터에 적용할 때 보호로 구성되지 않는 레이블을 사용하는지 확인합니다. 보호에는 서비스가 파일의 중요한 데이터를 탐지하지 못하게 하는 암호화를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p106">When applying labels to sensitive data, be sure to use a label that is not configured with protection. Protection includes encryption which prevents services from detecting sensitive data in the files.</span></span>

<span data-ttu-id="8b0d9-134">Azure Information Protection 스캐너를 사용하여 개인 데이터를 찾고 레이블 지정하는 방법에 대한 자세한 내용은 http://aka.ms/gdprpartners)에서 [Microsoft GDPR 데이터 검색 도구 키트](http://aka.ms/gdprpartners)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-134">For more information on using Azure Information Protection scanner to find and label personal data, see the [Microsoft GDPR Data Discovery Toolkit](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners).</span></span>

<span data-ttu-id="8b0d9-p107">조건을 위한 스캐너 구성 및 Office 365 DLP(데이터 손실 방지) 중요한 정보 유형의 사용에 대한 자세한 내용은 [Azure Information Protection의 자동 및 권장 분류를 위한 조건을 구성하는 방법](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification)을 참조하세요. 새 Office 365 중요한 정보 유형은 스캐너에서 즉시 사용할 수 없으며 사용자 지정 중요한 정보 유형은 스캐너에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p107">For information on configuring the scanner for conditions and using the Office 365 data loss prevention (DLP) sensitive information types, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification). Note that new Office 365 sensitive information types will not be immediately available to use with the scanner and custom sensitive information types cannot be used with the scanner.</span></span>

## <a name="removing-personal-information-from-office-files"></a><span data-ttu-id="8b0d9-137">Office 파일에서 개인 정보 제거</span><span class="sxs-lookup"><span data-stu-id="8b0d9-137">Removing personal information from Office files</span></span>

<span data-ttu-id="8b0d9-p108">SharePoint 문서 라이브러리에 저장된 Office 파일의 개인 정보(예: Word 문서의 메타데이터 또는 설명)를 수동으로 제거해야 합니다. 다음 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p108">Removing personal information (such as metadata or comments in a Word document) from Office files that are stored in a SharePoint document library must be done manually. Follow these steps:</span></span>

1.  <span data-ttu-id="8b0d9-140">SharePoint Server의 문서 복사본을 로컬 디스크에 다운도르합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-140">Download a copy of the document from SharePoint Server to your local disk.</span></span>

2.  <span data-ttu-id="8b0d9-141">SharePoint 문서 라이브러리에서 문서를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-141">Delete the document from the SharePoint document library.</span></span>

3.  <span data-ttu-id="8b0d9-142">[문서를 검사하여 숨겨진 데이터 및 개인 정보 제거](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F)의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-142">Follow the steps in [Remove hidden data and personal information by inspecting documents](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F).</span></span>

4.  <span data-ttu-id="8b0d9-143">문서를 SharePoint 문서 라이브러리에 다시 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-143">Upload the document back to the SharePoint document library.</span></span>

## <a name="telemetry-and-log-files"></a><span data-ttu-id="8b0d9-144">원격 분석 및 로그 파일</span><span class="sxs-lookup"><span data-stu-id="8b0d9-144">Telemetry and log files</span></span>

### <a name="uls-logs"></a><span data-ttu-id="8b0d9-145">ULS 로그</span><span class="sxs-lookup"><span data-stu-id="8b0d9-145">ULS Logs</span></span>

<span data-ttu-id="8b0d9-p109">SharePoint Server 트랙의 ULS(통합 로깅 서비스) 및 사용 현황 로깅은 다양한 시스템 기능을 추적하며 사용자 정보를 포함할 수 있습니다. ULS 로그 및 사용 현황 로그는 텍스트 파일이며 다양한 검색 도구를 사용하여 검색할 수 있습니다. [Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/ko-KR/powershell/module/sharepoint-server/merge-splogfile)은 팜의 여러 서버에 있는 ULS 로그의 레코드를 반환하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p109">Unified Logging Service (ULS) and Usage logging in SharePoint Server track a variety of system functions and can contain user information. ULS logs and usage logs are text files and can be searched using a variety of searching tools. The [Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/ko-KR/powershell/module/sharepoint-server/merge-splogfile) provides a way to return records from the ULS logs on multiple servers in a farm.</span></span>

<span data-ttu-id="8b0d9-p110">로그 보존 정책을 비즈니스 목적에 필요한 최소값으로 설정하는 것이 좋습니다. SharePoint Server에서 로깅을 구성하는 방법에 대한 자세한 내용은[ SharePoint Server에서 진단 로깅 구성](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p110">Consider setting log retention policies to the minimum value needed for your business purposes. For information about configuring logging in SharePoint Server, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

<span data-ttu-id="8b0d9-151">일부 시스템 이벤트는 Windows 이벤트 로그에도 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-151">Note that some system events are also logged to the Windows Event Log.</span></span>

### <a name="usage-database"></a><span data-ttu-id="8b0d9-152">사용 현황 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="8b0d9-152">Usage Database</span></span>

<span data-ttu-id="8b0d9-p111">SharePoint Server 사용 현황 데이터베이스(기본 이름 WSS_Logging)에는 ULS 로그에서 발견되는 정보의 하위 집합이 포함되어 있습니다. 데이터베이스에 있는 데이터의 최대 보존 기간은 30일입니다. 비즈니스 요구 사항에 따라 허용되는 최단 기간 동안 구성하는 것이 좋습니다. 자세한 내용은 [SharePoint Server에서 진단 로깅 구성](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p111">The SharePoint Server Usage database (default name WSS_Logging) contains a subset of the information found in the ULS logs. The maximum retention of data in this database is 30 days. We recommend that you configure it for the shortest duration allowable by your business needs. For more information, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

## <a name="personal-information-and-search"></a><span data-ttu-id="8b0d9-157">개인 정보 및 검색</span><span class="sxs-lookup"><span data-stu-id="8b0d9-157">Personal information and search</span></span>

<span data-ttu-id="8b0d9-158">검색 쿼리 기록 및 사용 현황 레코드에는 사용자 이름에 대한 참조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-158">The search query history and usage records contain references to user names.</span></span>

### <a name="query-history-and-favorite-queries"></a><span data-ttu-id="8b0d9-159">쿼리 기록 및 즐겨찾기 쿼리</span><span class="sxs-lookup"><span data-stu-id="8b0d9-159">Query history and favorite queries</span></span>

<span data-ttu-id="8b0d9-p112">SharePoint Server에서 쿼리 기록 및 ‘즐겨찾기’ 쿼리는 자동으로 365일 후에 만료됩니다. 사용자가 조직을 떠나면 다음 단계를 사용하여 쿼리 기록에서 사용자 이름에 대한 참조를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p112">In SharePoint Server 2013 and SharePoint Server 2016, query histories and ‘favorite’ queries automatically expire after 365 days. If a user leaves your organization, it is possible to remove references to a user's name from the query history using the steps below..</span></span>

<span data-ttu-id="8b0d9-162">다음 SQL 쿼리는 SharePoint Server에 적용되며 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-162">The following SQL queries apply to SharePoint 2013 and SharePoint 2016 and make it possible to:</span></span>

-   <span data-ttu-id="8b0d9-163">사용자의 쿼리 기록 또는 즐겨찾기 쿼리 내보내기</span><span class="sxs-lookup"><span data-stu-id="8b0d9-163">Export a user’s query history or favorite queries</span></span>

-   <span data-ttu-id="8b0d9-164">쿼리 기록의 사용자 이름에 대한 참조 제거</span><span class="sxs-lookup"><span data-stu-id="8b0d9-164">Remove references to user names in the query history</span></span>

#### <a name="export-a-users-queries-since-a-specific-date"></a><span data-ttu-id="8b0d9-165">특정 날짜 후 사용자의 쿼리 내보내기</span><span class="sxs-lookup"><span data-stu-id="8b0d9-165">Export a user’s queries since a specific date</span></span> 

<span data-ttu-id="8b0d9-166">@StartTime 후 @UserName에 의해 수행된 링크 스토어 쿼리 로그 테이블에서 쿼리를 내보내려면 다음 절차를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-166">Use the following procedure to export queries from the Link Store query log tables, performed by @UserName since @StartTime.</span></span>

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

#### <a name="export-a-users-queries-from-the-past-100-days"></a><span data-ttu-id="8b0d9-167">지난 100일 동안의 사용자 쿼리 내보내기</span><span class="sxs-lookup"><span data-stu-id="8b0d9-167">Export a user’s queries from the past 100 days</span></span>

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a><span data-ttu-id="8b0d9-168">사용자의 즐겨찾기 쿼리 내보내기</span><span class="sxs-lookup"><span data-stu-id="8b0d9-168">Export a user’s favorite queries</span></span>

<span data-ttu-id="8b0d9-169"><DateTime> 후 @UserName에 의해 수행된 검색 관리 DB 개인 결과 테이블에서 사용자의 즐겨찾기 쿼리를 내보내려면 다음 정차를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-169">Use the following procedure to export a user's favorite queries from the Search Admin DB personal result tables, performed by @UserName, since <DateTime>.</span></span>

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

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a><span data-ttu-id="8b0d9-170">지난 100일 동안 사용자의 즐겨찾기 쿼리 내보내기</span><span class="sxs-lookup"><span data-stu-id="8b0d9-170">Export a user’s favorite queries from the past 100 days</span></span> 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a><span data-ttu-id="8b0d9-171">X일보다 오래된 사용자 이름에 대한 참조 제거</span><span class="sxs-lookup"><span data-stu-id="8b0d9-171">Remove references to user names that are more than X days old</span></span>

<span data-ttu-id="8b0d9-p113">다음 절차를 통해 링크 스토어 쿼리 로그 테이블에서 @Days보다 오래된 *모든* 사용자 이름에 대한 참조를 제거합니다. 이 절차는 @LastCleanupTime에 도달하기 전의 참조만 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p113">Use the following procedure to remove references to *all* user names that are more than @Days old, from the Links Store query log tables. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

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

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a><span data-ttu-id="8b0d9-174">X일보다 오래된 특정 사용자 이름에 대한 참조 제거</span><span class="sxs-lookup"><span data-stu-id="8b0d9-174">Remove references to a specific user name that’s more than X days old</span></span>

<span data-ttu-id="8b0d9-p114">다음 절차를 사용하여 참조가 @Days일보다 오래된 링크 스토어 쿼리 로그 테이블에서 *특정* 사용자 이름에 대한 참조를 제거합니다. 절차는 @LastCleanupTime에 도달하기 전의 참조만 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p114">Use the following procedure to remove references to a *specific* user name from the Links Store query log tables, where the references are more than @Days old. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

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

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a><span data-ttu-id="8b0d9-177">날짜와 지난 30일 동안의 쿼리 기록에 있는 모든 사용자 이름에 대한 참조 제거</span><span class="sxs-lookup"><span data-stu-id="8b0d9-177">Remove references to all user names in the query history from a date and up to the past 30 days</span></span>

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a><span data-ttu-id="8b0d9-178">사용 현황 레코드 삭제</span><span class="sxs-lookup"><span data-stu-id="8b0d9-178">Delete usage records</span></span>

<span data-ttu-id="8b0d9-p115">SharePoint Server는 3년 후 자동으로 사용 현황 레코드를 삭제합니다. 다음 절차를 사용해 이러한 레코드를 수동으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p115">SharePoint Server 2013 and SharePoint Server 2016 automatically deletes usage records after 3 years. You can manually delete such records using the procedure below:</span></span>

<span data-ttu-id="8b0d9-181">삭제된 문서와 연관된 모든 사용 현황 레코드를 삭제하려면:</span><span class="sxs-lookup"><span data-stu-id="8b0d9-181">To delete all usage records associated with deleted documents:</span></span> 

1.  <span data-ttu-id="8b0d9-182">최신 SharePoint 업데이트가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-182">Ensure that you have the latest SharePoint update installed.</span></span> 

2.  <span data-ttu-id="8b0d9-183">SharePoint 관리 셀을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-183">Start a SharePoint Management shell.</span></span>

3.  <span data-ttu-id="8b0d9-184">사용 현황 분석 중지 및 지우기:</span><span class="sxs-lookup"><span data-stu-id="8b0d9-184">Stop and Clear the Usage Analytics analysis:</span></span> 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  <span data-ttu-id="8b0d9-185">다시 시작하려면 분석을 기다립니다(24시간 정도 소요될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="8b0d9-185">Wait for the analysis to start again (might take up to 24 hours).</span></span> 

5.  <span data-ttu-id="8b0d9-p116">다음번 분석 실행 시 분석 보고 데이터베이스에서 모든 레코드를 덤프합니다. 항목이 많은 대용량 데이터베이스의 경우 이 전체 덤프는 시간이 다소 소요될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p116">On the next run of the analysis, it will dump all records from the Analytics Reporting database. This full dump may take a while for a large database with many entries.</span></span>

6.  <span data-ttu-id="8b0d9-p117">10일 동안 기다립니다. 분석을 매일 실행하며 삭제된 문서와 연관된 레코드는 10번째 실행한 후 제거됩니다. 많은 레코드를 삭제해야 하는 경우 평소보다 시간이 더 소요될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p117">Wait for 10 days. The analysis runs daily, and records associated with deleted documents will be removed after the 10^th^ run. This run may take longer than normal if many records need to be deleted.</span></span> 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a><span data-ttu-id="8b0d9-191">SharePoint Server 2010의 개인 정보 및 검색</span><span class="sxs-lookup"><span data-stu-id="8b0d9-191">Personal information and search in SharePoint Server 2010</span></span>

#### <a name="fast-search-server-2010-for-sharepoint"></a><span data-ttu-id="8b0d9-192">FAST Search Server 2010 for SharePoint</span><span class="sxs-lookup"><span data-stu-id="8b0d9-192">FAST Search Server 2010 for SharePoint</span></span> 

<span data-ttu-id="8b0d9-p118">인덱스에 파일을 저장하는 것 외에 FAST Search Server 2010 추가 기능은 SFixML이라는 중간 형식에 파일을 저장합니다. FiXML 파일은 기본적으로 매일 새벽 3시에서 5시 사이에 정기적으로 압축됩니다. 압축하면 FiXML 파일에서 삭제된 파일이 자동으로 제거됩니다. 삭제된 사용자 또는 문서에 속한 정보를 적절한 시기에 제거하려면 항상 압축을 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p118">In addition to storing files in the index, the FAST Search Server 2010 Add-On also stores files in an intermediate format called FixML. FiXML files are compacted regularly, by default between 3 am and 5 am every night. Compaction removes deleted files from the FiXML files automatically. To ensure timely removal of information belonging to deleted users or documents, ensure that compaction is always enabled.</span></span>

### <a name="hybrid-search"></a><span data-ttu-id="8b0d9-197">하이브리드 검색</span><span class="sxs-lookup"><span data-stu-id="8b0d9-197">Hybrid Search</span></span> 

<span data-ttu-id="8b0d9-p119">하이브리드 검색 솔루션에 대한 권장 사항은 SharePoint Server 또는 SharePoint Online의 검색에 대한 권장 사항과 같습니다. 다음은 2가지 하이브리드 검색 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p119">The recommended actions for hybrid search solutions are the same as for search in SharePoint Server or SharePoint Online. There are two hybrid search solutions:</span></span>

<span data-ttu-id="8b0d9-p120">**클라우드 하이브리드 검색 솔루션** - SharePoint용 클라우드 하이브리드 검색 솔루션을 통해 Office 365의 검색 인덱스에서 온-프레미스 콘텐츠를 포함한 크롤링된 모든 콘텐츠를 인덱싱합니다. 사용자가 Office 365에서 검색 인덱스를 쿼리하면 온-프레미스 및 Office 365의 검색 결과를 모두 얻습니다. SharePoint Server 환경에서 문서가 삭제되면 Office 365의 검색 인덱스에서도 삭제됩니다. [클라우드 하이브리드 검색 솔루션](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) 및 [클라우드 하이브리드 검색에서 구성 요소 및 데이터베이스 상호 작용을 검색하는 방법](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint)을 자세히 읽어보면 GDPR이 하이브리드 환경에 미치는 영향을 더 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p120">**The cloud hybrid search solution -** With the cloud hybrid search solution for SharePoint, you index all your crawled content, including on-premises content, in your search index in Office 365. When users query your search index in Office 365, they get search results from both on-premises and Office 365 content. When documents are deleted from the SharePoint Server environment, they are also deleted from the search index in Office 365. [Read more about the cloud hybrid search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) and [how search components and databases interact in cloud hybrid search](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

<span data-ttu-id="8b0d9-p121">**하이브리드 페더레이션된 검색 솔루션** - 하이브리드 연결된 검색 솔루션을 사용하면 SharePoint Server의 인덱스와 Office 365의 인덱스를 둘 다 사용하게 됩니다. SharePoint Server 및 SharePoint Online Search 서비스는 둘 다 다른 환경의 검색 인덱스를 쿼리하고, 연결된 결과를 반환할 수 있습니다. 사용자가 검색센터에서 검색하면 검색 결과가 SharePoint Server의 검색 인덱스와 Office 365의 검색 인덱스에서 제공됩니다. [하이브리드 페더레이션된 검색 솔루션을 자세히 읽어보면](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) GDPR이 하이브리드 환경에 미치는 영향을 더 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p121">**The hybrid federated search solution -** With the hybrid federated search solution, you use both your index in SharePoint Server and your index in Office 365. Both SharePoint Server and SharePoint Online Search services can query the search index in the other environment and return federated results. When users search from a Search Center, the search results come from both your search index in SharePoint Server and your search index in Office 365. [Read more about the hybrid federated search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

## <a name="on-prem-to-cloud-migrations"></a><span data-ttu-id="8b0d9-208">온-프레미스에서 클라우드 마이그레이션으로</span><span class="sxs-lookup"><span data-stu-id="8b0d9-208">On Prem to Cloud Migrations</span></span>

<span data-ttu-id="8b0d9-p122">데이터를 SharePoint Server에서 SharePoint Online으로 마이그레이션하는 동안 중복 데이터가 한 번에 두 위치에 모두 있을 수 있습니다. 마이그레이션 중간에 삭제해야 하는 데이터가 있는 경우 먼저 마이그레이션을 완료한 다음 두 위치에서 데이터를 삭제하는 것이 좋습니다. 어느 위치에서든 내보낼 데이터를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p122">While migrating data from SharePoint Server to SharePoint Online, duplicate data may exist in both locations for a time. If you have data that you need to delete that is in mid-migration, we recommend that you complete the migration first, and then delete the data from both locations. You can query data for export from either location.</span></span>

## <a name="user-profile-data"></a><span data-ttu-id="8b0d9-212">사용자 프로필 데이터</span><span class="sxs-lookup"><span data-stu-id="8b0d9-212">User Profile data</span></span>

<span data-ttu-id="8b0d9-p123">사용자 프로필 서비스를 사용하면 다양한 외부 소스에서 프로필 데이터를 가져올 수 있습니다. 이러한 사용자 프로필 데이터에 대한 쿼리 및 업데이트는 데이터가 마스터된 시스템에서 처리해야 합니다. 외부 시스템을 업데이트하는 경우 SharePoint Server에서 사용자 프로필을 다시 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p123">The User Profile Service allows for import of profile data from a variety of external sources. Queries for and update of such user profile data should be handled in the systems in which the data is mastered. If you make updates to the external system, be sure to synchronize the user profiles in SharePoint Server again.</span></span>

<span data-ttu-id="8b0d9-216">다음 기존 단계에 따라 SharePoint Server 사용자 프로필에서 사용자의 개인 정보를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-216">Follow these basic steps to remove a user’s personal information from their SharePoint Server user profile:</span></span>

1.  <span data-ttu-id="8b0d9-p124">SharePoint Server 사용자 프로필에 제공되는 외부 시스템에서 사용자 정보를 제거합니다. 디렉터리 동기화를 사용하는 경우 사용자는 온-프레미스 활성 디렉터리 환경에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p124">Remove the user information from any external systems that feed into the SharePoint Server user profile. If you are using directory synchronization, the user must be removed from the on-premises Active Directory environment.</span></span>

2.  <span data-ttu-id="8b0d9-219">SharePoint Server에서 [프로필 동기화](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-219">Run a [profile synchronization](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually) on SharePoint Server.</span></span>

3.  <span data-ttu-id="8b0d9-p125">SharePoint Server에서 프로필을 삭제합니다. 삭제를 완료하면 SharePoint Server는 30일 이내에 사용자 프로필 데이터베이스에서 프로필을 완전히 제거합니다. 사용자의 프로필 페이지 및 개인 사이트가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p125">Delete the profile from SharePoint Server. Once this is done, SharePoint Server will fully remove the profile from the User Profile Database in 30 days. The user’s profile page and personal site will be deleted.</span></span>

<span data-ttu-id="8b0d9-p126">사용자의 프로필을 삭제한 후에도 일부 제한된 정보(예: 사용자 ID)는 사용자가 방문한 사이트 모음에 기록될 수 있습니다. 주어진 사이트 모음에서 이 데이터를 삭제하도록 선택한 경우 CSOM을 사용하여 이 작업을 수행할 수 있습니다. 샘플 스크립트는 다음과 같이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b0d9-p126">After deleting a user’s profile, some limited information (such as user ID) may still be recorded in site collections that the user has visited. If you choose to delete this data from a given site collection, this can be done using CSOM. A sample script is provided below:</span></span>

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