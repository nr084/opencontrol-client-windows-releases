<p align="center"><img src="assets/icon.png" width="104" alt="OpenControl" /></p>
<h1 align="center">OpenControl for Windows</h1>
<p align="center">Your corporate network · Windows 10 / 11</p>
<p align="center"><a href="README.md">Русский</a> · <b>English</b></p>

An independent Kerio Control VPN client built on the OpenControl Protocol Library. Your organization supplies the private server address and account. This project does not provide VPN access.

## Install and uninstall

[Download MSI](https://github.com/nr084/opencontrol-client-windows-releases/releases).

| System | Package |
|---|---|
| Windows 10/11 Intel/AMD 64-bit | x64 |
| Windows 10 32-bit | x86 |
| Windows 10/11 ARM64 | arm64 |

One MSI per architecture; Russian installer, RU/EN application. Desktop and Start menu shortcuts are installed by default.

0.6.0 installs **OpenControl VPN** (`OpenControlVpn`), an automatically started LocalSystem service that manages the adapter, routes and DNS. The interface runs with ordinary user permissions: connecting and disconnecting do not require UAC. Administrator permission is needed to install, upgrade or uninstall. The service supports one VPN session at a time; only its connected local pipe client controls that session. If the interface crashes, the session is stopped.

Before upgrading or uninstalling, choose **Exit** in the tray menu. Uninstall through **Windows Settings → Apps → Installed apps → OpenControl → Uninstall**, or standard `msiexec /x` with the original MSI. MSI stops and removes the service, program files and both shortcuts. User profiles and external synchronization files are preserved. A shared Wintun driver is not removed from the system when other applications may use it.

Official Wintun 0.14.1 is signed by WireGuard LLC. The project EXE/MSI do not yet have publisher Authenticode signatures; driver signing is separate. Verify SHA256SUMS.

## Connect and use

1. In **Profiles**, choose **New profile**, enter name, server, port (usually 4090), username and password, then save.
2. Select a connection on the **Connection** tab. Profiles are sorted by name, ignoring case.
3. Use the central VPN switch between OpenControl and Theme. On first connection, verify the certificate fingerprint with your administrator. A changed certificate requires another review.
4. On successful connection the window hides to the tray and a notification identifies the tunnel. Windows notification settings control its visibility.

Closing the window hides it without disconnecting. The tray icon exists throughout the application's lifetime: green mark when connected, red cross when disconnected. Windows may place it in the overflow area. Its right-click menu offers Open, Reconnect, Disconnect and **Exit**. Only Exit terminates the application after network cleanup. Reconnect finishes the old session before starting another.

The green shield fills most of the icon, retaining the red background. CPU rendering through Windows GDI requires no OpenGL, DirectX or 3D accelerator. Windows DPI scaling is respected. Light/dark themes change both background and text. Connected sessions never show a progress spinner.

Text fields support Ctrl+C / Ctrl+X / Ctrl+V. Password paste is supported; hidden passwords are not copied or cut to the clipboard. Saved passwords use Windows DPAPI bound to the user and profile.

Add/delete profiles while VPN is disconnected. **Delete selected** is a button with confirmation. Deleting the last profile leaves a blank editor.

![Interface with synthetic data](assets/connection-en.png)

## Settings: Kerio and synchronization

On first launch, the app offers to review an existing `%APPDATA%\Kerio\VpnClient\user.cfg`; import requires confirmation. **Settings → Import Kerio** selects another file. Names, endpoints, logins and saved D3S passwords are imported; certificate trust and Kerio startup settings are not. Duplicates are skipped, maximum 100 profiles. Unsupported passwords require manual entry. A normal import does not modify the source file.

**Export Users.cfg** writes the whole list in Kerio XML format, including saved passwords. Session-only passwords are excluded. Format compatibility is tested by synthetic re-import; acceptance by the external Kerio client requires a separate check.

**Select local users.cfg** enables two-way synchronization including deletions. Initially lists are merged; differing versions of the same connection require a choice. Later changes are compared with the last synchronized baseline. Concurrent edits to the same record pause synchronization and offer the client or file version for conflicts; unrelated changes are merged. The file is checked approximately every five seconds while VPN is disconnected and the profile editor is closed. Missing/malformed files or unsupported passwords pause synchronization without clearing profiles. **Unlink file** preserves both the file and local profiles.

Local disks only; network paths are unsupported. Kerio options outside the connection list are preserved. CFG contains portable passwords in Kerio's reversible format: restrict access to it. The client does not upload it to a cloud service.

## QR and network exclusions

Profiles offers QR import from PNG, **Show QR**, and **Save QR to PNG**. The format is compatible with OpenControl for Android.

**Networks** configures shared IPv4 exclusions for all profiles, up to 128 CIDRs, such as `192.168.1.0/24` or `10.0.0.5/32`. Excluded networks and DNS servers use the regular connection outside VPN. Changes apply from the next connection. IPv6 exclusions and per-app routing are not provided.

## Release status

0.6.0 is a preview. See [VALIDATION.md](VALIDATION.md) for actual checks. Operation in the reported Windows 11 ARM VM on Mac and a real corporate connection require testing on the target system; successful builds do not replace that testing.

[Privacy](PRIVACY.en.md) · [Русская политика](PRIVACY.md)

This public repository contains binaries and user documentation only. Client sources are private; the [protocol library](https://github.com/nr084/opencontrol-protocol) is a separate public project. This is not an official Kerio/GFI product.

<details>
<summary>Profiles, settings and network exclusions</summary>

![profiles](assets/profiles-en.png)

![settings](assets/settings-en.png)

![networks](assets/networks-en.png)

</details>
