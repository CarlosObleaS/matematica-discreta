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
layout: default
---

# El Condicional como un "Contrato de Software"
Para entender la **Verdad Vacua**, veamos el condicional $p \rightarrow q$ como una promesa legal.

> **Promesa del Desarrollador:** "Si me pagas ($p$), entonces te entrego el software ($q$)"

| Pago ($p$) | Entrega ($q$) | $p \rightarrow q$ | Estado del Contrato |
| :---: | :---: | :---: | :--- |
| **V** | **V** | ✅ **V** | **Cumplimiento:** Pagaste y recibiste. Todo legal. |
| **V** | **F** | ❌ **F** | **ESTAFA:** Pagaste y no recibiste nada. La promesa se rompió. |
| **F** | **V** | ✅ **V** | **Cortesía (Vacuo):** No pagaste, pero te lo regalé. No violé mi promesa. |
| **F** | **F** | ✅ **V** | **Neutral (Vacuo):** Ni pagaste ni recibíste. No hay incumplimiento. |

<div class="grid grid-cols-2 gap-4 mt-4">
<div class="border-l-4 border-red-500 pl-4">
  <p class="text-sm font-bold text-red-400">El Punto Crítico</p>
  <p class="text-xs italic">La única forma de que un condicional sea <b>Falso</b> es que el antecedente se cumpla y el consecuente no.</p>
</div>
<div class="border-l-4 border-blue-500 pl-4">
  <p class="text-sm font-bold text-blue-400">Nota para Ingeniería</p>
  <p class="text-xs italic">Si $p$ es Falso, el sistema es "Consistente por Defecto". No hay error de lógica porque la condición de activación nunca ocurrió.</p>
</div>
</div>

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
s
---
layout: default
---

#  El Bicondicional ($\leftrightarrow$): Detector de Igualdad
En ingeniería, $p \leftrightarrow q$ (si y solo si) se utiliza para verificar la **consistencia de estados**.

### Ejemplo: Sincronización de Base de Datos (Réplica)
Imagina un sistema con un nodo Maestro ($p$) y un nodo Espejo ($q$). El sistema está en **Estado Saludable** solo si ambos nodos están en el mismo nivel de actualización.

| Maestro Activo ($p$) | Espejo Activo ($q$) | Salud del Sistema ($p \leftrightarrow q$) | Diagnóstico |
| :---: | :---: | :---: | :--- |
| **V** | **V** | ✅ **V** | **Sincronizado:** Operación normal. |
| **V** | **F** | ❌ **F** | **Error:** El espejo falló. Riesgo de pérdida. |
| **F** | **V** | ❌ **F** | **Error:** El maestro falló. Inconsistencia. |
| **F** | **F** | ✅ **V** | **Consistente:** Sistema apagado correctamente. |

> **Fundamento:** $p \leftrightarrow q$ es la conjunción de dos implicaciones: $(p \rightarrow q) \wedge (q \rightarrow p)$. Si una falla, la igualdad se rompe.

---
layout: default
---

# El XOR ($\oplus$): Disyunción Exclusiva
<div class="text-sm">
El operador $\oplus$ es la base de la **aritmética binaria**. Representa "uno u otro, pero no ambos".

### Ejemplo: Control de Acceso (MFA)
Solo se permite **un** método de validación física a la vez.

<div class="scale-90 origin-top-left -mt-2">

| Huella ($p$) | Tarjeta ($q$) | Acceso ($p \oplus q$) | Lógica de Hardware |
| :---: | :---: | :---: | :--- |
| **V** | **V** | ❌ **F** | **Bloqueo:** Duplicidad de identidad. |
| **V** | **F** | ✅ **V** | **Éxito:** Validación por biometría. |
| **F** | **V** | ✅ **V** | **Éxito:** Validación por proximidad. |
| **F** | **F** | ❌ **F** | **Rechazo:** Sin credencial. |

</div>



[Image of XOR logic gate and truth table]


<div class="mt-2 text-xs opacity-80">
**Aplicación en Redes:** RAID 5 usa XOR para recuperar datos perdidos mediante la diferencia de bits.
</div>

</div>

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
layout: default
---

# La Flecha de Doble Lectura: $A \rightarrow B$

Dependiendo de por dónde empieces a leer, la flecha te dice cosas distintas sobre la relación.

### ⬅️ Lectura de Izquierda a Derecha (Suficiencia)
* **Foco:** El que inicia ($A$).
* **Significado:** "Si tengo $A$, ya me basta para asegurar que $B$ ocurre".
* **Concepto:** $A$ es **Suficiente** para $B$.

### ➡️ Lectura de Derecha a Izquierda (Necesidad)
* **Foco:** El que recibe ($B$).
* **Significado:** "Si veo que $B$ ocurre, es porque $A$ tuvo que estar ahí antes".
* **Concepto:** $B$ es **Necesario** para $A$.

---

### Ejemplo de Oro: "Si tienes Wifi ($w$), puedes navegar ($n$)"
$$w \rightarrow n$$

1. **Lectura IZQ $\rightarrow$ DER:** Tener Wifi es **suficiente** para navegar. (Si te conectas, ya estás adentro).
2. **Lectura DER $\leftarrow$ IZQ:** Poder navegar es prueba de que **necesariamente** tienes conexión. (Si estás navegando, es porque hay Wifi).
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
layout: default
---

# 🕵️ Análisis de Validez: El Caso del Log
Un argumento es válido si la conclusión es una consecuencia lógica de las premisas.

**Regla de Negocio:**
1. $(\neg p \lor q) \rightarrow r$ (Si hay falla, hay log)
2. $\neg r$ (No hay log)

**Deducción Automática:**
* Como la flecha apunta al **requisito** ($r$ es necesario para la falla), y el requisito no está...
* Entonces la **falla no ocurrió**.
* Por lo tanto: **$p$ es Verdadero** (El servidor responde).

> **En Ingeniería:** Esto se llama *Modus Tollens*. Si el efecto no está, la causa no ocurrió.
---
layout: default
---
<div class="text-sm">

# ¿Qué es una Tautología? 
Es una fórmula lógica que es **siempre verdadera**.

### Ejemplo en Código:
`if (servidor_activo || !servidor_activo) { ... }`

### En el análisis de argumentos:
| $p$ | $q$ | $[(p \rightarrow q) \land p] \rightarrow q$ |
| :---: | :---: | :---: |
| V | V | **V** |
| V | F | **V** |
| F | V | **V** |
| F | F | **V** |

**Resultado:** Como todos son **V**, es una Tautología.

</div>
---
layout: default
---

# Contradicción (El "Bug" Fatal)
<div class="text-sm">
Una contradicción es una proposición que es **falsa para todos los valores** de verdad. En ingeniería, representa una condición imposible o un bloqueo total.

* **Símbolo:** Se representa con $\perp$ o una **F** constante.
* **Ejemplo:** $p \wedge \neg p$ ("El sistema está encendido y apagado al mismo tiempo").

<div class="scale-90 origin-top-left mt-4">

| $p$ | $\neg p$ | $p \wedge \neg p$ | Diagnóstico Técnico |
| :---: | :---: | :---: | :--- |
| **V** | **F** | ❌ **F** | **Conflicto:** Estado físicamente imposible. |
| **F** | **V** | ❌ **F** | **Conflicto:** Estado físicamente imposible. |

</div>



<div class="mt-6 text-xs bg-red-900/20 p-2 rounded border border-red-500/50">
**Nota para programadores:** Una contradicción en un `if` genera "Código Muerto" (dead code), ya que esa sección del programa jamás se ejecutará.
</div>

</div>
---
layout: default
---

# Contingencia (El "Depende")
<div class="text-sm">
Es el escenario más común. El resultado **no es fijo**; puede ser verdadero o falso dependiendo de las variables de entrada.

* **Definición:** Su tabla de verdad contiene al menos un **V** y al menos un **F**.
* **Ejemplo:** $p \rightarrow q$ ("Si el usuario es admin, tiene acceso").

<div class="scale-90 origin-top-left mt-4">

| Admin ($p$) | Acceso ($q$) | $p \rightarrow q$ | Resultado del Sistema |
| :---: | :---: | :---: | :--- |
| **V** | **V** | ✅ **V** | Acceso correcto (Admin logueado). |
| **V** | **F** | ❌ **F** | **Error:** El admin no pudo entrar. |
| **F** | **V** | ✅ **V** | Acceso concedido por otra vía. |
| **F** | **F** | ✅ **V** | Correcto: No es admin, no entra. |

</div>



<div class="mt-4 text-xs bg-blue-900/20 p-2 rounded border border-blue-500/50">
**Importancia:** La mayoría de los requerimientos de software son contingencias. El sistema debe estar preparado para manejar tanto el éxito como el fallo.
</div>

</div>
---
layout: default
---

# 🔎 Glosario de Símbolos Especiales
<div class="text-sm">

Para identificar los resultados de una tabla de verdad, usamos estos "atajos":

| Símbolo | Nombre | Significado Técnico | Uso en Clase |
| :---: | :--- | :--- | :--- |
| **$\top$** | **Tautología** | El "Verdadero" absoluto (Siempre 1). | Éxito total. |
| **$\perp$** | **Contradicción** | El "Falso" absoluto (Siempre 0). | Error o Bug. |

### ¿Por qué la T invertida ($\perp$)?
Imagina que es un **muro o un tope**. La lógica "choca" contra algo imposible y no puede avanzar. 

**Ejemplo:**
Si intentas entrar a un sistema con `usuario && !usuario`, el resultado es $\perp$.
</div>

<div class="mt-8 p-4 bg-yellow-900/10 border-l-4 border-yellow-500 text-xs">
**Tip Pro:** Si en un examen te piden demostrar una contradicción, al final de tu tabla puedes poner el símbolo $\perp$ para indicar que "todo dio falso".
</div>
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
