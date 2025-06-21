# Lenguaje de Programación - Especificación

## Tipos de Datos

`<tipo>` = `cad` | `num` | `log`

Los tipos son:
- **cad**: cadena de caracteres
- **num**: número
- **log**: booleano

**Ejemplos:**
- `cad`: `"Hola"`
- `num`: `10`
- `log`: `ver`

## Expresiones

### Operadores Aritméticos
```
oper_aritmeticos = + | - | * | /
```

### Operadores Lógicos Binarios
```
oper_logicos_binario = yy | oo
```

### Operadores Lógicos Unarios
```
oper_logicos_unario = no
```

### Operadores de Comparación
```
oper_comparacion = < | > | <= | >= | == | !=
```

### Tipos de Expresiones
**Ejemplos:**
- `10 + 10`
- `ver yy fal`
- `ver oo fal`
- `10 > 0`

## Iteraciones

### Bucle For
```
for num: bucle (<var> = <num>; <condicion>; inc | dec <var>) {}
```

**Ejemplo:**
```
for num: bucle (i = 0; i < 10; inc i) {
  funncionB(i)
}
```

## Condicionales

### If
```
if: Si (<expr>) {}
```

## Funciones

El valor por defecto de un parámetro puede estar o no definido y los parámetros pueden no estar definidos.

**Ejemplo:**
```
funcion test() {
  funncionB("Hola")
}
```

### Función sin Retorno
```
funcion <identificador> (parametro1: <tipo> = <cad | num | log>, ...,<tipo> parametroN) {
  <content_func>
}
```

**Ejemplo:**
```
funcion test(num: num = 10) {
  funncionB(num)
}
```

### Función con Retorno
```
funcion <identificador>: <tipo> (parametro1: <tipo> = <cad | num | log>, ...,<tipo> parametroN) {
  <contenido_func>
  retorno <exp>
}
```

**Ejemplo:**
```
funcion test:num(num: num = 10) {
  funncionB(num)
  retorno 1
}
test(5)
```

## Asignación

```
<identificador>: <tipo> = <exp>
```

**Ejemplos:**
```
test: num = 10
test2: cad = "Hola"
test3: log = ver
```

## Inicio del Programa

```
$ <contenido> $$
```

**Ejemplo:**
```
$ 

funcion mostrar() {
  print("Hola")   // llamada al sistema para mostrar un mensaje en pantalla
}

$$
```

## BNF

```bnf
<prog> ::= $ <contenido> $$

<contenido> ::= <funciones> | <bucle> | <condicional> | <variable> | <exp> | <print> | λ

<print> ::= print(<exp>)

<variable> ::= <identificador>: <tipo> = <item_exp>

<tipo> ::= cad | num | log

<opArit> ::= + | - | * | /

<opLogicoBin> ::= yy | oo

<opLogicoUn> ::= no

<opComparacion> ::= < | > | <= | >= | == | !=

<bucle> ::= bucle ( <identificador> = <num>; <condicionBucle>; <direccion> <identificador>) { <contenido> }

<direccion> ::= inc | dec

<identificador> ::= <letra> <identificador> | <letra>

<condicionBucle> ::= <identificador> <opComparacion> <num>

<condicional> ::= si (<exp>) { <contenido> }

<exp> ::= <item_exp> <operador> <exp> | <opLogicoUn> <item_exp> | <item_exp> <operador> <item_exp> | <opLogicoUn> <item_exp> <operador> <exp> | <item_exp>

<item_exp> ::= <numero> | <identificador> | <logico>

<operador> ::= <opArit> | <opLogicoBin> | <opComparacion>

<numero> ::= <num> <numero> | <num>

<logico> ::= ver | fal

<letra> ::= a | e | i | o | u

<num> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<funciones> ::= <conRetorno> | <sinRetorno>

<conRetorno> ::= funcion <identificador>: <tipo> (<param>) { <contenido> retorno <contenido> }

<sinRetorno> ::= funcion <identificador> (<param>) { <contenido> }

<param> ::= <identificador>: <tipo>, <param> | <variable>, <param> | <identificador>: <tipo> | <variable>
```

### Notas importantes:

- Se puede usar cualquier operador de cualquier tipo de operador sobre cualquier tipo de dato (ej: sumar booleanos, dividir string, etc.)
- Admite programa vacío
- Solo tiene disponibles las vocales
- Acepta números de 0 a 9
- For solo hace loop sobre números
