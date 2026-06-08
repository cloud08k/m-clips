---
title: "Obsidian BasesとWeb ClipperでWebリンクのサムネイル付きカードビューが簡単に作れます｜teatown"
source: "https://note.com/teatown/n/n34eabc603a5d"
author:
  - "[[teatown]]"
published: 2025-08-31
created: 2026-06-06
description: "はじめに  みなさんもWebの気になった記事をアーカイブしたリンク集を作っていると思います。私は今までNotionでやってました。というのも、単にリンクがノートとして保存されるだけではなく、カードビューとして見たいからです。EvernoteやUpNoteではカードビューはできず、Obsidianでは色々複雑なプログラムを書けばできますが、ちょっと面倒だったので、普通に使えるNotionでやってました。  最近ObsidianのコアプラグインとしてBasesというデータベース機能がリリースされました。  Introduction to Bases - Obsidian Help"
tags:
  - "clippings"
image: "https://assets.st-note.com/production/uploads/images/212170002/rectangle_large_type_2_10f8b10089300dabb15cfbbc33b349ed.png?width=1280"
---
## はじめに

みなさんもWebの気になった記事をアーカイブしたリンク集を作っていると思います。私は今までNotionでやってました。というのも、単にリンクがノートとして保存されるだけではなく、カードビューとして見たいからです。EvernoteやUpNoteではカードビューはできず、Obsidianでは色々複雑なプログラムを書けばできますが、ちょっと面倒だったので、普通に使えるNotionでやってました。

最近ObsidianのコアプラグインとしてBasesというデータベース機能がリリースされました。

このBasesとObsidian Web Clipperというブラウザの拡張機能を使うと、とても簡単にWeb Clippingのカードビューができることが分かったので、さっそくやってみました。以下の記事を参考にさせてもらいました。著者のみなさま、ありがとうございます。

<iframe height="210" data-src="https://note.com/embed/notes/n20d31913131b" src="https://note.com/embed/notes/n20d31913131b"></iframe><iframe height="210" data-src="https://note.com/embed/notes/n0a5a5a82e47a" src="https://note.com/embed/notes/n0a5a5a82e47a"></iframe>

## 前提となるもの

前提として、ObsidianにBasesというコアプラグインがインストールされていて、ブラウザにObsidian Web Clipperという拡張機能がインストールされ＆有効になっていることを確認してください。ここでは、それぞれのインストールの手順などは説明しませんが、上の二つの記事などを参考にすると良いと思います。

Web ClipperでWeb記事をクリップすると、標準ではObsidianのClippingsというフォルダーにそのWeb記事のmdファイルが作られます。幾つか記事がクリップできていることを確認しておいてください。

## Baseファイルの作成

まずは、baseファイルを作ります。Obsidianのツールバーの中に Create new base というボタンがあるので、それを押します。すると新規のbaseファイルができます。名前は好きなものに変えてください。私は、WebClipCardとしました。Obsidianのファイルとしては、WebClipCard.baseというのができたことになります。

### Filterの作成

最初はTableビューになっていて、自分のVault内の全てのファイルが出てきていると思いますので、Clippingsのフォルダーの下のファイルだけにします。Filterボタンを押して、以下のように設定すると、Clippingsフォルダーのファイルだけが出てくるようになります。(このままだと、mdファイル以外の画像ファイルなどもあると、全部表示されるので、mdファイルだけにすることもできますので、色々やってみると良いでしょう。)

![画像](https://assets.st-note.com/img/1756647026-QzlYHoRG3mU7pNIqDkdCrsK4.png)

### Card Viewの作成

次はカードビューを作ります。以下の様にTableボタンをクリックし、+Add View ボタンを押してください。

![画像](https://assets.st-note.com/img/1756647254-QEHVrzTDb8kCYR724eWijqNA.png)

以下のようなConfigure View画面になるので、名前は適当に決めて(私はDefaultにしました)、LayoutをCardsにしてください。これで、Defaultという名前のCard Viewができました。

![画像](https://assets.st-note.com/img/1756647154-xq4mgobldU1sa0tAp8CZT27f.png)

まだサムネールはありませんが、Clippingsのフォルダーの下にあるmdファイルがそれぞれカードとして並んだ状態で表示されていると思います。

### デフォルトのViewの設定

ところで、この状態だと次にこのbaseファイルを開くとTable Viewで表示されてしまうと思います。私は基本的にCard Viewしか使わないつもりなので、このbaseファイルを開くとCard Viewで表示したいです。Obsidian BasesでのデフォルトのViewはViewのリストの一番上のものなので、Card ViewをドラッグしてViewリストの一番上に持ってくると、次回オープンした際に、Card Viewで開いてくれます。

ここでBasesを一旦離れて、Web Clipperの設定に移ります。

## Web Clipperの設定

サムネイル付きのCard Viewを作りたいので、Web Clipperで作成されたObsidianのmdファイルのpropertyとしてimageというのを付けるようにします。

### image propertyの追加

ブラウザの拡張機能のObsidian Web Clipperの設定を開きます。

その設定画面の左側のメニューの一番下にデフォルトというのがあるので、それをクリックします。すると右側にプロパティの一覧というのが出てきます。その下の +プロパティを追加 をクリックしてimageというpropertyを追加します。

次に、左側のメニューのプロパティをクリックします。すると、imageというpropertyが追加されていると思います。ただ、imageの右側のフィールドが空欄なので、{{image}} というのを入れてください。以下のようになるはずです。

![画像](https://assets.st-note.com/img/1756647341-h1KiPxIm8QTBXfnUgs72YA4r.png?width=1200)

以上でWeb Clipper側の設定は終了です。念のため、ブラウザーを再起動すると良いでしょう。

### 動作確認

テスト用に幾つかのページをWeb Clipperでクリップしてみてください。ObsidianのClippingsフォルダーにその新しいページのmdファイルができているのを確認してください。さらに、そのmdファイルの中を見てプロパティとしてimageというのがあるかを確認してください。もし、できていない場合は、このセクションの設定を再度やってみてください。

## Card Viewにサムネールを表示させる

ここで、再度Bases側の設定に戻ります。いよいよCard Viewにサムネールを表示させる設定をします。さきほどのbaseファイルを開いてください。

### thumbnailというプロパティの追加

上の方にあるBasesのコマンドバーのPropertiesをクリックします。その下にある Add fomulaをクリックします。そこに以下のように、thumbnailというpropertyを定義します。これは、mdのimageというプロパティの値となっているURLからイメージデータを取得してthumbnailというプロパティにセットしています。

![画像](https://assets.st-note.com/img/1756647439-ZGBMOUgoiHh92amI7Y6JdSDj.png)

### Card Viewのimage propertyの設定

次に最後のステップです。このthumbnailをCardに表示させる設定をします。Card Viewの設定であるConfigure viewを開いてください。下の方に Image property というフィールドがある(空欄になっているはず)ので、ここにthumbnailをセットします。

![画像](https://assets.st-note.com/img/1756647702-nZXR0LUr4pJd2lbOqK9EcyCo.png)

これでめでたく以下のような感じのWebページのサムネール付きのCard Viewが表示できたと思います。以下の例では、Card内にプロパティのsourceも表示させています。中には、以下のObsidian Helpのページの様に、imageプロパティに値がセットされないページもありますね。

![画像](https://assets.st-note.com/img/1756647750-6MIsPmkBDTpWj27yC9RNlVSY.png?width=1200)

## おわりに

このBasesとWeb Clipperを使ったWebページのクリップのCard Viewは、結構簡単に作れますし、柔軟性も高いのでとても良いと思います。

そもそもこのObsidian Basesがよくできているので、他の用途でも色々使ってみると楽しそうです。