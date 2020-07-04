---
title: Office 365에 대한 외부 Domain Name System 레코드
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: '요약: Office 365 배포를 계획할 때 사용할 DNS 레코드 목록을 참조합니다.'
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996542"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Office 365에 대한 외부 Domain Name System 레코드

|||
|:-----|:-----|
|![도메인](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)**으로 돌아가기**.  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Office 365에 필요한 외부 DNS 레코드(핵심 서비스)
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**DNS 레코드** <br/> |**용도** <br/> |**사용할 값** <br/> |
|**CNAME** <br/> **(제품군)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **참고:** CNAME은 21Vianet에서 운영되는 Office 365에만 적용됩니다.   |**별칭:** msoid  <br/> **대상:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(도메인 확인)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**호스트:** @(또는 일부 DNS 호스팅 공급자의 경우 도메인 이름)  <br/> **TXT 값:** Office 365에서 제공되는 _텍스트 문자열 _  <br/> Office 365 **도메인 설정** 마법사는 이 레코드를 만드는 데 사용하는 값을 제공합니다.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Office 365 (Exchange Online)에서 전자 메일에 필요한 외부 DNS 레코드
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **자동 검색 레코드**를 사용하면 클라이언트 컴퓨터는 Exchange를 자동으로 찾고 클라이언트를 적절히 구성할 수 있습니다.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
몇 개의 전자 메일 주소만 Office 365로 전환하시나요? [사용자 지정 도메인으로 된 전자 메일 주소로 Office 365 시험 사용](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7)할 수 있습니다.

- **SPF용 TXT 레코드**는 받는 사람의 전자 메일 시스템에서 전자 메일을 보내는 서버가 승인된 서버인지를 확인하는 데 사용됩니다. 이렇게 하면 전자 메일 스푸핑 및 피싱과 같은 문제를 방지할 수 있습니다. 레코드에 포함할 내용을 이해하는 데 도움이 되는 이 문서의 [SPF에 필요한 외부 DNS 레코드](external-domain-name-system-records.md#BKMK_SPFrecords)를 참조하세요.

Exchange 페더레이션을 사용하는 전자 메일 고객의 경우 표 아래쪽에 추가 CNAME 및 TXT 레코드도 필요합니다.
  
||||
|:-----|:-----|:-----|
|**DNS 레코드** <br/> |**용도** <br/> |**사용할 값** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**별칭:** autodiscover  <br/> **대상:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Office 365에서 도메인에 대한 받는 메일을 Exchange Online 서비스로 보냅니다.  <br/> [!NOTE] 전자 메일이 Exchange Online으로 이동되면 이전 시스템을 가리키는 MX 레코드를 제거해야 합니다.   |**도메인:** (예)contoso.com  <br/> **대상 전자 메일 서버:** \<MX token\> . mail.protection.outlook.com  <br/> **기본 설정/우선 순위:** 다른 MX 레코드보다 더 낮음(예: 1 또는 '낮음')(이를 통해 메일이 Exchange Online으로 전달됨)  <br/>  다음 단계에 따라를 찾습니다 \<MX token\> .  <br/>  Office 365에 로그인하고 Office 365 관리자 \> 도메인으로 이동합니다.  <br/>  도메인에 대한 작업 열에서 문제 해결을 선택합니다.  <br/>  MX 레코드 섹션에서 해결 방법을 선택합니다.  <br/>  이 페이지의 지시에 따라 MX 레코드를 업데이트합니다.  <br/> [MX 우선 순위란?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[SPF에 필요한 외부 DNS 레코드](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange 페더레이션)** <br/> |하이브리드 배포용 Exchange 페더레이션에 사용됩니다.  <br/> |**TXT 레코드 1:** 예를 들면 contoso.com 및 사용자 지정 생성된 관련 도메인 증명 해시 텍스트(예: Y96nu89138789315669824)와 같습니다.  <br/> **TXT 레코드 2:** 예를 들면 exchangedelegation.contoso.com 및 연관된 사용자 지정 생성 도메인 증명 해시(예: Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange 페더레이션)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**별칭:**(예) Autodiscover.service.contoso.com  <br/> **대상:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>비즈니스용 Skype Online에 필요한 외부 DNS 레코드
<a name="BKMK_ReqdCore"> </a>

[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)를 사용하여 네트워크가 올바르게 구성되었는지 확인할 경우 수행해야 할 특정 단계가 있습니다.

> [!NOTE]
> 이러한 DNS 레코드는 특히 특정 페더레이션 문제가 발생할 수 있는 하이브리드 Teams와 비즈니스용 Skype Online 시나리오에 해당하는 Teams에도 적용됩니다.
  
||||
|:-----|:-----|:-----|
|**DNS 레코드** <br/> |**용도** <br/> |**사용할 값** <br/> |
|**SRV** <br/> **(비즈니스용 Skype Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Service(서비스):** _sipfederationtls  <br/> **프로토콜:** _TCP  <br/> **우선 순위:** 100  <br/> **가중치:** 1  <br/> **포트:** 5061  <br/> **대상:** sipfed.online.lync.com  <br/> **참고:** 방화벽 또는 프록시 서버에서 외부 DNS의 SRV 조회를 차단하는 경우에는 내부 DNS 레코드에 이 레코드를 추가해야 합니다.   |
|**SRV** <br/> **(비즈니스용 Skype Online)** <br/> |비즈니스용 Skype에서 Lync 클라이언트 간의 정보 흐름을 조정하는 데 사용됩니다.  <br/> |**Service(서비스):** sip  <br/> **Protocol(프로토콜):** TLS   <br/> **우선 순위:** 100  <br/> **가중치:** 1  <br/> **포트:** 443  <br/> **대상:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(비즈니스용 Skype Online)** <br/> |Lync 클라이언트에서 비즈니스용 Skype Online 서비스 찾기 및 로그인을 지원하는 데 사용됩니다.  <br/> |**별칭:** sip  <br/> **대상:** sipdir.online.lync.com  <br/> 자세한 내용은 [Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)를 참조하세요.  <br/> |
|**CNAME** <br/> **(비즈니스용 Skype Online)** <br/> |Lync 모바일 클라이언트에서 비즈니스용 Skype Online 서비스 찾기 및 로그인을 지원하는 데 사용됩니다.  <br/> |**별칭:** lyncdiscover  <br/> **대상:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Office 365 Single Sign-On에 필요한 외부 DNS 레코드
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**DNS 레코드** <br/> |**용도** <br/> |**사용할 값** <br/> |
|**호스트 (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**대상:** (예)sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>SPF에 필요한 외부 DNS 레코드
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>SPF 레코드 구조

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

도메인으로부터 전자 메일을 수신하는 전자 메일 시스템에서 SFP 레코드를 조회한 다음 메시지를 보낸 전자 메일 서버가 Office 365 서버일 경우 메시지를 수락합니다. 예를 들어, 메시지를 보낸 서버가 기존 메일 시스템이거나 인터넷의 악성 시스템인 경우 SPF 검사가 실패하고 메시지가 배달되지 않을 수 있습니다. 스푸핑을 방지하고 피싱 메시지를 방지하려면 이 도움말을 확인하세요.
  
### <a name="choose-the-spf-record-structure-you-need"></a>필요한 SPF 레코드 구조 선택

Office 365용 Exchange Online 전자 메일을 사용하지 않는 시나리오의 경우(예: SharePoint Online에서 만든 전자 메일을 사용하는 경우 등)에는 다음 표를 사용하여 레코드 값에 포함할 내용을 결정합니다.
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||다음를 사용하는 경우...  <br/> |용도  <br/> |추가할 포함 내용  <br/> |
|1   <br/> |모든 전자 메일 시스템(필수)  <br/> |이 값으로 시작하는 모든 SPF 레코드  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online(일반적)  <br/> |Exchange Online만 사용  <br/> |포함:spf.protection.outlook.com  <br/> |
|3   <br/> |제3자 전자 메일 시스템(덜 일반적임)  <br/> ||포함되는 사항은 다음과 같습니다.\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |온-프레미스 메일 시스템(덜 일반적임)  <br/> |Exchange Online Protection 또는 Exchange Online 및 다른 메일 시스템을 사용하는 경우 사용  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> 포함되는 사항은 다음과 같습니다.\<mail.contoso.com\>  <br/> 괄호 안의 값(\<\>)은 도메인의 전자 메일을 전송하는 다른 메일 시스템이어야 합니다.  <br/> |
|5   <br/> |모든 전자 메일 시스템(필수)  <br/> ||-모두  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>예: 기존 SPF 레코드에 추가
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

이제 Office 365에 대 한 SPF 레코드를 업데이트 하 고 있습니다. 필요한 값이 포함 된 SPF 레코드가 있도록 현재 레코드를 편집 합니다. Office 365, "spf.protection.outlook.com"
  
정확함:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

정확하지 않음:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>일반적인 SPF 값에 대한 더 많은 예
<a name="bkmk_addtospf"> </a>

전체 Office 365 제품군을 사용 하는 경우 MailChimp을 사용 하 여 마케팅 전자 메일을 대신 전송 하는 경우 contoso.com의 SPF 레코드는 위의 표에 나오는 1, 3, 5 행을 사용 하는 다음과 같이 표시 될 수 있습니다. 행 1과 5가 필요 하다는 것을 염두에 두어야 합니다.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

또는 Office 365와 온-프레미스 메일 시스템 모두에서 전자 메일을 보내도록 Exchange 하이브리드 구성을 사용하는 경우 contoso.com의 SPF 레코드는 다음과 같을 수 있습니다.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/o365edns](https://aka.ms/o365edns)
