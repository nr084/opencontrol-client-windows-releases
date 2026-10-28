# Validation / Проверки — 1.1.3

Изменены обработчики трея и переключателя ВКЛ/ВЫКЛ. Действующий VPN пользователя
не прерывался. Установка MSI поверх работающей службы, новое живое VPN-подключение
и проверка на физическом ARM64-устройстве в этом выпуске не выполнялись.
Автоматические проверки интерфейса не заменяют проверку мышью в установленном клиенте.

This release changes tray gestures and ON/OFF handling. The existing user VPN
was not interrupted. MSI installation over the running service, a new live VPN
session and physical ARM64 execution were not tested in this release. Synthetic
pointer tests do not replace interactive acceptance of the installed application.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1; rustup update stable verified |
| Protocol | 0.9.0, unchanged pinned cacf1a738e5013922ca9678d529d014fffc22d11 |
| fmt + clippy all targets, warnings denied | Passed / Пройдено |
| Automated tests | 107 unit + 7 ROUTES migration = 114 passed |
| Pointer handling | Left/center/right switch hit regions at 100/150/200%; forced second egui layout pass; explicit OFF intent applied once |
| Tray gesture | Single-click delay, double-click ConnectSelected, suppression of trailing release, subsequent single click |
| Session safety | Connect action preserves existing worker; incomplete profile opens editor; intent waits for sync and is discarded on shutdown |
| Build/MSI | x86, x64, ARM64; static CRT; ProductVersion 1.1.3; Russian installer 1049; application RU/EN |
| MSI verification | PE architecture, payload hashes, icon extraction, shortcuts and standard service/uninstall tables checked |
| Wintun | Official 0.14.1; pinned archive SHA256; packaged DLL Authenticode Valid |
| Publisher signatures | EXE/MSI unsigned / EXE и MSI без издательской подписи |
| UI | Synthetic RU/EN Connection and About renders; smaller 150% light layout; native CPU window startup/shutdown |
| Live install/upgrade and Windows ARM device | Not run / Не проверено |

Маршруты, DNS, TLS, авторизация и протокольная реализация не изменялись.
Routes, DNS, TLS, authentication and protocol implementation are unchanged.
Historical 1.1.0 transport evidence is not a new 1.1.3 live run.
