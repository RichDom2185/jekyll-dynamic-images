---
layout: demo
---
<!-- markdownlint-disable-file no-inline-html -->
<!-- markdownlint-disable-file first-line-h1 -->
<!-- markdownlint-disable-file blanks-around-fences -->

> {{ site.description }}
{: style="font-size: 1.5em" }

For the full guide (usages, etc.), view the project on [GitHub]({{ site.github.repository_url }}).

<!-- markdownlint-disable-next-line blanks-around-headings -->
## Table of Contents
{: .no_toc}

* toc
{:toc}

## Showcase

{% capture md %}
```img
```light
https://fakeimg.pl/1200x800/eaeaea/?text=You%20are%20in:%0A%0ALight%20Mode%20%E2%98%80%EF%B8%8F&font=museo&font_size=96&retina=1
```dark
https://fakeimg.pl/1200x800/282828/?text=You%20are%20in:%0A%0ADark%20Mode%20%F0%9F%8C%91&font=museo&font_size=96&retina=1
```
{% endcapture %}

Change your system's theme to see the image below change accordingly.

{{ md }}

<details markdown="1">
<summary>View Code</summary>

Note that the [fallback image](#fallback-image) is empty in this example, as we provide both light and dark mode images.

````plaintext
{{- md -}}
````
</details>

## Usage

Use the following (extended) Markdown syntax:

````plaintext
```img
default-image-path
```dark
dark-mode-image-path
```light
light-mode-image-path
```
````

### Fallback Image

The `default-image-path` is the image that will be displayed if the user's system does not support dark mode.

### Light and Dark Mode Images

The sections `dark` and `light` are optional. If they are not provided, the default image will be displayed in both modes.
