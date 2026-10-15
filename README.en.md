<p align="center"><img src="assets/icon.png" width="104" alt="OpenControl" /></p>
<h1 align="center">OpenControl for Windows</h1>
<p align="center">Your corporate network · Windows 10 / 11</p>
<p align="center"><a href="README.md">Русский</a> · <b>English</b></p>

An independent Kerio Control VPN client built on the OpenControl Protocol Library.
Your organization’s administrator supplies the private server address and account.
This project does not provide VPN servers or access credentials.

## Installation

[Download MSI](https://github.com/nr084/opencontrol-client-windows-releases/releases).
Find your system type in Settings → System → About:

| System | Package |
|---|---|
| Windows 10/11, 64-bit Intel/AMD | `x64` |
| Windows 10, 32-bit | `x86` |
| Windows 10/11, ARM64 | `arm64` |

One MSI per architecture, with a Russian installer. Both languages are available in
the app via RU/EN. Windows 11 has no 32-bit edition; use x64 or ARM64. Administrator
permission is required. Close the client before upgrading or uninstalling.
The installer includes official signed Wintun 0.14.1; the adapter is created on connection.
Start menu and desktop shortcuts are installed by default for all users.

The project EXE/MSI do not yet have publisher Authenticode signatures. This is
separate from the valid WireGuard LLC signature on the included driver. Verify SHA256SUMS.

## First connection

1. Open Profiles and enter name, server, port (usually 4090), username and password.
2. Enable the separate checkbox to retain the password, then save the profile.
3. Read the traffic disclosure on the Connection tab and click Connect.
4. When no trusted certificate is configured, the client automatically retrieves it
   and opens a confirmation. Verify SHA-256 with your administrator through a trusted
   channel and confirm trust: connection continues automatically. No further prompt
   is needed while that certificate remains valid and unchanged. Alternatively,
   supply a trusted CA in PEM format.

Expired certificates require separate explicit consent bound to their exact SHA-256.
Changed certificates stop the connection and require a new review. Certificates
that are not yet valid remain rejected. No password is sent before trust is confirmed.
Manual certificate inspection remains available in Profiles.

## Tray and display scaling

After a successful connection the window automatically hides to the system tray.
A green check means VPN is connected; a red cross means disconnected, including
reconnection attempts. Left-click opens the window. Right-click offers Open OpenControl,
Disconnect and Exit. Exit disconnects VPN before closing. If the tray icon is
unavailable, the window stays visible.

The interface uses PerMonitorV2 to scale text and controls when moving between
monitors with different DPI. Status icons are rendered for the display scale.
Headless RU/EN rendering was checked at 100%, 125%, 150% and 200%; physical mixed-DPI
monitor acceptance remains pending.

## Features

- Android-compatible profile QR import/export (PNG); exported QR contains the password.
- Multiple profiles, default profile and user-scoped Windows DPAPI password storage.
- Russian and English UI, light/dark themes and the Android client’s icon.
- TLS, encrypted UDP, key rotation and replay protection.
- Repeated ROUTES without resetting keys or replacing the adapter for unchanged routes.
- Persistent reconnection after the first successful connection, until Disconnect.
- Traffic counters and bounded state-only activity history; no packet or password logs.
- No split-tunneling controls: no app selection or user network exclusions.
  The corporate server specifies VPN routes.

## Initial release limits

0.2.0 is a preview. Automated tests and builds do not substitute for testing against
your Kerio Control. Live corporate-server and physical ARM64-device acceptance are
not yet confirmed. See [validation](VALIDATION.md).

The protocol transports IPv4, and the outer server must resolve to IPv4. When the
server requests a full IPv4 tunnel, global IPv6 is routed into the adapter and dropped.
There is no system-wide kill switch: ordinary networking remains available between
reconnection attempts. Closing the app disconnects VPN; there is no background
service or pre-login autostart. Windows DNS behavior also depends on OS and corporate policies.

Settings are stored in `%LOCALAPPDATA%\OpenControl\profiles.json`. Retained passwords
are user-scoped DPAPI blobs and cannot be transferred to another Windows account by
copying the file. Uninstalling the MSI retains user profiles.

[Privacy policy](PRIVACY.en.md) · [Конфиденциальность](PRIVACY.md)

This public repository contains user documentation and release artifacts only.
Client sources are in a separate private repository. The public
[OpenControl Protocol Library](https://github.com/nr084/opencontrol-protocol) is a
separate project. Kerio Control belongs to its trademark owner; this client is not
an official Kerio/GFI product.

![Actual UI rendered headlessly with synthetic data](assets/connection-en.png)

## Import from Kerio VPN

On first launch, if `%APPDATA%\Kerio\VpnClient\user.cfg` exists, the application
 offers to review its connections. Nothing is imported until you click Import.
Use Profiles → Import Kerio VPN… to select a file manually, including after skipping
 the initial offer. The source file is read only.

Names, servers, ports, usernames and saved D3S passwords are imported. Passwords are protected with Windows DPAPI. Verify
server certificates before connecting. Kerio startup settings and trust are not migrated.
Semicolon-separated servers become separate profiles. Matching server, port and username
entries are skipped; existing profiles are never replaced. Maximum 100 profiles.
The result shows added and skipped counts.

Unsupported or damaged password entries are marked for manual entry. Passwords are not shown in the preview or written to logs.
