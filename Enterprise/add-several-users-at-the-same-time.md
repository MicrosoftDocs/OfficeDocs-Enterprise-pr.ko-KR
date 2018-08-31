---
title: Office 365에 여러 사용자를 동시에 추가 - 관리자 도움말
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
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
description: '파일을 서식이 지정 된 스프레드시트나 다른 CSV의 목록에서 비즈니스를 위한 Office 365에 여러 사용자를 추가 하는 방법에 알아봅니다. Office 365에 계정을 추가 하는 방법에 설명 하는 YouTube에서 비디오를 시청 합니다. 이 프로세스가 끝날 때 계정 사용 하 여 각 사용자는 Office 365 사서함을 갖게 됩니다. '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541957"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="d161f-105">Office 365에 여러 사용자를 동시에 추가 - 관리자 도움말</span><span class="sxs-lookup"><span data-stu-id="d161f-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="d161f-p102">팀에 각 사용자에 로그인 하 고 전자 메일 및 Office와 같은 Office 365 서비스에 액세스할 수 있도록 사용자 계정이 필요 합니다. 많은 사용자가 한번에 모든 Excel 스프레드시트 또는 CSV 형식으로 저장 하는 다른 파일에서 계정을 추가할 수 있습니다. [어떤 CSV 형식이 모르십니까?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="d161f-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a><span data-ttu-id="d161f-109">Office 365 관리 센터에서 Office 365에 여러 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="d161f-109">Add multiple users to Office 365 in the Office 365 admin center</span></span>

1. <span data-ttu-id="d161f-110">회사 또는 학교 계정을 사용하여 Office 365에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="d161f-111">Office 365 관리 센터에서 **사용자** 선택 \> **활성 사용자**입니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-111">In the Office 365 admin center, choose **Users** \> **Active users**.</span></span>
    
    ![관리 센터에서 사용자 및 다음 활성 사용자를 선택](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="d161f-113">**더 많은** 드롭다운 목록에서 **여러 사용자 가져오기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="d161f-114">**여러 사용자 가져오기** 패널에서 필요에 따라 또는 예제 데이터를 입력 하지 않고 샘플 CSV 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![더 많은 드롭다운 목록에서 선택 여러 사용자 가져오기](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="d161f-116">스프레드시트를 하나 샘플으로 **정확 하 게 동일한 열 머리글** 을 포함 해야 합니다. (사용자 이름, 성 등...). 서식 파일을 사용 하 고 메모장과 같은 텍스트 편집 도구에서 연 만으로는, 행 1에 있는 모든 데이터를 두고 아래의 하 고 행 2의에서 데이터를 입력만 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="d161f-117">또한 스프레드시트 (예: bob@contoso.com) 사용자 이름 및 각 사용자에 대 한 프로그램 표시 이름 (예: Bob Kelly)에 대 한 값을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="d161f-118">상자에 파일 경로 입력 하거나 **찾아보기** CSV 파일 위치로 이동 하 고 **확인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![CSV 파일 확인](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="d161f-p103">파일에 문제가 있는 경우이 문제는 패널에 표시 됩니다. 또한 로그 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="d161f-122">**사용자 옵션을 설정** 대화 상자에서 로그인 상태를 설정할 수 있으며 모든 사용자에 게 할당 되는 제품 라이선스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="d161f-123">**현재 사용자의 결과 보기** 대화 상자에서 결과를 보낼 사용자가 직접 또는 다른 사용자 (암호를 일반 텍스트로) 중 하나를 선택할 수 있습니다를 얼마나 많은 사용자가 작성 된 것을 볼 수 있습니다 경우 일부 새 사용자에 게 할당 하려면 추가 라이선스를 구입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="d161f-124">동영상 보기</span><span class="sxs-lookup"><span data-stu-id="d161f-124">Watch the video</span></span>
<span data-ttu-id="d161f-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="d161f-125"></span></span>

 <span data-ttu-id="d161f-126">짧은 비디오를 시청 대량으로 하는 방법을 보여줍니다 사용자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="d161f-127">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d161f-127">Next steps</span></span>
<span data-ttu-id="d161f-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="d161f-128"></span></span>

- <span data-ttu-id="d161f-p104">이제는 이러한 사용자 계정, [다운로드 및 설치](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)하거나 Office 365 또는 PC 또는 Mac에 Office 2016를 다시 설치 해야 합니다. 팀에 각 사람에 게는 최대 5 개의 Pc 또는 Mac에 Office 365를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p104">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="d161f-p105">각 사용자 수 최대 5 개의 태블릿과 Iphone, Ipad, Android 전화와 태블릿 등 5 개의 전화도 [Office 응용 프로그램 및 모바일 장치에서 전자 메일 설정](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) 합니다. 이러한 방식으로 어디에서 든 지 Office 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p105">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets. This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="d161f-133">설치 단계는 끝-목록에 대 한 [비즈니스를 위한 Office 365 설정](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d161f-133">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="d161f-134">Office 365에 사용자를 추가 하는 방법에 대 한 자세한 내용</span><span class="sxs-lookup"><span data-stu-id="d161f-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="d161f-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="d161f-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="d161f-136">모르십니까 어떤 CSV 형식 인지 확인</span><span class="sxs-lookup"><span data-stu-id="d161f-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="d161f-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="d161f-137"></span></span>

<span data-ttu-id="d161f-p106">CSV 파일은 쉼표로 구분 된 값을 가진 파일입니다. 만들 하거나 모든 텍스트 편집기 또는 Excel과 같은 스프레드시트 프로그램을 사용 하 여 다음과 같은 프로그램 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="d161f-p107">시작 지점으로 [이 샘플 스프레드시트](https://www.microsoft.com/en-us/download/details.aspx?id=45485) 를 다운로드할 수 있습니다. Office 365 첫째 행에서 열 머리글 하므로 하지 바꿉니다 다른 한다는 기억 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="d161f-142">새 이름으로 파일을 저장 하 고 CSV 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Excel에서 파일을 CSV 형식으로 저장 하는 방법의 이미지](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="d161f-p108">파일을 저장 하는 경우에 CSV 형식에 파일을 저장 하는 경우 통합 문서에 일부 기능이 손실 될 프롬프트를 얻을 수 있을 것입니다. 이 수 있습니다. **예** 를 계속을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Excel 정말 CSV 형식으로 파일을 저장 하려고 하는 경우 요청에서 가져올 수 있습니다 프롬프트의 그림](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="d161f-148">스프레드시트 서식 지정을 위한 팁</span><span class="sxs-lookup"><span data-stu-id="d161f-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="d161f-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="d161f-149"></span></span>

- <span data-ttu-id="d161f-p109">**샘플 스프레드시트와 같이 동일한 열 머리글 필요 합니까?** 예입니다. 샘플 스프레드시트 첫째 행에서 열 머리글을 포함합니다. 이러한 머리글이 필요 합니다. Office 365에 추가 하려는 각 사용자에 대 한 제목 아래에서 행을 만듭니다. 추가, 변경 또는 열 머리글을 삭제 하는 경우 Office 365 사용자를 만들고 이러한 파일의 정보에서 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="d161f-p110">**경우에 어떻게 없는 경우 각 사용자에 대해 필요한 모든 정보가?** 사용자 이름 및 표시 이름을 필수인 하 고이 정보 없이 새 사용자를 추가할 수는 없습니다. 다른 정보는 팩스 등의 일부를 설치 하지 않은 경우 필드 빈 유지할지를 나타내기 위해 공백과 쉼표를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="d161f-p111">* * 어떻게 소규모 또는 대규모 스프레드시트 수 있습니까? * * 스프레드시트에는 적어도 두 행 있어야 합니다. 하나는 열 머리글 (사용자 데이터 열 레이블) 용이고 다른 하나는 사용자에 대 한 것입니다. 251 개 이상의 행을 가질 수 없습니다. 250 명이 넘는 사용자 가져오기 해야하는 경우에 둘 이상의 스프레드시트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p111">** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="d161f-p112">* * 어떤 언어를 사용할 수 있습니까? * * 스프레드시트를 만들 때 언어 또는 문자에 사용자 데이터 열 레이블을 입력할 수 있지만 예제에 표시 된 것 처럼 레이블, 순서를 변경 하지 해야 합니다. 언어 또는 문자를 사용 하 여 해당 필드에 항목을 확인 하 고는 유니코드 또는 utf-8 형식으로 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p112">** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="d161f-p113">**경우에 어떻게 합니까 다른 국가 또는 지역에서 사용자를 추가 합니까?** 각 영역에 대 한 별도 스프레드시트를 만듭니다. 대량 각 단계를 수행 하는데 필요한 사용자 추가 마법사는 각 스프레드시트와 현재 작업 중인 파일에 포함 된 모든 사용자의 단일 위치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="d161f-p114">**사용할 수 있는 I 문자 수에 제한이 있습니까?** 다음 표에서 샘플 스프레드시트에 각각에 대 한 사용자 데이터 열 레이블 및 최대 문자 길이 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="d161f-172">**사용자 데이터 열 레이블**</span><span class="sxs-lookup"><span data-stu-id="d161f-172">**User data column label**</span></span>|<span data-ttu-id="d161f-173">**최대 문자 길이**</span><span class="sxs-lookup"><span data-stu-id="d161f-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d161f-174">사용자 이름 (필수)</span><span class="sxs-lookup"><span data-stu-id="d161f-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="d161f-p115">79 포함 하는 at 기호 (@), 형식 name@domain에 있습니다. \<확장\>합니다. 사용자의 별칭 30 자를 초과할 수 없습니다 하 고 도메인 이름을 48 문자를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="d161f-177">이름</span><span class="sxs-lookup"><span data-stu-id="d161f-177">First Name</span></span>  <br/> |<span data-ttu-id="d161f-178">64</span><span class="sxs-lookup"><span data-stu-id="d161f-178">64</span></span>  <br/> |
|<span data-ttu-id="d161f-179">성</span><span class="sxs-lookup"><span data-stu-id="d161f-179">Last Name</span></span>  <br/> |<span data-ttu-id="d161f-180">64</span><span class="sxs-lookup"><span data-stu-id="d161f-180">64</span></span>  <br/> |
|<span data-ttu-id="d161f-181">표시 이름 (필수)</span><span class="sxs-lookup"><span data-stu-id="d161f-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="d161f-182">256</span><span class="sxs-lookup"><span data-stu-id="d161f-182">256</span></span>  <br/> |
|<span data-ttu-id="d161f-183">직함</span><span class="sxs-lookup"><span data-stu-id="d161f-183">Job Title</span></span>  <br/> |<span data-ttu-id="d161f-184">64</span><span class="sxs-lookup"><span data-stu-id="d161f-184">64</span></span>  <br/> |
|<span data-ttu-id="d161f-185">부서</span><span class="sxs-lookup"><span data-stu-id="d161f-185">Department</span></span>  <br/> |<span data-ttu-id="d161f-186">64</span><span class="sxs-lookup"><span data-stu-id="d161f-186">64</span></span>  <br/> |
|<span data-ttu-id="d161f-187">사무실 번호</span><span class="sxs-lookup"><span data-stu-id="d161f-187">Office Number</span></span>  <br/> |<span data-ttu-id="d161f-188">128</span><span class="sxs-lookup"><span data-stu-id="d161f-188">128</span></span>  <br/> |
|<span data-ttu-id="d161f-189">사무실 전화</span><span class="sxs-lookup"><span data-stu-id="d161f-189">Office Phone</span></span>  <br/> |<span data-ttu-id="d161f-190">64</span><span class="sxs-lookup"><span data-stu-id="d161f-190">64</span></span>  <br/> |
|<span data-ttu-id="d161f-191">휴대폰 번호</span><span class="sxs-lookup"><span data-stu-id="d161f-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="d161f-192">64</span><span class="sxs-lookup"><span data-stu-id="d161f-192">64</span></span>  <br/> |
|<span data-ttu-id="d161f-193">Fax</span><span class="sxs-lookup"><span data-stu-id="d161f-193">Fax</span></span>  <br/> |<span data-ttu-id="d161f-194">64</span><span class="sxs-lookup"><span data-stu-id="d161f-194">64</span></span>  <br/> |
|<span data-ttu-id="d161f-195">주소</span><span class="sxs-lookup"><span data-stu-id="d161f-195">Address</span></span>  <br/> |<span data-ttu-id="d161f-196">1023</span><span class="sxs-lookup"><span data-stu-id="d161f-196">1023</span></span>  <br/> |
|<span data-ttu-id="d161f-197">구/군/시</span><span class="sxs-lookup"><span data-stu-id="d161f-197">City</span></span>  <br/> |<span data-ttu-id="d161f-198">128</span><span class="sxs-lookup"><span data-stu-id="d161f-198">128</span></span>  <br/> |
|<span data-ttu-id="d161f-199">시/도</span><span class="sxs-lookup"><span data-stu-id="d161f-199">State or Province</span></span>  <br/> |<span data-ttu-id="d161f-200">128</span><span class="sxs-lookup"><span data-stu-id="d161f-200">128</span></span>  <br/> |
|<span data-ttu-id="d161f-201">우편번호</span><span class="sxs-lookup"><span data-stu-id="d161f-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="d161f-202">40</span><span class="sxs-lookup"><span data-stu-id="d161f-202">40</span></span>  <br/> |
|<span data-ttu-id="d161f-203">국가 또는 지역</span><span class="sxs-lookup"><span data-stu-id="d161f-203">Country or Region</span></span>  <br/> |<span data-ttu-id="d161f-204">128</span><span class="sxs-lookup"><span data-stu-id="d161f-204">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="d161f-205">Office 365로 사용자를 추가 하는 경우 여전히 문제가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="d161f-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="d161f-p116">**스프레드시트 형식이 다시 확인 합니다.** 샘플 파일의 머리글을 일치 하는지 확인 하려면 열 머리글을 확인 합니다. 확인 문자 길이 대 한 규칙을 수행 하 고 각 필드는 쉼표로 구분 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="d161f-p117">* * 찾을 수 없으면 Office 365에서 새 사용자가 즉시, 몇 분정도 기다립니다. * * 해당 하는 동안 변경에 대 한 Office 365에서 모든 서비스 간에 이동 약간 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p117">** If you don't see the new users in Office 365 right away, wait a few minutes. ** It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a><span data-ttu-id="d161f-211">이전 Office 365 관리 센터에서 Office 365에 여러 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="d161f-211">Add multiple users to Office 365 in the old Office 365 admin center</span></span>

1. <span data-ttu-id="d161f-212">[이 샘플 스프레드시트](https://www.microsoft.com/en-us/download/details.aspx?id=45485) 를 다운로드 하 여 Excel에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="d161f-213">스프레드시트를 하나 샘플으로 **정확 하 게 동일한 열 머리글** 을 포함 해야 합니다. (사용자 이름, 성 등...). 서식 파일을 사용 하는 경우 만으로는, 행 1에 있는 모든 데이터를 두고 하 고 아래 하 고 행 2의에서 데이터를 입력만 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="d161f-p118">또한 스프레드시트 (예: bob@contoso.com) 사용자 이름 및 각 사용자에 대 한 프로그램 표시 이름 (예: Bob Kelly)에 대 한 값을 포함 해야 합니다. 다른 필드를 비워 공간을 더한에 쉼표를 필드에 입력 다음 그림과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![지정 된 빈 행에 있는 샘플 CVS 파일](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="d161f-p119">다른 국가에서 근무 하는 사용자가 각 국가에 사용자를 위한 하나의 스프레드시트를 만들기 위해 필요 합니다. 예, 한 스프레드시트는 미국에서 작동 하는 모든 사람 및 다른 나열 하는 일본에서 작동 하는 모든 사용자를 나열 하는 합니다. 즉, Office 365 서비스의 가용성 지역에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="d161f-p120">**팁:** Office 365에 많은 사용자를 추가 하기 전에 샘플 스프레드시트와 연습 하는 것이 좋습니다. 예, 소수의 사용자에 대 한 데이터를 사용 하 여 샘플 스프레드시트를 편집 5 또는 10, 라고 표시 하 고 새 이름으로 파일을 저장 합니다. 이 절차에 설명 된 단계를 통해 실행, 결과 확인 하 고 새 계정을 삭제 한 다시 처음부터 다시 시작 합니다. 이러한 방식으로 데이터 오른쪽의 모든 상황에 맞는 사용을 연습 수 있습니다. 또한 [스프레드시트 서식 지정을 위한 팁](add-several-users-at-the-same-time.md#__toc314595848)을 체크아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="d161f-225">회사 또는 학교 계정을 사용하여 Office 365에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="d161f-226">Office 365 관리 센터로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-226">Go to the Office 365 admin center.</span></span>
    
4. <span data-ttu-id="d161f-p121">Office 365 서비스를 사용 하 여 사용자에 게 라이선스를 할당 해야 합니다. 계속 하기 전에 스프레드시트에 나열 된 모든 사용자에 대 한 충분 한 라이센스가 있는지 확인 하는 것이 좋습니다. **대금 청구** 선택 \> **구독** 을 충분히 있는지 확인 합니다. 추가 라이선스를 구입 해야 하는 경우 선택 * * 라이선스 수량을 변경 * *. 또는 마법사를 실행 하 고가 한 다음 나중에 더 많은 라이선스를 구입 하 고 마법사를 다시 실행 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="d161f-p122">대량으로 이동 하십시오 사용자 마법사를 추가 하는 이제: **사용자** 선택 \> **활성 사용자**입니다. 선택 ![Office 365에 많은 사용자를 추가 하는 것에 대 한 아이콘](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) 다음 그림과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Office 365 관리 센터의 사용자 섹션의 이미지](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="d161f-235">대량은 마법사가 나타나고 Office 365로 사용자 그룹에 추가 (영문)을 단계별로 안내 하는 사용자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="d161f-236">1-단계에서 CSV 파일을 선택, 다음 그림과 같이 사용자 고유의 스프레드시트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![대량의 1 단계-사용자 마법사 선택 CSV 파일을 추가](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="d161f-238">확인,-2 단계에서 마법사를 알려 여부는 스프레드시트의 콘텐츠를 올바른 형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![대부분의 2 단계 확인-사용자 마법사를 추가 합니다.](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="d161f-p123">설정,-3 단계에서 스프레드시트에 나열 된 사용자가 Office 365를 사용할 수 있도록 **허용 됨** 을 선택 합니다. 또한 이러한 사용자가 Office 365를 사용 하는 국가 선택 합니다. 조직의 일부 사용자는 자신의 이름으로 별도 스프레드시트를 만들고, 다른 국가에서 Office 365를 사용 하려고 하 고 실행을 대량 사용자 마법사를 다시 추가할를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![대부분의 3 단계: 사용자가 마법사-설정 추가](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="d161f-244">사용 가능한 라이선스 수 라이선스 할당 페이지에서 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![대량 사용자 추가 마법사-라이선스의 4 단계](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="d161f-p124">**추가 라이선스를 구입**을 선택할 수는 있지만 대량 상태로 두면 됩니다 사용자 마법사를 추가 하 고 Office 365 관리 센터에서 **대금 청구** 를로 이동 합니다. 추가 라이선스를 구입 후 처리 순서에 대 한 잠시 대기 해야 하 고 시작을 대량 처음부터 사용자 마법사를 추가 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p124">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Office 365 admin center. After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="d161f-248">추가 라이선스를 구입 하지, 하는 경우 스프레드시트에 나열 된 모든 사용자에 대 한 계정은 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="d161f-249">이 예제에서는 라이선스를 추가로 구입 및 대량을 계속 하지는 사용자가 마법사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="d161f-250">-5 단계에서 결과 보내기, 스프레드시트에 있는 사람에 대 한 *모든* Office 365 사용자 이름 및 임시 암호를 나열 하는 전자 메일을 받게 하려는 사람의 전자 메일 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![대부분의 5 단계 사용자 추가 마법사-결과 보내기](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="d161f-p125">5 단계-보내기 결과에 지정 된 모든 전자 메일 주소에는 다음 전자 메일 전송 됩니다. 이 전자 메일 계정을 만든를 나타냅니다. 다음과 같은 충분 한 라이선스를 받지 때문에 일부 사용자에 대 한 계정을 만들 받지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![사용자 자격 증명 정보로 샘플 전자 메일](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="d161f-p126">사용자가 마법사에서 같은 스프레드시트와 기타 나중에 라이선스 및 대량 추가 다시 구입할 수 있습니다. 마법사 계정;에 이미 있는 사용자를 건너뜁니다. 결과 보고서에서 "중복 된 사용자 이름" 말할가 해당 계정을 해당 정보를 이미 있는 사용자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="d161f-258">대량의 마지막 페이지 다음 그림과 같이 사용자 이름과 임시 암호를 나열 하는 사용자가 마법사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![대부분의 6 단계 사용자 추가 마법사-결과 보내기](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="d161f-p127">Office 365로 사용자를 추가한 후에 게 자신의 Office 365 계정 정보에 대 한 알려주어야 해야 합니다. 새 암호를 전달 하기 위한 일반 프로세스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d161f-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

