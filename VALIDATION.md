# Validation / Проверки — 1.1.1

Date / Дата: 2026-10-26.

## Scope / Граница проверки

Действующий VPN пользователя не отключался. Установка/обновление службы,
реальное переключение режима через UAC и VPN до входа на физической Windows
в этом выпуске не проверялись: для этого нужен свободный Windows-стенд.
Автоматические проверки и снимки интерфейса не заменяют такую проверку.

The existing user VPN was not interrupted. Installed-service upgrade, real UAC
mode changes and pre-sign-in connection on a Windows machine were not exercised
in this release; they require a separate available Windows host. Automated tests
and rendered UI screenshots are not live installation acceptance.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1; rustup update stable checked 2026-10-26 |
| Protocol | Unchanged 0.9.0, pinned cacf1a738e5013922ca9678d529d014fffc22d11 |
| fmt and clippy all targets, warnings denied | Passed / Пройдено |
| Automated tests | 99 unit + 7 ROUTES migration = 106 passed |
| Startup modes | Success switches modes; failed/cancelled configuration preserves preferences; disabling boot does not enable another mode; unknown service state blocks client auto-connect |
| Persistence | Old default_profile is ignored; last selection survives JSON reload and sorting; save failures preserve safety of the active mode |
| Windows builds | x86, x64, ARM64; static CRT |
| MSI | Version 1.1.1, Russian installer 1049; application RU/EN; PE architecture, extracted payload hashes, service/uninstall tables and shortcuts checked |
| Driver | Official Wintun 0.14.1; pinned archive hash; extracted DLL Authenticode Valid |
| Publisher signatures | EXE/MSI unsigned / EXE и MSI не подписаны издателем |
| UI | Synthetic RU/EN settings, profiles and About; light/dark and scaled layout; native CPU window startup/shutdown |
| Live VPN for 1.1.1 | Not repeated: settings/UI change; existing host VPN left running |
| Windows ARM hardware, sleep/resume, installed upgrade/remove, boot connection | Not run / Не проверено |

Historical evidence from 1.1.0 only: a 1290-second live AES transport probe with
mock OS resources observed repeated ROUTES at 602/1202 seconds and one rekey ACK.
It did not test real Windows routes, DNS or Wintun and is not a new 1.1.1 live run.

Исторический результат 1.1.0: живой прогон транспорта AES 1290 секунд с имитацией
операций ОС, повторными ROUTES на 602/1202 секундах и одним ACK rekey. Он не
проверял реальные маршруты, DNS и Wintun и не выдаётся за новый прогон 1.1.1.
