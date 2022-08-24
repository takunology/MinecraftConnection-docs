---
title: "MinecraftCommands クラス"
date: "2022/08/24"
author: "Takunology"
---

# 概要
名前空間 : `MinecraftConnection`

マインクラフトサーバへコマンドを送信するためのインスタンスを作ることができます.

**コンストラクタ**

|引数名|型|説明|
|--|--|--|
|address|string|コマンド送信先のマンクラフトサーバのアドレス (IP / DNS)|
|port|ushort|RCON のポート番号|
|password|string|RCON の接続パスワード|

# 使い方
サーバへの接続方法は IP アドレスを使用した方法と, DNS を使用した方法の2種類が扱えます. 

```cs
// ローカルホストへの接続例
MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "passwd");

// hoge.minecraft-server.com への接続例
MinecraftCommands commands = new MinecraftCommands("hoge.minecraft-server.com", 25575, "passwd");
```

# 素朴な疑問

**Q. ExtendedSocketException の例外が発生します**

マイクラサーバに接続できなかったときに表示される例外（エラー）です. サーバの接続先アドレス, ポート番号, パスワードが合っているかを確認してください. 詳細は[こちら](https://www.mcwithcode.com/QandA)を確認してください. 
