# 📦 CashbackBot Server Guide

Полная инструкция по подключению, запуску и управлению ботом на сервере.

---

## 🔐 Подключение к серверу

### Команда для входа по SSH:

```bash
ssh root@45.155.207.128
```
Пароль:
```bash
7344c12242e6e6!
```

📁 Структура проекта

После входа в систему, перейдите в директорию проекта:
```bash
cd /home/CashbackBot
```
⚙️ Активация виртуального окружения

Перед запуском бота или сервера нужно активировать окружение:
```bash
source venv/bin/activate
```
🚀 Запуск
1. Запуск FastAPI-сервера (обработчик Admitad):
```bash
pkill -f "uvicorn cashback_bot.admitad_api.main:app"
nohup uvicorn cashback_bot.admitad_api.main:app --host 0.0.0.0 --port 8000 > logs/web.log 2>&1 &
```
2. Запуск Telegram-бота:
```bash
pkill -f "cashback_bot.bot"
nohup python -m cashback_bot.bot > logs/bot.log 2>&1 &
```

📄 Просмотр логов в реальном времени

Лог веб-сервера (Admitad Webhook):
```bash
tail -f logs/web.log
```
Лог Telegram-бота:
```bash
tail -f logs/bot.log
```
💀 Остановка процессов вручную

Если необходимо завершить процесс:

Остановить веб-сервер:
```bash
pkill -f "uvicorn cashback_bot.admitad_api.main:app"
```
Остановить Telegram-бота:
```bash
pkill -f "cashback_bot.bot"
```
