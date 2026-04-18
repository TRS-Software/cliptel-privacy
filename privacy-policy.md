# Privacy Policy — ClipTel Chrome Extension

**Last updated: 2026-04-18**

**Responsible:** Tino Strasser / TRS Software  
Walther-Rathenau-Str. 59 · 75180 Pforzheim · Germany  
E-Mail: info@trssoftware.com

---

## 1. Overview

ClipTel is a Chrome browser extension that lets you transfer clipboard contents between your PC and your mobile phone using your own private Telegram bot. The extension is designed with privacy in mind: no ClipTel server is involved in transmitting your data.

---

## 2. Data We Collect and Store

### 2.1 Locally on Your Device (Chrome Storage)

The following data is stored exclusively in `chrome.storage.local` on your device:

| Data | Purpose |
|------|---------|
| Telegram bot token | Authenticates with the Telegram Bot API |
| Telegram chat ID | Identifies your private chat channel |
| Last update ID | Tracks which Telegram messages have been processed |
| Poll interval setting | Your preferred background check interval |
| Long content mode setting | Your preference for handling large texts |
| Clipboard history (last 50 entries) | Shows sent/received snippets in the popup |

This data **never leaves your device** to any ClipTel server. It is deleted automatically if you uninstall the extension, or manually via the "Disconnect & reset" button in settings.

### 2.2 Data Transmitted to Telegram

When you send clipboard content or receive a message through ClipTel, the text content is transmitted to **Telegram Messenger Inc.** via their Bot API (`api.telegram.org`). This transmission is:

- **TLS-encrypted** (HTTPS)
- **Not end-to-end encrypted** — Telegram's cloud chats use server-side encryption. Telegram's servers can technically read the content. See Telegram's Privacy Policy for details.

Telegram's Privacy Policy applies: **https://telegram.org/privacy**

Your IP address is visible to Telegram's servers during each API request.

---

## 3. Third Parties

ClipTel only communicates with one external service:

**Telegram Messenger Inc.**  
71–75 Shelton Street, London, WC2H 9JQ, United Kingdom  
Privacy Policy: https://telegram.org/privacy

No other external services, analytics tools, advertising networks, or tracking services are used.

---

## 4. Permissions

| Permission | Reason |
|-----------|--------|
| `storage` | Store your bot token, chat ID, and settings locally |
| `clipboardRead` | Read your clipboard content to send it to your phone |
| `clipboardWrite` | Write incoming text from your phone to your clipboard |
| `notifications` | Display confirmation when text is sent or received |
| `alarms` | Run background polling every 30–60 seconds |
| `offscreen` | Chrome MV3 requirement for clipboard access from service worker |
| `contextMenus` | Add "Send to phone" entry to right-click menu |
| Host permission: `api.telegram.org` | Communicate with the Telegram Bot API (only this domain) |

---

## 5. Your Rights (GDPR)

If you are located in the European Economic Area (EEA), you have the right to:

- **Access** your data (all data is visible in Chrome DevTools → Application → Local Storage)
- **Delete** your data (use "Disconnect & reset" in settings, or uninstall the extension)
- **Data portability** — your data is stored in standard JSON format in Chrome's local storage
- **Lodge a complaint** with a supervisory authority

Since all user data is stored locally on your own device, we have no server-side records to provide or delete on request. The "Disconnect & reset" button in the extension settings permanently clears all locally stored data.

---

## 6. Data Retention

- **Local data**: Retained until you reset or uninstall the extension
- **Telegram data**: Subject to Telegram's own data retention policy (https://telegram.org/privacy)

---

## 7. Security

- Your bot token is stored in `chrome.storage.local` and is inaccessible to web pages
- The token is never logged to the browser console or included in error notifications
- All Telegram API communication uses HTTPS
- The extension's host permissions are strictly limited to `api.telegram.org` — it cannot read or modify any web pages you visit

---

## 8. Children

ClipTel is not directed at children under 13 years of age. We do not knowingly collect personal information from children.

---

## 9. Changes to This Policy

We may update this Privacy Policy from time to time. The current version is always available at:  
**https://trs-software.github.io/cliptel-privacy/**

---

## 10. Contact

Questions or concerns? Contact us at:  
**info@trssoftware.com**

---

*Tino Strasser / TRS Software · Walther-Rathenau-Str. 59 · 75180 Pforzheim · Germany*
