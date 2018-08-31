---
title: Office 365의 개인 데이터에 보호 적용
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: Office 365에서 DLP 정책을 사용하여 개인 데이터를 보호하는 방법을 알아봅니다.
ms.openlocfilehash: 80b0129ade12824ae5d6190042622ea55ac1d427
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915073"
---
# <a name="apply-protection-to-personal-data-in-office-365"></a><span data-ttu-id="a9509-103">Office 365의 개인 데이터에 보호 적용</span><span class="sxs-lookup"><span data-stu-id="a9509-103">Apply protection to personal data in Office 365</span></span>

<span data-ttu-id="a9509-p101">Office 365의 개인 정보 보호에는 데이터 손실 방지 기능을 사용하는 방식이 포함됩니다. Office 365 보안 및 규정 준수 센터의 DLP(데이터 손실 방지) 정책을 사용하여 Office 365 전체에서 중요한 정보를 식별, 모니터링하고 자동으로 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p101">Protection of personal information in Office 365 includes using data loss prevention capabilities. With data loss prevention (DLP) policies in the Office 365 Security & Compliance Center, you can identify, monitor, and automatically protect sensitive information across Office 365.</span></span>

<span data-ttu-id="a9509-p102">이 항목에서는 DLP를 사용하여 개인 데이터를 보호하는 방법을 설명합니다. 이 항목에서는 SharePoint 라이브러리의 권한 설정 및 장치 액세스 정책 사용을 포함하여 GDPR 규정 준수를 위해 사용할 수 있는 기타 보호 기능도 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p102">This topic describes how to use DLP to protect personal data. This topic also lists other protection capabilities that can be used to achieve GDPR compliance, including setting permissions in SharePoint libraries and using device access policies.</span></span>

## <a name="apply-protection-using-data-loss-prevention-in-office-365"></a><span data-ttu-id="a9509-108">Office 365에서 데이터 손실 방지를 사용하여 보호 적용</span><span class="sxs-lookup"><span data-stu-id="a9509-108">Apply protection using data loss prevention in Office 365</span></span>

<span data-ttu-id="a9509-109">DLP를 사용하면 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-109">With DLP, you can:</span></span>

-   <span data-ttu-id="a9509-110">여러 위치에서 중요한 정보를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-110">Identify sensitive information across many locations.</span></span>

-   <span data-ttu-id="a9509-111">중요한 정보가 실수로 공유되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-111">Prevent accidental sharing of sensitive information.</span></span>

-   <span data-ttu-id="a9509-112">사용자가 자신의 워크플로를 중단하지 않고 규정 준수 상태를 유지하도록 하는 방법을 알도록 도와줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-112">Help users learn how to stay compliant without interrupting their workflow.</span></span>

-   <span data-ttu-id="a9509-113">DLP 정책과 일치하는 내용을 표시하는 DLP 보고서를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-113">View DLP reports showing content that matches your organization’s DLP policies.</span></span>

<span data-ttu-id="a9509-114">자세한 내용은 [데이터 손실 방지 정책 개요](https://support.office.com/ko-KR/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9509-114">For more information, see [Overview of data loss prevention policies](https://support.office.com/ko-KR/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>

![데이터 손실 방지 정책을 만들기 위한 옵션](Media/Apply-protection-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="a9509-116">이 그림에서는 DLP 정책을 만들기 위한 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-116">This illustration shows the options for creating a DLP policy:</span></span>

-   <span data-ttu-id="a9509-p103">적용할 보호를 선택합니다. 보호에는 다음이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p103">Choose the protection to apply. Protection can include:</span></span>

    -   <span data-ttu-id="a9509-119">사용자에 대한 정책 팁</span><span class="sxs-lookup"><span data-stu-id="a9509-119">Policy tips for users</span></span>

    -   <span data-ttu-id="a9509-120">관리자에 대한 전자 메일 보고서</span><span class="sxs-lookup"><span data-stu-id="a9509-120">Email report for admins</span></span>

    -   <span data-ttu-id="a9509-121">외부/내부적 공유 방지</span><span class="sxs-lookup"><span data-stu-id="a9509-121">Prevent sharing externally, internally, or both</span></span>

-   <span data-ttu-id="a9509-p104">보호 적용 기준을 선택합니다. 이 유형의 콘텐츠를 포함하는 문서에 보호를 적용합니다. 중요한 정보 유형 및/또는 레이블을 사용하도록 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p104">Choose the criteria for applying the protection. Apply the protection to documents with this type of content: you can configure the policy to use sensitive information types and/or labels.</span></span>

### <a name="using-dlp-for-gdpr-compliance"></a><span data-ttu-id="a9509-124">GDPR 규정 준수를 위해 DLP 사용</span><span class="sxs-lookup"><span data-stu-id="a9509-124">Using DLP for GDPR compliance</span></span>

<span data-ttu-id="a9509-p105">Office 365 DLP의 기본적인 사용 중 하나는 Office 365 환경에서 EU 데이터 주체와 관련된 개인 데이터를 식별하는 것입니다. Office 365 DLP는 SharePoint Online 및 비즈니스용 OneDrive에서 개인 데이터가 저장되는 위치나 개인 정보를 포함하는 사용자가 전자 메일을 전송하는 경우를 규정 준수 팀에 알릴 수 있습니다. 또한 DLP는 EU 거주자와 관련된 개인 정보로 작업하는 경우 정책 팁을 직원에게 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p105">One of the primary uses of Office 365 DLP is to identify personal data related to EU data subjects in your Office 365 environment. Office 365 DLP can notify your compliance teams of where personal information is stored in SharePoint Online and OneDrive for Business, or when users send email containing personal information. DLP can also provide policy tips to your employees when working with personal information related to EU residents.</span></span>

<span data-ttu-id="a9509-p106">작업 환경에서 EU 거주자 데이터가 저장되는 위치와 직원이 해당 데이터를 처리하도록 허용된 방식을 교육하고 인식을 높이는 것도 Office 365 DLP의 한 가지 정보 보호 수준을 나타냅니다. 종종, 이 유형의 정보에 대한 액세스 권한이 이미 있는 직원에게는 일상 작업을 수행하기 위해 이러한 권한이 필요합니다. GDPR 준수를 지원하기 위해 DLP 정책을 적용해도 액세스 권한을 제한해야 할 필요는 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p106">Educating and raising awareness to where EU resident data is stored in your environment and how your employees are permitted to handle it represents one level of information protection using Office 365 DLP. Often, employees who already have access to this type of information require this access to perform their day to day work. Enforcing DLP policies to help comply with GDPR may not require restricting access.</span></span>

<span data-ttu-id="a9509-p107">그러나 GDPR을 준수할 때 법적 및 정보 보안 관점에서 저장되는 개인 정보의 유형과 저장 위치, 해당 정보를 저장하고 처리하는 것이 법률적 타당성이 있는지에 대한 조직의 위험 기반 평가가 수행됩니다. 이러한 평가에 따라, 조직을 보호하고 GDPR을 준수하기 위한 정책을 구현하기 위해 EU 데이터 주체에 대한 개인 정보를 포함하는 문서에 대한 직원 액세스 권한을 제거해야 할 수 있습니다. 추가 보호가 필요한 경우 추가 DLP 보호를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p107">However, complying with GDPR typically involves a risk based assessment of the organization from both a legal and information security perspective, identification of what type and where personal information is stored, as well as if there is a legal justification to store and process that information. Based on this assessment, implementing policies to protect the organization and comply with GDPR might require removing access for employees to documents that contain personal information for EU data subjects. In cases where further protection is required, additional DLP protection can be configured.</span></span>

<span data-ttu-id="a9509-p108">다음 표에서는 DLP를 사용하여 보호를 강화하는 3가지 구성을 보여 줍니다. 첫 번째 구성인 인식은 시작점이자 GDPR의 최소 보호 수준으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p108">The following table lists three configurations of increasing protection using DLP. The first configuration, awareness, can be used as a starting point and minimum level of protection for GDPR.</span></span>

### <a name="example-protection-levels-that-can-be-configured-with-dlp-policies-and-used-for-gdpr-compliance"></a><span data-ttu-id="a9509-136">DLP 정책을 사용하여 구성하고 GDPR 규정 준수에 사용할 수 있는 보호 수준 예제</span><span class="sxs-lookup"><span data-stu-id="a9509-136">Example protection levels that can be configured with DLP policies and used for GDPR compliance</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a9509-137"><strong>보호 수준</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-137"><strong>Protection level</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-138"><strong>EU 데이터 주체와 관련된 개인 정보가 포함된 문서에 대한 DLP 구성</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-138"><strong>DLP configuration for documents with personal information related to EU data subjects</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-139"><strong>장점과 위험</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-139"><strong>Benefits and risks</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-140">인식</span><span class="sxs-lookup"><span data-stu-id="a9509-140">Awareness</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-141">이 데이터가 SharePoint Online 및 비즈니스용 OneDrive의 문서에서 확인될 때 규정 준수 팀에게 전자 메일 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-141">Send email notifications to compliance teams when this data is found in documents in SharePoint Online and OneDrive for Business.</span></span></p>
<p><span data-ttu-id="a9509-142">이 데이터가 들어 있는 문서에 액세스할 때 정책 팁을 사용자 지정한 후 SharePoint 및 비즈니스용 OneDrive의 직원에게 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-142">Customize and display Policy Tips to employees in SharePoint and OneDrive for Business when accessing documents containing this data.</span></span></p>
<p><span data-ttu-id="a9509-143">이 데이터가 공유되는 경우를 감지하고 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-143">Detect and report when this data is being shared.</span></span></p></td>
<td align="left"><p><span data-ttu-id="a9509-144">이 데이터가 저장된 위치와 관련해서 직원은 물론 규정 준수 팀의 인식을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-144">Raise awareness with compliance teams as well as employees regarding where this data is stored.</span></span></p>
<p><span data-ttu-id="a9509-145">이 데이터를 포함하는 문서의 처리에 대한 회사 정책을 직원에게 교육합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-145">Educate employees on corporate policy for handling documents containing this data.</span></span></p>
<p><span data-ttu-id="a9509-146">직원이 내부 또는 외부적으로 이 데이터를 공유하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-146">Does not prevent employees from sharing this data internally or externally.</span></span></p>
<p><span data-ttu-id="a9509-147">공유 데이터에 대한 DLP 보고서를 검토하고 있는 보호를 강화해야 하는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-147">You can review DLP reports for shared data and decide if you need to increase the protection.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-148">외부 공유 방지</span><span class="sxs-lookup"><span data-stu-id="a9509-148">Prevent external sharing</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-149">콘텐츠가 외부 사용자와 공유되는 경우 SharePoint Online 및 비즈니스용 OneDrive에서 이 데이터를 포함하는 문서에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-149">Restrict access to documents that contain this data in SharePoint Online and OneDrive for Business when that content is shared with external users.</span></span></p>
<p><span data-ttu-id="a9509-150">이 데이터를 포함하는 문서가 첨부된 전자 메일을 외부 받는 사람에게 전송하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-150">Prevent sending emails with documents that contain this data to external recipients.</span></span></p>
<p><span data-ttu-id="a9509-151">이 데이터가 공유되는 경우를 감지하고 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-151">Detect and report when this data is being shared.</span></span></p></td>
<td align="left"><p><span data-ttu-id="a9509-152">직원이 내부에서는 이 데이터를 사용할 수 있지만 외부적으로 공유하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-152">Prevents external sharing of this data while allowing for employees to work with this data internally.</span></span></p>
<p><span data-ttu-id="a9509-153">공유 데이터에 대한 DLP 보고서를 내부적으로 검토하고 이 보호를 강화해야 하는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-153">You can review DLP reports for internally shared data and decide if you need to increase this protection.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-154">내부 및 외부 공유 방지</span><span class="sxs-lookup"><span data-stu-id="a9509-154">Prevent internal and external sharing</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-155">콘텐츠가 내부 또는 외부적으로 공유되는 경우 SharePoint Online 및 비즈니스용 OneDrive에서 이 데이터를 포함하는 문서에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-155">Restrict access to documents that contain this data in SharePoint Online and OneDrive for Business when that content is shared internally or externally.</span></span></p>
<p><span data-ttu-id="a9509-156">이 데이터를 포함하는 전자 메일을 내부 및 외부 받는 사람 둘 다에게 전송하지는 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-156">Prevent sending emails which contain this data to both internal and external recipients.</span></span></p></td>
<td align="left"><p><span data-ttu-id="a9509-157">이 데이터의 내부 및 외부 공유 방지</span><span class="sxs-lookup"><span data-stu-id="a9509-157">Prevents internal and external sharing of this data.</span></span></p>
<p><span data-ttu-id="a9509-158">직원이 이 데이터로 작업해야 하는 태스크를 완료하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-158">Employees might not be able to complete tasks that require working with this data.</span></span></p>
<p><span data-ttu-id="a9509-159">공유 데이터에 대한 DLP 보고서를 내부 또는 외부적으로 검토하고 최종 사용자 교육이 필요한지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-159">You can review DLP reports for internally or externally shared data and decide if end user training is needed.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9509-p109">참고: 보호 수준이 증가하면 정보에 액세스하는 사용자의 권한이 경우에 따라 줄어들며, 일상 태스크를 완료하기 위한 생산성이나 능력에 영향을 미칠 수 있습니다. 직원에게 영향을 미치는 정책을 구현하여 보호 수준을 높이는 작업은 일반적으로 최종 사용자 교육과 함께 진행됩니다. 사용자에게 새로운 보안 정책과 절차를 교육하여 좀 더 안전한 환경에서 지속적으로 생산성을 유지하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p109">Note: As the levels of protection increase, the ability of users to access information will decrease in some cases, and could potentially impact their productivity or ability to complete day to day tasks. Increasing protection levels by implementing policies that impact employees is typically accompanied by end user training, educating users on new security policies and procedures to help them continue to be productive in a more secure environment.</span></span>

### <a name="example-dlp-policy-for-gdpr--awareness"></a><span data-ttu-id="a9509-162">GDPR에 대한 DLP 정책 예제 — 인식</span><span class="sxs-lookup"><span data-stu-id="a9509-162">Example DLP policy for GDPR — Awareness</span></span> 

<span data-ttu-id="a9509-163">이름: GDPR이 적용되는 개인 데이터에 대한 인식</span><span class="sxs-lookup"><span data-stu-id="a9509-163">Name: Awareness for personal data that is subject to GDPR.</span></span>

<span data-ttu-id="a9509-164">설명: 직원에게 정책 팁을 표시하고, SharePoint Online 및 비즈니스용 OneDrive의 문서에서 이 데이터를 찾았을 때 규정 준수 팀에게 알리고, 이 데이터가 조직 외부에 공유될 경우를 감지하고 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-164">Description: Display policy tips to employees, notify compliance teams when this data is found in documents in SharePoint Online and OneDrive for Business, detect and report when this data is being shared outside your organization.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a9509-165"><strong>제어</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-165"><strong>Control</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-166"><strong>설정</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-166"><strong>Settings</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-167">보호할 정보 선택</span><span class="sxs-lookup"><span data-stu-id="a9509-167">Choose information to protect</span></span></td>
<td align="left"><span data-ttu-id="a9509-168">사용자 지정 정책 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-168">Select a Custom policy template.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-169">위치</span><span class="sxs-lookup"><span data-stu-id="a9509-169">Locations</span></span></td>
<td align="left"><span data-ttu-id="a9509-170">Office 365의 모든 위치</span><span class="sxs-lookup"><span data-stu-id="a9509-170">All locations in Office 365</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-171">포함된 콘텐츠 찾기</span><span class="sxs-lookup"><span data-stu-id="a9509-171">Find content that contains</span></span></td>
<td align="left"><span data-ttu-id="a9509-172">'편집'을 클릭하고 사용자 환경에 맞게 조정된 모든 중요한 정보 유형을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-172">Click ‘Edit’ and add all the sensitive information types you curated for your environment.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-173">이 콘텐츠가 공유될 경우 감지</span><span class="sxs-lookup"><span data-stu-id="a9509-173">Detect when this content is shared</span></span></td>
<td align="left"><span data-ttu-id="a9509-174">이 확인란을 선택하고 '조직 외부의 사용자'를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-174">Check this box and select ‘with people outside my organization.’</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-175">정책 설정과 일치하는 콘텐츠가 있을 때 사용자에게 알림</span><span class="sxs-lookup"><span data-stu-id="a9509-175">Notify users when content matches the policy settings</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-176">이 확인란("사용자에게 정책 팁 표시 및 전자 메일 알림 전송")을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-176">Check this box (“Show policy tips to users and send them an email notification.”)</span></span></p>
<p><span data-ttu-id="a9509-p110">'팁 및 전자 메일 사용자 지정'을 클릭하고 작업 환경에 맞게 업데이트합니다. <a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">전자 메일 알림 보내기 및 DLP 정책에 대한 정책 팁 표시</a> 문서에서 기본 알림을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9509-p110">Click ‘Customize the tip and email’ and update these for your environment. See the default notifications in this article: <a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">Send email notifications and show policy tips for DLP policies</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-179">한 번에 특정 양의 중요한 정보가 공유되는 경우 감지</span><span class="sxs-lookup"><span data-stu-id="a9509-179">Detect when a specific amount of sensitive info is being shared at one time</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-180">'공유 중인 콘텐츠에 다음이 포함될 때 감지: 동일한 중요한 정보 유형의 ___개 이상 인스턴스' - 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-180">‘Detect when content that’s being shared contains: At least ____ instances of the same sensitive info type’ — Set this to 1.</span></span></p>
<p><span data-ttu-id="a9509-p111">'사고 보고서를 전자 메일로 전송' - 이 확인란을 선택합니다. '보고서에 포함할 내용 및 받는 사람 선택'을 클릭합니다. 규정 준수 팀을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p111">‘Send incident reports in email’ — check this box. Click ‘Choose what to include in the report and who receives it.’ Be sure to add your compliance team.</span></span></p>
<p><span data-ttu-id="a9509-184">'콘텐츠에 액세스할 수 있는 사용자 제한 및 정책 재정의’ - 사용자가 해당 정보에 액세스하도록 하면서 중요한 정보에 대한 알림을 수신하도록 하려면 이 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-184">‘Restrict who can access the content and override the policy’ — clear this checkbox to receive notifications about sensitive information without preventing users from access that information.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9509-185">모든 위치에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-185">All locations includes:</span></span>

-   <span data-ttu-id="a9509-186">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a9509-186">SharePoint Online</span></span>

-   <span data-ttu-id="a9509-187">비즈니스용 OneDrive 계정</span><span class="sxs-lookup"><span data-stu-id="a9509-187">OneDrive for Business accounts</span></span>

-   <span data-ttu-id="a9509-188">Exchange 사서함</span><span class="sxs-lookup"><span data-stu-id="a9509-188">Exchange mailboxes</span></span>

<span data-ttu-id="a9509-189">현재 콘텐츠 검색 기능으로 전자 메일을 포함하는 중요한 정보 유형을 테스트할 수 없으므로, 각 정책의 중요한 정보 유형 부분에 대한 Exchange용 정책을 따로 만들고 이러한 정책의 롤아웃을 모니터링하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-189">Because Content Search doesn’t currently let you test sensitive information types with email,consider creating separate policies for Exchange with a subset of sensitive information types in each policy and monitoring the rollout of these policies.</span></span>

## <a name="additional-protection-you-can-apply-to-protect-personal-data-in-office-365"></a><span data-ttu-id="a9509-190">Office 365의 개인 데이터를 보호하기 위해 적용할 수 있는 추가 보호</span><span class="sxs-lookup"><span data-stu-id="a9509-190">Additional protection you can apply to protect personal data in Office 365</span></span>

<span data-ttu-id="a9509-p112">중요한 정보 유형, 레이블 및 데이터 손실 보호 정책은 특정 데이터를 포함하는 문서를 식별하고 보호를 적용하는 데 도움을 줍니다. 그러나 이러한 보호는 데이터 액세스에 대해 설정된 적절한 권한, 손상되지 않은 계정의 사용자, 정상 상태의 장치에 따라 좌우됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p112">Sensitive information types, labels, and data loss protection policies help you identify documents containing specific data and apply protection. However, these protections depend on appropriate permissions being set for access to data, users with accounts that are not compromised, and devices that are healthy.</span></span>

<span data-ttu-id="a9509-193">다음 그림에서는 개인 데이터에 대한 액세스를 보호하기 위해 적용할 수 있는 추가 보호 기능을 자세히 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-193">The following illustration details additional protection you can apply to protect access to personal data.</span></span>

![개인 데이터에 대한 액세스를 보호하기 위한 추가 보호](Media/Apply-protection-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="a9509-195">다음 표에서는 이해를 돕기 위해 그림과 동일한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-195">For accessibility, the following table provides the same information in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a9509-196"><strong>보호 범위</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-196"><strong>Scope of protection</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-197"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-197"><strong>Capabilities</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-198">문서 및 전자 메일 수준 보호(전송 중인 메일은 포함되지만, 현재, 휴지 상태의 사서함의 메일은 포함되지 않음)</span><span class="sxs-lookup"><span data-stu-id="a9509-198">Document and email-level protection (includes mail in transit, but not currently mailboxes at rest)</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-199">중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="a9509-199">Sensitive information types</span></span></p>
<p><span data-ttu-id="a9509-200">Office 레이블</span><span class="sxs-lookup"><span data-stu-id="a9509-200">Office labels</span></span></p>
<p><span data-ttu-id="a9509-201">데이터 손실 방지 정책</span><span class="sxs-lookup"><span data-stu-id="a9509-201">Data loss prevention policies</span></span></p>
<p><span data-ttu-id="a9509-202">전자 메일에 대한 Office 365 메시지 암호화</span><span class="sxs-lookup"><span data-stu-id="a9509-202">Office 365 Message Encryption for email</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-203">사이트 및 라이브러리 수준 보호(SharePoint Online 및 비즈니스용 OneDrive 사이트 포함)</span><span class="sxs-lookup"><span data-stu-id="a9509-203">Site and library-level protection (includes SharePoint Online and OneDrive for Business sites)</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-204">SharePoint Online 및 비즈니스용 OneDrive 사이트와 라이브러리에 대한 권한</span><span class="sxs-lookup"><span data-stu-id="a9509-204">Permissions for SharePoint Online and OneDrive for Business sites and libraries</span></span></p>
<p><span data-ttu-id="a9509-205">SharePoint Online 및 비즈니스용 OneDrive(사이트 수준)에 대한 외부 공유 정책</span><span class="sxs-lookup"><span data-stu-id="a9509-205">External sharing policies for SharePoint Online and OneDrive for Business (site-level)</span></span></p>
<p><span data-ttu-id="a9509-206">사이트 수준 장치 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="a9509-206">Site-level device access policies</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-207">서비스 액세스 보호(Office 365의 모든 서비스에 대한 액세스 포함)</span><span class="sxs-lookup"><span data-stu-id="a9509-207">Service access protection (includes access to all services in Office 365)</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-208">EMS(Enterprise Mobility + Security) 제품군의 ID 및 장치 액세스 보호</span><span class="sxs-lookup"><span data-stu-id="a9509-208">Identity and device access protection in Enterprise Mobility + Security (EMS) suite</span></span></p>
<p><span data-ttu-id="a9509-209">권한이 부여된 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="a9509-209">Privileged access management</span></span></p>
<p><span data-ttu-id="a9509-210">Windows 10 보안 기능</span><span class="sxs-lookup"><span data-stu-id="a9509-210">Windows 10 security capabilities</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9509-211">이 문서의 나머지 부분에서는 이러한 각 보호 범주에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-211">The rest of this article provides more information on each of these categories of protection.</span></span>

### <a name="capabilities-that-are-ok-to-use-with-gdpr"></a><span data-ttu-id="a9509-212">GDPR를 통해 사용이 허가된 기능</span><span class="sxs-lookup"><span data-stu-id="a9509-212">Capabilities that are OK to use with GDPR</span></span>

<span data-ttu-id="a9509-p113">GDPR 규정 준수에 대해 구성된 환경에서 다음과 같은 기능을 사용할 수 있습니다. 이러한 기능은 GDPR 규정 준수를 위해 필요하지는 않지만 GDPR 준수와 관련된 데이터를 검색, 보호, 모니터링 및 보고하는 기능에 영향을 미치지 않으면서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p113">You can use the following capabilities in an environment configured for GDPR compliance. These capabilities are not necessary for GDPR compliance, but they can be used without adversely affecting your ability to discover, protect, monitor, and report on data related to GDPR compliance.</span></span>

<span data-ttu-id="a9509-p114">고객 키 - 고객이 Office 365 내에서 휴지 상태의 데이터를 암호화하는 데 사용되는 암호화 키를 제공하고 제어할 수 있도록 합니다. 규정에 따라 자체 암호화 키를 관리해야 하는 고객에게만 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p114">Customer Key — Allows customers to provide and retain control over the encryption keys that are used to encrypt data at rest within Office 365. Recommended only for customers with a regulatory need to manage their own encryption keys.</span></span>

<span data-ttu-id="a9509-p115">고객 Lockbox - 고객 Lockbox를 사용하면 필요한 경우 사례별로 기술적 문제를 해결하기 위해 Microsoft 지원 엔지니어가 사용자의 데이터에 액세스하는 방식을 제어할 수 있습니다. 지원 엔지니어에게 사용자 데이터에 대한 액세스 권한을 부여할지 여부를 제어할 수 있습니다. 요청별로 만료 시간이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p115">Customer Lockbox — Customer lockbox allows you to control how a Microsoft support engineer accesses your data, if needed, to fix a technical issue on a case by case basis. You can control whether to give the support engineer access to your data or not. An expiration time is provided with each request.</span></span>

## <a name="site-and-library-level-protection"></a><span data-ttu-id="a9509-220">사이트 및 라이브러리 수준 보호</span><span class="sxs-lookup"><span data-stu-id="a9509-220">Site and library-level protection</span></span>

### <a name="permissions-for-sharepoint-and-onedrive-for-business-libraries"></a><span data-ttu-id="a9509-221">SharePoint 및 비즈니스용 OneDrive 라이브러리에 대한 사용 권한</span><span class="sxs-lookup"><span data-stu-id="a9509-221">Permissions for SharePoint and OneDrive for Business libraries</span></span>

<span data-ttu-id="a9509-p116">SharePoint의 사용 권한을 사용하여 사용자에게 사이트 또는 해당 콘텐츠에 대한 액세스 권한을 제공하거나 액세스를 제한할 수 있습니다. 기본 SharePoint 그룹에 개별 사용자 또는 Azure Active Directory 그룹을 추가하거나 보다 세밀한 제어를 위해 사용자 지정 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p116">Use permissions in SharePoint to provide or restrict user access to the site or its contents. Add individual users or Azure Active Directory groups to the default SharePoint groups. Or, create a custom group for finer-grain control.</span></span>

![모든 권한에서 보기 전용에 이르는 사용 권한 수준](Media/Apply-protection-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="a9509-p117">이 그림에서는 모든 권한부터 보기 전용에 이르는 사용 권한 수준을 보여 줍니다. 다음 표에는 동일한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p117">The illustration plots permission levels from Full control to View Only. The following table includes the same information.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a9509-228"><strong>모든 권한</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-228"><strong>Full Control</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-229"><strong>디자인</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-229"><strong>Design</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-230"><strong>편집</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-230"><strong>Edit</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-231"><strong>참가</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-231"><strong>Contribute</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-232"><strong>읽기</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-232"><strong>Read</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-233"><strong>보기만</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-233"><strong>View Only</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="a9509-234">참가 + 승인 및 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="a9509-234">Contribute + approve and customize</span></span></td>
<td align="left"><span data-ttu-id="a9509-235">참가 + 목록 추가, 편집, 삭제(항목 나열 이상)</span><span class="sxs-lookup"><span data-stu-id="a9509-235">Contribute + add, edit and delete lists (not just list items)</span></span></td>
<td align="left"><span data-ttu-id="a9509-236">항목과 문서 보기, 추가, 업데이트, 삭제</span><span class="sxs-lookup"><span data-stu-id="a9509-236">View, add, update, delete list items and documents</span></span></td>
<td align="left"><span data-ttu-id="a9509-237">보기 및 다운로드</span><span class="sxs-lookup"><span data-stu-id="a9509-237">View and download</span></span></td>
<td align="left"><span data-ttu-id="a9509-238">보기, 다운로드 없음</span><span class="sxs-lookup"><span data-stu-id="a9509-238">View, no download</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9509-239">추가 정보:</span><span class="sxs-lookup"><span data-stu-id="a9509-239">More information:</span></span>

-   [<span data-ttu-id="a9509-240">SharePoint의 권한 수준 이해</span><span class="sxs-lookup"><span data-stu-id="a9509-240">Understanding permission levels in SharePoint</span></span>](https://support.office.com/ko-KR/article/Understanding-permission-levels-in-SharePoint-87ecbb0e-6550-491a-8826-c075e4859848)

-   [<span data-ttu-id="a9509-241">SharePoint 그룹 이해</span><span class="sxs-lookup"><span data-stu-id="a9509-241">Understanding SharePoint groups</span></span>](https://support.office.com/ko-KR/article/Understanding-SharePoint-groups-94d9b261-161e-4ace-829e-eca1c8cd2eb8)

### <a name="external-sharing-policies-for-sharepoint-and-onedrive-for-business-libraries"></a><span data-ttu-id="a9509-242">SharePoint 및 비즈니스용 OneDrive 라이브러리에 대한 외부 공유 정책</span><span class="sxs-lookup"><span data-stu-id="a9509-242">External sharing policies for SharePoint and OneDrive for Business libraries</span></span>

<span data-ttu-id="a9509-p118">대부분의 조직에서는 공동 작업을 지원하기 위해 외부 공유를 허용합니다. 테넌트 전체 설정이 구성되는 방식을 알아보세요. 그런 후 개인 데이터를 포함하는 사이트에 대한 외부 공유 설정을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="a9509-p118">Many organizations allow external sharing to support collaboration. Find out how your tenant-wide settings are configured. Then review the external sharing settings for sites that contain personal data.</span></span>

<span data-ttu-id="a9509-246">외부 사용자는 SharePoint Online 사이트 및 문서에 액세스하도록 초대를 받았으나 SharePoint Online 또는 Microsoft Office 365 구독에 대한 라이선스가 없는 조직 외부의 사람입니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-246">An external user is someone outside of your organization who is invited to access your SharePoint Online sites and documents but does not have a license for your SharePoint Online or Microsoft Office 365 subscription.</span></span>

<span data-ttu-id="a9509-247">외부 공유 정책은 SharePoint Online 및 비즈니스용 OneDrive 둘 다에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-247">External sharing policies apply to both SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="a9509-248">공유 정책을 구성하려면 SharePoint Online 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-248">You must be a SharePoint Online admin to configure sharing policies.</span></span>

-   <span data-ttu-id="a9509-249">외부 사용자와 사이트 또는 문서를 공유하려면 사이트 소유자이거나 모든 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-249">You must be a Site Owner or have full control permissions to share a site or document with external users.</span></span>

<span data-ttu-id="a9509-250">다음 표에서는 구성할 수 있는 제어를 요약해서 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-250">The following table summarizes the controls you can configure.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a9509-251"><strong>제어 범주</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-251"><strong>Control category</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-252"><strong>옵션</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-252"><strong>Options</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-253">공유 유형</span><span class="sxs-lookup"><span data-stu-id="a9509-253">Type of sharing</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-254">조직 외부의 공유 허용 안 함(개별 사이트 모음에 대해 설정 가능)</span><span class="sxs-lookup"><span data-stu-id="a9509-254">Don’t allow sharing outside your organization (can be set for individual site collections)</span></span></p>
<p><span data-ttu-id="a9509-255">인증된 외부 사용자만 공유 허용(개별 사이트 모음에 대해서는 새로 허용 또는 기존으로 제한을 설정할 수 있음)\*</span><span class="sxs-lookup"><span data-stu-id="a9509-255">Allow sharing to authenticated external users only (allow new or limit to existing, can be set for individual site collections)\*</span></span></p>
<p><span data-ttu-id="a9509-256">익명 액세스 링크가 있는 외부 사용자의 공유 허용(개별 사이트 모음에 대해 설정 가능)</span><span class="sxs-lookup"><span data-stu-id="a9509-256">Allow sharing to external users with an anonymous access link (can be set for individual site collections)</span></span></p>
<p><span data-ttu-id="a9509-257">도메인을 사용하는 외부 공유 제한(허용 및 거부 목록)</span><span class="sxs-lookup"><span data-stu-id="a9509-257">Limit external sharing using domains (allow and deny list)</span></span></p>
<p><span data-ttu-id="a9509-258">기본 링크 유형(익명, 회사 공유 가능 또는 제한) 선택</span><span class="sxs-lookup"><span data-stu-id="a9509-258">Choose the default link type (anonymous, company shareable, or restricted)</span></span></p>
</td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-259">외부 사용자가 수행할 수 있는 작업</span><span class="sxs-lookup"><span data-stu-id="a9509-259">What external users can do</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-260">외부 사용자가 소유하지 않는 파일, 폴더, 사이트를 공유하지 못하도록 금지</span><span class="sxs-lookup"><span data-stu-id="a9509-260">Prevent external users from sharing files, folders, sites they don’t own</span></span></p>
<p><span data-ttu-id="a9509-261">외부 사용자는 초대를 받은 동일한 계정을 사용하여 공유 초대를 수락해야 함</span><span class="sxs-lookup"><span data-stu-id="a9509-261">Require external users to accept sharing invitations with the same account the invitation was sent to</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-262">알림</span><span class="sxs-lookup"><span data-stu-id="a9509-262">Notifications</span></span></td>
<td align="left"><p><span data-ttu-id="a9509-p119">현재 비즈니스용 OneDrive에서만 사용 가능합니다. 다음 경우에 소유자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p119">Currently only available in OneDrive for Business. Notify owners when:</span></span></p>
- <p><span data-ttu-id="a9509-265">사용자가 추가 외부 사용자를 공유 파일로 초대함</span><span class="sxs-lookup"><span data-stu-id="a9509-265">Users invite additional external users to shared files</span></span></p>
- <p><span data-ttu-id="a9509-266">외부 사용자가 파일 액세스 초대를 수락함</span><span class="sxs-lookup"><span data-stu-id="a9509-266">External users accept invitations to access files</span></span></p>
- <p><span data-ttu-id="a9509-267">익명 액세스 링크를 만들거나 변경함</span><span class="sxs-lookup"><span data-stu-id="a9509-267">An anonymous access link is created or changed</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9509-268">추가 정보:</span><span class="sxs-lookup"><span data-stu-id="a9509-268">More information:</span></span>

-   <span data-ttu-id="a9509-269">
  [SharePoint Online 환경에 대해 외부 공유 관리](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)</span><span class="sxs-lookup"><span data-stu-id="a9509-269">[Manage external sharing for your SharePoint Online environment](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)</span></span>

-   [<span data-ttu-id="a9509-270">조직 외부의 사용자와 사이트 또는 문서 공유</span><span class="sxs-lookup"><span data-stu-id="a9509-270">Share sites or documents with people outside your organization</span></span>](https://support.office.com/ko-KR/article/Share-sites-or-documents-with-people-outside-your-organization-80e49744-e30f-44db-8d51-16661b1d4232)

### <a name="site-level-device-access-policies"></a><span data-ttu-id="a9509-271">사이트 수준 장치 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="a9509-271">Site-level device access policies</span></span>

<span data-ttu-id="a9509-p120">SharePoint Online 및 비즈니스용 OneDrive를 사용하여 사이트 수준에서 장치 액세스 정책을 구성할 수 있습니다. 이를 통해 중요한 데이터가 포함된 사이트에 대해 더 많은 보호를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p120">SharePoint Online and OneDrive for Business let you configure device access policies at the site level. This lets you configure more protection for sites with sensitive data.</span></span>

<span data-ttu-id="a9509-274">사이트 수준 장치 액세스 정책을 사용하는 경우 테넌트 수준 정책과 Azure Active Directory, Intune 및 Intune 앱 관리에서 구성된 액세스 정책에 맞춰 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-274">If you configure site-level device access policies, be sure to coordinate these with tenant-level policies and also with access policies that are configured in Azure Active Directory, Intune, and Intune App Management.</span></span>

<span data-ttu-id="a9509-p121">SharePoint 및 비즈니스용 OneDrive에 대한 장치 액세스 정책은 구현하는 시나리오에 따라 Microsoft Intune 및 Azure Active Directory의 정책을 지원해야 합니다. 다음 표에서는 장치 액세스 정책으로 달성할 수 있는 목표를 요약해서 보여 주며 지원 정책이 필요한 제품을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p121">Device access policies for SharePoint and OneDrive for Business require supporting policies in Azure Active Directory and Microsoft Intune depending on the scenario you are implementing. The following table summarizes objectives you can achieve with device access policies and indicates which products require supporting policies.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left"><span data-ttu-id="a9509-277">특정 IP 주소 위치로부터의 액세스만 허용</span><span class="sxs-lookup"><span data-stu-id="a9509-277">Only allow access from specific IP address locations</span></span></th>
<th align="left"><span data-ttu-id="a9509-278">사용자가 도메인에 가입되지 않은 장치로 파일을 다운로드하지 못하도록 차단</span><span class="sxs-lookup"><span data-stu-id="a9509-278">Prevent users from downloading files to non-domain joined devices</span></span></th>
<th align="left"><span data-ttu-id="a9509-279">도메인에 가입되지 않은 장치에 대한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="a9509-279">Block access on non-domain joined devices</span></span></th>
<th align="left"><span data-ttu-id="a9509-280">사용자가 호환되지 않는 장치로 파일을 다운로드하지 못하도록 차단</span><span class="sxs-lookup"><span data-stu-id="a9509-280">Prevent users from downloading files to non-compliant devices</span></span></th>
<th align="left"><span data-ttu-id="a9509-281">호환되지 않는 장치에 대한 액세스 차단</span><span class="sxs-lookup"><span data-stu-id="a9509-281">Block access on non-compliant devices</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-282">SharePoint 관리 센터</span><span class="sxs-lookup"><span data-stu-id="a9509-282">SharePoint admin center</span></span></td>
<td align="left"><span data-ttu-id="a9509-283">예</span><span class="sxs-lookup"><span data-stu-id="a9509-283">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-284">예</span><span class="sxs-lookup"><span data-stu-id="a9509-284">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-285">예</span><span class="sxs-lookup"><span data-stu-id="a9509-285">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-286">예</span><span class="sxs-lookup"><span data-stu-id="a9509-286">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-287">예</span><span class="sxs-lookup"><span data-stu-id="a9509-287">Yes</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-288">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="a9509-288">Azure Active Directory</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="a9509-289">예</span><span class="sxs-lookup"><span data-stu-id="a9509-289">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-290">예</span><span class="sxs-lookup"><span data-stu-id="a9509-290">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-291">예</span><span class="sxs-lookup"><span data-stu-id="a9509-291">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-292">예</span><span class="sxs-lookup"><span data-stu-id="a9509-292">Yes</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-293">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="a9509-293">Microsoft Intune</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="a9509-294">예</span><span class="sxs-lookup"><span data-stu-id="a9509-294">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-295">예</span><span class="sxs-lookup"><span data-stu-id="a9509-295">Yes</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9509-296">자세한 내용: [SharePoint Online 관리 센터: 관리되지 않는 장치의 액세스 제어](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US)</span><span class="sxs-lookup"><span data-stu-id="a9509-296">More information: [SharePoint Online admin center: Control access from unmanaged devices](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US).</span></span>

## <a name="service-access-protection-for-identities-and-devices"></a><span data-ttu-id="a9509-297">ID 및 장치에 대한 서비스 액세스 보호</span><span class="sxs-lookup"><span data-stu-id="a9509-297">Service access protection for identities and devices</span></span>

<span data-ttu-id="a9509-p122">서비스에 액세스하는 ID 및 장치에 대한 보호를 구성하는 것이 좋습니다. Office 365 서비스에 대한 액세스를 보호하기 위해 구성한 작업을 사용하여 다른 SaaS 서비스, PaaS 서비스 및 기타 클라우드 공급자의 앱에 대한 액세스도 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p122">Microsoft recommends you configure protection for identities and devices that access the service. The work you put into protecting access to Office 365 services can also be used to protect access to other SaaS services, PaaS services, and even apps in other cloud providers.</span></span>

<span data-ttu-id="a9509-300">ID 및 장치에 대한 액세스 보호는 ID가 손상되지 않고, 장치가 안전하고, 장치에서 액세스되는 조직 데이터가 격리 및 보호되도록 하는 보호 기준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-300">Access protection for identities and devices provides a baseline of protection to ensure that identities are not compromised, devices are safe, and organization data that is accessed on devices is isolated and protected.</span></span>

<span data-ttu-id="a9509-301">권장 시작점 및 구성 지침에 대해서는 [정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](https://docs.microsoft.com/ko-KR/microsoft-365-enterprise/microsoft-security-guidance)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9509-301">For starting point recommendations and configuration guidance, see [Microsoft security guidance for political campaigns, nonprofits, and other agile organizations](https://docs.microsoft.com/ko-KR/microsoft-365-enterprise/microsoft-security-guidance).</span></span>

<span data-ttu-id="a9509-302">AD FS를 사용하는 하이브리드 ID 환경에 대해서는 [권장되는 보안 정책 및 구성](https://docs.microsoft.com/ko-KR/microsoft-365-enterprise/microsoft-security-guidance)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9509-302">For hybrid identity environments with AD FS, see [Recommended security policies and configurations](https://docs.microsoft.com/ko-KR/microsoft-365-enterprise/microsoft-security-guidance).</span></span>

<span data-ttu-id="a9509-p123">다음 그림에서는 클라우드 서비스(SaaS, PaaS), 계정 유형(테넌트 도메인 계정 및 B2B 계정), 서비스 액세스 기능이 관련디는 방식을 보여 줍니다. B2B 계정에 사용할 수 있는 기능을 이해하는 것도 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p123">The following illustration describes how cloud services (SaaS, PaaS), account types (tenant domain accounts vs. B2B accounts) and service access capabilities relate. It’s important to note which capabilities can be used with B2B accounts.</span></span>

![클라우드 서비스, 계정 유형 및 액세스 기능](Media/Apply-protection-to-personal-data-in-Office-365-image4.png)

<span data-ttu-id="a9509-306">이해를 돕기 위해 이 섹션의 나머지 부분에서는 이 그림을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-306">For accessibility, the rest of this section describes this illustration.</span></span>

### <a name="cloud-services"></a><span data-ttu-id="a9509-307">클라우드 서비스</span><span class="sxs-lookup"><span data-stu-id="a9509-307">Cloud services</span></span>

<span data-ttu-id="a9509-p124">Azure Active Directory는 Amazon Web Services와 같은 타사 공급자를 비롯한 모든 클라우드 서비스에 대한 ID 액세스를 제공합니다. 이 그림에서는 Office 365를 "기타 SaaS 앱" 및 "PaaS 앱”을 보여 줍니다. Azure Active Directory에서 이러한 각 서비스로 연결되는 화살표는 이러한 모든 앱 유형에 대한 인증에 Azure Active Directory를 사용할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p124">Azure Active Directory provides identity access to any cloud service, including non-Microsoft providers such as Amazon Web Services. The illustration shows Office 365, “Other SaaS app,” and “PaaS app.” Arrows point from Azure Active Directory to each of these services, showing that Azure Active Directory can be used for authentication to all of these app types.</span></span>

### <a name="types-of-accounts"></a><span data-ttu-id="a9509-311">계정 유형</span><span class="sxs-lookup"><span data-stu-id="a9509-311">Types of accounts</span></span>

<span data-ttu-id="a9509-p125">테넌트 도메인 계정은 테넌트에 추가하고 직접 관리하는 계정입니다. B2B 계정은 공동 작업을 위해 초대하는 조직 외부의 사용자를 위한 계정입니다. 이러한 계정은 다른 Office 365 계정, 다른 조직 계정 또는 소비자 계정(예: Gmail)일 수 있습니다. 이 그림에서는 Azure Active Directory 내의 두 계정 유형을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p125">Tenant domain accounts are account you add to your tenant and manage directly. B2B accounts are accounts for users outside your organization you invite to collaborate with. These can be other Office 365 accounts, other organization accounts, or consumer accounts (such as Gmail). The illustration shows both account types within Azure Active Directory.</span></span>

### <a name="capabilities"></a><span data-ttu-id="a9509-316">기능</span><span class="sxs-lookup"><span data-stu-id="a9509-316">Capabilities</span></span>

<span data-ttu-id="a9509-p126">다음 표의 기능은 ID 및 장치를 보호합니다. 이 표에서는 B2B 계정에서도 사용할 수 있는 기능을 그림과 비슷하게 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-p126">The capabilities in the following table protect identities and devices. The table indicates which capabilities can also be used with B2B accounts, similar to the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a9509-319"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-319"><strong>Capability</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-320"><strong>테넌트 도메인 계정 사용</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-320"><strong>Works with tenant domain accounts</strong></span></span></th>
<th align="left"><span data-ttu-id="a9509-321"><strong>Azure B2B 계정 사용(추가 라이선스 없음)</strong></span><span class="sxs-lookup"><span data-stu-id="a9509-321"><strong>Works with Azure B2B accounts (without additional licensing)</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-322">다단계 인증 및 조건부 액세스</span><span class="sxs-lookup"><span data-stu-id="a9509-322">Multi-factor authentication and conditional access</span></span></td>
<td align="left"><span data-ttu-id="a9509-323">예</span><span class="sxs-lookup"><span data-stu-id="a9509-323">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-324">예</span><span class="sxs-lookup"><span data-stu-id="a9509-324">Yes</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-325">Azure AD ID 보호</span><span class="sxs-lookup"><span data-stu-id="a9509-325">Azure AD Identity Protection</span></span></td>
<td align="left"><span data-ttu-id="a9509-326">예</span><span class="sxs-lookup"><span data-stu-id="a9509-326">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-327">예</span><span class="sxs-lookup"><span data-stu-id="a9509-327">Yes</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-328">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="a9509-328">Azure AD Privileged Identity Management</span></span></td>
<td align="left"><span data-ttu-id="a9509-329">예</span><span class="sxs-lookup"><span data-stu-id="a9509-329">Yes</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-330">MAM(모바일 응용 프로그램 관리)</span><span class="sxs-lookup"><span data-stu-id="a9509-330">Mobile Application Management (MAM)</span></span></td>
<td align="left"><span data-ttu-id="a9509-331">예</span><span class="sxs-lookup"><span data-stu-id="a9509-331">Yes</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9509-332">장치 등록 및 관리</span><span class="sxs-lookup"><span data-stu-id="a9509-332">Device enrollment and management</span></span></td>
<td align="left"><span data-ttu-id="a9509-333">예</span><span class="sxs-lookup"><span data-stu-id="a9509-333">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-334">하나의 조직에서 하나의 장치만 관리할 수 있음</span><span class="sxs-lookup"><span data-stu-id="a9509-334">Only one organization can manage a device</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9509-335">Windows 10 보안 기능(장치 규정 준수에 따른 조건부 액세스에서 장치 관리 요구)</span><span class="sxs-lookup"><span data-stu-id="a9509-335">Windows 10 security capabilities (conditional access based on device compliance requires device management)</span></span></td>
<td align="left"><span data-ttu-id="a9509-336">예</span><span class="sxs-lookup"><span data-stu-id="a9509-336">Yes</span></span></td>
<td align="left"><span data-ttu-id="a9509-337">예</span><span class="sxs-lookup"><span data-stu-id="a9509-337">Yes</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9509-338">필요한 경우 B2B 계정에 라이선스를 추가하여 사용자에게 이러한 추가 기능을 부 여함으로써 작업 환경의 개인 데이터에 대한 액세스를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9509-338">You can add licenses to B2B accounts to give these users additional capabilities, if needed, to protect access to personal data in your environment.</span></span>
