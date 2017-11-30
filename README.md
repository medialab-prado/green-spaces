# VillageVanguard
## Espacios verdes / Green space

Bienvenido a espacios-verdes!  /  Welcome to the green-spaces!


## Resumen

Aumentar los espacios verdes urbanos es una estrategia eficaz para combatir las cada vez más frecuentes olas de calor y los riesgos de efecto isla de calor causados por el cambio climático, empleando la participación comunitaria en su planificación y el mantenimiento necesario para su éxito. La participación comunitaria asegura que los proyectos de espacios verdes urbanos atiendan las necesidades locales y reflejen la historia cultural, demográfica y del desarrollo de la comunidad. Sin embargo, la colaboración comunitaria en persona puede ser costosa a la hora de prepararla, dirigirla, difundirla y repetirla.

Increasing urban green spaces is one successful strategy to combat increased heat waves and urban heat island effect risks caused by climate change, with community participation in their planning and maintenance necessary for their success. Community participation ensures that urban green space projects address local needs and reflect the cultural, demographic, and development history of the community. However, in-person community collaboration can be costly to prepare, run, report and replicate.


## Motivaciones

Desarrollo de un prototipo que utiliza SIG participativo (SIGP) para contribuir a la colaboración comunitaria cara a cara, con el fin de educar a los participantes en consideraciones medioambientales, económicas y políticas de planificación de espacios verdes urbanos en su ciudad. 
Involucrar a los participantes en un debate moderado cuyas ideas y necesidades cotidianas para el espacio verde son capturadas en el prototipo y serán entregadas a los responsables de la toma de decisiones y al público en general, en forma de informes generados dinámicamente, basados en la información geoespacial disponible, además de estar disponibles en línea.
Crear procesos de compromiso comunitario en persona cuya dirección, difusión y repetición sea más fácil para los responsables de la toma de decisiones, concretamente en lo que respecta a la planificación de espacios verdes urbanos de Madrid, Nueva York y Sao Paulo. 


## Objetivos / Goal for MediaLab-Prado Workshop

Diseño de una herramienta de colaboración en comunidad para el planeamiento urbano de espacios verdes mediante el desarrollo de un prototipo completamente funcional para el Proyecto de Restauración de New York y prueba para la ciudad de Madrid y posteriormente para Sao Paulo. Una vez se complete el proyecto NYRP sería deseable usar y probar el prototipo con el fin de evaluar el éxito y las necesidades de desarrollo reiterativo del prototipo.
Utilización de conjuntos de datos geoespaciales dispuestos en capas sobre un mapa interactivo, con las ideas y las necesidades de los participantes documentadas en su propia capa de datos.


## Recursos
- https://github.com/mapseed/espacios-verdes/wiki/Open-data-for-Madrid
- https://github.com/mapseed/espacios-verdes/wiki/Open-data-for-New-York
- https://github.com/mapseed/espacios-verdes/wiki/Open-Data-for-São-Paulo


## Procedimientos

### Gather open data for Brooklyn
Faced with the need to draw a profile of the area where the project will be implemented, we look for open data on New York City and, specifically, the Brooklyn neighborhood. We understand that the necessary information is related to the population profile, zoning, public transportation, bicycle corridor and flooding areas. With this information it is possible to understand how the population is distributed, moves, how the city is organized and the environmental problems already detected (floods, in the case of New York). We looked for this open data in American Census repositories anda NYC Open Data directory.

#### Population
[Density](https://data.cityofnewyork.us/City-Government/NYC_Population_Neighnborhoods/8hez-9j33);   
[Age](https://data.cityofnewyork.us/City-Government/New-York-City-Population-By-Census-Tracts/37cg-gxjd/data) or [Age2](https://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml);   
[Race](https://www.dropbox.com/s/0d2gs4hp0t42qg1/tab01-33.csv?dl=0);   
[Household income](https://data.cityofnewyork.us/Housing-Development/Map-of-NYCHA-Developments/i9rv-hdr5/data) or [Household income2](http://catalog.opendata.city/dataset/median-household-income-2010-census-tracts/resource/a49e4469-6185-4147-a009-e575d785cef5);   
[Open spaces](https://data.cityofnewyork.us/Recreation/Open-Space-Parks-/g84h-jbjm);   
[Gardens](http://www.greenthumbnyc.org/gardensearch.html#garden-list)

#### Transports
[Subways lines](https://data.cityofnewyork.us/Transportation/Subway-Lines/3qz8-muuu);   
[Subways stations](https://data.cityofnewyork.us/Transportation/Subway-Entrances/drex-xx56);   
[Bus routes](https://www.baruch.cuny.edu/confluence/display/geoportal/NYC+Mass+Transit+Spatial+Layers);   
[Bike lanes](https://data.cityofnewyork.us/Transportation/Bike-Routes/7vsa-caz7)

#### [Housing](https://data.cityofnewyork.us/City-Government/New-York-City-Population-By-Census-Tracts/37cg-gxjd/data)

#### [Zoning](http://www1.nyc.gov/site/planning/data-maps/open-data/dwn-gis-zoning.page#metadata)

#### [Flood](https://project.wnyc.org/flooding-sandy-new/#12.00/40.6776/-74.0620)


## **WORK FLOW**

![Summary](https://github.com/mapseed/espacios-verdes/blob/master/RemoteSensingWorkFlow.png)

_Data Source: https://remotepixel.ca/projects/satellitesearch.html_

## **GETTING DATA**

Check hottest days in New York for and Madrid in 2016.

	New York: 13th August 2016
	Madrid: One of the hottest days was on 9th July 2016

![Madrid 9 July 2016](https://github.com/mapseed/espacios-verdes/blob/master/Average%20Weather%2009072016.PNG)

There wasn’t data available for this day in the source so we decided to get the data for 21st August 2016 instead.
Luckily we had Satellite Imagery data for one of the hottest days and we downloaded the data for 9th July 2017.

## **PROCEDURE**
To generate the data for the Land Surface Temperature (LSD) we need Landsat 8 ([link](https://landsat.usgs.gov/what-are-band-designations-landsat-satellites)) Band 10 and MDL
- Band 10: Thermal Infrared (TIRS) 1
- MTL: Metadata of satellite information

Based on the location of the cities the data was selected and downloaded.

Once downloaded I loaded into QGIS and manipulate the data following this article which shows how the algorithm is calculated in ERDAS Software [here](http://community.hexagongeospatial.com/t5/Spatial-Recipes/Converting-Landsat-8-Thermal-Band-10-to-Temperature-values/ta-p/4230):

1. Clip data
2. TOA Radiance 
3. Kelvin 
4. Celsius 
5. Polygonize 
6. Smooth polygons


All this analysis and Raster manipulation was done using the QGIS Plugin “Semi-Automatic Classification Plugin” and the SAGA geotoolbox.

**Clipping original raster data**
![Clipping](https://github.com/mapseed/espacios-verdes/blob/master/clipping.PNG)

**Analyzing & calculating temperature in Celsius (From NIR to Temperature)**
![celsius](https://github.com/mapseed/espacios-verdes/blob/master/Temperature.PNG)

**Polygonize the raster data**
![polygonize](https://github.com/mapseed/espacios-verdes/blob/master/polygonize.PNG)

## **Styling** 

![First style](https://github.com/mapseed/espacios-verdes/blob/master/capture.PNG)

![Second style](https://github.com/mapseed/espacios-verdes/blob/master/capture2.PNG)

![Third style](https://github.com/mapseed/espacios-verdes/blob/master/Capture3.PNG)

![Last style](https://github.com/mapseed/espacios-verdes/blob/master/lastStyle.PNG)

## How the live version looks like [link](http://williams.mapseed.org/11/40.77534/-73.90297)

![Last style](https://github.com/mapseed/espacios-verdes/blob/master/heat%20wave%20Live.PNG)


## Cronograma

El taller internacional de desarrollo de proyectos “Inteligencia Colectiva para la Democracia 2017” tuvo lugar en Medialab-Prado del 6 de noviembre al 18 de noviembre de 2017.

## Necesidades

Desarrolladores web con experiencia y/o con conocimientos avanzados de programación de API.

Expertos en Gis, Git y librerías Javascript de edición colaborativa.

Expertos en Planificación urbana.

Expertos en comunicación.


## Referencias

### Madrid project overview / Resumen proyecto Corredor Manzanares:
La superficie total de la Ciudad de Madrid es de 60.430,70 Ha, de las cuales 6.029,84 Ha corresponden a zonas verdes de conservación municipal. A esta superficie de núcleo urbano habría que añadir las más de 15.800 Ha correspondientes al Monte del Pardo, que representan, por si solas, más de la cuarta parte (el 26,4%) de la superficie total del término municipal de la capital. 
Madrid apuesta por las infraestructuras verdes y por el impulso de la agricultura ecológica urbana para crear una ciudad más resiliente y sostenible. Las líneas de trabajo atienden a múltiples objetivos: ambientales, sociales y educativos, a través de la creación de nuevas áreas verdes, huertos urbanos, y de una oferta formativa y de programas de inclusión social.
Prueba del compromiso de Madrid por el medio ambiente es el incremento experimentado por la ratio de zonas verdes por habitante en los últimos años, teniendo en cuenta únicamente las zonas conservadas por el Ayuntamiento de Madrid. Un 10% de la superficie de Madrid es zona verde, lo que significa una dotación de 20,48 m2 (según dato de 2014 del Observatorio de la Ciudad) de zona verde por habitante, superando la ratio recomendada por la Organización Mundial de la Salud (OMS) en 5 m2 por habitante respecto del valor más exigente que dicho organismo contempla (15 m2 de superficie de zonas verdes por habitante).Al respecto, el proyecto #VillageVaugard propone la unión de la Casa de Campo con Madrid Río a través de un corredor verde, denominado "Corredor Manzanares" para la mejora ambiental, de la conexión entre los espacios verdes y medida de mitigación ante el cambio climático. Para ello se utilizará el prototipo SIG participativo (SIGP) co-diseñado para contribuir a la colaboración comunitaria cara a cara, con el fin de educar a los participantes en consideraciones medioambientales, económicas y políticas de planificación del espacio verde urbano propuesto. Después el prototipo de herramienta colaborativa capturará las ideas y necesidades cotidianas de los participantes para dicho espacio verde, que serán entregadas a los responsables de la toma de decisiones y al público en general, en forma de informes generados dinámicamente basados en la información geoespacial y que también estarán disponibles en línea, con el objetivo de que sean consideradas en el futuro corredor Manzanares.

The total area of the City of Madrid is 60,430.70 Ha, of which 6,029.84 Ha correspond to green areas of municipal conservation. To this area of urban nucleus would have to be added more than 15,800 hectares corresponding to Monte del Pardo, which represent, by themselves, more than a quarter (26.4%) of the total area of the municipality of the capital.
Madrid is committed to green infrastructure and to the promotion of urban ecological agriculture to create a more resilient and sustainable city. The lines of work serve multiple objectives: environmental, social and educational, through the creation of new green areas, urban gardens, and training and social inclusion programs.
One proof of Madrid's commitment to the environment is the increase experienced in the ratio of green area per inhabitant in recent years, taking into account only the areas preserved by the Madrid City Council. 10% of the surface of Madrid is a green zone, which means an endowment of 20.48 m2 (according to data from 2014 of the Observatory of the City) of green area per inhabitant, surpassing the ratio recommended by the World Health Organization (WHO) in 5 m2 per inhabitant with respect to the most demanding value that this organization contemplates (15 m2 of green areas per inhabitant).
In this regard, the #VillageVanguard project proposes the union of Casa de Campo with Madrid Río through a green corridor, called "Corredor Manzanares" for environmental improvement, the connection between green spaces and mitigation measurement in the face of climate change. To this end, the participatory GIS prototype (SIGP) co-designed to contribute to face-to-face community collaboration will be used to educate participants on the environmental, economic and political planning considerations of the proposed urban green space. Afterwards, the collaborative tool prototype will capture the participants' ideas and everyday needs for the green space, which will be delivered to decision-makers and the general public, in the form of dynamically generated reports based on geospatial information and also will be available online, with the objective of being considered in the future Manzanares corridor.

### São Paulo project overview
Con aproximadamente 12.4 millones de habitantes, São Paulo tiene 12.4 metros cuadrados de áreas verdes por persona, lo que está dentro del promedio de la ONU. Pero este promedio es profundamente desigual según la región de la ciudad. En el centro de São Paulo, por ejemplo, el índice mide solo 6 metros cuadrados por persona, mientras que en el sur, a 37 km del centro, llega a 2.655 metros cuadrados por persona. Sin embargo, el centro de São Paulo emite la mayoría de los contaminantes, especialmente los que causan efectos de invernadero.Para cambiar esta situación, la comunidad de São Paulo y los activistas ambientales se han organizado en grupos para solicitar la creación de nuevos parques. Uno de los movimientos más importantes es Parque Augusta, que ha estado activo desde 2013 reivindicando un parque en el barrio Consolação, en el corazón de la ciudad. El terreno tiene 24 mil metros cuadrados y representa la última área verde libre en el centro de la ciudad.El objetivo del proyecto Village Vanguard, que se llevará a cabo por el Movimiento Parque Augusta y Rede Nuevos Parques, será escuchar a la comunidad sobre lo que quieren hacer en esta área y presentarle un proyecto al alcalde, que está dispuesto a dar este parque a la ciudad y un corredor verde para vincularlo con la Plaza Roosevelt.

With about 12.4 million inhabitants, São Paulo has 12.4 square meters of green areas per person,  which is within the UN average. But this average is deeply unequal depending on the region of the city. In downtown São Paulo, for instance, the index is only 6 square meters per person, while in the south  – 37 km far from the center - it reaches 2.655 square meters per person. However, downtown São Paulo emits most of the pollutants, especially those that cause greenhouse effects. To change this situation, the São Paulo community and environmental activists have been organizing themselves in groups to ask for the creation of new parks. One of the most important movements is Parque Augusta, which has been active since 2013 vindicating a park in the Consolação neighborhood, in the heart of the city. The land is 24 thousands square meters and represents the last green free space in the downtown area. The objective of the Village Vanguard project, which will be implemented by Movimento Parque Augusta and Rede Novos Parques, is to listen the community about what they want to do in this area and present a project to the mayor, who is willing now to give this park to the city and a green corridor to link it to Roosevelt Square.



## Equipo / Team
### Promotor: 

Erika Whillas - Project lead, erika.whillas@gmail.com, Australia

### Colaboradores: 

Jake Caggiano - Desarrolador-Developer, jacob@mapseed.org, Estados Unidos

Sonia Delgado Berrocal - Arquitecta-Urbanista, paisajista e investigadora, sonarqpaisajes@gmail.com, España

Malu Oliveria - Comunicadora e investigadora, maluoliveira60@gmail.com, Brasil

Carles Boïls Gisbert - GIS experto, carboig@gmail.com, España

Trevor Croxson - Desarrolador-Developer, trevor@mapseed.org, Estados Unidos

Luke Swart - Ingeniero informático, luke@mapseed.org, Estados Unidos


## Licencia
CC by-sa-nc

## URL
hull.mapseed.org

williams.mapseed.org

manzanares.mapseed.org

augusta.mapseed.org


## Imagen


