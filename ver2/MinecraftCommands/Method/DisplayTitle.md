---
title: "DisplayTitle メソッド"
date: "2022/08/24"
author: "Takunology"
---

# 概要
任意の文字列を画面いっぱいに表示させることができます.

## 引数

|変数名|型|説明|
|--|--|--|
|title|string|表示させたいタイトル|

# 使い方
表示したい文字を引数に入れて, ゲーム画面いっぱいに文字列を表現します. 文字列の表示の際に, フェードインとフェードアウトのアニメーション効果があるので, 連続して表示させることはできません.

```cs
MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "passwd");
// 英語の文字列を表示する
commands.DisplayTitle("Hello, Minecraft!");
// 日本語の文字列を表示する
commands.DisplayTitle("冒険にでかけよう！");
```

実行結果の例

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/DisplayTitle_01.webp)

# 素朴な疑問

**Q. フェードインやフェードアウトの時間は設定できる？**

できますが, まだ MinecraftConnection には実装していません.