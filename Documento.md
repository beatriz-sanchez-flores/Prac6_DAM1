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

<img src="Medios\17.PNG"/>

 * Obtenga el intent que activó esta activity

 <img src="Medios\19.PNG"/>

 * Obtenga la cadena que contiene el mensaje de los extras de Intent usando el valor del objeto creado en la activity principal y obtenerlo usando la clave MainActivity.EXTRA_MESSAGE:

 <img src="Medios\20.PNG"/>

 
 Use findViewById() para obtener la referencia del TextView para el mensaje del layout
 
 <img src="Medios\21.PNG"/>

* Establezca el texto del TextView con la cadena obtenida del extra del intent

<img src="Medios\22.PNG"/>

Ejecute la aplicación. Cuando escriba el mensaje en el MainActivity, haga clic en el botón Enviar, se lanza la SegundaActivity y se muestra el mensaje

Muestre resultados a través de capturas de pantalla y comentarios

<img src="Medios\23.jpg"/>

Acá agregue la palabra hola 

<img src="Medios\24.jpg"/>

Ya acá me muestra el texto que escribi en la primer ventana

### 1.4 Devolver datos al activity principal

Ahora que tiene una aplicación que lanza una nueva activity y le envía datos, el paso final es devolver los datos de la segunda activity a la actividad principal. También usa un intent y extras de intención para esta tarea.

### Siga los siguientes pasos:

* Abra el fichero activity_segunda.xml y verifique que dispone de la estructura indicada al principio de estas tareas con sus identificadores correspondientes.

* Establezca el evento onClick al botón con identificador btRes.

<img src="Medios\24.PNG"/>

Solamente queda crear el método devolverRespuesta(), el cual puede agregarlo después del cierre de llave del método onCreate().

<img src="Medios\25.PNG"/>

### Crear respuesta del intent en la segunda Activity

Los datos de respuesta de la segunda actividad a la actividad principal se envían en un Intent extra. Construye este intent de retorno y coloca los datos en él de la misma manera que lo hace para el intento de envío.

* Abre Segunda.kt por si aún no lo está

* Agrega un companion object para obtener una sola instancia de objeto sin necesidad de crear una nueva, esto se debe agregar después de la apertura de la llave de la clase Segunda, al inicio para no generar confusiones

<img src="Medios\26.PNG"/>

* Agregue el código del método devolverRespuesta() creado en la tarea anterior

<img src="Medios\27.PNG"/>

### Tarea 1.5: Obtener la respuesta en el MainActivity y mostrarlo en el TextView

Cuando usa un intent explícito para iniciar otra activity, es posible que no espere recuperar ningún dato; solo está activando esa actividad. En ese caso, use startActivity() para iniciar la nueva activity como lo hizo anteriormente en esta práctica. Sin embargo, si desea recuperar datos de la activity activada, debe iniciarla con startActivityForResult().

En esta tarea, modifica la aplicación para iniciar Segunda Activity esperando un resultado, para extraer los datos devueltos del Intent y para mostrar esos datos en los elementos TextView que creó en la última tarea.

* Abra el fichero de MainActivity.kt
* Borre o comente la línea de startActivity(intent) a startActivityForResult(intent, TEXT_REQUEST), recuerde que TEXT_REQUEST está dentro del companion object

<img src="Medios\28.PNG"/>

Pasaremos a anular el método onActivityResult(), vamos a Code > Override methods o simplemente CTRL + O, busque el método onActivityResult()

<img src="Medios\29.png"/>

* Agregue el siguiente código a este método para obtener el extra y establecer en el TextView indicado para esto que se identifica con datoRecibido.

<img src="Medios\30.PNG"/>

* Ahora cuando envíes datos de la segunda Activity hacia la principal, deberías de obtener el mensaje.

<img src="Medios\33.jpg"/>

### Tarea 1.6: Crear el activity de Scrolling

Muestra el componente de interfaz de usuario de ScrollView. ScrollView es un ViewGroup que en este ejemplo contiene un TextView. Muestra una página de texto larga, en este caso, una reseña de un álbum de música, que el usuario puede desplazarse verticalmente para leer deslizando el dedo hacia arriba y hacia abajo. Aparece una barra de desplazamiento en el margen derecho. La aplicación muestra cómo puede usar texto formateado con etiquetas HTML mínimas para configurar el texto en negrita o cursiva, y con caracteres de nueva línea para separar párrafos. También puede incluir enlaces web activos en el texto.

* Agregue un nuevo Activity dando clic derecho en la carpeta app o en res en el proyecto

<img src="Medios\31.PNG"/>

### Estructura del Activity Scrolling:

<img src="Medios\33.PNG"/>

* El texto es aleatorio, puede usar alguno de Wikipedia o un generador de texto, pero debe cumplir con un título del artículo, un subtítulo, Texto con saltos de línea

* Es opcional agregar el botón regresar, pero para pruebas puede agregarlo y generar su manejador del evento clic y mandar a llamar al método finish(), para que observe que puede manipular el regreso, aunque también lo puede hacer con el botón de retroceso

* Deslícese hacia arriba y hacia abajo para desplazarse por el artículo y observe que el subtítulo ahora se desplaza junto con el artículo mientras el título permanece en su lugar. Esto se debe a que el título está fuera del ScrollView

<img src="Medios\33.PNG"/>

<img src="Medios\34.jpg"/>

### Tarea 1.7: Agregue un Activity Aritmética

Con este Activity se pondrá a prueba todo lo aprendido hasta el momento, constará de dos EditText, de los cuales tomará sus valores, los convertirá a entero y obtendrá la suma de estos dos valores, los cuales serán mostrados mediante un Toast y en un TextView. Esta Activity estará conectada a la Segunda Activity, la cual será llamada desde el botón Sumar.

* Agregue un nuevo Activity , yendo a la carpeta res, haga clic derecho sobre ella e ir a New> Activity> Empty Activity 

<img src="Medios\36.png"/>
<img src="Medios\37.png"/>

* Utilizar la estructura mostrada con anterioridad, agregando los elementos necesarios con sus identificadores correspondientes

* Obtenga la instancia del Button usando el método findViewById () .

* Cree el método realizarSuma () y establezca el resultado de la suma en la propiedad text de etResultadoSuma

* Debe agregar un item de string en strings.xml llamado resultado_aritmetica, debe contener el valor: El resultado es

* Ejecute la aplicación y explique los resultados obtenidos

<img src="Medios\35.jpg"/>

