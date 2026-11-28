# CyberChef Basics - [11-28-2026]

## What This Covers

This room introduces CyberChef, a web-based application used for encoding, decoding, encryption, decryption, and various data transformation tasks. It covers the CyberChef interface, common operations, and how to create recipes to process input data. It also provides hands-on practice with data extraction, Base64, Base85, Base58, Base62, URL encoding and decoding, binary conversion, and UNIX timestamps.

## Key Concepts

- **CyberChef:** A web-based tool developed to perform different cyber-related operations on data, including encoding, decoding, encryption, decryption, and data extraction.
- **Recipes:** A series of operations arranged in a specific order to process input data. Operations can be saved, loaded, or cleared.
- **CyberChef Interface:** Consists of four main areas:
  - **Operations:** Contains different operations that can be searched and selected.
  - **Recipe:** Allows users to arrange operations and configure their parameters. It is considered the heart of CyberChef.
  - **Input:** Accepts text or files through typing, pasting, or uploading.
  - **Output:** Displays the processed results and provides options to copy or save the output.
- **BAKE!:** Executes the selected recipe. Auto Bake can also be enabled to process data automatically whenever changes are made.
- **Common Operations:**
  - From Morse Code – Converts Morse code into alphanumeric characters.
  - URL Encode – Converts special characters into percent-encoded values.
  - To Base64 – Encodes raw data into a Base64 string.
  - To Hex – Converts input data into hexadecimal representation.
  - To Decimal – Converts input data into decimal values.
  - ROT13 – Uses a Caesar substitution cipher to rotate alphabetic characters.
- **CyberChef Workflow:**
  1. Define the objective.
  2. Put the data into the input area.
  3. Select the required operations and configure them in the recipe area.
  4. Examine the output to verify whether the objective has been achieved.
- **Extractors:** Operations used to extract specific information from input data:
  - Extract IP Addresses – Extracts IPv4 and IPv6 addresses.
  - Extract URLs – Extracts URLs from the input.
  - Extract Email Addresses – Extracts email addresses from the input.
- **Date and Time Operations:**
  - From UNIX Timestamp – Converts a UNIX timestamp into a readable date and time.
  - To UNIX Timestamp – Converts a date and time string into a UNIX timestamp.
- **Data Format Operations:**
  - From Base64 – Decodes Base64 data.
  - URL Decode – Converts percent-encoded characters into their original values.
  - From Base85 – Decodes Base85-encoded data.
  - From Base58 – Decodes Base58-encoded data.
  - To Base62 – Encodes data using Base62.
- **Base64 Encoding:** Converts binary data into a text-based representation using a set of 64 characters. The encoding process involves converting data into binary, dividing it into 6-bit groups, converting those groups into decimal values, and mapping them to Base64 characters.
- **UNIX Timestamp:** Represents the number of seconds elapsed since January 1, 1970 UTC.
- **URL Encoding:** Converts special characters into percent-encoded representations. For example, `:` becomes `%3A`, `/` becomes `%2F`, and `.` becomes `%2E`.

## Commands/Tools Used

### CyberChef

- **Online Access:** Used the CyberChef web application through the browser to perform the exercises.
- **Operations Used:**
  - Extract IP Addresses
  - Extract URLs
  - Extract Email Addresses
  - From UNIX Timestamp
  - To UNIX Timestamp
  - From Base64
  - To Base64
  - URL Decode
  - URL Encode
  - From Base85
  - From Base58
  - To Base62
  - From Morse Code
  - To Hex
  - To Decimal
  - ROT13

### Practical Exercises

- Extracted hidden email addresses, IP addresses, and domain names from the provided task data.
- Converted decimal values into binary.
- Encoded URLs and decoded percent-encoded URLs.
- Converted strings into Base64 and decoded Base64 values.
- Converted UNIX timestamps into readable date and time strings.
- Decoded Base85-encoded data.
- Created recipes by selecting and arranging operations in the recipe area.
- Used the output area to examine the results of the selected operations.

## What I Learned

I learned how CyberChef works and how its four main interface areas are used to process data. I understood how recipes allow multiple operations to be arranged and executed in sequence.

I practised extracting useful information such as IP addresses, URLs, and email addresses from input data. I also learned how different encoding formats work, including Base64, Base85, Base58, and Base62, along with URL encoding and decoding.

I explored UNIX timestamp conversion and understood the basic process of converting text into binary and then into Base64. I used the online CyberChef application to complete the exercises and learned how it can be useful during cybersecurity investigations for decoding data, extracting information, and analysing suspicious strings.
