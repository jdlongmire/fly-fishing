---
title: Home
nav_order: 1
---

# Fly Fishing Field Notes

A personal, growing field journal for fly fishing — the flies that work, the water worth returning to, hard-won tips, gear notes, and seasonal timing. Built to be searched, added to over years, and shared.

<div class="home-cards" markdown="0">
  <a class="home-card" href="{{ '/flies/reference/' | relative_url }}"><strong>🎣 Fly Reference</strong><span>Searchable, filterable table of every pattern</span></a>
  <a class="home-card" href="{{ '/locations/south-holston/' | relative_url }}"><strong>🗺️ South Holston</strong><span>Sections, access map, releases, flies, logistics</span></a>
  <a class="home-card" href="{{ '/locations/' | relative_url }}"><strong>📍 All Waters</strong><span>Everywhere documented so far</span></a>
  <a class="home-card" href="{{ '/catch-log/' | relative_url }}"><strong>📓 Catch Log</strong><span>Dated trips — conditions and what worked</span></a>
</div>

<style>
.home-cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(210px,1fr));gap:.7rem;margin:1.2rem 0}
.home-card{display:flex;flex-direction:column;gap:.25rem;border:1px solid #d9e2ec;border-radius:.5rem;padding:.8rem .9rem;text-decoration:none;background:#f8fafc}
.home-card:hover{border-color:#2b6cb0;background:#eef3f8}
.home-card strong{font-size:1rem}
.home-card span{font-size:.85rem;color:#556}
</style>

> Use the search box (top of the page) to jump straight to a fly, water, or tip — it indexes everything.

## What's here

| Folder | What it holds |
|---|---|
| [flies/](flies/) | Individual fly patterns — what they imitate, how to fish them, when they produce |
| [locations/](locations/) | Waters I fish — access, structure, hatches, regulations, honest notes |
| [tips/](tips/) | Technique and tactics — casting, reading water, presentation, knots |
| [gear/](gear/) | Rods, reels, lines, leaders, waders — what I use and why |
| [seasons/](seasons/) | Seasonal timing, hatch charts, what's working when |
| [catch-log/](catch-log/) | Dated trip entries — conditions, what worked, what didn't |

## How to add an entry

Each folder has a `_template.md` (where useful) and its own `README.md` index. To add a fly, location, or trip:

1. Copy the folder's `_template.md` to a new descriptively-named file (e.g. `flies/elk-hair-caddis.md`, `locations/south-holston-tailwater.md`).
2. Fill it in — partial is fine, notes beat blank.
3. Add a line to that folder's `README.md` index.

Keep it honest: record the skunkings and the misses too. The failures are half the value of a journal.

## Conventions

- **File names:** lowercase, hyphenated, descriptive (`pheasant-tail-nymph.md`, not `PTN.md`).
- **Locations:** don't publish anything that would burn a spot you want to protect — keep sensitive access details vague or in a private note. This repo is public.
- **Dates:** ISO format `YYYY-MM-DD`.
- **Photos:** drop images next to the entry or in an `img/` subfolder; link them inline.

## License

Personal notes shared freely — see [LICENSE](LICENSE). Tight lines.
