# OpenControl Client 1.0.0

## Русский

- О программе: кликабельная домашняя страница, ручная и ежедневная проверка обновлений GitHub. Новая версия автоматически скачивается и проверяется по SHA256; тихая установка ждёт отключения VPN, без принудительной перезагрузки. Возможен запрос UAC.
- Новое обновление отмечается жёлтым восклицательным знаком в трее и уведомлением; значок подключения остаётся виден.

- Единое название OpenControl Client: окно, установщик, папка установки, ярлыки, автозапуск, сведения о программе и службе. Обновлены значки информации и предупреждения в мастере установки.

- Русский язык по умолчанию при первом запуске; сохранённый выбор языка не сбрасывается.

- Исправлено повторное подключение после неверного пароля: завершённый IPC-канал заменяется новым после очистки сеанса, без перезапуска службы. Кратковременная занятость канала ожидается до 5 секунд; ошибки службы разделены по причинам.
- Исправлено обновление GUID-значка трея: подключение показывает зелёную точку в белой оправе. Крестик окна скрывает и неподключённый клиент; выход только через меню трея.
- Шрифт интерфейса — установленный в Windows Segoe UI. «Client» под названием; справа от переключателя — причина ошибки, без дублирующего статуса. Включение VPN не требует отдельного чекбокса разрешения.
- Пакеты: `OpenControl-client-1.0.0-windows-{x86,x64,arm64}.msi`.

- Переключатель ВКЛ / ВЫКЛ без подписи «Подключить»; вкладки одинаковой ширины, адаптивные ряды для узкого окна.
- Новый крупный зелёный щит на прозрачном фоне. Плавные контуры, сглаживание отметок трея, ICO 16–256 px и PNG 1024 px; картинка в окне подготавливается под текущий DPI.
- При подключении — зелёная точка с белой обводкой, без подключения — красный крестик. Меню трея переведено сразу при запуске и при смене языка.
- Подсказка трея показывает суммарный трафик сессии: отправлено / получено. Автоматическое восстановление соединения сохраняет сумму; новая сессия сбрасывает счётчики.
- После интерактивной установки кнопка «Готово» открывает интерфейс. При входе в Windows интерфейс автоматически запускается в трей, без автоматического подключения VPN. Штатное удаление убирает запись автозапуска.
- В импорте, включая первый запуск, доступен выбор любого CFG. Для дублей нужно выбрать: оставить существующие, заменить данными файла или сохранить оба варианта. Замена сохраняет локальную идентичность профиля и доверие сертификату.
- Экспорт по умолчанию в **user.cfg**. Автоматическая синхронизация раз в час; ручная синхронизация доступна. Во время подключения или редактирования проверка откладывается.
- Новый или изменившийся сертификат требует подтверждения доверия; просроченный требует отдельного согласия. Выбор запоминается для конкретного отпечатка.

**Windows 10/11 · x86 / x64 / ARM64 · RU + EN в каждом MSI.** Установщик русский. Перед обновлением выберите «Выйти» в трее старой версии. Wintun 0.14.1 имеет официальную подпись; EXE/MSI проекта не подписаны издателем.

Проверки сборки и тестов описаны в [VALIDATION.md](https://github.com/nr084/opencontrol-client-windows-releases/blob/v1.0.0/VALIDATION.md). Реальное подключение, полный цикл установки службы и целевая Windows 11 ARM VM на Mac ещё требуют проверки; номер 1.0 не означает, что эти проверки выполнены. В исходниках, пакетах и скриншотах нет личных соединений пользователя.

## English

- About: clickable home page, manual and daily GitHub update checks. New releases download automatically with SHA256 verification; silent installation waits for VPN disconnection, with no forced restart. Windows may request UAC.
- Available updates show a yellow tray exclamation badge and a version notification while retaining the VPN status badge.

- Consistent OpenControl Client branding across the window, installer, installation folder, shortcuts, startup entry, About and service display name. Updated information and warning icons in the installer.

- Russian is the first-launch default; saved language preferences are preserved.

- Fixed retry after an incorrect password: the completed IPC pipe is replaced after session cleanup, without restarting the service. Transient pipe contention is retried for up to 5 seconds; service errors now identify the failure category.
- Fixed GUID-based tray icon updates: connected sessions show a green dot with a white rim. Closing the window hides even an idle client; only tray Exit terminates it.
- Uses the installed Windows Segoe UI font. “Client” appears below the title; the area to the right of the switch shows failure reasons without a duplicate connection status. Enabling VPN requires no separate permission checkbox.
- Packages: `OpenControl-client-1.0.0-windows-{x86,x64,arm64}.msi`.

- ON / OFF switch without a Connect caption; equal-width tabs and adaptive rows for narrow windows.
- Larger green shield on a transparent background. Smooth contours, antialiased tray badges, 16–256 px ICO and 1024 px PNG; the UI image is filtered for the current DPI.
- Connected: green dot with a white rim. Disconnected: red cross. Tray menus localize from startup and immediately on language changes.
- Tray tooltip displays session Upload / Download totals. Automatic reconnect retains totals; a new session resets them.
- Finish opens the interface after an interactive installation. Windows sign-in starts the interface in the tray without connecting VPN automatically. Standard uninstall removes the startup entry.
- Choose any CFG in import, including first launch. Duplicates require Keep existing / Replace from file / Keep both. Replacement preserves local profile identity and certificate trust.
- Export defaults to **user.cfg**. Automatic synchronization is hourly, with manual Sync now; checks defer while connected or editing profiles.
- New or changed server certificates require confirmation; expired certificates require separate consent. Decisions are remembered for that fingerprint.

**Windows 10/11 · x86 / x64 / ARM64 · RU + EN in each MSI.** Russian installer. Exit the previous version from its tray menu before upgrading. Wintun 0.14.1 is officially signed; project EXE/MSI are not publisher-signed.

See [VALIDATION.md](https://github.com/nr084/opencontrol-client-windows-releases/blob/v1.0.0/VALIDATION.md) for actual checks. Real VPN, installed service lifecycle and the target Windows 11 ARM VM on Mac still need acceptance testing; version 1.0 does not imply those checks passed. No personal user connections are included in sources, packages or screenshots.

<details>
<summary>Screenshots / Скриншоты — RU</summary>

![connection ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/connection-ru.png)

![profiles ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/profiles-ru.png)

![settings ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/settings-ru.png)

![networks ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/networks-ru.png)

![about ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/about-ru.png)

</details>

<details>
<summary>Screenshots / Скриншоты — EN</summary>

![connection en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/connection-en.png)

![profiles en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/profiles-en.png)

![settings en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/settings-en.png)

![networks en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/networks-en.png)

![about en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v1.0.0/assets/about-en.png)

</details>

## Полная история изменений / Full changelog

Исторические примечания сохранены; актуальные правила 1.0 описаны выше. / Historical notes are preserved; current 1.0 behavior is described above.

<details>
<summary>v0.6.0</summary>

# OpenControl Client 0.6.0

## Русский

- Интерфейс работает без прав администратора. MSI устанавливает автоматически запускаемую службу OpenControl VPN (LocalSystem) для адаптера, маршрутов и DNS. Установка и удаление требуют повышения прав.
- Отрисовка на CPU через Windows GDI: убрана зависимость от OpenGL/GPU, из-за которой запуск в ARM64 VM мог завершаться без окна. Ошибки запуска теперь показываются явно.
- Переработаны главное окно и профили: центральный VPN-переключатель, равные кнопки, эмодзи, компактные поля и сворачиваемые параметры сертификата.
- Профили сортируются по названию; удаление — кнопкой с подтверждением. QR можно показать или сохранить в PNG без дополнительного флажка.
- Вкладка «Настройки»: импорт Kerio, экспорт всего списка в Users.cfg, двусторонняя синхронизация локального CFG, включая удаления и явное разрешение конфликтов.
- Зелёный щит увеличен с сохранением красного фона. Закрытие окна оставляет клиент в трее; завершение — через «Выйти».
- Штатное удаление через Windows удаляет программу, службу и ярлыки; профили и внешние CFG сохраняются.

Три MSI: **x86 / x64 / ARM64**. Каждый содержит **RU + EN**, установщик русский. Официальный подписанный Wintun 0.14.1. EXE/MSI проекта не имеют подписи издателя.

**Предварительный выпуск:** 57 тестов, три сборки и проверка содержимого MSI пройдены. Нативное CPU-окно проверено на x64. Установка новой службы под обычным пользователем, запуск в целевой Windows 11 ARM VM на Mac и подключение к реальному firewall ещё требуют проверки. Проверки перечислены в VALIDATION.md.

Перед обновлением выберите «Выйти» в меню трея старой версии. Личные соединения и пароли не включены в исходники и пакеты.

## English

- The interface runs without administrator permission. MSI installs an automatic LocalSystem OpenControl VPN service for the adapter, routes and DNS; installation/removal require elevation.
- CPU rendering through Windows GDI removes the OpenGL/GPU dependency that could prevent startup in ARM64 VMs. Startup failures now show an explicit error.
- Redesigned connection/profile views: central VPN switch, equal-width buttons, emoji labels, compact fields and collapsible certificate options.
- Profiles sort by name; deletion is a button with confirmation. Show QR or save PNG without an extra checkbox.
- Settings tab: Kerio import, whole-list Users.cfg export and bidirectional local CFG synchronization, including deletions and explicit conflict resolution.
- Larger green shield, retained red background. Closing the window keeps the client in the tray; Exit terminates it.
- Standard Windows uninstall removes program, service and shortcuts; profiles and external CFG files are preserved.

Three MSI packages: **x86 / x64 / ARM64**, each containing **RU + EN**, with a Russian installer. Official signed Wintun 0.14.1. Project EXE/MSI are not publisher-signed.

**Preview release:** 57 tests, three builds and extracted MSI checks passed; native CPU window startup was checked on x64. Installed service operation as an ordinary user, the target Windows 11 ARM VM on Mac and a real firewall connection still require acceptance testing. See VALIDATION.md.

Choose Exit in the old version's tray menu before upgrading. Personal connections and passwords are not included in sources or packages.

</details>

<details>
<summary>v0.5.0</summary>

# OpenControl Client 0.5.0

## Русский

- Новая вкладка **«Сети»**: общие IPv4-исключения для всех профилей, как в Android. До 128 CIDR-сетей, нормализация адресов и удаление повторов. Исключения применяются при подключении и обновлениях маршрутов сервера.
- Исключённые сети и DNS-серверы внутри них используют обычное подключение вне VPN. Изменение списка доступно после отключения VPN. IPv6-исключений и выбора приложений нет.
- **«Переподключиться» в трее** завершает старую сессию и очистку маршрутов, затем подключает тот же профиль. Повторные нажатия не создают параллельных соединений; «Отключить» и «Выход» отменяют перезапуск.
- Уведомление **«Туннель „Название профиля“ подключён»** после успешного соединения. Показ зависит от настроек уведомлений Windows.
- Зелёный щит в трее немного увеличен.
- Оформление установщика заново отрисовано в четырёхкратном разрешении для улучшения чёткости логотипа и текста.

Три MSI: x86, x64, ARM64; оба языка приложения RU/EN в каждом. Установщик на русском.
Перед обновлением выберите **«Выход» в меню трея** старой версии.

45 автоматических тестов, Clippy без предупреждений, три нативные сборки и проверки MSI.
EXE/MSI не подписаны издателем; Wintun 0.14.1 имеет официальную подпись. Проверяйте SHA256SUMS.

Предварительная версия: синтетические тесты и рендер не заменяют проверку реального VPN, системных уведомлений, установки/обновления и отображения MSI на физических мониторах с разным DPI. Подробности — в VALIDATION.md.

## English

- New **Networks** tab: shared IPv4 exclusions for all profiles, matching Android. Up to 128 CIDR networks with address normalization and deduplication. Applied on connection and server route updates.
- Excluded networks and DNS servers inside them use the regular connection outside VPN. Disconnect before editing. No IPv6 exclusions or per-app routing.
- Tray **Reconnect** waits for the previous session and route cleanup, then reconnects the same profile. Repeated clicks cannot create parallel sessions; Disconnect and Exit cancel a pending restart.
- **Tunnel “Profile name” connected** notification after successful connection. Windows notification settings control visibility.
- Slightly larger green tray shield.
- Installer artwork freshly rendered at four times the previous resolution to improve logo and text clarity.

Three MSI packages: x86, x64 and ARM64; both RU/EN application languages in every package. Russian installer.
Choose **Exit in the old version's tray menu** before upgrading.

45 automated tests, warning-free Clippy, three native builds and MSI checks.
EXE/MSI have no publisher signature; Wintun 0.14.1 carries its official signature. Verify SHA256SUMS.

Preview: synthetic tests and rendering do not replace live VPN, native notifications, installation/upgrade and physical-monitor MSI DPI acceptance. See VALIDATION.md.

</details>

<details>
<summary>v0.4.0</summary>

# OpenControl Client 0.4.0

## Русский

- После подключения индикатор ожидания больше не вращается.
- Включена поддержка буфера обмена Windows: копирование, вырезание и вставка в редактируемых полях. Вставка пароля работает; скрытый пароль не копируется в буфер.
- Исправлена смена темы: фон, текст и элементы управления переключаются согласованно.
- Добавление профиля сразу сохраняется. Удаление корректно обновляет выбор и профиль по умолчанию; после удаления последнего остаётся пустая форма. Ошибка сохранения отменяет изменение.
- Щит в трее немного увеличен, метка соединения уменьшена. Значок остаётся в трее всегда, крестик окна скрывает приложение.
- Сохранены фирменный установщик, ярлыки «Пуск» и рабочего стола, HiDPI, импорт Kerio и RU/EN.

Три MSI: x86, x64, ARM64; оба языка приложения в каждом. Установщик на русском.
Перед обновлением выберите **«Выход» в меню трея** старой версии.

37 автоматических тестов, три нативные сборки и проверки MSI. Официальный подписанный Wintun 0.14.1; EXE/MSI не подписаны издателем. Проверяйте SHA256SUMS.
Предварительный выпуск: результаты и границы проверок описаны в VALIDATION.md. Чистая установка/обновление, интерактивный буфер Windows, физический ARM64 и реальное VPN-подключение требуют отдельной приёмки.

## English

- The progress indicator stops once connected.
- Enabled Windows clipboard support: copy, cut and paste in editable fields. Password paste works; hidden passwords are not exported to the clipboard.
- Fixed theme changes so backgrounds, text and controls switch together.
- Adding a profile saves immediately. Deletion updates selection and the default profile; deleting the last profile leaves an empty form. Failed saves roll back the change.
- Slightly enlarged the tray shield and reduced its status badge. The tray icon remains present; closing the window hides the application.
- Branded installer, Start menu and desktop shortcuts, HiDPI, Kerio import and RU/EN remain available.

Three MSI packages: x86, x64 and ARM64; both application languages in each. Russian installer.
Choose **Exit in the old version's tray menu** before upgrading.

37 automated tests, three native builds and MSI checks. Official signed Wintun 0.14.1 is included; EXE/MSI have no publisher signature. Verify SHA256SUMS.
Preview release: see VALIDATION.md for evidence and limitations. Clean install/upgrade, interactive Windows clipboard, physical ARM64 and live VPN acceptance remain pending.

</details>

<details>
<summary>v0.3.0</summary>

# OpenControl Client 0.3.0

## Русский

- Исправлены значки ярлыков рабочего стола и меню «Пуск»: MSI теперь содержит корректный PE-ресурс значка с расширением `.exe`.
- Исправлен значок панели задач: окно явно назначает большой значок Windows в дополнение к значку заголовка.
- Значок трея существует постоянно с запуска до выхода, в том числе без VPN. Зелёная галочка означает подключение, красный крестик — отсутствие соединения.
- Крестик окна скрывает приложение в трей без отключения VPN. Левый щелчок по значку открывает окно, «Выход» в меню трея отключает VPN и завершает клиент. Windows может поместить значок в область скрытых значков; его положение регулируется настройками панели задач.
- Главное окно стало компактнее: статус, профиль, сервер и логин, кнопка настройки и сохранение пароля доступны на экране подключения.
- Фирменные изображения установщика в стиле OpenControl Client: логотип, тёмно-зелёная панель и зелёные акценты. Ярлыки «Пуск» и рабочего стола устанавливаются по умолчанию.
- Сохранены автоматический запрос сертификата с подтверждением доверия, импорт Kerio с сохранёнными паролями, HiDPI и RU/EN.

Три MSI: x86, x64, ARM64; оба языка приложения в каждом. Установщик на русском.
Перед обновлением выберите **«Выход» в меню трея** старой версии. Если старый ярлык был
закреплён на панели задач вручную, после обновления при необходимости закрепите новый.

30 автоматических тестов, три сборки и проверки MSI. EXE/MSI не подписаны издателем;
встроен официальный подписанный Wintun 0.14.1. Проверяйте SHA256SUMS.
Предварительный выпуск: реальный корпоративный VPN, чистая установка/обновление,
физический ARM64 и интерактивная проверка панели задач/трея требуют приёмки.

## English

- Fixed desktop and Start menu shortcut icons: the MSI now embeds a valid PE icon resource with the `.exe` extension.
- Fixed the taskbar icon: the window explicitly sets the Windows large icon in addition to its title-bar icon.
- The tray icon exists from startup until Exit, even with no VPN connection. A green check means connected; a red cross means disconnected.
- Closing the window hides it to the tray without disconnecting VPN. Left-click opens it; tray Exit disconnects VPN and quits. Windows may place the icon in notification overflow; placement is controlled by taskbar settings.
- A more compact main window groups status, profile, server, username, Configure and Remember password on the connection screen.
- OpenControl Client installer artwork: original logo, dark green panel and green accents. Start menu and desktop shortcuts are installed by default.
- Automatic certificate review with explicit trust confirmation, saved-password Kerio import, HiDPI and RU/EN remain available.

Three MSI packages: x86, x64 and ARM64; both application languages in every package.
The installer is Russian. Choose **Exit in the old version’s tray menu** before upgrading.
If you manually pinned an old shortcut to the taskbar, repin the updated shortcut if needed.

30 automated tests, three native builds and MSI checks. EXE/MSI have no publisher signature;
official signed Wintun 0.14.1 is included. Verify SHA256SUMS.
Preview release: live corporate VPN, clean installation/upgrade, physical ARM64 and
interactive taskbar/tray acceptance remain pending.

</details>

<details>
<summary>v0.2.0</summary>

# OpenControl Client 0.2.0

## Русский

- При нажатии «Подключиться» сертификат автоматически запрашивается, если доверие ещё не настроено. После однократной проверки SHA-256 и подтверждения подключение продолжается автоматически. Пароль до подтверждения не передаётся.
- Изменившийся сертификат требует нового подтверждения; просроченный — отдельного согласия. Проверка TLS не отключается.
- После успешного подключения окно скрывается в трей. Зелёная галочка означает активный VPN, красный крестик — отсутствие соединения. Левый щелчок открывает окно; меню содержит открытие, отключение и выход.
- HiDPI: PerMonitorV2, масштабируемые значки состояния; проверен программный рендер RU/EN на 100/125/150/200% и изменение масштаба одного контекста.
- Ярлыки в меню «Пуск» и на рабочем столе устанавливаются по умолчанию.
- Импорт соединений Kerio, включая сохранённые D3S-пароли с последующей защитой DPAPI, сохранён. Личные соединения в пакет не включены.
- Три MSI: x86, x64, ARM64. В каждом приложении есть русский и английский; установщик на русском. Без пользовательского split tunneling.

Rust stable 1.99.1, OpenControl Protocol 0.2.0, официальный подписанный Wintun 0.14.1.
EXE/MSI не имеют подписи издателя. Проверяйте SHA256SUMS. Перед обновлением закройте клиент.
Предварительный выпуск: реальный корпоративный VPN, установка/обновление на чистой Windows,
физический ARM64 и перенос окна между физическими мониторами требуют приёмки.

## English

- Connect automatically retrieves the server certificate when trust is not configured. After a one-time SHA-256 review and trust confirmation, connection continues automatically. No password is sent before confirmation.
- Replaced certificates require a new review; expired certificates require separate consent. TLS verification remains enabled.
- Successful connections hide the window to the tray. A green check means connected; a red cross means disconnected. Left-click opens the window; the menu provides Open, Disconnect and Exit.
- HiDPI: PerMonitorV2 and scaled status icons; RU/EN headless rendering checked at 100/125/150/200%, including scale changes in one context.
- Start menu and desktop shortcuts are installed by default.
- Kerio connection import, including saved D3S passwords rewrapped with DPAPI, remains available. No personal connections are included.
- Three MSI packages: x86, x64 and ARM64. Every application includes Russian and English; the installer is Russian. No user split-tunneling controls.

Rust stable 1.99.1, OpenControl Protocol 0.2.0, official signed Wintun 0.14.1.
EXE/MSI have no publisher signature. Verify SHA256SUMS and close the client before upgrading.
Preview release: live corporate VPN, clean Windows installation/upgrade, physical ARM64 and
moving between physical mixed-DPI monitors still require acceptance.

</details>

<details>
<summary>v0.1.1</summary>

# 0.1.1 — Kerio import / Импорт Kerio

## Русский

Добавлена возможность импорта user.cfg из Kerio VPN: предложение при первом запуске,
предварительный просмотр и ручной выбор файла во вкладке «Профили». Перенос выполняется
только после подтверждения пользователя. Названия, серверы, порты, логины и сохранённые пароли D3S (с защитой DPAPI); без переноса
автозапуска и доверия сертификатам. Дубликаты пропускаются, исходный файл
не изменяется. Альтернативные серверы становятся отдельными профилями.

Windows 10/11, x86/x64/ARM64, один MSI на архитектуру, приложение RU/EN. 24 автоматических теста.
Это предварительная версия. Реальное корпоративное подключение и установка/обновление
на чистых Windows ещё требуют приёмки. EXE/MSI без подписи издателя;
официальный Wintun имеет действительную подпись WireGuard LLC.

## English

Added Kerio VPN user.cfg import: first-launch offer, review before confirmation,
and manual file selection in Profiles. Import runs only after user confirmation.
Imports names, servers, ports, usernames and saved D3S passwords protected with DPAPI, without startup settings
or certificate trust. Skips duplicates and leaves the source file unchanged.
Alternative servers become separate profiles.

Windows 10/11, x86/x64/ARM64, one MSI per architecture, RU/EN application. 24 automated tests.
Preview release: real corporate connections and clean Windows install/upgrade
still require acceptance. EXE/MSI have no publisher signature;
official Wintun binaries carry valid WireGuard LLC signatures.

</details>
