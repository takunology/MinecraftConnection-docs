---
title: "SetBlock メソッド"
date: "2022/10/17"
author: "Takunology"
---

# 概要
指定した座標に任意のブロックを設置します.

## 引数

|変数名|型|説明|
|--|--|--|
|x|int|x 座標|
|y|int|y 座標|
|z|int|z 座標|
|block|string|ブロックID|

## 戻り値
コマンドの実行結果が返って来ます.

コマンドの実行に成功した場合：

```txt
Changed the block at 0, -60, -3
```

コマンドの実行に失敗した場合：

```txt
Could not set the block
```

すでに同じブロックが設置されているか, 設置が禁止されている座標へ設置を試みようとした場合に失敗します.

# 使い方
ブロックを設置したい座標（絶対座標）と, そのブロックIDを引数に代入して使用します.

```cs
using MinecraftConnection;

// 座標 (-1, -60, -2) に石ブロックを配置します
MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
commands.SetBlock(-1, -60, -2, "stone");
```

実行すると石ブロックが配置されます.

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/SetBlock_01.webp)

また, 反復処理を組み合わせることでブロックを複数配置させることができます.

```cs
for(int i = 0; i < 10; i++)
{
    for (int j = 0; j < 10; j++)
    {
        commands.SetBlock(-1, -60, -2 + i, "blue_concrete");
    }
}
```

実行すると青色のコンクリートが平面上に10×10の範囲で配置されます.


![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/SetBlock_02.webp)

配置したブロックを削除（空気ブロック）に置き換える場合は `air` を使います. 

```cs
for(int i = 0; i < 10; i++)
{
    for (int j = 0; j < 10; j++)
    {
        commands.SetBlock(-1 + j, -60, -2 + i, "air");
    }
}
```

これを実行すると平面に設置した青色のコンクリートをそのまま削除することができます. 

# 素朴な疑問

**Q. ブロックの向きを変えられますか？**

ブロックの向きを変更する場合は, ブロックIDの後に `[facing=]` を使用して方向を指定する必要があります. 例えば, ジャックオーランタンのブロックを使用して記述すると下記のようになります.

```cs
// 何も指定しない場合は北 (north) の方角に向きます
commands.SetBlock(-1, -60, -2, "jack_o_lantern");

// 南 (south) の方角を向かせる場合は [facing] をつけます
commands.SetBlock(-1, -60, -2, "jack_o_lantern[facing=south]");
```

**Q. ドアやハーブブロックの上半分側にうまく置けません**

例えば, ドアの場合は2ブロック分の高さがありますが, IDは同じです. その上部分 (upper) と下部分 (lower) とで区別するために, `half` を使用します. このとき, 座標に注意してください.

```cs
// ドアの下半分
commands.SetBlock(-1, -60, -2, "birch_door[half=lower]");
// ドアの上半分（2ブロックの高さなので座標に注意）
commands.SetBlock(-1, -59, -2, "birch_door[half=upper]");
```

ハーブブロックの場合は `[type=]` を使用します. 同様に上半分（top）と下半分 (bottom) で指定します.

```cs
// ハーフブロックの上半分側
commands.SetBlock(-1, -60, -2, "oak_slab[type=top]");
// ハーフブロックの下半分側
commands.SetBlock(-1, -60, -3, "oak_slab[type=bottom]");
```

**Q. ブロックIDがわかりません**

[マイクラWiki](https://minecraft.fandom.com/ja/wiki/%E3%83%87%E3%83%BC%E3%82%BF%E5%80%A4/Java_Edition) のブロックIDリストを参照してください.