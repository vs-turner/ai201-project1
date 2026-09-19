# The Unofficial Guide

> **This file is your submission.** Fill it in as you go — most sections get
> written during the milestone that produces them, not at the end.
>
> How the starter works, and every command you'll need, is in `RUNNING.md`.
> Leave that file alone.
>
> **Paste everything as text.** No screenshots, no video. A typed table gets
> full credit; a picture of the same table gets none.
>
> Delete these instruction blocks as you replace them. The `<!-- -->` comments
> are notes to you and don't show up when the page renders — you can leave them
> or remove them.

---

# Unit 1

## What This Does

I picked the campus life corpus because it seemed like a large, realistic database similar to a wiki or reddit forum. The system answers concrete questions about student life with specific details to a campus like dining hall wait times and hours, dorm laundry costs etc. If a question is clearly outside that world, the system is now tuned to refuse the question instead of guessing.

## Chunking Strategy

**Chunk size:** 6 lines
**Overlap:** none

```
 I chose 6 lines because most docs composed of 2 or 3 paragraphs (with an extra gap line in between) so 6 newline characters will catch most of these. Tehre were a few with 4 paragraphs (8 newlines) but I'm testing as is for now.
```



## Sample Chunks

**Chunk 1** — source: `admin_add_drop_deadline.txt#0` — produced by: `chunker.py::split_documents`

```
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

**Chunk 2** — source: `course_biol_160_workload.txt#0` — produced by: `chunker.py::split_documents`

```
Workload for BIOL 160 Cell Biology

People keep asking so: 9 to 11 hours a week, the heaviest first-year course by reputation. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

**Chunk 3** — source: `course_hist_118_workload.txt#0` — produced by: `chunker.py::split_documents`

```
Workload for HIST 118 Modern World History

People keep asking so: a lot of reading, about 120 pages a week, but no problem sets. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

**Chunk 4** — source: `dining_pellew_dining_hall_followup.txt#0` — produced by: `chunker.py::split_documents`

```
Re: Pellew Dining Hall

Adding to what people have said about Pellew Dining Hall. The wait figure of 12 to 18 minutes at peak matches what I've seen. If you're trying to eat between classes, go before 11:45 and it's a different building entirely.

Also worth saying: the furthest hall from anywhere, next to the athletics centre. Nobody tells you this at orientation.
```

**Chunk 5** — source: `housing_innisfree_hall.txt#0` — produced by: `chunker.py::split_documents`

```
Innisfree Hall — what it's actually like

Transferred in last year, so take this with a grain of salt. Built 1991, renovated 2022. Rooms are doubles arranged as pairs sharing one bathroom between two rooms.

The good: the shared-bathroom-between-two-rooms arrangement is the best compromise on campus.
```



## Sample Answer

**Question:** When is the deadline for dropping a course before it becomes a W?

**Answer:**

```
(best distance 0.213, cutoff 0.6)

The deadline for dropping a course before it shows as a W on your transcript is the end of the second week (admin_add_drop_deadline.txt).

Sources retrieved: admin_add_drop_deadline.txt, admin_declaring_a_major.txt, admin_grade_appeals.txt, admin_pass_fail_option.txt, admin_withdrawal_deadline.txt
```

**My relevance cutoff:** 0.6

In-corpus best distances were 0.19–0.29 from my sampling while out-of-scope were 0.82–0.93. The gap is somewhat wide already, so I kept the starter cutoff of 0.6 roughtly in the middle. A wider gap makes this easier to cut off when the question should be asked based on 0.6 cosine dissimilarity.


| Question                                                          | In corpus? | Best distance |
| ----------------------------------------------------------------- | ---------- | ------------- |
| What are wait times at Kestrel Commons between 12:15 and 1:00?    | Yes        | 0.2294        |
| What time does Halden Hall close on a weekday?                    | Yes        | 0.2948        |
| How late in the term can a student declare pass/fail for a class? | Yes        | 0.2732        |
| How much does it cost to do laundry at Calder Annexe?             | Yes        | 0.1917        |
| When is the deadline for dropping a course before it becomes a W? | Yes        | 0.2130        |
| What is the capital of Mongolia?                                  | No         | 0.8246        |
| How do I change the oil in a diesel engine?                       | No         | 0.9340        |
| Who won the 1994 World Cup?                                       | No         | 0.8859        |
| What is the recommended dosage of ibuprofen for a headache?       | No         | 0.8442        |
| How do I write a for loop in Rust?                                | No         | 0.8907        |




## How I Used AI

1. I asked for explanations of top k and what typical numbers are used in production. Now I know that top k retrieval plus cosine distance (or inversely, similarity) is used to decide whether a question can be answered direclty with a RAG database or not and determines in scope vs out of scope). Other additions that can be added are hybrid search (keyword search plus vector search) among other ideas which I don't yet understand (rerankers, calibrated scores, query rewriting, or learned gates).
2. I asked AI for a walk through of how cosine distance is used in production in combination with other methods, such as requiring the top few results to be close in score, or blending the score plus other metrics.

---



# Unit 2



## Run Log — Before


| Criterion                              | Target | Run 1 | Run 2 | Run 3 | Verdict |
| -------------------------------------- | ------ | ----- | ----- | ----- | ------- |
| 1. Retrieved chunk contains the answer | 4 of 5 |       |       |       |         |
| 2. Every answer names a source         | 5 of 5 |       |       |       |         |
| 3. Gate stops out-of-corpus questions  | 4 of 5 |       |       |       |         |
| 4.                                     |        |       |       |       |         |
| 5.                                     |        |       |       |       |         |




## Verdicts


| #   | Criterion | Verdict | How I decided |
| --- | --------- | ------- | ------------- |
| 1   |           |         |               |
| 2   |           |         |               |
| 3   |           |         |               |
| 4   |           |         |               |
| 5   |           |         |               |




## Diagnoses



## The Improvement

**What I changed:**

**Why I picked it:**

### Run Log — After


| Criterion                              | Target | Run 1 | Run 2 | Run 3 | Verdict |
| -------------------------------------- | ------ | ----- | ----- | ----- | ------- |
| 1. Retrieved chunk contains the answer | 4 of 5 |       |       |       |         |
| 2. Every answer names a source         | 5 of 5 |       |       |       |         |
| 3. Gate stops out-of-corpus questions  | 4 of 5 |       |       |       |         |
| 4.                                     |        |       |       |       |         |
| 5.                                     |        |       |       |       |         |


**Did it help?**

## What's Still Broken



## What I'd Do Differently

