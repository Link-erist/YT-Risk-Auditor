# Editorial review conventions

## Detection

The watchlist uses one UTF-8 term, phrase, or rule per line. Ignore blank lines. Compare case-insensitively and normalize whitespace for duplicate detection; retain distinct spellings, grammatical forms, and longer phrases.

- A rule without `*` matches the whole word or phrase, bounded by non-word characters. Do not match `die` inside `diet` or `fuck` inside `fucked` unless a suitable rule exists.
- A trailing `*` expands the preceding prefix within that word only. For example, `victim*` includes `victims` and `victimized`. Treat the star as syntax, not transcript text. Do not let it consume adjacent words.
- Allow phrase whitespace to span line breaks. Report the source start and end lines for cross-line matches. Preserve the original source wording in excerpts.
- Use Unicode-aware boundaries for accented terms. Normalizing case/whitespace does not make `Pizza Gate` and `Pizzagate` equivalent; retain both spelling rules or explicitly report normalization behavior.
- Retain raw matches in the occurrence CSV with `line_start,line_end,matched_text,watchlist_rule,context`. Existing subtitle times can be included separately. Deduplicate identical display findings while retaining their matching rules.
- If reporting counts, distinguish rule matches including overlaps, unique matched texts, and distinct passages. Never call all rule matches policy violations.

Broad rules can be noisy: `minor*` matches `minority`, `egg*` matches `eggshells`, `dead*` matches `deadline`, `control*` matches `controller`, and `explicit*` matches `explicitly`. Keep detections visible in the detailed results but explain/exclude innocent uses from recommended edits. Context takes priority over a rule's name.

## Editorial judgment

The creator favors high recall for true crime, conspiracy commentary, sensitive documentaries, and other videos. Flag their chosen terms even in innocent contexts, but explain the distinction. The list also contains medical, historical, disability, identity-related, and mild terms; their inclusion supplies no automatic severity or censorship requirement.

Use practical categories:

- **Censor/edit priority:** strong profanity or explicit/descriptive material, with a reason grounded in the passage. Recommend mute, rewrite, cut, or review rather than promising safety.
- **Context review:** non-graphic factual references, medical/identity/history terms, euphemisms, or ambiguous allegations. Keep where appropriate.
- **Evidence/framing review:** unsupported criminal or medical allegations, guilt by association, insinuations of homicide, or mobilization against identifiable targets. Editing the whole assertion may be necessary.
- **Innocent match:** ordinary language or a different meaning. Examples: phone/battery died, stripped of titles, hanging out, minor acting role, seed of doubt, miscarriage of accountability, and parental consent.

Do not infer child abuse from an ordinary child photo, predation from sexual orientation, or criminal knowledge from association, naming in files, a family embrace, set design, or food references. Do not present ordinary pizza or grape soda as confirmed criminal code. A Pizzagate mention can be discussed; unsupported allegations require separate review. A term describing a group is not inherently a slur.

Preserve negation, attribution, testimony, and relevant uncertainty. Distinguish fictional characters/film scenes from actual events. Do not infer intent from a malfunction, diagnose disease or mental illness from appearance, or equate every favorable court outcome with universal exoneration. Verify specific factual/legal outcomes only if that is part of the requested work.

Repeated euphemisms such as unalived do not remove a passage's meaning. `SH`, `s harassment`, `essay`, `PDF file`, `C word`, and similar ambiguous transcriptions need audio checks. Report only what the supplied text says; never claim an uninspected audio track contains a full profanity or inferred phrase.

Only review visuals/audio actually supplied and accessible. A transcript mentioning an image does not mean the image was inspected. Blurring captions does not remove speech, imagery, or underlying allegations. If asked for automated edits, require actual media/timing before preparing precise intervals; line numbers alone are not timing.

## Policy sources

Official starting point: https://support.google.com/youtube/answer/6162278

For policy-specific advice, fetch this page and relevant official linked policies during the task. Record when checked, quote minimally, and distinguish the creator's conservative preference from an official requirement. Do not store a timeless banned-word list or claim a guaranteed algorithmic trigger. Separately distinguish advertiser suitability from removal/strikes and factual verification.

## Updating keywords

The authoritative file is `references/watchlist.txt` in the skill currently being used. Resolve relative to that SKILL.md, not to a similarly named workspace export. The initial seed has 690 unique entries; future updates are expected to change that count.

On an explicit edit request:

1. Read current entries. For each proposed addition, distinguish exact presence from broader wildcard coverage; keep a requested exact variant even when a family already detects it.
2. Apply only requested additions/removals/changes. Deduplicate case-insensitively after normalizing whitespace, preserving first spelling and existing order. Do not erase variants or old rules merely because they overlap.
3. Save UTF-8, one entry per line. Reread and verify requested terms, uniqueness, and preservation of unrelated entries. Report counts and actual changes; if already present, say so.
4. If the environment blocks the write, disclose the blocker and provide a prepared updated artifact. Do not claim the installed skill changed.

For suggested additions during audits, save a separate proposal. Avoid treating every ordinary word in a disturbing sentence as a useful new rule. Consider matching variants rather than ever-growing generic prefixes. Review saved earlier proposals when available so recurring suggestions are not presented as newly discovered.

If both a packaged source and an installed copy exist, state which copy changed and synchronize only intended user-owned copies when authorized. An old zip or dated export is a snapshot; it does not update itself.

## Example

Input: `My phone died. A minor acting role. The witness described sex trafficking.`

Report `died` and `minor` as innocent contextual matches, retain the exact `sex trafficking` location for review, and do not declare the whole transcript demonetized. If asked to add `pedophile` and it already appears once in the watchlist, report already present and preserve a single copy.
