# flutter_telegram_login

A Flutter plugin providing the required functions in order to implement login with Telegram.

## Usage

To use this plugin, add `flutter_telegram_login` as a [dependency in your pubspec.yaml file](https://flutter.dev/platform-plugins/).

### Example

<?code-excerpt "basic.dart (basic-example)"?>
``` dart
import 'package:flutter/material.dart';
import 'package:flutter_telegram_login/flutter_telegram_login.dart';

final TelegramLogin telegramLogin = TelegramLogin(<PHONE_NUMBER:String>, <BOT_ID:String>, <BOT_DOMAIN:String>);

void main() => runApp(
  MaterialApp(
    home: Material(
      child: Center(
        child: Column(
          children: [
            ElevatedButton(
                onPressed: telegramLogin.loginTelegram,
                child: const Text("loginTelegram")
            ),
            ElevatedButton(
                onPressed: () async {
                  var success = await telegramLogin.checkLogin();
                  print(success);
                },
                child: const Text("checkLogin")
            ),
            ElevatedButton(
                onPressed: () async {
                  var data = await telegramLogin.getData();
                  print(data);
                  if (data) {
                    print(telegramLogin.userData);
                  }
                },
                child: const Text("getData")
            ),
            ElevatedButton(
                onPressed: () async {
                  await telegramLogin.telegramLaunch();
                },
                child: const Text("openTelegram")
            ),
          ]
        )
      )
    )
  )
);
```
