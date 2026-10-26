# Validation / Проверки — 1.1.2

Date / Дата: 2026-10-26.

Изменение касается сведений об ОС. Работающий VPN пользователя не отключался;
установленная служба, реальное новое VPN-соединение и таблица живого сервера
в этом выпуске не проверялись. Автоматические проверки и чтение серверного
обработчика не заменяют живую проверку. Маршруты, DNS, TLS и авторизация не менялись.

This release changes OS metadata. The existing user VPN was not interrupted.
The installed service, a new live VPN session and the live server table were not
exercised in this release. Automated tests and server-handler review are not live
acceptance. Routes, DNS, TLS and authentication are unchanged.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1; rustup update stable verified |
| Protocol | 0.9.0, unchanged pinned cacf1a738e5013922ca9678d529d014fffc22d11 |
| fmt + clippy all targets, warnings denied | Passed / Пройдено |
| Automated tests | 103 unit + 7 ROUTES migration = 110 passed |
| OS formatting | Windows 10/11, server product distinction, build/revision, native versus process architecture, missing values and bounded untrusted registry text |
| Compatibility | Old serialized os_release is ignored; new configuration does not persist OS metadata |
| Wire metadata | Windows OS code, application 1.1.2/build 9, full detailed description and zero padding verified |
| Native runtime detection | x64 process on Windows 11 reports current version/release/build and x64 |
| WOW64 runtime detection | x86 process on the same host reports native x64 plus client x86 |
| ARM64 | Native binary compiled; emulated architecture formatting covered by tests; actual ARM64 hardware runtime not tested |
| Server | Existing handler reviewed: preserves bounded client description separately from OS family and app version; no server changes |
| Build/MSI | x86, x64, ARM64; static CRT; ProductVersion 1.1.2; Russian installer 1049; application RU/EN |
| MSI verification | PE architecture, payload hashes, icon extraction, shortcuts and standard service/uninstall tables checked |
| Wintun | Official 0.14.1; pinned archive SHA256; packaged DLL Authenticode Valid |
| Publisher signatures | EXE/MSI unsigned / EXE и MSI без издательской подписи |
| UI | Updated synthetic RU/EN About screenshots; native CPU window startup/shutdown |
| Live install/upgrade, VPN before sign-in, Windows ARM device | Not run / Не проверено |

The OS metadata probe reads only OS version and architecture. It does not open
VPN profiles, authenticate, configure adapters or alter the active tunnel.
Проверка метаданных читает только версию ОС и архитектуру; профили, авторизацию,
адаптеры и действующее подключение не затрагивает.

Historical 1.1.0 evidence only: a 1290-second real AES transport probe with mock
OS resources observed ROUTES at 602/1202 seconds and one rekey ACK. It is not a
new 1.1.2 live run and does not validate real Windows route/DNS/Wintun operations.
Исторический прогон 1.1.0 не выдаётся за новый живой прогон 1.1.2.
