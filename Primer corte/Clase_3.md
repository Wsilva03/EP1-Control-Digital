<h1 align="center"> Discretización de Controladores </h1>

La discretización permite que los controladores diseñados en el dominio continuo (tiempo continuo) se implementen en sistemas digitales, como microcontroladores o procesadores digitales de señales. El proceso de discretización implica convertir las funciones de transferencia de controladores continuos en sus equivalentes discretos utilizando diversas técnicas.

# 1. Discretización de Señales Analógicas

La discretización de señales analógicas es el proceso de convertir señales continuas en secuencias discretas, permitiendo su manipulación en sistemas digitales.

- Ecuaciones: La discretización de una señal $x(t)$ en el dominio Z se realiza mediante la transformada Z, que se representa como:

$$X(z) = \sum_{k=0}^{\infty}x(kT)z^{-k}$$


# 2. Método de Invarianza al Impulso

El método de invarianza al impulso se utiliza para convertir un controlador continuo en uno discreto, manteniendo la respuesta al impulso del sistema original.

Ecuaciones: La ecuación que relaciona la función de transferencia continua C(s) con su equivalente discreta C(z) es:

$$C(z) = \mathcal{Z}\{C(s)\}|_{s=\frac{2}{T}\left(z-1\right)}$$

Ejemplo: Considerando $C(s) = \frac{5}{s+2}$, su equivalente discreto utilizando invarianza al impulso será:

$$C(z) = \mathcal{Z}\left\{\frac{5}{s+2}\right\}|_{s=\frac{2}{T}\left(z-1\right)}$$

# 3. Método de Invarianza al Paso

Este método se basa en la correspondencia de la respuesta al escalón (o paso) de un sistema continuo con su equivalente discreto.

>Invarianza al Paso: Técnica que asegura que la respuesta al escalón de un sistema discretizado coincida con la de su equivalente continuo.

Ecuaciones: La relación entre C(s) y C(z) usando invarianza al paso se da por:

$$C(z) = \frac{z-1}{z} \mathcal{Z}\left\{\frac{C(s)}{s}\right\}$$

Ejemplo: Dado $C(s) = \frac{2s-2}{(s+1)(s+3)}$, aplicando invarianza al paso:

$$C(z) = \frac{z-1}{z} \mathcal{Z}\left\{\frac{2s-2}{s(s+1)(s+3)}\right\}$$

# 4. Método de Euler Adelante

El método de Euler hacia adelante es una aproximación para discretizar sistemas continuos, utilizando una derivada hacia adelante.

Ecuaciones: La discretización de un controlador continuo usando Euler hacia adelante se expresa como:

$$\frac{d}{dt}x(t) \approx \frac{x(k+1) - x(k)}{T}$$

La relación con la Transformada Z es:

$$s \approx \frac{z-1}{T}$$

Ejemplo: Si $C(s) = \frac{1}{s+2}$, usando Euler hacia adelante:

$$C(z) = \frac{1}{\frac{z-1}{T} + 2} = \frac{T}{(z-1) + 2T}$$

# 5. Método de Euler Atrás

El método de Euler hacia atrás es otra aproximación para discretizar sistemas, utilizando una derivada hacia atrás.

Ecuaciones: La derivada se aproxima como:

$$\frac{d}{dt}x(t) \approx \frac{x(k) - x(k-1)}{T}$$

La relación con la Transformada Z es:

$$s \approx \frac{1 - z^{-1}}{T}$$

Ejemplo: Para $C(s) = \frac{3}{s+5}$, usando Euler hacia atrás:

$$C(z) = \frac{3}{\frac{1-z^{-1}}{T} + 5} = \frac{3T}{1 - z^{-1} + 5T}$$

# 6. Método Trapezoidal ("Tustin")

El método trapezoidal es una técnica de discretización que promedia las aproximaciones hacia adelante y hacia atrás de la derivada.

Ecuaciones: La aproximación trapezoidal de la derivada es:

$$s \approx \frac{2}{T} \cdot \frac{z-1}{z+1}$$

Ejemplo: Para $C(s) = \frac{4}{s+3}$, utilizando Tustin:

$$C(z) = \frac{4 \left( \frac{2}{T} \cdot \frac{z-1}{z+1} \right)}{\frac{2}{T} \cdot \frac{z-1}{z+1} + 3}$$

# 7. Teorema de Muestreo de Nyquist

El teorema de muestreo de Nyquist establece la relación entre la frecuencia de muestreo y la frecuencia máxima de la señal para evitar el aliasing.

Ecuaciones: La aproximación trapezoidal de la derivada es:

$$s \approx \frac{2}{T} \cdot \frac{z-1}{z+1}$$

Ejemplo: Para $C(s) = \frac{4}{s+3}$, utilizando Tustin:

$$C(z) = \frac{4 \left( \frac{2}{T} \cdot \frac{z-1}{z+1} \right)}{\frac{2}{T} \cdot \frac{z-1}{z+1} + 3}$$

# 8. Aliasing

 El aliasing es un fenómeno que ocurre cuando la frecuencia de muestreo es insuficiente para capturar correctamente la señal, resultando en la superposición de frecuencias.

Estrategias de Mitigación:

- Aumentar la frecuencia de muestreo.
- Aplicar un filtro pasa-bajos antes del muestreo.

# 9. Conclusiones

La discretización de controladores es un proceso esencial para implementar controladores analógicos en sistemas digitales. Cada método de discretización tiene sus propias ventajas y limitaciones, por lo que la selección del método adecuado depende del contexto específico del sistema. La comprensión y aplicación correcta de estos métodos aseguran un rendimiento óptimo del sistema controlado en tiempo discreto.

# 10. Referencias

1. Cote, J.E. Transformada Z de adelantos y atrasos (Presentación). 2024. 
2. Ramos, G. Material curso Control Digital. Universidad Nacional de Colombia, 2015.
3. Barrero Mendoza, Oscar. Sistemas de control digital. Universidad de Ibagué, 2021.

<br>