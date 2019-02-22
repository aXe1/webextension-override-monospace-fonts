# Override Monospace Fonts

Resets all monospace fonts to browser default one.

## Overview

Spending countless time in documentation, GitHub, StackOverflow, I just wanted to see code samples rendered with my favorite font with ligatures. Currently, there easy ways to do so.

## Status

Currently, it's [MVP](https://en.wikipedia.org/wiki/Minimum_viable_product) only. Although, it's usable right now, there it isn't optimized on performance, has no settings, and has no packaging. Also it's tested only in Firefox.

## Usage

1. Set default monospace font in your browser.
2. Install this extension.

## Description

Surprisingly, there are no straightforward way to do such a simple thing. So my extension does it best:

1. For each tag that commonly contains monospace text it gets computed `font-family` property.
2. If it contains one of well-known monospace font name (or `monospace` generic family name), and doesn't contains any of other generic family names then:
3. It sets inline styles that enforces browser's default monospace font and enables ligatures.
4. Subscribes to any meaningful DOM changes, and redo previous steps for changed subtree.

## Why not just use X?

### Browser settings

In Chrome you could only set fallback values, that every first website will override. In addition Firefox provides an option to restrict sites to use only default values, but for ALL generic families. No way to override only monospace ones.

### UserCSS

Pleasant option at first glance, it quickly becomes a nightmare, because it is plain old CSS, but you're cannot rewrite anything, only append. You always compete with site's CSS for specifity and `important` flag. Any inline styles and CSS overriding with JS bites you. Also, in practice general rules doesn't work and you end up writing UserCSS for every new site you visit.