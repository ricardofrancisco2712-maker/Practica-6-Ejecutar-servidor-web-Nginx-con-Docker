# Practica-6-Ejecutar-servidor-web-Nginx-con-Docker


## Descripción

El objetivo de esta práctica es crear y ejecutar un servidor web local utilizando **Nginx y Docker Compose**. Se configurará un contenedor que servirá una página HTML almacenada en nuestro equipo mediante un volumen.

## Objetivos

- Crear una página web básica con HTML.
- Utilizar Docker para ejecutar un servidor web Nginx.
- Configurar un contenedor mediante Docker Compose.
- Mapear un directorio local al directorio web del contenedor.
- Verificar el funcionamiento del servidor desde el navegador.
- Publicar el proyecto en un repositorio público de GitHub.

## Tecnologías utilizadas

- Docker Desktop
- Docker Compose
- Nginx
- HTML5
- Git y GitHub
- Windows

## Estructura del proyecto

```text
practica-nginx/
├── src/
│   └── index.html
├── docker-compose.yml
└── README.md
```

## 1. Página web HTML

Dentro del directorio `src` se crea el archivo `index.html`, que contiene el mensaje que mostrará el servidor web.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Práctica Nginx</title>
</head>
<body>
    <h1>¡Hola Mundo!</h1>
    <p>Mi servidor web Nginx está funcionando con Docker Compose.</p>
</body>
</html>
```

## 2. Configuración de Docker Compose

En la carpeta principal del proyecto se crea el archivo `docker-compose.yml` con la siguiente configuración:

```yaml
services:
  nginx:
    image: nginx:latest
    container_name: mi-servidor-nginx
    ports:
      - "8080:80"
    volumes:
      - ./src:/usr/share/nginx/html:ro
    restart: unless-stopped
```

### Explicación de la configuración

- **image:** utiliza la imagen oficial de Nginx.
- **container_name:** establece el nombre del contenedor como `mi-servidor-nginx`.
- **ports:** conecta el puerto 8080 del equipo local con el puerto 80 del contenedor.
- **volumes:** comparte el directorio `src` con `/usr/share/nginx/html`, donde Nginx busca los archivos de la página web.
- **ro:** monta el directorio en modo de solo lectura para el contenedor.
- **restart:** permite reiniciar automáticamente el contenedor, salvo que haya sido detenido manualmente.

## 3. Ejecución del servidor

Para ejecutar el proyecto, es necesario tener Docker Desktop instalado y en funcionamiento.

Desde una terminal ubicada en la carpeta principal del proyecto, se ejecuta el siguiente comando:

```bash
docker compose up -d
```

Este comando descarga la imagen de Nginx si es necesario, crea el contenedor e inicia el servidor web en segundo plano.

## 4. Verificación del contenedor

Para comprobar que el contenedor se encuentra funcionando, se ejecuta:

```bash
docker compose ps
```

Para consultar los registros del servidor:

```bash
docker compose logs nginx
```

## 5. Acceso al servidor web

Una vez iniciado el contenedor, se abre el navegador y se accede a la siguiente dirección:

**http://localhost:8080**

Si la configuración es correcta, se mostrará la página HTML con el mensaje **¡Hola Mundo!**.

## 6. Detener el servidor

Para detener y eliminar el contenedor del proyecto, se utiliza:

```bash
docker compose down
```

Este comando no elimina los archivos HTML del proyecto.

## Resultado esperado

Se obtiene un servidor web Nginx ejecutándose localmente mediante Docker Compose, capaz de servir una página HTML almacenada en el directorio `src` del proyecto.

## Conclusión

Con esta práctica se aplican los conceptos básicos de contenedores, imágenes, puertos y volúmenes de Docker. Además, se aprende a utilizar Docker Compose para administrar un servidor web y a publicar el código fuente en GitHub.

## Repositorio

**Enlace al repositorio público:** [Agregar aquí la URL de GitHub]

---

**Práctica académica:** Servidor web Nginx con Docker Compose.
