---
theme: academic
background: https://images.unsplash.com/photo-1509228468518-180dd482180c?auto=format&fit=crop&q=80
class: text-center
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
transition: fade-out
title: Conectivos Lógicos Avanzados y Formalización
---

# Matemática Discreta para Ingeniería
## Conectivos Avanzados, Jerarquía y Formalización de Enunciados

<div class="pt-12">
  <span class="text-sm opacity-50">Unidad I: Lógica Proposicional - Parte II</span>
</div>

---

# 1. El Condicional ($\rightarrow$): Implicación Lógica

En ingeniería, el condicional $p \rightarrow q$ define la **causalidad formal** y las **precondiciones** de un sistema.

### Definición Semántica
Es falso **únicamente** cuando el antecedente ($p$) es verdadero y el consecuente ($q$) es falso. 

| $p$ | $q$ | $p \rightarrow q$ | Interpretación en Sistemas |
|:---:|:---:|:---:|:---|
| V | V | **V** | Ejecución correcta. |
| V | F | **F** | **Error de Lógica:** La condición se cumple pero el resultado falla. |
| F | V | **V** | Verdad vacua (Vacuously True). |
| F | F | **V** | Verdad vacua. |

> **Fundamento Teórico:** La "Verdad Vacua" ocurre porque el condicional no afirma que $q$ sea verdadero, sino que $q$ **debe ser** verdadero *siempre que* $p$ lo sea. Si $p$ es falso, la sentencia no ha sido violada.

---

# 2. Bicondicional ($\leftrightarrow$) y XOR ($\oplus$)

### Bicondicional (Equivalencia)
$p \leftrightarrow q$ es verdadero si y solo si $p$ y $q$ tienen el mismo valor de verdad.
* **Formalización:** $(p \rightarrow q) \wedge (q \rightarrow p)$
* **Uso:** Definiciones formales y estados de igualdad de bits.

### Disyunción Exclusiva (XOR)
$p \oplus q$ representa exclusividad estricta: "uno u otro, pero no ambos".
* **Definición:** $(p \lor q) \wedge \neg(p \wedge q)$
* **Propiedad:** Es la base de los sumadores binarios en hardware ($Sum = A \oplus B$).

| $p$ | $q$ | $p \leftrightarrow q$ | $p \oplus q$ |
|:---:|:---:|:---:|:---:|
| V | V | **V** | **F** |
| V | F | **F** | **V** |
| F | V | **F** | **V** |
| F | F | **V** | **F** |

---

# 3. Jerarquía de Operadores y Ambigüedad

Para evitar ambigüedad en expresiones complejas como $\neg p \wedge q \rightarrow r \vee s$, se establece una precedencia estricta (de mayor a menor):

1.  **Negación ($\neg$)**: Operador unario de mayor prioridad.
2.  **Conjunción ($\wedge$) y Disyunción ($\vee$)**: Tienen igual jerarquía (se evalúan de izquierda a derecha si no hay paréntesis).
3.  **Condicional ($\rightarrow$) y Bicondicional ($\leftrightarrow$)**: Los de menor jerarquía.

### El rol de los paréntesis
Los paréntesis rompen la jerarquía. En ingeniería de software, el uso de paréntesis es una **buena práctica** para evitar errores de interpretación por el compilador o por otros desarrolladores.

> **Regla de Oro:** Ante la duda, usa paréntesis. $p \wedge (q \lor r)$ es radicalmente distinto a $(p \wedge q) \lor r$.

---

# 4. Formalización de Lenguaje Natural

La traducción del lenguaje humano al formal requiere identificar **Condiciones Necesarias y Suficientes**.

### Claves de Traducción
* **"Pero" / "Sin embargo":** Se formalizan como conjunciones ($\wedge$).
* **"Ni p ni q":** $\neg p \wedge \neg q$.
* **"A menos que q":** $\neg q \rightarrow p$ o $p \lor q$.

### Suficiencia vs. Necesidad
| Frase | Formalización | Explicación |
|:---|:---:|:---|
| "$p$ es **suficiente** para $q$" | $p \rightarrow q$ | Si ocurre $p$, basta para garantizar $q$. |
| "$p$ es **necesario** para $q$" | $q \rightarrow p$ | Si ocurre $q$, es obligatorio que haya ocurrido $p$. |
| "$p$ **solo si** $q$" | $p \rightarrow q$ | No puede ocurrir $p$ sin que ocurra $q$. |

---

# 5. Análisis de Párrafos y Validez

Para analizar un argumento complejo:
1.  **Atomización:** Identificar proposiciones simples ($p, q, r$).
2.  **Estructuración:** Identificar premisas ($P_1, P_2...$) y conclusión ($C$).
3.  **Evaluación:** Un argumento es válido si $[P_1 \wedge P_2 \wedge ... \wedge P_n] \rightarrow C$ es una **tautología**.

### Ejemplo de Formalización Avanzada:
> "Si el servidor no responde ($\neg p$) o la base de datos está caída ($q$), entonces el log de errores se genera ($r$). El log de errores no se genera. Por lo tanto, el servidor responde."

**Formalización:**
* Premisa 1: $(\neg p \lor q) \rightarrow r$
* Premisa 2: $\neg r$
* Conclusión: $p$

---

# Ejercicios de Aplicación (Challenge)

### Ejercicio 1: Tablas de Verdad
Determine si la siguiente forma es una contradicción, contingencia o tautología:
$$(p \oplus q) \leftrightarrow \neg(p \leftrightarrow q)$$

### Ejercicio 2: Formalización de Requerimientos
Un cliente de software dice: *"El sistema debe permitir el acceso ($a$) solo si el usuario está autenticado ($u$) y tiene permisos de admin ($p$). Sin embargo, si el usuario es un invitado ($i$), no debe tener acceso."*

**Tarea:** Exprese los requerimientos del cliente en una sola fórmula lógica.

### Ejercicio 3: Condición Necesaria
Formalice: *"Que el puerto 80 esté abierto es condición necesaria para que el servidor web funcione, pero no es suficiente."*

---
layout: center
---

# Solución al Ejercicio 2 (Sugerida)

$((a \rightarrow (u \wedge p)) \wedge (i \rightarrow \neg a))$

¿Deseas que profundicemos en las pruebas de validez mediante **Reglas de Inferencia**?