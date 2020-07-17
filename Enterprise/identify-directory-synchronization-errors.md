---
title: Microsoft 365에서 디렉터리 동기화 오류 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
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
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Microsoft 365 관리 센터에서 디렉터리 동기화 오류를 확인 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 57ca9ce125679931adcca93621474cec9ee9b82f
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842080"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="b3ee4-103">Microsoft 365에서 디렉터리 동기화 오류 보기</span><span class="sxs-lookup"><span data-stu-id="b3ee4-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="b3ee4-104">Microsoft 365 관리 센터에서 디렉터리 동기화 오류를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-104">You can view directory synchronization errors in the Microsoft 365 admin center.</span></span> <span data-ttu-id="b3ee4-105">사용자 개체 오류만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="b3ee4-106">PowerShell을 사용 하 여 오류를 보려면 [DirSyncProvisioningErrors를 사용 하 여 개체 확인](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-106">To view errors with PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a><span data-ttu-id="b3ee4-107">Microsoft 365 관리 센터에서 디렉터리 동기화 오류 보기</span><span class="sxs-lookup"><span data-stu-id="b3ee4-107">View directory synchronization errors in the Microsoft 365 admin center</span></span>

<span data-ttu-id="b3ee4-108">Microsoft 365 관리 센터에서 오류를 확인 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-108">To view any errors in the Microsoft 365 admin center:</span></span>
  
1. <span data-ttu-id="b3ee4-109">전역 관리자 계정으로 [Microsoft 365 관리 센터](https://admin.microsoft.com) 에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-109">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a global administrator account.</span></span> 
    
2. <span data-ttu-id="b3ee4-110">**홈** 페이지에서 **사용자 관리** 카드를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-110">On the **Home** page, you'll see the **User management** card.</span></span> 
    
    ![Microsoft 365 관리 센터의 사용자 관리 카드](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. <span data-ttu-id="b3ee4-112">카드에서 **AZURE AD Connect** 아래에 있는 **동기화 오류** 를 선택 하 여 **디렉터리 동기화 오류** 페이지에서 오류를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-112">On the card, choose **Sync errors** under **Azure AD Connect** to see the errors on the **Directory sync errors** page.</span></span>   
    
    ![디렉터리 동기화 오류 페이지의 예](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. <span data-ttu-id="b3ee4-114">오류에 대 한 정보 및 문제 해결 방법에 대 한 팁이 포함 된 세부 정보 창을 표시 하려면 오류를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-114">Choose any of the errors to display the details pane with information about the error and tips on how to fix it.</span></span>

   ![디렉터리 동기화 오류 세부 정보의 예](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
<span data-ttu-id="b3ee4-116">확인 후에는 [Microsoft 365에 대 한 디렉터리 동기화 문제 해결](fix-problems-with-directory-synchronization.md) 을 참조 하 여 식별 된 모든 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-116">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>

