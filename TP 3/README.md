# TP 3

Armar la GIC, BNF, EBNF y ABNF para UN LENGUAJE ESOTÉRICO

# LOLCODE

## BNF

```
<programa> ::= "HAI" [<version>] <sentencias> "KTHXBYE"

<version> ::= número

<sentencias> ::= <sentencia>
               | <sentencia> <sentencias>

<sentencia> ::= <comentario_simple>
              | <comentario_multilinea>
              | <inclusion_libreria>
              | <declaracion>
              | <asignacion>
              | <impresion>
              | <entrada>
              | <comparacion>
              | <operacion>
              | <concatenacion>
              | <conversion>
              | <conversor_tipo_var>
              | <if_statement>
              | <switch_statement>
              | <loop>
              | <salir_bucle>

<comentario_simple> ::= "BTW" texto

<comentario_multilinea> ::= "OBTW" texto "TLDR"

<inclusion_libreria> ::= "CAN HAS" identificador "?"

<declaracion> ::= "I HAS A" identificador
                | "I HAS A" identificador "ITZ" <valor>
                | "I HAS A" identificador "ITZ A" <tipo>
                | "I HAS A" identificador "ITZ LIEK A" identificador

<asignacion> ::= identificador "R" <valor>
               | identificador "R" <conversion_completa>

<entrada> ::= "GIMMEH" identificador

<impresion> ::= "VISIBLE" <valor> ["!"]

<comparacion> ::= "BOTH SAEM" <expresion> "AN" <expresion>
                | "DIFFRINT" <expresion> "AN" <expresion>
                | "BIGGR OF" <expresion> "AN" <expresion>
                | "SMALLR OF" <expresion> "AN" <expresion>

<operacion> ::= "SUM OF" <expresion> "AN" <expresion>
              | "DIFF OF" <expresion> "AN" <expresion>
              | "PRODUKT OF" <expresion> "AN" <expresion>
              | "QUOSHUNT OF" <expresion> "AN" <expresion>
              | "MOD OF" <expresion> "AN" <expresion>

<concatenacion> ::= "SMOOSH" <argumentos_concatenacion> "MKAY"

<argumentos_concatenacion> ::= <expresion>
                             | <expresion> "AN" <argumentos_concatenacion>

<conversion> ::= "MAEK" <expresion> "A" <tipo>

<conversion_completa> ::= "MAEK" identificador "A" <tipo>

<conversor_tipo_var> ::= identificador "IS NOW A" <tipo>

<if_statement> ::= <expresion> "," "O RLY?"
                   "YA RLY" <sentencias>
                   ["NO WAI" <sentencias>]
                   "OIC"

<switch_statement> ::= <expresion> "," "WTF?" <casos> "OIC"

<casos> ::= <caso>
          | <caso> <casos>
          | <default_case>

<caso> ::= "OMG" <literal> <sentencias> ["GTFO"]

<default_case> ::= "OMGWTF" <sentencias>

<loop> ::= "IM IN YR" identificador <bucle_opciones> <sentencias> "IM OUTTA YR" identificador

<bucle_opciones> ::= [("UPPIN" | "NERFIN") "YR" identificador ("TIL" | "WILE") <expresion>]

<salir_bucle> ::= "GTFO"

<valor> ::= <literal>
          | identificador
          | <operacion>
          | <concatenacion>
          | <conversion>

<expresion> ::= <valor>
              | <comparacion>

<literal> ::= número
           | cadena

<tipo> ::= "NOOB"
         | "NUMBR"
         | "NUMBAR"
         | "YARN"
         | "TROOF"
         | "BUKKIT"

<identificador> ::= combinación de letras y números que empieza con letra

```



## GIC

```
Programa → HAI VersionOpt Sentencias KTHXBYE

VersionOpt → Version | ε

Version → Número

Sentencias → Sentencia
           | Sentencia Sentencias

Sentencia → ComentarioSimple
           | ComentarioMultilinea
           | InclusionLibreria
           | Declaracion
           | Asignacion
           | Impresion
           | Entrada
           | Comparacion
           | Operacion
           | Concatenacion
           | Conversion
           | ConversionVar
           | IfStatement
           | SwitchStatement
           | Bucle
           | SalirBucle

ComentarioSimple → BTW Texto

ComentarioMultilinea → OBTW Texto TLDR

InclusionLibreria → CAN HAS Identificador ?

Declaracion → I HAS A Identificador
            | I HAS A Identificador ITZ Valor
            | I HAS A Identificador ITZ A Tipo
            | I HAS A Identificador ITZ LIEK A Identificador

Asignacion → Identificador R Valor
           | Identificador R ConversionCompleta

Entrada → GIMMEH Identificador

Impresion → VISIBLE Valor ExclamacionOpt

ExclamacionOpt → ! | ε

Comparacion → BOTH SAEM Expresion AN Expresion
             | DIFFRINT Expresion AN Expresion
             | BIGGR OF Expresion AN Expresion
             | SMALLR OF Expresion AN Expresion

Operacion → SUM OF Expresion AN Expresion
          | DIFF OF Expresion AN Expresion
          | PRODUKT OF Expresion AN Expresion
          | QUOSHUNT OF Expresion AN Expresion
          | MOD OF Expresion AN Expresion

Concatenacion → SMOOSH ArgumentosConcatenacion MKAY

ArgumentosConcatenacion → Expresion
                         | Expresion AN ArgumentosConcatenacion

Conversion → MAEK Expresion A Tipo

ConversionCompleta → MAEK Identificador A Tipo

ConversionVar → Identificador IS NOW A Tipo

IfStatement → Expresion , O RLY? YaBloque NoBloqueOpt OIC

YaBloque → YA RLY Sentencias

NoBloqueOpt → NO WAI Sentencias | ε

SwitchStatement → Expresion , WTF? Casos OIC

Casos → Caso
      | Caso Casos
      | DefaultCase

Caso → OMG Literal Sentencias GtfoOpt

GtfoOpt → GTFO | ε

DefaultCase → OMGWTF Sentencias

Bucle → IM IN YR Identificador BucleOpcionesOpt Sentencias IM OUTTA YR Identificador

BucleOpcionesOpt → IteracionCondicional | ε

IteracionCondicional → (UPPIN | NERFIN) YR Identificador (TIL | WILE) Expresion

SalirBucle → GTFO

Valor → Literal
      | Identificador
      | Operacion
      | Concatenacion
      | Conversion

Expresion → Valor
           | Comparacion

Literal → Número
        | Cadena

Tipo → NOOB
     | NUMBR
     | NUMBAR
     | YARN
     | TROOF
     | BUKKIT

Identificador → Letra LetrasDigitosOpt

LetrasDigitosOpt → LetraDigito LetrasDigitosOpt | ε

LetraDigito → Letra | Digito


```


## EBNF

```
programa ::= "HAI" [ version ] sentencias "KTHXBYE"

version ::= número

sentencias ::= sentencia { sentencia }

sentencia ::= comentarioSimple
            | comentarioMultilinea
            | inclusionLibreria
            | declaracion
            | asignacion
            | impresion
            | entrada
            | comparacion
            | operacion
            | concatenacion
            | conversion
            | conversionVar
            | ifStatement
            | switchStatement
            | bucle
            | salirBucle

comentarioSimple ::= "BTW" texto

comentarioMultilinea ::= "OBTW" texto "TLDR"

inclusionLibreria ::= "CAN HAS" identificador "?"

declaracion ::= "I HAS A" identificador [ "ITZ" (valor | "A" tipo | "LIEK A" identificador) ]

asignacion ::= identificador "R" (valor | conversionCompleta)

entrada ::= "GIMMEH" identificador

impresion ::= "VISIBLE" valor [ "!" ]

comparacion ::= "BOTH SAEM" expresion "AN" expresion
              | "DIFFRINT" expresion "AN" expresion
              | "BIGGR OF" expresion "AN" expresion
              | "SMALLR OF" expresion "AN" expresion

operacion ::= "SUM OF" expresion "AN" expresion
           | "DIFF OF" expresion "AN" expresion
           | "PRODUKT OF" expresion "AN" expresion
           | "QUOSHUNT OF" expresion "AN" expresion
           | "MOD OF" expresion "AN" expresion

concatenacion ::= "SMOOSH" argumentosConcatenacion "MKAY"

argumentosConcatenacion ::= expresion { "AN" expresion }

conversion ::= "MAEK" expresion "A" tipo

conversionCompleta ::= "MAEK" identificador "A" tipo

conversionVar ::= identificador "IS NOW A" tipo

ifStatement ::= expresion "," "O RLY?" yaBloque [ noBloque ] "OIC"

yaBloque ::= "YA RLY" sentencias

noBloque ::= "NO WAI" sentencias

switchStatement ::= expresion "," "WTF?" casos "OIC"

casos ::= { caso } [ defaultCase ]

caso ::= "OMG" literal sentencias [ "GTFO" ]

defaultCase ::= "OMGWTF" sentencias

bucle ::= "IM IN YR" identificador [ bucleOpciones ] sentencias "IM OUTTA YR" identificador

bucleOpciones ::= ( "UPPIN" | "NERFIN" ) "YR" identificador ( "TIL" | "WILE" ) expresion

salirBucle ::= "GTFO"

valor ::= literal
       | identificador
       | operacion
       | concatenacion
       | conversion

expresion ::= valor
           | comparacion

literal ::= número
         | cadena

tipo ::= "NOOB" | "NUMBR" | "NUMBAR" | "YARN" | "TROOF" | "BUKKIT"

identificador ::= letra { letra | digito }




```



## ABNF

```
programa = "HAI" [ version ] sentencias "KTHXBYE"

version = 1*DIGIT "." 1*DIGIT

sentencias = 1*sentencia

sentencia = comentarioSimple
          / comentarioMultilinea
          / inclusionLibreria
          / declaracion
          / asignacion
          / impresion
          / entrada
          / comparacion
          / operacion
          / concatenacion
          / conversion
          / conversionVar
          / ifStatement
          / switchStatement
          / bucle
          / salirBucle

comentarioSimple = "BTW" SP texto

comentarioMultilinea = "OBTW" SP texto "TLDR"

inclusionLibreria = "CAN HAS" SP identificador "?"

declaracion = "I HAS A" SP identificador
            [ SP "ITZ" SP ( valor / "A" SP tipo / "LIEK A" SP identificador ) ]

asignacion = identificador SP "R" SP ( valor / conversionCompleta )

entrada = "GIMMEH" SP identificador

impresion = "VISIBLE" SP valor [ "!" ]

comparacion = ( "BOTH SAEM" / "DIFFRINT" / "BIGGR OF" / "SMALLR OF" )
              SP expresion SP "AN" SP expresion

operacion = ( "SUM OF" / "DIFF OF" / "PRODUKT OF" / "QUOSHUNT OF" / "MOD OF" )
            SP expresion SP "AN" SP expresion

concatenacion = "SMOOSH" SP argumentosConcatenacion "MKAY"

argumentosConcatenacion = expresion *( SP "AN" SP expresion )

conversion = "MAEK" SP expresion SP "A" SP tipo

conversionCompleta = "MAEK" SP identificador SP "A" SP tipo

conversionVar = identificador SP "IS NOW A" SP tipo

ifStatement = expresion "," SP "O RLY?" CRLF yaBloque [ noBloque ] "OIC"

yaBloque = "YA RLY" CRLF sentencias

noBloque = "NO WAI" CRLF sentencias

switchStatement = expresion "," SP "WTF?" CRLF casos "OIC"

casos = 1*(caso) [ defaultCase ]

caso = "OMG" SP literal CRLF sentencias [ "GTFO" ]

defaultCase = "OMGWTF" CRLF sentencias

bucle = "IM IN YR" SP identificador [ bucleOpciones ] CRLF
        sentencias "IM OUTTA YR" SP identificador

bucleOpciones = ( "UPPIN" / "NERFIN" ) SP "YR" SP identificador
                SP ( "TIL" / "WILE" ) SP expresion

salirBucle = "GTFO"

valor = literal
      / identificador
      / operacion
      / concatenacion
      / conversion

expresion = valor
          / comparacion

literal = número
        / cadena

tipo = "NOOB" / "NUMBR" / "NUMBAR" / "YARN" / "TROOF" / "BUKKIT"

identificador = ALPHA *( ALPHA / DIGIT )

número = [ "+" / "-" ] 1*DIGIT

cadena = DQUOTE *(%x20-21 / %x23-7E) DQUOTE

texto = *(%x20-7E)

ALPHA = %x41-5A / %x61-7A   ; Letras A-Z o a-z
DIGIT = %x30-39             ; Dígitos 0-9
SP = %x20
CRLF = %x0D %x0A
DQUOTE = %x22


```


