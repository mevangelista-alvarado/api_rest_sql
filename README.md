# API Rest SQL
Ejemplo de una API REST con SQL DB + Docker

# Clonar repo
## Opción 1 (Manual)
 1.- Hacer click en el botón __CODE <>__  
 2.- Hacer click en el botón __Download ZIP__   
<img width="407" alt="image" src="https://github.com/user-attachments/assets/ec0e5f1e-3254-4d2b-9b69-f19c88e9c205" />

## Opción 2 (Terminal) 
Ejecutar  
```
  git clone https://github.com/mevangelista-alvarado/api_rest_sql.git 
```

# Docker
## Primera Vez
Antes de iniciar, asegúrate de copiar el archivo `.env.example` a `.env` y ajustarlo con tu configuración:
```
cp .env.example .env
```
1.- Ejecutar en terminal (en la carpeta donde esté el archivo `docker-compose.yml`)  
```
  docker-compose up --build
```
Asegúrate también de tener el archivo `.env` configurado antes de ejecutar los comandos.
2.- Abrir un terminal nueva y ejecutar en terminal (en la carpeta donde esté el archivo `docker-compose.yml` & `init_db.py`)  
```
  docker-compose exec web python init_db.py
```
3.- Visitar en su navegador [http://localhost:5050/](http://localhost:5050/)  

## Si NO es la primera vez
1.- Ejecutar en terminal (en la carpeta donde esté el archivo `docker-compose.yml`)
```
  docker-compose up
```
Verifica que el archivo `.env` esté correctamente configurado.
2.- Visitar en su navegador [http://localhost:5050/](http://localhost:5050/)

# PostgreSQL
Para probar PostgreSQL, vaya a Docker Desktop y seleccione (dar click) el servicio de postgres (db-1) 

<img width="574" alt="image" src="https://github.com/user-attachments/assets/96dce66f-5f5c-45fd-ac78-36c4c1dfa91d" />

Después damos click en terminal  

<img width="404" alt="image" src="https://github.com/user-attachments/assets/c60c99a9-465f-46e1-9798-15a6033d9c4a" />
  
Ejecute 
```
psql -U postgres
```
<img width="378" alt="image" src="https://github.com/user-attachments/assets/e577913f-e190-4067-900b-a36117d3d4ad" />

Y ya estará dentro de la terminal de Postgres

## Consultado el contenido de una base de datos

Para listar bases de datos, ejecute
```
\l 
```
<img width="884" alt="image" src="https://github.com/user-attachments/assets/fc7f1f9a-68d3-49ae-b1c8-34b4adece61d" />

Para conectarte a la base de datos `postdb`
```
\c postdb
```
<img width="486" alt="image" src="https://github.com/user-attachments/assets/b828723b-bc87-4101-9aa7-307b152bcef7" />

Para listar tablas de la base de datos `postdb `
```
\d    
```
<img width="445" alt="image" src="https://github.com/user-attachments/assets/8845a0ae-38dc-4d06-a1ed-af8600ee29e4" />

Por último, para obtener todas las filas de la tabla `post`
```
SELECT * FROM post;
```
<img width="454" alt="image" src="https://github.com/user-attachments/assets/365a5005-e12a-4c65-9669-aae5b79ee444" />

# Configuración del archivo .env

Para configurar las variables de entorno necesarias, asegúrate de tener un archivo `.env` en la raíz del proyecto.

Puedes usar el archivo `.env.example` como base. Solo necesitas copiarlo y renombrarlo:
```
cp .env.example .env
```

Asegúrate de revisar y modificar los valores del archivo `.env` según tu configuración. Estas son las variables que debes establecer:
```
- `POSTGRES_USER`: Usuario de PostgreSQL (por defecto: `postgres`)
- `POSTGRES_PASSWORD`: Contraseña de PostgreSQL (por defecto: `postgres`)
- `POSTGRES_DB`: Nombre de la base de datos (por defecto: `postdb`)
- `POSTGRES_HOST`: Host del contenedor PostgreSQL (por defecto: `db`)
- `POSTGRES_PORT`: Puerto del servicio PostgreSQL (por defecto: `5432`)
- `DATABASE_URL`: Cadena de conexión completa (por ejemplo: `postgresql://postgres:postgres@db:5432/postdb`)
- `FLASK_ENV`: Entorno de ejecución (por ejemplo: `development` o `production`)
- `SECRET_KEY`: Clave secreta para la aplicación Flask
```


Estas variables son utilizadas por la aplicación para conectarse a la base de datos y configurar el entorno de ejecución.
