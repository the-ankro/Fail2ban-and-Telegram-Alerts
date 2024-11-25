# Fail2ban-and-Telegram-Alerts
Безопасный доступ по SSH с помощью Fail2ban и оповещений Telegram

**Настройки:**    
- Бан на 7 дней (604800 секунд)
- 3 попытки за 10 минут
- Группировка уведомлений (не чаще 1 раза в 5 минут)
- IP сервера в хэштегах для удобного поиска

## Установка: 
1. ```curl -O https://github.com/the-ankro/Fail2ban-and-Telegram-Alerts/blob/main/fail2bantelegram.sh && chmod +x fail2bantelegram.sh```

2. ```./fail2bantelegram.sh```

## Команды управления:
**Посмотреть все забаненные IP**
- fail2ban-client status sshd

**Разбанить конкретный IP**
- fail2ban-client set sshd unbanip IP_ADDRESS

**Разбанить все IP**
- fail2ban-client unban --all

**Изменить время бана (в секундах)**
- fail2ban-client set sshd bantime 86400  # установить бан на 1 день

**Остановить/запустить fail2ban**
- systemctl stop fail2ban
- systemctl start fail2ban

**Редактировать конфигурацию**
- nano /etc/fail2ban/jail.local

**Например, чтобы установить:**
 - Бан на 1 день: bantime = 86400
 - Считать попытки за 30 минут: findtime = 1800
 - Максимум 5 попыток: maxretry = 5

**После изменений перезапустить**
- systemctl restart fail2ban
