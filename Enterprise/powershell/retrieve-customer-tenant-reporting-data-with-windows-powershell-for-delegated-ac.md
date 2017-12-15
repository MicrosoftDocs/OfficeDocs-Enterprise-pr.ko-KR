---
title: "DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: "요약: 개별 고객 테 넌 트에서 보고서를 검색 하려면 remoteWindows Microsoft Exchange online PowerShell을 사용 합니다."
ms.openlocfilehash: 40c1dedd8fb223ea6fa478b3a5c3e716fe07dd93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색

 **요약:** RemoteWindows Microsoft Exchange online PowerShell을 사용 하 여 개별 고객 테 넌 트에서 보고서를 검색 합니다.
  
신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너 Exchange Online PowerShell에 대 한 remoteWindows PowerShell 통해 직접 고객 테 넌 트 보고서를 구성 하는 데이터에 액세스할 수 있습니다. 이렇게 하면 파트너를 수집 및 보고 데이터를 저장 하 고 다음에 다른 작업을 수행할 수 있습니다. 원격 연결을 연 후에 고객 테 넌 트에 대 한 보고 데이터를 검색 하는 프로그램 고객 테 넌 트에 대해 모든 cmdlet을 실행 하 동일 합니다.
  
이 문서에서는 단일 고객 테 넌에 연결 하 고 보고서를 검색할 remoteWindows Exchange Online에 대 한 PowerShell을 사용 합니다. 기본적으로 Windows PowerShell 지원 하지 않습니다 여러 고객 테에서 보고 데이터를 집계 합니다. 이 절차를 검색 하는 보고서에 연결 하는 _DelegatedOrg_ 에 대해서만 됩니다.
  
대화 모든 고객 테에 대 한 단일 보고서를 검색 하려는 경우이 작업을 수행 하는 샘플 스크립트는 [위임 된 액세스 권한 (DAP) 파트너에 대 한 Windows PowerShell을 통해 집계 고객 보고 데이터](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) 에 확인할 수 있습니다.
  
## <a name="before-you-begin"></a>시작하기 전에

- 원격 Windows PowerShell을 사용 하 여 Exchange Online 테 넌 트에 연결 해야 합니다. 자세한 내용은 [연결에 대 한 액세스 권한을 위임 (DAP) 파트너에 대 한 원격 Windows PowerShell을 사용한 Exchange Online 테 넌 트를](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md) 참조 하십시오.
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Get-StaleMailboxReport 샘플 실행

날짜 범위에 대 한 **Get StaleMailboxReport** 를 검색 하려면이 명령을 실행 하는 Exchange Online에 대 한 원격 세션을 연 후 03/25/2015 03/31/2015 통해 합니다.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

사용할 수 있는 메시지 추적에 대 한 Exchange Online, Lync Online 및 SharePoint Online으로 다른 사용자에 대해 사용할 수 있는 다른 많은 보고 cmdlet이 있습니다. 사용 가능한 보고 cmdlet 및 Office 365 보고 웹 서비스에 대 한 자세한 내용을 보려면 다음 섹션의 항목은를 참조 하십시오.
  
## <a name="see-also"></a>See also

#### 

[Office 365 보고 웹 서비스](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online의 보고 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[파트너에 대 한 도움말](https://go.microsoft.com/fwlink/p/?LinkID=533477)

