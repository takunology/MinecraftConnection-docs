---
title: "ItemStack 構造体"
date: "2022/08/17"
author: "Takunology"
---

# 概要
名前空間 : `MinecraftConnection`

アイテムスロット番号, アイテムID, アイテムの数量の3つのデータを持つ型（アイテムスタック）を扱うことができます.

メンバ変数

|変数名|型|説明|
|--|--|--|
|Slot|ushort|アイテムスロットの番号|
|Id|string|アイテムID（アイテム名）|
|Count|ushort|アイテムの数量|

コンストラクタ

|引数|型|説明|
|--|--|--|
|slot|ushort|アイテムスロットの番号|
|id|string|アイテムID（アイテム名）|
|count|ushort|アイテムの数量|

# 使い方
コンストラクタの引数にはスロット番号, アイテムID, 数量の3つのパラメータの入力が必要です. 

チェスト内のアイテムやエンティティが持つアイテムを取得したり, 書き換えたりするときに使用できます. 特に, リスト化することで複数のアイテム要素を保持することができます.

```cs
// スロット番号 0 にダイヤモンドを 4 個設定する
ItemStack item = new ItemStack(0, "diamond", 4);

// 複数のアイテムを設定する
ItemStack myItem = new List<ItemStack>
{
    new ItemStack(0, "diamond", 2),
    new ItemStack(1, "gold_ingot", 4),
    new ItemStack(2, "iron_ingot", 16),
    new ItemStack(3, "redstone", 32)
};

// 指定した座標にある, チェスト内のアイテムを取得して格納する
var commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
var chestPos = new Position(-449, 63, 58);
List<ItemStack> chestItems = commands.GetChestItems(chestPos);

// 指定した座標にある, チェスト内のアイテムを書き換える
commands.SetChestItems(chestPos, myItem);
```

書き換えたときの例
![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/Struct/media/ItemStack_01.webp)


# 素朴な疑問
## Q. 最大値と最小値は？

各方向ともに最小値が -10.0 で最大値が 10.0 です. ちなみに 1.0 でもそれなりの速度がでます.

## Q. それぞれの方向は何を表しているの？

座標と同じく, x 方向は東西方向, y 方向は高さ方向, z 方向は南北方向を表しています. x 方向はプラス側が東でマイナス側が西です. z 座標はプラス側が南でマイナス側が北です. 

## Q. プレイヤー以外にも使えるの？

動きのデータを持つエンティティであれば使えます. 例えば, モンスターやトロッコ, 矢にも使えます. `data get` コマンドを実行してみて, `Motion` という項目が出てくるかどうかで使えるかどうかを判断できます.