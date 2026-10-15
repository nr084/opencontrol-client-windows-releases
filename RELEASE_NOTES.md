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