# UNIDAD-4-BASE-DE-DATOS-EJERCICIO-9
1. ¿Qué sistema representa?
La base de datos permite administrar una plataforma educativa virtual.

En este sistema:
- Los instructores crean y ofrecen cursos.
- Los estudiantes se registran en la plataforma.
- Los estudiantes pueden inscribirse en diferentes cursos.
- Cada curso contiene módulos.
- Cada módulo contiene lecciones.
- Los cursos pueden tener evaluaciones.
- Las evaluaciones contienen preguntas.
- Los estudiantes realizan intentos para resolver las evaluaciones y obtienen calificaciones.
La finalidad es organizar toda la información de una plataforma de aprendizaje en un único sistema de base de datos.
2. Explicación de las 9 tablas
La base de datos está formada por nueve tablas. Cada una almacena información de una parte específica del sistema.
Tabla 1: INSTRUCTOR
Datos de los profesores
Esta tabla almacena la información de las personas encargadas de crear e impartir los cursos.
Campo	Explicación
id_instructor	Identificador único del instructor.
nombre	Nombre del instructor.
apellido	Apellido del instructor.
biografia	Descripción de su trayectoria o experiencia.
especialidad	Área de conocimiento en la que se especializa.
datos_contacto	Información para comunicarse con el instructor.

Ejemplo práctico:

Un instructor podría ser Juan Pérez, especializado en programación, con experiencia en desarrollo de software.

Su identificador podría ser INS01.

¿Por qué existe esta tabla?

Porque necesitamos guardar los datos de cada profesor una sola vez, sin repetir su información en todos los cursos que imparte.
Tabla 2: CURSO
Información de los cursos
Esta tabla almacena los cursos disponibles en la plataforma.
Campo	Explicación
id_curso	Identificador único del curso.
titulo	Nombre del curso.
duracion	Duración estimada del curso.
precio	Precio del curso.
nivel_dificultad	Nivel: principiante, intermedio o avanzado, por ejemplo.
id_instructor	Identificador del instructor que imparte el curso.

Ejemplo práctico:

Un curso podría tener los siguientes datos:
- Código: CUR01.
- Título: Introducción a la programación.
- Duración: 30 horas.
- Precio: $25.000.
- Nivel: Principiante.
- Instructor: INS01.
Relación con INSTRUCTOR

La columna id_instructor funciona como clave foránea (FK).

Esto significa que permite identificar qué instructor está asociado a cada curso.

La relación es:
- Un instructor puede impartir varios cursos.
- Cada curso está asociado a un instructor.
Por lo tanto, es una relación de uno a muchos (1:N).
Tabla 3: ESTUDIANTE
Datos de los alumnos
Esta tabla almacena los datos personales de los estudiantes que utilizan la plataforma.
Campo	Explicación
id_estudiante	Identificador único del estudiante.
telefono	Número de teléfono.
nombre	Nombre del estudiante.
apellido	Apellido del estudiante.
dni	Documento Nacional de Identidad.
correo	Dirección de correo electrónico.

Ejemplo práctico:

Un estudiante se registra con:
- ID: EST01.
- Nombre: Ana.
- Apellido: Gómez.
- DNI: 40123456.
- Teléfono: 2614010101.
- Correo: ana@gmail.com.
¿Por qué se separa esta tabla de CURSO?

Porque un estudiante puede realizar diferentes cursos y un curso puede tener muchos estudiantes.

No sería conveniente repetir los datos personales del estudiante cada vez que se inscribe.
Tabla 4: INSCRIPCION
Registro de inscripciones
Esta tabla es fundamental porque permite registrar qué estudiante se inscribió en qué curso.
Campo	Explicación
id_inscripcion	Identificador único de la inscripción.
fecha	Fecha en la que se realizó la inscripción.
id_estudiante	Estudiante que se inscribe.
id_curso	Curso al que se inscribe.

Ejemplo práctico:

Ana Gómez se inscribe en el curso de programación el 25/11/2026.

La inscripción podría contener:
Campo	Valor
id_inscripcion	INS001
fecha	2026-11-25
id_estudiante	EST01
id_curso	CUR01

¿Por qué existe esta tabla?

Porque resuelve una relación muchos a muchos (N:M).

Veamos:
- Un estudiante puede inscribirse en muchos cursos.
- Un curso puede tener muchos estudiantes.
Para resolver esta relación se crea una tabla intermedia llamada INSCRIPCION.

Esta tabla conecta ambas entidades mediante dos claves foráneas.
Tabla 5: MODULO
Organización del contenido
Esta tabla permite dividir un curso en diferentes módulos o unidades temáticas.
Campo	Explicación
id_modulo	Identificador único del módulo.
titulo	Nombre del módulo.
numero_orden	Posición del módulo dentro del curso.
id_curso	Curso al que pertenece el módulo.

Ejemplo práctico:

Un curso llamado Introducción a la programación podría dividirse en:
1. Introducción a los algoritmos.
2. Variables y tipos de datos.
3. Estructuras condicionales.
4. Estructuras repetitivas.
Cada uno de esos temas puede almacenarse como un módulo.

Relación con CURSO

La columna id_curso es una clave foránea.

La relación es de uno a muchos (1:N):
- Un curso puede contener varios módulos.
- Cada módulo pertenece a un curso.
Tabla 6: LECCION
Contenido de aprendizaje
Esta tabla almacena las lecciones que forman parte de cada módulo.
Campo	Explicación
id_leccion	Identificador único de la lección.
titulo	Nombre de la lección.
contenido	Descripción o contenido de la lección.
duracion	Tiempo estimado de la lección.
tipo	Tipo de contenido, por ejemplo, video o texto.
id_modulo	Módulo al que pertenece la lección.

Ejemplo práctico:

Dentro del módulo Variables y tipos de datos podríamos tener:
- Lección 1: ¿Qué es una variable?
- Lección 2: Tipos de datos.
- Lección 3: Declaración de variables.
- Lección 4: Ejemplos prácticos.
Relación con MODULO

Es una relación uno a muchos (1:N):
- Un módulo puede contener varias lecciones.
- Cada lección pertenece a un módulo.
Tabla 7: EVALUACION
Evaluaciones de los cursos
Esta tabla permite registrar las evaluaciones que tiene cada curso.
Campo	Explicación
id_evaluacion	Identificador único de la evaluación.
tipo	Tipo de evaluación.
id_curso	Curso al que pertenece la evaluación.

Ejemplo práctico:

Un curso de programación puede tener:
- Evaluación 1: Cuestionario teórico.
- Evaluación 2: Evaluación práctica.
- Evaluación 3: Examen final.
Cada evaluación tiene un identificador propio.

Relación con CURSO

Es una relación uno a muchos (1:N):
- Un curso puede tener varias evaluaciones.
- Cada evaluación pertenece a un curso.
Tabla 8: PREGUNTAS
Preguntas de las evaluaciones
Esta tabla almacena las preguntas que forman parte de cada evaluación.
Campo	Explicación
id_pregunta	Identificador único de la pregunta.
enunciado	Texto de la pregunta.
opciones	Opciones disponibles para responder.
respuesta_correcta	Respuesta correcta de la pregunta.
id_evaluacion	Evaluación a la que pertenece la pregunta.

Ejemplo práctico:

Evaluación: Introducción a la programación.

Pregunta:

¿Qué es una variable?

Opciones:
- A) Un espacio de memoria.
- B) Un programa completo.
- C) Un lenguaje de programación.
Respuesta correcta: A.

Relación con EVALUACION

Es una relación uno a muchos (1:N):
- Una evaluación puede tener varias preguntas.
- Cada pregunta pertenece a una evaluación.
Tabla 9: INTENTO_RESOLUCION
Resultados de los estudiantes
Esta tabla registra los intentos que realizan los estudiantes para resolver las evaluaciones.
Campo	Explicación
id_intento	Identificador único del intento.
fecha_intento	Fecha en que se realizó el intento.
calificacion	Nota obtenida por el estudiante.
estado	Estado del intento, por ejemplo, aprobado o desaprobado.
id_estudiante	Estudiante que realizó el intento.
id_evaluacion	Evaluación que resolvió.
id_curso	Curso al que corresponde el intento.

Ejemplo práctico:

Ana Gómez realiza una evaluación del curso de programación.

Obtiene una calificación de 8 y su estado es aprobado.

El registro podría ser:
Campo	Valor
id_intento	INT001
fecha_intento	2026-11-25
calificacion	8
estado	Aprobado
id_estudiante	EST01
id_evaluacion	EVA01
id_curso	CUR01

¿Por qué es importante esta tabla?

Porque permite llevar un historial de los resultados de los estudiantes.

Por ejemplo, si un estudiante realiza tres intentos de una misma evaluación, se pueden guardar los tres resultados por separado.

3. ¿Qué son las claves primarias (PK)?
En el archivo, todas las tablas tienen una clave primaria.

La clave primaria es un campo que identifica de manera única cada registro de una tabla.

Por ejemplo, en ESTUDIANTE:
id_estudiante (PK)	nombre	apellido
EST01	Ana	Gómez
EST02	Bruno	Díaz
EST03	Carla	Pérez

La clave primaria evita que dos registros tengan el mismo identificador.

En tu archivo, las claves primarias son:
Tabla	Clave primaria
INSTRUCTOR	id_instructor
CURSO	id_curso
ESTUDIANTE	id_estudiante
INSCRIPCION	id_inscripcion
MODULO	id_modulo
LECCION	id_leccion
EVALUACION	id_evaluacion
PREGUNTAS	id_pregunta
INTENTO_RESOLUCION	id_intento
<img width="1206" height="365" alt="image" src="https://github.com/user-attachments/assets/6b74a899-3589-4177-9c79-a659763cc698" />
