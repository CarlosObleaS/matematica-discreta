---
theme: default
background: https://cover.sli.dev
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Matemática Discreta
  Semana 4 - Sesión 1
drawings:
  persist: false
transition: slide-left
title: Conjunto Potencia y Producto Cartesiano
mdc: true
---

# Conjunto Potencia y Producto Cartesiano

### Matemática Discreta — Semana 4, Sesión 1
Ingeniería de Sistemas

---
layout: default
---

# Agenda de hoy

<v-clicks>

- 🔢 **Conjunto Potencia** — definición y construcción
- 📐 **Fórmula** $|\mathcal{P}(A)| = 2^n$ — ¿por qué funciona?
- 🗂️ **Producto Cartesiano** — pares ordenados
- 📊 **Cardinalidad** de $A \times B$
- 🧩 **Ejercicios** integrados

</v-clicks>

---
layout: section
---

# Parte 1
## Conjunto Potencia

---
layout: default
---

# ¿Qué es el Conjunto Potencia?

> Dado un conjunto $A$, el **conjunto potencia** $\mathcal{P}(A)$ es el conjunto de **todos los subconjuntos** de $A$.

$$\mathcal{P}(A) = \{ S \mid S \subseteq A \}$$

<v-click>

### Observaciones clave

| Hecho | Detalle |
|---|---|
| $\emptyset \in \mathcal{P}(A)$ | El vacío **siempre** es subconjunto |
| $A \in \mathcal{P}(A)$ | El conjunto mismo **siempre** está incluido |
| $\emptyset \neq \{\emptyset\}$ | ¡Cuidado con esta distinción! |

</v-click>

---
layout: default
---

# Construcción Explícita

Sea $A = \{a, b\}$. Listemos **todos** sus subconjuntos:

<v-clicks>

- Subconjunto de 0 elementos: $\emptyset$
- Subconjuntos de 1 elemento: $\{a\}$, $\{b\}$
- Subconjunto de 2 elementos: $\{a, b\}$

</v-clicks>

<v-click>

$$\mathcal{P}(A) = \bigl\{ \emptyset,\ \{a\},\ \{b\},\ \{a,b\} \bigr\}$$

$$|\mathcal{P}(A)| = 4 = 2^2$$

</v-click>

---
layout: default
---

# Patrón: crecimiento de $\mathcal{P}(A)$

| $n = \vert A \vert$ | Conjunto $A$ | $\mathcal{P}(A)$ | $\vert \mathcal{P}(A) \vert$ |
| :---: | :--- | :--- | :---: |
| 0 | $\emptyset$ | $\{ \emptyset \}$ | $1 = 2^0$ |
| 1 | $\{ a \}$ | $\{ \emptyset, \{ a \} \}$ | $2 = 2^1$ |
| 2 | $\{ a, b \}$ | $\{ \emptyset, \{ a \}, \{ b \}, \{ a, b \} \}$ | $4 = 2^2$ |
| 3 | $\{ a, b, c \}$ | *(8 subconjuntos en total)* | $8 = 2^3$ |
| $n$ | ... | ... | $2^n$ |

> [!CAUTION]
> El crecimiento es **exponencial** — para $n = 30$ hay más de mil millones de subconjuntos.

---
layout: default
---

# ¿Por qué $2^n$?

<div class="text-sm leading-tight">

### Argumento combinatorio

Para cada elemento $x \in A$ tomamos una decisión binaria:
$x \in S$ o $x \notin S$

<v-click>

Con $n$ elementos hay $n$ decisiones independientes (2 opciones cada una):
$$\underbrace{2 \times 2 \times \cdots \times 2}_{n \text{ veces}} = 2^n$$

</v-click>

<v-click>

<div class="mt-2">

### Ejemplo con $A = \{a, b, c\}$

| $a$ | $b$ | $c$ | Subconjunto |
|:---:|:---:|:---:|:--- |
| ✗ | ✗ | ✗ | $\emptyset$ |
| ✓ | ✗ | ✗ | $\{a\}$ |
| ✗ | ✓ | ✓ | $\{b,c\}$ |
| ✓ | ✓ | ✓ | $\{a,b,c\}$ |

</div>

</v-click>

</div>

---
layout: default
---

# Ejercicio rápido ✏️

<v-click>

Sea $B = \{1, 2, 3\}$. Calcula $\mathcal{P}(B)$ y verifica que $|\mathcal{P}(B)| = 8$.

</v-click>

<v-click>

### Solución

$$\mathcal{P}(B) = \bigl\{\, \emptyset,\ \{1\},\ \{2\},\ \{3\},\ \{1,2\},\ \{1,3\},\ \{2,3\},\ \{1,2,3\} \,\bigr\}$$

</v-click>

<v-click>

**¿Pertenencia o subconjunto?**

- ¿Es $\{1,2\} \in \mathcal{P}(B)$? &nbsp;→ ✅ Sí
- ¿Es $\{1,2\} \subseteq \mathcal{P}(B)$? &nbsp;→ ❌ No
- ¿Es $\{\{1,2\}\} \subseteq \mathcal{P}(B)$? &nbsp;→ ✅ Sí

</v-click>

---
layout: section
---

# Parte 2
## Producto Cartesiano

---
layout: default
---

# Definición: Par Ordenado

Un **par ordenado** $(a, b)$ tiene una primera y una segunda componente.

$$\boxed{(a, b) = (c, d) \iff a = c \land b = d}$$

<v-click>

### Diferencia crucial con conjuntos

| Concepto | Ejemplo | Observación |
|---|---|---|
| Conjunto | $\{a, b\} = \{b, a\}$ | El orden **no importa** |
| Par ordenado | $(a, b) \neq (b, a)$ | El orden **sí importa** |

</v-click>

<v-click>

> $(1, 2) \neq (2, 1)$ aunque ambos usan los mismos elementos.

</v-click>

---
layout: default
---

# Definición: Producto Cartesiano

> Dados dos conjuntos $A$ y $B$, el **producto cartesiano** es:

$$A \times B = \{(a,b) \mid a \in A \land b \in B\}$$

<v-click>

### Ejemplo

Sea $A = \{1, 2\}$ y $B = \{x, y, z\}$:

$$A \times B = \{(1,x),\ (1,y),\ (1,z),\ (2,x),\ (2,y),\ (2,z)\}$$

$$|A \times B| = 2 \times 3 = 6$$

</v-click>

---
layout: two-cols
---

# Visualización tabular

$A = \{1, 2\}$, $B = \{x, y, z\}$

|  | $x$ | $y$ | $z$ |
|:---:|:---:|:---:|:---:|
| **1** | (1,x) | (1,y) | (1,z) |
| **2** | (2,x) | (2,y) | (2,z) |

::right::

<v-click>

# Propiedades

$$|A \times B| = |A| \cdot |B|$$

<br>

> ⚠️ En general:
> $$A \times B \neq B \times A$$

<br>

> ✅ Pero sí:
> $$|A \times B| = |B \times A|$$

</v-click>

---
layout: default
---

# Producto Cartesiano de 3 conjuntos

$$A \times B \times C = \{(a,b,c) \mid a \in A,\ b \in B,\ c \in C\}$$

$$|A \times B \times C| = |A| \cdot |B| \cdot |C|$$

<v-click>

### Ejemplo práctico

Una contraseña formada por: 1 letra $\in \{A,B,C\}$, 1 dígito $\in \{0,1\}$, 1 símbolo $\in \{!, ?\}$

$$|\{A,B,C\} \times \{0,1\} \times \{!,?\}| = 3 \cdot 2 \cdot 2 = 12 \text{ contraseñas}$$

</v-click>

<v-click>

### Conexión futura 🔗

> El producto cartesiano $A \times A$ es el dominio natural de las **relaciones binarias** — tema de la próxima semana.

</v-click>

---
layout: default
---

# Ejercicio integrador ✏️

Sea $A = \{0, 1\}$ y $B = \{a, b\}$.

<v-clicks>

1. Calcula $A \times B$
2. Calcula $B \times A$
3. ¿Son iguales? ¿Tienen la misma cardinalidad?
4. Calcula $\mathcal{P}(A)$ y $|\mathcal{P}(A \times B)|$

</v-clicks>

<v-click>

### Respuestas

1. $A \times B = \{(0,a),(0,b),(1,a),(1,b)\}$
2. $B \times A = \{(a,0),(a,1),(b,0),(b,1)\}$
3. No son iguales, pero $|A \times B| = |B \times A| = 4$
4. $\mathcal{P}(A) = \{\emptyset, \{0\}, \{1\}, \{0,1\}\}$ y $|\mathcal{P}(A \times B)| = 2^4 = 16$

</v-click>

---
layout: default
---

# Resumen de la sesión

| Concepto | Definición | Cardinalidad |
|---|---|:---:|
| Conjunto Potencia | Todos los subconjuntos de $A$ | $2^n$ |
| Par Ordenado | $(a,b)$: el orden importa | — |
| Producto Cartesiano | Todos los pares $(a,b)$ con $a \in A$, $b \in B$ | $|A| \cdot |B|$ |

<v-click>

### Para la próxima sesión 📅

> **Sesión 2:** Cardinalidad — conjuntos finitos, principio de inclusión-exclusión, e infinitos contables vs. no contables.

</v-click>

---
layout: center
class: text-center
---

# ¡Gracias!

### ¿Preguntas?

Matemática Discreta — Semana 4, Sesión 1

*Ingeniería de Sistemas*