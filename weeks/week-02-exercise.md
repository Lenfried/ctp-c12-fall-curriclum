# Week 2 Project Time — Your Product's Relations, on Paper First

*About 15 minutes in class, finished as part of this week's homework · your
team, one sheet of paper or one shared canvas · started the night your team
forms*

Your team just adopted a pitch. Before anyone types `schema.prisma`, draw what
the product actually is. Paper first, on purpose: it's faster to erase, easier
to argue with, and nobody gets attached to the first name that got typed.

---

## 1 · Nouns first

Say the product out loud in one sentence. It's on your adopted pitch.
Underline the nouns. Those are your candidate **entities**. Most products at
this stage have three to six. If you have more than eight, you're designing
v2, so cross some out. Save them for the week-9 pitch.

## 2 · One card each

For each entity, write its name (singular) and three to five fields you're
sure about. Skip timestamps and ids, since those come free. If you can't name
three fields, it might not be an entity. If one of your fields is a list, it
might be an entity itself.

## 3 · Draw the lines

Connect the entities that relate to each other, and label each line with how
many, in plain words: "a Trip *has many* Stops," "a Stop *belongs to one*
Trip." Every line has to survive being read out loud as a sentence that makes
sense.

The line everyone argues about is the most valuable one on the page. That
argument is a design review, happening early and for free.

## 4 · The ownership question

Circle the entity that answers: whose data is this? Almost every product ties
its data to a user or a team. One circle, one arrow from it to what it owns.
You already saw this rule in the starter, in the line that decides whose todos
a query returns. Your product has the same line, so draw it now.

## 5 · Predict one problem

Before you leave, each person names one place this model might be wrong: a
relation that could turn out to be many-to-many, an entity that might split in
two, a field that might need to be its own table. Write them in the margin.
You'll check them against real queries in week 3.

---

## Done means

A photo of the sheet posted in your team channel tonight. It doesn't need to
be right, it needs to exist. This week's homework — **the schema doc**, where
your entities become draft Prisma models and get PR'd into your team repo —
starts from this exact page, and the design review will look at both.
