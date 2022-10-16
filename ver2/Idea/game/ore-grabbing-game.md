---
title: "鉱石つかみゲーム"
date: "2022/10/17"
author: "Takunology"
---

# 概要
鉱石つかみゲームとは, チェストブロック内に出現する鉱石（鉄インゴット, 金インゴット, ダイヤモンド, エメラルドなど）をつかんで自分のインベントリに持ってくるゲームです. 

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/idea/game/media/ore-grabbing-game.gif)

[Wait] メソッドを使用すれば, 鉱石が出現するスピードを調整する事ができます.

# サンプルコード

```cs
using MinecraftConnection;

var commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
var chestPos = new Position(2, -60, -3);
var rnd = new Random();

while (true)
{
    Random rand = new Random();
    var myItem = new List<ItemStack>
    {
        new ItemStack((ushort)rand.Next(0, 27), "diamond", 1),
        new ItemStack((ushort)rand.Next(0, 27), "gold_ingot", 1),
        new ItemStack((ushort)rand.Next(0, 27), "iron_ingot", 1),
        new ItemStack((ushort)rand.Next(0, 27), "redstone", 1)
    };
    commands.SetChestItems(chestPos, myItem);
    commands.Wait(100);
}
```

# 攻略法
P氏によれば, Shift + クリック連打で鉱石つかみ放題らしい！