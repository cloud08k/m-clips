---
title: "Pocket終了に備えてObsidian Web Clipperに移行した話"
source: "https://www.wantedly.com/companies/wantedly/post_articles/978503"
author:
  - "[[冨永 康二郎]]"
published: 2025-05-28
created: 2026-06-08
description: "こんにちは。ウォンテッドリーのEnablingチームでバックエンドエンジニアをしている冨永(@kou_tominaga)です。Enablingチームでは技術的な取り組みを社外にも発信すべく、メン..."
tags:
  - "clippings"
image: "https://www.wantedly.com/post_articles/978503/ogp_image"
---
![header](https://www.wantedly.com/post_articles/978503/ogp_image)

[冨永 康二郎](https://www.wantedly.com/users/163268744)

Wantedly, Inc. / Dev Branch

こんにちは。ウォンテッドリーのEnablingチームでバックエンドエンジニアをしている冨永([@kou\_tominaga](https://x.com/kou_tominaga))です。Enablingチームでは技術的な取り組みを社外にも発信すべく、メンバーが週替わりで技術ブログをリレー形式で執筆しています。前回は市古さんによる「 [BigQuery × GitHubで始める行動量の可視化【AI導入後の変化をラフに捉えるために】](https://www.wantedly.com/companies/wantedly/post_articles/976929) 」 でした。今回は「Pocket終了に備えてObsidian Web Clipperに移行した話」についてです。

Mozilla社が提供していた「あとで読む」サービス [Pocketが2025年7月8日で終了](https://support.mozilla.org/en-US/kb/future-of-pocket#w_when-is-pocket-shutting-down) します。技術記事やインスピレーションになる投稿を日々集めておりPocketの終了は大きな痛手でした。

そこで代替ツールを検討した結果「 [Obsidian Web Clipper](https://obsidian.md/clipper) 」に移行することを決めました。本記事では私がなぜObsidian Web Clipperを選び、どのように移行を進めたかをまとめます。移行先を検討している方の参考になれば幸いです。

## Obsidianとは？

ObsidianはMarkdown形式でノートを作成・管理できるローカル保存型のノートアプリです。 特徴的なのは以下点です。

- ノートはすべてローカルファイルとして保存される（クラウド依存なし）
- Markdown形式なのでエンジニアにもなじみやすい
- ノート同士をリンクできる「内部リンク機能」が強力
- プラグインやカスタマイズ性が高く、知識ベース構築にも使われる

すでに日々のメモや読書ノートをObsidianで管理している人も多く、知識を育てるツールとして注目されています。[Obsidian - Sharpen your thinking](https://obsidian.md/)

[

The free and flexible app for your private thoughts.

](https://obsidian.md/)

## なぜObsidian Web Clipper？

### PCとモバイルの両方から「あとで読む」の登録ができる

PCとモバイル両方に対応したブラウザ拡張機能があり、そこからWeb Clipperを呼び出して記事を登録できます。私は移動中に情報収集することが多いため、モバイル環境で使えることは必須条件でした。

### 豊富な拡張機能によりカスタマイズできる

Obsidian Web ClipperはRaindropなど他の「あとで読む」ツールと比べると、視認性にやや不安がありました。ですが、拡張機能によるカスタマイズが可能で自分なりに見やすい形に整えることが可能でした。

### Markdownで残せる

ObsidianはMarkdownファイルを直接編集・管理できるノートアプリでWebクリップもMarkdown形式で保存されます。LLMでの解析や活用に適した形式である事や、使い慣れたMarkdown形式は私にとって魅力的でした。

### Obsidianで全てを一元管理

すでにメモ・日報・読書ノートなどをObsidianで管理していたので「Web記事もObsidianで一元管理したい」という思いが決め手になりました。[Obsidian Web Clipper](https://obsidian.md/clipper)

[

Highlight and capture web pages in your favorite browser. Save anything and everything with just one click.

](https://obsidian.md/clipper)

## Obsidian Web Clipperの導入手順

### Vaultの準備

Obsidian上にWebクリップ専用のVault（またはフォルダ）を作成。私の場合は既存のVault内に `webclips/` というディレクトリを作成しました。

### ブラウザ拡張のインストール

[こちら](https://obsidian.md/clipper) から利用しているブラウザに一致する拡張機能をインストールしました。

### Obsidianと連携

拡張機能の設定で以下を指定しました。

- Vaultのパス
- 保存するフォルダパス（例: `webclips/` ）
- テンプレートのプロパティ（後述）

### テンプレートのプロパティ設定

プロパティの設定ではタイトルやURLなどの変数を使って自由にレイアウトを設定できます。カード形式で表示したいので以下形式でテンプレートを登録しました。

![]()

※ [公式ドキュメント](https://help.obsidian.md/web-clipper/variables#Preset+variables) から利用できる変数を確認できます。

## Pocketからのデータ移行

### Pocketからのエクスポート

[こちら](http://getpocket.com/export) から保存済みの記事をCSV形式でエクスポートします。CSVは「 `title,url,time_added,tags,status」` の形式で出力されました。

### CSVファイルをMarkdownにして登録する

以下Rubyで記載したスクリプトを実行して、PocketからエクスポートしたCSVファイルをMarkdownファイルに変換しました。

```ruby
require 'csv'
require 'fileutils'

# Pocketからエクスポートしたファイルのパスを設定する
POCKET_CSV_PATH = 'XXXXXX'
# Markdownファイルの出力先のパスを設定する
OBSIDIAN_VAULT_PATH = 'XXXX'

puts "#{OBSIDIAN_VAULT_PATH} への変換を開始します。"
FileUtils.mkdir_p(OBSIDIAN_VAULT_PATH)

CSV.foreach(POCKET_CSV_PATH, headers: true, liberal_parsing: true) do |row|
  title = row['title']
  url = row['url']
  time_added = row['time_added']
  status = row['status']

  next if url.nil? || title.strip.empty?

  # front matterのタイトルはダブルクオートで囲む必要があるためダブルクオートをエスケープ
  yaml_title = title.gsub('"', '\"')

  # ファイル名に使えない文字を除去
  safe_title = title.gsub(/[\/:*?"<>|\\]/, '').strip[0..50]
  filename = "#{safe_title}.md"

  # 作成日時
  created_at = Time.at(time_added.to_i).strftime('%Y-%m-%d')

  content = <<~MARKDOWN
    ---
    title: "#{yaml_title}"  
    source: #{url}  
    author:
    created: #{created_at}  
    description:
    tags: #{["webclip", status]}
    caverImageUrl:
    ---

    #{title} を Pocket から移行しました。  
  MARKDOWN

  File.write(File.join(OBSIDIAN_VAULT_PATH, filename), content)
end

puts "完了！#{OBSIDIAN_VAULT_PATH} に Markdown を出力しました。"
```

## Obsidianの設定

Pocketのデータが移行できたので表示するための設定をします。

- コミュニティプラグイン [Detaview](https://blacksmithgu.github.io/obsidian-dataview/) のインストール
- - tagを指定したデータを取得するために利用します
		- Enable JavaScript queriesをONにしてください
- テーマ [Minimal](https://minimal.guide/home) を有効にする
- - カード表示を利用するために利用します

そしてファイルを作成して以下を貼り付けます。  
※デフォルトで表示したい画像がある場合はDEFAULT\_IMAGEに画像のURLを設定してください。  
※ [こちら](https://minimal.guide/cards#Helper+classes) のHelper classを利用すればカードの表示形式をカスタマイズできます。

```
---
cssclasses:
  - cards
  - cards-16-9
---

\`\`\`dataviewjs
const DEFAULT_IMAGE_URL = "XXXXX";

dv.table(["Cover", "Title", "Created"],
  dv.pages('"webclips"')
    .sort(p => p.created, 'desc')
    .map(p => [
      \`![](${p.caverImageUrl ?? DEFAULT_IMAGE_URL})\`,
      p.file.name,
      p.description,
      p.created
    ])
)
\`\`\`
```

リーディングビューで閲覧すると以下形式で表示されます。

![]()

## まとめ

Pocketの終了は残念でしたが、結果として自分に合った管理スタイルを見直す良いきっかけになりました。 **情報収集を資産に変えたい** 人にとってObsidian Web Clipperは非常に相性の良いツールです。これからもWeb記事は読むだけでなく、活用するというスタンスで取り入れていきたいと思います。

Wantedly, Inc.では一緒に働く仲間を募集しています

- [Webプロダクト開発エンジニア](https://www.wantedly.com/projects/2389039)
- [PdM](https://www.wantedly.com/projects/1635459)
- [仕組み作りが好きな人歓迎✨️](https://www.wantedly.com/projects/2398579)
- 他33件の職種