---
title: "NotebookLMを卒業してClaudeでポッドキャストを作るやり方 | ライフハッカー・ジャパン"
source: "https://www.lifehacker.jp/article/2606generated-a-research-podcast-using-claude-opus-embarrassed-every-notebooklm-episode/"
author:
  - "[[ライフハッカー・ジャパン編集部]]"
published: 2026-06-30
created: 2026-07-05
description: "GoogleのNotebookLMが生成するAIポッドキャストの「マンネリ感」に悩んでいませんか？本記事では、オープンソースの「Open Notebook」を活用し、頭脳にClaude 4.8 Opusを採用して自分好みの極上音声解説を作る方法を紹介。ビジネスパーソンのインプットを豊かにする新アプローチを解説します。"
tags:
  - "clippings"
image: "https://media.loom-app.com/loom/2026/06/28/8d3cecca-2a68-4ca0-998e-7e7c12d93c30/original.jpg?w=563"
---
![header](https://media.loom-app.com/loom/2026/06/28/8d3cecca-2a68-4ca0-998e-7e7c12d93c30/original.jpg?w=563)

<iframe frameborder="0" src="https://faf6fd5892ea593940e4998c0622d254.safeframe.googlesyndication.com/safeframe/1-0-45/html/container.html" title="サードパーティの広告コンテンツ" width="360" height="50" aria-label="広告"></iframe>

![NotebookLMを卒業してClaudeでポッドキャストを作るやり方](https://media.loom-app.com/loom/2026/06/28/8d3cecca-2a68-4ca0-998e-7e7c12d93c30/original.jpg?w=563)

Image: MakeUseOf

Advertisement

<iframe frameborder="0" src="https://faf6fd5892ea593940e4998c0622d254.safeframe.googlesyndication.com/safeframe/1-0-45/html/container.html" title="サードパーティの広告コンテンツ" width="360" height="202" aria-label="広告"></iframe>

NotebookLMのPodcastを生成する「音声概要（Audio Overviews）」機能。

ポッドキャストが大好きで、AirPodsを片時も手放せない私にとって、まさに自分専用に仕立てられたかのような機能だと大興奮したものです。

そんな生活が、ある日 **「Claude 4.8 Opus」** というモデルを使って、たった1つのポッドキャストエピソードを生成するまでは続いたのです。

その出来栄えは、これまでに作ったNotebookLMの音声概要が、少し色あせて見えてしまうほどでした。

[!["全部のせ"の最新ルンバが、この価格？しかもユーザーに寄り添う手厚いサービス付き](https://cdn-content-production.cxpublic.com/962fae4a13f254e1193c5c828c55d6868706f94402dada4921aab3d8806dd212.jpg)](https://s-adserver.cxad.cxense.com/adserver/click/NV53IDEWQw7xy_RNVGPJFj5ugd2IDq7thXzdcte6HNllixNDMvao3We-rce6Zt9Nzkg0I3r0zxT_PFZLQrXoTalzAVB87TPNjcvNcsjQU8mcXTKKDA9yJzSIFnpFWVmxA08o2oPEJwiovSFYgyFnkFY4n1lK-KfOE3CAwocFSJjtlRi1Is7M-HOVaI-TrrM.)

["全部のせ"の最新ルンバが、この価格？しかもユーザーに寄り添う手厚いサービス付き](https://s-adserver.cxad.cxense.com/adserver/click/NV53IDEWQw7xy_RNVGPJFj5ugd2IDq7thXzdcte6HNllixNDMvao3We-rce6Zt9Nzkg0I3r0zxT_PFZLQrXoTalzAVB87TPNjcvNcsjQU8mcXTKKDA9yJzSIFnpFWVmxA08o2oPEJwiovSFYgyFnkFY4n1lK-KfOE3CAwocFSJjtlRi1Is7M-HOVaI-TrrM.)

## どんな資料も、なぜか同じテンションに？

![](https://media.loom-app.com/loom/2026/06/28/e632bf1b-77b1-435f-8029-ecf4e718b43f/original.jpg?w=640)

台本執筆（LLM）： 対話の流れや内容を考える頭脳 データ処理（埋め込みモデル）： 資料をAIが理解できるように変換する役割 音声合成（TTS）： 完成した台本を声に出して読み上げる役割

NotebookLMのポッドキャストは、最初は感動します。しかし、私のように日常的に何本も聴いていると、少しずつ不自然な部分が気になり始めます。

この問題の根本にあるのは、台本を書いているAIモデルそのものの「個性（パーソナリティ）」です。どんな大規模言語モデル（LLM）にも、特定の書き方の癖や好みのフレーズ、特有のリズムが存在します。

**NotebookLMはGoogleの製品なので、当然中身はGeminiモデル（現在はGemini 3.5）です。**

つまり、私が感じていたマンネリを打破するには、台本を書く「頭脳」そのものを変えるしかありません。しかし、NotebookLMにはそんな選択肢は用意されていないのです。 **そこで登場するのが、「Open Notebook」というアプローチでした。**

Advertisement

[![暑さが「貯まってる！」に。セールでカンタンにはじめるJackeryの自家発電](https://cdn-content-production.cxpublic.com/3ba441c1c22a58140d49c4bf734be76bff9a2e04622da45c631b6bff39417176.jpg)](https://s-adserver.cxad.cxense.com/adserver/click/CnpME_HhoHfyT_u5D9_nM5ayziPG02fhqbWObJ5UmAGwxy_GIopjWNM-WC4WrTnjmSmCCo3Xb9ivHgpAuu4b5w0Qe3Wo-YhOQ8ZrpsKlhslEsUm6Hjotpvpts459NZOiu-uwNLyZ29-N55X-c8J7fyj3QjHkcLqXmA8X9zaR7r0Q_PryKA9qeBsuRTooyrI.)

[暑さが「貯まってる！」に。セールでカンタンにはじめるJackeryの自家発電](https://s-adserver.cxad.cxense.com/adserver/click/CnpME_HhoHfyT_u5D9_nM5ayziPG02fhqbWObJ5UmAGwxy_GIopjWNM-WC4WrTnjmSmCCo3Xb9ivHgpAuu4b5w0Qe3Wo-YhOQ8ZrpsKlhslEsUm6Hjotpvpts459NZOiu-uwNLyZ29-N55X-c8J7fyj3QjHkcLqXmA8X9zaR7r0Q_PryKA9qeBsuRTooyrI.)

## 自分好みの頭脳を選べる、もう一つの選択肢

![](https://media.loom-app.com/loom/2026/06/28/05b8c5d3-a84d-4d32-a8d1-9e773319536d/original.jpg?w=640)

台本執筆（LLM）： 対話の流れや内容を考える頭脳 データ処理（埋め込みモデル）： 資料をAIが理解できるように変換する役割 音声合成（TTS）： 完成した台本を声に出して読み上げる役割

「 [Open Notebook](https://www.open-notebook.ai/) 」は、NotebookLMの仕組みを再現した、オープンソースかつ自分でサーバーを用意して動かす（セルフホスト型の）代替ツールです。 **開発者のLuis Novo氏がGitHub上で公開しており、MITライセンスで提供されています。**

自分のパソコンやローカル環境で動かすため、Googleのサーバーにデータを送る必要がありません。Dockerという仕組みを使って手元で立ち上げるのですが、正直なところ、初期設定は少し手がかかります。

私もガジェットや技術には強い方だと自負していますが、最初にDockerとOpen Notebookを連携させて動かす時は、かなり苦戦しました。

しかし、機能面での設計思想は、私がNotebookLMを気に入った理由そのものでした。

PDF、ウェブリンク、テキストファイル、YouTube動画、さらにはPowerPointのスライドまで、読み込ませた資料にしっかりと基づいて動作します。要約やインサイトの抽出はもちろん、お目当てのポッドキャスト生成もバッチリこなしてくれます。

[![晴れた日はベランダへ。自分でつくって使う「自家発電」がもたらす新しい達成感](https://cdn-content-production.cxpublic.com/eae98ef76430fc08cf3052618dfad1726d73704576ba77fb57361137bb609351.jpg)](https://s-adserver.cxad.cxense.com/adserver/click/u0oDDOwm15zh-ZZnhgi80FHvwnBkYf2mj4AxF49DnHOs3oLXGio9wv6aQlroM1PGXPPqKWqmBObXS7fUzu0esa-cyqqplT0vPvG5NyJwn62rrxxwC2p0MncVUXe8kAVsOFEKseJb4UPSud2Yan_uFdvg02CgMR82lpS2ifokvW10KSKjhbseYvH1gaq9Klo.)

[晴れた日はベランダへ。自分でつくって使う「自家発電」がもたらす新しい達成感](https://s-adserver.cxad.cxense.com/adserver/click/u0oDDOwm15zh-ZZnhgi80FHvwnBkYf2mj4AxF49DnHOs3oLXGio9wv6aQlroM1PGXPPqKWqmBObXS7fUzu0esa-cyqqplT0vPvG5NyJwn62rrxxwC2p0MncVUXe8kAVsOFEKseJb4UPSud2Yan_uFdvg02CgMR82lpS2ifokvW10KSKjhbseYvH1gaq9Klo.)

## Open Notebookの最大の魅力

プライバシー面で優れていること以上に、私がこのツールに惹かれたのは「プロセスのあらゆる段階で、好きなAIモデルを指名できる」という点です。

- **台本執筆（LLM）：** 対話の流れや内容を考える頭脳
- **データ処理（埋め込みモデル）：** 資料をAIが理解できるように変換する役割
- **音声合成（TTS）：** 完成した台本を声に出して読み上げる役割

NotebookLMではGemini一択ですが、Open Notebookなら、お持ちのAPIキー（Anthropic、OpenAI、Google、xAIなど）を登録するだけで、その提供元が持つ最新モデルを自由に選べます。

十分なスペックのPCがあれば、完全にローカルなAIモデルを使うことも可能で、データを一歩も外に出さずに完結させられます。

Advertisement

[![七夕セール！買い切り型クラウドストレージが今オトク](https://cdn-content-production.cxpublic.com/fb6a421a198378f1bd9112e0c87ed8b6263f6f61e9f4f7bc37f47b82c52964ff.png)](https://s-adserver.cxad.cxense.com/adserver/click/hHF1TMIjWWt9mKRQ1wedBhPUsCezoMYpPpYlMkXTN-Wk2TQAyDcBLUyE9yNDdAwpIMjXdSgT7u70Jn--z0zDIOMAsyA_tqnZcTqiO8RR13J3zIgNaS8jUgOoNlLQWUwjzd8xeL4iK6nnaPGJdps-fUVNt6CvkeNyApRfs01S9hMmZWgK08QajoabQ7G5Z0M.)

[七夕セール！買い切り型クラウドストレージが今オトク](https://s-adserver.cxad.cxense.com/adserver/click/hHF1TMIjWWt9mKRQ1wedBhPUsCezoMYpPpYlMkXTN-Wk2TQAyDcBLUyE9yNDdAwpIMjXdSgT7u70Jn--z0zDIOMAsyA_tqnZcTqiO8RR13J3zIgNaS8jUgOoNlLQWUwjzd8xeL4iK6nnaPGJdps-fUVNt6CvkeNyApRfs01S9hMmZWgK08QajoabQ7G5Z0M.)

## 表現力豊かな「Claude」をディレクターに迎えてみた

![](https://media.loom-app.com/loom/2026/06/28/35c9067c-06f3-4d0f-bdd0-bff1e805e691/original.jpg?w=640)

台本執筆（LLM）： 対話の流れや内容を考える頭脳 データ処理（埋め込みモデル）： 資料をAIが理解できるように変換する役割 音声合成（TTS）： 完成した台本を声に出して読み上げる役割

今回の実験では、クリエイティブな文章作成やストーリーテリングで最も評価の高い、 **Anthropicの「Claude 4.8 Opus」を台本担当に選びました。**

このモデル自体は音声合成の機能を持っていないため、資料の処理にはOpenAIの「text-embedding-3-small」を、音声の出力にはOpenAIの「tts-1」を組み合わせる計画体系にしました。 **つまり、Claudeにじっくり考えてもらい、周囲の技術的な処理をOpenAIにサポートしてもらう体制です。**

Dockerの設定さえ終われば、あとはそれぞれのAPIキーを取得してOpen Notebookに入力するだけ。今回はツール内に新しいノートを作成し、「Z世代のメンタルヘルスサービスに対する意識」に関する、全80ページの博士論文（PDFファイル）を読み込ませてみました。

[![イヤホンを「二刀流で使い分ける」という選択肢](https://cdn-content-production.cxpublic.com/f3c117154bc16b1c14d383e7eafdae0d7627b91bb114cee8e29d949d14ce960e.jpg)](https://s-adserver.cxad.cxense.com/adserver/click/tBrrwEckYHudd88Uju05UgQXkfhi2FxeLoSs-8wyeWXAo89Vs9dQtHkrsHWuh8NwTAY5nX9iBBgnEr5B4Cy0pda6rWN5JIPmRJweYtxKSG8ykkFiRFZv6Yez3cQcSUemPoxgTyH98q2VkE0tmFri6yhUGCfSI7XxN0-qJbiZZaNpTe-JK0E3yiPv0UbPiAI.)

[イヤホンを「二刀流で使い分ける」という選択肢](https://s-adserver.cxad.cxense.com/adserver/click/tBrrwEckYHudd88Uju05UgQXkfhi2FxeLoSs-8wyeWXAo89Vs9dQtHkrsHWuh8NwTAY5nX9iBBgnEr5B4Cy0pda6rWN5JIPmRJweYtxKSG8ykkFiRFZv6Yez3cQcSUemPoxgTyH98q2VkE0tmFri6yhUGCfSI7XxN0-qJbiZZaNpTe-JK0E3yiPv0UbPiAI.)

## 音声生成の手順と、仕上がるまでの流れ

ポッドキャストを作る前に、エピソードや話し手のプロフィールを細かく設定します。

1. ホストの人数を設定する。
2. 話し方のトーンや雰囲気を指定する。
3. 構成案の作成、台本執筆、音声合成のそれぞれに、どのAIモデルを割り当てるか選択する。

このように、これから作る音声のあらゆる要素を自分でコントロールできます。プロフィールを整え、いざ生成ボタンを押しました。

生成プロセスは段階的に進みます。

まずClaude（Opus）がエピソード全体の4部構成のプロットを組み立て、それを1行ずつのセリフへと落とし込んでいき、計31行の台本を書き上げました。

**台本が完成すると、次はOpenAIの音声モデルが1行ずつ音声データへ変換し、それらを綺麗に繋ぎ合わせて1本の番組に仕上げてくれます。**

ボタンを押してから、実際に聴ける20分間のエピソードが完成するまでにかかった時間は約18分。ほぼ等倍の待ち時間です。

とはいえ、待ち時間のほとんどは音声の変換処理によるものです。Claudeが台本を書き上げる自体は2分ほどで終わり、残りの16分はOpen Notebookが音声を順次処理していく時間でした。

[次ページ  
専門家が目の前で語りかけてくるような贅沢な体験](https://www.lifehacker.jp/article/2606generated-a-research-podcast-using-claude-opus-embarrassed-every-notebooklm-episode/?page=2)

[1](https://www.lifehacker.jp/article/2606generated-a-research-podcast-using-claude-opus-embarrassed-every-notebooklm-episode/) [2](https://www.lifehacker.jp/article/2606generated-a-research-podcast-using-claude-opus-embarrassed-every-notebooklm-episode/?page=2)

あわせて読みたい![見たい位置から動画がスタート!?YouTubeの新AI検索「Ask YouTube」を試してみた](https://media.loom-app.com/loom/2026/06/10/fdfd854f-be96-430b-92a8-c8db033559d3/original.png?w=180&h=120)

見たい位置から動画がスタート!?YouTubeの新AI検索「Ask YouTube」を試してみた

[

見たい位置から動画がスタート!?YouTubeの新AI検索「Ask YouTube」を試してみた

](https://api.cxense.com/public/widget/click/dxvYJsrj-x5BguwIGeIWRPgd8EfQQXOv9JnzDj0UfDiYpEnWQZO_AJTNjlR29CiBMLlUNKbMHSltMpDl6HkKx8lyZ-2czd_0EwpT4azXTRs_Krf2CiX4mRdxCoMWhbwjpBZXe6XyW5fxBGB0gZuPc-5yLsukedR37StA1QTD3uBaRQWe_hdJPxN_7Fw0EPthn7aL6aruHzRJShsn4s5KHGZ_l02cG4UBlGLskWSlW_6tJRyFM4Qp0GTbfrIN88lH6Vam96odxyog3Yw--RJ8NgdVg4o3FE3EE45bLkHxRB4ATUuFk56h0UlCE5WWaBXgTHTEiL5Ogaw58tzqOfSV7JpKjESlzXeKnjrlJMG8Tj8HyC5BrL78u4AD7PjuL4YiPDI1Aa1TfWvAjb6_bfkX5sSvXQbOfRgamnGoFVyZBLIQ3GESkim73FEKldhUd-P8L9Fhnnttb5atqq13pnCdg2NFVeDu7p_WWY2XzPcX0MLby1MFzqbjJqMPQ_jNg0IIyCFvwgTONxC3LHBxurmBA-b3I5U6SvYoQozvP51eyF5_1GCQ3AUTdAgT9ZUDPb1jyYYtUHWyxFq1XdbBi87zKfMKOv_Gm9EOKEhqqO3uHJbTFaWqfJME-O7GQRxw1uvnTnqsfOWAnrNaW8ovbNMBrtCsvAT0Mk7vAutxUq-eLfzjnVzQ169yIxbHoXa7pHriU3np1HyKdETacJZ1P0a-bByjQONt_SyH2BjcrvUgLAB-wRLFt0hPztP8_6am7bJmZXt3gTb9qHI0)

[

![Apple最新「macOS 27」ベータ版を徹底レビュー!期待できる神アプデ5選](https://media.loom-app.com/loom/2026/07/03/ffc4bfab-d540-4699-a684-e91e791d8c98/original.png?w=180&h=120)

Apple最新「macOS 27」ベータ版を徹底レビュー!期待できる神アプデ5選

Apple最新「macOS 27」ベータ版を徹底レビュー!期待できる神アプデ5選

](https://api.cxense.com/public/widget/click/k8LB6Woqe2nNRngUYnbY3oiGNfrtYq3deKb8p7BuLikfjtI13me9yi0Hico0Reezuh8fyH08lCSDHVitonu5x-ek8vacIvQlpdxrxCGf8U7F4imxJ4CeQRQEMfJ2rkq3B5Rzhm569OWG7I9GUyuAmQ9XrQVQhtJCBjq799ZJEH_xuj_AezUmN3opwBRclpmAEoELjt5AlHN1u1dPyA6gRaKU3dlSbZmhnju4-tHNe3CL0smRWMxZTDZXTqvpSSbH7iwoXziwPyOhyuZr94Oo8U7fabCewwUsIaawCyK-sO9-4lNG64La_HJ2_1ZppQDMV3J7503hS0JnyCaFmszNDpalQgdIeRb0QrY4R2JBwO2xQMsYcsozNswrdSZcK7QsZyXzxYqccErNGhRn9IwHUni1-JFpTIJqm_G1e4Dj2WdkudwMBvbx2FaSSIi3YOnTEGwMr8FtekhDkesksdhmM7byqcx3VufnV9K6yCYtjH-RiiyT3JM4QEdMgv9hLJ3QlUhTb-MzGMjAsjOdGYmNUkqRkmh6w6t8rwn0zFR0U_QgN5biEAzmdqmPwAzhVz6B57lt-ETyNxQgCuDyxpmo65U9Esu32n-q0aj-lRfBKgyBJOHGQhmcYYWQzDvDHPz67S-MlhQtbXyaoSyFZTz1Xi51WD6csS0EpOZeqDWC5nhTR0M3_2_MTyrNZqq90qbOdyY789oKQnHPrmAWj4Ue3eWrgoanUGI-vhH79yT39vis4DYbPcI0)[

![買い切りストレージが、容量と心に余裕をもたらす](https://cdn-content-production.cxpublic.com/3fe82faffc904512e17eac8e134de096922ca62f569e884312073067eca62edc.jpg)

買い切りストレージが、容量と心に余裕をもたらす

買い切りストレージが、容量と心に余裕をもたらす

Sponsored by pCloud Ltd.

](https://s-adserver.cxad.cxense.com/adserver/click/KilNcbBIyW4Qq8FIkPHCuilWQq7uP0Ga9kQ-ipUfb5eiWiYd9kaoNge0J0fnPQY4h_ddIFbTB-i5tbzsTNivuW5PJJnqho3x4v_kWvMayqJp0OA2xVVDQUnWkXME3GsXRbcirnLGO_Xc2jHXUSdnNOPnlgs8j3FfmJXK0xcivarprzLjOtW3cwOxP9QRc-s.)[

![立ち話での決定事項も逃さない。この薄型AIボイスレコーダーがあれば](https://cdn-content-production.cxpublic.com/f768f257bcc24e48661d90489b54ecc7b526dac6eab726725c237827cf4d7d89.jpg)

立ち話での決定事項も逃さない。この薄型AIボイスレコーダーがあれば

立ち話での決定事項も逃さない。この薄型AIボイスレコーダーがあれば

Sponsored by Notta株式会社

](https://s-adserver.cxad.cxense.com/adserver/click/cJNroRgb-HtWu3jnaXX3m7lbdtBgL1uklMi0RDecj3I2QQoCCGjrBN-pOWjcjV1pnavf_cBvFxxBO9QjNgH9RHooYf9V8Es99RweL9MlZSX1OXxf1sqG62mxdkmEGxvZrhx6CbvlIBHxoAQ_I_-jDQvSJFavRLiUJPsmzk9xT-4-mxIpHET7thDkLAfHXVY.)[

![「JINS」発の最新コンタクトレンズは、欲張りな私たちの味方だった！](https://cdn-content-production.cxpublic.com/b35cad020cb7e8b471d79fa77be5619bfdd5509ec8b80435f167147e8d425593.jpg)

「JINS」発の最新コンタクトレンズは、欲張りな私たちの味方だった！

「JINS」発の最新コンタクトレンズは、欲張りな私たちの味方だった！

Sponsored by 株式会社ジンズ

](https://s-adserver.cxad.cxense.com/adserver/click/k8Qbxt5U4KN7AKcH2Y8xUX4oofZWStgbWZZ3faI60BN3FaPc1MNPCKA7eAJl4qSGnNaANbrt2XQeDx3Qg2kAeZvuI5r02AmMd_QLLDj0rKFrjXcU-gGKLuLPfDrFpeS8EttInXzD-xau3bgKD7EwWUMWwUl_7kI5FunZa_lS5Rp3JBX7gelFzDORKBH13a4.)[

![フラッグシップモデルで培われた技術を受け継いだ、JBLの新作](https://cdn-content-production.cxpublic.com/f3c117154bc16b1c14d383e7eafdae0d7627b91bb114cee8e29d949d14ce960e.jpg)

フラッグシップモデルで培われた技術を受け継いだ、JBLの新作

フラッグシップモデルで培われた技術を受け継いだ、JBLの新作

Sponsored by ハーマンインターナショナル株式会社

](https://s-adserver.cxad.cxense.com/adserver/click/2_1iVtzZYoeu9mED7nOttmB8itFHr_c_mcMMBupdCswF0BD55n3DD7BztJaNtX2Ng4vgasKWHi1rMwVWx-_urqXn4QAGwjQ027F116rFajLwWy7P1xG8FGhlN-0Cpfjg97O58Iny0Raibtpn3ars74GliLrFfq4oYHYUGyFToyH8pTSqcsXTt8rtGs8dv7g.)[

![数式エラーの犯人探しは終わり。Googleスプレッドシートの新Geminiが意外と親切だった](https://media.loom-app.com/loom/2026/06/29/72444c69-1e09-4e3e-8f31-442a5eccca98/original.png?w=180&h=120)

数式エラーの犯人探しは終わり。Googleスプレッドシートの新Geminiが意外と親切だった

数式エラーの犯人探しは終わり。Googleスプレッドシートの新Geminiが意外と親切だった

](https://api.cxense.com/public/widget/click/Q36Ev1niBr1gDR_MVG1QBOG43sbyjpKhtZ-Kc_uZ4IpKIVWrcEyyRsVk3mG4FtykkgehYE8rZ6OWOr0GzegDaXl78ih9kJrK5nQjhefbxJkwCULIyHm-ZpyMyQi7ijRY19RHoe5WYNg7IeJUJDziD7uGM9LKldrz4VJUo6yqxo0eCOFniwKJyClT_PGez2Hc3ljEDSoTdgHe2VS6XX3bsgZ35WNXPnaVRNjJULy9Q_bRmnYwHwRVQNPrMWnyaE6P8x0U0sHJihuj33lVZEB5Xgw_sCIuUZOX8w_2UJpvislp-td88PfQJuPogizakYBIfONLsRffTw8W8XzUQ7PIFSYaNZnqtjUiaJNUJ6TvAkW8XAdktCjKw-4ONUBZa7tKeRQnAGI2jcpOOMCpqs-ZlO7JjOp-nabLubAFYYu_U1kmFbxIgNPPVQ4GO3k_QyXhMO45aJ5_H2O9saCAz1xVy1Wk1-n1LaABKlRlYB41oGMgDd6LTG0-qVbujQ6crzREBKf7cre0bVu8hHUCu3dnwSSYegUXhMiSbz2gsLJ3KUI7cfx20JFu9E06TUTGkUHCN3HNePe34tR-zDNWfP5xL1E5yqmm2Iu8-F3hi5um_VpHNSW93d9eWt_6QONIjtkIFiU4ck5aUKjpjj9XqQsk8QP8HD8FQIiw1LKnIYRDJqiET3AgrbpGokurXZUCiOJQvIEyreNf8D9PkQrSHpuzDjVBAWEIXi5ufokbxpPEloCRrwjbz9ho8ggF91NxufUZlGGpfd44kEL0QIDhZ-s0)[

![Jackeryポタ電・ソーラーパネルが最大45％オフの公式セール開催中](https://cdn-content-production.cxpublic.com/d5dc0b4de20ddb5816bba34bceaca72fc0a8bb60001b7b325dcddc68d3bece29.jpg)

Jackeryポタ電・ソーラーパネルが最大45％オフの公式セール開催中

Jackeryポタ電・ソーラーパネルが最大45％オフの公式セール開催中

Sponsored by 株式会社Jackery Japan

](https://s-adserver.cxad.cxense.com/adserver/click/XQNZI-xYr9UpfVy3GINzRZEY1np-h4l6x9wTdKKIOJ8KzB1oVT7hlsUTAj1zFLWJz3HFrZAZPmiLQb-K_bIo81onx9FhfLfmCQkHicempyWmNgDrAf99qALXkbwOE6IzbYL1kL3gyWua9l-1XF8faXdGB5DgnuRaihw0WoxXDYhvise0_ngXtpMMC5l6mC4.)[

![iPhone用ブラウザ「Safari」と「Vivaldi」ベストはどちら?実用性を重視して下した決断](https://media.loom-app.com/loom/2026/06/30/16af752e-bfbd-4330-9215-303500bb4f0b/original.jpg?w=180&h=120)

iPhone用ブラウザ「Safari」と「Vivaldi」ベストはどちら?実用性を重視して下した決断

iPhone用ブラウザ「Safari」と「Vivaldi」ベストはどちら?実用性を重視して下した決断

](https://api.cxense.com/public/widget/click/MH2CWKko2zDgP6QkgIG41efnOQZS-J8w-ID_IwmEwrEh6nSEDheyI3UrspQaiDaPQ4r1W2USgjQqA02IZLGLSy8cx71rx1qNe7LhEBVpRd_jV2H-uZTQjCPDnbfywA0IESuUjDmPMJQPMBI3HHcrf1xRSXJAh6DBwgQYlGHl7prO_MgWcGs-wqxNk0MEAg6DEZhpv9OMu5b4JFKRvn9Uygu147WRGkD0xyVZt3g1jhUmjmcjay1vItjgwdmAqKkVV1fVhcwE8IFGLMISdOsBkfB5BE6J1rknG3uTqQKMS51qVCIbLmCSJHN--A94200J6cXCjm2O2AO1SgF7OlDCfVrYL8DaxJ_PimLR6TY_rhtyi4pyFPSFIcTzsvx3UZoSvRsqSZMGilpMypKePjIgU-EMfg5V8y_Nu1g1OuTFNRAHY6gOc2OtWjpJ6CyTLuJ4UexUbg8X3IwGSCAGEqDCd9or-u9PHP0H-zVNXZntj2RLdCVXOT8efBw7JqHsQq1PGev36PhdJRHWlFFkwDZhW4bUj9xYaKdo9H2L6m62SlLS0RPC895DoSNHHFRF8ryqCEf1cW5NLm_566O2-heIJWoq327m8IYO5RTwQubmGkYJ_Udanoz6Kj06CXwPDOIi0fdGEk7iTmI1OCGd6l-bFLaK39nwQUUg77FyboRcU1uYauCe3tNStZmjHgFjaTwF2j5Btwo1SBDwEj9Xy3ogG0-mA9b_5Z45YZhCjbZqylCSRfq-r1v8IzdLRFPStxaYJQd5W2kxXj-GLXVtQI-1-VuONtkp3blroSHfw9LLDA0)[

![NotebookLMの限界を突破する代替ツール「Open Notebook」が自由すぎた](https://media.loom-app.com/loom/2026/06/22/fae03123-27ef-4344-ab22-bdef6c3ad914/original.jpg?w=180&h=120)

NotebookLMの限界を突破する代替ツール「Open Notebook」が自由すぎた

NotebookLMの限界を突破する代替ツール「Open Notebook」が自由すぎた

](https://api.cxense.com/public/widget/click/RZEZEz57hIAtp827UhEoEBnMENqXxxje2JcyXxN_MGia76urpIETqZZpSWZz7VmhabZXucCkZmTb5hHlk2uLgCCcdNytxhyBnhFw-XIhG8D7gdLKOiCR0DYW6Y5JP2djQ5Xiozv9tQ8XI86iwoAva1WlZF2Xt74drfBqiKcrG2HrMnmLA1ZUDydMQm5E1H8PCpFEMpwud08XqwDxrjDa166OeStZimXEbzYAskN85XdYiWroI5pZftExVQgebuSXmSAn53xGgDyfA76UTIV7Jizg7ZarDKRJtsCouIlYhMnwRscVWr09g95V6dgGnWQiZHEMqXdqR0k-VS3jBIqltwqE07AEUMYL9ZgW-tXh8jjqS_HBoLJUvaiQYronbEk1bJLNV9U6szolTzNFlsyzzM1cn2wKt6lAZBRzNgv36g_WCQNJJGYPEy6KsWj6bhyXVxMdJ2JkSo3d1ZfxXAxbcda-I2UiIsmPHlObiEclXrkJrRrNIOxUJ6IS0BDhZhLrPruWWFS79yc5-9GoQEmDOAYpd19GjoECt7kGCoVaTXsHvB2ZcGiEPL6LhzDpPDxz3wPRRQksVfAVmNnsqIf2vI1QCLtFbGmUnhJctuwmkh1LfHyQ5-pzDdXordmYz-SIiEI-pHtQv-hCAf4sxXuz7x7wqWvRgMOXVfO_oHZ25E9GuqofefQocuJPREpNBvWn3TzyEYgzP2raR-ZNJ92RJe0lbJ3N2RrDvktcObk3ZHXHkMkGyzekbJDP0Xq7XQGXZup7-YsR_49PlAtAzBS11Q0)[

!["全部のせ"の最新ルンバが、この価格？しかもユーザーに寄り添う手厚いサービス付き](https://cdn-content-production.cxpublic.com/962fae4a13f254e1193c5c828c55d6868706f94402dada4921aab3d8806dd212.jpg)

"全部のせ"の最新ルンバが、この価格？しかもユーザーに寄り添う手厚いサービス付き

"全部のせ"の最新ルンバが、この価格？しかもユーザーに寄り添う手厚いサービス付き

Sponsored by アイロボットジャパン合同会社

](https://s-adserver.cxad.cxense.com/adserver/click/RPE0HgrZCs9GgQzFee1-x46d36-RBQcj7dofD7OnzPNxaE0jHquXPguKJp7S-6c5tySXjaxrMiWlSu3KS8BuvVIWxzN9us6_GcoE2AXkBKPZbdLteuLg_U_4XY6mDWggcG6WC6hnVxRg1do8OlcAoAMxlMkE7jvldzT7aAaZQ1IIHRVvnJaAE4klWoXsPxQ.)

ホットキーワード

[- ![新しいWindows PCを買ったら即実行！削除していいアプリ5つ](https://media.loom-app.com/loom/2026/07/01/4dd0c257-cd39-4c94-97fb-111c916d7ad3/original.png?w=135&h=135)
	新しいWindows PCを買ったら即実行！削除していいアプリ5つ](https://www.lifehacker.jp/article/2606useless-pre-installed-apps-windows-pc/)[- ![時間に追われない人は、ゴールを「一番遠く」に置く。クリエイティブディレクター・水野学の逆算時間術](https://media.loom-app.com/loom/2026/06/29/07b3ad34-16ba-4f47-81ea-a9f9af9f8db6/original.jpg?w=135&h=135)
	時間に追われない人は、ゴールを「一番遠く」に置く。クリエイティブディレクター・水野学の逆算時間術](https://www.lifehacker.jp/article/2606-manabu-mizuno-interview/)[- ![Claude Codeを「VS Code」で動かしたいこれだけの理由](https://media.loom-app.com/loom/2026/07/02/736264f7-198c-4d53-a19d-2bde5ca32563/original.jpg?w=135&h=135)
	Claude Codeを「VS Code」で動かしたいこれだけの理由](https://www.lifehacker.jp/article/2606this-underrated-claude-code-mode-makes-it-a-real-ide-rival/)[- ![夏の“スーツ暑すぎ問題”どうする？AOKIの「夏向けスーツ」が正解すぎて笑ってしまった](https://media.loom-app.com/loom/2026/06/24/1a148388-f63b-461d-98f9-4bb493452895/original.jpg?w=135&h=135)
	夏の“スーツ暑すぎ問題”どうする？AOKIの「夏向けスーツ」が正解すぎて笑ってしまった](https://www.lifehacker.jp/article/2606-aoki-yoryu-suit/)[- ![Amazonプライムデーで「買ってよかったもの」を振り返ってみた。編集部の愛用品16](https://media.loom-app.com/loom/2026/07/03/72e7056d-db2a-43aa-ad00-114d4155993b/original.png?w=135&h=135)
	Amazonプライムデーで「買ってよかったもの」を振り返ってみた。編集部の愛用品16](https://www.lifehacker.jp/article/2607-amazon-sale-editors-best-buy/)

[キーワードをもっと見る](https://www.lifehacker.jp/keyword/)

[![](https://content.cxpublic.com/creatives/d50fee6937dfc6ccb4abf34c668e2623ac33a929.png)](https://costory.jp/cf-published-sku-groups/1204742862?utm_source=MG_lifehacker&utm_medium=in&utm_campaign=gm-aimdesk-pro-cus)

ランキング

1. [
	1
	フォームローラーでほぐし続けて3カ月。体に起きた4つの変化と効果を感じた使い方
	](https://www.lifehacker.jp/article/2606-amazon-primeappreciation-sale-foam-roller-qxh/?cx_click=sp_ranking)
2. [
	2
	古いAndroidスマホ、捨てないで!自宅で再利用するアイデア6選
	](https://www.lifehacker.jp/article/26066-jobs-for-the-old-phone-in-your-drawer-that-beat-buying-a-gadget/?cx_click=sp_ranking)
3. [
	3
	運動会の我が子も豆粒サイズだった満月も。付属の望遠レンズでクッキリ撮れる手のひらカメラ
	Buy PR
	](https://www.lifehacker.jp/article/2606-costorypo-n300-review1-1196858319/?cx_click=sp_ranking)
4. [
	4
	さらばGmail。私がAndroid版「Thunderbird」に乗り換えて、もう二度と戻らないと決めた理由
	](https://www.lifehacker.jp/article/2606-use-thunderbird-for-email-android/?cx_click=sp_ranking)
5. [
	5
	Google Keepがもっと便利になる「10の機能」
	](https://www.lifehacker.jp/article/2606-10-hacks-every-google-keep-user-should-know/?cx_click=sp_ranking)

PR

1. [
	1
	![](https://m.media-amazon.com/images/I/61glUf9qzSL._AC_SL100_.jpg)
	COAST 単4形 充電池 4本セット
	¥3,080 -30%
	](https://www.amazon.co.jp/dp/B0DPFP4YH4?ots=1&tag=lifehacker-dir-22&linkCode=ogi&th=1&psc=1&ref=mgac2017)
2. [
	2
	![](https://m.media-amazon.com/images/I/71zyXQ496cL._AC_SL100_.jpg)
	PLOM エクスポッケ
	¥3,190
	](https://www.amazon.co.jp/dp/B0F3CPWH8S?ots=1&tag=lifehacker-dir-22&linkCode=ogi&th=1&psc=1&ref=mgac2017)
3. [
	3
	![](https://m.media-amazon.com/images/I/61-I+v5+gsL._AC_SL100_.jpg)
	山崎実業 テーブル下 レジ袋ハンガー
	¥1,980
	](https://www.amazon.co.jp/dp/B0CG5DH9CZ?ots=1&tag=lifehacker-dir-22&linkCode=ogi&th=1&psc=1&ref=mgac2017)
4. [
	4
	![](https://m.media-amazon.com/images/I/61CE2gnloxL._AC_SL100_.jpg)
	LG モバイルモニター 17インチ
	¥48,900-18%
	](https://www.amazon.co.jp/dp/B0F2F4SKMD?ots=1&tag=lifehacker-dir-22&linkCode=ogi&th=1&psc=1&ref=mgac2017)
5. [
	5
	![](https://m.media-amazon.com/images/I/31LhD3HUpSL._AC_SL100_.jpg)
	ダイゴー ノート isshoni.
	¥613
	](https://www.amazon.co.jp/dp/B09BB6S132?ots=1&tag=lifehacker-dir-22&linkCode=ogi&th=1&psc=1&ref=mgac2017)

新着記事![「引くだけ」で光が手元へ。夜の読書・仕事がはかどるニトリのライト](https://media.loom-app.com/loom/2026/07/03/574c45c6-de90-4780-b161-834e3087a77a/original.png?w=180&h=120)

「引くだけ」で光が手元へ。夜の読書・仕事がはかどるニトリのライト

[

「引くだけ」で光が手元へ。夜の読書・仕事がはかどるニトリのライト

2026.07.04

](https://www.lifehacker.jp/article/2607-lht-nitori-pendant-bar-light/)

[

![【毎日書評】「今の職場」でもっと幸せに働くための小さな習慣](https://media.loom-app.com/loom/2026/07/03/faef5732-f22a-4609-a64d-84eef9055b01/original.jpg?w=180&h=120)

【毎日書評】「今の職場」でもっと幸せに働くための小さな習慣

【毎日書評】「今の職場」でもっと幸せに働くための小さな習慣

2026.07.04

](https://www.lifehacker.jp/article/2607-book_to_read_weekend_160/)[

![傾けるだけで本格コーヒーも緑茶も。デスクに「小さなカフェ」を生み出すグラス](https://media.loom-app.com/loom/2026/06/29/1df12ceb-e078-4e2e-99e9-43499a80956f/original.png?w=180&h=120)

傾けるだけで本格コーヒーも緑茶も。デスクに「小さなカフェ」を生み出すグラス

傾けるだけで本格コーヒーも緑茶も。デスクに「小さなカフェ」を生み出すグラス

2026.07.04 Buy PR

](https://www.lifehacker.jp/article/2607-machi-ya-airomini-lh-editorialreview/)[

![面倒なアイロンがけのハードルを下げる。ティファールの衣類スチーマーが15％オフ](https://media.loom-app.com/loom/2026/07/04/0d7171c6-2dea-4c4a-ae13-b2c5eb8d5be5/original.jpg?w=180&h=120)

面倒なアイロンがけのハードルを下げる。ティファールの衣類スチーマーが15％オフ

面倒なアイロンがけのハードルを下げる。ティファールの衣類スチーマーが15％オフ

2026.07.04 Buy PR

](https://www.lifehacker.jp/article/amazon-timesale-2026-0704-2/)[

![「なんだか気持ちが疲れた…」をリセットして、自分を取り戻す4つのアイデア](https://media.loom-app.com/loom/2026/07/03/3d079594-09f3-4c73-afe2-1cf2d1ce7b2f/original.jpg?w=180&h=120)

「なんだか気持ちが疲れた…」をリセットして、自分を取り戻す4つのアイデア

「なんだか気持ちが疲れた…」をリセットして、自分を取り戻す4つのアイデア

2026.07.04

](https://www.lifehacker.jp/article/2607-matome-mental-reset/)[

![「ストレス」と「不安」の決定的な違い](https://media.loom-app.com/loom/2026/07/03/ea5c5cda-66ef-4a2f-9f84-5de8ae10dcba/original.jpg?w=180&h=120)

「ストレス」と「不安」の決定的な違い

「ストレス」と「不安」の決定的な違い

2026.07.04

](https://www.lifehacker.jp/article/2606what-anxiety-actually-does-to-you-and-what-you-can-do/)