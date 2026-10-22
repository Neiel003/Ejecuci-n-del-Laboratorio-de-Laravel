<p align="center">
  <a href="https://laravel.com" target="_blank">
    <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo">
  </a>
</p>

<p align="center">
  <a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

<h1 align="center">Laboratorio de Laravel: Introducción al Framework MVC</h1>

<p align="center">
  <strong>Autora: Vasdti Legaspi</strong><br>
  <strong>Fecha: viernes, 23 de octubre de 2026</strong>
</p>

## Introducción

En este README voy a contar cómo fui haciendo el laboratorio de Laravel, siguiendo la guía de la asignatura de Desarrollo Web de la Universidad Tecnológica de Panamá. La idea es explicar el proceso como lo hice yo, paso por paso, con los comandos que fui utilizando y lo que debía revisar en cada momento.

Durante el laboratorio preparé el entorno de trabajo, creé el proyecto, revisé la conexión con MySQL, ejecuté las migraciones e inicié la aplicación. Después trabajé con Laravel UI y Bootstrap para generar las vistas de autenticación. Fui colocando las capturas en el mismo orden en que aparecen en las evidencias para que sea más fácil seguir el procedimiento.

## Objetivos

- Familiarizarse con la estructura básica de un proyecto Laravel.
- Comprender la organización del framework y el patrón Modelo-Vista-Controlador (MVC).
- Crear un proyecto utilizando Composer y Laravel.
- Configurar las variables de entorno y la conexión con MySQL.
- Ejecutar migraciones mediante Artisan.
- Iniciar el servidor de desarrollo y comprobar la aplicación.
- Generar vistas de inicio de sesión y registro utilizando Laravel UI y Bootstrap.
- Documentar el proceso mediante capturas de pantalla.

## Herramientas utilizadas

- **Laravel:** framework de desarrollo web.
- **PHP:** lenguaje utilizado por Laravel.
- **Composer:** administrador de dependencias de PHP.
- **Node.js y npm:** herramientas para gestionar recursos del frontend.
- **WampServer:** entorno de desarrollo local.
- **MySQL:** sistema de gestión de bases de datos.
- **phpMyAdmin:** herramienta para administrar la base de datos.
- **Bootstrap:** framework utilizado para los estilos de las vistas.
- **GitHub:** plataforma utilizada para documentar y compartir el laboratorio.

## Desarrollo del laboratorio paso a paso

Bueno, vamos con el laboratorio paso a paso. Voy a ir contando qué hice, qué escribí en la terminal y qué revisé para poder continuar. Las capturas están guardadas en la carpeta `Imagenes` y las puse en el mismo orden del procedimiento.

### Paso 1. Abrir la terminal y ubicarse en la carpeta de WampServer

![Paso 1: abrir la terminal y ubicarse en la carpeta](Imagenes/Img1.png)

Primero abrí CMD o PowerShell. Para empezar, escribí este comando para ubicarme en la raíz de la unidad:

```bat
cd \
```

Después me fui a la carpeta donde WampServer guarda los proyectos:

```bat
cd C:\wamp64\www
```

Así quedé dentro de `C:\wamp64\www`, que es la carpeta donde iba a guardar el proyecto.

Ya ubicada en esa carpeta, creé el proyecto con este comando:

```bat
laravel new Lab_Laravel
```

En mi caso le puse `Lab_Laravel` para identificar el laboratorio más rápido y tener claro cuál era la carpeta del proyecto.

Cuando se abrió el asistente de Laravel, me preguntó si quería utilizar un *starter kit*. En esa parte escribí `no`, porque quería continuar sin agregar uno. Después me preguntó qué frontend quería utilizar y seleccioné `blade`, que era la opción que iba a utilizar en esta práctica. Luego esperé a que terminara de crear el proyecto.

> Puede que las preguntas cambien un poco según la versión de Laravel que tengas instalada, así que fíjate en las opciones que te aparezcan en la terminal.

### Paso 2. Actualizar las dependencias del proyecto

![Paso 2: actualizar dependencias](Imagenes/Img2.png)

Cuando terminó de crearse el proyecto, entré en la carpeta que acababa de crear:

```bat
cd Lab_Laravel
```

Ya dentro de `Lab_Laravel`, ejecuté el siguiente comando:

```bat
composer update
```

Con esto Composer revisa y actualiza las dependencias de PHP del proyecto. Esperé a que terminara y revisé que no apareciera ningún error que impidiera continuar.

### Paso 3. Comprobar que WampServer esté funcionando

![Paso 3: comprobar WampServer](Imagenes/Img3.png)

Después abrí WampServer para comprobar que estuviera funcionando. Luego abrí el navegador y escribí esta dirección:

```text
http://localhost
```

Al entrar, debía aparecer la página de WampServer. Hice esta comprobación para asegurarme de que el entorno local estuviera respondiendo antes de seguir con Laravel. También necesitaba que MySQL estuviera funcionando para poder trabajar con la base de datos.

### Paso 4. Revisar la configuración de la base de datos

![Paso 4: revisar la base de datos](Imagenes/Img4.png)

Luego abrí phpMyAdmin desde WampServer para revisar la base de datos. Después abrí el archivo `.env`, que está en la carpeta principal de `Lab_Laravel`, y revisé los datos de conexión. Los valores que utilicé como referencia fueron:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=
```

Estos datos tienen que coincidir con la configuración de MySQL de tu equipo. En mi evidencia aparece la base de datos `laravel`; si todavía no existe en tu phpMyAdmin, hay que crearla o cambiar `DB_DATABASE` por el nombre de la base de datos que estés utilizando.

### Paso 5. Limpiar la caché de configuración y ejecutar las migraciones

![Paso 5: configurar Laravel y ejecutar migraciones](Imagenes/Img5.png)

Después volví a la terminal, asegurándome de estar dentro de `Lab_Laravel`, y ejecuté los comandos uno por uno. Primero escribí:

```bat
php artisan config:clear
```

Con esto limpié la caché de configuración para que Laravel leyera los valores actuales del archivo `.env`.

Después escribí:

```bat
php artisan config:cache
```

Este comando vuelve a guardar la configuración en caché.

Por último, ejecuté las migraciones:

```bat
php artisan migrate
```

Laravel revisa los archivos de `database/migrations` y crea las tablas que todavía no estén creadas. En la terminal pueden aparecer nombres como `users`, `cache` y `jobs`. Si te aparece un error, revisa el mensaje antes de continuar, sobre todo la conexión a MySQL y el nombre de la base de datos.

### Paso 6. Iniciar el servidor de Laravel

![Paso 6: iniciar el servidor](Imagenes/Img6.png)

Con la terminal todavía ubicada en la carpeta del proyecto, escribí:

```bat
php artisan serve
```

Este comando inicia el servidor de desarrollo de Laravel. Cuando se ejecutó correctamente, la terminal me mostró una dirección parecida a esta:

```text
http://127.0.0.1:8000
```

Dejé esa terminal abierta porque, si la cierro, el servidor deja de ejecutarse. Después abrí en el navegador la dirección que me apareció.

### Paso 7. Abrir la aplicación en el navegador

![Paso 7: abrir Laravel en el navegador](Imagenes/Img7.png)

Con el servidor encendido, abrí en el navegador la dirección que apareció en la terminal. En mi caso, normalmente sería:

```text
http://127.0.0.1:8000
```

Aquí revisé que la página de Laravel cargara. Si en vez de eso aparece un error, como me pasó durante la práctica, toca revisar qué está indicando antes de seguir con los siguientes pasos.

### Paso 8. Reconocer y resolver el error de tabla inexistente

![Paso 8: error de tabla inexistente](Imagenes/Img8.png)

En esta parte me apareció un error de MySQL que decía que no existía la tabla `sessions` dentro de la base de datos `laravel`. Esto puede pasar cuando Laravel está configurado para guardar las sesiones en la base de datos, pero todavía no se ha creado la tabla que necesita.

Lo primero que revisé fue que el archivo `.env` apuntara a la base de datos correcta y que las migraciones se hubieran ejecutado. Para comprobar las migraciones, volví a ejecutar:

```bat
php artisan migrate
```

Si el error continúa, también hay que revisar si el proyecto tiene una migración para crear la tabla `sessions`. La solución depende de la versión y de la configuración que tenga Laravel, así que conviene revisar eso antes de crear o modificar tablas.

Importante: no borres las tablas ni ejecutes comandos que eliminen datos sin comprobar primero qué hacen.

### Paso 9. Volver a comprobar la página de Laravel

![Paso 9: volver a comprobar Laravel](Imagenes/Img9.png)

Después de revisar la configuración, volví al navegador y actualicé la página para comprobar si el error había desaparecido. Si todavía aparece, hay que leer el mensaje y seguir revisando la causa; no basta con actualizar la página si el problema sigue ahí.

### Paso 10. Instalar los paquetes de frontend

![Paso 10: instalar dependencias de frontend](Imagenes/Img10.png)

Luego, desde la terminal y dentro de `Lab_Laravel`, ejecuté:

```bat
npm install
```

Este comando instala los paquetes de frontend que están definidos en `package.json`. Esperé a que terminara y revisé el resultado que apareció en la terminal.

### Paso 11. Comprobar las migraciones aplicadas

![Paso 11: comprobar las migraciones](Imagenes/Img11.png)

Después revisé el resultado de las migraciones en la terminal. Entre los mensajes que pueden aparecer están `Preparing database`, `Creating migration table` y `Running migrations`, seguidos de los nombres de las tablas. Eso indica que Laravel está preparando la base de datos y ejecutando las migraciones que faltan.

### Paso 12. Revisar la estructura de la base de datos

![Paso 12: revisar tablas de la base de datos](Imagenes/Img12.png)

Después abrí phpMyAdmin, seleccioné la base de datos que tenía configurada en `.env` y revisé que aparecieran las tablas creadas por las migraciones, como `users`, `cache` y `jobs`, dependiendo de las migraciones del proyecto. Así pude comprobar también desde MySQL que las tablas estuvieran creadas.

### Paso 13. Ejecutar el entorno de desarrollo

![Paso 13: ejecutar el entorno de desarrollo](Imagenes/Img13.png)

Más adelante, comprobé que seguía dentro de la carpeta del proyecto y ejecuté este comando para iniciar el entorno de desarrollo:

```bat
composer run dev
```

En mi caso, el comando podía iniciar varios procesos, como el servidor de Laravel y Vite. Revisé la terminal para comprobar que se estuvieran ejecutando. Si no te reconoce `composer run dev`, puedes iniciar los procesos por separado con los comandos que tenga tu proyecto.

### Paso 14. Instalar Laravel UI

![Paso 14: instalar Laravel UI](Imagenes/Img14.png)

Después instalé Laravel UI. Para eso, desde la terminal dentro de `Lab_Laravel`, escribí:

```bat
composer require laravel/ui
```

Con este comando agregué el paquete `laravel/ui`, que utilicé para generar los recursos de interfaz y las vistas de autenticación con Bootstrap. Si Composer muestra algún conflicto, revisa las versiones instaladas de Laravel y del paquete.

### Paso 15. Generar Bootstrap y las vistas de autenticación

![Paso 15: generar Bootstrap y autenticación](Imagenes/Img15.png)

Cuando terminó la instalación, ejecuté el comando para generar el scaffolding de Bootstrap:

```bat
php artisan ui bootstrap
```

Con esto se generó la estructura inicial de frontend para Bootstrap. Después escribí el siguiente comando para generar también las vistas de autenticación:

```bat
php artisan ui bootstrap --auth
```

La opción `--auth` agrega las vistas de inicio de sesión, registro y otras pantallas de autenticación. En mi terminal apareció una pregunta sobre un archivo que ya existía; si te pasa lo mismo, lee bien el mensaje antes de elegir si quieres sobrescribirlo.

### Paso 16. Instalar y compilar los recursos de Bootstrap

![Paso 16: instalar y compilar recursos](Imagenes/Img16.png)

Después de generar los archivos de Bootstrap, volví a instalar las dependencias con:

```bat
npm install
```

Luego ejecuté el comando para compilar los recursos del frontend:

```bat
npm run dev
```

Este proceso compila los archivos CSS y JavaScript del proyecto. Dejé la terminal abierta mientras trabajaba con Vite. Si te aparece un error con `npm`, revisa que Node.js y npm estén instalados correctamente.

### Paso 17. Comprobar las vistas de autenticación

![Paso 17: comprobar las vistas de autenticación](Imagenes/Img17.png)

Con los recursos generados, volví a abrir la aplicación en el navegador para revisar si aparecían las opciones o formularios de autenticación. Si no aparecen, revisa que hayas ejecutado `php artisan ui bootstrap --auth`, que `npm install` haya terminado y que el servidor siga activo. El resultado también puede depender de la versión de Laravel que tengas.

### Paso 18. Comprobación final del proyecto

![Paso 18: comprobar el proyecto](Imagenes/Img18.png)

Y para terminar, volví al navegador y actualicé la aplicación para revisar cómo había quedado. Comprobé que el servidor siguiera activo, que los recursos del frontend se hubieran compilado y que las páginas generadas se pudieran visualizar. Con esto terminé el recorrido: creé el proyecto, preparé la base de datos, ejecuté las migraciones e incorporé las vistas de autenticación con Bootstrap.

## Comandos principales utilizados

### Crear un proyecto Laravel

```bash
laravel new NombreProyecto
```

Como alternativa, se puede utilizar Composer:

```bash
composer create-project laravel/laravel mi-proyecto
```

### Ejecutar migraciones

```bash
php artisan migrate
```

### Limpiar y reconstruir la configuración

```bash
php artisan config:clear
php artisan config:cache
```

### Iniciar el servidor de desarrollo

```bash
php artisan serve
```

### Instalar Laravel UI y generar las vistas

```bash
composer require laravel/ui
php artisan ui bootstrap
php artisan ui bootstrap --auth
```

### Instalar y ejecutar dependencias del frontend

```bash
npm install
npm run dev
```

En proyectos que tengan configurado el script correspondiente en `composer.json`, también se puede utilizar:

```bash
composer run dev
```

Este comando puede iniciar conjuntamente el servidor de Laravel y Vite, según la configuración del proyecto.

## Configuración de la base de datos

La conexión con MySQL se configura en el archivo `.env`, ubicado en la raíz del proyecto. Los parámetros deben adaptarse a la configuración del entorno local utilizado. Por ejemplo:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nombre_de_la_base_de_datos
DB_USERNAME=root
DB_PASSWORD=
```

Después de modificar las variables de entorno, se recomienda limpiar la caché de configuración antes de volver a ejecutar las migraciones.

## About Laravel

Laravel es un framework para aplicaciones web con una sintaxis expresiva y elegante. Facilita tareas comunes del desarrollo web, como:

- Enrutamiento rápido y sencillo.
- Contenedor de inyección de dependencias.
- Gestión de sesiones y caché.
- ORM para trabajar con bases de datos mediante Eloquent.
- Migraciones de esquemas de base de datos.
- Procesamiento de trabajos en segundo plano.
- Difusión de eventos en tiempo real.

Laravel ofrece herramientas para desarrollar aplicaciones web robustas y mantenibles.

## Learning Laravel

La documentación oficial de Laravel incluye guías y ejemplos para aprender a utilizar el framework:

- [Documentación oficial de Laravel](https://laravel.com/docs)
- [Laravel Learn](https://laravel.com/learn)
- [Laracasts](https://laracasts.com)

## Agentic Development

Laravel también dispone de herramientas para flujos de desarrollo asistidos por agentes de programación. Una de ellas es Laravel Boost, cuya documentación se encuentra en [Laravel AI](https://laravel.com/docs/ai).

Los comandos de instalación que aparecen en la documentación de Boost son:

```bash
composer require laravel/boost --dev
php artisan boost:install
```

Estos comandos son información complementaria de Laravel y no forman parte de los pasos principales documentados en este laboratorio.

## Contributing

Este repositorio documenta una práctica académica. Para conocer las pautas de contribución al framework Laravel, consulta la [guía oficial de contribuciones](https://laravel.com/docs/contributions).

## Code of Conduct

Laravel mantiene un código de conducta para fomentar una comunidad respetuosa e inclusiva. Puede consultarse en el [Código de Conducta de Laravel](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

Para obtener información sobre cómo reportar vulnerabilidades de seguridad en el framework Laravel, consulta la [documentación oficial de seguridad](https://laravel.com/docs).

## License

Laravel es software de código abierto distribuido bajo la licencia [MIT](https://opensource.org/licenses/MIT).

## Conclusión

Durante este laboratorio se recorrieron los procedimientos básicos para comenzar a desarrollar una aplicación utilizando Laravel. Se revisó el entorno local, se ejecutaron comandos desde la terminal, se trabajó con la configuración de la base de datos y se exploró el uso de migraciones.

También se documentó la ejecución de la aplicación en el navegador y la generación de vistas de autenticación mediante Laravel UI y Bootstrap, siguiendo los pasos indicados en la guía.

Las capturas conservan evidencia del desarrollo de la práctica, incluyendo las comprobaciones realizadas y los errores encontrados durante el proceso.

## Referencia académica

**Guía de Laboratorio: Introducción al Framework Laravel – MVC.** Universidad Tecnológica de Panamá, Facultad de Ingeniería en Sistemas Computacionales, asignatura de Desarrollo Web. Docente: Ing. Irina Fong.

---

<p align="center">Laboratorio realizado por <strong>Vasdti Legaspi</strong> · 23 de octubre de 2026.</p>
