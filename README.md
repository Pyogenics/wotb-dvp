# wotb-dvp
WOTB dvp type file specification.

## .dvpm
DVPM files are split into 3 sections: meta, file table and footer.
### meta
This section is at the very start of the file and has a magic string of "met3".
```c
struct DVPMMeta
{
    char magic[3]; // "met3"
    uint32_t footerUnknown; // Unknown value that is also present in the footer (metaSectionUnknown)
}
```
### file table
TODO
### footer
The footer is 44 bytes large and the last 4 bytes are a magic big endian string that reads "DVPM".

```c
struct DVPMFooter
{
    byte unknown1[8];
    uint32_t metaSectionCRC32;
    uint32_t metaSectionSize;
    byte unknown2[4];
    uint32_t metaSectionUnknown; // Unknown value that is also present in the meta section
    byte unknown3[8];
    uint32_t fileTableSize;
    uint32_t fileTableCRC32;
    char magic[4]; // "DVPM"
}
```
