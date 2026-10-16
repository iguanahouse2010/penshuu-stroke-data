# Notice of changes and licenses

This repository contains the stroke data used by the Penshuu iPad app, exactly as the app ships it. The data is modified from the AnimCJK project. This notice states what we changed, when we changed it, and which license covers each part of the data.

## Contents

| Path | What it holds |
|---|---|
| `kanji/` | 2,238 JSON files made from AnimCJK `svgsJa` (kanji, plus 々 U+3005) |
| `kana/` | 177 JSON files made from AnimCJK `svgsJaKana` (hiragana and katakana) |
| `licenses/` | The license texts listed at the end of this notice |
| `SHA256SUMS` | A SHA-256 hash for every data file |

Each file is named by its character's Unicode code point in hexadecimal. For example, `kanji/66F8.json` is 書.

## Sources

- **AnimCJK.** AnimCJK project - Copyright 2016-2025 - FM&SH. <https://github.com/parsimonhi/animCJK>, revision `95af6e64ea347c881df7c2d95b22e1e2f7c2fb8d` (2025-10-06). Its own notice, `licenses/COPYING.txt`, states that AnimCJK is derived from the Arphic PL KaitiM GB font, the Arphic PL UKai font and the Makemeahanzi project.
- **KanjiVG.** © Ulrich Apel. <https://kanjivg.tagaini.net/>, release r20160426.

## Licenses, field by field

Each file holds `character`, `unicode`, `strokeCount` and a list of `strokes`. Each stroke holds `id`, `outlineSVG`, `centerlineSVG`, `points` and `type`.

| Data | Files in `kanji/` | Files in `kana/` |
|---|---|---|
| The stroke shapes (`outlineSVG`, `centerlineSVG`, `points`) and the strokes' number and order | Arphic Public License (`licenses/APL/ARPHICPL.TXT`) | GNU Lesser General Public License, version 3 or later (`licenses/LGPL.txt`, which incorporates `licenses/GPL-3.0.txt`) |
| `type` | Creative Commons Attribution-ShareAlike 3.0 (`licenses/CC-BY-SA-3.0.txt`) | Creative Commons Attribution-ShareAlike 3.0 (`licenses/CC-BY-SA-3.0.txt`) |

`character` and `unicode` identify which character a file describes.

The `type` values (`tome`, `harai`, `hane`, `straight`) are derived from KanjiVG's stroke classifications (its `kvg:type` attribute). A small number of them were set by us instead: `straight` where a KanjiVG classification has no match in our mapping, and, for a few characters, values entered by hand or carried over from an earlier version of our data. We offer those values under Creative Commons Attribution-ShareAlike 3.0 as well.

## What we changed, and when

We adopted AnimCJK on 2026-03-18 and froze this data on 2026-10-10. Every change below was made between those two dates.

1. **Format.** Each AnimCJK SVG file became one JSON file.
   - `outlineSVG` is the stroke's AnimCJK outline path.
   - `centerlineSVG` is the stroke's AnimCJK median (centerline) path.
   - `points` is new. It is the centerline sampled into points, with 4 points for each curve segment, scaled from AnimCJK's 1024-unit grid to the range 0–1 and rounded to 4 decimal places.
2. **Outline pieces joined.** Where AnimCJK draws one kana stroke's outline as two pieces, we joined them into one path. This affects 25 strokes, one in each of 25 hiragana files.
3. **Stroke order.** In 75 characters, we reordered the strokes to match the stroke order in KanjiVG.
4. **One merged stroke.** For 衷 (U+8877), AnimCJK draws 10 strokes, while the Japanese form is written with 9. On 2026-06-09 we merged AnimCJK's strokes 1 and 6 into a single stroke, joining their outlines and their centerlines.
5. **Stroke types.** We added the `type` field to every stroke, as described above. We adopted this approach on 2026-03-25.

Apart from the joins in items 2 and 4, the outline and centerline paths are AnimCJK's path data, byte for byte. We measured this against revision `95af6e64e`:

- 23,792 of the 23,818 outlines are identical to an AnimCJK path, and the other 26 are the joins in items 2 and 4.
- 23,817 of the 23,818 centerlines are identical to an AnimCJK path, and the other one is the join in item 4.

## License texts

| File | Where it comes from |
|---|---|
| `licenses/APL/ARPHICPL.TXT` | AnimCJK `95af6e64e`, `licenses/APL/english/ARPHICPL.TXT`, unaltered |
| `licenses/COPYING.txt` | AnimCJK `95af6e64e`, `licenses/COPYING.txt`, unaltered |
| `licenses/LGPL.txt` | AnimCJK `95af6e64e`, `licenses/LGPL.txt`, unaltered |
| `licenses/GPL-3.0.txt` | <https://www.gnu.org/licenses/gpl-3.0.txt>. AnimCJK does not include it, and the LGPL incorporates it. |
| `licenses/CC-BY-SA-3.0.txt` | <https://creativecommons.org/licenses/by-sa/3.0/legalcode.txt> |
