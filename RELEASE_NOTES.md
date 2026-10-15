# OpenControl Windows 0.5.0

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
