---
layout: default
title: Configuration
parent: page1
nav_order: 2
---

# Configuration
{: .no_toc }

Just the Docs has some specific configuration parameters that can be defined in your Jekyll site's \_config.yml file.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

View this site's [\_config.yml](https://github.com/just-the-docs/just-the-docs/tree/main/_config.yml) file as an example.

## Site logo

```yaml
# Set a path/url to a logo that will be displayed instead of the title
logo: "/assets/images/just-the-docs.png"
```


## Heading anchor links

```yaml
# Heading anchor links appear on hover over h1-h6 tags in page content
# allowing users to deep link to a particular heading on a page.
#
# Supports true (default) or false
heading_anchors: true
```

## Color scheme

```yaml
# Color scheme supports "light" (default) and "dark"
color_scheme: dark
```

<button class="btn js-toggle-dark-mode">Preview dark color scheme</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Preview dark color scheme';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Return to the light side';
  }
});
</script>

## Callouts

To use this feature, you need to configure a `color` and (optionally) `title` for each kind of callout you want to use, e.g.:

```yaml
callouts:
  warning:
    title: Warning
    color: red
```

This uses the color `$red-000` for the background of the callout, and `$red-300` for the title and box decoration.[^dark] You can then style a paragraph as a `warning` callout like this:

```markdown
{: .warning }
A paragraph...
```

[^dark]:
    If you use the `dark` color scheme, this callout uses `$red-300` for the background, and `$red-000` for the title.

The colors `grey-lt`, `grey-dk`, `purple`, `blue`, `green`, `yellow`, and `red` are predefined; to use a custom color, you need to define its `000` and `300` levels in your SCSS files. For example, to use `pink`, add the following to your `_sass/custom/custom.scss` file:

```scss
$pink-000: #f77ef1;
$pink-100: #f967f1;
$pink-200: #e94ee1;
$pink-300: #dd2cd4;
```

You can override the default `opacity` of the background for a particular callout, e.g.:

```yaml
callouts:
  custom:
    color: pink
    opacity: 0.3
```

You can change the default opacity (`0.2`) for all callouts, e.g.:

```yaml
callouts_opacity: 0.3
```

You can also adjust the overall level of callouts.
The value of `callouts_level` is either `quiet` or `loud`;
`loud` increases the saturation and lightness of the backgrounds.
The default level is `quiet` when using the `light` or custom color schemes,
and `loud` when using the `dark color scheme.`
