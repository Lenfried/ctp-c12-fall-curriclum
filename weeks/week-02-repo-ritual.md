# The Team Repo Ritual — exact clicks

*Week 2 project time · about 30 minutes · one repo per team, created the night
your team forms, and used for the whole semester. From tonight on, homework
lands here as PRs. At week-3 kickoff your schema lands in the blank skeleton.
This same repo deploys in week 10 and demos in December.*

---

## 1 · Create the repo (one member drives, screen shared)

1. Open the course template: `⟨github.com/…/starter⟩`
2. Click the green **Use this template** → **Create a new repository**
3. **Owner:** the driving member's account. **Name:** your team name in
   kebab-case, like `night-shift-app`
4. Visibility: **Private** → **Create repository**

Your new repo is the **blank skeleton**: default branch only, empty schema,
all the infrastructure. That's what it should be. The worked example
(`example/todo`) stays upstream in the course starter repo, which everyone
cloned in week 1's study hall. That clone is your jigsaw study copy.

## 2 · Add your people

**Settings → Collaborators → Add people:**

- every teammate, with the **Admin** role
- the instructor and your section's TAs, so we can see your work. Not to grade
  it — there are no grades.

## 3 · Protect main — the merge gate

**Settings → Branches → Add branch protection rule**, pattern `main`:

- ☑ **Require a pull request before merging**
- ☑ **Require approvals**, set to **1**

That's the whole gate, and it does more than it looks like. GitHub won't let
you approve your own PR, so "1 approval" really means "a teammate read your
code." You can't self-merge, by design. **Homework counts when it's MERGED**,
which means it was reviewed. That holds all semester.

## 4 · Everyone: clone

Every member, on their own machine:

```bash
git clone ⟨your-team-repo⟩ && cd ⟨your-team-repo⟩
```
