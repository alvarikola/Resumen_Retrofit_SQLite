# Retrofit
![retrofit](image-2.png)
## Cómo agregar dependencias de Retrofit
### Android Gradle te permite agregar bibliotecas externas a tu proyecto. Además de la dependencia de la biblioteca, también debes incluir el repositorio en el que se aloja.

1. Abre el archivo de Gradle de nivel de módulo build.gradle.kts (Module :app).
2. En la sección dependencies, agrega las siguientes líneas para las bibliotecas Retrofit:

    1. // Retrofit  
    `implementation("com.squareup.retrofit2:retrofit:2.9.0")`
    2. // Retrofit with Scalar Converter
    `implementation("com.squareup.retrofit2:converter-scalars:2.9.0")`

### Las dos bibliotecas funcionan juntas. La primera dependencia es para la biblioteca Retrofit2 y la segunda es para el conversor escalar de Retrofit. Retrofit2 es la versión actualizada de la biblioteca de Retrofit. Este conversor escalar permite que Retrofit muestre el resultado JSON como String. JSON es un formato para almacenar y transportar datos entre el cliente y el servidor.

## Cómo usar retrofit

### Retrofit convierte tu HHTP API en una interfaz de java

    interface ApiServiceJsonPlaceholder {

        @GET("/albums") 
        suspend fun getAlbums(): Response<List<AlbumsDataResponse>> 
    
    }

    //  la función getAlbums() realizará una solicitud HTTP de tipo GET a la URL /albums.

    // La función getAlbums devuelve un objeto de tipo Response, que es una envoltura proporcionada por Retrofit para manejar tanto el contenido de la respuesta como los posibles errores (código de estado, excepciones, etc.). El cuerpo de la respuesta es de tipo List<AlbumsDataResponse>, lo que indica que esperamos que el servidor nos devuelva una lista de objetos.

    // Response es un tipo genérico que tiene dos partes importantes:

        isSuccessful: Si la solicitud fue exitosa (código HTTP 200-299).

        body(): Si la respuesta fue exitosa, este método devuelve el cuerpo de la respuesta (en este caso, una lista de objetos de tipo AlbumsDataResponse).
<br>

    data class AlbumsDataResponse(
        @SerializedName("userId") val userID: String,
        @SerializedName("id") val id: String,
        @SerializedName("title") val title: String,
    )

    // Este es un data class de Kotlin que representa los datos de cada álbum que se obtiene de la respuesta de la API.

    // @SerializedName: Esta anotación proviene de la librería Gson y se usa para mapear el nombre de un campo en el JSON que se recibe desde la API a un nombre de propiedad en el data class


