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
Un sistema es asintóticamente estable si su respuesta ante cualquier conjunto de condiciones iniciales tiende a cero cuando 𝑘 tiende a infinito.

La estabilidad asintótica se expresa matemáticamente como:
$$\lim_{t \to \infty} y(k)=0$$

5. Estabilidad BIBO

La estabilidad BIBO (Bounded Input, Bounded Output) se refiere a la propiedad de un sistema de producir una salida acotada para cualquier entrada acotada.
La condición BIBO se expresa como:

$$∣y(k)∣ ≤ M para ∣u(k)∣ ≤ N$$

donde M y N son valores máximos finitos.

# 6. Criterio de Jury

El criterio de Jury es un método algebraico que se utiliza para verificar la estabilidad de un sistema en el espacio Z. Involucra evaluar el polinomio característico del sistema y construir una tabla para aplicar varias condiciones de estabilidad.

Ecuaciones: Dado un polinomio característico en Z:

$$D(z) = a_0 z^n + a_1 z^{n-1} + ... + a_{n-1}z + a_n$$

Condiciones de estabilidad:
* a_0 > 0
* |P(z=1)| > 0
* |P(z=-1)| > 0

### Ejemplo:

Consideremos el siguiente polinomio característico:

$$D(z) = z^3 - 1.5z^2 + 0.8z - 0.2$$

Verificación de las condiciones iniciales:

- a0 = 1 > 0 **(cumple)**
- |P(z=1)| = |1 - 1.5 + 0.8 - 0.2| = 0.1 > 0 **(cumple)**
- |P(z=-1)| = |-1 - 1.5 - 0.8 - 0.2| = 3.5 > 0 **(cumple)**

Ahora, procedemos a construir el arreglo de Jury.

Paso 1: Escribir el polinomio característico en el arreglo de Jury
El polinomio se puede escribir como:

$$D(z)=[1,−1.5,0.8,−0.2]$$

Paso 2: Primera fila del arreglo de Jury

$$(\frac { (1​) (−1.5) (0.8) (​−0.2)} {(−0.2) (0.8)​ (−1.5) (1)}​)$$

Paso 3: Segunda fila del arreglo de Jury

El cálculo de los términos para la segunda fila se realiza de la siguiente manera:

$$b0 =−0.2⋅1−(−0.2)⋅(−0.2)=−0.2+0.04=−0.16$$
$$b1 =−0.2⋅(−1.5)−0.8⋅(−0.2)=0.3+0.16=0.46$$
$$b2 =−0.2⋅0.8−(−1.5)⋅(−0.2)=−0.16−0.3=−0.46$$

La segunda fila del arreglo es:

( −0.16 0.46 −0.46)

Paso 4: Tercera fila del arreglo de Jury

Utilizamos los valores calculados en la segunda fila:

$$c0 =−0.16⋅(−0.16)−0.46⋅(−0.46)=0.0256+0.2116=0.2372$$

La tercera fila es:

( 0.2372 )

Paso 5: Verificación de las condiciones de estabilidad

Las condiciones de estabilidad que deben cumplir los elementos en el arreglo de Jury son:

1.  |b₀| < |bₙ₋₁|
2.  |c₀| < |b₁|

**Verificación**

* **|b₀| < |bₙ₋₁|**
    * |b₀| = |-0.16| = 0.16
    * |bₙ₋₁| = |0.46| = 0.46
  
   Como 0.16 < 0.46, se cumple esta condición.

* **|c₀| < |b₁|**
    * |c₀| = |0.2372| = 0.2372
    * |b₁| = |0.46| = 0.46
  
   Como 0.2372 < 0.46, se cumple esta condición.

**Conclusión**: Dado que todas las condiciones del test de Jury se cumplen, se concluye que **el sistema es estable**.

# 7. Conclusiones

La estabilidad de sistemas discretos es un concepto central en el control digital. Los métodos de ubicación de polos, estabilidad asintótica, estabilidad BIBO y el criterio de Jury son herramientas esenciales para garantizar que un sistema funcione de manera predecible y controlada. La comprensión y correcta aplicación de estos métodos son fundamentales para el diseño de sistemas de control robustos.

8. Referencias

- Cote, J.E. Estabilidad en Sistemas Discretos (Presentación). 2024.
- Visioli, A. Digital Control Engineering. 2nd Edition. Elsevier, 2013.
- Barrero Mendoza, Oscar. Sistemas de control digital. Universidad de Ibagué, 2021.


<br>