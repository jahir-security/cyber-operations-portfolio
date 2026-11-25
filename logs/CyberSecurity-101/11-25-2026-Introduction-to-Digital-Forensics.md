# Introduction to Digital Forensics - [11-25-2026]

## What this covers

This lab room provides an understanding of digital forensics and an overview of how it is done. The procedures and guidelines to be followed in digital forensics. It also covers diferent types and tools of digital forensics.

## Key concepts

* understanding phases of digital forensics
* Types of digital forensics and different tools
* Procedure to evidence acquisition and NIST framwork (collection, examination, analysis, reporting)
* Basic concept of different forensic tools
* Chain of Custody
* Use of write blocker
* A small forensic activity

## Commands and tools used



```bash
# Basic concept of FTK imager, autopsy, volatility

# To get metadata of a pdf
pdfinfo document.pdf

# To get metadata of an image and filter out its camera model
exiftool image.jpg | grep -i Camera

```
## What I Learned

I learned about how digitial forensics team work and the process of getting authorization first. Importance of chain of Custody to maintain integrity. Usecase of write blocker so the actual data stays in its original form without any changes. Also learned what type of different tools are use for different purposes.
