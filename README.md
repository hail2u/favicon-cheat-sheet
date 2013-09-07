ファビコン・カンニング・ペーパー
================================

A painfully obsessive cheat sheet to favicon sizes/types. Compiled from:

  * http://mathiasbynens.be/notes/rel-shortcut-icon <-- special thanks [@mathiasbynens][1]
  * http://mathiasbynens.be/notes/touch-icons <-- special thanks [@mathiasbynens][1]
  * http://www.jonathantneal.com/blog/understand-the-favicon/
  * https://en.wikipedia.org/wiki/Favicon.ico
  * http://snook.ca/archives/design/making\_a\_good\_favicon
  * http://www.netmagazine.com/features/create-perfect-favicon
  * http://www.ravelrumba.com/blog/android-apple-touch-icon/
  * http://msdn.microsoft.com/en-us/library/ie/gg491740(v=vs.85).aspx


The HTML
--------

### Basics

For the main favicon itself, it's [best][2] for cross-browser compatibility not to
use any HTML. Just name the file `favicon.ico` and place it in [the root of your
domain][2].

This works in every desktop browser/version all the way back to IE6, except for SeaMonkey.


### Optional But Encouraged

You probably also want the following:

  1. Touch icon for iOS 2.0+ and Android 2.1+:

     ```html
     <link rel="apple-touch-icon-precomposed" href="path/to/favicon-152.png">
     ```

  2. IE 10 Metro tile icon (Metro equivalent of apple-touch-icon):

     ```html
     <meta name="msapplication-TileColor" content="#FFFFFF">
     <meta name="msapplication-TileImage" content="/path/to/favicon-144.png">
     ```

     Replace #FFFFFF with your desired tile color.


### Very Optional, for the Obsessive

If you're obsessive, you want all this too:

  1. Largest to smallest [apple-touch-icons][4]:

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

  2. Favicons targeted to any additional png sizes that you add that aren't covered above:

     ```html
     <link rel="icon" href="/path/to/favicon-32.png" sizes="32x32">
     ```


The Images
----------

Create at least this:

|Sizes        |Name           |Purpose                                                                |
|-------------|---------------|-----------------------------------------------------------------------|
|16x16 & 32x32|favicon.ico    |Default required by IE. Chrome and Safari may pick ico over png, sadly.|

More about favicon.ico below. Yes, it's 1 file with multiple sizes.

If you also sort of care about iOS and Android but are lazy:

|Sizes  |Name           |Purpose                                                  |
|-------|---------------|---------------------------------------------------------|
|152x152|favicon-152.png|General use iOS/Android icon, auto-downscaled by devices.|

But keep in mind that icons with complex detail often don't downscale well.
Often you have to tweak subtle design details for smaller sizes.

If you're obsessive, create these too:

|Sizes  |Name           |Purpose                                                             |
|-------|---------------|--------------------------------------------------------------------|
|32x32  |favicon-32.png |Certain old but not too old Chrome versions mishandle ico           |
|57x57  |favicon-57.png |Standard iOS home screen (iPod Touch, iPhone first generation to 3G)|
|72x72  |favicon-72.png |iPad home screen icon                                               |
|96x96  |favicon-96.png |GoogleTV icon                                                       |
|120x120|favicon-120.png|iPhone retina touch icon (Change for iOS 7: up from 114x114)        |
|128x128|favicon-128.png|Chrome Web Store icon                                               |
|144x144|favicon-144.png|IE10 Metro tile for pinned site                                     |
|152x152|favicon-152.png|iPad retina touch icon (Change for iOS 7: up from 144x144)          |
|195x195|favicon-195.png|Opera Speed Dial icon                                               |


ICO File
--------

An .ico file is a container for multiple .bmp or .png icons of different sizes.
In favicon.ico, create at least these:

|Sizes|Purpose                                                                |
|-----|-----------------------------------------------------------------------|
|16x16|IE9 address bar, Pinned site Jump List/Toolbar/Overlay                 |
|32x32|New tab page in IE, taskbar button in Win 7+, Safari Read Later sidebar|
|48x48|Windows site icons                                                     |

If you're obsessive and don't mind 1-3kb extra size, also include these sizes
in your .ico:

|Sizes|Purpose                                                      |
|-----|-------------------------------------------------------------|
|24x24|IE9 Pinned site browser UI                                   |
|64x64|Windows site icons, Safari Read Later sidebar in HiDPI/Retina|

Create your .ico out of optimized .png files.

*TODO:* get confirmation that IE9+ supports .ico files that contain .png files ([Issue #9][5])


Helpful Tools
-------------

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


Forcing a Favicon Refresh
-------------------------

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

FAQ
---

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


Contribute!
-----------

Send pull requests if you have anything to add/change, providing citations
and justification. I'd love to see this improve.


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
