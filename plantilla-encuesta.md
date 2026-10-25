# Plantilla de diseño — Encuesta de satisfacción (hito 1)

**Equipo:** 2 · **Integrantes:** Andrea Cumbal, Paula Granda, Anthony Jaramillo, Paola Pacheco · **Fecha:** 26/10/2026

**Repositorio (fork):** github.com/Anthony8719/IDSD422-lab2-diseno-encuesta.git

**Enfoque del equipo (aprobado en clase):** Enfoque Promocional

Completa cada sección. Usa commits por sección; la historia del repositorio se revisa.

> **Formato del entregable:** exporta esta plantilla completada a PDF, con el enlace de tu fork en la carátula, y guarda el PDF en `informes/` del fork. Entrega el PDF y el enlace del fork en el aula virtual.

## 1. Objetivo de la encuesta

*Analizar el nexo existente entre las promociones comerciales y la frecuencia de compras no planificadas de los consumidores de supermercados en Quito, mediante una encuesta de satisfacción, con la finalidad de proporcionar información que apoye a la gerencia de RetailAndina en el diseño y optimización de sus estrategias promocionales.*

## 2. Población objetivo

- Población: 

Personas mayores a 18 años que realizan compras con una frecuencia de al menos una vez al mes en los supermercados y que residen en Quito.
- Límites y justificación: 

La investigación se centra solamente en aquellos consumidores que sean mayores de edad y vivan en Quito, dado que son los únicos que podrían aportar datos sobre el momento en el que llevan a cabo sus hábitos de compra, así como sobre el tipo de promociones comerciales que llevarían a cabo.

A estos efectos, se considera válida una frecuencia mínima de una compra al mes. Así se incluyen, en la muestra, aquellos consumidores que tengan experiencias más o menos recientes en sus compras. Por el contrario, la delimitación de la investigación también facilita la recogida de respuestas, exigiendo solamente a los encuestados que sean familiares, amigos o conocidos (que cumplan con el criterio de consumidores de RetailAndina) que nos ayuden a llevar a cabo la investigación.

Los resultados permitirán explorar la relación entre las promociones y las compras no planificadas dentro del grupo encuestado, aunque no podrán generalizarse a todos los clientes de RetailAndina sin un muestreo probabilístico representativo.


## 3. Método de muestreo

*Elige aleatorio simple, estratificado o conveniencia y justifica. Meta: 15–30 respuestas reales (3–6 por integrante); opcional: relleno simulado hasta 60–100 filas marcadas con la columna `origen`.*

- Método:
- Tamaño y justificación:
- Cómo se seleccionarán los participantes:
- **Equivalente en código (Python o R):** la línea que implementa tu método sobre un CSV de clientes (aleatorio simple, estratificado o conveniencia) con el resultado de una corrida con semilla, y una frase sobre por qué tu método (y no la conveniencia) justifica el hito.

## 4. Cuestionario (5–10 preguntas)

*Preguntas neutras, específicas, una idea por pregunta, opciones exhaustivas y excluyentes.*

| # | Pregunta | Tipo de variable | Dtype al cargar | Opciones / escala |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| ... | | | | |

*Nota: la columna "tipo de variable" usa la clasificación del cap. 3 (numérica continua/discreta, categórica binaria/ordinal). "Dtype al cargar" es cómo crees que llegará la columna en `df.dtypes`/`str()` (`int64`, `float64`, `str`/`object` según la versión de pandas). Pista: el dtype es una pista, no la clasificación — una ordinal puede llegar como `int`.*

## 5. Análisis de sesgos

*Identifica 2 problemas potenciales de esta encuesta y su mitigación.*

| Sesgo potencial | Mitigación |
|---|---|
| 1. | |
| 2. | |

## 6. Confidencialidad (RA3)

- Datos personales que se piden y por qué:
- Plan de anonimización (qué se quita o codifica antes de compartir):

## 7. Verificación con herramientas (Python/R)

*Escribe `scripts/verificacion_encuesta.py` (o `.R`): debe cargar `plantillas/encuesta_respuestas.csv` y reportar los tipos de cada columna, los datos faltantes por columna y la distribución de `satisfaccion_general` y `recomendaria`. Incluye la salida y responde:*

- ¿Coinciden los tipos con tu predicción de la sección 4?
- ¿Cuántos datos faltantes hay por columna?

*Ejecuta el script sobre el CSV final (separa con un filtro de la columna `origen` las filas reales de las simuladas): ¿qué resultado delataría un sesgo de **no respuesta** y cuál un sesgo de **respuesta**? Escribe tu interpretación usando solo las respuestas reales.*
