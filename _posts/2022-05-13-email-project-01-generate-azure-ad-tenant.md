---
title: "[Email Project 01] Azure AD 테넌트 생성"
categories:
- Cloud
- Azure 
tags:
- Cloud
- Azure
- Active Directory
author: Jun
last_modified_at: 2022-05-13T18:00:00+09:00
---

Microsoft Azure에서 제공하는 Managed Active Directory인 **Azure Active Directory**를 사용해보겠습니다.

Azure 계정은 이미 있다는 가정 하에 실습을 진행합니다.

# Azure 접속

![Azure 접속]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/01.png)

[Azure Portal](https://portal.azure.com)에 접속한 후, `Azure Active Directory`로 접속합니다.

# 테넌트 생성

![Azure AD 접속]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/02.png)

처음 접속하면, 다음과 같이 **기본 디렉터리**가 나오게 됩니다. 상단의 `Manage tenants`를 클릭해 새로운 테넌르를 생성하겠습니다.

![Switch tenant]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/03.png)

테넌트 목록이 나오면, 상단의 `Create`를 클릭합니다.

![Create a tenant - Basics]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/04.png)

테넌트 유형을 선택합니다.

`Azure Active Directory` : 우리가 일반적으로 알고 있는 AD

`Azure Active Directory (B2C)` : 고객들에게 제공하는 비즈니스를 위한 AD

두 옵션은 AD라는 공통점이 있지만 완전히 다른 서비스입니다. 저희는 일반적인 AD가 필요하므로 첫번째 옵션인 `Azure Active Directory`를 선택하겠습니다.

옵션을 선택하셨으면 하단의 `Next: Configuration`을 클릭합니다.

![Create a tenant - Configuration]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/05.png)

AD의 세부 설정을 하는 곳입니다.

`Organization name` : AD에서 사용할 조직의 이름

`Initial domain name` : AD에서 사용할 도메인

`Country/Region` : AD가 동작할 리전

조직 이름과 도메인은 적절히 지정해주세요. 도메인은 추후에 커스텀 도메인을 사용할 예정입니다.

리전은 `한국`을 선택하시면 아시아 태평양 리전으로 자동으로 인식됩니다. 다른 나라에서 사용하실 예정이라면 그 나라를 선택하시면 됩니다.

설정을 완료하셨으면 하단의 `Next: Review +  create`를 클릭합니다.

![Create a tenant - Review + create]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/06.png)

잠깐 기다리면 상단의 **Validation passed.** 라는 문구를 볼 수 있습니다.

전에 설정한 도메인은 **Azure AD 전체에서 고유**해야 하기 때문에, 중복되면 Validation이 실패하게 됩니다.

Validation이 성공했으면 하단 좌측의 `Create`를 클릭합니다.

![Create a tenant - Help us prove you're not a robot]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/07.png)

로봇이 아니냐고 물어봅니다. 보안문자를 입력하시고 `Submit`를 클릭합니다.

![Create a tenant - Tenent creation in progress]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/08.png)

테넌트 생성이 시작됩니다. 1분정도 기다려주시면 완료됩니다.

![Create a tenant - Tenant creation was successful]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/09.png)

테넌트 생성이 완료되면 **Tenant creation was successful.** 라는 문구를 확인할 수 있습니다.

새로운 테넌트의 링크로 접속해보겠습니다.

![Complete to create a new tenant]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-01-generate-azure-ad-tenant/10.png)

새로운 테넌트 생성이 완료되었습니다. 설정했었던 Organization Name이었던 **wsskore**가 잘 나오네요.