2. Special Characters
=====================

The following EBNF describes the different special characters and
operator sequences that may be present in the EDK II meta-data
specification elements. In the following, values on the right side of
the ::= character sequence that start with 0x are the
hexadecimal character values.

### Prototype

```ini
<Tab>            ::= 0x09

<Space>          ::= 0x20

<TabSpace>       ::= {<Tab>} {<Space>}

<TS>             ::= <TabSpace>*

<MTS>            ::= <TabSpace>+

<CR>             ::= 0x0D

<LF>             ::= 0x0A

<CRLF>           ::= <CR> <LF>

<WhiteSpace>     ::= {<TS>} {<CR>} {<LF>} {<CRLF>}

<EOL>            ::= <TS> <CRLF>

<WS>             ::= <WhiteSpace>\*

<Eq>             ::= <TS> "=" <TS>

<FieldSeparator> ::= "|"

<FS>             ::= <TS> <FieldSeparator> <TS>

<Wildcard>       ::= "*"

<CommaSpace>     ::= "," <Space>*

<Cs>             ::= "," <Space>*

<DblQuote>       ::= 0x22

<FileSep>        ::= "/"
```
### Parameter Definitions

*EOL*
<p>
The DOS End Of Line: "0x0D 0x0A" character sequence must be used for all
EDK II meta-data files. All *Nix based tools can properly process the
DOS EOL characters. Microsoft based tools cannot process the *Nix style
EOL characters.
</p>

*FileSep*
<p>
FileSep refers to either the back slash "\" or forward slash "/"
characters that are used to separate directory names. All EDK II
meta-data files must use the "/" forward slash character when specifying
the directory portion of a filename. Microsoft operating systems, that
normally use a back slash character for separating directory names, will
interpret the forward slash character correctly.
</p>

