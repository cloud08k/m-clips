---
title: "仕組みを理解する動画を、Claude Codeに作らせると便利すぎる"
source: "https://zenn.dev/explaza/articles/c749042ecbe232"
author:
published: 2026-10-21
created: 2026-10-22
description:
tags:
  - "clippings"
image: "https://res.cloudinary.com/zenn/image/upload/s---OmM6dY2--/c_fit%2Cg_north_west%2Cl_text:notosansjp-medium.otf_55:%25E4%25BB%2595%25E7%25B5%2584%25E3%2581%25BF%25E3%2582%2592%25E7%2590%2586%25E8%25A7%25A3%25E3%2581%2599%25E3%2582%258B%25E5%258B%2595%25E7%2594%25BB%25E3%2582%2592%25E3%2580%2581Claude%2520Code%25E3%2581%25AB%25E4%25BD%259C%25E3%2582%2589%25E3%2581%259B%25E3%2582%258B%25E3%2581%25A8%25E4%25BE%25BF%25E5%2588%25A9%25E3%2581%2599%25E3%2581%258E%25E3%2582%258B%2Cw_1010%2Cx_90%2Cy_100/g_south_west%2Cl_text:notosansjp-medium.otf_34:musoukun%2Cx_220%2Cy_108/bo_3px_solid_rgb:d6e3ed%2Cg_south_west%2Ch_90%2Cl_fetch:aHR0cHM6Ly9zdGF0aWMuemVubi5zdHVkaW8vdXNlci11cGxvYWQvYXZhdGFyLzQzOWQzZGM0MGMuanBlZw==%2Cr_20%2Cw_90%2Cx_92%2Cy_102/co_rgb:6e7b85%2Cg_south_west%2Cl_text:notosansjp-medium.otf_30:%25E6%25A0%25AA%25E5%25BC%258F%25E4%25BC%259A%25E7%25A4%25BE%25E3%2582%25A8%25E3%2582%25AF%25E3%2582%25B9%25E3%2583%2597%25E3%2583%25A9%25E3%2582%25B6%2Cx_220%2Cy_160/bo_4px_solid_white%2Cg_south_west%2Ch_50%2Cl_fetch:aHR0cHM6Ly9zdGF0aWMuemVubi5zdHVkaW8vdXNlci11cGxvYWQvYXZhdGFyL2Q2ZDNkY2FmNzUuanBlZw==%2Cr_max%2Cw_50%2Cx_139%2Cy_84/v1627283836/default/og-base-w1200-v2.png?_a=BACMTiAE"
---
![header](https://res.cloudinary.com/zenn/image/upload/s---OmM6dY2--/c_fit%2Cg_north_west%2Cl_text:notosansjp-medium.otf_55:%25E4%25BB%2595%25E7%25B5%2584%25E3%2581%25BF%25E3%2582%2592%25E7%2590%2586%25E8%25A7%25A3%25E3%2581%2599%25E3%2582%258B%25E5%258B%2595%25E7%2594%25BB%25E3%2582%2592%25E3%2580%2581Claude%2520Code%25E3%2581%25AB%25E4%25BD%259C%25E3%2582%2589%25E3%2581%259B%25E3%2582%258B%25E3%2581%25A8%25E4%25BE%25BF%25E5%2588%25A9%25E3%2581%2599%25E3%2581%258E%25E3%2582%258B%2Cw_1010%2Cx_90%2Cy_100/g_south_west%2Cl_text:notosansjp-medium.otf_34:musoukun%2Cx_220%2Cy_108/bo_3px_solid_rgb:d6e3ed%2Cg_south_west%2Ch_90%2Cl_fetch:aHR0cHM6Ly9zdGF0aWMuemVubi5zdHVkaW8vdXNlci11cGxvYWQvYXZhdGFyLzQzOWQzZGM0MGMuanBlZw==%2Cr_20%2Cw_90%2Cx_92%2Cy_102/co_rgb:6e7b85%2Cg_south_west%2Cl_text:notosansjp-medium.otf_30:%25E6%25A0%25AA%25E5%25BC%258F%25E4%25BC%259A%25E7%25A4%25BE%25E3%2582%25A8%25E3%2582%25AF%25E3%2582%25B9%25E3%2583%2597%25E3%2583%25A9%25E3%2582%25B6%2Cx_220%2Cy_160/bo_4px_solid_white%2Cg_south_west%2Ch_50%2Cl_fetch:aHR0cHM6Ly9zdGF0aWMuemVubi5zdHVkaW8vdXNlci11cGxvYWQvYXZhdGFyL2Q2ZDNkY2FmNzUuanBlZw==%2Cr_max%2Cw_50%2Cx_139%2Cy_84/v1627283836/default/og-base-w1200-v2.png?_a=BACMTiAE)

## 最近は動画で説明資料を作っている

アプリの仕組みをお客さんに説明するとき、構成図とかHTML・Markdownで、説明するのが一般的かと思いますが

最近はjavascriptを用いて、Claudeで動画を生成しやすくなったので、アプリの操作と、その裏で起きている処理を交互に見せる解説動画を作って説明に使っています。

めちゃくちゃ便利なので、Claude Code に作らせる指示テンプレートと、動画の作りを紹介します。

<iframe src="https://embed.zenn.studio/card#zenn-embedded__196494d7a30a4" frameborder="0" height="122"></iframe>上記の  
**「animated-arch-diagram」スキルです。**

## 完成形

まずこんな感じの動画が出ます（44秒）。

![](https://www.youtube.com/watch?v=fP8p30uolMw)

この記事では、架空の図書館の本探しチャットをダミーで作り、同じ指示で動画を作り直しました。（画面に出てくる本や数字は、すべてこのダミーアプリのものです。）

![](https://res.cloudinary.com/zenn/image/fetch/s--n8VcxB7l--/v1/explainer-video-sample/article/images/explainer-zenn.gif?_a=BACMTiAE)

## 方法

手順は3つです。

1. animated-arch-diagram スキルを Claude Code に入れます。
2. 説明したいアプリのディレクトリで、指示テンプレートのアプリ名を記載して、Claude Code に渡します。

スキルは上のリポジトリの `animated-arch-diagram` フォルダを、 `~/.claude/skills/` にコピーすれば使えます。

2.の記録は、送った質問、途中の結果（区切った語、10冊の点数）、返事を JSON にしたものです。動画に出す数字は、全部ここから取ります。

### 指示テンプレート（サンプル）

```
【アプリ名】の解説動画を作って。形式は「操作 → 仕組み → 操作 → 仕組み」の交互。

- 操作の場面：実画面の録画ではなく、それっぽいモック画面でよい。カーソルが動いてクリックし、クリックや入力に合わせてズームする（Screen Studio 風）
- 仕組みの場面：送った文字などを、Mac の全画面切り替えのように画面いっぱいに広げて引っ張り出す。そのまま処理の様子を動きで見せる（例：文字が区切られる、順位表の棒が伸びて並べ替わる）
- 構成図：全体の構成図は、操作の合間に該当する部分だけ差し込む
- 数字・例：画面に出す数字や例は実データから取る。例は【使いたい質問例】、【使わない例】は使わない
- 字幕：下に小見出しと一行の字幕。
```

モック画面は、本物そっくりに作った見本の画面のことです。Screen Studio は、クリックした場所に自動で寄ってくれる画面録画アプリです。

今回のダミーアプリでは、下記のように指示しています。

| 【】 | 書き換えた内容 |
| --- | --- |
| アプリ名 | みどり町図書館の本探しチャット |
| 使いたい質問例 | 「猫が出てくる小説を読みたい」 |
| 使わない例 | 実在する本のタイトル |

## 指示と動画の対応

指示の各行が、実際の動画ではこのように表現されます。

| 指示 | 動画ではこうなる |
| --- | --- |
| クリックや入力に合わせてズーム | 入力欄やボタンを押す前に、そこへ寄る |
| 送った文字を画面いっぱいに引っ張り出す | 吹き出しが広がって、中の文字も一緒に大きくなる |
| 処理の様子を動きで見せる | 文が9語に区切られる。10冊の棒が伸びて並べ替わる |
| 構成図は該当部分だけ差し込む | 操作のあとに、いま通った箱だけ光る |
| 数字は実データから取る | 9語、10冊の点数、差1点、棚の場所は、アプリの記録のまま |
| 下に小見出しと一行の字幕 | KUROMOJI、SCORE などの小見出しと、1行の字幕 |

入力欄に寄ってから質問を打つ様子  
![](https://static.zenn.studio/user-upload/31c1952f4ee5-20261021.png)

送った吹き出しが、横に広がるイメージ  
![](https://static.zenn.studio/user-upload/a67d9f8becad-20261021.png)

広がった文が9語に区切られ、名詞の「猫」「小説」だけが強調される。  
![](https://static.zenn.studio/user-upload/3b8d62bd3ad1-20261021.png)

検索ランキングの中から上位に当たったものを取り出す様子。  
![](https://static.zenn.studio/user-upload/3fac6bf5060b-20261021.png)

操作の合間に、いま通った処理だけを強調した構成図を挟んで説明。  
![](https://static.zenn.studio/user-upload/f3533be902c2-20261021.png)

## 作り

動画は画面を録画していません。「時刻を渡すと、その瞬間の絵を描く Web ページ」を作って  
1コマずつ撮ってつないでいます。  
撮るのは Playwright（ブラウザを自動で動かす道具）で、ffmpeg（動画を作る）で撮ったものを動画にしています。  
何度書き出しても同じ動画になる点が良いです。

### 撮る部分の処理

やっていることは、時間経過で画面を動かすことで、何かしらを描かせて  
その様子を撮るを繰り返すイメージです。

```
// 1/30 秒ずつ時刻を進めて、そのたびに描かせて撮る
for (let i = 0; i < frames; i++) {
  await page.evaluate((t) => ARCH.render(t), i / 30);
  ffmpeg.stdin.write(await page.screenshot({ type: 'jpeg' }));
}
```

※44秒の動画は1314コマあり、だいたい書き出しは手元の Mac で45秒ほどでした。

### 動画の作り方

場面ごとに「何秒目に何をするか」を並べて書きます。  
操作1の場面の例だとこんな感じ。

```
steps: [
  { at: 0.5, cursor: 'input', dur: 0.8 },       // カーソルを入力欄へ動かす
  { at: 0.7, zoom: 'form', z: 1.8, dur: 1.0 },  // 入力欄に 1.8 倍で寄る
  { at: 1.4, click: 'input' },
  { at: 1.6, type: R.question, cps: 6 },        // 記録の質問を、1秒に6文字で打つ
  { at: 4.1, cursor: 'send', dur: 0.5 },
  { at: 4.7, click: 'send', show: 'm1' },       // 送信すると吹き出しが出る
  { at: 5.0, zoom: 'm1', z: 2.0, dur: 0.9 },    // 出た吹き出しに寄る
],
```

`R` がアプリの記録です。

```
{ at: 6.2, kicker: 'CHOOSE', text: \`1位と2位の差が${R.gap}点なので、上位3冊を候補にする\` },
```

※アプリを直して流し直せば、字幕の数字も一緒に変わります。

## 感想

Claudeでこういうのがポンと出せるようになって、動画制作がしやすくなっていると思う。すごく進化しているなぁと。

34