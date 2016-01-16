# What is this?

It may occasionally be hard to run failing program under debugger
e.g. if it runs inside deeply nested build system.

This project solves this by providing a library (libdebugme.so)
which can be linked or even preloaded to system to catch signals
and automatically run gdb (or, in future, any other debugger).

# Usage

Simply preload libdebugme.so to process and ask it to intercept
"bad" events:
```
DEBUGME_OPTIONS=handle_signals=1 LD_PRELOAD=libdebugme.so make
```
and it'll automatically run gdb on error.

Alternatively you can manually link your app against libdebugme
and/or run debugger explicitly (public APIs are in debugme.h).

# Future plans

Here're some plans for libdebugme:
* ensure thread-safety
* support running gdb in a dedicated terminal (xterm, gnome-terminal, etc.)
* support other debuggers (ddd, lldb, Visual Studio, etc.)
* use CMake
* other minor TODO/FIXME are scattered all over the codebase
