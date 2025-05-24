# Binding en Parámetros: Estático vs Dinámico

Esta tabla resume los distintos tipos de binding que pueden aplicarse a los parámetros en lenguajes de programación, diferenciando entre binding estático y dinámico, junto con ejemplos en código reales para cada caso.

## Tabla de Binding para Parámetros (con ejemplos)

| **Binding**                                     | **¿Qué es?**                                                                           | **Estático**                                           | **Dinámico**                                    | **Ejemplo estático**                                                                                          | **Ejemplo dinámico**                                                                                             |
| ----------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **De valor**                                    | Valor pasado al parámetro al momento de llamar a la función (copiado o referenciado)   | C, Java (primitivos), Pascal                           | Python, JavaScript, Ruby, Lisp                  | `c\nvoid f(int x) { x = x + 1; }\nint main() { int n = 5; f(n);\nprintf("%d", n); }  // Imprime 5`            | `python\ndef f(x): x = x + 1\nn = 5\nf(n)\nprint(n)  # 5, no se modifica`                                        |
| **De tipo**                                     | Tipo de dato permitido por el parámetro                                                | Java, C++, Kotlin (tipado fuerte y estático)           | Python, JavaScript, PHP (tipado débil/dinámico) | `java\nvoid saludar(String nombre) {\n  System.out.println(\"Hola \" + nombre);\n}`                           | `python\ndef saludar(nombre):\n    print(\"Hola \" + str(nombre))\nsaludar(123)  # Acepta número y lo convierte` |
| **De nombre**                                   | Nombre del identificador dentro del cuerpo de la función                               | Todos los lenguajes con funciones nombradas            | No aplica                                       | `java\nint sumar(int a, int b) {\n  return a + b;\n}`                                                         | `python\ndef sumar(a, b):\n    return a + b\nsumar(2, 3)  # a y b solo viven dentro de la función`               |
| **De posición o asociación**                    | Forma de enlazar los argumentos a los parámetros formales (por posición, nombre, etc.) | C, Java, Pascal (por posición)                         | Python, Ruby, Lua (soporta posición y nombre)   | `java\nvoid f(int x, int y) {\n  System.out.println(x + y);\n}\nf(3, 5);`                                     | `python\ndef f(x, y):\n    print(x, y)\nf(3, y=2)  # mezcla de posición y nombre`                                |
| **De dirección o referencia**                   | Si se pasa por referencia (modificable) o por valor (copiado)                          | C++ (referencia `&`), Fortran (`INOUT`)                | Python (depende si el objeto es mutable)        | `cpp\nvoid f(int& x) {\n  x++;\n}\nint main() {\n  int a = 5;\n  f(a);\n  cout << a;  // 6\n}`                | `python\ndef modificar(lista):\n    lista.append(1)\nl = [0]\nmodificar(l)\nprint(l)  # [0, 1]`                  |
| **De tiempo de evaluación (binding del valor)** | Cuándo se evalúa el valor del argumento                                                | Lenguajes eager (evaluación estricta): C, Java, Python | Lazy (evaluación diferida): Haskell             | `java\nint cuadrado(int x) {\n  return x * x;\n}\nint r = cuadrado(3 + 2);  // Se evalúa 3+2 antes de llamar` | `haskell\nf x = 1\nmain = print (f (undefined))  -- OK, no evalúa undefined`                                     |

## 🔧 Diagrama: Binding Estático vs Dinámico en Parámetros

            +---------------------------+                +---------------------------+
            |     Parámetros Estáticos  |                |    Parámetros Dinámicos   |
            +---------------------------+                +---------------------------+
                       |                                           |
        +--------------v---------------+           +---------------v--------------+
        | BINDING ESTÁTICO EN PARÁMS   |           | BINDING DINÁMICO EN PARÁMS   |
        +------------------------------+           +------------------------------+
        | Se determina en compilación  |           | Se decide en ejecución       |
        | - Copiado por valor          |           | - Tipo y valor pueden variar |
        | - Tipado estricto            |           | - Se permite inferencia      |
        | - No muta el original (en C) |           | - Puede mutar si es mutable  |
        +------------------------------+           +------------------------------+
                       |                                           |
                       |                                           |
        +--------------v---------------+           +---------------v--------------+
        | Ej: Java, C (primitivos)     |           | Ej: Python, JavaScript, Ruby |
        +------------------------------+           +------------------------------+

## 📌 Resumen: Binding Estático y Dinámico en Variables

El **binding** (o ligadura) es el momento en que se asocia una **variable** con alguno de sus **atributos**, como su tipo, valor, nombre, ubicación en memoria, alcance, etc.

### Tipos de Binding según el Momento

| **Tipo de binding** | **¿Cuándo ocurre?**      | **Características**                                           | **Ejemplos**                         |
| ------------------- | ------------------------ | ------------------------------------------------------------- | ------------------------------------ |
| **Estático**        | En tiempo de compilación | Más seguro, predecible, permite detección temprana de errores | `int x = 5;` en C, Java              |
| **Dinámico**        | En tiempo de ejecución   | Más flexible, pero menos seguro; puede cambiar tipo y valor   | `x = "hola"` luego `x = 5` en Python |

### Atributos que pueden tener binding:

- **Tipo**: qué valores puede contener (int, float, string, etc.)
- **Valor**: el contenido actual de la variable
- **Alcance (scope)**: desde qué partes del código es accesible
- **Nombre**: cómo se referencia (identificador)
- **Almacenamiento**: dónde está ubicada en memoria
- **Tiempo de vida**: desde que se crea hasta que se destruye

### 💡 Ejemplo en C

```c
const int n = 5;         // Binding de tipo, nombre y valor (estático)
int x;                   // Binding de tipo y nombre (estático)
double f(int n) { ... }  // Binding de función, parámetro, tipo y nombre (estático)
```

## 🔍 Diagrama: Binding Estático vs Dinámico

            +-------------------------+                +--------------------------+
            |     Tiempo de Compilación|               |     Tiempo de Ejecución  |
            +-------------------------+                +--------------------------+
                       |                                         |
        +--------------v--------------+           +--------------v---------------+
        |      BINDING ESTÁTICO       |           |      BINDING DINÁMICO        |
        +-----------------------------+           +-------------------------------+
        | Se fija antes de ejecutar   |           | Se resuelve en tiempo real    |
        | - Tipo de variable          |           | - Tipo puede cambiar          |
        | - Nombre                    |           | - Valor puede cambiar         |
        | - Alcance                   |           | - Puede depender de contexto  |
        | - Almacenamiento            |           | - Más flexible pero riesgoso  |
        +-----------------------------+           +-------------------------------+
                       |                                         |
                       |                                         |
        +--------------v--------------+           +--------------v---------------+
        |   Ej: C, Java, Pascal        |           |   Ej: Python, JS, Lisp        |
        +-----------------------------+           +-------------------------------+
