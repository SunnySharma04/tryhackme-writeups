# TryHackMe: Data Representation

## Room Summary

This room covers how digital computers represent and store information at the low-level data layer. It explores binary arithmetic, base numbering system conversions (Decimal, Binary, Hexadecimal), nibble-to-hex mappings, and RGB color encoding models.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Data Representation |
| Difficulty | Easy |
| Topic | Binary Arithmetic, Hexadecimal, Base Conversions, Data Encoding |
| Status | Completed |

## Skills Practiced

- Understanding digital bits, bytes, and 4-bit nibbles
- Converting between Decimal (Base-10), Binary (Base-2), and Hexadecimal (Base-16)
- Grouping binary strings into nibbles for fast hexadecimal conversion
- Analyzing 24-bit RGB color encoding structures and `#RRGGBB` hex triplets
- Applying low-level data representation knowledge to hex editors, memory analysis, and network packet payloads

## Tools and Platforms Learned

- TryHackMe
- Binary & Hexadecimal Calculators / Converters
- Hex Editors (HxD, Ghidra concept)
- Base Conversion Methods

## Key Takeaways

- Hexadecimal acts as a readable shorthand for binary data—each hex digit corresponds directly to a 4-bit nibble.
- Standard RGB colors use 3 bytes (24 bits) to represent over 16.7 million distinct color combinations.
- Low-level data structures are foundational for reverse engineering, file signature identification (magic bytes), and log analysis.

## Defensive Learning

- Analyze hex-encoded web requests (e.g., URL encoding) to identify payload evasion attempts.
- Inspect binary file headers (magic bytes) to detect file extension spoofing in malware delivery.
- Understand low-level memory layouts when analyzing crash dumps or memory artifacts in forensic investigations.
