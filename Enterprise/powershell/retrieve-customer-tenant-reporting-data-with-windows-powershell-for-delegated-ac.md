---
title: DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: '요약: Microsoft Exchange Online용 원격Windows PowerShell을 사용하여 개별 고객 테넌트에서 보고서를 검색합니다.'
ms.openlocfilehash: 4e18eb2e2ed5f801106535b31577d3186e87c58c
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230284"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

Microsoft Exchange Online 용 원격 Windows PowerShell을 사용 하 여 개별 고객 테 넌 트에서 보고서를 검색 합니다.
  
배포 및 CSP (클라우드 솔루션 공급자) 파트너는 원격 Windows PowerShell을 사용 하 여 Exchange Online PowerShell을 통해 직접 고객 테 넌 트 보고서를 구성 하는 데이터에 액세스할 수 있습니다. 이를 통해 파트너는 보고 데이터를 수집하고 저장한 후 여기에서 다른 작업을 수행할 수 있습니다. 원격 연결을 연 후 고객 테넌트에 대한 보고 데이터 검색은 고객 테넌트에 대해 cmdlet을 실행하는 것과 동일합니다.
  
이 문서에서는 Exchange Online 용 원격 Windows PowerShell을 사용 하 여 단일 고객의 테 넌 트에 연결 하 고 보고서를 검색 합니다. 기본적으로 Windows PowerShell에서는 여러 고객 테 넌 트의 보고 데이터 집계를 지원 하지 않습니다. 이 절차를 사용 하 여 검색 하는 보고서는 연결 하는 _DelegatedOrg_ 에만 적용 됩니다.
  
 
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

