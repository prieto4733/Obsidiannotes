# Special Characters

---

#script #comment #semicolon #dot 

---


## The comment symbol

To write a comment for a bash script, this is the symbol.

```bash
# This is a comment
```

There is a few rules and ways you can write a comment.

```bash
# of course you can start the line with a comment

		# you can start the line with white space and then the comment

systemctl status httpd # the comment can start after a command 

man magic | grep 'symbol' # this is a comment
#                   ^ you can have space between the comment 

# but you cant neve have a comment before the command  grep 'worng_comment'
```


### When this symbol is not a comment

There is a few places where this simbol is not translated as a comment. Of course the [[Shibang]] has the comment simbol but is not translated as a comment.

```bash
#!bin/bash

echo ${PATH#*:}       # Parameter substitution, not a comment
echo $(( 2#101011 ))  # Base conversion, not a comment

```

## Command Separators 

To separate commands that are written in the same line we use a [[semicolon]]

```bash
#!/bin/bash
#command separator

echo hello; echo world

if [ -x "$filename" ]; then   # Note the space after the semicolon
#                    ^^

  echo "File $filename exist."; cp $filename $filename.back
else. #                       ^^
  echo "File $filename not found"; touch $filename
fi; echo "File test complete"
```

Double semicolon is used as a case terminator

```bash
#!/bin/bash
#case terminator

case $variable in
   abc) echo "\$variable = abc" ;;
   xyz) echo "\$variable - xyz" ;;
esac
```

### Dot

The dot is a bash builtin, it is used for the file system specifics. It is used to hide a file by starting the filename with a dot. Also it is used to determine what directory you are working with

```bash

ls .  # This is used for the current working directory
ls .. # This is used for the parent directory
```

