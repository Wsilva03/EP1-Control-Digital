```markdown
# Apuntes: Análisis de Polinomios y Controladores

## 1. Localización de Polos y Multiplicación de Polinomios

### Concepto:
Los polos del sistema se ubican en un espacio dado y se combinan algebraicamente mediante multiplicación para formar un polinomio característico que describe la dinámica del sistema.

### Pasos:
1. Identificar los polos individuales.
2. Multiplicar las expresiones correspondientes para generar el polinomio completo.
3. Simplificar el polinomio eliminando términos complejos o redundantes.

### Ejemplo 1 Resuelto:
**Polos:**  
$-1$, $Z+2$, $Z+100$.  

**Desarrollo:**  
1. Multiplicamos los dos primeros polos:  
   $$   (Z+2)(Z+100) = Z^2 + 102Z + 200$$
2. Combinamos con el tercer polo:  
   $$   (Z^2 + 102Z + 200)(Z+1) = Z^3 + 103Z^2 + 302Z + 200$$

### Ejemplo 2 Resuelto:
**Polos:**  
$Z+2.73j$, $Z-2.73j$.  

**Desarrollo:**  
1. Aplicamos la fórmula del producto de binomios conjugados:  
   $$   (Z+2.73j)(Z-2.73j) = Z^2 - (2.73)^2 = Z^2 - 7.45$$

---

## 2. Diseño de Controladores en Lazo Cerrado

### Concepto:
El controlador en lazo cerrado se diseña usando la fórmula:
$$C(Z) = \frac{\text{Modelo deseado en lazo cerrado}}{\text{Modelo en lazo abierto}} \cdot \left( 1 - \text{Modelo deseado en lazo cerrado} \right)
\]

### Pasos:
1. Determinar el polinomio característico del sistema en lazo cerrado.
2. Calcular los términos numeradores y denominadores aplicando la fórmula.
3. Simplificar y organizar los resultados para obtener el controlador.

### Ejemplo 1 Resuelto:
**Dado:**  
- Polinomio en lazo abierto: $Z^2 + 2Z + 1$  
- Polinomio en lazo cerrado: $Z^3 + 4Z^2 + 6Z + 4$  

**Desarrollo:**  
1. Sustituimos en la fórmula:  
   $$   C(Z) = \frac{Z^3 + 4Z^2 + 6Z + 4}{(Z^2 + 2Z + 1)(1 - (Z^3 + 4Z^2 + 6Z + 4))}$$
2. Simplificamos:
   $$   C(Z) = \frac{Z^3 + 4Z^2 + 6Z + 4}{Z^5 + 6Z^4 + 12Z^3 + \dots}$$

### Ejemplo 2 Resuelto:
**Dado:**  
- Polinomio en lazo abierto: $Z^2 + 5Z + 6$  
- Polinomio en lazo cerrado: $Z+1$  

**Desarrollo:**  
1. Sustituimos en la fórmula:  
   $$   C(Z) = \frac{Z+1}{(Z^2 + 5Z + 6)(1 - (Z+1))}$$
2. Simplificamos:  
   $$   C(Z) = \frac{Z^2 + 5Z + 5}{Z+1}$$

---

## 3. Análisis de Márgenes de Fase y Ganancia

### Concepto:
- **Margen de fase**: Se evalúa en el punto donde la ganancia cruza $0 \, \text{dB}$.  
- **Margen de ganancia**: Se evalúa en el punto donde la fase cruza $-180^\circ$.  

**Criterio de estabilidad:** Ambos márgenes deben ser positivos para garantizar estabilidad en el lazo cerrado.

### Ejemplo 1 Resuelto:
**Datos del diagrama de Bode:**  
- Cruce de ganancia: $\phi = -150^\circ$.  
- Cruce de fase: $G = -5 \, \text{dB}$.  

**Cálculos:**  
1. **Margen de fase:**  
   $$   -150^\circ - (-180^\circ) = 30^\circ$$
2. **Margen de ganancia:**  
   $$   0 \, \text{dB} - (-5 \, \text{dB}) = 5 \, \text{dB}$$

### Ejemplo 2 Resuelto:
**Datos del diagrama de Bode:**  
- Cruce de ganancia: $\phi = -170^\circ$.  
- Cruce de fase: $G = -2 \, \text{dB}$.  

**Cálculos:**  
1. **Margen de fase:**  
   $$   -170^\circ - (-180^\circ) = 10^\circ$$
2. **Margen de ganancia:**  
   $$   0 \, \text{dB} - (-2 \, \text{dB}) = 2 \, \text{dB}$$

---
