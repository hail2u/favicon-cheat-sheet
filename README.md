ファビコン・カンニング・ペーパー
================================

ファビコンのサイズや形式についての読むと頭が痛くなる偏執的なカンニング・ペーパーです。以下のURLを参考にしました:

  * [rel="shortcut icon" considered harmful · Mathias Bynens][1] <-- special thanks [@mathiasbynens][2]
  * [Everything you always wanted to know about touch icons · Mathias Bynens][3] <-- special thanks [@mathiasbynens][2]
  * [Jonathan T. Neal | Understand the Favicon][4]
  * [Favicon - Wikipedia, the free encyclopedia][5]
  * [Making a Good Favicon - Snook.ca][6]
  * [Create the perfect favicon | Feature | .net magazine][7]
  * [Getting Android to Recognize Apple Touch Icons - Ravelrumba by Rob Flaherty][8]
  * [Customizing the Site Icon (Windows)][9]


HTMLでのマークアップ
--------------------

### 基本

メインになるファビコンについては各ブラウザーでの互換性を考慮して[HTMLでは特に指定しないのが望ましい][2]です。単に`favicon.ico`という名前でドメインのルートに配置するだけで構いません。

こうするとIE6も含めすべてのデスクトップ向けブラウザー(SeaMonkey以外)のあらゆるバージョンでうまくいきます。


### 推奨

以下のコードは指定しておくと良いかもしれません:

  1. iOS 2.0以降とAndroid 2.1以降向けのタッチ・アイコン:

     ```html
     <link rel="apple-touch-icon-precomposed" href="path/to/favicon-152.png">
     ```

  2. IE10のMetroタイル・アイコン(Metroにおけるタッチ・アイコンのようなもの):

     ```html
     <meta name="msapplication-TileColor" content="#FFFFFF">
     <meta name="msapplication-TileImage" content="/path/to/favicon-144.png">
     ```

     あなたの好きな色で`#FFFFFF`は置き換えましょう。


### 任意(偏執的な方だけどうぞ)

ありとあらゆるものをカバーしたいのならば以下のようにすることになります:

  1. [Appleの各デバイス向けタッチ・アイコン][3]の全サイズ:

     ```html
     <!-- For iPad with high-resolution Retina display running iOS ≥ 7: -->
     <link rel="apple-touch-icon-precomposed" sizes="152x152" href="/path/to/favicon-152.png">

     <!-- For iPad with high-resolution Retina display running iOS ≤ 6: -->
     <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/path/to/favicon-144.png">

     <!-- For iPhone with high-resolution Retina display running iOS ≥ 7: -->
     <link rel="apple-touch-icon-precomposed" sizes="120x120" href="/path/to/favicon-120.png">

     <!-- For iPhone with high-resolution Retina display running iOS ≤ 6: -->
     <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/path/to/favicon-114.png">

     <!-- For first- and second-generation iPad: -->
     <link rel="apple-touch-icon-precomposed" sizes="72x72" href="/path/to/favicon-72.png">

     <!-- For non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
     <link rel="apple-touch-icon-precomposed" href="/path/to/favicon-57.png">
     ```

  2. 上記でカバーできないサイズ:

     ```html
     <link rel="icon" href="/path/to/favicon-32.png" sizes="32x32">
     ```

     *訳注:* 必要なサイズで作成し、`sizes`属性を使ってそのサイズを教えてやるということです。


画像の作成
----------

最低でも以下のものは作りましょう:

|サイズ       |ファイル名 |目的                                                              |
|-------------|-----------|------------------------------------------------------------------|
|16x16 & 32x32|favicon.ico|IEのデフォルトで、残念ながらChromeとSafariはpngよりicoを優先します|

`favicon.ico`について詳しくは後述しますが、ひとつのファイルで複数のサイズをまかなえます。

iOSやAndroidへ簡単に対応したい場合は以下のサイズで作成します:

|サイズ |ファイル名     |目的                                                |
|-------|---------------|----------------------------------------------------|
|152x152|favicon-152.png|iOSやAndroidで使われ、デバイス側で適切に縮小されます|

しかしながら複雑なアイコンの場合、デバイスによる縮小がきれいに行われないことがあることは頭に入れておいた方が良いでしょう。きれいに縮小されるように細かい修正を行う必要があるかもしれません。

偏執狂のあなたは以下のサイズも作りましょう:

|サイズ |ファイル名     |目的                                                                     |
|-------|---------------|-------------------------------------------------------------------------|
|32x32  |favicon-32.png |特定の古いかといって古過ぎもしないChromeがicoを適切に扱わないバグへの対応|
|57x57  |favicon-57.png |非RetinaのiOSのホーム・スクリーン(iPod TouchやiPhoneの第一世代から3Gまで)|
|72x72  |favicon-72.png |iPadのホーム・スクリーン・アイコン                                       |
|96x96  |favicon-96.png |GoogleTVのアイコン                                                       |
|120x120|favicon-120.png|Retina iPhoneのタッチ・アイコン(iOS 7で114x114から変更)                  |
|128x128|favicon-128.png|Chrome ウェブストアのアイコン                                            |
|144x144|favicon-144.png|IE10のピン留めされたサイト向けタイル・アイコン                           |
|152x152|favicon-152.png|Retina iPadのタッチ・アイコン(iOS 7で144x144から変更)                    |
|195x195|favicon-195.png|Operaのスピード・ダイヤル・アイコン                                      |


ICOファイル
-----------

`ico`ファイルはサイズの違う`.bmp`や`.png`のアイコンを複数まとめることができるフォーマットです。`favicon.ico`では以下のサイズを作れば十分でしょう:

|サイズ|目的                                                                                                                   |
|------|-----------------------------------------------------------------------------------------------------------------------|
|16x16 |IE9のアドレス・バーやピン留めされたサイト、ジャンプ・リスト、お気に入りツールバー、新しいタブのサムネイルのオーバーレイ|
|32x32 |IEの新しいタブやWidows 7以降のタスクバー・ボタン、Safariのリーディング・リストのサイドバー                             |
|48x48 |Windowsサイト・アイコン                                                                                                |

偏執狂のあなたは、1-3KBのファイルサイズの増加を気にしないのなら、以下のサイズも`favicon.ico`に含めると良いでしょう:

|サイズ|目的                                                                                 |
|------|-------------------------------------------------------------------------------------|
|24x24 |IE9のピン留めされたサイトでブラウザー・ウィンドウに表示されるアイコン                |
|64x64 |高解像度デバイスでのWindowsサイト・アイコンやSafariのリーディング・リストのサイドバー|

まずきっちりと`.png`を作り、それを元にして`.ico`を作成しましょう。

*TODO:* IE9以降で`.png`を`.ico`に含められることについての確認([Issue #9][10])


お役立ちツール
--------------

オススメなのは以下の2つです:

  1. [OptiPNG][11]: `.ico`にまとめる前に`.png`を最適化
  2. [ImageMagick][12]: [複数の`.png`画像をまとめて、ひとつの`.ico`ファイルに変換][13]

試したわけではありませんが、以下のツールも役に立つでしょう:

  * Ubuntu/Debianのパッケージである`icoutil`には`.png`から`.ico`を作成するツールが含まれています
  * MSDNでは[X-Icon Editor][14]の利用を推奨しています
  * リサイズには[Faviconer][15]が良いでしょう
  * [icon][16]もリサイズに向いたツールです
  * JavaScriptを利用して動的にファビコンを変更する[favicon-setter][17]というツールもあります
  * ファイル・アップロードのプログレス表示などをファビコンで行える[piecon][18]というツールも面白いでしょう
  * [Web Icon][19]は12種類のサイズのファビコンを一気に作成してくれるシェルスクリプトです
  * [Icon Slate app][20] (OS X)
  * [png2ico wrapper for ImageMagick][21]


ファビコンの強制的な再読み込み
------------------------------

通常は必要ありません。開発中にうまくファビコンが再読み込みされずイライラする時だけ試してみましょう:

  * ブラウザーのキャッシュをクリアする(Ctrl+F5またはCtrl+Shift+R)
  * IEの場合はブラウザーを再起動する
  * それでもダメな場合は新しいタブを開くか、[複雑な手順][22]をこなす
  * 一時的にマークアップを変更してクエリ文字列を追加する。必ず後で削除しましょう:

    ```html
    <link rel="shortcut icon" href="http://www.yoursite.com/favicon.ico?v=2">
    <link rel="icon" sizes="16x16 32x32" href="/favicon.ico?v=2">
    ```

大きな変更を加えたバージョンの公開時には全ての訪問者のファビコンを強制的に再読み込みさせたいこともあるでしょう:

  * 以下のようなマークアップ(`sizes`属性の変更を忘れずに)を加えて、バージョン番号をファイル名に入れるようにしましょう:

    ```html
    <link rel="shortcut icon" href="/favicon-v2.ico">
    <link rel="icon" sizes="16x16 32x32" href="/favicon-v2.ico">
    ```

    *TODO:* このマークアップがうまくいかないケースのさらなる調査([Issue #3][23]).


よくある質問
------------

### `favicon.ico`と`favicon.png`の両方がルートにあるとどうなりますか？

`favicon.ico`のみを設置し、`favicon.png`は置かない方が良いと思います。その理由は:

  * `.ico`形式は複数の`.bmp`や`.png`のためのコンテナー・フォーマットです。`favicon.png`を1つ定義し、`favicon.ico`の代わりに`favicon.png`を使うようにすると、ブラウザーのリサイズ機能にすべて任せることになり、ファビコンが違う解像度でどのように表示されるかコントロールできなくなります。例えば64x64のアイコンでは文字を表示したいが、16x16のアイコンでは読めなくなるであろうことから文字は表示したくないというようなケースにも対応できます。
  * HTML5仕様には`favicon.ico`については出てきますが、`favicon.png`については出てきません。[現在のHTML仕様によると][24]:
    > 'In the absence of a link with the icon keyword, for Documents obtained over HTTP or HTTPS, user agents may instead attempt to fetch and use an icon with the absolute URL obtained by resolving the URL "/favicon.ico" against the document's address, as if the page had declared that icon using the icon keyword.'

このことについて詳しくは[似たような質問に対してのStackOverflowでの答え][25]を参照すると良いでしょう(注: アルファ・チャンネルという点での優位性を説明した答えは間違っているので、2つ目の答えを読んでください)。


### ファビコンはルートに置くべきというのは本当ですか？

いいえ、それはブラウザーやデバイスごとにファビコンのパスを指定した`<link>`タグを明示的に書かなかった場合に限った話です。Wikipediaの[Favicon.ico記事][5]も参照してください。

もし`favicon.ico`をルートに置いていないなら、置くかHTTPステータス・コードで`204`を返すようにしましょう。多くのツールやサービス(ブックマークやフィード・リーダー、検索エンジンのクローラーなど)がルートに`favicon.ico`があるとしてリクエストしてきますが、もし無いとHTTPステータス・コードとして`404`を受け取ることになります。最悪の場合、ファビコンよりも何倍もサイズの大きいカスタム・エラー・ページを返す羽目になるかもしれません。


### PNGの場合は`favicon.png`という名前にする必要があるというのは本当ですか？

いいえ、私が偏執的に調べたところによるとそういった事実はまったくありません。


### ICOの場合は`favicon.ico`という名前にする必要があるというのは本当ですか？

もし明示的に`<link>`タグを書かないのならばその通りです。明示的に書くのが一番確実なので、`favicon.ico`という名前にして明示的に`<link>`タグを書くようにしています。


### なぜ"apple-touch-icon"を頭に付けないのですか？

`<link>`タグを書かない場合、iOSは勝手に`apple-touch-icon`か`apple-touch-icon-precomposed`が頭についたファイルを探します。HTML5 Boilerplateなど多くがこの挙動に依存しています。しかし:

  * 明示的に`<link>`タグを書く方がよりわかりやすく、Appleがサポートしている形です
  * ファイル名を`apple-touch-icon`のように決め打ちしないことにより、同じサイズのアイコンの再利用性が高まります(例えば`favicon-144.png`をWindowsのピン留めされたサイトに再利用する場合など)


### なぜiOS向けに編集済みアイコン(precomposed icon)を指定するのですか？

  * iOSは編集済みでないアイコンに角丸と影・反射の特殊効果を付け加えます。一見それで良さそうですが、実際にはそううまくはいかず、特にデザイナーには納得の行くような結果にはなってくれません。
  * 編集済みでないアイコンにAndroid 2.1は対応していません。


### なぜ絶対パスを使うのですか？

Firefoxの古いバージョンで絶対パスである必要があります。また絶対パスならば全てのブラウザーでサポートされているので、最も無難な選択でしょう。


### なぜクエリ文字列を追加して全ての訪問者に強制的に再読み込みさせないのですか？

いくつかのプロクシーやロード・バランサーでクエリ文字列の解釈に失敗するケースが確認されています。


是非、寄稿を！
--------------

もし他の文書の引用や根拠の提示のために追加や変更を加えたい場合はプル・リクエストを送ってください。この文書を充実させてくれることを楽しみにしています！


--------


訳注
----

  * OptiPNGは適切なオプションを指定しないと256色かつ透過色に減色するので、それをそのまま`.ico`に含めると透過色が失われます
  * Markdownフォーマットの翻訳が[GitHubのリポジトリ][26]にあります
  * この文書も元のドキュメントのライセンスと同じく[MITライセンス][27]で提供されます
  * この日本語訳について何かある場合は[フィードバック・フォーム][28]よりお願いします


[1]:  http://mathiasbynens.be/notes/rel-shortcut-icon
[2]:  https://github.com/mathiasbynens
[3]:  http://mathiasbynens.be/notes/touch-icons
[4]:  http://www.jonathantneal.com/blog/understand-the-favicon/
[5]:  https://en.wikipedia.org/wiki/Favicon.ico
[6]:  http://snook.ca/archives/design/making_a_good_favicon
[7]:  http://www.netmagazine.com/features/create-perfect-favicon
[8]:  http://www.ravelrumba.com/blog/android-apple-touch-icon/
[9]:  http://msdn.microsoft.com/en-us/library/ie/gg491740(v=vs.85).aspx
[10]: https://github.com/audreyr/favicon-cheat-sheet/issues/9
[11]: http://optipng.sourceforge.net/
[12]: http://www.imagemagick.org/Usage/thumbnails/#favicon
[13]: http://blog.morzproject.com/convert-multiple-png-images-into-a-single-icon-file/
[14]: http://www.xiconeditor.com
[15]: http://faviconer.com
[16]: https://github.com/abrkn/icon
[17]: https://github.com/HenrikJoreteg/favicon-setter
[18]: https://github.com/component/piecon
[19]: https://github.com/emarref/webicon
[20]: https://itunes.apple.com/us/app/icon-slate/id439697913
[21]: https://github.com/bebraw/png2ico
[22]: http://stackoverflow.com/questions/2208933/how-do-i-force-a-favicon-refresh/5239747#5239747
[23]: https://github.com/audreyr/favicon-cheat-sheet/issues/3
[24]: http://www.w3.org/html/wg/drafts/html/CR/links.html#rel-icon
[25]: http://stackoverflow.com/questions/1344122/favicon-png-vs-favicon-ico-why-should-i-use-pngs-instead-of-icos/1344379#1344379
[26]: https://github.com/hail2u/favicon-cheat-sheet
[27]: https://github.com/hail2u/favicon-cheat-sheet/blob/master/LICENSE
[28]: http://hail2u.wufoo.com/forms/feedback/
