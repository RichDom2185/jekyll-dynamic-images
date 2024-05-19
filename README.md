# Jekyll Dynamic Images

> View the demo [here](https://richdom2185.github.io/jekyll-dynamic-images).

GitHub Pages only allows a specific set of [plugins](https://pages.github.com/versions/) to run, hence, additional plugins that are in the form of RubyGems are not supported.

This plugin wraps the HTML `<picture>` element, generating the necessary `<source>` elements for the specified light/dark modes. This allows for different images to be displayed based on the user's system theme preference.

Benefits:

* Fully compatible with GitHub Pages
* Easily customisable to your needs
* Composable API with all my [other Jekyll plugins](https://github.com/RichDom2185/jekyll-showcase)

## Add it to your site

### Step 1: Copy the required files

Copy the `dynamic-images.liquid` file to your site's `_includes` folder. This is the main file that converts the extended Markdown syntax into HTML.

### Step 2: Include it in your site

#### As a HTML layout

Simply include it in any of the layouts you want to add support for:

**Recommended:** Reassign the layout's `content` variable. This approach ensures composability should you want to include additional plugins/perform additional processing on the content.

```html
{% capture content %}{% include dynamic-images.liquid html=content %}{% endcapture %}
<!-- Some other stuff... -->
{{ content }}
```

**Alternative:** Replace `{{ content }}` directly:

* Before:

  ```html
  <!-- Some other stuff... -->
  {{ content }}
  ```

* After:

  ```html
  <!-- Some other stuff... -->
  {% include dynamic-images.liquid html=content %}
  ```

## Usage

Write your dynamic images in this format:

````markdown
```img
default-image-path
```dark
dark-mode-image-path
```light
light-mode-image-path
```
````

The plugin converts it to the following HTML code:

```html
<picture>
  <source
    media="(prefers-color-scheme: dark)"
    srcset="dark-mode-image-path"
  >
  <source
    media="(prefers-color-scheme: light)"
    srcset="light-mode-image-path"
  >
  <img src="default-image-path" alt="">
</picture>
```

This allows the browser to natively control the displayed image based on the user's system theme, without any JavaScript.

**Note:** The sections `dark` and `light` are optional. If they are not provided, the default image will be displayed in both modes. Their ordering also does not matter.

If both the `dark` and `light` sections are provided, there is no need to provide a `default` image. For example:

````markdown
```img
```light
https://fakeimg.pl/1200x400/eaeaea/?text=You%20are%20in:%0A%0ALight%20Mode%20%E2%98%80%EF%B8%8F&font=museo&font_size=72
```dark
https://fakeimg.pl/1200x400/282828/?text=You%20are%20in:%0A%0ADark%20Mode%20%F0%9F%8C%91&font=museo&font_size=72
```
````

Gives the following (you may want to change the system theme between light and dark mode to see the effect):

<picture>
  <source
    media="(prefers-color-scheme: light)"
    srcset="https://fakeimg.pl/1200x400/eaeaea/?text=You%20are%20in:%0A%0ALight%20Mode%20%E2%98%80%EF%B8%8F&font=museo&font_size=72"
  >
  <source
    media="(prefers-color-scheme: dark)"
    srcset="https://fakeimg.pl/1200x400/282828/?text=You%20are%20in:%0A%0ADark%20Mode%20%F0%9F%8C%91&font=museo&font_size=72"
  >
  <img src="" alt="">
</picture>

## Use Cases

* Product Screenshots
* User Avatars
* Background Images
* Logos
