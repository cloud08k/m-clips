---
title: "Claude Codeの設定を複数のMacで同期する方法【Git+シンボリックリンク】｜KAWAI"
source: "https://note.com/kawaidesign/n/n61970a877b79"
author:
  - "[[KAWAI]]"
published: 2026-03-30
created: 2026-08-19
description: "この記事は全文無料（期間限定）で閲覧できます。   見出し画像はAIで生成しました。 プロンプトは100,000文字超えの記事に掲載中。  Claude Codeを複数のMacで使っていると、端末を変えるたびにCLAUDE.mdやrulesがない状態からのスタートになります。  この記事では、4台のMacから全く同じ設定でClaude Codeを動かすためのセットアップ手順を、コピペできるコマンド付きで解説します。  所要時間は5分。一度やれば、以降は git push / git pull だけで全端末の設定が揃います。   【先着100名限定ウェビナー】 笑っちゃうほど簡単な C"
tags:
  - "clippings"
image: "https://assets.st-note.com/production/uploads/images/263286272/rectangle_large_type_2_91ae379e5b0b633e5dca12dd568c09db.jpeg?width=1280"
---
![header](https://assets.st-note.com/production/uploads/images/263286272/rectangle_large_type_2_91ae379e5b0b633e5dca12dd568c09db.jpeg?width=1280)

> この記事は **全文無料（期間限定）** で閲覧できます。

見出し画像はAIで生成しました。  
プロンプトは100,000文字超えの記事に掲載中。

<iframe data-src="https://note.com/embed/notes/n09dd9fcc4810" src="https://note.com/embed/notes/n09dd9fcc4810" height="230px"></iframe>

Claude Codeを複数のMacで使っていると、端末を変えるたびにCLAUDE.mdやrulesがない状態からのスタートになります。

この記事では、4台のMacから全く同じ設定でClaude Codeを動かすためのセットアップ手順を、コピペできるコマンド付きで解説します。

所要時間は5分。一度やれば、以降は git push / git pull だけで全端末の設定が揃います。

---

**【先着100名限定ウェビナー】**  
**笑っちゃうほど簡単な Claude Code入門**

連日満席のため、増枠しました！

<iframe height="210" data-src="https://note.com/embed/notes/n6b3f4de8acce" src="https://note.com/embed/notes/n6b3f4de8acce"></iframe>

【 もう導入は済んだ方はこちら 】

**もうパワポには絶対に戻れない**  
**〜Claude Codeによる非常識なスライド制作〜**

無料申し込みはこちら

[**もうパワポには絶対に戻れない 〜Claude Codeによる非常識なスライド制作〜** *応援チケットは、4/7（火）22時半までお求めいただけます。 特典の送付は、全てのチケット販売終了後、4/7（火）22時半* *miraichi0406.peatix.com*](https://miraichi0406.peatix.com/)

## なぜ端末ごとに設定がバラバラになるのか

Claude Codeのユーザー設定は **\`~/.claude/\`** というフォルダに保存されています。このフォルダは端末ローカルなので、Mac Aで作り込んだ設定はMac Bには反映されません。

公式ドキュメントにも「 **Auto memory is machine-local（端末ごとにローカル）** 」と明記されています。

つまり、普通に使っている限り、端末ごとに設定がバラバラになるのは仕様通りの動作です。

## 解決策：Git + シンボリックリンク

iCloud DriveやDropboxで同期する方法もありますが、シンボリックリンクとの相性問題が起きることがあります（特にiCloudはシンボリックリンク先を正しく同期しないケースがある）。

**Gitで管理するのがベスト** です。理由は3つ。

- 変更履歴が残る。「前の設定に戻したい」ができる
- CLAUDE.mdやrulesはテキストファイルなのでGitと相性が良い
- GitHubのプライベートリポジトリなら安全（無料プランでも作成可）

## 同期すべきファイルと、してはいけないファイル

**\`~/.claude/\`** の中身は全部同期すればいいわけではありません。

大きく2種類に分かれます。

![画像](https://assets.st-note.com/img/1774839486-CLMJzljEwDZq35hHXnNg4Yf0.png?width=1200)

## セットアップ手順

---

### Step 1：メインのMacでGitリポジトリを作る

```swift
mkdir ~/claude-config
cd ~/claude-config
git init
```

同期したいファイルをコピーします。

```javascript
cp ~/.claude/CLAUDE.md .
cp ~/.claude/settings.json .
cp -r ~/.claude/rules .
```

**\`commands/\`** や **\`hooks/\`** がある場合はそれらもコピーしてください。

```ruby
cp -r ~/.claude/commands .   # あれば
cp -r ~/.claude/hooks .      # あれば
```

---

### Step 2：GitHubのプライベートリポジトリにpush

```cs
git add -A && git commit -m "initial"
git remote add origin git@github.com:自分のアカウント/claude-config.git
git push -u origin main
```

事前にGitHubでプライベートリポジトリを作っておいてください。

---

### Step 3：シンボリックリンクに置き換え

シンボリックリンクとは「ショートカット」のようなものです。 **\`~/.claude/CLAUDE.md\`** を開くと、実体は **\`~/claude-config/CLAUDE.md\`** を見に行く仕組みになります。

まず元ファイルを退避します。

```javascript
mv ~/.claude/CLAUDE.md ~/.claude/CLAUDE.md.bak
mv ~/.claude/settings.json ~/.claude/settings.json.bak
mv ~/.claude/rules ~/.claude/rules.bak
```

> **重要：** \`mv\`（移動）してから \`ln\`（リンク）を張ります。既にフォルダが存在する状態で \`ln -s\` すると、フォルダの中にリンクが作られてしまうためです。

シンボリックリンクを作成します。

```javascript
ln -s ~/claude-config/CLAUDE.md ~/.claude/CLAUDE.md
ln -s ~/claude-config/settings.json ~/.claude/settings.json
ln -s ~/claude-config/rules ~/.claude/rules
```

正しく張れたか確認します。

```javascript
ls -la ~/.claude/CLAUDE.md
```

**\`-> /Users/自分/claude-config/CLAUDE.md\`** と表示されればOKです。

---

### Step 4：他の端末でも同じことをやる

```java
git clone git@github.com:自分のアカウント/claude-config.git ~/claude-config
```

あとはStep 3と同じです。既存ファイルを退避してリンクを張ります。

```javascript
mv ~/.claude/CLAUDE.md ~/.claude/CLAUDE.md.bak
mv ~/.claude/settings.json ~/.claude/settings.json.bak
mv ~/.claude/rules ~/.claude/rules.bak

ln -s ~/claude-config/CLAUDE.md ~/.claude/CLAUDE.md
ln -s ~/claude-config/settings.json ~/.claude/settings.json
ln -s ~/claude-config/rules ~/.claude/rules
```

## 運用のコツ

設定を変更したら、その端末でpushします。

```cs
cd ~/claude-config
git add . && git commit -m "update" && git push
```

他の端末では、作業を始める前にpullします。

```
cd ~/claude-config
git pull
```

これだけです。シンボリックリンクが張ってあるので、pullした瞬間にClaude Codeの設定も更新されます。

---

### 注意点

2台の端末で同時に設定を変更すると、Gitのコンフリクト（衝突）が起きます。基本は「 **1台で変更 → push → 他の端末で pull** 」の流れを守ってください。

慣れてきたら、CLAUDE.md自体に「 **設定ファイルを変更したら ~/claude-config で git add, commit, push して** 」と書いておくと、Claude Codeが自動で同期してくれるようになります。

## projects/ を同期しなくて大丈夫？

大丈夫です。

**\`projects/\`** はClaude Codeが作業中に自動で蓄積するメモリ（Auto Memory）で、ディレクトリのパスをキーにして管理されています。

例えば **\`/Users/kawai/myproject\`** で作業すると **\`-Users-kawai-myproject/\`** というフォルダが自動生成されます。

端末ごとにユーザー名やパスが異なれば別のキーになるため、同期しても意味がありません。そして同期しなくても、各端末で作業するうちに自然と蓄積されていきます。

本当に大事なのは **\`CLAUDE.md\`** と **\`rules/\`** です。ここに自分の指示やルールが集約されていれば、どの端末でも同じ振る舞いになります。

## まとめ

- **\`~/.claude/\`** は端末ローカル。複数Macで使うなら同期の仕組みが必要
- Git + シンボリックリンクがベスト。iCloud/Dropboxよりトラブルが少ない
- 同期すべきは **\`CLAUDE.md\`,** **\`settings.json\`**, **\`rules/\`** の3つ。 **認証情報** と **\`projects/\`** は同期しない

セットアップは5分、運用は git push / git pull だけ。まずはメインのMacで **\`~/claude-config\`** を作るところから始めてみてください。

---

**【先着100名限定ウェビナー】**  
**笑っちゃうほど簡単な Claude Code入門**

連日満席のため、増枠しました！

<iframe height="210" data-src="https://note.com/embed/notes/n6b3f4de8acce" src="https://note.com/embed/notes/n6b3f4de8acce"></iframe>

【 もう導入は済んだ方はこちら 】

**もうパワポには絶対に戻れない**  
**〜Claude Codeによる非常識なスライド制作〜**

無料申し込みはこちら

[**もうパワポには絶対に戻れない 〜Claude Codeによる非常識なスライド制作〜** *応援チケットは、4/7（火）22時半までお求めいただけます。 特典の送付は、全てのチケット販売終了後、4/7（火）22時半* *miraichi0406.peatix.com*](https://miraichi0406.peatix.com/)

noteメンバーシップに参加すると700本以上の記事が読み放題です。

[**KAWAI BOOKS｜KAWAI** *1,000本以上の記事が読み放題。AI × デザインを主軸に、独自の視点やノウハウをお届けします。AI時代にキャリアアップ* *note.com*](https://note.com/kawaidesign/membership)

書籍「AIでゼロからデザイン」好評発売中

[**AIでゼロからデザイン** *www.amazon.co.jp*](https://www.amazon.co.jp/dp/4798193429?tag=note0e2a-22&linkCode=ogi&th=1&psc=1&language=ja_JP)

[*2,310円* (2026年05月05日 22:04時点](https://www.amazon.co.jp/dp/4798193429?tag=note0e2a-22&linkCode=ogi&th=1&psc=1&language=ja_JP)

[

Amazon.co.jpで購入する

](https://www.amazon.co.jp/dp/4798193429?tag=note0e2a-22&linkCode=ogi&th=1&psc=1&language=ja_JP)

お問い合わせ・個別相談・法人研修のご依頼などはこちら

[**KAWAI DESIGN | 川合卓也 公式サイト** *AI × デザインでビジネスに「熱」と「純度」を。株式会社SHIFT AI デザイン部長、川合卓也のオフィシャルサイト。* *kawai-official.pages.dev*](https://kawai-official.pages.dev/)

[#AI](https://note.com/hashtag/AI) [#生成AI](https://note.com/hashtag/%E7%94%9F%E6%88%90AI) [#AIエージェント](https://note.com/hashtag/AI%E3%82%A8%E3%83%BC%E3%82%B8%E3%82%A7%E3%83%B3%E3%83%88) [#AI時代](https://note.com/hashtag/AI%E6%99%82%E4%BB%A3) [#AI活用](https://note.com/hashtag/AI%E6%B4%BB%E7%94%A8) [#AI人材](https://note.com/hashtag/AI%E4%BA%BA%E6%9D%90) [#AI研修](https://note.com/hashtag/AI%E7%A0%94%E4%BF%AE) [#AIツール](https://note.com/hashtag/AI%E3%83%84%E3%83%BC%E3%83%AB) [#デザイン](https://note.com/hashtag/%E3%83%87%E3%82%B6%E3%82%A4%E3%83%B3) [#デザイナー](https://note.com/hashtag/%E3%83%87%E3%82%B6%E3%82%A4%E3%83%8A%E3%83%BC)

---

参考：

- [Claude Code公式ドキュメント（設定）](https://code.claude.com/docs/en/settings)
- [Claude Code公式ドキュメント（メモリ）](https://code.claude.com/docs/en/memory)
- [Claude Code公式ドキュメント（認証）](https://code.claude.com/docs/en/authentication)

### メンバーシップ ¥ 980 /月〜

1,000本以上の記事が読み放題。AI × デザインを主軸に、独自の視点やノウハウをお届けします。A…[このメンバーシップの詳細](https://note.com/kawaidesign/membership/join)

538名が参加中

[ログイン](https://note.com/login?redirectPath=%2Fkawaidesign%2Fn%2Fn61970a877b79)

- [
	#AI
	](https://note.com/hashtag/AI)
- [
	#生成AI
	](https://note.com/hashtag/%E7%94%9F%E6%88%90AI)
- [
	#AI活用
	](https://note.com/hashtag/AI%E6%B4%BB%E7%94%A8)
- [
	#デザイン
	](https://note.com/hashtag/%E3%83%87%E3%82%B6%E3%82%A4%E3%83%B3)
- [
	#Claude
	](https://note.com/hashtag/Claude)
- [
	#AIエージェント
	](https://note.com/hashtag/AI%E3%82%A8%E3%83%BC%E3%82%B8%E3%82%A7%E3%83%B3%E3%83%88)
- [
	#デザイナー
	](https://note.com/hashtag/%E3%83%87%E3%82%B6%E3%82%A4%E3%83%8A%E3%83%BC)
- [
	#ClaudeCode
	](https://note.com/hashtag/ClaudeCode)
- [
	#AI時代
	](https://note.com/hashtag/AI%E6%99%82%E4%BB%A3)
- [
	#AIツール
	](https://note.com/hashtag/AI%E3%83%84%E3%83%BC%E3%83%AB)
- [
	#Github
	](https://note.com/hashtag/Github)
- [
	#Git
	](https://note.com/hashtag/Git)
- [
	#AI研修
	](https://note.com/hashtag/AI%E7%A0%94%E4%BF%AE)
- [
	#AI人材
	](https://note.com/hashtag/AI%E4%BA%BA%E6%9D%90)

14