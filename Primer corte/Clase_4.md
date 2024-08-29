<h1 align="center"> Estabilidad en Sistemas Discretos </h1>

La estabilidad de los sistemas discretos, garantiza que un sistema responda de manera predecible y controlada ante entradas limitadas. Esta presentación explora diferentes criterios y métodos para evaluar la estabilidad de sistemas discretos, incluyendo la ubicación de polos en el plano Z, la estabilidad asintótica, la estabilidad BIBO, y el criterio de Jury.

# 1. Estabilidad Absoluta

La estabilidad absoluta de un sistema se refiere a su capacidad para producir una salida limitada en respuesta a una entrada limitada. Si un sistema responde de manera estable a una entrada paso, se considera absolutamente estable.

Ecuaciones: La estabilidad se evalúa observando la respuesta del sistema a una entrada paso:
$$\lim_{t \to \infty} y(t) = k$$

# 2. Espacio LaPlace vs Espacio Z

El análisis de estabilidad en el espacio Z es diferente al realizado en el espacio de LaPlace. Mientras que en el dominio de LaPlace la estabilidad se determina por la ubicación de los polos en relación con el eje imaginario, en el dominio Z la estabilidad se evalúa según la posición de los polos dentro o fuera del círculo unitario.<br>
>Espacio Z: Dominio de análisis para sistemas discretos, donde la estabilidad se evalúa en función de la ubicación de polos dentro del círculo unitario.<br>
>Círculo Unitario: En el plano Z, un círculo con radio 1, dentro del cual deben ubicarse todos los polos para que el sistema sea estable.

cuaciones: La relación entre los polos en el espacio de LaPlace y el espacio Z se expresa como:

$$𝑧=e^{𝑇𝑠}$$
donde $s=σ+jω$ y 𝑇 es el periodo de muestreo.

| Espacio LaPlace | Espacio Z                                 |
|----------------|------------------------------------------|
| Eje imaginario  | Círculo unitario                          |
| σ < 0: Estable  | Polos dentro del círculo unitario: Estable |
| σ = 0: Marginalmente estable | Polos en el borde del círculo unitario: Marginalmente estable |
| σ > 0: Inestable | Polos fuera del círculo unitario: Inestable |

# 3. Estabilidad por Ubicación de Polos

La ubicación de los polos en el plano Z determina la estabilidad de un sistema. Si todos los polos están dentro del círculo unitario, el sistema es estable. Si uno o más polos están fuera del círculo unitario, el sistema es inestable.

# 4. Estabilidad Asintótica


<br>