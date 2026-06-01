# Forward-Deployed Engineer — take-home

## The problem

We build software that turns a client's raw source material into a finished, near-final
**advice document**. A human adviser then reviews and signs it off. Your job in this exercise
is the heart of that work: take a client's sources and a configurable generation pipeline, and
make it produce a **correct, well-judged advice report** — then improve the pipeline itself
where you think it should be better.

This is deliberately close to the real role. You are not building a product from scratch; you
are taking a working-but-rough pipeline and making it trustworthy. Most of the skill is
**judgement about data and language**, not heavy software engineering.

## What you're given

```
data/                     four clients' source material, increasing in difficulty (see below)
pipeline/
  generate.py             the generator: reads the config + a client's data, produces a report
  formatter.py            turns the generated section content into a finished .md document (leave as-is)
config/
  template_config.json    the report definition you will mostly work in:
                          sections, the prompts that fill them, inclusion rules, source mappings
outputs/                  where generated reports land
```

Each client folder under `data/` contains:

- `meeting_notes.docx` — the adviser's latest conversation with the client.
- `client_data_db.json` — structured holdings/account data from our systems.
- `report_request.docx` — the adviser's instruction for what this report should cover.
- `fde_notes.md` — internal notes on the data sources and how they fit together. **Read these
  carefully.**
- `template_spec.md` — what each section of the report should contain.

The starting pipeline runs and produces a document. It is an honest first draft, not a finished
system — treat it the way you'd treat a colleague's rough cut. Change anything: the config, the
prompts, the pipeline code. If you see a better way to structure the generation, do it (or, if
you don't have time to build it, write down what you'd do and why).

## What we'd like you to do

1. **Make the reports correct.** Work through the clients (`client_01_clean` → `client_04_stretch`).
   The generated documents should faithfully reflect each client's situation and the adviser's
   instruction. Most of your effort will be in `config/template_config.json` — the prompts, inclusion
   rules, and how each value is sourced. Read the source material closely; the clients get harder, and
   the last one is a deliberate stretch — we're interested in how you approach it even if you don't
   fully finish.
2. **Improve the pipeline where it deserves it.** You have free rein over `pipeline/` and the
   config. Use whatever model(s) and structure you think are right.
3. **Write your own evaluation.** We don't give you expected outputs. Decide what "correct" means,
   and write something that checks it. How you choose to evaluate tells us how you think about the
   problem.
4. **Keep a short decisions log** (`DECISIONS.md`): the 3 hardest calls you made and why, plus
   anything you'd change about the pipeline that you didn't have time to build.

## Working method + what to submit

- **Fork this repository** (keep your fork public), work in your fork, and **commit as you go** —
  we read the commit history, so let it show your thinking, not one big final dump.
- Use whatever AI / coding tools you like. We care about your reasoning and what you notice, not
  whether you typed every character.
- When you're done, send us your fork URL. Make sure it contains: your `config/`, your `pipeline/`,
  your eval, your `DECISIONS.md`, and the final generated reports in `outputs/`.

## How we'll assess it

We look at the generated reports, your config and prompts, your eval, your decisions log, and your
commits. We're weighing **judgement** far more than software polish:

- Did the reports get the facts right, and did you reason correctly about where each value should
  come from when sources don't agree?
- Did the right sections appear (and the wrong ones stay away)?
- Are your prompts clear and well-structured? Did you iterate them?
- Did your eval check things that actually matter?
- Did you spot where the pipeline's shape could be better — and act on it or articulate it?

Clean code is hygiene, not the headline. We are not grading you on Docker, CI, or a UI.

## A candid word on the role

This is a forward-deployed engineering role and it's genuinely satisfying, but be clear-eyed about
it: a good chunk of the job is unglamorous, careful **reading** — meeting notes, data, an adviser's
half-formed instruction — and translating that into something a non-technical person can trust. The
best outcome is often **less**: a simpler config, a rule removed. If building flashy systems is what
you want, this isn't that. If turning messy human input into something correct and clear sounds
satisfying, you'll enjoy it. Ask us anything about what it's really like — we'd rather you know now.
