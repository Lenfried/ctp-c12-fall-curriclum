# The Expert Jigsaw — Week 1 Homework

*Your first homework. You claim an aspect at tonight's pod meet, and it's due
before week 2.*

The starter app has **eight aspects**. Each person in your pod claims one
(first come in your pod thread, and no two people on the same aspect) and
becomes the pod's expert on it. Together, your pod covers the whole app.

Pods are temporary week-1 groups. Teams form in week 2 around the pitches, so
whichever team you end up on, everyone there will have studied all eight
aspects.

All of this runs against the **course starter's `example/todo` branch**. The
clone you made in week 1's study hall is your study copy. Your team's repo,
created in week 2, starts as the blank skeleton, and the example stays
upstream.

| # | Aspect | Where it lives | The question you'll answer for your pod |
|---|--------|----------------|------------------------------------------|
| 1 | The request path | `apps/web` | What happens between a click and a render? |
| 2 | The domain door | `packages/domain` | Where's the one place input becomes trusted? |
| 3 | The data layer | `packages/db` · `apps/db-server` · `apps/migrate` | Why does `pnpm dev` start a database, and what are the three doors? |
| 4 | Identity | `packages/auth` | Who am I, according to the app, and why is that safe for now? |
| 5 | The background half | `apps/worker` | How does work get done when no request is in flight? |
| 6 | The cloud seams | `packages/services` | What changes when we point at real Azure? |
| 7 | Tests & CI | `tests/` · `.github/workflows` | What does a green check prove, and what doesn't it? |
| 8 | The docs & agents system | `docs/` · `AGENTS.md` · `.opencode/` | Where does a decision live, versus a behavior, versus a procedure? |

## How to study

Your aspect has **six study questions** in
[expert-jigsaw-study-questions.md](expert-jigsaw-study-questions.md). Work
through them **in order**. They build up: first run it, then trace it, then
work out why, and finally an experiment you predict before you run it.

Two rules:

- **Check everything by running the code.** The mentor agent (ask it
  anything; it lives in `.opencode/`) and the READMEs are both fair sources,
  but neither one counts as true until you've run it yourself.
- **The last question in every set is an experiment.** Say your prediction
  out loud first, then do it. Being wrong is the useful part.

## What you hand in

**The teach-back**, in week 2, in class, in your pod, about 4 minutes. Walk
your pod through 2–3 of your six questions, whichever ones you pick. Expect
follow-up questions from the rest of the set. No slides. Your editor and the
running app are what you present. From week 2 through kickoff, you're the
first person people ask about this layer, first in your pod and then on the
team you join.

While you study, keep a list of every question you could only answer by
reading the source code, never from the docs. Each one of those is a gap in
the documentation. Bring the worst one to your teach-back. What you wish had
been written down when you started is the sharpest thing an expert can say
about their layer.
