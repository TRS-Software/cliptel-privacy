# Privacy Policy — ClipTel Chrome Extension

**Last updated:** 18 April 2026

---

## 1. Scope

This Privacy Policy applies to the Chrome browser extension **ClipTel – Clipboard to Telegram** (hereinafter "Extension" or "ClipTel") and all associated data processing operations. It is addressed to natural persons who install and use ClipTel.

ClipTel is a browser-side piece of software with no cloud infrastructure of its own. There is no ClipTel server that processes or stores user data. The Extension routes data exclusively between the user's device and Telegram's Bot API service.

---

## 2. Data Controller (Art. 4(7) GDPR)

The data controller within the meaning of the General Data Protection Regulation (GDPR) is:

**Tino Strasser / TRS Software**  
Walther-Rathenau-Str. 59  
75180 Pforzheim  
Germany  
E-mail: info@trssoftware.com

---

## 3. General Principles and Legal Bases

### 3.1 Data Minimisation

ClipTel is built on the principle of data minimisation (Art. 5(1)(c) GDPR). Only data strictly necessary to the core function of the Extension — bidirectional clipboard transfer between PC and mobile device via a Telegram bot — is processed.

### 3.2 Legal Bases

Processing of personal data by ClipTel is based on the following legal grounds:

- **Art. 6(1)(b) GDPR (contract performance):** Processing of technical configuration data (bot token, chat ID) is necessary to provide the functionality agreed with the user.
- **Art. 6(1)(a) GDPR (consent):** Where clipboard contents are transmitted via Telegram servers, this occurs on the basis of the user's explicit consent. Consent is obtained in the onboarding flow before first use (privacy notice with confirmation checkbox) and can be withdrawn at any time by uninstalling the Extension or using "Disconnect & reset".
- **Art. 6(1)(f) GDPR (legitimate interests):** Technically necessary data (e.g. the last update ID for the Telegram polling mechanism) is stored locally to ensure proper functioning of the Extension.

---

## 4. Categories of Data Processed

### 4.1 Locally on the User's Device (chrome.storage.local)

The following data is stored exclusively in Chrome's local browser storage (`chrome.storage.local`) on the user's device. It does not leave the device in the direction of ClipTel:

| Data | Purpose | Legal basis |
|------|---------|-------------|
| Telegram bot token | Authentication with the Telegram Bot API | Art. 6(1)(b) GDPR |
| Telegram chat ID | Identification of the user's private chat channel | Art. 6(1)(b) GDPR |
| Last update ID | Preventing duplicate processing of incoming messages | Art. 6(1)(f) GDPR |
| Poll interval setting | Storing user preference for background polling | Art. 6(1)(b) GDPR |
| Long-content mode setting | User preference for handling content >4,000 characters | Art. 6(1)(b) GDPR |
| Clipboard history (up to 50 entries) | Displaying recently sent/received texts in the popup | Art. 6(1)(a) GDPR |
| Privacy acknowledgement (boolean) | Record of consent given | Art. 6(1)(c) GDPR |

### 4.2 Processing per Chrome Permission

**`storage`** — Storing all configuration data listed above locally in the browser. Not accessible to websites or other extensions.

**`clipboardRead`** — The Extension reads the clipboard content exclusively on explicit user action (click on "Send" button, keyboard shortcut Ctrl+Shift+C, or context menu). The content is then transmitted to the Telegram Bot API (see Section 5) and stored locally in the history.

**`clipboardWrite`** — The Extension writes incoming text messages from the user's mobile device (transmitted via the Telegram Bot API) to the clipboard. This happens automatically on receipt.

**`notifications`** — The Extension displays desktop notifications confirming that text was sent or received. Notifications contain a preview (max. 100 characters) of the transferred text and never contain the bot token.

**`alarms`** — The Extension creates a repeating background alarm (minimum 30 seconds, adjustable by the user up to 60 seconds) to regularly fetch new incoming messages from the Telegram Bot API (polling). This is a technical requirement, as Manifest V3 service workers cannot maintain persistent connections.

**`offscreen`** — Chrome Manifest V3 does not allow service workers direct access to the Clipboard API. The Extension therefore creates an offscreen document (an invisible background page) on demand, which performs clipboard read and write operations on its behalf. The offscreen document contains no personal data and is released after the operation.

**`contextMenus`** — The Extension adds a "Send to phone (ClipTel)" entry to the browser's right-click context menu when text is selected. The selected text is transmitted via the Telegram Bot API on click.

**`host_permissions: https://api.telegram.org/*`** — This is the only domain contacted by the Extension. The Extension does not contact any other websites, services, or APIs. In particular, it does not read or manipulate any websites visited by the user.

---

## 5. Data Transmission to Telegram

### 5.1 Recipient and Data Categories

When the user sends clipboard contents to their mobile device or receives text from their mobile device, those contents are transmitted to Telegram Messenger Inc.:

**Telegram Messenger Inc.**  
71–75 Shelton Street  
London, WC2H 9JQ  
United Kingdom  
Privacy Policy: https://telegram.org/privacy

Data transmitted includes:
- The text of the clipboard content (when sending)
- The bot token as an authentication credential (in every API request URL)
- The user's chat ID (as recipient identifier)
- The IP address of the user's PC (technically unavoidable in any HTTPS connection)

### 5.2 Encryption and Security

Transmission is exclusively over HTTPS (TLS 1.2 or higher). Data is therefore encrypted in transit. **This is not end-to-end encryption.** Telegram cloud chats using bots use server-side encryption. Telegram can technically access the content of messages transmitted via Bot APIs. ClipTel is expressly not suitable for transmitting highly sensitive data (e.g. passwords, medical information, banking data).

### 5.3 Notice in Onboarding

The Extension draws users' attention to this fact through a prominent notice with a confirmation checkbox before first use. The send function cannot be used until the user has given explicit confirmation.

---

## 6. Retention Periods

| Data type | Retention period | How to delete |
|-----------|----------------|---------------|
| Local configuration data | Until extension uninstalled or manual reset | "Disconnect & reset" in settings |
| Clipboard history | Until manually cleared, or until 50-entry limit is exceeded (oldest entries are automatically displaced) | "Clear" button in popup |
| Data held by Telegram | Per Telegram's own privacy policy (https://telegram.org/privacy) | Deletable by the user in the Telegram chat |

---

## 7. International Data Transfers

### 7.1 Transfer to Telegram

Telegram Messenger Inc. is based in the United Kingdom (UK). Following the UK's departure from the EU, the EU Commission adopted an adequacy decision for the UK on 28 June 2021 (Art. 45 GDPR), permitting transfers of personal data to the UK without additional safeguards. This decision is kept under review.

Telegram also has operational offices in Dubai (UAE). No EU Commission adequacy decision exists for the UAE. Transfers to the UAE are based on:

- **Art. 49(1)(a) GDPR (explicit consent after notice):** Users are expressly informed in the onboarding flow that their clipboard contents will be transmitted to Telegram servers, and confirm this by checking the privacy checkbox.

Users are made aware that the UAE may not maintain a level of data protection equivalent to EU law.

### 7.2 Google Chrome Web Store

To install ClipTel, users use the Google Chrome Web Store, operated by Google LLC (USA). This process is subject to Google's Terms of Service and Privacy Policy: https://policies.google.com/privacy. Transmission of data to Google via the Chrome Web Store is outside the responsibility of TRS Software.

---

## 8. Automated Decision-Making and Profiling

ClipTel does not carry out automated decision-making within the meaning of Art. 22 GDPR and does not create profiles about users. No analytics data, tracking data, or usage statistics are collected.

---

## 9. Rights of Data Subjects

As a data subject, you have the following rights under the GDPR:

**Art. 15 GDPR — Right of access:** You have the right to obtain information about the personal data processed about you. Since all data is stored locally in your browser, you can view it at any time via Chrome DevTools → Application → Local Storage.

**Art. 16 GDPR — Right to rectification:** You have the right to have inaccurate personal data corrected. You can update your token and chat ID at any time in the Extension settings.

**Art. 17 GDPR — Right to erasure:** You have the right to have your personal data deleted. Use "Disconnect & reset" in the Extension settings or uninstall the Extension — both permanently delete all locally stored data.

**Art. 18 GDPR — Right to restriction of processing:** You have the right to request restriction of processing where the legal conditions are met.

**Art. 20 GDPR — Right to data portability:** Data stored in the Extension is in standard JSON format and can be exported via Chrome DevTools → Application → Local Storage.

**Art. 21 GDPR — Right to object:** Where processing is based on Art. 6(1)(f) GDPR (legitimate interests), you have the right to object to processing on grounds relating to your particular situation.

**Art. 7(3) GDPR — Right to withdraw consent:** Where processing is based on consent, you have the right to withdraw consent at any time without affecting the lawfulness of processing carried out before withdrawal. Withdrawal is effected by uninstalling the Extension or using "Disconnect & reset".

**Art. 77 GDPR — Right to lodge a complaint:** You have the right to lodge a complaint with a supervisory authority. In Germany, the competent authority is:

**Der Landesbeauftragte für den Datenschutz und die Informationsfreiheit Baden-Württemberg (LfDI BW)**  
Königstraße 10a  
70173 Stuttgart  
Germany  
Phone: +49 711 615541-0  
E-mail: poststelle@lfdi.bwl.de  
Website: https://www.baden-wuerttemberg.datenschutz.de

---

## 10. Data Protection Officer

TRS Software, as a sole proprietorship, is not required to appoint a Data Protection Officer (Art. 37 GDPR). For data protection enquiries, please contact:

**info@trssoftware.com**

---

## 11. Security

- The bot token is stored in `chrome.storage.local`, which is inaccessible to websites and other extensions.
- The bot token is never output to the browser console or included in desktop notifications.
- All communication with the Telegram Bot API is via HTTPS (TLS).
- The Extension's host permissions are restricted to `https://api.telegram.org/*` — the Extension has no write access to websites visited by the user.
- Extension files are transferred during installation from the Chrome Web Store via a Google-secured connection.

---

## 12. No Cookies, No Tracking, No Analytics

ClipTel uses:
- **No cookies** (neither first-party nor third-party)
- **No tracking** (no Google Analytics, Matomo, Mixpanel, or equivalent services)
- **No fingerprinting** (no collection of browser or device characteristics)
- **No advertising** (no ad networks, no behavioural advertising)
- **No data sales** (user data is not sold to third parties)

---

## 13. Open Source

The Extension source code is held in the private GitHub repository `TRS-Software/cliptel`. The binary is distributed via the Chrome Web Store. This Privacy Policy is publicly available at:  
**https://trs-software.github.io/cliptel-privacy/**

The Privacy Policy repository is public:  
**https://github.com/TRS-Software/cliptel-privacy**

---

## 14. Changes to This Privacy Policy

TRS Software reserves the right to update this Privacy Policy when material changes are made to the Extension or to applicable law. The date of the most recent update is shown above. For material changes affecting users' rights, a corresponding notice will be displayed in the Extension.

The current version is always available at:  
**https://trs-software.github.io/cliptel-privacy/privacy-en.html**

---

## 15. Contact

For any data protection questions or concerns:

**Tino Strasser / TRS Software**  
Walther-Rathenau-Str. 59  
75180 Pforzheim  
Germany  
E-mail: **info@trssoftware.com**

---

*This Privacy Policy has been prepared with care. It does not substitute individual legal advice. If you have legal concerns, we recommend consulting a lawyer specialising in data protection law.*

*Tino Strasser / TRS Software · Walther-Rathenau-Str. 59 · 75180 Pforzheim · Germany*
