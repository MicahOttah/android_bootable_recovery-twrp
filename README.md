**Team Win Recovery Project (TWRP)**

You can find a compiling guide [here](http://forum.xda-developers.com/showthread.php?t=1943625 "Guide").

## LG G Pad X 8.0 (V521)

Fork for the V521 port (branch `lineage-15.1-v521`).  Change: when the GUI
crashes, a crash report (fault address, registers, stack, memory map) is
written to `/tmp/recovery.log` instead of a silent restart loop.

Port and device tree: https://github.com/MicahOttah/android_device_lge_v521
