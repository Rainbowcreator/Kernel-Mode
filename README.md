# Kernel-Mode
Based on x86-64 and ARM PC,System plug-ins outside of Linux,Can be used to maintain the system Different from Linux liveIt can be used directly locally through GRUB

# Table of Contents  
- [Project Introduction](#project-introduction)  
- [Project Status](#project-status)  
- [Directory Structure](#directory-structure)  
- [Quick Start](#quick-start)  
- [Contribution Guide](#contribution-guide)  
- [Developer Documentation](#developer-documentation)

# KM (Kernel Mode) Project
An independent kernel-mode system separated from the Linux root directory, built in phases to integrate a lightweight tool ecosystem.

## Project Status
- Phase 1: Minimal bootable system (80% complete)
- Goal: Integrate 900+ tools with graphical support

## Directory Structure
 
 
```txt
KM/
├── Boot/         # Boot core components
├── RootFS/       # Independent root file system
├── Build/        # Build scripts & configs
└── Docs/         # Documentation
```


## Quick Start
1. Compile kernel: `cd Build && ./build_kernel.sh`
2. Package root file system: `./build_rootfs.sh`
3. Test: Boot with QEMU or VirtualBox

## Contribution
- Submit issues for bug reports/feature requests
- Send pull requests for code improvements
- Expand toolset (see `Build/tool_list.txt`)


# KM Project Contribution Guide

## How to Contribute
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-tool`
3. Commit changes: `git commit -m 'Add top tool'`
4. Push to branch: `git push origin feature/new-tool`
5. Submit a pull request

## Code Style
- Use POSIX Shell for scripts
- Follow Linux kernel coding style for C code
- Add copyright header to all files:
  ```c
  /*
   * Copyright (C) 2025 KM Project
   * Licensed under GPLv3
   */


#### Developer Documentation (Docs/developer.md)
```markdown
# KM Developer Manual

## Kernel Customization Guide
1. Modify `Build/config/kernel.config`
2. Run `Build/scripts/build_kernel.sh` to compile
3. Key kernel config options:
   - `CONFIG_INITRAMFS_SOURCE="RootFS/"`
   - `CONFIG_EXT4_FS=y` (enable ext4 filesystem)
   - `CONFIG_SERIAL_8250=y` (serial port for debugging)

## Tool Compilation Tips
1. Static compilation: `gcc -static -o tool tool.c`
2. Dependency check: `ldd tool | grep -v "not found"`
3. Reduce binary size: `strip tool`
