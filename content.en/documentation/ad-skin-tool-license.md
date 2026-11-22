---
title: "AD Skin Tool License Guide"
translationKey: "ad-skin-tool-license"
summary: "Start the trial, purchase and activate a license, manage devices, and understand online validation and offline access."
description: "A guide to the AD Skin Tool License window, including the 48-hour trial, checkout, activation, device deactivation, automatic validation, and offline access."
date: 2026-10-06T22:23:00+11:00
lastmod: 2026-11-22T18:40:45+11:00
tags: ["maya", "ad-skin-tool", "license", "documentation", "tutorial"]
categories: ["documentation"]
comments: true
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

This guide covers the **License** window, including the 48-hour trial, purchasing and activating a licence, managing device activations, and offline access.

For installation and tool workflows, see the [AD Skin Tool Documentation & Tutorials](/en/documentation/ad-skin-tool-tutorial/). For pricing, compatibility, and downloads, visit the [AD Skin Tool product page](/en/3dtools/ad-skin-tool/).

## Open the License window

Open AD Skin Tool in Maya, then click **License** in the top-right corner. The window displays the current computer's licence status and the actions available for that status.

Opening Maya, AD Skin Tool, or the **License** window—or attempting to use a licensed feature—does **not** start the trial. The 48-hour period begins only when **Start 48-Hour Trial** is clicked.

<!-- GIF suggestion: open-license-window.gif -->

## Start the 48-hour trial

The AD Skin Tool trial provides full access to all features for 48 hours. To begin:

1. Connect the computer to the internet.
2. Open the **License** window.
3. Click **Start 48-Hour Trial**.
4. Wait for the status to change to **Trial active**.

The 48-hour period is measured using server time and continues running even after Maya is closed or the computer is turned off. Resetting local licence data does not restart or extend the trial. The **License** window displays the trial end time in the computer's local time.

When the trial ends, the status changes to **Trial ended** and most tool features become unavailable.

<!-- GIF suggestion: start-trial.gif -->

## Buy a licence after the trial

Click **Buy License** to open AD Skin Tool checkout in the default browser. Freemius handles payment processing as the *Merchant of Record*.

If a launch promotion code appears in the **License** window, select **Have a promotional code?** at checkout and enter the code. Confirm that the discount is reflected in the total, then review the final price, applicable taxes, and checkout terms before payment.

<!-- GIF suggestion: buy-license-checkout.gif -->

## Receive and protect the licence key

After the order is completed, Freemius sends the AD Skin Tool licence key to the email address entered at checkout. Keep the confirmation email, licence key, and invoice for future reference.

If the email has not arrived after a few minutes:

1. Check the Spam, Junk, and Promotions folders.
2. Search the inbox for **AD Skin Tool** or **Freemius**.
3. Check the inbox associated with the email address entered at checkout.
4. If the email is still missing, contact [hello@adiendendra.com](mailto:hello@adiendendra.com) with the purchase email address and a short description of the problem.

Keep the licence key private. Do not publish it, display it in tutorial recordings, or include the complete key in screenshots.

## Activate the paid licence

An internet connection is required for initial activation. Once connected:

1. Return to Maya and open the **License** window.
2. Copy the complete licence key from the Freemius purchase email or customer account.
3. Paste it into the **License Key** text box.
4. Click **Activate License**.
5. Wait for the status to change to **License active**.

A successful activation displays:

> **License active**  
> This device is licensed and ready to use.  
> Next auto-validation: *date and time*.  
> Offline access available until: *date and time*.

Each Individual licence can be active on up to **two personal devices**. If both slots are occupied, deactivate an unused device before activating another one.

<!-- GIF suggestion: activate-license.gif -->

## Understand automatic validation and offline access

AD Skin Tool uses a perpetual licence. The two dates in the **License** window govern online validation and offline access, **not the expiry of the purchased licence**.

| License window text | Meaning |
|---|---|
| **Next auto-validation** | When the next online licence check is due, normally seven days after the last successful activation or validation. |
| **Offline access available until** | How long saved offline access remains valid without a server connection, normally 30 days after the last successful activation or validation. |

Once **Next auto-validation** is reached, AD Skin Tool checks the licence automatically when the tool is next opened or a licensed feature is used. No manual action is needed to start the check.

If the computer is temporarily offline, the status may show **Working offline**. Licensed features remain available until the offline-access date shown in the window. AD Skin Tool retries validation the next time it opens. After reconnecting, click **Retry Now** to check immediately.

Each successful online check refreshes both dates based on the time of that check. If the computer remains offline past the offline-access date, licensed features are blocked and the window shows:

> **Online check required**  
> Offline access has ended.  
> Connect to the internet and click Retry Now to validate your license.

To restore access, reconnect the computer to the internet, click **Retry Now**, and wait for the status to return to **License active**.

## Deactivate This Device

Use **Deactivate This Device** to release the activation slot assigned to the current computer. This is useful before selling or reformatting the computer, reinstalling its operating system, or transferring the licence to another personal device.

1. Connect the currently activated computer to the internet.
2. Open the **License** window.
3. Click **Deactivate This Device**.
4. Read the confirmation dialog, then click **Deactivate**.

Successful deactivation frees one of the two device slots and removes the paid-licence data stored locally by AD Skin Tool. The same computer can be activated again using the same licence key.

Deactivation does **not** cancel the purchase, revoke the licence, deactivate another computer, or delete the order. If the server cannot be reached, local licence data is retained so deactivation can be retried safely.

If an activated computer is lost or no longer accessible, contact [hello@adiendendra.com](mailto:hello@adiendendra.com) for assistance. Do not share the licence key.

<!-- GIF suggestion: deactivate-this-device.gif -->

## Other controls in the License window

| Control | Purpose |
|---|---|
| **Retry Now** | Retries a saved trial or paid-licence request when the current status permits it. Use after reconnecting to the internet or resolving a computer issue. |
| **Reset Local License Data** | Appears only when local licence data requires repair. Clears data on the current computer without freeing a device slot on the server or restarting or extending the trial. Use only when prompted by the **License** window. |
| **Buy License** | Opens the official checkout in the default web browser. |
| **Update** or **Upgrade** | Appears only when a newer release is available for the current installation. Opens the official AD Skin Tool page without installing software in the background or changing the current licence. |

## Common status messages

| Status | What it means and what to do |
|---|---|
| **Trial available** | The trial has not started. Connect to the internet and click **Start 48-Hour Trial** when ready. |
| **Trial active** | All licensed features are available until the trial end time shown in the window. |
| **Trial ended** | Activate a paid license to use licensed features again. |
| **License active** | This computer is activated and all licensed features are ready to use. |
| **Checking license** | An automatic online check is in progress. Licensed features remain available during the check. |
| **Working offline** | The online check could not finish, but saved offline access remains valid. Reconnect before the offline-access date. |
| **Online check required** | Offline access has ended. Connect to the internet and click **Retry Now**. |
| **License not found** | Check that the complete key was copied from the purchase email, then try again. |
| **Device inactive** | This device is no longer activated. Enter the licence key and activate again if a device slot is available. |
| **License inactive** | The licence is no longer active. Activate another valid licence or contact support. |
| **Temporarily unavailable** | The service could not be reached. Check the internet connection and try again later. |
| **Computer clock needs attention** | Correct the computer's date, time, and time zone, then try online validation again. |
| **Local license data needs repair** | Use **Reset Local License Data** when offered, then start the trial if still available or activate a licence. |
| **License checking unavailable** | Reinstall the official AD Skin Tool package. If the message still appears, contact support. |

If activation reports that the device limit has been reached, deactivate AD Skin Tool on an unused device. Contact support if that device is no longer accessible.

## License support

For licence support, email [hello@adiendendra.com](mailto:hello@adiendendra.com) and include:

- Operating system and Maya version. To copy these details, click **Tool Help**, then **Copy Diagnostics**.
- The exact status title and message shown in the **License** window.
- A short description of the action in progress when the problem occurred.
- The purchase email address, if needed to locate the order.

Never send the licence key, payment card details, passwords, or AD Skin Tool files.
