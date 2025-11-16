# Conferences Repository Documentation

## Overview

This repository serves as a curated archive of security conference presentation slides from leading cybersecurity conferences. The collection includes presentations from offensive security, vulnerability research, exploit development, and various other security domains.

## Repository Structure

The repository is organized by conference name and year, with the following main directories:

```
Conferences/
├── Black Hat Asia 2023 slides/
├── Black Hat Europe 2023 slides/
├── Black Hat USA 2023 slides/
├── BlackHat ASIA 2024-Slides/
├── OffensiveCon24 slides/
├── Offensivecon 2023 slides/
└── REcon 2023 Slides/
```

## Statistics

- **Total PDF Presentations**: 229
- **Total Reference Files**: 18
- **Conferences Covered**: 7 (across 2023-2024)

## Content Types

### 1. PDF Presentation Slides
The main content of this repository consists of PDF files containing presentation slides from various security conferences. These slides cover topics including but not limited to:

- Vulnerability research and exploit development
- Mobile and embedded systems security
- Web application security
- Cryptographic analysis
- Cloud security
- Hardware hacking
- Reverse engineering
- Network protocol security
- Kernel exploitation
- Side-channel attacks

### 2. Reference Files (.txt)

The repository includes text files that complement the presentations:

#### Tool References (_tools.txt)
Files ending with `_tools.txt` contain links to tools, frameworks, or software mentioned in the corresponding presentations.

**Example:**
```
Willy Vasquez & Stephen Checkoway & Hovav Shacham_The Most Dangerous Codec in the World Finding and Exploiting Vulnerabilities in H.264 Decoders_tools.txt
→ Contains: https://github.com/h26forge/h26forge
```

#### Proof of Concept References (_poc.txt)
Files ending with `_poc.txt` contain links to proof-of-concept code or vulnerability demonstrations.

**Example:**
```
Moshe Kol_Racing Against the Lock Exploiting Spinlock UAF in the Android Kernel_poc.txt
→ Contains: https://github.com/0xkol/badspin
```

#### Missing Presentations (NOT_IN_LIST.txt / NotInList.txt)
These files track presentations from the conference schedule that are not yet included in the repository. They contain:
- Direct links to conference schedule pages
- Lists of presentation titles and speakers

## Conferences Included

### Black Hat USA 2023
Location: Las Vegas, Nevada
Date: August 2023
Focus: One of the world's leading information security conferences, covering cutting-edge research and practical demonstrations.

### Black Hat Asia 2023 & 2024
Location: Singapore
Dates: 2023 and April 16-19, 2024
Focus: Asian edition of Black Hat, featuring regional and international security research.

### Black Hat Europe 2023
Location: London, UK
Date: December 2023
Focus: European edition featuring regional security research and industry trends.

### OffensiveCon 2023 & 2024
Location: Berlin, Germany
Dates: 2023 and May 10-11, 2024
Focus: Specialized conference focusing on offensive security techniques, exploitation, and vulnerability research.

### REcon 2023
Location: Montreal, Canada
Date: June 2023
Focus: Reverse engineering and advanced exploitation techniques.

## How to Navigate This Repository

### Finding Presentations by Topic

To find presentations on specific topics, you can:

1. **Browse by Conference**: Navigate to the specific conference directory
2. **Search by Keyword**: Use file names which include presenter names and presentation titles
3. **Look for Tools**: Check `_tools.txt` files for specific security tools or frameworks
4. **Check POCs**: Review `_poc.txt` files for exploit code and demonstrations

### File Naming Convention

Files follow this naming pattern:
```
[Presenter Name(s)]_[Presentation Title]_[optional suffix].pdf
```

Where suffixes might include:
- `_tools.txt` - Associated tools/code
- `_poc.txt` - Proof of concept code
- `_wp.pdf` - Whitepaper version

### Example Presentations by Category

#### Mobile & Embedded Security
- "Jailbreaking an Electric Vehicle in 2023 or What It Means to Hotwire Tesla's x86-Based Seat Heater" (Black Hat USA 2023)
- "Physical Attacks Against Smartphones" (Black Hat USA 2023)
- "Racing Against the Lock Exploiting Spinlock UAF in the Android Kernel" (OffensiveCon 2023)

#### CPU & Hardware Security
- "Single Instruction Multiple Data Leaks in Cutting-edge CPUs, AKA Downfall" (Black Hat USA 2023)
- "Sweet Dreams Abusing Sleep Mode to Break Wi-Fi Encryption and Disrupt WPA2/3 Networks" (Black Hat Asia 2023)

#### Web & Application Security
- "ODDFuzz Hunting Java Deserialization Gadget Chains via Structure-Aware Directed Greybox Fuzzing" (Black Hat USA 2023)
- "Attacking WebAssembly Compiler of Webkit" (Black Hat Asia 2023)

#### Communication Protocols
- "All Cops Are Broadcasting Breaking TETRA After Decades in the Shadows" (Black Hat USA 2023)
- "The Most Dangerous Codec in the World Finding and Exploiting Vulnerabilities in H.264 Decoders" (Black Hat USA 2023)

#### Cloud Security
- "When a Zero Day and Access Keys Collide in the Cloud Responding to the SugarCRM 0-Day Vulnerability" (Black Hat USA 2023)

## Using Referenced Tools and POCs

Many presentations include links to:
- Open-source tools developed for research
- Proof-of-concept exploit code
- Supporting materials and datasets

**Important Security Note:**
> The tools and POCs referenced in this repository are intended for:
> - Educational purposes
> - Authorized security testing
> - Security research
> - Defensive security implementations
>
> Always ensure you have proper authorization before using any security tools or techniques on systems you do not own.

## Missing Content

Each conference directory may contain a `NOT_IN_LIST.txt` or `NotInList.txt` file that tracks presentations from the conference agenda that are not yet available in this repository. This helps identify gaps in the collection.

## Contributing

When adding new presentations to this repository:

1. Use the established naming convention: `[Author]_[Title].pdf`
2. Create companion `.txt` files for tools or POCs when applicable
3. Place files in the appropriate conference directory
4. Update `NOT_IN_LIST.txt` files as content is added

## Additional Resources

- [Black Hat Conferences](https://www.blackhat.com/)
- [OffensiveCon](https://www.offensivecon.org/)
- [REcon Conference](https://recon.cx/)

## License and Usage

This repository archives publicly available conference presentations. Users should:
- Respect the intellectual property rights of presenters
- Follow responsible disclosure practices
- Use the information for legitimate security research and education
- Cite sources appropriately when referencing this work

## Changelog

See individual commit history for detailed changes to the repository.

---

**Last Updated**: November 2025
**Maintainer**: Repository owner
**Repository Type**: Security Conference Archive
