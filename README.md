# Code::Blocks GCC RISC-V Compiler Options

**NOTE: this is currently a work-in-progress and is not feature-complete. Currently it is focused on providing sufficient-enough options for use with RV32EC-architecture microcontrollers.**

This is a compiler definition and options file set to allow the use of the [GCC](https://gcc.gnu.org) [RISC-V](https://en.wikipedia.org/wiki/RISC-V) 'riscv-none-elf' cross-compiler with the [Code::Blocks IDE](https://www.codeblocks.org/).

It adds a compiler choice named 'GNU GCC Compiler for RISC-V' and defines a configurable selection of command-line options for it that are relevant or specific to the RISC-V platform.

The RISC-V-specific option groups presented are as follows:

- All RISC-V platform-specific options that do not require a user-provided value (e.g. not `-m<opt>=<value>` options), plus ISA specification options (`-misa-spec=...`).
- RISC-V architecture choice (e.g. RV32I, RV32E), including a selection of common extension combinations.
- RISC-V ABI calling convention choices (e.g. ilp32).

Please note that no `-mcpu=...` options are included, as the choices currently supported by GCC are exclusively focused on [SiFive](https://www.sifive.com) products, but the aim is to be manufacturer- and device-agnostic, so for SiFive devices the appropriate discrete architecture and ABI choices should be made instead (or a `-mcpu=...` option specified manually in project build options).

## Compatibility

These options files are compatible with the current (at time of writing) release version of Code::Blocks, 20.03. It may also work with newer nightly builds and releases, but has not been tested with these.

Compiler options are based upon those found in GCC version 12.2 or newer. Not all may be supported by older versions.

## How to Use

Copy both the `compiler_riscv-elf-gcc.xml` and `options_riscv-elf-gcc.xml` files into a folder named `compilers` inside the `share` folder of your user-specific CodeBlocks settings folder. For example, on Windows this will be `%APPDATA%\CodeBlocks\share\codeblocks\compilers`; on Linux, this will probably be `~/.codeblocks/share/codeblocks/compilers` (although for Ubuntu, this may be `~/.config/codeblocks/...` instead).

Then restart (or start) Code::Blocks.

**Important:** the compiler definition file does not specify *any* default paths to toolchain executables, so you *must* configure them before attempting to build anything. To do this:

1. Open the compiler settings window (*Settings->Compiler*).
2. Select the 'GNU GCC Compiler for RISC-V' compiler from the list.
3. Go to the 'Toolchain executables' tab.
4. Set the compiler installation directory.
5. The appropriate program executable filenames are pre-set, but modify if necessary.

## Resources

* [Code::Blocks compiler options file documentation](https://wiki.codeblocks.org/index.php/Compiler_options_file)
* [Code::Blocks compiler definition file documentation](https://wiki.codeblocks.org/index.php/Compiler_file)

## TODO

- Add more architecture options, particularly for RV64 devices.

Pull requests with any additions or corrections are welcome.