---
title: "Chrome extension dev - efficiently generate icons for your extension"
date: 2024-06-28
layout: post
tags: [dev]
---

Working on a chrome extension, I had to generate icon(s) from an SVG image I created. Chrome extensions icons should be named as follow:

```
images
├── icon-128.png
├── icon-16.png
├── icon-32.png
└── icon-48.png
```

I searched around but didn't found any simple and efficient solution for this. After quick reading Inkscape help I found that exporting from command line is now super fluid (this wasn't the case some years ago).

So here is the bash script:

```bash
for size in 16 32 48 128; do
    flatpak run org.inkscape.Inkscape --export-filename images/icon-$size.png --export-width $size icon.svg
done
```
