# Validation / Проверки — 1.0.5

Date / Дата: 2026-10-22.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1, upstream check passed |
| OpenControl Protocol | 0.2.0, upstream HEAD 35a5c848fb2a25a64da36268026906ce3757b974 |
| Format + clippy all targets, warnings denied | Passed / Пройдено |
| Unit + ROUTES regression tests | 91 + 4 = 95 passed |
| Native release builds, static CRT | x86 / x64 / ARM64 passed |
| MSI payloads | Six allowlisted files per package; extracted EXE SHA256 matches build |
| MSI platform/language | Intel / x64 / Arm64; Russian installer 1049; application RU/EN |
| Wintun | Official 0.14.1 bytes and valid Authenticode, all architectures |
| Shortcuts/icons | Desktop + Start; PE icon stream; native large/small extraction verified |
| Service registration/removal tables | LocalSystem, automatic, --service, stop/delete on uninstall; standard RemoveFiles/RemoveShortcuts/RemoveFolders |
| GUI manifest | asInvoker; PerMonitorV2 |
| CPU native startup | Hidden native x64 window created/rendered/closed using synthetic settings |
| UI headless | 1.0.5 About and Settings RU/EN rendered and visually inspected; earlier dark/light, 100/150/200%, widths 620/900 checks retained from previous releases |
| Dependencies | softbuffer 0.4.8, egui-winit clipboard + arboard 3.7.0; no glow/glutin/wgpu in ARM64 normal graph |
| IPC rejection | Fake native named-pipe endpoint receives no credentials; malformed/oversized requests rejected |
| CFG | Synthetic Unicode/D3S export-reimport, saved-password policy, merge/conflicts/deletions, missing-file protection, stale-write rejection |
| Privacy | Explicit publication allowlist and synthetic screenshots; personal configuration stores not read for this reissue |
| EXE/MSI Authenticode | Not signed / Не подписаны |
| Installed service + ordinary-user session | Not tested on a clean VM / Не проверено на чистой VM |
| Install/upgrade/uninstall end to end | MSI tables verified; actual lifecycle not yet tested / Полный цикл пока не проверен |
| Target Windows 11 ARM VM on Mac | Not available / Недоступна для проверки |
| Live corporate VPN, suspend/resume, actual network cleanup | Not tested / Не проверено |
| External Kerio client accepting exported CFG | Not tested; synthetic re-import only |

Service boundary: local interactive clients only, protected pipe ACL without user pipe-instance creation, remote-pipe rejection, server PID checked against SCM before credentials. Each VPN session owns a fresh pipe instance; the old protected handle remains until its successor exists, after VPN cleanup. The service does not load per-user profile files or accept shell commands. In 1.0.3 it may read the explicitly configured protected machine boot profile; only the UAC helper writes that credential. These are source/unit checks, not a completed installed-service security assessment.

Граница службы: локальные интерактивные клиенты, ограниченный ACL канала без права создавать экземпляры, запрет удалённых подключений, проверка PID службы через SCM до отправки пароля. Одна сессия принадлежит одному открытому каналу. Служба не загружает файлы пользовательских профилей и не принимает команды оболочки. В 1.0.3 она читает отдельно настроенную защищённую конфигурацию запуска компьютера; записывает её только UAC-помощник. Это проверки кода и тестов, а не завершённая проверка установленной службы.

No real credentials, private profiles or user screenshots are included in this repository or its assets. All displayed UI images use synthetic data. The privacy audit does not cover inaccessible deleted GitHub objects/caches or third-party copies.

1.0 additions: duplicate import policies and DPAPI rebinding, atomic replacement rollback, cumulative reconnect traffic, localized bounded tray tooltip. Autostart Run registration and interactive Finish action are checked in MSI tables; actual sign-in/Finish behavior remains a Windows acceptance check. Tray badges are supersampled; the UI logo is filtered to the current DPI. Physical multi-monitor DPI acceptance remains unverified.

Reissue checks: native Windows named-pipe regression reproduces EOF/closing-pipe on the old reused instance after AuthenticationFailed; replacement-instance test passes for the next session. Service error classification and cancelled opening are covered. This is a synthetic broker test, not a real firewall or target ARM VM test. Native Windows Shell GUID tooltip and icon updates passed for disconnected → connected → disconnected. Physical tray appearance on the target ARM VM still needs user acceptance.
Branding rebuild: all three MSI ProductName, installation folder, shortcut names, service display name and extracted EXE ProductName/FileDescription checked against OpenControl Client. Installed EXE filename is OpenControl-client.exe. Embedded information/warning ICO streams match the new transparent multi-resolution assets. Fresh synthetic RU/EN screenshots rendered at 150%, including About. Native installer dialog appearance on physical DPI settings remains unverified.

Updater checks: numeric stable-version comparison, architecture selection, fixed-repository assets and HTTPS redirects, checksum ambiguity rejection, MSI corruption detection and native deny-write/delete file locking passed. Native tray updates with and without the update badge passed. Live public GitHub metadata check correctly reports no newer version at 1.0.0; no MSI was downloaded or installed by this check. Silent upgrade, UAC cancellation and restart on a clean Windows VM remain untested. GitHub checksum verification is an integrity check, not an independent publisher signature. Fresh RU/EN About screenshots show the manual update button and home page.

1.0.1: wire metadata version matches Cargo; build 2 and Windows OS identity checked. Synthetic profile-switch tests verify cleanup waiting, stable profile identity, duplicate/stale action rejection and cancellation. History tests verify timestamps, tunnel names, loss-of-connection entries and deduplication. Native tray submenu add/update/remove and RU/EN updates passed. Actual remote administration table and live switching between corporate servers were not tested. © 2026 nr084 is included in About and EXE resources.


1.0.2: successful update results 0/3010 open the main window even with the legacy --autostart argument; failed/cancelled updates retain tray startup. Synthetic Kerio tests cover existing/missing paths, no read before selection, cancellation without profile changes, own-file preview, read failure and duplicate decisions. RU/EN import and About screenshots use synthetic settings. Preview timestamps advance to let modal animations settle. Native x64 CPU startup/render/shutdown passed. Full MSI update/UAC/relaunch and target ARM VM acceptance remain untested.

1.0.2: результаты обновления 0/3010 открывают окно, в том числе при старом --autostart. Синтетические тесты проверяют выбор CFG, отмену, отсутствие файла, ошибку чтения и дубли. Полный цикл автообновления с UAC на чистой VM не проверен.


1.0.3: synthetic export matches exact Kerio XML layout, including declaration, LF, indentation, empty elements and application section. Bidirectional sync tests cover add/edit/delete uploads and repeat no-op. Result timestamps, counts and error codes are persisted. No personal fixtures are shipped.

Pre-sign-in VPN: machine DPAPI roundtrip, required saved-password/pin validation, one-shot GUI-owned pipe creation, boot-tunnel status/cleanup handoff and existing broker retry tests pass. GUI helper verifies the elevated child PID, helper verifies parent pipe PID. Its one-shot pipe is restricted to owner/Administrators/SYSTEM; the existing VPN service ACL is unchanged. The fixed registry credential key is restricted to SYSTEM/Administrators. MSI uninstall cleanup is fixed-purpose, deferred and excluded from upgrades. Actual UAC, machine registry persistence, reboot-before-logon and live VPN acceptance remain untested; unit tests do not replace these checks.


1.0.4: notification policy tests cover manual attempt success, repeated automatic reconnects, silent boot attachment, sleep/lock interruption, returning between UI polls, missing tray and suppressed notifications. Native synthetic-window checks verify power/session registration and dispatch of display off/on, lock and suspend messages. The test does not suspend or lock Windows. CPU native startup/shutdown and clippy pass. Physical Modern Standby, screen/lid transitions and Shell balloon presentation on the target laptop remain untested. No claim is made about purging the entire Windows notification queue.

API reference: [Windows notification state](https://learn.microsoft.com/en-us/windows/win32/api/shellapi/ne-shellapi-query_user_notification_state). The implementation additionally tracks session display power events rather than assuming that a hidden app window means an absent user.

1.0.5: synthetic tests cover independent startup preferences, legacy defaults (no automatic VPN), one-shot startup intent, waiting for the service probe, preserving an existing service/manual tunnel, UUID selection across rename/sort, deleted/missing profiles and missing credentials without network activity. Tooltip tests cover RU/EN, long Unicode/emoji names, control filtering, UTF-16 limits and preserved traffic counters. Native GUID tray updates and hidden CPU startup checks passed. These tests do not perform real user sign-in, install a service or connect to a corporate firewall.

1.0.5 dependency refresh: Rust stable 1.99.1 and protocol HEAD unchanged; compatible stable Cargo updates include Tokio 1.54.1, rustls-webpki 0.103.16 and schannel 0.1.30. Cargo.lock pins the complete resolved graph.
