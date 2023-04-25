# <a href="https://github.com/OnlyRad/Telegram">Telegram</a>

## <a href="https:t.me/onlyRad">Telegram Channel</a> | <a href="https://github.com/OnlyRad">GitHub</a> | <a href="https:rubika.ir/TheLinux">Rubika Channel</a>

### لطفا مراحل را با دقت انجام بدید که به مشکل نخورید

## نصب کتابخونه و نحوه ایمپورت آن

```python
pip install pyrogram
```
```python
from pyrogram import Client

app = Client(
    "اسم سشن",
    "API-ID",
    "API-Hash",
    "Bot-Token"
)
```
## ساخت بات ساده برای جواب دادن

```python
@app.on_handler()
async def start(client , message):
    await app.send_message(message.chat.id , "متن پیامتون")
app.run()
```
### حتما حواستون باشه بصورت ایسینک باشه



## ساخت کیبورد اینلاین

```python
@app.on_message()
async def start(client , message):
    text = message.text
    mark = InlineKeyboardMarkup(
        [
            [
                InlineKeyboardButton("Config GER🇩🇪","GER"),
                InlineKeyboardButton("Config USA🇺🇸" , "USA"),
                InlineKeyboardButton("Config CAN🇨🇦", "CAN"),
            ] ,
            [
                InlineKeyboardButton("Config","Config")
            ],
            [
                InlineKeyboardButton("Telegram",url="t.me/OnlyRad"),
                InlineKeyboardButton("Rubika",url="rubika.ir/TheLinux"),
                InlineKeyboardButton("GitHub", url="github.com/OnlyRad")
            ]
        ]
    )
        
    await app.send_message(message.chat.id , "متن پیامتون")
    
app.run()
```
## اگر میخواید از کیبورد ها استفاده کنید باید این قسمت رو به اول کدتون اضافه کنید
```python
from pyrogram.type import *
```

#### خب اینجا به کدهای قبلی یه سری متود اضافه کردیم ولی یه مشکلی هست<br>
مشکل اینه که کاربر روی کیبورد کلیک کنه اتفاقی نمیوفته<br>
توی کد پایین این مشکلو حل میکنیم
```python
@app.on_callback_query()
def Callback(client, call):
    if call.data == 'GER':
        app.edit_message_text(call.from_user.id , call.message.id , "متن پیام نشان دهنده"
```

------
## Forward Message
 پارامتر های مورد نیاز برای فروارد مسیج:
 - چت آیدی مورد نظر برای ارسال پیام
 - چت آیدی منبع<br>
 تا اینجا کافیه بقیه پارامتر ها برای  موارد خاص هستند
-----

### به نمونه ی زیر دقت کنید

```python
from pyrogram import client

app = client(
    "اسم سشن",
    "API-ID",
    "API-Hash",
    "Bot-Token"
)
@app.on_message()
async def forwardmessage(client , message):
    await app.forward_messages("Chat ID" , "From chat ID")
```

------
## Send Photo
پارامتر های مورد نیاز برای ارسال عکس:
- چت آیدی مورد نظر برای ارسال عکس
- آدرس فایل مورد نظر / میتونید آدرس url بهش بدید تا ارسال کنه
- کپشن فایل (اختیاری)
- برای بولد کردن و مارک داون های html
-----

### به نمونه ی زیر دقت کنید
```python
from pyrogram import client

app = client(
    "اسم سشن",
    "API-ID",
    "API-Hash",
    "Bot-Token"
)
@app.on_message()
async def send_photo(client,message):
    await app.send_photo("Chat ID","Photo/URL Photo","Caption","Parse_mode")
```
