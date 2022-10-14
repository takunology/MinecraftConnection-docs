---
title: "SetSubTitle メソッド"
date: "2022/10/15"
author: "Takunology"
---

# 概要
任意の文字列をサブタイトルとして設定することができます.

## 引数

|変数名|型|説明|
|--|--|--|
|subTitle|string|表示させたいサブタイトル|

# 使い方
表示したいサブタイトルを引数に代入して, [DisplayTitle()](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=MinecraftCommands%2FMethod&fileName=DisplayTitle)を実行します. 

```cs
MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
commands.SetSubTitle("~hugahuga~");
commands.DisplayTitle("Hoge");
```

実行結果

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/SetSubTitle.webp)

# 素朴な疑問

**Q. SetSubTitle()メソッドだけで文字を表示できないの？**

タイトルコマンドを使用しないと文字が表示されません. 必ず [DisplayTitle()](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=MinecraftCommands%2FMethod&fileName=DisplayTitle) メソッドと併用してください.