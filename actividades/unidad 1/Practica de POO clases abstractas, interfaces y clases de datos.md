# Práctica de Programación Orientada a Objetos  :computer: 

## Modelado de Animales y Frutas usando clases abstractas, interfaces y clases de datos

---

## Objetivo de la práctica

El objetivo de esta práctica es aplicar los siguientes conceptos de **programación orientada a objetos**: 

* Abstracción
* Herencia
* Interfaces
* Composición de objetos
* Modelado de entidades del mundo real mediante **clases de datos**

Para ello se desarrollará un sistema que represente **animales y frutas**, así como la capacidad de algunos objetos de ser **comestibles**.

---

## Descripción del problema

Una aplicación educativa necesita clasificar distintos elementos del mundo real en dos grandes grupos:

* **Animales**
* **Frutas**

Cada grupo tiene características propias, pero algunos objetos pueden compartir ciertos comportamientos. Por ejemplo, algunos elementos pueden ser **comestibles**.

Además, se desea modelar información adicional del mundo real mediante **clases de datos**, como el **hábitat de un animal** o el **origen de una fruta**.

Para representar este sistema correctamente se deben utilizar **clases abstractas, interfaces y clases de datos**.

---

## Parte 1. Interfaz Comestible

Se debe crear una **interfaz** llamada:

`Comestible`

Esta interfaz representa la capacidad de un objeto de ser consumido como alimento.

### Métodos sugeridos

* `formaDeComer()`
  Describe cómo se consume el alimento.

* `caloriasAportadas()`
  Indica cuántas calorías aporta.

Ejemplos:

| Objeto  | Forma de comer     |
| ------- | ------------------ |
| Manzana | Cruda o en postres |
| Naranja | En jugo o gajos    |
| Gallina | Cocida             |
| Vaca    | Carne              |

No todos los objetos del sistema deben implementar esta interfaz.

---

## Parte 2. Clase abstracta Animal

Se debe crear una **clase abstracta** llamada:

`Animal`

Esta clase representa las características comunes de todos los animales.

### Atributos sugeridos

* nombre
* edad
* peso
* habitat
* cuidador

### Métodos

* `hacerSonido()` → método abstracto
* `mostrarInfo()` → método que muestre la información del animal

---

## Parte 3. Clase abstracta Fruta

Se debe crear una **clase abstracta** llamada:

`Fruta`

Esta clase representa las características comunes de todas las frutas.

### Atributos sugeridos

* nombre
* color
* peso
* nivelDulzura
* origen
* informacionNutricional

### Método abstracto

Las frutas deben indicar su **tipo de sabor predominante**, por lo que la clase abstracta debe definir el método:

`tipoSabor()`

Este método deberá ser implementado por cada fruta concreta.

---

# Tipo de sabor

El **tipo de sabor** describe el sabor predominante de una fruta.

Ejemplos de sabores:

| Fruta   | Tipo de sabor |
| ------- | ------------- |
| Manzana | Dulce         |
| Plátano | Dulce         |
| Naranja | Cítrico       |
| Limón   | Ácido         |

El método `tipoSabor()` debe devolver ese valor.

Ejemplo conceptual:

```text
Manzana → Dulce
Naranja → Cítrico
Plátano → Dulce
```

Opcionalmente, si el lenguaje lo permite, se puede usar un **tipo enumerado (enum)** para representar los sabores:

```
TipoSabor
---------
DULCE
ACIDO
CITRICO
AMARGO
```

---

## Parte 4. Clases concretas

A partir de las clases abstractas se deben crear las siguientes clases.

---

# Animales

Se deben implementar al menos los siguientes animales:

* Leon
* Gallina
* Vaca

Relaciones:

| Clase   | Hereda de | Implementa Comestible |
| ------- | --------- | --------------------- |
| Leon    | Animal    | No                    |
| Gallina | Animal    | Sí                    |
| Vaca    | Animal    | Sí                    |

Cada clase debe implementar el método:

`hacerSonido()`

Ejemplos:

| Animal  | Sonido  |
| ------- | ------- |
| León    | Rugido  |
| Gallina | Cacareo |
| Vaca    | Mugido  |

Los animales que implementen `Comestible` deben definir también:

* `formaDeComer()`
* `caloriasAportadas()`

---

# Frutas

Se deben implementar al menos tres frutas:

* Manzana
* Platano
* Naranja

Todas las frutas:

* heredan de `Fruta`
* implementan `Comestible`

Cada fruta debe implementar:

* `tipoSabor()`
* `formaDeComer()`
* `caloriasAportadas()`

Ejemplo:

| Fruta   | Sabor   |
| ------- | ------- |
| Manzana | Dulce   |
| Naranja | Cítrico |
| Plátano | Dulce   |

---

## Parte 5. Clases de datos

El sistema debe utilizar **clases de datos** para representar información adicional asociada a animales y frutas.

Estas clases **no contienen lógica compleja**, solamente almacenan información.

---

# Clase de datos Habitat

Representa el lugar donde vive un animal.

### Atributos sugeridos

* tipo
* temperaturaPromedio
* region

### Relación

Un **Animal tiene un Habitat**.

Ejemplo:

| Animal  | Habitat |
| ------- | ------- |
| León    | Sabana  |
| Gallina | Granja  |
| Vaca    | Campo   |

---

# Clase de datos Cuidador

Representa la persona que cuida al animal.

### Atributos sugeridos

* nombre
* aniosExperiencia
* especialidad

### Relación

Un **Animal tiene un Cuidador**.

Ejemplo:

| Animal  | Cuidador              |
| ------- | --------------------- |
| León    | cuidador de zoológico |
| Gallina | granjero              |
| Vaca    | ganadero              |

---

# Clase de datos Origen

Representa el origen agrícola de una fruta.

### Atributos sugeridos

* pais
* region
* productor

### Relación

Una **Fruta tiene un Origen**.

Ejemplo:

| Fruta   | Origen  |
| ------- | ------- |
| Manzana | México  |
| Naranja | España  |
| Plátano | Ecuador |

---

# Clase de datos InformacionNutricional

Representa los valores nutricionales de un alimento.

### Atributos sugeridos

* calorias
* azucar
* fibra
* proteinas

### Relación

Las **frutas tienen información nutricional**.

Opcionalmente, también se puede asociar a animales comestibles.

---

# Relación general del sistema

```
Comestible (interfaz)

Animal (abstracta)
 ├── Leon
 ├── Gallina
 └── Vaca

Fruta (abstracta)
 ├── Manzana
 ├── Platano
 └── Naranja

Clases de datos
Habitat
Cuidador
Origen
InformacionNutricional
```

Relaciones:

* Animal contiene → Habitat
* Animal contiene → Cuidador
* Fruta contiene → Origen
* Fruta contiene → InformacionNutricional
* Algunas clases implementan → Comestible

___

## Diagrama UML de clases

<img width="1536" height="1024" alt="diagrama_UML_animales_frutas" src="https://github.com/user-attachments/assets/cc83cd49-1e8a-413b-9126-519263800ff8" />


## Parte 6. Programa principal

El programa debe:

1. Crear varios objetos de animales y frutas.
2. Asignar sus clases de datos correspondientes.
3. Guardarlos en una colección.
4. Mostrar la información de cada objeto.
5. Identificar cuáles implementan la interfaz `Comestible`.
6. Mostrar cómo se consumen.

---

# Ejemplo de salida esperada

```
Animal: León
Edad: 5
Peso: 190 kg
Hábitat: Sabana
Sonido: Rugido
Comestible: No

Animal: Gallina
Edad: 2
Peso: 3 kg
Hábitat: Granja
Sonido: Cacareo
Comestible: Sí
Forma de comer: Cocida

Fruta: Manzana
Color: Roja
Sabor: Dulce
Origen: México
Forma de comer: Cruda o en postres
Calorías: 52
```

