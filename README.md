# Curso de SQL por soy dalto

## Indice
1. [¿Qué es SQL?](#qué-es-sql)
2. [¿Para qué sirve SQL?](#para-qué-sirve-sql)
3. [Notación de Chen](#notación-de-chen)
4. [Crear DATABASE](#crear-una-base-de-datos)
5. [Talbas, Campos y registros](#tablas-campos-y-registros)
6. [Creación de tablas](#creación-de-tablas)
---
## ¿Qué es SQL?
SQL (Structured Query Language) es un lenguaje estándar para gestionar y manipular bases de datos relacionales, permitiendo realizar 
consultas, inserciones, actualizaciones y eliminación de datos, así como definir y controlar la estructura de las bases.

## ¿Para qué sirve SQL?
SQL sirve para:  
- **Consultar datos**: Recuperar información específica de una base de datos.  
- **Manipular datos**: Insertar, actualizar y eliminar registros.  
- **Actualizar datos**: Modificar registros existentes sin eliminarlos.  
- **Administrar bases de datos**: Crear, modificar y eliminar tablas y esquemas.  
- **Controlar acceso**: Definir permisos y roles de usuario.  
- **Garantizar integridad**: Implementar restricciones y relaciones entre datos.

## Notación de Chen  
La **notación de Chen** es una forma de representar diagramas entidad-relación (ER), utilizada en el modelado de bases de datos.  
Fue propuesta por Peter Chen en 1976 y se caracteriza por:  

- **Entidades**: Representadas con **rectángulos**. Las entidades corresponden a objetos o conceptos del mundo real que necesitan ser almacenados en la base de datos.  

- **Atributos**: Representados con **óvalos** conectados a las entidades. Existen diferentes tipos:  
  - **Simples**: Contienen datos únicos y no se componen de otros atributos.  
    *Ejemplo*: Nombre o Identificación.  
  - **Compuestos**: Se descomponen en múltiples sub-atributos más pequeños.  
    *Ejemplo*: Un atributo "Ambiente" que se compone de **tipo** (living o comedor) y **tamaño**.  
  - **Multivalorados**: Representados con **dobles óvalos**. Son aquellos que pueden tener más de un valor.  
    *Ejemplo*: Un atributo "Ventanas" para una habitación puede incluir múltiples ventanas.  
  - **Derivados**: Atributos obtenidos a partir de otros, representados con **óvalos de borde punteado**.  
    *Ejemplo*: La edad, derivada de la fecha de nacimiento.  

- **Relaciones**: Representadas con **rombos**, que conectan dos o más entidades, describiendo cómo se relacionan entre sí.  

- **Cardinalidad**: Define el número mínimo y máximo de ocurrencias entre entidades relacionadas. Esto permite entender la cantidad de instancias que participan en una relación (por ejemplo, "un cliente puede tener varias cuentas bancarias").  

![Notación de chen](./images/Notación%20de%20Chen.png)

---
## Crear una base de datos
Para crear una base de datos utilizaremos el comando:

```
CREATE DATABASE "nombre_de_la_base_de_datos"
```
y para utilizar dicha tabla utilizamos el comando:

```
USE "nombre_de_la_base_de_datos"
```
Aquí tienes una explicación clara:  

## Tablas, Campos y Registros 

- **Tabla**:  
  Es una estructura de datos dentro de una base de datos que organiza la información en filas y columnas. Cada tabla se enfoca en un tema específico (por ejemplo, una tabla de *Clientes* o *Productos*).  

  **Ejemplo de tabla "Clientes"**:  
  | ID | Nombre  | Email              | Teléfono  |
  |----|---------|--------------------|-----------|
  | 1  | Juan    | juan@gmail.com     | 123456789 |
  | 2  | María   | maria@gmail.com    | 987654321 |

---

- **Campo (Columna)**:  
  Cada columna en una tabla representa un **campo**, que almacena un tipo específico de dato para todos los registros. Es como una categoría o atributo de la información.  
  - **Ejemplo**: En la tabla anterior, "Nombre", "Email" y "Teléfono" son campos.

---

- **Registro (Fila)**:  
  Un **registro** es una fila en la tabla, que almacena una instancia completa de datos según los campos definidos. Cada registro representa una unidad específica de información.  
  - **Ejemplo**: La fila con `ID = 1` corresponde al registro del cliente "Juan".  

En resumen:  
- **Tabla**: Estructura que organiza datos.  
- **Campos**: Categorías o atributos de datos.  
- **Registros**: Cada unidad específica de información (fila) en una tabla

### Creación de tablas
Al crear tablas en una base de datos, puedes utilizar varios tipos de datos para definir las columnas de la tabla. Aquí hay una lista de tipos de datos comunes que puedes usar, aunque los nombres y la disponibilidad pueden variar según el sistema de gestión de bases de datos (DBMS) que estés utilizando:

#### Tipos de datos numéricos
- **INT**: Número entero. Dependiendo del DBMS, puedes tener variantes como `TINYINT`, `SMALLINT`, `MEDIUMINT`, `BIGINT`.
- **FLOAT**: Número de punto flotante de precisión simple.
- **DOUBLE**: Número de punto flotante de precisión doble.
- **DECIMAL(p,s)**: Número decimal con precisión fija, donde `p` es el total de dígitos y `s` es el número de dígitos a la derecha del punto decimal.

#### Tipos de datos de cadena
- **CHAR(n)**: Cadena de caracteres de longitud fija. Si el contenido es más corto que `n`, se rellenará con espacios.
- **VARCHAR(n)**: Cadena de caracteres de longitud variable con un máximo de `n` caracteres.
- **TEXT**: Cadena de caracteres de longitud variable que puede contener hasta 65,535 caracteres (o más, dependiendo del DBMS).
- **BLOB**: Objeto binario grande, usado para almacenar datos binarios como imágenes o archivos.

#### Tipos de datos de fecha y hora
- **DATE**: Fecha en formato `YYYY-MM-DD`.
- **TIME**: Hora en formato `HH:MM:SS`.
- **DATETIME**: Combinación de fecha y hora en formato `YYYY-MM-DD HH:MM:SS`.
- **TIMESTAMP**: Marca de tiempo que representa el número de segundos desde el 1 de enero de 1970.
- **YEAR**: Representa un año en formato `YYYY`.

#### Tipos de datos booleanos
- **BOOLEAN**: Representa un valor verdadero o falso (a menudo almacenado como 0 para falso y 1 para verdadero).

#### Otros tipos de datos
- **ENUM**: Una cadena que puede tener un valor de una lista de valores predefinidos.
- **SET**: Una cadena que puede tener cero o más valores de una lista de valores predefinidos.

#### Ejemplo de creación de tabla
Aquí hay un ejemplo básico de cómo definir una tabla utilizando algunos de estos tipos de datos en SQL:

```sql
CREATE TABLE usuarios (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100),
    apellido VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    fecha_nacimiento DATE,
    activo BOOLEAN DEFAULT TRUE
);
```
