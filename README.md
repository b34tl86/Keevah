<picture>
  <source media="(prefers-color-scheme: dark)" srcset="brand/hero-dark.svg">
  <img alt="Keevah, the AI phone receptionist for Grandstream and Yeastar: answers like your best colleague. Beside the headline, a call on the Keevah board: Keeva is putting a caller through to Accounts." src="brand/hero-light.svg">
</picture>

<p align="center">
  <a href="https://github.com/b34tl86/Keevah/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/b34tl86/Keevah?label=release&color=262b33"></a>
  <img alt="Platforms: Windows, macOS and Linux" src="https://img.shields.io/badge/platforms-Windows%20%7C%20macOS%20%7C%20Linux-262b33">
  <a href="LICENSE"><img alt="Licence: proprietary" src="https://img.shields.io/badge/licence-Proprietary-262b33"></a>
</p>

<p align="center">
  <a href="#editions-and-download">Download</a> ·
  <a href="docs/getting-started.md">Getting started</a> ·
  <a href="ROADMAP.md">Roadmap</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="SUPPORT.md">Support</a>
</p>

## What it does

Keevah answers your business's phone calls with an AI receptionist. Callers ring your usual number. Keeva picks up in a natural voice, finds out who's calling and why, then puts them through to the right department, takes a message, books an appointment, or answers their question from your own documents. Your team sees every call as it happens, with a transcript afterwards and a summary by email.

It works with the Grandstream and Yeastar phone systems you already have. One Keevah server can run reception for many organisations, each with its own receptionist, voice, opening hours and knowledge. You name the receptionist and choose from ten voices.

**New in 1.16:** appointment booking with Google and Outlook calendars, returning callers and Contacts, spam and robocall blocking, frustrated callers offered a person, webhooks and an API, and caller data requests. See the [changelog](CHANGELOG.md).

## Key features

### On the phone

<table>
  <tr>
    <td width="52" valign="top"><img src="brand/icons/answer.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Answers every call</strong><br>Keeva picks up at any hour in a natural voice, lets the caller explain, and asks one thing at a time. Name her, pick one of ten voices from a short list, and hear it before you save.</td>
    <td width="52" valign="top"><img src="brand/icons/transfer.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Puts callers through</strong><br>To a department, or to a person by name. Each department chooses cold, straight through, or warm, where Keeva asks your colleague first. Callers can press 0 for a person at any time.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/message.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Takes messages</strong><br>When nobody's free, or you're closed, she takes a message and a number to ring back. It waits under Messages to return until someone marks it returned.</td>
    <td valign="top"><img src="brand/icons/knowledge.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Answers from your knowledge</strong><br>Add PDF and Word files, web pages and short notes. Keeva answers from them, gives contact details exactly as written, never made up, and says so when she doesn't know.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/hours.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Books appointments</strong><br>Connect Google Calendar or Microsoft 365 / Outlook. Keeva finds free times, books, moves and cancels appointments during the call, and checks again before booking so nothing is double-booked.</td>
    <td valign="top"><img src="brand/icons/team.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Knows returning callers</strong><br>Keeva knows when a number has called before, checks the name before using it, and knows if their message is still waiting. Callers who give their name are saved to Contacts.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/alerts.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Notices frustrated callers</strong><br>When a caller asks for a person, repeats themselves or sounds upset, Keeva offers a person, or puts them through straight away. The call shows Needs attention on the dashboard.</td>
    <td valign="top"><img src="brand/icons/ai-notice.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Blocks spam and robocalls</strong><br>Block numbers or whole prefixes, keep an allow list, and block from a call in one click. Likely spam is flagged. Blocked callers never reach the AI and don't count as usage.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/transfer.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Waiting audio</strong><br>A hold tone, built-in music or your own audio, with spoken waiting messages, for the organisation or each department. Callers hear it on every transfer and while they wait for the fallback.</td>
    <td valign="top"><img src="brand/icons/answer.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Greets your staff</strong><br>Colleagues ringing from their extension are greeted by first name, however your phone system writes the number. With a PIN, they can have Keevah dial an outside number for them.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/ai-notice.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>AI notice on every call</strong><br>Every call opens with a short recorded notice that the caller is talking to an AI and that the call is transcribed. Reword it if you like; it can't be switched off.</td>
    <td valign="top"><img src="brand/icons/hours.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Opening hours</strong><br>Hours and a time zone for each organisation. Out of hours, Keeva takes a message and tells the caller when you reopen.</td>
  </tr>
</table>

### For your team

<table>
  <tr>
    <td width="52" valign="top"><img src="brand/icons/dashboard.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Live dashboard</strong><br>Who's on the line now, calls and minutes, how calls ended, what callers wanted and your busiest hours, for any dates. Take a live call to your own phone, or send it to the fallback. Light and dark, on desktop and phone.</td>
    <td width="52" valign="top"><img src="brand/icons/transcript.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Call logs and transcripts</strong><br>Every call is logged with its transcript, an AI summary and action items, encrypted on the server. Filter, export to CSV, resend the summary or email a call to a colleague.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/email.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Email summaries</strong><br>A summary of each call goes to the address each organisation chooses, and call notes to the department a caller was put through to. The transcript stays out unless they switch it on.</td>
    <td valign="top"><img src="brand/icons/team.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Members, roles and permissions</strong><br>Invite people by email as an Owner, Admin, Manager, Receptionist or Staff, or make your own roles with just the permissions they need. One login can belong to several organisations. Two-step sign-in, signed-in devices and an audit log of who changed what.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/organisations.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Many organisations</strong><br>Run reception for many organisations from one server. Each has its own receptionist, voice, departments, hours and knowledge, and sees only its own calls.</td>
    <td valign="top"><img src="brand/icons/usage.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Usage and AI cost</strong><br>Calls and minutes for each organisation, month by month, and an estimate of the AI cost for super admins, with CSV downloads.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/pbx.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Webhooks and API</strong><br>Tell your CRM or helpdesk when a call starts or ends, a message is taken, a caller is put through or an appointment is booked, with signed webhooks. API tokens read calls and messages.</td>
    <td valign="top"><img src="brand/icons/transcript.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Caller data requests</strong><br>When a caller asks what you hold about them, find everything by their number or name, download it, or erase it without touching anyone else's. You can also stop recording or transcribing a number.</td>
  </tr>
</table>

### Running Keevah

<table>
  <tr>
    <td width="52" valign="top"><img src="brand/icons/setup.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Setup checklist and test calls</strong><br>Each organisation sees what's done and what's missing. A test call rings a phone through your own line, so you hear exactly what callers hear.</td>
    <td width="52" valign="top"><img src="brand/icons/pbx.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Grandstream and Yeastar</strong><br>Works with Grandstream UCM and Yeastar S-Series systems, connected through Asterisk. Keevah joins your phone system as one extension, and your numbers stay as they are.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/backups.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Backups</strong><br>Encrypted backups daily, weekly or monthly, to a folder, a NAS, a network share or S3-compatible cloud storage, all set up from the dashboard. Back up now, one organisation or everything, and keep or download it. A restore checks every file first.</td>
    <td valign="top"><img src="brand/icons/setup.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Updates and rollback</strong><br>On a Linux server, System health shows each new release and its notes. Update now or at a time you choose, with a backup taken first, and roll back to an earlier version from the dashboard if you need to.</td>
  </tr>
  <tr>
    <td valign="top"><img src="brand/icons/alerts.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Outage alerts</strong><br>Super admins are emailed when the phone service, Gemini, a phone line, the email server or the backups fail, and again when they recover. System health puts problems first.</td>
    <td valign="top"><img src="brand/icons/ai-notice.svg" width="40" height="40" alt=""></td>
    <td valign="top"><strong>Kept private</strong><br>Callers can't talk Keeva out of her instructions, and such calls are marked. Keys, tokens and passwords are taken out of every log line, and transcripts, summaries and messages are encrypted.</td>
  </tr>
</table>

## How it works

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="brand/how-it-works-dark.svg">
  <img alt="How Keevah works: a caller rings your usual number; your Grandstream or Yeastar phone system passes the call to Keevah; Keeva answers, then puts the caller through, takes a message or answers from knowledge; your team sees every call live on the dashboard, with a log, a transcript and a summary by email." src="brand/how-it-works-light.svg">
</picture>

1. **A caller rings your usual number.** Your Grandstream or Yeastar phone system passes the call to Keevah, which is set up on it as one extension.
2. **Keeva answers.** The AI notice plays, then she greets the caller for your organisation, in your chosen voice, and finds out what they need.
3. **She deals with it.** She puts the caller through to the right department, takes a message, or answers from your knowledge.
4. **Your team sees every call.** It shows on the dashboard while it's happening, then in Call logs with the transcript, a summary and action items, and the summary goes out by email.

If something goes wrong, callers still reach a person: when the AI can't be reached, or Keevah's phone service is down, calls go to the organisation's fallback extension, and the super admins are emailed.

Keeva's voice and understanding come from Google Gemini. The dashboard, the call records and the knowledge base stay on the server Keevah runs on.

## Screenshots

Every screenshot uses demo data: the organisations, people and calls in them are made up.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="screenshots/dashboard-group-dark.png">
  <img alt="The group dashboard for three demo organisations over seven days: headline numbers with trend lines, calls per day stacked by organisation, two calls in progress, and the table by organisation." src="screenshots/dashboard-group.png">
</picture>

<sub><strong>Group dashboard.</strong> Three organisations over seven days: headline numbers, calls per day, who's on the line now, and the board by organisation. Demo data.</sub>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="screenshots/call-transcript-dark.png">
  <img alt="A call's transcript in Call logs: the AI notice, the caller asking about a Saturday collection, Keeva answering from the organisation's knowledge, then taking a message." src="screenshots/call-transcript.png">
</picture>

<sub><strong>A call's transcript.</strong> It opens with the AI notice, answers a question about Saturday collections from the organisation's knowledge, then takes a message. Demo data.</sub>

<img alt="The Knowledge page for a demo organisation: a summary of what Keeva knows, Ask Keevah with a sample question, and three documents marked Ready." src="screenshots/knowledge.png">

<sub><strong>Knowledge.</strong> What Keeva knows about an organisation, Ask Keevah to try a question the way a caller would, and the documents she answers from. Demo data.</sub>

<img alt="The Setup page for a demo organisation: all six required steps done, the Test call card with a finished test call, and the optional steps." src="screenshots/setup-test-call.png">

<sub><strong>Setup.</strong> The checklist an organisation works through before real calls, with a finished test call. Demo data.</sub>

<details>
<summary><strong>More screenshots</strong> (9)</summary>
<br>

<img alt="One demo organisation's dashboard: its 24-hour day strip with opening hours and the current time, headline numbers, calls per day, a call in progress, and messages to return." src="screenshots/dashboard-organisation.png">

<sub><strong>One organisation's dashboard.</strong> Its day at a glance on a 24-hour strip, the headline numbers, calls per day and messages to return. Demo data.</sub>

<img alt="The same organisation dashboard at phone width." src="screenshots/dashboard-phone.png" width="320">

<sub><strong>On a phone.</strong> The same dashboard at phone width. Demo data.</sub>

<img alt="A call's details in Call logs: the caller, Message taken, the AI summary, action items, the message left, and Mark as returned." src="screenshots/call-detail.png">

<sub><strong>A call's details.</strong> Who called and why, the AI summary, action items and the message left, with Mark as returned. Demo data.</sub>

<img alt="The Knowledge page's notes, and Couldn't answer: three questions callers asked, with how often and when." src="screenshots/knowledge-couldnt-answer.png">

<sub><strong>Notes and Couldn't answer.</strong> Short facts typed in, and the questions Keeva couldn't answer, ready to answer with a note. Demo data.</sub>

<img alt="Settings, Voice and greeting for a demo organisation: the Settings menu grouped into Receptionist, Routing, Alerts and records, Access, Integrations, Privacy and Platform; the receptionist's instructions and name; the Receptionist voice list set to Kore, Female, Firm, with Preview; and Notice frustrated callers switched on." src="screenshots/settings-voice-and-greeting.png">

<sub><strong>Voice and greeting.</strong> The Settings menu grouped by what you came to do, the receptionist's name, the voice picked from a short list with Preview, and what to do about frustrated callers. Demo data.</sub>

<img alt="Settings, Contacts for a demo organisation, with the Routing group open in the Settings menu: Departments, Staff directory, Dialling out, Contacts and Blocked numbers. Returning callers: recognise returning callers, look back 30 days, save callers as contacts, and the country code for local numbers." src="screenshots/settings-contacts.png">

<sub><strong>Contacts and returning callers.</strong> Keeva recognises numbers that have called before and saves callers who give their name. Demo data.</sub>

<img alt="Usage and AI cost for a month: calls, minutes and estimated cost for each demo organisation, then the cost rates." src="screenshots/usage-ai-cost.png">

<sub><strong>Usage &amp; AI cost.</strong> A month's calls, minutes and estimated AI cost for every organisation, and the rates behind it. Demo data.</sub>

<img alt="System health: the platform's checks, each with its state." src="screenshots/system-health.png">

<sub><strong>System health.</strong> The platform's checks on one page. Demo data, from a demo server.</sub>

<img alt="Outage alerts with nothing open and two resolved incidents from the last 30 days, then Backups with the last nightly backup." src="screenshots/system-alerts-backups.png">

<sub><strong>Outage alerts and backups.</strong> Two resolved incidents from the last 30 days, and the last nightly backup. Demo data.</sub>

</details>

## Editions and download

Keevah comes as a **Preview** package for each system. Download the zip for yours from the [latest release](https://github.com/b34tl86/Keevah/releases/latest), check it against `SHA256SUMS.txt` on the same page, then follow [Getting started](docs/getting-started.md).

| Edition | File on the release page | Dashboard | Answers live calls |
|---|---|---|---|
| Windows | `keevah-<version>-windows.zip` | Yes | Not yet |
| macOS | `keevah-<version>-macos.zip` | Yes | Not yet |
| Linux | `keevah-<version>-linux.zip` | Yes | Yes, with Asterisk set up beside it |

**Preview** means the dashboard runs on all three systems, but answering live calls needs Linux with Asterisk. Built-in Asterisk, with installers for Windows, macOS and Linux, is on the [roadmap](#roadmap) as Next.

The packages aren't signed yet, so Windows and macOS warn you the first time you open Keevah. [Getting started](docs/getting-started.md) shows what to press.

To run Keevah for your business, on your own phone lines, talk to [TechTrust](https://techtrust.ae).

## Roadmap

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="brand/roadmap-dark.svg">
  <img alt="Keevah roadmap. Shipped: v0.9 Group dashboard and reception settings; v1.0 Knowledge base and commercial launch pack; v1.1 to 1.9 Transfers, staff by name and updates; v1.10 to 1.13 Roles, live calls and backups from the dashboard; v1.14 to 1.15 Waiting audio and safer updates; v1.16 Calendars, contacts and integrations. Now: Arabic and other languages on calls; data residency. Next: built-in Asterisk, Keevah Connector and installers for Windows, macOS and Linux, with signed packages; call recording; concurrent call limits; licensing. Later: SMS and WhatsApp messages; themes; signed updates and audited support access; the techtrust.ae product website; the Android app for personal calls." src="brand/roadmap-light.svg">
</picture>

| Version | Milestone | Status |
|---|---|---|
| v0.9 | Group dashboard and reception settings | Shipped |
| v1.0 | Knowledge base and commercial launch pack: usage & AI cost, AI notice, setup checklist and test calls, invites, backups, outage alerts | Shipped |
| v1.1–1.9 | Cold or warm transfers, callers asking for a person by name, staff dialling out, updates from the dashboard | Shipped |
| v1.10–1.13 | Settings a page per job, Receptionist and custom roles, taking a live call, backups to a NAS or the cloud | Shipped |
| v1.14–1.15 | Waiting audio, staff recognition, backing up before an update, rolling back from the dashboard | Shipped |
| v1.16 | Appointment booking, returning callers and Contacts, spam and robocall blocking, frustrated callers, webhooks and API, caller data requests | Shipped |
| — | [Arabic and other languages on calls](https://github.com/b34tl86/Keevah/issues/33) | Now |
| — | [Data residency](https://github.com/b34tl86/Keevah/issues/34): where call data is processed, and in-country options | Now |
| — | Built-in Asterisk, Keevah Connector and installers for Windows, macOS and Linux, with [signed packages](https://github.com/b34tl86/Keevah/issues/9) | Next |
| — | [Call recording](https://github.com/b34tl86/Keevah/issues/32): playback, retention and a notice to callers | Next |
| — | [Concurrent call limits](https://github.com/b34tl86/Keevah/issues/36) per organisation and per server | Next |
| — | [Licensing](https://github.com/b34tl86/Keevah/issues/26): a licence for each Keevah server | Next |
| — | [SMS and WhatsApp messages](https://github.com/b34tl86/Keevah/issues/38) to callers and staff | Later |
| — | [Themes](https://github.com/b34tl86/Keevah/issues/22): your branding, colours and fonts | Later |
| — | [Signed updates](https://github.com/b34tl86/Keevah/issues/10) and [audited support access](https://github.com/b34tl86/Keevah/issues/15) | Later |
| — | techtrust.ae product website | Later |
| — | Android app for personal calls | Later |

Nothing on the roadmap has a date, and plans can change. [ROADMAP.md](ROADMAP.md) says what each step means for you. Have an idea? Share it in [Discussions → Ideas](https://github.com/b34tl86/Keevah/discussions/categories/ideas).

## FAQ

<details>
<summary><strong>Which phone systems does Keevah work with?</strong></summary>
<br>

Grandstream UCM and Yeastar S-Series, connected through Asterisk. Keevah's Asterisk joins your phone system as one extension, and an ordinary inbound route sends calls to it, so your numbers, handsets and colleagues' extensions stay as they are.

</details>

<details>
<summary><strong>Which AI does it use?</strong></summary>
<br>

Google Gemini. Keeva talks to callers through Gemini's real-time voice model, and Gemini also writes each call's summary and searches your knowledge. Super admins choose the models in Settings.

</details>

<details>
<summary><strong>Which languages does Keeva speak?</strong></summary>
<br>

English today. Arabic and other languages are under Now on the [roadmap](ROADMAP.md).

</details>

<details>
<summary><strong>Do callers know they're talking to an AI?</strong></summary>
<br>

Yes, always. Every call opens with a short recorded notice that the caller is talking to an AI and that the call is transcribed. Each organisation can reword it, but the wording must still say both, and it can't be switched off. If a caller asks, Keeva says she's an AI assistant.

</details>

<details>
<summary><strong>Where does our call data go?</strong></summary>
<br>

It stays on the server Keevah runs on: call records, transcripts, summaries, messages, knowledge and settings. Transcripts, summaries and messages are encrypted there, and nightly backups go, encrypted, to a folder or NAS you choose.

The exception is the conversation with Google Gemini. The call's audio goes to Gemini so Keeva can hear and answer, and Gemini gets the text it needs to write the summary and search your knowledge. Summary emails go only to the addresses each organisation chooses.

Each organisation can also have its call history deleted automatically after anything from 30 days to 7 years. When one caller asks what you hold about them, Settings → Privacy finds it, downloads it or erases it. Where Gemini processes call data, and in-country options, are under Now on the [roadmap](ROADMAP.md).

</details>

<details>
<summary><strong>What happens if something goes wrong on a call?</strong></summary>
<br>

The caller reaches a person. If the AI can't be reached, or Keevah's phone service is down, calls go to the organisation's fallback extension, and the super admins are emailed. Callers can also press 0 for a person at any time.

</details>

<details>
<summary><strong>How much does it cost?</strong></summary>
<br>

Talk to [TechTrust](https://techtrust.ae).

</details>

<details>
<summary><strong>Can it answer my mobile?</strong></summary>
<br>

Not yet. An Android app that answers your own mobile calls when you can't is on the [roadmap](ROADMAP.md), under Later.

</details>

<details>
<summary><strong>Can I try it?</strong></summary>
<br>

Yes. The Preview packages run the dashboard on Windows, macOS and Linux: see [Getting started](docs/getting-started.md). Answering live calls needs Linux with Asterisk, and a Grandstream or Yeastar phone system.

</details>

<details>
<summary><strong>Is the source code available?</strong></summary>
<br>

No. Keevah is proprietary software made by TechTrust. This repository is its public home: releases, the roadmap, documentation, and a place to report bugs and share ideas. See [CONTRIBUTING.md](CONTRIBUTING.md).

</details>

## Built by TechTrust

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="brand/keevah-logo-dark.svg">
  <img alt="Keevah" src="brand/keevah-logo.svg" height="40">
</picture>

Keevah is designed and built by [TechTrust](https://techtrust.ae). For pricing, or to run Keevah on your own phone lines, get in touch at [techtrust.ae](https://techtrust.ae).

Questions and ideas go in [Discussions](https://github.com/b34tl86/Keevah/discussions), and bugs in a released package in [Issues](https://github.com/b34tl86/Keevah/issues). Security problems are reported privately: see [SECURITY.md](SECURITY.md). Everyone here follows the [code of conduct](CODE_OF_CONDUCT.md), and [SUPPORT.md](SUPPORT.md) says where to go for what.

<sub>© 2026 TechTrust. All rights reserved. Keevah is proprietary software: this repository holds its releases, roadmap and documentation, not its source code. See [LICENSE](LICENSE). Screenshots use demo data; every organisation, person and phone number in them is made up. Grandstream, Yeastar, Asterisk and Google Gemini are trademarks of their respective owners.</sub>
