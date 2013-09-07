ファビコン・カンニング・ペーパー
================================

ファビコンのサイズや形式についての読むと頭が痛くなる偏執的なカンニング・ペーパーです。以下のURLを参考にしました:

  * http://mathiasbynens.be/notes/rel-shortcut-icon <-- special thanks [@mathiasbynens][1]
  * http://mathiasbynens.be/notes/touch-icons <-- special thanks [@mathiasbynens][1]
  * http://www.jonathantneal.com/blog/understand-the-favicon/
  * https://en.wikipedia.org/wiki/Favicon.ico
  * http://snook.ca/archives/design/making\_a\_good\_favicon
  * http://www.netmagazine.com/features/create-perfect-favicon
  * http://www.ravelrumba.com/blog/android-apple-touch-icon/
  * http://msdn.microsoft.com/en-us/library/ie/gg491740(v=vs.85).aspx


HTMLでのマークアップ
--------------------

### 基本

メインになるファビコンについては各ブラウザーでの互換性を考慮して[HTMLでは特に指定しないのが望ましい][2]です。単に`favicon.ico`という名前でドメインのルートに配置するだけで構いません。

こうするとIE6も含め全てのデスクトップ向けブラウザーのすべてのバージョン(SeaMonkey以外)でうまくいきます。


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

  1. [Appleのデバイス向けタッチ・アイコン][4]の全サイズ:

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

     *訳注:* 非標準の`sizes`属性を使ってサイズを教えてやるということです。


画像の作成
----------

最低でも以下のものは作りましょう:

|サイズ       |ファイル名 |目的                                                                                     |
|-------------|-----------|-----------------------------------------------------------------------------------------|
|16x16 & 32x32|favicon.ico|IEがデフォルトで必要とします。残念ながらChromeとSafariはpngよりicoを優先してしまいます。|

`favicon.ico`について詳しくは後述しますが、ひとつのファイルで複数のサイズをまかなえます。

iOSやAndroidへ簡単に対応したい場合は以下のサイズで作成します:

|サイズ |ファイル名     |目的                                                  |
|-------|---------------|------------------------------------------------------|
|152x152|favicon-152.png|iOSやAndroidで使われ、デバイス側で適切に縮小されます。|

しかしながら複雑なアイコンの場合、デバイス側の縮小がきれいに行われないことがあることは頭に入れておいた方が良いでしょう。きれいに縮小されるように細かい修正を行う必要があるかもしれません。

偏執狂のあなたは以下のサイズも作りましょう:

|サイズ |ファイル名     |目的                                                                         |
|-------|---------------|-----------------------------------------------------------------------------|
|32x32  |favicon-32.png |特定の古いかといって古過ぎもしないChromeがicoを適切に扱わないバグへの対応    |
|57x57  |favicon-57.png |非RetinaであるiOSのホーム・スクリーン(iPod TouchやiPhoneの第一世代から3Gまで)|
|72x72  |favicon-72.png |iPadのホーム・スクリーン                                                     |
|96x96  |favicon-96.png |GoogleTVのアイコン                                                           |
|120x120|favicon-120.png|Retina iPhoneのタッチ・アイコン(iOS 7で114x114から変更)                      |
|128x128|favicon-128.png|Chrome ウェブストアのアイコン                                                |
|144x144|favicon-144.png|IE10のピン留めされたサイト向けタイル・アイコン                               |
|152x152|favicon-152.png|Retina iPadのタッチ・アイコン (iOS 7で144x144から変更)                       |
|195x195|favicon-195.png|Operaのスピード・ダイヤル・アイコン                                          |


ICOファイル
-----------

`ico`ファイルはサイズの違う`.bmp`や`.png`のアイコンを複数まとめることができるフォーマットです。`favicon.ico`では以下のサイズを最低限作成しておけばよいでしょう:

|サイズ|目的                                                                                    |
|------|----------------------------------------------------------------------------------------|
|16x16 |IE9のアドレス・バーやピン留めされたサイト、ジャンプ・リスト、ツールバー、オーバーレイ   |
|32x32 |IEの新しいタブやWidows 7以降のタスクバー・ボタン、Safariのリーディングリスト・サイドバー|
|48x48 |Windowsサイト・アイコン                                                                 |

偏執狂のあなたは1–3KBのファイルサイズの増加を気にしないのなら、以下のサイズも`favicon.ico`に含めると良いでしょう:

|サイズ|目的                                                                               |
|------|-----------------------------------------------------------------------------------|
|24x24 |IE9のピン留めされたサイトでブラウザーウィンドウに表示されるアイコン                |
|64x64 |高解像度デバイスでのWindowsサイト・アイコンやSafariのリーディングリスト・サイドバー|

まずきっちりと`.png`を作り、それを元にして`.ico`を作成しましょう。

*TODO:* IE9以降で`.png`を`.ico`に含められることについての確認 ([Issue #9][5])

お役立ちツール
--------------

I recommend:

  1. [OptiPNG][6], to optimize .png files before putting them into an .icon
  2. [ImageMagick][7], [to create an .ico from .png files][8]

Others that I haven't tried:

  * Ubuntu/Debian package `icoutil` has an icotool program which creates .ico from .png files.
  * MSDN recommends this [web-based .ico creator][9]
  * Resize favicons: [Faviconer][10]
  * More resizing: [icon][11]
  * Dynamically setting favicons: [favicon-setter][12]
  * Fancy favicon tricks: [piecon][13]
  * [Web Icon][14] - a simple shell script that generates favicon and touch icons
  * [Icon Slate app][15] (OS X)
  * [png2ico wrapper for ImageMagick][16]


ファビコンの強制的な再読み込み
------------------------------

Not normally needed. This is only for those frustrating times when you can't
get your favicon to refresh, during development:

  * Clear the browser cache (Ctrl+F5 or Ctrl+Shift+R).
  * Also close and reopen browser if IE.
  * If still stuck, try opening new tab. Or follow [these complicated steps][17].
  * Temporarily add explicit HTML markup and append a query string. Remove
    this when you're done:

    ```html
    <link rel="shortcut icon" href="http://www.yoursite.com/favicon.ico?v=2">
    <link rel="icon" sizes="16x16 32x32" href="/favicon.ico?v=2">
    ```

For large versioned deployments, if all site visitors need their favicon force-refreshed in an extreme situation:

  * Add explicit HTML markup (customize the sizes part) and put your version
    number in the filename.

    ```html
    <link rel="shortcut icon" href="/favicon-v2.ico">
    <link rel="icon" sizes="16x16 32x32" href="/favicon-v2.ico">
    ```

    *TODO:* find edge cases where this markup doesn't work ([Issue #3][18]).

よくある質問
------------

### What about having both a default root favicon.ico and favicon.png?

I think it's actually better to provide only `favicon.ico` and not `favicon.png`, because:

  * An `.ico` is a container for multiple `.bmp` or `.png` files. If you specify 1 default `favicon.png`, and if that `favicon.png` overrides the `favicon.ico`, you are giving up control over how the favicon looks at different resolutions and allowing the browser to do all resizing. For example, you might want the 64x64 version to contain text and the 16x16 version to not display the text at all, since at 16x16 it would be unreadable anyway.
  * There is no `favicon.png` in the HTML5 specification, just `/favicon.ico`. From [current HTML specification][3]:
    > 'In the absence of a link with the icon keyword, for Documents obtained over HTTP or HTTPS, user agents may instead attempt to fetch and use an icon with the absolute URL obtained by resolving the URL "/favicon.ico" against the document's address, as if the page had declared that icon using the icon keyword.'

More about this in [an answer on StackOverflow][19] (Note: the text in the chosen answer about alpha transparency is incorrect. See the 2nd answer.)


### Is it true that favicons should be in the site root?

No, that's only if you don't explicitly specify the browser/device-specific
`<link>` tags with a favicon path. See [Favicon.ico article][20] on Wikipedia.

If you don't have favicon.ico in the root consider adding one, or returning a HTTP 204 instead.
Many tools and services e.g. bookmarking sites, feed readers, web crawlers etc., request a
favicon.ico from the site root, and so recieve a HTTP 404 if it's not present. In the worst
case some frameworks will return a custom error page which is likely to be many times larger
than the missing favicon.


### Is it true that the png has to be named favicon.png?

No, this has never been true as far as I can tell from my obsessive research.


### Is it true that the ico has to be named favicon.ico?

If you don't explicitly specify its `<link>` tag, yes. Explicitness is best,
so we both name it `favicon.ico` and explicitly specify the `<link>` tag.


### Why not prefix with "apple-touch-icon"?

If you don't specify `<link>` tags, iOS looks for files prefixed with
`apple-touch-icon` or `apple-touch-icon-precomposed`. Many (e.g. HTML5
Boilerplate) rely on this assumption, but:

  * Explicitly specifying `<link>` tags is clearer and supported by Apple.
  * Not hard-coding names as `apple-touch-icon` clears up confusion as to whether
    the same icons can be reused for other purposes as-is, e.g. reusing
    favicon-144.png for Windows pinned site.


### Why use iOS precomposed icons?

  * iOS non-precomposed icons add rounded corners, drop shadow, and reflective
    shine. Sounds great in theory, but in practice the results can be very
    frustrating, especially to designers.
  * Non-precomposed icons don't work with Android 2.1.


### Why absolute paths?

Some Firefox versions require absolute paths. Since all browsers support them,
it's the simplest choice.


### Why not append a query string to force-refresh for all visitors?

Some proxies and load balancers can fail to read query strings in edge cases.


是非、寄稿を！
--------------

もし他の文書の引用や根拠の提示のために追加や変更を加えたい場合はプル・リクエストを送ってください。この文書が充実させてくれることを楽しみにしています！


[1]:  https://github.com/mathiasbynens
[2]:  http://mathiasbynens.be/notes/rel-shortcut-icon
[3]:  http://www.w3.org/html/wg/drafts/html/CR/links.html#rel-icon
[4]:  http://mathiasbynens.be/notes/touch-icons
[5]:  https://github.com/audreyr/favicon-cheat-sheet/issues/9
[6]:  http://optipng.sourceforge.net/
[7]:  http://www.imagemagick.org/Usage/thumbnails/#favicon
[8]:  http://blog.morzproject.com/convert-multiple-png-images-into-a-single-icon-file/
[9]:  http://www.xiconeditor.com
[10]: http://faviconer.com
[11]: https://github.com/abrkn/icon
[12]: https://github.com/HenrikJoreteg/favicon-setter
[13]: https://github.com/component/piecon
[14]: https://github.com/emarref/webicon
[15]: https://itunes.apple.com/us/app/icon-slate/id439697913
[16]: https://github.com/bebraw/png2ico
[17]: http://stackoverflow.com/questions/2208933/how-do-i-force-a-favicon-refresh/5239747#5239747
[18]: https://github.com/audreyr/favicon-cheat-sheet/issues/3
[19]: http://stackoverflow.com/questions/1344122/favicon-png-vs-favicon-ico-why-should-i-use-pngs-instead-of-icos/1344379#1344379
[20]: https://en.wikipedia.org/wiki/Favicon.ico
