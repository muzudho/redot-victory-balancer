# プロジェクトの作り方

# シーンウィンドウを準備する

Redot ではゲームオブジェクトを ノード（Node） と呼び、  
ツリー階層のことを シーン（Scene） と呼びます。  
他のゲームエンジンと比べ、用語が独特なので、読み替えてください  

👇　とりあえずシーンウィンドウの以下のような第１～３階層のノードを、  
他の Muzudho 制のプロジェクトを真似て新規作成してください。  
ノードの中身や、その下のノードは、あとで整えれば構いません  

```plaintext
[シーンウィンドウ]
  👥Staff
  ├─ ⚙Config
  ├─ 🐵Monkey
  ├─ Grid
  ├─ 👤Illustrator
  ├─ 👤Musician
  │  ├─ 🌏BgMusics
  │  └─ 🌏SoundFX
  ├─ 👤Programmer
  ├─ 👤ScenarioWriter
  ├─ 👤TelopCoordinator
  └─ 👤Scorer
```

# ファイルシステムウィンドウを準備する

👇　ファイルシステムウィンドウの第一階層フォルダーも、  
他の Muzudho 制のプロジェクトを真似て新規作成してください。  
フォルダーの中身は後で整えれば構いません  

```plaintext
res://
├─ docs
├─ 🍋audio_bg_musics
├─ 🍋audio_sound_fx
├─ 🍋fonts
├─ 🍋images
├─ 🍋label_settings
├─ 🍋scripts
├─ icon.svg
└─ README.md
```

とりあえず、シーンを保存しましょう。  
名前は最初は 👥staff.tscn ぐらい適当で構いません。  
気になったら後で整えれば構いません  

# git の準備

👇　別ファイルを読んでください  
📖 [gitの準備](./preparing_git.md)  

# キーコンフィグ

Muzudho が `🎄addon_🍉key_config` というシーンのまとめを作っているのでコピー貼り付けしてください。  

📖 [GitHub > Muzudho > godot-practice](https://github.com/muzudho/godot-practice)  

```plaintext
res://
├─ 中略
└─ 🎄addon_🍉key_config
  ├─ 👤illustrator.tscn
  ├─ 👤musician_🌏bg_musics.tscn
  ├─ 👤musician_🌏sound_fx.tscn
  ├─ 👤programmer.tscn
  └─ 👤telop_coordinator.tscn
```

👆　２階層目の `.tscn` ファイル名が、[シーンウィンドウ]のどこでインポートするかの指示になっています  

例えば `👤illustrator.tscn` をダブルクリックすると何の画像が足りないか表示されます  

```
res://🍋images/🪑grayscale/1280x720/background/in_front_of_sakiwaka_station.png
res://🍋images/🪑grayscale/1280x720/windows/window_at_top_lerge.png
```

該当する画像もコピー貼り付けして持ってきておいてください  
めんどくさかったらフォルダー丸ごとコピーしておいてください  

再度 `👤illustrator.tscn` をダブルクリックしてください  

```plaintext
[シーンウィンドウ]
  📂🍉KeyConfig
  ├─ ーーーー背景（Ｚ＝０）ーーーー
  ├─ 🗻崎川駅前
  ├─ ーーーーメッセージ・ウィンドウ（Ｚ＝１０００）ーーーー
  ├─ ■下
  └─ ■上_大
```

👆　シーン（いわゆるツリー構造）が入っています  

👇　ドラッグ＆ドロップを使い、

```plaintext
res://
└─ 🎄addon_🍉key_config
  └─ 👤illustrator.tscn    👈 （１）このファイルを
```

```plaintext
👥Staff
└─ 👤Illustrator    👈 （２）ここにドラッグ＆ドロップすると
```

```plaintext
👥Staff
└─ 👤Illustrator
  └─ 📂🍉KeyConfig    👈　（３）これがコピーされました
```

👇　同様に以下の４つのシーンもコピーしてください  

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ 🎄addon_🍉key_config
	├─ 👤illustrator.tscn
	├─ 👤musician_🌏bg_musics.tscn    👈　これ
	├─ 👤musician_🌏sound_fx.tscn    👈　これ
	├─ 👤programmer.tscn    👈　これ
	└─ 👤telop_coordinator.tscn    👈　これ
```

# `🐵Monkey` ノード

Redot エディターのプレイボタンをクリックしても、 `🐵Monkey` ノードが設定されていないのでエラーが出ます。  
Redot エディターの停止ボタンをクリックしてください  

Muzudho が作った Redot の他のプロジェクトでは、以下のような感じで gd スクリプトファイルを置いています    

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ ⚓local_🍉JapaneseRiver
	├─ config.gd
	├─ programmer.gd
	├─ programmer_input.gd
	├─ programmer_input_extension.gd
	├─ programmer_monkey.gd
	├─ staff.gd
	└─ staff_monkey.gd    👈　これが `🐵Monkey` ノード用のスクリプト
```

例えば `⚓local_🍉JapaneseRiver` を自分のプロジェクトへコピーして `JapaneseRiver` の部分の名前を変えてください。  

👇　それでは、  

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ ⚓local_🍉VictoryBalancer
	└─ staff_monkey.gd    👈　（１）このファイルを
```

```plaintext
[シーンウィンドウ]
  👥Staff
  └─ 🐵Monkey    👈　（２）このノードの上へ
```

👆　（３）ドラッグ＆ドロップしてください  
それで `🐵Monkey` ノードに `staff_monkey.gd` スクリプトがアタッチされます  

# `MonkeyHelper`

Redot エディターのプレイボタンをクリックすると、今度は `MonkeyHelper` が無いというエラーが出ます  
Redot エディターの停止ボタンをクリックしてください  

`MonkeyHelper` クラスは、例えば `src-japanese-river/🍋scripts/🪑grayscale_🍉bench/👤programmer/monkey_helper.gd` といった場所にあります。  
フォルダーごと丸ごとコピーして持ってきてください  

📖 [GitHub > Muzudho > japanese-river](https://github.com/muzudho/japanese-river)  

# `⚙Config`

まだゲームは動きません  

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ ⚓local_🍉VictoryBalancer
	└─ config.gd		👈　（１）このファイルを
```

```plaintext
[シーンウィンドウ]
  👥Staff
  └─ ⚙Config    👈　（２）このノードの上へ
```

👆　（３）ドラッグ＆ドロップしてください  

config.gd ファイルの内容のうち、以下の部分に注目してください  

```gd
# ーーーーーーーー
# キー・コンフィグ
# ーーーーーーーー

var key_config_background_image_name = &"🗻崎川駅前"


# ーーーーーーーー
# ビジュアル・ノベル
# ーーーーーーーー

# 最初に実行する部門をここに書く。頭に「📗」を付けているのは見やすさのためで、付けなくても構わない
var start_department_name = &"📗会話部門_🍉JapaneseRiver"
```

👆　キーコンフィグ画面の背景画像の名前を指定しています。  

```plaintext
[シーンウィンドウ]
  👥Staff
  └─ 👤Illustrator    👈　（１）このノードの中の
```

```plaintext
[シーンウィンドウ]
  📂🍉KeyConfig
  ├─ ーーーー背景（Ｚ＝０）ーーーー
  └─ 🗻崎川駅前    👈　（２）このノードで指定されている画像リソースが
```

👆　（３）　キーコンフィグ画面の背景に表示されます  

また、ビジュアルノベルとして最初に実行される部門名を指定しています。  
ビジュアルノベルについては後で説明します  

# ビジュアルノベル

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ 🎄addon_🍉visual_novel
	├─ 👤musician_🌏bg_musics.tscn
	├─ 👤musician_🌏sound_fx.tscn
	├─ 👤programmer_🌏message_windows.tscn
	├─ 👤programmer_🎬scenario_player.tscn
	├─ 👤programmer_📂department_controller.tscn
	├─ 👤programmer_📂message_windows.tscn
	├─ 👤scenario_writer_🐵monkey.tscn
	├─ 👤scenario_writer_📂visual_novel.tscn
	└─ 👤telop_coordinator.tscn
```

👆　ビジュアルノベルを動かすには上記のシーンが必要なので、全部 [シーンウィンドウ] へコピーしておいてください  

# `👥Staff`

まだゲームは動きません  

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ ⚓local_🍉VictoryBalancer
	└─ staff.gd		👈　（１）このファイルを
```

```plaintext
[シーンウィンドウ]
  👥Staff    👈　（２）このノードの上へ
```

👆　（３）ドラッグ＆ドロップしてください  

staff.gd ファイルの中身は以下のように書かれています  

```gd
# スタッフ（Staff；制作者）
extends Node2D


# ーーーーーーーー
# ノード・パス関連
# ーーーーーーーー

# ディレクター・ハブ取得
func monkey():
	return $"🐵Monkey"


# ーーーーーーーー
# 初期化
# ーーーーーーーー

# サブツリーが全てインスタンス化されたときに呼び出される
# Called when the node enters the scene tree for the first time.
func _ready():
	self.monkey().programmer().owner_node().ready_in_staff()
```

👆　`_ready()` 関数が最初に呼び出されると思ってください。  

# `👤Programmer` ノード

まだゲームは動きません  

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ ⚓local_🍉VictoryBalancer
	└─ programmer.gd		👈　（１）このファイルを
```

```plaintext
[シーンウィンドウ]
  👥Staff
	└─ 👤Programmer    👈　（２）このノードの上へ
```

👆　（３）ドラッグ＆ドロップしてください  

👇　以下の２つの Node を作成してください  

```plaintext
[シーンウィンドウ]
  👥Staff
	└─ 👤Programmer
	  ├─ 🐵Monkey    👈　（１）これ
	  └─ 🕹️Input    👈　（２）これ
```

👇　以下の２つのファイルをアタッチしてください  

```plaintext
[ファイルシステムウィンドウ]
  res://
  └─ ⚓local_🍉VictoryBalancer
	├─ programmer_input.gd		👈　（２）これ
	└─ programmer_monkey.gd		👈　（１）これ
```

👇　以下の

```plaintext
[シーンウィンドウ]
  👥Staff
	└─ 👤Programmer
	  └─ 🎬🍉KeyConfig    👈　（１）このノードに
```

（２） `🍋scripts\🪑grayscale_🍉key_config\👤programmer\🎬🍉key_config\key_config.gd` ファイルをアタッチしてください  

# `🎄addon_🍉japanese_river`

`🎄addon_🍉japanese_river` をコピーして持ってきて、自分のプロジェクト名 `🎄addon_🍉victory_balancer` などに名前を変えてください  
以下同様  

# `👤ScenarioWriter` ノード

以下のノードを作成してください  

```plaintext
[シーンウィンドウ]
  👥Staff
	└─ 👤ScenarioWriter
	  ├─ 🐵Monkey_🍉VisualNovel    👈　（１）これ
	  └─ 📘DepartmentControl    👈　（２）これ
```

👆　（２） `📘DepartmentControl` ノードに、 `🍋scripts\🪑grayscale_🍉victory_balancer\👤scenario_writer\switch_department.gd` ファイルをアタッチしてください  

（１） `🐵Monkey_🍉VisualNovel` ノードに、 `🍋scripts\🪑grayscale_🍉victory_balancer\👤scenario_writer\scenario_writer_monkey.gd` ファイルをアタッチしてください  
