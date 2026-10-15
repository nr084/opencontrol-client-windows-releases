# OpenControl Windows 0.4.0

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
