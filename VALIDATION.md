# Validation / Проверки — 0.6.0

Date / Дата: 2026-10-16.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1, upstream check passed |
| OpenControl Protocol | 0.2.0, upstream HEAD 35a5c848fb2a25a64da36268026906ce3757b974 |
| Format + clippy all targets, warnings denied | Passed / Пройдено |
| Unit + ROUTES regression tests | 53 + 4 = 57 passed |
| Native release builds, static CRT | x86 / x64 / ARM64 passed |
| MSI payloads | Six allowlisted files per package; extracted EXE SHA256 matches build |
| MSI platform/language | Intel / x64 / Arm64; Russian installer 1049; application RU/EN |
| Wintun | Official 0.14.1 bytes and valid Authenticode, all architectures |
| Shortcuts/icons | Desktop + Start; PE icon stream; native large/small extraction verified |
| Service registration/removal tables | LocalSystem, automatic, --service, stop/delete on uninstall; standard RemoveFiles/RemoveShortcuts/RemoveFolders |
| GUI manifest | asInvoker; PerMonitorV2 |
| CPU native startup | Hidden native x64 window created/rendered/closed using synthetic settings |
| UI headless | Actual production painter, RU/EN, dark/light, 100/150/200%, widths 620/760; visually inspected |
| Dependencies | softbuffer 0.4.8, egui-winit clipboard + arboard 3.7.0; no glow/glutin/wgpu in ARM64 normal graph |
| IPC rejection | Fake native named-pipe endpoint receives no credentials; malformed/oversized requests rejected |
| CFG | Synthetic Unicode/D3S export-reimport, saved-password policy, merge/conflicts/deletions, missing-file protection, stale-write rejection |
| Privacy | Current source/reachable history and extracted MSI checked against read-only local references; no endpoint, login, password or profile-ID matches |
| EXE/MSI Authenticode | Not signed / Не подписаны |
| Installed service + ordinary-user session | Not tested on a clean VM / Не проверено на чистой VM |
| Install/upgrade/uninstall end to end | MSI tables verified; actual lifecycle not yet tested / Полный цикл пока не проверен |
| Target Windows 11 ARM VM on Mac | Not available / Недоступна для проверки |
| Live corporate VPN, suspend/resume, actual network cleanup | Not tested / Не проверено |
| External Kerio client accepting exported CFG | Not tested; synthetic re-import only |

Service boundary: local interactive clients only, protected pipe ACL without user pipe-instance creation, remote-pipe rejection, server PID checked against SCM before credentials. One persistent pipe owns the VPN session. The service does not load user profiles, accept shell commands or persist passwords. These are source/unit checks, not a completed installed-service security assessment.

Граница службы: локальные интерактивные клиенты, ограниченный ACL канала без права создавать экземпляры, запрет удалённых подключений, проверка PID службы через SCM до отправки пароля. Одна сессия принадлежит одному открытому каналу. Служба не загружает пользовательские профили, не принимает команды оболочки и не сохраняет пароли. Это проверки кода и тестов, а не завершённая проверка установленной службы.

No real credentials, private profiles or user screenshots are included in this repository or its assets. All displayed UI images use synthetic data. The privacy audit does not cover inaccessible deleted GitHub objects/caches or third-party copies.
