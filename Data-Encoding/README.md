# TryHackMe: Data Encoding

## Room Summary

This room covers character encoding standards, digital character mapping, and payload transformation mechanisms. It explores ASCII tables, variable-length Unicode encodings (UTF-8, UTF-16, UTF-32), and Base64 data encoding schemes.

## Room Details

| Field      | Details                                           |
| ---------- | ------------------------------------------------- |
| Platform   | TryHackMe                                         |
| Room       | Data Encoding                                     |
| Difficulty | Easy                                              |
| Topic      | Character Encoding, ASCII, Unicode, UTF-8, Base64 |
| Status     | Completed                                         |

## Skills Practiced

* Understanding 7-bit ASCII and 8-bit Extended ASCII character mapping
* Differentiating between Unicode code points and byte encodings (UTF-8, UTF-16, UTF-32)
* Performing Base64 encoding/decoding calculations and identifying `=` padding
* Executing command-line encoding transformations using CLI utilities (`base64`, `xxd`, `od`, `hexdump`)
* Analyzing obfuscated security payloads and web-encoded strings (URL/Percent encoding)

## Hands-On & Command Reference

### Command-Line Encoding & Decoding

```bash
# Encode text string to Base64
echo -n "CyberSecurity" | base64

# Decode a Base64 encoded string
echo "Q3liZXJTZWN1cml0eQ==" | base64 -d

# Convert string to Hexadecimal representation using xxd
echo -n "TryHackMe" | xxd -p

# Decode Hexadecimal string back to raw text
echo "5472794861636b4d65" | xxd -p -r

# Inspect ASCII/Byte layout of a text file
od -c input.txt
hexdump -C payload.bin
```

### Python Data Transformation Snippets

```python
# ASCII / Ordinal Value Conversions
char = 'A'
ascii_val = ord(char)
char_back = chr(ascii_val)

print(ascii_val)
print(char_back)

# Base64 Encoding and Decoding in Python
import base64

raw_data = b"PreSecurity"
encoded = base64.b64encode(raw_data)
decoded = base64.b64decode(encoded)

print(f"Encoded: {encoded.decode()}")
print(f"Decoded: {decoded.decode()}")

# UTF-8 Byte Inspection
string_data = "Security"
utf8_bytes = string_data.encode('utf-8')
hex_bytes = utf8_bytes.hex()

print(f"Hex: {hex_bytes}")
```

## Tools and Platforms Learned

* **TryHackMe**
* **Linux CLI Utilities**

  * `base64`
  * `xxd`
  * `hexdump`
  * `od`
* **Python**

  * `base64`
  * `codecs`
* **CyberChef**

## Key Takeaways

* Encoding is a reversible process designed for data interoperability and rendering, not confidentiality.
* UTF-8 is backward-compatible with ASCII and uses variable byte lengths (1 to 4 bytes) per code point.
* Base64 maps binary data into 6-bit index chunks across 64 printable ASCII characters, using `=` for padding.

## Defensive Learning

* Decode Base64-encoded CLI commands (e.g., PowerShell `-e` / `-EncodedCommand`) during SIEM triage.
* Audit web application inputs for double-encoding (`%253C`) or Unicode bypass attempts against WAF rules.
* Inspect executable binary strings for UTF-16LE wide-character indicators of compromise (IOCs).
