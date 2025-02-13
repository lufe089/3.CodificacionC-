
# Mis primeras clases en C++ 
## C++
### ¿Qué es un lenguaje compilado?

Un **lenguaje compilado** es aquel en el que el código fuente (los archivos que escribimos con nuestra lógica) se **traduce completamente** a código máquina antes de ser ejecutado.

- **Traducción a código máquina**: Significa que el programa queda en un formato que la computadora entiende directamente (un archivo ejecutable).
- **Ejemplos**: C, C++, Rust, Go.
- En C++, escribimos archivos `.cpp` y `.h`, luego usamos un programa llamado **compilador** (por ejemplo, `g++` en Linux/Mac o MinGW en Windows) que genera un **ejecutable** (por ejemplo, `miPrograma.exe` o `./miPrograma`).

> **Compilador**: Es un programa que lee tu código fuente, lo analiza y lo transforma en un archivo binario listo para ejecutarse.

El hecho de que esté "compilado" significa que una vez creado ese ejecutable, podemos ejecutarlo sin necesidad de un intérprete en el sistema final, siempre y cuando tengamos el sistema operativo adecuado y las librerías requeridas.

---

### Comparación con un lenguaje interpretado

Los **lenguajes interpretados** (como Python, JavaScript o PHP) no producen típicamente un solo ejecutable autónomo, sino que **requieren** de un **intérprete** o **máquina virtual** para poder funcionar.

- **Intérprete**: Programa que lee el código "línea a línea" o "instrucción a instrucción" y lo va ejecutando al momento.
- **Máquina virtual**: Software que simula un entorno de ejecución, muy común en lenguajes como Java.

**Ventajas de los interpretados**:
- Mayor **flexibilidad** y **rapidez de prototipado**.
- Suelen ser más sencillos de depurar en tiempo real porque no requieren recompilar.

**Desventajas**:
- Al ejecutarse línea a línea, pueden ser más **lentos** que un compilado, dependiendo del tipo de tarea.
- El usuario necesita el intérprete (o la máquina virtual) instalado.

---

### Ventajas de un lenguaje compilado

1. **Mayor velocidad de ejecución**: Al no interpretarse en tiempo real, el tiempo de ejecución suele ser menor.
2. **Optimizaciones del compilador**: El compilador puede analizar y optimizar el código en diferentes fases (por ejemplo, reordenar instrucciones para que sean más eficientes).
3. **Distribución sencilla**: Puedes entregar el archivo ejecutable, y el usuario final no necesita tener un intérprete.

> **Ejecutable**: Archivo final que tu sistema operativo puede correr directamente, como `miPrograma.exe` en Windows o `./miPrograma` en Linux.

---

### Por qué puede ser más rápido un lenguaje compilado

1. **Sin capa de interpretación**: Al no traducir instrucción por instrucción en tiempo de ejecución, se **ahorra** ese procesamiento adicional.
2. **Compilador**: Realiza **optimizaciones** a nivel de hardware, como usar mejor los registros de la CPU, "desenrollar bucles" (loop unrolling) o "insertar" llamadas de funciones simples (inlining), todo lo cual acelera la ejecución.

---
### Tipado Fuerte y Diferencias con Python

Cuando decimos que un lenguaje es **fuertemente tipado**, nos referimos a que:

- Cada variable tiene un **tipo** (por ejemplo, `int`, `float`, `string`) y el compilador **exige** coherencia al usarlas.
- No se puede convertir una variable a otro tipo incompatible sin que el compilador reclame o requiera una conversión explícita.

> **Tipo**: Define qué clase de datos se almacenan en la variable (por ejemplo, números enteros, texto, etc.) y qué operaciones se pueden realizar sobre ese valor.

**En C++**:

- Si declaras `int x = 10;`, no podrás asignarle directamente un `double*` o un `std::string` sin que ocurra un **error de compilación**.
- La mayoría de los errores de tipo se detectan antes de ejecutar el programa, haciendo que los errores aparezcan temprano en el proceso.

**En Python**:

- Python también es **fuertemente tipado** (cada objeto en Python tiene un tipo), pero es **dinámicamente tipado** (no necesitas declarar el tipo antes de usarlo).
- Python hace muchas conversiones internamente y asocia los tipos a los **objetos**, no a las **variables**.
- Muchos errores de tipo se detectan en **tiempo de ejecución** (es decir, cuando ya se está corriendo el programa).

**¿Beneficio de C++?**

- El compilador **detecta** errores de tipo y problemas de sintaxis antes de ejecutar el programa, haciéndolo más **robusto** y predecible.

#### Diferencias Claves entre Python y C++

| Característica           | Python                         | C++                                        |
| ------------------------ | ------------------------------ | ------------------------------------------ |
| **Tipado**               | Dinámico (no tipado)           | Estático (fuertemente tipado)              |
| **Definición de clases** | class sin tipos                | class con tipos especificados              |
| **Instanciación**        | `obj = Clase()`                | `Clase obj;` o `Clase* obj = new Clase();` |
| **Memoria**              | Automática (Garbage Collector) | Manual (uso de `new` y `delete`)           |s librerías necesarias, para formar el **ejecutable** final. Si faltan definiciones de funciones u otros símbolos, surgirá un **error de enlazado**.

---

#- **Directivas de preprocesador**: Le indican al compilador (o más específicamente, al preprocesador) que realice tareas específicas **antes** de compilar el código principal. Por ejemplo:
  - `#include <iostream>`: Copia el contenido del archivo de cabecera (en este caso, de la librería de entrada y salida estándar) en tu código.
  - `#define MAX 100`: Define una constante o macro llamada `MAX` con el valor 100, que luego será sustituido en el código.

Durante el **preprocesado**, se **expanden** estas directivas. Para el caso de `#include`, se copia todo el contenido del archivo incluido dentro de tu archivo final, antes de pasar a la etapa de compilación.

#### Compilación

En la **compilación**, el compilador traduce el código fuente (ya preprocesado) de cada archivo `.cpp` a un archivo objeto (`.o` en Linux/macOS o `.obj` en Windows). En esta etapa se revisa la sintaxis, los tipos de datos, la corrección del código, etc.

#### Enlazado (Linking)

En el **enlazado**, los distintos archivos objeto se unen entre sí, junto con las librerías necesarias, para formar el **ejecutable** final. Si faltan definiciones de funciones u otros símbolos, surgirá un **error de enlazado**.

---

**Ejemplo de compilación**: Si tenemos un solo archivo `main.cpp`, podemos compilar y ejecutar en Linux/Mac:

```bash
g++ main.cpp -o miPrograma
./miPrograma
```

En Windows (con g++ de MinGW):

```bash
g++ main.cpp -o miPrograma.exe
miPrograma.exe
```

---

### ¿Qué se necesita para que un programa en C++ funcione?

1. **Compilador**: Necesitas contar con un compilador C++ instalado en tu sistema, por ejemplo `g++` o `clang++`. Este se encarga de traducir el código fuente en un ejecutable.
2. **Bibliotecas estándar**: C++ provee librerías como `<iostream>` (para imprimir en consola), `<vector>`, `<string>`, etc. Estas librerías normalmente vienen con el compilador.
3. **Sistema operativo**: El programa compilado deberá ser compatible con el sistema operativo para el cual fue compilado (Windows, Linux, macOS, etc.).
4. **Ambiente de ejecución**: Para programas de consola, solo necesitas el ejecutable y las bibliotecas asociadas (normalmente incluidas en la instalación de C++). Para interfaces gráficas u otras librerías, debes asegurarte de que estén instaladas.

---

### Partes típicas de un proyecto orientado a objetos en C++

En un proyecto de C++ de tamaño mediano o grande, es común tener:

1. **Archivos de encabezado (`.h` o `.hpp`)**: Contienen las **declaraciones** de clases, funciones y constantes. Normalmente incluyen:
   - `#ifndef`, `#define`, `#endif` (las llamadas guardas de inclusión) para evitar que se incluya el archivo varias veces.

Ejemplo de una guarda en un archivo de encabezado:

```cpp
#ifndef MI_CLASE_H
#define MI_CLASE_H

class MiClase {
private:
    int atributo;
public:
    MiClase(int valor);
    int getAtributo();
};

#endif // MI_CLASE_H
```

En este ejemplo:
- `#ifndef MI_CLASE_H` verifica si `MI_CLASE_H` no ha sido definido antes.
- `#define MI_CLASE_H` lo define para que el archivo solo se procese una vez.
- `#endif` marca el final de la inclusión condicional.
   - `#include` de otras librerías o encabezados necesarios.
   - Definiciones de las clases (atributos y métodos) pero sin la implementación completa de las funciones.

2. **Archivos fuente (********`.cpp`********\*\*\*\*)**: Contienen las **implementaciones** de las clases y funciones declaradas en los archivos `.h`:

   - `#include "MiClase.h"` para poder implementar esas clases.
   - El cuerpo de cada método, usando el **operador de resolución de ámbito** (`::`) para indicar que pertenece a la clase declarada en el `.h`.

3. **Archivo principal (********`main.cpp`********\*\*\*\*)**: Es el **punto de entrada** del programa. Allí implementas la función `int main()` que, al ejecutarse, inicia tu aplicación.

4. **Fichero de construcción (CMakeLists.txt, Makefile, etc.)** (opcional pero muy recomendado para proyectos más grandes): Indica al compilador cómo compilar y enlazar los distintos archivos, qué librerías incluir, etc. Por ejemplo, en proyectos con CMake, se define este archivo para especificar rutas, nombres de ejecutable, etc.

5. **Carpetas organizadas** (opcional, pero útil):

   - `include/` para archivos de encabezado.
   - `src/` para archivos fuente.
   - `build/` para colocar los archivos objeto y ejecutables.

---
### CLion: Un IDE para C++

Un **IDE (Integrated Development Environment)** es un programa que integra diversas herramientas de desarrollo en una sola aplicación. Para C++, uno de los entornos más populares y potentes es **CLion**, desarrollado por JetBrains. A continuación, algunas de sus funcionalidades importantes y por qué usar un IDE puede resultar muy beneficioso:

1. **Edición con resaltado de sintaxis**: CLion reconoce la estructura de tu código C++, colorea y formatea automáticamente los elementos (palabras clave, variables, métodos, etc.). Esto facilita la lectura y ayuda a prevenir errores.
2. **Autocompletado inteligente (Code Completion)**: Mientras escribes, CLion sugiere nombres de variables, funciones, clases y métodos existentes en tu proyecto. Esto acelera la velocidad de programación y reduce errores de tipeo.
3. **Depuración (Debugging)**: Con CLion puedes poner puntos de interrupción (breakpoints), inspeccionar variables en tiempo real, ejecutar tu código paso a paso y revisar el flujo para encontrar errores lógicos.
4. **Integración con CMake**: CMake es una herramienta de configuración y compilación multiplataforma. CLion se integra perfectamente con CMake, permitiéndote gestionar proyectos grandes sin complicaciones.
5. **Gestión de proyectos y archivos**: CLion te facilita organizar tus carpetas, archivos fuente, librerías y dependencias en un solo lugar. Esto es útil para mantener una estructura clara en proyectos de tamaño mediano o grande.
6. **Control de versiones**: CLion ofrece integración con sistemas como Git o SVN. Puedes hacer commits, push, pull, ver el historial de cambios, etc., directamente desde el IDE.
7. **Refactorización**: Herramientas que permiten cambiar el nombre de variables, extraer funciones, reestructurar clases, todo de manera automática y segura. El IDE se encarga de aplicar los cambios en todos los lugares donde se use ese código.
8. **Productividad y mantenimiento**: Al unificar la edición de código, la compilación, la depuración y la gestión de versiones, CLion ayuda a que el flujo de trabajo sea más ágil y mantenible.

> **¿Por qué es importante usar un IDE como CLion?**
>
> - **Ahorra tiempo**: automatiza tareas comunes, como la compilación y la generación de archivos.
> - **Ayuda a encontrar errores**: el resaltado de sintaxis y el debugging integrado facilitan la detección de fallos.
> - **Favorece el aprendizaje**: ver los avisos de error inmediatamente, contar con autocompletado y ver ejemplos de uso refuerza la comprensión del lenguaje.
> - **Entorno unificado**: todo en un solo lugar: editor, compilador, debugger, control de versiones, etc.

---
## Programación orientada a objetos en C++
Para entender la **Programación Orientada a Objetos (POO) en C++**, primero debemos retomar dos conceptos clave: **clases** y **objetos**.

1. **Clase**: Es una plantilla o modelo que define cómo será un objeto, qué datos tendrá y qué podrá hacer. Es como un plano de construcción para un edificio: describe la estructura, pero aún no es un edificio real.
2. **Objeto**: Es una instancia de la clase, es decir, una versión concreta de ese modelo con valores específicos. Siguiendo la analogía del edificio, un objeto sería un edificio real construido a partir del plano. **Instanciar**: Significa crear un objeto a partir de una clase. Es el proceso de dar vida a una clase y asignarle valores específicos.

La **Programación Orientada a Objetos (POO)** se basa en el uso de **objetos**, no solo en la definición de **clases**. Una clase por sí sola es solo una idea, un molde o un diseño. Sin objetos, el código no hace nada útil.

### Ejemplo simple: Receta de galletas 🍪

Imagina que una **clase** es una receta para hacer galletas. La receta dice qué ingredientes usar y cómo mezclarlos, pero no es una galleta real, solo una instrucción.

Cuando sigues la receta y horneas una galleta, estás **instanciando** una galleta basada en la receta. Cada galleta tiene los mismos ingredientes, pero pueden tener decoraciones diferentes.

En C++:

```cpp
class Galleta {
public:
    string sabor;
    int tamaño;
};

int main() {
    Galleta g1; // Creamos una galleta (instancia de la clase Galleta)
    g1.sabor = "Chocolate";
    g1.tamaño = 10;
    
    Galleta g2; // Otra galleta con diferentes atributos
    g2.sabor = "Vainilla";
    g2.tamaño = 8;

    cout << "Galleta 1: " << g1.sabor << " - Tamaño: " << g1.tamaño << endl;
    cout << "Galleta 2: " << g2.sabor << " - Tamaño: " << g2.tamaño << endl;
    return 0;
}
```

Aquí:

- `Galleta` es la clase (receta).
- `g1` y `g2` son objetos (galletas creadas a partir de la receta).
- Cada galleta tiene un sabor y un tamaño diferente.

### Diferencia entre una clase y un objeto

### 1. Una clase sin objetos es como un plano sin construcción

Imagina que tienes el plano de una casa. El plano te dice cuántas habitaciones hay, dónde van las puertas y ventanas, y cómo se verá la casa. Pero **sin construir la casa**, el plano no sirve para vivir en él.

En POO, una clase es como ese plano: define las características de los objetos, pero si no creamos objetos (instanciamos la clase), el programa no hace nada útil.

Ejemplo en C++:

```cpp
class Auto {
public:
    string marca;
    int velocidad;
};
```

Esta clase `Auto` solo existe como una idea, pero no tiene uso real hasta que creamos objetos a partir de ella:

```cpp
int main() {
    Auto miAuto; // Ahora la clase cobra vida como un objeto
    miAuto.marca = "Toyota";
    miAuto.velocidad = 120;
    
    cout << "Marca: " << miAuto.marca << ", Velocidad: " << miAuto.velocidad << " km/h" << endl;
    return 0;
}
```

Aquí `miAuto` es un objeto de la clase `Auto`. Ahora, el programa tiene datos concretos y puede ejecutarse.

---

### 2. Los objetos almacenan y manipulan datos

Los objetos permiten **guardar información específica y manipularla**. Sin objetos, no podríamos representar datos reales en un programa.

Ejemplo:

```cpp
class Persona {
public:
    string nombre;
    int edad;
    void saludar() {
        cout << "Hola, soy " << nombre << " y tengo " << edad << " años." << endl;
    }
};
```

Si solo tenemos esta clase, el programa no hace nada. Pero si creamos objetos:

```cpp
int main() {
    Persona p1;
    p1.nombre = "Sofia";
    p1.edad = 22;
    
    p1.saludar(); // Llamamos a un método en el objeto
    return 0;
}
```

Ahora, el programa muestra:

```
Hola, soy Sofia y tengo 22 años.
```

Esto demuestra cómo un objeto **almacena datos y ejecuta acciones**, algo que una clase por sí sola no puede hacer.

---

### 3. Los objetos permiten reutilización y organización del código

En lugar de escribir código repetitivo, podemos crear múltiples objetos de una misma clase. Esto hace que nuestro código sea **modular y reutilizable**.

Ejemplo:

```cpp
int main() {
    Persona p1, p2;
    p1.nombre = "Carlos";
    p1.edad = 30;
    
    p2.nombre = "Ana";
    p2.edad = 25;
    
    p1.saludar();
    p2.saludar();
    return 0;
}
```

Salida del programa:

```
Hola, soy Carlos y tengo 30 años.
Hola, soy Ana y tengo 25 años.
```

Esto demuestra que podemos crear múltiples objetos a partir de la misma clase, cada uno con su propia información.

---

### 4. Los objetos reflejan cómo funciona el mundo real

En el mundo real, todo lo que usamos son "objetos" con propiedades y comportamientos. Por ejemplo:

- Un **carro** tiene una marca, un modelo y una velocidad (atributos), y puede acelerar o frenar (métodos).
- Una **cuenta bancaria** tiene un saldo y un número de cuenta (atributos), y permite hacer depósitos y retiros (métodos).
- Un **usuario** en una red social tiene un nombre y amigos (atributos), y puede publicar mensajes y comentar (métodos).

La POO busca **representar estos objetos reales dentro de un programa**.

---

## Preguntas Frecuentes sobre la Creación de Objetos e Instanciación

### 1. ¿Cuántas instancias puedo tener de una clase?

Puedes crear tantas instancias como necesites. Cada objeto creado a partir de una clase ocupa su propio espacio en la memoria y puede tener valores distintos en sus atributos.

Ejemplo:

```cpp
class Persona {
public:
    string nombre;
    int edad;
};

int main() {
    Persona p1;
    Persona p2;
    Persona p3;
    return 0;
}
```

Aquí hemos creado tres objetos (`p1`, `p2`, `p3`) de la misma clase `Persona`.

---

### 2. ¿Cómo se diferencia un objeto de otro?

Cada objeto tiene su propia copia de los atributos definidos en la clase, lo que le permite almacenar información diferente.

Ejemplo:

```cpp
Persona p1;
p1.nombre = "Carlos";
p1.edad = 20;

Persona p2;
p2.nombre = "Ana";
p2.edad = 25;
```

Aunque `p1` y `p2` provienen de la misma clase `Persona`, tienen valores diferentes en sus atributos.

---

### 3. ¿Para qué sirven los atributos y los métodos en una clase?

- **Atributos**: Son las variables que almacenan la información de un objeto. Por ejemplo, el nombre y la edad de una persona.
- **Métodos**: Son funciones dentro de la clase que permiten interactuar con los atributos y realizar acciones.

Ejemplo:

```cpp
class Persona {
public:
    string nombre;
    int edad;
    void mostrarInfo() {
        cout << "Nombre: " << nombre << ", Edad: " << edad << endl;
    }
};
```

Aquí, `mostrarInfo()` es un método que imprime la información de la persona.

---

### 4. ¿Qué es el estado de un objeto y por qué es importante?

El **estado** de un objeto es el conjunto de valores que tienen sus atributos en un momento determinado. Cambiar los valores de los atributos modifica el estado del objeto.

Ejemplo:

```cpp
Persona p1;
p1.nombre = "Luis";
p1.edad = 30;

// Cambiamos el estado del objeto
p1.nombre = "Mario";
p1.edad = 40;
```

El estado inicial de `p1` era `nombre = "Luis"`, `edad = 30`. Después lo modificamos a `nombre = "Mario"`, `edad = 40`.

Comprender el concepto de estado es clave para entender cómo los objetos cambian con el tiempo en un programa.

---

### ¿Para qué sirven los getters y setters?
En POO, uno de los principios clave es la encapsulación, que consiste en ocultar los detalles internos de una clase y exponer solo lo necesario al exterior. Los métodos que usamos para leer (obtener) o modificar (establecer) los valores internos de los atributos de una clase se conocen como getters y setters.

Getters (métodos de acceso): Permiten obtener el valor de un atributo privado de la clase.

Por convención, suelen nombrarse con el prefijo get seguido del nombre del atributo (por ejemplo, getNombre(), getEdad()).
Setters (métodos modificadores): Permiten cambiar el valor de un atributo privado de la clase.

Por convención, suelen nombrarse con el prefijo set seguido del nombre del atributo (por ejemplo, setNombre(...), setEdad(...)).

**¿Por qué encapsular?**
* Control: Podemos validar o filtrar datos antes de asignarlos.
* Seguridad: Evitamos que otras partes del código modifiquen directamente valores críticos.
* Mantenibilidad: Si en el futuro cambiamos la forma en que guardamos un atributo, no rompemos todo el código. Solo actualizamos el método setter/getter.

Ejemplo de getters y setters en C++
```cpp
#ifndef PERSONA_H
#define PERSONA_H

#include <string>

class Persona {
private:
    std::string nombre;
    int edad;

public:
    // Constructor con parámetros
    Persona(std::string nombre, int edad);

    // Getters
    std::string getNombre();
    int getEdad();

    // Setters
    void setNombre(std::string nuevoNombre);
    void setEdad(int nuevaEdad);
};

#endif // PERSONA_H



#include "Persona.h"

// Constructor
Persona::Persona(std::string nombre, int edad) {
  Persona::nombre = nombre;
  Persona::edad = edad; 

}

// Getter para nombre
std::string Persona::getNombre() {
    return nombre;
}

// Setter para nombre
void Persona::setNombre(std::string nuevoNombre) {
    if (!nuevoNombre.empty()) {
        nombre = nuevoNombre;
    }
}

// Getter para edad
int Persona::getEdad() {
    return edad;
}

// Setter para edad
void Persona::setEdad(int nuevaEdad) {
    if (nuevaEdad > 0) {
        edad = nuevaEdad;
    }
}

```
En este ejemplo, la clase Persona mantiene sus atributos nombre y edad como privados (private). Cualquier acceso o modificación a estos atributos se hace mediante los métodos getNombre(), setNombre(...), getEdad() y setEdad(...). De esta forma, podemos validar o filtrar la información antes de asignarla, y protegemos los datos internos de la clase.

### ¿Qué son los constructores y cómo se crean?
Un constructor en C++ es una función especial que se ejecuta automáticamente al crear (instanciar) un objeto de una clase. Tiene las siguientes características:

* Mismo nombre que la clase: Si la clase se llama Persona, el constructor se llamará Persona(...).
* No tiene tipo de retorno (ni siquiera void).
* Puede recibir parámetros o no (constructor por defecto o sin parámetros).
* Se usa para inicializar los atributos de la clase.

#### Constructor sin parámetros
Un constructor sin parámetros (también llamado constructor por defecto) no recibe ningún argumento. Útil cuando no queremos —o no podemos— suministrar datos de inicialización en el momento de crear el objeto. Podemos asignar valores por defecto a los atributos dentro de este constructor.

Ejemplo
```cpp
#ifndef PERSONA_H
#define PERSONA_H

#include <string>

class Persona {
private:
    std::string nombre;
    int edad;

public:
    // Constructor sin parametros
    Persona();

    // Constructor con parámetros
    Persona(std::string nombre, int edad);

    // Getters
    std::string getNombre();
    int getEdad();

    // Setters
    void setNombre(std::string nuevoNombre);
    void setEdad(int nuevaEdad);
};

#endif // PERSONA_H



#include "Persona.h"

// Constructor sin parámetros (por defecto)
Persona() {
    nombre = "Desconocido";
    edad   = 0;
}

// Constructor
Persona::Persona(std::string nombre, int edad) {
  Persona::nombre = nombre;
  Persona::edad = edad; 

}

// Getter para nombre
std::string Persona::getNombre() {
    return nombre;
}

// Setter para nombre
void Persona::setNombre(std::string nuevoNombre) {
    if (!nuevoNombre.empty()) {
        nombre = nuevoNombre;
    }
}

// Getter para edad
int Persona::getEdad() {
    return edad;
}

// Setter para edad
void Persona::setEdad(int nuevaEdad) {
    if (nuevaEdad > 0) {
        edad = nuevaEdad;
    }
}

// Archivo Main

int main() {
    // Uso del constructor sin parámetros
    Persona persona1;
    // persona1 tiene nombre "Desconocido" y edad 0.

    // Uso del constructor con parámetros
    Persona persona2("Ana", 25);

    // Mostramos los resultados
    std::cout << "Persona 1: " << persona1.getNombre()
              << ", " << persona1.getEdad() << " años.\n";

    std::cout << "Persona 2: " << persona2.getNombre()
              << ", " << persona2.getEdad() << " años.\n";
    
    return 0;
}
```
En este ejemplo:
```
Persona(): Constructor sin parámetros. Asigna valores por defecto ("Desconocido" y 0).
Persona(std::string, int): Constructor con parámetros. Inicializa nombre y edad con los valores dados.
Nota: Si no definimos ningún constructor, el compilador genera un constructor por defecto automáticamente. Sin embargo, si definimos un constructor con parámetros, el constructor por defecto no se genera automáticamente (a menos que lo declaremos explícitamente).
```

## Diseño UML y Ejemplo Práctico en C++
Ahora que hemos revisado los fundamentos de la compilación, las partes típicas de un proyecto en C++ y cómo estructurar nuestro código fuente, vamos a llevar todo ese conocimiento a la práctica. En esta sección, diseñaremos un programa orientado a objetos mediante UML y luego mostraremos la transición de ese diseño al código en C++.

### ¿Cómo se asocian los atributos y métodos definidos en UML con la parte práctica?
Cuando diseñamos nuestras clases en UML, definimos sus **atributos** (por ejemplo, `nombre`, `id`) y sus **métodos** (por ejemplo, `getNombre()`, `setNombre()`), junto con las relaciones (asociaciones, agregaciones, etc.). En C++:

- **Atributos**: se convierten en **variables miembro** dentro de nuestras clases en los archivos `.h`. Normalmente los colocamos como `private` para mantener el encapsulamiento.
- **Métodos**: se declaran en el archivo `.h` como funciones dentro de la clase, y se **implementan** en el archivo `.cpp` usando el operador de resolución de ámbito (`Clase::metodo`).
- **Relaciones**: si en UML decimos que un `Profesor` puede dictar varios `Curso`, usamos un contenedor, por ejemplo `std::vector<Curso>`, para representar esa relación en C++.
- **main**: la parte práctica se concreta en `main.cpp`, donde instanciamos nuestros objetos y comprobamos su funcionamiento. Recuerda que solo puede existir un `main`.

Gracias a esta separación (declaraciones en `.h`, implementación en `.cpp`, y punto de entrada en `main.cpp`), el proyecto adquiere un orden claro. Si quieres modificar atributos de `Profesor`, cambias su declaración en el header (`.h`), implementas la lógica que necesites en el `.cpp`, y usas esos cambios en tu `main.cpp`.

## Ejercicios Prácticos de Clases y UML

A continuación, se presentan **tres ejercicios** para reforzar lo aprendido. Cada ejercicio incluye un **diagrama UML** y una consigna de programación en C++.

---

### Ejercicio 1

#### Instrucciones

1. Observa el siguiente diagrama UML que representa una **sola clase** llamada `Libro`.  
2. Implementa la clase en C++:  
   - Declara sus atributos de manera **privada**.  
   - Crea los **getters y setters** para cada atributo.  
   - Escribe al menos un **constructor** para inicializar los atributos.  
3. En el archivo `main.cpp`, crea **tres objetos** de tipo `Libro` con atributos distintos y muestra por pantalla los valores de cada uno.

#### Diagrama UML

```mermaid
classDiagram
    class Libro {
        -string titulo
        -string autor
        -int anioPublicacion
        +Libro(string, string, int)
        +string getTitulo()
        +void setTitulo(string)
        +string getAutor()
        +void setAutor(string)
        +int getAnioPublicacion()
        +void setAnioPublicacion(int)
    }
```


### Ejercicio 2

#### Instrucciones

1. Analiza el siguiente diagrama UML con **dos clases**: `Persona` y `Automovil`.  
2. Las clases tienen una **relación de asociación**: cada `Persona` **posee** un `Automovil`.  
3. Implementa ambas clases en C++ con sus getters, setters y un constructor que inicialice los atributos.  
4. Relaciona los objetos en tu `main.cpp`:
   - Crea al menos **dos objetos** de tipo `Persona`.
   - A cada persona, asígnale un `Automovil`.
   - Muestra la relación persona-automóvil en la salida (por ejemplo, *"La persona Juan conduce un Toyota 2020"*).

#### Diagrama UML

```mermaid
classDiagram
    class Persona {
        -string nombre
        -int edad
        -Automovil miAuto
        +Persona(string, int, Automovil)
        +string getNombre()
        +void setNombre(string)
        +int getEdad()
        +void setEdad(int)
        +Automovil getMiAuto()
        +void setMiAuto(Automovil)
    }

    class Automovil {
        -string marca
        -int anio
        +Automovil(string, int)
        +string getMarca()
        +void setMarca(string)
        +int getAnio()
        +void setAnio(int)
    }

    Persona --> Automovil
```
### Enunciado completo: Diseña UML con Profesor, Curso y Salón

Imagina que trabajas en la Oficina de Registro Académico de la **Universidad XYZ**. El objetivo principal es organizar la información sobre la asignación de cursos a los profesores asociados y sobre en qué salones se dicta cada curso. Se sabe lo siguiente:

- **Profesor**: Persona que dicta uno o varios cursos. Además de su nombre e identificación, puede estar asociado a múltiples cursos.
- **Curso**: Toda asignatura que ofrece la universidad. Cada curso tiene un nombre, un código único y se imparte en un único salón.
- **Salón**: Espacio físico en el campus universitario. Se identifica por un nombre o número y tiene una capacidad limitada de estudiantes.

La **gerencia de la universidad** desea que se diseñe un sistema para:

1. **Administrar** los datos de cada profesor (nombre, ID) y los cursos que dicta.
2. **Controlar** la información de cada curso (nombre, código) y el salón asignado.
3. **Monitorear** las características del salón (nombre, capacidad).

En la práctica:

- Un Profesor puede dictar uno **o varios** cursos a lo largo de un período.
- Cada Curso se dicta en un **solo Salón**, el cual determina cuántos estudiantes se pueden matricular.

**Práctica**: A partir de esta historia, diseña un **diagrama UML** (usando la sintaxis de **mermaid**) que represente las clases `Profesor`, `Curso` y `Salon`. Luego, implementa las clases en C++ separando la declaración (`.h`) de la implementación (`.cpp`) y crea un programa (`main.cpp`) que demuestre la creación de objetos y la relación entre ellos. Asegúrate de contar con al menos cuatro objetos en tu programa: por ejemplo, un par de profesores, un par de cursos y los salones correspondientes.

Recuerda que el objetivo de este ejercicio es **fortalecer tus habilidades** para identificar clases, métodos y atributos a partir de una historia y representarlos en UML para luego llevarlos al código. ** TRATA DE HACERLO TU SOLO ANTES DE REVISAR LA SOLUCIÓN - INVESTIGA PARA QUE SIRVE LA CLASE VECTOR EN C++**

### Solución paso a paso

#### 1. Diagrama UML en mermaid

```mermaid
classDiagram
    class Profesor {
        -string nombre
        -string id
        -Vector cursos
        +Profesor(string nombre, string id)
        +void agregarCurso(Curso curso)
    }

    class Curso {
        -string nombreCurso
        -int codigo
        -Salon salon
        +Curso(string nombreCurso, int codigo)
        +void asignarSalon(Salon s)
    }

    class Salon {
        -string nombreSalon
        -int capacidad

        +Salon(string nombreSalon, int capacidad)
    }

    Profesor o-- Curso 
    Curso --> Salon 
```

En el diagrama:

- Se muestra una **agregación** (`o--`) de `Profesor` a varios `Curso` (1 a muchos). Esto indica que un profesor tiene una relación de propiedad parcial sobre los cursos, pero los cursos pueden existir sin el profesor.
- `Curso` tiene una **asociación** unidireccional (`-->`) con `Salon`, reflejando que un curso “conoce” el salón donde se dicta, pero el salón no necesita conocer al curso.

#### 2. Código fuente en C++

A continuación, explicamos **paso a paso** la transición a código en C++.

1. **Archivos .h** (cabeceras):

   - Empiezan con **guardas de inclusión** (`#ifndef`, `#define` y `#endif`) para evitar que se incluyan duplicadamente.
   - Se declaran las clases, sus atributos y los métodos que tendrán.
   - Se pueden incluir otras cabeceras necesarias, por ejemplo `#include <string>`.

2. **Archivos .cpp** (implementación):

   - Incluyen la cabecera `.h` para acceder a la declaración de la clase.
   - Desarrollan el **cuerpo** de cada método, usando el **operador de resolución de ámbito** (`Clase::metodo`) para indicar a qué clase pertenece. 

<details>
<summary><b>¿Qué es el operador de resolución de ámbito (::) en C++?</b></summary>

El **operador de resolución de ámbito (`::`)** en C++ se utiliza para especificar a qué espacio de nombres o a qué clase pertenece un identificador. Esto es fundamental cuando definimos los métodos de una clase en un archivo `.cpp` después de haberlos declarado en su correspondiente archivo `.h`.

Ejemplo:

```cpp
class Profesor {
public:
    void mostrarNombre();
};
```

En el archivo `.cpp`, definimos el método utilizando `::` para indicar que pertenece a `Profesor`:

```cpp
#include "Profesor.h"
#include <iostream>

void Profesor::mostrarNombre() {
    std::cout << "Nombre del profesor" << std::endl;
}
```

En este caso, `Profesor::mostrarNombre()` indica que el método `mostrarNombre` pertenece a la clase `Profesor`. Si no usáramos `::`, el compilador no sabría a qué clase pertenece la función.

</details>
   - Pueden incluir librerías adicionales si se necesitan.

3. **Archivo main.cpp**:

   - Incluye las cabeceras principales (por ejemplo `#include "Profesor.h"`, `#include "Curso.h"`, `#include "Salon.h"`).
   - Define la función `int main()`, que es el punto de entrada de la aplicación.
   - Allí, creas objetos, llamas métodos, etc.

A continuación, se muestra un ejemplo concreto:

##### 2.1 Profesor.h

```cpp
#ifndef PROFESOR_H
#define PROFESOR_H

// Librerías necesarias
#include <string>
#include <vector>
#include "Curso.h"  // Para que Profesor sepa sobre la clase Curso

// Declaración de la clase Profesor
class Profesor {
private:
    // Atributos
    std::string nombre;
    std::string id;
    std::vector<Curso> cursos; // Contenedor de cursos

public:
    // Constructor
    Profesor(std::string nombre, std::string id);

    // Métodos de acceso (getters)
    std::string getNombre();
    std::string getId();

    // Métodos para modificar (setters)
    void setNombre(std::string nombre);
    void setId(std::string id);

    // Otros métodos
    void agregarCurso(Curso curso);
    std::vector<Curso> getCursos();
};

#endif
```

1. Usamos `#ifndef PROFESOR_H` y `#define PROFESOR_H` para que este archivo sólo se cargue una vez.
2. Incluimos `<string>` y `<vector>` porque los usamos en los atributos y métodos. También `Curso.h` para poder declarar un vector de tipo `Curso`.
3. Declaramos la clase `Profesor` con sus atributos privados y métodos públicos.

##### 2.2 Profesor.cpp

```cpp
#include "Profesor.h"  // Incluimos la cabecera correspondiente

// Definición del constructor
Profesor::Profesor(std::string nombre, std::string id)
{
  Profesor::nombre = nombre;
  Profesor::id = id;
}

// Definición de métodos
std::string Profesor::getNombre() {
    return nombre;
}

std::string Profesor::getId() {
    return id;
}

void Profesor::setNombre(std::string nombre) {
    this->nombre = nombre;
}

void Profesor::setId(std::string id) {
    this->id = id;
}

void Profesor::agregarCurso(Curso curso) {
    cursos.push_back(curso);
}

std::vector<Curso> Profesor::getCursos() {
    return cursos;
}
```

1. Incluimos `"Profesor.h"` para que el compilador conozca la declaración de la clase.
2. Usamos `Profesor::Profesor(...)` para definir el **constructor**.
3. En el **inicializador** asignamos los valores recibidos a los atributos.
4. El resto de métodos se implementan usando la forma `TipoRetorno Clase::metodo() {...}`.

##### 2.3 Curso.h

```cpp
#ifndef CURSO_H
#define CURSO_H

#include <string>
#include "Salon.h" // Para relacionar Curso con Salon

class Curso {
private:
    std::string nombreCurso;
    int codigo;
    Salon salonAsignado;

public:
    Curso(std::string nombreCurso, int codigo);

    std::string getNombreCurso();
    int getCodigo();

    void setNombreCurso(std::string nombreCurso);
    void setCodigo(int codigo);

    void asignarSalon(Salon salon);
    Salon getSalonAsignado();
};

#endif
```

##### 2.4 Curso.cpp

```cpp
#include "Curso.h"

Curso::Curso(std::string nombreCurso, int codigo){
  Curso::nombreCurso = nombreCurso;
  Curso::codigo = codigo;
}

std::string Curso::getNombreCurso() {
    return nombreCurso;
}

int Curso::getCodigo() {
    return codigo;
}

void Curso::setNombreCurso(std::string nombreCurso) {
    this->nombreCurso = nombreCurso;
}

void Curso::setCodigo(int codigo) {
    this->codigo = codigo;
}

void Curso::asignarSalon(Salon salon) {
    salonAsignado = salon;
}

Salon Curso::getSalonAsignado() {
    return salonAsignado;
}
```

Aquí se implementan todos los métodos del curso y se guarda el `Salon` asignado.

##### 2.5 Salon.h

```cpp
#ifndef SALON_H
#define SALON_H

#include <string>

class Salon {
private:
    std::string nombreSalon;
    int capacidad;

public:
    Salon(std::string nombreSalon, int capacidad);

    std::string getNombreSalon();
    int getCapacidad();

    void setNombreSalon(std::string nombreSalon);
    void setCapacidad(int capacidad);
};

#endif
```

##### 2.6 Salon.cpp

```cpp
#include "Salon.h"

Salon::Salon(std::string nombreSalon, int capacidad){
  Salon::nombreSalon = nombreSalon;
  Salon::capacidad = capacidad;
}

std::string Salon::getNombreSalon() {
    return nombreSalon;
}

int Salon::getCapacidad() {
    return capacidad;
}

void Salon::setNombreSalon(std::string nombreSalon) {
    this->nombreSalon = nombreSalon;
}

void Salon::setCapacidad(int capacidad) {
    this->capacidad = capacidad;
}
```

##### 2.7 main.cpp

```cpp
#include <iostream>
#include "Profesor.h"
#include "Curso.h"
#include "Salon.h"

int main() {
    // 1. Creamos un objeto Salon
    Salon salon101("Salon 101", 30);

    // 2. Creamos un Curso y lo asignamos al salon anterior
    Curso poo("Programación Orientada a Objetos", 1001);
    poo.asignarSalon(salon101);

    // 3. Creamos un Profesor y le agregamos el curso
    Profesor profJuan("Juan Perez", "P001");
    profJuan.agregarCurso(poo);

    // 4. Creamos otro Salón, otro Curso y otro Profesor
    Salon salon202("Salon 202", 50);
    Curso algebra("Algebra Lineal", 2002);
    algebra.asignarSalon(salon202);

    Profesor profMaria("Maria Lopez", "P002");
    profMaria.agregarCurso(algebra);

    // Mostramos información por consola
    std::cout << "Profesor: " << profJuan.getNombre()
              << " dicta el curso: "
              << profJuan.getCursos()[0].getNombreCurso()
              << " en el salon: "
              << profJuan.getCursos()[0].getSalonAsignado().getNombreSalon()
              << std::endl;

    std::cout << "Otro profesor: " << profMaria.getNombre()
              << " dicta el curso: "
              << profMaria.getCursos()[0].getNombreCurso()
              << " en el salon: "
              << profMaria.getCursos()[0].getSalonAsignado().getNombreSalon()
              << std::endl;

    return 0;
}
```

1. Incluimos `<iostream>` para poder usar `std::cout`.
2. Incluimos los encabezados (`Profesor.h`, `Curso.h`, `Salon.h`) para poder crear objetos de esas clases.
3. Creamos varios objetos y los relacionamos tal como definimos en el diagrama UML.
4. Finalmente, usamos `std::cout` para imprimir datos de interés y comprobar que la relación entre objetos funciona correctamente.

##### 2.8 Compilación

Para compilar un proyecto en C++ de manera eficiente, especialmente en proyectos con múltiples archivos, es recomendable utilizar un sistema de construcción como **CMake**. En un archivo `CMakeLists.txt`, se especifican los archivos fuente, el compilador a usar y las opciones de compilación.

Ejemplo de un `CMakeLists.txt` básico para este proyecto:

```cmake
cmake_minimum_required(VERSION 3.10)
project(MiProyecto)

set(CMAKE_CXX_STANDARD 20)

add_executable(miPrograma 
    Profesor.cpp 
    Curso.cpp 
    Salon.cpp 
    main.cpp)
```

Este archivo define:
- El nombre del proyecto (`MiProyecto`).
- La versión mínima de CMake requerida.
- El estándar de C++ a utilizar (`C++20`).
- Los archivos fuente que deben compilarse en un ejecutable (`miPrograma`).

<details>
<summary><b>Compilar sin CMake (solo con g++)</b></summary>

Si todos estos archivos (`Profesor.h`, `Profesor.cpp`, `Curso.h`, `Curso.cpp`, `Salon.h`, `Salon.cpp`, y `main.cpp`) están en la misma carpeta, se pueden compilar manualmente con:

```bash
g++ Profesor.cpp Curso.cpp Salon.cpp main.cpp -o miPrograma
./miPrograma
```

En Windows (con g++ de MinGW):

```bash
g++ Profesor.cpp Curso.cpp Salon.cpp main.cpp -o miPrograma.exe
miPrograma.exe
```
</details>
