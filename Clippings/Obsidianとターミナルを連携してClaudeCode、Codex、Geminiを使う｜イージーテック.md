---
title: "Obsidianとターミナルを連携してClaudeCode、Codex、Geminiを使う｜イージーテック"
source: "https://note.com/ez_tech/n/nf1eee623b122"
author:
  - "[[イージーテック]]"
published: 2026-05-20
created: 2026-06-08
description: "今回はObsidianとターミナルを連携してやろうっていう内容のnoteです。  これまでObsidianとClaudianを使ってClaudeCodeやCodexと連携するっていうことをやってきましたが今回はターミナルですね。  ターミナルと連携することによって、こんな風にObsidianにターミナルを突っ込んで、そこで指示をして作業することができるようになります。  ターミナルからClaudeCodeやCodexを呼んで、Obsidianのメモを書いてもらったりっていうことができます。  やることはターミナル連携とAIのCLI活用  やることとしてはObsidianにターミナル"
tags:
  - "clippings"
image: "https://assets.st-note.com/production/uploads/images/277876879/rectangle_large_type_2_e48f08a7d9cdf4cc70c56429ea67b97c.png?width=1280"
---
![header](https://assets.st-note.com/production/uploads/images/277876879/rectangle_large_type_2_e48f08a7d9cdf4cc70c56429ea67b97c.png?width=1280)

今回はObsidianとターミナルを連携してやろうっていう内容のnoteです。

これまでObsidianとClaudianを使ってClaudeCodeやCodexと連携するっていうことをやってきましたが今回はターミナルですね。

<iframe data-src="https://note.com/embed/notes/n0bab625e5f2a" src="https://note.com/embed/notes/n0bab625e5f2a" height="230px"></iframe><iframe data-src="https://note.com/embed/notes/n453968d50526" src="https://note.com/embed/notes/n453968d50526" height="230px"></iframe>

ターミナルと連携することによって、こんな風にObsidianにターミナルを突っ込んで、そこで指示をして作業することができるようになります。

![画像](https://assets.st-note.com/img/1779033232-0Ml8R1zrnhoHgx29imOuUE6C.png?width=1200)

ターミナルからClaudeCodeやCodexを呼んで、Obsidianのメモを書いてもらったりっていうことができます。

## やることはターミナル連携とAIのCLI活用

やることとしてはObsidianにターミナルを突っ込んで、そこからCLI版のAIツールを使うっていう方法です。

![画像](https://assets.st-note.com/img/1779033235-0DaBrwR9n6Y4TcIWZfuMUml3.png?width=1200)

ですので、そもそも使いたいAIのCLIツールがインストールされていないとObsidianにターミナルを連携したとしてもそれらを使うことはできません。単にターミナル作業ができるだけです。

### AIのCLIが入っているか確認する

- geminiと入力・・・GeminiCLIが入っているか確認
- codexと入力・・・codexが入っているか確認
- claudeと入力・・・ClaudeCodeが入っているか確認
![画像](https://assets.st-note.com/img/1779033238-2t0lRruxECzKb3w4GgHJQDiI.png?width=1200)

Gemini

![画像](https://assets.st-note.com/img/1779033240-wFKQr27E1SURJ5xeIzcpDL0t.png?width=1200)

Codex

![画像](https://assets.st-note.com/img/1779033243-VU4B9p8EkdYTNRtvhrqcGKZC.png?width=1200)

ClaudeCode

各CLIのインストール方法は公式のドキュメントを見てみるといいです。

[**クイックスタート - Claude Code Docs** *Claude Code へようこそ！* *code.claude.com*](https://code.claude.com/docs/ja/quickstart)

## ターミナルプラグインをインストールする

さあターミナルをObsidianにインストールしましょう。コミュニティプラグインからTerminalを見つけます。

![画像](https://assets.st-note.com/img/1779033246-w4qE9I1PjTpZ3HxrmhNg0iKa.png?width=1200)

これをインストールします。

![画像](https://assets.st-note.com/img/1779033253-DLbzmoRyG5vd7IhrWKi0XE3U.png?width=1200)

## ターミナルの設定

Terminalをインストールしたら設定をします。 **Defaultプロファイルを統合** にしましょう。

![画像](https://assets.st-note.com/img/1779033257-mIbES80g3FQiqdTYaGBnWZ4K.png?width=1200)

統合にしておくとObisidianの中でターミナルを開くことができます。外部だとアプリケーションの外で開いちゃうんですよね。

**（ただWindowsの場合は外部で開いちゃうので、後で少し設定をします）**

そしたらTerminalのアイコンをクリックすればターミナルを出すことができます。

![画像](https://assets.st-note.com/img/1779033330-SPYV7QthIsLowNkRUu4DjKze.png?width=1200)

このターミナルはドラッグして右側に寄せることができるので、使いづらかったらドラッグしておくといいです。

![画像](https://assets.st-note.com/img/1779033480-OhFkBjJIysgHYqxbnAwDmUNo.png?width=1200)

右側にターミナルを配置して使う

## シェルを変更する

プロファイルをクリックして、使いたいシェルを選択します。

![画像](https://assets.st-note.com/img/1779033504-45smJC6Y390wMBIuTlFR7ipc.png?width=1200)

![画像](https://assets.st-note.com/img/1779033515-OkKumMihJSoDNRl8IcEzH62Q.png?width=1200)

Defaultプロファイルには今設定したものを選択しておくといいでしょう。

![画像](https://assets.st-note.com/img/1779033526-PsbjeHy3huAwkQmoiOW9Gd8B.png?width=1200)

例えばPowerShellを選択するとこんな感じでPowerShellになります。

![画像](https://assets.st-note.com/img/1779033539-no95mVpvTcQKCwB8uJFRqfeX.png?width=1200)

## Windowsの場合は外部でターミナルが出る

Windowsの場合はターミナルが外部で出てしまいます。

![画像](https://assets.st-note.com/img/1779037684-q8uUQV6b5RB1DHGAgiF0oZaS.png?width=1200)

これはストレスが溜まるのでなんとかしたいですよね。プラグインのGithubにWindowsについて書かれているので手順に沿って進めます。

[https://github.com/polyipseity/obsidian-terminal](https://github.com/polyipseity/obsidian-terminal)

書かれているコマンドを実行です。

![画像](https://assets.st-note.com/img/1779033585-ABWjmghkeP9bnqTLGHEzNJdp.png?width=1200)

コマンドを実行したら、プロファイルから、使っているものの右側の編集ボタンをクリックして下の方にあるPython実行ファイルを編集します。

![画像](https://assets.st-note.com/img/1779033608-naWNpHfGMUEd2mSKcoF4t7vC.png?width=1200)

ここをpythonにしておきます。右側のボタンを押すとチェックしてくれるので、そこでエラーが出なかったらOKです。

![画像](https://assets.st-note.com/img/1779033674-ANE9dS1bqmwxrURTyvkgVz0Q.png?width=1200)

これでターミナルを再度使ってみると、 **一瞬ターミナルの画面が出てしまいます** がマシな状態にはなりました。

![画像](https://assets.st-note.com/img/1779033703-M3lKVzsfaUhmZTLx5Xv0JbI7.png?width=1200)

うーんやっぱりWindowsちょと面倒そうですね。一瞬出るのはしょうがないのかな。

## Gemini CLI終わるみたい

追記しているんですけど、GemniCLI終わるみたいなのでこれからはAntigravityCLIっていうやつ使うのがいいかもです。

[**An important update: Transitioning Gemini CLI to Antigravity CLI- Google Developers Blog** *Announcement for the sunsetting of Gemini CLI in favor of Ant* *developers.googleblog.com*](https://developers.googleblog.com/an-important-update-transitioning-gemini-cli-to-antigravity-cli/)