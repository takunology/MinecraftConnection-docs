---
title: "SetItems メソッド"
date: "2023/08/31"
author: "Takunology"
---

# 概要
作成したチェストブロック（シュルカーボックス）のインスタンスにアイテムを書き込みます.

## 引数

|変数名|型|説明|
|--|--|--|
|items|List&lt;[ItemStack](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=ItemStack)&gt;|上書きしたいアイテムのリスト|


# 使い方
作ったチェストブロックのインスタンスにアイテムを上書きしたいときに使います. 例えば他の座標にあるチェストのアイテムを `GetItems()` メソッドで取得し, それを `SetItems()` メソッドを用いてコピーしたりもできます.

```cs
using MinecraftConnection;
using MinecraftConnection.Block;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
ChestBlock blockA = new ChestBlock(29, -60, -67);
ChestBlock blockB = new ChestBlock(29, -60, -71);

var items = blockA.GetItems();
blockB.SetItems(items);
```

上記の例では, 座標 `29, -60, -67` にあるチェストのアイテムを, 座標 `29, -60, -71` にあるチェストにコピーできます. 

また, 任意のアイテムを書き込みたい場合は下記のように `ItemStack` 型のリストを作成して, `SetItems()` の引数に代入することで, 実装できます.

```cs
ChestBlock blockB = new ChestBlock(29, -60, -71);

ItemStack items = new List<ItemStack>
{
    new ItemStack(0, "diamond", 2),
    new ItemStack(1, "gold_ingot", 4),
    new ItemStack(2, "iron_ingot", 16),
    new ItemStack(3, "redstone", 32)
};

blockB.SetItems(items);
```

書き込んだ例

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/Struct/media/ItemStack_01.webp)



