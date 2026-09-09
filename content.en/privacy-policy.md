+++
title = "Privacy Policy"
translationKey = "privacy-policy"
description = "How this website and AD Skin Tools process website, support, comment, transaction, licensing, and local-device data."
date = 2026-09-09T20:58:00+10:00
lastmod = 2026-09-09T20:58:00+10:00
comments = false
showToc = true
TocOpen = true
ShowReadingTime = false
ShowPostNavLinks = false
+++

**Effective date: 9 September 2026**

This Privacy Policy explains how the website `architecture.adiendendra.com` and AD Skin Tools process information. The website and product are operated by Adien Dendra in Sydney, Australia. Privacy enquiries can be sent to [hello@adiendendra.com](mailto:hello@adiendendra.com).

This policy does not claim that no data is collected. Website infrastructure, email, comments, payment providers, and the licensing service necessarily process limited information to operate.

## 1. Website visits and hosting

The website is a static Hugo site hosted through Cloudflare Pages and delivered through Cloudflare's network. Cloudflare may process technical request and security information such as:

- IP address and approximate network location.
- Requested URL, date, and time.
- Browser, device, operating-system, and request-header information.
- Cache, performance, error, abuse-prevention, and security events.

Cloudflare may set strictly necessary security cookies when its protection features require them. This website does not intentionally configure advertising trackers or third-party advertising cookies.

The site uses browser `localStorage` to remember the visitor's light or dark theme preference. The local 3D Tools filter operates in the browser and does not send filter selections to a server.

See [Cloudflare's Privacy Policy](https://www.cloudflare.com/privacypolicy/) and [Cloudflare Cookies](https://developers.cloudflare.com/fundamentals/reference/policies-compliances/cloudflare-cookies/) for information about Cloudflare's processing.

## 2. External content used by the website

The website currently loads Mermaid and KaTeX resources from the jsDelivr content-delivery network. The homepage also loads the profile image from GitHub. When these resources load, the provider may receive ordinary request information such as the visitor's IP address, browser headers, requested resource, and timestamp.

There is currently no third-party video player embedded on the AD Skin Tools product page. This policy will be updated when a demo-video provider is added.

## 3. Email and support

The website uses an email link rather than a contact form. If you send an email, the information processed may include your:

- Email address and display name.
- Message, attachments, and technical information you choose to provide.
- Order reference and support history when relevant.

This information is used to respond to installation, licensing, compatibility, privacy, and product-related technical enquiries. Email is processed by the email providers used by the sender and recipient.

Do not send a full licence key, confidential production asset, password, or other sensitive information unless it is specifically required and a suitable transfer method has been agreed.

## 4. Comments

Comments are disabled on the AD Skin Tools and policy pages, but an Isso comment system is available on some blog and project pages.

If you submit a comment, Isso may process:

- The comment text, associated page, and timestamps.
- An optional name, email address, or website supplied by you.
- Moderation status and anti-abuse information.
- Technical network information, including a partially anonymised IP address.

Approved comment text and the supplied display name may become public. Email addresses are used for administration or notification and are not intentionally displayed publicly.

Comments are stored in a self-hosted Isso SQLite database. Traffic to the service passes through Cloudflare, and moderation notifications may be sent using Google SMTP. Do not place confidential or sensitive personal information in a public comment.

## 5. Purchases through Lemon Squeezy

When sales open, Lemon Squeezy will provide checkout and act as Merchant of Record. Lemon Squeezy may collect and process information required for payment, tax, fraud prevention, digital delivery, refunds, and chargebacks, including:

- Customer name, email, billing country, and billing details.
- Payment information and transaction identifiers.
- Product, order, tax, refund, and chargeback information.
- Device, network, fraud-prevention, and checkout usage information.

Payment-card details are handled by Lemon Squeezy and its payment providers, not by this website or the AD Skin Tools licensing database. Lemon Squeezy's processing is governed by its [Privacy Policy](https://www.lemonsqueezy.com/privacy) and [Buyer Terms](https://www.lemonsqueezy.com/buyer-terms).

The AD Skin Tools licensing service is designed not to store customer names or email addresses received from Lemon Squeezy webhooks.

## 6. Trial and paid licensing

AD Skin Tools communicates with a licensing service hosted on Amazon Web Services when a user starts a trial or activates, validates, or deactivates a paid licence.

The licensing service may process:

- A device fingerprint generated by the installed tool.
- A pseudonymous digest derived from that fingerprint.
- A licence key during activation or validation.
- A hashed licence-key lookup value rather than the raw key in persistent storage.
- Trial, licence, activation, device-slot, entitlement, and revocation status.
- Server timestamps, validation dates, expiry dates, and request results.
- Standard network and security metadata processed by AWS infrastructure.

The application is designed so that raw device fingerprints and raw licence keys are not written to the licensing database or application logs. Pseudonymous identifiers are still data relating to a device and are treated accordingly.

The licensing information is used to provide the 48-hour trial, enforce the two-device limit, issue signed entitlements, support offline use, validate licences, prevent trial resets, and revoke licences after qualifying refunds, reversals, or other invalidating events.

## 7. Local information on the customer's computer

AD Skin Tools stores a local entitlement and licensing cache on the customer's computer. This may contain pseudonymous device binding information, licence or trial status, signed entitlement data, validation timestamps, and offline-expiry information.

This local information is needed to operate the trial and paid offline grace period. Removing or modifying it does not guarantee a new trial and may require the product to reconnect to the licensing service.

## 8. Why information is processed

Information described in this policy is processed to:

- Deliver, secure, and troubleshoot the website.
- Display site content and remember essential preferences.
- Publish and moderate comments where enabled.
- Respond to support and privacy enquiries.
- Process purchases and digital delivery.
- Start trials and activate, validate, deactivate, or revoke licences.
- Prevent fraud, abuse, licence sharing, and unauthorised trial resets.
- Meet accounting, tax, consumer-protection, dispute, and legal obligations.

## 9. Service providers and disclosure

Information is disclosed only where reasonably required to operate these functions, comply with law, or protect the service. Current relevant providers include Cloudflare, jsDelivr, GitHub, the email provider, Google SMTP for comment notifications, Lemon Squeezy for commerce, and Amazon Web Services for licensing.

These providers may process information in countries outside Australia under their own privacy terms and infrastructure arrangements.

Personal information is not sold by Adien Dendra for advertising purposes.

## 10. Retention

Retention depends on the type of information and operational or legal need:

- Website and security logs follow the settings and retention practices of the hosting provider.
- Support email is kept while needed to resolve the request, maintain support history, prevent abuse, or meet legal obligations.
- Comments remain while the relevant discussion is published or until moderation or a valid deletion request requires removal, subject to backup and security needs.
- Transaction records are retained by Lemon Squeezy and relevant providers according to payment, tax, fraud, dispute, and legal requirements.
- Licensing and pseudonymous device records may remain for the life of the trial or licence and as needed to enforce device, refund, fraud, and revocation state.

Information may be retained longer where required by law, an active dispute, fraud prevention, or security investigation. It will be deleted or anonymised when it is no longer reasonably needed, subject to those requirements.

## 11. Security

Reasonable technical and organisational measures are used to protect information, including encrypted network connections, pseudonymous device identifiers, hashed licence-key lookup, restricted service access, and avoidance of raw keys and raw fingerprints in application logs. No method of transmission or storage can be guaranteed completely secure.

## 12. Access, correction, and deletion requests

You may contact [hello@adiendendra.com](mailto:hello@adiendendra.com) to request access to, correction of, or deletion of personal information controlled by Adien Dendra. Enough information may be required to verify the request and locate the relevant record.

Some information may need to be retained for legal, transaction, fraud-prevention, security, or licence-integrity reasons. Requests concerning checkout or payment data controlled by Lemon Squeezy should also be directed to Lemon Squeezy.

## 13. Changes to this policy

This policy may be updated when the website, video provider, commerce flow, licensing service, or legal requirements change. The effective date will be updated when material changes are published.
