5. Meta-Data File Headers
=========================

This section defines the EBNF syntax for EDK II INF, DEC, DSC and FDF
files. While this header section is not needed by the EDK II build
system, the headers in the INF files will be used by the build tools for
generating "As Built" INF files from sources. For both INF and DEC
files, these sections are used by the UEFI Packaging Tool (UEFIPT) that
is included with the EDK II build system binaries.

### Summary

This section contains Copyright and License notices for the INF file in
comments that start the file. This section is optional using a format
of:

```C
## @file
# Abstract
#
# Description
#
# Copyright
#
# License
#
##

```

## 5.1 Source and Binary INF and DEC File Header Format
-------------------------------------------------------

### Prototype

```ini
<Header> ::= <CommonHeader> [<BinaryHeader>]
```

### Example

```C
## @file  MdePkg.dec
# This Package provides all definitions, library classes and libraries instances.
#
# It also provides the definitions(including PPIs/PROTOCOLs/GUIDs) of
# EFI1.10/UEFI2.5/PI1.4 and some Industry Standards.
#
# Copyright (c) 2007 - 2015, Intel Corporation. All rights reserved.<BR>
# Portions copyright (c) 2008 - 2009, Apple Inc. All rights reserved.<BR>
#
# This program and the accompanying materials are licensed and made available under
# the terms and conditions of the BSD License which accompanies this distribution.
# The full text of the license may be found at
# http://opensource.org/licenses/bsd-license.php
#
# THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS" BASIS,
# WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED.
#
##

[Defines]

```

## 5.2 DSC and FDF File Header Format
-------------------------------------

### Prototype

```ini
<Header> ::= <CommonHeader>
```

### Example

```C
## @file
# EFI/PI MdePkg Package
#
# Copyright (c) 2007 - 2016, Intel Corporation. All rights reserved.<BR>
# Portions copyright (c) 2008 - 2009, Apple Inc. All rights reserved.<BR>
#
#    This program and the accompanying materials
#    are licensed and made available under the terms and conditions of the BSD License
#    which accompanies this distribution. The full text of the license may be found at
#    http://opensource.org/licenses/bsd-license.php
#
#    THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS" BASIS,
#    WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED.
#
##

[Defines]

```

## 5.3 As Built INF Header Format
---------------------------------

### Prototype

```ini
<Header> ::= <AsBuiltHeader>
```

### Example

```C
## @file
#  ATA Bus driver to enumerate and identfy ATA devices.
#
#  This driver follows UEFI driver model and layers on ATA Pass Thru protocol defined
#  in UEFI spec 2.2. It installs Block IO and Disk Info protocol for each ATA device
#  it enumerates and identifies successfully.
#
#  Copyright (c) 2009 - 2015, Intel Corporation. All rights reserved.<BR>
#
#  This program and the accompanying materials
#  are licensed and made available under the terms and conditions of the BSD License
#  which accompanies this distribution. The full text of the license may be found at
#  http://opensource.org/licenses/bsd-license.php
#  THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS" BASIS,
#  WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED.
#
#
##

# DO NOT EDIT
# FILE auto-generated

[Defines]

```


