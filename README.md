### 警告
**This `master` branch contains the `v2.x` codebase for ZeroClipboard! For the `v1.x` codebase, see the [`1.x-master`](https://github.com/zeroclipboard/zeroclipboard/tree/1.x-master) branch instead.**


# ZeroClipboard
[![GitHub Latest Release](https://badge.fury.io/gh/zeroclipboard%2Fzeroclipboard.svg)](https://github.com/zeroclipboard/zeroclipboard) [![Build Status](https://secure.travis-ci.org/zeroclipboard/zeroclipboard.svg?branch=master)](https://travis-ci.org/zeroclipboard/zeroclipboard) [![Coverage Status](https://coveralls.io/repos/zeroclipboard/zeroclipboard/badge.svg?branch=master)](https://coveralls.io/r/zeroclipboard/zeroclipboard?branch=master) [![Dependency Status](https://david-dm.org/zeroclipboard/zeroclipboard.svg?theme=shields.io)](https://david-dm.org/zeroclipboard/zeroclipboard) [![Dev Dependency Status](https://david-dm.org/zeroclipboard/zeroclipboard/dev-status.svg?theme=shields.io)](https://david-dm.org/zeroclipboard/zeroclipboard#info=devDependencies)

zeroclipboard图书馆提供的文本复制到剪贴板的使用看不见的一个简单的方法 [Adobe Flash](http://en.wikipedia.org/wiki/Adobe_Flash) 电影和 [JavaScript](http://en.wikipedia.org/wiki/JavaScript)界面。这个"Zero" 表示该库是不可见的，用户界面完全由你所留下。

这是通过自动漂浮在一个看不见的电影 [DOM](http://en.wikipedia.org/wiki/Document_Object_Model)你选择的元素。标准的鼠标事件甚至传播到你的DOM元素，所以你仍然可以有侧翻和MouseDown效果。

建议欢迎阅读 [contributing](/CONTRIBUTING.md) 指南。

## 安装程序

要在终端中设置本地开发项目，开始使用这些命令。

```sh
$ git clone https://github.com/zeroclipboard/zeroclipboard.git
$ cd zeroclipboard/
$ npm install -g grunt-cli
$ npm install
$ grunt
```

## 发展

在提交请求之前，您需要验证、生成和测试代码。在你的终端运行默认的繁重的任务。

```sh
$ grunt
```

## 测试

如果你想运行测试，测试运行的咕噜。

```sh
$ grunt test
```

## 局限性

### 需要用户交互

由于浏览器和闪存的安全限制，这个剪贴板注入可以 _**ONLY**_ 发生时

用户点击看不见的闪光电影。模拟 `click` 事件的JavaScript将不

这样就够了 [clipboard poisoning](http://www.computerworld.com/s/article/9117268/Adobe_patches_Flash_clickjacking_and_clipboard_poisoning_bugs).

### Other Limitations

For a complete list of limitations, see [docs/instructions.md#limitations](docs/instructions.md#limitations).

On that page, you will also find an [explanation of why ZeroClipboard will _NOT_ work by default on code playground sites](docs/instructions.md#starter-snippets-for-playground-sites) like JSFiddle, JSBin, and CodePen, as well as the appropriate "View" URLs to use on those sites in order to allow ZeroClipboard to work.


## Simple Example

```html
<html>
  <body>
    <button id="copy-button" data-clipboard-text="Copy Me!" title="Click to copy me.">Copy to Clipboard</button>
    <script src="ZeroClipboard.js"></script>
    <script src="main.js"></script>
  </body>
</html>
```

```js
// main.js
var client = new ZeroClipboard( document.getElementById("copy-button") );

client.on( "ready", function( readyEvent ) {
  // alert( "ZeroClipboard SWF is ready!" );

  client.on( "aftercopy", function( event ) {
    // `this` === `client`
    // `event.target` === the element that was clicked
    event.target.style.display = "none";
    alert("Copied text to clipboard: " + event.data["text/plain"] );
  } );
} );
```

See [docs/instructions.md](docs/instructions.md) for more advanced options in using the library on your site.
See [docs/api/ZeroClipboard.md](docs/api/ZeroClipboard.md) for the complete API documentation.

Here is a working [test page](http://zeroclipboard.org/#demo) where you can try out ZeroClipboard in your browser.


## Testing ZeroClipboard Locally

To test the page [demo page](http://zeroclipboard.org/#demo) locally, clone the [website repo](https://github.com/zeroclipboard/zeroclipboard.org).

## Support

This library is fully compatible with Flash Player 11.0.0 and above, which requires
that the clipboard copy operation be initiated by a user click event inside the
Flash movie. This is achieved by automatically floating the invisible movie on top
of a [DOM](http://en.wikipedia.org/wiki/Document_Object_Model) element of your
choice. Standard mouse events are even propagated out to your DOM element, so you
can still have rollover and mousedown effects with just a _little_ extra effort.

ZeroClipboard `v2.x` is expected to work in IE9+ and all of the evergreen browsers.
Although support for IE7 & IE8 was officially dropped in `v2.0.0`, it was actually
still _technically_ supported through `v2.0.2`.

## Releases

Starting with version [1.1.7](https://github.com/zeroclipboard/zeroclipboard/releases/tag/v1.1.7), ZeroClipboard uses [semantic versioning](http://semver.org/).

see [releases](https://github.com/zeroclipboard/zeroclipboard/releases)

## Related

* [jquery.zeroclipboard](https://github.com/zeroclipboard/jquery.zeroclipboard)
* [zeroclipboard-rails](https://github.com/zeroclipboard/zeroclipboard-rails)

## License

MIT &copy; [James M. Greene](http://greene.io/) [Jon Rohan](http://jonrohan.codes)
