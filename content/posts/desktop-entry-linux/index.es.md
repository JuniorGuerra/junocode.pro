---
title: "Como crear una desktop entry en linux"
date: 2024-05-20T08:06:25+06:00
description: Creacion de Desktop Entry en Linux
menu:
  sidebar:
    name: Desktop Entry
    identifier: desktop-entry
    weight: 10
tags: ["Basic", "Linux", "Desktop"]
categories: ["Basic"]
---


Si usas Linux como tu sistema operativo principal, probablemente hayas notado que algunas aplicaciones descargadas no vienen con una entrada de escritorio predefinida. Esto es común cuando descargamos aplicaciones en formato `.tar.gz` que no incluyen instrucciones específicas para integrarse en el sistema de manera automática.

Afortunadamente, Linux nos permite crear nuestras propias entradas de escritorio para que estas aplicaciones aparezcan en el buscador de aplicaciones. En este tutorial, aprenderás a crear un archivo `name_file.desktop` para lograrlo.

Tomaremos como ejemplo Postman, una aplicación que se descarga como un archivo `.tar.gz` y que no crea automáticamente una entrada de escritorio al descomprimirlo. Sigue estos sencillos pasos para configurar la entrada manualmente.

## Creación de un archivo `.desktop`

### Paso 1: Crear el archivo `.desktop`

Vamos a crear un nuevo archivo `.desktop`. Como nuestro ejemplo es con Postman, lo llamaremos `postman.desktop`.

El archivo debe incluir las siguientes claves:

- `[Desktop Entry]`: Indica que estamos creando una entrada de escritorio.
- `Name`: El nombre de la aplicación.
- `Exec`: La ruta donde se encuentra el ejecutable.
- `Type`: El tipo de aplicación.
- `Icon`: La ruta del icono de la aplicación.

### Opcionales

Estos campos son opcionales, pero proporcionan más información y mejoran la integración:

- `Comment`: Una breve descripción de la aplicación.
- `Categories`: Categorías de la aplicación.
- `GenericName`: Nombre genérico de la aplicación.
- `Path`: La ruta donde se encuentra ubicada la aplicación.

### Paso 2: Configuración del archivo

Debemos crear el archivo en `/usr/share/applications` para que esté disponible para todos los usuarios. Si no tienes permisos de superusuario, puedes crearlo en `~/.local/share/applications`.

Para crear el archivo, usa tu editor de texto preferido. Aquí usamos `vim` como ejemplo. Si no lo tienes instalado, puedes hacerlo con `sudo apt install vim`.

```sh
sudo vim /usr/share/applications/postman.desktop
```

Añade la siguiente configuración al archivo:

```ini
[Desktop Entry]
Name=Postman
Comment=Test endpoint
GenericName=Internet API TEST
Exec=/usr/share/Postman/Postman
Icon=/usr/share/Postman/postman.png
Type=Application
Categories=Network;InstantMessaging;
Path=/usr/share/Postman
```

Guarda y cierra el archivo presionando `Esc` y luego escribiendo `:wq`.

### Paso 3: Asignar permisos

Una vez terminado, podemos validar si funciona y, si es necesario, asignar permisos de ejecución al archivo:

```sh
chmod +x /usr/share/applications/postman.desktop
```

### Paso 4: Refrescar el entorno de escritorio

Si tu máquina no reconoce los cambios en tiempo real, puedes refrescar el entorno de escritorio:

```sh
sudo update-desktop-database
```

Siguiendo estos pasos, habrás creado una entrada de escritorio para Postman que aparecerá en el buscador de aplicaciones de tu entorno de escritorio en Linux. Esta técnica se puede aplicar a cualquier otra aplicación que necesite una entrada de escritorio personalizada.