---
title: "SetOffFireworks メソッド"
date: "2022/08/25"
author: "Takunology"
---

# 概要
指定した座標から花火を打ち上げます.

## オーバーロード

```cs
public string SetOffFireworks(Position position, Fireworks fireworks);
```

|変数名|型|説明|
|--|--|--|
|position|[Position](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Struct&fileName=Position)|花火を打ち上げる座標|
|fireworks|[Fireworks](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks&fileName=Fireworks)|花火のインスタンス|

```cs
public string SetOffFireworks(double x, double y, double z, Fireworks fireworks);
```

|変数名|型|説明|
|--|--|--|
|x|double|花火を打ち上げる x 座標|
|y|double|花火を打ち上げる y 座標|
|z|double|花火を打ち上げる z 座標|
|fireworks|[Fireworks](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks&fileName=Fireworks)|花火のインスタンス|

# 使い方
定義の方法は [Fireworks](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks&fileName=Fireworks) を参照してください. 任意の座標を定義して, 作成した花火のインスタンスを使用して打ち上げる方法の例を示します.

```cs
using MinecraftConnection;
using MinecraftConnection.Entity;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
Position pos = new Position(20, 64, 80);

Fireworks fw = new Fireworks()
{
    LifeTime = 30,
    Type = FireworkType.Star,
    Colors = new List<FireworkColors> {FireworkColors.RED},
    Flicker = true
};

commands.SetOffFireworks(pos, fw);
```

次は, 疑似乱数を使用してランダムな座標に花火を打ち上げる方法です.

```cs
using MinecraftConnection;
using MinecraftConnection.Entity;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
Position pos = new Position(-465, 62, 58);
Random rnd = new Random();

for(int i = 0; i < 10; i++)
{
    Fireworks fw = new Fireworks()
    {
        LifeTime = 30,
        Type = FireworkType.LargeBall,
        Colors = FireworkOption.RandomColor(),
    };
    commands.SetOffFireworks(pos.X, pos.Y, pos.Z + rnd.Next(-20, 20), fw);
    commands.Wait(500);
}
```

[Wait](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=MinecraftCommands%2FMethod&fileName=Wait) メソッドを使用して, コマンドの実行を待機させることで一定間隔に花火を打ち上げることができます.

実行例

![](https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/MinecraftCommands/Method/media/SetOffFireworks_01.gif)

# 素朴な疑問

**Q. 花火を打ち上げすぎて処理落ちする可能性はある？**

あります. 時間間隔を空ければ問題ないですが, 一気に打ち上げようとすると, 打ち上がるときのアニメーションが省略されたり, 爆発したときに動作が不安定になったりすることがあります. ただし, 十分なマシンスペックであれば問題なさそうですが, サーバへの負荷が大きいので注意が必要です.