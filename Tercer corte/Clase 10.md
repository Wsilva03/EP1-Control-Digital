# Observadores de Estado y Control Multivariable

## 1. Eliminación de Error de Estado Estacionario

### Conceptos

- **Regulación**: Todos los estados tienen una referencia de valor cero.
- **Servo**: Al menos uno de los estados tiene una referencia distinta de cero para ajustar la salida $y_{ss}$ a una entrada $r_{ss}$, logrando $e_{ss} = 0$.

### Técnicas de Diseño

1. **Desacoplamiento mediante retroalimentación:** Se utiliza retroalimentación para anular las interacciones entre variables.
2. **Control Óptimo:** Minimiza una función de costo para garantizar un desempeño deseado.
3. **Colocación de polos:** Se ajustan los polos del sistema controlado para lograr la dinámica deseada.

### Ley de Control

Para lograr seguimiento integral, se propone la siguiente ley de control:

$$ u(k) = -Kx(k) + Fr(k) $$

donde $K$ es el vector de ganancias y $F$ compensa la referencia.

#### Tipos comunes de leyes de control:

- Control de retroalimentación: Ajusta las entradas basándose en el error (diferencia entre salida deseada y real).
- Control feedforward: Compensa perturbaciones conocidas sin depender del error.
- Control en tiempo discreto: Diseñado para sistemas digitales, donde las actualizaciones ocurren en pasos discretos.

#### Ejercicio 1

Dado un sistema con 
$A = \begin{bmatrix} 0 & 1 \\ -2 & -3 \end{bmatrix}$ 
y 
$B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$
, encuentra los valores de $K$ y $F$ para eliminar el error de estado estacionario con una entrada de referencia constante.

**Solución**:
Para este sistema, calculamos $K$ y $F$ mediante la asignación de polos deseada. Supongamos polos en $-1$ y $-2$, y utilizamos la técnica de asignación de polos.

1. Calcular los valores de $K$:
    - Asumimos una matriz de polos deseados y resolvemos para $K$ usando la función de asignación de polos.

2. Determinar $F$ para compensar la referencia:
    - Usamos $F = -1 / (C (A - BK)^{-1} B)$ donde $C = \begin{bmatrix} 1 & 0 \end{bmatrix}$.

| Matriz | Valores |
|--------|---------|
| $A$ | $\begin{bmatrix} 0 & 1 \\ -2 & -3 \end{bmatrix}$ |
| $B$ | $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$ |
| $K$ | Calculado |
| $F$ | Calculado |

#### Ejercicio 2
Diseña una ley de control para un sistema cuya matriz $A$ tiene polos en $z = -0.5$ y $z = -1$, logrando que el error de estado estacionario sea cero cuando $r(t) = 1$.

**Solución**:
1. Colocamos los polos del sistema en $z = -0.5$ y $z = -1$.
2. Calculamos $K$ para esta colocación de polos y aplicamos la ley de control.

---

## 2. Esquema de Control Integral

### Conceptos
- Se introduce una nueva variable de estado $v(k)$ para compensar la referencia y asegurar seguimiento.
- Ecuación de estado ampliada:
  $$
  \begin{bmatrix} x(k+1) \\ v(k+1) \end{bmatrix} = \begin{bmatrix} A & 0 \\ -C & 1 \end{bmatrix} \begin{bmatrix} x(k) \\ v(k) \end{bmatrix} + \begin{bmatrix} B \\ 0 \end{bmatrix} u(k) + \begin{bmatrix} 0 \\ 1 \end{bmatrix} r(k)
  $$

#### Ejercicio 1
Para el sistema con $A = \begin{bmatrix} 0.5 & 0.1 \\ -0.2 & 0.7 \end{bmatrix}$, $B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$, y $C = \begin{bmatrix} 1 & 0 \end{bmatrix}$, define el sistema ampliado y escribe sus ecuaciones de estado.

**Solución**:
- Expresamos las matrices ampliadas:
  $$
  A_a = \begin{bmatrix} 0.5 & 0.1 & 0 \\ -0.2 & 0.7 & 0 \\ -1 & 0 & 1 \end{bmatrix}, \quad B_a = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}
  $$

| Matriz Ampliada | Valores |
|-----------------|---------|
| $A_a$ | $\begin{bmatrix} 0.5 & 0.1 & 0 \\ -0.2 & 0.7 & 0 \\ -1 & 0 & 1 \end{bmatrix}$ |
| $B_a$ | $\begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$ |

#### Ejercicio 2
Implementa el esquema de control integral para un sistema en Simulink y comprueba que el error de estado estacionario es cero para una entrada escalón.

**Solución**:
1. Crear el modelo en Simulink utilizando el esquema de control integral.
2. Introducir un escalón como entrada de referencia.
3. Verificar que el sistema sigue la referencia sin error estacionario.

---

## 3. Observador de Estados

### Conceptos
- Un observador permite estimar los estados de un sistema cuando no se pueden medir directamente.
- Ecuación del observador de estados:
  $$
  \hat{x}(k+1) = (A - K_pC)\hat{x}(k) + Bu + K_p y
  $$
- Este observador es útil cuando el sistema es **observable**.

Cuando no todos los estados del sistema son medibles, los observadores estiman los estados internos utilizando las entradas y salidas disponibles.

### Tipos de Observadores
1. **Luenberger:** Usa un modelo lineal para estimar estados con un error convergente a cero.
2. **Extendido:** Maneja sistemas no lineales mediante una linealización local.
3. **Kalman:** Combina mediciones con un modelo probabilístico para minimizar el error de estimación.


#### Ejercicio 1
Comprueba la observabilidad de un sistema con $A = \begin{bmatrix} 1 & 2 \\ 0 & 1 \end{bmatrix}$ y $C = \begin{bmatrix} 1 & 0 \end{bmatrix}$. ¿Es posible diseñar un observador de estados?

**Solución**:
1. Calcular la matriz de observabilidad:
   $$
   O = \begin{bmatrix} C \\ CA \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 1 & 2 \end{bmatrix}
   $$
2. Determinar si $O$ es de rango completo (tiene rango igual a 2). El sistema es observable.

| Matriz de Observabilidad | Valor |
|--------------------------|-------|
| $O$ | $\begin{bmatrix} 1 & 0 \\ 1 & 2 \end{bmatrix}$ |

#### Ejercicio 2
Calcula la matriz de ganancias $K_p$ para un observador de estados en un sistema con polos deseados en $z = -0.5$.

**Solución**:
1. Seleccionamos polos en $z = -0.5$.
2. Utilizamos el método de asignación de polos para determinar $K_p$.

| Parámetro | Valor |
|-----------|-------|
| Polos deseados | $z = -0.5$ |
| $K_p$ | Calculado |

---

## 4. Error de Estimación y Diseño del Observador

### Conceptos
- El error de estimación depende de la matriz $A$.
- Agregar un vector de ganancias $K_p$ permite ajustar el observador y reducir el error:
  $$
  e(k+1) = (A - K_pC)e(k)
  $$

#### Ejercicio 1
Diseña un observador para el sistema con $A = \begin{bmatrix} 1.2 & 0 \\ 1 & 1 \end{bmatrix}$, $B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$, y polos del observador en $z = -0.3$.

**Solución**:
1. Comprobamos la observabilidad del sistema.
2. Calculamos $K_p$ para colocar los polos en $z = -0.3$.

| Parámetro | Valor |
|-----------|-------|
| Matriz $A$ | $\begin{bmatrix} 1.2 & 0 \\ 1 & 1 \end{bmatrix}$ |
| Polos deseados | $z = -0.3$ |
| $K_p$ | Calculado |

#### Ejercicio 2
Implementa un observador en Simulink y grafica la evolución del error de estimación para diferentes valores de $K_p$.

**Solución**:
1. Configurar el observador en Simulink.
2. Probar distintos valores de $K_p$ y observar cómo el error de estimación se reduce.

| Parámetro | Valores |
|-----------|---------|
| $K_p$ | Diferentes valores probados |
| Error de estimación | Gráfica en Simulink |

---

## Referencias

- Cote, J.E. 8. Observadores de estados (Presentación). 2024. 
- Ogata, K. (2010). Discrete-Time Control Systems. Pearson. Profundiza en análisis y diseño de sistemas de control discreto.
- Franklin, G., Powell, J., & Workman, M. (1997). Digital Control of Dynamic Systems. Addison-Wesley. Ideal para estrategias de control digital, como controladores discretos y diseño de sistemas.
