# セットアップ
MinecraftConnection ライブラリの導入とマイクラプログラミングに必要な環境構築についてです。

## 必要な環境
- .NET Stanadard 2.0 以上
- Java版 Minecraft 1.18 以上
- RCON接続許可された Minecraft Server

NET Standard 2.0 では .NET Core 2.0 および .NET 5 などがサポートされています。詳細は [こちら]()を御覧ください。

MinecraftConnection は NuGet パッケージからもダウンロードできるので、Visual Studio または VS Code での作業をおすすめします。

Minecraft(Java) は 1.18 以上のバージョンを準備してください。1.18 以上では動作確認済みですが、それ以前のバージョンでは未確認です。また、1.13 にてコマンドが大幅に変更されたため、それ以前のバージョンでは正常に動作しません。セキュリティの観点からも古いバージョンでのプログラム実行は推奨されません。

Minecraft Server はクライアント（本体）と同じバージョンに揃える必要があります。また、MinecraftConnection によって外部からコマンドを送信するため、RCON接続許可が必要になります。

<div class="alert alert-info" role="alert">
    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-info-circle" viewBox="0 0 20 20">
        <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z" />
        <path d="m8.93 6.588-2.29.287-.082.38.45.083c.294.07.352.176.288.469l-.738 3.468c-.194.897.105 1.319.808 1.319.545 0 1.178-.252 1.465-.598l.088-.416c-.2.176-.492.246-.686.246-.275 0-.375-.193-.304-.533L8.93 6.588zM9 4.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0z" />
    </svg>
    ここでは MinecraftConnection を利用する方法のみ紹介しています。Visual Studio の使用方法や Minecraft ゲーム本体の導入に関しては割愛します。
</div>

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