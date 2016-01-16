# svgxuse

A simple polyfill that fetches external SVGs referenced in `<use>` elements when the browser itself fails to do so.

Example of `<use>` with external reference:
```html
<svg class="icon icon-edit"><use xlink:href="symbol-defs.svg#icon-edit"></use></svg>
```

IE (9, 10, 11) fails to load **symbol-defs.svg** in the example above. svgxuse goes through every `<use>` element. If the element is referencing an external SVG and the browser has failed to load it, the script sends a GET request to grab and prepend the SVG to `<body>`.

[**Try this demo**](https://icomoon.io/svgxuse-demo/) in IE or other browsers to see how this polyfill works in action.

## Features

#### No browser sniffing
This polyfill relies on feature detection. As a result, it detects and attempts to solve issues in any browser that may fail to fetch the linked SVG. For example, cross domain linking to external SVGs may fail with this error:
`Unsafe attempt to load URL X from frame with URL Y. Domains, protocols and ports must match.`
Using svgxuse, your SVG would still load as long as it is served with proper CORS headers.
#### Doesn't try to support IE8
svgxuse is a polyfill and therefore doesn't need to support IE8. It's minimal and to the point.
#### No requestAnimationFrame or setTimeout for polling the DOM
Unlike similar solutions, svgxuse doesn't use requestAnimationFrame or setTimeout for polling the DOM.
#### No repetitive addition of inline SVGs
Instead of replacing `<use>` elements with SVG paths, svgxuse only adds symbol definitions to the markup once.

## Usage

```html
<script src="svgxuse.js" defer></script>
```
#### With NPM
```bash
npm install --save svgxuse
```
```html
<script defer src="node_modules/svgxuse/svgxuse.js"></script>
```
#### With Bower
```bash
bower install --save svgxuse
```
```html
<script defer src="bower_components/svgxuse/svgxuse.js"></script>
```

## License

MIT &copy; [IcoMoon.io](https://icomoon.io)

