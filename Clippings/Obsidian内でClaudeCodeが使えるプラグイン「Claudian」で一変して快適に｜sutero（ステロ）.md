---
title: "Obsidian内でClaudeCodeが使えるプラグイン「Claudian」で一変して快適に｜sutero（ステロ）"
source: "https://note.com/sutero/n/ncdf112dba547"
author:
  - "[[sutero（ステロ）]]"
published: 2026-04-12
created: 2026-06-09
description: "デジタルでの記録として、様々なアプリやサービスを試しては挫折を繰り返し、メモアプリ迷子って投稿をしてたりもする程度に色々使って来た中で、何とか使い続けていたのがObsidian。  Markdown形式の書式とファイル構成という、シンプルな仕組みが気に入ってはいたけれど、増えていくメモなファイルをリンクで繋げて関連するものを簡単に辿ることが出来る、というのを意識して新規ファイルを作らないといけないってのが、何とも苦戦したというか苦手で。  それが、「Claudian」というプラグインを活用して、ClaudeCodeをObsidian内で走らせることが可能となり、一変しましたよ、と。"
tags:
  - "clippings"
image: "https://assets.st-note.com/production/uploads/images/266888244/rectangle_large_type_2_f2e9dac18bad744acaeaaf0d55a235d7.png?width=1280"
---
![header](https://assets.st-note.com/production/uploads/images/266888244/rectangle_large_type_2_f2e9dac18bad744acaeaaf0d55a235d7.png?width=1280)

デジタルでの記録として、様々なアプリやサービスを試しては挫折を繰り返し、メモアプリ迷子って投稿をしてたりもする程度に色々使って来た中で、何とか使い続けていたのがObsidian。

Markdown形式の書式とファイル構成という、シンプルな仕組みが気に入ってはいたけれど、増えていくメモなファイルをリンクで繋げて関連するものを簡単に辿ることが出来る、というのを意識して新規ファイルを作らないといけないってのが、何とも苦戦したというか苦手で。

それが、「Claudian」というプラグインを活用して、ClaudeCodeをObsidian内で走らせることが可能となり、一変しましたよ、と。

## Claudian以前

### それまでのObdisianの使い方

とにかくひたすら、何か書くことがある場合にはデイリーノートって、日付がタイトルなファイルに箇条書き。

以前に書いたものと関連している場合は、気付けばバックリンクを貼る程度で、記録を蓄積させることに注力し「いつか何とかしよう」程度で、ある意味フワッとした感じで、溜めるだけ溜めていた。

### AIが使えないか？

ここ1年程度で、生成AI系が様々な使われ方をするという事例が圧倒的に増え、ObsidianとClaudeCodeを連携させるというのも目にし始める。

ターミナルで、VScodeで、Cursorで、zedで、と、色々な連携方法があるってのは試してみるしかないと、実際にIDE系を入れてObsidianの保管庫と呼ばれるVaultフォルダをそれらで開いてみたり。

しかし、全然しっくり来ない。

一応、メモ以外の仕事的な部分では、zedというコードエディタ上で、エージェントとしてClaudeCodeを動かして作業するように。

### Claude.aiに聞いてみる

課金してClaudeCodeを使うようになってからは、ブラウザでもClaude.aiをよく使うようになる。

ふと「Obsidian内でClaudeCodeをイイ感じで使いたいんだけど？」みたいなことを聞いてみた時に、たくさん提案が返って来た。

ほとんどが、前述した、他のアプリやサービスとの連携だったり、使いにくそうなプラグインを提案され、「それ試したけど合わない」という返答を繰り返していて、最後に出て来たのが「Claudianというのが最近出てるよ」との回答。

## Claudian導入

ここから、Obsidian内の導入メモを引用。

---

### Claudianとは

ObsidianにClaude Codeをまるごと組み込んだプラグイン。Claude Code SDKを内蔵しており、チャット型のアシスタントではなく、ファイル操作・外部API通信・分析・レポート作成まで一連の作業を自律的に実行できるフルエージェント型。

- **GitHub**: [https://github.com/YishenTu/claudian](https://github.com/YishenTu/claudian)
- **課金方式**: Claudeサブスクリプション定額内で動作（API従量課金ではない）
- **MCP対応**: Gmail、Googleカレンダー、ブラウザ操作、Notionなど外部サービスと接続可能

### 導入の前提条件

- Claudeのサブスクリプション契約（Pro $20/月 または Max $100/月以上）
- Node.js v18以上

### セットアップ手順

**1\. Claude Code CLIのインストール  
**（既に導入済み）

[**高度なセットアップ - Claude Code Docs** *Claude Code のシステム要件、プラットフォーム固有のインストール、バージョン管理、およびアンインストール。* *code.claude.com*](https://code.claude.com/docs/ja/setup)

**2\. Claudianのインストール** ~~**（BRAT経由）**~~

1. Obsidian設定 → コミュニティプラグイン → 有効化
2. ~~「閲覧」ボタン →~~ [~~**BRAT**~~](https://github.com/TfTHacker/obsidian42-brat) ~~を検索してインストール・有効化  
	~~「閲覧」ボタン → **Claudian** を検索してインストール・有効化
3. ~~BRATの設定画面 →「Add beta plugin」→ YishenTu/claudian を入力~~
4. コミュニティプラグインに「Claudian」が表示されていることを確認
5. Claudianの設定 → Languageを「日本語」に切り替え

> 現在、Claudianがベータ版から公式のコミュニティプラグインになったので、インストール方法の一部を変更しました。

BRAT経由のベータ版で使っている人向けに乗り換え方法を書きました。

<iframe height="210" data-src="https://note.com/embed/notes/n83a3c2dd577c" src="https://note.com/embed/notes/n83a3c2dd577c"></iframe><iframe allowfullscreen="" allow="autoplay *; encrypted-media *; ch-prefers-color-scheme *" src="https://cdn.iframe.ly/8lAYyiRS?v=1&amp;app=1"></iframe>

---

Obsidian内の導入メモを引用終わり。

## Claudianでメモが楽々

### Obsidianに馴染む

![画像](https://assets.st-note.com/img/1775991621-c3uw7nMOfqCGmbaJFN5PS4se.png?width=1200)

Obsidian内でClaudianを使ってるサンプル。

見た目的には、VScodeやCursorだったり、zedで使っているのと同じ感じで、Obsidianのウィンドウ内にClaudeCodeのチャット欄があって、ここで質問したり、開いているファイルについての指示だったりをする感じ。

他のIDEなエディターと圧倒的に違っているのは、プラグインなので、 **Obsidian固有の操作とClaudeCodeのAI的な操作を切り替えなしのシームレスに行える点** 。

非エンジニアな人間にとっては、Obsidianさえ開いておけば、全て完結させられるというのが、とにかくデカい。

### リンクで繋ぐも楽々

Obsidianで便利なのは分かっているが、自分のみだとなかなか上手く繋げられなかったリンクも、ファイル作成時に関連するものをClaudeCodeが自動的にやってくれる。

Claudian導入以前のファイル同士でも、日本語のテキストでClaudeCodeに頼めば簡単に教えてくれて繋いでくれるし。

この部分が、一番大きいし、単にメモして溜めるだけだったのが、意識せずとも、対話しながらメモすることで、ファイルもリンクも勝手に作成されていく。

### 設定は必要

Claudianを通してClaudeCodeに指示してファイルを作成するだけでは、リンクまでは基本的にはされない。

もちろん、ファイル作成の指示の時に関連するものをリンクして、と言えば、やってはくれるけれど、CLAUDE.mdという設定ファイルに記述しておけば、ファイル作ってだけでリンクしてくれるようになる。

コレが出来るから、Obsidian一択になってしまったと言っても過言ではない。

### 自分の設定

CLAUDE.mdという設定用のファイルもClaudianで「CLAUDE.mdを作りたい」と言えば、提案しながら作ってはくれる。

自分もそうやって作った。

リンクを作成する部分の指示内容を書いておきましょう。

```ruby
## 新規ノート作成時のwikilink構築

新しいノートを作成するときは、以下の手順で関連ノートへのリンクを構築する：

1. **関連ノートを探す**：作成するノートのテーマ・タグに近い既存ノートを〇〇を中心にGrepで検索する（〇〇にはよく使ってるフォルダをいくつか指定することで、トークン消費を抑えられる）
2. **リンクを提案する**：見つかった関連ノートをユーザーに提示し、\`related:\` への追加とフロントマター更新を提案する（フロントマターにrelatedを記述しているので）
3. **双方向リンクを検討する**：必要に応じて、既存ノート側の \`related:\` にも新規ノートへのリンクを追加する（確認を取ってから）
```

こんな感じの5行程度の指示が記述してあるだけ。

ここに辿り着くまでに色々とやってみてはいて、つい最近知った、「LLM Wiki」という仕様書を参考にしてこういう感じに。

> [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)

### 試行錯誤が資産に

まだ、Obsidian+ClaudeCodeという組み合わせで運用を半月程度しか経過していないが、様々な方法を試してみている。

ムダっぽい部分も当然あるけれど、参考になりそうなものを見つけると、とにかく試してみている。

こればっかりは、自分で実際に指示したり使ってみないと分からない。

普段のメモもだが、こうした設定に関する試行錯誤の記録も、半自動的にObsidianには蓄積されている。

その、試行錯誤の流れが残っていることで、ClaudeCodeもそれを汲んで提案してくれるし、ある意味資産となっている。

使うのに慣れてくると、今度はトークン消費と制限との戦いになる。

しかし、便利でObsidianを有効利用しているという実感はある。

### claudian使い始めたら次はスキル

<iframe height="180" data-src="https://note.com/embed/notes/n1e44caafe742" src="https://note.com/embed/notes/n1e44caafe742"></iframe><iframe height="210" data-src="https://note.com/embed/notes/n2be437e390a2" src="https://note.com/embed/notes/n2be437e390a2"></iframe>

### Codexも導入してみた

<iframe height="180" data-src="https://note.com/embed/notes/n41b7a6035a34" src="https://note.com/embed/notes/n41b7a6035a34"></iframe><iframe height="210" data-src="https://note.com/embed/notes/n53690d4d84f0" src="https://note.com/embed/notes/n53690d4d84f0"></iframe><iframe height="180" data-src="https://note.com/embed/notes/n1bb64c179299" src="https://note.com/embed/notes/n1bb64c179299"></iframe>

---

[**実践Claude Code入門―現場で活用するためのAIコーディングの思考法** *amzn.to*](https://amzn.to/4efgK2W)

[*3,300円* (2026年04月13日 01:13時点](https://amzn.to/4efgK2W)

[

Amazon.co.jpで購入する

](https://amzn.to/4efgK2W)

[**開発効率をアップする！ Claude Code 実用入門** *amzn.to*](https://amzn.to/4th5kR1)

[*3,300円* (2026年04月13日 01:14時点](https://amzn.to/4th5kR1)

[

Amazon.co.jpで購入する

](https://amzn.to/4th5kR1)

---

<iframe height="186" data-src="https://note.com/embed/notes/n5665a4ffbb09" src="https://note.com/embed/notes/n5665a4ffbb09"></iframe><iframe height="210" data-src="https://note.com/embed/notes/n5ceb1398d6b0" src="https://note.com/embed/notes/n5ceb1398d6b0"></iframe><iframe height="207" data-src="https://note.com/embed/notes/n3740c97c89ec" src="https://note.com/embed/notes/n3740c97c89ec"></iframe>