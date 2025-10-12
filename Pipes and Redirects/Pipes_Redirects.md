🌀 Basic Linux Commands – Pipes and Redirects

Linux provides powerful ways to handle data flow between commands and files using pipes (|) and redirects (>, >>, <).

1️⃣ Pipes (|)
| Concept | Symbol | Description | Example                                                    |        |       |
| ------- | ------ | ----------- | ---------------------------------------------------------- | ------ | ----- |
| Pipe    |   '|'  |    '|'      | Pass the **output of one command** as **input to another** | `ls -l | less` |


Other Examples:
```
ps aux | grep ssh         # Find processes related to ssh

cat file.txt | wc -l      # Count number of lines in file.txt
```

2️⃣ Output Redirection
| Operator | Description                                     | Example                       |
| -------- | ----------------------------------------------- | ----------------------------- |
| `>`      | Redirect output to a file (overwrite if exists) | `echo "Hello" > file.txt`     |
| `>>`     | Redirect output to a file (append if exists)    | `echo "New Line" >> file.txt` |

Examples:
```
ls -l > listing.txt                  # Save directory listing to a file

echo "Another line" >> file.txt      # Append line to file
```

Tip: Use > when you want a fresh file, >> to add to existing file.

3️⃣ Input Redirection
| Operator | Description                           | Example               |
| -------- | ------------------------------------- | --------------------- |
| `<`      | Use a file as **input** for a command | `sort < unsorted.txt` |

Examples:
```
wc -l < file.txt      # Count lines from a file

```
4️⃣ Combining Pipes and Redirects

You can combine multiple commands to create powerful workflows:

| Command                                                    | Description                                                                |
| ---------------------------------------------------------- | -------------------------------------------------------------------------- |
| `cat file.txt \| grep "error" \| sort > errors_sorted.txt` | Chain commands: output of `cat` → filter with `grep` → sort → save to file |

🚀 Summary

Pipes (|): Pass output from one command to another

Output redirect (>, >>): Save command output to files

Input redirect (<): Feed file content into commands

Combine them to build powerful command chains for automation and data processing


