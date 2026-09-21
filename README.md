 
 
##                    --- 32bit PE Protector v1.7 ---
------------------------------------------------------------------------
A tool for protecting Windows executable files (PE32) against static
analysis, unauthorized copying, and modification.

 Platform: Windows (x86 / WOW64)
 Target format: PE32 (32-bit Executable)

  Features:

- **Multi-layered protection of code and data** — several independent
  processing mechanisms applied to executable sections.
- **Section compression** — reduction of the physical file size without
  loss of functionality.
- **Dynamic restoration at launch** — protected sections are restored to
  their original state before control is passed to the entry point.
- **Modular protection architecture** — each layer can be enabled or
  disabled independently.
- **Performance presets** — ready-made configurations for files of
  different sizes.
- **Debugging resistance** — built-in mechanism that counteracts
  interactive analysis.
- **Compatibility with some external packers** — a protected file continues
  to work correctly after being processed by third-party packers

Advantages over classic packers:

    Restoration at launch — the protected code is fully returned to
    its original state before the program starts running. This preserves
    compatibility with tools that need the "real" code at execution time.

    Modularity — only the required protection layers can be enabled.
    Different configurations are used for debugging and for production.

    No runtime dependencies — the entire restoration mechanism is
    embedded in the file itself, with no external libraries required.

Over commercial protectors:

    Small size overhead — the service section occupies less than 20 KB
    for a typical file.

    Transparent operation — the program behaves identically to the
    original, including error handling, resource access, and interaction
    with the operating system.

    Compatibility with external packers — a protected file continues
    to work correctly after being processed by third-party packers, which
    makes it possible to combine file size reduction with protection
    against analysis. Verified with UPX.

Performance:

    No runtime overhead — restoration is performed once at launch.
    Does not alter the behavior of multi-threaded applications.
    Does not require administrator privileges to run the protected file.

Supported Formats:

**Architecture**   PE32 (32-bit)

**OS bitness**  x86 and x64 (through WOW64)

**DEP** Supported

**ASLR** Supported

-------------------------------------------------------------------------

Not supported:

    PE32+ (64-bit EXE) — will be rejected with an error message.

	.NET assemblies — managed code is not native x86.
    
	Files with an existing TLS section — will be rejected.
    
	Files already protected by other protectors (Themida, VMProtect,
    
	Enigma, etc.) — behavior is not guaranteed.
    
	Digitally signed files — the signature becomes invalid.

May not work correctly:
    Files with self-verification of checksums.
	
    Files with custom exception handlers at load time.
	
    Exotic builds with a non-standard section layout.
	
    Files with a very large number of sections (> 32 without using the "large" preset).

Compatible compilers:

Tested with output from the following compilers:

    FASM, MASM, NASM, MinGW / GCC (native x86), MSVC (native x86)
    Borland C++, Watcom C/C++, Delphi (native x86, non-.NET)
    Free Pascal (native x86)
	    Operation with other compilers is possible but not guaranteed.

Requirements:
    For processing files: Windows XP or newer, with user privileges for user files.

Version history:

 **1.0 - Base version**

 **1.1 - Support to all windows Version**
 
 **1.2 - ASLR full support**

 **1.5 - fix bugs, many changes: (new options / some GCC compiled files support / increase cryptolayers)**

 **1.7 - Add extended protection options with combine mechanism between them (different License features)**

Legal Notice:

This tool is intended for protecting your own software. Do not using it to
circumvent the protection of third-party applications which violates copyright
law and is subject to prosecution.

I`m not respose for the result when you use 'protector' eg. damage you hardware or files.
Use it with apply you brain and remember about you risc.
----------------------------------------------------------------------------

  Syntax:
protector.exe [options] <target.exe>

          |      Option        |   Description:                                 |
          |--------------------|------------------------------------------------|
          | -nobf              | - disable code obfuscation                     |
          | -nocomp            | - disable compression                          |
          | -nocr              | - disable file encryption                      |
          | -notprot           | - disable debug resistance                     |
          | -nodump            | - disable anti-dump (metadata wipe)            |
          | -nowipe            | - disable IAT metadata wipe                    |
          | -needkey <key>     | - you custom serial on command line            |
          | --nkoneshot        | - save key after first run (needs -needkey)    |
          | -limitruns <n>     | - limit runs <1..255> without key              |
          | ------------------ | (may uses without needkey. (256 - is UNRECOVER |
		  | ------------------ | mode, after 255 runs))                         |
          | -timetolive <d>    | - days since compile (1..365)                  |
          | -bindmachine       | - bind to registry at first launch             |
          | -fsmall            | - small preset   (< 100 KB)                    |
          | -fdefault          | - default preset (100 KB - 1 MB)               |
          | -flarge            | - large preset   (1 MB - 50 MB)                |

          You can combine keys: -needkey --nkoneshot -nklimitruns -timetolive

          Default: all enabled, preset = default.


Options can be combined in any order. If no options are provided, the
default configuration is used: all mechanisms enabled, preset `default`.

  Examples:
--------------------------------------------------------
  Protection with default settings
 
protector.exe application.exe

  Maximum protection for a large file
  
protector.exe -flarge application.exe

  Protection without debugging resistance (for testing)

protector.exe -notprot application.exe

  Compression only, no other layers

protector.exe -nobf -nocr -notprot application.exe

  Fully disabled — useful for compatibility testing

protector.exe -nobf -nocomp -nocr -notprot application.exe

Output:
file named <name>_pro.exe next to the source file.
(original file is not modified).

----------------------------------------------------------------------------
    License type: shareware
        Copyright Protector v1.7 (c) 2026 by Den aka Quriositer
        Contact:
        My telegram: @Quriositer
        
        Welcome to my GIt https://github.com/Deniskain3D/Quantum-Messenger




