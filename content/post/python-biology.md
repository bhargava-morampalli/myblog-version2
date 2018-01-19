+++
date = "2018-01-11"
description = "Python cheat sheet for biology"
draft = true
tags = ["python", "cheat sheet"]
title = "Python commands useful in biological data analysis"
topics = ["Bioinformatics"]
+++


#### To convert characters of a string to upper and lower cases

Methods **.upper()** and **.lower()** are used on the variable to which the string is assigned

For example:
```python
sequence = "ATTCGTACTACTGACGT"
# to convert this string into lower cases
uppersequence = sequence.lower()
print(sequence)
print(uppersequence)

# result obtained
ATTCGTACTACTGACGT
attcgtactactgacgt
```
Similarly, this can be used vice-versa to convert from lower case to upper case.

#### To replace particular character(s) in a string with desired characters

Method **.replace()** is used for this purpose. This can also be used to replace bunch of characters together

```python
rna = "AUGGCUAACUGGUCAG"
# to replace U with a T for it's cDNA complement sequence
cdna = rna.replace("U", "T")
print cdna

#result obtained
ATGGCTAACTGGTCAG
```
Similarly, a block of characters can also be replaced using same syntax except to replace single characters in quotes with block of characters to be replaced followed by other block of characters in quotes

#### To extract part of a string/sequence either to print out or assign to a different variable

This can be done using simple slicing commands as depicted below

```Python
sequence = "ATTGCTAGC"
print(sequence[0:5])
print(sequence[6:])
print(sequence[3:7])

#result obtained
ATTGC
AGC
GCTA
```
Important things to remember here are:
1. Index of characters start from 0 through end (not 1)
2. Index should be included between square brackets
3. If starting(0) or ending is not specified i.e., left blank, python assumes from the start and to the ending respectively

#### Counting number of a specific nucleotide in a sequence and identify when it occurs first in a sequence

Counting can be done using the method **.count()** on the variable containing string of nucleotides where as the position identification can be done using the method **.find()**

Examples of using both methods is depicted below on the same string:
```Python
newdna = "ATGGCTTAAGCTGCAGTCGTAGCTGACGTGCA"
print("'A' content in the sequence is: " + str(newdna.count("A")))
print("'T' content in the sequence is: " + str(newdna.count("T")))
print("'G' content in the sequence is: " + str(newdna.count("G")))
print("'C' content in the sequence is: " + str(newdna.count("C")))

print("'A' occurs first in the sequence at the position: " + str(newdna.find("A")))
print("'C' occurs first in the sequence at the position: " + str(newdna.find("C")))
```

In the above example, usage of the methods was combined with the print statement to reduce the work and the output comes out beautifully as below:

```
#result obtained
'A' content in the sequence is: 7
'T' content in the sequence is: 8
'G' content in the sequence is: 10
'C' content in the sequence is: 7
'A' occurs first in the sequence at the position: 0
'C' occurs first in the sequence at the position: 4
```
