---
type: concept
tags: [it, email, accounts, ops, sop]
status: in-progress
owner: dima
---

# E-Mail-Account & Domain-Struktur

> Konvention für alle E-Mail-Adressen, Accounts und Domains bei cobby. Definiert wer welche Adresse wofür nutzt – intern, bei Kunden und für Services.

## Account-Schema

### Persönliche Accounts

| E-Mail | Zweck |
|---|---|
| `vorname.nachname@cobby.io` | Persönliches Postfach (Google Workspace) |

### Team-Postfächer (Shared)

| E-Mail | Zweck |
|---|---|
| `hello@cobby.io` | Allgemeiner Kontakt, Impressum, **Catch-All** |
| `support@cobby.io` | Kundensupport |
| `sales@cobby.io` | Vertriebsanfragen (Inbound) |
| `billing@cobby.io` | Rechnungsanfragen |
| `jobs@cobby.io` | Bewerbungen |
| `team@cobby.io` | Interne Team-Kommunikation |
| `info@cobby.io` | **TODO:** Zweck klären – versenden / empfangen? |

### Service-Accounts: Intern

Für Services die cobby selbst nutzt (OpenAI, AWS, Hetzner, GitHub etc.):

| E-Mail | Rolle | Beispiel |
|---|---|---|
| `user@cobby.io` | User-Zugang | OpenAI User, GitHub User |
| `admin@cobby.io` | Admin-Zugang | OpenAI Admin, AWS Admin |

### Service-Accounts: Kundenprojekte

Für Tools die wir bei Kunden einrichten (n8n, Shopware etc.):

| E-Mail | Rolle | Beispiel |
|---|---|---|
| `user+kundenname@cobby.io` | User-Zugang beim Kunden | `user+bob@cobby.io` → n8n User bei Bob |
| `admin+kundenname@cobby.io` | Admin-Zugang beim Kunden | `admin+bob@cobby.io` → n8n Admin bei Bob |

### Legacy / Service-Versand

| E-Mail | Zweck | Anmerkung |
|---|---|---|
| `passbolt@cobby.io` | Passbolt-Instanz | Versand via Mailgun Postmaster |

---

## Domain-Struktur

### cobby.io – Interne Kommunikation

**Tool:** Google Workspace | **DMARC:** `p=reject`

Alle persönlichen, Team-, User- und Admin-Postfächer.

### mail.cobby.io – Marketing

**Tool:** Odoo → Mailgun | **DMARC:** `p=quarantine`

| Absender | Typische Events |
|---|---|
| `hello@mail.cobby.io` | Newsletter, Produkt-Updates, Feature-Ankündigungen, Webinare/Events, Partner-Kommunikation, Nurturing-Kampagnen, Case Studies/Content |

> Upgrade auf `p=reject` möglich, sobald DMARC-Reports sauber sind.

### app.cobby.io – Transaktionale E-Mails

**Tool:** Mailgun | **DMARC:** `p=reject`

| Absender | Typische Events |
|---|---|
| `noreply@app.cobby.io` | Passwort zurücksetzen, E-Mail-Verifizierung, App-Onboarding, Produkt-Sync fertiggestellt, Lizenz/Plan-Änderungen, Billing/Rechnungen, Zahlungserinnerungen, Sicherheitswarnungen, Team-Einladungen, Export fertig |

### getcobby.io – Vertrieb

**Tool:** offen | **DMARC:** `p=quarantine`

| Absender | Typische Events |
|---|---|
| `vorname@getcobby.io` | Cold Outreach, Follow-ups, Demo-Einladungen, Angebote/Proposals, Vertragsunterlagen |

> **TODO:** Vertriebstool auswählen, dann DNS-Records ergänzen.

### cobby.it – Ops

**Tool:** Mailgun | **DMARC:** `p=reject`

| Absender | Typische Events |
|---|---|
| `alerts@cobby.it` | System-Alerts, Monitoring, Cronjob-Reports, Error-Logs, Uptime-Benachrichtigungen, Deployment-Notifications |

---

## Credentials

| Tool | Zweck |
|---|---|
| **Bitwarden** | Passwörter, Logins, Kunden-Zugänge, API-Keys (für Menschen) |
| **Infisical** | Secrets, Env-Variablen, API-Keys (für Services/CI) |

**Regel:** Jeder Account wird in Bitwarden gespeichert. Kundenprojekte bekommen eine eigene Collection pro Kunde.

---

## DNS-Checkliste pro Domain

- [ ] SPF-Record konfiguriert
- [ ] DKIM-Record konfiguriert
- [ ] DMARC-Record gesetzt (inkl. `rua`-Tag für Reports)
- [ ] DMARC-Reports gehen an DMARC Analyzer
- [ ] Testmail pro Absender erfolgreich zugestellt
- [ ] Keine SPF/DKIM-Fehler nach 2 Wochen

---

## Offene Punkte

- [ ] `info@cobby.io` – Zweck definieren, versenden und/oder empfangen?
- [ ] Vertriebstool für `getcobby.io` auswählen
- [ ] `passbolt@cobby.io` – noch in Nutzung oder durch Bitwarden abgelöst?
- [ ] DMARC `mail.cobby.io` auf `p=reject` upgraden wenn Reports sauber

---

## Related

- Company: [[companies/cobby]]

---

## History

- **2026-04-23** | Konzept erstellt – Account-Schema und Domain-Struktur dokumentiert
