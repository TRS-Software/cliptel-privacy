# Datenschutzerklärung — ClipTel Chrome-Extension

**Stand:** 18. April 2026

---

## 1. Geltungsbereich

Diese Datenschutzerklärung gilt für die Chrome-Browser-Extension **ClipTel – Clipboard to Telegram** (nachfolgend „Extension" oder „ClipTel") sowie alle damit verbundenen Datenverarbeitungsvorgänge. Sie richtet sich an natürliche Personen, die ClipTel installieren und nutzen.

ClipTel ist eine browserseitige Software ohne eigene Cloud-Infrastruktur. Es existiert kein ClipTel-Server, der Nutzerdaten verarbeitet oder speichert. Die Extension vermittelt Daten ausschließlich zwischen dem Gerät des Nutzers und dem Telegram-Bot-API-Dienst.

---

## 2. Verantwortlicher (Art. 4 Nr. 7 DSGVO)

Verantwortlicher im Sinne der Datenschutz-Grundverordnung (DSGVO) ist:

**Tino Strasser / TRS Software**  
Walther-Rathenau-Str. 59  
75180 Pforzheim  
Deutschland  
E-Mail: info@trssoftware.com

---

## 3. Allgemeines zur Datenverarbeitung und Rechtsgrundlagen

### 3.1 Grundsatz der Datenminimierung

ClipTel ist nach dem Prinzip der Datenminimierung (Art. 5 Abs. 1 lit. c DSGVO) entwickelt. Es werden ausschließlich die Daten verarbeitet, die zur Kernfunktion der Extension — dem bidirektionalen Clipboard-Transfer zwischen PC und Mobilgerät via Telegram-Bot — zwingend erforderlich sind.

### 3.2 Rechtsgrundlagen

Die Verarbeitung personenbezogener Daten durch ClipTel stützt sich auf folgende Rechtsgrundlagen der DSGVO:

- **Art. 6 Abs. 1 lit. b DSGVO (Vertragserfüllung):** Die Verarbeitung der technischen Konfigurationsdaten (Bot-Token, Chat-ID) ist zur Erbringung der mit dem Nutzer vereinbarten Funktion der Extension erforderlich.
- **Art. 6 Abs. 1 lit. a DSGVO (Einwilligung):** Soweit Clipboard-Inhalte über Telegram-Server übertragen werden, erfolgt dies auf Grundlage der ausdrücklichen Einwilligung des Nutzers. Diese Einwilligung wird im Onboarding-Prozess der Extension vor der erstmaligen Nutzung eingeholt (Datenschutz-Hinweis mit Bestätigungs-Checkbox). Die Einwilligung ist jederzeit widerrufbar durch Deinstallation der Extension oder Nutzung der Funktion „Trennen & zurücksetzen".
- **Art. 6 Abs. 1 lit. f DSGVO (berechtigte Interessen):** Soweit technisch notwendige Daten (z. B. letzte Update-ID für den Telegram-Polling-Mechanismus) lokal gespeichert werden, um den bestimmungsgemäßen Betrieb der Extension sicherzustellen.

---

## 4. Art der verarbeiteten Daten

### 4.1 Lokal auf dem Gerät des Nutzers (chrome.storage.local)

Folgende Daten werden ausschließlich lokal im Chrome-Browser-Speicher (`chrome.storage.local`) auf dem Gerät des Nutzers gespeichert. Sie verlassen das Gerät nicht in Richtung ClipTel:

| Datum | Zweck | Rechtsgrundlage |
|-------|-------|----------------|
| Telegram Bot-Token | Authentifizierung gegenüber der Telegram Bot-API | Art. 6 Abs. 1 lit. b DSGVO |
| Telegram Chat-ID | Identifikation des privaten Chat-Kanals des Nutzers | Art. 6 Abs. 1 lit. b DSGVO |
| Letzte Update-ID | Vermeidung doppelter Verarbeitung eingehender Nachrichten | Art. 6 Abs. 1 lit. f DSGVO |
| Poll-Intervall-Einstellung | Speicherung der Nutzerpräferenz für das Hintergrund-Polling | Art. 6 Abs. 1 lit. b DSGVO |
| Einstellung „Lange Inhalte" | Nutzerpräferenz für Verarbeitung von Inhalten >4.000 Zeichen | Art. 6 Abs. 1 lit. b DSGVO |
| Clipboard-Verlauf (max. 50 Einträge) | Darstellung zuletzt gesendeter/empfangener Texte im Popup | Art. 6 Abs. 1 lit. a DSGVO |
| Datenschutz-Bestätigung (Boolean) | Nachweis der erteilten Einwilligung | Art. 6 Abs. 1 lit. c DSGVO |

### 4.2 Verarbeitung nach Chrome-Permission

**`storage`** — Speicherung aller oben genannten Konfigurationsdaten lokal im Browser. Kein Zugriff durch Webseiten oder andere Extensions.

**`clipboardRead`** — Die Extension liest den Inhalt der Zwischenablage (Clipboard) des Nutzers ausschließlich auf explizite Nutzerinitiative (Klick auf „Senden"-Schaltfläche, Tastaturkürzel Ctrl+Shift+C oder Kontextmenü). Der Clipboard-Inhalt wird anschließend an die Telegram Bot-API übermittelt (siehe Abschnitt 5) und lokal im Verlauf gespeichert.

**`clipboardWrite`** — Die Extension schreibt eingehende Textnachrichten vom Mobilgerät des Nutzers (übermittelt via Telegram Bot-API) in die Zwischenablage. Dieser Vorgang erfolgt automatisch beim Empfang einer Nachricht.

**`notifications`** — Die Extension zeigt Desktop-Benachrichtigungen an, die bestätigen, dass ein Text gesendet oder empfangen wurde. Benachrichtigungen enthalten eine Vorschau (max. 100 Zeichen) des übertragenen Textes sowie den Bot-Token zu keiner Zeit.

**`alarms`** — Die Extension erstellt einen wiederkehrenden Hintergrund-Alarm (mindestens 30 Sekunden, durch Nutzer auf 60 Sekunden anpassbar), um regelmäßig neue eingehende Nachrichten bei der Telegram Bot-API abzurufen (Polling). Dies ist eine technische Notwendigkeit, da Manifest-V3-Service-Worker keine dauerhaften Verbindungen aufrechterhalten können.

**`offscreen`** — Chrome Manifest V3 erlaubt Service-Workern keinen direkten Zugriff auf die Clipboard-API. Die Extension erstellt daher bei Bedarf ein sogenanntes Offscreen-Document (eine unsichtbare Hintergrundseite), die Lese- und Schreibzugriffe auf die Zwischenablage stellvertretend durchführt. Das Offscreen-Document enthält keine personenbezogenen Daten und wird nach der Operation freigegeben.

**`contextMenus`** — Die Extension fügt dem Rechtsklick-Kontextmenü des Browsers bei markiertem Text einen Eintrag „An Handy senden (ClipTel)" hinzu. Der markierte Text wird auf Klick über die Telegram Bot-API übermittelt.

**`host_permissions: https://api.telegram.org/*`** — Ausschließlich diese eine Domain wird von der Extension kontaktiert. Die Extension greift auf keine weiteren Webseiten, Dienste oder APIs zu. Insbesondere liest oder manipuliert die Extension keine vom Nutzer besuchten Webseiten.

---

## 5. Datenübermittlung an Telegram

### 5.1 Empfänger und Datenart

Wenn der Nutzer Clipboard-Inhalte über ClipTel an sein Mobilgerät sendet oder Text von seinem Mobilgerät empfängt, werden diese Inhalte an die Telegram Messenger Inc. übermittelt:

**Telegram Messenger Inc.**  
71–75 Shelton Street  
London, WC2H 9JQ  
Vereinigtes Königreich  
Datenschutzerklärung: https://telegram.org/privacy

Die übermittelten Daten sind:
- Der Text des Clipboard-Inhalts (beim Senden)
- Der Bot-Token als Authentifizierungsmerkmal (in jeder API-Anfrage, im HTTP-Header-Pfad)
- Die Chat-ID des Nutzers (als Empfänger-Identifikation)
- Die IP-Adresse des PC des Nutzers (technisch unvermeidbar bei jeder HTTPS-Verbindung)

### 5.2 Verschlüsselung und Sicherheit

Die Übertragung erfolgt ausschließlich über HTTPS (TLS 1.2 oder höher). Die Daten sind damit auf dem Transportweg verschlüsselt. **Es handelt sich jedoch nicht um Ende-zu-Ende-Verschlüsselung.** Telegram-Cloud-Chats, die Bots verwenden, nutzen serverseitige Verschlüsselung. Telegram kann technisch auf den Inhalt der über Bot-APIs übertragenen Nachrichten zugreifen. Für das Versenden hochsensibler Daten (z. B. Passwörter, medizinische Informationen, Bankdaten) ist ClipTel ausdrücklich nicht geeignet.

### 5.3 Hinweis im Onboarding

Die Extension macht Nutzer vor der erstmaligen Nutzung durch einen hervorgehobenen Hinweis mit Bestätigungs-Checkbox auf diesen Sachverhalt aufmerksam. Eine Nutzung der Sendefunktion ist erst nach ausdrücklicher Bestätigung möglich.

---

## 6. Speicherdauer

| Datenart | Speicherdauer | Löschmöglichkeit |
|----------|--------------|-----------------|
| Lokale Konfigurationsdaten | Bis zur Deinstallation der Extension oder manuellem Reset | „Trennen & zurücksetzen" in den Einstellungen |
| Clipboard-Verlauf | Bis zur manuellen Löschung oder bis max. 50 Einträge überschritten werden (älteste werden automatisch verdrängt) | „Löschen"-Button im Popup |
| Daten bei Telegram | Gemäß der Datenschutzerklärung von Telegram (https://telegram.org/privacy) | Im Telegram-Chat durch den Nutzer löschbar |

---

## 7. Übermittlung in Drittstaaten

### 7.1 Drittlandstransfer zu Telegram

Telegram Messenger Inc. ist im Vereinigten Königreich (UK) ansässig. Seit dem 31. Januar 2020 gilt das UK nicht mehr als EU-Mitgliedsstaat. Die EU-Kommission hat jedoch am 28. Juni 2021 einen Angemessenheitsbeschluss für das UK erlassen (Artikel 45 DSGVO), der die Übermittlung personenbezogener Daten in das UK ohne zusätzliche Garantien gestattet. Dieser Beschluss gilt bis mindestens Juni 2025 und wird laufend überprüft.

Darüber hinaus hat Telegram seinen operativen Sitz in Dubai (VAE). Für Übermittlungen in die VAE besteht kein Angemessenheitsbeschluss der EU-Kommission. Die Übermittlung stützt sich in diesem Fall auf:

- **Art. 49 Abs. 1 lit. a DSGVO (Einwilligung nach ausdrücklichem Hinweis):** Nutzer werden im Onboarding-Prozess ausdrücklich darauf hingewiesen, dass ihre Clipboard-Inhalte an Telegram-Server übermittelt werden, und bestätigen dies durch Ankreuzen der Datenschutz-Checkbox.

Der Nutzer wird darauf hingewiesen, dass im Drittland (VAE) möglicherweise kein dem EU-Recht gleichwertiges Datenschutzniveau besteht.

### 7.2 Google Chrome Web Store

Um ClipTel zu installieren, nutzen Nutzer den Google Chrome Web Store, der von Google LLC (USA) betrieben wird. Dieser Vorgang unterliegt den Nutzungsbedingungen und der Datenschutzerklärung von Google: https://policies.google.com/privacy. Die Übermittlung von Daten an Google im Rahmen des Chrome Web Stores liegt außerhalb des Verantwortungsbereichs von TRS Software.

---

## 8. Automatisierte Entscheidungsfindung und Profiling

ClipTel führt keine automatisierte Entscheidungsfindung im Sinne von Art. 22 DSGVO durch und erstellt keine Profile über Nutzer. Es werden keine Analysedaten, Tracking-Daten oder Nutzungsstatistiken erhoben.

---

## 9. Rechte der betroffenen Person

Als betroffene Person stehen Ihnen nach der DSGVO folgende Rechte zu:

**Art. 15 DSGVO — Auskunftsrecht:** Sie haben das Recht, Auskunft darüber zu verlangen, welche Sie betreffenden personenbezogenen Daten verarbeitet werden. Da alle Daten lokal in Ihrem Browser gespeichert sind, können Sie diese jederzeit selbst über Chrome DevTools → Application → Local Storage einsehen.

**Art. 16 DSGVO — Recht auf Berichtigung:** Sie haben das Recht, die Berichtigung unrichtiger Sie betreffender personenbezogener Daten zu verlangen. In den Einstellungen der Extension können Sie Token und Chat-ID jederzeit aktualisieren.

**Art. 17 DSGVO — Recht auf Löschung:** Sie haben das Recht, die Löschung Ihrer personenbezogenen Daten zu verlangen. Nutzen Sie die Funktion „Trennen & zurücksetzen" in den Extension-Einstellungen oder deinstallieren Sie die Extension — beides löscht alle lokal gespeicherten Daten vollständig.

**Art. 18 DSGVO — Recht auf Einschränkung der Verarbeitung:** Sie haben das Recht, die Einschränkung der Verarbeitung zu verlangen, sofern die gesetzlichen Voraussetzungen vorliegen.

**Art. 20 DSGVO — Recht auf Datenübertragbarkeit:** Die in der Extension gespeicherten Daten liegen in standardisiertem JSON-Format vor und sind über Chrome DevTools → Application → Local Storage exportierbar.

**Art. 21 DSGVO — Widerspruchsrecht:** Soweit die Verarbeitung auf Art. 6 Abs. 1 lit. f DSGVO (berechtigte Interessen) gestützt wird, haben Sie das Recht, Widerspruch einzulegen.

**Art. 7 Abs. 3 DSGVO — Widerruf der Einwilligung:** Soweit die Verarbeitung auf Ihrer Einwilligung beruht, haben Sie das Recht, diese jederzeit zu widerrufen, ohne dass die Rechtmäßigkeit der bis zum Widerruf erfolgten Verarbeitung berührt wird. Der Widerruf erfolgt durch Deinstallation der Extension oder durch Nutzung von „Trennen & zurücksetzen".

**Art. 77 DSGVO — Beschwerderecht bei einer Aufsichtsbehörde:** Sie haben das Recht, sich bei der zuständigen Datenschutz-Aufsichtsbehörde zu beschweren:

**Der Landesbeauftragte für den Datenschutz und die Informationsfreiheit Baden-Württemberg (LfDI BW)**  
Königstraße 10a  
70173 Stuttgart  
Telefon: +49 711 615541-0  
E-Mail: poststelle@lfdi.bwl.de  
Website: https://www.baden-wuerttemberg.datenschutz.de

---

## 10. Datenschutzbeauftragter

TRS Software ist als Einzelunternehmen nicht zur Bestellung eines Datenschutzbeauftragten verpflichtet (Art. 37 DSGVO). Für datenschutzrechtliche Anfragen wenden Sie sich bitte direkt an:

**info@trssoftware.com**

---

## 11. Datensicherheit

- Der Bot-Token wird in `chrome.storage.local` gespeichert, der für Webseiten und andere Extensions nicht zugänglich ist.
- Der Bot-Token wird zu keinem Zeitpunkt in die Browser-Konsole ausgegeben oder in Desktop-Benachrichtigungen angezeigt.
- Alle Kommunikation mit der Telegram Bot-API erfolgt über HTTPS (TLS).
- Die Host-Permissions der Extension sind auf `https://api.telegram.org/*` beschränkt — die Extension hat keinen Schreibzugriff auf Webseiten, die der Nutzer besucht.
- Die Extension-Dateien werden bei der Installation aus dem Chrome Web Store über eine von Google gesicherte Verbindung übertragen.

---

## 12. Keine Cookies, kein Tracking, kein Analytics

ClipTel verwendet:
- **Keine Cookies** (weder Erstanbieter noch Drittanbieter)
- **Kein Tracking** (kein Google Analytics, kein Matomo, kein Mixpanel oder vergleichbare Dienste)
- **Kein Fingerprinting** (keine Erhebung von Browser- oder Geräteeigenschaften)
- **Keine Werbung** (keine Werbenetzwerke, keine verhaltensbasierte Werbung)
- **Keine Datenverkäufe** (Nutzerdaten werden nicht an Dritte verkauft)

---

## 13. Open-Source-Hinweis

Der Quellcode der Extension ist im privaten GitHub-Repository `TRS-Software/cliptel` hinterlegt. Das Binary wird über den Chrome Web Store verteilt. Diese Datenschutzerklärung ist öffentlich einsehbar unter:  
**https://trs-software.github.io/cliptel-privacy/**

Das Repository der Datenschutzerklärung ist öffentlich:  
**https://github.com/TRS-Software/cliptel-privacy**

---

## 14. Änderungen dieser Datenschutzerklärung

TRS Software behält sich vor, diese Datenschutzerklärung bei wesentlichen Änderungen der Extension oder der Rechtslage zu aktualisieren. Das Datum der letzten Änderung ist oben angegeben. Bei wesentlichen Änderungen, die die Rechte der Nutzer berühren, wird ein entsprechender Hinweis in der Extension eingeblendet.

Die jeweils aktuelle Version ist stets abrufbar unter:  
**https://trs-software.github.io/cliptel-privacy/privacy-de.html**

---

## 15. Kontakt

Bei Fragen oder Anliegen zum Datenschutz:

**Tino Strasser / TRS Software**  
Walther-Rathenau-Str. 59  
75180 Pforzheim  
Deutschland  
E-Mail: **info@trssoftware.com**

---

*Diese Datenschutzerklärung wurde mit Sorgfalt erstellt. Sie ersetzt keine individuelle Rechtsberatung. Bei rechtlichen Unsicherheiten empfehlen wir die Konsultation eines auf Datenschutzrecht spezialisierten Rechtsanwalts.*

*Tino Strasser / TRS Software · Walther-Rathenau-Str. 59 · 75180 Pforzheim*
