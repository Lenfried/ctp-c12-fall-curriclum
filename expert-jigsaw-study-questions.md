# The Expert Jigsaw — Study Questions

One aspect per pod member. Between you, cover all eight (see
[expert-jigsaw.md](expert-jigsaw.md)).

Every question here is about the **course starter's `example/todo` branch**,
the clone you made in week 1's study hall. It's the skeleton plus one small
app (username sign-in, todos, image attachments, a thumbnail worker, live
notifications) that runs through every layer.

Work through your aspect's questions **in order**. They build up: first run
it, then trace it, then work out why, then break it. The rules:

- **Check everything by running the code.** The mentor agent and the READMEs
  are both fair sources, but neither one counts as true until you've run it
  yourself.
- **The last question in every set is an experiment.** Say your prediction
  out loud first, then do it. Being wrong is the useful part.
- **Gaps in the docs count as findings.** Any question you could only answer
  by reading source code is a documentation gap. Note the worst one and bring
  it to your teach-back.
- **Teach-back (wk 2, about 4 min):** walk your team through 2–3 of these,
  your choice, and expect follow-ups from the rest of the set.

---

## 1 · The request path (`apps/web`)

1. Open the app while signed out. What happens, and where in the code is that
   redirect decided? Then sign in and load the list. What files does that
   request touch, in order, from the browser to the database and back?
2. Where does the app decide what data to fetch, on the client or the server?
   How can you tell by reading the code?
3. What's the difference between a page and a route handler here? Which one
   serves `/api/health`, and why that kind?
4. What does a request see when the database is down? Try it: stop the
   database, load `/` and `/api/health`, and compare what each one tells you.
5. Why does `/api/health` exist at all? Who calls it besides you?
6. **Experiment:** rename a route folder. Predict what breaks first, the
   build or the request. Check, then put it back.

## 2 · The domain door (`packages/domain`)

1. Find the schema that validates creating a todo. `curl` a POST with an
   empty title. What exactly comes back, and with what status code? Where is
   that response shape decided, and why use one shape everywhere?
2. The schema lives in a package the browser could import. Where does it
   actually run today? What would you gain by also running it in the form,
   and what does the server-side check guarantee no matter what the form
   does?
3. Sign in as `Ada`, then as `ada`. One account or two? Find the single line
   that makes that true, and explain why that's validation's job rather than
   the login form's.
4. Only the web app is allowed to import this package. What problem does that
   boundary prevent? (The ADR index will point you at the reasoning.)
5. How does a query in this package know whose todos to return? What stops it
   from returning someone else's? Find the test that proves it.
6. **Experiment:** `curl` a PATCH with `{"done": "true"}`, a string instead of
   a boolean. Predict the status code and the body, then check.

## 3 · The data layer (`packages/db`, `apps/db-server`, `apps/migrate`)

1. What actually starts when `pnpm dev` starts "your own Postgres server"?
   Where does its data live on disk?
2. What are the three doors in the database client, and when do you use each
   one?
3. What happens to migrations when the app boots? And why is editing a
   migration that's already been applied never the right move? What would go
   wrong?
4. Run `pnpm db:seed` twice. Why didn't the second run create duplicates?
   Find the two different mechanisms that prevent it (hint: users and todos
   are protected in different ways).
5. Where does the connection string live? When this app points at a cloud
   database in week 10, what's the only thing that changes?
6. **Experiment:** delete `.pgdata/`. Predict the full recovery path,
   including what happens to your session cookie, then run it.

## 4 · Identity (`packages/auth`)

1. Where does `currentUserId()` get its answer? What writes that value, and
   when? Trace one sign-in from the form to the cookie landing.
2. There's no password. So what does signing in actually prove? This
   package's README insists on separating two ideas. Which of the two does
   the app have today?
3. What's the rule about client-supplied user ids anywhere in the app? Find
   one query that shows the rule in action.
4. Why does asking for another user's todo return 404 instead of 403? What
   would a 403 give away?
5. When real sign-in arrives in week 8, what changes and what stays exactly
   the same? Which seam absorbs the swap? Also, find the guard that keeps
   this version of sign-in out of production, and quote it.
6. **Experiment:** run the attack we're sanctioning. Sign in as yourself,
   edit the `session` cookie in devtools to another user's id, and refresh.
   Predict first: what will you see, and what will `curl` return for a todo
   id you don't own? Why is being someone else not the same as gaining more
   access than they have?

## 5 · The background half (`apps/worker`)

1. How does the worker find out there's work to do? Attach an image and trace
   the job from enqueued to done, naming every file it passes through.
2. Why is the worker a separate process instead of more code in the web app?
   What can it do that a request handler shouldn't?
3. What database does the worker talk to, and why does having a second client
   matter when it writes the thumbnail?
4. Attach an image while the worker is stopped. What does the UI tell you,
   and is it honest? What happens when the worker comes back, and where was
   the job waiting in the meantime?
5. A job fails halfway through, from a bad image or a crash. Read the
   worker's loop carefully. What does this design choose to lose, and what
   record does it leave behind? Would you make the same choice?
6. **Experiment:** kill the worker mid-job. Predict the state of the queue,
   the database, and the UI, then look at all three.

## 6 · The cloud seams (`packages/services`)

1. What is Azurite standing in for? What starts it, and where does its data
   live?
2. Trace an upload. Where do the bytes end up, and what goes into the
   database instead? Why are those two split? (An ADR has the reasoning.)
3. A thumbnail finishes and a toast appears, with no polling anywhere. Trace
   that notification backwards: toast, then SSE stream, then Postgres. What
   does `pg_notify` get you that a `setInterval` wouldn't?
4. State the seam pattern in one sentence. Then list every seam in the app:
   database, blob, queue, notify, identity. What's the environment variable
   that switches each one?
5. What breaks if Azurite isn't running, and how does the app tell you? Is
   the failure honest?
6. **Experiment:** stop Azurite mid-session. Predict which features fail and
   how loudly, then check.

## 7 · Tests & CI (`tests/`, `.github/workflows`)

1. What runs when you run `pnpm test`, and why doesn't it need a running
   database or emulator? What is PGlite doing here?
2. What exactly does CI run on every PR? When the check is red, where do you
   look first?
3. Find the integration test that proves users can't see each other's todos.
   What specifically would have to break in the app for that test to fail?
4. What does a green check not prove? Find one real behavior the test suite
   doesn't cover (the thumbnail pipeline is a good place to look).
5. "Tests that can't fail don't count." Pick a test, delete the behavior it
   tests, and run the suite. Did it fail? What did that tell you about the
   test?
6. **Experiment:** make the smallest code change you can that turns CI red.
   What does that tell you about where the gate actually is?

## 8 · The docs & agents system (`docs/`, `AGENTS.md`, `.opencode/`)

1. What are the four kinds of document, and what's the lifecycle of each?
   Which ones are you allowed to edit, and which ones never?
2. A PR changes a behavior. What's the rule about which document has to
   change in the same PR?
3. State the one-way linkage rule. If you wanted the history of a spec, where
   would you look?
4. What does AGENTS.md tell a coding agent that a README doesn't? Ask the
   `mentor` agent something about the repo. Can you tell which document its
   answer came from?
5. Which reviewer agent looks at changes under `docs/specs/`, and what would
   it flag?
6. **Experiment:** ask the mentor agent one question about a teammate's
   aspect, then check its answer by running code. Did it hold up? Bring the
   verdict to the roundtable.
