# Observadores de Estado y Control Multivariable

## 1. Eliminación de Error de Estado Estacionario

### Conceptos
- **Regulación**: Todos los estados tienen una referencia de valor cero.
- **Servo**: Al menos uno de los estados tiene una referencia distinta de cero para ajustar la salida $y_{ss}$ a una entrada $r_{ss}$, logrando $e_{ss} = 0$.

### Ley de Control
Para lograr seguimiento integral, se propone la siguiente ley de control:
$$
u(k) = -Kx(k) + Fr(k)
$$
donde $K$ es el vector de ganancias y $F$ compensa la referencia.

#### Ejercicio 1
Dado un sistema con $A = \begin{bmatrix} 0 & 1 \\ -2 & -3 \end{bmatrix}$ y $B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$, encuentra los valores de $K$ y $F$ para eliminar el error de estado estacionario con una entrada de referencia constante.

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
# Controladores por Retroalimentación de Estados

## 1. Controlabilidad y Observabilidad

### Conceptos
- **Controlabilidad**: Un sistema es controlable si es posible transferir cualquier estado inicial $x(t_0)$ a otro estado en un tiempo finito mediante un vector de control.
- **Observabilidad**: Un sistema es observable si es posible determinar el estado a partir de la observación de la salida en un intervalo de tiempo.

### Matriz de Controlabilidad
La matriz de controlabilidad $U$ se define como:
$$
U = [B \ AB \ A^2B \ \dots \ A^{n-1}B]
$$
- El sistema es controlable si el rango de $U$ es igual al número de estados (dimensión de $A$).

#### Ejercicio 1
Verificar si el sistema con:
$$
A = \begin{bmatrix} 1.5 & 1 \\ 1 & 0 \end{bmatrix}, \quad B = \begin{bmatrix} 1 \\ 0 \end{bmatrix}
$$
es controlable.

**Solución**:
1. Calcular $AB$:
   $$
   AB = \begin{bmatrix} 1.5 & 1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} 1.5 \\ 1 \end{bmatrix}
   $$
2. Formar la matriz de controlabilidad $U$:
   $$
   U = \begin{bmatrix} 1 & 1.5 \\ 0 & 1 \end{bmatrix}
   $$
3. Calcular el determinante de $U$:
   $$
   \text{det}(U) = (1)(1) - (0)(1.5) = 1 \neq 0
   $$
   El sistema es **controlable**.

| Matriz | Valores |
|--------|---------|
| $A$ | $\begin{bmatrix} 1.5 & 1 \\ 1 & 0 \end{bmatrix}$ |
| $B$ | $\begin{bmatrix} 1 \\ 0 \end{bmatrix}$ |
| $U$ | $\begin{bmatrix} 1 & 1.5 \\ 0 & 1 \end{bmatrix}$ |
| Determinante de $U$ | $1$ |

#### Ejercicio 2
Verificar si el sistema con:
$$
A = \begin{bmatrix} 0 & 1 \\ -0.4 & -1.3 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}
$$
es controlable.

---

### Matriz de Observabilidad
La matriz de observabilidad $V$ se define como:
$$
V = \begin{bmatrix} C \\ CA \\ CA^2 \\ \vdots \\ CA^{n-1} \end{bmatrix}
$$
- El sistema es observable si el rango de $V$ es igual al número de estados.

#### Ejercicio 1
Verificar si el sistema con:
$$
A = \begin{bmatrix} 1.5 & 1 \\ 1 & 0 \end{bmatrix}, \quad C = \begin{bmatrix} 2 & -1 \end{bmatrix}
$$
es observable.

**Solución**:
1. Calcular $CA$:
   $$
   CA = \begin{bmatrix} 2 & -1 \end{bmatrix} \begin{bmatrix} 1.5 & 1 \\ 1 & 0 \end{bmatrix} = \begin{bmatrix} 2 & 2 \end{bmatrix}
   $$
2. Formar la matriz de observabilidad $V$:
   $$
   V = \begin{bmatrix} 2 & -1 \\ 2 & 2 \end{bmatrix}
   $$
3. Calcular el determinante de $V$:
   $$
   \text{det}(V) = (2)(2) - (-1)(2) = 6 \neq 0
   $$
   El sistema es **observable**.

| Matriz | Valores |
|--------|---------|
| $A$ | $\begin{bmatrix} 1.5 & 1 \\ 1 & 0 \end{bmatrix}$ |
| $C$ | $\begin{bmatrix} 2 & -1 \end{bmatrix}$ |
| $V$ | $\begin{bmatrix} 2 & -1 \\ 2 & 2 \end{bmatrix}$ |
| Determinante de $V$ | $6$ |

---

## 2. Control por Retroalimentación de Estados

### Conceptos
- Objetivo: Colocar los polos del sistema en lazo cerrado mediante ganancias proporcionales.
- La señal de control $u(t)$ se obtiene a partir de las variables de estado:
  $$
  u(k) = -Kx(k)
  $$
  
### Metodología de Diseño
1. Comprobar la controlabilidad del sistema.
2. Calcular el polinomio característico de $A$ (lazo abierto).
3. Definir el polinomio deseado en lazo cerrado con polos específicos.
4. Calcular la matriz de ganancias $K$.

#### Ejercicio 1
Para el sistema con:
$$
A = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ -1 & -5 & -6 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}
$$
diseñar un controlador de retroalimentación que ubique los polos en $z = -0.2 \pm j0.4$ y $z = -0.02$.

**Solución**:
1. Verificamos la controlabilidad del sistema calculando la matriz $U$ y su rango (omitido aquí).
2. Calculamos el polinomio característico deseado:
   $$
   P_d(z) = (z + 0.2 + 0.4j)(z + 0.2 - 0.4j)(z + 0.02)
   $$
3. Obtenemos las ganancias $K$ utilizando el polinomio deseado y la técnica de asignación de polos.

| Parámetro | Valor |
|-----------|-------|
| Polos deseados | $z = -0.2 \pm j0.4$, $z = -0.02$ |
| $K$ | Calculado |

#### Ejercicio 2
Para el sistema:
$$
A = \begin{bmatrix} 0 & -0.4 \\ 1 & -1.3 \end{bmatrix}, \quad B = \begin{bmatrix} 0.8 \\ 1 \end{bmatrix}
$$
calcula las ganancias de retroalimentación para ubicar los polos en $z = -0.5$.

---

## Resumen
- **Controlabilidad** y **observabilidad** son propiedades esenciales para determinar si un sistema puede ser controlado o observado completamente.
- La **retroalimentación de estados** permite controlar el sistema ajustando los polos de lazo cerrado.
- **Asignación de polos** se usa para diseñar las ganancias del controlador y garantizar que el sistema cumpla con las especificaciones deseadas.

---

## Referencias

- Cote, J.E. 8. Control por retroalimentación de estados (Presentación). 2024. 
- Dorf, R. C., & Bishop, R. H. (2010). Modern Control Systems. Pearson. Este libro es un recurso extenso sobre control digital, ideal para fundamentos y aplicaciones avanzadas.
- Kuo, B. C., & Golnaraghi, F. (2002). Automatic Control Systems. Wiley. Este texto proporciona una base sólida en teoría de control, incluyendo control digital y retroalimentación.




