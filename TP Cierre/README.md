# Lenguaje de Programación - Especificación


### 🎯 Objetivo
MiLenguaje es un lenguaje de programación didáctico, simple y estructurado, orientado a representar construcciones básicas como funciones, asignaciones, bucles, condicionales y expresiones con tipos estáticos.


## Tipos de Datos

`<tipo>` = `cad` | `num` | `log`

Los tipos son:
- **cad**: cadena de caracteres
- **num**: número
- **log**: booleano

**Ejemplos:**
- `cad`: `"a"`
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

### Bucle 
```
 bucle (<var> = <num>; <condicion>; inc | dec <var>) {}
```

**Ejemplo:**
```
 bucle (i = 0; i < 10; inc i) {
  e(i)
}
```

## Condicionales


```
 Si (<expr>) {
  <contenido>
 }
```

## Funciones

El valor por defecto de un parámetro puede estar o no definido y los parámetros pueden no estar definidos.


### Función con Retorno
```
funcion <identificador>: <tipo> (parametro1: <tipo> = <cad | num | log>, ...,<tipo> parametroN) {
  <contenido_func>
  retorno <exp>
}
```

**Ejemplo:**
```
funcion ei:num(num: num = 10) {
  a(num)
  retorno 1
}
ei(5)
```

## Asignación

```
<identificador>: <tipo> = <exp>
```

**Ejemplos:**
```
test: num = 10
test2: cad = "aei"
test3: log = ver
```

## Inicio del Programa

```
$ <contenido> $$
```

**Ejemplo:**
```
$ 

funcion ao() {
 retorno print("oa")   // llamada al sistema para mostrar un mensaje en pantalla
}

$$
```

## BNF

```bnf

<programa>::= $ <vacio_contenido> $$
<vacio_contenido>::= <contenido> | λ | <contenido> <contenido>
<contenido>::=  <bucle> | <condicional> | <retornable>|  <variable> | <asignar>
<retornable>::= <funciones>  | <exp> | <print>| <inv_funcion> | <item_exp>
<print>::= print(<exp>)

<funciones>::= funcion <identificador>: <tipo> (<param>) {<vacio_contenido> retorno <retornable>}
<param>::= <identificador> : <tipo>,  <param> | <variable>, <param> | <identificador> : <tipo>  | <variable>
<inv_funcion> ::= <identificador>() |  <identificador>(<argumento>)

<bucle>::=  bucle ( <identificador> = <num>; <condicionBucle>; <direccion> <identificador>) { <vacio_contenido>}
<condicionBucle>::= <identificador> <opComparacion> <num>

<condicional>::= Si (<retornable>) { <vacio_contenido> }

<exp>::= 
 <retornable> <operador> <retornable> |
    <retornable>  <operador>  <exp>|
    <retornable> | 
    <opLogicoUn> <retornable> <operador><retornable> |
    <opLogicoUn>< <retornable><operador><exp> |
    <opLogicoUn><item_exp> |
     <identificador> <operador> <retornable> |
    <identificador> <operador><exp> |
    <identificador>


<variable>::= <identificador>:  <tipo> = <retornable> 
<asignar>::= <identificador> = <retornable>
<argumento> ::= <retornable>, <argumento> | <retornable>
<identificador>::= <letra> <identificador> | <letra>

<cad>::= "<cad_contenido>"
<cad_contenido>::= <letra> <cad_contenido> | <cad_contenido>


<item_exp> ::= <numero> | <cad> | <logico>
<operador> ::= <opArit> | <opLogicoBin>  | <opComparacion>
<numero> ::= <num><numero> | <num>
<direccion>::= inc | dec
<tipo> ::= cad | num | log
<opArit> ::= + | - | / | *
<opLogicoBin>::= yy | oo
<opLogicoUn>::= no
<opComparacion>::= < | > | <= | >= | == | !=
<logico>::=   ver | fal
<letra>::=  a|e |i | o|u
<num>::= 0 |1 |2 |3 |4 |5 |6 |7 |8 |9

```

**Ejemplo:**
```
$ 


funcion ae: num() {

 e: num = 5

a: num = 0

si (e > 0){
  
 bucle( i=0; i < 3; inc i) {
  a: num = e
  }
}

retorno a 
}

print(ae())




$

funcion ae: num(num: num = 3) {
  suma: num = 0

  si (num > 0) {
    bucle(i = 0; i < num; inc i) {
      suma: num = suma + i
    }
  }

  retorno suma
}

print(ae(5))

$$



```


### Notas importantes:

- Se puede usar cualquier operador de cualquier tipo de operador sobre cualquier tipo de dato (ej: sumar booleanos, dividir string, etc.)
- Admite programa vacío
- Solo tiene disponibles las vocales
- Acepta números de 0 a 9
- For solo hace loop sobre números
- Los TIPOS manejan todo tipo de expresiones
- Todos mis contenidos tienen retorno
- No hay asignacion vacia 



## 🔧 Características

| **Aspecto**                          | **Descripción**                                                                 |
|--------------------------------------|----------------------------------------------------------------------------------|
| **Paradigma**                        | Imperativo, estructurado                                                        |
| **Tipos de datos**                   | Primitivos: `cad`, `num`, `log`                                                 |
| **Tipado**                           | Estático, fuerte (sin coerción implícita)                                       |
| **Inferencia de tipos**             | No (siempre se debe declarar el tipo al declarar una variable)                 |
| **Asignación**                       | Sí                                                                              |
| **Nivel de abstracción**            | Bajo-medio (no soporta colecciones ni objetos, solo tipos básicos)             |
| **Independencia de la máquina**     | Sí (modelo pseudocódigo sin dependencia del sistema)                           |
| **Orientación a objetos**           | No                                                                              |
| **Sensibilidad a mayúsculas**       | No se especifica, pero se asume **no sensible** (solo letras vocales permitidas) |
| **Esotérico**                       | Sí (solo acepta vocales como identificadores, tipos extraños de operaciones)   |
| **Extensibilidad**                  | No (no permite definir nuevos tipos)                                            |
| **Modularidad**                     | Parcial (funciones sí, módulos no)                                              |
| **Concurrencia**                    | No                                                                              |
| **Gestión de errores / excepciones**| No contemplada                                                                 |
| **Gestión de memoria**              | No modelado                                                                    |
| **Modelo de ejecución**             | Interpretado (pseudocódigo, sin compilación)                                   |
| **Entrada de datos**                | No (no hay funciones explícitas de entrada)                                    |

## 🔁 Control de Flujo

| **Mecanismo**                            | **Soportado**                           |
|------------------------------------------|------------------------------------------|
| Secuencial                                | Sí                                       |
| Condicional                               | Sí (`si`)                                |
| Iterativo                                 | Sí (`bucle`)                             |
| Recursividad                              | Sí (permitida en funciones)              |
| Pasaje de parámetros                      | Por valor                                |
| Valores por defecto en parámetros         | Sí                                       |
| Funciones con retorno                     | Sí                                       |
| Saltos incondicionales (`goto`)          | No                                       |
| Saltos controlados (`break`, `continue`) | No                                       |
| Control estructurado                      | Sí                                       |
| Control no estructurado                   | No                                       |


## 📊 Ficha Técnica de MiLenguaje

| **Campo**               | **Valor**                                                                 |
|-------------------------|---------------------------------------------------------------------------|
| **Nombre**              | MiLenguaje                                                                |
| **Paradigma**           | Imperativo, Estructurado                                                  |
| **Nivel**               | Bajo-medio                                                                |
| **Dominio**             | Específico                                                                |
| **Traductor**           | Interpretado                                                              |
| **Almacenamiento**      | Estático (tipado explícito)                                               |
| **Generación**          | Cuarta                                                                    |
| **Manera de Abordar**   | Operativo                                                                 |
                                             |
| **Concurrencia**        | No                                                                         |
| **Interactividad**      | No interactivo (sin entrada de datos)                                     |
| **Realización Visual**  | Textual                                                                   |
| **Predicción Estado**   | Determinista                                                              |
| **Características**     | Sintaxis restringida, tipos estáticos, esotérico, retorno obligatorio     |
| **Dato Extra**          | Lenguaje esotérico diseñado para análisis formal y uso didáctico          |
