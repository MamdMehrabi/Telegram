# <a href="https://github.com/OnlyRad/Telegram">Telegram</a>

<a href="https:t.me/onlyRad">Telegram Channel</a> | <a href="https://github.com/OnlyRad">GitHub</a> | <a href="https:rubika.ir/TheLinux">Rubika Channel</a>

لطفا مراحل را با دقت انجام بدید که به مشکل نخورید

نصب کتابخونه و نحوه ایمپورت آن

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
 ساخت بات ساده برای جواب دادن

```python
@app.on_handler()
async def start(client , message):
    await app.send_message(message.chat.id , "متن پیامتون")
app.run()
```
 حتما حواستون باشه بصورت ایسینک باشه



ساخت کیبورد اینلاین(کیبورد داخلی)

```python
from pyrogram.type import *
@app.on_message()
async def start(client , message):
    mark = InlineKeyboardMarkup(
        [
            [
                InlineKeyboardButton("نام دکمه","CallBackData")
        ]
    )
        
    await app.send_message(message.chat.id , "متن پیامتون",replymarkup=mark)
    
app.run()
```
خب اینجا باید جوابی به کال بک دیتا بدیم(یکی از پارامتر های اینلاین کیبورد باتن)<br>
اگر  اینکارو انجام ندید  وقتی کاربر روی دکمه ها کلیک کنه هیچ اتفاقی نمیوفته پس حتما اضافه اش کنید به سورستون

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

به نمونه ی زیر دقت کنید

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
به نمونه ی زیر دقت کنید
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
لطفا برای حمایت از من استار یادتون نره و صفحه رو فالو کنید که بزودی آپدیت های خفنی میزارم
