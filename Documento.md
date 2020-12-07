### I. Visión general de la aplicación
El resultado debe seguir la siguiente lógica:

<img src="Medios\1.PNG"/>

## Tarea 1.1: Crear el proyecto con dos Activities
Cree una app con las siguientes características:

<img src="Medios\2.PNG"/>

* Cree la segunda Activity yendo al panel Project > Android y dar clic derecho sobre la carpeta app de su proyecto y dar a New > Activity > Empty Activity, nombre este activity como Segunda

<img src="Medios\8.png"/>
<img src="Medios\9.png"/>

* Use el mismo nivel de API y el lenguaje de programación Kotlin. Al final crearemos dos Activities con las siguientes características



## Tarea 1.2: Diseñando la primera Activity

Se crea el diseño de la interfaz de usuario para la aplicación Dos Actividades en el editor de diseño mediante las características ConstraintLayout.

### Detallando las propiedades del activity_main

* Abra activity_main.xml desde el panel Proyecto > Android si aún no está abierto. Si la pestaña Design (diseño) aún no está seleccionada, haga clic en ella.

<img src="Medios\5.png"/>
<img src="Medios\6.png"/>

* A continuación, se le presenta la estructura del activity, su trabajo será diseñar en base a lo mostrado, es posible que no obtenga el mismo diseño solicitado, pero se le recomienda explorar al momento de crear, es libre de diseñar a su manera, pero cuidando la estructura otorgada.

<img src="Medios\10.png"/>

Estructura del activity_main, observe que al lado del tipo de elemento se establecen los identificadores posibles, es libre de cambiar ese identificador. Luego dentro de cada elemento se muestra el posible valor del texto.

De forma generalizada, se ve que las dos pantallas agrupan las vistas usando ConstraintLayout, le corresponde diseñar con mucho empeño para obtener un buen resultado. Tenga en cuenta que los EditText se les establece la propiedad hint y no la propiedad text, en el caso de que la propiedad text disponga de algún valor establecido debe borrarse.

<img src="Medios\7.png"/>

* Establezca la propiedad visibility a invisible a los TextView del activity_main, estos serán activados en el momento en que la segunda activity le mande un resultado, en primera instancia están ocultos.

<img src="Medios\11.png"/>

* Establezca el evento onClick al botón del activity_main que tiene el identificador btEnviar, puede usar el siguiente código XML. Puede usar la corrección automática para generar el código correspondiente a este manejador de evento.

<img src="Medios\12.PNG"/>

* En el caso de que no pueda generar el método a través de las correcciones automáticas, tiene la siguiente estructura

<img src="Medios\13.PNG"/>

### Agregando un Intent al MainActivity.kt
* Abra el fichero MainActivity.kt
* Agregue un object companion dentro de la clase MainActivity, no dentro de algún método, este servirá para simular un objeto estático que no cambia el valor de sus propiedades en toda la aplicación. El valor EXTRA_MESSAGE nos servirá para la clave del extra en el intent.

<img src="Medios\14.PNG"/>

Agregue el siguiente código en el método lanzarSegundaActivity, relacionado a la creación de un intent.

<img src="Medios\15.PNG"/>

* Muestre el resultado en el momento en que la segunda activity fue lanzada
* Regrese a la activity principal e indique que instancias del ciclo de vida del activity se han ejecutado


### Tarea 1.3: Compartiendo datos de Activity principal a la segunda

En la tarea anterior, agregó un intent explícito a MainActivity que lanzó SecondActivity. También puede usar un intent para enviar datos de una activity a otra mientras la inicia.

Los extras de intent son pares clave/valor en un paquete (Bundle). Un paquete (Bundle) es una colección de datos almacenados como pares clave/valor. Para pasar información de una actividad a otra, coloque claves y valores en el paquete adicional de intención de la actividad de envío y luego vuelva a obtenerlos en la actividad de recepción.

* Agregue el siguiente código para enviar datos activities, debe reemplazar el código anterior del método lanzarSegundaActivity. Muetre los resultados

<img src="Medios\16.PNG"/>

### Modificando la segunda activity para obtener los extras
 * Abra el fichero Segunda.kt para agregar código al método onCreate()
 
 * Obtenga el intent que activó esta activity