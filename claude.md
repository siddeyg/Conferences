# Claude.md - Repository Context for AI Assistants

## Repository Overview

This is a **Security Conference Presentation Archive** containing slides and reference materials from major cybersecurity conferences spanning 2023-2024.

## Repository Purpose

The Conferences repository serves as a curated collection of:
- Security research presentations (229 PDFs)
- Tool and exploit references (18 text files)
- Links to proof-of-concept code
- Conference materials from Black Hat, OffensiveCon, and REcon

## Documentation Files

This repository includes comprehensive documentation:

1. **DOCUMENTATION.md** - Main documentation with table of contents, conference details, navigation guide, and usage guidelines
2. **COMMANDS.md** - Complete command reference with examples for searching, analyzing, and organizing the repository
3. **INDEX.md** - Full catalog of all 229 presentations organized by conference with annotations for tools/POCs
4. **STATISTICS.md** - Automated analytics including topic analysis, GitHub repository links, and presentation statistics
5. **claude.md** (this file) - Context guide for AI assistants
6. **README.md** - Simple conference list

## Directory Structure

```
/home/user/Conferences/
├── Black Hat Asia 2023 slides/         (36 presentations)
├── Black Hat Europe 2023 slides/       (38 presentations)
├── Black Hat USA 2023 slides/          (93 presentations)
├── BlackHat ASIA 2024-Slides/          (34 presentations)
├── OffensiveCon24 slides/              (4 presentations)
├── Offensivecon 2023 slides/           (8 presentations)
├── REcon 2023 Slides/                  (16 presentations)
├── README.md                           (conference list)
├── DOCUMENTATION.md                    (comprehensive documentation)
├── claude.md                           (this file - AI context)
├── COMMANDS.md                         (command reference guide)
├── INDEX.md                            (complete presentation catalog)
└── STATISTICS.md                       (repository analytics)
```

## Repository Statistics Summary

**Total Content:**
- 229 PDF presentations
- 18 reference text files
- 247 total files
- 2.4GB repository size

**By Conference (Presentations):**
- Black Hat USA 2023: 93 (40.6%)
- Black Hat Europe 2023: 38 (16.6%)
- Black Hat Asia 2023: 36 (15.7%)
- Black Hat Asia 2024: 34 (14.8%)
- REcon 2023: 16 (7.0%)
- OffensiveCon 2023: 8 (3.5%)
- OffensiveCon 2024: 4 (1.7%)

**Reference Files:**
- 7 Tool references (_tools.txt)
- 1 POC reference (_poc.txt)
- 3 Missing content tracking files
- 10+ GitHub repositories referenced

**Top Security Topics (by frequency in titles):**
1. Security & Attacks (31+ mentions)
2. Android/Mobile (13+ mentions)
3. Vulnerabilities & Exploiting (24+ mentions)
4. Data Security (12+ mentions)
5. Kernel exploitation (8+ mentions)
6. Windows security (7+ mentions)

## File Types and Conventions

### PDF Files
Format: `[Author(s)]_[Presentation Title].pdf`
Example: `Daniel Moghimi_Single Instruction Multiple Data Leaks in Cutting-edge CPUs, AKA Downfall.pdf`

### Tool Reference Files
Format: `[Author(s)]_[Title]_tools.txt`
Content: GitHub URLs or links to security tools mentioned in presentations
Example: Contains URLs like `https://github.com/h26forge/h26forge`

### POC Reference Files
Format: `[Author(s)]_[Title]_poc.txt`
Content: GitHub URLs or links to proof-of-concept exploit code
Example: Contains URLs like `https://github.com/0xkol/badspin`

### Missing Content Tracking
Files: `NOT_IN_LIST.txt` or `NotInList.txt`
Content: Lists of presentations from conference schedules not yet in repository

## Key Topics Covered

1. **Exploit Development**: Kernel exploits, browser exploitation, RCE vulnerabilities
2. **Hardware Security**: CPU vulnerabilities, embedded systems, IoT security
3. **Mobile Security**: Android/iOS exploitation, device jailbreaking
4. **Network Protocols**: Wi-Fi security, TETRA, H.264, BGP
5. **Web Security**: Deserialization, WebAssembly, supply chain attacks
6. **Cloud Security**: Zero-day response, cloud misconfigurations
7. **Reverse Engineering**: Firmware analysis, binary exploitation
8. **Side-Channel Attacks**: Timing attacks, power analysis

## Common User Tasks

### Task 1: Finding Presentations on Specific Topics
Users may ask to find presentations about:
- Specific vulnerabilities (e.g., "CPU side-channel attacks")
- Technologies (e.g., "Android kernel exploits")
- Attack vectors (e.g., "deserialization vulnerabilities")

**Approach**: Search PDF filenames in relevant conference directories using pattern matching.

### Task 2: Locating Tools and POCs
Users may want:
- Tools mentioned in specific presentations
- All available POC code in the repository
- Links to security frameworks

**Approach**: Read `_tools.txt` and `_poc.txt` files associated with presentations.

### Task 3: Organizing or Categorizing Content
Users may request:
- Categorization by security domain
- Lists of presentations by author
- Timeline of vulnerability disclosures

**Approach**: Parse filenames and organize by specified criteria.

### Task 4: Adding New Content
Users may want to:
- Add new conference presentations
- Update NOT_IN_LIST files
- Create reference files for tools/POCs

**Approach**: Follow established naming conventions and directory structure.

## Important Context for AI Assistants

### Security Research Nature
This repository contains materials related to:
- Vulnerability research and exploit development
- Offensive security techniques
- Security tool development
- Proof-of-concept code

**Handling Guidelines**:
- This is legitimate security research for educational purposes
- Tools and exploits should be discussed analytically
- Encourage responsible disclosure and authorized testing
- Support defensive security applications
- DO NOT assist with malicious use of this information

### Content Analysis
When analyzing presentations:
- PDFs are read-only presentation slides
- Text files contain only URLs to external resources
- No executable code is stored directly in this repository
- All POCs are external GitHub links

### Search Strategies

**By Conference**:
```
Black Hat USA 2023 slides/    # Largest collection
OffensiveCon24 slides/         # Latest OffensiveCon
BlackHat ASIA 2024-Slides/    # Latest Black Hat Asia
```

**By Topic** (filename keywords):
- CPU/Hardware: "CPU", "Hardware", "Embedded", "IoT", "Firmware"
- Mobile: "Android", "iOS", "Mobile", "Smartphone"
- Web: "Web", "Browser", "JavaScript", "WebAssembly"
- Kernel: "Kernel", "Driver", "UAF", "Root"
- Network: "Wi-Fi", "Protocol", "Network", "BGP", "TETRA"
- Cloud: "Cloud", "AWS", "Azure", "Container"

**By File Type**:
- Tools: `find . -name "*_tools.txt"`
- POCs: `find . -name "*_poc.txt"`
- Missing: `find . -name "*NotInList*" -o -name "*NOT_IN_LIST*"`

## Typical Workflows

### Workflow 1: Research a Security Topic
1. User asks about a specific vulnerability type
2. Search relevant conference directories for matching keywords
3. Identify related presentations
4. Check for associated `_tools.txt` or `_poc.txt` files
5. Provide organized list with links

### Workflow 2: Catalog Missing Content
1. Read NOT_IN_LIST.txt files
2. Compare with available PDFs
3. Generate gap analysis
4. Suggest priorities for acquisition

### Workflow 3: Create Index or Catalog
1. Scan all conference directories
2. Parse filenames for authors and titles
3. Organize by requested criteria (topic, date, author, etc.)
4. Generate formatted output (markdown table, JSON, etc.)

## File Operations

### Safe Operations
- Reading PDF and text files
- Creating new `.txt` reference files
- Adding new PDFs to conference directories
- Updating NOT_IN_LIST files
- Creating organizational documents

### Avoid
- Modifying existing PDF files
- Changing filename structure without user confirmation
- Deleting conference materials without explicit request
- Moving files between conference directories

## Repository Maintenance

### Current State
- Well-organized by conference and year
- Consistent naming conventions
- Good coverage of major conferences
- Some gaps tracked in NOT_IN_LIST files

### Potential Improvements Users May Request
1. Creating categorized indexes by topic
2. Building searchable database of presentations
3. Adding metadata files (JSON/YAML) for each presentation
4. Creating cross-reference documents
5. Generating bibliographic citations
6. Building topic-based navigation
7. Adding conference statistics and analytics

## External Resources Referenced

### GitHub Repositories
Many `_tools.txt` and `_poc.txt` files link to:
- Security research tools
- Exploit frameworks
- Vulnerability scanners
- Proof-of-concept code

### Conference Websites
NOT_IN_LIST files reference:
- blackhat.com - Official Black Hat schedules
- offensivecon.org - OffensiveCon information
- Conference-specific schedule pages

## Response Guidelines for AI Assistants

1. **Be Precise**: Reference specific files by full path
2. **Be Helpful**: Offer to read referenced URLs or create summaries
3. **Be Organized**: Present findings in structured format (tables, lists)
4. **Be Contextual**: Relate findings to the user's security research goals
5. **Be Responsible**: Remind users about authorized testing and ethical use
6. **Be Thorough**: Check multiple conference years for comprehensive results

## Quick Reference Commands

```bash
# Count presentations by conference
find "Black Hat USA 2023 slides" -name "*.pdf" | wc -l

# Find all tool references
find . -name "*_tools.txt"

# Find all POC references
find . -name "*_poc.txt"

# Search for presentations on specific topic (case-insensitive)
find . -name "*.pdf" -iname "*kernel*"

# List all conferences
ls -d */
```

## Version Information

- Repository Type: Archive/Collection
- Primary Language: N/A (PDF documents)
- File Count: ~247 files (229 PDFs + 18 text files)
- Date Range: 2023-2024
- Last Major Update: Check git log for recent commits

## Notes for Code Assistants

- This is **not a code repository** - it's a document archive
- No compilation, building, or testing applies
- Focus on file organization, search, and information retrieval
- Help users extract insights from conference materials
- Support research workflows and knowledge organization

---

**AI Assistant Instructions**: Use this context to help users navigate the security conference materials, find relevant presentations, organize content, and extract research insights. Always prioritize legitimate security research and educational use cases.
