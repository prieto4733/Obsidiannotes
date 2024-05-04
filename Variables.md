# Variables 
---
#variables 

---
## Variables
To write variables in bash, start by name=value no spaces in between, if bash is reading from input give the command "read name" with a space in between. 
To call variables, we give the $ sign and the name of the variable: 

### Simple variable 
```bash
myname=Danny
echo $myName
```

### Read input variable
```bash
echo "What is your age? " 
read age 
echo "What is your name? " 
read name 
echo "You are $name and you are $age years old." 
```

This variable has a value of a string and we can use numbers also without the double quotation marks. 
 
To capture a command output as the value for the variable: 

```bash
myDirectory=$(ls)
```

Using the dollar sign and the parentesis and the command we whant the output for (called a subshell), we give the variable the values of the commands output. 
When you write the names of variables, remember that the enviroment variables are writen in upper case, so always write them in lowercases so you dont get confused 
