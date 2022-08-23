---
title: "ここにタイトルを入れる"
date: "リファレンスの更新日"
author: "編集者A, 編集者B, 編集者C ..."
---

# タイトル
ここは本文

## サブタイトル
ここも本文

画像を配置する場合は `raw.githubusercontent.com` を経由すること. 相対パスでは正しく読み込まれません.

`https://raw.githubusercontent.com/takunology/MinecraftConnection-docs/main/ver2/<dir>/<file>.webp`

リンクは自由に貼ってOK.

Note は下記テンプレートをコピーしてください.
```html
<div class="alert alert-info" role="alert">
    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-info-circle" viewBox="0 0 20 20">
        <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z" />
        <path d="m8.93 6.588-2.29.287-.082.38.45.083c.294.07.352.176.288.469l-.738 3.468c-.194.897.105 1.319.808 1.319.545 0 1.178-.252 1.465-.598l.088-.416c-.2.176-.492.246-.686.246-.275 0-.375-.193-.304-.533L8.93 6.588zM9 4.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0z" />
    </svg>
    文章はこちらへ
</div>
```

**表を書く**

|ヘッダ1|ヘッダ2|ヘッダ3|
|---|---|---|
|01|要素A|説明A|
|02|要素B|説明B|

**サンプルコード**

```cs:Program.cs
using MinecraftConnection;
namespace ConsoleApp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            var commands = new MinecraftCommands("127.0.0.1", 25575, "minecraft");
            commands.DisplayTitle("Hello, Minecraft!");
        }
    }
}
```

画像は各階層の `media` へ保存しておいてください. また、保存形式を `webp` にしておくとかなり圧縮できるのでオススメ。

https://squoosh.app/