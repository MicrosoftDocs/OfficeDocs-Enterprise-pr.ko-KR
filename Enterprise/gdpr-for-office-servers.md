---
title: Office Server GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Office 온-프레미스 Server에서 GDPR 요구 사항을 해결하는 방법을 알아보세요.
ms.openlocfilehash: bfacb297c77041cf905d2eef6645da3b7459962c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915483"
---
# <a name="gdpr-for-office-on-premises-servers"></a>Office 온-프레미스 Server GDPR

GDPR(일반 데이터 보호 규정)은 조직에 요구 사항을 소개하여 개인 데이터를 보호하고 데이터 주체 요청에 적절하게 응답합니다. 이 일련의 문서는 온-프레미스 작업에 권장되는 접근 방식을 제공합니다.

-   [SharePoint Server](gdpr-for-sharepoint-server.md)

-   [Exchange Server](gdpr-for-exchange-server.md)

-   [비즈니스용 Skype 서버](gdpr-for-skype-for-business-server.md)

-   [Project Server](gdpr-for-project-server.md)

-   [Office Web Apps Server 및 Office Online Server](gdpr-for-office-online-server.md)

-   [온-프레미스 파일 공유](gdpr-for-on-premises-file-shares.md)

GDPR 및 Microsoft가 지원하는 방법에 대한 자세한 내용은 [Microsoft 보안 센터](https://www.microsoft.com/ko-KR/TrustCenter/Privacy/gdpr/default.aspx)를 참조하세요.

온-프레미스 데이터로 작업을 수행하기 전에 먼저 법률 및 규정 준수 팀에 문의하여 안내를 받고 개인 데이터를 사용하여 작업하는 접근 방식 및 기존 분류 스키마에 대해 알아보세요. 수 및 기존 분류에 대한 자세한 내용은  스키마 및 개인 데이터 작업을 위한 접근 방식을합니다. Microsoft는 [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>)에서 Microsoft GDPR 데이터 검색 도구 키트의 분류 스키마를 개발하고 확장하는 권장 사항을 제공합니다. 또한, 이 도구 키트는 원하는 경우 더 정교한 데이터 거버넌스 기능을 사용할 수 있는 클라우드로 온-프레미스 데이터를 이동하는 접근 방식을 설명합니다. 이 섹션에 나와 있는 문서는 온-프레미스로 유지하기 위한 데이터 권장 사항을 제공합니다.

다음 그림은 이러한 각 작업에 사용하여 개인 데이터를 검색, 분류, 보호, 모니터링할 수 있는 권장 기능을 나열합니다. 자세한 내용은 이 섹션의 문서를 참조하세요.

![](media/gdpr-for-office-servers-image1.png)

## <a name="illustration-description"></a>그림 설명

다음 표에서는 이해를 돕기 위해 그림과 동일한 예제를 제공합니다.

|             |Windows Server 파일 공유|SharePoint Server|Exchange Server|비즈니스용 Skype|Project Server|
|:------------|:-------------------------|:----------------|:--------------|:-----------------|:-------------|
|검색|Azure Information Protection 스캐너*|검색 센터 또는 eDiscovery(데이터 분류 후), Azure Information Protection 스캐너*|Exchange eDiscovery 포털|Exchange eDiscovery 포털|검색 및 내보내기용 SQL 스크립트|
|분류|Azure Information Protection 스캐너*, Office 365 중요한 정보 유형|Azure Information Protection 스캐너*, Office 365 중요한 정보 유형|Exchange 보존 태그 및 보존 정책|Exchange 보존 태그 및 보존 정책||
|보호||Exchange Server 데이터 손실 방지 규칙, 권한, 라이브러리의 IRM 보호|Exchange Server 데이터 손실 방지 규칙, Exchange Server와 IRM 통합|||
|모니터링|SIEM 도구와 로그 통합|SIEM 도구와 로그 통합|SIEM 도구와 로그 통합|SIEM 도구와 로그 통합|SIEM 도구와 로그 통합|

*보호는 파일을 암호화합니다. 따라서 SharePoint Server가 보호된 파일에서 중요한 정보 유형을 찾을 수 없습니다.
