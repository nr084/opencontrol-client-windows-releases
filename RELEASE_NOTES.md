# OpenControl Windows 0.6.0

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

<details>
<summary>Скриншоты 0.6.0 — демонстрационные данные</summary>

![connection ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/connection-ru.png)

![profiles ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/profiles-ru.png)

![settings ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/settings-ru.png)

![networks ru](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/networks-ru.png)

</details>

<details>
<summary>0.6.0 screenshots — demo data</summary>

![connection en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/connection-en.png)

![profiles en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/profiles-en.png)

![settings en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/settings-en.png)

![networks en](https://raw.githubusercontent.com/nr084/opencontrol-client-windows-releases/v0.6.0/assets/networks-en.png)

</details>
