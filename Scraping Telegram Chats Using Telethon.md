# 📚 Getting Telegram API ID and Hash

To use the Telegram API, you need a Telegram account. Once you have one, you can obtain your API ID and hash from the following link:

[https://my.telegram.org/auth?to=apps](https://my.telegram.org/auth?to=apps)

---

## Authorization

Home FAQ Apps API Protocol Delete Account or Manage Apps  
Log in here to manage your apps using the Telegram API or delete your account.  
Enter your phone number and Telegram will send a confirmation code via the Telegram app (not SMS).

- Your Phone Number  
  Please enter your number in international format.

---

# 📚 Example: Scraping a Telegram Chat Using Telethon

Make sure Python and pip are installed on your system.  
Then, install the required libraries:

```bash
$ pip install pandas
$ pip install telethon
```

```python
import pandas as pd
from telethon import TelegramClient

# Insert your API ID, hash, and the chat link to scrape messages
name = 'test'
api_id = '<api_id>'
api_hash = '<api_hash>'
chat = '<chat_link>'

data = []

# Connect to the Telegram server
async def some_function():
    async with TelegramClient(name, api_id, api_hash) as client:
        async for message in client.iter_messages(chat):
            data.append([message.sender_id, message.text])

df = pd.DataFrame(data, columns=['SENDER', 'MESSAGE'])
df.to_csv('test.csv', encoding='utf-8')
```

The example above asynchronously fetches messages from a specified Telegram chat using Telethon.  
Fetched messages are stored in a DataFrame and exported to a CSV file using `to_csv()`.
