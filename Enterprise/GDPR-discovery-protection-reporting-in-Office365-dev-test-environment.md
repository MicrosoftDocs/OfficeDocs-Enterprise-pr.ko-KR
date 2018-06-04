---
title: GDPR 검색, 보호 및 Office 365 개발/테스트 환경에서 보고
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: Office 365의 GDPR 기능을 설명합니다.
ms.openlocfilehash: d5be0967142725d3735eed0d97be581c8e40fee8
ms.sourcegitcommit: 76643a1b3363624c1a0cc4b0f282e9f354652d77
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2018
ms.locfileid: "19454849"
---
# <a name="gdpr-discovery-protection-and-reporting-in-the-office-365-devtest-environment"></a>GDPR 검색, 보호 및 Office 365 개발/테스트 환경에서 보고

 **요약:** Office 365의 GDPR 기능을 설명합니다. 
  
이문서에서는 Office 365 개발/테스트 환경에서 일반 데이터 보호 규정(GDPR)에 대한 개인 식별이 가능한 정보(PII) 검색, 보호 및 보호를 구성하고 설명하는 방법에 대해 설명합니다.
  
## <a name="phase-1-create-and-configure-your-trial-office-365-subscription"></a>1단계: 평가판 Office 365 구독 만들기 및 구성

먼저 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md#phase-2-create-an-office-365-trial-subscription) 문서의 2단계를 따릅니다.

다음으로, eDiscovery 관리자를 구성하려면 다음 단계를 사용합니다.

1. 전역 관리자 계정을 사용하여 Office 365 평가판 테넌트에 로그인하세요.
2. Office 365 홈 페이지에서 **Security & Compliance**를 클릭합니다.
3. 새 Security & Compliance 탭에서 **권한** > **eDiscovery 매니저**를 클릭합니다.
4. eDiscovery 매니저의 **편집**을 클릭한 다음 **eDiscovery 매니저 선택**을 클릭합니다.
5. **+ 추가**를 클릭하고 전역 관리자 계정 이름을 검색하고 전역 관리자 계정을 eDiscovery 매니저로 추가합니다.
6. **완료** > **저장** > **닫기**를 클릭합니다.
  
## <a name="phase-2-add-personally-identifiable-information-to-your-tenant"></a>2단계: 개인 식별이 가능한 정보를 테넌트에 추가

이 단계에서는 예제 IBAN(국제 은행 계좌 번호) 집합에 대해 PII가 있는 문서를 만들고 Office 365 개발/테스트 환경에서 SharePoint Online 사이트에 저장합니다.

1. 로컬 컴퓨터에서 Microsoft Word를 엽니다.
2. 다음 테이블을 Word 파일에 붙여넣고 로컬 컴퓨터에 ‘IBANs.docx’로 저장합니다.
    
    숫자  |국가  |코드 |IBAN  |
    |---------|---------|---------|---------|
    |1     |  오스트리아 SEPA      | AT            |AT611904300234573201       |
    |2     |  불가리아 SEPA       |BG    |BG80BNBG96611020345678      |
    |3     |  덴마크 SEPA      |   DK      |DK5000400440116243      |
    |4     |  핀란드 SEPA      |   FI      |FI2112345600000785         |
    |5     |  프랑스 SEPA       |   FR      |FR1420041010050500013M02606         |
    |6     |  독일 SEPA      |   DE      |DE89370400440532013000         |
    |7     |  그리스 SEPA       |   GR      |GR1601101250000000012300695         |
    |8     |  이탈리아 SEPA       |    IT     |GR1601101250000000012300695         |
    |9     |  네덜란드 SEPA      |   NL      |    NL91ABNA0417164300     |
    |10     | 폴란드 SEPA       |  PL       | PL27114020040000300201355387        |

3. 브라우저의 새 탭에 **https://**\<YourTenantName\>**.sharepoint.com**을 입력합니다.
4. **문서**를 클릭하여 사이트에 대한 문서 라이브러리를 엽니다. 새 목록 환경 둘러보기를 요청하는 경우 완료될 때까지 **다음**을 클릭합니다.
5.  **파일** > **업로드**를 클릭하고 2단계에서 만든 IBANs.docx를 선택합니다.

  
## <a name="phase-3-demonstrate-data-discovery"></a>3단계: 데이터 검색 설명

이 단계에서는 IBAN이 포함된 콘텐츠를 기반으로 2단계에서 만들어지고 저장된 문서를 찾을 수 있는 검색 기능을 설명합니다.

1. Security & Compliance 탭에서 **홈**을 클릭한 다음 **검색 및 확인** > **콘텐츠 검색**을 클릭합니다.
2. **+** 를 클릭하여 새 검색 항목을 만듭니다.
3. 새 창에서 다음 정보를 제공합니다.  
    a. 이름: IBAN 검색  
    b. 검색 대상: **검색할 특정 사이트를 선택**(**+** 클릭)하고 사이트의 URL을 입력합니다. **https://**\<YourTenantName\>**.sharepoint.com/**  
    c. **추가**를 클릭한 다음 **확인**을 클릭합니다. 경고가 표시되면 **확인**을 클릭합니다.  
    d. **새로 검색** 창에서 **다음**을 클릭합니다.  
    e. **검색 대상**: **SensitiveType:"IBAN(국제 은행 계좌 번호)"** 와 **검색**을 차례로 클릭합니다.

4. **IBAN 검색** 결과에 나열된 항목이 하나 이상 표시되는지 확인합니다.


## <a name="phase-4-create-a-custom-sensitive-information-type-via-powershell"></a>4단계: PowerShell을 통해 사용자 지정 중요한 정보 유형 만들기

이 단계에서는 Microsoft PowerShell Contoso를 사용하여 가상 Contoso Corporation에 대해 사용자 지정 중요한 정보 형식을 만듭니다. Contoso는 Contoso 사용자 지정 숫자(CCN)를 사용하여 고객 데이터베이스에서 각 고객을 식별합니다. CCN은 다음 구조로 구성됩니다.
- 레코드가 만들어진 연도를 나타내는 두 자리 숫자입니다.
    - Contoso는 2002년에 설립되었습니다. 따라서 가능한 가장 빠른 값은 02입니다. 
- 레코드를 만든 파트너 에이전시를 나타내는 세 자리 숫자.
    - 가능한 에이전시 값 범위는 000에서 999입니다. 
- 비즈니스 분야를 나타내는 알파벳 문자입니다.
    - 가능한 값은 a-z이고 대/소문자를 구분하지 않습니다.
- 4자리 일련 번호입니다. 
    - 가능한 일련 번호 값의 범위는 0000에서 9999까지입니다.   

Contoso는 내부 서신, 외부 서신, 문서 및 기타 양식에서 항상 CCN을 사용하여 고객을 참조합니다. Office 365 콘텐츠에서는 사용자 지정 중요한 항목 유형을 만들어 CCN의 사용을 감지할 수 있으므로 이러한 형식의 개인 식별 가능한 정보를 사용할 때 보호 기능을 적용할 수 있습니다.

1. [다단계 인증을 사용한 Office 365 보안 및 준수 센터 PowerShell 연결](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)의 지침을 사용하여 전역 관리자 계정의 UPN을 사용하여 보안 및 준수 센터에 연결합니다.
2. 다음 PowerShell 명령을 실행합니다.

     ```
    #Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName#Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName
    ```
3. 다음 PowerShell 명령을 실행하고 만들어진 GUID를 컴퓨터의 열린 메모장 인스턴스에 나열된 순서대로 복사합니다.
    ```
    #Generate three unique GUIDs
    Write-Host "GUID1 = "([guid]::NewGuid().Guid)
    Write-Host "GUID2 = "([guid]::NewGuid().Guid)
    Write-Host "GUID3 = "([guid]::NewGuid().Guid)
    ```
4. 로컬 컴퓨터에서 메모장의 다른 인스턴스를 열고 다음 콘텐츠를 붙여넣습니다.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"> 
    <RulePack id="GUID1">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="GUID2" />
    <Details defaultLangCode="en"> 
    <LocalizedDetails langcode="en"> 
    <PublisherName>Contoso Ltd.</PublisherName> 
    <Name>Contoso Rule Package</Name> 
    <Description>Defines Contoso's custom set of classification rules</Description>
    </LocalizedDetails>
    </Details>
    </RulePack>
    <Rules>
    <!-- Contoso Customer Number (CCN) -->
    <Entity id="GUID3" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
    <IdMatch idRef="Regex_contoso_ccn" />
    <Match idRef="Keyword_contoso_ccn" />
    <Match idRef="Regex_eu_date" />
    </Pattern>
    </Entity>
    <Regex id="Regex_contoso_ccn">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</Regex>
    <Keyword id="Keyword_contoso_ccn">
    <Group matchStyle="word">
    <Term caseSensitive="false">customer number</Term>
    <Term caseSensitive="false">customer no</Term>
    <Term caseSensitive="false">customer #</Term>
    <Term caseSensitive="false">customer#</Term>
    <Term caseSensitive="false">Contoso customer</Term>
    </Group>
    </Keyword>
    <Regex id="Regex_eu_date"> (0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)? |feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|apr(ile|il)?|abr(il)?|avril |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)? |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}</Regex>
    <LocalizedStrings>
    <Resource idRef="GUID3">
    <Name default="true" langcode="en-us">Contoso Customer Number (CCN)</Name>
    <Description default="true" langcode="en-us">Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</Description>
    </Resource>
    </LocalizedStrings>
    </Rules>
    </RulePackage>
    ```
5. 4단계의 XML 텍스트에 있는 GUID1, GUID2, GUID3 값을 3단계의 값으로 바꾼 다음 ContosoCCN.xml이라는 이름으로 로컬 컴퓨터의 내용을 저장합니다.
6. ContosoCCN.xml 파일에 경로를 채우고 다음 명령을 실행합니다.
    ```
    #Create new Sensitive Information Type
    $path="<path to the ContosoCCN.xml file, such as C:\Scripts\ContosoCCN.xml>"
    New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path $path -Encoding Byte -ReadCount 0)
    ```
7. Security & Compliance 탭에서 **분류** > **중요한 정보 유형**을 클릭합니다. 목록에서 Contoso 사용자 지정 숫자(CCN)를 표시해야 합니다.

## <a name="phase-5-demonstrate-data-protection"></a>5단계: 데이터 보호 설명

Office 365의 개인 정보 보호에는 데이터 손실 방지(DLP) 기능을 사용하는 방식이 포함됩니다. Office 365 보안 및 준수 센터의 DLP 정책을 사용하여 Office 365 전체에서 중요한 정보를 자동으로 보호할 수 있습니다.

보호를 적용할 수 있는 여러 가지 방법이 있습니다. EU 상주 데이터가 사용자 환경에 저장되고 직원이 처리하도록 허용된 방법에 대한 인식을 개선하고 교육하는 것은 Office 365 DLP를 사용하는 한 수준의 정보 보호를 나타냅니다.

이 단계에서는 새 DLP 정책을 만들고 2단계에서 SharePoint Online에 저장된 IBANs.docx 파일에 적용되는 방법과 IBAN을 포함하는 전자 메일을 보내려고 시도하는 경우에 대해 설명합니다.

1. 브라우저의 Security & Compliance 탭에서 **홈**을 클릭합니다.
2. **데이터 손실 방지** > **정책**을 클릭합니다
3. **+ 정책 만들기**를 클릭합니다.
4. **템플릿으로 시작하거나 사용자 지정 정책 만들기**에서 **사용자 지정** > **사용자 지정** > **다음**을 클릭합니다.
5. **정책 이름 지정**에서 다음 세부 정보를 제공하고 **다음**을 클릭합니다. a. 이름: **EU 시민 PII 정책** b. 설명: **유럽 시민의 개인 식별이 가능한 정보 보호**
6. **위치 선택**에서 **Office 365의 모든 위치**를 선택합니다. 여기에는 Exchange 전자 메일, OneDrive, SharePoint 문서의 콘텐츠가 포함됩니다. 그리고 **다음**을 클릭합니다.
7. **보호하려는 콘텐츠의 유형 사용자 지정**에서 **다음이 포함된 콘텐츠 찾기:** 를 클릭한 다음 **편집**을 클릭합니다.
8. **보호할 콘텐츠 유형 선택**에서 **추가** > **중요한 정보 유형**을 클릭합니다.
9. **중요한 정보 유형**에서 **+ 추가**를 클릭합니다.
10. **중요한 정보 유형**에서 **IBAN**을 검색하고 **IBAN(국제 은행 계좌 번호)** 의 확인란을 선택한 다음 **추가**를 클릭합니다.
11. **IBAN(국제 은행 계좌 번호)** 중요한 정보 유형이 추가되었는지 확인한 다음 **완료**를 클릭합니다.
12. **콘텐츠 포함**에서 중요한 정보 유형이 추가되었는지 확인한 다음 **저장**을 클릭합니다.
13. **보호할 콘텐츠 유형 사용자 지정**에서 **포함된 콘텐츠 찾기**에 **IBAN(국제 은행 계좌 번호)** 을 포함하고 **다음**을 클릭합니다.
14. **다음이 공유되는 콘텐츠에 포함된 경우 검색**에서 값을 **10**에서 **1**로 변경하고 **다음**을 클릭합니다.
15. **정책을 켜거나 먼저 테스트를 수행하시겠습니까?** 에서 다음 설정을 선택하고 **다음**을 클릭합니다.  
    a. **먼저 테스트 수행**에 대한 옵션 선택  
    b. **테스트 모드인 경우 정책 팁 표시**에 대한 확인란 선택 
16. **설정 검토**에서 설정을 검토한 후 **만들기**를 클릭합니다. 참고: 새 DLP 정책을 만든 후 적용되려면 시간이 걸립니다.
17. 로컬 컴퓨터에서 브라우저의 개인 인스턴스를 엽니다.
18. 주소 표시줄에 **https://**\<YourTenantName\>**.sharepoint.com**을 입력하고 전역 관리자 계정을 사용하여 로그인합니다.
19. **문서**를 클릭합니다.
20. ‘IBANs.docx’라는 파일을 클릭합니다. ‘IBANs.docx의 정책 팁’이 표시되어야 합니다. IBANs.docx 파일은 외부 수신자와 공유되어 DLP 정책이 위반됩니다. 
21. 주소 표시줄에 **https://outlook.office365.com**을 입력합니다.
22. **새** - **전자 메일 메시지**를 클릭하고 다음을 입력합니다.  
    - **받는 사람:** \<개인 전자 메일 주소\>  
    - **제목:** GDPR 테스트  
    - **본문:** 아래 표시된 값의 테이블에 복사합니다.
  
        |숫자  |국가  |코드 |IBAN  |
        |---------|---------|---------|---------|
        |1     |  오스트리아 SEPA      | AT            |AT611904300234573201       |
        |2     |  불가리아 SEPA       |BG    |BG80BNBG96611020345678      |
        |3     |  덴마크 SEPA      |   DK      |DK5000400440116243      |
        |4     |  핀란드 SEPA      |   FI      |FI2112345600000785         |
        |5     |  프랑스 SEPA       |   FR      |FR1420041010050500013M02606         |
        |6     |  독일 SEPA      |   DE      |DE89370400440532013000         |
        |7     |  그리스 SEPA       |   GR      |GR1601101250000000012300695         |
        |8     |  이탈리아 SEPA       |    IT     |GR1601101250000000012300695         |
        |9     |  네덜란드 SEPA      |   NL      |   NL91ABNA0417164300      |
        |10     | 폴란드 SEPA       |  PL       | PL27114020040000300201355387        |
23. DLP 정책은 전자 메일의 본문에 IBAN이 포함되어 있음을 인식하고 메시지 창 상단에 정책 팁을 제공합니다.
24. 브라우저의 개인 인스턴스를 닫습니다.


## <a name="phase-6-demonstrate-reporting"></a>6단계: 보고 설명
 
이 단계에서는 5단계에서 구성된 DLP 정책에 따라 Office 365 보고에 대해 설명합니다.

   1. 브라우저의 Security & Compliance 탭에서 **홈**을 클릭합니다.
   2. **보고서** > **대시보드** > **DLP 정책 일치**를 클릭합니다.
   3. DLP 정책은 조직의 중요한 정보를 식별하고 보호하는 데 도움이 됩니다. 예를 들어, 보고서에서 SharePoint Online에 저장된 IBAN을 포함하는 문서를 정책에서 식별했음을 알 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[GDPR에 대한 Office 365 정보 보호](office-365-information-protection-for-gdpr.md)

[Microsoft 365에 대한 GDPR](https://docs.microsoft.com/microsoft-365/compliance/gdpr?toc=/microsoft-365/enterprise/toc.json)
