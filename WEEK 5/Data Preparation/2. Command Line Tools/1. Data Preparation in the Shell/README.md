# Data Preparation in the Shell

This module demonstrates how **UNIX shell commands** can be used for fast and efficient **data preparation and analysis**. Shell tools are widely used in data science because they are lightweight, fast, and allow quick exploration of large datasets directly from the command line.

The exercise uses **Apache web server logs** from the site *s-anand.net* for April 2024 and processes them using various shell commands.

---

## Why Use Shell for Data Preparation

UNIX command-line tools are useful because they are:

- **Agile** – Commands give immediate results for quick exploration.
- **Fast** – Most tools are written in C and optimized for performance.
- **Flexible** – Commands can be chained together using pipes.
- **Widely Available** – Supported on Linux, macOS, and environments like Google Colab.

---

## Key Shell Commands Used

### 1. Download Data with `curl`

Used to fetch files from the internet.

Example:

```bash
curl --location --output s-anand-net-Apr-2024.gz <URL>
````

Options used:

* `--location` → follow redirects
* `--continue-at -` → resume downloads if interrupted
* `--output` → save file with a specified name

---

### 2. List Files with `ls`

Displays files in the current directory.

```bash
ls
ls -l
```

`-l` provides a **detailed listing**, including file size and permissions.

---

### 3. Decompress Files with `gzip`

The downloaded log file is compressed.

```bash
gzip -d s-anand-net-Apr-2024.gz
```

After decompression, the file expands significantly (compressed logs are much smaller).

---

### 4. Preview File Contents

Use `head` and `tail` to inspect parts of a file.

First 5 lines:

```bash
head -n 5 s-anand-net-Apr-2024
```

Last 5 lines:

```bash
tail -n 5 s-anand-net-Apr-2024
```

These commands help quickly understand the **structure of log data**.

---

### 5. Count Requests with `wc`

`wc` counts lines, words, and characters.

```bash
wc -l s-anand-net-Apr-2024
```

Result: ~208K web requests in April 2024.

---

### 6. Extract Columns with `cut`

Log files contain fields separated by spaces.

Example: extract **IP addresses (first column)**

```bash
cut --delimiter " " --fields 1 s-anand-net-Apr-2024
```

This prints all visitor IP addresses.

---

### 7. Sort Data

Sorting groups identical values together.

```bash
cut --delimiter " " --fields 1 s-anand-net-Apr-2024 | sort
```

---

### 8. Count Unique Entries

`uniq` counts repeated values.

```bash
cut --delimiter " " --fields 1 s-anand-net-Apr-2024 | sort | uniq -c
```

This shows **how many requests each IP address made**.

Sorting numerically reveals the most active IPs:

```bash
... | sort -n | tail
```

This identifies potential **bots or crawlers** sending large numbers of requests.

---

### 9. Search Logs with `grep`

`grep` searches for patterns using **regular expressions**.

Example: show requests from a specific IP:

```bash
grep "^136.243.228.193" s-anand-net-Apr-2024
```

`^` ensures the match occurs **at the beginning of the line**.

---

### 10. Identify Bots

Search for user agents containing the word *bot*.

```bash
grep -o "\S*bot\S*" s-anand-net-Apr-2024 | sort | uniq -c
```

This extracts bot names such as:

* Googlebot
* Applebot
* Bingbot
* Claude crawler

---

### 11. Replace Text with `sed`

Log timestamps were enclosed in square brackets:

```
[31/Mar/2024:11:27:43 -0500]
```

They were converted to quoted values for easier CSV parsing.

Example:

```bash
sed 's/\[\([^]]*\)\]/"\1"/' s-anand-net-Apr-2024 > log.csv
```

This replaces:

```
[date]
```

with:

```
"date"
```

---

### 12. Export Data for Excel

After formatting, the log file can be opened in Excel as a **space-delimited dataset**.

Sometimes issues occur when fields contain quotes or unusual characters, which may require additional cleanup.

---

## Additional Useful Commands

Some other helpful shell utilities include:

* `cat` – concatenate and display file contents
* `awk` – powerful text processing language
* `less` – view large files interactively
