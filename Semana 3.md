---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: true
info: |
  ## Sesión 1: El Lenguaje de los Conjuntos
  Teoría de Conjuntos - Semana 3
drawings:
  persist: false
transition: slide-left
title: Teoría de Conjuntos - Sesión 1
---

# Teoría de Conjuntos
## Sesión 1: El Lenguaje de los Conjuntos

¿Cómo se escriben y quién pertenece a quién?

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer hover:bg-white hover:bg-opacity-10">
    Presiona Espacio para empezar <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: section
---

# Bloque 1: Definición y Representación
(45 minutos)

---

# ¿Qué es un Conjunto?
### El concepto de "La Bolsa" vs "El Contenido"

* **El Conjunto:** Imaginalo como una bolsa o contenedor. Se nombra con letras MAYÚSCULAS ($A, B, C$).
* **El Elemento:** Es cada objeto dentro de la bolsa. Se nombra con letras minúsculas ($a, b, c$) o números.

<v-click>

> **Nota Crítica:** Un conjunto puede contener otros conjuntos. 
> Ejemplo: $A = \{1, 2, \{3, 4\}\}$. Aquí, $\{3, 4\}$ es **un solo elemento** dentro de $A$.

</v-click>

---

# Formas de Representación

### 1. Por Extensión (Enumerativa)
Listamos cada elemento uno por uno entre llaves `{ }`.
* Ejemplo: $V = \{a, e, i, o, u\}$
* Ejemplo: $D = \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}$

### 2. Por Comprensión (Descriptiva)
Usamos una propiedad común y la barra "tal que" ($|$ o $:$).
* Estructura: $\{ \text{forma del elemento} \mid \text{condición} \}$
* Ejemplo: $V = \{x \mid x \text{ es una vocal}\}$
* Ejemplo: $P = \{x \in \mathbb{Z} \mid x \text{ es par y } 1 < x < 10\}$

---
layout: section
---

# Bloque 2: Pertenencia vs. Inclusión
(45 minutos)

---

# Relaciones Fundamentales

### Pertenencia ($\in$)
**Elemento $\to$ Conjunto**
Se usa para decir que un objeto individual está dentro de la bolsa.
* Si $A = \{1, 2, 3\}$, entonces $1 \in A$.

### Inclusión ($\subseteq$)
**Conjunto $\to$ Conjunto**
Se usa cuando todos los elementos de una "bolsa pequeña" están en una "bolsa grande".
* Si $A = \{1, 2, 3\}$ y $B = \{1, 2\}$, entonces $B \subseteq A$.

El Conjunto Vacío ($\emptyset$): No tiene elementos, pero por definición matemática, 
$\emptyset$ está incluido en todos los conjuntos ($\emptyset \subseteq A$).

<div class="bg-yellow-100 p-4 rounded text-black mt-4">
  <strong>El Conjunto Vacío ($\emptyset$):</strong> No tiene elementos, pero por definición matemática, 
  <strong>$\emptyset$ está incluido en todos los conjuntos</strong> ($\emptyset \subseteq A$).
</div>
El Conjunto Vacío ($\emptyset$): No tiene elementos, pero por definición matemática, 
$\emptyset$ está incluido en todos los conjuntos ($\emptyset \subseteq A$).
---
layout: center
---

# Bloque 3: Práctica Relámpago
(30 minutos)

---

# ¿Verdad o Falso?
Sea el conjunto $A = \{1, 2, \{3\}\}$

1. $1 \in A$ <v-click>➡️ **Verdadero**</v-click>
2. $3 \in A$ <v-click>➡️ **Falso** (3 está atrapado dentro de otro conjunto)</v-click>
3. $\{3\} \in A$ <v-click>➡️ **Verdadero** (El conjunto $\{3\}$ es un elemento directo)</v-click>
4. $\{1, 2\} \subseteq A$ <v-click>➡️ **Verdadero**</v-click>
5. $\{3\} \subseteq A$ <v-click>➡️ **Falso** (Para ser subconjunto debería escribirse $\{\{3\}\}$)</v-click>

---
layout: center
class: text-center
---

# ¡Fin de la Sesión 1!
Próxima sesión: **Operaciones y Álgebra de Conjuntos**