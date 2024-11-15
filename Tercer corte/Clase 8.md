# Espacio de Estados

El espacio de estados es una representación matemática de los sistemas dinámicos que considera no solo las entradas y salidas, sino también otras variables que permiten describir la dinámica interna del sistema. Esta metodología se conoce como **representación interna**, en contraste con la función de transferencia, que se considera una **representación externa**.

## 1. Conceptos Clave

- **Estado**: Conjunto de variables necesarias para describir completamente el comportamiento de un sistema.
- **Variables de Estado**: Variables que determinan el comportamiento del sistema, y no necesariamente deben ser medibles.
- **Ecuaciones de Estado**: Ecuaciones que relacionan las variables de estado a través de operadores matemáticos y describen el sistema en el llamado espacio de estados.

> 🔑 **_Espacio de Estados:_** Representación matemática de un sistema que considera todas las variables de estado relevantes para caracterizar su dinámica.

## 2. Representación Matemática

En un sistema, se tienen las siguientes variables y ecuaciones:

- **Entradas**: $u_1(k), u_2(k), ..., u_r(k)$
- **Salidas**: $y_1(k), y_2(k), ..., y_m(k)$
- **Variables de Estado**: $x_1(k), x_2(k), ..., x_n(k)$

Las ecuaciones de estado y de salida se representan como:

$$\mathbf{X}(k+1) = \mathbf{A} \mathbf{X}(k) + \mathbf{B} \mathbf{u}(k)$$
$$\mathbf{y}(k) = \mathbf{C} \mathbf{X}(k) + \mathbf{D} \mathbf{u}(k)$$

Donde:
- **A** es la matriz de estados.
- **B** es la matriz de entrada.
- **C** es la matriz de salida.
- **D** es la matriz de transmisión directa.

## 3. Características del Espacio de Estados

Las ecuaciones en espacio de estados pueden adoptar distintas formas, incluyendo:

- **No lineales**: Cuando las funciones $f$ y $g$ no son lineales.
- **Dependientes del tiempo**: Cuando las funciones $f$ y $g$ varían con el tiempo.
- **Sistemas Multivariable**: El espacio de estados permite representar sistemas con múltiples entradas y salidas (MIMO).

En el caso de sistemas **lineales invariantes en el tiempo (LTI)**, las ecuaciones se simplifican, y los sistemas se representan de forma matricial, con matrices constantes en el tiempo.

> 🔑 **_Sistemas LTI:_** Sistemas donde las funciones de estado no dependen del tiempo y son lineales.

## 4. Construcción de un Modelo en Espacio de Estados

Para construir un modelo en espacio de estados a partir de una ecuación diferencial, se debe:

1. Expresar la ecuación diferencial en términos de variables de estado.
2. Despejar las ecuaciones de estado y de salida.
3. Organizar los términos en matrices $A$, $B$, $C$, y $D$.

## 5. Ejemplo Básico de Representación en Espacio de Estados

Considerando el sistema mecánico:
$$M\ddot{y}(t) + B\dot{y}(t) + Ky(t) = u(t)$$

Las ecuaciones de estado se representan como:

$$\mathbf{X}(k+1) = \begin{bmatrix} 0 & 1 \\ -\frac{K}{M} & -\frac{B}{M} \end{bmatrix} \mathbf{X}(k) + \begin{bmatrix} 0 \\ \frac{1}{M} \end{bmatrix} u(k)$$
$$y(k) = \begin{bmatrix} 1 & 0 \end{bmatrix} \mathbf{X}(k)$$

Donde $\mathbf{X}(k)$ representa el vector de estado compuesto por la posición y la velocidad.

**Conclusión**: El espacio de estados ofrece una forma compacta y completa de modelar sistemas dinámicos, lo que facilita el análisis y diseño de controladores robustos.

---

# Operaciones en el Espacio de Estados

En el control multivariable, el espacio de estados permite representar una función de transferencia en diversas formas. Este tipo de representación facilita tanto el análisis como el diseño de sistemas y controladores, ofreciendo diferentes vistas estructurales del sistema en función de la aplicación deseada.

## 1. Representación en Espacio de Estados desde Función de Transferencia

Una función de transferencia genérica se puede expresar como:

$$G(z) = \frac{b_0 z^n + b_1 z^{n-1} + \dots + b_{n-1} z + b_n}{z^n + a_1 z^{n-1} + \dots + a_{n-1} z + a_n}$$

Esta función se puede representar en distintas formas canónicas dentro del espacio de estados, entre las que destacan:
- **Forma Canónica Controlable**
- **Forma Canónica Observable**
- **Forma de Jordan**

> 🔑 **_Espacio de Estados desde Función de Transferencia:_** Representación de la función de transferencia en diferentes formas estructurales para simplificar el análisis y diseño del sistema.

## 2. Formas Canónicas en el Espacio de Estados

### 2.1 Forma Canónica Controlable

Para una función de transferencia $G(z)$, la forma canónica controlable se define mediante la siguiente estructura matricial:

$$\mathbf{X}(k+1) = \begin{bmatrix} 0 & 1 & 0 & \dots & 0 \\ 0 & 0 & 1 & \dots & 0 \\ \vdots & \vdots & \vdots & \ddots & \vdots \\ -a_n & -a_{n-1} & -a_{n-2} & \dots & -a_1 \end{bmatrix} \mathbf{X}(k) + \begin{bmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{bmatrix} u(k)$$

$$y(k) = \begin{bmatrix} b_n & b_{n-1} & \dots & b_1 \end{bmatrix} \mathbf{X}(k)$$

> 🔑 **_Forma Canónica Controlable:_** Representación que permite controlar el sistema desde el vector de entrada mediante matrices estructuradas.

### 2.2 Forma Canónica Observable

La forma canónica observable es otra estructura común en espacio de estados, representada así:

$$
X(k+1) = \begin{bmatrix}
0 & 1 & 0 & \cdots & 0 \\
0 & 0 & 1 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
-a_n & -a_{n-1} & -a_{n-2} & \cdots & -a_1
\end{bmatrix} X(k) + \begin{bmatrix}
0 \\
0 \\
\vdots \\
1
\end{bmatrix} u(k)
$$

$$
y(k) = \begin{bmatrix}
b_n & b_{n-1} & \cdots & b_1
\end{bmatrix} X(k)
$$

> 🔑 **_Forma Canónica Observable:_** Representación en la que cada estado puede ser observado directamente desde la salida.

### 2.3 Forma Canónica Diagonal

Cuando los polos de la función de transferencia son diferentes, se puede representar en forma canónica diagonal, como sigue:

$$\mathbf{X}(k+1) = \begin{bmatrix} P_1 & 0 & \dots & 0 \\ 0 & P_2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & P_n \end{bmatrix} \mathbf{X}(k) + \begin{bmatrix} 1 \\ 1 \\ \vdots \\ 1 \end{bmatrix} u(k)$$

$$y(k) = \begin{bmatrix} c_1 & c_2 & \dots & c_n \end{bmatrix} \mathbf{X}(k)$$

> 🔑 **_Forma Diagonal:_** Estructura donde el sistema se descompone en modos independientes, cada uno con un valor propio específico.

---

# Procesos Integrantes y Métodos de Sintonización

La sintonización de controladores en procesos industriales implica ajustar los parámetros para alcanzar un comportamiento óptimo del sistema. En procesos con características integrantes, la variable de proceso responde de manera lineal cuando la variable de control se ajusta, introduciendo un tiempo muerto que debe ser considerado en el diseño del controlador.

## 1. Procesos Integrantes

Un proceso integrante es aquel en el que la variable de proceso (PV) continúa cambiando en respuesta a un cambio en la variable de control (CV) en lazo abierto, moviéndose linealmente, como se muestra en la Figura 9. Esto se modela con la siguiente función de transferencia:

$$G_m(s) = \frac{K_m \cdot e^{-s \tau_m}}{s}$$

Donde:
- $K_m$: Ganancia de integración, calculada como:

  $$K_m = \frac{O_2 - O_1}{(I_2 - I_1) \cdot (T_3 - T_2)}$$

- $\tau_m$: Tiempo muerto, calculado como:

  $$\tau_m = T_2 - T_1$$

> 🔑 **_Proceso Integrante:_** Un tipo de proceso en el que la variable de proceso cambia continuamente en respuesta a un ajuste en la variable de control.

## 2. Métodos de Sintonización de Controladores PID

La sintonización de un controlador PID consiste en ajustar los parámetros de ganancia proporcional ($K_c$), tiempo integral ($T_i$), y tiempo derivativo ($T_d$) para lograr un rendimiento de control robusto. Para esto, se debe identificar la dinámica del proceso y seleccionar un método de sintonización adecuado.

### 2.1 Métodos de Sintonización para Procesos Autorregulados

#### Controlador PI

Para implementar un controlador PI en un proceso autorregulado, los valores de $K_c$ y $T_i$ se pueden calcular mediante métodos como los siguientes:

| Método | K_c | T_i |
|---|---|---|
| Chien | $\frac{0.7 T_m}{K_m \tau_m}$| $2.33 \tau_m$|
| Ziegler and Nichols | $\frac{0.9 T_m}{K_m \tau_m}$| $3.33 \tau_m$|
| Callender | $\frac{0.568 T_m}{K_m \tau_m}$| $3.64 \tau_m$|
| Moros | $\frac{0.8 T_m}{K_m \tau_m}$| $3 \tau_m$|
| Reswick | $\frac{0.2}{K_m}$| $0.2 \tau_m$|
| Fertik and Sharpe | $\frac{0.56}{K_m}$| $0.65 T_m$|

#### Controlador PID

Para un controlador PID en un proceso autorregulado, los parámetros de sintonización se calculan mediante métodos como los siguientes:

| Método | K_c | T_i | T_d |
|---|---|---|---|
| Chien | $\frac{0.95T_m}{K_m \tau_m}$| $2.38 \tau_m$| $0.42 \tau_m$|
| Ziegler-Nichols | $a \frac{T_m}{K_m \tau_m}$, donde $a \in [1.2, 2]$| $2 \tau_m$| $0.5 \tau_m$|
| Callender | $\frac{1.066}{K_m \tau_m}$| $1.418 \tau_m$| $0.353 \tau_m$|
| Parr | $\frac{1.25 T_m}{K_m \tau_m}$| $2.5 \tau_m$| $0.4 \tau_m$|
| Moros | $\frac{1.2 T_m}{K_m \tau_m}$| $2 \tau_m$| $0.42 \tau_m$|

> 🔑 **_Sintonización de Controladores:_** Ajuste de parámetros para lograr un control robusto y eficiente, basado en las características del proceso.

### 2.2 Métodos de Sintonización para Procesos Integrantes

#### Controlador PI

En un proceso integrante, un controlador PI se sintoniza utilizando métodos como los siguientes:

| Método | K_c | T_i |
|---|---|---|
| Ziegler and Nichols | $\frac{0.9}{K_m \tau_m}$| $3.33 \tau_m$|
| Coon | $\frac{1.0}{K_m \tau_m}$| $0$|
| Åström and Hägglund | $\frac{0.63}{K_m \tau_m}$| $3.2 \tau_m$|
| Hay | $\frac{0.42}{K_m \tau_m}$| $5.8 \tau_m$|
| Skogestad | $\frac{0.404}{K_m \tau_m}$| $7 \tau_m$|

#### Controlador PID

Para sintonizar un controlador PID en un proceso integrante, se utilizan métodos como los siguientes:

| Método | K_c | T_i | T_d |
|---|---|---|---|
| Ford | $\frac{1.48}{K_m \tau_m}$| $2 \tau_m$| $0.37 \tau_m$|
| Hay | $\frac{0.4}{K_m \tau_m}$| $3.2 \tau_m$| $0.8 \tau_m$|
| Åström and Hägglund | $\frac{0.94}{K_m \tau_m}$| $2 \tau_m$| $0.5 \tau_m$|
| Leonard | $\frac{0.74}{K_m \tau_m}$| $12.2 \tau_m$| $0.41 \tau_m$|
| Rotach | $\frac{1.21}{K_m \tau_m}$| $1.6 \tau_m$| $0.48 \tau_m$|

> 🔑 **_Métodos de Sintonización:_** Métodos específicos de cálculo para ajustar los controladores PI y PID según las características del proceso, ya sea autorregulado o integrante.

---

## Ejercicios

### 📚 Ejercicio 1

**Enunciado**: Dado el sistema de ecuaciones en diferencias:

$$
\begin{cases}
y[k+1] = 0.5y[k] + 2u[k] \\
y[k+2] = -0.3y[k+1] + u[k]
\end{cases}
$$

Obtén la representación en espacio de estados en la forma canónica controlable.

**Solución**:

1. **Definir las variables de estado**:
   Definimos $x_1[k] = y[k]$ y $x_2[k] = y[k+1]$.
   
2. **Ecuaciones en términos de los estados**:
   $$
   x_1[k+1] = x_2[k]
   $$
   $$
   x_2[k+1] = -0.3x_2[k] + u[k]
   $$

3. **Escribir el sistema en forma matricial**:
    $$
    \begin{bmatrix}
    x_1(k+1) \\
    x_2(k+1)
    \end{bmatrix}
    =
    \begin{bmatrix}
    0 & 1 \\
    0 & -0.3
    \end{bmatrix}
    \begin{bmatrix}
    x_1(k) \\
    x_2(k)
    \end{bmatrix}
    +
    \begin{bmatrix}
    0 \\
    1
    \end{bmatrix}
    u(k)
    $$

    La salida es:

    $$
    y(k) = \begin{bmatrix}
    1 & 0
    \end{bmatrix}
    \begin{bmatrix}
    x_1(k) \\
    x_2(k)
    \end{bmatrix}
    $$

**Conclusión**: La representación en espacio de estados en forma canónica controlable es:

$$
\mathbf{X}(k+1) = \begin{bmatrix} 0 & 1 \\ 0 & -0.3 \end{bmatrix} \mathbf{X}(k) + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u(k)
$$
$$
y(k) = \begin{bmatrix} 1 & 0 \end{bmatrix} \mathbf{X}(k)
$$

---

### 📚 Ejercicio 2

**Enunciado**: Dado un sistema con función de transferencia:

$$
G(s) = \frac{2}{s^2 + 3s + 2}
$$

Convierte esta función de transferencia a espacio de estados en forma canónica observable.

**Solución**:

1. **Expresar la función de transferencia en términos de los polos**:
   Factorizamos el denominador:
   $$
   G(s) = \frac{2}{(s+1)(s+2)}
   $$
2. **Definir las ecuaciones de estado**:
   
   Usamos las siguientes ecuaciones en la forma canónica observable:
   
   $$
   x_1[k+1] = -2x_1[k] + x_2[k] + u[k]
   $$
   $$
   x_2[k+1] = -3x_1[k] + u[k]
   $$

3. **Escribir el sistema en forma matricial**:
   
$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix}
=
\begin{bmatrix}
0.8 & 1 \\
0 & 0.3
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k)
\end{bmatrix}
+
\begin{bmatrix}
0 \\
1
\end{bmatrix}
u(k)
$$
La salida es: 
$$
y(k) = \begin{bmatrix}
1 & 0
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k)
\end{bmatrix}
$$

**Conclusión**: La representación en espacio de estados en forma canónica observable es:

$$
\mathbf{X}(k+1) = \begin{bmatrix} -2 & 1 \\ 0 & -3 \end{bmatrix} \mathbf{X}(k) + \begin{bmatrix} 1 \\ 0 \end{bmatrix} u(k)
$$
$$
y(k) = \begin{bmatrix} 2 & 0 \end{bmatrix} \mathbf{X}(k)
$$

---

### 📚 Ejercicio 3

**Enunciado**: Dado el sistema en espacio de estados:

$$
\mathbf{X}(k+1) = \begin{bmatrix} 0 & 1 \\ -2 & -3 \end{bmatrix} \mathbf{X}(k) + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u(k)
$$
$$
y(k) = \begin{bmatrix} 1 & 0 \end{bmatrix} \mathbf{X}(k)
$$

Encuentra la función de transferencia $G(s) = \frac{Y(s)}{U(s)}$ del sistema.

**Solución**:

1. **Calcular $sI - A$:
   $$
   sI - A = \begin{bmatrix} s & -1 \\ 2 & s+3 \end{bmatrix}
   $$

2. **Calcular la inversa de $sI - A$:
   
   $$
   (sI - A)^{-1} = \frac{1}{s^2 + 3s + 2} \begin{bmatrix} s + 3 & 1 \\ -2 & s \end{bmatrix}
   $$

3. **Obtener la función de transferencia**:
   $$
   G(s) = C(sI - A)^{-1}B + D = \begin{bmatrix} 1 & 0 \end{bmatrix} \frac{1}{s^2 + 3s + 2} \begin{bmatrix} s + 3 \\ -2 \end{bmatrix}
   $$

**Conclusión**: La función de transferencia es:
$$
G(s) = \frac{s + 3}{s^2 + 3s + 2}
$$

---

### 📚 Ejercicio 4

**Enunciado**: Dado el sistema de matrices:

$$
A = \begin{bmatrix} 0 & 1 \\ -4 & -5 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} 1 & 0 \end{bmatrix}, \quad D = \begin{bmatrix} 0 \end{bmatrix}
$$

Encuentra los polos del sistema en espacio de estados.

**Solución**:

1. **Formar la ecuación característica**:
   Los polos se encuentran resolviendo el determinante de $sI - A = 0$.
   $$
   sI - A = \begin{bmatrix} s & -1 \\ 4 & s+5 \end{bmatrix}
   $$

2. **Calcular el determinante de $sI - A$:
   $$
   \det(sI - A) = (s)(s + 5) - (-1)(4) = s^2 + 5s + 4
   $$

3. **Resolver para los valores propios**:
   Factorizamos la ecuación característica:
   $$
   s^2 + 5s + 4 = (s + 4)(s + 1) = 0
   $$
   Los valores propios, y por tanto los polos, son:
   $$
   s = -4 \quad \text{y} \quad s = -1
   $$

**Conclusión**: Los polos del sistema son $s = -4$ y $s = -1$.

---

### 📚 Ejercicio 5

**Enunciado**: Dado un proceso de nivel de tanque que se comporta como un proceso integrante, los tiempos registrados fueron: $T_1 = 5$ s y $T_2 = 10$ s. La salida $O_1$ y $O_2$ corresponde a 2 m y 3 m, respectivamente, y las entradas $I_1 = 0.5$ L/s y $I_2 = 1$ L/s. Calcula el valor de la ganancia de integración $K_m$ y el tiempo muerto $\tau_m$ del sistema.

**Solución**:

1. **Cálculo de $K_m$:
   $$
   K_m = \frac{O_2 - O_1}{(I_2 - I_1) \cdot (T_3 - T_2)}
   $$
   Dado que $O_2 = 3$ m, $O_1 = 2$ m, $I_2 = 1$ L/s, $I_1 = 0.5$ L/s, y $T_3 - T_2 = 5$:
   $$
   K_m = \frac{3 - 2}{(1 - 0.5) \cdot (10 - 5)} = \frac{1}{0.5 \cdot 5} = \frac{1}{2.5} = 0.4 \, \text{m/L}
   $$

2. **Cálculo de $\tau_m$:
   $$
   \tau_m = T_2 - T_1 = 10 - 5 = 5 \, \text{s}
   $$

**Conclusión**: La ganancia de integración $K_m$ es 0.4 m/L y el tiempo muerto $\tau_m$ es 5 s.

---

### 📚 Ejercicio 6

**Enunciado**: Un proceso integrante tiene los siguientes valores: $T_1 = 2$ s, $T_2 = 6$ s, $O_1 = 1.5$ m, $O_2 = 4$ m, $I_1 = 0.3$ L/s y $I_2 = 0.8$ L/s. Determina el valor de $K_m$ y $\tau_m$.

**Solución**:

1. **Cálculo de $K_m$:
   $$
   K_m = \frac{O_2 - O_1}{(I_2 - I_1) \cdot (T_3 - T_2)}
   $$
   Sustituyendo los valores:
   $$
   K_m = \frac{4 - 1.5}{(0.8 - 0.3) \cdot (6 - 2)} = \frac{2.5}{0.5 \cdot 4} = \frac{2.5}{2} = 1.25 \, \text{m/L}
   $$

2. **Cálculo de $\tau_m$:
   $$
   \tau_m = T_2 - T_1 = 6 - 2 = 4 \, \text{s}
   $$

**Conclusión**: La ganancia de integración $K_m$ es 1.25 m/L y el tiempo muerto $\tau_m$ es 4 s.

---

## Conclusiones

- El espacio de estados permite representar la función de transferencia en diferentes formas estructuradas, útiles para el análisis y control de sistemas.
- La sintonización de controladores PID en procesos industriales varía según el tipo de proceso (autorregulado o integrante).
- Elegir el método adecuado para la sintonización de controladores es fundamental para optimizar el rendimiento del sistema de control, garantizando estabilidad y robustez.

## Referencias
- Cote, J.E. 8. Intro Espacio de estados (Presentación). 2024. 
- Franklin, G. F., Powell, J. D., & Emami-Naeini, A. (2015). Feedback Control of Dynamic Systems. Pearson.
- Ogata, K. (2009). Modern Control Engineering. Prentice Hall.
