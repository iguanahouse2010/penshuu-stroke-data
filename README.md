# Penshuu stroke data

This repository holds the stroke data used by Penshuu, an iPad app for practicing Japanese handwriting with a pen. It describes the strokes of 2,415 characters, which the app uses to animate stroke order.

The data is modified from [AnimCJK](https://github.com/parsimonhi/animCJK). Stroke types are derived from [KanjiVG](https://kanjivg.tagaini.net/). It is published free of charge, as its licenses require.

**[NOTICE.md](NOTICE.md) states what we changed, when, and which license covers each part of the data.** Read it before reusing the data.

## Check the files

Every data file has a SHA-256 hash in `SHA256SUMS`:

```bash
shasum -a 256 -c SHA256SUMS
```
