---
title: "ItemStack 構造体"
date: "2022/08/17"
author: "Takunology"
---

# 概要
名前空間 : `MinecraftConnection`

アイテムスロット番号, アイテムID, アイテムの数量の3つのデータを持つ型（アイテムスタック）を扱うことができます.

メンバ変数

| 変数名 | 型 | 説明 |
| :---: | :---: | :---: |
| Slot | ushort | アイテムスロットの番号 |
| Id | string | アイテムID（アイテム名） |
| Count | ushort | アイテムの数量 |

コンストラクタ

|引数|型|説明|
|:---:|:---:|:---:|
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
**Q. アイテムは何個まで？**

1つにつき64個までですが, 一部のアイテム（雪玉やエンダーパール）は16個です.

**Q. アイテムスロットは何番まで？**

チェスト内のアイテムは0番目から26番目までの27個まで収納可能です.

**Q. アイテムIDがわかりません**

ダイヤモンドは `diamond`. 石ブロックは `stone` などが割り振られていますが, ここで紹介するには数が多すぎて紹介しきれません. 詳細はマイクラWikiなどで検索してみてください. 

[Minecraft Wiki - データ値/Java Edition](https://minecraft.fandom.com/ja/wiki/%E3%83%87%E3%83%BC%E3%82%BF%E5%80%A4/Java_Edition)

**Q. チェスト以外にも使える？**

チェスト以外にもストレージ変数やアイテムスロットを持つブロックエンティティなどに利用できます. ちなみに, プレイヤーデータの書き換えはできないので, 指定のアイテムで上書きはできません. 代わりに `give` コマンドを使用してアイテムを与えることはできますが, スロットまでは指定できません. 