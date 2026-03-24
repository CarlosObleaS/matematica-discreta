---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
transition: slide-left
title: Clase 1 - Fundamentos y Alfabeto Lógico
---

# Matemáticas Discretas
## Clase 1: Fundamentos y Alfabeto Lógico

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer hover:bg-white hover:bg-opacity-10">
    Presiona Espacio para continuar <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: default
---

# 1. Introducción a la Lógica Formal

La **Lógica** es la disciplina que estudia los métodos y principios utilizados para distinguir el razonamiento correcto del incorrecto.

### ¿Por qué es importante en Computación? 🤔

- **Circuitos Digitales:** Las compuertas lógicas (AND, OR, NOT) son la base del hardware.
- **Algoritmos:** Las condiciones `if/else` son expresiones lógicas.
- **Bases de Datos:** Las consultas SQL utilizan lógica booleana para filtrar datos.
- **Inteligencia Artificial:** Sistemas de inferencia y resolución de problemas.

---

# 2. ¿Qué es una Proposición?

Es una oración declarativa que tiene un **valor de verdad**: o es verdadera ($V$) o es falsa ($F$), pero no ambas a la vez.

<div class="grid grid-cols-2 gap-4">
<div>

### ✅ Sí son proposiciones
- "2 + 2 = 4" (Es $V$)
- "La Tierra es plana" (Es $F$)
- "Quito es la capital de Ecuador" ($V$)

</div>
<div>

### ❌ No son proposiciones
- **Órdenes:** "¡Cierra la puerta!"
- **Preguntas:** "¿Qué hora es?"
- **Exclamaciones:** "¡Qué lindo día!"
- **Ambigüedades:** "Él es alto" (¿Quién es él?)

</div>
</div>

---

# 3. Variables Proposicionales

Para simplificar el análisis, representamos las proposiciones con letras minúsculas (usualmente a partir de la $p$).

### Ejemplos:
- $p$: "Está lloviendo".
- $q$: "La calle está mojada".
- $r$: "2 es un número primo".

> **Dato:** Estas letras se conocen como **átomos** o proposiciones atómicas porque no se pueden dividir más.

---

# 4. Conectivos Lógicos (Parte I)

Los conectivos nos permiten crear **proposiciones compuestas**.

| Conectivo | Símbolo | Lectura Natural |
| --- | :---: | --- |
| **Negación** | $\neg$ | "No", "No es cierto que" |
| **Conjunción** | $\wedge$ | "y", "pero", "además" |
| **Disyunción** | $\vee$ | "o" |

### Ejemplos rápidos:
- $\neg p$: "No está lloviendo".
- $p \wedge q$: "Está lloviendo **y** la calle está mojada".
- $p \vee q$: "Está lloviendo **o** la calle está mojada".

---

# 5. Traducción Inicial

Pasar del lenguaje natural al lenguaje formal es clave para evitar confusiones.

### Ejercicio de ejemplo:
**Frase:** "No es cierto que hoy es lunes, pero hoy hay clases".

1. **Identificar átomos:**
    - $p$: "Hoy es lunes".
    - $q$: "Hoy hay clases".
2. **Identificar conectores:**
    - "No es cierto que" $\rightarrow \neg$
    - "pero" (funciona como una "y") $\rightarrow \wedge$
3. **Fórmula resultante:**
    $$\neg p \wedge q$$

---
layout: center
class: text-center
---

# ¡Gracias!
## ¿Preguntas?

[Regresar al temario](https://notion.so/tu-pagina)