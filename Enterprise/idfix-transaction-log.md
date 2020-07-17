---
title: Microsoft 365 IdFix 트랜잭션 로그
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 예제를 제공 하 고 Microsoft 365 IdFix 트랜잭션 로그의 명명 규칙 및 기본 로그 수준에 대해 설명 합니다.
ms.openlocfilehash: 199d765d640a30fa163f74e6b6029b228b41a63d
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774513"
---
# <a name="microsoft-365-idfix-transaction-log"></a><span data-ttu-id="52a94-103">Microsoft 365 IdFix 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="52a94-103">Microsoft 365 IdFix transaction log</span></span>

<span data-ttu-id="52a94-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="52a94-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="52a94-105">예제를 제공 하 고 Microsoft 365 IdFix 트랜잭션 로그의 명명 규칙 및 기본 로그 수준에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-105">Provides an example and describes the naming convention and default log level of the Microsoft 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="52a94-106">IdFix 트랜잭션 로그 위치</span><span class="sxs-lookup"><span data-stu-id="52a94-106">IdFix transaction log location</span></span>

<span data-ttu-id="52a94-107">Microsoft 365 IdFix 도구는 IdFix에서 **Apply** 를 클릭 하 고 변경 내용을 Active Directory 포리스트에 적용할 때마다 새 트랜잭션 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-107">The Microsoft 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="52a94-108">트랜잭션 로그는 IdFix를 설치한 동일한 폴더에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-108">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="52a94-109">기본적으로이 폴더는 C:\Deployment Tools\IDFix.입니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-109">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="52a94-110">트랜잭션 로그 파일 이름에 날짜 및 시간 스탬프 형식을 사용 하는 경우 (예: Verbose 6-1-2018 6-17-22 PM)에는 6:17:22 2018 년 6 월 1 일에 생성 된 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-110">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="52a94-111">Verbose 로깅 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-111">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="52a94-112">IdFix 트랜잭션 로그 로깅 수준</span><span class="sxs-lookup"><span data-stu-id="52a94-112">IdFix transaction log logging level</span></span>

<span data-ttu-id="52a94-113">트랜잭션 로그 파일 이름의 단어 verbose는 파일의 로깅 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-113">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="52a94-114">Verbose는 로그에서 정보의 양이 최대한 포착 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-114">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="52a94-115">기본 로깅 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-115">This is the default logging level.</span></span> <span data-ttu-id="52a94-116">현재로 서는 로깅 수준을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-116">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="52a94-117">IdFix 트랜잭션 로그 형식</span><span class="sxs-lookup"><span data-stu-id="52a94-117">IdFix transaction log format</span></span>

<span data-ttu-id="52a94-118">IdFix는 다음 예제와 같이 각 **업데이트** 작업의 결과를 트랜잭션 로그에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="52a94-118">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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