6. Meta-data File Header EBNF
===============================

## 6.1 Common Header Format
---------------------------

All EDK II INF, DEC, DSC and FDF files should include this header. For
completeness, the optional sections Abstract and Description should be
completed prior to creating an UEFI Distribution Package.

#### Prototype

```ini
<CommonHeader>   ::= <Comment>*
                     "##" [<Space>] <Space> "@file" [<TS> <Filename>] <EOL>
                     [<Abstract>]
                     [<Description>]
                     <Copyright>+
                     "#" <EOL>
                     <License>+
                     "##" <EOL>+

<Abstract>       ::= "#" <MTS> <AsciiString> <EOL>
                     ["#" <EOL>]

<Description>    ::= ["#" <MTS> <AsciiString> <EOL>]+
                     ["#" <EOL>]

<Copyright>      ::= "#" <MTS> <CopyName> <Date> "," <CompInfo>

<CopyName>       ::= ["Portions" <MTS>] "Copyright (c)" <MTS>

<Date>           ::= <Year> [<TS> {<DateList>} {<DateRange>}]

<Year>           ::= "2" (0-9)(0-9)(0-9)

<DateList>       ::= <CommaSpace> <Year> [<CommaSpace> <Year>]*

<DateRange>      ::= "-" <TS> <Year>

<CompInfo>       ::= (0x20 - 0x7e)* <MTS> "All rights reserved." [<TS> "<BR>"] <EOL>

<License>        ::= ["#" <MTS> <AsciiString> <EOL>]+
                     ["#" <EOL>]
```

#### Parameters

*Abstract*

<p>
A brief one line description of what the module does.
<ul>
<li>The INF or DEC file will always have an English version of the Abstract. 
Other localized versions of the abstract must be stored in a Multi-string UNI 
file that is specified in the <code>[Defines]</code> section's 
<code>`MODULE_UNI_FILE</code>` entry in INF files or 
<code>`PACKAGE_UNI_FILE</code> entry in DEC files.</li></ul>
</p>

*Description*
<p>
A detailed description of what the module does.
<ul>
<li>The INF or DEC file will always have an English version of the 
Description. Other localized versions of the description must be stored in
a Multi-string UNI file that is specified in the <code>[Defines]</code> 
section's <code>MODULE_UNI_FILE</code> entry in INF files or 
<code>PACKAGE_UNI_FILE</code> entry in DEC files.</li></ul>
</p>

*Copyright*
<p>
The copyright date should be modified if there is a functional change to the 
source code or meta-data file. Copyright data will not be localized.
</p>

*License*
<p>
One or more licenses that the module with source code is released under. 
License content will not be localized.
</p>

## 6.2 Binary Header Format
---------------------------

This optional header is valid for INF and DEC file only. It must
immediately follow the common header.

#### Prototype

```ini
<BinaryHeader>       ::= <Comment>*
                         "##" [<Space>] <Space> "@BinaryHeader" <EOL>
                         <BinaryAbstract>
                         "#" <EOL>
                         <BinaryDescription>
                         "#" <EOL>
                         <Copyright>+
                         "#" <EOL>
                         <BinaryLicense>+
                         "##" <EOL>+

<BinaryAbstract>     ::= "#" <MTS> <AsciiString> <EOL>

<BinaryDescription>  ::= ["#" <MTS> <AsciiString> <EOL>]+

<BinaryLicense>      ::= ["#" <MTS> <AsciiString> <EOL>]+
                         ["#" <EOL>]
```

#### Parameters

*@BinaryHeader*
<p>
In a Binary or AsBuilt INF or a DEC file, this Doxygen tag must not be 
present.
</p>

*BinaryAbstract*
<p>
A brief one line description of what the module does that may be 
different from a source abstract.<ul>
<li>The INF or DEC file will always have an English version of the 
Abstract. Other localized versions of the abstract must be stored in a 
Multi-string UNI file that is specified in the <code>[Defines]</code> 
section's <code>MODULE_UNI_FILE</code> entry in INF files or 
<code>PACKAGE_UNI_FILE</code> entry in DEC files.</li></ul>
</p>

*BinaryDescription*
<p>
A detailed description of what the module does that may be different from 
a source description.<ul>
<li>The INF or DEC file will always have an English version of the 
Description. Other localized versions of the description must be stored in
a Multi-string UNI file that is specified in the <code>[Defines]</code> 
section's <code>MODULE_UNI_FILE</code> entry in INF files or 
<code>PACKAGE_UNI_FILE</code> entry in DEC files.</li></ul>
</p>

*Copyright*
<p>
The copyright date should be modified if there is a functional change to 
the source code. Since binaries are constructed from source, the binary 
file may have the same copyright date as the source INF. Copyright data 
will not be localized.
</p>

*License*
<p>
One or more licenses that the binary module or package is released under. 
License content will not be localized.
</p>


## 6.3 As Built INF Header Format
--------------------------------
The AsBuilt INF is generated by the EDK II build tools.

#### Prototype

```ini
<AsBuiltHeader>  ::= <Comment>*
                     "##" [<Space>] <Space> "@file" <EOL>
                     [{<BinaryAbstract>} {<Abstract>}]
                     "#" <EOL>
                     [{<BinaryDescription>} {<Description>}]
                     "#" <EOL>
                     <Copyright>+
                     "#" <EOL>
                     {<BinaryLicense>+} {<License>+}
                     "##" <EOL>+
                     <EOL>
                     "# DO NOT EDIT" <EOL>
                     "# FILE auto-generated" <EOL>
                     <EOL>
```
