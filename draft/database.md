Database index format
=====================

Entries
-------

id
:   Primary key

folderID
:   ID of the containing folder

key
:   Key of the entry. Integer are padded with 0 until they are 10
    characters long, for sorting purposes.

scenarioID
:   ID of the scenario in which the Bell expression resides.

shortName
:   Optional short name of the Bell expression.

canonicalHash When the expression is canonical, contains a hash of the
coefficients of the Bell expression. Because the expression is
canonical, these coefficients are integers in the NP representation. The
low-order 32 bits of each coefficient are hashed using the
[Murmur3](http://code.google.com/p/smhasher/wiki/MurmurHash3) hash
function from Austin Appleby, ordered version, with initial seed
`0xFAAACE73`, as implemented in the standard Scala library.

oppositeHash
:   Hash of the coefficients of the minimal lexicographic representative
    of the opposite of the current Bell Expression. Computed as for
    `canonicalHash`.

firstPubID
:   ID of the first publication in which the Bell expression is
    referenced.

ioLifted
:   Is the expression an io-lifting ?

composite
:   Is the expression composite ?

Scenarios
---------

text
:   Text representation of the scenario using the `[(2 2) (2 2)]`
    notation.

numOfParties
:   Number of parties in the scenario.

minNumInputs
:   Minimal number of inputs per party.

maxNumInputs
:   Maximal number of inputs per party.

minNumOutputs
:   Minimal number of outputs per input.

maxNumOutputs
:   Maximal number of outputs per input.


