# サンプルプログラム
MinecraftConnection を用いたマイクラプログラミングの例です。</br></br>
ここでは、.NET 5 のコンソールアプリケーションを用いた作成方法についてご紹介します。プロジェクトを作成し、NuGet パッケージマネージャーコンソールにて

```
Install-Package MinecraftConnection
```

を実行し、ライブラリを導入します。また、Minecraft Server の設定ファイルをもとに、接続先のIPアドレスとパスワード、ポート番号を控えておきます。

## 時間を 0 に設定するサンプルプログラム
時間を設定するには `/time set` というコマンドを使用します。

```cs
using MinecraftConnection;

namespace ExampleApp
{
    class Program
    {
        static string address = "127.0.0.1";
        static ushort port = 25575;
        static string pass = "minecraft";
        static MinecraftCommands command = new MinecraftCommands(address, port, pass);

        static void Main(string[] args)
        {
            command.SendCommand("/time set 0");
        }
    }
}
```

このプログラムを実行すると、時間が 0 (マイクラ世界では午前6:00) にセットされます。MinecraftCommands はマイクラのコマンドが定義されたクラスで、様々なメソッドが用意されています。なお、上記のプログラムは実行するための必要最低限のコードとなります。</br></br>

プログラムの実行にはサーバで設定したRCONのIPアドレス、パスワード、ポート番号が必要です。

## 花火を打ち上げるサンプルプログラム
マインクラフトで花火を打ち上げるには NBT という文字列を指定する必要がありますが、MinecraftConnection を使用すると簡単に作る事ができます。Fireworks クラスのコンストラクタで花火の形状や色、流星効果、きらめき効果などを指定することができます。Fireworks クラスは Items 名前空間に入っています。

```cs
using MinecraftConnection;
using MinecraftConnection.Items;

namespace ExampleApp
{
    class Program
    {
        static string address = "127.0.0.1";
        static ushort port = 25575;
        static string pass = "minecraft";
        static MinecraftCommands command = new MinecraftCommands(address, port, pass);

        static void Main(string[] args)
        {
            string playerName = "takunology";
            // プレイヤーの現在地を取得する
            var playerData = command.GetPlayerData(playerName);
            int x = playerData.PositionX;
            int y = playerData.PositionY;
            int z = playerData.PositionZ;
            // 花火の色を決める
            List<FireworksColors> explosionColor = new List<FireworksColors>() { FireworksColors.BLUE };
            List<FireworksColors> fadeColor = new List<FireworksColors>() { FireworksColors.CYAN };
            // 花火玉を作る
            Fireworks fireworks = new Fireworks(20, FireworksShapes.LargeBall, explosionColor, fadeColor).Trail();
            // 花火を打ち上げる
            command.SetOffFireworks(x + 10, y, z, fireworks);
        }
    }
}
```

Minecraft 1.16.3 での実行結果です。

<img src="https://raw.githubusercontent.com/takunology/MinecraftConnection/1.X.X/images/fireworks_sample.png" class="img-fluid my-3" />
