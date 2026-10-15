# Validation / Проверки — 0.1.1

Date / Дата: 2026-10-15.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.0, stable channel verified against upstream |
| Protocol dependency | 0.2.0, upstream HEAD `35a5c848fb2a25a64da36268026906ce3757b974` |
| Formatting / Форматирование | Passed / Пройдено |
| Clippy all targets, warnings denied | Passed / Пройдено |
| Unit + ROUTES regression tests | 24 passed / 24 пройдено |
| Native release builds | x86, x64, ARM64 passed |
| MSI platform and language | 3 packages: Intel/x64/Arm64; installer 1049; application RU/EN |
| Extracted EXE | Matches release build SHA256; PE machine 014c/8664/aa64 |
| Extracted Wintun DLL | Exact official bytes; Authenticode Valid on all packages |
| MSI payload allowlist | 6 files: EXE, Wintun, Wintun license, notices, RU/EN guides |
| RU/EN UI | Actual UI rendered headlessly using synthetic profile data and visually inspected |
| EXE/MSI publisher signature | Not signed / Не подписаны |
| Clean Windows install/upgrade/uninstall | Not yet verified / Пока не проверено |
| Real Kerio Control connection | Not tested / Не проверено |
| Physical ARM64, Windows 10 hardware | Not tested / Не проверено |
| Network switching, sleep/resume, live DNS | Not yet accepted / Требуют приёмки |

The tests cover authentication transcript state, netmask validation, transactional
ROUTES, repeated unchanged updates, rekey/replay preservation, failed route-apply
rollback in a synthetic platform, certificate pin/expiry boundaries, DPAPI roundtrip
and profile binding, reconnection policy and Android-compatible QR payload parsing.
They do not exercise the actual Windows adapter against a corporate server.

Тесты проверяют состояние авторизации, маски сетей, транзакционное применение ROUTES,
повторные неизменные маршруты, сохранение rekey/replay, отказ синтетической платформы,
границы доверия сертификатам, DPAPI и привязку к профилю, восстановление и формат QR.
Эти тесты не проверяют реальный Windows-адаптер на корпоративном сервере.

This is a preview, not a claim of production or third-party certification.
Это предварительная версия, без заявления о производственной готовности или внешней сертификации.

Kerio import: 7 synthetic regression tests cover XML parsing, DTD rejection, size limits, invalid endpoints, alternatives, duplicates and profile capacity. No personal connections were imported or included in test fixtures.

Импорт Kerio: 7 синтетических тестов проверяют XML, отказ DTD, размер, неверные адреса, альтернативы, дубликаты и лимит профилей. Личные соединения не переносились и в тесты не включались.

D3S compatibility: independent synthetic .NET TripleDES vectors, ASCII/UTF-8, invalid padding, savePassword policy, DPAPI roundtrip and profile binding. Read-only format checks used an external sample; no profiles were saved and no passwords printed. This does not verify server authentication.

Совместимость D3S: независимые синтетические векторы .NET TripleDES, ASCII/UTF-8, неверное дополнение, флаг savePassword, DPAPI и привязка к профилю. Внешний пример проверен только на чтение; профили не сохранялись, пароли не выводились. Авторизация на сервере не проверялась.
