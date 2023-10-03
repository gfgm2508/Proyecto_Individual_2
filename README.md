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

Con los 2 dataframe ajustados, se procedió a unirlos, creando el archico total_victimas.xlsx, eliminando una serie de variables innecesarias, realizando búsqueda/eliminación de duplicados y ajuste de formatos de algunos campos.

## **EDA**

La base final para análsis, total_victimas.xlsx, quedo conformada por 664 registros correspondientes cada uno a victimas mortales de accidentes de tránsito ocurridos en CABA durate los años 2016 a 2021.

La distribución de las víctimas por año, muestra un descenso significativo en los últimos 3 años de las muertes en accidentes de tránsito, de 

![Alt text](image-3.png)


<img src="../_src/muertes_año.png">
