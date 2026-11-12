# Keevah roadmap

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="brand/roadmap-dark.svg">
  <img alt="Keevah roadmap. Shipped: v0.9 Group dashboard and reception settings; v1.0 Knowledge base and commercial launch pack; v1.1 to 1.9 Transfers, staff by name and updates; v1.10 to 1.13 Roles, live calls and backups from the dashboard; v1.14 to 1.15 Waiting audio and safer updates; v1.16 Calendars, contacts and integrations. Now: Arabic and other languages on calls; data residency. Next: built-in Asterisk, Keevah Connector and installers for Windows, macOS and Linux, with signed packages; call recording; concurrent call limits; licensing. Later: SMS and WhatsApp messages; themes; signed updates and audited support access; the techtrust.ae product website; the Android app for personal calls." src="brand/roadmap-light.svg">
</picture>

Where Keevah is, and where it's heading.

- **Shipped:** in a release you can download.
- **Now:** what we're working on.
- **Next:** what we're working towards after that.
- **Later:** what we mean to do in time.

Nothing here has a date or is a promise. The order and the details can change as we learn from the people who use Keevah. What has shipped is in the [changelog](CHANGELOG.md).

Follow along on the **Keevah Roadmap** board under this repository's [Projects](https://github.com/b34tl86/Keevah/projects) tab, and tell us what you need in [Discussions → Ideas](https://github.com/b34tl86/Keevah/discussions/categories/ideas). A 👍 on an idea that's already there counts too.

## Shipped

### v0.9 · Group dashboard and reception settings

One dashboard for the whole group and for each organisation: calls and minutes, who's on the line, busiest times, what callers wanted and messages to return. One Settings area for opening hours, call handling, voices, data retention, the email server and sign-in security, and two-step sign-in for everyone.

### v1.0 · Knowledge base and commercial launch pack

Keeva answers callers from each organisation's own documents, web pages and notes, and lists the questions she couldn't answer. The launch pack adds what you need to run Keevah as a business: usage & AI cost, the AI notice on every call, a setup checklist with test calls, invites by email, nightly encrypted backups and outage alerts.

### v1.1 to 1.9 · Transfers, staff by name and updates

Each department chooses how Keeva puts callers through: cold, straight through, or warm, where she checks with the colleague first. Callers can ask for a person by name, and colleagues ringing from their own extension are greeted by name and, with a PIN, can have Keevah dial an outside number. People join organisations with a role in each. A Linux server installs with one command and is set up in the browser, and Keevah updates itself from the dashboard. Settings has a search box, and a call's summary can be resent or emailed to a colleague.

### v1.10 to 1.13 · Roles, live calls and backups from the dashboard

Settings became a page per job, grouped by what you came to do. One login can belong to several organisations, with Owner, Admin, Manager, Receptionist and Staff roles, or roles of your own. From the dashboard, take a live call to your own phone or send it to the fallback extension. Backups are set up from the dashboard, to a folder, a NAS, a network share or S3-compatible cloud storage, and you can back up one organisation or everything on demand, then download or keep it. Callers can't talk Keeva out of her instructions.

### v1.14 to 1.15 · Waiting audio and safer updates

Callers hear a hold tone, built-in music or your own audio while they wait, with spoken waiting messages, on every transfer. Staff are recognised however your phone system writes their number. Keeva gives contact details exactly as your website has them. Updates take a backup first, and you can roll back to an earlier version from the dashboard. Keys, tokens and passwords are kept out of the logs.

### v1.16 · Calendars, contacts and integrations

Keeva books, moves and cancels appointments in Google Calendar and Microsoft 365 / Outlook during the call. She knows returning callers, and callers who give their name are saved to Contacts. Spam and robocalls are blocked before they reach the AI. Frustrated callers are offered a person, and the call shows Needs attention. Webhooks and an API connect Keevah to your CRM or helpdesk, and Settings → Privacy finds, downloads or erases one caller's data on request.

## Now

### Arabic and other languages on calls

Keeva answering callers in Arabic, and in other languages, as well as English. Follow [#33](https://github.com/b34tl86/Keevah/issues/33).

### Data residency

Saying plainly where call data is processed, and options to keep it in your country. Follow [#34](https://github.com/b34tl86/Keevah/issues/34).

## Next

### Built-in Asterisk, Keevah Connector and installers for Windows, macOS and Linux

Keevah brings its own Asterisk, so there's no separate phone server to build, and the Keevah Connector links your phone system to Keevah. Guided installers for Windows, macOS and Linux take over from today's Preview zips, with live calls on all three systems, and the packages are signed so Windows and macOS no longer warn you ([#9](https://github.com/b34tl86/Keevah/issues/9)).

### Call recording

Recording calls, with playback on the call's page, how long recordings are kept, and a notice to callers. Follow [#32](https://github.com/b34tl86/Keevah/issues/32).

### Concurrent call limits

A limit on how many calls each organisation, and each server, takes at once, so a burst of calls can't overload the server or run up the AI cost. Follow [#36](https://github.com/b34tl86/Keevah/issues/36).

### Licensing

A licence for each Keevah server. Follow [#26](https://github.com/b34tl86/Keevah/issues/26).

## Later

### SMS and WhatsApp messages

Confirmations for callers, and alerts for your team, by SMS and WhatsApp as well as by email. Follow [#38](https://github.com/b34tl86/Keevah/issues/38).

### Themes

Your own branding, colours and fonts on the dashboard, and ready-made themes. Follow [#22](https://github.com/b34tl86/Keevah/issues/22).

### Signed updates and audited support access

Keevah checks itself at start-up and installs only signed updates ([#10](https://github.com/b34tl86/Keevah/issues/10)), and when TechTrust needs to look at your server for support, you allow it and every step is recorded ([#15](https://github.com/b34tl86/Keevah/issues/15)).

### techtrust.ae product website

A home for Keevah on techtrust.ae: what it does, how to get it, and where to find help.

### Android app for personal calls

Keeva will answer your own mobile calls when you can't.
