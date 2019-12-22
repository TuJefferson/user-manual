<justify>

Esta sección presenta la información en forma de tablas que pueden ser invocadas porel usuario.  

Las tablas fundamentalmente muestran la información de tres fuentes, el **Audit** (Información de los agentes), el **CDR** (Información de las llamadas)y el **CallEntry** (Información de las colas). Adicionalmente esta información se combina con elementos que permiten su clasificación.  

Todas las tablas tienen acceso a un "selector" que se activa al presionar el link de "Filtre la información aquí", donde el usuario puede escoger una fecha, un intervalo de fecha, intervalos de hora, modalidades del reporte o variables de clasificación tanto de agentes como de colas.  

Nótese que todas las tablas generadas aquí pueden invocarse directamente con una herramienta de consultas SQL, accediendo a la base de datos con un usuario de solo lectura, lo que permite obtener variantes de los reportes para usuarios avanzados.

# Portada

![Texto alternativo](/img/04-reports/reports-main/01-reports.jpg)

Al ingresar en el módulo puede visualizar un portada que contiene una barra de navegación.  

El cuerpo de la portada despliega el logo de la organización, el nombre del reporte, el slogan, la versión de Proser y la versión de la sección.  

**NOTA TÉCNICA:** La información del logo y nombre de la organización y el slogan pueden modificarse en los archivos de las variables de entorno de frontend (env.js)  

Si el usuario no está logueado, el sistema solo permite acceso a la funcionalidad de login para que el usuario escriba un nombre de usuario y una contraseña.

![Texto alternativo](/img/04-reports/reports-main/01-login.jpg) 

Una vez logueado podrá tener acceso a las funcionalidades del sistema.

## Barra de navegación
![Texto alternativo](/img/04-reports/reports-main/06-main.jpg) 

Esta barra de navegación contiene:

### Logo de ProSer
![Texto alternativo](/img/04-reports/reports-main/07-logo.jpg) 

Que actúa como un botón para regresar al menú principal.

### Link de Reportes
![Texto alternativo](/img/04-reports/reports-main/08-link.jpg) 

Que regresa siempre a esta portada.

### Menú de llamadas
![Texto alternativo](/img/04-reports/reports-main/09.jpg) 

Que despliega un menú mostrando los reportes asociados a las llamadas:  

Entrantes, salientes, detalle de llamadas, abandonadas y un reporte sobre los tiempos de espera.

### Menú de agentes
![Texto alternativo](/img/04-reports/reports-main/10.jpg) 

Aquí observamos links al reporte de conexión, detalle de auxiliares y de asignaciones.

### Menú de operación
![Texto alternativo](/img/04-reports/reports-main/11.jpg) 

Este menú presenta dos vistas de la misma data: Operativo detallado y el consolidado.  

La información que presentan es la misma, pero difiere la forma en que es mostrada cuando se trata de un intervalo de fechas ya que el primero agrupa la información por fechas mientras que el segundo la acumula por agente.

### Menú de data
![Texto alternativo](/img/04-reports/reports-main/12.jpg) 

El menú de data permite ver, acceder y exportar las tablas principales que registran la información:  

**Audit** se refiere a la tabla que guarda la información relacionada con los agentes.  

Aquí se registra la información de los logueos (conexión y desconexión),las pausas o interrupciones de trabajo que son de dos tipos, las que son para el agente (Auxiliares tales como ir al baño, reuniones, seguimiento de actividades, etc) y las que son para el proyecto ejecutado (Llamadas salientes, redes sociales, análisis de información, tareas asignadas queno implican llamar por teléfono). Estas clasificaciones y nombres varían según como se hayan configurado.  

La tabla de audit se genera en el momento en que se inicia una actividad tal como loguearse, o entrar en pausa. El registro no está completo y algunos campos están en blanco hasta que el usuario decide cerrar la actividad. Una vez cerrado el registro este no se altera.  

El audit posee los campos originales generados por el call center y algunos campos adicionales para la clasificación.  

**Cdr** se refiere a la información relacionada con las llamadas realizadas desde la Central Telefónica.  

Cada vez que la central telefónica detecta alguna actividad en las colas o en las extensiones, crea un registro detallado de dicha información llamado CDR (Call Detail Record). La data se guarda en una base de datos que contiene toda esta información y puede ser consultada en cualquier momento.  

Cada registro es creado una vez que la llamada finaliza, así que cualquier actividad en curso no existe para el CDR.  

Este reporte exporta los campos originales del CDR y le agrega alguna información complementaria para efectos de análisis y clasificación.  

**CallEntry** se refiere a la actividad en las colas.  

Cada vez que una llamada ingresa a una cola, se crea un registro en esta tabla. La información no está completa hasta que la llamada finaliza, en cuyo caso el registro llena los campos faltantes (hora y fecha de finalización, estado y duración por ejemplo).  

La data contiene la información del registro y algunos campos que facilitan la clasificación de la llamada.

### Menú de usuario
![Texto alternativo](/img/04-reports/reports-main/13.jpg) 

Este menú muestra el nombre del usuario, el estado de la conexión (online/offline) y la hora. Si se oprime aparece la opción para desloguearse.

## Reportes de llamadas entrantes

Es una vista que expresa información sobre los indicadores más relevantes de las llamadas entrantes por día según la fecha o intervalo de fecha seleccionada, brindando estadísticas que permiten conocer el comportamiento global de las llamadas recibidas.  

Esta herramienta proporciona la capacidad de navegar a través de datos 
históricos, dando a conocer, desde el inicio de la operación del Call Center hasta la fecha actual, los valores solicitados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/4.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/4-1.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/01-calls/01-incoming/4-2.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/5.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Gráfico
Permite visualizar la información de los indicadores principales del reporte en un gráfico de barras. Es un gráfico interactivo, concede la oportunidad al usuario de ocultar y/o hacer visible los valores.  

Dentro de la vista del gráfico aparecen dos (02) botones: Tabla, Recalcular.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/5-1.jpg) 
**<center> Figura 7 - Zona de botones(Gráfico) </center>**

##### Tabla
Devuelve al usuario a la vista con la tabla de contenido del reporte.

##### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra.

#### Exportar excel
Inicia el proceso de exportación de la información mostrada en el 
reporte hacia un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/5-2.jpg) 
**<center> Figura 8 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de llamadas entrantes:

![Texto alternativo](/img/04-reports/01-calls/01-incoming/6.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### Fecha
Indica el nombre del día y la fecha de la información solicitada.

#### Hora inicio
Indica la hora en la que fue recibida la primera llamada de la fecha.

#### Hora final
Indica la hora en la que fue recibida la última llamada de la fecha.

#### Recibidas
Indica la cantidad de llamadas recibidas en la fecha indicada.

#### Atendidas
Indica la cantidad de llamadas atendidas en la fecha indicada.

#### Atendidas antes de
Indica la cantidad de llamadas atendidas antes de cumplirse el umbral de tiempo ideal de atención, en la fecha indicada.

#### Atendidas después de
Indica la cantidad de llamadas atendidas después de cumplirse el umbral de tiempo ideal de atención, en la fecha indicada.

#### Abandonadas
Indica la cantidad de llamadas abandonadas en la fecha indicada.

#### Cortas
Indica la cantidad de llamadas finalizadas antes de un valor de tiempo previamente definido por la empresa o el cliente, en la fecha indicada. Usualmente el valor de tiempo corresponde a los 10 segundos.

#### Colgadas agente
Indica la cantidad de llamadas culminadas por los agentes, es decir, cuando la llamada finaliza porque el agente colgó primero que el llamante. El cálculo de este valor corresponde a la fecha indicada.

#### Nivel servicio
Indica el porcentaje de llamadas contestadas antes de finalizar el 
tiempo ideal de atención, conocido comúnmente como umbral (normalmente es de 20 segundos). El cálculo de este valor corresponde a la fecha indicada. 

#### Nivel atención
Indica el porcentaje que representa las llamadas atendidas con respecto a la cantidad de llamadas recibidas. El cálculo de este valor corresponde a la fecha indicada.

![Texto alternativo](/img/04-reports/01-calls/01-incoming/6-1.jpg) 
**<center> Figura 10 - Tabla de contenido </center>**

#### Nivel abandono
Indica el porcentaje que representa la cantidad de llamadas no contestadas con respecto a las llamadas recibidas. El cálculo de este 
valor corresponde a la fecha indicada.

#### Tiempo medio de operación (TMO)
Indica el tiempo promedio que dura un agente atendiendo una llamada, en la fecha indicada.

#### Tiempo medio de espera (ASA)
Indica el tiempo promedio que transcurre desde que las llamadas ingresan a la cola hasta ser atendidas, en la fecha indicada.

#### Seg operación
Indica la duración total de operación en segundos, en la fecha indicada.

#### Hrs operación
Indica la duración total de operación en: hora, minutos y segundos, en la fecha indicada.

#### Seg espera
Indica el tiempo total de espera en segundos, en la fecha indicada.

#### Hrs operación
Indica el tiempo total de espera en: hora, minutos y segundos, en la fecha indicada.

## Reportes de llamadas entrantes por intervalo
Es una vista que expresa información sobre los indicadores más relevantes de las llamadas entrantes por día según la fecha seleccionada, brindando estadísticas que permiten conocer el comportamiento global de las llamadas recibidas.  

A diferencia del reporte de llamadas entrantes, el reporte de llamadas entrantes por intervalo ofrece la funcionalidad de fragmentar la información en intervalos de tiempo.  

Esta herramienta proporciona la capacidad de navegar a través de datos históricos, dando a conocer, desde el inicio de la operación del Call Center hasta la fecha actual, los valores solicitados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/4.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/4-1.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/4-2.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/5.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Gráfico
Permite visualizar la información de los indicadores principales del reporte en un gráfico de barras. Es un gráfico interactivo, concede la oportunidad al usuario de ocultar y/o hacer visible los valores.  

Dentro de la vista del gráfico aparecen dos (02) botones: Tabla, Recalcular.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/5-1.jpg) 
**<center> Figura 7 - Zona de botones(Gráfico) </center>**

##### Tabla
Devuelve al usuario a la vista con la tabla de contenido del reporte.

##### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra.

#### Exportar excel
Inicia el proceso de exportación de la información mostrada en el 
reporte hacia un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/5-2.jpg) 
**<center> Figura 8 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de llamadas entrantes:

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/6.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### Fecha
Indica el nombre del día y la fecha de la información solicitada.

#### Intervalo inicial
Indica la hora inicial del intervalo.

#### Intervalo final
Indica la hora final del intervalo.

#### Recibidas
Indica la cantidad de llamadas recibidas en la fecha indicada.

#### Atendidas
Indica la cantidad de llamadas atendidas en la fecha indicada.

#### Atendidas antes de
Indica la cantidad de llamadas atendidas antes de cumplirse el umbral de tiempo ideal de atención, en la fecha indicada.

#### Atendidas después de
Indica la cantidad de llamadas atendidas después de cumplirse el umbral de tiempo ideal de atención, en la fecha indicada.

#### Abandonadas
Indica la cantidad de llamadas abandonadas en la fecha indicada.

![Texto alternativo](/img/04-reports/01-calls/02-incoming-by-interval/6-1.jpg) 
**<center> Figura 10 - Tabla de contenido </center>**

#### Cortas
Indica la cantidad de llamadas finalizadas antes de un valor de tiempo previamente definido por la empresa o el cliente, en la fecha indicada. Usualmente el valor de tiempo corresponde a los 10 segundos.

#### Colgadas agente
Indica la cantidad de llamadas culminadas por los agentes, es decir, cuando la llamada finaliza porque el agente colgó primero que el llamante. El cálculo de este valor corresponde a la fecha indicada. 

#### Nivel servicio
Indica el porcentaje de llamadas contestadas antes de finalizar el 
tiempo ideal de atención, conocido comúnmente como umbral (normalmente es de 20 segundos). El cálculo de este valor corresponde a la fecha indicada. 

#### Nivel atención
Indica el porcentaje que representa las llamadas atendidas con respecto a la cantidad de llamadas recibidas. El cálculo de este valor corresponde a la fecha indicada.

#### Nivel abandono
Indica el porcentaje que representa la cantidad de llamadas no contestadas con respecto a las llamadas recibidas. El cálculo de este 
valor corresponde a la fecha indicada.

#### Tiempo medio de operación (TMO)
Indica el tiempo promedio que dura un agente atendiendo una llamada, en la fecha indicada.

#### Tiempo medio de espera (ASA)
Indica el tiempo promedio que transcurre desde que las llamadas ingresan a la cola hasta ser atendidas, en la fecha indicada.

#### Seg operación
Indica la duración total de operación en segundos, en la fecha indicada.

#### Hrs operación
Indica la duración total de operación en: hora, minutos y segundos, en la fecha indicada.

#### Seg espera
Indica el tiempo total de espera en segundos, en la fecha indicada.

#### Hrs operación
Indica el tiempo total de espera en: hora, minutos y segundos, en la fecha indicada.

## Reportes de llamadas salientes manuales
Es una vista que expresa información sobre los indicadores más relevantes de las llamadas salientes manuales por día según la fecha o intervalo de fecha seleccionada, brindando estadísticas que permiten conocer el comportamiento global de las llamadas salientes manuales.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/4.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/4-1.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/4-2.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/5.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Gráfico
Permite visualizar la información de los indicadores principales del reporte en un gráfico de barras. Es un gráfico interactivo, concede la oportunidad al usuario de ocultar y/o hacer visible los valores.  

Dentro de la vista del gráfico aparecen dos (02) botones: Tabla, Recalcular.

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/5-1.jpg) 
**<center> Figura 7 - Zona de botones(Gráfico) </center>**

##### Tabla
Devuelve al usuario a la vista con la tabla de contenido del reporte.

##### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra.

#### Exportar excel
Inicia el proceso de exportación de la información mostrada en el 
reporte hacia un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/5-2.jpg) 
**<center> Figura 8 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de llamadas salientes manuales:

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/6.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### Fecha
Indica el nombre del día y la fecha de la información solicitada.

#### Hora inicio
Indica la hora en la que fue realizada la primera llamada de la fecha.

#### Hora final
Indica la hora en la que fue realizada la última llamada de la fecha.

#### Llamadas realizadas
Indica la cantidad de llamadas realizadas por el agente en la fecha indicada.

#### Llamadas fallidas
Indica la cantidad de llamadas realizadas por los agentes que fueron fallidas en la fecha indicada.

#### Llamadas contestadas
Indica la cantidad de llamadas realizadas por los agentes que fueron contestadas en la fecha indicada.

#### Llamadas efectivas
Indica la cantidad de llamadas realizadas por los agentes que fueron efectivas en la fecha indicada.

#### Llamadas colgadas
Indica la cantidad de llamadas realizadas por los agentes que fueron colgadas en la fecha indicada.

#### Nivel de contactabilidad
Indica el porcentaje que representa la cantidad de llamadas contestadas por el destinatario con respecto a la cantidad de llamadas realizadas. El cálculo de este valor corresponde a la fecha indicada. 

#### Nivel de efectividad
Indica el porcentaje que representa las llamadas efectivas con respecto a la cantidad de llamadas realizadas. El cálculo de este valor corresponde a la fecha indicada. 

![Texto alternativo](/img/04-reports/01-calls/03-manual-outgoing/6-1.jpg) 
**<center> Figura 10 - Tabla de contenido </center>**

#### Segundos de operación 
Indica la duración total de operación en segundos, en la fecha indicada.

#### Tiempo de operación
Indica el tiempo promedio que dura un agente atendiendo una llamada, en la fecha indicada.

#### Tiempo medio de operación (TMO) saliente
Indica el tiempo promedio que dura un agente realizando una llamada saliente, en la fecha indicada.

## Reportes de llamadas salientes manuales por intervalo
Es una vista que expresa información sobre los indicadores más relevantes de las llamadas salientes manuales por día según la fecha seleccionada, brindando estadísticas que permiten conocer el comportamiento global de las llamadas realizadas por los agentes.  

A diferencia del reporte de llamadas salientes manuales, el reporte de llamadas salientes manuales por intervalo ofrece la funcionalidad de fragmentar la información enintervalos de tiempo.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Gráfico
Permite visualizar la información de los indicadores principales del reporte en un gráfico de barras. Es un gráfico interactivo, concede la oportunidad al usuario de ocultar y/o hacer visible los valores.  

Dentro de la vista del gráfico aparecen dos (02) botones: Tabla, Recalcular.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Gráfico) </center>**

##### Tabla
Devuelve al usuario a la vista con la tabla de contenido del reporte.

##### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra.

#### Exportar excel
Inicia el proceso de exportación de la información mostrada en el 
reporte hacia un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/4-2.jpg) 
**<center> Figura 8 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada porel reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de llamadas salientes manuales por intervalo:

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/5.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### Fecha
Indica el nombre del día y la fecha de la información solicitada.

#### Intervalo inicial
Indica la hora inicial del intervalo.

#### Intervalo final
Indica la hora final del intervalo.

#### Llamadas realizadas
Indica la cantidad de llamadas realizadas por el agente en la fecha indicada.

#### Llamadas fallidas
Indica la cantidad de llamadas realizadas por los agentes que fueron fallidas en la fecha indicada.

#### Llamadas contestadas
Indica la cantidad de llamadas realizadas por los agentes que fueron contestadas en la fecha indicada.

#### Llamadas efectivas
Indica la cantidad de llamadas realizadas por los agentes que fueron efectivas en la fecha indicada.

#### Llamadas colgadas
Indica la cantidad de llamadas realizadas por los agentes que fueron colgadas en la fecha indicada.

![Texto alternativo](/img/04-reports/01-calls/04-manual-outgoing-by-interval/5-1.jpg) 
**<center> Figura 10 - Tabla de contenido </center>**

#### Nivel de contactabilidad
Indica el porcentaje que representa la cantidad de llamadas contestadas por el destinatario con respecto a la cantidad de llamadas realizadas. El cálculo de este valor corresponde a la fecha indicada. 

#### Nivel de efectividad
Indica el porcentaje que representa las llamadas efectivas con respecto a la cantidad de llamadas realizadas. El cálculo de este valor corresponde a la fecha indicada. 

#### Segundos de operación 
Indica la duración total de operación en segundos, en la fecha indicada.

#### Tiempo de operación
Indica el tiempo promedio que dura un agente atendiendo una llamada, en la fecha indicada.

#### Tiempo medio de operación (TMO) saliente
Indica el tiempo promedio que dura un agente atendiendo una llamada saliente, en la fecha indicada.


## Reporte de detalles de llamadas
Es un reporte que muestra el detalle de cada llamada del Call Center, brindando datos referentes a las fechas y los valores importantes según sus estadísticas.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Exportar excel
Inicia el proceso de exportación de la información mostrada en el 
reporte hacia un archivo excel.

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de detalles de llamadas:  

Dentro de la tabla de contenido se despliega la información solicitada, esta información varía de acuerdo al reporte. Para el caso del reporte de detalles de llamadas, muestra los datos que identifica una llamada en el Call Center. Esta tabla se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Grabación
Indica la grabación de la llamada específica asociada a ese registro.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/6.jpg) 
**<center> Figura 9 - Tabla de contenido(Grabación) </center>**

#### Tipo de llamada
Indica el tipo de llamada asociada a ese registro.

#### Origen
Indica el origen de la llamada asociada a ese registro.

#### Destino
Indica el destino de la llamada asociada a ese registro.

#### Id
Indica el ID del agente que operó la llamada asociada a ese registro.

#### Ext
Indica la extensión de que operó la llamada asociada a ese registro.

#### Trans
Indica si una llamada fue transferida. El valor que correspondiente es: xfer.

#### Agente
Indica el nombre del agente que atendió la llamada asociada a ese registro.

#### Fecha de inicio
Indica la fecha en la que la llamada asociada a ese registro fue atendida o realizada.

#### Hora de inicio 
Indica la hora en la que la llamada asociada a ese registro fue atendida o realizada, en formato de horas, minutos y segundos.

#### Hora fin
Indica la hora en la que la llamada asociada a ese registro fue finalizada o salió de la cola sin ser atendida.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/5-1.jpg) 
**<center> Figura 10 - Tabla de contenido </center>**

#### Duración
Indica la duración, de la llamada asociada a ese registro.

#### Estatus

#### Colgado cliente
Indica la hora en la que la llamada fue colgada por el cliente.

![Texto alternativo](/img/04-reports/01-calls/05-calls-detail/5-2.jpg) 
**<center> Figura 11 - Tabla de contenido </center>**

#### Colgado agente
Indica la hora en la que la llamada fue colgada por el agente.

#### Hora de abandono
Indica la hora en que la llamada fue abandonada.

#### Supervisor
Indica el nombre del supervisor, asociada a ese registro.

#### Cdr id
Indica la identificación del Cdr perteneciente a ese registro.

#### Uniqueid
Indica un código único de identificación de la llamada asociada a ese registro.

## Reporte de llamadas abandonadas

Es una vista que expone información sobre las llamadas recibidas que no fueronatendidas en una fecha señalada, brindando datos referentes a las fechas y los valores importantes según sus estadísticas.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Exportar excel
Inicia el proceso de exportación de la información mostrada en el 
reporte hacia un archivo excel.

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada, 
esta información varía de acuerdo al reporte. Para el caso del registro de llamadas abandonadas, muestra los datos que identifica una llamada que no fue atendida al ingresar al Call Center. Esta tabla se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/01-calls/06-abandoned-calls/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Origen
Indica el origen de la llamada abandonada.

#### Fecha
Indica la fecha de la llamada abandonada.

#### Entrada cola
Indica la hora en la que la llamada asociada a ese registro ingresó en la cola.

#### Segundos espera
Indica la duración, en segundos, que la llamada asociada a ese registro esperó en la cola para ser atendida.

#### Tiempo de espera
Indica la duración, en formato horas, minutos y segundos, que la 
llamada asociada a ese registro esperó en la cola para ser atendida.

#### Final
Indica la hora en la que la llamada asociada a ese registro abandonó la cola.

#### Uniqueid
Indica un código único de identificación de la llamada asociada a 
ese registro.

#### Nombre cola
Indica el nombre de la cola asociada a ese registro.

#### Número cola
Indica el número de la cola asociada a ese registro.

## Reporte de tiempo de espera
Es una vista que expresa información sobre la cantidad de llamadas que 
esperaron para ser atendidas. La información se clasifica en intervalos de segundos definidos, brindando estadísticas que permiten conocer el comportamiento global de los tiempos de espera de los clientes.  

El reporte de tiempo de espera ofrece la funcionalidad de fragmentar la 
información en intervalos de tiempo.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Gráfico
Permite visualizar la información de los indicadores principales del reporte en un gráfico de barras. Es un gráfico interactivo, concede la oportunidad al usuario de ocultar y/o hacer visible los valores.  

Dentro de la vista del gráfico aparecen dos (02) botones: Tabla, Recalcular.

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Gráfico) </center>**

##### Tabla
Devuelve al usuario a la vista con la tabla de contenido del reporte.

##### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra.

#### Exportar excel
Inicia el proceso de exportación de la información mostrada en el 
reporte hacia un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/4-2.jpg) 
**<center> Figura 8 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de tiempos de espera: 

![Texto alternativo](/img/04-reports/01-calls/07-wait-time/5.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### Fecha
Indica el nombre del día y la fecha de la información solicitada.

#### Intervalo inicial
Indica la hora inicial del intervalo.

#### Intervalo final
Indica la hora final del intervalo.

#### 0-5
Indica la cantidad de llamadas que esperaron entre 0 y 5 segundos para ser atendidas.

#### 6-10
Indica la cantidad de llamadas que esperaron entre 6 y 10 segundos para ser atendidas.

#### 11-15
Indica la cantidad de llamadas que esperaron entre 11 y 15 segundos para ser atendidas.

#### 16-20
Indica la cantidad de llamadas que esperaron entre 16 y 20 segundos para ser atendidas.

#### 21-25
Indica la cantidad de llamadas que esperaron entre 21 y 25 segundos para ser atendidas.

#### 26-30
Indica la cantidad de llamadas que esperaron entre 26 y 30 segundos para ser atendidas.

#### 31-60 
Indica la cantidad de llamadas que esperaron entre 31 y 60 segundos para ser atendidas.

#### 61-120
Indica la cantidad de llamadas que esperaron entre 61 y 120 segundos para ser atendidas.

#### 121-180
Indica la cantidad de llamadas que esperaron entre 121 y 180 segundos 
para ser atendidas.

#### 181-240
Indica la cantidad de llamadas que esperaron entre 181 y 240 segundos 
para ser atendidas.

#### 241 ->
Indica la cantidad de llamadas que esperaron más de 241 segundos para
ser atendidas.


## Reportes de agentes conexión y desconexión
En este reporte se puntualiza toda la información referente a las estadísticas de conexión y desconexión de los agentes a la consola de trabajo. Tiene la capacidad de mostrar datos sumarizados y detallados al mismo tiempo.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Exportar consolidad
Inicia el proceso de exportación de la información mostrada de manera sumarizada en el reporte, en un archivo excel.

#### Exportar detalle
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada porel reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de agentes conexión y desconexión muestra la sumarización de los valores por cada agente y se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/6.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Conectado
Muestra un ícono que varía su color de acuerdo al estado de conexión del agente: si el agente se encuentra conectado en es instante el ícono será de color verde, si el agente se encuentra desconectado en ese instante el ícono será de color rojo.  

También el ícono es un botón que, al hacer clic sobre él, despliega una ventana informativa con el detalle de conexión y desconexión del agente seleccionado.

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/5.jpg) 
**<center> Figura 9 - Tabla de contenido(Conectado) </center>**

![Texto alternativo](/img/04-reports/02-agents/01-connection-disconnection/5-1.jpg) 
**<center> Figura 10 - Tabla de contenido(Conectado) </center>**

#### Previo
Indica si un agente se encuentra conectado desde el día anterior a la fecha actual.

#### Nombre agente
Indica el nombre del agente.

#### Cantidad
Indica la cantidad de conexiones realizadas por el agente.

#### Id agente
Indica el ID del agente.

#### Duración
Indica la cantidad de tiempo conectado del agente, expresado en formato de hora, minutos y segundos.

#### Fecha inicial
Indica el valor de la fecha inicial en el cuál hay información de 
conexión o desconexión del agente dentro del intervalo de fecha 
seleccionada. Si la información solicitada corresponde únicamente a un 
día, el valor de fecha inicial será igual al valor de fecha final.

#### Fecha final
Indica el valor de la fecha final en el cuál hay información de 
conexión o desconexión del agente dentro del intervalo de fecha 
seleccionada. Si la información solicitada corresponde únicamente a un 
día, el valor de fecha final será igual al valor de fecha inicial.

#### Hora inicial
Indica la hora en la que efectuó la primera conexión del agente para la fecha mostrada.

#### Hora final
Indica la hora en la que efectuó la última desconexión del agente para la fecha mostrada.

#### Segundos conexión
Indica la cantidad de tiempo conectado del agente, expresado en formato de segundos.

#### Id (reporte detallado)
Indica el número de identificación único del registro.

## Reportes detallado de auxiliares
En este reporte se puntualiza toda la información referente a las estadísticas de los auxiliares ejecutados por los agentes. Tiene la capacidad de mostrar datos sumarizados y detallados al mismo tiempo.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Exportar consolidad
Inicia el proceso de exportación de la información mostrada de manera sumarizada en el reporte, en un archivo excel.

#### Exportar detalle
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte detallado de auxiliares muestra la sumarización de los valores por cada agente y se estructura de la siguiente forma: 

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Conectado
Muestra un ícono que varía su color de acuerdo al estado de conexión del agente: si el agente se encuentra conectado en es instante el ícono será de color verde, si el agente se encuentra desconectado en ese instante el ícono será de color rojo.  

También el ícono es un botón que, al hacer clic sobre él, despliega una ventana informativa con el detalle de los auxiliares del agente seleccionado.

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/6.jpg) 
**<center> Figura 9 - Tabla de contenido(Conectado) </center>**

![Texto alternativo](/img/04-reports/02-agents/02-auxiliary-details/6-1.jpg) 
**<center> Figura 10 - Tabla de contenido(Conectado) </center>**

#### Previo
Indica si un agente se encuentra en auxiliar desde el día anterior a la fecha actual.

#### Nombre agente
Indica el nombre del agente.

#### Cantidad
Indica la cantidad de auxiliares realizados por el agente.

#### Id agente
Indica el ID del agente.

#### Duración
Indica la cantidad de tiempo en auxilar del agente, expresado en formato de hora, minutos y segundos.

#### Fecha inicial
Indica el valor de la fecha inicial en el cuál hay información de 
auxiliares del agente en auxiliar dentro del intervalo de fecha 
seleccionada. Si la información solicitada corresponde únicamente a un día, el valor de fecha inicial será igual al valor de fecha final.

#### Fecha final
Indica el valor de la fecha final en el cuál hay información de 
auxiliares del agente en auxiliar dentro del intervalo de fecha 
seleccionada. Si la información solicitada corresponde únicamente a un día, el valor de fecha final será igual al valor de fecha inicial.

#### Hora inicial
Indica la hora en la que el agente efectuó el primer auxiliar para la
fecha mostrada.

#### Hora final
Indica la hora en la que el agente efectuó el último auxiliar para la 
fecha mostrada.

#### Segundos conexión
Indica la cantidad de tiempo conectado del agente en auxiliar, expresado en formato de segundo.

## Reporte detallado de asignaciones
En este reporte se puntualiza toda la información referente a las estadísticas de las asignaciones realizadas por los agentes. Tiene la capacidad de mostrar datos sumarizados y detallados al mismo tiempo.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por tres (03)botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/4.jpg) 
**<center> Figura 5 - Zona de botones </center>**

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Exportar consolidad
Inicia el proceso de exportación de la información mostrada de manera sumarizada en el reporte, en un archivo excel.

#### Exportar detalle
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/4-1.jpg) 
**<center> Figura 6 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la informaciónsolicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte detallado de asignaciones, se muestra lasumarización de los valores por cada agente y se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/5.jpg) 
**<center> Figura 7 - Tabla de contenido </center>**

#### Conectado
Muestra un ícono que varía su color de acuerdo al estado de conexión del agente: si el agente se encuentra conectado en ese instante el ícono será de color verde, si el agente se encuentra desconectado en ese instante el ícono será de color rojo.  

También el ícono es un botón que, al hacer clic sobre él, despliega una ventana informativa con el detalle de las asignaciones del agente seleccionado.

![Texto alternativo](/img/04-reports/02-agents/03-assignments-detail/6.jpg) 
**<center> Figura 8 - Tabla de contenido(Conectado) </center>**

#### Previo
Indica si un agente se encuentra en asignación desde el día anterior a la fecha actual.

#### Nombre agente
Indica el nombre del agente.

#### Cantidad
Indica la cantidad de asignaciones realizadas por el agente.

#### Id agente
Indica el ID del agente.

#### Duración
Indica la cantidad de tiempo en asignación del agente, expresado en formato de hora, minutos y segundos.

#### Fecha inicial
Indica el valor de la fecha inicial en el cuál hay información de 
asignación(es) del agente dentro del intervalo de fecha seleccionada. Si la información solicitada corresponde únicamente a un día, el valor de fecha inicial será igual al valor de fecha final.

#### Fecha final
Indica el valor de la fecha final en el cuál hay información de 
asignación(es) del agente dentro del intervalo de fecha seleccionada. Si la información solicitada corresponde únicamente a un día, el valor de fecha final será igual al valor de fecha inicial.

#### Hora inicial
Indica la hora en la que efectuó la primera asignación del agente para la fecha mostrada.

#### Hora final
Indica la hora en la que efectuó la última asignación del agente para la fecha mostrada.

#### Segundos conexión
Indica la cantidad de tiempo en asignación del agente, expresado en formato de segundos.

## Reporte operativo detallado
El reporte operativo detallado muestra la información del agente referente al porcentaje de tiempo empleado en sus actividades, tomando como base el tiempo de conexión (login). Si se solicita la información por un intervalo de tiempo, aparecerá el detalle de operación de cada agente por cada día seleccionado dentro del intervalo.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido.*

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que 
facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por dos (02) botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Exportar excel
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido 
de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada por el reporte, esta información varía de acuerdo al reporte. Para el caso del reporte de detalles de operaciones se muestra el detalle de los valores por cada agente y por cada día. Este reporte se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Id agente
Indica el ID del agente.

#### Nombre agente
Indica el nombre del agente.

#### Fecha 
Indica la fecha del detalle de operación del agente.

#### Duración seg login 
Indica la cantidad de tiempo conectado (logueado) del agente,expresado en formato de segundos.

#### Duración seg llamadas atendidas 
Indica la cantidad de tiempo empleado por el agente atendiendo llamadas entrantes, expresado en formato de segundos.

#### Duración seg llamadas realizadas 
Indica la cantidad de tiempo empleado por el agente realizando llamadas salientes manuales, expresado en formato de segundos.

#### Duración seg llamadas internas 
Indica la cantidad de tiempo empleado por el agente realizando llamadas internas, expresado en formato de segundos.

#### Duración seg auxiliares
Indica la cantidad de tiempo empleado por el agente en auxiliares,expresado en formato de segundos.

#### Duración seg asignaciones
Indica la cantidad de tiempo empleado por el agente en asignaciones, expresado en formato de segundos.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/5-1.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### Duración seg disponible
Indica la cantidad de tiempo disponible del agente, expresado en 
formato de segundos.

#### Duración hms login
Indica la cantidad de tiempo conectado (logueado) del agente, expresado en formato de hora, minutos y segundos.

#### Duración hms llamadas atendidas
Indica la cantidad de tiempo empleado por el agente atendiendo 
llamadas entrantes, expresado en formato de hora, minutos y segundos.

#### Duración hms llamadas realizadas
Indica la cantidad de tiempo empleado por el agente realizando 
llamadas salientes manuales, expresado en formato de hora, minutos y 
segundos.

#### Duración hms llamadas internas
Indica la cantidad de tiempo empleado por el agente realizando 
llamadas internas, expresado en formato de hora, minutos y segundos.

#### Duración hms auxiliares
Indica la cantidad de tiempo empleado por el agente en auxiliares,minutos y segundos.

#### Duración hms asignaciones
Indica la cantidad de tiempo empleado por el agente en asignaciones, expresado en formato de hora, minutos y segundos.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/5-2.jpg) 
**<center> Figura 10 - Tabla de contenido </center>**

#### Duración hms disponible
Indica la cantidad de tiempo disponible del agente, expresado en 
formato de hora, minutos y segundos.

#### Llamadas atendidas
Indica la cantidad de llamadas atendidas por el agente.

#### Llamadas realizadas
Indica la cantidad de llamadas realizadas por el agente.

#### Llamadas internas
Indica la cantidad de llamadas internas realizadas por el agente.

#### Porcentaje duración atendidas
Indica el porcentaje de tiempo empleado por el agente atendiendo llamadas entrantes.

#### Porcentaje duración realizadas
Indica el porcentaje de tiempo empleado por el agente realizando 
llamadas salientes manuales.

#### Porcentaje duración internas
Indica el porcentaje de tiempo empleado por el agente realizando 
llamadas internas.

![Texto alternativo](/img/04-reports/03-operation/01-detailed-operating/5-3.jpg) 
**<center> Figura 11 - Tabla de contenido </center>**

#### Porcentaje auxiliares
Indica el porcentaje de tiempo en auxiliares empleado por el agente.

#### Porcentaje asignaciones
Indica el porcentaje de tiempo en asignaciones empleado por el 
agente.

#### Porcentaje disponible
Indica el porcentaje de tiempo disponible del agente.

## Reporte operativo consolidado
El reporte operativo consolidado muestra la información del agente referente al porcentaje de tiempo empleado en sus actividades, tomando como base el tiempo de conexión (login). Si se solicita la información por un intervalo de tiempo, aparecerá la sumarización de la operación de cada agente por el rango de fecha seleccionado. 
  
Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que 
facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por dos (02) botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Exportar excel
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido 
de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada porel reporte, esta información varía de acuerdo al reporte. Para el caso del reporte operativo consolidado se muestra la sumarización de los valores por cada agente y se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Id agente
Indica el ID del agente.

#### Nombre agente
Indica el nombre del agente.

#### Fecha inicio 
Indica el valor de la fecha inicial del rango de fecha seleccionado.

#### Fecha fin
Indica el valor de la fecha final del rango de fecha seleccionado.

#### Duración seg login 
Indica la cantidad de tiempo conectado (logueado) del agente,expresado en formato de segundos.

#### Duración seg llamadas atendidas 
Indica la cantidad de tiempo empleado por el agente atendiendo llamadas entrantes, expresado en formato de segundos.

#### Duración seg llamadas realizadas 
Indica la cantidad de tiempo empleado por el agente realizando 
llamadas salientes manuales, expresado en formato de segundos.

#### Duración seg llamadas internas 
Indica la cantidad de tiempo empleado por el agente realizando 
llamadas internas, expresado en formato de segundos.

#### Duración seg auxiliares
Indica la cantidad de tiempo empleado por el agente en auxiliares,expresado en formato de segundos.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/5-1.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### Duración seg asignaciones
Indica la cantidad de tiempo empleado por el agente en 
asignaciones, expresado en formato de segundos.

#### Duración seg disponible
Indica la cantidad de tiempo disponible del agente, expresado en 
formato de segundos.

#### Duración hms login
Indica la cantidad de tiempo conectado (logueado) del agente,expresado en formato de hora, minutos y segundos.

#### Duración hms llamadas atendidas
Indica la cantidad de tiempo empleado por el agente atendiendo 
llamadas entrantes, expresado en formato de hora, minutos y segundos.

#### Duración hms llamadas realizadas
Indica la cantidad de tiempo empleado por el agente realizando 
llamadas salientes manuales, expresado en formato de hora, minutos y 
segundos.

#### Duración hms llamadas internas
Indica la cantidad de tiempo empleado por el agente realizando 
llamadas internas, expresado en formato de hora, minutos y segundos.

#### Duración hms auxiliares
Indica la cantidad de tiempo empleado por el agente en auxiliares,minutos y segundos.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/5-2.jpg) 
**<center> Figura 10 - Tabla de contenido </center>**

#### Duración hms asignaciones
Indica la cantidad de tiempo empleado por el agente en asignaciones, expresado en formato de hora, minutos y segundos.

#### Duración hms disponible
Indica la cantidad de tiempo disponible del agente, expresado en 
formato de hora, minutos y segundos.

#### Llamadas atendidas
Indica la cantidad de llamadas atendidas por el agente.

#### Llamadas realizadas
Indica la cantidad de llamadas realizadas por el agente.

#### Llamadas internas
Indica la cantidad de llamadas internas realizadas por el agente.

#### Porcentaje duración atendidas
Indica el porcentaje de tiempo empleado por el agente atendiendollamadas entrantes.

#### Porcentaje duración realizadas
Indica el porcentaje de tiempo empleado por el agente realizando 
llamadas salientes manuales.

![Texto alternativo](/img/04-reports/03-operation/02-consolidated-operating/5-3.jpg) 
**<center> Figura 11 - Tabla de contenido </center>**

#### Porcentaje duración internas
Indica el porcentaje de tiempo empleado por el agente realizando 
llamadas internas.

#### Porcentaje auxiliares
Indica el porcentaje de tiempo en auxiliares empleado por el agente.

#### Porcentaje asignaciones
Indica el porcentaje de tiempo en asignaciones empleado por el 
agente.

#### Porcentaje disponible
Indica el porcentaje de tiempo disponible del agente.


## Auditoría (Audit)
El reporte de Audit o auditoría (por su traducción al castellano) puntualiza toda la información referente a las acciones de conexión, desconexión y pausas realizadas por los agentes, tal cual, como es almacenada en la base de datos. Este reporte ofrece la oportunidad al usuario de conocer el origen de los datos utilizados para la base de cálculo de todos los reportes que hacen referencia a las actividades de los agentes en la reportería ProSer.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botonesy la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/04-data/01-audit/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/04-data/01-audit/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/04-data/01-audit/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/04-data/01-audit/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/04-data/01-audit/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que 
facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por dos (02) botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/04-data/01-audit/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Exportar excel
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido 
de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/04-data/01-audit/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada, esta información varía de acuerdo al reporte. Para el caso del reporte de Audit, muestra los datos que registran la jornada de los agentes. Esta tabla se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/04-data/01-audit/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

![Texto alternativo](/img/04-reports/04-data/01-audit/6.jpg) 
**<center> Figura 9 - Tabla de contenido(Botón azul) </center>**

![Texto alternativo](/img/04-reports/04-data/01-audit/7.jpg) 
**<center> Figura 10 - Tabla de contenido(Botón azul) </center>**

#### Id
Indica la identificación del registro dentro de la base de datos.

#### Fecha
Indica la fecha de la actividad del agente asociada a ese registro.

#### Agente
Indica el nombre del agente que realizó la actividad asociada a ese registro.

#### Concepto
Indica la actividad asociada a ese registro.

#### Inicio
Indica la hora en la que inició la actividad asociada a ese registro.

#### Final
Indica la hora en la que finalizó la actividad asociada a ese registro.

#### Duración
Indica la duración de la actividad del agente asociada a ese registro. Este valor se muestra en formato de hora, minutos y segundos.

#### Duración sec.
Indica la duración, en segundos, de la actividad del agente asociada a ese registro.

![Texto alternativo](/img/04-reports/04-data/01-audit/5-1.jpg) 
**<center> Figura 11 - Tabla de contenido </center>**

#### Id Agente
Indica el ID del agente que efectuó la actividad asociada a ese 
registro.

#### Cédula
Indica el número de identificación nacional del agente que efectuó la actividad asociada a ese registro.

#### Doc. Interno
Indica el código de identificación laboral interno del agente que 
efectuó la actividad asociada a ese registro. Este campo aplica para las empresas u organizaciones que cuenten con dicha estrategia de identificación sobre su personal.

#### Supervisor
Indica el nombre del supervisor que dirige al agente que efectuó 
la actividad relacionada a ese registro.

![Texto alternativo](/img/04-reports/04-data/01-audit/5-2.jpg) 
**<center> Figura 12 - Tabla de contenido </center>**

#### Turno
Indica el turno al que pertenece el agente que efectuó la actividadrelacionada a ese registro.

#### Rol
Indica el rol que posee el agente que efectuó la actividad 
relacionada a ese registro.

#### Cliente
Indica el nombre del cliente al que fue asignado el agente que 
efectuó la actividad relacionada a ese registro.

#### Cola
Indica el nombre de la cola a la que fue asignado el agente que efectuó la actividad relacionada a ese registro.

![Texto alternativo](/img/04-reports/04-data/01-audit/5-2.jpg) 
**<center> Figura 13 - Tabla de contenido </center>**

#### Servicio
Indica el nombre del servicio al que fue asignado el agente que 
efectuó la actividad relacionada a ese registro.

## Registro de detalle de las llamadas (CDR)
Este reporte expresa la información obtenida del CDR, en él se encuentra el registro de todas las llamadas del Call Center. A diferencia del CallEntry, el CDR registra las llamadas entrantes, internas, salientes, del sistema, entre otras. El reporte ofrece la oportunidad al usuario de conocer el origen de los datos utilizados para la basede cálculo de todos los reportes que hacen referencia a todas llamadas (entrantes, salientes, internas, automáticas) en la reportería ProSer.  

Es una herramienta que proporciona al gerente o supervisor obtener los valores de las métricas de días pasados. Este reporte está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/04-data/02-cdr/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/04-data/02-cdr/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/04-data/02-cdr/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/04-data/02-cdr/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/04-data/02-cdr/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que 
facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por dos (02) botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/04-data/02-cdr/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Exportar excel
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido 
de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/04-data/02-cdr/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada, esta información varía de acuerdo al reporte. Para el caso del registro de detalle de las llamadas, muestra los datos que identifica una llamada en todos sus procesos a través del Call Center. Esta tabla se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/04-data/02-cdr/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Id
Indica la identificación del registro dentro de la base de datos.

#### Fecha
Indica la fecha de la llamada asociada a ese registro.

#### clid
Indica la identificación, en texto, del llamante asociado a la 
llamada perteneciente a ese registro.

#### src
Indica el número de identificación del llamante asociado a la 
llamada perteneciente a ese registro.

#### dst
Indica la extensión de destino de la llamada asociada a ese 
registro.

#### dcontext
Indica el contexto de destino de la llamada asociada a ese 
registro.

#### channel
Indica el nombre del canal utilizado por la llamada asociada a eseregistro.

#### dstchannel
Indica el nombre del canal de destino de la llamada asociada a 
ese registro.

#### lastapp
Indica la última aplicación que ejecutó el canal de la llamada 
asociada a ese registro.    

![Texto alternativo](/img/04-reports/04-data/02-cdr/5-1.jpg) 
**<center> Figura 9 - Tabla de contenido </center>**

#### lastdata
Indica los datos de la aplicación para la última aplicación que 
ejecutó el canal de la llamada asociada a ese registro.

#### Duración seg.
Indica la duración, en segundos, de la llamada asociada a ese 
registro.

#### Segundos facturables
Indica la cantidad de segundos facturables para la llamada asociada a 
ese registro.

#### disposition
Indica el estado final de la llamada asociada a ese registro.

#### amaflags
Indica la clasificación del CDR para una sistema externo.

#### accountcode
Indica un código de cuenta (en caso de existir) asociado al canal de la llamada.

#### uniqueid
Indica un código único de identificación de la llamada asociada a 
ese registro.

#### userfield
Indica un campo asociado al usuario configurado previamente en el canal. 

#### Grabación
Indica el directorio en el que se encuentra almacenada la grabación de la llamada asociada a ese registro.

## Registro de entrada de llamadas (CallEntry)
Es una vista que se caracteriza por expresar la información de cada llamada recibida, tal cual, como es almacenada en la base de datos. Este reporte ofrece la oportunidad al usuario de conocer el origen de los datos utilizados para la base de cálculo de todos los reportes que hacen referencia a las llamadas entrantes en la reportería ProSer.  

Está compuesto por un *menú superior, menú inferior, zona de botones* y la *tabla de contenido*.

### Menú superior 
Se encuentra ubicado en la parte superior de la ventana y en él podemos divisar: el logo de ProSer, el nombre del módulo, las opciones de las vistas que conforman el módulo, el nombre del usuario, el estado de conexión y la hora actual.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/2.jpg) 
**<center> Figura 1 - Menú Superior </center>**

### Menú inferior 
Se ubica debajo del *menú superior* y está dividido en tres (03) secciones que describen, de manera general, la vista actual. De izquierda a derecha: sección uno, sección dos y sección tres.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/3.jpg) 
**<center> Figura 2 - Menú Inferior </center>**

#### Sección uno
En esta sección del *menú inferior* encontramos la leyenda que 
representa la información expuesta en el módulo. En el orden de arriba hacia abajo, se encuentran las siguientes descripciones: Nombre de la vista del módulo, fecha de la información, rango de tiempo de la información.

#### Sección dos
Dentro de la sección dos se puntualiza el nombre del Call Center del cual hace referencia la información mostrada en la vista.

#### Sección tres
En la sección tres, al hacer clic sobre “Filtre la información aquí”, 
encontramos el *selector* de opciones. Esta funcionalidad proporciona la capacidad de filtrar, a través de un abanico de posibilidades, la 
información que se muestra en la pizarra de indicadores.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/3-1.jpg) 
**<center> Figura 3 - Menú Inferior(Sección tres) </center>**

Así como también, en esta sección se visualizará la(s) opción(es) 
seleccionada(s). El *selector* es explicado en detalle en su sección del Manual de Usuario correspondiente.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/3-2.jpg) 
**<center> Figura 4 - Menú Inferior(Sección tres) </center>**

![Texto alternativo](/img/04-reports/04-data/03-callEntry/3-3.jpg) 
**<center> Figura 5 - Menú Inferior(Sección tres) </center>**

### Zona de botones
La zona de botones se caracteriza por brindar opciones al usuario que 
facilita la transformación, actualización y exportación de la información contenida en el reporte. Esta zona se conforma por dos (02) botones y una barra de búsqueda.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/4.jpg) 
**<center> Figura 6 - Zona de botones </center>**

#### Exportar excel
Inicia el proceso de exportación de la información mostrada de manera detallada en el reporte, en un archivo excel.

#### Recalcular
Ejecuta nuevamente la consulta a la base de datos para actualizar la información, hasta ese instante, que se muestra. 

#### Barra de búsqueda
La barra de búsqueda permite al usuario hacer un filtrado rápido 
de la información expuesta en el reporte. La búsqueda se hace a través de los valores de los campos.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/4-1.jpg) 
**<center> Figura 7 - Zona de botones(Barra de búsqueda) </center>**

### Tabla de contenido
Dentro de la tabla de contenido se despliega la información solicitada, esta información varía de acuerdo al reporte. Para el caso del registro de entrada de llamadas, muestra los datos que identifica una llamada al ingresar al Call Center. Esta tabla se estructura de la siguiente forma:

![Texto alternativo](/img/04-reports/04-data/03-callEntry/5.jpg) 
**<center> Figura 8 - Tabla de contenido </center>**

#### Id
Indica la identificación del registro dentro de la base de datos.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/6.jpg) 
**<center> Figura 9 - Tabla de contenido(Id) </center>**    

![Texto alternativo](/img/04-reports/04-data/03-callEntry/6-1.jpg) 
**<center> Figura 10 - Tabla de contenido(Id) </center>**    

#### Agente
Indica el nombre del agente que atendió la llamada asociada a 
ese registro.

#### Id cola
Indica la identificación de la cola asociada a la llamada 
perteneciente a ese registro.

#### Cola número
Indica el número de la cola asociada a la llamada perteneciente a 
ese registro.

#### Entrada en cola
Indica la fecha y hora en la que la llamada asociada a ese registro ingresó en la cola.

#### Inicio
Indica la fecha y hora en la que la llamada asociada a ese registro fue atendida.

#### Final
Indica la fecha y hora en la que la llamada asociada a ese registro fue finalizada o salió de la cola sin ser atendida.

#### Duración seg.
Indica la duración, en segundos, de la llamada asociada a ese 
registro.

#### Status
Indica el estado de la llamada: “terminada” para las llamadas 
atendidas y “abandonada” para las llamadas abandonadas.

![Texto alternativo](/img/04-reports/04-data/03-callEntry/5-1.jpg) 
**<center> Figura 11 - Tabla de contenido </center>**  

#### Espera seg
Indica la duración, en segundos, que la llamada asociada a ese registro esperó en la cola para ser atendida o abandonada

#### Uniqueid
Indica un código único de identificación de la llamada asociada a ese registro.

#### Campaña
Indica la identificación de la campaña asociada a la llamada perteneciente a ese registro.

#### Trunk
Indica la troncal por la que ingres la llamada asociada al registro.

#### Fecha
Indica la fecha de la llamada asociada a ese registro.

#### Tiempo expirado

![Texto alternativo](/img/04-reports/04-data/03-callEntry/5-2.jpg) 
**<center> Figura 12 - Tabla de contenido </center>**  

#### Tipo
Indica el tipo de la llamada asociada a ese registro. Para este 
caso, el valor siempre va a ser “inbound” por ser un registro únicamente de llamadas entrantes.

#### Auto campaña
Indica el nombre de la campaña automática (en caso de haber sido configurado) a la que pertenece la llamada asociada el registro.

#### Colgada
Indica quien finalizó la llamada asociada a ese registro, colgado la
misma. En el caso que haya colgado el agente, el campo tendrá el valor “COMPLETEAGENT”. Para el caso de que haya finalizado la llamada el cliente, el campo tendrá el valor “COMPLETECALLER”.

#### Colgada agente
Indica con el valor “1” si la llamada fue colgada por el agente.

#### Colgada llamante
Indica con el valor “1” si la llamada fue colgada por el llamante o cliente.

#### Id llamante

![Texto alternativo](/img/04-reports/04-data/03-callEntry/5-3.jpg) 
**<center> Figura 13 - Tabla de contenido </center>**  

#### Llamante
Indica el número de teléfono de la persona que llama o llamante.

#### Transferido
Indica si la llamada fue transferida.