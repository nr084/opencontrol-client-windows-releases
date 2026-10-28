# Validation / Проверки — 1.1.5

Действующий VPN пользователя не прерывался. Новая установка MSI, живое VPN-подключение,
ручной двойной щелчок в установленном клиенте и физическое ARM64-устройство не проверялись.
Проверки событий и отрисовки используют синтетические данные.

The existing user VPN was not interrupted. MSI installation, a new live VPN session,
manual double-click acceptance in the installed client and physical ARM64 execution
were not tested. Event and rendering tests use synthetic data.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1; rustup update stable verified |
| Protocol | 0.9.0, unchanged pinned cacf1a738e5013922ca9678d529d014fffc22d11 |
| fmt + clippy all targets, warnings denied | Passed / Пройдено |
| Automated tests | 111 unit + 7 ROUTES migration = 118 passed |
| Tray gestures | Double-click emits ToggleWindow, suppresses the trailing release and preserves subsequent single clicks |
| Visibility | Repeated hide/show with and without a synthetic worker; no cancellation, new connection intent or profile change; ignored during shutdown |
| Minimized window | Restore issues Visible(true), Minimized(false), Focus without connecting |
| Rendering | Opaque colors, non-white texture fallback, DPI clipping, transparent shared-edge blending |
| Image comparison | RU/EN 760×780 synthetic frames before/after: maximum channel difference 1/255 (flat-color rounding) |
| Timing observation | Same unoptimized synthetic renderer: 448/552 ms before versus 70/72 ms after; not a hardware-independent latency guarantee |
| Build/MSI | x86, x64, ARM64; static CRT; ProductVersion 1.1.5; Russian installer 1049; application RU/EN |
| MSI verification | PE architecture, payload hashes, icon extraction, shortcuts and standard service/uninstall tables checked |
| Wintun | Official 0.14.1; pinned archive SHA256; packaged DLL Authenticode Valid |
| Publisher signatures | EXE/MSI unsigned / EXE и MSI без издательской подписи |
| UI | Synthetic RU/EN screenshots and native CPU window startup/shutdown |

Routes, DNS, TLS, authentication and protocol implementation are unchanged.
Маршруты, DNS, TLS, авторизация и реализация протокола не изменялись.
