La forma más eficaz de evitar vulnerabilidades de recorrido de ruta es evitar por completo pasar la entrada proporcionada por el usuario a las API del sistema de archivos. Muchas funciones de aplicación que hacen esto se pueden reescribir para ofrecer el mismo comportamiento de una manera más segura.

Si no puede evitar pasar la entrada proporcionada por el usuario a las API del sistema de archivos, le recomendamos utilizar dos capas de defensa para evitar ataques:

- Valide la entrada del usuario antes de procesarla. Lo ideal es comparar la entrada del usuario con una lista blanca de valores permitidos. Si eso no es posible, verifique que la entrada contenga solo contenido permitido, como caracteres alfanuméricos únicamente.
- Después de validar la entrada suministrada, agregue la entrada al directorio base y use una API del sistema de archivos de la plataforma para canonizar la ruta. Verifique que la ruta canonizada comience con el directorio base esperado.

A continuación se muestra un ejemplo de un código Java simple para validar la ruta canónica de un archivo según la entrada del usuario:

`File file = new File(BASE_DIRECTORY, userInput); if (file.getCanonicalPath().startsWith(BASE_DIRECTORY)) { // process file }`