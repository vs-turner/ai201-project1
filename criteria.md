# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---



## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**

**This is testing for 80% accuracy which is a good first benchmark.**

---



## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**

**This is essential to all RAG systems so it is applied 100% of the time.**

---



## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

**Why this target:**

**The performance of rejecting and not guessing is checked so it works most of the time, but the program still generally works if this does not function so 4 out of 5 is fine.**

---



## 4. Chunk size is reasonable

At least 4 of 5 times, the chunks contain the contents from no more than one document.

**Why this target:**

This target means that the chunking is not bridging multiple entries. This is not essential to performance but nice to have, so 4 out of 5 is the goal.

---



## 5. Citation is correct

Every single time, if there is a citation, the cited name of the corpus source matches the location of the text which is reproduced in the response.

**Why this target:**

Now the sources are not just included but correctly included. This should happen all of the time so 5 out of 5 is appropriate.

---

