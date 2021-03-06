---
title: Cloudflare Domain Configuration
provider: Cloudflare
dnsprovider: true
description: Learn how to point your Cloudflare domain to a Pantheon site.
tags: [providers]
permalink: docs/:basename/
editpath: dns-providers/cloudflare.md/
---
## Before You Begin
Be sure that you have a:

- Registered domain name using Cloudflare to host DNS
- [Paid Pantheon plan](/docs/guides/launch/plans/)
- [Domain connected](/docs/guides/launch/domains/) to the target Pantheon environment (typically Live)

## Configure DNS Records on Cloudflare
### A Record
1. Click **DNS** in the menu bar.
2. Select **A** from the dropdown menu.
4. Enter **@** in the **Name** field and enter the A record value provided by Pantheon in the **IPv4 Address** field.
5. Select desired Time to Live (TTL).

    {% include("ttl.twig") %}

6. Disable Cloudflare's CDN by clicking the cloud icon (should be gray, not orange).
6. Click **Add Record**.

### AAAA Records
1. Select **AAAA** from the dropdown menu.
2. Enter **@** in the **Name** field and enter the A record value provided by Pantheon in the **IPv6 Address** field.
3. Select desired Time to Live (TTL).
4. Disable Cloudflare's CDN by clicking the cloud icon (should be gray, not orange).
5. Click **Add Record**.
6. Repeat steps 1-5 for the second AAAA record value provided by Pantheon. There are two AAAA records for improved uptime and reliability.

### CNAME Record
The CNAME record is required if you wish to include `www` within your site's primary domain name.

1. Select **CNAME** from the dropdown menu.
2. Enter **www** in the **Name** field and enter the CNAME record value provided by Pantheon (e.g. `live-example.pantheonsite.io`) in the **Domain name** field.
3. Select desired Time to Live (TTL).
4. Disable Cloudflare's CDN by clicking the cloud icon (should be gray, not orange).
5. Click **Add Record**.


## FAQs
### Can I stack Cloudflare's CDN ontop of Pantheon's Global CDN?
We only recommend this if you are using CloudFlare's WAF tools or other features may want to keep CloudFlare in their stack. There are no known issues with layering CloudFlare and the Global CDN together, but we strongly recommend you enforce HTTPS in Cloudflare **and** within WordPress or Drupal to avoid mixed content warnings and infinite redirect errors.

Within Cloudflare, set SSL mode to Full and enable Automatic HTTPS Rewrites. For details on how to enforce HTTPS in your CMS, see [Redirect to a Primary Domain](/docs/guides/launch/redirects/).

## Cloudflare Docs

* <a href="https://support.cloudflare.com/hc/en-us/articles/200169046-How-do-I-add-a-CNAME-record-" target="blank">How do I add a CNAME record? <span class="glyphicons glyphicons-new-window-alt"></span></a>
* <a href="https://support.cloudflare.com/hc/en-us/articles/200169096-How-do-I-add-A-records-" target="blank">How do I add A records? <span class="glyphicons glyphicons-new-window-alt"></span></a>

## Next Steps

* [Launch Essentials: Domains & HTTPS](/docs/guides/launch/domains/)
* [Launch Essentials: Redirect to a Primary Domain](/docs/guides/launch/redirects/)
