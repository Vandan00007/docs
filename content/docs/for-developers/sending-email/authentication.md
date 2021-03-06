---
seo:
 title: Authentication 
 description: Authenticating with the SendGrid API.
 keywords: getting started, Authentication, authorization, API key
title: Authentication
group: sending-email
weight: 0
layout: page
navigation:
 show: true
---

SendGrid supports both API key and basic authentication, depending on the functionality you are using. On top of API key authentication, SendGrid offers two-factor authentication (2FA) to improve security.

## API key (recommended)

Authenticate to the SendGrid API by creating an API Key in the Settings section of the SendGrid UI.

SendGrid recommends API Keys because they are a secure way to talk to the SendGrid API that is separate from your username and password. If your API key gets compromised in any way, it is easy to delete and create a new one and update your environment variables with the new key. An API key permissions can be set to provide access to different functions of your account, without providing full access to your account as a whole.

To use the API Key, have a header with a key Authorization and a value of `Bearer <Your-API-Key-Here>`, where you replace `<Your-API-Key-Here>` with the API Key that you created in the UI.

<call-out>

SendGrid supports API keys with the SMTP API, the /v3/ API (except the methods to create API keys), and with the `/api/mail.send.json` and `/api/mail.send.xml`.

</call-out>

Example header:

```
GET https://api.sendgrid.com/v3/resource HTTP/1.1
Authorization: Bearer Your.API.Key-HERE
```

``` bash
curl -X "GET" "https://api.sendgrid.com/v3/templates" -H "Authorization: Bearer Your.API.Key-HERE" -H "Content-Type: application/json"
```

## Basic authentication

SendGrid does not recommend using basic authentication because it is inherently less secure than API Key authentication and does not allow the usage of Two-Factor Authentication. However, if you are using our legacy v2 API, you have to use basic authentication to connect.

### Security with basic authentication

Using basic authentication is not as secure as using an API key because it uses your username and password credentials, allowing full access to your account. So, if your credentials get compromised, (like if you accidentally commit them to GitHub), it is more difficult to regain the security of your account.

<call-out type="warning">

If you are currently using basic authentication, we recommend upgrading your authentication method to [API Keys]({{root_url}}/ui/account-and-settings/api-keys/) and then enabling Two-Factor Authentication for improved security.

</call-out>

## Two-factor authentication

Enabling two-factor authentication (2FA) will allow Twilio SendGrid to deliver confirmation codes via SMS to your mobile phone. You will not be able to log in when cellular service is not available. SMS 2FA is powered by [Authy](https://authy.com/). Selecting this option does not require an Authy account, but if you have one, you will be able to use either the [Authy App](https://www.authy.com/app/mobile/) or SMS messages.

SendGrid recommends enabling two-factor authentication (2FA) for all users. For more information about setting up 2FA, see [Two-factor authentication]({{root_url}}/ui/account-and-settings/two-factor-authentication/).

<call-out type="warning">

It is not possible to use basic authentication for users, subusers, or teammates that enable 2FA.

