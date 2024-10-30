# プロジェクトの作り方

# シーンウィンドウを準備する

Redot ではゲームオブジェクトを ノード（Node） と呼び、  
ツリー階層のことを シーン（Scene） と呼びます。  
他のゲームエンジンと比べ、用語が独特なので、読み替えてください  

👇　とりあえずシーンウィンドウの第１階層、第２階層のノードを、  
他の Muzudho 制のプロジェクトを真似て新規作成してください。  
ノードの中身や、その下のノードは、あとで整えれば構いません  

```plaintext
👥Staff
├─ ⚙Config
├─ 🐵Monkey
├─ Grid
├─ 👤Illustrator
├─ 👤Musician
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

# git の準備をする

👇　他の人が書いた記事を読んでください  

📖 [【Godot4】Gitでのバージョン管理：準備編① Git/GitHub環境構築](https://hiramame-gclab.com/godot4_git_part1_inst/)  

👇　git をダウンロードしてください  

📖 [git > Downloads](https://git-scm.com/downloads)  

👇　ターミナルでコマンドを打鍵してください  

入力：  

```shell
git -v
```

出力例：  

```plaintext
git version 2.47.0.windows.2
```

[Git Hub](https://github.com/) にアカウントを開設しておいてください。  
説明は省略します  

👇　以下のコマンドを打鍵して、 git を設定してください  

```shell
git config --global user.name {GitHubのユーザー名}
git config --global user.email {GitHubに登録してあるメールアドレス}
git config --list
```

git の設定が一覧されたら、ユーザー名とメールアドレスが保存されていることを確認してください。  
メモ：一覧画面から抜けられないとき、 `:q` と打鍵してエンターキーを打鍵する？？  

## git の SSH 設定

👇　以下のコマンドを打鍵してください  

入力：  

```shell
ssh-keygen -t rsa
```

出力：  

```plaintext
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\muzud/.ssh/id_rsa):
```

質問は全て空欄のまま、エンターキーを打鍵し続けてください。  
📁 `C:\Users\{ユーザー名}\.ssh` フォルダーに公開鍵、秘密鍵が保存されます  

```plaintext
C
└─ Users
  └─ {ユーザー名}
	└─  .ssh
	  ├─ id_rsa			# 秘密鍵
	  └─ id_rsa.pub		# 公開鍵
```

👇　以下のコマンドを打鍵してください（クリップボードに公開鍵をコピーします）  
Power Shell だと `<` 記号がエラーになるので、 Command Prompt を使うか、ファイルを直接開いて中身をコピーしてください  

```shell
clip < C:/Users/{ユーザー名}/.ssh/id_rsa.pub
```

[GitHub > Settings > SSH keys](https://github.com/settings/ssh) ページを開き、[New SSH key] ボタンをクリックしてください。  
[Add new SSH Key] ページが開きます。  

* `Title` - 任意のタイトルを入力
* `Key type` - `Authentication Key` を選択
* `Key` - `[Ctrl]+[V]` キーで貼り付け

[Add SSH key] ボタンをクリックしてください。  
２要素認証の入力が求められるかもしれません。入力してください  

👇　以下のコマンドを打鍵してください（Git Hubに接続できるか確認します）  

入力：  

```shell
ssh -T git@github.com
```

出力：  

```plaintext
The authenticity of host 'github.com (20.27.177.113)' can't be established.
～中略～
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

入力：  

```shell
yes
```

出力：  

```plaintext
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Hi {ユーザー名}! You've successfully authenticated, but GitHub does not provide shell access.
```

以上で接続成功です  

Git Hub の方にリモートリポジトリを作っておいてください。  
説明は省略します  

👇　Redot エディターを開いているＰＣ（ローカルＰＣ）の方に
ローカルリポジトリを作ってください  

* プロジェクト作成時に［バージョン管理メタデータ：Git］を選択しておいてください

👇　ターミナルから以下のコマンドを打鍵してください  
`Redotのプロジェクトフォルダーへのパス` は、 [ファイルシステムウィンドウ] の `res://` を右クリックして [ターミナルで開く] を選べば出てきます  
パスにスペースが含まれている場合は、ダブルクォーテーション（`"`）で挟んでください  

```shell
cd {Redotのプロジェクトフォルダーへのパス}
```

👇　以下のコマンドを打鍵してください（ローカルリポジトリを作成します）  

```shell
git init
```

📁 `.git` というフォルダーが作られました  

Git Hub のリモートリポジトリの `Code` という緑色のボタンの [Local] - [SSH] タブを開き、  
アドレスをコピーしてください  

例： `git@github.com:{ユーザー名}/{リモートリポジトリ名}.git`  

👇　以下のコマンドを打鍵してください  

```shell
git remote add origin {コピーしたアドレス}
git remote -v
```

一覧が表示されるので、コピーしたアドレスが記憶されていることを確認してください  

# ステージング

👇　以下のコマンドを打鍵してください  

```shell
git add --all
git status
```

これからローカルまたはリモートのリポジトリにアップロードしようとしているファイルの一覧が表示されていることを確認してください  

# コミット

👇　以下のコマンドを打鍵してください（ローカルリポジトリに変更を保存します）  
ダブルクォーテーションで囲んだメッセージは任意に記述してください  

```shell
git commit -m "初回コミット"
```

# プッシュ

👇　以下のコマンドを打鍵してください（リモートリポジトリに変更を保存します）  

書式：  

```shell
git push {リポジトリ名} {<ローカルブランチ名}:{リモートブランチ名}
```

例：  

```shell
git push origin main:main
```
