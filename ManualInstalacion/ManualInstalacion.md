# Manual de instalación Componente Centralizador

## 1. Introducción

Este manual te guiará paso a paso en la configuración e instalación completa de la aplicación Componente Centraolizador del proyecto Cognicare. Este proyecto está diseñado para que cualquier desarrollador desde conocimientos básicos hasta avanzados pueda duplicarlo, por lo que cada etapa del proceso se explica de forma clara, sencilla y detallada.

## 2. Arquitectura de Componente Centralizador

El proyecto implementa un patrón arquitectónico de capas, con las cuales se les da responsabilidades a cada capa para generar la administración crentralizada de todos los componentes de Cognicare.

![Arquetipo_Referencia](https://hackmd.io/_uploads/SJ-04v48xx.png)

### 2.1 Componentes

#### Users (Usuarios):

- ¿Quiénes son? ¡Eres tú y todos los que usarán nuestro sistema!

- ¿Qué hacen? Son las personas que interactúan directamente con la aplicación. Podrían estar usando nuestra página web y cualquier otro modulo de Cognicare.

#### Http (Conexión a Internet):

- ¿Qué es? Es la forma en que los usuarios se conectan a nuestro sistema a través de internet. Piensa en esto como la "autopista" por donde viajan las solicitudes y respuestas cuando usas una página web o una aplicación.

- ¿Qué hace? Permite que tu computador o dispositivo envíe una petición al sistema (por ejemplo, "quiero ver mi información") y reciba una respuesta ("aquí está tu información").

#### Node.js - Componente-Centralizador-api (El Cerebro Central / La Oficina de Atención):

- ¿Qué es? Este es el corazón de nuestro sistema, construido con Node.js. Imagina que es una "oficina de atención al cliente" muy eficiente.

- ¿Qué hace? Cuando un usuario hace una solicitud (a través de Http), esta es la primera parada. El Componente Centralizador recibe la petición, la entiende y decide a qué otra parte del sistema debe enviarla para obtener la información correcta o realizar la acción solicitada. También es el que organiza la respuesta para enviársela de vuelta al usuario.

#### Variables-Cognitivas-api (El Especialista en Procesos Complejos / El Experto en los juegos):

- ¿Qué es? Este es un módulo especializado que se encarga de realizar tareas de entrenamiento de los estudiantes.

- ¿Qué hace? Son los componentes de entrenamiento Cognitivo que por medio del juego los estudiantes de la Universidad Catolica de Oriente pueden interactuar y mejorar sus habilidades en cada campo que deban ingresar y entrenar.

#### Postgresql (La Gran Biblioteca / El Archivador Maestro):

- ¿Qué es? Es una base de datos, específicamente PostgreSQL. Piensa en ella como una biblioteca gigantesca o un archivador muy bien organizado donde guardamos toda la información importante del sistema.

- ¿Qué hace? El Componente Centralizador-api (y a veces el Especialista) la usa para guardar nueva información, buscar datos que necesita o actualizar información existente. Es donde se almacena de forma segura todo lo que el sistema necesita recordar.

## 3. Requisitos Previos y Preparación del Entorno

**Propósito:**
Antes de instalar cualquier herramienta, es importante identificar la arquitectura de tu sistema operativo, ya que esto determinará qué versiones de software debes descargar e instalar.

**Descargo de responsabilidad:**
Las instrucciones proporcionadas en este manual se basan y validan con las versiones de software especificadas en cada subsección (Git 2.49.0, Node 20.19.4, Express 5.1.0, Docker 28.1.1, Docker Compose 2.12.2). Si decides instalar o utilizar versiones diferentes a las aquí indicadas, no podemos garantizar el correcto funcionamiento del proceso de configuración y despliegue. Los autores de este manual no asumen responsabilidad alguna por los problemas, errores o incompatibilidades que puedan surgir como resultado de la instalación o uso de versiones de software distintas a las recomendadas. Se sugiere encarecidamente seguir las versiones exactas mencionadas para asegurar el éxito del despliegue.

### 3.1 Identificación de la Arquitectura del Sistema

**Propósito:**
Antes de instalar cualquier herramienta, es importante identificar la arquitectura de tu sistema operativo, ya que esto determinará qué versiones de software debes descargar e instalar.

**Para Windows:**
1. Para verificar si tu sistema es de 32 o 64 bits:
   - Método 1: En el explorador de archivo de Windows haz clic derecho en "Este equipo" o "Mi PC" → Propiedades
   ![Explorador_Archivos](https://hackmd.io/_uploads/H1Si4KtWeg.png)
   ![Propiedades_Explorador](https://hackmd.io/_uploads/HJADOPEUxe.png)
   ![Final_Meto1](https://hackmd.io/_uploads/SkdsuvVUel.png)
   - En el apartado de "Tipo de sistema" te dira si tu procesador es de 64 bits o 32 bits

   - Método 2: Abre la configuración de Windows → Sistema → Acerca de o Información
   ![Meto2Confi](https://hackmd.io/_uploads/r1PlKDELlg.png)
   ![Meto2Final](https://hackmd.io/_uploads/HyKUKw4Uex.png)
   - Método 3: Presiona Win+R se abrira un cuadro donde se puede ingresar texto, escribe "msinfo32" y presiona Ente, donde en la variable de Tipo de sistema le dira sobre que arquitectura esta construido su procesador.
   ![Meto3_Conso](https://hackmd.io/_uploads/S15YKPEUlx.png)
   ![Meto3Final](https://hackmd.io/_uploads/ByQnYvE8xl.png)
   
2. En la información del sistema, busca "Tipo de sistema":
   - "Sistema operativo de 64 bits, procesador basado en x64": Debes usar versiones x64/AMD64
   - "Sistema operativo de 32 bits, procesador basado en x86": Debes usar versiones x86

### 3.2 Instalación de Git

**Propósito:**
Git es una herramienta que permite gestionar el código fuente de un proyecto, facilitando tanto el control de versiones como la descarga desde repositorios remotos. En este caso, utilizaremos Git porque el código fuente de la aplicación **Componente Centralizador** se encuentra alojado en un repositorio remoto.

**Instalación y Configuración:**

**Para Windows:**
1. Visita [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Descarga el instalador para Windows
3. Ejecuta el archivo descargado y sigue el asistente de instalación
4. Durante la instalación, mantén las opciones predeterminadas a menos que sepas lo que estás cambiando
5. Al llegar a "Adjusting your PATH environment", selecciona "Git from the command line and also from 3rd-party software"
6. Para las demás opciones, mantén los valores predeterminados
7. Completa la instalación

**Verificación:**
1. Abre una ventana de terminal
-En **Windows**: usa **Command Prompt** o **PowerShell**.
3. Escribe: `git --version`
4. Deberías ver algo como: `git version 2.35.1`

**Configuración inicial:**
1. Configura tu nombre de usuario: `git config --global user.name "Tu Nombre"`
2. Configura tu correo electrónico: `git config --global user.email "tu.email@ejemplo.com"`

**Límites de uso o condiciones:**
- Git es completamente gratuito y de código abierto
- No hay límites de uso
- No requiere registro de cuenta para uso local

**Errores comunes y soluciones:**
- **Error "git no se reconoce como un comando interno"**: Reinicia la terminal después de la instalación. Si persiste, verifica que la ruta de instalación de Git se haya añadido correctamente a la variable PATH, verifica las variables de entorno.

![VariableInicio](https://hackmd.io/_uploads/r1L-0PVLex.png)

- Para verificar si se agrego las variables que requiere git para trabajar en Windows se debe buscar en variables del sistema la variable que se llama Path y darle Editar

![VariableInfo](https://hackmd.io/_uploads/rJ7NRDEUlg.png)

- Donde debes de buscar una ruta parecida a esta:

![VariablesFinal](https://hackmd.io/_uploads/HJcYADNIge.png)

Si no aparece una ruta así, incluso después de verificar que Git se instaló correctamente, no es suficiente con reinstalarlo nuevamente.

Si tras la reinstalación Git aún no aparece en el PATH, es posible que los cambios no se estén aplicando correctamente. En ese caso, asegúrate de:

- Ejecutar el instalador como administrador, para que pueda modificar las variables del sistema.
- Añadir manualmente la ruta de Git al `Path`, siguiendo estos pasos:

    1. Abre el menú Inicio y busca **"variables de entorno"**, luego selecciona "Editar las variables de entorno del sistema".

    2. En la ventana que aparece, haz clic en el botón "Variables de entorno".

    3. En la sección **"Variables del sistema"**, selecciona la variable llamada `Path` y haz clic en **"Editar"**.

    4. Dentro del editor de la variable `Path`, haz clic en **"Nuevo"**.

    5. Pega la siguente ruta `C:\Program Files\Git\cmd`
    6. Cierra todas las ventanas haciendo clic en **"Aceptar"** para guardar los cambios.

Finalmente, para volver a verificar la instalación, cierra y vuelve a abrir la terminal (o reinicia el sistema si es necesario) y ejecuta:`git --version`

### 3.3 Instalación de Node js
Node.js es como una herramienta que permite que el lenguaje de programación JavaScript, que normalmente se usa para hacer que las páginas web sean interactivas en tu navegador, pueda funcionar también como el "cerebro" detrás de aplicaciones en un servidor. Imagina que es un intérprete que toma las instrucciones de JavaScript y las ejecuta fuera del navegador, permitiendo crear programas que gestionan información, se conectan a bases de datos y manejan las peticiones de muchos usuarios al mismo tiempo de manera eficiente, lo que lo hace muy popular para construir las "oficinas de atención" (APIs) que vimos en tu diagrama.

**Instalación y Configuración**

1. Visita [Node.js](https://nodejs.org/en/download)
2. Donde vas a ver una pagina como esta:

En la cual debes señalar la versión del Node que deseas instalar, la recomendada es la 20.19.4.
![InstaladorNode](https://hackmd.io/_uploads/H10lg_EIgg.png)

De igual forma revisa la arquitectura del computador para tu sistema operativo, en la parte inferior lo puedes cambiar.
![image](https://hackmd.io/_uploads/SJEDxdN8ex.png)

3. El archivo que te instala en el explorador de archivos debes abrirlo y te mostrara esta vista:
![NodeInicio](https://hackmd.io/_uploads/B1Lal_NUlg.png)

Para instalarlo lo unico que debes hacer es darle en el boton de **Next** que te muestra la vista y no debes de cambiar nada en la instalación solo aceptar los terminos y condiciones y continuar con la instalación que te deja sin cambiar ninguna propiedad.

**Verificación:**
1. Abre una nueva terminal
-En **Windows**: usa **Command Prompt** o **PowerShell**.
2. Ejecuta: `node -v`
3. Deberías ver información de la versión de Node (20.19.4)

**Errores comunes y soluciones:**
- **"node no se reconoce como un comando interno"**: Verifica que NVM_SYMLINK y PATH estén correctamente configurados, y reinicia la terminal donde ejecuto la verificación de la versión de Node, si todavía no reconoce el comando verifique que si se agregaran Node en las variables de entorno, puede revisar los pasos que se mostraban en la instalación de Node en Windows, sino encuentra la propiedad de Node debe agregarla manualmente o reintentar la instalación.
Pasos para agregarla manualmente:
1. Debe buscar el programa de variables de entorno de Windows, cuando lo encuentre se le abrira una vista como esta:

![VariablesEntorno](https://hackmd.io/_uploads/BJiK3_ELee.png)

Donde debe darle donde señala la flechala cual le abrirá:

![InfoVariables](https://hackmd.io/_uploads/BkS3nuE8xg.png)

2. Donde la opción que se ve subrayada en azul es lo que le debe aparecer, en caso de que no sea así, debe crearla, le debe dar en **Nuevo...**
3. La cual le abrira esta vista donde debe llenar los datos con la información que se le muestra en la siguiente imagen

![CrearVariable](https://hackmd.io/_uploads/S1G_6uEUex.png)

Ya despues de agregar los datos solo debe darle en aceptar y abrir de nuevo una nueva terminal y volver ejecutar el comando de **node -v**.

### 3.4 Instalación de Docker

**Propósito:**
Docker es una plataforma que permite desarrollar, enviar y ejecutar aplicaciones en contenedores. MessageUcoLab utiliza Docker para gestionar todos los componentes de infraestructura como Kafka, PostgreSQL, MongoDB, Redis y servicios de observabilidad.

**Instalación y Configuración:**

Vease la documentación oficial de Docker: https://docs.docker.com/engine/install/

**Para Windows debe instalar Docker Desktop**
En el link anterior puedes encontrar el apartado donde te llevará a descargar Docker Desktop, donde debes seguir los pasos de instalación según tu arquitectura del procesador y el sistema operativo.

![InstalarDocker](https://hackmd.io/_uploads/H1tVk5KWgx.png)

Debes de buscar esta opción para descargar Docker Desktop, si tu sistema operativo es Windows le das a esa opción si es Mac le das a esa opción.

![Windows Docker](https://hackmd.io/_uploads/ryUq19FZxg.png)

Donde debe señalar la arquitectura de su computador para descargar el ejecutable de la intalacion, una vez descargado solo siga los pasos y no es necesario cambiar nada de las configuraciones de descarga

Una vez se culmina la instalación, es necesario crear una cuenta o iniciar sesión con Google o GitHub, esto para poder acceder a algunas herramientas de Docker hub que solo se pueden acceder cuando se está autenticado.

### 3.5 Instalación de Docker Compose

**Propósito:**
Docker Compose es una herramienta para definir y ejecutar aplicaciones multi-contenedor. En MessageUcoLab, se utiliza para orquestar todos los servicios necesarios y garantizar que se inicien en el orden correcto con la configuración adecuada.

**Instalación y Configuración:**

**Para Windows:**
- Docker Compose viene incluido con Docker Desktop, no requiere instalación adicional

**Verificación:**
1. Abre una terminal
-En **Windows**: usa **Command Prompt** o **PowerShell**.
-En **macOS** o **Linux**: usa la aplicación **Terminal**.
2. Ejecuta: `docker-compose --version`
3. Deberías ver algo como: `Docker Compose version v2.12.2`

**Límites de uso o condiciones:**
- Docker Compose es completamente gratuito y de código abierto
- No hay restricciones de uso ni limitaciones técnicas
- Compatible con todas las funcionalidades de Docker

**Errores comunes y soluciones:**
- **"docker-compose: command not found"**: Este error aparece cuando el sistema no reconoce el comando docker-compose, lo que impide ejecutar archivos docker-compose.yml para levantar servicios. Puede deberse a una instalación incompleta, ausencia del binario, o configuración incorrecta del entorno.

    Si Docker Compose está instalado, pero aún no se reconoce, es posible que no esté en la ruta de acceso del sistema. Para solucionar este problema, agregue Docker Compose a PATH.

    **En Windows:**
    Agregar Docker Compose a la ruta de acceso en Windows

    Busca en el equipo 'Editar las variables de entorno del sistema'.
    En la sección 'Variables del sistema', busque y seleccione la variable 'Path' y luego haga clic en 'Editar'.

    ![Variables](https://hackmd.io/_uploads/ByyIaM0-el.png)

    Haga clic en 'Nuevo' y agregue la ruta al directorio donde se encuentra docker-compose.exe.

    ![VariablesDocker](https://hackmd.io/_uploads/H1Rspz0-eg.png)

    Aplique los cambios y reinicie el CMD o PowerShell para verificar la instalación.

- **Repository does not exist or may require 'docker login'**: Este error ocurre cuando Docker intenta descargar una imagen desde un repositorio privado y no tiene credenciales válidas. El daemon de Docker rechaza la solicitud porque es necesario iniciar sesión para obtener acceso a la imagen.
    Entre las soluciones esta:
        1. **Inicia sesión en Docker Hub o el registro correspondiente:**
           Para Docker Hub:
           ```bash
           docker login
           ```
        2. **Comprueba que tu usuario tenga permisos para acceder a la imagen:**
        - Verifica que la cuenta con la que hiciste docker login tiene acceso a la imagen
        - Si estás usando tokens o claves de acceso, asegúrate de que no hayan expirado y sean válidas

    - En Windows: Asegúrate de que Docker Desktop esté abierto y corriendo

## 4. Componentes basados en Docker

Los siguientes componentes se gestionan automáticamente mediante Docker en el proyecto Componenete Centralizador, pero es importante entender su propósito:

### 4.1 PgAdmin y Postgresql

**Propósito**

- **PostgreSQL**: Sistema de gestión de bases de datos relacionales robusto y de código abierto.

- **pgAdmin**: Herramienta de administración y desarrollo para PostgreSQL con interfaz gráfica.

En el Componente Centrealizador, PostgreSQL y pgAdmin se utilizan para:
- Almacenar y organizar de manera estructurada los datos de la aplicación.
- Asegurar la integridad y consistencia de la información manejada por el sistema.
- Permitir a los desarrolladores y administradores crear, consultar, actualizar y eliminar datos de forma eficiente.
- Facilitar la gestión de usuarios, permisos y seguridad de la base de datos.
- Visualizar y manipular las tablas, vistas y otros objetos de la base de datos de manera sencilla (con pgAdmin).
- Ayudar en la depuración y optimización de consultas a la base de datos.

## 5. Procedimiento de Clonación y Compilación del Proyecto

### 5.1 Clonación del Repositorio

**Propósito:**
Descargar el código fuente del proyecto desde GitHub a tu máquina local para poder trabajar con él.

**Procedimiento:**
1. Abre una terminal o línea de comandos
2. Navega a la carpeta donde quieres guardar el proyecto
3. Ejecuta el comando de clonación, para el FrontEnd:
   ```bash
   git clone -b develop https://github.com/CognicareUCO/CentralizadorFrontEnd.git
   ```
4. Entra en el directorio del proyecto:
   ```bash
   cd CentralizadorFrontEnd
   ```
5. Ejecuta el comando de clonación, para el BackEnd:
   ```bash
   git clone -b develop https://github.com/CognicareUCO/CentralizadorBackEnd.git
   ```
6. Entra en el directorio del proyecto:
   ```bash
   cd CentralizadorBackEnd
   ```
7. Ejecuta el comando de clonación, para el FrontEnd:
   ```bash
   git clone -b develop https://github.com/CognicareUCO/BaseDeDatos.git
   ```
8. Entra en el directorio del proyecto:
   ```bash
   cd ComponenteCentralizador
   ```
   
**Ejecución De los dos proyectos**
Para ejecutar los dos proyectos tanto del Frontend y el Backend, debes entrar en la ruta raiz, de cada proyecto y debes ejecutar el siguiente comando parado en la ruta raiz de los proyectos:
1. El primero comando que debes lanzar es para instalar todas las dependencias que requiere el proyecto, esto en los dos proyectos.
```
npm install
```
2. Lo segundo es el comando para ejecutar los dos proyectos.
```
npm run dev
```
   
### 5.2 Despliegue con Docker Compose
**Propósito:**
Docker Compose permite levantar todos los servicios necesarios para la aplicación Componente Centralizador de forma orquestada, asegurando que se inicie en el orden correcto y con las configuraciones adecuadas. Este despliegue incluye bases de datos.

1. Nos ubicamos en la ruta dentro del proyecto del Backend
```bash
cd deployment
```
2. Inicia todos los servicios en modo background:
   - Ve a la carpeta donde copiaste la base de datos
   - Dentro donde encuentres los script de la base de datos crea un archivo `docker-compose.yml`
   - Puedes copiar y pegar esta configuración de ejemplo con las credenciales de la base de datos y al configuración para el docker:
```yml
services:
  postgres:
    image: postgres:latest
    container_name: postgres_test
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: password
      POSTGRES_DB: CC
    ports:
      - "5432:5432"
    volumes:
      # Mapear todos los scripts SQL de la carpeta init_scripts al directorio de inicialización de PostgreSQL
      - ./init.sql:/docker-entrypoint-initdb.d/init.sql
      - ./data:/data
    networks:
      - postgres_network

  pgadmin:
    image: dpage/pgadmin4
    container_name: pgadmin_test
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@admin.com
      PGADMIN_DEFAULT_PASSWORD: admin
    ports:
      - "5050:80"
    depends_on:
      - postgres
    networks:
      - postgres_network

networks:
  postgres_network:
    driver: bridge

```
En esta configuración debes poner los scripts de la base de datos en un archivo `init.sql` en la misma carpeta donde tengas el archivo `docker-compose.yml`

Guarda el archivo y ejecuta el comando en la consola
   ```bash
   docker-compose up -d
   ```
   Este comando crea y arranca todos los contenedores definidos en `docker-compose.yml`.

4. Para verificar que todos los servicios se han iniciado correctamente:
   ```bash
   docker-compose ps
   ```
   Deberías ver todos los servicios con estado "Up" o similar.

5. Para acceder a la base de datos puedes usar el PGAdmin, también configurado en el `docker-compose-yml`.
   
**Límites de uso o condiciones:**
- Requiere al menos 8GB de RAM asignados a Docker para un funcionamiento óptimo
- Necesita aproximadamente 5GB de espacio en disco
- El inicio completo puede tomar más de 5 minutos dependiendo del hardware

**Errores comunes y soluciones:**

- **Puertos en uso:**
Docker Compose asigna puertos a cada servicio según la configuración del archivo docker-compose.yml. Si otro proceso en tu sistema ya está usando alguno de esos puertos, el contenedor no podrá iniciarse correctamente.
Para verificar qué procesos están usando un puerto:

    **En Windows y macOS puedes usar:**

    ```bash
    lsof -i :<puerto>
    ```
    o bien puedes usar la herramienta de docker compose para verificar los puertos de los servicios.

![DockerContenedor](https://hackmd.io/_uploads/BkIHoYVUle.png)

    Si detectas un conflicto, modifica el archivo docker-compose.yml para cambiar los puertos o detén lo que los este ocupando.

- **Problemas de memoria**: Docker requiere recursos adecuados (RAM y CPU) para ejecutar contenedores correctamente, especialmente cuando se levantan varios servicios simultáneamente. Si no se asigna suficiente memoria o CPU, algunos contenedores pueden fallar o quedar en estado pausado.

    - En Docker Desktop , revisa y aumenta los recursos asignados desde Settings > Resources.
    Además, limpiar recursos innecesarios puede ayudar, por ejemplo al usar.
    
    >**Nota importante**
    >Tener precaución al usar el comando pues elimina todas las imagenes no utilizadas.

    ```bash
    docker system prune -af
    ```

- **Conflicto de nombre de contenedor:** Este error ocurre cuando intentas crear o levantar un contenedor con un nombre que ya está siendo utilizado por otro contenedor existente, incluso si ese contenedor no está en ejecución. Entre las causas posibles estan:
    - Un contenedor anterior no fue eliminado correctamente
    - Reinicios frecuentes del despliegue sin limpiar los contenedores antiguos
    
    Identifica el contenedor en conflicto:

    ```bash
    docker ps -a
    ```
    Elimínalo manualmente si ya no lo necesitas:

    ```bash
    docker rm <nombre_del_contenedor>
    ```
    (Opcional) Cambia el nombre del contenedor en docker-compose.yml:

    ```yaml
    container_name: nuevo_nombre_contenedor
    ```
    Vuelve a levantar los servicios:

    ```bash
    docker-compose up -d
    ```

- **Problemas de conexión:** Durante la primera ejecución, Docker debe descargar todas las imágenes necesarias. Si la conexión a internet es inestable o lenta, estas descargas pueden fallar o demorarse excesivamente, causando que el proceso pare o se quede “colgado”.

    - Revisa tu conexión a internet y asegúrate de tener conexión estable. Si no es posible realizar esta acción, se sugiere verificar el archivo docker compose y descargar una imagen uno por uno
        ```bash
        docker pull nombre-de-la-imagen:tag
        ```
        Y despues ejecuta nuevamente el comando.
        ```bash
        docker-compose up -d
        ```
    - En caso de que la descarga se interrumpa, puedes cancelar la ejecución (con Ctrl + C en Windows) y volver a intentarlo
    
- **Contenedores que se quedan “colgados” o no terminan de arrancar:** A veces, al instalar o levantar servicios con Docker Compose, el proceso parece detenerse sin avanzar (por ejemplo, sin finalizar la descarga o la inicialización). Esto puede deberse a:
    - Problemas con la configuración de red
    - Recursos insuficientes (como memoria o espacio en disco)
    - Imágenes corruptas o incompatibles

    Para solucionar:

    Detén la ejecución con Ctrl + C (o Cmd + C en macOS).

    Verifica el estado de los contenedores y elimina los que estén en mal estado con:

    ```bash
    docker-compose down
    ```
    ```bash
    docker system prune -af
    ```
    Vuelve a ejecutar el comando para levantar los servicios:
    ```bash
    docker-compose up -d
    ```
    Si aun con eso no cargan, se recomienda verificar los logs en base al siguiente paso.

**Contenedores que no inician correctamente (Base de datos):**
En algunos casos, ciertos contenedor Postgresql, PGAdmin pueden no cargarse correctamente durante el arranque inicial. Esto puede deberse a un problema de dependencias de red, tiempo de espera agotado o condiciones de carrera entre los servicios.

El contenedor aparece como detenido (exited) o no muestra actividad significativa en los logs.

- Solución: Detén todos los contenedores y vuelve a ejecutar el entorno completo. Esto suele resolver los problemas de arranque. Puedes hacerlo con los siguientes comandos:

```bash
docker-compose down
docker-compose up -d
```

- **Servicios que no inician:** Puede suceder que algunos contenedores no arranquen correctamente o se detengan inmediatamente. Para diagnosticar el problema, utiliza el comando:  
  ```bash
  docker-compose logs <nombre-servicio>
  ```
    Esto mostrará los registros (logs) del servicio en cuestión, donde podrás identificar errores específicos, como problemas de configuración, fallos en la conexión a bases de datos, o errores internos de la aplicación. También puedes revisar el estado general con:
    ```bash
    docker-compose ps
    ```
    para asegurarte de qué contenedores están activos, detenidos o reiniciando.
    
**Límites de uso o condiciones:**
- Los comandos deben ejecutarse desde el directorio donde está el archivo `docker-compose.yml`
- Algunos comandos requieren permisos de administrador en ciertos sistemas
- La ejecución de `docker-compose down` detendrá todos los servicios de la aplicación

**Errores comunes y soluciones:**
- **Error "Connection refused" al verificar servicios**: Espera unos minutos a que todos los servicios estén completamente iniciados
- **No se puede conectar a las bases de datos**: La aplicación no logra conectarse a PostgreSQL. Verifica que las credenciales y URIs configuradas en el archivo .env sean correctas. También asegúrate de que los puertos de las bases de datos estén expuestos y accesibles.

## 6. Acceso a la API y Documentación

**Propósito:**
Swagger UI proporciona una interfaz interactiva para explorar y probar los endpoints de la API. La documentación OpenAPI describe formalmente la estructura de la API, permitiendo entender los recursos disponibles, parámetros requeridos y respuestas esperadas.

**Procedimiento:**
1. Asegúrate de que la aplicación esté en ejecución

2. Accede a Swagger UI a través de:
   ```
   http://localhost:3001/api-docs/#/Autenticaci%C3%B3n
   ```
   ![image](https://hackmd.io/_uploads/ByNQ9K4Ige.png)

4. En Swagger UI, puedes:
   - Ver todos los endpoints disponibles agrupados por controladores
   - Expandir cada endpoint para ver detalles de parámetros y respuestas
   - Probar endpoints directamente desde la interfaz
   - Ver modelos de datos utilizados por la API

**Características principales de la documentación:**
- Descripción detallada de cada endpoint
- Parámetros de entrada requeridos y opcionales

![Swagger](https://hackmd.io/_uploads/rklfD9tNUll.png)

- Formato de respuesta esperado y códigos de estado HTTP
- Modelos de datos utilizados en la API

**Límites de uso o condiciones:**
- Swagger UI consume recursos adicionales, por lo que puede estar deshabilitado en entornos de producción
- Algunas funcionalidades avanzadas pueden requerir autenticación

**Errores comunes y soluciones:**
- **No se puede acceder a Swagger UI**: Verifica que la aplicación esté en ejecución.
    **Solución:**
    Esto lo logras verificando que desplegaste la aplicación, esto lo miras ejecutando los pasos del punto 6.3. Del documento, donde podrás ver los pasos para desplegar la aplicación.

## 7. Configuración del proyecto en Visual Studio Code

### 7.1 Instalación de IDE (Visual Studio Code)

**Propósito:**
Visual Studio Code (VS Code) es un editor de código ligero y multiplataforma que puede convertirse en un entorno de desarrollo completo para Java mediante extensiones. Esta sección describe cómo configurar el proyecto MessageUcoLab desde VS Code.

**Procedimiento:**
1. Descarga desde: https://code.visualstudio.com/Download

2. Selecciona según tu sistema operativo 

![VisualDescargar](https://hackmd.io/_uploads/ryVH3ERblg.png)

3. Abrir el proyecto en el IDE de visual studio code
Puedes abrir los dos proyectos del backend y el frontend con el mismo programa en dos ventanas diferentes. 

- Cuando se instalan las dependencias en el proyecto, te mostrará esta vista:

![Visual](https://hackmd.io/_uploads/SkbKVqAWxg.png)

- Donde puedes darle a la opción de `Open Folder...`. Cuando le das a esta opción, se te abrirá un explorador de archivos donde debes buscar la ruta donde clonaste el proyecto de Componente Centralizador, lo abres y se te comenzarán a cargar todas las dependencias y carpetas que posee.

Donde se te abrira algo parecido a esto:
![Proyecto](https://hackmd.io/_uploads/B1gfOtN8lx.png)

- Visual Studio IntelliCode (autocompletado asistido por IA)
   - Ver modelos de datos utilizados por la API
