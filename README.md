# GCC Cross-Compiler Builder
### xbuild.sh
Builds a cross-compiler for a desired architecture, as well as downloading/installing required dependencies. <br/> The purpose of **xbuild** is to expedite the awkward process of downloading/configuring/building a useable cross-compiler. <br/>(It's essentially a glorified Make file.)<br/>
Made with OS development in mind, on a Debian/Ubuntu system, so individual efficacy may vary.
## Usage
```
GCC Cross-Compiler Builder 

Usage: ./xbuild.sh [options] TARGET

Required:
	TARGET                                  Architecture to build CC for

Options:
  -h, --help                              Show usage (this page)
  -t, --tool-dir=DIR                      Where to install cross-compiler tools.
                                            (Default: $HOME/opt/cross)
  -s, --source-dir=DIR                    Where to download GCC/Binutils source code, if needed.
                                            (Default: $HOME/src)
  --gcc-build=--args,--no,--spaces        Additional arguments to pass when configuring GCC
  --gcc-build=--args,--no,--spaces        Additional arguments to pass when configuring Binutils

Examples:
xbuild.sh i386
xbuild.sh --gcc-build=--disable-nls,--enable-languages=c --bin-build=--disable-werror x86_64-pc-linux-gnu
xbuild.sh --tool-dir=$HOME/Desktop/tools --source-dir=/tmp/source i686-elf arm-eabi
```
#### After setting source and tool directories, **xbuild** performs the following actions:
1. Installs *build-essential* package (if the system doesnt already have GCC, Make, libc6-dev, etc.)
2. Installs general cross-compiler dependencies: *bison*, *flex*, *libgmp3-dev*, *libmpc-dev*, *libmpfr-dev*, and *texinfo*.
3. Downloads/unzips GCC/Binutils source code, if necessary.
4. Builds GCC and Binutils tools, installing them in the directory defined by *-t*,*--tool-dir*
## GCC/Binutils Configuration
Configuration flags are customizable in ***xbuild***. See link below for details.<br/>
[GCC Config Documentation](https://gcc.gnu.org/install/configure.html)<br/>
## Issues
- GCC/Binutils download URLs are currently hardcoded in, which could become an issue in the future.
- Downloading GCC/Binutils source code takes forever. Nothing I can really do about it, but it does.
- Building GCC also takes forever. See point about download time.
 ## To do
- Automatically download most recent version of GCC/Binutils. Retrieve names dynamically. (Currently hardcoded)
- Check if sources are already installed before downloading, as it takes forever.
