---
title: "Excel을 사용하여 Office 365 보고 데이터 검색"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 510d5528-ac00-4f54-9d38-75fa043d0a06
description: "요약: Microsoft Excel의 oData 기능을 사용하여 Office 365 배포에 대한 자세한 보고 정보를 검색합니다."
ms.openlocfilehash: 0749160e1d9bf5e8e0b6ee73aa1baa5ae826ba49
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a>Excel을 사용하여 Office 365 보고 데이터 검색

 **요약:** Microsoft Excel의 oData 기능을 사용하여 Office 365 배포에 대한 자세한 보고 정보를 검색합니다.
  
보고는 시스템 관리의 핵심 부분입니다. Office 365 관리 센터는 미리 정의된 보고서를 다수 포함하고 있으며, 왼쪽 탐색의 **보고서** 섹션에서 액세스할 수 있습니다. 여기에는 사용 현황 보고서와 보안 및 준수 보고서가 있습니다.
  
사용할 수 있는 보고서는 사용 중인 Office 365 버전 및 사용하도록 설정한 Office 365 서비스에 따라 다릅니다. 자세한 내용은 [보고서 페이지](https://technet.microsoft.com/ko-KR/library/office-365-reports.aspx)를 참조하세요.
  
미리 정의된 관리 센터 보고서는 유용한 리소스입니다. 이 보고서를 사용하면 사서함 사용량이나 사용자가 온라인 회의에 소요한 시간(분)과 같은 사항을 쉽게 확인할 수 있습니다. 그러나 이러한 보고서는 Office 365 도메인을 자세히 분석할 때 몇 가지 제한이 있습니다.
  
이러한 제한을 해결하는 한 가지 방법은 Windows PowerShell 또는 다른 개발 언어를 사용하여 Office 365 보고 서비스에 액세스하여 사용자 지정 보고서를 만드는 것입니다. 사용자 지정 보고서를 사용하면 Office 365 보고 서비스에서 반환되는 데이터 및 데이터 양을 나타낼 수 있습니다. 사용자 지정 보고서를 작성하여 데이터를 정렬 및 그룹화하는 방법을 지정할 수도 있고, 해당되는 경우 이러한 데이터가 저장되는 방식을 지정할 수도 있습니다. 예를 들어 데이터를 XML 형식 또는 Excel에서 쉽게 가져올 수 있는 쉼표로 구분된 값 형식으로 저장할 수 있습니다. 
  
또한 사용자 지정 스크립트/응용 프로그램을 사용하여 Office 365 관리 센터에서는 사용할 수 없는 보고서에 액세스할 수 있습니다. 예를 들어 관리 센터는 보유하고 있는 오래된 사서함의 수를 알려줄 수는 있지만 지난 30일 동안 액세스하지 않은 사서함이 어느 것인지 알려줄 수는 없습니다. 사용자 지정 PowerShell 스크립트로는 이러한 사실을 확인할 수 있습니다. 이러한 기능을 함께 사용하면 아주 유연하게 작업할 수 있으므로 짧으면서 비교적 간단한 Windows PowerShell 스크립트만 작성하면 됩니다.
  
> [!VISUAL BASIC NOTE] Office 365 보고 서비스에 대한 자세한 내용은 [홈 페이지](https://msdn.microsoft.com/ko-KR/library/office/jj984325%28v=office.15%29.aspx)를 참조하세요.
  
이 데이터를 검색하려면 일종의 코드를 작성해야 합니다. 반환되는 정보의 양과 유형을 제한해야 하는 더 큰 조직에 있는 경우 이러한 작업이 중요합니다. 그러나 규모가 좀 더 작은 조직이고 반환되는 정보의 양과 유형을 제한할 필요가 없는 경우라면 Excel 자체에서 Office 365 보고서를 여는 것을 고려할 수 있습니다.
  
하지만 몇 가지 제한 사항이 있다는 사실만 인식하면 됩니다. 먼저 데이터가 반환되기 전에는 데이터를 필터링, 정렬, 선택하거나 달리 조작할 수 없습니다. 대신 보고서에서 반환되는 기본 데이터 집합만 볼 수 있습니다. 일부 경우에는 데이터가 충분하지 않을 수 있습니다. 예를 들어 보고서가 전체 연도가 아닌 이전 달의 데이터만 반환할 수 있습니다. 이와는 대조적으로 데이터가 너무 많을 수도 있습니다. 이전 달의 데이터만 원함에도 전체 연도의 데이터가 반환될 수 있습니다.
  
Excel 내에서 직접 Office 365 보고서를 열려면 다음 절차를 완료합니다.
  
1. 먼저 Excel에서 새 워크시트를 엽니다. 해당 워크시트에서 **데이터** 와 **기타 원본** 을 차례로 클릭한 다음 **OData 피드** 를 클릭합니다. 이렇게 하면 **데이터 연결 마법사** 대화 상자가 표시됩니다.
    
     ![데이터 연결 마법사의 데이터 피드에 연결 대화 상자 예제입니다.](images/o365_reporting_connect_data_feed.png)
  
2. **데이터 피드에 연결** 페이지에서 **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** 를 데이터 피드 위치로 입력합니다. 표시된 것처럼 기본 URL만 입력할 수 있고 Select, Filter 또는 Format 문은 추가할 수 없습니다. 기본 URL 이외의 항목을 입력하면 어떤 데이터도 반환되지 않으며 다음과 같은 오류 메시지가 표시됩니다.
    
     ![Select, Filter 또는 Format 문을 추가할 때 표시되는 오류 메시지 예제입니다.](images/o365_reporting_incorrect_data_feed.png)
  
3. 보고 서비스 URL을 입력한 후 **로그온 자격 증명** 에서 **이 이름과 암호 사용** 을 선택합니다. **사용자 이름** 상자에 Office 365 로그온 이름(예: admin@litwareinc.onmicrosoft.com)을 입력합니다. **암호** 상자에 Office 365 로그온 암호를 입력한 후 **다음** 을 클릭합니다. Excel은 제공된 자격 증명을 사용하여 보고 서비스에 연결하려고 합니다.
    
4. 인증을 받으면 **표 선택** 페이지가 표시됩니다. 보려는 보고서(예: **MailTrafficTop** )를 선택하고 **다음** 을 클릭합니다.
    
     ![데이터 연결 마법사의 테이블 선택 페이지 예제입니다.](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > 여러 보고서를 선택할 수 있습니다. 이렇게 하면 여러 표/차트가 Excel 스프레드시트에 추가됩니다. 또한 여러 보고서의 데이터를 조합하는 표/차트를 만들 수도 있습니다. 그러나 본 소개 문서에서는 이 내용을 다루지 않습니다. 
  
5. **다음** 을 클릭하면 **데이터 연결 파일 저장 및 마침** 페이지가 표시됩니다.
    
     ![데이터 연결 마법사의 데이터 연결 파일 저장 및 마침 페이지 예제입니다.](images/o365_reporting_odata_finish.png)
  
    여기에는 정보를 입력하지 않아도 됩니다. 데이터를 검색하려면 **마침** 만 클릭하면 됩니다. 그러나 Excel에서 사용자가 만든 각 데이터 연결에 대한 정보를 저장한다는 사실은 기억해 두는 것이 좋습니다. 이 데이터는 **내 데이터 원본** 폴더에 저장됩니다.
    
     ![내 데이터 원본 폴더에 대한 파일 저장 대화 상자 예제입니다.](images/o365_reporting_save_data_source.png)
  
    이 대화 상자에는 **이름** 및 **키워드 검색** 과 같은 레이블이 붙은 텍스트 상자가 포함되어 있습니다. 이러한 옵션을 사용하여 해당 데이터 연결을 사용자 지정할 수 있습니다. 이렇게 해야 다음과 같은 전체 데이터 원본이 표시되지 않습니다.
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

**파일에 암호 저장** 확인란을 선택하면 이러한 데이터 필드를 다시 사용할 수 있습니다. 예를 들어 데이터 연결을 **클라이언트 브라우저 보고서** 로 저장하는 경우 다음 번부터는 Office 365 도메인 액세스에 사용되는 웹 브라우저에 대한 정보를 알고 싶을 때 데이터 연결 마법사를 진행할 필요가 없습니다. 대신 Excel을 열고 **데이터** 를 클릭한 다음 **기존 원본** 을 클릭하기만 하면 됩니다. **기존 연결** 대화 상자에서 원하는 데이터 연결을 선택하고 **확인** 을 클릭합니다.
    
![기존 연결 대화 상자에서 원하는 데이터 연결을 선택하는 예제입니다.](images/o365_reporting_select_connection.png)
  
이때는 Excel에서 자동으로 해당 연결을 설정하고 데이터를 검색합니다.
    
이러한 .ODC 파일은 일반 텍스트 XML 파일입니다. 이러한 일반 텍스트 XML 파일에는 Office 365 사용자 이름 및 암호가 포함되어 있습니다.
    
\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString>
    
사용자 이름과 암호를 일반 텍스트 파일에 저장하고 싶지 않은 경우 **파일에 암호 저장** 확인란을 선택하지 않도록 합니다. 확인란을 선택하는 경우 이러한 데이터 연결을 다시 사용할 수 없게 됩니다. 사용자 이름과 암호가 없으면 Office 365는 사용자의 서비스 로그온 시도를 인증할 수 없습니다.
    
6. **데이터 연결 파일 저장 및 마침** 페이지에서 **마침** 을 클릭하면 **데이터 가져오기** 대화 상자가 제공됩니다.
    
     ![데이터 가져오기 대화 상자 예제입니다.](images/o365_reporting_import_data.png)
  
7. 보기 옵션(예: **피벗 테이블 보고서** )을 선택하고 **확인** 을 클릭합니다. 모든 작업이 문제 없이 진행되면 데이터를 가져온 후 선택한 보기 옵션에 표시합니다.
    
     ![Excel 워크시트로 성공적으로 가져온 데이터 예제입니다.](images/o365_reporting_sample_spreadsheet.png)
  
해당 데이터의 용도는 전적으로 사용자에게 달려 있습니다. 제안 사항을 보려면 [oData 데이터 피드를 사용하여 Excel Services 대시보드 만들기](https://technet.microsoft.com/ko-KR/library/jj873965%28v=office.15%29.aspx)를 참조하세요. 이 문서는 Office 365 보고 서비스를 사용하지는 않지만 새 대시보드에 필터 및 슬라이서를 추가하는 작업과 같은 간단한 작업에 대한 힌트를 제공합니다.
  
## <a name="see-also"></a>참고 항목

#### 

[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
  
[Office 365에서 Windows PowerShell을 사용하여 보고서 만들기](use-windows-powershell-to-create-reports-in-office-365.md)

