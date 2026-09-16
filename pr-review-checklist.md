# PR Review Checklist v1

*You'll learn this in 10 minutes in week 2 and use it every week after. This
really is the whole checklist. v1 fits on an index card. The job-grade
version, with adversarial reading, subtle breakage, and AI hallucinations,
shows up in week 11.*

---

## The four moves

**1 · Pull it.** Check out the branch. Reviewing from the diff page alone is
guessing with a green button in front of you.

**2 · Run it.** Boot it, click the thing, hit the endpoint. Does it do what
the PR says it does? You're the first person to use this change.

**3 · Read it, hunk by hunk.** Run `hunk diff` against the base branch, and
use `[` and `]` to walk through it. Read **every hunk**. Approving means "I
read all of it," not "I read the interesting parts." If the author used an
agent, this is the point where "the agent wrote it" stops being an
explanation. You've read it now, so now two people own it.

**4 · Ask one real question.** Every review gets at least one comment that
isn't "LGTM." A real question is one you actually want the answer to: "what
happens if this list is empty?" or "why a string here and an enum there?" or
"I can't follow this function from its name — what does it do?" Not knowing
something is worth saying. "I can't follow this" is one of the most useful
comments a reviewer can leave.

## The ground rules

- **Comment on the code, not the person.** "This query isn't scoped" works.
  "You forgot to scope" doesn't. Same fact, but the first one is about the
  work.
- **Approving means you read every hunk and ran it.** Don't give your
  approval away for less than that. Your teammate is counting on it, since
  the gate means their homework can't merge without you.
- **Blocking is normal.** Requesting changes is a reviewer doing the job, not
  an insult. What counts as a blocker versus a nit goes in your team charter
  at kickoff.
- **Stuck for 15 minutes means ask**, and that includes reviews. If you can't
  tell whether a change is right, say so in the comments and pull in a
  teammate or a TA. A stuck review that stays silent blocks the author twice.
