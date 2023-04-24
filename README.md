# <a href="https://github.com/OnlyRad/Telegram">Telegram</a>

## How Created bot Telegram

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
#### خب اینجا به کدهای قبلی یه سری متود اضافه کردیم ولی یه مشکلی هست<br>
مشکل اینه که کاربر روی کیبورد کلیک کنه اتفاقی نمیوفته<br>
توی کد پایین این مشکلو حل میکنیم
```python
@app.on_callback_query()
def Callback(client, call):
    if call.data == 'GER':
        app.edit_message_text(call.from_user.id , call.message.id , "متن پیام نشان دهنده"
```
