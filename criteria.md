# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** None are given. You've had two projects of
practice.

An acceptance criterion names a number. *"The model is accurate"* is an
opinion. *"Every label has an F1 of at least 0.60 on the held-out set"* is a
criterion.

Under each, write a sentence or two on **why that number**. A reason that says
something about your data or your taxonomy earns credit — *"I picked 0.60 F1
for `reaction` because it's my smallest label and I only have about 50
examples of it"*. A reason that could be attached to any project does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## Pick numbers you can defend

Not numbers that sound impressive. Three labels means a coin-flip guesser gets
about 33%, so a target of 0.40 is barely a target. Your number should sit
somewhere you'd honestly call useful.

**Cover at least three of these five areas.** They're here as prompts, not as a
form to fill in — a criterion that fits none of them is fine if it names a
number.

| Area | A question it could answer |
|---|---|
| Overall accuracy | How often does it need to be right to be worth using? |
| Per-label performance | Is one label allowed to be much worse than the others? |
| Balance | How lopsided can your label counts get before it's a problem? |
| Consistency | If someone else labelled the same posts, how often should you agree? |
| Confidence | Should a confident prediction be right more often than an unsure one? |

Two things worth knowing before you pick numbers, because both will affect
whether you hit them:

- **Your smallest label will have the jumpiest score.** If a label has 50
  examples, about 8 land in the test split. An F1 computed on 8 examples moves
  a lot between seeds. A target for that label should be looser than one for
  your biggest label, and saying so is a good reason.
- **Unit 6 tests across three seeds, and the target has to hold across all
  three.** A target of 0.65 against results of 0.71, 0.62, 0.68 is a **miss**.
  Pick with that in mind — it is stricter than it first sounds.

---

## 1. 

<!-- Your criterion. It must name a number. -->
Overall accuracy on the test set is at least 0.65 on all three seeds


**Why this target:**

With 3 labels, random guessing gets about 33%, so 0.65 is about double that. I didn't go higher because my test set is only about 25 posts, so one seed can lose a few points on bad luck. 


---

## 2.

<!-- Your criterion. -->
Each label ('career_doubt', 'interview_advice', 'market_take') has an F1 of at least 0.60 on all three seeds.


**Why this target:**
Accuracy can look fine while one label fails. In the practice run, one label scored 0.0. It's lower than criterion 1 because each label only has about 8 test posts, so one wrong post moves its F1 a lot. 


---

## 3.

<!-- Your criterion. -->
No more than 2 test posts that are really 'interview_advice' are predicted as 'career_doubt', on any seed.



**Why this target:**

This is my hardest boundary. Interview posts that mention layoffs are 'career_doubt', but plain interview questions aren't. If the model mixes these up often, my decision rule isn't working. 

---

## 4.

<!-- Your criterion. -->

Each label is at least 25% of my dataset


**Why this target:**
Most posts in r/cscareerquestions are 'career_doubt', so the other two will be rarer unless I go looking for them. Below 25%, a label has too few test posts for criterion 2 to mean anything. 


---

## 5.

<!-- Your criterion. -->
The model's most confident predictions are at least 15 points more accurate than its least confident ones on all three seeds.


**Why this target:**

Its confidence should mean something. In the practice run, it was about equally confident whether it was right or wrong (0.37 vs 0.35)


---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 6 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath, like this:

         ## 2. Every label performs acceptably

         The model performs well on all labels.

         **Why this target:** ...

         > **Revised in unit 6:** Every label has an F1 of at least 0.60 on
         > the held-out set.
         >
         > **Why revised:** "performs well" gave me nothing to check. I
         > couldn't produce a verdict from it at all.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "Overall accuracy of at least 0.65" → "at least 0.55", because
            0.65 turned out to be optimistic for 200 examples.

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
