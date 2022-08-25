---
title: "Fireworks クラス"
date: "2022/08/25"
author: "Takunology"
---

# 概要
名前空間 : `MinecraftConnection.Entity`
継承 : `LivingEntityBase` → `Fireworks`

花火アイテムを作成するためのインスタンスを作ります.

## コンストラクタ
引数はありません.

```cs
Fireworks fw = new Fireworks();
```

## プロパティ

|名称|型|説明|
|--|--|--|
|LifeTime|ushort|花火が打ち上がってから爆発するまでの時間(tick)を設定または取得します.|
|Flight|int|花火の飛翔距離を設定または取得します.|
|Type|[FireworkType](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks%2FEnum&fileName=FireworkType)|花火が爆発したときの形状を設定または取得します.|
|Flicker|bool|花火にきらめき効果を設定または取得します.|
|Trail|bool|花火に流星効果を設定または取得します.|
|Colors|List&lt;[FireworkColor](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks%2FEnum&fileName=FireworkColor)&gt;|花火が打ち上がってから爆発するまでの時間を設定または取得します.|
|FadeColors|List&lt;[FireworkColor](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks%2FEnum&fileName=FireworkColor)&gt;|花火が爆発してからフェードアウトするときの色を設定または取得します.|
|IsEmpty|bool|爆発しない花火を設定または取得します.|

## メソッド
|名称|引数|戻り値|説明|
|--|--|--|--|
|[GetNBT()](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks%2FMethod&fileName=GetNBT)|なし|string|花火アイテムの NBT を取得します.|

# 使い方
花火インスタンスのプロパティを変更することによって, 様々な形状や色の花火を定義することができます.

```cs
using MinecraftConnection.Entity;

// 1.5秒(30[tick])後に爆発する青色の小玉花火を作る
Fireworks fw = new Fireworks()
{
    LifeTime = 30,
    Type = FireworkType.SmallBall,
    Colors = new List<FireworkColors> {FireworkColors.BLUE}
};

// 2秒後(40[tick])後に爆発する、きらめき効果の付与された緑色のクリーパー型花火を作る
Fireworks fw2 = new Fireworks()
{
    LifeTime = 40,
    Type = FireworkType.Creeper,
    Colors = new List<FireworkColors> {FireworkColors.GREEN},
    Flicker = true    
};

// x 方向に対して正の方向へ打ち出すバースト型花火を作る
Fireworks fw3 = new Fireworks()
{
    LifeTime = 0,
    Type = FireworkType.Burst,
    Colors = new List<FireworkColors> {FireworkColors.PINK},
    Motion = new Motion(1.0, 0, 0)
};

// 打ち上がるエフェクトだけを表示する花火を作る
Fireworks fw3 = new Fireworks()
{
    LifeTime = 40,
    IsEmpty = true
};

// 作った花火インスタンス fw の NBT 構造をコンソール出力する
Console.WriteLine(fw.ToNBT());
```

作った花火インスタンスを使用して打ち上げるには `SetOffFireworks()` メソッドを使用します. 詳しい使い方については [SetOffFireworks](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=MinecraftCommands%2FMethod&fileName=SetOffFireworks) を参考にしてください.

# 素朴な疑問

**Q. インスタンスのプロパティを設定しなくても花火アイテムを作れますか？**

作ることはできます. ただし, 色は指定しないと黒っぽい色で花火としては美しくはありません. また, 初期値として小玉花火になっています.

**Q. 空の花火ってなんですか？**

爆発せず, 打ち上がっていく軌跡だけを残す花火です. 例えば, Motion 構造体を使用して打ち出す方向と大きさ（ベクトル）を定義すれば, 演出にも使えます.

![](https://storage.googleapis.com/zenn-user-upload/0815406b14c0-20220605.gif)