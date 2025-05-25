# TP 3

Armar la GIC, BNF, EBNF y ABNF para UN LENGUAJE ESOTÉRICO

# FROM HERE TO THERE

## BNF

```
<program>       ::= <line>

<line>          ::= <format-line> <endl> <line>
                 | <format-line> <endl>

<format-line>   ::= "FROM " <from> " TO " <to>

<from>          ::= "LINE"
                 | "IN"
                 | <file>
                 | <int>
                 | <str>
                 | <id>

<to>            ::= "LINE"
                 | "OUT"
                 | "ERR"
                 | <file>
                 | <int>
                 | <str>
                 | <id>
                 | <varexpr>

<file>          ::= "<" <file-fe> <file-se> <file-ne> ">"

<file-fe>       ::= "~"
                 | "."
                 | <id>

<file-se>       ::= "/" <file-se>
                 | <id> <file-se>
                 | <id>
                 | "/"

<file-ne>       ::= "." <file-se>
                 | <id> <file-se>
                 | <id>
                 | "."

<int>           ::= <number> <int>
                 | <number>

<str>           ::= <letter> <str>
                 | <letter>

<varexpr>       ::= <id> <operator> <id>
                 | <id> <operator> <int>

<operator>      ::= "+"
                 | "-"
                 | "*"
                 | "/"

<letter>        ::= "a" | "b" | ... | "z"
                 | "A" | "B" | ... | "Z"

<number>        ::= "1" | "2" | ... | "0"

<id>            ::= <str> <int>
                 | "_" <str> <int>
                 | <str>
                 | "_" <id>

<endl>          ::= ";"


```



## EBNF

```
<program>       ::= { <format-line> <endl> }+

<format-line>   ::= "FROM " <from> " TO " <to>

<from>          ::= "LINE"
                 | "IN"
                 | <file>
                 | <int>
                 | <str>
                 | <id>

<to>            ::= "LINE"
                 | "OUT"
                 | "ERR"
                 | <file>
                 | <int>
                 | <str>
                 | <id>
                 | <varexpr>

<file>          ::= "<" <file-fe> <file-se> <file-ne> ">"

<file-fe>       ::= "~" | "." | <id>

<file-se>       ::= { "/" | <id> }* 
                 | <id> 
                 | "/"

<file-ne>       ::= { "." | <id> }*
                 | <id> 
                 | "."

<int>           ::= { <number> }+

<str>           ::= { <letter> }+

<varexpr>       ::= <id> <operator> <id>
                 | <id> <operator> <int>

<operator>      ::= "+" | "-" | "*" | "/"

<letter>        ::= "a" | "b" | ... | "z"
                 | "A" | "B" | ... | "Z"

<number>        ::= "0" | "1" | ... | "9"

<id>            ::= <str> <int>
                 | "_" <str> <int>
                 | <str>
                 | "_" <id>

<endl>          ::= ";"

```


## ABNF

```
### Símbolo inicial
<program>

### Producciones

<program>      ::= <line>

<line>         ::= { <format-line> <endl> }

<format-line>  ::= "FROM " <from> " TO " <to>

<from>         ::= "LINE"
                | "IN"
                | <file>
                | <int>
                | <str>
                | <id>

<to>           ::= "LINE"
                | "OUT"
                | "ERR"
                | <file>
                | <int>
                | <str>
                | <id>
                | <varexpr>

<file>         ::= "<" ( <file-fe> | <file-se> | <file-ne> ) ">"

<file-fe>      ::= "~"
                | "."
                | <id>

<file-se>      ::= "/" <file-se>
                | <id> <file-se>
                | <id>
                | "/"

<file-ne>      ::= "." <file-se>
                | <id> <file-se>
                | <id>
                | "."

<int>          ::= { <number> }

<str>          ::= { <letter> }

<varexpr>      ::= <id> <operator> <id>
                | <id> <operator> <int>

<operator>     ::= "+"
                | "-"
                | "*"
                | "/"

<letter>       ::= uno de: "a"–"z" | "A"–"Z"

<number>       ::= uno de: "0"–"9"

<id>           ::= <str> <int>
                | "_" <str> <int>
                | <str>
                | "_" <id>

<endl>         ::= ";"

```

## GIC

```
S -> Li
Li -> Fl E Li | Fl E
Fl -> "FROM " F " TO " T
F -> "LINE" | "IN" | Fi | In | St | Id
T -> "LINE" | "OUT" | "ERR" | Fi | In | St | Id | Ve
Fi -> "<" Ff Fs Fn ">"
Ff -> "~" | "." | Id
Fs -> "/" Fs | Id Fs | Id | "/"
Fn -> "." Fs | Id Fs | Id | "."
In -> N In | N
St -> L St | L
Ve -> Id O Id | Id O In
O -> "+" | "-" | "*" | "/"
L -> "a" | "b" | ... | "z" | "A" | "B" | ... | "Z"
N -> "1" | "2" | ... | "0"
Id -> St In | "_" St In | St | "_" Id
E -> ";"
```


