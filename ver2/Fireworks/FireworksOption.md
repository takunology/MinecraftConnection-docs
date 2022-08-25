---
title: "FireworksOption クラス"
date: "2022/08/25"
author: "Takunology"
---

# 概要
名前空間 : `MinecraftConnection.Entity`

花火インスタンスを作る際のオプションを用意しています. 例えば, 色をランダムに取得するメソッドなどが使えます. 

## メソッド

|名称|引数|戻り値|説明|
|--|--|--|--|
|RandomColor()|なし|List&lt;[FireworkColor](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks%2FEnum&fileName=FireworkColor)&gt;|ランダムな色を1色選択します.|
|RandomColors()|byte colorCount|List&lt;[FireworkColor](https://www.mcwithcode.com/Reference/GitHubDocument?version=ver2&path=Fireworks%2FEnum&fileName=FireworkColor)&gt;|ランダムな色を任意の数だけ選択します.|

# 使い方
マイクラの花火の色は複数色選択できるので, これを利用してカラフルな花火を作成することができます.

```cs
using MinecraftConnection.Entity;
// ランダムな色の花火を定義します. 
Fireworks fw = new Fireworks()
{
    LifeTime = 30,
    Type = FireworkType.LargeBall,
    Colors = FireworkOption.RandomColor(),
};

// ランダムな3色の花火を定義します.
Fireworks fw2 = new Fireworks()
{
    LifeTime = 30,
    Type = FireworkType.LargeBall,
    Colors = FireworkOption.RandomColors(3),
};
```

また, 打ち上げるたびに再定義することで, できるだけ重複しない色の花火を定義することもできます.

```cs
// 10発分のランダムな色の花火を定義する
for (int i = 0; i < 10 i++)
{
    Fireworks fw = new Fireworks()
    {
        LifeTime = 30,
        Type = FireworkType.LargeBall,
        Colors = FireworkOption.RandomColor(),
    };
}
```

# 素朴な疑問

**花火は何色あるの？**

定義次第では何色でも作ることはできますが, MinecraftConnection で用意しているプリセットカラーは 16 色です. もし, 任意の色で定義したい場合は自分でコマンドを生成する必要があります. 