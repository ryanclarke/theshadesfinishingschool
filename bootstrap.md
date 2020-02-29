# Bootstrap [Hugo](https://gohugo.io) site

Using [Tailwind CSS](https://tailwindcss.com), [Ionicons](https://ionicons.com) and [NetlifyCMS](https://www.netlifycms.org)

_Assumes you have `hugo` and `npm` on your `PATH`._

* Create Hugo site `hugo new site <dir>`
* Create Hugo theme `hugo new theme <themename>`
* Add `theme = "<themename>"` to `config.toml`
* Create `package.json` with `npm init`
* Add Tailwind CSS `npm install tailwindcss`
* Run `npm install -g postcss-cli`
* Run `npm install -g autoprefixer`
* Create a `postcss.config.js` file with content:

```js
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('autoprefixer'),
  ]
}
```

* Create `assets/css/main.css` in theme dir with content:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

* Insert in `layouts/partials/head.html` in theme dir:

```html
{{ $style := resources.Get "css/main.css" | postCSS | minify | fingerprint }}
<link rel="stylesheet" href="{{ $style.Permalink }}">
```

* Insert in `layouts/partials/footer.html` in theme dir:

```html
<script src="https://unpkg.com/ionicons@5.0.0/dist/ionicons.js"></script>
```
