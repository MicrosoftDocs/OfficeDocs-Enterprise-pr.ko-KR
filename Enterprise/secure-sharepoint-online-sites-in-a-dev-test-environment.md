---
title: "개발/테스트 환경에서 SharePoint Online 사이트 보호"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "요약: 개발/테스트 환경에서 공용, 개인, 소문자를 구분 및 기밀 사항이 SharePoint Online 팀 사이트를 만듭니다."
ms.openlocfilehash: 17abee7a293996194a097693607b4b4d9c117046
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>개발/테스트 환경에서 SharePoint Online 사이트 보호

 **요약:** 개발/테스트 환경에서 공용, 개인, 소문자를 구분 및 기밀 사항이 SharePoint Online 팀 사이트를 만듭니다.
  
이 문서는 4 개의 서로 다른 유형의 [SharePoint Online 보안 사이트 및 파일](secure-sharepoint-online-sites-and-files.md) 솔루션을 위한 SharePoint Online 팀 사이트를 포함 하는 개발/테스트 환경을 만드는 단계별 지침을 제공 합니다.
  
![보안 SharePoint Online 개발/테스트 환경의 모든 네 개의 팀 사이트입니다.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
이 개발/테스트 환경을 사용 하 여 정보 보호 동작과 테스트 및 프로덕션 환경에서 SharePoint Online 팀 사이트를 배포 하기 전에 특정 요구 사항에 대 한 설정을 세부적으로 조정 합니다.
  
## <a name="phase-1-create-your-devtest-environment"></a>1 단계: 개발/테스트 환경 만들기

이 단계에서는 가상의 조직에 대 한 Office 365 및 Enterprise 이동성 + 보안에 대 한 평가판 구독 얻을 수 있습니다.
  
먼저, [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)중 **2 단계** 지침을 따릅니다.
  
다음으로, EMS 평가판 구독에 등록 하 고 Office 365 평가판 구독와 같은 조직에 추가 합니다.
  
1. 평가판 구독의 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 필요한 경우에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. **Admin** 타일을 클릭 합니다.
    
3. On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.
    
4. On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.
    
5. On the **Confirm your order** page, click **Try now**.
    
6. On the **Order receipt** page, click **Continue**.
    
다음으로, 엔터프라이즈 이동성 + 전역 관리자 계정에 대 한 보안 E5 라이선스 사용 하도록 설정 합니다.
  
1. 왼쪽 탐색 영역에서 브라우저에서 **Office 365 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.
    
2. Click your global administrator account, and then click **Edit** for **Product licenses**.
    
3. On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>2 단계: 만들기 및 Azure Active Directory (AD) 그룹 및 사용자를 구성 합니다.

이 단계에서 만들기 및 가상의 조직에 대 한 Azure AD 그룹 및 사용자를 구성 합니다.
  
먼저 Azure 포털을 사용 하는 일반적인 조직에 대 한 그룹의 집합을 만듭니다.
  
1. 브라우저에서 별도 탭을 만들고 [https://portal.azure.com](https://portal.azure.com)에서 Azure 포털으로 이동 합니다. 필요한 경우 Office 365 E5 평가판 구독에 대 한 전역 관리자 계정의 자격 증명을 사용 하 여 로그인 합니다.
    
2. Azure 포털에서 클릭 **Azure Active Directory > 사용자 및 그룹 > 모든 그룹**합니다.
    
3. **모든 그룹** 블레이드에서 **+ 새 그룹을**클릭 합니다.
    
4. **그룹** 블레이드에서:
    
  - **사용자 이름에서**형식 **C 제품군**
    
  - **멤버 자격**에서 **할당** 을 선택 합니다.
    
  - **Office를 사용 하도록 설정 기능**에 대 한 **예** 를 클릭 합니다.
    
5. **만들기**클릭 한 다음 **그룹** 블레이드를 닫습니다.
    
6. 다음 그룹 이름에 대해 3-5 단계를 반복 합니다.
    
  - IT 담당자
    
  - 리서치 직원
    
  - 정규 직원
    
  - 마케팅 직원
    
  - 영업 직원
    
7. 브라우저 열기에서 Azure 포털 탭을 유지 합니다.
    
다음으로 자동 라이선스 그룹의 구성원 Office 365 및 EMS 구독에 대 한 라이선스를 자동으로 할당 됩니다 되도록 구성 합니다.
  
1. Azure 포털에서 클릭 **Azure Active Directory > 라이선스 > 모든 제품**합니다.
    
2. 목록에서 **엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise e 5**를 선택한 다음 **할당**을 클릭 합니다.
    
3. **라이선스를 할당** 블레이드에서 **사용자 및 그룹을**클릭 합니다.
    
4. 그룹 목록에서 다음을 선택 합니다.
    
  - C-제품군
    
  - IT 담당자
    
  - 리서치 직원
    
  - 정규 직원
    
  - 마케팅 직원
    
  - 영업 직원
    
5. **선택**을 클릭 하 고 **할당**을 클릭 합니다.
    
6. 브라우저에서 Azure 포털 탭을 닫습니다.
    
다음에는 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)있습니다.
  
조직 이름, 사용자 위치 및 공통 암호를 입력 하 고 스크립트 ISE (통합 환경) 사용자 계정을 만들고 해당 그룹에 추가 하는 PowerShell 명령 프롬프트에서 다음이 명령을 실행 합니다.
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> 여기에 일반적인 암호 사용 자동화 및 개발/테스트 환경에 대 한 구성이 쉽기 때문입니다. 프로덕션 구독에 대 한 권장 되지 않습니다. 
  
라이선스 그룹 기반 제대로 작동 하는지 확인 하려면 다음이 단계를 사용 합니다.
  
1. 브라우저의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
2. 브라우저의 새 **Office 관리 센터** 탭에서 **사용자**를 클릭 합니다.
    
3. 사용자의 목록에서 **CEO**를 클릭 합니다.
    
4. **CEO** 사용자 계정의 속성을 나열 하는 창에는 할당 된 **제품 라이선스**) (에서 **엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise E5** 라이선스를 확인 합니다.
    
## <a name="phase-3-create-office-365-labels"></a>3 단계: Office 365 레이블 만들기

이 단계에서는 다양 한 수준의 SharePoint Online 팀 사이트 문서 폴더에 대 한 보안에 대 한 레이블을 만듭니다.
  
1. 필요한 경우 인터넷 브라우저의 개인 인스턴스를 사용 하 고 Office 365 E5 평가판 구독의 전역 관리자 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
3. 브라우저의 새 **Office 관리 센터** 탭을 클릭 **관리 센터 > 보안 &amp; 준수**합니다.
    
4. 새에서 **홈-보안 &amp; 준수** 탭 클릭 하 여 브라우저의 **분류 > 레이블**합니다.
    
5. **홈 > 레이블** 창 **레이블 만들기**를 클릭 합니다.
    
6. **이름에 레이블** 창에서 **내부 공용**, 입력 하 고 ****을 클릭 합니다.
    
7. **레이블 설정** 창에서 **다음**을 클릭 합니다.
    
8. **설정 검토** 창에서 **이 레이블 만들기**를 클릭 하 고 **닫기**를 클릭 합니다.
    
9. 이러한 추가 레이블에 대 한 5 ~ 8 단계를 반복 합니다.
    
  - 개인
    
  - Sensitive
    
  - 기밀
    
10. **홈 > 레이블** 창 **게시 레이블**을 클릭 합니다.
    
11. **게시를 선택 레이블** 창에서 **게시를 선택 레이블을**클릭 합니다.
    
12. **Choose 레이블** 창에서 **추가** 클릭 하 고 모든 4 개의 레이블을 선택 합니다.
    
13. Click **Done**.
    
14. On the **Choose labels to publish** pane, click **Next**.
    
15. **Choose 위치** 창에서 **다음**을 클릭 합니다.
    
16. **이름에 정책** 창에서 **이름** **예제 조직** 를 입력 하 고 ****을 클릭 합니다.
    
17. **설정 검토** 창에서 **게시 레이블**를 클릭 한 다음 **닫기**를 클릭 합니다.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>4 단계: SharePoint Online 팀 사이트 만들기

이 단계에서 만들고 예제 조직에 대 한 다음과 같은 네가지 유형의 SharePoint Online 팀 사이트를 구성 합니다.
  
### <a name="organization-wide-team-site"></a>조직 전체 팀 사이트

초기 계획 공용 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.
  
1. 필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. In the list of tiles, click **SharePoint**.
    
3. 브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **사이트 이름** **조직 전체**를 입력 합니다. 
    
6. **팀 사이트 설명** **전체 조직에 대 한 SharePoint 사이트**를 입력 합니다.
    
7. **개인 설정** **공용-이 사이트에 액세스할 수는 조직의 모든 사용자**를 선택 하 고 ****을 클릭 합니다.
    
8. On the **Who do you want to add?** pane, click **Finish**.
    
Next, configure the documents folder of the Organization wide team site for the Internal Public label.
  
1. In the **Organization wide-Home** tab of your browser, click **Documents**.
    
2. Click the settings icon, and then click **Library settings**.
    
3. **사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.
    
4. **레이블 설정 적용** **내부 공용**을 선택 하 고 **저장**을 클릭 합니다.
    
구성 결과는 다음과 같습니다.
  
![조직 차원 공용 SharePoint Online 팀 사이트에 대한 기준 수준 보호입니다.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>프로젝트 1 팀 사이트

조직 내에서 프로젝트에 대 한 초기 계획 개인 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.
  
1. 필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. In the list of tiles, click **SharePoint**.
    
3. 브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **사이트 이름** **프로젝트 1**을 입력 합니다. 
    
6. **팀 사이트 설명** 에서 **프로젝트 1에 대 한 SharePoint 사이트**를 입력 합니다.
    
7. **개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.
    
8. On the **Who do you want to add?** pane, click **Finish**.
    
다음으로 개인 레이블에 대 한 프로젝트 1 팀 사이트의 문서 폴더를 구성 합니다.
  
1. 브라우저의 **프로젝트 1 홈** 탭에서 **문서**를 클릭 합니다.
    
2. 설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.
    
3. **사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.
    
4. **레이블 설정 적용** **개인**을 선택 하 고 **저장**을 클릭 합니다.
    
구성 결과는 다음과 같습니다.
  
![Project1 개인 SharePoint Online 팀 사이트에 대한 기준 수준의 보호입니다.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>마케팅 캠페인 팀 사이트

대부분은 중요 하지 수준의 격리 된 SharePoint Online 팀 사이트 마케팅 캠페인 리소스에 대 한를 만들려면 다음을 수행 합니다.
  
1. Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In the list of tiles, click **SharePoint**.
    
3. 브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **팀 사이트 이름** **마케팅 캠페인**을 입력 합니다.
    
6. In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.
    
7.  In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.
    
8. On the **Who do you want to add?** pane, click **Finish**.
    
9. On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.
    
10. In the **Site permissions** pane, click **Advanced permissions settings**.
    
11. In the new **Permissions** tab in your browser, click **Access Request Settings**.
    
12. In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.
    
13. Click **Marketing campaigns Members** in the list.
    
14. On the **People and Groups** page, click **New**.
    
15. In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.
    
16. Repeat steps 14 and 15 for the **Researcher1** user account.
    
17. 브라우저에서 뒤로 단추를 클릭합니다.
    
18. Click **Marketing campaigns Owners** in the list.
    
19. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
20. In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.
    
21. 브라우저에서 뒤로 단추를 클릭합니다.
    
22. Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.
    
사용 권한 구성 결과는 다음과 같습니다.
  
- **마케팅 캠페인 Members** SharePoint 그룹에는 **마케팅 캠페인** 그룹 (포함 하는 전역 관리자 사용자 계정), (Marketing1 및 Marketing2 사용자가 들어 있는 **마케팅 직원** 그룹 포함 계정) 및 **Researcher1** 사용자 계정입니다.
    
- The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).
    
- The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.
    
- Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).
    
- Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.
    
Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.
  
1. In the **Marketing campaigns-Home** tab of your browser, click **Documents**.
    
2. Click the settings icon, and then click **Library settings**.
    
3. Under **Permissions and Management**, click **Apply label to items in this library**.
    
4. In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.
    
Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.
  
1. From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.
    
2. On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.
    
3. In the **Data loss prevention** pane, click **+ Create a policy**.
    
4. In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.
    
5. In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.
    
6. In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.
    
7. In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.
    
8. In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.
    
9. In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.
    
10. In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.
    
11. In the **Choose the types of content to protect** pane, click **Save**.
    
12. In the **Customize the types of sensitive info you want to protect** pane, click **Next**.
    
13. In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.
    
14. In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.
    
15. In the text box, type or paste in the following:
    
  - To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.
    
16. **확인**을 클릭합니다.
    
17. In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.
    
18. In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.
    
19. In the **Review your settings** pane, click **Create**, and then click **Close**.
    
구성 결과는 다음과 같습니다.
  
![격리된 SharePoint Online 팀 사이트의 마케팅 캠페인에 대한 중요한 수준의 보호입니다.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>회사 전략 팀 사이트

조직의 수석 경영진의 전략적 회사 리소스에 대 한 매우 기밀 수준에서 격리 된 SharePoint Online 팀 사이트를 만들 하려면 다음을 수행 합니다.
  
1. 필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **팀 사이트 이름**, **회사 전략**을 입력 합니다.
    
6. **팀 사이트 설명** **회사 전략 (기밀)에 대 한 SharePoint 사이트**를 입력 합니다.
    
7.  **개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.
    
8. 에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.
    
9. 도구 모음에서 브라우저에서 새 **회사 전략** 탭에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.
    
10. **사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.
    
11. 브라우저에서 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.
    
12. **액세스 요청 설정** 대화 상자에서 **사이트 및 개별 파일 및 폴더 공유 허용 구성원** 및 **사이트 구성원 그룹에 다른 사용자를 초대 하도록 허용 구성원** (있도록 삭제 세 확인란을 모두 선택이 취소 됩니다), 다음 **를 클릭 하 고 확인**합니다.
    
13. 목록에서 **회사 전략 구성원을** 클릭 합니다.
    
14. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
15. **공유** 대화 상자에서 입력 **C 제품군**을 선택한 다음 **공유**를 클릭 합니다.
    
16. 목록에서 **회사 전략 소유자를** 클릭 합니다.
    
17. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
18. **공유** 대화 상자에서 입력 **IT 담당자**를 선택한 다음 **공유**를 클릭 합니다.
    
19. 브라우저에서 뒤로 단추를 클릭합니다.
    
20. 브라우저에서 **사용자 및 그룹** 탭을 닫은 브라우저에서 **회사 전략 홈** 탭을 클릭 한 다음 **사이트 사용 권한** 창을 닫습니다.
    
사용 권한 구성 결과는 다음과 같습니다.
  
- The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).
    
- The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).
    
- The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.
    
- Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).
    
- Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.
    
Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.
  
1. In the **Company strategy-Home** tab of your browser, click **Documents**.
    
2. Click the settings icon, and then click **Library settings**.
    
3. **사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.
    
4. In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.
    
다음으로, DLP 정책 구성 요소 (영문)가 사용 하는 조직 외부의 회사 전략 사이트를 포함 하는 매우 기밀 레이블로 SharePoint Online 팀 사이트에 문서를 공유 하는 경우.
  
1. 필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.
    
3. 새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.
    
4. **데이터 손실 방지** 창에서 **+ 정책 만들기를**클릭 합니다.
    
5. **서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.
    
6. **이름에 정책** 창에서 **이름** **매우 기밀 레이블 SharePoint Online 팀 사이트** 를 입력 하 고 ****을 클릭 합니다.
    
7. **선택 위치** 창에서 **특정 위치를 선택 합니다.**를 클릭 하 고 ****을 클릭 합니다.
    
8. 위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.
    
9. **중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **편집**을 클릭 합니다.
    
10. **보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.
    
11. **레이블** 창에서 **+ 기호 추가**클릭, **기밀 사항이** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.
    
12. **보호 하기 위해 콘텐츠 형식 선택** 창에서 **저장**을 클릭 합니다.
    
13. **중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **다음**을 클릭 합니다.
    
14. **는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **사용자 지정 팁 및 전자 메일을**클릭 합니다.
    
15. **사용자 지정 정책 팁 및 전자 메일 알림** 창에서 **사용자 지정 정책 팁 텍스트를**클릭 합니다.
    
16. 텍스트 상자에 입력 하거나 다음에 붙여넣습니다.
    
  - 조직 외부의 사용자와 공유 하려면 파일을 다운로드 하 고 파일을 엽니다. 파일을 다음 문서 보호를 클릭 하 고 암호를 암호화 하 고 강력한 암호를 지정 합니다. 별도 전자 메일 또는 다른 수단 통신의 암호를 보냅니다.
    
17. **확인**을 클릭합니다.
    
18. **는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **, 업무 효율성을 재정의 하려면 필요**를 선택 하 고 **다음**을 클릭 합니다.
    
19. **먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.
    
20. **설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.
    
다음으로, [Office 365 관리 센터와 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)의 지시를 따릅니다.
  
다음, 새 범위가 지정 된 정책 및 하위 레이블 보호 및 다음 단계를 사용 하 여 권한을 사용 하 여 Azure 정보 보호를 구성 합니다.
  
1. 보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 브라우저의 별도 탭에서 Azure 포털 ([https://portal.azure.com](https://portal.azure.com))로 이동 합니다.
    
3. 처음으로 Azure 정보 보호를 구성 하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조 하십시오.
    
4. 목록 창에서 **서비스를 더**, **정보**를 입력 한 다음 **Azure 정보 보호**를 클릭 합니다.
    
5. **Azure 정보 보호** 블레이드에서를 클릭 **정책 범위 > 새 정책을 추가 +**합니다.
    
6. **정책 이름** 및 **설명**에 **회사 전략 팀 사이트의 문서에 대 한 레이블** **CompanyStrategy** 를 입력 합니다.
    
7. 클릭 **있는 사용자 또는 그룹에이 정책을 가져오려면 선택 > 사용자/그룹**, **C 제품군**을 선택 합니다.
    
8. 클릭 **선택 > 확인**합니다.
    
9. **기밀 사항이** 레이블에 대 한 줄임표 (...)를 클릭 하 고 **하위 레이블 추가**클릭 합니다.
    
10. **이름** 및 **설명**의 레이블 내에 대 한 설명을 하위 레이블에 대 한 이름을 입력 합니다.
    
11. **문서 및이 레이블이 포함 된 전자 메일에 대 한 사용 권한 설정**에서 **암호로 보호**를 클릭 합니다.
    
12. **보호** 섹션에서 **Azure (클라우드 키)를**클릭 합니다.
    
13. **보호** 블레이드 **보호 설정**아래에서 **+ 추가 사용 권한을**클릭 합니다.
    
14. **추가 사용 권한** 블레이드 **지정 사용자 및 그룹을**에서 **디렉터리 찾아보기 +**을 클릭 합니다.
    
15. **AAD 사용자 및 그룹** 창에서 **C 제품군**선택 하 고 **선택**을 클릭 합니다.
    
16. **사전 설정에서 사용 권한을 선택**아래에서 **인쇄**, **복사 및 콘텐츠 추출**및 **앞으로** 확인란의 선택을 취소 합니다.
    
17. 두 번 **확인** 을 클릭 합니다.
    
18. **하위 레이블** 블레이드에서 **저장**을 클릭 합니다.
    
19. 새 범위가 지정 된 정책 블레이드를 닫습니다.
    
20. **Azure 정보 보호-범위가 지정 된 정책** 블레이드에서 **게시**클릭 한 다음 **예**를 클릭 합니다.
    
Azure 정보 보호 하 고이 새 레이블을 사용 하 여 문서를 보호 하려면 테스트 컴퓨터에서 [Azure 정보 보호 클라이언트 설치](https://docs.microsoft.com/information-protection/rms-client/install-client-app) 를 수행 해야, Office 365 포털에서 Office를 설치 하 고에 **계정을 사용 하 여 Microsoft Word에서 로그인 C-제품군** 평가판 구독의 그룹입니다.
  
구성 결과는 다음과 같습니다.
  
![격리된 SharePoint Online 팀 사이트의 회사 전략에 대한 높은 기밀 수준의 보호입니다.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
이제 평가판 구독에서 다양 한 사용자 계정에 대 한 액세스를 테스트 하 고 이러한 4 개 사이트에서 문서를 만들 준비가 되었습니다.
  
4 개의 모든 SharePoint Online 팀 사이트에 대 한 전체 구성 다음과 같습니다.
  
![보안 SharePoint Online 개발/테스트 환경의 모든 네 개의 팀 사이트입니다.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>다음 단계

보안 SharePoint Online 사이트의 프로덕션 배포에 대 한 준비가 되 면 [보안 SharePoint Online 사이트 및 파일에](secure-sharepoint-online-sites-and-files.md) 대 한 자세한 정보와 단계별 배포 문서 링크를 참조 합니다.
  
## <a name="see-also"></a>See Also

[SharePoint Online 사이트 및 파일의 보안](secure-sharepoint-online-sites-and-files.md)
  
[보안 솔루션](security-solutions.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




