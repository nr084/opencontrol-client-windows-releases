# OpenControl Windows 0.3.0

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
