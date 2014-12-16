---
layout: page
title: Scenarios and parties
---

Bell experiments are performed using several observers, called parties.
These parties are often numbered and named alphabetically Alice, Bob,
Charlie and so on. A sequence of parties is a Bell scenario.

A party is unambiguously described by a sequence giving the number of
outcomes for each measurement settings.

A scenario can be represented in plain text using the following grammar:

-   `Scenario := [Party Party ... ]`
-   `Party := (Input Input ...)`
-   `Input := number >= 2`

Examples:

-   the CHSH scenario is written down `[(2 2) (2 2)]`,
-   the Sliwa scenario is written down `[(2 2) (2 2) (2 2)]`,
-   the I2233 scenario is written down `[(3 3) (3 3)]`,
-   the I3322 scenario is written down `[(2 2 2) (2 2 2)]`.

In the [FaacetsPaper](http://www.arxiv.org), we introduced the following
notation:
\\( (k\_{11} k\_{12} \ldots k\_{1 m\_1})~(k\_{21} k\_{22} \ldots k\_{2 m\_2}) \ldots (k\_{n 1} k\_{n 2} \ldots k\_{n m\_n}) \\) ,
with \\(m\_i \ge 1\\) is the number of measurement settings for the
\\(i^\text{th}\\) party and \\(k\_{i j} \ge 2\\) is the number of measurement
outcomes for the \\(j^\text{th}\\) measurement setting of the \\(i^\text{th}\\)
party.


Canonical parties
-----------------

Notice that parties `(3 2)` and `(2 3)` have essentially the same
measurement structure up to a reordering to measurement settings. We
thus define a party as canonical when the number of outcomes for
successive measurement settings is non-increasing.

Thus, the canonical form of `(2 3)` is `(3 2)`.

Canonical scenarios
-------------------

Notice also that scenarios `[(2 2) (3 3)]` and `[(3 3) (2 2)]` are
identical under reordering of parties. We thus prescribe that a scenario
is canonical when its parties are themselves canonical and ordered
lexicographically: for all successive non-identical parties \(i\) and
\\(i+1\\), there is a \\(j \ge 0\\) such that \\(\forall k < j\\) we have
\\(k\_{i k} = k\_{i+1, k}\\) and \\(k\_{i j} \> k\_{i+1, j}\\). For these ordering
purposes, we define \\(k\_{i j} = 0\\) for \\(j > m\_i\\).
