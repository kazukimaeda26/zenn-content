---
title: "【超入門】Laravelデバッグ：禁断の知識を解き明かす"
emoji: "📚"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Laravel", "debug", "php", "tech"]
published: true
---


# 🔮今宵のクエスト（できるようになること）🔮
Laraveでの開発中に
- ここの処理（xxxxController.phpのOOOOメソッド）に来ているのかな？の確認
- 深淵に巣食う禁断の知識を解き明かすこと **（変数の確認）**

# 🔮混沌の叫び声（発端）🔮
我の旅路は、遙かなる鉄路（Rails）に始まった。

鉄路（Rails）を征する際、pry-railsの力を借り、binding.pryの秘術を使いこなし、未知を解明することができた。

だが今、我は新たなる地、Laravelの大地を踏み締めることとなった。

そしてここで、我は問いかける。「Laravelでデバッグは何処に向かうべきか？」
その答えを見つけるため、我々はこの場に集ったのだ！


# 🔮秘術の儀式（手順）🔮
1. デバッグの戦いに備え、適当なプロジェクトを作り出そう。

我はこの記事のために新たなる創造を行なった。
関係ない者は無視して進むが良い。

創造の地を決め、下記の秘符を唱えよ。
（プロジェクトを作成したいディレクトリに移動し、下記のコマンドを打ってください）
```
composer create-project laravel/laravel laravel-test
```

さすれば、新たなるプロジェクトが生まれ出る。

さらに、[Breeze](https://laravel.com/docs/10.x/starter-kits)という強力なるパワーを我の創造物に注入する。
（Breezeは認証機能のライブラリ）

導入の詳細な儀式は[こちら](https://laravel.com/docs/10.x/starter-kits#laravel-breeze-installation)に記されている。
こちらも一瞬で導入できる。
我の場合は下記の3行の呪文を唱えるだけだ。
```
composer require laravel/breeze --dev
php artisan breeze:install
php artisan migrate
```

今宵の戦いの場は、"ユーザー登録"という儀式の際に動く、RegisteredUserController.phpのstoreメソッド。我々の目標は、変数$requestの深淵を見つめることだ！


2. プロジェクトを呼び覚ませ！
目の間には、このような光景が広がるはずだ。
![](/images/laravel-debug/top.png)

3. 闇の力を解き放つ
戦いを挑む箇所に、Logの力を解き放つのだ！
(35行目の様にLogを仕込みましょう)

我々の目標は$requestの深淵を解き明かすこと。
それを目指して、35行目のようにLogの力を注ぎ込むのだ！
![](/images/laravel-debug/log.png)

そして忘れてはならない、useを唱えてimportをする必要があることを。（16行目）
![](/images/laravel-debug/use.png)

4. 古の知識の扉を開く（ログファイルを開きます）
tailという古の力を使って、ログファイル（storage/laravel.log）を開くのだ。
尚、tailは尻尾や末尾を意味する言葉。それは最後尾にある記述を見るための力。
-fというオプションを付けると便利だ。
follow、つまり「追う」の意。
新しく上書きされたものもその都度反映してくれる力を持つ。
ログファイルを見るときの強力な助けとなる！

プロジェクトの神殿（ルートディレクトリ）で下記の秘符を唱えよ。
```
tail -f storage/logs/laravel.log
```

5. 幕開けの瞬間（実際に動かしてみましょう）

![](/images/laravel-debug/terminal.gif)

（画面を並べて実際にLogを仕込んだ箇所を通るように動かしてみましょう。Logを仕込んだ箇所を通った瞬間にログが追加されるのが把握できます。）

ついに$requesetの深淵が明らかとなった。全てはここから始まる！我々の勝利だ！