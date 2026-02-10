#  Ejercicio: *Registro simple de usuarios*


Crea un programa en **Kotlin** que simule un **registro básico de usuarios** y muestre información por consola.

## Objetivos (qué conceptos practicas)

* `val` y `var`
* Tipos de datos (`Int`, `String`, `Boolean`)
* Condicionales (`if / else`, `when`)
* Null safety (`?`, `?:`)
* Listas (`List`, `MutableList`)
* Bucles (`for`)
* Funciones básicas


## Requisitos del ejercicio

### 1 Datos del usuario

Declara las siguientes variables:

* Nombre del usuario (`String`)
* Edad (`Int`)
* Email (`String?`) → puede ser `null`
* Estado de suscripción (`Boolean`)


### 2 Función de validación

Crea una función llamada `esMayorDeEdad` que:

* Reciba la edad
* Retorne `true` si es mayor o igual a 18
* Retorne `false` en caso contrario


### 3 Evaluación con condicionales

* Usa `if / else` para mostrar:

  * “Acceso permitido” si es mayor de edad
  * “Acceso denegado” si no lo es


### 4 Manejo de null safety

* Si el email es `null`, muestra `"Email no registrado"`
* Si no es `null`, muéstralo normalmente
  👉 Usa el operador `?:` (Elvis)


### 5 Lista de usuarios

* Crea una `MutableList<String>` con nombres de usuarios
* Agrega al menos 3 usuarios
* Recorre la lista con un `for` y muéstralos en consola


### 6 Uso de `when`

Usa `when` para clasificar al usuario según la edad:

* Menor de 13 → `"Niño"`
* 13 a 17 → `"Adolescente"`
* 18 a 64 → `"Adulto"`
* 65 o más → `"Adulto mayor"`

