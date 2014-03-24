Scenarios and parties
=====================

Bell experiments are performed using several observers, called parties. These parties are often numbered and named alphabetically Alice, Bob, Charlie and so on. A sequence of parties is a Bell scenario.

A party is unambiguously described by a sequence giving the number of outcomes for each measurement settings.

A scenario can be represented in plain text using the following grammar:

- ``Scenario := [Party Party ... ]``
- ``Party := (Input Input ...)``
- ``Input := number >= 2``

Examples:

- the CHSH scenario is written down ``[(2 2) (2 2)]``,
- the Sliwa scenario is written down ``[(2 2) (2 2) (2 2)]``,
- the I2233 scenario is written down ``[(3 3) (3 3)]``,
- the I3322 scenario is written down ``[(2 2 2) (2 2 2)]``.

In the FaacetsPaper_, we introduced the following notation: :math:`[(k_{11} k_{12} \ldots k_{1 m_1})~(k_{21} k_{22} \ldots k_{2 m_2}) \ldots (k_{n 1} k_{n 2} \ldots k_{n m_n})]`, with :math:`m_i \ge 1` is the number of measurement settings for the :math:`i^\text{th}` party and :math:`k_{i j} \ge 2` is the number of measurement outcomes for the :math:`j^\text{th}` measurement setting of the :math:`i^\text{th}` party.

.. _FaacetsPaper: http://www.arxiv.org

Canonical parties
-----------------

Notice that parties ``(3 2)`` and ``(2 3)`` have essentially the same measurement structure up to a reordering to measurement settings. We thus define a party as canonical when the number of outcomes for successive measurement settings is non-increasing.

Thus, the canonical form of ``(2 3)`` is ``(3 2)``.

Canonical scenarios
-------------------

Notice also that scenarios ``[(2 2) (3 3)]`` and ``[(3 3) (2 2)]`` are identical under reordering of parties. We thus prescribe that a scenario is canonical when its parties are themselves canonical and ordered lexicographically: for all successive non-identical parties :math:`i` and :math:`i+1`, there is a :math:`j \ge 0` such that :math:`\forall k < j` we have :math:`k_{i k} = k_{i+1, k}` and :math:`k_{i j} > k_{i+1, j}`. For these ordering purposes, we define :math:`k_{i j} = 0` for :math:`j > m_i`.
