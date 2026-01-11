# DISCLAIMER

THIS REPOSITORY IS FORK OF [https://github.com/MichaelDipperstein/lzss](https://github.com/MichaelDipperstein/lzss) WITH SUPPORT LZSSL FORMAT!

modified by cam900 ([https://github.com/cam900](https://github.com/cam900), [https://gitlab.com/cam900](https://gitlab.com/cam900))

# LZSSL

LZSS variant with Literal copy command, Byte aligned for make unnecessary to bit-level file access.

## Structure:

```
First byte:
Bit 7 Literal(Set)/Copy(Clear)
- if Bit 7 is set:
  - Bit 6-0: Literal count - 1
  - Following bytes: Literal datas
- if Bit 7 is clear:
  - Bit 6-3: Copy length
  - Bit 2-0: Copy offset MSB
  - Next byte: Copy offset LSB
```
