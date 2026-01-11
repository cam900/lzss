# DISCLAIMER

THIS REPOSITORY IS FORK OF [https://github.com/MichaelDipperstein/lzss](https://github.com/MichaelDipperstein/lzss) WITH SUPPORT LZSSL FORMAT!

modified by cam900 ([https://github.com/cam900](https://github.com/cam900), [https://gitlab.com/cam900](https://gitlab.com/cam900))

# LZSSL

LZSS variant with Literal copy command, Byte aligned for make unnecessary to bit-level file access.

## Structure:

```
First byte:
Bit 7 Literal (Set) / Copy (Clear)
- if Bit 7 is set:
  - Bit 6-0: Literal count
  - Following bytes: Literal datas, repeated to Literal count + 1
- if Bit 7 is clear:
  - Bit 6-3: Copy length
  - Bit 2-0: Copy offset MSB
  - Next byte: Copy offset LSB
```

# LZSSLE

LZSSL variant with variable length copy offset, literal count support

## Structure:

```
First byte:
Bit 7 Literal (Set) / Copy (Clear)
- if Bit 7 is set:
  - Bit 6: Extended literal count (Set) / Short literal count (Clear)
  - if Bit 6 is clear:
    - Bit 5-0: Literal count
  - if Bit 6 is set:
    - Bit 5-0: Literal count MSB
    - Next byte: Literal count LSB
  - Following bytes: Literal datas, repeated to Literal count + 1
- if Bit 7 is clear:
  - Bit 6-3: Copy length
  - Bit 2: Extended copy offset (Set) / Short copy offset (Clear)
  - if Bit 2 is clear:
    - Bit 1-0: Copy offset MSB
    - Next byte: Copy offset LSB
  - if Bit 2 is set: 3 byte for copy offset
    - Bit 1-0: Copy offset bit 16-17
    - Byte #1: Copy offset bit 8-15
    - Byte #2: Copy offset bit 0-7
```
