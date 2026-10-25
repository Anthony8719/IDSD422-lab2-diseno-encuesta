# Plantilla de diseño — Encuesta de satisfacción (hito 1)

**Equipo:** 2 · **Integrantes:** Andrea Cumbal, Paula Granda, Anthony Jaramillo, Paola Pacheco · **Fecha:** 26/10/2026

**Repositorio (fork):** github.com/Anthony8719/IDSD422-lab2-diseno-encuesta.git

**Enfoque del equipo (aprobado en clase):** Enfoque Promocional



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

- **Método:** *Se plantea prevenir la utilización de un muestreo no probabilístico por conveniencia, es decir, se tomarán como participantes aquellos individuos que cumplan con los criterios de la población objetivo y que por tanto puedan ser abordados por los miembros del equipo. Este método será el que permita obtener información sobre la percepción y las promociones comerciales teniendo en cuenta la frecuencia de realizar compras no planificadas y las limitaciones de tiempo y de recursos que poseen el laboratorio.*

- **Tamaño y justificación:** *Se establece como objetivo obtener 20 respuestas a partir de personas que sean consumidores de 18 años o más, residentes en Quito, que realicen compras en un supermercado al menos una vez al mes. Esta cantidad está dentro de las 15-30 respuestas que se solicitan para la práctica y permitirá llevar a cabo un análisis descriptivo exploratorio de las variables bajo estudio. Debido al tamaño y a la forma no probabilística de la muestra, el resultado no puede ser generalizable a toda la población de consumidores de Quito.*

- **Cómo se seleccionarán los participantes:** *Las personas que tengamos en el equipo de investigación contactarán a familiares, amigos/compañeros de trabajo, conocidos, etcétera (cualquier persona en el cuerpo o grupo de individuos que se considere que cumplen las condiciones citadas) a través de medios digitales o mediante contacto personal. Antes de aplicar la encuesta se comprobará que los participantes cumplen con las condiciones sujetas a la edad/hábitos de residencia y la frecuencia mínima de compra, conforme se había comentado en el apartado 2. La participación será voluntaria y se intentará incluir consumidores con hábitos de compra diferentes para que haya mayor variabilidad en las respuestas. Cada consumidor responderá una única vez.*

- **Equivalente en código (Python o R):** *Se utilizará Python con la biblioteca pandas para filtrar un archivo CSV de posibles participantes según los criterios de inclusión. Posteriormente, se organizará una lista de hasta 20 personas accesibles para el equipo. El uso de una semilla permitirá reproducir el orden generado, pero no convertirá el procedimiento en un muestreo probabilístico, puesto que los participantes provendrán de contactos disponibles y su participación dependerá de su aceptación.*

```bash


import pandas as pd

# Archivo de posibles participantes
df = pd.read_csv("clientes.csv")

# Verificar los criterios de inclusión
elegibles = df[
    (df["edad"] >= 18) &
    (df["ciudad"].str.strip().str.lower() == "quito") &
    (df["compras_mes"] >= 1)
]

# Organizar hasta 20 contactos elegibles y accesibles
# La semilla hace reproducible el orden
muestra = elegibles.sample(
    n=min(20, len(elegibles)),
    random_state=42
)

print("Participantes elegibles:", len(elegibles))
print("Contactos seleccionados:", len(muestra))
print(muestra)


```

- **Justificación del método:** *El muestreo por conveniencia se ha elegido en vez del aleatorio simple o el estratificado, en vista que el equipo no disponga de un marco muestral completo de los consumidores de los supermercados de Quito. Es cierto que, dadas las condiciones adecuadas, los métodos probabilísticos posibilitarán llevar a cabo inferencias estadísticas; sin embargo, ello exigiría la elaboración de una lista de la población, además de procedimientos de selección de la misma con probabilidades conocidas. Así pues, dado los propósitos exploratorios del laboratorio, la conveniencia se muestra más útil pues posibilitará captar tendencias preliminares que puedan dar cuenta de las estrategias promocionales de RetailAndina.*

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
