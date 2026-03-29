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
title: Semana 3 - Teoría de Conjuntos

---

# Teoría de Conjuntos
## Semana 3: Planificación Completa (3 Sesiones)

**Sesión 1:** El Lenguaje de los Conjuntos  
**Sesión 2:** Operaciones y Álgebra  
**Sesión 3:** Visualización y Problemas Reales  

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer hover:bg-white hover:bg-opacity-10">
    Comenzar Semana 3 <carbon:arrow-right class="inline"/>
  </span>
</div>

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
layout: default
---

# 1.1 Ontología del Conjunto
### El Axioma de Extensionalidad y la Naturaleza del Objeto

Un **conjunto** es una construcción mental abstracta que agrupa objetos (elementos) bajo un criterio de pertenencia unívoco. A diferencia de otras estructuras, se rige por principios fundamentales:

<div class="grid grid-cols-2 gap-6 mt-4">
<div class="bg-gray-800/50 p-4 rounded-lg border-l-4 border-blue-500">

### 💎 Principios Fundamentales
1. **Axioma de Extensionalidad:** Dos conjuntos son idénticos si y solo si tienen los mismos elementos. 
   * $A = B \iff \forall x (x \in A \iff x \in B)$
2. **Irrelevancia del Orden:** $\{a, b, c\} = \{c, b, a\}$. El conjunto es una estructura "plana" sin secuencia.
3. **Unicidad (Idempotencia):** La multiplicidad no existe. $\{a, a, b\} \equiv \{a, b\}$. 
</div>

<div class="bg-gray-800/50 p-4 rounded-lg border-l-4 border-purple-500">

### 🧩 Tipología de Elementos
Un elemento $x$ puede ser:
* **Atómico:** Un objeto simple (ej. $1, \pi, \text{'a'}$).
* **Compuesto:** Otro conjunto. Esto genera **Estructuras Jerárquicas** o Recurrencia.
* **Abstracto:** Una propiedad o una función.
</div>
</div>

---
class: text-sm
---

# La Jerarquía de Contención y Profundidad
### Análisis Crítico de Niveles de Pertenencia

En computación, confundir un **objeto** con el **contenedor que lo rodea** es un error de tipo (Type Error). 

$S = \{ \alpha, \{ \beta, \gamma \}, \emptyset \}$

<div class="bg-blue-900/10 p-4 rounded border border-blue-500/30 text-center">

Sea el conjunto complejo:

<p class="text-2xl font-mono text-yellow-400">
$$S = \{ \alpha, \{ \beta, \gamma \}, \emptyset \}$$
</p>

</div>

<v-clicks>

* **Cardinalidad $|S| = 3$**: Los elementos son $\alpha$, el conjunto $\{ \beta, \gamma \}$ y el conjunto vacío $\emptyset$.
* **El Abismo de la Pertenencia ($\in$):**
  * $\alpha \in S$ : **Verdadero.** Es un elemento directo.
  * $\beta \in S$ : <span class="text-red-500">**Falso.**</span> $\beta$ pertenece a un subconjunto de $S$, pero no a $S$ directamente. 
  * $\{ \beta, \gamma \} \in S$ : **Verdadero.** El conjunto entero actúa como una unidad atómica para $S$.
* **El Vacío como Elemento:**
  * $\emptyset \in S$ : **Verdadero.** Aquí el vacío no es la ausencia de elementos, es un objeto presente en la lista.

</v-clicks>

---

# Representación Formal: Comprensión Avanzada
### El Predicado de Pertenencia

No definimos conjuntos solo listando; usamos la **Lógica de Primer Orden** para filtrar el Universo ($U$).

$$A = \{ x \in U \mid \Phi(x) \}$$

* **$x \in U$**: El dominio de discurso (contexto). Sin un $U$ definido, caemos en la *Paradoja de Russell*.
* **$|$ o $:$**: Operador de restricción ("tal que").
* **$\Phi(x)$**: Una función booleana o **predicado**. Solo si $\Phi(x)$ es $True$, el objeto $x$ "entra en la bolsa".

<div class="mt-4 p-3 bg-green-900/20 rounded border-t border-green-500/50 text-sm">
  <strong>Ejemplo Computacional:</strong> 
  <code>Users = { u ∈ DB.all | u.active == true && u.age > 18 }</code>
  <br>La teoría de conjuntos es el motor detrás de las consultas SQL y el filtrado de Arrays funcional.
</div>



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

---
class: text-sm
---

# 1.3 El Dualismo Pertenencia e Inclusión
### Formalismo Lógico de Estructuras

La distinción entre $\in$ y $\subseteq$ no es solo notación, es una diferencia de **jerarquía de tipos**.

<div class="grid grid-cols-2 gap-4 mt-2">
<div class="bg-blue-900/10 p-3 rounded border-l-4 border-blue-500">

### Pertenencia ($\in$)
**Relación Incidencial: Objeto $\to$ Familia**
Indica que un ente es un componente directo del conjunto.
* **Definición:** $x \in A$ es un predicado atómico.
* **Ejemplo:** Si $A = \{ \emptyset, \{ \emptyset \} \}$, entonces $\emptyset \in A$.
</div>

<div class="bg-purple-900/10 p-3 rounded border-l-4 border-purple-500">

### Inclusión ($\subseteq$)
**Relación Estructural: Subconjunto $\to$ Superconjunto**
Indica que una estructura está contenida en otra.
* **Definición:** $A \subseteq B \iff \forall x (x \in A \implies x \in B)$.
* **Ejemplo:** $\{1, 2\} \subseteq \{1, 2, 3\}$.
</div>
</div>

---

# El Teorema del Conjunto Vacío ($\emptyset$)
### La base de la jerarquía conjuntista

El vacío no es "nada", es un objeto matemático con propiedades únicas:

<v-clicks>

1. **Unicidad:** Solo existe un único conjunto que no contiene elementos.
2. **Universalidad de la Inclusión:** $\emptyset \subseteq A$ para cualquier conjunto $A$.
   * *Demostración lógica:* La sentencia $\forall x (x \in \emptyset \implies x \in A)$ es **vacuamente verdadera** porque el antecedente ($x \in \emptyset$) siempre es falso.
3. **Pertenencia vs Inclusión:**
   * $\emptyset \subseteq \{1, 2\}$ : **Siempre Verdadero.**
   * $\emptyset \in \{1, 2\}$ : <span class="text-red-500">**Falso.**</span> (A menos que el vacío esté listado explícitamente como elemento).

</v-clicks>


 Diferencia entre $A = \emptyset$ (bolsa vacía) y $B = \{ \emptyset \}$ (bolsa que contiene una bolsa vacía). 
  En $A$ no hay nada, en $B$ hay <strong>un</strong> elemento. $|A|=0$, $|B|=1$.
<div class="mt-4 p-2 bg-yellow-900/20 rounded border border-yellow-500/50 text-xs">
  <strong>⚠️ Alerta de Examen:</strong> 
  Diferencia entre $A = \emptyset$ (bolsa vacía) y $B = \{ \emptyset \}$ (bolsa que contiene una bolsa vacía). 
  En $A$ no hay nada, en $B$ hay <strong>un</strong> elemento. $|A|=0$, $|B|=1$.
</div>

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
class: text-sm
---

# Laboratorio de Análisis: ¿Verdad o Falso?
### Desafiando la Intuición Estructural

Sea el conjunto complejo: 
$A = \{ 1, 2, \{3\} \}$

Analiza las siguientes proposiciones basadas en la **jerarquía de tipos**:

<div class="grid grid-cols-1 gap-2 mt-2">

<v-clicks>

1. **$1 \in A$** ➡️ <span class="text-green-500 font-bold">Verdadero.</span> Es un elemento atómico listado directamente en el primer nivel de $A$.
2. **$3 \in A$** ➡️ <span class="text-red-500 font-bold">Falso.</span> El entero `3` no existe en el primer nivel; existe el objeto `{3}`. Hay un **Error de Tipo**.
3. **$\{3\} \in A$** ➡️ <span class="text-green-500 font-bold">Verdadero.</span> El conjunto `{3}` es tratado como un objeto único (un elemento) por el conjunto $A$.
4. **$\{1, 2\} \subseteq A$** ➡️ <span class="text-green-500 font-bold">Verdadero.</span> Se cumple que todos los elementos de la izquierda ($1$ y $2$) están presentes en $A$.
5. **$\{3\} \subseteq A$** ➡️ <span class="text-red-500 font-bold">Falso.</span> Para que esto fuera cierto, el elemento `3` debería estar en $A$. Como el elemento es `{3}`, la inclusión correcta sería $\{\{3\}\} \subseteq A$.
6. **$\emptyset \subseteq A$** ➡️ <span class="text-green-500 font-bold">Verdadero.</span> Por el **Teorema de Vacuidad**, el vacío es subconjunto de cualquier estructura.

</v-clicks>

</div>

---

# Explicación Técnica: El Salto de Nivel
### ¿Por qué $\{3\} \not\subseteq A$?

Para que $X \subseteq Y$ sea **Verdadero**, se debe cumplir la prueba de pertenencia de sus elementos:



<div class="bg-gray-800 p-3 rounded border-l-4 border-yellow-500 mt-4">

**Prueba de Inclusión para $\{3\} \subseteq A$:**
1. Tomamos el elemento dentro de $\{3\}$, que es el número `3`.
2. Preguntamos: ¿$3 \in A$?
3. Resultado: **No**, en $A$ solo viven el `1`, el `2` y el bloque `{3}`.
4. Conclusión: La condición $\forall x (x \in \{3\} \implies x \in A)$ falla.

</div>

<div class="mt-4 text-xs opacity-70">
💡 <strong>Regla mnemotécnica:</strong> Para pasar de <b>Pertenencia</b> ($\in$) a <b>Inclusión</b> ($\subseteq$), debes "envolver" el elemento entre llaves adicionales.
<br>Si $\{3\} \in A$ es cierto, entonces $\{\{3\}\} \subseteq A$ es obligatorio.
</div>

---
layout: center
class: text-center
---

# ¡Fin de la Sesión 1!
Próxima sesión: **Operaciones y Álgebra de Conjuntos**