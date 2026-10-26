# Validation / Проверки — 1.1.0

Date / Дата: 2026-10-26.

**Граница проверки:** действующий VPN пользователя не отключался. Длительный
живой прогон использует транспорт Windows-клиента с синтетическим пакетным
устройством и имитацией операций ОС. Он НЕ проверяет установку службы, Wintun,
маршруты и DNS Windows. Эти проверки требуют отдельного свободного Windows-стенда.

**Scope:** the existing user VPN was left running. The live probe uses the actual
Windows client transport with a synthetic packet device and mock OS operations.
It does NOT validate installed-service, Wintun, Windows route or DNS behaviour.
Those checks require a separate available Windows test host.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1, upstream update/check passed |
| OpenControl Protocol | 0.9.0, pinned cacf1a738e5013922ca9678d529d014fffc22d11; annotated v0.9.0 resolves to that commit |
| fmt + clippy all targets, warnings denied | Passed / Пройдено |
| Client tests | 94 unit + 7 migration = 101 passed |
| Protocol all-feature tests and doctests | Passed; two slots/generations, current-slot peer replacement, ACK, stale epochs, legacy opt-in and independent liveness |
| ROUTES model tests | Initial/empty, START without END, unchanged retry after OS failure, partial ACK, full/split endpoint order, failed delete ownership; virtual 600/1200 seconds |
| Windows release builds | x86, x64, ARM64; static CRT; PE machine 014c/8664/aa64 |
| MSI contents | Six allowlisted payloads per architecture; extracted EXE matches build; correct 1.1.0 ProductVersion |
| MSI languages | Russian installer 1049; application Russian/English in every architecture |
| Wintun | Official 0.14.1, pinned SHA256 and valid Authenticode for all three DLLs |
| EXE/MSI publisher signature | Not signed / Не подписаны |
| Shortcuts/icons | Desktop and Start; PE icon stream and native large/small extraction checked |
| GUI and service manifests/tables | asInvoker/PerMonitorV2; LocalSystem, automatic service; standard MSI service stop/delete and uninstall tables checked |
| UI | Synthetic RU/EN profile editor and About rendered; light/dark and 150% narrow layout inspected; native hidden CPU window startup/shutdown passed |
| Live AES transport | 1290 seconds; initial ROUTES at 2s, repeated at 602/1202s; one rekey ACK; 256/258 validated ICMP replies; no reconnect; intentional cancellation passed |
| Live Legacy transport | Expected rejection: supplied modern Kerio does not accept Legacy clients (confirmed by owner). No automatic downgrade. Separate AES reconnect: 6/6 replies in 30 seconds |
| Installed service, actual Wintun/route/DNS apply and restoration | Not run: user explicitly prohibited interrupting the existing VPN |
| Windows 11 ARM device, Modern Standby, network handover | Not run / Не проверено |
| Publication | Public allowlist only: MSI, checksums, user documents and synthetic screenshots; no sources, keys, credentials or raw lab logs |

TLS/authentication policy was retained. Runtime Legacy is off by default and
never selected after an error. UDP endpoint migration requires a new session;
no seamless migration claim is made. safeLan is status, not a firewall command.

DNS recovery uses only the dedicated adapter, retains a backup on errors or
external changes and requires confirmed restoration before clearing it. Automatic
models and code review do not prove failure recovery against a live Windows OS.
Windows route APIs lack cross-process compare-and-delete transactions; an
unrelated administrator can still race an identity check and OS operation.

Kerio configuration and users were not changed for the transport probe. Lab
credentials stayed in process/stdin memory. SSH-key access to the authorized
Ubuntu host was restored at the user's request. No temporary firewall rules or
corporate configuration are included in this release.

The two unanswered AES test packets were observed after the rekey, while replies
continued through the second ROUTES and completion. Their cause was not isolated;
this is not a zero-loss claim. Legacy packet interoperability with an accepting
legacy client server was not live-tested in this Windows release; deterministic
codec/session tests passed. No server policy was weakened for testing.

Два AES-запроса остались без ответа; причина потерь не установлена. Работа
Legacy с принимающим его сервером в этом Windows-выпуске не проверена вживую.
На предоставленном современном Kerio отказ ожидаем и подтверждён владельцем;
автоматического перехода на AES не было. Политика сервера не изменялась.
