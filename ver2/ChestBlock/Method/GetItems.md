---
title: "GetItems メソッド"
date: "2023/08/31"
author: "Takunology"
---

# 概要
作成したチェストブロック（シュルカーボックス）の中に入っている, アイテムデータを取得します.

## 引数
なし

# 使い方
作ったチェストブロックのインスタンスの持つアイテムデータを取得するときに使います. 事前にチェストの中にアイテムを入れておき, そのアイテムの数量やID, どのスロット番号に配置されているかも取得できます.

```cs
using MinecraftConnection;
using MinecraftConnection.Block;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
ChestBlock block = new ChestBlock(29, -60, -72);

var items = block.GetItems();
items.ForEach(x => Console.WriteLine($"{x.Id}\t{x.Count}"));
```

下記画像のようにアイテムが配置されている場合の出力例.

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/ChestBlock/media/GetItems_01.webp)

```txt
minecraft:iron_ingot    1
minecraft:iron_ingot    1
minecraft:iron_ingot    1
minecraft:iron_ingot    3
```
