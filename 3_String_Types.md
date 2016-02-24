3. String Types
===============

The following EBNF describes the different ASCII Character formats for
strings.

### Prototype

```ini
<Word>                   ::= (a-zA-Z0-9_)(a-zA-Z0-9_-.)*
                             ; Alphanumeric characters with optional
                             ; period ".", dash "-" and/or
                             ; underscore "_" characters.
                             ; A period character may not be followed by
                             ; another period character.
                             ; No white space characters are permitted.

<SimpleWord>             ::= (a-zA-Z0-9)(a-zA-Z0-9_-)*
                             ; A word that cannot contain a period character.

<ToolWord>               ::= (A-Z)(a-zA-Z0-9)*
                             ; Alphanumeric characters. white space characters
                             ; are not permitted.

<Extension>              ::= (a-zA-Z0-9_-)+
                             ; One or more alphanumeric characters.

<File>                   ::= <Word> ["." <Extension>]

<MACRO>                  ::= (A-Z)(A-Z0-9_)*

<MACROVAL>               ::= "$(" <MACRO> ")"

<PATH>                   ::= [<MACROVAL> <FileSep>] <RelativePath>

<RelativePath>           ::= <DirName> [<FileSep> <DirName>]*

<DirName>                ::= {<Word>} {<MACROVAL>}

<FullFilename>           ::= <PATH> <FileSep> <File>

<Filename>               ::= [<PATH> <FileSep>] <File>

<Chars>                  ::= (a-zA-Z0-9_)

<Digit>                  ::= (0-9)

<NonDigit>               ::= (a-zA-Z_)

<Identifier>             ::= <NonDigit> <Chars>\*

<CName>                  ::= <Identifier>
                             ; A valid C variable name.

<AsciiChars>             ::= (0x21 - 0x7E)

<EscapeSequence>         ::= "\\" {"n"} {"t"} {"f"} {"r"} {"b"} {"0"} {"\\"} {<DblQuote>}

<CChars>                 ::= [{0x21} {(0x23 - 0x5B)} {(0x5D - 0x7E)} {<EscapeSequence>}]*

<AsciiString>            ::= [ <TS>* <AsciiChars>* ]*

<EmptyString>            ::= <DblQuote> <DblQuote>

<CFlags>                 ::= <AsciiString>

<PrintChars>             ::= {<TS>} {<CChars>}

<QuotedString>           ::= <DblQuote> <PrintChars>* <DblQuote>

<CString>                ::= ["L"] <QuotedString>

<NormalizedString>       ::= <DblQuote> [{<Word>} {<Space>}]+ <DblQuote>

<GlobalComment>          ::= <WS> "#" [<AsciiString>] <EOL>+

<Comment>                ::= <TS> "#" <AsciiString> <EOL>+

<UnicodeString>          ::= "L" <QuotedString>

<PcdName>                ::= <TokenSpaceGuidCName> "." <PcdCName>

<PcdCName>               ::= <CName>

<TokenSpaceGuidCName>    ::= <CName>

<PCDVAL>                 ::= "PCD(" <PcdName> ")"

<ModuleType>             ::= {"BASE"} {"SEC"} {"PEI_CORE"} {"PEIM"}
                             {"DXE_CORE"} {"DXE_DRIVER"} {"SMM_CORE"}
                             {"DXE_RUNTIME_DRIVER"} {"DXE_SAL_DRIVER"}
                             {"DXE_SMM_DRIVER"} {"UEFI_DRIVER"}
                             {"UEFI_APPLICATION"} {"USER_DEFINED"}

<ModuleTypeList>         ::= <ModuleType> [" " <ModuleType>]*

<IdentifierName>         ::= <TS> {<MACROVAL>} {<PcdName>} <TS>

<OA>                     ::= (a-zA-Z)(a-zA-Z0-9)*

<arch>                   ::= {"IA32"} {"X64"} {"IPF"} {"EBC"} {<OA>} {"common"}
```

### Parameter Definitions

*UnicodeString*
<p>
When the <code><UnicodeString></code> element (these characters are string
literals as defined by the C99 specification: <code>L"string"</code>, not actual 
Unicode characters) is included in a value, the build tools may be 
required to expand the ASCII string between the quotation marks into a
valid UCS-2 encoded string. The build tools parser must treat all content
between the field separators (excluding white space characters around the
field separators) as ASCII literal content when generating the <i>AutoGen.c</i>
and <i>AutoGen.h</i> files.
</p>

*Comments*
<p>
Strings that appear in comments may be ignored by the build tools. An ASCII string
matching the format of the ASCII string defined by 
<code><UnicodeString></code> (<code>L"Foo"</code>, for example) that appears
in a comment must never be expanded by any tool.
</p>

*TokenSpaceGuidCName*
<p>
A word that is a valid C variable that specifies the name space for a particular PCD.
</p>

*PcdCName*
<p>
A word that is a valid C variable that specifies the name of the token number which 
a member of the name space specified by the TokenSpaceGuidCName.
</p>

*CFlags*
<p>
<code>CFlags</code>` refers to a string of valid arguments appended to the command
line of any third party or provided tool. It is not limited to just a compiler 
executable tool. MACRO values that appear in quoted strings in <code>CFlags</code>
content must not be expanded by parsing tools.
</p>

*OA*
<p>
Other Architecture - One or more user defined target architectures, such as ARM or 
PPC. The architectures listed here must have a corresponding entry in the EDK II 
meta-data file, <i>Conf/tools_def.txt</i>. Only IA32, X64 and EBC are routinely 
validated.
</p>

