# Bash Example 

---

#example #script #variables #hardvalues

---

### From simple to more complex

This script will be an example from a simple to a more complex and more functional script. The script cleans up files in /var/log

Example 1

```bash
#clean up
#run as root

cd /var/log 
cat /dev/null > messages
cat /dev/null > wtpm 
echo "Log files cleaned up"
```


Example 2 Same script but with more functionality

```bash
#!bin/bash
# proper header for bash script

# cleanup version 2

# Run as root
# Insert code here to print error messages and exit if not root.

LOG_DIR=/var/log
# variables are better than hard coded values
cd $LOG_DIR

cat /dev/null > messages
cat /dev/null > wtmp

echo "Logs cleaned up"

exit #   The right and proper method of "exiting" from a script
     #   A bare "exit" (no parameters) returns the exit status
     #+  of the preciding command
```

In this example, instead of a hard coded value, we use a variable for the path, and we give a proper method of exiting the script with an [[exit status]], no [[parameters]]

