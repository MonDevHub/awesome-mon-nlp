# Next steps

This is a curated list. Eight files, no code, so this document is short on purpose.
A list that acquires a roadmap larger than itself has stopped being a list.

Findings live in [AUDIT-2026-08-08.md](AUDIT-2026-08-08.md), which carries its own
status table, roadmap, and *Deliberately not recommended* section. This file holds
what is still open here.

---

## Status, re-verified 2026-08-12

Every URL in `README.md` was fetched today and all of them returned 200. That
includes `mon.monnews.org` and the FlipHTML5 bookcase, the two most likely to rot.
`ocr.mondevhub.com` answered as well, which matters because that entry claims a
service is running, not that a page exists.

**Count the links one way and say which way.** The command in the next section
extracts **24 unique absolute URLs**. That number includes the two `awesome.re`
badge URLs on the title line. It excludes the two relative links to
`CONTRIBUTING.md` and `CODE_OF_CONDUCT.md`, and the eleven in-page anchors in
Contents. Drop the badge pair and 22 remain. Drop the two Wikipedia links in the
intro sentence as well and 20 remain, which is the number of URLs attached to an
actual entry.

Earlier drafts of this file said 19 and a commit message said 24. Neither was a bad
measurement, they were different conventions left unstated, and the 24 in the commit
message was read off the README as it stood before the dead entries came out. Whatever
the published command reproduces is what this file uses, so quote the convention with
the number or the count drifts again.

---

## Licence check on the fonts entry, 2026-08-13

`CONTRIBUTING.md:9-11` holds an entry to *available* and *usable*. It says nothing
about redistribution terms, and one entry needed it to.

**Myanmar Unicode Fonts** ships 82 `.ttf` files, has no `LICENSE` anywhere in its
tree, and its README does not mention licensing — GitHub's licence API returns 404
for it, and `master` has not moved since `f313142`, 2025-01-31. Its README credits
six Box, MediaFire and pCloud folders, which is a download trail rather than a
licence trail.

The fonts' own `name` table settles what the repository does not state. Read name
IDs 0, 13 and 14 over `**/*.ttf` with `fonttools`:

| Declared in the font's own metadata | Files |
| :--- | ---: |
| SIL OFL | 32 |
| Apache 2.0 | 26 |
| Something else, or a vendor EULA | 22 |
| Nothing at all | 2 |

Those 22 are why the entry now carries a warning. They include Microsoft's
`mmrtext.ttf` under the Windows product EULA, a Samsung font, and YoeYar-One, which
licenses per purchased seat on at most three computers. None of those are
redistributable, and a reader taking the collection at its word would not know.

**Kept rather than dropped.** The four families the entry names — Padauk,
Pyidaungsu, Noto Sans Myanmar and MON3 Anonta — each declare OFL or Apache, and
MON3 Anonta is OFL 1.1 and the one genuinely Mon-specific font in the set.
Dropping the entry would cost the most convenient source of the font a Mon project
actually needs, to avoid a problem one sentence solves. The entry states the mix
and tells the reader to check. It does not claim a licence for a repository that
states none.

---

## 1. Make the link check a command, not an afternoon

The check above took one shell loop. Nothing in the repository runs it.

```bash
UA="Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 \
(KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"
grep -ohE "https?://[^)\" ]+" README.md | sort -u | while read -r u; do
  code=$(curl -sS -o /dev/null -w "%{http_code}" -L --max-time 25 -A "$UA" "$u")
  [ "$code" = "200" ] || echo "$code  $u"
  sleep 2
done
```

Sequential, with a delay and a real User-Agent, because several of these hosts rate
limit and one of them is a Myanmar news site.

What the loop does not do: it skips the two relative links, and it cannot tell a bot
block or a geo block from a 404. Both matter for `mon.monnews.org`. Anything this
prints needs a person to look at it before an entry is removed.

**If it ships, ship it as `scripts/check-links.sh` plus a monthly scheduled workflow
that opens an issue rather than failing a build.** A dead upstream is not this
repository's defect and should not turn its CI red.

The audit files this under *Long-term* and gates it on rot becoming recurrent. One
round has happened, which is not yet recurrent, so this stays a proposal.

---

## 2. Open, and none of it is engineering

| Open | What it actually is |
|---|---|
| Topics `awesome` and `awesome-list` | The only two errors `npx awesome-lint` reports. They are a checkbox in repository settings on GitHub, set by the maintainer. No pull request can clear them and no code change is involved |
| This branch onto `main` | `docs/awesome-list-audit` is three commits ahead of `origin/main` with nothing in the reverse direction. A merge, once someone opens it |
| `mon_OCR` back in the list | Blocked upstream. `github.com/janakhpon/mon_OCR` still returns 404 as of 2026-08-12. The list already carries its weights and both its SDKs, so add the training repo back the day it goes public |

---

## Deliberately not doing

| Not doing | Why |
|---|---|
| **A static site or a generator** | Six markdown files. GitHub renders them. A build step would be the largest thing in the repository |
| **Restoring CI** | Removed on purpose in `5e4747c` in favour of local linting. §1 proposes one scheduled job that opens an issue, which is a different thing from a build gate |
| **Broadening beyond Mon** | The list's value is that it is exhaustive on a small subject. A general Myanmar-script list would be one of several and add nothing |
| **Listing work in progress** | An index of things you can use is worth reading. An index of things that might exist later is a plan |
