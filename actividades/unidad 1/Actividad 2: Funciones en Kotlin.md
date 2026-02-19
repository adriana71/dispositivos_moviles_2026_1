# 👷‍♀️ Guía de actividad: Lambdas y funciones de orden superior (Kotlin)

##  Objetivo del taller

Al final de la actividad,  podrás:

* Crear una lista de instrumentos usando `Pair`
* Usar lambdas con `filter`, `map`, `sumOf`, `sortedBy`
* Crear y usar **funciones de orden superior** (funciones que reciben otras funciones)

## Contexto: Instrumentos del laboratorio 🔬

Representaremos cada instrumento como:

```kotlin
Pair<String, Double>
```

* `first` → nombre
* `second` → precio



## Paso 0 — Crear el proyecto y el `main`

Crea un archivo Kotlin y pega esto:

```kotlin
fun main() {
    println("Taller: Laboratorio de automatización")
}
```

Ejecuta y verifica que funcione.

## 🟢 Paso 1 — Crear la lista de instrumentos

Dentro de `main()`, crea esta lista:

```kotlin
val instrumentos = listOf(
    Pair("Osciloscopio Digital", 1500.0),
    Pair("Voltímetro Digital", 120.0),
    Pair("Generador de Ondas", 980.0),
    Pair("Cable BNC", 15.0),
    Pair("Resistencia 1kΩ", 0.10),
    Pair("Protoboard", 25.0)
)
```

✅ **Mini-reto:** imprime todos los instrumentos con su precio:

```kotlin
instrumentos.forEach { println("${it.first} -> ${it.second}") }
```

## 🟢 Paso 2 — Usar `filter` con una lambda

Filtra los instrumentos que cuesten **más de 500**.

📌 Guía:

* `filter` recibe una función (lambda) que devuelve `true/false`

```kotlin
val costosos = instrumentos.filter { it.second > 500 }
println("\nInstrumentos costosos (> 500):")
costosos.forEach { println(it.first) }
```

✅ **Mini-reto:** cambia 500 por 100 y observa cómo cambia la lista.

## 🟢 Paso 3 — Usar `map` para obtener solo nombres

Ahora crea una lista que contenga **solo los nombres**:

```kotlin
val nombres = instrumentos.map { it.first }
println("\nNombres de instrumentos:")
nombres.forEach { println(it) }
```

✅ **Mini-reto:** en vez de nombres, genera un texto tipo: `"Osciloscopio Digital cuesta 1500.0"`.

## 🟢 Paso 4 — Usar `sumOf` para calcular el costo total

Calcular el costo total del laboratorio (suma de precios):

```kotlin
val total = instrumentos.sumOf { it.second }
println("\nCosto total del laboratorio: $total")
```

✅ **Mini-reto:** suma solo los instrumentos que cuesten más de 100:

* (pista: primero `filter`, luego `sumOf`)

## 🟢 Paso 5 — Ordenar por precio con `sortedBy`

Ordenar instrumentos por precio de menor a mayor:

```kotlin
val ordenados = instrumentos.sortedBy { it.second }
println("\nInstrumentos ordenados por precio:")
ordenados.forEach { println("${it.first} - ${it.second}") }
```

✅ **Mini-reto:** ordena de mayor a menor usando `sortedByDescending`.

# ⭐ Parte clave: Funciones de orden superior

## 🟢 Paso 6 — Crear una función de orden superior (filtrar)

Fuera de `main()` (arriba o abajo), crea esto:

```kotlin
fun filtrarInstrumentos(
    lista: List<Pair<String, Double>>,
    criterio: (Pair<String, Double>) -> Boolean
): List<Pair<String, Double>> {
    return lista.filter(criterio)
}
```

Ahora reemplaza el filter anterior por esta función:

```kotlin
val costosos2 = filtrarInstrumentos(instrumentos) { it.second > 500 }
println("\n(Con función de orden superior) Costosos (> 500):")
costosos2.forEach { println(it.first) }
```

✅ **Mini-reto:** usa la misma función para filtrar cables:

* pista: `it.first.contains("Cable")`

## 🟢 Paso 7 — Crear una función de orden superior (transformar)

Crea esta función genérica:

```kotlin
fun <T> transformarInstrumentos(
    lista: List<Pair<String, Double>>,
    transformacion: (Pair<String, Double>) -> T
): List<T> {
    return lista.map(transformacion)
}
```

Úsala para obtener nombres:

```kotlin
val nombres2 = transformarInstrumentos(instrumentos) { it.first }
println("\n(Con función de orden superior) Nombres:")
nombres2.forEach { println(it) }
```

✅ **Mini-reto:** transforma a precios con `it.second`.

## 🟢 Paso 8 — Crear una función de orden superior (cálculo total)

Crea una función que reciba una operación sobre la lista:

```kotlin
fun calcular(
    lista: List<Pair<String, Double>>,
    operacion: (List<Pair<String, Double>>) -> Double
): Double {
    return operacion(lista)
}
```

Y úsala así:

```kotlin
val total2 = calcular(instrumentos) { lista -> lista.sumOf { it.second } }
println("\n(Con función de orden superior) Total: $total2")
```

✅ **Mini-reto:** calcula el total solo de los instrumentos de medición:

* Osciloscopio y Voltímetro (pista: `contains`)

# ✅ Entrega del taller (lo que deben entregar)

1. Código en github funcionando con:

   * lista de instrumentos
   * al menos 2 filtros diferentes
   * una transformación con `map`
   * un total con `sumOf`
   * lista ordenada por precio
2. Uso de al menos **2 funciones de orden superior** creadas por el estudiante.

# 🧩 Reto final (opcional)

Crea una función:

```kotlin
fun buscarPrimero(
    lista: List<Pair<String, Double>>,
    criterio: (Pair<String, Double>) -> Boolean
): Pair<String, Double>?
```
Que devuelva el **primer instrumento** que cumpla un criterio (pista: `firstOrNull`).
