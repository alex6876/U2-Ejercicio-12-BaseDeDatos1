# Ejercicio — Base de Datos de Gestión de Red Social (Publicaciones, Interacciones y Seguimiento)



Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para una plataforma de red social, administrando cuentas de usuario, relaciones de seguimiento, publicaciones multimedia, comentarios, respuestas, reacciones y etiquetas o hashtags.

---

## Descripción

El sistema modela una estructura de datos relacional para la gestión de interacciones dentro de una red social estilo plataforma de contenido multimedia. Permite la creación y perfilado de usuarios, el establecimiento de vínculos de seguimiento (seguidor/seguido), la publicación de contenidos con descripción e imagen, la categorización mediante etiquetas o hashtags, la interacción a través de comentarios y respuestas en hilo, así como la asignación de reacciones sobre publicaciones o comentarios.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* Usuario:


* id_username: Clave primaria única que identifica a la cuenta de usuario.


* fecha_alta: Fecha de creación o registro del usuario.


* correo electronico: Dirección de correo electrónico asociada.


* contraseña: Clave de acceso o autenticación.


* biografia: Texto descriptivo breve del perfil de usuario.




* Seguimiento:


* username seguidor: Clave foránea referenciando al usuario que realiza el seguimiento.


* username seguidos: Clave foránea referenciando al usuario que es seguido.




* Publicación:


* id_publicación: Clave primaria identificadora de la publicación.


* url_imagen: Dirección o enlace al recurso de imagen almacenado.


* descripción: Texto o leyenda explicativa del post.


* fecha publicación: Fecha en que fue realizada la publicación.


* hora de publicación: Hora precisa del posteo.




* Etiqueta:


* id_nombre hastag: Clave primaria del hashtag o etiqueta de categorización.




* Publicacion-Etiqueta:


* id_publicación: Clave foránea referenciando a la publicación etiquetada.


* id_nombre hastag: Clave foránea referenciando al hashtag utilizado.




* Comentario:


* id_comentario: Clave primaria identificadora del comentario.


* texto: Contenido o mensaje del comentario.


* fecha_hora: Marca temporal del comentario.


* id_username: Clave foránea del usuario autor del comentario.


* id_publicación: Clave foránea de la publicación comentada.




* Responde comentarios:


* id_comentario: Clave foránea que referencia al comentario respondido o generado.


* id_username: Clave foránea del usuario autor de la respuesta.


* id_publicación: Clave foránea referenciando a la publicación a la que pertenece la conversación.




* Reacción:


* tipo de reacción: Atributo que almacena la clase de interacción (ej. me gusta, me encanta, etc.).





---

## Relaciones del Modelo

1. Usuario ↔ Seguimiento (Relación N:M autorreferencial):


* Un usuario puede seguir a múltiples usuarios y, a su vez, ser seguido por múltiples usuarios. La entidad `Seguimiento` gestiona los roles de `username seguidor` y `username seguidos`.




2. Usuario ↔ Publicación (Relación 1:N):


* Un usuario puede realizar múltiples publicaciones en la plataforma, pero cada publicación pertenece a un único usuario autor.




3. Publicación ↔ Etiqueta (Relación N:M via Publicacion-Etiqueta):


* Una publicación puede contener múltiples etiquetas/hashtags y una etiqueta puede asociarse a múltiples publicaciones. Se resuelve mediante la entidad intermedia `Publicacion-Etiqueta`.




4. Usuario ↔ Comentario (Relación 1:N):


* Un usuario puede redactar múltiples comentarios en diferentes o iguales publicaciones.




5. Publicación ↔ Comentario (Relación 1:N):


* Una publicación agrupa múltiples comentarios realizados por los usuarios.




6. Comentario ↔ Responde comentarios (Relación 1:N / Auto-asociación):


* Un comentario puede recibir múltiples respuestas de otros usuarios en forma de hilo conversacional.




7. Usuario / Publicación / Comentario ↔ Reacción (Relación N:M):


* Los usuarios pueden interactuar mediante la entidad `Reacción`, registrando el `tipo de reacción` tanto en publicaciones como en comentarios específicos.
