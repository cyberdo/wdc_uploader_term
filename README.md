# wdc_uploader_term
My fork of wdc_uploader_term from WDC. To be used with newer monitors for W65C816SXB.

The original file was sent to me by WDC support and committed as the first version to this repo, without changes.

This tool solved my communication issue I had here: http://forum.6502.org/viewtopic.php?f=1&t=8087

My changes are improvements to the tool.

# Changes
Some of the changes made from the original version

## Support Intel HEX files and binary files
  * If the filename ends with .bin or .out, use binary (see Notes on formats below)
  * If the file content starts with `Z`, use zardoz binary format (as original tool)
  * If the file content starts with `:`, use Intel HEX format

## Notes on formats
The binary format has no addressing built in, therefore the address must be supplies on the command line.

Example:
```
python3 wdc_uploader_term.py -d /dev/ttyUSB0 -a 001000 -x -m write -v code.bin
```

# Known limits/issues
Writing to flash is known to be broken (by my changes). Only writing to RAM works,

The tool is not tested on Windows nor OSX.

The tool's reset function does not actually reset the CPU. There is no solution to this according to the schema. Press the RESET button manually before invoking a write.

The code is littered with commented out code I use for testing or developing. Since I am the only developer so far I'll keep it in when I am too lazy to remove it.
