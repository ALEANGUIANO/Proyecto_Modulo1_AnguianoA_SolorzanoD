# **Optimización de la Mezcla de Concreto para Máxima Resistencia y Menor Costo**
---

# **Definición de la función a optimizar**
El objetivo es minimizar el costo de los materiales de la mezcla de concreto, asegurando que la resistencia a la compresión sea igual o mayor a un valor objetivo.

Nuestra función objetivo será:

**Costo total = Cc x Volumen de cemento + Cs x Volumen de escoria + Ca x Volumen de ceniza + Cw x Volumen de agua + Cp x Volumen de superplastificante + Cg x Volumen de agregado grueso + Cf x Volumen de agregado fino**

Donde:

Cc, Cs, Ca, Cw, Cp, Cg, Cf son los costos unitarios de cada material, expresados en $/m³.
Las variables representan el volumen de cada material en m³.
---
### 📌 Restricciones
Se debe cumplir con una resistencia a la compresión mínima (𝑅min), basada en la relación entre los materiales y la resistencia real del dataset.
Podemos ajustar esto con un modelo de regresión para predecir la resistencia en función de los materiales.

Suma de proporciones de materiales:
La mezcla debe cumplir con una cantidad total de materiales adecuada para formar concreto.

Límites en cada material:
No se pueden usar cantidades excesivas o insuficientes de un material, respetando rangos típicos de diseño

### 📌 Deducción y explicación de las ecuaciones
Usaremos un modelo de regresión basado en el dataset para obtener la ecuación que predice la resistencia:

𝑅 = 𝑓 (cemento, escoria, ceniza, agua, superplastificante, agregado grueso, agregado fino)
Con esta ecuación, podemos agregar la restricción:

𝑓 (cemento, escoria, ceniza, agua, superplastificante, agregado grueso, agregado fino) ≥ 𝑅 min
⁡ 
El modelo de optimización buscará minimizar el costo respetando esta restricción.

### 📌 Definición de Parámetros
Cc, Cs, Ca, Cw, Cp, Cg, Cf  Costo unitario de los materiales (se puede definir con datos del mercado).
𝑅min : Resistencia mínima deseada en MPa
⁡
cemento, escoria, ceniza, agua, superplastificante, agregado grueso, agregado fino

Variables de decisión (cantidades de cada material en kg/m³).

--- 

## 📌 **Descripción del Dataset**
### 🔍 Contexto y Origen
Este dataset proviene de estudios sobre la resistencia del concreto en función de su composición. Se ha utilizado en múltiples investigaciones sobre el diseño óptimo de mezclas para mejorar la resistencia del material. La resistencia a la compresión es una de las propiedades más importantes del concreto, y su predicción permite optimizar su diseño, reduciendo costos y mejorando su desempeño estructural.

Este conjunto de datos se ha utilizado en modelos de machine learning y en análisis de optimización para encontrar mezclas más eficientes.
| Variable        | Descripción | Unidades |
|----------------|------------|----------|
| **cement**     | Cantidad de cemento en la mezcla | kg/m³ |
| **slag**       | Cantidad de escoria granulada de alto horno | kg/m³ |
| **ash**        | Cantidad de ceniza volante utilizada | kg/m³ |
| **water**      | Cantidad de agua en la mezcla | kg/m³ |
| **superplastic** | Dosis de superplastificante | kg/m³ |
| **coarseagg**  | Cantidad de agregado grueso | kg/m³ |
| **fineagg**    | Cantidad de agregado fino | kg/m³ |
| **age**        | Edad del concreto al momento de la prueba | días |
| **strength**   | Resistencia a la compresión | MPa |

---

## 📚 **Metodología**
**Modelo de Optimización**: Para la optimización, el objetivo es minimizar el costo total de la mezcla de concreto mientras se cumplen las restricciones de resistencia.

Esto, considerando los datos con los que se cuente en obra (por ponerlo en contexto real), para que en base a eso se calcule la mezcla óptima de tus materiales. Estos materiales los puedes modificar declarandolos en el **"punto_inicial ="** en el siguiente orden:
- Cemento
- Escoria/grava
- Ceniza/Arena
- Agua
- Superplastificante
- Agregados gruesos
- Agregados finos
  
**Modelo de Regresión**: Se emplea un modelo de regresión basado en los datos del conjunto para predecir la resistencia a la compresión en función de la cantidad de materiales. Esta predicción es clave para ajustar las restricciones de resistencia.

Se han empleado limitantes según las sigueintes normativas para asegurar que cuentas con los materiales necesarios para la correcta ejecución de tu mezcla:
- ACI 318 (American Concrete Institute)
- NMX-C-155 (Norma mexicana para diseño de concreto)
- NTC Construcción de la CDMX

De no contar con los materiales necesarios o no cumplir con alguno de los parametros indicados por la norma, aparecerá el siguiente mensaje: 

**"❌ No se logró encontrar una solución óptima."**















