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
