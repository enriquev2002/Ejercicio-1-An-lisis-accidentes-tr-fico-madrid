# Ejercicio-1-An-lisis-accidentes-tr-fico-madrid: Análisis de los accidentes de tráfico y su implicación en personas en la ciudad de Madrid en los 7 primeros meses de 2026
Ejercicio 1: "Dashboard &amp; Análisis de Datos" para el curso de Data Analysht de "ThePower"
Análisis de los accidentes de tráfico y su implicación en personas en la ciudad de Madrid en los 7 primeros meses de 2026

Dicho análisis consiste en, a través de datos abiertos del ayuntamiento de Madrid, analizar aspectos de los incidentes viales como son la ubicación, estado meteorlógico, día de la semana, número de personas implicadas y heridas, tipos de accidentes, etc.
Se ha hecho un análisis descriptivo usando herramientas de Excell y Power-Query. 
En la carpeta del proyecto podremos encontrar el archivo CSV original, el archivo excell con el tratamiento de los datos y el posterior análisis mediante un Dashboar interactivo y este archivo README en el que se detallas los pasos del proceso y un posterior informe.

Información obtenida de las fuentes abiertas del ayuntamiento de Madrid con la colaboración de la Policía Municipal de la ciudad que puede ser encontrado en el siguiente enlace:
Accidentes de tráfico en la ciudad de Madrid (https://datos.madrid.es/dataset/300228-0-accidentes-trafico-detalle/resource/300228-34-accidentes-trafico-detalle/download/300228-34-accidentes-trafico-detalle.csv)


PASOS DEL PROCESO
CARGA DE DATOS
-Descarga de csv e importación a Excell mediante a Power-Query

IDENTIFICACIÓN DE VARIABLES
- Tenemos una fila por cada incidente de tráfico registrado en la ciudad de Madrid, comprendidos entre el 1 de enero de 2026 y el 31 de Julio de 2026
- Inicialmente tenemos 19 columnas, una con el número de expediente (un expediente por accidente), otra con la fecha expresada en DD/MM/AAAA, La siguiente con la hora, seguimos con dos más, una con la ubicación/calle y la siguiente con el número o kilómetro de la calle, dos más para los distritos, una de manera codificada y otra de manera escrita, después el tipo de accidente, el estado meteorológico, el tipo de vehículo causante del accidente, el tipo de persona implicadas en el accidente con dos columnas más para la edad y otra para el sexo, después dos columnas para lesividad del paciente (una con código y otra con información escrita), dos columnas para coordenadas del accidente y otras dos para positivos de alcohol y drogas respectivamente.
-La mayoría de columnas contienen datos de carácter cualitativo excepto la fecha, códigos y edades que son de carácter cuantitativo

TRANSFORMACIÓN Y LIMPEZA
- En un primer momento se identifican 30.457 filas que podríamos suponer que es el número total de incidentes.
- Se comprueban duplicados, da un total de 28.372  nº de de expediente duplicados en las filas, se investiga y esto se da porque cada accidente tiene un único número pero puede haber más de una fila con el mismo número si se da que hay dos o más personas implicadas, es decir hay una fila por cada persona implicada en un accidente. Es por eso que para evitar la perdida de datos relacionados con pacientes pero a la vez no tener sesgo a la hora de analizar los datos relacionados con los accidentes (ubicación, hora, etc) se decide duplicar la hoja y hacer análisis paralelos, una centrada en el accidente y otra en las personas.
-Eliminando los duplicados, y dejado solo una fila por accidente nos da un total de 13.144. En este libro se ocultan los datos relativos a personas para facilitar el análisis
-Por tanto el total de personas implicadas en accidentes es 30.457
-Se calculan las celdas en blanco para su posterior gestión (2 tipo accidente, 1675 estado metrológico, 227 tipo vehículo, 5728 código lesividad y lesividad ,4 coordenadas, 82 positivos alcoholemia y 13076 positivos drogas)
-Se crea una columna al lado de la fecha para saber el día de la semana
-Se crea una columna al lado del día de la semana para saber el mes
-El formato hora se transforma a HH:MM en formato 24 horas, eliminando los segundos.
-Como la Policía Municipal de Madrid trabaja en turnos de mañana, tarde y noche (07:01 a 15:00, 15:01 a 23:00 y 23:01 a 07:00 respectivamente), se crea una nueva columna para agrupar en estos turnos para posteriormente ver necesidades específicas
-Se rellenan los huecos en blanco por "Se desconoce".
-Se realizan los mismo pasos en el libro relacionado con los datos a las personas

PATRONES Y IDENTIFICACIÓN
- Se obtiene mediante tablas dinámicas los datos principales (Nº total de accidentes, Nº Total de personas implicadas y Nº Total heridos)
-Se generan tablas dinámicas y gráficos dinámicos para el análisis de:
	-El reparto de accidentes por días de la semana y turnos
	-El reparto de accidentes por distritos (por calles no debido a que se generan datos excesivos que no dejan ver los resultados con claridad)
	-El tipo de accidente
	-El estado meteorológico en el momento del accidente
	-Diferencias de género por personas implicadas
	-Reparto de edades de las personas implicadas
	-Nº de positivos en alcohol
	-Nº de personas implicadas según tipo de vehículo
- No se identifica ninguna anomalía ni ningún "Outlier". Si que existen datos mínimos como son el número de fallecidos o algún tipo de vehículos poco frecuentes en accidentes, pero decido dejarlos ya que aportan una visión completa de la versatilidad de los accidentes.

DASHBOARD INTERACTIVO Y VERIFICACIÓN DE SUPOSICIONES
-Para empezar a contrastar hipótesis se genera de manera gráfica un dashboard, para esto primero se duplica la hoja de tablas dinámicas.
-Referenciando con la hoja anterior se colocan título y "Big Numbers" en la parte superior.
-Se colocan las tablas dinámicas realizadas con anterioridad, tanto los que afectan a solo accidentes como las de personas.
- respecto a las tablas con información sobre los accidentes se generan unos segmentadores de datos, para hacer el dashboard interactivo. Se agregan segmentadores relacionados con el mes (de enero a julio), turno, distrito, tipo de accidente y estado meteorológico.

INFORME EXPLICATIVO
En el presente análisis de la siniestralidad vial en la ciudad de Madrid durante los 7 primeros meses del año 2026, podemos ver como ha habido 13.144 accidentes viales de distinta índole teniendo implicados a 30.457 personas, la mayoría de veces había más de una persona implicada en cada accidente, y dejando un total de 6.380 de heridos, un 21% con respecto al total de personas implicadas.

Si nos fijamos en el reparto por día de la semana y según los turnos en los que trabaja la Policía municipal de Madrid (mañana, tarde y noche), podemos apreciar como el nº mayor de accidentes no se dan un Lunes por la mañana, que es cuando podríamos pensar por la entrada a los trabajos y colegios, sino los jueves por la tarde y el menor número los domingos por la noche, motivados tal vez por el menor número de personas circulando, esto nos sirve para poder ajustar así mejor el número de efectivos de la policía para cada turno y hacer un uso más efectivo de estos.

En caso de sectorizarlos por distrito el mayor número de accidentes ocurren en el distrito de Carabanchel y el menor en el de barajas, información útil también para desplegar más policías, sobre todo aquellos que hacen funciones de atestados, en aquellas zonas más concurridas. También podría servir esto para localizar por cercanía las bases del SAMUR.

En cuanto al tipo de accidentes, aunque pudiéramos pensar que la mayor parte de estos ocurren por alcance podemos apreciar que estos solo han sido 2.666, frente a las 3.092 colisiones fronto-laterales que se han registrado siendo así el mayor motivo de accidente. También podemos apreciar algunas casi anecdóticas como 0 despeñamientos, 57 vuelcos y 46 atropellos a animales, que se pueden justificar conociendo que la ciudad de Madrid es una gran urbe en la cual no hay casi fauna salvaje y las velocidades están muy limitadas a 30 o 50 kilómetros por hora.

En cuanto al estado meteorológico, aunque podamos pensar que interfiere mucho, no podríamos achacarle gran cosa debido a que la gran mayoría de los accidentes ocurren en días despejados, ya que son la mayoría de los días en Madrid. También tenemos algunos estados propios de los meses de invierno (enero, febrero y marzo) como son las nevadas o granizadas.

Si nos referimos a las personas implicadas comentar que el grupo de edad que en más incidentes viales se ve involucrado hablaríamos de aquellas edades comprendidas entre 45 y 49, aunque exista bastante homogeneidad desde los 25 hasta los 54. Por genero solamente comentar que la mayoría de implicados son varones con un 60% frente al 29% de las mujeres.

En el caso de la lesividad la mayoría de incidentes viales transcurre sin registrase heridos o con activaciones del SAMUR pero sin necesidad de realizar ninguna asistencia por parte de los sanitarios, de ese 21% de personas heridas que hemos comentado al principio la mayoría de ellas son atendidas en el propio lugar del siniestro sin necesidad de traslado a centro hospitalario (3.234), siendo solo necesario ingresar en los hospitales madrileños a 1.113 personas durante una estancia igual o menor a 24 horas y 309 excediendo ese límite de horas. Comentar también que se han registrado 11 fallecimientos, los cuales la mayoría se han dado por atropellos, siendo este un futuro tema de estudio para proponer posibles medidas que reduzcan la siniestralidad comentada.

En cuanto a positivos en alcoholemia la cifra es ínfima con solo un 3% y como era de suponer el vehículo más implicado es el turismo (20.970) seguido muy de lejos en segundo lugar de las furgonetas (2.028). Llama la atención que vehículos de conductores profesionales como son ambulancias, autobuses de la EMT y autobuses articulados del mismo servicio público tienen muy poca siniestralidad para la alta exposición que tienen, 2, 10 y 1 respectivamente.

En conclusión , dicho estudio aporta unas pequeñas pinceladas del estado y la afectación de los accidentes de tráfico en la ciudad de Madrid y aconsejo ampliar dicho estudio para poder profundizar en las causas y por tanto poder aplicar soluciones efectivas a dicha problemática.


AUTOR:
Enrique Miguel Villanueva Viamonte.
El autor declara que no existe ningún conflicto de interés en la realización del trabajo.

