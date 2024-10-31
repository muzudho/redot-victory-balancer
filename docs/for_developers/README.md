# プロジェクトの作り方

# シーンウィンドウを準備する

Redot ではゲームオブジェクトを ノード（Node） と呼び、  
ツリー階層のことを シーン（Scene） と呼びます。  
他のゲームエンジンと比べ、用語が独特なので、読み替えてください  

👇　とりあえずシーンウィンドウの以下のような第１～３階層のノードを、  
他の Muzudho 制のプロジェクトを真似て新規作成してください。  
ノードの中身や、その下のノードは、あとで整えれば構いません  

```plaintext
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
res://
├─ 中略
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
  └─ 🐵Monkey    👈　（２）このファイルの上へ
```

👆　（３）ドラッグ＆ドロップしてください  
それで `🐵Monkey` ノードに `staff_monkey.gd` スクリプトがアタッチされます  

Redot エディターのプレイボタンをクリックすると、今度は `MonkeyHelper` が無いというエラーが出ます  
Redot エディターの停止ボタンをクリックしてください  
