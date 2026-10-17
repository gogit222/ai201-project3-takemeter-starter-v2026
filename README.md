# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->



---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `analysis`

**Definition:** Makes an interpretive or evaluative claim about a film and supports it with a specific, checkable detail or comparison that does real work in the reasoning.

**Example 1:** [The Verdict (1982)](https://www.reddit.com/r/TrueFilm/comments/1x71u9t/the_verdict_1982_by_sidney_lumet/) connects long shots, unscored courtroom scenes, and the final phone call to its reading of the film's mood and ending.

**Example 2:** [Primetime as an anti-war film](https://www.reddit.com/r/TrueFilm/comments/1x7r6pb/primetime_as_an_antiwar_film_a_critique_of_the/) uses named historical footage and parallels with *To Catch a Predator* to support its argument about media spectacle.

### `hot_take`

**Definition:** States a confident general verdict or interpretation about a film or filmmaker without a specific, load-bearing reason; a detail mentioned in passing does not count as support.

**Example 1:** [I think Backrooms (2026) will be looked back on as a masterpiece](https://www.reddit.com/r/TrueFilm/comments/1x68qdy/i_think_backrooms_2026_will_be_looked_back_on_as/) predicts future acclaim but offers no concrete film detail to support the prediction.

**Example 2:** [Digger is Tom Cruise's Best Acting](https://www.reddit.com/r/TrueFilm/comments/1x526sd/) makes a strong comparative claim about Cruise's performance without pointing to a specific performance choice or scene.

### `reaction`

**Definition:** Primarily reports the writer's personal viewing response or taste, rather than using evidence to establish a broader interpretation or claim.

**Example 1:** [Whalefall](https://www.reddit.com/r/TrueFilm/comments/1x6s2av/whalefall/) centers on the writer holding their breath, gripping the seat, and feeling trapped during the viewing.

**Example 2:** [Gone Girl (2014) - the last great Hollywood thriller?](https://www.reddit.com/r/TrueFilm/comments/1x65fpw/gone_girl_2014_the_last_great_hollywood_thriller/) is mainly a personal account of enjoying the pacing, cast, and mood, rather than a developed argument about the film.

### `question`

**Definition:** Primarily asks for an explanation, recommendation, or interpretation and does not present the answer as settled; supporting details provide context for the question.

**Example 1:** [Memento question - How can Leonard change his old memories with new information?](https://www.reddit.com/r/TrueFilm/comments/1x7c5t4/memento_question_how_can_leonard_change_his_old/) lays out the film's memory premises and asks how they fit together.

**Example 2:** [What was the OG trapped-in-an-insane-asylum horror film?](https://www.reddit.com/r/TrueFilm/comments/1x56455/) asks about the origin of a horror trope without proposing a settled answer.

### The hardest boundary

**Which two labels:** `reaction` and `analysis`

**The post:** [Whalefall](https://www.reddit.com/r/TrueFilm/comments/1x6s2av/whalefall/). It names close-ups and dangerous scenes, but uses them mainly to describe the writer's own physical response.

**The decision rule I used every time:** If scene details mainly explain what the writer felt while watching, label `reaction`; use `analysis` only when those details support a broader claim about the film's craft, meaning, or effect. If both are present, classify by what the post spends most of its words doing.


---

## Candidate Distinctions

These are preliminary, observable patterns from reading 32 public posts in r/TrueFilm. They informed the labels above but are not themselves labels. The initial 30-post sample included a cluster about one current film, so the dataset should span dates and avoid spoiler-heavy examples.

- **Film-specific evidence vs. general evaluation:** Does the writer point to a scene, shot, performance, line, or sound and use it to support a claim? A passing detail may not do that work. For example, [The Verdict (1982)](https://www.reddit.com/r/TrueFilm/comments/1x71u9t/the_verdict_1982_by_sidney_lumet/) discusses long shots and unscored courtroom scenes.
- **Film-only discussion vs. connections to other works or contexts:** Does the post build its interpretation through comparisons to other films, historical events, source texts, or critical ideas? For example, [Primetime as an anti-war film](https://www.reddit.com/r/TrueFilm/comments/1x7r6pb/primetime_as_an_antiwar_film_a_critique_of_the/) compares the film with the War on Terror and *To Catch a Predator*.
- **Personal viewing experience vs. detached interpretation:** Does the writer make their own emotional response or life experience part of the claim, or focus mainly on formal analysis? For example, [Whalefall](https://www.reddit.com/r/TrueFilm/comments/1x6s2av/whalefall/) describes a physical reaction to suspense and close-ups.
- **Open inquiry vs. settled thesis:** Is the post weighing alternatives or asking for an explanation, or presenting one interpretation as settled? For example, the [Memento memory question](https://www.reddit.com/r/TrueFilm/comments/1x7c5t4/memento_question_how_can_leonard_change_his_old/) asks how a character could retain information given the film's stated memory condition.

These patterns can overlap. A personal reaction can cite scene details, and a confident interpretation can be carefully argued. For evidence-based distinctions, test whether cited details actually support the claim.


---

## Stress Test

These eight synthetic boundary probes were AI-generated for testing the definitions; they are not source posts and must not be added to the dataset.

1. **`hot_take`** — "This is the best film of the year. The director has never made a bad one." The verdict has no supporting reason.
2. **`analysis`** — "The opening frames Mara behind a locked door; the final shot repeats that framing with the door open. That visual change makes her decision to leave feel earned." Checkable details support the interpretation.
3. **`reaction`** — "I watched it last night and left the theater buzzing; the quiet minute after the final scene made me unexpectedly sad." The point is the viewer's response.
4. **`question`** — "The same key appears in the first and last scenes. Do you read it as proof that Mara planned the escape, or as a visual echo?" It requests interpretation without settling one.
5. **`hot_take`** — "The ending is objectively terrible. The director has lost it." This is a confident judgment with no evidence.
6. **`analysis`** — "The film cuts away before the door opens twice, then holds on the third attempt; that change makes Mara's choice more important than the outcome." The repeated formal detail supports the claim.
7. **`reaction`** — "I got restless halfway through and felt relieved when it ended. It just didn't hold me." This reports personal taste without asserting a general verdict.
8. **`question`** — "The final conversation leaves the accusation unanswered. Which earlier scene gives the strongest clue about who is lying?" It asks for evidence rather than offering a conclusion.

The probes were consistently classifiable after distinguishing genuine requests from rhetorical questions, personal response from general verdict, and load-bearing evidence from decorative detail. I kept the four definitions and made those checks explicit in the decision rule.



---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->

**Counts per label:**

| Label | Count | Share |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |
| **Total** |  | 100% |

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

**2.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

**3.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:**

**Settings:** <!-- epochs, learning rate, batch size, seed -->

**Anything I changed from the defaults, and why:**

**Split sizes:** <!-- train / val / test, and per-label counts in the test
split. If a label had fewer than about 8 in test, say so — it explains a lot
of next unit's variance. -->



---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:*
- *What came back:*
- *What I changed:*

**Moment 2**

- *What I asked for:*
- *What came back:*
- *What I changed:*

**Pre-labelling disclosure:**

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy |  |  |  |
| Macro F1 |  |  |  |
| F1 — `label_one` |  |  |  |
| F1 — `label_two` |  |  |  |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->



---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted |  |  |  |
|---|---|---|---|
| **** |  |  |  |
| **** |  |  |  |
| **** |  |  |  |

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->



---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** ___ / 30 = ___%

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**2.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**What the pattern in my disagreements tells me:**



---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
