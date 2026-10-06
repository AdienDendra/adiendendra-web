---
title: "AD Skin Tool License Guide"
translationKey: "ad-skin-tools-license"
summary: "Start the trial, purchase and activate a license, manage devices, and understand online validation and offline access."
description: "A guide to the AD Skin Tool License window, including the 48-hour trial, checkout, activation, device deactivation, automatic validation, and offline access."
date: 2026-10-06T22:23:00+11:00
lastmod: 2026-10-06T23:46:00+11:00
tags: ["maya", "ad-skin-tools", "license", "documentation", "tutorial"]
categories: ["documentation"]
comments: false
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

This guide covers the **License** window: starting the trial, buying AD Skin Tool, activating your license key, moving your activation to another device, and using the tool offline.

For installation and tool workflows, see the [AD Skin Tool Documentation & Tutorials](/en/documentation/ad-skin-tools/). For pricing, compatibility, and downloads, visit the [AD Skin Tool product page](/en/3dtools/ad-skin-tools/).

## Open the License window

Open AD Skin Tool in Maya, then click **License** in the top-right corner. The License window shows the license status for the computer you are using and the actions available for that status.

Opening Maya, AD Skin Tool, or the License window, or trying to use a feature that requires a license, does **not** start the trial. It starts when you click **Start 48-Hour Trial**.

<!-- GIF suggestion: open-license-window.gif -->

## Start the 48-hour trial

The AD Skin Tool trial gives you access to all features for 48 hours. To start your trial:

1. Connect the computer to the internet.
2. Open the **License** window.
3. Click **Start 48-Hour Trial**.
4. Wait for the status to change to **Trial active**.

The 48-hour period is based on server time. It keeps running even when you close Maya or turn off your computer. Resetting local license data does not restart or extend the trial. The License window shows the trial end time in your computer's local time.

When the trial ends, the status changes to **Trial ended** and most tool features become unavailable.

<!-- GIF suggestion: start-trial.gif -->

## Buy a license after the trial

Click **Buy License** to open the AD Skin Tool checkout in your web browser. Lemon Squeezy handles the checkout as the payment provider and *Merchant of Record*.

Before paying, make sure the checkout shows **AD Skin Tool**, then check the price, currency, taxes, and final total. The fields may vary slightly depending on your payment method and billing country.

| Checkout section | What to enter |
|---|---|
| Email | Use an address you can access. The order confirmation and license key are sent to this address. |
| Payment method | Choose one of the methods offered at checkout, such as a debit or credit card, or PayPal. |
| Card details | If paying by debit or credit card, enter the card number, expiry date, and security code. |
| Cardholder and billing details | Enter the cardholder name, country, billing address, city, state or region when requested, and postal code. |
| Tax ID number | Optional. Fill this in only if it applies to your purchase. |
| Discount code | Optional. Enter a valid discount code, then check the updated total. |

The payment form may offer to save your payment information for faster checkout next time. This is optional and is not required to receive or use your AD Skin Tool license.

Once you have checked the final total, complete the payment using the button showing **Pay** and the amount. Wait for confirmation that your order is complete before closing the checkout page.

<!-- GIF suggestion: buy-license-checkout.gif -->

## Receive and protect the license key

Once your order is complete, Lemon Squeezy sends an email to the address you used at checkout. This email contains your AD Skin Tool license key.

If you have not received the email after a few minutes:

1. Check the Spam, Junk, and Promotions folders.
2. Search your inbox for **AD Skin Tool** or **Lemon Squeezy**.
3. Make sure you are checking the same email address you used at checkout.
4. If you still cannot find it, contact [hello@adiendendra.com](mailto:hello@adiendendra.com) with your purchase email address and a short description of the problem.

Keep your license key private. Do not publish it, show it in tutorial recordings, or include the complete key in screenshots.

## Activate the paid license

You need an internet connection to activate the tool. Once your computer is connected:

1. Return to Maya and open the **License** window.
2. Copy the complete license key from the Lemon Squeezy email.
3. Paste it into the **License Key** text box.
4. Click **Activate License**.
5. Wait for the status to change to **License active**.

A successful activation displays:

> **License active**  
> This device is licensed and ready to use.  
> Next auto-validation: *date and time*.  
> Offline access available until: *date and time*.

Each Individual license can be active on up to **two personal devices**. If both slots are in use, deactivate a device you no longer need before activating another one.

<!-- GIF suggestion: activate-license.gif -->

## Understand automatic validation and offline access

AD Skin Tool comes with a perpetual license. The two dates in the License window refer to license checks and offline access, **not the expiry of your purchased license**.

| License window text | Meaning |
|---|---|
| **Next auto-validation** | When the tool is due to check your license status online again. This is normally seven days after your last successful activation or validation. |
| **Offline access available until** | How long your saved offline access remains valid without connecting to the server. This is normally 30 days after your last successful activation or validation. |

Once the **Next auto-validation** time is reached, AD Skin Tool tries to check your license automatically when you open the tool or use a licensed feature. You do not need to press a button to start this check.

If your computer is temporarily offline, the status may show **Working offline**. You can keep using the licensed features until the offline-access date shown in the window. The tool will try again when you next open it. Once you are back online, you can also click **Retry Now** to check immediately.

Each successful online check refreshes both dates from the time of that check. If your computer stays offline beyond the offline-access date, licensed features are blocked and the window shows:

> **Online check required**  
> Offline access has ended.  
> Connect to the internet and click Retry Now to validate your license.

To restore access, connect your computer to the internet, click **Retry Now**, and wait for the status to return to **License active**.

## Deactivate This Device

Use **Deactivate This Device** to free up the activation slot used by your current computer. For example, do this before selling or reformatting the computer, reinstalling its operating system, or moving your license to another personal device.

1. Connect the currently activated computer to the internet.
2. Open the **License** window.
3. Click **Deactivate This Device**.
4. Read the confirmation dialog, then click **Deactivate**.

Once deactivation succeeds, one of your two device slots is freed and the paid license data stored by AD Skin Tool on this computer is removed. You can activate the same computer again using the same license key.

Deactivation does **not** cancel your purchase, revoke your license, deactivate another computer, or delete your order. If the tool cannot connect to the server, it keeps your local license data so you can try deactivation again safely.

If your old computer is lost or you can no longer access it, contact [hello@adiendendra.com](mailto:hello@adiendendra.com) for help. Do not share your license key.

<!-- GIF suggestion: deactivate-this-device.gif -->

## Other controls in the License window

| Control | Purpose |
|---|---|
| **Retry Now** | Tries your saved trial or paid-license request again, when available for the current status. Use it after reconnecting to the internet or correcting your computer's clock. |
| **Reset Local License Data** | Appears only when your local license data needs repair. It clears the license data on this computer, but does not free up a device slot on the server or restart or extend your trial. Use it only when the License window asks you to. |
| **Buy License** | Opens the official checkout in your default web browser. |
| **Update** or **Upgrade** | Appears only when a newer release is available for your installation. It opens the official AD Skin Tool page. The tool does not install software in the background or change your current license. |

## Common status messages

| Status | What it means and what to do |
|---|---|
| **Trial available** | Your trial has not started. Connect to the internet and click **Start 48-Hour Trial** when you are ready. |
| **Trial active** | All licensed features are available until the trial end time shown in the window. |
| **Trial ended** | Activate a paid license to use licensed features again. |
| **License active** | This computer is activated and all licensed features are ready to use. |
| **Checking license** | An automatic online check is in progress. Licensed features remain available during the check. |
| **Working offline** | The online check could not finish, but your saved offline access is still valid. Reconnect before the offline-access date. |
| **Online check required** | Offline access has ended. Connect to the internet and click **Retry Now**. |
| **License not found** | Make sure you copied the complete key from the correct purchase email, then try again. |
| **Device inactive** | This device is no longer activated. Enter your key and activate it again if a device slot is available. |
| **License inactive** | Your license is no longer active. Use another valid license or contact support. |
| **Temporarily unavailable** | The service could not be reached. Check your internet connection and try again later. |
| **Computer clock needs attention** | Correct your computer's date, time, and time zone, then try online validation again. |
| **Local license data needs repair** | Use **Reset Local License Data** when offered, then start the trial or activate again. |
| **License checking unavailable** | Reinstall the official AD Skin Tool package. If the message still appears, contact support. |

If activation reports that you have reached the device limit, deactivate AD Skin Tool on a device you no longer use. If you cannot access that device, contact support.

## License support

For help with your license, email [hello@adiendendra.com](mailto:hello@adiendendra.com) and include:

- Your operating system and Maya version. To copy these details, click **Tool Help**, then **Copy Diagnostics**.
- The exact status title and message shown in the License window.
- A short description of what you were doing when the problem occurred.
- Your purchase email address, if needed to find your order.

Never send your license key, payment card details, passwords, or AD Skin Tool files.
