---
theme: seriph
background: https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=2000
class: text-center
highlighter: shiki
lineNumbers: true
transition: slide-left
title: Unidad 1 - Parte 1
---

# Teoría de Números y Matemática Computacional
## Sesión 1: Fundamentos y Aritmética Entera

<div class="pt-12 text-sm opacity-60">
  Ejes: Introducción a la Teoría de Números y Divisores (DIV/MOD)
</div>

---
layout: default
---

# 1. Introducción a la Teoría de Números

La Teoría de Números estudia las propiedades de los **números enteros** ($\mathbb{Z}$). En computación, esto es crítico porque el hardware trabaja con estados discretos (0 y 1).

### Conceptos Clave para la Ingeniería:
* **El Conjunto $\mathbb{Z}$:** $\{\dots, -2, -1, 0, 1, 2, \dots\}$.
* **Divisibilidad ($b|a$):** Decimos que un entero $b$ divide a $a$ si existe un entero $k$ tal que $a = b \cdot k$.
* **Números Primos:** Son los bloques de construcción de la seguridad informática. Un número $p > 1$ es primo solo si sus únicos divisores son $1$ y $p$.

> **Dato Técnico:** El Teorema Fundamental de la Aritmética garantiza que cualquier entero mayor a 1 tiene una **única** descomposición en factores primos.

---

# 2. Divisores: La Operación DIV y MOD

En matemáticas continuas la división da decimales, pero en **Matemática Computacional** usamos la división euclídea.

### El Teorema de la División
Para cualquier entero $a$ (dividendo) y un entero positivo $d$ (divisor):
$$a = d \cdot q + r$$

Donde:
* **$q$ (DIV):** Es el cociente entero. $q = \lfloor a/d \rfloor$.
* **$r$ (MOD):** Es el residuo. $r = a - (d \cdot q)$.

### Propiedad Fundamental del Residuo:
$$0 \le r < d$$

---

# Aplicaciones de MOD en Programación

La operación módulo (`%`) es una de las más potentes en desarrollo de software:

* **Determinación de Paridad:**
  * `n % 2 == 0` $\rightarrow$ Es Par.
  * `n % 2 != 0` $\rightarrow$ Es Impar.

* **Estructuras de Datos Circulares:**
  Si tienes un array de tamaño `N`, el siguiente índice siempre es:
  `nuevo_indice = (indice_actual + 1) % N`

* **Agrupamiento (Hashing):**
  Para distribuir datos en `k` cubetas: `posicion = id_usuario % k`.

---
layout: fact
---

# Ejemplo Práctico: DIV y MOD

**¿Cómo convertir 145 minutos a horas y minutos?**

$a = 145$ (minutos totales)
$d = 60$ (minutos por hora)

1. **$145 // 60 = 2$** (Este es el **DIV**, representa las horas).
2. **$145 \% 60 = 25$** (Este es el **MOD**, representa los minutos restantes).

**Resultado:** 2 horas y 25 minutos.

---
layout: section
---

# Sesión 2: Algoritmos Avanzados y Teoremas
## Ejes 3 y 4: Algoritmo de Euclides y Teorema de Fermat

---
layout: default
---

# 3. El Algoritmo Euclidiano (MCD)

El Máximo Común Divisor ($MCD$) de dos enteros es el número más grande que divide a ambos sin dejar residuo. El método de Euclides es el más eficiente para esto.

### Lógica Recursiva:
$$MCD(a, b) = MCD(b, a \pmod{b})$$

**Ejemplo paso a paso: $MCD(252, 105)$**

1. Dividimos $252$ entre $105$: $252 = 105 \cdot 2 + \mathbf{42}$
2. Dividimos $105$ entre $42$: $105 = 42 \cdot 2 + \mathbf{21}$
3. Dividimos $42$ entre $21$: $42 = 21 \cdot 2 + \mathbf{0}$

> El último residuo antes de llegar a cero es **21**. Por lo tanto, $MCD(252, 105) = 21$.

---

# 3.1 Algoritmo de Euclides Extendido

Es una variante que no solo halla el MCD, sino que expresa dicho valor como una combinación lineal de los números originales.

$$MCD(a, b) = a \cdot x + b \cdot y$$

### ¿Para qué sirve en computación?
Es la herramienta principal para encontrar el **inverso multiplicativo modular**. 
Si necesitas resolver $ax \equiv 1 \pmod{n}$, el algoritmo extendido te da la solución. Esto es lo que permite que el cifrado **RSA** funcione al generar las llaves privadas.

---

# 4. El Pequeño Teorema de Fermat

Este teorema es una propiedad fundamental de los números primos en la aritmética modular.

### Definición:
Si $p$ es un número **primo** y $a$ es un entero que no es divisible por $p$, entonces:
$$a^{p-1} \equiv 1 \pmod{p}$$

### Ejemplo:
Sea $a = 2$ y $p = 7$ (primo):
$2^{7-1} = 2^6 = 64$
$64 \pmod{7} = 1$ (porque $7 \cdot 9 = 63$, sobra $1$).



---

# Aplicaciones del Teorema de Fermat

1. **Test de Primalidad:** Permite a las computadoras verificar rápidamente si un número es primo (usado en la generación de certificados SSL).
2. **Reducción de Potencias:** Permite calcular potencias gigantes de forma instantánea.
   * *Ejemplo:* Calcular $3^{100000} \pmod{7}$ se vuelve trivial usando Fermat.
3. **Criptografía RSA:** Junto con el Teorema de Euler, permite el cifrado de datos en internet.

---
layout: quote
---

# "Los números primos son los átomos de la seguridad informática. Sin ellos, el comercio electrónico sería imposible."

---
layout: section
---

# Sesión 2: Algoritmos Avanzados y Teoremas
## Ejes 3 y 4: Algoritmo de Euclides y Teorema de Fermat

---
layout: default
---

# 3. El Algoritmo Euclidiano (MCD)

El Máximo Común Divisor ($MCD$) de dos enteros es el número más grande que divide a ambos sin dejar residuo. El método de Euclides es el más eficiente para esto.

### Lógica Recursiva:
$$MCD(a, b) = MCD(b, a \pmod{b})$$

**Ejemplo paso a paso: $MCD(252, 105)$**

1. Dividimos $252$ entre $105$: $252 = 105 \cdot 2 + \mathbf{42}$
2. Dividimos $105$ entre $42$: $105 = 42 \cdot 2 + \mathbf{21}$
3. Dividimos $42$ entre $21$: $42 = 21 \cdot 2 + \mathbf{0}$

> El último residuo antes de llegar a cero es **21**. Por lo tanto, $MCD(252, 105) = 21$.

---

# 3.1 Algoritmo de Euclides Extendido

Es una variante que no solo halla el MCD, sino que expresa dicho valor como una combinación lineal de los números originales.

$$MCD(a, b) = a \cdot x + b \cdot y$$

### ¿Para qué sirve en computación?
Es la herramienta principal para encontrar el **inverso multiplicativo modular**. 
Si necesitas resolver $ax \equiv 1 \pmod{n}$, el algoritmo extendido te da la solución. Esto es lo que permite que el cifrado **RSA** funcione al generar las llaves privadas.

---

# 4. El Pequeño Teorema de Fermat

Este teorema es una propiedad fundamental de los números primos en la aritmética modular.

### Definición:
Si $p$ es un número **primo** y $a$ es un entero que no es divisible por $p$, entonces:
$$a^{p-1} \equiv 1 \pmod{p}$$

### Ejemplo:
Sea $a = 2$ y $p = 7$ (primo):
$2^{7-1} = 2^6 = 64$
$64 \pmod{7} = 1$ (porque $7 \cdot 9 = 63$, sobra $1$).



---

# Aplicaciones del Teorema de Fermat

1. **Test de Primalidad:** Permite a las computadoras verificar rápidamente si un número es primo (usado en la generación de certificados SSL).
2. **Reducción de Potencias:** Permite calcular potencias gigantes de forma instantánea.
   * *Ejemplo:* Calcular $3^{100000} \pmod{7}$ se vuelve trivial usando Fermat.
3. **Criptografía RSA:** Junto con el Teorema de Euler, permite el cifrado de datos en internet.

---
layout: quote
---

# "Los números primos son los átomos de la seguridad informática. Sin ellos, el comercio electrónico sería imposible."

---
layout: section
---

# Sesión 4: Estándares de Codificación
## Ejes 7 y 8: BCD, ASCII, UNICODE y Datos Alfanuméricos

---
layout: default
---

# 7. Sistemas de Codificación: BCD

**BCD (Binary Coded Decimal)** es un estándar donde cada dígito decimal se representa con su propio cuarteto de bits (nibble).

### Comparación Crucial:
Para representar el número **12**:
* **Binario Puro:** `1100` (Un solo bloque).
* **BCD (8421):** `0001 0010` (El '1' y el '2' por separado).

| Ventajas | Desventajas |
|---|---|
| Lectura directa para humanos. | Menos eficiente (usa más bits). |
| Ideal para displays de 7 segmentos. | Operaciones matemáticas más complejas. |
| Evita errores de redondeo decimal. | No usa todas las combinaciones (10 a 15 sobran). |

---

# 7.1 El Estándar ASCII

**ASCII** (American Standard Code for Information Interchange) fue el primer gran estándar para textos.

* **ASCII Original:** 7 bits (128 caracteres). Suficiente para el alfabeto inglés y control.
* **ASCII Extendido:** 8 bits (256 caracteres). Incluye tildes, la 'ñ' y símbolos gráficos.



### Limitación Técnica:
El ASCII de 8 bits es insuficiente para la globalización. ¿Cómo representamos el alfabeto griego, cirílico o chino? Aquí es donde entra el siguiente estándar.

---

# 7.2 UNICODE: El Estándar Universal

Unicode asigna un "punto de código" único a **cada carácter de cada idioma del mundo**, incluyendo emojis y símbolos matemáticos.

### Esquemas de Codificación (UTF):
1. **UTF-8:** El más usado en la web. Es de longitud variable (1 a 4 bytes).
   - *Dato clave:* Los primeros 128 caracteres son **idénticos al ASCII**, lo que lo hace retrocompatible.
2. **UTF-16:** Usado internamente en Windows y Java. Siempre usa al menos 2 bytes.
3. **UTF-32:** Longitud fija. Muy ineficiente en espacio, pero rápido para indexar.

> **Curiosidad:** El emoji 😂 tiene el punto de código `U+1F602`.

---

# 8. Sistemas Binarios Alfanuméricos

Estos sistemas combinan números, letras y símbolos de control para la comunicación entre dispositivos.

### Métodos de Detección de Errores
Al transmitir datos alfanuméricos en binario, pueden ocurrir interferencias. Se utilizan mecanismos de control:

* **Bit de Paridad:** Se añade un bit extra para que el conteo de "1s" sea siempre Par o Impar.
* **Checksum (Suma de comprobación):** Suma aritmética de los bytes transmitidos.
* **CRC (Cyclic Redundancy Check):** Basado en división de polinomios (teoría de números aplicada).

---
layout: center
---

# 🏁 Resumen de la Unidad 1

1. **Matemática:** DIV/MOD y Euclides gestionan la lógica de los datos.
2. **Seguridad:** Fermat y Primos permiten el cifrado (RSA).
3. **Bases:** Binario y Hexadecimal son el lenguaje del hardware.
4. **Texto:** ASCII y Unicode permiten la comunicación humana global.

---
layout: end
---

# ¡Unidad 1 Completada!
## Matemática Computacional
### 24 Horas de Teoría y Práctica