# Command Reference Guide

A comprehensive guide to searching, analyzing, and organizing the Conferences repository using command-line tools.

## Table of Contents

- [Basic Navigation](#basic-navigation)
- [Finding Presentations](#finding-presentations)
  - [By Topic](#by-topic)
  - [By Author](#by-author)
  - [By Conference](#by-conference)
  - [By File Type](#by-file-type)
- [Statistics and Analysis](#statistics-and-analysis)
- [Working with References](#working-with-references)
- [Advanced Searches](#advanced-searches)
- [Organizing and Cataloging](#organizing-and-cataloging)
- [Useful One-Liners](#useful-one-liners)

---

## Basic Navigation

### List all conference directories
```bash
ls -d */
```
**Output:**
```
Black Hat Asia 2023 slides/
Black Hat Europe 2023 slides/
Black Hat USA 2023 slides/
BlackHat ASIA 2024-Slides/
OffensiveCon24 slides/
Offensivecon 2023 slides/
REcon 2023 Slides/
```

### List files in a specific conference
```bash
ls "Black Hat USA 2023 slides/"
```

### Count total files in repository
```bash
find . -type f | wc -l
```

### Show directory sizes
```bash
du -sh */
```

---

## Finding Presentations

### By Topic

#### Find presentations about Android/Mobile
```bash
find . -name "*.pdf" -iname "*android*"
find . -name "*.pdf" -iname "*mobile*"
find . -name "*.pdf" -iname "*ios*"
```

**Example output:**
```
./Offensivecon 2023 slides/Moshe Kol_Racing Against the Lock Exploiting Spinlock UAF in the Android Kernel_poc.txt
```

#### Find presentations about Kernel exploitation
```bash
find . -name "*.pdf" \( -iname "*kernel*" -o -iname "*uaf*" -o -iname "*use-after-free*" \)
```

#### Find presentations about Web security
```bash
find . -name "*.pdf" \( -iname "*web*" -o -iname "*browser*" -o -iname "*javascript*" -o -iname "*xss*" \)
```

#### Find presentations about Hardware/CPU
```bash
find . -name "*.pdf" \( -iname "*cpu*" -o -iname "*hardware*" -o -iname "*chip*" -o -iname "*side-channel*" \)
```

#### Find presentations about Cloud security
```bash
find . -name "*.pdf" \( -iname "*cloud*" -o -iname "*aws*" -o -iname "*azure*" -o -iname "*gcp*" \)
```

#### Find presentations about Fuzzing
```bash
find . -name "*.pdf" -iname "*fuzz*"
```

### By Author

#### Find all presentations by a specific author (case-insensitive)
```bash
find . -name "*.pdf" -iname "*daniel*"
```

#### Find presentations with multiple authors
```bash
find . -name "*.pdf" -name "*&*"
```

#### List unique authors (extract from filenames)
```bash
find . -name "*.pdf" -printf "%f\n" | cut -d'_' -f1 | sort -u
```

### By Conference

#### List only Black Hat USA 2023 presentations
```bash
ls "Black Hat USA 2023 slides/"*.pdf
```

#### Count presentations in each conference
```bash
for dir in */; do
  count=$(find "$dir" -name "*.pdf" 2>/dev/null | wc -l)
  echo "$dir: $count presentations"
done
```

#### Find the latest conference materials (2024)
```bash
find . -path "*2024*" -name "*.pdf"
```

### By File Type

#### Find all PDF presentations
```bash
find . -name "*.pdf"
```

#### Find all tool reference files
```bash
find . -name "*_tools.txt"
```

#### Find all POC reference files
```bash
find . -name "*_poc.txt"
```

#### Find all reference text files (tools, POCs, etc.)
```bash
find . -name "*.txt"
```

#### Find missing content tracking files
```bash
find . -name "*NotInList*" -o -name "*NOT_IN_LIST*"
```

---

## Statistics and Analysis

### Total count by file type
```bash
echo "PDFs: $(find . -name "*.pdf" | wc -l)"
echo "Text files: $(find . -name "*.txt" | wc -l)"
echo "Total files: $(find . -type f | wc -l)"
```

### Presentations per conference (detailed)
```bash
echo "=== Presentations by Conference ==="
find "Black Hat USA 2023 slides" -name "*.pdf" | wc -l | xargs echo "Black Hat USA 2023:"
find "Black Hat Asia 2023 slides" -name "*.pdf" | wc -l | xargs echo "Black Hat Asia 2023:"
find "Black Hat Europe 2023 slides" -name "*.pdf" | wc -l | xargs echo "Black Hat Europe 2023:"
find "BlackHat ASIA 2024-Slides" -name "*.pdf" | wc -l | xargs echo "Black Hat Asia 2024:"
find "OffensiveCon24 slides" -name "*.pdf" | wc -l | xargs echo "OffensiveCon 2024:"
find "Offensivecon 2023 slides" -name "*.pdf" | wc -l | xargs echo "OffensiveCon 2023:"
find "REcon 2023 Slides" -name "*.pdf" | wc -l | xargs echo "REcon 2023:"
```

### Most common keywords in titles (top 20)
```bash
find . -name "*.pdf" -printf "%f\n" | \
  tr '[:upper:]' '[:lower:]' | \
  tr '_' '\n' | \
  tr ' ' '\n' | \
  grep -v '^$' | \
  grep -v '.pdf' | \
  sort | uniq -c | sort -rn | head -20
```

### List presentations with associated tools or POCs
```bash
for file in $(find . -name "*_tools.txt" -o -name "*_poc.txt"); do
  echo "=== $file ==="
  cat "$file"
  echo ""
done
```

---

## Working with References

### Display all tool references with their URLs
```bash
echo "=== All Tool References ==="
find . -name "*_tools.txt" -exec echo "File: {}" \; -exec cat {} \; -exec echo "" \;
```

### Display all POC references with their URLs
```bash
echo "=== All POC References ==="
find . -name "*_poc.txt" -exec echo "File: {}" \; -exec cat {} \; -exec echo "" \;
```

### Extract all GitHub URLs from reference files
```bash
find . -name "*.txt" -exec grep -h "github.com" {} \; | sort -u
```

### Count references by type
```bash
echo "Tool references: $(find . -name "*_tools.txt" | wc -l)"
echo "POC references: $(find . -name "*_poc.txt" | wc -l)"
echo "Missing content lists: $(find . -name "*NotInList*" -o -name "*NOT_IN_LIST*" | wc -l)"
```

### View missing presentations from a conference
```bash
cat "Black Hat USA 2023 slides/NOT_IN_LIST.txt"
```

---

## Advanced Searches

### Find presentations from a specific year
```bash
find . -path "*2023*" -name "*.pdf"
find . -path "*2024*" -name "*.pdf"
```

### Find presentations with specific words in title (multiple keywords)
```bash
# Find presentations about both "exploit" AND "kernel"
find . -name "*.pdf" -iname "*exploit*" -iname "*kernel*"

# Find presentations about "exploit" OR "vulnerability"
find . -name "*.pdf" \( -iname "*exploit*" -o -iname "*vulnerab*" \)
```

### Search for presentations modified in last 30 days
```bash
find . -name "*.pdf" -mtime -30
```

### Find presentations by file size
```bash
# Find presentations larger than 10MB
find . -name "*.pdf" -size +10M

# Find presentations smaller than 1MB
find . -name "*.pdf" -size -1M
```

### Find presentations with whitepaper versions
```bash
find . -name "*_wp.pdf"
```

### Case-sensitive exact title search
```bash
find . -name "*Tesla*"
```

---

## Organizing and Cataloging

### Create a simple index of all presentations
```bash
find . -name "*.pdf" -printf "%p\n" | sort > presentations_index.txt
```

### Create categorized index by conference
```bash
{
  echo "# Conference Presentations Index"
  echo ""
  for dir in */; do
    echo "## ${dir%/}"
    echo ""
    find "$dir" -name "*.pdf" -printf "- %f\n" | sort
    echo ""
  done
} > INDEX.md
```

### Export presentation titles only (cleaned)
```bash
find . -name "*.pdf" -printf "%f\n" | \
  sed 's/_/ - /1' | \
  sed 's/.pdf$//' | \
  sort > titles_list.txt
```

### Create CSV list of presentations
```bash
{
  echo "Conference,Author,Title,Has_Tools,Has_POC"
  find . -name "*.pdf" | while read pdf; do
    dir=$(dirname "$pdf" | cut -d'/' -f2)
    filename=$(basename "$pdf" .pdf)
    author=$(echo "$filename" | cut -d'_' -f1)
    title=$(echo "$filename" | cut -d'_' -f2-)
    base="${pdf%.pdf}"
    tools=$([ -f "${base}_tools.txt" ] && echo "Yes" || echo "No")
    poc=$([ -f "${base}_poc.txt" ] && echo "Yes" || echo "No")
    echo "\"$dir\",\"$author\",\"$title\",\"$tools\",\"$poc\""
  done
} > presentations.csv
```

### Generate statistics report
```bash
{
  echo "# Repository Statistics Report"
  echo "Generated: $(date)"
  echo ""
  echo "## Overall Statistics"
  echo "- Total PDFs: $(find . -name '*.pdf' | wc -l)"
  echo "- Total reference files: $(find . -name '*.txt' | wc -l)"
  echo "- Total directories: $(find . -type d | wc -l)"
  echo "- Total size: $(du -sh . | cut -f1)"
  echo ""
  echo "## By Conference"
  for dir in */; do
    pdf_count=$(find "$dir" -name "*.pdf" 2>/dev/null | wc -l)
    txt_count=$(find "$dir" -name "*.txt" 2>/dev/null | wc -l)
    echo "- ${dir%/}: $pdf_count presentations, $txt_count reference files"
  done
  echo ""
  echo "## Reference Files"
  echo "- Tool references: $(find . -name '*_tools.txt' | wc -l)"
  echo "- POC references: $(find . -name '*_poc.txt' | wc -l)"
  echo "- Missing content tracking: $(find . -name '*NotInList*' -o -name '*NOT_IN_LIST*' | wc -l)"
} > STATISTICS.md
```

---

## Useful One-Liners

### Quick topic searches
```bash
# Android security
find . -name "*.pdf" -iname "*android*" -printf "%f\n"

# Tesla/automotive
find . -name "*.pdf" -iname "*tesla*" -o -iname "*vehicle*" -o -iname "*automotive*"

# WiFi/wireless
find . -name "*.pdf" \( -iname "*wifi*" -o -iname "*wireless*" -o -iname "*802.11*" \)

# Cryptography
find . -name "*.pdf" \( -iname "*crypto*" -o -iname "*encryption*" -o -iname "*cipher*" \)

# AI/ML security
find . -name "*.pdf" \( -iname "*ai*" -o -iname "*machine*learning*" -o -iname "*gpt*" \)
```

### List presentations with their conference
```bash
find . -name "*.pdf" -printf "%h - %f\n" | sed 's/\.\///' | sort
```

### Find duplicate or similar titles (basic)
```bash
find . -name "*.pdf" -printf "%f\n" | sort | uniq -d
```

### Show only presentation titles (clean format)
```bash
find . -name "*.pdf" -printf "%f\n" | sed 's/_/ | /1' | sed 's/.pdf$//' | column -t -s'|'
```

### List all references (tools + POCs) with context
```bash
find . \( -name "*_tools.txt" -o -name "*_poc.txt" \) | while read file; do
  echo "=== $(basename "$file" | sed 's/_tools.txt//;s/_poc.txt//') ==="
  cat "$file"
  echo ""
done
```

### Search file contents for specific URLs or keywords
```bash
# Find all files mentioning "exploit"
find . -name "*.txt" -exec grep -l "exploit" {} \;

# Find all GitHub repositories referenced
find . -name "*.txt" -exec grep -h "github.com" {} \; | sort -u
```

### Recent additions (last 7 days)
```bash
find . -name "*.pdf" -mtime -7 -printf "%TY-%Tm-%Td %TH:%TM - %p\n" | sort
```

---

## Examples by Use Case

### Use Case 1: Researching Android Kernel Exploits

```bash
# Step 1: Find relevant presentations
find . -name "*.pdf" \( -iname "*android*" -o -iname "*kernel*" \)

# Step 2: Check for POCs
find . -name "*Android*poc.txt" -o -name "*Kernel*poc.txt"

# Step 3: Extract all related GitHub links
find . -name "*.txt" -path "*ndroid*" -exec grep -h "github" {} \;
```

### Use Case 2: Building a Reading List on Hardware Security

```bash
# Create a focused index
{
  echo "# Hardware Security Reading List"
  echo ""
  find . -name "*.pdf" \( -iname "*hardware*" -o -iname "*cpu*" -o -iname "*chip*" -o -iname "*embedded*" \) -printf "- [ ] %f\n"
} > hardware_security_reading_list.md
```

### Use Case 3: Comparing Conference Coverage

```bash
# Compare presentations count
echo "Conference Coverage Comparison:"
for conf in "Black Hat USA 2023" "OffensiveCon24" "REcon 2023"; do
  count=$(find . -path "*$conf*" -name "*.pdf" | wc -l)
  printf "%-25s: %3d presentations\n" "$conf" "$count"
done
```

### Use Case 4: Finding Missing Resources

```bash
# Check which presentations have supporting materials
find . -name "*.pdf" | while read pdf; do
  base="${pdf%.pdf}"
  has_tools=$([ -f "${base}_tools.txt" ] && echo "✓" || echo "✗")
  has_poc=$([ -f "${base}_poc.txt" ] && echo "✓" || echo "✗")
  echo "$(basename "$pdf") - Tools: $has_tools, POC: $has_poc"
done | grep "✗"
```

---

## Tips and Best Practices

1. **Always use quotes** around directory names with spaces:
   ```bash
   # Good
   ls "Black Hat USA 2023 slides/"

   # Bad
   ls Black Hat USA 2023 slides/
   ```

2. **Use case-insensitive search** (`-iname`) for broader results:
   ```bash
   find . -iname "*android*"  # Finds Android, android, ANDROID, etc.
   ```

3. **Combine multiple conditions** with `-o` (OR) or multiple `-name` (AND):
   ```bash
   # OR: Find presentations about Android OR iOS
   find . -name "*.pdf" \( -iname "*android*" -o -iname "*ios*" \)

   # AND: Find presentations mentioning both "kernel" AND "exploit"
   find . -name "*.pdf" -iname "*kernel*" -iname "*exploit*"
   ```

4. **Use `-printf` for custom formatting**:
   ```bash
   # Show modification time and path
   find . -name "*.pdf" -printf "%TY-%Tm-%Td %p\n"
   ```

5. **Redirect output to files** for later analysis:
   ```bash
   find . -name "*.pdf" > all_presentations.txt
   ```

6. **Chain commands** with pipes for complex operations:
   ```bash
   find . -name "*.pdf" | wc -l  # Count results
   find . -name "*.pdf" | sort   # Sort results
   find . -name "*.pdf" | grep -i android  # Filter results
   ```

---

## Quick Reference Table

| Task | Command |
|------|---------|
| List all PDFs | `find . -name "*.pdf"` |
| Count PDFs | `find . -name "*.pdf" \| wc -l` |
| Find by keyword | `find . -name "*.pdf" -iname "*keyword*"` |
| Find tools | `find . -name "*_tools.txt"` |
| Find POCs | `find . -name "*_poc.txt"` |
| List conferences | `ls -d */` |
| Count by conference | `for dir in */; do echo "$dir: $(find "$dir" -name "*.pdf" \| wc -l)"; done` |
| View all GitHub links | `find . -name "*.txt" -exec grep -h "github.com" {} \; \| sort -u` |
| Recent files (7 days) | `find . -name "*.pdf" -mtime -7` |
| Large files (>10MB) | `find . -name "*.pdf" -size +10M` |

---

**Note:** All commands assume you're running them from the repository root directory (`/home/user/Conferences/`).

For more information, see [DOCUMENTATION.md](./DOCUMENTATION.md).
