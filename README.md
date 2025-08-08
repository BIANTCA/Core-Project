### bot.py – Telegram Bot Core

**bot.py** is a single-file, lightweight Python wrapper around the official Telegram Bot API.  
It provides a clean, reusable `tgBot` class that handles:

- sending / receiving messages, media, stickers, polls  
- inline keyboards, webhooks, file uploads  
- error logging and auto-retry  
- rate-limiting with semaphore (optional)

Notes:
 - you can get api from [@botfather](https://t.me/BotFather) at [Telegram](https://telegram.com/)

No external frameworks – just Python 3.8+, `requests`, and standard library.

---

#### Quick Start

```python
from bot import tgBot

bot = tgBot("123456:ABC-DEF...")
bot.send_message(chat_id=123, text="Hello World")
```

#### class tgBot

| Method | Purpose |
|---|---|
| `get_me()` | Retrieve bot info |
| `send_message(chat_id, text, **opts)` | Send text message |
| `send_photo(chat_id, file, caption=None)` | Send image |
| `send_video(chat_id, file, caption=None)` | Send video |
| `get_updates(offset=None, limit=100)` | Pull updates |
| `read_message()` | Return one unread message |
| `delete_message(chat_id, msg_id)` | Delete message |
| `get_chat_member(chat_id, user_id)` | Get member status |

#### Usage Example
```python
from bot import tgBot

bot = tgBot("YOUR_BOT_TOKEN")

for upd in bot.read_message() or []:
    msg = upd.get("message")
    if msg and msg.get("text") == "/start":
        bot.send_message(msg["chat"]["id"], "Hello from bot.py!")

```
