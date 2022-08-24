---
title: "DisplayMessage メソッド"
date: "2022/08/24"
author: "Takunology"
---

# 概要
任意の文字列をチャット欄に表示させることができます.

**引数**

|変数名|型|説明|
|--|--|--|
|message|string|表示させたいメッセージ|

# 使い方
表示したい文字を引数に入れて, チャット欄に文字列を表示します. DisplayTitle とは異なりアニメーション効果がないので, 連続して表示したいときに便利です.

```cs
MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "passwd");

commands.DisplayMessage("Hello!");
commands.DisplayMessage("from");
commands.DisplayMessage("CSharp!");
```

実行結果の例

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/DisplayMessage_01.webp)

# 素朴な疑問

**Q. 指定したプレイヤーのみに表示できる？**

できますが, まだ MinecraftConnection には実装していません.