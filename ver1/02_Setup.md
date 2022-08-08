# セットアップ
MinecraftConnection ライブラリの導入とマイクラプログラミングに必要な環境構築についてです。

## 必要な環境
- .NET Standard 2.0 以上
- Visual Studio 2019
- Java版 Minecraft 1.15 以上
- RCON接続許可された Minecraft Server

NET Standard 2.0 では .NET Core 2.0 および .NET 5 などがサポートされています。詳細は [こちら]()を御覧ください。

MinecraftConnection は NuGet パッケージからもダウンロードできるので、Visual Studio での作業をおすすめします。

Minecraft(Java) は 1.15 以上のバージョンを準備してください。1.15 以上では動作確認済みですが、それ以前のバージョンでは未確認です。また、1.13 にてコマンドが大幅に変更されたため、それ以前のバージョンでは正常に動作しない可能性があります。

Minecraft Server はクライアント（本体）と同じバージョンに揃える必要があります。また、MinecraftConnection によって外部からコマンドを送信するため、RCON接続許可が必要になります。

**Note**
ここでは MinecraftConnection を利用する方法のみ紹介しています。Visual Studio の使用方法や Minecraft ゲーム本体の導入に関しては割愛します。

## RCON接続のセットアップ
サーバのセットアップ方法については [マイクラ自動化 第0回](https://www.mcwithcode.com/Automation) にて解説していますので、参考にしてください。 Minecraft Server の保存されているディレクトリ内に `server.properties` があるので、これを次のように書きかえてください。

```ini
rcon.port=25575
rcon.password=minecraft
enable-rcon=true
```

ここではポート番号を `25575`, パスワードを `minecraft` としています。編集できたら上書き保存して、サーバを起動してください。

## Nuget パッケージによる導入
Visual Studio のパッケージマネージャコンソールにて下記のコマンドを実行します。

```
Install-Package MinecraftConnection
```

異なるバージョンを利用する場合は [こちら](https://www.nuget.org/packages/MinecraftConnection) から確認してください。

実際のプログラムの書き方や動かし方についてはメニュー「はじめに」から「サンプルプログラム」をご覧ください。