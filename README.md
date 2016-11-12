# \<x-frame\>

[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg?style=flat-square)](https://beta.webcomponents.org/element/vpusher/x-frame)

Cross document communication with frame content made easy.

Example:
<!---
```
<custom-element-demo>
  <template>
    <script src="../webcomponentsjs/webcomponents-lite.js"></script>
    <link rel="import" href="x-frame.html">
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<x-frame src="demo/frame.html"></x-frame>
<script>
  document.querySelector('x-frame').addEventListener('msg', function(e){
    alert(e.detail.data.message)
  });
</script>
```

## Installation

First, make sure you have [Bower](https://bower.io/) and the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed.

Then,

```
bower install
polymer serve -o
```

## Usage

Add a `<x-frame>` element to your page and set the `src` attribute:

```html
<!-- Main document -->

[...]

<x-frame src="frame.html" on-msg="onMessageFromFrame"><x-frame>
```

The target page (here `frame.html`) needs to contain at least one `<x-framed>` element to enable the cross document communication:

```html
<!-- Frame document -->

[...]

<x-framed on-msg="onMessageFromParent"><x-framed>
```

The frame document can also contain more than one `<x-framed>` element to allow multi-channels cross document communication:

```html
<!-- Frame document -->

[...]

<x-framed on-msg="onMessageForUsers" channel="user"><x-framed>
<x-framed on-msg="onMessageForData" channel="data"><x-framed>
```

> This is helpful for the separation of concerns.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

* **1.0.0:** initial release.

## License

MIT license
