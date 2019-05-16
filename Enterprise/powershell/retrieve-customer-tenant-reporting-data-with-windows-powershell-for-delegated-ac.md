---
title: DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 요약:Microsoft Exchange Online용 원격Windows PowerShell을 사용하여 개별 고객 테넌트에서 보고서를 검색합니다.
ms.openlocfilehash: c1c5ca880d73cf226a5ae7dae79df89351b537f1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071194"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색

 **요약:** Microsoft Exchange Online용 원격Windows PowerShell을 사용하여 개별 고객 테넌트에서 보고서를 검색합니다.
  
Syndication 및 CSP(클라우드 솔루션 공급자) 파트너는 Exchange Online PowerShell용 원격Windows PowerShell을 통해 직접 고객 테넌트 보고를 구성하는 데이터에 액세스할 수 있습니다. 이를 통해 파트너는 보고 데이터를 수집하고 저장한 후 여기에서 다른 작업을 수행할 수 있습니다. 원격 연결을 연 후 고객 테넌트에 대한 보고 데이터 검색은 고객 테넌트에 대해 cmdlet을 실행하는 것과 동일합니다.
  
이 문서에서는 Exchange Online용 원격Windows PowerShell을 사용하여 단일 고객 테넌트에 연결하고 보고서를 검색합니다. 기본적으로 Windows PowerShell은 여러 고객 테넌트에서 보고 데이터 집계를 지원하지 않습니다. 이 절차를 사용하여 검색하는 보고서는 연결되는  _DelegatedOrg_에만 해당합니다.
  
 
## <a name="before-you-begin"></a>시작하기 전에

- 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결해야 합니다. 자세한 내용은 [DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)을 참조하세요.
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Get-StaleMailboxReport 샘플 실행

원격 세션을 Exchange Online으로 연 후 이 명령을 실행하여 날짜 범위 2015/03/25에서 2015/03/31까지에 대해 **Get-StaleMailboxReport** 를 검색합니다.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

사용할 수 있는 메시지 추적에 대해 Exchange Online, Lync Online, SharePoint Online 등에 다양한 보고 cmdlet을 사용할 수 있습니다. 사용 가능한 보고 cmdlet 및 Office 365 보고 웹 서비스에 대한 자세한 내용은 다음 섹션의 항목을 참조하세요.
  
## <a name="see-also"></a>참고 항목

#### 

[Office 365 보고 웹 서비스](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online의 보고 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[파트너를 위한 도움말](https://go.microsoft.com/fwlink/p/?LinkID=533477)

