# Chapter 01 Rain Ritual Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the container-based rain ritual in chapter one with the embodied game «آخرین جای خشک», carry its causal consequence into chapter two, and synchronize the active canon without changing later plot outcomes.

**Architecture:** Treat the redesign as the single atomic revision issue `WW-046`, because chapter one, chapter two, and the two canon entries are one causal chain that cannot be accepted independently. Rewrite chapter one around the communal rain game; revise only the dependent frame of chapter two while preserving the three-step event; then validate the live manuscript and canon together before one focused commit.

**Tech Stack:** Persian Markdown manuscript, canonical story documents, revision ledger, Git, `rg`, `git diff --check`.

## Global Constraints

- The live manuscript remains 26 ordered units and chapters one and two retain Rha as focal character.
- The cradle is a genuinely loving home and its preventive care remains useful and successful.
- Niva's fall is not a moral failure, and her knee injury in chapter one remains fully prevented.
- Rha is not immune to humanic command; the bodily cost and the third step in chapter two remain unchanged in outcome.
- No new water-production, water-storage, filtration, institutional, historical, or regulatory world rule may be created.
- Chapter one must not teach water-work terminology; Saya and the practical water-work introduction move out of that chapter.
- The clay bowl receives no substitute symbol.
- The causal chain «مراقبت پیشگیرانه از نیوا در فصل یک → مراقبت منتخب در فصل بیست‌ودو → نمی‌دانم معتبر در پایان» remains intact.
- Chapter twenty-two and its three baskets remain unchanged.
- Every accepted revision issue is implemented as one focused change and one independent commit.

---

## File Map

- Modify `docs/work/revision-ledger.md`: open `WW-046` with evidence, impact, scope, locks, acceptance criteria, and the author's accepted decision; close it only after validation.
- Modify `drafts/chapters/01-روز-باران.md`: remove the bowls, work baskets, Saya, and water-work exposition; execute «آخرین جای خشک» and preserve the fall, examination, family warmth, Mehra, Aran, and the question about pain.
- Modify `drafts/chapters/02-سه-قدم-اضافه.md`: replace the bowl-washing frame with Rha's deliberate return to the fall site; remove all clay-bowl dependencies; preserve the three steps, Saya's work-scene presence, bodily command, cleanup, family care, and the unresolved Rha–Aran ending.
- Modify `docs/story/plot.md`: replace the broken-bowl beat in chapter one with the rain game and its direct causal bridge into chapter two.
- Modify `docs/story/style.md`: remove the clay-bowl motif budget entry; retain the rain, knee, and three-step budgets.
- Retain `docs/story/story.md`, `docs/story/world.md`, `docs/story/characters.md`, and every chapter after chapter two unchanged unless validation finds a direct live reference that cannot be removed within the five listed files.

### Task 1: Open and execute atomic revision issue WW-046

**Files:**
- Modify: `docs/work/revision-ledger.md`
- Modify: `drafts/chapters/01-روز-باران.md`
- Modify: `drafts/chapters/02-سه-قدم-اضافه.md`
- Modify: `docs/story/plot.md`
- Modify: `docs/story/style.md`

**Interfaces:**
- Consumes: the approved design in `docs/superpowers/specs/2026-08-10-chapter-01-rain-ritual-redesign.md` and the live revision rules in `docs/story/revision-contract.md`.
- Produces: one validated manuscript/canon revision whose stable decision is recorded in the canon and whose ledger has no active issue.

- [x] **Step 1: Record the accepted issue before changing the manuscript**

Update `docs/work/revision-ledger.md` so its active issue is `WW-046` and contains all of the following concrete facts:

```markdown
## ایشوی فعال

### WW-046 — جداسازی رسم باران از کار آب

- شاهد: فصل اول هم‌زمان کاسه‌های آیینی، سبد حامل کاسه‌ها و سبدهای توریِ کار را معرفی می‌کند و برای تفکیک آن‌ها توضیح مستقیم می‌دهد.
- اثر: تجربهٔ جمعی و بدنی باران زیر بار شناختی ظرف‌ها و سازوکار کار آب می‌رود و فصل اول پیش از نیاز، زبان فصل‌های کاری بعد را آموزش می‌دهد.
- دامنه: فصل‌های ۱ و ۲، `plot.md` و `style.md`.
- قفل‌ها: گرمی واقعی گهواره، موفقیت مراقبت پیشگیرانه، سه قدم و پیامد جسمانی فصل دوم، و زنجیرهٔ فصل‌های ۱ و ۲۲ و پایان حفظ می‌شوند.
- معیار پذیرش: کاسه و سبد توری از فصل اول حذف شوند؛ «آخرین جای خشک» بدون توضیح آیین‌نامه‌ای اجرا شود؛ افتادن نیوا و سؤال درد در مرکز بمانند؛ بازگشت عمدی رها علت سه قدم شود؛ وابستگی‌های کاسه در فصل دوم و کانون پاک شوند؛ فصل ۲۲ دست‌نخورده بماند.
- تصمیم نویسنده: طرح در ۱۰ اوت ۲۰۲۶ تأیید شد.
```

Set the baseline state to «ایشوی WW-046 پذیرفته و آمادهٔ اجراست» and keep the next issue number at `WW-047`.

- [x] **Step 2: Establish the pre-rewrite reference set**

Run:

```bash
rg -n 'کاسهٔ گلی|شش کاسه|سبد توری|رسم باران|کاسه‌ها|پارچهٔ دور کاسه|تحویل کاسه' drafts/chapters/01-روز-باران.md drafts/chapters/02-سه-قدم-اضافه.md docs/story/plot.md docs/story/style.md
rg -n 'مراقبت پیشگیرانه از نیوا|سه سبد|کانون دید: رها|سه قدم' docs/story/plot.md docs/story/style.md
```

Expected: the first command identifies every obsolete bowl/work-basket dependency to remove; the second confirms the protected causal chain and viewpoint markers before editing.

- [x] **Step 3: Rewrite chapter one around «آخرین جای خشک»**

Rewrite `drafts/chapters/01-روز-باران.md` as one coherent scene with this exact causal sequence:

1. Preserve the burned bread, Niva's batter mischief, Sef's twelve-minute forecast, the half-worn shoe, and the family's affectionate rush.
2. Remove the six bowls, their carrier basket, the clay bowl, gutters as competition sites, Saya, work baskets, branch names, reading turns, and every explanatory contrast between ritual and work tools.
3. Let families arrive with ordinary food, towels, a ball, and light seats; show that they came for the rain itself without explaining a water economy.
4. Establish «آخرین جای خشک» through behavior: adults and children notice protected dry patches, move as rain reaches them, crowd together as the patches shrink, and wait for someone to announce that no dry stone remains.
5. Keep Mehra's roasted seeds and ordinary belonging. Introduce Aran through shared space, play, and physical ease with Rha, without naming their job.
6. Give Niva a small correct judgment about a disputed dry patch so her confidence precedes the accident.
7. Have the ball escape as the remaining dry space contracts; Niva runs after it, slips on wet stone, and the ground softens before her knee strikes.
8. After the silence, let Niva laugh and announce the rain has fully arrived. Keep the family's relief and Sef's examination materially equivalent to the live version.
9. Preserve Niva's inability to identify the knee, Rha's question «اگه درد می‌گرفت چی؟», and Sef's answer «لازم نبود درد بگیرد.»
10. Let Niva return to play after the timed restriction. End with Rha physically attending to the restored hard surface where the prevented impact left no trace; do not explain the theme.

Prose requirements: close third person through Rha; concrete sensory language; no explanatory paragraph defining the rules; no organized dance; no replacement breakable object; no newly named ritual office or authority.

- [x] **Step 4: Validate chapter one's standalone execution**

Run:

```bash
rg -n 'کاسهٔ گلی|شش کاسه|سبد توری|گروه آب|مسیر غربی|خوانش آخر|سایا' drafts/chapters/01-روز-باران.md
rg -n 'آخرین|خشک|مهرا|آران|کدوم زانوت|اگه درد می‌گرفت|لازم نبود درد بگیرد' drafts/chapters/01-روز-باران.md
```

Expected: the first command returns no matches; the second finds enacted dry-place play, both supporting characters, and the protected examination beats. Read the complete chapter once to reject any rulebook-like explanation, false menace in Sef's care, or loss of family warmth.

- [x] **Step 5: Reframe chapter two without changing its event outcome**

Revise `drafts/chapters/02-سه-قدم-اضافه.md` with this exact dependency replacement:

1. Open the morning after rain with Rha deliberately returning to the place where Niva fell; the restored surface shows no mark of the prevented knee impact.
2. Let the dry service strip beyond the valid route attract her because it is ground that will not soften for her. Preserve her desire to know what that ground feels like.
3. Remove the washing rack, six bowls, clay bowl, tied repair cloth, delivery program, and every later bowl callback.
4. Keep Aran arriving on his valid work route with the shallow basket of cut stalks. His work basket is not a ritual vessel and remains justified by the scene.
5. Preserve Sef's valid-route command, the contrast between a machine command and Aran's words, the first two steps, vomiting, Saya's arrival with the work net, the delayed western-path work, the third step, and the cleanup of the leaf and soil.
6. Replace Aran's offer to carry bowls with an attempt to make Rha return for her own bodily safety; after the third step, he interrupts his route and accompanies her home despite Sef noting that his assigned work continues.
7. Preserve the family care sequence at home, the moved western turn, Rha's impaired right hand, and the question of whether Aran reported her.
8. Rebuild the final exchange without the bowl on the windowsill: Aran may remain outside after escorting her or return after delivering the stalks, but Rha must ask whether he reported her, he must say no, and his reason must remain tied to her asking how many steps she took. End on unresolved distance, not reconciliation.

- [x] **Step 6: Validate chapter two and the chapter-one-to-two causal handoff**

Run:

```bash
rg -n 'کاسهٔ گلی|شش کاسه|کاسه‌ها|پارچهٔ دور کاسه|تحویل کاسه|شستن کاسه' drafts/chapters/02-سه-قدم-اضافه.md
rg -n 'زمین|مسیر|قدم سوم|سه قدم|گزارش کردی|نوبت غربی|سایا|توری' drafts/chapters/02-سه-قدم-اضافه.md
```

Expected: the first command returns no obsolete bowl dependency; the second confirms the ground/route motive, third step, reporting conflict, and retained work-world consequence. Read chapters one and two consecutively and verify that the second morning is caused by the first day's prevented impact without a retrospective explanatory summary.

- [x] **Step 7: Synchronize plot and style canon**

In `docs/story/plot.md`, replace the broken-bowl bullet under chapter one with two concise bullets:

```markdown
- خانواده‌ها «آخرین جای خشک» را بازی می‌کنند؛ باران تجربه‌ای جمعی و بدنی است و از کار آبراه‌ها جدا می‌ماند.
- رها به سطحی توجه می‌کند که پیش از برخورد نیوا نرم و سپس بی‌نشان سفت می‌شود؛ بازگشت صبح بعد و سه قدم از همین پرسش می‌آیند.
```

Keep the existing bullets for focalization, useful preventive care, the pain question, and the value of safety. Under chapter two, make the choice explicit without adding a new outcome:

```markdown
- رها برای سنجیدن زمینی که پس از نجات نیوا دوباره سفت شده به باغ برمی‌گردد و آگاهانه از مسیر امن بیرون می‌رود.
```

In `docs/story/style.md`, delete only this motif-budget line:

```markdown
- کاسهٔ گلی: فقط فصل‌های یک و دو؛ به نماد پایانی تبدیل نشود.
```

Retain the rain, knee, and three-step motif lines verbatim.

- [x] **Step 8: Run focused continuity and scope validation**

Run:

```bash
rg -n 'کاسهٔ گلی|شش کاسه|پارچهٔ دور کاسه|تحویل کاسه' drafts/chapters docs/story docs/work/revision-ledger.md
rg -n 'آخرین جای خشک|مراقبت پیشگیرانه از نیوا|زانو|باران:|سه قدم:' drafts/chapters/01-روز-باران.md drafts/chapters/02-سه-قدم-اضافه.md docs/story/plot.md docs/story/style.md
git diff --check
git diff --stat
```

Expected:

- The obsolete clay-bowl phrases are absent from the live manuscript and active canon; the approved design/plan may still describe their removal.
- The new game and the protected rain/knee/three-step causal chain are present.
- `git diff --check` returns no errors.
- The diff is limited to the ledger, chapters one and two, plot, and style; the approved design and this plan may appear only as already recorded planning artifacts.

Then inspect:

```bash
git diff -- docs/work/revision-ledger.md drafts/chapters/01-روز-باران.md drafts/chapters/02-سه-قدم-اضافه.md docs/story/plot.md docs/story/style.md
```

Reject the revision if it introduces a substitute symbol, explains the game's rules in an expository block, weakens the real usefulness of care, changes the outcome of the three steps, or alters chapter twenty-two.

- [x] **Step 9: Close WW-046 in the ledger**

After the focused read passes, remove the active issue body and record this result:

```markdown
## ایشوی فعال

ندارد.

## نتیجهٔ چرخهٔ جاری

- `WW-046` قبول شد: رسم «آخرین جای خشک» جای کاسه‌های باران را گرفت، معرفی کار آب از فصل اول کنار رفت، و بازگشت عمدی رها به محل افتادن نیوا علت مستقیم سه قدم شد؛ مراقبت موفق فصل اول، پیامد جسمانی فصل دوم و زنجیرهٔ نیوا تا فصل ۲۲ دست‌نخورده ماندند.
```

Set the baseline to the version after `WW-046`, the state to «بازطراحی رسم باران و پیوند فصل دوم اعتبارسنجی شد», and the next issue number to `WW-047`.

- [x] **Step 10: Perform final verification and commit the atomic revision**

Run:

```bash
git diff --check
git status --short
rg -n 'WW-046|WW-047|ایشوی فعال|آخرین جای خشک' docs/work/revision-ledger.md docs/story/plot.md drafts/chapters/01-روز-باران.md
```

Expected: no whitespace errors; only the five implementation files plus this plan are uncommitted; the ledger is closed on `WW-046` and points to `WW-047`; the new ritual is present in chapter one and plot.

Commit the complete atomic revision:

```bash
git add docs/superpowers/plans/2026-08-10-chapter-01-rain-ritual-redesign.md docs/work/revision-ledger.md drafts/chapters/01-روز-باران.md drafts/chapters/02-سه-قدم-اضافه.md docs/story/plot.md docs/story/style.md
git commit -m "revise(opening): جداسازی رسم باران از کار آب"
```

After committing, run:

```bash
git status --short
git log -1 --oneline
```

Expected: clean worktree and a new `revise(opening)` commit for `WW-046`.
