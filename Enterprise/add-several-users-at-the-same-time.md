---
title: Microsoft 365에 여러 사용자를 동시에 추가-관리자 도움말
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
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
description: '스프레드시트나 기타 CSV 파일의 목록에서 비즈니스용 Microsoft 365에 여러 사용자를 추가 하는 방법에 대해 알아봅니다. Microsoft 365에 계정을 추가 하는 방법을 설명 하는 YouTube의 비디오를 시청 하세요. 이 프로세스가 끝나면 계정이 있는 각 사용자에 게 Microsoft 365 사서함이 포함 됩니다. '
ms.openlocfilehash: 5f328185b56d1c5436f763d811d85dd55f912919
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711811"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a>Microsoft 365에 여러 사용자를 동시에 추가-관리자 도움말

팀의 각 사용자는 전자 메일 및 Office와 같은 Microsoft 365 서비스에 로그인 하 고 액세스할 수 있으려면 먼저 사용자 계정을 사용 해야 합니다. 사용자가 많은 경우 Excel 스프레드시트 또는 CSV 형식으로 저장 된 다른 파일에서 모든 계정을 한 번에 추가할 수 있습니다. [CSV 형식이 무엇 인지 알 수 없습니까?](add-several-users-at-the-same-time.md#__toc316652088)
  
> [!NOTE] 
> 새로운 Microsoft 365 관리 센터를 사용하지 않는 경우 홈페이지 상단에 있는 **새 관리 센터 시도** 토글을 선택하여 켤 수 있습니다.

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a>Microsoft 365 관리 센터에서 여러 사용자 추가

1. 회사 또는 학교 계정으로 Microsoft 365에 로그인합니다. 
    
2. 관리 센터에서 **사용자** \> **활성 사용자**를 선택합니다.

3. **여러 사용자 추가**를 선택 합니다.

4. 
            **여러 사용자 가져오기** 패널에서 예제 데이터가 입력되어 있는 예제 CSV 파일과 입력되어 있지 않은 예제 CSV 파일 중 선택하여 다운로드할 수 있습니다. 
    
    스프레드시트는 **정확히 동일한 열 머리글** 을 예제(사용자 이름, 성 등...)로 포함해야 합니다. 서식 파일을 사용하는 경우에는 메모장과 같은 텍스트 편집 도구에서 열어서 행 1에 있는 모든 데이터는 그대로 두고 행 2와 그 아래 행에만 데이터를 입력해 보세요. 
    
    스프레드시트는 사용자 이름(예: hyunki@contoso.com)과 각 사용자에 대한 표시 이름(예: 유현기)에 대한 값도 포함해야 합니다. 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. 상자에 파일 경로를 입력하거나 **찾아보기**를 선택하여 CSV 파일의 위치를 찾은 다음 **확인**을 선택합니다.
  
    파일에 문제가 있는 경우에는 문제가 창에 표시됩니다. 로그 파일을 다운로드할 수도 있습니다.
    
5. 
            **Set user options**(사용자 옵션 설정) 대화 상자에서는 로그인 상태를 설정하고 모든 사용자에게 할당할 제품 라이선스를 선택할 수 있습니다. 
    
6. 
            **View your result**(결과 보기) 대화 상자에서는 결과를 자신이나 다른 사용자(암호는 일반 텍스트가 됨)에 보내도록 선택할 수 있으며, 만들어진 사용자의 수와 새 사용자에게 할당하기 위해 추가 라이선스를 구입해야 하는지를 알 수도 있습니다. 

## <a name="next-steps"></a>다음 단계
<a name="bk_preview"> </a>

- 이러한 사용자는 이제 [PC 또는 Mac에서 Microsoft 365 또는 Office 2016을 다운로드 하 고 설치 하거나 다시](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)설치 해야 합니다. 팀의 각 사용자는 최대 5 대의 Pc 또는 Mac에 Microsoft 365을 설치할 수 있습니다. 
    
- 각 사용자는 iPhones, iPads 및 Android 휴대폰 및 태블릿과 같은 최대 5대의 태블릿과 5대의 휴대폰에서 [모바일 장치의 Office 앱 및 전자 메일을 설정](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)할 수도 있습니다. 이 방법으로 어디서나 Office 파일을 편집할 수 있습니다. 
    
    설치 단계에 대 한 종단 간 목록을 보려면 [Microsoft 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) 를 참조 하세요. 
    
## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a>Microsoft 365에 사용자를 추가 하는 방법에 대 한 자세한 정보
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>CSV 형식이란?
<a name="__toc316652088"> </a>

CSV 파일은 쉼표로 구분된 값을 사용한 파일입니다. 모든 텍스트 편집기나 Excel과 같은 스프레드시트 프로그램에서 이와 같은 파일을 만들거나 편집할 수 있습니다.
  
시작점으로 [이 예제 스프레드시트](https://www.microsoft.com/download/details.aspx?id=45485)를 다운로드할 수 있습니다. Microsoft 365에서는 첫 번째 행에 열 머리글이 필요 하므로 다른 항목으로 바꿀 수 없습니다. 
  
파일을 새 이름으로 저장하고 CSV 형식을 지정합니다.
  
![Excel CSV 형식으로 파일을 저장하는 방법 이미지](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
파일을 저장할 때 파일을 CSV 형식으로 저장하면 통합 문서의 일부 기능이 손실된다는 메시지가 표시될 수 있지만 괜찮습니다. **예**를 클릭하여 계속합니다. 
  
![Excel에서 파일을 정말로 CSV 형식으로 저장할지 묻는 메시지 그림](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>스프레드시트 서식 지정 팁
<a name="__toc314595848"> </a>

- **예제 스프레드시트와 같은 열 머리글이 필요한가요?** 예. 예제 스프레드시트에는 첫 행에 열 머리글이 포함되어 있습니다. 해당 머리글은 필수 항목입니다. Microsoft 365에 추가 하려는 각 사용자에 대해 머리글 아래에 행을 만듭니다. 열 머리글을 추가, 변경 또는 삭제 하면 Microsoft 365에서 해당 파일의 정보를 사용자에 게 만들지 못할 수도 있습니다. 
    
- **각 사용자에 대해 필요한 정보가 일부만 있는 경우** 사용자 이름 및 표시 이름은 필수 항목입니다. 이 정보 없이는 새 사용자를 추가할 수 없습니다. 팩스 등 기타 정보가 없는 경우 공백과 쉼표를 사용해 필드를 빈 상태로 둘 수 있습니다. 
    
- **스프레드시트의 크기는 얼마나 작거나 클 수 있나요?** 스프레드시트에는 행이 두 개 이상 있어야 합니다. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet. 
    
- **사용할 수 있는 언어** 스프레드시트를 만들 때 모든 언어나 문자에 사용자 데이터 열 레이블을 입력할 수 있지만 예제에 표시 된 대로 레이블 순서를 변경 해서는 안 됩니다. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format. 
    
- **다른 국가나 지역의 사용자를 추가하는 경우** 각 지역에 대해 별도의 스프레드시트를 만듭니다. 각 스프레드시트의 사용자 일괄 추가 마법사를 단계적으로 따르면 작업 중인 파일에 포함된 모든 사용자를 한 곳에서 볼 수 있습니다. 
    
- **사용할 수 있는 문자 수 제한** 다음 표에서는 예제 스프레드시트의 사용자 데이터 열 레이블 및 최대 문자 길이를 각각 보여 줍니다. 
    
|**사용자 데이터 열 레이블**|**최대 문자 길이**|
|:-----|:-----|
|사용자 이름 (필수)  <br/> |@ 기호를 포함 하는 79는 name@domain 형식으로 되어 \<extension\> 있습니다. 사용자의 별칭은 50 자를 초과할 수 없으며 도메인 이름은 48 자를 초과할 수 없습니다.  <br/> |
|이름  <br/> |64  <br/> |
|성  <br/> |64  <br/> |
|표시 이름 (필수)  <br/> |256  <br/> |
|직함  <br/> |64  <br/> |
|부서  <br/> |64  <br/> |
|사무실 번호  <br/> |128  <br/> |
|사무실 전화  <br/> |64  <br/> |
|휴대폰  <br/> |64  <br/> |
|팩스  <br/> |64  <br/> |
|주소  <br/> |1023  <br/> |
|구/군/시  <br/> |128  <br/> |
|시/도  <br/> |128  <br/> |
|우편 번호  <br/> |40  <br/> |
|국가 또는 지역  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a>Microsoft 365에 사용자를 추가할 때 여전히 문제가 발생 하나요?

- **스프레드시트 형식이 올바른지 다시 한 번 확인합니다.** 열 머리글이 예제 파일의 머리글과 일치하는지 확인합니다. 문자 길이 규칙을 준수했고 각 필드를 쉼표로 구분했는지 확인합니다. 
    
- **Microsoft 365의 새 사용자가 바로 표시 되지 않으면 몇 분 정도 기다립니다.** Microsoft 365의 모든 서비스에서 변경 내용을 적용 하는 데 약간의 시간이 걸릴 수 있습니다. 
    
## <a name="related-articles"></a>관련 문서

[사용자를 개별적으로 또는 대량으로 Microsoft 365에 추가](https://docs.microsoft.com/office365/admin/add-users/add-users)




