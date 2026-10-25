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


## 3. Diseño de preguntas de la encuesta

| N.º | Pregunta | Tipo de variable | Dtype esperado en pandas | Opciones / escala |
|---|---|---|---|---|
| 1 | ¿En cuál de los siguientes rangos se encuentra su edad? | Categórica ordinal | category | 18–24; 25–34; 35–44; 45–54; 55 años o más |
| 2 | Durante los últimos 30 días, ¿cuántas veces realizó compras en supermercados? | Numérica discreta | Int64 | Número entero de 0 a 60 |
| 3 | Durante su compra más reciente en un supermercado, ¿observó promociones o descuentos en algún producto? | Categórica binaria | category | Sí; No |
| 4 | En su compra más reciente, ¿adquirió algún producto que estuviera en promoción o tuviera descuento? | Categórica binaria | category | Sí; No |
| 5 | En su compra más reciente, ¿compró algún producto que no tenía previsto adquirir debido a una promoción o descuento? | Categórica binaria | category | Sí; No |
| 6 | Durante los últimos 30 días, ¿en cuántas de sus compras adquirió productos que no tenía planificado comprar debido a promociones? | Numérica discreta | Int64 | Número entero entre 0 y el valor indicado en P2 |
| 7 | ¿Qué tan importantes son las promociones y descuentos al momento de elegir un supermercado? | Categórica ordinal | category | 1 = Nada importantes; 2 = Poco importantes; 3 = Moderadamente importantes; 4 = Importantes; 5 = Muy importantes |
| 8 | ¿Qué tan satisfecho/a se encuentra con las promociones y descuentos ofrecidos por el supermercado donde realizó su compra más reciente? | Categórica ordinal | category | 1 = Muy insatisfecho/a; 2 = Insatisfecho/a; 3 = Ni satisfecho/a ni insatisfecho/a; 4 = Satisfecho/a; 5 = Muy satisfecho/a |
| 9 | Considerando su experiencia de compra más reciente, ¿recomendaría ese supermercado a familiares o amigos? | Categórica binaria | category | Sí; No |
| 10 | En su compra más reciente, ¿cuánto dinero gastó aproximadamente en productos que no tenía previsto comprar, pero adquirió debido a promociones o descuentos? | Numérica continua | float64 | Valor en USD mayor o igual a 0; 0 si no realizó compras no planificadas; puede omitir si no recuerda |



## 5. Análisis de sesgos

Se identifican dos posibles sesgos que podrían afectar la calidad y confiabilidad de los resultados de la encuesta.

| Sesgo potencial | Mitigación |
|---|---|
| **1. Sesgo de selección:** Al utilizar un muestreo no probabilístico por conveniencia, los participantes serán principalmente familiares, amigos y conocidos de los integrantes del equipo. Esto puede ocasionar que las respuestas correspondan a consumidores con características o hábitos de compra similares, limitando la diversidad de opiniones y la representatividad de los resultados. | Se procurará incluir personas de diferentes rangos de edad y con distintas frecuencias de compra, siempre que cumplan con los criterios establecidos. Además, se evitará concentrar las encuestas en un solo grupo de conocidos y se reconocerá que los resultados representan únicamente a los participantes encuestados. |
| **2. Sesgo de respuesta:** Los participantes podrían proporcionar respuestas que consideran socialmente aceptables en lugar de reflejar sus verdaderos hábitos de compra. Por ejemplo, podrían minimizar la cantidad de productos que compran impulsivamente debido a las promociones para demostrar un mayor control sobre sus gastos. | Se utilizarán preguntas claras y neutrales, evitando expresiones que puedan influir en las respuestas. Además, se garantizará el anonimato de los participantes y se explicará que no existen respuestas correctas o incorrectas, con el fin de fomentar respuestas sinceras. |

## 6. Confidencialidad (RA3)

- **Datos personales que se piden y por qué:**

La encuesta recopilará únicamente la información necesaria para cumplir con los objetivos de la investigación. Se solicitará el rango de edad para analizar posibles diferencias en los hábitos de compra entre grupos etarios. También se verificará que los participantes residan en Quito y realicen compras en supermercados al menos una vez al mes, ya que estos son los criterios establecidos para formar parte de la población objetivo.

Adicionalmente, se recogerá información sobre la frecuencia de compra, la influencia de las promociones, el gasto aproximado en productos no planificados y el nivel de satisfacción. Estos datos permitirán analizar la relación entre las promociones comerciales y las decisiones de compra de los consumidores.

No se solicitarán nombres completos, números de cédula, direcciones domiciliarias, números telefónicos ni correos electrónicos, debido a que esta información no es necesaria para el análisis.

- **Plan de anonimización (qué se quita o codifica antes de compartir):**

Para proteger la privacidad de los participantes, cada respuesta será identificada mediante un código único, por ejemplo, E001, E002 y E003, sin asociarlo con la identidad de la persona encuestada.

La edad se registrará mediante rangos en lugar de valores exactos y la residencia se utilizará únicamente para verificar que el participante viva en Quito. Antes de compartir el archivo CSV, se eliminará cualquier información que permita identificar directamente a una persona, en caso de haberse recopilado durante el contacto inicial.

Los datos se utilizarán exclusivamente con fines académicos y se compartirán únicamente en formato anonimizado. Asimismo, se informará a los participantes sobre el objetivo de la investigación, el carácter voluntario de su participación y el uso que se dará a sus respuestas.

De esta manera, se busca garantizar la confidencialidad de la información recopilada y respetar la privacidad de los participantes durante el desarrollo de la investigación.
  

## 7. Verificación con herramientas (Python/R)

*Escribe `scripts/verificacion_encuesta.py` (o `.R`): debe cargar `plantillas/encuesta_respuestas.csv` y reportar los tipos de cada columna, los datos faltantes por columna y la distribución de `satisfaccion_general` y `recomendaria`. Incluye la salida y responde:*

- ¿Coinciden los tipos con tu predicción de la sección 4?
- ¿Cuántos datos faltantes hay por columna?

*Ejecuta el script sobre el CSV final (separa con un filtro de la columna `origen` las filas reales de las simuladas): ¿qué resultado delataría un sesgo de **no respuesta** y cuál un sesgo de **respuesta**? Escribe tu interpretación usando solo las respuestas reales.*
