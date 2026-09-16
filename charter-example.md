# Team Charter — Night Shift *(worked example)*

*This is a finished charter for a made-up team, so you can see what "done"
looks like before you write your own (that's week 3's homework). Copy the
shape, not the answers. Your team's answers will be different, and they
should be. Blank version: [charter-template.md](charter-template.md) ·
How-to: [charter-guide.md](charter-guide.md).*

---

## 1 · Team & Project

**Team name:** Night Shift

**Project (the pitch we adopted):** StudyBuddy — spaced-repetition flashcards
for CUNY transfer-credit exams, built by the people who have to take them.

**Section:** Fri 6:30 · **TA:** Priya

**Members:**

| Name | GitHub | Email |
|------|--------|-------|
| Ada Lovelace (pitcher) | @adalovelace |
| Grace Hopper | @gracehopper | grace@… |
| Hector Garcia | @hgarcia | hector@… |
| Keyshawn Seymour | @kseymour | key@… |

### Roles & responsibilities

Roles rotate every week so nobody turns into "the person who always does
that." The **stand-up lead** runs Tuesday's 15 minutes and posts the notes.
The **review captain** is the first person to respond to any PR opened that
week. Anyone else can review too; the captain just makes sure nobody is left
waiting. The **demo owner** keeps `main` deployable and runs our status share
when it's our turn. Whoever has a role, has it. Swaps need a message in the
channel. The current rotation is in the pinned message.

Ownership that doesn't rotate (from the jigsaw): each member is the first
person to ask about their aspect. First to ask, not the only one allowed to
touch it. Anyone can change anything, but ask the expert before you rewrite
their layer.

Everyone, every week: one homework PR merged, one review given, and either
stand-up attended or an update posted in the channel before it starts.

## 2 · The Product

*From the pitch we adopted, sharpened as a team.*

**The problem:** Transfer students lose credits because the requirements are
spread across three CUNY sites and some out-of-date PDFs. There's also no
practice material for the placement exams that decide what transfers.

**Who it's for:** CUNY students planning a transfer. We're starting with
BMCC to Baruch business majors, which is Ada's own path, so we can test with
real people.

**Three core features (our MVP):**

1. Decks by exam — pick a target exam, get a deck put together for it.
2. Spaced review — cards come back on a schedule, and streaks are visible.
3. Share a deck — a read-only link you can send to a study partner or
   advisor.

**What ships by week 13 (demo day):** A stranger opens our URL, signs in with
GitHub, picks the "Baruch business transfer" deck, studies ten cards, closes
the tab, comes back the next day, and the app knows which cards are due.

**Out of scope, or ideas for v2:** cards written by users, a mobile app,
AI-generated decks, and any social features beyond the share link. These are
week-9 pitch material.

## 3 · Working Agreement

**Where we talk:** `#team-night-shift` in the course Slack. Decisions get a
📌. Everything else is allowed to scroll away.

**How fast we answer:** within 24 hours on weekdays, 48 on weekends. "Seen,
I'll answer tonight" counts as an answer.

**When we meet outside class:** Tuesday 8:00 pm stand-up, 15 minutes, hard
stop. Optional pairing block Thursday 7–8 pm for whoever is stuck.

**Availability notes:** Grace works Saturday and Sunday and is offline both
days. Hector is in Puerto Rico Oct 9–14 and can only work async. Keyshawn has
a Wednesday night class, so never schedule anything then. Ada gets up early;
message her before 10 pm or wait for the morning.

**How we decide when we disagree:** try to agree within ten minutes. If we
can't, we build the smaller version first and revisit it after it's merged.
Working code settles arguments faster than opinions do. Questions about
product scope go to Ada, since it's her pitch. Technical questions go to
whoever owns that layer.

**Definition of done:** merged into `main` through the gate, CI green,
reviewed by someone who pulled the branch and ran it, and working at the
preview URL. "Works on my machine" doesn't count.

### Rituals

| Ritual | When | What happens |
|--------|------|--------------|
| Stand-up | Tue 8:00 pm, 15 min | Each person says what's merged, what's in review, and what's blocked. Every blocker gets someone's name on it before we hang up. |
| Team review (in class) | Every session, about 15 min of project time | One person's PR on the screen, and the four moves: pull it, run it, read it, ask one real question. Comments get filed as actual review comments. |
| Async check-in | Thu, in the channel | One line each: what you're working on, and anything that's going to slip. This replaces a meeting, not a conversation. |
| Retro | Midterm (wk 7) and before demo day | 20 minutes of keep / stop / start. We edit the charter right there. That's the whole point. |
| Planning | Sunday night, async, 10 min | Next week's PRs claimed in the channel by name, one issue each. If you can't name your PR on Sunday, say that first at stand-up. |

We use GitHub issues as our board: one issue per PR, assigned to one person,
closed when the PR merges. If it isn't an issue, it isn't planned.

## 4 · Code & Review Norms

*Written together at the week-3 kickoff, right after our first migration
review.*

**How branches and PRs work:** `main` is protected. Branch off `main` as
`yourname/short-thing`, open a PR early (a draft is fine), and request the
review captain plus one other person. We squash-merge, and the PR title
becomes the commit message, so write it like one.

**What blocks approval:** the reviewer couldn't run it; a query that isn't
scoped to the current user; a migration that edits an earlier migration
instead of adding a new one; AI-generated code the author can't explain when
asked. Style never blocks. Leave a `nit:` and approve.

**How fast reviews get answered:** first response within 24 hours on
weekdays. If you can't review in time, say so in the PR so the captain can
send it to someone else. Silence is the only answer that isn't okay.

**Comment conventions:** `nit:` (take it or leave it) · `q:` (a real
question, answer it before merging) · `blocker:` (this has to change) ·
`praise:` (say what's good, so we all learn what to repeat). One `blocker:`
per real problem, not a pile of them.

## 5 · How We Use AI

**Course policy, not optional:** no AI-generated code gets merged unread.
Whoever opens the PR owns every line in it, no matter where it came from. If
AI explains something, check the explanation by running the code.

**How we use AI as a team:** as a partner while we build and as an explainer
we double-check. Every PR description says in one line which parts were
drafted by AI. That isn't a confession; it tells the reviewer where to slow
down.

**What we never hand to AI:** the schema and migrations (we type those by
hand, per kickoff), anything to do with user scoping, and reviews themselves.
A reviewer reads the diff, not a summary of it.

**What we build by hand first:** the first of each kind of thing. The first
endpoint, the first component, and the first test in a file get typed out. AI
helps with the second one.

## 6 · When Things Go Wrong

Stuck protocol (the course default): stuck for 15 minutes, post in the team
thread. Still stuck, bring it to stand-up. Still stuck, ask your TA, then go
to office hours.

**If someone can't deliver on time:** say so in the channel as soon as you
know. "I'm not going to make it" on Tuesday is a plan. Silence until Friday
is a problem. The review captain redistributes, the missed PR moves to next
week, and the person owes the captain a coffee, not an apology.

**If we have a conflict:** name it at stand-up, out loud and kindly. If it's
still there at the next stand-up, Priya mediates. If it's about product
direction, Ada decides and we move on.

## 7 · Commitment

We wrote this together, we mean it, and we'll look at it again at midterm and
change whatever isn't working.

| Signed | Date |
|--------|------|
| Ada Lovelace | Sep 18, 2026 |
| Grace Hopper | Sep 18, 2026 |
| Hector Garcia | Sep 18, 2026 |
| Keyshawn Seymour | Sep 18, 2026 |
