# Rederection 
---

#rederect #pipe #tee #output #input #errormesseges

---

## Examples 

To display command output to terminal, the **2>** sends the error messeges to the **/dev/null** directory, hence ingnoring the error messesges.

```bash
2>/dev/null
```

Sends the command output to **file**, **2>** the error messeges to **file2**.

```bash
>file 2>file2
```

Sends output and errors to the same **file**. 

```bash
&>file
```

Preserve existing file content, send output and errors to the same file

```bash
>>file 2>&1
```

Runs a command and sends everything, output and errors to the **/dev/null**.

```bash
&>/dev/null
```

Sends command to the terminal and to the file at the same time.

```bash
| tee file
```

Runs the command, saves output to **file** and discard the errors.

```bash
> file 2>/dev/null
```


