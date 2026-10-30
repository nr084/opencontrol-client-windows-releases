# Validation / Проверки — 1.1.8

Действующий VPN не прерывался. Новая установка MSI, живая проверка маршрутов/DNS/Wintun
и запуск на физическом ARM64 не выполнялись. Проверки политики и повторных ROUTES
автоматические, без изменения сетевых ресурсов Windows.

The existing VPN was not interrupted. MSI installation, live Windows routing/DNS/Wintun
acceptance and physical ARM64 execution were not performed. Policy and repeated ROUTES
tests are automated and do not mutate Windows network resources.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1; rustup update stable verified |
| Protocol | 0.9.0, unchanged pinned cacf1a738e5013922ca9678d529d014fffc22d11 |
| fmt + clippy all targets, warnings denied | Passed / Пройдено |
| Automated tests | 120 unit + 7 ROUTES migration = 127 passed |
| Policy | Exclude parity; Include empty/full/overlapping/invalid lists; selected routes independent of full/split/empty server updates |
| DNS | Include filters DNS outside selection; Exclude retains prior DNS behavior |
| Persistence | Missing mode defaults to Exclude; explicit Include round-trip; unknown mode rejected; failed save rolls back |
| Service and boot | Explicit Request mode serialized, default omitted; encrypted boot Config preserves Include and list; reconnect snapshot preserves mode |
| UI | Active session blocks mode changes; pointer click survives repeated layout pass; Networks RU/EN and 150% screenshots retained from 1.1.7; About version refreshed in 1.1.8 |
| Route lifecycle | Existing migration tests cover endpoint ordering, partial ACK/retry, unchanged ROUTES at 600/1200 seconds and cancellation |
| Build/MSI | x86, x64, ARM64; ProductVersion 1.1.8; Russian installer 1049; application RU/EN |
| MSI verification | PE architecture, payload hashes, icon extraction, shortcuts and service/uninstall tables checked |
| Wintun | Official 0.14.1; pinned archive hash; packaged DLL Authenticode Valid |
| Publisher signatures | EXE/MSI unsigned / EXE и MSI без издательской подписи |
| Native UI | Refreshed RU/EN About screenshot with production CPU painter; no installed-client launch |

Include changes routing selection. Endpoint protection, ownership checks, recovery journals,
TLS, authorization, encryption and rekey mechanisms remain unchanged. A live deployment
must validate selected destinations, corporate DNS and cleanup on its own network.

1.1.8: synthetic tests cover vanished LUID, reused index, changed index, enumeration error, invalid identity and failed-save rollback. A native read-only test confirms that a nonexistent LUID has no interface/route. No host reboot, installed upgrade or live VPN/DNS recovery was performed; the protected user journal was not read or modified. / Тесты не заменяют живую проверку после перезагрузки; сеть и журнал пользователя не изменялись.
