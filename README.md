# ComposeTutorial

Actividad dirigida **Android Compose**
<br>

![perrito](https://media0.giphy.com/media/Dh5q0sShxgp13DwrvG/giphy.gif?cid=ecf05e47tz0icr4ojj10v3ce4wrfj9t1iwsn9yhlh1jgwwvm&ep=v1_gifs_search&rid=giphy.gif&ct=g)

## Composable Functions
### PASO 1

Omitiendo los pasos de la creacion del proyecto, el primer paso es agregar un elemento de texto en el metodo *´onCreateView´*
<br><br>
Code
<br>
```kotlin
class MainActivity : ComponentActivity() {
   override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContent {
        Text("Hello World")
    }
   }
}
```
<br><br>
Preview
<br>
![PASO 1 PREVIEW](https://github.com/Jiza18/ComposeTutorial/assets/113170616/73c8f615-6a57-478f-a92a-dc4c33e0e809)
<br><br>
### PASO 2

El segundo paso a seguir en el tutoria es definir una funcion de componibilidad utilizando la etiqueta *´@Composable´*
<br><br>
Code
<br>
```kotlin
@Composable
fun MessageCard(name: String) {
    Text(text = "Hello $name!")
}
```
<br><br>

### PASO 3
En el siguiente paso usamos la etiqueta *'@Preview'* para obtener una vista previa de una función sin necesidad de emular un dispositivo.
<br><br>
Code
```kotlin
@Preview
@Composable
fun PreviewMessageCard() {
    MessageCard("Android")
}
```
<br><br>
Preview
<br><br>
![PASO 3 VIEW](https://github.com/Jiza18/ComposeTutorial/assets/113170616/009c14ea-bebf-4fae-8767-cdd2507e933b)
<br><br>
## Layouts
### PASO 1
En este paso modificamos la funcion *'MessageCard'* para que reciba como parametro un objeto *Message* en vez de un *String*, luego definir este objeto para poder colocar mas contenido dentro del mensaje.
<br><br>
Code
```kotlin
data class Message(val author: String, val body: String)

@Composable
fun MessageCard(msg: Message) {
    Text(text = msg.author)
    Text(text = msg.body)
}
```
<br><br>
## PASO 2
En este caso organizamos el contenido de el mensaje con la funcion *'Column'* que te permite organizar elementos de forma vertical.
<br><br>
Code
```kotlin
@Composable
fun MessageCard(msg: Message) {
    Column {
        Text(text = msg.author)
        Text(text = msg.body)
    }
}
```
<br><br>
Preview
<br><br>
![PASO 2 (2)](https://github.com/Jiza18/ComposeTutorial/assets/113170616/603458ac-a002-4bae-bdc1-fd2d85480c0a)
<br><br>

### PASO 3
En este paso agregamos un elemeto de imagen usando el *Resource Manager* que nos ofrece el IDE de **Android Studio** para importarla desde nuestra biblioteca y dentro de un elemento *'Row'* agregamos el codigo de la imagen junto a la columna con el texto para que quede el contenido bien estrucuturado.
<br><br>

Code

```kotlin
@Composable
fun MessageCard(msg: Message) {
    Row {
        Image(
            painter = painterResource(R.drawable.profile_picture),
            contentDescription = "Que bonita esta la asiatica",
        )
    
       Column {
            Text(text = msg.author)
            Text(text = msg.body)
        }
  
    }
  
}
```
<br><br>
Preview
<br><br>
![PASO 3 (3)](https://github.com/Jiza18/ComposeTutorial/assets/113170616/4a099f7d-4221-4784-90ae-367c453284d3)
<br><br>

### PASO 4
En este paso usamos modificadores de Compose para cambiar el diseño de nuestra imagen, ya que puede esta bien estructurado el mensaje pero las dimensiones de la imagen pueden ser demasiado grandes. NOTA: en este paso tuve algunos inconvenientes con algunas variables del tutorial que en mi version de android studio no me permitia utilizar.
<br><br>
Code
```kotlin
@Composable
fun MessageCard(msg: Message) {
    Row(modifier = Modifier.padding(all = 8.dp)) {
        Image(painter = painterResource(R.drawable.profile_picture),
            contentDescription = "Que bonita esta la asiatica",
            modifier = Modifier
                .size(40.dp)
                .clip(CircleShape)
                .border(1.5.dp, MaterialTheme.colorScheme.secondary, CircleShape)
        )

        Spacer(modifier = Modifier.width(8.dp))

         Column {
            Text(text = msg.author)
            Spacer(modifier = Modifier.height(4.dp))
            Text(text = msg.body)
        }
    }
}
```
<br><br>
Preview
<br><br>
![PASO 4 (2)](https://github.com/Jiza18/ComposeTutorial/assets/113170616/36f61367-51ec-42bc-b08a-790134c08e33)
<br><br>

## Material Desing
### PASO 1
En esta sección empezamos a dar diseño y estilo a nuestra aplicación, por lo tanto en este paso unimos nuestra funcion *'MessageCard'* con el tema de nuestro proyecto e implementamos un elemento *'Surface'*. Esto hace que los elementos hereden estilos del tema de la app y conservar la coherencia entre del estilo de la aplicación.

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            ComposeTutorialTheme {
                Surface(modifier = Modifier.fillMaxSize()) {
                    MessageCard(Message("Jose Miguel", "Compose Tutorial"))
                }
            }
        }
    }
}

@Preview
@Composable
fun PreviewMessageCard() {
    ComposeTutorialTheme {
        Surface {
            MessageCard(msg = Message("Algo", "De puerba"))
        }
    }
}
```
<br><br>
### PASO 2
En este paso usamos la libreria *'MaterialThemes.color'*
para aplicar colores con la paleta del tema del proyecto. NOTA: en este paso tuve invonvenientes con alguna variables de la libreria, por lo tanto, trate de conseguir el mismo resultado, pero con variables diferentes a las del tutorial.
<br><br>
Code
```kotlin
@Composable
fun MessageCard(msg: Message) {
   Row(modifier = Modifier.padding(all = 8.dp)) {
       Image(
           painter = painterResource(R.drawable.profile_picture),
           contentDescription = "Que bonita esta la asiatica",
           modifier = Modifier
               .size(40.dp)
               .clip(CircleShape)
               .border(1.5.dp, MaterialTheme.colorScheme.secondary, CircleShape)
       )

       Spacer(modifier = Modifier.width(8.dp))

       Column {
           Text(text = msg.author,)
           Spacer(modifier = Modifier.height(4.dp))
           Text(text = msg.body)
       }
   }
}
```
<br><br>
### PASO 3
NOTA: en este paso el tutorial propone perzonalizar la tipografía del texto pero no logre hacerlo porque en mi version de Android Studio, no funcionaban esas referencias a la libreria.

### PASO 4
En este paso unimos el cuerpo del texto del mensaje con un elemento *'Surface'* y agregamos el *'Shape'* que nos permite personalizar la forma y el cuerpo del mensaje. En este caso indicamos que si se expande el mensaje muestra todo el contenido, de no ser asi, solo mostrara una linea.

```kotlin
Surface(
            shape = MaterialTheme.shapes.medium,
        ){
            Text(text = msg.body,
                modifier = Modifier.padding(all = 4.dp),t
                maxLines = if (isExpanded) Int.MAX_VALUE else 1)
        }
```

### PASO 5
En este paso habilitamos el tema oscuro de nuestra aplicación. Jetpack Compose es capaz de hacerlo de forma predeterminada.
<br><br>
Code
```kotlin
@Preview(name = "Light Mode")
@Preview(
    uiMode = Configuration.UI_MODE_NIGHT_YES,
    showBackground = true,
    name = "Dark Mode"
)
```
<br><br>
Preview
<br><br>
![preview dark mode](https://github.com/Jiza18/ComposeTutorial/assets/113170616/de20460f-95d5-461e-a227-9ec2ae1a0777)
<br><br>
## List and Animations
### PASO 1
En esta sección implementamos una lista y animaciones para nuestra aplicación. Creamos una función *'Conversation'* para mostrar varios mensajes. Usamos un elemento nuevo LazyColumn, es un elemento de Compose que renderiza objetos visibles en la pantalla, especialmente diseñado para listas largas. Ademas agregamos contenido a la aplicacion con una lista de mensajes que nos proporciona el tutorial.
<br><br>
Code
```kotlin
@Composable
fun Conversation(messages: List<Message>) {
    LazyColumn {
        items(messages) { message ->
            MessageCard(message)
        }
    }
}
@Preview
@Composable
fun PreviewConversation() {
    ComposeTutorialTheme {
        Conversation(SampleData.conversationSample)
    }
}
```
<br><br>
Preview
<br><br>
**Sin expandir**
<br>
![a1](https://github.com/Jiza18/ComposeTutorial/assets/113170616/0f23efdf-350e-4281-ac61-13c989539593)
<br><br>
**Expandido**
<br>
![a2](https://github.com/Jiza18/ComposeTutorial/assets/113170616/b2507717-70d1-45f5-8e4c-12958811c106)
<br><br>
### PASO 2
Por ultimo agregamos animaciones a las tarjetas de conversación desplegables. NOTA: en este paso tambien tuve problemas y solo consegui una animación.
<br><br>
![a2](https://github.com/Jiza18/ComposeTutorial/assets/113170616/b2507717-70d1-45f5-8e4c-12958811c106)

## FIN
Las definiciones redactadas, es lo que pude interpretar de cada paso de la actividad.
<br>
Repositorio diseñado con Markdown - Jose Miguel Izarra©.
<br>
![gatito](https://media.tenor.com/1NRoxR1fXngAAAAi/hug-cat.gif)
