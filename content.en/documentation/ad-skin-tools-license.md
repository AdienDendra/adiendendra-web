---
title: "AD Skin Tools License Guide"
translationKey: "ad-skin-tools-license"
summary: "Start the trial, purchase and activate a license, manage devices, and understand online validation and offline access."
description: "Customer guide to the AD Skin Tools License window, including the 48-hour trial, checkout, activation, device deactivation, automatic validation, and offline access."
date: 2026-10-06T22:23:00+11:00
lastmod: 2026-10-06T22:23:00+11:00
tags: ["maya", "ad-skin-tools", "license", "documentation", "tutorial"]
categories: ["documentation"]
comments: false
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

This guide explains the **License** window from a customer's point of view: how to start the full-featured trial, purchase AD Skin Tools, activate a license key, move an activation between devices, and work offline.

For installation and tool workflows, see the [AD Skin Tools Documentation & Tutorials](/en/documentation/ad-skin-tools/). For pricing, compatibility, and downloads, visit the [AD Skin Tools product page](/en/3dtools/ad-skin-tools/).

## Open the License window

Open AD Skin Tools in Maya, then click **License** in the main tool window. The License window shows the current status for this computer and the actions available for that status.

Simply opening Maya, AD Skin Tools, the License window, or a protected tool action does **not** start the trial. The trial starts only when you explicitly click **Start 48-Hour Trial**.

<!-- GIF suggestion: open-license-window.gif -->

## Start the 48-hour trial

The trial provides access to all protected AD Skin Tools features for 48 hours.

1. Connect the computer to the internet.
2. Open the **License** window.
3. Click **Start 48-Hour Trial**.
4. Wait for the status to change to **Trial active**.

The 48-hour period is measured using server time. It continues while Maya or the computer is closed, and resetting local license data does not restart or extend it. The License window displays when the trial ends in your computer's local time.

When the period ends, the status changes to **Trial ended** and protected tool actions are unavailable. You can still open the License window, purchase a license, and activate it.

<!-- GIF suggestion: start-trial.gif -->

## Buy a license after the trial

Click **Buy License** to open the secure AD Skin Tools checkout in your default web browser. The checkout is hosted by Lemon Squeezy, the payment provider and Merchant of Record.

Before paying, confirm that the checkout shows **AD Skin Tools** and review the displayed price, currency, taxes, and final total. The available fields can vary slightly by payment method and billing country.

| Checkout section | What to enter |
|---|---|
| Email | Use an address you can access. The order confirmation and license key are sent to this address. |
| Payment method | Choose one of the methods offered at checkout, such as card or PayPal. |
| Card details | For a card payment, enter the card number, expiration date, and security code. |
| Cardholder and billing details | Enter the cardholder name, country, billing address, city, state or region when requested, and postal code. |
| Tax ID number | Optional. Complete this only when it applies to your purchase. |
| Discount code | Optional. Enter a valid current code, if you have one, then verify the updated total. |

The payment form may offer to save your payment information for faster checkout. This is optional and is not required to receive or use an AD Skin Tools license.

After checking the final total, complete the payment using the button that displays **Pay** and the amount. Do not close the checkout until it confirms that the order has completed.

<!-- GIF suggestion: buy-license-checkout.gif -->

## Receive and protect the license key

After a completed order, Lemon Squeezy sends an email to the address used at checkout. The email contains the license key required by AD Skin Tools.

If the email does not appear after a few minutes:

1. Check the Spam, Junk, and Promotions folders.
2. Search the mailbox for **AD Skin Tools** or **Lemon Squeezy**.
3. Confirm that you are checking the same address used at checkout.
4. If it is still missing, contact [hello@adiendendra.com](mailto:hello@adiendendra.com) and include the order email and a short description of the problem.

Treat the license key as private. Do not publish it, include it in a tutorial recording, or send the complete key in a screenshot or support message.

## Activate the paid license

Activation requires an internet connection.

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

The license key text box is cleared after successful activation. You do not need to paste the key again during normal use.

Each Individual license may be active on up to **two personal devices**. If both slots are already in use, deactivate a device you no longer need before activating another one.

<!-- GIF suggestion: activate-license.gif -->

## Understand automatic validation and offline access

AD Skin Tools is a perpetual purchase; the two dates in the License window are validation windows, **not the expiration date of the purchased license**.

| License window text | Meaning |
|---|---|
| **Next auto-validation** | The next date when the tool should refresh its license status online. This is normally seven days after the last successful activation or validation. |
| **Offline access available until** | The final date when the currently stored, verified offline access can be used without a successful server connection. This is normally 30 days after the last successful activation or validation. |

After **Next auto-validation** is reached, the tool automatically attempts validation when AD Skin Tools is opened or when a protected action is used. You do not normally need to click anything.

If the computer is temporarily offline, the status can show **Working offline**. Protected actions remain available until the displayed offline-access date. The tool tries again on a later eligible launch or protected action, and **Retry Now** can request an immediate check after the internet connection is restored.

Every successful online validation moves both dates forward from that successful check. If the computer remains offline until the offline-access date passes, protected actions are blocked and the window displays:

> **Online check required**  
> Offline access has ended.  
> Connect to the internet and click Retry Now to validate your license.

Reconnect the computer, click **Retry Now**, and wait for **License active** to return.

## Deactivate This Device

Use **Deactivate This Device** when you want to release this computer's activation slot—for example, before replacing, selling, or reformatting the computer, or when moving the license to another personal device.

1. Connect the currently activated computer to the internet.
2. Open the **License** window.
3. Click **Deactivate This Device**.
4. Review the confirmation, then click **Deactivate**.

Successful deactivation releases one of the two device slots and removes the paid license data stored by AD Skin Tools on that computer. You can activate the same computer again later using the same license key.

Deactivation does **not** cancel the purchase, revoke the license, deactivate another computer, or delete the customer's order. If deactivation cannot reach the server, the local license is kept so the operation can be retried safely.

If the old computer is lost or no longer accessible, contact [hello@adiendendra.com](mailto:hello@adiendendra.com) for help instead of sharing the license key.

<!-- GIF suggestion: deactivate-this-device.gif -->

## Other controls in the License window

| Control | Purpose |
|---|---|
| **Retry Now** | Immediately retries a stored trial or paid-license request when the current status allows it. It is mainly used after restoring an internet connection or correcting the computer clock. |
| **Reset Local License Data** | A recovery action shown only when local license data needs repair. It clears license data on this computer, but it does not release a server-side device slot or restart or extend a trial. Use it only when the window instructs you to do so. |
| **Buy License** | Opens the official hosted checkout in the default web browser. |
| **Update** or **Upgrade** | Appears only when a newer applicable release is available. It opens the official AD Skin Tools page; it does not silently install software or change the current license. |

## Common status messages

| Status | What it means and what to do |
|---|---|
| **Trial available** | The trial has not started. Connect to the internet and click **Start 48-Hour Trial** when ready. |
| **Trial active** | All protected features are available until the displayed trial end time. |
| **Trial ended** | Activate a paid license to continue using protected features. |
| **License active** | This computer is activated and ready to use. |
| **Checking license** | An automatic online check is running. Protected actions remain available during the check. |
| **Working offline** | The online check could not complete, but the stored offline period is still valid. Restore the connection before the offline-access date. |
| **Online check required** | Offline access has ended. Connect to the internet and click **Retry Now**. |
| **License not found** | Check that the complete key was copied from the correct purchase email, then try again. |
| **Device inactive** | This device is no longer active. Paste the key and activate it again if a device slot is available. |
| **License inactive** | The license is no longer active. Use another valid license or contact support. |
| **Temporarily unavailable** | The service could not be reached. Check the internet connection and retry later. |
| **Computer clock needs attention** | Correct the computer's date, time, and time zone, then retry online. |
| **Local license data needs repair** | Use **Reset Local License Data** when offered, then start the trial or activate again. |
| **License checking unavailable** | Reinstall the official AD Skin Tools package. If the message remains, contact support. |

If activation reports that the device limit has been reached, deactivate AD Skin Tools on a device you no longer use. If that device is unavailable, contact support.

## License support

For licensing help, email [hello@adiendendra.com](mailto:hello@adiendendra.com) with:

- The operating system and Maya version.
- The exact status title and message shown in the License window.
- A short description of what you were doing when the problem occurred.
- The purchase email address when order lookup is required.

Never send the complete license key, payment-card details, passwords, or confidential production files.
