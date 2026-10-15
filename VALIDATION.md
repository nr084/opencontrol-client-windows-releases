# Validation / Проверки — 0.5.0

Date / Дата: 2026-10-15.

| Check / Проверка | Result / Результат |
|---|---|
| Rust stable | 1.99.1, stable channel verified against upstream |
| Protocol dependency | 0.2.0, upstream HEAD `35a5c848fb2a25a64da36268026906ce3757b974` |
| Formatting / Форматирование | Passed / Пройдено |
| Clippy all targets, warnings denied | Passed / Пройдено |
| Unit + ROUTES regression tests | 45 passed / 45 пройдено |
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

0.2.0 additions: certificate review tests cover consent gating, stale endpoints and unchanged/replaced certificates. Status badges are checked at six resolutions. RU/EN render checks cover 100/125/150/200%, a 470-point-wide window and a native-scale change within one egui context. Embedded icon includes 16/24/32/48/64/128/256 pixel sizes; the executable manifest declares PerMonitorV2. The MSI Shortcut table is checked for both Start menu and Desktop entries in all three architectures.

Дополнения 0.2.0: тесты проверки сертификата охватывают ожидание согласия, устаревший адрес и прежний/заменённый сертификат. Значки статуса проверены в шести размерах. Рендер RU/EN проверен на 100/125/150/200%, при ширине 470 логических пикселей и смене масштаба одного контекста egui. Значок EXE содержит размеры 16/24/32/48/64/128/256; манифест объявляет PerMonitorV2. Таблица Shortcut каждого MSI проверяется на наличие ярлыков «Пуск» и рабочего стола.

Native tray interaction, Explorer restart, physical monitor changes and real VPN connection are not exercised by headless rendering. These remain manual acceptance items.
Работа нативного трея, перезапуск Explorer, смена физических мониторов и реальное VPN-подключение не проверяются программным рендером и требуют ручной приёмки.

0.3.0: two added regression tests verify that closing a window with a tray preserves the session cancellation token and that unavailable-tray cleanup does not leave an unreachable active session. Windows ExtractIconEx checks both large and small icons from the EXE and the MSI icon stream. The extracted MSI icon stream must match the release EXE; branding BMPs must match the source artwork. Actual main-window RU/EN renders at 100/125/150/200% and narrow width were inspected. Native Windows icon extraction is not a full installed-shell acceptance test.

0.3.0: два новых теста проверяют сохранение сессии при закрытии окна в трей и безопасное завершение при недоступном трее. Windows ExtractIconEx проверяет большие и малые значки EXE и потока значка MSI. Поток значка MSI должен совпадать с EXE сборки; BMP оформления — с исходными изображениями. Проверен рендер нового главного окна RU/EN на 100/125/150/200% и при узкой ширине. Извлечение значков Windows не заменяет проверку установленного приложения в оболочке.

0.4.0: seven additional tests cover connected-state animation, synthetic Unicode paste/copy/cut events in actual text fields, password clipboard protection, consistent dark/light colors, profile JSON roundtrip, last-profile deletion and failed-save rollback. The native eframe → egui-winit → arboard clipboard feature chain is enabled. Personal clipboard contents were neither read nor changed; native interactive clipboard acceptance remains pending. Light RU/EN renders cover 100/125/150/200% and narrow width; dark renders include normal and narrow layouts. Tray status icons pass checks at nine sizes from 16 to 128 pixels.

0.4.0: семь новых тестов проверяют отсутствие анимации после подключения, синтетические события Unicode-вставки/копирования/вырезания в настоящих текстовых полях, защиту пароля от копирования, согласованность цветов тем, сериализацию профилей, удаление последнего профиля и откат при ошибке записи. Включена цепочка нативного буфера eframe → egui-winit → arboard. Личный буфер не читался и не менялся; интерактивная проверка нативного буфера остаётся отдельной приёмкой. Светлый интерфейс RU/EN отрендерен на 100/125/150/200% и узкой ширине; тёмный — в обычном и узком окне. Значки трея проверены в девяти размерах от 16 до 128 пикселей.

0.5.0: eight added tests cover Android-style CIDR normalization and limits, subtraction across full/split/connected/DNS routes and address boundaries, serialized exclusions and legacy defaults, reconnect waiting for a synthetic worker to finish, session snapshot preservation, pending-restart cancellation, notification-edge deduplication and UTF-16 bounds. Exclusions are applied to the complete Windows route candidate before transactional installation. With exclusions configured, the interface uses a /32 address to avoid an implicit connected-subnet route overriding them. Existing IPv6 full-tunnel blocking behavior is retained; IPv6 exclusions are not supported.

0.5.0: восемь новых тестов проверяют нормализацию CIDR и лимит исключений, вычитание из полных/частичных маршрутов, подключённой подсети и DNS, границы адресов, сериализацию и совместимость старых настроек, ожидание завершения синтетического рабочего потока, сохранение параметров сессии, отмену перезапуска, отсутствие повторных уведомлений и границы UTF-16. Исключения применяются к полному кандидату Windows-маршрутов перед транзакционной установкой. При наличии исключений интерфейс получает адрес /32, чтобы неявный маршрут подключённой подсети не перекрыл исключения. Прежняя блокировка IPv6 при полном туннеле сохранена; исключения IPv6 не поддерживаются.

Actual Networks RU/EN UI rendered headlessly at 100/125/150/200% and narrow width. Installer BMPs freshly generated at 1972×1248 and 1972×232; source and embedded hashes/dimensions verified. Artwork previews at 100/125/150/200% are raster scaling checks, not interactive MSI rendering. Native notification delivery, physical DPI behavior and live routing/cleanup still require manual acceptance.

Настоящая вкладка «Сети» RU/EN отрендерена программно на 100/125/150/200% и в узком окне. BMP заново созданы в 1972×1248 и 1972×232; проверены размеры и хеши вложений MSI. Предпросмотры оформления на 100/125/150/200% проверяют масштабирование изображений, а не интерактивный MSI. Доставка системных уведомлений, физические DPI и реальная маршрутизация/очистка требуют ручной приёмки.

Notification API reference: https://learn.microsoft.com/en-us/windows/win32/api/shellapi/ns-shellapi-notifyicondataw
MSI bitmap scaling reference: https://learn.microsoft.com/en-us/windows/win32/msi/bitmap-control
