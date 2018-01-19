+++
date = "2018-01-11"
description = "Python cheat sheet for biology"
draft = true
tags = ["python", "cheat sheet"]
title = "Python commands useful in biological data analysis - 2"
topics = ["Bioinformatics"]
+++

#### Opening external files

As you can imagine, sequence data is not as small as depicted in examples of series 1. It is usually in files of specific formats and the file sizes are huge (in GB). So, it makes perfect sense to have a way of reading in these huge files to work on the data.

Usually, the sequence data i.e., DNA or protein sequence is present as a text in files. The file might also contain other parameters like - sequencing reads, quality scores, SNPs, phylogenetic trees, read maps, geographical sample data, genetic distance matrices. Python can be used to manipulate/analyze all this data.

```Python
#This can be done by these simple commands
sequence = open("mydna.txt")
seqcontents = sequence.read()
print(seqcontents)

# This can also be done by including another step and it will be useful if we need to use the filename again in the same program.
filename = "mydna.txt"
sequence = open(filename)
seqcontents = sequence.read()
print(seqcontents)
```
It is important to remember these steps when inputting the file.
1. Assign the name of the file as a string to the function **open()** or assign the file name as a string to a variable and then open it using function **open()**.
2. Read the contents of the file by using the **.read()** method on the file
3. Only now we can use the content of the files.

**NOTE**
If you try to print the contents right after using the open function or if you try to use the **.read()** method on filename before opening the file, you would get an error.

#### Optional arguments:

For the open() function, there are several options that are essential to keep in mind to work with external files.

1. If you don't specify any argument, the **open()** method takes the argument - **"r"** as a default. This indicates "read" and with this argument, you can only open the file to read the contents.
2. Another possible argument is **"w"** which indicates "write" and is used to write content into the file. Important thing to remember here is that this argument overwrites the existing contents of the file. If there is no file with specified filename, this argument creates a new file with that name.
3. Final argument we should discuss about is **"a"** indicating "append" and this is used to add content to the file without overwriting the content already in the file.

**NOTE** Both the arguments **"w"** and **"a"** will create a new file if a file doesn't already exist with that file name.

```Python
# Examples of usage of the arguments with the file "mydna.txt"

filename = "mydna.txt"

#reading
read = open(filename, "r")
#writing
write = open(filename, "w")
#appending
append = open(filename, "a")
```
#### Writing content to the file:

After opening the file with write argument, the method **.write()** should be used to write content into the file.

```Python
# Using the same filename as above
write.write("ATTGCTGA")
```

#### Closing the files:

Finally, after you have worked with the files as you intended to, it's important to close the file. This can be done using the method **.close()**.

```Python
# Using the same filenames as above
read.close()
write.close()
append.close()
```

### Summary:

When dealing with external files, it's important to do these in this order. This might be a little over-simplification but these are important to remember.
 
1. Assign the name of the file as a string to a variable (Optional but recommended).
2. Open the file using the function - **open()**
3. Read the contents of the file using the method - **.read()**
4. Write contents onto the file using the method - **.write()**
5. Close the file using the method - **.close()**
