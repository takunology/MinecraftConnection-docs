---
title: "SendCommand メソッド"
date: "2022/10/15"
author: "Takunology"
---

# 概要

任意のコマンドを実行することができます. 

## 引数

|変数名|型|説明|
|---|---|---|
|command|string|任意のコマンド|

## 戻り値
コマンドの実行結果が string 型で返って来ます.

# 使い方
引数には Minecraft で用意されているコマンドを入力します。

```cs
using MinecraftConnection;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");

// ゲーム設定を変更する（昼夜サイクルのオフ）
commands.SendCommand("gamerule doDaylightCycle false");
```

戻り値ありでコンソール出力する場合は変数などを使用して受け取ることができます.

```cs
var result = commands.SendCommand("gamerule doDaylightCycle false");
Console.WriteLine(result);
```

実行結果

```txt
Gamerule doDaylightCycle is now set to: false
```

```cs
// エンティティのデータを取得する例（プレイヤーの座標）
var result = commands.SendCommand("data get entity Takunology Pos");
Console.WriteLine(result);
```

実行結果

```txt
Takunology has the following entity data: [213.79175149505863d, -42.0d, -184.95366446483624d]
```

また, 存在しないコマンドを実行した場合はその旨を知らせる実行結果が返って来ます.

```cs
// 存在しないコマンド
commands.SendCommand("​give tak moneyAndTime10000000");
```

```txt
Unknown or incomplete command, see below for error?give tak moneyAndTime10000000<--[HERE]
```

# 素朴な疑問

**Q. 先頭に`/`（スラッシュ）つけなくていいの？**
スラッシュはつけても、つけなくてもコマンドを実行することができます。