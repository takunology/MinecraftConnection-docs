---
title: "GetNBT メソッド"
date: "2022/08/25"
author: "Takunology"
---

# 概要
作成した花火のインスタンスから, NBT を取得します. 

## 引数
なし

# 使い方
作った花火のインスタンスの NBT 構造を把握したいときや, マイクラのコマンドで NBT を記載したいときに利用することができます. 

```cs
using MinecraftConnection.Entity;

Fireworks fw = new Fireworks()
{
    LifeTime = 30,
    Type = FireworkType.Star,
    Colors = new List<FireworkColors> {FireworkColors.RED},
    Flicker = true
};

Console.WriteLine(fw.GetNBT());
```

実行結果

```txt
{"LifeTime":30,"FireworksItem":{"id":"firework_rocket","Count":1,"tag":{"Fireworks":{"Flight":2,"Explosions":[{"Type":2,"Flicker":1,"Trail":0,"Colors":[I;11743532],"FadeColors":[I;]}]}}}}
```

# 素朴な疑問

**Q. これって何の役にたつの？**

これだけではなんの役にも立ちません. が, NBT を把握したいときや, 誰かに共有したいときには使えるかもしれません. 

**Q. NBT って何？**

マイクラの世界で利用できる, データの構造体の規格です. 正しく記載しないと, データ構造が無効になってしまいます.