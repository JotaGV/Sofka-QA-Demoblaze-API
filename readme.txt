EJERCICIO 2 - PRUEBAS DE API DEMOBLAZE CON POSTMAN

DESCRIPCIÓN
Este ejercicio valida cuatro escenarios de las API de registro e inicio de sesión de Demoblaze, utilizando Postman. Las solicitudes incluyen comprobaciones automáticas del código HTTP y del contenido de la respuesta.

REQUISITOS
Postman (aplicación de escritorio o versión web con un agente capaz de enviar las solicitudes), conexión a Internet y el archivo JSON de la colección exportada desde Postman.

ARCHIVOS DE LA ENTREGA
- Colección de Postman en formato JSON, exportada desde la colección "Sofka QA - Demoblaze API".
- readme.txt: instrucciones de ejecución.
- conclusiones.txt: resultados, hallazgos y limitaciones.

INSTRUCCIONES DE EJECUCIÓN
1. Descargar el archivo JSON de la colección desde este repositorio.
2. Abrir Postman y seleccionar Import. Importar el archivo JSON descargado.
3. Abrir la colección "Sofka QA - Demoblaze API" y comprobar que contiene las cuatro solicitudes de registro y autenticación.
4. En cada solicitud, comprobar que el método sea POST, que el encabezado Content-Type sea application/json y que el Body esté configurado como raw / JSON.
5. Para la prueba de registro exitoso, sustituir el valor de username por uno que no haya sido registrado anteriormente. Demoblaze conserva los usuarios registrados y devolverá un error de duplicidad si se repite el nombre.
6. Ejecutar cada solicitud con Send y consultar Scripts / Post-response y Test Results para revisar las validaciones automáticas.
7. Ejecutar el registro de usuario existente utilizando un nombre ya registrado, como el creado en el paso 5. Para el inicio de sesión correcto, utilizar un usuario registrado y su contraseña correspondiente. Para el inicio de sesión incorrecto, utilizar credenciales inválidas.
8. Confirmar que las dos comprobaciones de cada solicitud aparezcan como PASSED. Registrar cualquier resultado distinto para su análisis.

ESCENARIOS Y RESULTADOS ESPERADOS
1. Registro de usuario nuevo: POST https://api.demoblaze.com/signup. Se espera HTTP 200 y una respuesta JSON de cadena vacía ("").
2. Registro de usuario existente: POST https://api.demoblaze.com/signup. Se espera HTTP 200 y errorMessage igual a "This user already exist."
3. Inicio de sesión válido: POST https://api.demoblaze.com/login. Se espera HTTP 200 y una respuesta de texto que incluya "Auth_token:".
4. Inicio de sesión inválido: POST https://api.demoblaze.com/login. Se espera HTTP 200 y errorMessage igual a "Wrong password." o "User does not exist.", según las credenciales utilizadas.

ALCANCE
La implementación se limita a las cuatro solicitudes solicitadas y sus validaciones básicas en Postman. No se incluyen ejecución programada, integración continua, pruebas de carga ni comprobación criptográfica del token. La solicitud de registro exitoso requiere un usuario nuevo en cada repetición.
