# ComposeTutorial

Actividad dirigida **Android Compose**
<br>

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



