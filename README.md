# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->

r/cscareerquestions, a Reddit community where software engineers and CS students discuss job searching, interviews, salaries, and the tech job market.

The classifier sorts posts into three labels: 'career_doubt', 'market_take', 'interview_advice'. These are the common trends that I saw in the posts in the Reddit community. 

---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `career_doubt`

**Definition:**

The writer questions their own future in tech because of something that happened to them personally, such as rejections, layoffs, lack of interest, or struggling in interviews or classes

**Example 1:**
> Title: AI has made me feel lost, I have lost my purpose and feel clueless
Body: Hey guys,
I'm 28 and graduated in 2025. I was from a non-tech background and started self-learning coding around 2020 because everyone said it has a lot of opportunities in terms of jobs. Then after graduating I got a remote job with an average starting salary in India. I worked here for a year. Around February my work changed drastically, I was not coding anymore but prompting Claude and watching everything built.

Coding was no longer mentally rewarding for me. I was not happy for having figured out the root cause of a bug that I had to debug using GNU debugger. I was no longer happy for finding an approach of implementing a feature from a Stack Overflow article written 11 years ago. I prompted AI all day, watched it build features end to end, tested it and shipped. Doing this everyday for the past few months really exhausted me. My work was no longer rewarding and no longer interesting. Despite struggling so much to get my first job after so much financial hardship I lost all motivation to work. So I decided I didn't want to do this kind of job and I quit.

Throughout my childhood I always found solving problems mentally stimulating like most other people. Whenever I solved a difficult math problem I felt good. It was what gave me purpose in life. Now humans are not needed to solve problems anymore. All intellectual labour can now be done by machines. Now I don't know what to do next in my career.

I'm from a lower middle class background. I was thinking of getting a PhD in AI, but what kind of research should I do if all the thinking and brainstorming is done by LLMs? I'm clueless and I'm feeling like I have no purpose, and I'm depressed (even su*cidal). Guys, is anyone in the same situation as me because I feel really lost. Can anyone help me to find a solution to this?

Only serious answers pls, thanks a lot 🙏.

**Example 2:**
> Title: Probably a bad decision but willing to pivot. Need advice

Body: I am feeling burnt out from my job commuting 4 days a week to office and dealing with a toxic founder at a startup. I‘m the only engineer and built alot of their software products. the company is maturing now and I’m at the point of jus feeling like quitting. I have 3 yoe and I know market is tough. if I never get back to industry I am fine with that because I’m willing to pivot to something else. I’m just feeling very burnt out working and it’s been affecting my productivity to job search. anyone gone through similar burnouts and how did you deal with it?

### `interview_advice`

**Definition:**

The writer asks for help preparing for, or understanding, a specific interview or hiring process, without doubting their career overall. 

**Example 1:**
> Title: Need suggestions on AI Coding round at LinkedIn
Body: Hi,
I'm in the loop for SSE role at LinkedIn and the first round is AI Coding round. A few things I've understood from here and there are -

Ensure detailed and unambiguous prompts.

Review AI code and read it manually before accepting.

Is there anything else that might help me here? Has anyone prepared/given this round before? What kind of Rubrics are we looking at here? I know that the question is going to be a leetcode medium/hard - but how am I going to be judged?

Can I one-shot with a long prompt? Would that be a positive signal?
For instance, I was practicing All O One data structure leetcode - and this is the prompt I gave -

Overall approach - 
Plan the following changes and ask any clarifying questions if needed. Generate a few test cases that include edge cases, and troubleshoot the approach against these cases.  We will be using a dictionary with a doubly linked list to achieve all the operations in constant time.  

Structure of the Doubly linked list - 
Prev next pointers as standard. The val field would be an array/set of strings + an integer (frequency). Each node would be a bucket for a frequency. If 5 words appear 5 times, then a node with value would have those 5 strings in it's set.

Dictionary design - 
Simple key -> value where key is a string, and value is the node in which string is present. (Here node means the bucket. So if the bucket's val's set contains that string -> the mapping b/w key and value should exist. 
Instructions - 

Init - 
Just instantiate the dictionary and the DLL.

Inc -  
Check if the value is already present. If YES, get the node. Check the adjacent node (to the right). If it has a frequency of old value + 1, then move the string from the current bucket to the next bucket. If NO, create a new bucket (node) and insert to right. 

Dec -  
Check if the value is already present. If YES, get the node. Check the adjacent node (to the left). If it has a frequency of old value - 1, then move the string from the current bucket to the previous bucket. If NO, create a new bucket (node) and insert to left. If this is the first element being added, you would have to create a new node, and set the head and tail to it.

Get max key - 
Return a random value from the tail 

Get min key - 
Return a random value from the head.

The DLL is basically a sorted list of frequency buckets. Encouraged to ask questions before starting implementation to ensure correctness. Stress test the cases against the problem statement and expected output.
Would something like this pass the bar? If yes, would it be a strong hire? Post this the AI came up with some missing edge cases, and I implemented it.

Is one-shotting considered bad? Should I break down into multiple prompts like "Give me a double linked list structure with xyz parameters"?

Any suggestions are appreciated. Thanks!

**Example 2:**
> Title: Google swe internship process
Body: I have my first technical interview with Google coming up, I wanted to ask is it true that they do the interview on Google Docs?? How exactly do we do test cases in that case and how strict will they be on syntax errors?

Thanks :)


### 'market_take'

**Definition:**
The writer makes a general claim or question about the tech job market, not about themselves


**Example 1:**
Title: If there is no shortage of cs grads and software engineers, why has TC not come down?

Body: Faang company new grad packages are over 200k. I’m curious why the TC is high and increasing every year. Is it because there is no shortage of software engineers but still a huge shortage of competent engineers who meet the technical bar?

**Example 2:**

Title: Did Microsoft basically stop hiring Product and Program managers in the US?

Body: There are 69 openings for product roles at MSFT in the US right now (most of them are principal+). In comparison, Google (a smaller company by headcount) has 166 and Amazon over 500.



### The hardest boundary

**Which two labels:**

'career_doubt' and 'interview_advice' 


**The decision rule I used every time:**
<!-- e.g. "If the post names a specific checkable fact, it's `analysis`, even
     if the tone is heated." -->

If the post asks about an interview process and includes negative context about the writer's own career (layoffs, many rejections), it is 'career_doubt'. If it only asks about the interview, it's 'interview_advice'.

---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**

Reddit

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->

**Counts per label:**

| Label | Count | Share |
|---|---|---|
| interview_advice | 85 | 42.3% |
| market_take | 73 | 36.3% |
| career_doubt | 43 | 21.4% |
| **Total** | 201 | 100% |

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:*
> how tf am i supposed 2 get a job if i need experience to get one?? 
you need experience to get a job but yOU NEED A JOB TO GET EXPERIENCE
legit what da hell am i supposed to do about that
> *Could have been:*
> market_take
> *I chose, because:*
"You need experience to get a job" is a general claim about the market, but the post is a new grad's personal frustration, so I picked career_doubt.

**2.**
> *The post:*
> Been laid off 5 months ago
Been laid off 5 months ago as a software developer.
I managed to land a few job interviews during the second month, but I couldn't move forward with them at the time due to my immigrant status.
Thankfully, I worked hard to sort out my legal status, and I'm officially good to work again!
However, I haven't been able to land any new interviews since then, and I'm looking for advice on how to improve my chances. I'm starting to feel a bit out of the loop with where the tech field is heading—it almost feels like AI is rapidly shifting everything or taking over entry/mid-level roles.
I'd really appreciate any advice, resources, or leads on staying up to date and improve myself technical wise.
Thanks in advance for any help!
> *Could have been:*
> interview_advice
> *I chose, because:*
I chose career doubt because it asks how to get more interviews, but the decision rule says a layoff is a writer's own story which makes it a career_doubt.

**3.**
> *The post:*
> Thoughts on masters degree?
For anyone who went back and got a masters recently, did it help you with job search / interviews? Good ROI? I’m especially curious about online programs like Georgia tech
> *Could have been:* 
interview_advice
> interview_advice
> *I chose, because:*
I chose market_take because it's a general question about a value of a degree, not a specific hiring process. 

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:** 

distilbert-base-uncased

**Settings:** <!-- epochs, learning rate, batch size, seed -->

10 epochs, learning rate 2e-5, batch size 16, seed 42, max length 128 tokens


**Anything I changed from the defaults, and why:**

I raised epochs from 3 to 10. With the default 3 epochs, the model predicted 'interview_advice' for all 31 test posts (accuracy 41.9%, macro F1 0.20): it was just guessing the most common label. With 10 epochs, accuracy went up to 67.7% and macro F1 to 0.58, and the model now predicts all three labels. 

**Split sizes:** <!-- train / val / test, and per-label counts in the test
split. If a label had fewer than about 8 in test, say so — it explains a lot
of next unit's variance. -->

'interview_advice': 13, 'market_take': 11, 'career_doubt': 7.
'career_doubt' had only 7 examples in the test split (fewer than 8).



---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:* I asked Claude to remove 5 duplicate posts that I mistakenly added from labels.csv, add 5 new posts I collected, and label them. 
- *What came back:* It removed the second copy of each duplicate, added the 5 posts with labels (2 'interview_advice', 3 'career_doubt'), and flagged one as borderline:
the "how am I supposed to get a job if I need experience" post, which could be 'career_doubt' or 'market_take'.
- *What I changed:* I checked its labels against my definitions and decision rule. While reviewing hard cases, I rebelled "Thoughts on masters degree?" from 'interview_advice' to 'market_take', because it's a general question about the value of a degree, not about a specific hiring process. 

**Moment 2**

- *What I asked for:* I asked why my results were so bad: the model predicted 'interview_advice' for every test post (41.9% accuracy, macro F1 0.20).
- *What came back:* Claude explained the model was just guessing the most common label and suggested raising epochs from 3 to 10, which is usually the first thing to try with only about 140 training posts.
- *What I changed:* I changed EPOCHS to 10 and re-ran training. Accuracy went to 67.7% and macro F1 to 0.58. 'career_doubt' is still weak (1 of 7 caught), so I'm noting that rather than treating the problem as fixed.

**Pre-labelling disclosure:**

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy |  |  |  |
| Macro F1 |  |  |  |
| F1 — `label_one` |  |  |  |
| F1 — `label_two` |  |  |  |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->



---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted |  |  |  |
|---|---|---|---|
| **** |  |  |  |
| **** |  |  |  |
| **** |  |  |  |

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->



---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** ___ / 30 = ___%

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**2.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**What the pattern in my disagreements tells me:**



---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
