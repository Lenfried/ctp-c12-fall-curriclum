# Code Kickoff Runbook — Week 3 Project Time

*This is the night your data model stops being a drawing. About 35 minutes of
project time, one shared screen per team, everyone's editor open.*

**The bar, said once:** by the end of tonight, your team's **first migration
is MERGED through the gate** and the app boots against your schema. That's it.
Seed data and first endpoints are this week's homework. If you get to them
tonight, you're ahead, not on schedule.

**What "blank" means:** your repo's `main` has an empty Prisma schema, just a
generator and a datasource, no models. Nothing gets replaced tonight;
something gets created. The full worked example lives on the course starter's
`example/todo` branch, the clone you made in week 1, if you want to see what a
finished schema looks like. That's what your jigsaw expert studied.

---

## Before class (strongly encouraged)

Turn your week-2 entity sketch into a draft `schema.prisma`, on a branch,
unmerged. Teams that show up with a draft spend tonight reviewing instead of
typing. Your data-layer expert from the jigsaw is the obvious person to drive,
and the design-review feedback from your TA is your punch list.

## The ritual (one driver, everyone reading)

**1 · Branch.**

```bash
git switch -c kickoff/schema
```

**2 · Write the schema.** Open `packages/db/prisma/schema.prisma` and turn
your sketch into models. The ground rules from the design review still apply:
every user-owned table carries the id of whoever owns it, name your relations,
put timestamps (`createdAt`/`updatedAt`) on everything, and start with fewer
models than you think you need. Migrations exist so you can add more next
week.

**3 · Generate the migration.** From `packages/db/`:

```bash
npx prisma migrate diff --from-empty \
  --to-schema-datamodel prisma/schema.prisma --script \
  > prisma/migrations/0001_init.sql
```

**4 · Read the SQL.** The whole team, on the shared screen, before you run
anything. This is tonight's real lesson: the migration *is* your schema,
written in the language the database speaks. Can you point at the line that
creates each table from your sketch? The line that enforces each relation?

**5 · PR it, review it, merge it.** Push the branch and open the PR. A
teammate who isn't the driver reviews it hunk by hunk. The checklist applies
to migrations too: pull it, run it, read it, ask one real question. ("Why is
this field optional?" is a good one.) Merge it through the gate. **Kickoff is
done when this PR is merged.**

**6 · While the review is fresh:** write section 4 of your team charter — what
blocks an approval, how fast people should respond to review requests, and
your comment conventions. The charter is this week's homework (see
[charter-guide.md](../charter-guide.md)). Ten minutes on section 4 tonight
will save you an argument in week 6.

## This week's homework

**The team charter** — the template, worked example, and how-to are all in the
repo root, and the whole thing gets merged into your team repo by the week-4
session.

Then the follow-through: the demo seed (it should be safe to run twice — model
it on the seed in the example branch) and your first scoped queries, each as
its own gated PR. By next session, Prisma Studio should show your product's
demo data.

## When it goes sideways (TA triage)

| Symptom | Fix |
|---|---|
| Migration SQL looks wrong or is missing a table | The schema and the sketch disagree. Fix `schema.prisma` and regenerate. Step 3 overwrites the file, which is fine before you merge. |
| `pnpm dev` fails to boot on a migration | Read the error; it names the SQL line. Usually it's a bad enum value, or a self-referencing relation missing `@relation` names. |
| Old example data still in the local db | Run `pnpm db:reset`, then restart dev. |
| Team is still arguing about the model at :20 | Merge the smallest version you can defend tonight, and model the entity you're arguing about next week as migration 0002. A small migration that ships beats a big one you're still debating. |
| Merged after class instead of during it | Fine. The bar is merged *this week*; tonight is just the target. Log it in the TA thread either way. |

## TA end-of-night checklist

- [ ] Every team has a `kickoff/schema` PR
- [ ] Merged, or a specific blocker logged in the TA thread with an owner
- [ ] Reviewed hunk by hunk by a teammate who wasn't the driver
- [ ] `/api/health` green against the new schema on at least the driver's machine
- [ ] Charter section 4 (review norms) drafted; the whole charter is due by wk 4
