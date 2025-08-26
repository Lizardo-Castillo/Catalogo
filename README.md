# 🚀 Instalación de Laravel con React en Windows (Usando XAMPP)

Este documento detalla paso a paso cómo instalar y configurar un entorno Laravel + React en Windows utilizando XAMPP y Composer.

---

## 📦 Requisitos Previos

Antes de comenzar, asegúrate de tener instalado lo siguiente:

1. **XAMPP**  
   Descárgalo desde: [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)

2. **Composer**  
   Descárgalo desde: [https://getcomposer.org/](https://getcomposer.org/)

3. **Node.js y npm**  
   Descárgalo desde: [https://nodejs.org/](https://nodejs.org/)

---

## ✅ Verificar Instalación

Abre una terminal y ejecuta los siguientes comandos:

```bash
# Verificar Composer
composer --version

# Verificar XAMPP (iniciar desde el Panel de Control)
# Asegúrate de que Apache y MySQL funcionen correctamente
```

---

## ⚙️ Instalación de Laravel

1. Instalar el instalador global de Laravel:

```bash
composer global require laravel/installer
```

2. Verificar que Laravel esté instalado correctamente:

```bash
laravel --version
composer global show
```

---

## 🧱 Crear un Proyecto Laravel

Para crear un nuevo proyecto Laravel:

```bash
# Reemplaza 'example-project' por el nombre que desees
laravel new example-project
```

### ⚛️ Selección de Stack Frontend

Durante la instalación, se te pedirá elegir:

* **Frontend**: Selecciona `React`
* **Autenticación**: Selecciona `Laravel`
* **Framework de Testing**: Selecciona `Pest`

Una vez creado el proyecto, accede a la carpeta:

```bash
cd example-project
```

---

## 🛠 Inicializar el Proyecto

### 1. Habilitar extensión `zip` en PHP

Abre el archivo:

```
C:\xampp\php\php.ini
```

Busca (línea ~962):

```ini
;extension=zip
```

Y descoméntala (quita el `;`):

```ini
extension=zip
```

Guarda el archivo y reinicia Apache desde el Panel de XAMPP.

---

### 2. Instalar Dependencias

Desde la terminal, ubicado en la raíz del proyecto, ejecuta:

```bash
composer install
npm install
npm run build
```

---

### 3. Iniciar XAMPP

Abre el **Panel de Control de XAMPP** e inicia los siguientes servicios:

* ✅ Apache
* ✅ MySQL

> Asegúrate de que ambos servicios muestren el estado "Running" en color verde.

**⚠️ Nota**: Si algún puerto está ocupado, puedes cambiarlo desde la configuración de XAMPP (por ejemplo, Apache usa el puerto 80, y MySQL el 3306).

---

### 4. Configurar la Base de Datos

1. Abre tu navegador y ve a:
   [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

2. Crea una nueva base de datos (por ejemplo: `colegio`)
   Cotejamiento recomendado: `utf8mb4_general_ci`

3. Duplica el archivo `.env.example` y renómbralo a `.env`

4. Edita el archivo `.env` y configura la conexión a MySQL:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=colegio      # Nombre de la base de datos que creaste
DB_USERNAME=root
DB_PASSWORD=             # En blanco si no configuraste una contraseña
```

---

### 5. Generar Clave de Aplicación

```bash
php artisan key:generate
```

---

### 6. Ejecutar Migraciones

Para instalar las tablas por primera vez:

```bash
php artisan migrate
```

> Para limpiar la base de datos completamente:

```bash
php artisan migrate:reset
php artisan migrate
```

📌 **Comandos útiles:**

* `php artisan migrate`: Ejecuta migraciones nuevas
* `php artisan migrate:reset`: Elimina todas las tablas
* `php artisan db:seed`: Agrega datos de prueba (si existen seeders configurados)

---

## ▶️ Ejecutar el Proyecto

### Requisitos antes de ejecutar:

* XAMPP corriendo con Apache y MySQL activos
* Base de datos configurada en `.env`
* Migraciones ejecutadas correctamente
* Dependencias instaladas

### Iniciar servidor de desarrollo:

```bash
composer run dev
```

> Este comando inicia el entorno con Laravel + React compilado.

---

## 🧪 Otros Comandos Útiles

* Ejecutar servidor local:

```bash
php artisan serve
```

* Compilar assets en tiempo real:

```bash
npm run dev
```

* Compilar assets para producción:

```bash
npm run build
```

---

## 💡 Notas Finales

* Siempre que hagas cambios en `.env`, ejecuta:

```bash
php artisan config:cache
```

* Si tienes errores de permisos en Windows, intenta correr la terminal como administrador.

---

## ✅ Si todo está bien...

Deberías poder acceder al proyecto desde tu navegador:

```
http://localhost:8000
```

---

¡Listo! 🎉 Ya tienes un entorno Laravel + React completamente funcional en tu máquina Windows.
