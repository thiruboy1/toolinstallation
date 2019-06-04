# To change password for script.
```sh
#!/bin/sh
for i in `more userlist.txt `
do
echo $i
echo $i"123" | passwd –-stdin "$i"
echo; echo "User $username’s password changed!"
done
```

# Linux Command  numbers the lines in a file.
```sh
nl [OPTION]... [FILE]...
nl test.txt
```

# To WHAT CAN WE DO WITH AWK ?
```sh
1. AWK Operations:
(a) Scans a file line by line (b) Splits each input line into fields (c) Compares input line/fields to pattern (d) Performs action(s) on matched lines

2. Useful For: 
(a) Transform data files (b) Produce formatted reports

3. Programming Constructs: 
(a) Format output lines (b) Arithmetic and string operations (c) Conditionals and loops
eg: awk '{print}' employee.txt
    awk '/manager/ {print}' employee.txt 
    awk '/manager/ {print}' employee.txt 
    ```
