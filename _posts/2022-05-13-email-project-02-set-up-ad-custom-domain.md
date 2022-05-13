---
title: "[Email Project 02] Azure AD Custom Domain w/ Amazon Route 53"
categories:
- Cloud
- Azure
- AWS
tags:
- Cloud
- Azure
- Active Directory
- Route 53
author: Jun
last_modified_at: 2022-05-13T20:00:00+09:00
---

Route53을 이용해 Azure AD의 Custom domain name을 적용시켜보겠습니다.

# Custom domain name 생성

![Azure Active Directory 접속]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/01.png)

**Azure Active Directory**로 접속한 후, 좌측의 `Custom domain names`를 클릭합니다.

![Custom domain names - Main]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/02.png)

상단의 `Add custom domain`을 클릭합니다.

![Custom domain names - Add Domain]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/03.png)

원하는 도메인을 입력하고 하단의 `Add domain`을 클릭합니다.

![Custom domain names - Domain Verification]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/04.png)

도메인 검증을 위해 TXT 또는 MX 레코드를 자신이 소유한 DNS에 입력해야만 합니다.

저희는 AWS의 Amazon Route 53을 사용해보겠습니다.

# Amazon Route 53에 Verification Record 생성

![Route 53]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/05.png)

AWS의 Route 53으로 접속합니다. 미리 사용할 도메인의 Hosted Zone은 생성이 되어 있어야 합니다.

우측의 `Create record`를 클릭해 레코드 생성을 시작합니다.

![Route 53 - Create record]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/06.png)

Azure에서 안내한대로 TXT 레코드에 값을 추가합니다. 서브도메인은 입력하지 않습니다.

Route 53에서 `@`는 루트 도메인을 의미하므로, 서브도메인은 빈칸으로 두는 것이 올바른 설정 방법입니다.

바로 `Create records`를 클릭해 레코드를 생성합니다.

### 이미 TXT 레코드가 있는 경우

![Route 53 - Create Record Error]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/07.png)

```
Error occurred
A record with the specified name already exists.
(InvalidChangeBatch 400: Tried to create resource record set [name='wsskorea.cloud.', type='TXT'] but it already exists)
```

Route 53에서 다음과 같은 오류가 발생할 때는, 이미 TXT 레코드가 존재하기 때문에 나타나는 오류입니다.

이때는 TXT 레코드에 Azure의 값을 원래 존재했던 레코드에 **추가**해야 합니다.

![Route 53 - Find Existed TXT Record]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/08.png)

레코드 목록을 확인하면, 다음과 같이 TXT 레코드가 이미 존재하는데, 이 레코드를 클릭 후 우측에서 `Edit record`를 클릭합니다.

![Route 53 - Edit TXT Record]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/09.png)

`Value` 항목에 엔터를 누른 후 따옴표로 다음과 같이 감싸주시면 됩니다.

설정이 완료되면 `Save`를 클릭해 변경사항을 적용합니다.

# Azure AD Custom Domain Verification

![Custom Domain Name - Verify]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/10.png)

다시 Azure로 돌아와서, `Verify`를 클릭합니다.

![Custom Domain Name - Verification succeeded]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/11.png)

설정이 정상적으로 완료되었다면, **Verification succeeded!** 라는 문구를 확인할 수 있습니다.

상단의 `Make primary`를 클릭해 이 도메인을 기본 도메인으로 변경합니다.

![Custom Domain Name - Completion]({{ site.url }}{{ site.baseurl }}/assets/images/posts/email-project-02-set-up-ad-custom-domain/12.png)

도메인 목록으로 돌아오면 다음과 같이 새로운 도메인이 추가됨을 확인할 수 있습니다.
