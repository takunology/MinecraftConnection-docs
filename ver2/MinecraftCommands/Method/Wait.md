---
title: "Wait メソッド"
date: "2022/08/25"
author: "Takunology"
---

# 概要
指定した時間(ミリ秒)だけ, コマンドの実行を待機します.

## 引数
|名称|型|説明|
|--|--|--|
|time|ushort|任意の時間(ミリ秒)|

# 使い方
コマンドの実行を待機したいときに使います. 例えば, チャットコマンドやブロックを配置する際に時間間隔を空けることができます. また, 連続実行による負荷を軽減させる目的でも利用可能です.

```cs
using MinecraftConnection;

MinecraftCommands commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
commands.DisplayMessage("Hello!");
commands.Wait(500); // 500ミリ秒(0.5秒)待機
commands.DisplayMessage("from");
commands.Wait(1000); // 1000ミリ秒(1秒)待機
commands.DisplayMessage("CSharp!");
```
