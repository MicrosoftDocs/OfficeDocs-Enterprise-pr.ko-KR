---
title: 동시에 여러 사용자를 Office 365에 추가 - 관리자 도움말
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: '스프레드시트 또는 다른 CSV로 서식이 지정 된 파일의 목록에서 비즈니스용 Office 365에 여러 사용자를 추가하는 방법을 알아봅니다. YouTube에서 Office 365에 계정을 추가하는 방법을 설명하는 비디오를 보세요. 이 프로세스 종료 시, 계정이 있는 각 사용자에게는 Office 365 사서함이 있습니다. '
ms.openlocfilehash: 5256e67139b50c1804f83e11d00c115b5f419f47
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782428"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="feeb4-105">동시에 여러 사용자를 Office 365에 추가 - 관리자 도움말</span><span class="sxs-lookup"><span data-stu-id="feeb4-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="feeb4-p102">팀의 각 구성원이 전자 메일 및 Office와 같은 Office 365 서비스에 로그인 및 액세스하려면 사용자 계정이 있어야 합니다. 사용자가 많은 경우 Excel 스프레드시트 또는 CSV 형식으로 저장된 다른 파일에서 모든 계정을 한 번에 추가할 수 있습니다. [CSV 형식이란?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="feeb4-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="feeb4-109">Microsoft 365 관리 센터에서 여러 사용자를 Office 365에 추가</span><span class="sxs-lookup"><span data-stu-id="feeb4-109">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="feeb4-110">회사 또는 학교 계정을 사용하여 Office 365에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="feeb4-111">관리 센터에서 **사용자** \> **활성 사용자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-111">In the Admin center, choose **Users** \> **Active users**.</span></span>
    
    ![관리 센터에서 사용자와 활성 사용자를 차례로 선택합니다.](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="feeb4-113">
            **자세히\*\* 드롭다운에서 *\*여러 사용자 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="feeb4-114">
            **여러 사용자 가져오기\*\* 패널에서 예제 데이터가 입력되어 있는 예제 CSV 파일과 입력되어 있지 않은 예제 CSV 파일 중 선택하여 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![자세히 드롭다운에서 여러 사용자 가져오기 선택](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="feeb4-116">스프레드시트는 **정확히 동일한 열 머리글** 을 예제(사용자 이름, 성 등...)로 포함해야 합니다. 서식 파일을 사용하는 경우에는 메모장과 같은 텍스트 편집 도구에서 열어서 행 1에 있는 모든 데이터는 그대로 두고 행 2와 그 아래 행에만 데이터를 입력해 보세요.</span><span class="sxs-lookup"><span data-stu-id="feeb4-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="feeb4-117">스프레드시트는 사용자 이름(예: hyunki@contoso.com)과 각 사용자에 대한 표시 이름(예: 유현기)에 대한 값도 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="feeb4-118">상자에 파일 경로를 입력하거나 **찾아보기**를 선택하여 CSV 파일의 위치를 찾은 다음 **확인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![CSV 파일이 확인됨](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="feeb4-p103">파일에 문제가 있는 경우에는 문제가 창에 표시됩니다. 로그 파일을 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="feeb4-122">
            \*\*Set user options\*\*(사용자 옵션 설정) 대화 상자에서는 로그인 상태를 설정하고 모든 사용자에게 할당할 제품 라이선스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="feeb4-123">
            \*\*View your result\*\*(결과 보기) 대화 상자에서는 결과를 자신이나 다른 사용자(암호는 일반 텍스트가 됨)에 보내도록 선택할 수 있으며, 만들어진 사용자의 수와 새 사용자에게 할당하기 위해 추가 라이선스를 구입해야 하는지를 알 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="feeb4-124">비디오 보기</span><span class="sxs-lookup"><span data-stu-id="feeb4-124">Watch the video</span></span>
<span data-ttu-id="feeb4-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="feeb4-125"></span></span>

 <span data-ttu-id="feeb4-126">많은 사용자를 추가하는 방법을 보여 주는 짧은 비디오를 보세요.</span><span class="sxs-lookup"><span data-stu-id="feeb4-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="feeb4-127">다음 단계</span><span class="sxs-lookup"><span data-stu-id="feeb4-127">Next steps</span></span>
<span data-ttu-id="feeb4-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="feeb4-128"></span></span>

- <span data-ttu-id="feeb4-129">이제 이 사용자에게 계정이 있으므로 [PC 또는 Mac에 Office 365 또는 Office 2016를 다운로드하여 설치하거나 다시 설치](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-129">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="feeb4-130">팀의 각 사용자는 최대 5대의 PC 또는 Mac에 Office 365를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-130">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="feeb4-131">각 사용자는 iPhones, iPads 및 Android 휴대폰 및 태블릿과 같은 최대 5대의 태블릿과 5대의 휴대폰에서 [모바일 장치의 Office 앱 및 전자 메일을 설정](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-131">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="feeb4-132">이 방법으로 어디서나 Office 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-132">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="feeb4-133">포괄적인 설치 단계를 보려면 [Office 365 비즈니스 에디션 설정](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="feeb4-133">See [Set up Office 365 for Business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="feeb4-134">Office 365에 사용자를 추가하는 방법에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="feeb4-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="feeb4-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="feeb4-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="feeb4-136">CSV 형식이란?</span><span class="sxs-lookup"><span data-stu-id="feeb4-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="feeb4-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="feeb4-137"></span></span>

<span data-ttu-id="feeb4-p106">CSV 파일은 쉼표로 구분된 값을 사용한 파일입니다. 모든 텍스트 편집기나 Excel과 같은 스프레드시트 프로그램에서 이와 같은 파일을 만들거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="feeb4-p107">시작점으로 [이 예제 스프레드시트](https://www.microsoft.com/en-us/download/details.aspx?id=45485)를 다운로드할 수 있습니다. Office 365에는 첫 행에 열 머리글이 필요하므로 이를 다른 것으로 바꾸지 마세요.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="feeb4-142">파일을 새 이름으로 저장하고 CSV 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Excel CSV 형식으로 파일을 저장하는 방법 이미지](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="feeb4-p108">파일을 저장할 때 파일을 CSV 형식으로 저장하면 통합 문서의 일부 기능이 손실된다는 메시지가 표시될 수 있지만 괜찮습니다. **예**를 클릭하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Excel에서 파일을 정말로 CSV 형식으로 저장할지 묻는 메시지 그림](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="feeb4-148">스프레드시트 서식 지정 팁</span><span class="sxs-lookup"><span data-stu-id="feeb4-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="feeb4-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="feeb4-149"></span></span>

- <span data-ttu-id="feeb4-p109">**예제 스프레드시트와 같은 열 머리글이 필요한가요?** 예. 예제 스프레드시트에는 첫 행에 열 머리글이 포함되어 있습니다. 해당 머리글은 필수 항목입니다. Office 365에 추가할 각 사용자에 대해 머리글 아래에 행을 만듭니다. 열 머리글을 추가, 변경 또는 삭제할 경우 Office 365에서 파일의 정보를 토대로 사용자를 만들지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="feeb4-p110">**각 사용자에 대해 필요한 정보가 일부만 있는 경우** 사용자 이름 및 표시 이름은 필수 항목입니다. 이 정보 없이는 새 사용자를 추가할 수 없습니다. 팩스 등 기타 정보가 없는 경우 공백과 쉼표를 사용해 필드를 빈 상태로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="feeb4-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="feeb4-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="feeb4-p113">**다른 국가나 지역의 사용자를 추가하는 경우** 각 지역에 대해 별도의 스프레드시트를 만듭니다. 각 스프레드시트의 사용자 일괄 추가 마법사를 단계적으로 따르면 작업 중인 파일에 포함된 모든 사용자를 한 곳에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="feeb4-p114">**사용할 수 있는 문자 수 제한** 다음 표에서는 예제 스프레드시트의 사용자 데이터 열 레이블 및 최대 문자 길이를 각각 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="feeb4-172">**사용자 데이터 열 레이블**</span><span class="sxs-lookup"><span data-stu-id="feeb4-172">**User data column label**</span></span>|<span data-ttu-id="feeb4-173">**최대 문자 길이**</span><span class="sxs-lookup"><span data-stu-id="feeb4-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="feeb4-174">사용자 이름 (필수)</span><span class="sxs-lookup"><span data-stu-id="feeb4-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="feeb4-p115">기호(@)를 포함하여 이름@도메인.\<확장자\> 형식으로 된 79자. 사용자의 별칭은 30자, 도메인 이름은 48자를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="feeb4-177">이름</span><span class="sxs-lookup"><span data-stu-id="feeb4-177">First Name</span></span>  <br/> |<span data-ttu-id="feeb4-178">64</span><span class="sxs-lookup"><span data-stu-id="feeb4-178">6.4</span></span>  <br/> |
|<span data-ttu-id="feeb4-179">성</span><span class="sxs-lookup"><span data-stu-id="feeb4-179">Last Name</span></span>  <br/> |<span data-ttu-id="feeb4-180">64</span><span class="sxs-lookup"><span data-stu-id="feeb4-180">6.4</span></span>  <br/> |
|<span data-ttu-id="feeb4-181">표시 이름 (필수)</span><span class="sxs-lookup"><span data-stu-id="feeb4-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="feeb4-182">256</span><span class="sxs-lookup"><span data-stu-id="feeb4-182">256 KB</span></span>  <br/> |
|<span data-ttu-id="feeb4-183">직함</span><span class="sxs-lookup"><span data-stu-id="feeb4-183">Job Title</span></span>  <br/> |<span data-ttu-id="feeb4-184">64</span><span class="sxs-lookup"><span data-stu-id="feeb4-184">6.4</span></span>  <br/> |
|<span data-ttu-id="feeb4-185">부서</span><span class="sxs-lookup"><span data-stu-id="feeb4-185">Department</span></span>  <br/> |<span data-ttu-id="feeb4-186">64</span><span class="sxs-lookup"><span data-stu-id="feeb4-186">6.4</span></span>  <br/> |
|<span data-ttu-id="feeb4-187">사무실 번호</span><span class="sxs-lookup"><span data-stu-id="feeb4-187">Office Number</span></span>  <br/> |<span data-ttu-id="feeb4-188">128</span><span class="sxs-lookup"><span data-stu-id="feeb4-188">128 GB</span></span>  <br/> |
|<span data-ttu-id="feeb4-189">사무실 전화</span><span class="sxs-lookup"><span data-stu-id="feeb4-189">Office Phone</span></span>  <br/> |<span data-ttu-id="feeb4-190">64</span><span class="sxs-lookup"><span data-stu-id="feeb4-190">6.4</span></span>  <br/> |
|<span data-ttu-id="feeb4-191">휴대폰</span><span class="sxs-lookup"><span data-stu-id="feeb4-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="feeb4-192">64</span><span class="sxs-lookup"><span data-stu-id="feeb4-192">6.4</span></span>  <br/> |
|<span data-ttu-id="feeb4-193">팩스</span><span class="sxs-lookup"><span data-stu-id="feeb4-193">Fax</span></span>  <br/> |<span data-ttu-id="feeb4-194">64</span><span class="sxs-lookup"><span data-stu-id="feeb4-194">6.4</span></span>  <br/> |
|<span data-ttu-id="feeb4-195">주소</span><span class="sxs-lookup"><span data-stu-id="feeb4-195">Address</span></span>  <br/> |<span data-ttu-id="feeb4-196">1023</span><span class="sxs-lookup"><span data-stu-id="feeb4-196">1023</span></span>  <br/> |
|<span data-ttu-id="feeb4-197">구/군/시</span><span class="sxs-lookup"><span data-stu-id="feeb4-197">City</span></span>  <br/> |<span data-ttu-id="feeb4-198">128</span><span class="sxs-lookup"><span data-stu-id="feeb4-198">128 GB</span></span>  <br/> |
|<span data-ttu-id="feeb4-199">시/도</span><span class="sxs-lookup"><span data-stu-id="feeb4-199">State or Province</span></span>  <br/> |<span data-ttu-id="feeb4-200">128</span><span class="sxs-lookup"><span data-stu-id="feeb4-200">128 GB</span></span>  <br/> |
|<span data-ttu-id="feeb4-201">우편 번호</span><span class="sxs-lookup"><span data-stu-id="feeb4-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="feeb4-202">40</span><span class="sxs-lookup"><span data-stu-id="feeb4-202">40 KB</span></span>  <br/> |
|<span data-ttu-id="feeb4-203">국가 또는 지역</span><span class="sxs-lookup"><span data-stu-id="feeb4-203">Country or Region</span></span>  <br/> |<span data-ttu-id="feeb4-204">128</span><span class="sxs-lookup"><span data-stu-id="feeb4-204">128 GB</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="feeb4-205">Office 365에 사용자를 추가할 때 여전히 문제가 발생하나요?</span><span class="sxs-lookup"><span data-stu-id="feeb4-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="feeb4-p116">**스프레드시트 형식이 올바른지 다시 한 번 확인합니다.** 열 머리글이 예제 파일의 머리글과 일치하는지 확인합니다. 문자 길이 규칙을 준수했고 각 필드를 쉼표로 구분했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="feeb4-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a><span data-ttu-id="feeb4-211">기존 관리 센터에서 여러 사용자를 Office 365에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-211">Add multiple users to Office 365 in the old admin center</span></span>

1. <span data-ttu-id="feeb4-212">[이 예제 스프레드시트](https://www.microsoft.com/en-us/download/details.aspx?id=45485)를 다운로드하고 Excel에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="feeb4-213">스프레드시트는 **정확히 동일한 열 머리글** 을 예제(사용자 이름, 성 등...)로 포함해야 합니다. 서식 파일을 사용하는 경우에는 행 1에 있는 모든 데이터는 그대로 두고 행 2와 그 아래 행에만 데이터를 입력해 보세요.</span><span class="sxs-lookup"><span data-stu-id="feeb4-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="feeb4-p118">스프레드시트는 사용자 이름(예: hyunki@contoso.com)과 각 사용자에 대한 표시 이름(예: 유현기)에 대한 값도 포함해야 합니다. 다른 필드는 공백으로 두려면 다음 그림과 같이 필드에 공백과 쉼표를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![빈 행이 지정되어 있는 예제 CVS 파일](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="feeb4-p119">다른 국가에서 작업하는 사용자가 있는 경우 국가별로 사용자에 대한 스프레드시트를 하나씩 만들어야 합니다. 예를 들어 스프레드시트 하나에는 미국에서 작업하는 사람을 모두 나열하고 또 다른 스프레드시트에는 일본에서 작업하는 사람을 모두 나열합니다. 이렇게 하는 이유는 Office 365 서비스의 가용성이 지역별로 다르기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="feeb4-p120">**팁:** Office 365에 여러 사용자를 추가하기 전에 예제 스프레드시트로 연습할 수 있습니다. 예를 들어 사용자 5명 또는 10명의 데이터를 사용하여 예제 스프레드시트를 편집하고 파일을 새 이름으로 저장합니다. 이 절차에 설명된 단계를 실행하여 결과를 확인한 다음 새 계정을 삭제하고 처음부터 다시 시작합니다. 이 방법으로 자신의 상황에 맞게 모든 데이터를 가져오는 연습을 할 수 있습니다. [스프레드시트 서식 지정 팁](add-several-users-at-the-same-time.md#__toc314595848)도 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="feeb4-225">회사 또는 학교 계정을 사용하여 Office 365에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="feeb4-226">관리 센터로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-226">Go to the old admin center.</span></span>
    
4. <span data-ttu-id="feeb4-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="feeb4-p122">**사용자** \> **활성 사용자**를 선택하여 사용자 일괄 추가 마법사로 이동합니다. 다음 그림에서처럼 ![Office 365에 여러 사용자 추가 아이콘](media/3481ffea-d552-4a7f-9a3b-014504e69746.png)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![관리 센터의 사용자 섹션 이미지](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="feeb4-235">사용자 일괄 추가 마법사가 나타나고 사용자 그룹을 Office 365에 추가하는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="feeb4-236">'1단계 - CSV 파일 선택'에서 다음 그림에 나오는 것처럼 고유 스프레드시트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![사용자 일괄 추가 마법사 1단계 - CSV 파일 선택](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="feeb4-238">'2단계 - 확인'에서 마법사는 스프레드시트에 있는 콘텐츠의 서식이 올바른지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![사용자 일괄 추가 마법사 2단계 - 확인](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="feeb4-p123">'3단계 - 설정'에서는 스프레드시트에 나열된 사용자들이 Office 365를 사용할 수 있도록 **허용**을 선택합니다. 또한 이러한 사용자가 Office 365를 사용할 국가를 선택합니다. 조직의 일부 사용자가 다른 국가에서 Office 365를 사용하는 경우 이름을 사용하여 별도의 스프레드시트를 만들고 사용자 일괄 추가 마법사를 다시 실행하여 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![사용자 일괄 추가 마법사 3단계 - 설정](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="feeb4-244">라이선스 할당 페이지에서 사용 가능한 라이선스 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![사용자 일괄 추가 마법사 4단계 - 라이선스](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="feeb4-246">**추가 라이선스 구입**을 선택할 수 있지만 사용자 일괄 추가 마법사를 종료하고 Microsoft 365 관리 센터의 **청구**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-246">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Microsoft 365 admin center.</span></span> <span data-ttu-id="feeb4-247">추가 라이선스를 구입한 후에는 주문이 처리될 때까지 몇 분 정도 기다렸다가 사용자 일괄 추가 마법사를 처음부터 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-247">After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="feeb4-248">추가 라이선스를 구입하지 않으면 스프레드시트에 나열된 모든 사용자에게 대해 계정이 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="feeb4-249">이 예제에서는 추가 라이선스를 구입하지 않고 사용자 일괄 추가 마법사를 계속하면 어떻게 되는지 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="feeb4-250">'5단계 - 결과 보내기'에서는 스프레드시트에 있는 사용자에 대한  *모든*  Office 365 사용자 이름과 임시 암호가 나열된 전자 메일을 수신하도록 할 사용자의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![사용자 일괄 추가 마법사 5단계 - 결과 보내기](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="feeb4-p125">'5단계 - 결과 보내기'에서 지정한 모든 전자 메일 주소로 다음 전자 메일이 전송됩니다. 이 전자 메일에는 만들어진 계정이 표시되어 있습니다. 라이선스가 충분하지 않아 일부 사용자에 대해서는 계정이 만들어지지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![사용자 자격 증명 정보가 포함된 예제 전자 메일](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="feeb4-p126">나중에 추가 라이선스를 구입하고 동일한 스프레드시트를 사용하여 사용자 일괄 추가 마법사를 다시 실행할 수 있습니다. 마법사가 이미 계정을 가지고 있는 사용자를 건너뜁니다. 결과 보고서에 해당 정보의 사용자가 이미 계정을 가지고 있음을 나타내는 "사용자 이름이 중복되었습니다." 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="feeb4-258">사용자 일괄 추가 마법사의 마지막 페이지에는 다음 그림에 나온 것처럼 사용자 이름과 임시 암호가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![사용자 일괄 추가 마법사 6단계 - 결과 보내기](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="feeb4-p127">Office 365에 사용자를 추가한 후에는 해당 사용자에게 Office 365 계정 정보를 알려야 합니다. 새 암호를 전달하는 데 일반 프로세스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="feeb4-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

