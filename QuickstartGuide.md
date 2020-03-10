![](https://raw.githubusercontent.com/avangemail/documentation/master/img/email-smtp.gif)

# Quickstart Guide 

Send email from your app (such as Laravel, WordPress and and etc), with SMTP and API. With sign up in AvangEmail, you'll have a unique token which you can use to authenticate against our SMTP service or our HTTP API.



## Verify Domain

To set up domain for sending, you should add it to your AvangEmail account, and verify that in some step. First of all domain should be accessible . With verify your domain, you will show that authorized sender,not show sent via avangemail.com, positive reputation for your domain.

### How to verify your domain

You point DNS entries from your DNS provider (like Cpanel, Directadmin, Cloudflare, DigitalOcean , Rackspace or DNSSimple) to avangemail. 

| Type  | Value                                                        | Purpose             |
| ----- | ------------------------------------------------------------ | ------------------- |
| TXT   | Find this record in your Control Panel, Domains Tab, this would be like: "v=spf1 a mx include:spf.avang.eu ~all" | SPF (Required)      |
| TXT   | Find this record in your Control Panel                       | DKIM (Required)     |
| CNAME | Find this record in your Control Panel, this would be like: point "psrp.yourdomain.com" to "rp.avang.eu" | Tracking (Optional) |

You can set dns in all dns providers, but we listed a common providers.
