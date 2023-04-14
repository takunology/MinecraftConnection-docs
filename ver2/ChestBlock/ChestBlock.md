---
title: "ChestBlock クラス"
date: "2023/04/15"
author: "Takunology"
---

# 概要
名前空間 : `MinecraftConnection.Block`</br>
継承：`BlockBase` → `ChestBlock`

チェストブロックまたはシュルカーボックスのブロックエンティティに関するインスタンスを作ることができます.

## コンストラクタ

|引数名|型|説明|
|--|--|--|
|x|int|ブロックの x 座標|
|y|int|ブロックの y 座標|
|z|int|ブロックの z 座標|

```cs
ChestBlock chest = new ChestBlock(int x, int y, int z);
```

|引数名|型|説明|
|--|--|--|
|position|List&lt;[Position](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=Position)&gt;|ブロックの座標|

```cs
ChestBlock chest = new ChestBlock(Position position);
```

## メソッド
|名称|引数|戻り値|説明|
|--|--|--|--|
|[GetItems()](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=ChestBlock%2FMethod&fileName=GetItems)|なし|List&lt;[ItemStack](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=ItemStack)&gt;|ブロックに格納されているアイテムを取得します.|
|[SetItems()](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=ChestBlock%2FMethod&fileName=GetItems)|List&lt;[ItemStack](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=ItemStack)&gt;|なし|ブロックにアイテムを格納することができます.|

# 使い方
ブロックの座標を使用して2種類の方法でインスタンスを作成できます. 

```cs
// 各座標を代入する方法
ChestBlock chest = new ChestBlock(20, 44, -128);

// Position 構造体を代入する方法
Position pos = new Position(20, 44, -128);
ChestBlock chest = new ChestBlock(pos);
```