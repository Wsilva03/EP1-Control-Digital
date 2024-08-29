<h1 align="center"> La Transformada Z de adelantos y atrasos </h1>

Es una herramienta matemática utilizada en el análisis y diseño de sistemas discretos en el dominio del tiempo que permite convertir secuencias temporales en una representación algebraica en el dominio Z, facilitando el estudio de sus propiedades y el diseño de filtros y controladores. El adelanto  $z^n$  y el atraso  $z^{-n}$  en la Transformada Z representan desplazamientos temporales hacia el futuro o el pasado, respectivamente, lo que es útil para manipular señales y analizar su comportamiento dinámico en sistemas de control digital y procesamiento de señales.

# 1.  Muestreo y Representación Matemática de Sistemas Discretos

 El muestreo es el proceso mediante el cual una señal continua se convierte en una secuencia de muestras discretas a intervalos regulares. Esto permite que los sistemas continuos puedan ser analizados y controlados digitalmente.
> **Muestreo:** Proceso de convertir una señal continua en una secuencia de valores discretos.<br>
> **Periodo de Muestreo (T):** Intervalo de tiempo entre dos muestras consecutivas. 
>$$f(t) =f(kt)$$
Señal continua:
$y(t) = 5 \cdot \sin(1.04t)$

Señal muestreada:
$y(kT) = 5 \cdot \sin(1.04kT)$

# 2. Ecuacion en diferencias

 Las ecuaciones en diferencias describen la relación matemática entre las entradas y salidas de un sistema discreto, representando su dinámica.

 ## ¿Para qué sirven estas ecuaciones?

- **Modelado de sistemas:** Se utilizan para describir la evolución de sistemas discretos en el tiempo, como sistemas de control, procesamiento de señales, y demas.
- **Análisis de sistemas:** Permiten analizar la estabilidad, la respuesta a entradas.
- **Diseño de sistemas:** Se utilizan para diseñar filtros, controladores y otros sistemas discretos.

## Ecuacion

 $$b_n u(k) + b_{n-1} u(k-1) + \ldots + b_0 u(k-n) = y(k) + a_{n-1} y(k-1) + \ldots + a_0 y(k-n)$$

- **y(k):** Salida del sistema en el instante de tiempo k.
- **u(k):** Entrada del sistema en el instante de tiempo k.
- **a, b:** Coeficientes que caracterizan el sistema.

## Tipos de ecuaciones

- **Lineal, invariante en el tiempo, homogénea:** 
$$y(k+2)+0.8y(k+1)+0.07y(k)u(k)=0$$
- **Lineal, variante en el tiempo, homogénea:** 
$$y(k+4)+sin(0.4k)y(k+1)+0.3y(k)=0$$
- **No lineal, invariante en el tiempo, homogénea:** 
$$y(k+1)=−0.1y(k)^2$$

# 3. Solución de Ecuaciones en Diferencias

Las ecuaciones en diferencias se pueden resolver mediante métodos iterativos o utilizando la Transformada Z, dependiendo del objetivo del análisis.

>Métodos Iterativos: Técnica para encontrar soluciones numéricas mediante repetidas aproximaciones.<br>
>Transformada Z: Herramienta matemática que convierte ecuaciones en diferencias en expresiones algebraicas en el dominio Z.


# 4. Transformada Z

La Transformada Z es la contraparte discreta de la Transformada de Laplace y es fundamental para analizar sistemas de control digital.

>Transformada de Laplace: Herramienta utilizada en el análisis de sistemas continuos.
>$$\mathcal{L}\{f(t)\} = \int_0^\infty f(t)e^{-st} dt$$
>Transformada Z: Convierte una secuencia discreta en una función algebraica en el dominio Z.<br>
>$$Z\{f(k)\} = \sum_{k=0}^\infty f(k)z^{-k}$$

# 5. Adelantos y Atrasos en la Transformada Z

En sistemas de control digital, los conceptos de adelantos y atrasos son críticos para modelar y analizar el comportamiento dinámico de las señales.

>**Atraso (Delay):** Desplazamiento temporal de una señal hacia el pasado.
>$$Z\{f(k-1)\} = z^{-1}F(z)$$
>**Adelanto (Advance):** Desplazamiento temporal de una señal hacia el futuro.
>$$Z\{f(k+1)\} = z[F(z) - f(0)]$$

# 6. Funciones de Transferencia en el Dominio Z

La función de transferencia en el dominio Z describe la relación entre la entrada y la salida de un sistema discreto, facilitando el análisis y diseño de sistemas de control.

- Función de Transferencia: Relación algebraica entre la salida 
𝑌(𝑧) y la entrada X(z) de un sistema.
- Función de Transferencia Pulso: Relación entre la salida y entrada muestreadas de un sistema dinámico.

$$H(z)=\frac{Y(z)}{X(z)}$$

# 7. Sistemas Causales y No Causales

Se aborda la diferencia entre sistemas causales y no causales, donde la causalidad es esencial para determinar si un sistema responde a entradas pasadas o futuras.

Sistema Causal: Responde solo a entradas presentes y pasadas, donde el grado del numerador es menor o igual al del denominador.
$$G(z)=\frac{N(z)}{D(z)}$$
Sistema No Causal: Puede responder a entradas futuras, ocurre si el sistema responde sin ninguna entrada aplicada previamente.

# 8. Tiempo Muerto en Sistemas Discretos

El tiempo muerto es un retraso temporal entre la entrada y la salida de un sistema, más fácil de identificar en sistemas discretos.

>Tiempo Muerto: Número de muestras por el cual la salida se retrasa respecto a la entrada.<br>
>Sistema Bipropio: Un sistema con tiempo muerto cero.

$$r=m−n$$
- r es el tiempo muerto, 
- m es el grado del numerador, y 
- n es el grado del denominador.

# 9. Conclusiones

La Transformada Z es esencial en el control digital, permitiendo analizar y diseñar sistemas discretos con precisión. Entender los conceptos de adelantos, atrasos, y funciones de transferencia en el dominio Z es crucial para implementar sistemas eficientes y efectivos. La causalidad y el tiempo muerto son aspectos críticos que deben considerarse en el análisis de estos sistemas.

# 10. Referencias

1. Cote, J.E. Transformada Z de adelantos y atrasos (Presentación). 2024. 
2. Barrero Mendoza, Oscar. Sistemas de control digital. Universidad de Ibagué, 2021.
3. Chen, C.-T. Analog and Digital control design. Saunders College Publishing.
<br>