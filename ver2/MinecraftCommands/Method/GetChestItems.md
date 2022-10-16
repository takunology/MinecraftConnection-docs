---
title: "GetChestItems メソッド"
date: "2022/10/17"
author: "Takunology"
---

# 概要
チェストブロックの中に入っているアイテムを取得します.

## オーバーロード

|引数名|型|説明|
|--|--|--|
|position|[Position](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=Position)|チェストブロックの設置されている座標|

|引数名|型|説明|
|--|--|--|
|x|int|チェストブロックの x 座標|
|y|int|チェストブロックの y 座標|
|z|int|チェストブロックの z 座標|

## 戻り値
List&lt;[ItemStack](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=ItemStack)&gt; としてアイテムリストを受け取ることができます.

# 使い方
チェストブロックを予め用意しておき, その座標をメモしておきます. チェストブロックの中に何かアイテムを入れておくと, そのアイテムのスロット番号, アイテムID, 数量を取得できます.

```cs
using MinecraftConnection;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");

// 座標を指定して取得する方法
var items = commands.GetChestItems(2, -60, -3);
// Position 構造体を使用して取得する方法
var pos = new Position(2, -60, -3);
var items = commands.GetChestItems(pos);

items.ForEach(x => Console.WriteLine($"{x.Slot}\t{x.Id}\t{x.Count}"));
```

実行結果

例えば, このようにアイテムが配置されていた場合は

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/SetChestItems_01.webp)

コンソール出力にて下記のように表示されます.

```txt
0       minecraft:diamond       4
1       minecraft:stone 8        
2       minecraft:glass 32       
3       minecraft:diamond       7
```

# 素朴な疑問

**Q. 例外(Exception)が発生するんだけど？**

チェストブロックの座標が正しくないと下記のような例外が発生します. チェストの設置されている座標を再度確認してください.

```txt
Unhandled exception. System.Exception: Chest is not found.
```

**Q. シュルカーボックスには使えるの？**

シュルカーボックスにも対応しています. シュルカーボックスの設置されている座標に対して使用すると, アイテムを取得できます.