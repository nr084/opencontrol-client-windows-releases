# OpenControl Windows 0.2.0

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
