---
title: Handling Long Words and URLs (Forcing Breaks, Hyphenation, Ellipsis, etc)
createdAt: 2020-04-29T23:10:44Z
---

# CSS: Handling Long Words and URLs (Forcing Breaks, Hyphenation, Ellipsis, etc)

https://css-tricks.com/snippets/css/prevent-long-urls-from-breaking-out-of-container/

SCSS-inclined

```css
@mixin word-wrap() {
  overflow-wrap: break-word;
  word-wrap: break-word;
  -ms-word-break: break-all;
  word-break: break-all;
  word-break: break-word;
  -ms-hyphens: auto;
  -moz-hyphens: auto;
  -webkit-hyphens: auto;
  hyphens: auto;
}
```

```css
@mixin ellipsis() {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```