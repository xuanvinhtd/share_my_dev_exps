# How to setup telegram bot with firebase

## Setup Environment

- [Guide](setupcicdenv.md)

## Setup CI/CD for your project

- [For Flutter](cicdflutter.md)
- [For React Native](cicdrn.md)

## Setup Telegram bot

- [Add fastlane-plugin-telegram](https://github.com/sergpetrov/fastlane-plugin-telegram):

```
fastlane add_plugin telegram
```

- Add script to your Fastfile of ios and android:

```
telegram(
      token: "1974698014:AAHlfaULucAHfgGqnCDzF9V83CBaVVX0x5g",
      chat_id: '1927830626',
      text: "Đã lên bản build iOS cho App XXXX trên Firebase. cc: @QC, @Teser"
     )
```

- `Token`: this is a token of your bot, your can create a bot and get token by [BotFather](https://t.me/botfather)
- `chat_id`: this is a token of group chat.
You must to add your bot into a group and after that you run this api on browser to get group id.

```
https://api.telegram.org/botXXX:YYY/getUpdates
```

Result:

```
"chat":{"id":-1001577933444,..."  -> this is a id: -1001577933444
```

XXX, YYY in your `Token` above.

ex:
```
https://api.telegram.org/bot1974698014:AAHlfaULucAHfgGqnCDzF9V83CBaVVX0x5g/getUpdates
```

