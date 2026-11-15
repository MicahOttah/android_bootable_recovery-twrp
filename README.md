**Team Win Recovery Project (TWRP)**

You can find a compiling guide [here](http://forum.xda-developers.com/showthread.php?t=1943625 "Guide").

## LG G Pad X 8.0 (V521) - LineageOS 15.1

This is the fork of TWRP that the **LG G Pad X 8.0 (V521)** **LineageOS
15.1** port uses.

  Branch              lineage-15.1-v521
  Device tree         https://github.com/MicahOttah/android_device_lge_v521

What is different on lineage-15.1-v521
--------------------------------------

  790c815  v521: print a crash report when the GUI dies

When the TWRP GUI crashes, init just restarts the service and nothing is
printed anywhere, which makes the failure impossible to diagnose: the only
symptom is a loop of restarts.

The crash handler dumps the fault address, the registers, the stack and the
memory map to stderr, which the recovery redirects to `/tmp/recovery.log`,
so that the report can be pulled off the device and symbolised on the
host.  The memory map is what makes the report usable for a position
independent executable, because it holds the load base of the binary.

Everything in the handler is done with `write(2)` only - no stdio, no
malloc - so that it stays usable from a signal handler.
