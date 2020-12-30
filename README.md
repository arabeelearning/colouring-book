# `<colouring-book>` [![Published on npm](https://img.shields.io/npm/v/@manastrophe/colouring-bbok.svg)](https://www.npmjs.com/package/@anastrophe/colouring-book)

This webcomponent follows the [open-wc](https://github.com/open-wc/open-wc) recommendations.

With special thanks to `https://github.com/collinph/jl-coloringbook` for the original concept and `<canvas>` code

## Installation
```bash
npm i colouring-book
```

## API
#### Properties/Attributes
| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| `identity` | `String` | `annonymous` | a string containing a unique ID for each user (used for local caching of coluring in).
| `images` | `Array` | `''` | An array of URLs for each page to be coloured in - defaults to first image in array.
| `colourPalette` | `Array` | see example | An array of colours (in html/css format) that can be selected by the user - defaults to first colour.
| `noPrint` | `Boolean` | `false` | Restricts the user from printing pages with their colouring in.
| `noSave` | `Boolean` | `false` | Restricts the user from saving pages locally as `.png` files.
| `noThumbnails` | `Boolean` | `false` | Applies the colouring in to the thumbnail images of each page.
| `preview` | `String` | `''` | When set to `right` the thumbnails will appear on the right of the `image`, default is above images.

### Events
| Event Name | Target       | Detail             | Description
| ---------- | ------------ | ------------------ | -----------
| `image-selected`    | `colouring-book` | `image`, `index`           | Fired when a new `image` is selectd. 
| `add-path`   | `colouring-book` | `image`, `path`           | Fired when the a new coluring `path` is added to an `image`. 
| `remove-path`   | `colouring-book` | `image`, `path`           | Fired when a `path` is removed from an `image`. 
| `clear`   | `colouring-book` | `image`           | Fired when all `path`'s are removed from an `image`. 
| `on-first-updated`   | `colouring-book` | `images`           | Custom event fired inside FirstUpdated() that passes all the images loaded. 
| `on-touch-start`   | `colouring-book` | `position`           | Custom event fired during onTounchStart of canvas.
| `on-touch-end`   | `colouring-book` | `position`           | Custom event fired during onTounchEnd of canvas. 
| `on-touch-move`   | `colouring-book` | `position`           | Custom event fired during onTounchMove of canvas.
| `print-worksheet`   | `colouring-book` | `isDownloading`, `link`           | Custom event fired onClick of print button.
| `download-worksheet`   | `colouring-book` | `isDownloading`, `link`           | Custom event fired onClick of download button.


## Example
```html
    const img = ['images/L0_P_U1_IW2.pdf-1.png','images/L0_P_U1_IW2.pdf-2.png'];
    const cols=[
            'rgba(87, 87, 87,0.8)',
            'rgba(220, 35, 35,0.8)',
            'rgba(42, 75, 215,0.8)',
            'rgba(29, 105, 20,0.8)',
            'rgba(129, 74, 25,0.8)',
            'rgba(129, 38, 192,0.8)',
            'rgba(160, 160, 160,0.8)',
            'rgba(129, 197, 122,0.8)',
            'rgba(157, 175, 255,0.8)',
            'rgba(41, 208, 208,0.8)',
            'rgba(255, 146, 51,0.8)',
            'rgba(255, 238, 51,0.8)',
            'rgba(233, 222, 187,0.8)',
            'rgba(255, 205, 243,0.8)',
            'white'];
    render(
      html`
        <colouring-book noPrint noSave .images=${img} .colourPalette=${cols} onThumbnails @add-path=${(e) => _addPath(e)}> 
        </colouring-book>
        `
    );

```

## Usage
```html
<script type="module">
  import 'colouring-book/colouring-book.js';
</script>

<colouring-book></colouring-book>
```

## Local Demo with `es-dev-server`
```bash
npm start
```
To run a local development server that serves the basic demo located in `demo/index.html`
