    Gestor de Tareas — Backend + Frontend
#   -------------------------------------     #

Este es un proyecto sencillo que busca crear, editar, eliminar y por supuesto editar tareas, diferenciandolas por tres estados (Pendiente, En progreso y Completadas) y ademas de esto tambien por color, tiene un gran punto que se utiliza SharedPreference con el fin de poder identificar el dispotivio (Su id que se almacena localmente desde el frontend y se envia al backend) y que este sin necesidad de tener una sesion iniciada me permita solo listar las tareas de ese usuario.


#   -----------------------------    #
    Backend - Nestjs + PostgreSQL
#   -----------------------------    #
URL desplegado:

REQUISITOS PREVIOS
1. Node.js >= 18
2. PostgreSQL instalado y en ejecución
3. Nest CLI (npm i -g @nestjs/cli)
4. Tener configurado un usuario y base de datos en PostgreSQL


CONFIGURACION INICIAL
(Aunque el backend lo cree en esta ruta https://github.com/SantiagoBoS/backend_task_manager inicialmente, se puede descargar como la estructura que se dia para entrega de la prueba)
1. git clone https://github.com/SantiagoBoS/proyecto-tareas
2. cd server
3. npm install (Para instalar las depencias)
4. IMPORTANTE, hay que crear el archivo .env en la raiz para la conexion a la base de datos, ejemplo:
    DB_HOST=localhost
    DB_PORT=5432
    DB_USERNAME=postgres
    DB_PASSWORD=tu_password
    DB_NAME=task_manager
5. Y para ejecutar el proyecto, el siguiente comando: "npm run start"


ESTRUCUTRA DE LOS MODULOS PRINCIPALES
1. Task Entity: Define los campos: id, title, description, status, deviceId.
2. DTOs:
    - CreateTaskDto: valida que el titulo no este vacio y que el estado sea valido.
    - UpdateTaskDto: permite actualizar solo campos opcionales, sin borrar información previa.
3. TasksService:
    - findAll(deviceId): lista tareas filtradas por dispositivo.
    - create(data): crea nueva tarea.
    - update(id, data): actualiza solo campos enviados, conservando valores previos.
    - delete(id, deviceId): elimina una tarea especifica de un dispositivo.
4. TasksController:
    GET /tasks/:deviceId
    POST /tasks
    PUT /tasks/:id
    DELETE /tasks/:id/:deviceId


# ------------------------------------------------------------------------------------- #
# ------------------------------------------------------------------------------------- #


#   -------------------------    #
    Frontend - Flutter y Dart
#   -------------------------    #
URL desplegado:

REQUISITOS PREVIOS
1. Flutter SDK instalado (flutter doctor)
2. Android Studio
3. Emulador Android
4. (Aunque el frontend lo cree en esta ruta https://github.com/SantiagoBoS/frontend_task_manager inicialmente, se puede descargar como la estructura que se dia para entrega de la prueba)
   - git clone https://github.com/SantiagoBoS/proyecto-tareas
   - cd mobile
5. Paquete http y shared_preferences instalados: 
    - Importante que se encuentren estan dependencias:
        - dependencies:
            flutter:
                sdk: flutter
            http: ^0.13.6
            shared_preferences: ^2.2.2
6. Manera de poderlo ejecutar: 
   - Verificar que se haya seleccionado algun dispositivo en el emulador de android studio
   - flutter run


FUNCIONALIDAES IMPLEMENTADAS
1. Listar tareas: usando FutureBuilder con un ListView.separated
2. Crear tarea: botón flotante (FloatingActionButton.extended) siempre visible en la parte inferior derecha
3. Editar tarea: icono de lapiz en cada tarea, abre modal con datos prellenados
4. Eliminar tarea: icono de papelera con confirmación modal (showDialog)
5. Colores dinamicos:
    - pending: gris claro
    - in_progress: amarillo claro
    - completed: verde claro
6. Traducción de estados:
    - pending: "Pendiente"
    - in_progress: "En progreso"
    - completed: "Completada"
7. Mensajes y validaciones:
    - Formulario con TextFormField y validaciones de campos
    - SnackBar para notificaciones de éxito o error
8. Soporte offline por dispositivo:
    - Las tareas estan ligadas al deviceId, por lo que no se mezclan con otros dispositivos


# ------------------------------------------------------------------------------------- #
# ------------------------------------------------------------------------------------- #


#   ---------------------------------    #
    IMAGENES DEL PROCESO DE EJECUCION
#   ---------------------------------    #
Link al google drive: https://drive.google.com/drive/folders/14rC37qDdhlwO5omn6384rVdoLyEv86vD?usp=sharing