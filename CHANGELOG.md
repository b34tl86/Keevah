# Changelog

What's new in each Keevah release, in plain words. Downloads and release notes are on the [releases page](https://github.com/b34tl86/Keevah/releases).

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and Keevah uses [Semantic Versioning](https://semver.org/).

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

[1.0.0]: https://github.com/b34tl86/Keevah/releases/tag/v1.0.0
[0.9.0]: https://github.com/b34tl86/Keevah/releases/tag/v0.9.0
