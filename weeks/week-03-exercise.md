# Code Kickoff Runbook — Week 3 Project Time

*This is the night your data model stops being a drawing. About 35 minutes of
project time, one shared screen per team, everyone's editor open.*

**The bar, said once:** by the end of tonight, your team's **first migration
is MERGED**.

---

## Team coding! (One driver, everyone contributing)

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

**3 · Generate the migration.** From `packages/db/`. The skeleton doesn't have
a `migrations/` folder yet, so make one first:

```bash
mkdir -p prisma/migrations
npx prisma migrate diff --from-empty \
  --to-schema-datamodel prisma/schema.prisma --script \
  > prisma/migrations/0001_init.sql
```

**4 · Read the SQL.** The whole team, on the shared screen, before you run
anything. This is tonight's real lesson: the migration *is* your schema,
written in the language the database speaks. Can you point at the line that
creates each table from your sketch? The line that enforces each relation?

**5 · Run it.** From the repo root. Stop `pnpm dev` first if it's running.

```bash
pnpm prisma:generate     # regenerate the typed client
pnpm db:reset            # deletes .pgdata — local db starts over
pnpm dev                 # boot — the db-server applies migrations/ on startup
```

The db-server logs `applied migration 0001_init.sql`, and `/api/health` says
`db:"ok"`. It said that on the empty schema too, so the log line is your real
proof. To see the tables, from `packages/db/`:

```bash
DATABASE_URL=postgresql://postgres:postgres@127.0.0.1:5433/postgres npx prisma studio
```

Empty tables with your names on them. That's your product.

**6 · PR it, review it, merge it.** Push the branch and open the PR. A
teammate who isn't the driver reviews it hunk by hunk. The checklist applies
to migrations too: pull it, run it, read it, ask one real question. ("Why is
this field optional?" is a good one.) Merge it through the gate. **Kickoff is
done when this PR is merged.**

**7 · While the review is fresh:** write section 4 of your team charter — what
blocks an approval, how fast people should respond to review requests, and
your comment conventions. The charter is this week's homework (see
[charter-guide.md](../charter-guide.md)). Ten minutes on section 4 tonight
will save you an argument in week 6.

## This week's homework

**The team charter** — the template, worked example, and how-to are all in the
repo root. Put it up as a canvas in your team channel by the week-4 session.

**The reflection** — What are the advantages and disadvantages of using Prisma
instead of SQL to talk to the database?

**Watch ahead** — This week's watch-ahead playlist, plus the reflection.
