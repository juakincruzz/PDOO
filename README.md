# PDOO - Programación y Diseño Orientado a Objetos

![Java](https://img.shields.io/badge/Java-OOP-blue)
![Ruby](https://img.shields.io/badge/Ruby-OOP-red)
![Swing](https://img.shields.io/badge/UI-Swing-lightgrey)
![MVC](https://img.shields.io/badge/Architecture-MVC-green)

Repositorio de prácticas de la asignatura **Programación y Diseño Orientado a Objetos**.

El proyecto principal es **Irrgarten**, un juego de laberinto desarrollado de forma incremental en **Java** y **Ruby**, aplicando conceptos de programación orientada a objetos, diseño modular, herencia, polimorfismo, interfaces y separación entre modelo, vista y controlador.

---

## Descripción

**Irrgarten** es un juego de laberinto en el que uno o varios jugadores se desplazan por un tablero, se enfrentan a monstruos, reciben recompensas y tratan de alcanzar la casilla de salida.

El desarrollo se organiza en varias prácticas progresivas. Cada una introduce nuevos elementos del diseño orientado a objetos, partiendo de clases simples y evolucionando hacia una aplicación más completa con lógica de juego, combate, herencia, polimorfismo e interfaz gráfica.

El repositorio contiene dos líneas de implementación:

- **Java**, con prácticas desde `Practica0_Java` hasta `Practica5_Java`.
- **Ruby**, con prácticas desde `Practica0_Ruby` hasta `Practica4_Ruby`.

---

## Tecnologías utilizadas

- Java
- Ruby
- Swing
- NetBeans
- Git y GitHub

---

## Conceptos trabajados

- Clases y objetos
- Encapsulación
- Constructores y constructores de copia
- Herencia
- Polimorfismo
- Clases abstractas
- Interfaces
- Enumerados
- Colecciones
- Composición de objetos
- Separación modelo-vista-controlador
- Interfaz gráfica con Swing
- Traducción de diseño entre Java y Ruby

---

## Proyecto principal: Irrgarten

El juego se estructura alrededor de varias entidades principales:

| Clase / componente | Responsabilidad |
|---|---|
| `Game` | Núcleo del juego: gestiona turnos, jugadores, monstruos, combate, recompensas y finalización de la partida. |
| `Labyrinth` | Representa el tablero, la salida, obstáculos, jugadores, monstruos y movimientos válidos. |
| `Player` | Representa a los jugadores, sus atributos, armas, escudos, movimiento, ataque, defensa y recompensas. |
| `Monster` | Representa a los enemigos del laberinto y su comportamiento en combate. |
| `LabyrinthCharacter` | Clase base abstracta para personajes del laberinto. |
| `FuzzyPlayer` | Variante polimórfica de `Player`, usada tras la resurrección del jugador. |
| `Weapon` / `Shield` | Objetos equipables que modifican ataque y defensa. |
| `CardDeck` | Estructura base para barajas de armas y escudos. |
| `GameState` | Objeto de transferencia con el estado observable del juego. |
| `Controller` | Coordina la interacción entre el modelo y la interfaz. |
| `UI`, `TextUI`, `GraphicalUI` | Interfaces de usuario textual y gráfica. |

---

## Arquitectura

La versión final en Java aplica una estructura cercana al patrón **Modelo-Vista-Controlador**:

```text
Modelo        -> Game, Labyrinth, Player, Monster, Weapon, Shield...
Vista         -> UI, TextUI, GraphicalUI, Cursors
Controlador   -> Controller
Punto entrada -> Main
```

El programa principal crea el modelo del juego, la interfaz gráfica y el controlador. A partir de ahí, el controlador dirige la ejecución de la partida, solicitando movimientos al usuario y actualizando la vista con el estado del juego.

---

## Estructura del repositorio

```text
PDOO/
├── PracticasPDOOJava/
│   ├── Practica0_Java/
│   ├── Practica1_Java/
│   ├── Practica2_Java/
│   ├── Practica3_Java/
│   ├── Practica4_Java/
│   └── Practica5_Java/
│
├── PracticasPDOORuby/
│   ├── Practica0_Ruby/practicadeprueba/
│   ├── Practica1_Ruby/
│   ├── Practica2_Ruby/
│   ├── Practica3_Ruby/
│   └── Practica4_Ruby/
│
└── README.md
```

---

## Evolución por prácticas

| Práctica | Java | Ruby | Contenido principal |
|---|---|---|---|
| Práctica 0 | Sí | Sí | Introducción al entorno de trabajo y primeras pruebas. |
| Práctica 1 | Sí | Sí | Clases básicas del juego, enumerados, dados, armas, escudos y estado del juego. |
| Práctica 2 | Sí | Sí | Ampliación del modelo con personajes, jugadores, monstruos y lógica inicial del laberinto. |
| Práctica 3 | Sí | Sí | Implementación del flujo principal del juego: movimiento, combate, turnos, recompensas y logs. |
| Práctica 4 | Sí | Sí | Herencia, clase base de personajes, copia de objetos, polimorfismo y versión Ruby más completa. |
| Práctica 5 | Sí | No | Versión final en Java con controlador, interfaz gráfica Swing y ejecución integrada del juego. |

---

## Detalles de implementación

### Gestión del juego

La clase `Game` centraliza la lógica principal:

- Creación de jugadores.
- Creación del laberinto.
- Colocación de monstruos.
- Gestión del jugador actual.
- Ejecución de turnos.
- Resolución de combates.
- Recompensas al jugador.
- Resurrección y conversión a `FuzzyPlayer`.
- Registro de eventos mediante logs.

### Laberinto

La clase `Labyrinth` representa el tablero mediante estructuras paralelas para:

- Celdas del laberinto.
- Jugadores.
- Monstruos.

También gestiona la salida, obstáculos, posiciones aleatorias, movimientos válidos y colocación de entidades.

### Jugadores y combate

`Player` hereda de `LabyrinthCharacter` y añade lógica específica de jugador:

- Armas y escudos equipados.
- Cálculo de ataque.
- Cálculo de defensa.
- Gestión de impactos consecutivos.
- Recepción de recompensas.
- Eliminación de equipo agotado.
- Resurrección.

`FuzzyPlayer` extiende `Player` y modifica el comportamiento de movimiento y ataque, mostrando el uso de polimorfismo en la práctica.

### Interfaz

La versión final en Java incluye una interfaz gráfica basada en **Swing**. La clase `GraphicalUI` implementa la interfaz `UI`, muestra el estado del laberinto, jugadores, monstruos y log, y solicita al usuario el siguiente movimiento mediante una ventana de cursores.

---

## Implementación en Ruby

Además de la versión Java, el repositorio incluye una línea completa de prácticas en Ruby dentro de `PracticasPDOORuby`, desde `Practica0_Ruby` hasta `Practica4_Ruby`.

Esta parte reproduce progresivamente los conceptos de orientación a objetos trabajados en Java, adaptándolos a la sintaxis y filosofía de Ruby:

- Módulo `Irrgarten`.
- Clases para jugadores, monstruos, armas, escudos, dados y laberinto.
- Uso de `attr_reader` y métodos protegidos.
- Herencia entre `LabyrinthCharacter`, `Player` y variantes especializadas.
- Copia de objetos mediante métodos propios.
- Gestión de armas y escudos.
- Lógica de ataque, defensa, daño, resurrección y recompensas.
- Organización del código mediante `require_relative`.

La parte Ruby permite comparar cómo se implementa el mismo diseño orientado a objetos en un lenguaje dinámico frente a Java.

---

## Ejecución

### Java

La versión Java está organizada como proyectos de NetBeans.

Para ejecutar la versión final:

1. Abrir `PracticasPDOOJava/Practica5_Java` en NetBeans.
2. Compilar el proyecto.
3. Ejecutar la clase principal:

```text
irrgarten.main.Main
```

La clase `Main` crea una instancia de `Game`, inicializa la interfaz `GraphicalUI`, construye el `Controller` y comienza la partida.

### Ruby

Las prácticas Ruby se encuentran en:

```text
PracticasPDOORuby/
```

Cada práctica tiene su propia estructura y archivos de prueba. Para ejecutarlas, entra en la carpeta correspondiente y lanza el archivo principal o de prueba indicado en esa práctica.

---

## Aprendizajes principales

Este proyecto permite practicar de forma progresiva los fundamentos de la programación orientada a objetos mediante un caso práctico completo.

Los aspectos más importantes trabajados son:

- Diseñar clases con responsabilidades claras.
- Separar la lógica del juego de la interfaz.
- Reutilizar código mediante herencia.
- Usar polimorfismo para modificar comportamientos sin cambiar el flujo principal.
- Encapsular el estado interno de los objetos.
- Gestionar colecciones de objetos relacionados.
- Traducir diseños entre Java y Ruby.
- Comparar la implementación de un mismo modelo en un lenguaje estático y en uno dinámico.
- Construir una aplicación interactiva a partir de un modelo orientado a objetos.

---

## Autor

**Joaquín Cruz Lorenzo**  
GitHub: [@juakincruzz](https://github.com/juakincruzz)
