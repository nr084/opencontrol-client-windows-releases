<p align="center"><img src="assets/icon.png" width="96" alt="OpenControl" /></p>
<h1 align="center">OpenControl Client</h1>
<p align="center">Your organization’s network · Windows 10 / 11</p>
<p align="center"><a href="README.md">Русский</a> · <b>English</b></p>
<p align="center"><a href="https://github.com/nr084/opencontrol-client-windows-releases/releases/latest">Download 1.0.0</a> · <a href="RELEASE_NOTES.md">What’s new</a> · <a href="SHA256SUMS">SHA256</a></p>

OpenControl connects your PC to a private corporate network through Kerio Control. Your organization supplies the server address and account. This independent client is not an official Kerio/GFI product or a provider of VPN access.

![Main window](assets/connection-en.png)

## Install and connect

Each MSI includes Russian and English. **Russian is the default on first launch**, regardless of the Windows language. Click **EN / RU** to switch; your choice is saved.

| Computer | Download |
|---|---|
| Intel / AMD 64-bit PC | [x64](https://github.com/nr084/opencontrol-client-windows-releases/releases/download/v1.0.0/OpenControl-client-1.0.0-windows-x64.msi) |
| Windows 10, 32-bit | [x86](https://github.com/nr084/opencontrol-client-windows-releases/releases/download/v1.0.0/OpenControl-client-1.0.0-windows-x86.msi) |
| Windows on ARM, including a Windows 11 VM on Mac | [ARM64](https://github.com/nr084/opencontrol-client-windows-releases/releases/download/v1.0.0/OpenControl-client-1.0.0-windows-arm64.msi) |

1. Install the app. Desktop and Start menu shortcuts are created by default.
2. Add a connection in **Profiles**, or import your CFG in **Settings**.
3. Select the profile and turn the switch **ON**. No separate permission checkbox is needed.
4. When prompted, verify the server certificate fingerprint with your administrator before trusting it.

Once connected, the window hides in the tray and a notification identifies the tunnel. A failure reason, such as an incorrect password, appears beside the switch. Hover to read longer messages.

## Window and tray controls

| Feature | How it works |
|---|---|
| Close the window | The X hides the app in the tray, even while disconnected |
| Connection indicator | Green dot with a white rim: connected. Red cross: disconnected |
| Reopen | Click the tray icon or select Open OpenControl |
| Reconnect | Right-click the tray → Reconnect; the old session finishes before the next starts |
| Disconnect or exit | Disconnect ends VPN; Exit also closes the app |
| Traffic totals | Hover over the tray for session Upload / Download; totals also appear in the window |
| Windows startup | Starts in the tray without connecting VPN automatically; disable in Windows Startup Apps if desired |
| Appearance | Light/dark theme, Windows Segoe UI, DPI scaling and multi-size icons; no 3D accelerator required |
| Activity | Connection events, without passwords or packet contents |

Windows may put the icon in its overflow area. Notification visibility depends on Windows settings. After an established connection drops, the client attempts to restore it and retains session traffic totals.

## Profiles and QR

![Profiles](assets/profiles-en.png)

Add, edit and delete connections while VPN is disconnected. Profiles sort by name. Deletion has a separate confirmation button; a profile can be set as default.

Use a password for one session or save it with Windows protection for the current user. Text fields support copy/paste. Password fields accept paste but do not copy or cut hidden passwords.

Move one profile using **Show QR**, **Save QR to PNG**, or **Import QR from PNG**. The format is compatible with OpenControl for Android.

New or changed certificates require confirmation; expired certificates require a separate decision. Trust is remembered for that profile’s specific certificate.

## Kerio import and file synchronization

![Settings](assets/settings-en.png)

**Import CFG…** selects your own file. First launch also offers to review an existing Kerio `user.cfg`. Names, servers, ports, usernames and supported saved D3S passwords are imported. Unsupported passwords need manual entry; certificate trust is not imported.

Duplicates require **Keep existing**, **Replace from file**, or **Keep both**. Normal import leaves the original file unchanged. Up to 100 profiles are supported.

**Export user.cfg** saves all profiles and saved passwords in Kerio format; session-only passwords are excluded. The file contains portable passwords, so treat it as access data. Synthetic re-import is tested; acceptance by the external Kerio client still needs checking.

**Select local user.cfg** links the profile list to a file:

- Edits and deletions synchronize both ways.
- Checks run hourly or with **Sync now**.
- Checks pause while connecting, connected, or editing profiles.
- Conflicting edits ask you to choose a version.
- A missing or malformed file never clears the profile list.
- **Unlink file** preserves both the file and local profiles.

Network paths are unsupported. The file is not uploaded to the cloud.

## Networks outside VPN

![Network exclusions](assets/networks-en.png)

In **Networks**, enter destinations that should use your regular connection, such as `192.168.1.0/24` or `10.0.0.5/32`. These are shared IPv4 exclusions for all profiles, up to 128 entries, applied on the next connection. Per-app routing and IPv6 exclusions are not provided.

## Updates, uninstall and checks

Before updating, choose **Exit** from the tray. This release replaces the previous **1.0.0** files: if 1.0.0 is already installed, uninstall it normally before installing the new MSI. Profiles are preserved.

Uninstall through **Windows Settings → Apps → OpenControl → Uninstall**. The program, service, shortcuts and startup entry are removed; profiles and external CFG files remain. Installation and removal require administrator rights, ordinary operation does not. The service starts with Windows and serves one VPN session at a time.

The Wintun driver is officially signed. Project EXE/MSI files are not yet publisher-signed. Check [SHA256SUMS](SHA256SUMS).

64 automated tests, three architecture builds and MSI content checks passed. Retry after authentication failure was tested with a synthetic Windows pipe; native tray updates were also checked. Full operation on the target ARM VM and a real firewall remains outside these tests. See [VALIDATION.md](VALIDATION.md).

All screenshots contain fictional profiles. This repository publishes installers and documentation; client sources are private. The [protocol library](https://github.com/nr084/opencontrol-protocol) is a separate public project.

[Changelog](RELEASE_NOTES.md) · [Privacy](PRIVACY.en.md) · [Component licenses](THIRD-PARTY-NOTICES.txt)