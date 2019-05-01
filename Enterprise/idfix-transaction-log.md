---
title: Office 365 idfix 트랜잭션 로그
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 예제를 제공 하 고 Office 365 idfix 트랜잭션 로그의 명명 규칙 및 기본 로그 수준에 대해 설명 합니다.
ms.openlocfilehash: c652f8dcbc23a6f0165d894ce6317443db72ceee
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490944"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="4c46c-103">Office 365 idfix 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="4c46c-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="4c46c-104">예제를 제공 하 고 Office 365 idfix 트랜잭션 로그의 명명 규칙 및 기본 로그 수준에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-104">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="4c46c-105">idfix 트랜잭션 로그 위치</span><span class="sxs-lookup"><span data-stu-id="4c46c-105">IdFix transaction log location</span></span>

<span data-ttu-id="4c46c-106">Office 365 idfix 도구는 idfix에서 **Apply** 를 클릭 하 고 변경 내용을 Active Directory 포리스트에 적용할 때마다 새 트랜잭션 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-106">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="4c46c-107">트랜잭션 로그는 idfix를 설치한 동일한 폴더에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-107">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="4c46c-108">기본적으로이 폴더는 c:\deployment tools\idfix.입니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-108">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="4c46c-109">트랜잭션 로그 파일 이름에 날짜 및 시간 스탬프 형식을 사용 하는 경우 (예: Verbose 6-1-2018 6-17-22 pm)에는 2018 년 6 월 1 일에 생성 된 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-109">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="4c46c-110">Verbose 로깅 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-110">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="4c46c-111">idfix 트랜잭션 로그 로깅 수준</span><span class="sxs-lookup"><span data-stu-id="4c46c-111">IdFix transaction log logging level</span></span>

<span data-ttu-id="4c46c-112">트랜잭션 로그 파일 이름의 단어 verbose는 파일의 로깅 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-112">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="4c46c-113">Verbose는 로그에서 정보의 양이 최대한 포착 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-113">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="4c46c-114">기본 로깅 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-114">This is the default logging level.</span></span> <span data-ttu-id="4c46c-115">현재로 서는 로깅 수준을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-115">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="4c46c-116">idfix 트랜잭션 로그 형식</span><span class="sxs-lookup"><span data-stu-id="4c46c-116">IdFix transaction log format</span></span>

<span data-ttu-id="4c46c-117">idfix는 다음 예제와 같이 각 **업데이트** 작업의 결과를 트랜잭션 로그에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="4c46c-117">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```