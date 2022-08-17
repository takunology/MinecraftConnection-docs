---
title: "Motion 構造体"
date: "2022/08/17"
author: "Takunology"
---

# 概要
名前空間 : `MinecraftConnection`

エンティティの動きを扱うことができます.

**メンバ変数**

|変数名|型|説明|
|---|---|---|
|X|double|x 方向|
|Y|double|y 方向|
|Z|double|z 方向|

**コンストラクタ**

|引数|型|説明|
|---|---|---|
|X|double|x 方向|
|Y|double|y 方向|
|Z|double|z 方向|

# 使い方
コンストラクタの引数は x, y, z の3方向に対する動きを設定する必要があります. どれか1方向だけを定義することはできません.

トロッコや Mob などの動き回るエンティティに対して, Motion を上書きすることで加減速させることができます.

```cs
// 動きを (-1.0, 0, 0.5) に設定する
Motion mot = new Motion(-1.0, 0, 0.5);

// 動きを (0.0, 1.0, 0.0) に設定する
Motion mot2 = new Motion(5.0, 0.0, 0.0);

// プレイヤーの動きを取得して格納する
var commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
Motion playerMot = commands.GetPlayerData("playerID").Motion;

// 村人をその場でジャンプさせる
Motion mot3 = new Motion(0.0, 1.0, 0.0);
commands.SendCommand($"data modify entity <entityID> Motion[1] set value {mot3.Y}")
```

村人をジャンプさせる実行例

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/Struct/media/Motion_01.gif)

# 素朴な疑問

**Q. 最大値と最小値は？**

各方向ともに最小値が -10.0 で最大値が 10.0 です. ちなみに 1.0 でもそれなりの速度がでます.

**Q. それぞれの方向は何を表しているの**

座標と同じく, x 方向は東西方向, y 方向は高さ方向, z 方向は南北方向を表しています. x 方向はプラス側が東でマイナス側が西です. z 座標はプラス側が南でマイナス側が北です. 

**Q. プレイヤー以外にも使えるの？**

動きのデータを持つエンティティであれば使えます. 例えば, モンスターやトロッコ, 矢にも使えます. `data get` コマンドを実行してみて, `Motion` という項目が出てくるかどうかで使えるかどうかを判断できます.