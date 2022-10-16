---
title: "SetChestItems メソッド"
date: "2022/10/17"
author: "Takunology"
---

# 概要
チェストブロックの中に入っているアイテムを書き換えます.

## オーバーロード

|引数名|型|説明|
|--|--|--|
|position|Position|チェストブロックの設置されている座標|
|List&lt;[ItemStack](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=ItemStack)&gt;|int|チェスト内のアイテム情報を保持したリスト|

|引数名|型|説明|
|--|--|--|
|x|int|チェストの x 座標|
|y|int|チェストの y 座標|
|z|int|チェストの z 座標|
|List&lt;[ItemStack](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=ItemStack)&gt;|int|チェスト内のアイテム情報を保持したリスト|

# 使い方
チェストを予め用意しておき, その座標をメモしておきます. 次に, ItemStack のリストを宣言して, アイテムスロット, アイテムID, 数量を定義します. 最後に, 座標とリストを使用して引数に代入して使用します.

```cs
using MinecraftConnection;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
var items = new List<ItemStack>()
{
    new ItemStack(0, "diamond", 4),
    new ItemStack(1, "stone", 8),
    new ItemStack(2, "glass", 32),
    new ItemStack(3, "diamond", 7),
};
// チェストブロックのおいてある座標
var pos = new Position(2, -60, -3);
commands.SetChestItems(pos, items);
```

実行結果

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/SetChestItems_01.webp)


# 素朴な疑問

**Q. 例外(Exception)が発生するんだけど？**

チェストの座標が正しくないと下記のような例外が発生します. チェストの設置されている座標を再度確認してください.

```txt
Unhandled exception. System.Exception: Chest is not found.
```

**Q. シュルカーボックスには使えるの？**

シュルカーボックスにも対応しています. シュルカーボックスの設置されている座標に対して使用すると, アイテムを書き換えることができます.

**Q. チェストに元々入っていたアイテムはどうなるの？**

全て上書きされます.