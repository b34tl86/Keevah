# Getting started with the Preview packages

This guide takes you from download to signing in, on Windows, macOS or Linux.

> **Preview.** The dashboard runs on all three systems. Answering live calls needs Linux with Asterisk beside Keevah, until built-in Asterisk (v1.2, Next on the [roadmap](../ROADMAP.md)). On Windows and macOS you can set Keevah up and look around, but it can't take calls yet.

## What you need

- A computer running Windows, macOS or Linux, with a web browser.
- For calls, summaries and the knowledge base: a Google Gemini API key with access to a real-time voice (Live) model.
- For live calls as well:
  - Linux, with Asterisk 20 LTS or newer on the same machine as Keevah;
  - a Grandstream UCM or Yeastar S-Series phone system, where you can add an extension and an inbound route;
  - a network that lets the Linux machine and the phone system reach each other for calls (SIP and RTP).

## 1. Download

Open the [latest release](https://github.com/b34tl86/Keevah/releases/latest) and download two files into the same folder: the zip for your system, and `SHA256SUMS.txt`.

| System | File |
|---|---|
| Windows | `keevah-<version>-windows.zip` |
| macOS | `keevah-<version>-macos.zip` |
| Linux | `keevah-<version>-linux.zip` |

## 2. Check the download

The checksum proves your zip is exactly the file published on the release page, not damaged or changed on the way. Do this before you open anything.

### Windows

Open PowerShell in the folder with the two files (in Windows 11, right-click an empty part of the folder and choose **Open in Terminal**), then run:

```powershell
$zip = Get-Item .\keevah-*-windows.zip
$expected = ((Select-String -Path .\SHA256SUMS.txt -Pattern $zip.Name -SimpleMatch).Line -split '\s+')[0]
if ((Get-FileHash $zip -Algorithm SHA256).Hash -eq $expected) { 'OK: the checksum matches.' } else { 'STOP: the checksum does not match.' }
```

Keep only one Keevah zip in the folder while you do this.

### macOS

In Terminal:

```bash
cd ~/Downloads
shasum -a 256 -c SHA256SUMS.txt --ignore-missing
```

### Linux

In a terminal:

```bash
cd ~/Downloads
sha256sum -c SHA256SUMS.txt --ignore-missing
```

On macOS and Linux, a good download prints your zip's name followed by `OK`. If you don't see `OK`, don't open the zip. Download it again, and if it still doesn't match, [report it](https://github.com/b34tl86/Keevah/issues/new/choose).

## 3. Unpack and open Keevah

Each zip unpacks to a folder called `keevah`. Inside is the launcher, `keevah.exe` on Windows and `keevah` on macOS and Linux. It starts Keevah and opens the dashboard in your browser at <http://127.0.0.1:8000>.

The packages aren't signed yet, so the first time you open Keevah your system warns you that it comes from an unidentified developer. Go ahead only with a zip whose checksum matched.

### Windows

1. Right-click the zip, choose **Extract All…**, then **Extract**.
2. Open the `keevah` folder and double-click `keevah.exe`.
3. If **Windows protected your PC** appears, choose **More info**, then **Run anyway**.

### macOS

1. Double-click the zip to unpack it.
2. Open the `keevah` folder. Control-click (or right-click) `keevah`, choose **Open**, then choose **Open** again in the warning.
3. On macOS 15 Sequoia and later the warning may have no **Open** button. Choose **Done**, then open **System Settings → Privacy & Security**, scroll down to **Security**, and choose **Open Anyway** beside the message about `keevah`. Confirm with your password or Touch ID.

If macOS then refuses one of the files inside the `keevah` folder, it is still treating the whole folder as downloaded. For a zip whose checksum matched, you can clear that in Terminal (change the path if you unpacked it somewhere else), then open `keevah` again:

```bash
xattr -dr com.apple.quarantine ~/Downloads/keevah
```

### Linux

1. Unpack the zip with your file manager, or in a terminal:

   ```bash
   cd ~/Downloads
   unzip keevah-*-linux.zip
   ```

2. Start Keevah:

   ```bash
   cd keevah
   ./keevah
   ```

3. If you see `Permission denied`, make the launcher executable and try again:

   ```bash
   chmod +x keevah
   ./keevah
   ```

On every system: if your browser doesn't open by itself, open <http://127.0.0.1:8000> on the same computer.

## 4. First-run settings

The first time you open Keevah, it sets itself up in its window and asks three things. Your typing stays hidden for the key and the password.

1. **Your Gemini API key**, from <https://aistudio.google.com/apikey>. You can press Enter to add it later: the dashboard works without one, but Keevah can't answer calls until you add it with `keevah setup`.
2. **The first super admin's email address and full name.** This is the account that runs Keevah and adds organisations.
3. **A password for it**, typed twice: at least 12 characters, with an uppercase and a lowercase letter, a digit and a symbol. It's stored only as a hash and never written to a file.

Then Keevah says it's set up and starts. If you stop it partway through the questions, nothing is saved, and the next start asks again.

### Where Keevah keeps your data

Keevah keeps its settings, keys and data in a folder of your own, never in the program's folder:

| System | Data folder |
|---|---|
| Windows | `%LOCALAPPDATA%\Keevah` |
| macOS | `~/Library/Application Support/Keevah` |
| Linux | `~/.local/share/keevah` (or `$XDG_DATA_HOME/keevah`) |

In it:
- **`keevah.env`** holds Keevah's keys and settings. On macOS and Linux only you can read it. Keep it private.
- **`keevah.db`** is the database.
- Uploaded knowledge, AI notice recordings and logs appear in sub-folders as you use them.

**Back up `keevah.env` and `keevah.db` together.** The data can't be read without the keys. For the same reason, if Keevah finds a database without its `keevah.env`, it won't set itself up again over it.

### Every time after that

Keevah asks nothing. It prints where your data is and the dashboard's address, opens the dashboard, and shows **Press Ctrl+C to stop**. Ctrl+C, or closing the window, stops Keevah cleanly.

Useful options (`keevah --help` lists them all):
- `--port 8001` if something else already uses port 8000. Keevah tells you if it does.
- `--no-browser` to start without opening the dashboard.
- `--data-dir FOLDER` to keep the data somewhere else.
- `keevah setup` to add or change the Gemini API key.

### Updating to a new version

Unzip the new version's package and open its `keevah` as before. Your data folder isn't touched, so your settings, organisations and calls carry over. Back it up first, to be safe.

To start again from nothing, stop Keevah and delete the data folder. That removes everything, and the next start asks the first-run questions again.

### Behind HTTPS

The packages serve the dashboard over plain http on your own computer, so `keevah.env` has `COOKIE_SECURE=false`. If you put Keevah behind HTTPS, change it to `COOKIE_SECURE=true` and restart.

## 5. Sign in

Sign in as the super admin, with the account from the first-run settings above. The first screen is the group dashboard.

To set up your first organisation:

1. **Settings → Organisations → New organisation.** Give it a name, its phone system's address and a fallback extension: the colleague who takes calls when the receptionist can't.
2. **Settings → Organisation → Setup.** The checklist lists what's left, with a link to each setting: the receptionist's name and voice, departments, who gets call summaries, and the test call.
3. **Settings → Users.** Add the organisation's admins and viewers.

For your own account, open **My account** from the menu at the top right, where you can turn on two-step sign-in.

On Windows and macOS, the dashboard and System health say **Live calls are off on this computer**. That's expected, because the Preview packages answer calls only on Linux. On Linux, until Asterisk is connected, System health reports a problem with the phone system; that's expected too.

## Answering live calls

Live calls need Keevah on Linux, with Asterisk 20 LTS or newer on the same machine. Keevah's Asterisk joins your Grandstream UCM or Yeastar S-Series as one extension, and an inbound route on the phone system sends calls to that extension. Your numbers and handsets stay as they are.

Connecting Asterisk and a phone system takes some telephony know-how. For help, talk to [TechTrust](https://techtrust.ae).

Once it's connected, the **test call** on the Setup page proves the whole path: Keevah rings a phone through the organisation's own line, and you hear exactly what a caller hears.

## Getting help

- **Questions:** [Discussions → Q&A](https://github.com/b34tl86/Keevah/discussions/categories/q-a).
- **Bugs in a released package:** [open a bug report](https://github.com/b34tl86/Keevah/issues/new/choose).
- **Sales and commercial support:** [TechTrust](https://techtrust.ae).

Please keep customer data out of anything you post: no callers' names or numbers, transcripts, recordings, passwords or keys.
