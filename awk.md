# AWK in Linux

## 1. What is AWK?

AWK is a powerful text-processing tool in Linux/Unix used to search, filter, extract, and manipulate data from files.

It is especially useful for:
- Reading CSV files.
- Extracting specific columns.
- Filtering rows based on conditions.
- Performing calculations.
- Formatting output.
- Processing logs and command output.

## 2. Basic Syntax

```bash
awk 'pattern { action }' filename
```

Explanation:

| Component | Meaning |
|----------|---------|
| `awk` | Command |
| `pattern` | Condition to match |
| `{ action }` | Operation to perform |
| `filename` | Input file |

Example:

```bash
awk '{ print $1 }' data.txt
```

This prints the first field of every line.

## 3. Understanding Fields in AWK

AWK automatically divides each line into fields using whitespace as the default separator.

Consider `students.txt`:

```text
101 Neha 85
102 Rahul 90
103 Amit 75
104 Priya 95
```

Important AWK variables:

| Variable | Meaning |
|----------|---------|
| `$0` | Entire current line |
| `$1` | First field |
| `$2` | Second field |
| `$3` | Third field |
| `$NF` | Last field |
| `NF` | Number of fields in current line |
| `NR` | Total record number (line number across all files) |
| `FNR` | Record number within the current file |
| `FS` | Input field separator |
| `OFS` | Output field separator |
| `RS` | Input record separator |
| `ORS` | Output record separator |

Example:

```bash
awk '{ print $2 }' students.txt
```

Output:

```text
Neha
Rahul
Amit
Priya
```

## 4. AWK Examples

### Example 1: Print entire file

```bash
awk '{ print $0 }' students.txt
```

Output:

```text
101 Neha 85
102 Rahul 90
103 Amit 75
104 Priya 95
```

Equivalent to:

```bash
cat students.txt
```

### Example 2: Print a particular column

```bash
awk '{ print $2 }' students.txt
```

Output:

```text
Neha
Rahul
Amit
Priya
```

Print ID and marks:

```bash
awk '{ print $1, $3 }' students.txt
```

Output:

```text
101 85
102 90
103 75
104 95
```

### Example 3: Print the last column

```bash
awk '{ print $NF }' students.txt
```

Output:

```text
85
90
75
95
```

Here:
- `NF` represents the number of fields.
- `$NF` represents the value of the last field.

### Example 4: Print line numbers

```bash
awk '{ print NR, $0 }' students.txt
```

Output:

```text
1 101 Neha 85
2 102 Rahul 90
3 103 Amit 75
4 104 Priya 95
```

### Example 5: Print only a specific line

Print the second line:

```bash
awk 'NR == 2 { print }' students.txt
```

Output:

```text
102 Rahul 90
```

Print lines 2 to 4:

```bash
awk 'NR >= 2 && NR <= 4 { print }' students.txt
```

### Example 6: Filter using conditions

Print students with marks greater than 80:

```bash
awk '$3 > 80 { print $2, $3 }' students.txt
```

Output:

```text
Neha 85
Rahul 90
Priya 95
```

Print students with marks less than 80:

```bash
awk '$3 < 80 { print $2, $3 }' students.txt
```

Output:

```text
Amit 75
```

## 5. AWK with CSV Files

Suppose `students.csv`:

```csv
ID,Name,Marks
101,Neha,85
102,Rahul,90
103,Amit,75
104,Priya,95
```

By default, AWK uses spaces or tabs as separators.

For CSV files, use `-F` to specify the field separator.

### Set field separator

```bash
awk -F ',' '{ print $2 }' students.csv
```

Output:

```text
Name
Neha
Rahul
Amit
Priya
```

Explanation:
- `-F ','` means comma is the field separator.
- `$2` means second column.

### Skip the header

```bash
awk -F ',' 'NR > 1 { print $2 }' students.csv
```

Output:

```text
Neha
Rahul
Amit
Priya
```

### Print students scoring above 80

```bash
awk -F ',' 'NR > 1 && $3 > 80 { print $2, $3 }' students.csv
```

Output:

```text
Neha 85
Rahul 90
Priya 95
```

Note: These simple examples assume CSV values do not contain commas inside quoted fields.

## 6. BEGIN and END Blocks

AWK has three important execution sections:

| Section | Meaning |
|---------|---------|
| `BEGIN` | Executed before reading input |
| Main block | Executed for every input record |
| `END` | Executed after all input is processed |

Example:

```bash
awk 'BEGIN { print "Student Details" }
     { print $2 }
     END { print "Completed" }' students.txt
```

Output:

```text
Student Details
Neha
Rahul
Amit
Priya
Completed
```

Uses:
- `BEGIN`: Initialize variables and print headings.
- Main block: Process each line.
- `END`: Calculate totals, averages, and print summaries.

## 7. AWK Arithmetic Operations

AWK supports arithmetic operations.

| Operator | Meaning |
|----------|---------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus |
| `++` | Increment |
| `--` | Decrement |

### Example: Calculate total marks

```bash
awk -F ',' 'NR > 1 { total += $3 }
END { print "Total:", total }' students.csv
```

Output:

```text
Total: 345
```

### Example: Calculate average marks

```bash
awk -F ',' 'NR > 1 { total += $3; count++ }
END { print "Average:", total/count }' students.csv
```

Output:

```text
Average: 86.25
```

### Example: Find maximum marks

```bash
awk -F ',' 'NR > 1 {
    if (!seen || $3 > max)
        max = $3
    seen = 1
}
END {
    if (seen)
        print "Maximum:", max
}' students.csv
```

Output:

```text
Maximum: 95
```

## 8. AWK Variables

You can create your own variables inside AWK.

```bash
awk '{ total = total + $3 }
END { print total }' students.txt
```

Output:

```text
345
```

Variables do not need explicit declaration.

Example:

```bash
awk 'BEGIN { a = 10; b = 20; print a+b }'
```

Output:

```text
30
```

## 9. AWK Conditions (if-else)

AWK supports `if`, `else if`, and `else`.

```bash
awk -F ',' 'NR > 1 {
    if ($3 >= 90)
        print $2, "Excellent"
    else if ($3 >= 80)
        print $2, "Good"
    else
        print $2, "Average"
}' students.csv
```

Output:

```text
Neha Good
Rahul Excellent
Amit Average
Priya Excellent
```

## 10. AWK Loops

AWK supports `for`, `while`, and `do-while`.

### For loop

```bash
awk 'BEGIN {
    for(i=1; i<=5; i++)
        print i
}'
```

Output:

```text
1
2
3
4
5
```

### While loop

```bash
awk 'BEGIN {
    i=1
    while(i<=5) {
        print i
        i++
    }
}'
```

Output:

```text
1
2
3
4
5
```

### Do-while loop

```bash
awk 'BEGIN {
    i=1
    do {
        print i
        i++
    } while(i<=5)
}'
```

Output:

```text
1
2
3
4
5
```

## 11. AWK with Regular Expressions

AWK supports pattern matching using regular expressions.

### Print lines containing Neha

```bash
awk '/Neha/ { print }' students.txt
```

### Print lines starting with 101

```bash
awk '/^101/ { print }' students.txt
```

### Print lines ending with 90

```bash
awk '/90$/ { print }' students.txt
```

### Case-insensitive matching

```bash
awk 'tolower($2) == "neha" { print }' students.txt
```

Output:

```text
101 Neha 85
```

## 12. AWK with Linux Pipes

AWK can process output from other Linux commands.

### Example: List files and print filenames

```bash
ls -l | awk '{ print $9 }'
```

Note: This works for simple filenames without spaces. It may not work correctly for filenames containing spaces.

### Example: Print running processes

```bash
ps aux | awk '{ print $1, $2, $11 }'
```

### Example: Find Java processes

```bash
ps aux | awk '/java/ { print $2, $11 }'
```

### Example: Print disk usage

```bash
df -h | awk '{ print $1, $5 }'
```

## 13. AWK Formatting

AWK supports `printf`, similar to C.

Example:

```bash
awk -F ',' 'NR > 1 {
    printf "%-10s %-10s %5d\n", $1, $2, $3
}' students.csv
```

Output:

```text
101        Neha          85
102        Rahul         90
103        Amit          75
104        Priya         95
```

Useful formatting:

| Format | Meaning |
|--------|---------|
| `%s` | String |
| `%d` | Integer |
| `%f` | Decimal |
| `%.2f` | 2 decimal places |
| `%10s` | String in 10-character width |
| `%-10s` | Left-aligned string |

## 14. Important AWK Commands Cheat Sheet

| Command | Purpose |
|--------|---------|
| `awk '{print}' file` | Print complete lines |
| `awk '{print $1}' file` | Print first column |
| `awk '{print $NF}' file` | Print last column |
| `awk '{print NR,$0}' file` | Print line number |
| `awk 'NR==2' file` | Print second line |
| `awk 'NR>1' file` | Skip first line |
| `awk '$3>50' file` | Filter based on third column |
| `awk -F ',' '{print $2}' file` | Use comma separator |
| `awk 'BEGIN{...}'` | Execute before input |
| `awk 'END{...}'` | Execute after input |
| `awk '/word/' file` | Search matching lines |
| `awk '{sum+=$1} END{print sum}' file` | Sum first column |

## 15. Difference Between AWK, SED, and GREP

| Tool | Main purpose |
|------|-------------|
| `grep` | Search text |
| `sed` | Modify or replace text |
| `awk` | Extract columns, filter rows, and calculate values |

Example using the same file:

### GREP

```bash
grep "Neha" students.txt
```

Search for Neha.

### SED

```bash
sed 's/Neha/NEHA/' students.txt
```

Replace Neha with NEHA in the output.

### AWK

```bash
awk '{print $2}' students.txt
```

Extract the second column.

## 16. Real-world Example: Movie Dataset

Suppose `movies.csv`:

```csv
Name,Year,Gross
MovieA,2020,100
MovieB,2021,200
MovieC,2020,150
MovieD,2022,300
```

### Total gross earnings

```bash
awk -F ',' 'NR>1 {sum += $3}
END {print sum}' movies.csv
```

Output:

```text
750
```

### Gross earnings by year

```bash
awk -F ',' 'NR>1 {year[$2] += $3}
END {
    for(y in year)
        print y, year[y]
}' movies.csv
```

Output (order may vary):

```text
2020 250
2021 200
2022 300
```

### Find movies with gross above 150

```bash
awk -F ',' 'NR>1 && $3>150 {print $1,$3}' movies.csv
```

Output:

```text
MovieB 200
MovieD 300
```

---

## 17. Important Points to Remember

- `$0` represents the entire line.
- `$1`, `$2`, `$3` represent individual fields.
- `$NF` represents the last field.
- `NF` represents the number of fields.
- `NR` represents the total record number.
- `FNR` represents the record number in the current file.
- `-F` is used to specify the field separator.
- `BEGIN` executes before processing input.
- `END` executes after processing input.
- AWK supports conditions, loops, arithmetic, arrays, and regular expressions.
- AWK is useful for processing CSV files and analyzing datasets.
