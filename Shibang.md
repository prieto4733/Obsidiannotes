# SHIBANG

---

#shibang #script #bash #comments #comment 

---

### What is the Shebang

This is the part of the script that will invoke the translator to run the command.

```bash

#!

```

It is written at the first line and the first two simbols are the bits that will run the translator.
Then the path of the translator need to be given without no errors.

```bash
#!bin/bash
```


### Different types of translators or shells

The script is not only for the bash shell but it could be written for multiple types of translators. 

```bash
#!bin/sh       # This is for the default shell translator for your system
#!bin/bash.    # Of course the bash shell
#!bin/sed -f.  # This is for SED to translate 
#!bin/awk -f   # This is for AWK
#!urs/bin/perl # For perl to compile
```

> Note that the # in the begining of the line is not a #comment	 