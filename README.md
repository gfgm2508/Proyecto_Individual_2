 <h1 align='center'>
 <b>PROYECTO INDIVIDUAL Nº2</b>
</h1>
 
# <h1 align="center">**`Siniestros viales`**</h1>

<p>

## **Descripción del problema**

Los siniestros viales, también conocidos como accidentes de tráfico o accidentes de tránsito, son eventos que involucran vehículos en las vías públicas y que pueden tener diversas causas, como colisiones entre automóviles, motocicletas, bicicletas o peatones, atropellos, choques con objetos fijos o caídas de vehículos. Estos incidentes pueden tener consecuencias que van desde daños materiales hasta lesiones graves o fatales para los involucrados.

En el contexto de una ciudad como Buenos Aires, los siniestros viales pueden ser una preocupación importante debido al alto volumen de tráfico y la densidad poblacional. Estos incidentes pueden tener un impacto significativo en la seguridad de los residentes y visitantes de la ciudad, así como en la infraestructura vial y los servicios de emergencia.

Las tasas de mortalidad relacionadas con siniestros viales suelen ser un indicador crítico de la seguridad vial en una región. Estas tasas se calculan, generalmente, como el número de muertes por cada cierto número de habitantes o por cada cierta cantidad de vehículos registrados. Reducir estas tasas es un objetivo clave para mejorar la seguridad vial y proteger la vida de las personas en la ciudad.

Es importante destacar que la prevención de siniestros viales involucra medidas como la educación vial, el cumplimiento de las normas de tráfico, la infraestructura segura de carreteras y calles, así como la promoción de vehículos más seguros. El seguimiento de las estadísticas y la implementación de políticas efectivas son esenciales para abordar este problema de manera adecuada.

### **Contexto**

En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales. Aunque muchas jurisdicciones han logrado disminuir la cantidad de accidentes de tránsito, esta sigue siendo la principal causa de muertes violentas en el país.
Los informes del Sistema Nacional de Información Criminal (SNIC), del Ministerio de Seguridad de la Nación, revelan que entre 2018 y 2022 se registraron 19.630 muertes en siniestros viales en todo el país. Estas cifras equivalen a 11 personas por día que resultaron víctimas fatales por accidentes de tránsito.

Solo en 2022, se contabilizaron 3.828 muertes fatales en este tipo de hechos. Los expertos en la materia indican que en Argentina es dos o tres veces más alta la probabilidad de que una persona muera en un siniestro vial que en un hecho de inseguridad delictiva.

### **Rol a desarrollar**

El `Observatorio de Movilidad y Seguridad Vial` (OMSV), centro de estudios que se encuentra bajo la órbita de la ***Secretaría de Transporte*** del Gobierno de la Ciudad Autónoma de Buenos Aires, CABA, me ha solicitado la elaboración de un proyecto de análisis de datos, con el fin de generar información que le permita a las autoridades locales tomar medidas para disminuir la cantidad de víctimas fatales de los siniestros viales.
Para ello, disponibiliza un dataset sobre homicidios en siniestros viales acaecidos en la Ciudad de Buenos Aires durante el periodo 2016-2021. Este dataset se encuentra en formato *xlsx* y contiene dos hojas llamadas: **hechos** y **víctimas**. Asimismo, incluye otras dos hojas adicionales de diccionarios de datos, que sirve de guía para un mayor entendimiento de la data compartida.

## **Propuesta de trabajo**

Acorde al requerimiento recibido, los productos a entregar son los siguientes:

- 'ETL' (Extract, Transfrom and Load) de la data recibida para llegar a una base de datos limpia y completa que permita realizar todo el análisis requerido.

- `EDA` (Exploratory Data Analysis) de la data, con el propósito de caracterizar a la población víctima y permita identificar patrones de conducta o de espacio/tiempo o de uso del servicio de transporte que, a su vez, sean herramientas importantes para la autoridad competente y puedan definir políticas y/o acciones que logren reducir año a año los accidentes de tránsito y, por ende, las muertes en ellos.

- `Dashboard` interactivo que permita explorar detalladamente los datos, que sea de fácil interpretación tanto su lectura como los análisis extraídos de los mismos y oriente a los interesados en las acciones a implementar para redudcr los casos en estudio.

- `KPIs`, a saber:

    - *Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior*
 
    - *Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior*

- `Repositorio de GitHub`, por último, se entrega todo en un repositorio de github, debidamente documentado.

## Fuente de datos
- [Buenos Aires Data](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales): deberán utilizar el dataset denominado `Homicidios`

## **ETL**

Se recibe del OMSV una data en un archivo en excel de título: homicidios.xlsx, que contiene dos hojas con datos, una HECHOS con datos de los diversos accidentes de tránsito fatales registrados en CABA entre 2016 y 2021, con 697 registros, y VICtIMAS con el detalle de las víctimas en los mismos, 717 registros.

Lo primero que se hizo fue transformar las dos hojas de datos en dataframe de python: df_victimas y df_hechos. A ambas DF se les eliminaron duplicados y columnas innecesarias para el análisis. 

Al df_victimas se le realizóp un análisis descriptivo para detectar valores atípicos, encontrando que el campo edad tenía 53 registros sin dato de edad, por lo que se decidió eliminar dichos registros y posteriormente, se convirtió el campo en entero para poder procesarlo adecuadamente, se renombró el campo ID_hechos como ID para poder realizar el cruce con el df_hechos. Al df_hechos, además de lo nombrado ya, no se le realizaron más depuracines o ajustes.

Con los 2 dataframe ajustados, se procedió a unirlos, creando el archivo victimas.xlsx, eliminando una serie de variables innecesarias, realizando búsqueda/eliminación de duplicados y ajuste de formatos de algunos campos.

## **EDA**

La base final para análsis, victimas.xlsx, quedo conformada por 663 registros correspondientes cada uno a una víctima mortal en accidentes de tránsito, ocurridos en CABA durante los años 2016 a 2021 y se generarn dos variables nuevas: ciclo_vida (reagrupamiento de la variable edad, en los grupos: infantes (1 a 5 años), niños (6 a 11 años). adolescenten (12 a 17 años), jóvenes (18 a 28 años), adultos (29 a 59 años) y ancianos (mayores de 50 años)) y horario (reagrupamiento de la variable HH en los grupos: mañana (6 a 12), tarde (12 a 18) y noche (18 a 6)), necesarias para un mejor análisis de los datos.

La distribución de las víctimas mortales por año, muestra un descenso significativo en los últimos 3 años, del 35% entre el periodo 2019-2021 y el periodo 2016-2018, coioncidencialmente el periodo 2019-2021 fue el tiempo de la pandemia, por lo que esa disminución puede ser como consecuencia de las normas de comportamiento determinadas en su momento. A continuación se muestra la tabla y la gráfica resumen:

| Año | Muertes |
| ------ | ------ |
| 2016 | 130 |
| 2017 | 133 |
| 2018 | 141 |
| 2019 | 91 |
| 2020 | 75 |
| 2021 | 93 |
| Total | 663 |

<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/muertes_a%C3%B1o.jpg">
<p>

Siendo los meses de noviembe, diciembre y enero los de mayor concentración de las muertes, coincidencialmente época de verano, vacaciones:

<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/muertes_mes.png">
</p>

Y analizando por el vehículo donde se transportaba la víctima, los meses de diciembre y enero son los que presentan mayor cantidad de accidentes mortales en moto, 73 de 280, que representan el 26% de las muertes en moto. Esto es una alerta para las autoridades respectivas, para que ejerzan un mayor control a los motociclistas en dicho periodo y que tengan en buen estado las vías más frecuentadas por ellos.

<p align='center'>
TABLA 1. TOTAL VICTIMAS DE ACCIDENTE DE TRANSITO EN CABA, ENTRE 2016-2021, DIFERENCIAS POR MES Y MEDIO DE TRANSPORTE
</P>
<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/TABLA03.png">
</p>

Construyendo un perfil para caracterizar a las diferentes víctimas, la siguiente tabla puede brindar información relevante:

<p align='center'>
TABLA 1. TOTAL VICTIMAS DE ACCIDENTE DE TRANSITO EN CABA, ENTRE 2016-2021, DIFERENCIAS POR SEXO, ROL Y MEDIO DE TRANSPORTE
</P>
<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/TABLA02.png">
</p>

- La mayoría de las víctimas son hombres (el 77%, 509 de 663 víctimas).
- El 42% (281 de 663) perdió la vida en un accidente involucrada una moto, de los cuales el 88% eran hombres (247 de 281) y casi la totalidad eran los conductores de la moto (231 de 247, motociclistas hombres).
- El 37% de las víctimas eran peatones (245 de 663), de los cuales el 61% eran hombres y el 39% mujeres.
- Al respecto, el ser peatones es el rol más importante entre las causas de muerte entre las mujeres, el 62% de las víctimas mujeres eran peatones (96 de 155), y el segundo, el ser pasajeras, el 20% (31 de 155), principalmente de motos.
- Entre los hombres, el rol que tenían la mayoría de las víctima al momento del accidente era de conductor, bien sea de moto, auto, carga, móvil, el 58% (293 de 509), seguido del hecho de ser peatón, el 30% (149 de 509).

De lo anterior, se pueden sacar conclusiones importantes:

- La población más vulnerable a morir en un accidente de tránsito son los hombres, no importanto el rol que desempeñen en el accidente, y con mayor probabilidad si conducen una moto, por lo que la tarea de las autoridades se debe intensificar en esa población, ejerciendo mayores controles a los motociclistas, con retenes de control, obligatoriedad de los sistemas de seguridad personal como el uso del casco, chalecos reflectivos, exigencia de una revisión tecnico-mecánico periódica a las motos, cursos de reforzamiento sobre las leyes de tránsito, tener en buen estado y bien señaladas las vías principales y alternas y con semáforos funcionando al 100% siempre.
- Entre las mujeres, preocupa la alta tasa de muertes como peatonas, por lo que se debe intensificar jornadas pedagógicas para mejorar el comportamiento de ellas y todos, como el respeto de los semáforos, cruzar las vías solo por las zonas delimitadas y los puentes peatonales, evitar camimar cerca a vías de alto tráfico en horas de la noche y si es necesario hacerlo, llevar elementos de serguridad como chalecos reflectivos y para los mayores de edad, ir acompañados.

Relizando un análisis por ciclos de vida, se ve lo siguiente:

<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/muertes_edad.png">
</p>

El 3% del total de muertes es comprendido por los infantes, niños y adolescentes, que aunque no es muy alto, es para tener presente, generando comunicaciones para reforzar el uso adecuado de los vehículos (cantidad de pasajeros), el uso de los sistemas de seguridad (cinturos de seguridad, cascos, etc), buen estado de los vehículos (frenos, luces, airbag, motor, etc), respeto de las señales de tránsito, buen estado de las vías (pavimentadas, señalización, limpieza de la calzada, etc).

<p align='center'>
TABLA 2. VICTIMAS DE ACCIDENTE DE TRANSITO EN CABA POR CICLO DE VIDA, ENTRE 2016-2021.
</P>
<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/TABLA04.png">
</p>

De la tabla anterior, se puede notar que de las víctimas en moto el 50% eran adolescentes y jóvenes, entre 12 y 28 años y de las víctimas peatones, el 84% eran adultos y ancianos, mayores de 29 años. Dos hechos a tener presente al momento de tomar acciones para prevenir y disminuir los accidentes viales, hacia los jóvenes pueden ser campañas recalcando el importancia del respeto de las normas de tránsito (semáforos en rojo, límites de velocidad) y de seguridad vial (cascos, buen estado del vehículo, etc) y entre los adultos, igualmente, el respeto de las normas de tránsito: cruzar las vías por las zonas demarcadas, respetar los semáforos en rojo, entre otras y algunas respecto a la seguridad personal, como no andar solo por vías muy concurridas, usar los puentes peatonales, evitar cruzar vías en horas de la noche, etc.

<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/muertes_comuna.png">
</p>

<p align='center'>
<img src="https://github.com/gfgm2508/Proyecto_Individual_2/blob/main/_src/assets/muertes_calle.png">
</p>

Aunque en las avenidas se presentán la mayorías de los siniestros viales, no deja de llamar la atención el 9% de accidentes presentados en la Gral. Paz, una vía conocida por al alto tráfico vehicular, con tramos que pueden albergar hasta 300.000 vehículos por día.





