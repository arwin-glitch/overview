# Briefing templates

The Daily Overview (`morning-brief.html`) and Daily Recap (`afternoon-checkpoint.html`)
routines build their dashboards from these files. The meeting dossier's editorial
look is the standard, and every run must look the same.

**Copy the file exactly**: the same `<head>`, the same `<style>` block character
for character, the same class names and section order. Replace only the example
text and numbers (all of it is fictional). Never add a script, edit the CSS, or
invent new components or colours. The pages are print-ready (Save as PDF gives
clean letter pages) and render without JavaScript.

## Timeline (6 AM to 10 PM Central = 16 hours)

- `left% = (start hour - 6) / 16 x 100`, `width% = duration in hours / 16 x 100` (at least 2).
- Each block has a short label in its `<span>`, e.g. `10:00 Ledgerly`.
- If a block starts within 90 minutes of the previous one, add class `lo` so its label drops a line.
- Self-blocked holds get class `hold`.
- No events: `<div class="tl short"></div>`.
- Checkpoint only: `.past` width and `.now` left are both `(now hour - 6) / 16 x 100`; draw blocks only for events still ahead.

## Cards

- `.card.r` = real cost if ignored today, `.card.a` = soft deadline, `.card.g` = good news.
- The pill is a short state: "Day 27 past due", "3rd reminder", "Due Oct 1", "Unanswered".
- `h3` = who + what (+ amount). One or two sentences in `<p>`.
- `<p class="where">` says where the email is hiding and ends with an "Open in Gmail" link to the thread.

## Text

- `h1`: one sentence, at most ~110 characters, stating the real shape of the day.
- `.stand`: one or two sentences.
- Escape `&`, `<` and `>` in all text.
- Omit any `<section>` (or the `.stale` block) that would be empty. When nothing is going stale,
  put "Going-stale sweep: nothing at risk across all folders" in the `.src` line instead.

## Morning brief order

Eyebrow `Morning Brief · <Weekday, Month D, YYYY> · Central` · h1 · `.stand` ·
4 stats in this order: Going stale (`r`), Act today (`a`), Quick wins (`g`), Meetings (no class) ·
`.src` sweep line · `.stale` block · Today (timeline + one `.ag` row per event) ·
Act today (cards) · Quick wins (`ul.qw`) · Portfolio & pipeline (table Who / Update / Flag).

## Afternoon checkpoint order

Eyebrow `Afternoon Checkpoint · <Weekday, Month D, YYYY> · <h:mm AM/PM> Central` · h1 · `.stand` ·
3 stats in this order: Act before EOD (`r`, or no class when 0), Changed since AM (`g`), Meetings left (no class) ·
`.src` sweep line · Rest of today (timeline, then `.ag` rows or a one-line `.stand`) ·
Changed since this morning (`ul.chg`, each item leads with the change) · `.stale` block ·
Act before end of day (cards). On a quiet day use
`<div class="quiet">Quiet afternoon - nothing needs Nick before end of day.</div>` in place of empty sections.
