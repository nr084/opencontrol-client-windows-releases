# Validation / Проверки — 1.1.4

Изменены визуальные состояния переключателя и момент выполнения команды после
показа кадра. Действующий VPN пользователя не прерывался. Установка поверх
работающего клиента, новое живое VPN-подключение и физическое ARM64-устройство
не проверялись. Синтетические события мыши не являются проверкой установленного клиента.

This release changes switch presentation and commits actions after presenting the
frame. The existing user VPN was not interrupted. Installation over the running
client, a new live VPN session and physical ARM64 execution were not tested.
Synthetic pointer events are not installed-client acceptance.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1; rustup update stable verified |
| Protocol | 0.9.0, unchanged pinned cacf1a738e5013922ca9678d529d014fffc22d11 |
| fmt + clippy all targets, warnings denied | Passed / Пройдено |
| Automated tests | 108 unit + 7 ROUTES migration = 115 passed |
| Immediate feedback | Pointer ON and OFF paint the knob at the center in the accepted-click frame, before connection work |
| States | Pending request, connecting, connected, cancelled worker awaiting cleanup, stopped worker, failure and certificate consent |
| Repeated input | Layout retries preserve one intent; disconnecting has no new command; connecting can be cancelled |
| DPI input | Switch left/center/right hit regions at 100/150/200% |
| Build/MSI | x86, x64, ARM64; static CRT; ProductVersion 1.1.4; Russian installer 1049; application RU/EN |
| MSI verification | PE architecture, payload hashes, icon extraction, shortcuts and standard service/uninstall tables checked |
| Wintun | Official 0.14.1; pinned archive SHA256; packaged DLL Authenticode Valid |
| Publisher signatures | EXE/MSI unsigned / EXE и MSI без издательской подписи |
| UI | Synthetic RU/EN connecting/disconnecting renders; native CPU window startup/shutdown |
| Live install/upgrade and Windows ARM device | Not run / Не проверено |

Routes, DNS, TLS, authentication and protocol implementation are unchanged.
Маршруты, DNS, TLS, авторизация и реализация протокола не изменялись.
