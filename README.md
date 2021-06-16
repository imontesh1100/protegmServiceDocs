**ProteGM Services Documentation**
----
  _A continuacion se muestra de forma general cada uno de los servicios creados para la aplicacion movil ProteGM, se incluye toda la información necesaria para hacer las consultas correspondientes._

**Usuarios**
----
| Titulo      | Creacion de Usuario  | 
| :------------ |:---------------    | 
| URL         | `/services/signup`   |
| Metodo      | **POST**             |
| Parametros  | `nombre[string]*`    |
|             | `email[string]*`     | 
|             | `password[string]*`  |
| Success Response | `{token:***********,is_signup:true}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'El email ya fue previamente registrado',is_signup:false}`  |
|                | `{error_msg:'Ha ocurrido un error al crear el usuario',is_signup:false}`  |

_*Parametro obligatorio_

| Titulo      | Login  | 
| :------------ |:---------------   | 
| URL         | `/services/login`   |
| Metodo      | **GET**             |
| Parametros  | `email[string]*`    |
|             | `password[string]*` | 
| Success Response | `{token:***********,is_login:true}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'El email o la contraseña es incorrecta',is_signup:false}`  |
|                | `{error_msg:'Ha ocurrido un error al iniciar sesion.',is_signup:false}`  |

_*Parametro obligatorio_

| Titulo      | Login Premium | 
| :------------ |:---------------   | 
| URL         | `/services/login/premium`   |
| Metodo      | **GET**             |
| Parametros  | `password[string]*`    |
|             | `code[string]*` | 
| Success Response | `{token:***********,is_login:true}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'Asegurate que el codigo premium y la contraseña sean correctos',is_signup:false}`  |
|                | `{error_msg:'Ha ocurrido un error al iniciar sesion.',is_signup:false}`  |

_*Parametro obligatorio_

| Titulo      | Recuperar Contraseña  | 
| :------------ |:---------------   | 
| URL         | `/services/usuario/password/recuperar`   |
| Metodo      | **POST**             |
| Parametros  | `email[string]*`    |
| Success Response | `{msg:'La nueva contraseña es:ProteGm-App',password_restored:true}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'"No se ha podido restaurar la contraseña para el email',password_restored:false}`  |
|                | `{error_msg:'Ha ocurrido un error inesperado',password_restored:false}`  |

_*Parametro obligatorio_

| Titulo      | Informacion del usuario  | 
| :------------ |:---------------   | 
| URL         | `/services/usuario/informacion`   |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
| Success Response | `{nombre: ***** ****,email: ***@*****.com, is_premium: true,code: $%#$%&}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'Token incorrecto'}`  |
|                | `{error_msg:'Ha ocurrido un error, intenta de nuevo.'}`  |

_*Parametro obligatorio_

| Titulo      | Verificar tipo de usuario | 
| :------------ |:---------------   | 
| URL         | `/services/usuario/is-premium`   |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
| Success Response | `{is_premium:true,code:*******}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'Token incorrecto'}`  |
|                | `{error_msg:'Ha ocurrido un error, intenta de nuevo.'}`  |

_*Parametro obligatorio_

**Contactos**
----
| Titulo      | Nuevo Contacto  | 
| :------------ |:---------------    | 
| URL         | `/services/contacto/nuevo`   |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`     |
|             | `nombre[string]*`    |
|             | `email[string]*`     | 
|             | `telefono[string]*`  |
|             | `tipo[string]*`      |
| Success Response | `{msg:'Contacto guardado',"contacto_info": {"id": -,"nombre":"--","email": "---","telefono": "--","tipo": "--"}}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'Tipo de Contacto Incorrecto'}`  |
|                | `{error_msg:'El contacto no puede ser guardado ya sea por el token o exceso de contactos del tipo:SEGURIDAD/MEDICO'}`  |
|                | `{error_msg:'Ha ocurrido un error al guardar el contacto'}`  |

_*Parametro obligatorio_

| Titulo      | Borrar Contacto  | 
| :------------ |:---------------    | 
| URL         | `/services/contacto/borrar`   |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`     |
|             | `id[string]*`    |
| Success Response | `{msg:'Contacto eliminado'}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios}`  |
|                | `{error_msg:'El contacto no puede ser eliminado'}`  |
|                | `{error_msg:'Ha ocurrido un error al eliminar el contacto'}`  |

_*Parametro obligatorio_

| Titulo      | Informacion de Contactos  | 
| :------------ |:---------------    | 
| URL         | `/services/contacto/informacion`   |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
| Success Response | `[{"id":*,"nombre":"***","email":"***.com","telefono":"######","tipo":"MEDICO/SEGURIDAD"},{..},{...}]`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'Token Incorrecto'}`  |
|                | `{msg:'No existen contactos guardados para este usuario'}`  |
|                | `{error_msg:'Ha ocurrido un error inesperado'}`  |

_*Parametro obligatorio_

**Noticias**
----
| Titulo      | Todas las Noticias  | 
| :------------ |:---------------    | 
| URL         | `/services/noticias` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
|             | `qty[string]`        |
| Success Response | `[{id:-,titulo:--,fecha:DD/MM/AAAA,p1:**,img_1:--},{id:-,titulo:--,fecha:DD/MM/AAAA,p1:**,img_1:--}]`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{msg:'No existen noticias'}`  |
|                | `{error_msg:'Ha ocurrido un error inesperado'}`  |

_*Parametro obligatorio_

| Titulo      | Obtener Noticia  | 
| :------------ |:---------------    | 
| URL         | `/services/noticias/{id}` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
| Success Response | `{id:#,titulo:******,subtitulo:**********,fecha:DD/MM/AAA,p1:***********,p2:**********,p3:*********,img_1:/media/noticias/{id}/img1.jpg,img_2:/media/noticias/{id}/img2.jpg,fuente:******,categoria:*******}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{msg:'No existe noticia con id:{id}'}`  |
|                | `{error_msg:'Ha ocurrido un error inesperado'}`  |

_*Parametro obligatorio_

| Titulo      | Obtener Municipio(Solo CDMX)  | 
| :------------ |:---------------    | 
| URL         | `/services/municipio` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
|             | `latitud[string]*`     |
|             | `longitud[string]*`     |
| Success Response | `{municipio:------}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:'Ha ocurrido un error :('}`  |

_*Parametro obligatorio_

**Dependencias**
----
| Titulo      | Dependencias por categoria | 
| :------------ |:---------------    | 
| URL         | `/services/dependencias` |
| Metodo      | **GET**              |
| Parametros  | `token[string]*`     |
|             | `municipio[string]* `|
|             | `estado[string]*`    |
|             | `categoria[string]* "SEGURIDAD" "SALUD" "BOMBEROS" "PROTECCION CIVIL"`         |
| Success Response | `[{"nombre": "****","telefono": "---","latitud": "---","longitud": "----","google": "----"},{"nombre": "****","telefono": "---","latitud": "---","longitud": "----","google": "----"}]`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:'No existen dependencias de ---- que coincidan con: ----, ----'}`  |

_*Parametro obligatorio_

| Titulo      | Dependencia mas cercana | 
| :------------ |:---------------    | 
| URL         | `/services/dependencia-cercana` |
| Metodo      | **GET**              |
| Parametros  | `token[string]*`     |
|             | `municipio[string]* `|
|             | `estado[string]*`    |
|             | `latitud[string]*`    |
|             | `longitud[string]*`    |
|             | `categoria[string]* "SEGURIDAD" "SALUD" "BOMBEROS" "PROTECCION CIVIL"`         |
| Success Response | `{"nombre": "****","telefono": "---","latitud": "---","longitud": "----","google": "----","distancia":""}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:'No existen dependencias de ---- que coincidan con: ----, ----'}`  |

_*Parametro obligatorio_

**Zonas de Riesgo**
----
| Titulo      | Todas las Zonas de Riesgo | 
| :------------ |:---------------    | 
| URL         | `/services/zonas-all` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
|             | `estado[string]`        |
| Success Response | `[{"id":1,"nombre":"****","estado":"---"},{"id":2,"nombre":"*****"",estado":"---"}]`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:'Ha ocurrido un error al obtener las zonas.'}`  |

_*Parametro obligatorio_

| Titulo      | Zonas de riesgo por Municipio | 
| :------------ |:---------------    | 
| URL         | `/services/zonas` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
|             | `municipio[string]*`        |
|             | `estado[string]*`        |
| Success Response | `[{"id":1,"nombre":"****"},{"id":2,"nombre":"*****"}]`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:'No existen zonas que coincidan con:----,----'}`  |

_*Parametro obligatorio_

| Titulo      | Informacion detallada Zona de riesgo | 
| :------------ |:---------------    | 
| URL         | `/services/zonas/detalle` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
|             | `zona[int]*`        |
| Success Response | `{"id": 1,"nombre": "*****","resumen": "***********",   "link_google": "-------","categorias": "-----,----,----,-----,------",   "municipio_id": ---,"map_options": "(-----, ----),--"}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:'No existen zona que coincidan con:----'}`  |

_*Parametro obligatorio_

| Titulo      | Push Notification  | 
| :------------ |:---------------    | 
| URL         | `/services/zonas/push` |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`     |
|             | `latitud[string]*`        |
|             | `longitud[string]*`        |
|             | `onesignal[string]*`        |
| Success Response | `{'status_push':'true',"colonia_id":-,"nombre":"---,"distancia":--}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{status_push:'false'}`  |

_*Parametro obligatorio_

**Publicaciones**
----
| Titulo      | Nueva Publicacion | 
| :------------ |:---------------    | 
| URL         | `/services/publicaciones/nueva` |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`     |
|             | `municipio[string]* `        |
|             | `estado[string]*`        |
|             | `titulo[string]*`        |
|             | `comentario[string]*`        |
|             | `categoria[string]* DELITOS ACCIDENTE CLIMA TEMBLOR OTROS` |
|             | `referencia[string]*`        |
|             | `fecha[string]*`        |
|             | `hora[string]*`        |
|             | `latitud[string]*`        |
|             | `longitud[string]*`        |
| Success Response | `{"msg":Tu publicación ha sido guardada con exito!!! }`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:Ha ocurrido un error al crear la publicación :( }`  |

_*Parametro obligatorio_

| Titulo      | Ultimas 3 Publicaciones | 
| :------------ |:---------------    | 
| URL         | `/services/publicaciones/ultimas` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
|             | `municipio[string]*`        |
|             | `estado[string]*`        |
| Success Response | `[{"id": 3,"titulo": "---","comentario": "---","fecha": "---","hora": "---","usuario": "---"},{"id": 2,"titulo": "*","comentario": "*","fecha":"**","hora": "***","usuario": "---"},{"id":1,"titulo": "*****", "comentario": "*****","fecha": "****","hora": "***","usuario": "--"}]`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:No existen publicaciones para ---,----}`  |

_*Parametro obligatorio_

| Titulo      | Publicacion detalle | 
| :------------ |:---------------    | 
| URL         | `/services/publicacion/detalle` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`     |
|             | `id_publicacion[string]*`        |
| Success Response | `{"id": -,"titulo": "*","comentario": "***","fecha": "**",   "referencia": "*****","hora": "***","categoria": "*****","usuario": "mmm", "municipio": "----"}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:No existe publicacion con id: ---}`  |

_*Parametro obligatorio_

**Estadisticas**
----
| Titulo      | Delitos del mes en curso | 
| :------------ |:---------------    | 
| URL         | `/services/estadisticas/delitos-mes` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
|             | `estado[string]*`   |
| Success Response | `{"anio": "---","mes": "---","delitos": "----","100_mil_hab": "--","variacion": "-"}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:No existe expediente para: --,-- -- ** }`  |
|                | `{error_msg:Ha ocurrido un error al obtener la informacion :( }`  |

_*Parametro obligatorio_

| Titulo      | Resumen| 
| :------------ |:---------------    | 
| URL         | `/services/estadisticas/resumen` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
|             | `estado[string]*`   |
|             | `anio[string]*`   |
| Success Response | `{"poblacion": "***","incidencia_delictiva": "*****","denuncias": "***","cifra_negra": "**","indice_paz": "---","principales_delitos": "-----"},anio:"--"`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:No existe expediente para: --,-- -- ** }`  |
|                | `{error_msg:Ha ocurrido un error al obtener la informacion :( }`  |

_*Parametro obligatorio_

| Titulo      | Denuncias Totales| 
| :------------ |:---------------    | 
| URL         | `/services/estadisticas/denuncias` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
|             | `estado[string]*`   |
|             | `anio[string]*`   |
| Success Response | `{"enero": {"delitos_mensuales": "1","x_100_mil_hab": "10","variacion": "+"},"febrero": {"delitos_mensuales": "1","x_100_mil_hab": "10","variacion": "+"},anio:"--" ...`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:No existe expediente para: --,-- -- ** }`  |
|                | `{error_msg:Ha ocurrido un error al obtener la informacion :( }`  |

_*Parametro obligatorio_

| Titulo      | Tipos de Delito| 
| :------------ |:---------------    | 
| URL         | `/services/estadisticas/tipos-delito` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
|             | `estado[string]*`   |
|             | `anio[string]*`   |
| Success Response | `{"transeuntes": {"delitos_mensuales": "44","x_100_mil_hab": "5"},"vehiculos": {"delitos_mensuales": "66","x_100_mil_hab": "5"},anio:"--" ...}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:No existe expediente para: --,-- -- ** }`  |
|                | `{error_msg:Ha ocurrido un error al obtener la informacion :( }`  |

_*Parametro obligatorio_

| Titulo      | Comparativo | 
| :------------ |:---------------    | 
| URL         | `/services/estadisticas/comparativo` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
|             | `estado[string]*`   |
| Success Response | `{"pasado": {"anio": "2017", "mes": "diciembre","delitos": "17,129" "habitantes": "192.1"},"actual": {"anio": "2018","mes": "diciembre","delitos": "19,905",     "habitantes": "223.6"}}`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{error_msg:No existe informacion suficiente para un comparativo de: *** - **, ---}`  |
|                | `{error_msg:Ha ocurrido un error al obtener la informacion para el comparativo :( }`  |

_*Parametro obligatorio_

**Modo Protegm**
----
| Titulo      | Iniciar | 
| :------------ |:---------------    | 
| URL         | `/services/protegm/on` |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`    |
|             | `lat_actual[string]*`   |
|             | `lng_actual[string]*`   |
|             | `lat_destino[string]*`   |
|             | `lng_destino[string]*`   |
|             | `contacto[string]*`   |
| Success Response | `{protegm_status:true,protegm_token:'----',msg:'Haz habilitado el modo PROTEGM'}`  |
| Error Response | `{error_msg:'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{protegm_status:false,msg:'Ha ocurrido un error al iniciar el modo PROTEGM'}`  |
|                | `{protegm_status:false,msg:'El modo PROTEGM ya se encuentra habilitado.'}`  |

_*Parametro obligatorio_

| Titulo      | Terminar  | 
| :------------ |:---------------    | 
| URL         | `/services/protegm/off` |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`    |
| Success Response | `{protegm_status:false,msg:'El modo PROTEGM ya se encuentra deshabilitado!!!'}`  |
|                  | `{protegm_status:false,msg:'El modo PROTEGM se ha deshabilitado con exito!!!'}`|
| Error Response | `{error_msg:'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{protegm_status:false,msg:'Ha ocurrido un error al finalizar el modo PROTEGM'}`  |
|                | `{protegm_status:true,msg:'No se ha podido finalizar el modo PROTEGM'}`  |

_*Parametro obligatorio_

| Titulo      | Actualizar posición actual  | 
| :------------ |:---------------    | 
| URL         | `/services/protegm/position` |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`    |
|             | `latitud[string]*`    |
|             | `longitud[string]*`    |
| Success Response | `{protegm_status:true}`|
| Error Response | `{error_msg:'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{protegm_status:false,msg:'Asegurate que el modo PROTEGM este habilitado'}`  |
|                | `{protegm_status:false,msg:'Ha expirado el tiempo para el modo PROTEGM'}`  |
|                | `{protegm_status:false,msg:'Ha ocurrido un error dentro del modo PROTEGM'}`  |

_*Parametro obligatorio_

| Titulo      | Obtener ultima posición  | 
| :------------ |:---------------    | 
| URL         | `/services/protegm/position` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
|             | `protegm_token[string]*`    |
| Success Response | `{protegm_status:true,data:{emisor:'----',contacto:'----',ultima_posicion:{latitud:'--',longitud:'--',fecha:'--'},inicio:{latitud:'--',longitud:'--'},destino:{latitud:'--',longitud:'--'}}}`|
| Error Response | `{error_msg:'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{protegm_status:false,msg:'Asegurate que el modo PROTEGM este habilitado'}`  |
|                | `{protegm_status:false,msg:'Ha expirado el tiempo para el modo PROTEGM'}`  |
|                | `{protegm_status:false,msg:'El token PROTEGM es incorrecto'}`  |
|                | `{protegm_status:false,msg:'Ha ocurrido un error dentro del modo PROTEGM'}`  |

_*Parametro obligatorio_

**Cuestionarios**
----
| Titulo      | Obtener Cuestionario activo | 
| :------------ |:---------------    | 
| URL         | `/services/cuestionario` |
| Metodo      | **GET**             |
| Parametros  | `token[string]*`    |
| Success Response | `{"titulo": "--","preguntas": {"pregunta 1": "--?",        "pregunta 2": "---","pregunta 3": "---","pregunta 4": "---" },"id": "-","status": true }`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{"msg": "Encuesta previamente contestada","status": false }`|

_*Parametro obligatorio_

| Titulo      | Guardar Respuestas| 
| :------------ |:---------------    | 
| URL         | `/services/cuestionario` |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`    |
|             | `contestado[boolean]*`    |
|             | `cuestionario[string]*`    |
|             | `respuestas[JSON]`    |
| Success Response | `{ "msg": "Gracias por participar", "status": true }`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{error_msg:'El token es incorrecto'}`  |
|                | `{"msg": "Encuesta previamente contestada","status": false}`  |
|                | `{error_msg:Ha ocurrido un error :( }`  |

_*Parametro obligatorio_

**Metricas**
----
| Titulo      | Actualizar Visita (Home) | 
| :------------ |:---------------    | 
| URL         | `/services/metricas/home` |
| Metodo      | **POST**             |
| Parametros  | `token[string]*`    |
| Success Response | `{"msg": "Metrica actualizada","status": true }`  |
| Error Response | `{error_msg':'Faltan Parametros Obligatorios'}`  |
|                | `{"msg": "Metrica no actualizada","status": false }`|

_*Parametro obligatorio_

