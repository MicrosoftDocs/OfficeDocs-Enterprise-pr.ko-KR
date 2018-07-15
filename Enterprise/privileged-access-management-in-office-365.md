---
title: Office 365의에서 관리 기능에 액세스 권한
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Office 365의 액세스 권한을된 관리 기능에 대 한 자세한 내용은이 항목을 사용 하 여
ms.openlocfilehash: b2db3e16e53cca7deb2bf8fbff61b5b981f42fa6
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319209"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="cadb5-103">Office 365의에서 관리 기능에 액세스 권한</span><span class="sxs-lookup"><span data-stu-id="cadb5-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cadb5-104">이 항목에서는 Office 365 e 5 및 고급 준수 Sku에만 현재 제공 되는 공용 베타 기능에 대 한 배포 및 구성 지침에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="cadb5-p101">액세스 권한 관리 Office 365에서 권한이 부여 된 관리 작업을 통해 세분화 된 액세스 제어를 허용 합니다.  기존 관리자가 권한이 부여 된 사용자 계정은 중요 한 데이터에 대 한 순위 액세스 또는 중요 한 구성 설정에 대 한 액세스를 사용할 수 있는 침해에서 조직을 보호 하는 것이 도움이 됩니다. 권한이 부여 된 액세스 관리를 사용 하도록 설정한 후 사용자가 높은 범위가 지정 되며 시간 제한이 있는 승인 워크플로 통해 관리자 권한 및 권한 있는 작업을 완료 하려면 적시에 액세스를 요청 해야 합니다. 이 사용자가 액세스할 수 방금-만큼 충분히-중요 한 데이터 나 중요 한 구성 설정의 노출 시 키 지 않고, 수행 중인 작업을 수행할 수 있습니다. Office 365에서 권한이 부여 된 액세스 관리를 사용 하도록 설정 하면 조직 0 순위 권한으로 작동 하 고 이러한 순위 관리 액세스로 인해 발생 하는 취약점에 대 한 방어 계층을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="cadb5-110">이 항목에 사용 하도록 설정 하 고 Office 365 조직에서 권한이 부여 된 액세스 관리를 구성 하는 과정을 안내 합니다 및 요청, 승인 및 기능 관리에 대 한 참조 (영문) 지침으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="cadb5-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cadb5-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="cadb5-112">제한 된 기능</span><span class="sxs-lookup"><span data-stu-id="cadb5-112">Limited functionality</span></span>
<span data-ttu-id="cadb5-p102">공개 베타 하는 동안 액세스 권한이 부여 된 관리 기능을 Office 365의 [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) 통해 사용할 수만 있습니다. 권한 관리 하는 방법을 다룹니다 Exchange 관리 cmdlet의 수준에서 작업 정의 액세스합니다. Office 365 놓을 나중에 권한이 부여 된 액세스 기능 관리 포털을 통해 사용할 수 및 다른 Office 365 작업 서비스에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="cadb5-116">Exchange Online PowerShell 연결</span><span class="sxs-lookup"><span data-stu-id="cadb5-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="cadb5-117">이 항목의 구성 단계 과정을 안내 합니다 활성화 및 Exchange Online PowerShell을 사용 하 여 Office 365에서 권한이 부여 된 액세스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="cadb5-118">[다단계 인증을 사용 하 여 Exchange Online powershell 연결을](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) 사용 하도록 설정 하 고 조직에 대 한 액세스 권한을된 구성 하 여 Office 365 자격 증명으로 Exchange Online PowerShell에 연결 하려면의 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="cadb5-p103">Exchange Online PowerShell에 연결 하는 동안 액세스 권한을된 사용 하도록 설정 하는 단계를 사용 하 여 Office 365 조직에 대해 다단계 인증을 사용할 필요가 없습니다. 다단계 인증을 통해 연결 요청에 서명 하는 것에 대 한 권한이 부여 된 액세스에 사용 되는 OAuth 토큰을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="cadb5-121">설정 하 고 액세스 권한을된 관리 구성</span><span class="sxs-lookup"><span data-stu-id="cadb5-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="cadb5-122">1 단계-승인자의 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="cadb5-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="cadb5-p104">Office 365 관리 포털에서 **그룹**을 선택 > **그룹 추가**누른 다음 권한이 부여 된 기본 액세스 승인자에 대 한 메일 사용 가능 보안 그룹을 만듭니다. 완료 되 면 만들고 승인자 그룹을 저장 하려면 **추가** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Office 365 관리 포털에 액세스 권한을된 승인자 화면](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="cadb5-p105">이 시간에 관리자 액세스 권한 가진 사용자만가 Office 365 특수 액세스에서 요청을 승인 수 있습니다. 나중에 승인자 그룹의 구성원 인 모든 사용자 액세스 요청 승인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="cadb5-128">2 단계-Office 365에 대 한 액세스 권한을된 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="cadb5-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="cadb5-129">권한이 부여 된 액세스 권한이 부여 된 액세스 관리 액세스 제어에서 제외 하려는 시스템 계정 집합을 포함 하 여 기본 승인자 그룹 명시적으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="cadb5-130">액세스 권한을된 사용 하도록 설정 하 고 승인자의 그룹을 할당 하려면 Exchange Online PowerShell에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="cadb5-131">예제:</span><span class="sxs-lookup"><span data-stu-id="cadb5-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="cadb5-132">그러나 기능 사용 가능 조직 내에서 특정 자동화가 되도록 시스템 계정 액세스 권한을된 의존 관계 없이 사용할 수 있는, 것이 좋습니다 이러한 제외 뛰어난 수 및 승인 고 감사를 수행 해야 허용 된 정기적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="cadb5-133">3 단계-승인 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="cadb5-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="cadb5-p106">승인 정책을 사용 하면 개별 작업에서 범위가 지정 된 특정 승인 요구 사항을 정의할 수 있습니다. 승인 유형 옵션은 **자동** 또는 **수동**입니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="cadb5-136">다음 명령을 실행 Exchange 온라인 승인 정책을 정의 하는 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="cadb5-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="cadb5-137">예제:</span><span class="sxs-lookup"><span data-stu-id="cadb5-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="cadb5-138">Office 365 조직에서 권한이 부여 된 액세스를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="cadb5-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="cadb5-139">요청 하는 작업을 실행 하기 상승 권한 부여</span><span class="sxs-lookup"><span data-stu-id="cadb5-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="cadb5-p107">한번 사용 하도록 설정, 권한이 부여 된 액세스는 연결 된 승인 정책 정의 된 모든 작업을 실행 하는 것에 대 한 승인 필요 합니다. 필요에 포함 된 작업을 실행 하는 사용자는 승인 정책을 요청 해야 하 고 작업을 실행 하는 데 필요한 사용 권한이 하기 위해 액세스 승인에 게 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="cadb5-142">다음 명령을 실행 Exchange Online을 만들고 승인자의 그룹에 대 한 승인 요청을 제출 하는 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="cadb5-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="cadb5-143">예제:</span><span class="sxs-lookup"><span data-stu-id="cadb5-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="cadb5-144">권한 상승 요청 상태 보기</span><span class="sxs-lookup"><span data-stu-id="cadb5-144">View status of elevation requests</span></span>
<span data-ttu-id="cadb5-145">승인 요청을 만든 후 상승 요청 상태를 검토할 수 있습니다 사용 하 여 연결 된 요청 id</span><span class="sxs-lookup"><span data-stu-id="cadb5-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="cadb5-146">다음 명령을 실행 Exchange 온라인 PowerShell 특정 요청 ID에 대 한 승인 요청 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="cadb5-147">예제:</span><span class="sxs-lookup"><span data-stu-id="cadb5-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="cadb5-148">권한 상승 권한 부여 요청이 승인</span><span class="sxs-lookup"><span data-stu-id="cadb5-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="cadb5-149">관련 승인자 그룹의 구성원이 전자 메일 알림을 받게 됩니다 및 요청 ID와 연결 된 요청을 승인할 수를 승인 요청을 만들 때</span><span class="sxs-lookup"><span data-stu-id="cadb5-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="cadb5-150">다음 명령을 실행 Exchange 온라인는 상승 인증 요청을 승인 하는 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="cadb5-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="cadb5-151">예제:</span><span class="sxs-lookup"><span data-stu-id="cadb5-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="cadb5-152">권한 상승 인증 요청이 거부</span><span class="sxs-lookup"><span data-stu-id="cadb5-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="cadb5-153">그룹의 구성원은 관련 승인자 요청 ID와 연결 된 요청을 거부할 수를 승인 요청을 만들 때</span><span class="sxs-lookup"><span data-stu-id="cadb5-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="cadb5-154">다음 명령을 실행 Exchange Online PowerShell는 상승 인증 요청을 거부 하려면:</span><span class="sxs-lookup"><span data-stu-id="cadb5-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="cadb5-155">예제:</span><span class="sxs-lookup"><span data-stu-id="cadb5-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="cadb5-156">작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-156">Running the task</span></span>
<span data-ttu-id="cadb5-p108">승인 권한이 부여 되 면 요청 하는 사용자 의도 한 작업을 실행할 수 있고 권한이 부여 된 액세스 권한을 부여 하 고 사용자를 대신 하 여 작업을 실행 됩니다. 승인의 요청에 대해 유효 기간 (기본 기간은 4 시간)을 하는 동안 요청자 수 의도 한 작업을 여러 번 실행 합니다. 이러한 모든 실행 기록 하 고 보안 및 규정 준수 감사를 위해 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="cadb5-160">Office 365에 대 한 액세스 권한을된 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="cadb5-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="cadb5-p109">필요한 경우에 Office 365에서 권한이 부여 된 액세스 관리를 비활성화할 수 있습니다. 권한 사용 하지 않도록 설정 액세스 삭제 되지 않습니다 모든 관련된 승인 정책 또는 승인자 그룹.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="cadb5-163">다음 명령을 실행 Exchange Online Powershell 액세스 권한을된 사용 하지 않도록 설정 하려면:</span><span class="sxs-lookup"><span data-stu-id="cadb5-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="cadb5-164">다음은 Microsoft Graph in Microsoft Azure에 대 한 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="cadb5-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cadb5-165">이 섹션에서는 Office 365 e 5 및 고급 준수 Sku에서 현재 사용할 수만 공개 베타 Microsoft Graph 기능에 대 한 배포 및 구성 지침에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-165">This section covers deployment and configuration guidance for a public beta Microsoft Graph feature only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="cadb5-p110">Microsoft Azure의 Microsoft Graph에 대 한 관리 되는 액세스는 세분화 된 자신의 Office 365 데이터에 대 한 제어 수준을 강력 하는 조직에 도움이 되는 서비스입니다. 이 시스템에는 응용 프로그램 개발자가 해당 데이터와 의견을 대장간을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="cadb5-p111">이 시스템 액세스 권한이 부여 된 Office 365를 사용 하 여 관리 감독을 사용 하 여 Office 365 데이터에 대 한 범위가 지정 된 액세스를 허용 하는 승인 워크플로 통해 자신의 데이터에 대 한 제어를 가정 합니다. 응용 프로그램을 설치 하 고 Office 365 데이터에 액세스할 수 있어야 하는 경우 데이터에 대 한 요청 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="cadb5-170">요청 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="cadb5-170">View request details</span></span>
<span data-ttu-id="cadb5-171">Office 365 데이터에 대 한 액세스 요청에 대 한 세부 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="cadb5-172">다음 명령을 실행 Exchange Online Powershell 데이터 요청을 보려면:</span><span class="sxs-lookup"><span data-stu-id="cadb5-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="cadb5-173">예제 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="cadb5-174">데이터 액세스 요청을 승인</span><span class="sxs-lookup"><span data-stu-id="cadb5-174">Approve data access requests</span></span>
<span data-ttu-id="cadb5-175">표준 액세스 권한을된 승인 cmdlet을 통해 모든 데이터 액세스 요청을 승인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="cadb5-176">다음 명령을 실행 Exchange 온라인 특정 요청자에 대 한 모든 데이터 요청을 승인 하는 Powershell:</span><span class="sxs-lookup"><span data-stu-id="cadb5-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="cadb5-177">예제:</span><span class="sxs-lookup"><span data-stu-id="cadb5-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="cadb5-178">도움말 및 의견을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-178">Getting help and providing feedback</span></span>
<span data-ttu-id="cadb5-p112">공개 베타 하는 동안 필요에 따른 버그를 발견할 수도 있습니다 피드백 및 액세스 권한을된 관리 개선할 수 있는 방법에 대 한 추천 항목으로 확인 되었습니다. 여러분의 의견을 값 하 고 촉진 우리와 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="cadb5-181">[Office 미리 보기 Yammer 그룹](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)에서 여러분의 의견 ad 추천 항목을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="cadb5-182">[Office 미리 보기 VSO](https://office-previews.visualstudio.com/previews)에서 영역 경로 "Office 365 권한이 부여 된 액세스 관리"에서 버그 보고서 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="cadb5-183">질문과 대답</span><span class="sxs-lookup"><span data-stu-id="cadb5-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="cadb5-184">Office 365에서 권한이 부여 된 액세스를 사용 하 여 어떤 Sku를 필요 합니까?</span><span class="sxs-lookup"><span data-stu-id="cadb5-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="cadb5-185">액세스 권한이 부여 된 현재 Office 365의 관리는 e 5 및 고급 준수 Sku와 고객을 위해 사용할 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="cadb5-186">액세스 권한을된 사용할 수 있게 될 Exchange 이외 Office 365 작업 부하에 대 한?</span><span class="sxs-lookup"><span data-stu-id="cadb5-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="cadb5-p113">다른 Office 365 작업에서이 기능을 곧 제공 예정입니다. 시간 표시 막대를 공유할 준비가 되었습니다, Office 365 로드맵을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="cadb5-189">어떻게 Azure Active Directory 권한 있는 Id 관리와에서 다른 인가요?</span><span class="sxs-lookup"><span data-stu-id="cadb5-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="cadb5-p114">권한 다른 범위에서 적시에 액세스할 수 있는 Office 365에 대 한 액세스를 제공 하 여 서로 제어 하는 [Azure AD 권한 있는 Id 관리](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) 보수 관리에 액세스 합니다. 함께 데이터를 보호 하는 것에 대 한 강력한 컨트롤 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="cadb5-p115">액세스 권한이 부여 된 Office 365의 관리를 정의 하 고 여러 작업을 실행 하는 기능 역할 수준에서 적용 하는 Azure AD 권한 있는 Id 관리 하는 동안 작업 수준으로 범위가 지정 수 있습니다.  Azure AD 권한 있는 Id 관리 주로 AD 역할 및 권한 하는 동안 역할 그룹에 대 한 액세스를 관리할 수 있도록 Office 365에서 액세스 관리 작업 수준에서 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="cadb5-194">**이미 Azure AD 권한 있는 Id 관리를 사용 하는 동안 Office 365의에서 관리 기능에 대 한 사용 권한 액세스:** Office 365에서 액세스 권한을된 관리 추가 (영문) 다른 세분화 된 보호 계층을 제공 하 고 Office 365 데이터에 대 한 권한이 부여 된 액세스에 대 한 기능을 감사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="cadb5-195">**이미 사용 하는 동안 Id 관리를 사용 하도록 설정 Azure AD 권한 있는 사용자는 Office 365에 대 한 액세스 관리 권한이:**  Azure AD 권한 있는 Id 관리 권한 추가 Office 365에서 액세스 관리는 주로 사용자의 역할 또는 id에 의해 정의 된 Office 365의 외부 데이터에 대 한 액세스 권한을된를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="cadb5-196">Office 365에 대 한 액세스 권한을된 관리 하는 전역 관리자 되도록 필요 합니까?</span><span class="sxs-lookup"><span data-stu-id="cadb5-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="cadb5-p116">미리 보기 하는 동안 Office 365에 대 한 액세스 권한을된 관리할 수 있도록 전역 관리자 권한이 필요 합니다. 승인자의 그룹에 포함 된 사용자 수를 검토 하 고 요청을 승인 하려면 전역 관리자 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="cadb5-199">Office 365와 관련 된 고객 Lockbox에서에서 액세스 권한을된 관리는 어떻게 합니까?</span><span class="sxs-lookup"><span data-stu-id="cadb5-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="cadb5-p117">[고객 Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) 서비스 공급자, 즉, Microsoft가 데이터에 대 한 액세스에 대 한 조직에 대 한 액세스 제어의 수준 수 있습니다. 액세스 권한이 부여 된 Office 365의 관리는 모든 Office 365의 권한 있는 작업에 대 한 조직 내에서 세분화 된 액세스 제어를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadb5-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>