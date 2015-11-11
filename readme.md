# svgxuse

A simple polyfill that fetches external SVGs referenced in `<use>` elements when the browser itself fails to do so.

Example of `<use>` with external reference:
```html
<svg class="icon icon-edit"><use xlink:href="symbol-defs.svg#icon-edit"></use></svg>
```

IE (9, 10, 11) fails to load **symbol-defs.svg** in the example above. svgxuse goes through every `<use>` element. If the element is referencing an external SVG and the browser has failed to load it, the script sends a GET request to grab and prepend the SVG to `<body>`.

## Usage

```html
<script src="svgxuse.js" defer></script>
```

## License

MIT &copy; [IcoMoon.io](https://icomoon.io)

