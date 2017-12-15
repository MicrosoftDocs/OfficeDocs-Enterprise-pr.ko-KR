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
- DecEntMigration
- Ent_Office_Other
- PowerShell
ms.assetid: 510d5528-ac00-4f54-9d38-75fa043d0a06
description: "요약: Office 365의 배포에 대 한 자세한 보고 정보를 검색 하려면 Microsoft Excel에서 oData 기능을 사용"
ms.openlocfilehash: 72c0fce0a70f5cc3136ab01b48bb178d32a8f64d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a>Excel을 사용하여 Office 365 보고 데이터 검색

 **요약:** Microsoft Excel에서 oData 기능을 사용 하 여 Office 365의 배포에 대 한 자세한 보고 정보를 검색할 수
  
보고 시스템 관리의 핵심 부분입니다. Office 365 관리 센터에서 **보고서** 구역의 왼쪽된 탐색에서 액세스할 수 있는 미리 정의 된 보고서의 번호를 포함 합니다. 사용 현황 보고서 및 보안 및 규정 준수 보고서 있습니다.
  
사용할 수 있는 보고서를 사용 하 고 있는 Office 365 서비스 사용 하도록 설정한 Office 365의 버전에 따라 달라 집니다. 자세한 내용은 [보고서 페이지](https://technet.microsoft.com/en-us/library/office-365-reports.aspx)를 참조 하십시오.
  
미리 정의 된 관리 센터 보고서는 하는 훌륭한 리소스입니다. 늦 쉽게 사서함 사용량 또는 시간 (분)을 사용자가 온라인 회의에 투입 된가 수 등에서 확인할 수 있습니다. 그러나와 관련해 서 Office 365 도메인의 상세한 분석 보고서에 그에 따른 제한 않아도 됩니다.
  
이러한 제한 사항을 해결 하는 한 가지 방법은 Windows PowerShell 또는 다른 개발 언어에서 Office 365 보고 서비스에 액세스 하 고, 사용자 지정 보고서 만들기를 사용 하는 사용자 지정 보고서를 사용 하면 데이터 (및 데이터의 양을)를 지정 하는 기능 Office 365에서 반환 되는 서비스를 보고 합니다. 사용자 지정 보고서 데이터를 정렬 및 그룹화 해야 하는 방법 및 해당 하는 경우에 지정할 수 있습니다를 작성 하 여 어떻게 해당 데이터 저장 해야 합니다. 예, XML 형식에서 또는 Excel에서 쉽게 가져올 수 있는 쉼표로 구분 된 값 형식으로 데이터를 저장할 수 있습니다. 
  
또한 사용자 지정 스크립트/응용 프로그램을 사용 하는 Office 365 관리 센터에서 사용할 수 없는 보고서에 액세스할 수 있습니다. 예, 관리 센터에 있는 오래 된 사서함 수를 알 수 있습니다 하지만 지난 30 일 후에는 사서함을 액세스 하지 않은 알 수 없습니다. 사용자 지정 PowerShell 스크립트를 확인할 수 있는. 전체적으로 볼 때, 상당한을 유연성 짧고 상대적으로 간단한 Windows PowerShell 스크립트를 작성 하는 것 대신 나타냅니다.
  
> [! VISUAL BASIC 참고] 서비스를 보고 Office 365에 대 한 자세한 내용은 [홈페이지](https://msdn.microsoft.com/en-us/library/office/jj984325%28v=office.15%29.aspx) 를 참조 합니다.
  
이 데이터를 검색 하기 위해 일종의 코드를 작성을 수행 해야 합니다. 이것이 가치가 양과 반환 되는 정보의 종류를 제한 하는 대규모 조직 하는 경우입니다. 하지만 소규모 조직 참가 하 고 있는 경우 반환 되는 정보의 종류와 양을 제한 하지 않아도 됩니다. Excel 자체 내에서 Office 365 보고서 열기 고려할 수 있습니다.
  
하지만 몇 가지 제한 사항이 있다는 사실만 인식하면 됩니다. 먼저 데이터가 반환되기 전에는 데이터를 필터링, 정렬, 선택하거나 달리 조작할 수 없습니다. 대신 보고서에서 반환되는 기본 데이터 집합만 볼 수 있습니다. 일부 경우에는 데이터가 충분하지 않을 수 있습니다. 예를 들어 보고서가 전체 연도가 아닌 이전 달의 데이터만 반환할 수 있습니다. 이와는 대조적으로 데이터가 너무 많을 수도 있습니다. 이전 달의 데이터만 원함에도 전체 연도의 데이터가 반환될 수 있습니다.
  
Excel 내에서 직접 Office 365 보고서를를 열려면 다음 절차를 완료 합니다.
  
1. Excel에서 새 워크시트를 열어서를 시작 합니다. 해당 워크시트에서 **데이터**를 클릭 하 고 **에서 기타 원본**을 클릭 다음 **OData 데이터 피드에서**클릭 합니다. **데이터 연결 마법사** 대화 상자를 가져옵니다.
    
     ![데이터 연결 마법사의 데이터 피드에 연결 대화 상자 예제입니다.](images/o365_reporting_connect_data_feed.png)
  
2. **피드 데이터에 연결** 페이지에서 데이터 피드 위치 대로 **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** 를 입력 합니다. 참고;와 같이 기본 URL을 입력만 사용할 수 있습니다. 모든 선택에 추가할 수 없습니다 Filter 또는 문 서식을 지정 합니다. 외의 기본 URL을 입력 하면 여러분은 얻지 다시 모든 데이터입니다. 대신 다음과 같은 오류 메시지가 표시 하면 됩니다.
    
     ![Select, Filter 또는 Format 문을 추가할 때 표시되는 오류 메시지 예제입니다.](images/o365_reporting_incorrect_data_feed.png)
  
3. 보고 서비스 URL을 입력 한 후 **이 이름 및 암호를 사용 하 여** **로그온 자격 증명에서**를 선택 합니다. **사용자 이름** 상자에 Office 365 로그온 이름 (예: admin@litwareinc.onmicrosoft.com)을 입력 합니다. **암호** 상자에 Office 365 로그온 암호를 입력 하 고 ****을 클릭 합니다. Excel 제공 된 자격 증명을 사용 하 여 보고 서비스에 연결을 시도 합니다.
    
4. 인증을 받은 후에 **테이블 선택** 페이지를 표시 됩니다. 보고서 보기 (예: **MailTrafficTop** )를 되 고 **다음**을 클릭 한 다음이 선택 합니다.
    
     ![데이터 연결 마법사의 테이블 선택 페이지 예제입니다.](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > 여러 보고서;를 선택 하는 것이 불가능 여러 테이블/차트 Excel 스프레드시트에 추가 되는 만들어집니다. 도 차트를 만드는 단일 테이블/데이터 여러 보고서를 포함 하는 것이 불가능 합니다. 그러나 다루지 않습니다 하는 소개이 문서에서. 
  
5. **다음** 을 클릭 한 후 **데이터 연결 파일 저장 및 마침** 페이지와 함께 표시 됩니다.
    
     ![데이터 연결 마법사의 데이터 연결 파일 저장 및 마침 페이지 예제입니다.](images/o365_reporting_odata_finish.png)
  
    여기에 모든 정보를 입력할 필요가 없습니다. 데이터 검색을 수행 해야 하는 작업만 **완료**를 클릭 합니다. 그러나는 기본적으로 Excel 저장 하는; 할 각 데이터 연결에 대 한 정보를 주목할 만한 것은 이 데이터는 **내 데이터 원본** 폴더에 저장 됩니다.
    
     ![내 데이터 원본 폴더에 대한 파일 저장 대화 상자 예제입니다.](images/o365_reporting_save_data_source.png)
  
    따라서 **친숙 한 이름** 및 **검색 키워드**; 등과 같은 레이블이 있는 텍스트 상자를 포함 하는 대화 상자 이러한 옵션 이러한 데이터 연결을 사용자 지정할 수 있는 기회를 제공 합니다. 그렇게 하면 끝나지 않는 다음과 같은 표시 된 데이터 원본의 전체 묶음 일:
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

**암호 파일에 저장**확인란을 선택 하는 경우 이러한 데이터 피드를 다시 사용할 수 있습니다. 예를들어 **클라이언트 브라우저 보고서**로 데이터 연결을 저장 합니다. 다음에 Office 365 도메인에 액세스 하는 데 사용 되는 웹 브라우저에 대 한 정보를 원하는 데이터 연결 마법사를 통해 진행 필요가 없습니다. 대신 하기만 하면 Excel을 열, **데이터**클릭 한 다음 **기존 원본**를 클릭 합니다. **기존 연결** 대화 상자에서 원하는 데이터 연결을 선택 하 고 **확인**을 클릭 합니다.
    
![기존 연결 대화 상자에서 원하는 데이터 연결을 선택하는 예제입니다.](images/o365_reporting_select_connection.png)
  
이때는 Excel에서 자동으로 해당 연결을 설정하고 데이터를 검색합니다.
    
이때 이러한 합니다. ODC 파일은 일반 텍스트 XML 파일입니다. Office 365 사용자 이름과 암호는 이러한 일반 텍스트 XML 파일에 포함 합니다.
    
\<odc:ConnectionString > 데이터 원본 = https://reports.office365.com/ecp/reportingwebservice/reporting.svc/; 네임 스페이스를 포함 하도록 = *. 최대 메시지 크기를 받은 4398046511104; = 통합 보안 = 기본; **사용자 ID=admin@litwareinc.onmicrosoft.com; 암호 MYpassw0rd =!**; 보안 정보 유지 = false; 서비스 문서 Url https://reports.office365.com/ecp/reportingwebservice/reporting.svc/ =\</odc:ConnectionString >
    
사용자 이름 및 암호를 일반 텍스트 파일에 저장 된 것을 원치 않으면 다음 하지 라는 상자는 선택 **암호 파일에 저장**합니다. 그러나 이렇게 하면 염두에 있는지에 이러한 데이터 연결을 다시 사용할 수 없습니다. 사용자 이름과 암호의 없이 Office 365 됩니다 서비스에 대 한 로그온 시도 인증할 수 때문입니다.
    
6. **데이터 가져오기** 대화 상자 표시 됩니다 **데이터 연결 파일 저장 및 마침** 페이지에서 **완료** 를 클릭 합니다.
    
     ![데이터 가져오기 대화 상자 예제입니다.](images/o365_reporting_import_data.png)
  
7. 보기 옵션 (예: **피벗 테이블 보고서** )를 선택한 다음 **확인**을 클릭 합니다. 데이터를 가져올 수는 모든 작업을 완료 하는 경우에서 제공 하 고 선택 하려면 이러한 상황이 발생 하면 어떤 보기 옵션:
    
     ![Excel 워크시트로 성공적으로 가져온 데이터 예제입니다.](images/o365_reporting_sample_spreadsheet.png)
  
해당 데이터를 사용 하 여 할는 전적으로 사용자 다음 됩니다. 일부 제안 합니다. [oData 데이터 피드를 사용 하 여 Excel Services 대시보드 만들기](https://technet.microsoft.com/en-us/library/jj873965%28v=office.15%29.aspx)를 살펴보겠습니다. 이 문서는 Office 365 서비스를 보고를 사용 하지 않지만 새 대시보드 필터 및 슬라이서에 추가 하는 등의 작업을 수행 하는 것에 대 한 간편 하 게 되는 힌트 제공 합니다.
  
## <a name="see-also"></a>See also

#### 

[Office 365 PowerShell로 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
  
[Windows PowerShell을 사용 하 여 Office 365에서 보고서를 만들려면](use-windows-powershell-to-create-reports-in-office-365.md)

