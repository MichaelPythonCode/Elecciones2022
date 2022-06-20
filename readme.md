# Promedio electoral de las elecciones presidenciales colombianas de 2022

## Comenzando 🚀

El objetivo es dar una idea agregada de la situación de los distintos candidatos ante las elecciones presidenciales de Colombia de 2022.




### Pre-requisitos 📋

Tidyverse para lo básico, RStan para el modelo experimental.


### Componentes ⚙️

1a_v.R <- es el script maestro para los análisis de las encuestas en primera vuelta. Está convenientemente comentado para que resulte legible (¡espero!). Absorbe los datos de recetas-electorales.com y los transforma en los outputs necesarios. Esos outputs son en muchos casos tablas de datos que después empleo para realizar gráficos en datawrapper. Dichas tablas quedan en el directorio raíz como archivos .csv con el sufijo "dw" y constituyen el punto de salida de todo el script, que no genera ningún gráfico por sí mismo.

ponderador_lsv <- Mantiene una tabla de referencia de las puntuaciones que asignó el [Equipo ANCORT] a cada casa encuestadora para realizar la ponderación.

modelo <- aquí está el modelo experimental

### Explicación metodológica del promedio

A día de hoy, el **promedio de encuestas básico** incluye las últimas publicadas de cada casa encuestadora registrada ante el Consejo Nacional Electoral hasta el 5 de abril, desde el 14 de marzo de 2022 (el día posterior a las consultas interpartidistas que terminaron por definir las candidaturas a la presidencia. La recopilación se recoge desde la plataforma recetas-electorales.com, y se contrasta con la publicación en diversos medios. También recoge una evolución del promedio.

Cada encuesta tiene un peso ligeramente distinto en el promedio que depende de la valoración numérica realizada por el Semáforo de Encuestadoras ANCORT, que valora a cada una de las casas de encuestas de acuerdo con una serie de parámetros técnicos, metodológicos y de acierto en el resultado final. Para evitar sesgar en exceso el promedio, el peso asignado solo varía en un 20%, de manera que la encuesta de la encuestadora mejor valorada recibe un 100% y la peor valorada recibe un 80% de peso sobre el promedio final. Cuando una encuestadora sí está registrada ante el CNE pero no está valorada por ANCORT, el promedio le asigna un punto intermedio entre ambos extremos.

En la última ronda de encuestas (desde el 1 de mayo de 2022) algunas casas han decidido eliminar a los indecisos de la base de cálculo. Para normalizar todos los promedios se ha procedido a eliminar los indecisos de su base de cálculo sin especificar cuántos son. Para poder ponderar y comparar todas las encuestas es necesario eliminar estos indecisos en todos los casos en que se incluyan. Por ejemplo, si en una encuesta los indecisos son 20,6%, tras restarle ese 5,6% de la categoría anterior queda un 15% de indecisos. Si en esa encuesta un candidato X tiene un 50% del voto, el voto normalizado se podría conseguir mediante la fórmula 

50/(100-15)=50/85=58,8%

Después se obtiene el promedio ponderado.

## Modelo experimental

A partir del trabajo de ANCORT para definir un modelo de pronóstico electoral bayesiano con RStan DESARROLLADORES INC, construyo un modelo idéntico pero alimentado con mi promedio normalizado. Está en la carpeta /modelo.


## Autores ✒️

**Michael C.** - *Responsable del repo*

Pero este proyecto habría sido imposible sin el trabajo del Equipo ANCORT, encabezado por Rafael Unda; y sin el juicioso recopilado que realiza DESARROLLADORES INC habría sido sin duda mucho más costoso.

## Licencia 📄

Licencia libre, úsalo como consideres: ATT: Michael Cardona :)
