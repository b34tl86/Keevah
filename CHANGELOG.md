# Changelog

What's new in each Keevah release, in plain words. Downloads and release notes are on the [releases page](https://github.com/b34tl86/Keevah/releases).

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and Keevah uses [Semantic Versioning](https://semver.org/).

## [1.13.0] - 2026-11-10

**Back up now, your way: one organisation or everything, saved or downloaded, labelled and kept.**

### Added
- Back up now lets you choose how the backup is made (#25), on System health → Backups and now on Settings → Backups too.
  - What to include: everything, or one organisation. A backup of one organisation holds its data, its knowledge files and its unsaved call records, without the server's settings or keys and without anyone's password. It can't be restored on its own yet: a restore says so and changes nothing.
  - Where to save it: the backup location, a download to your computer, or both. A download waits on the server for an hour, or until it's downloaded.
  - A label, such as "Before moving to the new server", shown in the list of backups and in the email.
  - Keep this backup: automatic clean-up leaves it alone until you unpin it. Up to 10 backups can be kept.
  - Before it starts, the dialog says how big the backup will be and warns when there isn't room, when one is already running (and offers to follow it) or when one was started in the last 10 minutes.
  - Its progress (preparing, encrypting, saving, with the size so far) shows in the dialog and on the page. Close the dialog at any time: the backup carries on and the page shows how it went.
  - The emails say who started it and its label.
- Settings → Backups lists manual backups with who made them and their label, and kept ones with a pin. Filter the list by All, Scheduled, Manual or Kept, download any backup (encrypted, as it's kept, with its SHA-256 checksum), and Keep or Unpin it.
- The audit log records each manual backup's options and label, every download, and every Keep and Unpin.

### Fixed
- Settings → Backups: a folder Keevah isn't allowed into, such as one inside a home folder, no longer says it "doesn't exist". The message says why and gives the commands to make a folder Keevah can use. A folder Keevah can't write to, or a file instead of a folder, gets its own message too.

### Removed
- The Agent Office developer pages (`/office`, `/agent-office` and `/api/agent-office/*`), a visualiser of local AI coding sessions that was never part of the product and was off in production.

## [1.12.0] - 2026-11-10

**Roles you can shape, calls you can take, backups from the dashboard, and a receptionist that keeps its instructions to itself.**

### Added
- Callers can't get the receptionist's instructions out of it (#7).
  - Its rules now say to keep its instructions, settings, tool names, extensions and routing to itself, and to give knowledge as short answers, never word for word.
  - When a caller asks for the "system prompt", says "ignore your instructions" or similar, the receptionist turns them away politely and is reminded in the moment. The after-call summary also notices reworded attempts.
  - These calls are marked "Asked for instructions" in Call logs, with what the caller said. More filters can show only these calls, and the CSV export has a column for it.
- Send a call in progress to the fallback extension from the dashboard (#16).
  - Open the call in Live calls and choose "Send to fallback". Keeva tells the caller she's putting them through, and the fallback rings while the caller holds.
  - The caller is connected only once someone answers. If nobody does, Keeva comes back and offers to take a message.
  - Turn it on per organisation in Settings → Departments, under Fallback extension; it's off until then. Owners, admins and managers can use it, one person at a time.
  - The call log and the audit log record who did it.
  - Upgrading: the telephony service listens on a new loopback-only port, `TELEPHONY_CONTROL_PORT` (4580 by default).
- One login in several organisations, with a role in each (Owner, Admin, Manager, Staff) and switches for transcripts, export and departments. The members API lives under `/api/tenants/{id}/members`. Every organisation keeps at least one Owner. A new organisation can name its first Owner.
- Settings → Members replaces Users. Invite people with a role and their access (transcripts, export, departments), change their role or access, switch them off, or remove them.
- Organisation switcher in the header, for people in more than one organisation.
- The Organisations list marks organisations that need an owner.
- Accepting an invite shows the organisation first. Someone who already has an account just joins.
- Settings → Platform → Accounts lists every login and how many organisations it belongs to.
- New organisations can invite their first owner.
- Backups are set up from the dashboard (#1): Settings → Backups, for super admins.
  - Where they go: a folder on the server (or an NFS share mounted there), a network share (SMB), or cloud storage (Amazon S3, Wasabi, MinIO and other S3-compatible services). Test connection checks the location can be reached, written to and has room, and a new location is only saved once it passes. Passwords and keys are stored encrypted and never shown again.
  - When: daily, weekly or monthly, at a time in a chosen time zone. A new schedule applies straight away.
  - How many: the last N backups, or those from the last N days.
  - Who hears: emails to chosen addresses (every super admin by default), on every backup or failures only. A location that can't be reached or is full opens its own outage alert.
  - Changing the location never deletes the old backups, and the page offers to copy them to the new one.
- Settings → Backups lists the backups with their time, size and result, and restores one from the list or from an uploaded file. The private key is used once to check the backup and never stored. Keevah then stops, swaps the files in, and starts again, putting the old files back if it doesn't come up.
- Each server has its own id, shown on System health with its edition ("Self-hosted"). It's never in a backup, so a future licence can't travel with one.
- Moving to a new server: restoring a backup made elsewhere brings the data, re-encrypted to the new server's key, but not the old server's passwords and keys. System health lists what to enter again. The README has the steps.
- The packaged app can restore a backup: from the dashboard, or with `keevah restore FILE`.
- A Receptionist role, and roles of your own (#17).
  - Receptionist: the dashboard, live calls, call logs and transcripts, and marking messages returned. They can take a live call or send it to the fallback, but can't open settings, people, knowledge or usage, and can't export.
  - Settings → Roles & permissions (Owners and Admins) lists the roles and how many people have each. Built-in roles can't be changed, only duplicated. A new role starts from any role or from empty; tick what it can do, each permission explained in a line.
  - Nobody can make or give a role with a permission they don't have themselves, and permissions you don't have are shown but can't be ticked. A role someone has can't be deleted until they're moved to another.
  - Changes to a role apply to everyone with it straight away.
  - Pick the role when inviting someone or on their Members entry, which shows what they can do.
  - The audit log records roles made, changed and deleted, and role changes, with the permissions before and after.
- Take call: take a call in progress to your own phone from the dashboard (#17).
  - Open the call in Live calls and choose "Take call". Keeva tells the caller she's putting them through, your extension rings, and the caller is connected once you answer. If you don't, Keeva takes a message.
  - One person at a time: whoever presses second sees "Already taken by" and the name.
  - Each person has an extension in each organisation, set on their Members entry or on My account ("My extension in …"). Without one, the dashboard asks for it first.
  - It follows the same switch as Send to fallback; with it off, both buttons are hidden.
  - The call log shows "Taken by Sam Lee (Receptionist) at 10:42", and the audit log records it.

### Changed
- Permissions: "manage members" is now two, "Invite people" and "Change people's roles", and there's a new "Manage roles and permissions". Owners and Admins have all three, as before. Managers can now take live calls to their own phone.
- Someone who can view knowledge but not edit it sees it read only.
- API: members take `role_id` (a built-in's `role` key still works) and an `extension`, and return `role_id`, `role_name`, `full_access`, `capabilities`, `extension` and `can_resend`; `role` is the built-in's key or `custom`. `/auth/me` adds `role_name` and `extension`. New: `GET /api/permissions`, `/api/roles`, `POST /api/live-calls/{id}/take`, `GET /api/live-calls/options` and `PUT /auth/organisations/{id}/extension`.
- Menus, pages and buttons follow what each person may do in the organisation they're using.
- Invites: someone who already has a Keevah account gets "You've been added to {organisation}" and joins without choosing a new password. Each organisation's invite link works on its own, and links sent before the upgrade still work.
- `/api/users` is now for operators only: accounts across the platform.
- Audit log: each line shows the role the person had at the time, and an organisation's log also shows its current members' sign-ins.
- Staff can now mark messages returned, and undo it. Viewers, who became Staff, could only read the list. This is the one permission that widens in this release.
- API: `/auth/me` adds `is_super_admin`, `memberships` and `active` (the organisation in use, with its capabilities and departments). It takes `?tenant_id=`. `role`, `tenant_id` and `tenant_name` are deprecated and will be removed.
- Calls and the dashboard follow each person's access: someone limited to some departments sees only those departments' calls, counts and live calls (calls with no department aren't shown to them), and someone without the transcripts switch sees the summary but not the transcript.
- A backup keeps the settings file's secrets in a separately sealed part, restored only on the server the backup came from.
- Backups no longer need settings in `.env`. Servers that use `BACKUP_DIR` and the other `.env` settings keep working until the settings are saved in the dashboard.

## [1.11.0] - 2026-11-09

**System health shows what needs a look first.**

### Changed
- The title says what needs a look ("1 problem, 3 to look at"), and problems and warnings come first. Working checks follow in a compact list, then the ones not set up.
- On wide screens the page is two columns: the checks and outage alerts on the left, and the server's version, updates and backups on the right.

## [1.10.1] - 2026-11-09

**The Settings menu is easier to scan.**

### Changed
- Group titles stand out from the pages under them: full-strength text, a line between groups, and each group's pages indented beneath its title. The group you're in is marked in yellow, and screen readers name the group as you move into it. ([#18](https://github.com/b34tl86/Keevah/issues/18))
- The menu folds its groups. Only the group of the page you're on is open, and clicking another group's title opens that one instead, so the whole menu fits on the screen without scrolling.

## [1.10.0] - 2026-11-06

**Settings is a page per job, instead of one long page.**

### Changed

- **Short settings pages, grouped by what you came to do.** The long Reception settings page is now ten short pages, and the Settings menu groups them:
  - **Receptionist:** Voice and greeting, AI notice, Knowledge, Opening hours, Call timing.
  - **Routing:** Departments (now with the fallback extension), Staff directory, Dialling out, Dial-out contacts.
  - **Alerts and records:** Email summaries, Data retention (with the Danger zone), Usage.
  - **Access:** Users, Phone system (the organisation's name, the PBX connection and its wiring).
- **Each page has its own Save button,** and leaving with unsaved changes asks first. If a save is stopped by a setting on another page, the message names that page and links to it.
- **Setup shows how far along you are** ("2 of 6") beside it in the menu until the required steps are done.
- **Old links still work.** Bookmarks and links to Reception settings open the page that has that setting now, and the settings search points at the new pages.
- "Usage & AI cost" is now **AI cost**, and Contacts is **Dial-out contacts**.

## [1.9.1] - 2026-11-06

**Fixes across the dashboard, and calmer motion.**

### Fixed

- **The Users page no longer crashes** when it lists someone whose role the dashboard didn't recognise. The role now shows as a plain word.
- **A call's details panel opens at its full width**, and so does a link's pages panel in Knowledge. They had been squeezed to half their width, so buttons wrapped and long organisation names broke over several lines.
- **Server status no longer shows a double line** along its right edge.

### Changed

- **Calmer motion.** Side panels slide in quickly and settle, and close a little faster. The sidebar collapses with the same smooth ease. The page behind a panel or dialog is dimmed instead of blurred, so you can still read it. With reduced motion switched on, loading spinners keep turning (slower) instead of looking frozen.
- **On phones the fifth headline tile spans the full width** instead of sitting alone in half a row.

## [1.9.0] - 2026-11-06

**Email a call to colleagues, safely.**

### Added

- **Email to a member.** Each call's page in Call logs has an Email to a member button for admins. Pick colleagues from your organisation's members and choose what to include: caller details, summary, transcript. There's no box to type an address, so a call can't be sent outside your organisation. The transcript only goes to people allowed to read transcripts. Keevah sends only when your email server uses encryption, gives each person their own email, and records who got what in the audit log.

## [1.8.0] - 2026-11-06

**Resend a call's summary email from Call logs.**

### Added

- **Resend summary email.** Each call's page in Call logs has a Resend summary email button for admins. It sends the call's summary to your organisation's summary address again, even for a call the email setting skipped. If it can't send, it says why: no address set, no email server, or the server refused the message. Every resend is recorded in the audit log.

## [1.7.0] - 2026-11-06

**Updates from the dashboard work with a private GitHub repository.**

### Added

- **GitHub access for updates.** If your copy of Keevah comes from a private GitHub repository, enter a GitHub token in System health → Updates → GitHub access. A fine-grained token with read-only access to the code is enough. Keevah tries it with GitHub before saving it, keeps it encrypted, and only ever shows its last four characters.

### Changed

- **A clearer message when GitHub says no.** If GitHub turns the server away, System health now says the repository is private and points you to the new setting, instead of asking you to check the internet connection.

### Upgrading

- A server that can't reach a private repository yet needs this one update by hand. After that, enter the token and update from the dashboard as usual.

## [1.6.0] - 2026-11-05

**Keevah knows your staff when they call in, and can dial out for them.** Staff ringing from their own extension are greeted by name, and can ask Keevah to call a UAE number for them, protected by a PIN.

### Added

- **Staff are greeted by name.** When someone calls from an extension on your staff list, Keevah says hello by their first name. On a shared extension she asks who's calling.
- **Keevah can dial out for your staff.** Turn it on in Settings → Reception settings → Call handling. Staff calling from their extension can then ask Keevah to call a UAE mobile or landline, or a saved contact by name, and she puts them through.
- **A PIN for each person.** Set it in Reception settings → Staff. Staff key it in on the phone's keypad; Keevah never hears it. Wrong PINs stop dialling out, and repeated wrong PINs lock it for an hour.
- **Only UAE numbers.** International, premium-rate and emergency numbers are never dialled.
- **A contact list.** Settings → Contacts keeps every number your staff have dialled, with the name they gave, so next time they can just say "call Ahmed at Emaar". Admins can add, edit and remove contacts.
- **Clear records.** Call details show who dialled which number, and every dial-out and PIN change is in the audit log.

### Upgrading

- Dialling out is off until you turn it on. Your phone system must let Keevah's extension make outside calls; some systems also need a digit, such as 9, for an outside line, which you can enter in the same settings.

## [1.5.1] - 2026-11-05

**A fix for warm transfers.**

### Fixed

- **When a colleague hung up first, the caller heard the fallback extension ring.** After a warm transfer, if your colleague ended the call before the caller did, Keevah sent the caller on to the fallback extension instead of ending the call. The call now ends as it should. Nothing on your phone system needs changing.

## [1.5.0] - 2026-11-05

**Keevah updates itself from the dashboard.** Super admins can install new releases from System health, and every setting can be found with a search.

### Added

- **Update Keevah from the dashboard.** System health → Updates shows the newest release and what's in it. Install it now, or schedule it for a quiet hour. A backup is taken first when backups are set up, and if the update fails, the version you had is put back. Super admins see a note on the dashboard when a release is out.
- **Search settings.** Type what you're looking for at the top of the Settings menu, or press Ctrl+K (⌘K on a Mac) anywhere: "voice", "opening hours", "SMTP". Pick a result to go straight to that setting.

### Upgrading

- Updating from the dashboard works on servers set up with the installer. Install this release the usual way once; later releases can then be installed from System health → Updates.

## [1.4.0] - 2026-11-05

**Callers can ask for a person by name.** Keevah now knows your staff, not only your departments.

### Added

- **A staff list.** In Settings → Reception settings → Staff, add each person's name, extension and department, up to 200 people. Names can be in any language, and two people can share an extension.
- **"Can I speak to John?"** During opening hours, Keevah puts the caller through to the person they ask for. If two people share the name, she asks which one. If nobody on the list matches, she offers a department or a message.
- **People follow their department's settings.** A person in a department is transferred the way that department is set up, Cold or Warm, with its call notes. On a warm transfer, Keevah asks the person by name whether they'll take the call. Someone with no department gets a warm transfer and no notes.
- **When the person can't take the call,** Keevah offers their department instead, or a message for them. The department is only rung if the caller agrees.
- **Call logs and the dashboard show people.** Call details read "Put through to John Smith (Billing)", and the dashboard has a new "Put through to people" list.
- **Install on a Linux server with one command.** The installer sets everything up without asking questions, then you finish in the browser: the first administrator, the Gemini key and your first organisation.
- **The Gemini key and the phone system wiring are entered in the dashboard,** so changing them no longer means editing files on the server.

### Fixed

- **Warm transfers could hang up on every colleague** when the Gemini key was entered in the dashboard rather than on the server.

### Upgrading

- If you added people as departments to get around the department limit, move them to Staff by hand.

## [1.2.0] - 2026-10-27

**Groundwork for roles in each organisation.** People now belong to organisations through memberships, with four roles: Owner, Admin, Manager and Staff. The pages look the same, and nobody gains a permission. The Members page, where you manage this, comes in a later release.

### Changed

- **Everyone moves into a membership on upgrade.** Admins become Admin, and each organisation's longest-serving active admin becomes its Owner. Viewers become Staff, keeping transcripts and without export, as today.
- **Every organisation keeps an Owner.** Switching off the only Owner, or making them a viewer, is refused until someone else is made an Owner.
- **Signing in needs an organisation you can use.** Your membership there must be on and accepted, and the organisation must be on. Switching an organisation off now blocks only that organisation's people; anyone who also belongs to another organisation can still sign in there.
- **Deactivating someone on the Users page removes their access to that organisation,** and switching them back on restores it.
- **An invite link joins only the organisation it names.**
- **"Require two-step sign-in for admins" now covers every Owner and Admin.**

### Upgrading

- Back up before upgrading: on first start, Keevah moves everyone into memberships. The move runs once and is recorded in the audit log.

## [1.1.0] - 2026-10-27

**Cold or warm transfers, per department.** Choose for each department whether Keeva puts callers straight through, or asks your colleague first.

### Added

- **Cold or warm, per department.** In Settings → Departments, each department has a Transfer choice. **Cold** puts the caller straight through, which suits ring groups, queues and menus. **Warm** means Keeva asks your colleague first. Existing departments start as Warm, so nothing changes until you edit them.
- **Colleagues answer out loud.** On a warm transfer, Keeva tells the caller she's checking and plays a soft hold tone. She rings your colleague, waits for them to speak, says who's calling and why, and asks whether they'll take the call. Only a yes puts the caller through. If the answer is no, or nobody picks up, Keeva comes back and offers to take a message. She's built to recognise voicemail, recorded menus and queue messages and to leave no caller details there; for lines a recording may answer, Cold is the safer choice.
- **Call notes by email.** Each department can have a notes address, and you choose when notes go: Always, Ask the colleague, or Never. Notes arrive after the call, with the transcript only if your organisation includes transcripts.
- **One try per department.** A department that didn't take the call isn't rung again in the same call.
- **Call logs show each transfer:** for example "Sales didn't take it · Support no answer · message taken".

### Upgrading

- If Keevah answers calls on your phone system, warm transfers need a new step added to Asterisk. Until it's added, warm transfers take a message instead, and nobody is put through. Talk to [TechTrust](https://techtrust.ae) or your installer.

## [1.0.2] - 2026-10-27

**Steadier backups, invites and knowledge.** A set of fixes found in our own reviews.

### Fixed

- **Backups check there's room first,** and stop before writing anything if a disk is too full, saying which one. Network drives that don't report their size are no longer refused.
- **"Back up now" isn't used up by a refusal:** pressing it while a backup is already running doesn't start the ten-minute wait.
- **Restoring a backup** puts the database back under its own name, whatever its file extension.
- **Invite links and sign-in codes work exactly once,** even if two people or two tabs use the same one at the same moment. Invite links are read exactly as sent.
- **Saving a knowledge note no longer hangs when Gemini is down:** it gives up after 14 seconds and says so, and an edit keeps the old note.
- **More Word files can be added to the knowledge base,** including files that store their text under an unusual name. A spreadsheet or slide deck renamed to .docx is still refused.
- **Reading picks up again after a restart:** documents left on "Reading…" are read again, one at a time, and one that stops Keevah twice is marked as failed rather than tried for ever.
- **Test calls refuse "0000" too,** like every other emergency number, for everyone.

## [1.0.1] - 2026-10-27

**The first downloads, and tidier wording.** Keevah now comes as a Preview package for Windows, macOS and Linux, and a dozen small things callers hear and the dashboard shows have been put right.

### Added

- **Preview packages for Windows, macOS and Linux.** Each release has a zip per system (Windows x64; macOS on Apple silicon, macOS 11 or later; Linux x64 with glibc 2.35 or later, such as Ubuntu 22.04 and Debian 12) and a `SHA256SUMS.txt` to check your download. Nothing else needs installing. The dashboard runs on all three; answering live calls needs Linux with Asterisk.
- **The `keevah` launcher.** The first start asks for a Gemini API key (you can add it later) and creates the first super admin; after that it starts Keevah and opens the dashboard. Your data stays in a folder of your own, so updating never touches it. See [Getting started](docs/getting-started.md).
- **Open-source notices** in every package, in `THIRD-PARTY-NOTICES.txt`.
- On Windows and macOS the dashboard says **Live calls are off on this computer**, rather than reporting a fault.

### Changed

- **The standard AI notice reads better:** "Hello, you're through to Keeva, the AI assistant at Harbourline Logistics. This call is transcribed." Organisations on the standard wording hear it from their next call; Keeva reads it aloud on that first call while the recording is made.

### Fixed

- **Names ending in "s" sound right:** "Harbourline Logistics'", not "Harbourline Logistics's", in the AI notice, in what Keeva says, and on screen. A name that already ends in "'s" is left as it is.
- **Searching for a phone number you copied from the screen finds the call**, with or without spaces and dashes.
- **A new organisation's usage** begins in the month it joined, not with a year of empty months.
- **On the dashboard:**
  - the calls chart's scale runs in whole, even steps;
  - a near-empty day shows the plain difference ("↑ 5 calls") instead of a huge percentage, and the average call's change reads in minutes and seconds;
  - phone numbers are grouped ("+971 50 555 0101") and never break across lines;
  - a call's reason has one name everywhere ("Billing question");
  - transcripts show the receptionist's name;
  - super admins see the time zone beside each organisation's last call;
  - on a phone, the header's controls fit in two rows.
- **On the Test call card,** "Read the call" now looks like the link it is.

## [1.0.0] - 2026-10-26

**The knowledge base and the commercial launch pack.** Keeva now answers callers from each organisation's own material, and Keevah has what an operator needs to sell it and run it as a business.

### Added

**Knowledge base**

- **Documents, web pages and notes.** Each organisation adds PDF and Word files (up to 20 MB each, 50 in all), web pages with the pages beneath them (up to 10 links, 200 pages each), and short typed notes (up to 1,000 characters each, 100 in all). A note wins over a document that says something different, so it's the quick way to correct one.
- **Keeva looks things up on calls.** Asked about products, services, prices, policies or opening times, she checks the knowledge base and answers in a sentence or two. When she can't find the answer, she says so and offers to put the caller through to Sales or a colleague, or to take a message. An organisation with no knowledge gets the receptionist as before.
- **Couldn't answer:** the questions Keeva couldn't answer in the last 30 days, with how often each came up. It keeps the question only, never who asked. Answer one with a note, or dismiss it.
- **Ask Keevah:** ask a question the way a caller would, and see the answer and where it came from before any caller asks.
- **Plain states for every source:** Ready, Read with gaps, Couldn't read or Reading…. **Update** reads a web page again, and keeps the pages read before if that fails.

**Commercial launch pack**

- **Usage for each organisation:** calls and minutes for this month and the last 12, counted on the organisation's own calendar. Test calls are never counted.
- **AI cost estimate** for super admins: calls, minutes and an estimated AI cost for every organisation in any month, with totals and a CSV download. New rates apply from the month they're saved and never rewrite earlier months. It's an estimate, not a bill, and organisations' own admins never see it.
- **The AI notice.** Every call opens with a short notice, recorded in the receptionist's voice, that the caller is talking to an AI and that the call is transcribed. Admins can reword it, listen to it and reset it. It can't be switched off.
- **The transcript in summary emails** is now a choice for each organisation, off by default.
- **A setup checklist** for every organisation: phone system wiring, the phone system connection tested, a named receptionist with a voice, a department, someone to receive call summaries, and a test call, with opening hours and knowledge as optional extras. Admins see "Finish setting up Keevah" on their dashboard until it's done.
- **Test calls.** From the Setup page, Keevah rings a number or extension through the organisation's own line, so you hear exactly what a caller hears. It checks first that the line really leads to that organisation. Test calls are marked Test in Call logs and never counted as usage.
- **Invites by email.** People set their own password from a link that works once and lasts 72 hours.
- **Nightly encrypted backups** to a folder or NAS you choose: the database, the knowledge files and the server's settings, encrypted so that only a key you keep off the server can open them. A restore checks every file before it puts anything back.
- **Outage alerts.** Super admins are emailed when the phone service, Asterisk, Gemini, an organisation's phone line, the email server or the backups fail, and again when they recover. A line that keeps dropping and coming back sends one "Down" and one "Resolved". System health lists the last 30 days and can send a test alert.
- **Clear history and Remove organisation** for super admins, in a Danger zone that asks for the organisation's name to be typed first.

### Changed

- **Summary emails leave out the transcript** for every organisation, existing ones included, unless an admin switches it back on. The email still carries the summary, the action items and any message, and the whole conversation is always in Call logs.
- **Every call now opens with the AI notice.** Callers hear a few seconds of recorded speech before the receptionist's greeting. Organisations without their own wording get the standard one, so nothing needs setting up.

### Security

- When Keevah reads a website for the knowledge base, it stays on that site, respects robots.txt, refuses internal and private addresses, and connects only to the address it checked.
- Uploads must really be PDF or Word files, and Word files built to unpack into something enormous are refused.
- Test calls never ring emergency numbers, however they're dialled. An organisation's admins can ring only extensions and local numbers.
- Secrets are never shown in settings or in error messages.
- CSV downloads can't carry spreadsheet formulas, even ones hidden behind spaces.

## [0.9.0] - 2026-10-25

**The group dashboard and reception settings.** The first release published here.

### Added

**The dashboard**

- **One dashboard** for the whole group and for each organisation, for any dates: Today, Yesterday, 7 days, 30 days or a range from the calendar. The dates are kept in the address, so a bookmark opens the same view.
- **Headline numbers:** calls received, handled by the receptionist, hung up early, minutes on the phone and the average call, each compared with the time before and drawn as a small trend line.
- **Calls per hour or per day**, stacked by organisation. Press a name in the legend to hide it.
- **Who's on the line now**, with each call's organisation.
- **A table by organisation:** local time, open or closed, today's 24-hour strip, calls, calls after hours, messages and more. Sort it by any number.
- **Busiest times** by weekday and hour, **what callers wanted**, **how calls ended**, and **who was put through**, by department.
- **Messages to return:** the newest messages nobody has rung back yet, with the number to ring and "Mark as returned".
- **Whether calls are being answered**, beside the dashboard's title, and server status with what needs fixing. Super admins can show an organisation's staff their own status, in plain words.
- **A new look:** a charcoal sidebar with a yellow "you are here" bar, board-style tables and Fira Sans, in light and dark themes that meet WCAG AA contrast.

**Settings**

- **One Settings area** for every organisation and for the platform.
- **Opening hours and a time zone** for each organisation. Out of hours the receptionist takes a message and says when the office reopens.
- **Call handling:** how long a department's phone rings on a transfer, the longest call, and when to check on a silent caller.
- **Ten voices**, five female and five male, with a sample of each, and a **name** for the receptionist.
- **Data retention:** keep call history for ever, or for anything from 30 days to 7 years.
- **The email server and recipients:** the mail server is set once, and each organisation chooses who gets its call summaries.
- **AI models** chosen in the app, with a button to check they still work.
- **Sign-in security:** password rules, how long people stay signed in, and whether admins must use two-step sign-in.

**Your account**

- **Two-step sign-in** with an authenticator app and one-time recovery codes.
- **Signed-in devices** by name ("Chrome on macOS"), signing out any of them, and your recent activity.
- With an email server set up: **Forgot password?** by email, and a notice whenever your password, email address or two-step sign-in changes.
- Change your own name, phone number and email address.

**Calls**

- **Press 0 for a person** at any time.
- **Silent callers** are asked whether they're still there, then the call ends politely.
- **Long calls carry on** when Gemini closes its connection, without greeting the caller again.
- **A busy Gemini is tried again** while the caller hears ringing, not silence.
- **Every call records how it ended.**
- **An hourly tally** keeps the dashboard's numbers when old calls are deleted.

### Changed

- If Keevah's phone service stops in the middle of a call, the caller goes to the fallback extension instead of being cut off.
- Times are shown in each organisation's own time zone on every page and in summary emails.

### Fixed

- The dashboard no longer scrolls sideways on a laptop screen.
- Each voice sample now plays in its own voice.

### Security

- In production, Keevah won't start while the example secrets are still in place.

[1.1.0]: https://github.com/b34tl86/Keevah/releases/tag/v1.1.0
[1.0.2]: https://github.com/b34tl86/Keevah/releases/tag/v1.0.2
[1.0.1]: https://github.com/b34tl86/Keevah/releases/tag/v1.0.1
[1.0.0]: https://github.com/b34tl86/Keevah/releases/tag/v1.0.0
[0.9.0]: https://github.com/b34tl86/Keevah/releases/tag/v0.9.0
