4. Numeric Types
================

The following shows the ASCII character formats for specifying numeric
or boolean values.

### Prototype

```ini
<HexDigit> ::= (a-fA-F0-9)

<HexByte> ::= {"0x"} {"0X"} [<HexDigit>] <HexDigit>

<HexNumber> ::= {"0x"} {"0X"} <HexDigit>+

<HexVersion> ::= "0x" [0]* <Major> <Minor>

<Major> ::= <HexDigit>? <HexDigit>? <HexDigit>? <HexDigit>

<Minor> ::= <HexDigit> <HexDigit> <HexDigit> <HexDigit>

<DecimalVersion> ::= {"0"} {(1-9) [(0-9)]*} ["." (0-9)+]

<VersionVal> ::= {<HexVersion>} {(0-9)+ "." (0-99)}

<GUID> ::= {<RegistryFormatGUID>} {<CFormatGUID>}

<RegistryFormatGUID> ::= <RHex8> "-" <RHex4> "-" <RHex4> "-" <RHex4> "-" <RHex12>

<RHex4> ::= <HexDigit> <HexDigit> <HexDigit> <HexDigit>

<RHex8> ::= <RHex4> <RHex4>

<RHex12> ::= <RHex4> <RHex4> <RHex4>

<RawH2> ::= <HexDigit>? <HexDigit>

<RawH4> ::= <HexDigit>? <HexDigit>? <HexDigit>? <HexDigit>

<OptRawH4> ::= <HexDigit>? <HexDigit>? <HexDigit>? <HexDigit>?

<Hex2> ::= {"0x"} {"0X"} <RawH2>

<Hex4> ::= {"0x"} {"0X"} <RawH4>

<Hex8> ::= {"0x"} {"0X"} <OptRawH4> <RawH4>

<Hex12> ::= {"0x"} {"0X"} <OptRawH4> <OptRawH4> <RawH4>

<Hex16> ::= {"0x"} {"0X"} <OptRawH4> <OptRawH4> <OptRawH4> <RawH4>

<CFormatGUID> ::= "{" <Hex8> <CommaSpace> <Hex4> <CommaSpace>
     <Hex4> <CommaSpace> "{"
     <Hex2> <CommaSpace> <Hex2> <CommaSpace>
     <Hex2> <CommaSpace> <Hex2> <CommaSpace>
     <Hex2> <CommaSpace> <Hex2> <CommaSpace>
     <Hex2> <CommaSpace> <Hex2> "}" "}"

<CArray> ::= "{" {<NList>} {<CArray>} "}"

<NList> ::= <HexByte> [<CommaSpace> <HexByte>]*

<RawData> ::= <TS> <HexByte> [ <Cs> <HexByte> [<EOL> <TS>] ]*

<Integer> ::= {(0-9)} {(1-9)(0-9)+}

<Number> ::= {<Integer>} {<HexNumber>}

<HexNz> ::= (\x1 - \xFFFFFFFFFFFFFFFF)

<NumNz> ::= (1-18446744073709551615)

<GZ> ::= {<NumNz>} {<HexNz>}

<TRUE> ::= {"TRUE"} {"true"} {"True"} {"0x1"} {"0x01"} {"1"}

<FALSE> ::= {"FALSE"} {"false"} {"False"} {"0x0"} {"0x00"} {"0"}

<BoolType> ::= {<TRUE>} {<FALSE>}

<UINT8> ::= {"0x"} {"0X"} (\x0 - \xFF)

<UINT16> ::= "0x"} {"0X"} (\x0 - \xFFFF)

<UINT32> ::= {"0x"} {"0X"} (\x0 - \xFFFFFFFF)

<UINT64> ::= {"0x"} {"0X"} (\x0 - \xFFFFFFFFFFFFFFFF)

<UINT8z> ::= {"0x"} {"0X"} <HexDigit> <HexDigit>

<UINT16z> ::= {"0x"} {"0X"} <HexDigit> <HexDigit> <HexDigit> <HexDigit>

<UINT32z> ::= {"0x"} {"0X"} <HexDigit> <HexDigit> <HexDigit> <HexDigit>
     <HexDigit> <HexDigit> <HexDigit> <HexDigit>

<UINT64z> ::= {"0x"} {"0X"} <HexDigit> <HexDigit> <HexDigit> <HexDigit>
     <HexDigit> <HexDigit> <HexDigit> <HexDigit> <HexDigit>
     <HexDigit> <HexDigit> <HexDigit> <HexDigit> <HexDigit>
     <HexDigit> <HexDigit>

<ShortNum> ::= (0-255)

<IntNum> ::= (0-65535)

<LongNum> ::= (0-4294967295)

<LongLongNum> ::= (0-18446744073709551615)

<NumValUint8> ::= {<ShortNum>} {<UINT8>}

<NumValUint16> ::= {<IntNum>} {<UINT16>}

<NumValUint32> ::= {<LongNum>} {<UINT32>}

<NumValUint64> ::= {<LongLongNum>} {<UINT64>}
```

### Parameter Definitions

*CArray*

<p>
All C data arrays used in PCD value fields must be byte arrays. The C 
format GUID style is a special case that is permitted in some fields 
that use the <code><CArray></code> nomenclature.
</p>


