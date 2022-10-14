---
title: "GetPlayerData メソッド"
date: "2022/10/15"
author: "Takunology"
---

# 概要
プレイヤーに関するエンティティデータを受け取ることができます.

## 引数

|変数名|型|説明|
|--|--|--|
|playerName|string|プレイヤーのID|

## プロパティ

|フィールド|型|説明|
|--|--|--|
|OnGround|bool|プレイヤーが地面についているかどうかの有無|
|Air|short|プレイヤーが無呼吸でいられる時間 [tick]|
|Fir|short|エンティティについた火が消えるまでの時間 [tick]|
|FallDistance|double|エンティティの落下した距離 [block]|
|[Motion](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=Motion)|Motion|プレイヤーの速度 (x, y, z)|
|[Rotation](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=Rotation)|Rotation|プレイヤーの向いている方角 (x, y)|
|[Position](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=Position)|Position|プレイヤーの座標 (x, y, z)|
|EntityId|string|プレイヤーのID（名前）|
|PortalCooldown|int|ポータルを通過できない状態でいる残り時間 [tick]|
|Invulnerable|bool|無敵状態の有無|


# 使い方
プレイヤーのエンティティデータそのものが返って来ますので, 各種プロパティへアクセスしてデータを取得します.

## プレイヤーのIDを取得する

```cs
MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "passwd");
// プレイヤーのエンティティクラスを取得する
var result = commands.GetPlayerData("takunology");
// プレイヤーIDを参照してコンソール出力
Console.WriteLine(result.EntityId);
```

実行結果

```txt
takunology
```

## プレイヤーの座標を取得する

```cs
var result = commands.GetPlayerData("takunology").Postision;
Console.WriteLine($"{result.X}\t{result.Y}\t{result.Z}");
```

実行結果

```txt
213.79175149505863      -42     -184.95366446483624
```

## プレイヤーの動きを取得する
地面に立っている間にも重力による影響は受けているので, Y軸方向の値は常に一定になります. ただし, 空中で静止している間はどの軸の値も 0 になります.

```cs
var motion = commands.GetPlayerData("takunology").Motion;
Console.WriteLine($"{motion.X}\t{motion.Y}\t{motion.Z}");
```

実行結果

```txt
0       -0.0784000015258789     0
```

## プレイヤーの速度を重複なく取得するサンプルコード
プレイヤーを255の高さから落下させていくときの速度の変化をコンソール出力するプログラムです. リストの重複をなくすために `Distinct()` メソッドを使用しています. 

```cs
commands.SendCommand("tp takunology ~ 255 ~");
var data = new List<string>();
while(true)
{
    var posY = commands.GetPlayerData("takunology").Postision.Y;
    var motY = commands.GetPlayerData("takunology").Motion.Y;
    if (posY < -55)
    {
        break;
    }
    data.Add(posY.ToString());
}

var motData = data.Distinct();
foreach(var item in motData)
{
    Console.WriteLine(item);
}
```

実行結果の例

```txt
-0.0784000015258789
-0.1552320045166016
-0.230527368912964
-0.30431682745754424
...
```

実行結果をグラフに直すとこのような関係を得られます.

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/Motion.webp)

# 素朴な疑問

**Q. データ取得して何の役に立つの？**

プレイヤーの座標を取得しながらブロックを設置したり、物理演算の解析？に役立てられるかも？？