# Apuntes básicos de MySQL / MariaDB

## Ingresar a MySQL

Para ingresar a MySQL usando el usuario root:

```sql
mysql -u root -p
```

Después el sistema pedirá la contraseña.

---

# Bases de datos

## Ver todas las bases de datos

Para listar todas las bases de datos existentes:

```sql
SHOW DATABASES;
```

## Crear una base de datos

Para crear una nueva base de datos:

```sql
CREATE DATABASE db_biblioteca;
```

## Usar una base de datos

Para ingresar a una base de datos:

```sql
USE db_biblioteca;
```

---

# Tablas

## Ver tablas existentes

```sql
SHOW TABLES;
```

---

# Crear tabla Autor

Esta tabla guarda la información de los autores.

```sql
CREATE TABLE autor(
    id_autor INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL
);
```

### Explicación
- **id_autor**: identificador único del autor.  
- **PRIMARY KEY**: clave primaria.  
- **AUTO_INCREMENT**: el valor aumenta automáticamente.  
- **nombre**: nombre del autor y no puede ser vacío.

---

# Ver estructura de una tabla

Para ver los atributos o columnas de una tabla:

```sql
DESCRIBE autor;
```

---

# Crear tabla Libro

Esta tabla almacena información sobre los libros.

```sql
CREATE TABLE libro(
    cod_libro INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(255) NOT NULL,
    nro_paginas INT CHECK(nro_paginas > 0),
    isbn VARCHAR(10),
    editorial VARCHAR(100) NOT NULL
);
```

### Explicación

- **cod_libro**: identificador único del libro.  
- **titulo**: título del libro.  
- **nro_paginas**: número de páginas (debe ser mayor que 0).  
- **isbn**: código identificador del libro.  
- **editorial**: nombre de la editorial.

---

# Tabla de relación

La tabla **escribe** sirve para relacionar **autores con libros**.

Un autor puede escribir varios libros y un libro puede tener varios autores.

```sql
CREATE TABLE escribe(
    id_autor INT NOT NULL,
    cod_libro INT NOT NULL,
    fecha DATE DEFAULT CURRENT_TIMESTAMP
);
```

### Explicación

- **id_autor**: identifica al autor.  
- **cod_libro**: identifica al libro.  
- **fecha**: fecha en que se registró la relación.

---

# Claves foráneas (Foreign Keys)

## Relación con la tabla Autor

```sql
ALTER TABLE escribe
ADD CONSTRAINT fk_autor
FOREIGN KEY (id_autor)
REFERENCES autor(id_autor)
ON DELETE CASCADE
ON UPDATE CASCADE;
```

## Relación con la tabla Libro

```sql
ALTER TABLE escribe
ADD CONSTRAINT fk_libro
FOREIGN KEY (cod_libro)
REFERENCES libro(cod_libro)
ON DELETE CASCADE
ON UPDATE CASCADE;
```

---

# Explicación de CASCADE

## ON DELETE CASCADE

Significa que **si se elimina un registro de la tabla principal**, también se eliminarán automáticamente los registros relacionados en la tabla secundaria.

Ejemplo:

```sql
DELETE FROM autor WHERE id_autor = 1;
```

También se eliminarán los registros relacionados en la tabla **escribe**.

---

## ON UPDATE CASCADE

Significa que **si cambia la clave primaria en la tabla principal**, ese cambio se actualizará automáticamente en las tablas relacionadas.

---

# Resumen

- **SHOW DATABASES** → muestra las bases de datos.  
- **CREATE DATABASE** → crea una base de datos.  
- **USE** → selecciona una base de datos.  
- **SHOW TABLES** → muestra las tablas.  
- **CREATE TABLE** → crea tablas.  
- **DESCRIBE** → muestra la estructura de una tabla.  
- **FOREIGN KEY** → crea relaciones entre tablas.  
- **CASCADE** → mantiene la integridad de los datos eliminando o actualizando registros relacionados automáticamente.
