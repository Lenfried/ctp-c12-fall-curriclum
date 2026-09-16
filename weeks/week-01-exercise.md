# Week 1 Study Hall — Clone it. Run it. Start your aspect.

*About 55 minutes · in pods, but on your own machine*

---

## 0 · What you're cloning

The **course starter**, on its **`example/todo` branch**. It's the skeleton
plus one small, complete app that runs through every layer: username sign-in,
todos, image attachments, a thumbnail worker, and live notifications.

Your *team* repo comes next week, once teams form around the pitches. That one
starts as the blank skeleton with no example in it. This clone is yours to
break, and it's also your **jigsaw study copy** for this week's homework, so
hang onto it.

```bash
git clone https://github.com/CUNYTechPrep/ctp-starter.git starter && cd starter
git switch example/todos
```

## 1 · Get it running (the health check)

```bash
pnpm install
pnpm prisma:generate     # builds the typed database client
pnpm dev                 # web + YOUR OWN Postgres server + Azurite
```

Then, in a **second terminal**:

```bash
pnpm db:migrate             # creates users @ada and @grace with starter todos
```

Stuck on any of this? You're not behind. Week 1's study hall is partly there
to sort out install problems. Flag a TA right away. Nobody leaves tonight
unable to run the app.

## 2 · Prove it runs

- Open `http://localhost:3000`. You didn't ask for `/login`, but that's where
  you end up. Remember that. Someone in your pod owns "the request path" for
  homework.
- Sign in as `ada`. Her todos are there because you seeded them. The data came
  from your own database server, the one `pnpm dev` started.
- Open `http://localhost:3000/api/health` and read the JSON. Both of the
  things it reports will matter later.

## 3 · Change one visible thing

Find any string or color in `apps/web`, like a heading or a button label.
Change it, save, and watch the browser update. It's a trivial change on
purpose. You've just proven the whole loop works on your machine — editor to
dev server to browser — and you now know at least one file that's really the
UI.

## 4 · Start your aspect (the rest of the block)

Open your aspect's six study questions in
[expert-jigsaw-study-questions.md](../expert-jigsaw-study-questions.md) and
start working through them **in order**, right now, while the instructor and
your pod are still in the room. A realistic target for tonight is the first
question or two, the "run it" ones. The reason to start here instead of at
home is that the first confusion hits while you can just ask someone.

Two habits to start practicing at question one:

- **Check everything by running the code.** The mentor agent and the READMEs
  are fair sources, but neither counts as true until you've run it yourself.
- When you get stuck, write down what you predicted and what actually
  happened before you ask anyone. That sentence *is* your question.

---

## This week, at home (part of your jigsaw study)

Two experiments from tonight's demo, before you get to your deeper questions.
Both are predict-first:

- **Stop the database.** Write your prediction first, both parts: what will
  the todo page show when the database is down, and what will `/api/health`
  say? Then `Ctrl+C` the `pnpm dev` terminal, start only the web app with
  `pnpm dev:web`, and load both URLs. Was the failure honest? Did it tell you
  what was actually wrong, in plain words? Restore with `Ctrl+C` and
  `pnpm dev`.
- **Trace the seed.** Where does `pnpm db:seed` get its data? Follow the trail
  from the root `package.json` to the actual rows. Then predict what happens
  if you run it a second time. Run it, and find the reason in the code. Users
  and todos are protected from duplication in two different ways. Name both.

## Done early? (stretch)

- Sign in as `grace`. Different todos. Find the line of code that decides
  whose todos a query returns. That's the most important rule in the app.
- Start the background half. Run `pnpm worker` in a third terminal, attach an
  image to a todo, and watch it go: queued, processing, toast. No refresh, no
  polling. Someone in your pod is about to become the expert on how that
  works.

## Done means

You ran the app, changed it, and started your aspect's study questions.

Before week 2: the two at-home experiments, your aspect studied and ready for
the teach-back, and **your pitch plus your choices in the project interest
spreadsheet**.

If any step still fails on your machine, tell a TA **before you leave
tonight**.
