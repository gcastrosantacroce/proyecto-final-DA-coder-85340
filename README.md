## PROYECTO FINAL CODER DATA ANALYTICS 85340

# Alumno: Castro Santacroce Gonzalo

## Introducción:

Este proyecto explora un conjunto de datos históricos de los Juegos Olímpicos modernos, centrándose en el rendimiento de los atletas tanto en los Juegos de verano como en los de invierno, desde los Juegos de Atenas de 1896 hasta los Juegos de Río de 2016. El conjunto de datos, extraído de Sports Reference en Mayo de 2018, contiene más de 270.000 registros de eventos de atletas, lo que ofrece una visión general amplia de las tendencias olímpicas durante más de un siglo.


### Objetivos y situación problemática

En este proyecto, analizaremos los datos olímpicos con el objetivo de descubrir tendencias en la participación de los atletas, los logros de medallas y la popularidad del deporte a lo largo del tiempo. El análisis se centrará principalmente en:

-	Participación de los deportistas por género, país y deporte.
-	Recuento de medallas y distribución entre países y deportes.
-	Los conocimientos sobre las tendencias olímpicas después de que los juegos de verano y de invierno fueran escalonados posterior a 1992.

Finalmente, los conocimientos obtenidos del análisis, se presentaran en un panel interactivo, que permita la exploración visual de tendencias y patrones olímpicos claves.

### Detalle del Dataset

El archivo principal, atleta_events.csv, contiene 15 columnas que detallan el desempeño de los atletas individuales en varios eventos durante los Juegos de verano e invierno. La información clave incluye:
-	ID: Identificador único para cada deportista
-	Name: Nombre completo del atleta
-	Sex: Género (M o F)
-	Age: Edad del deportista en el momento de la competición.
-	Height: Altura en centímetros
-	Weight: Peso en kilogramos
-	Team: Nombre del equipo o país
-	NOC: Código de 3 letras del Comité Olímpico Nacional
-	Games: Año y temporada de los Juegos
-	Year: Año del evento
-	Season: Juegos de verano o invierno
-	City: Ciudad anfitriona del evento
-	Sport: Categoría deportiva
-	Event: Evento específico dentro del deporte
-	Medal: Medalla ganada (Oro, Plata, Bronce o NA)



## DIAGRAMA ENTIDAD RELACIÓN (DER):

### Diagrama de Entidad Relación Simplificado:

```plaintext
+---------------------+     +----------------------+     +-------------------+     +-------------------+     +-------------------+
|      ATLETA         |     |      JUEGO           |     |     DEPORTE        |     |     EVENTO         |     |      MEDALLA       |
+---------------------+     +----------------------+     +-------------------+     +-------------------+     +-------------------+
| PK  | ID            |     | PK  | ID_Juego       |     | PK  | ID_Deporte    |     | PK  | ID_Evento    |     | PK  | ID_Medalla    |
|     | Name          |     |     | Games          |     |     | Sport         |     |     | Event        |     |     | Medal        |
|     | Sex           |     |     | Year           |     |                   |     |                   |     |                   |
|     | Age           |     |     | Season         |     |                   |     |                   |     |                   |
|     | Height        |     |     | City           |     |                   |     |                   |     |                   |
|     | Weight        |     |                     |     |                   |     |                   |     |                   |
|     | Team          |     |                     |     |                   |     |                   |     |                   |
|     | NOC           |     |                     |     |                   |     |                   |     |                   |
+---------------------+     +----------------------+     +-------------------+     +-------------------+     +-------------------+

             |                          |                         |                          |
             |                          |                         |                          |
             v                          v                         v                          v
+------------------------+     +------------------------+     +------------------------+     +------------------------+
|   ATLETA_JUEGO         |     |    ATLETA_EVENTO       |     |   ATLETA_MEDALLA        |     |                        |
+------------------------+     +------------------------+     +------------------------+     |                        |
| FK  | ID_Atleta         |     | FK  | ID_Atleta        |     | FK  | ID_Atleta          |     |                        |
| FK  | ID_Juego          |     | FK  | ID_Evento       |     | FK  | ID_Medalla         |     |                        |
+------------------------+     +------------------------+     +------------------------+     |                        |
```

### Descripción del Diagrama:

1. **Entidades**:
   - **ATLETA**: Representa a los atletas que participaron en los juegos. Atributos importantes: `ID`, `Name`, `Sex`, `Age`, `Height`, `Weight`, `Team`, `NOC`.
   - **JUEGO**: Representa los juegos olímpicos. Atributos importantes: `ID_Juego`, `Games`, `Year`, `Season`, `City`.
   - **DEPORTE**: Representa los deportes de los juegos olímpicos. Atributos importantes: `ID_Deporte`, `Sport`.
   - **EVENTO**: Representa los eventos dentro de un juego olímpico (por ejemplo, "100 metros" en atletismo). Atributos importantes: `ID_Evento`, `Event`.
   - **MEDALLA**: Representa los tipos de medallas ganadas en los eventos. Atributos importantes: `ID_Medalla`, `Medal`.

2. **Relaciones**:
   - **ATLETA_JUEGO**: Relaciona a los atletas con los juegos en los que participaron. Relaciona las claves foráneas `ID_Atleta` y `ID_Juego`.
   - **ATLETA_EVENTO**: Relaciona a los atletas con los eventos en los que participaron. Relaciona las claves foráneas `ID_Atleta` y `ID_Evento`.
   - **ATLETA_MEDALLA**: Relaciona a los atletas con las medallas que ganaron. Relaciona las claves foráneas `ID_Atleta` y `ID_Medalla`.

### Relaciones en el diagrama:
- **ATLETA** tiene una relación con **JUEGO**, **EVENTO** y **MEDALLA** a través de las tablas de relación **ATLETA_JUEGO**, **ATLETA_EVENTO** y **ATLETA_MEDALLA**.
- Cada **JUEGO** tiene muchos **ATLETAS** (relación muchos a muchos).
- Cada **EVENTO** puede tener muchos **ATLETAS** (relación muchos a muchos).
- Un **ATLETA** puede ganar varias **MEDALLAS** (relación muchos a muchos).

### Entidades:
1. **Atleta**
   - **ID** (Clave primaria)
   - **Name**
   - **Sex**
   - **Age**
   - **Height**
   - **Weight**
   - **Team**
   - **NOC**

2. **Juego**
   - **ID_Juego** (Clave primaria)
   - **Games**
   - **Year**
   - **Season**
   - **City**

3. **Deporte**
   - **ID_Deporte** (Clave primaria)
   - **Sport**

4. **Evento**
   - **ID_Evento** (Clave primaria)
   - **Event**

5. **Medalla**
   - **ID_Medalla** (Clave primaria)
   - **Medal** (Podría ser "Gold", "Silver", "Bronze" o "NA")

### Relaciones:
- **Atleta participa en Juego**
   - Un atleta puede participar en varios juegos.
   - Un juego tiene varios atletas.
   - Relación muchos a muchos entre Atleta y Juego.

- **Juego tiene Deporte**
   - Un juego tiene un solo deporte.
   - Un deporte puede estar presente en varios juegos.
   - Relación uno a muchos entre Juego y Deporte.

- **Atleta compite en Evento**
   - Un atleta puede competir en varios eventos dentro de un juego.
   - Un evento puede tener varios atletas compitiendo.
   - Relación muchos a muchos entre Atleta y Evento.

- **Atleta recibe Medalla**
   - Un atleta puede recibir una medalla en un evento específico.
   - Un evento puede tener varios atletas ganando medallas.
   - Relación uno a muchos entre Atleta y Medalla.

### Ejemplo de cómo se conectarían las tablas:
- **Atleta (ID)** → **Atleta_Juego (ID_Atleta, ID_Juego)** (Relación de muchos a muchos)
- **Juego (ID_Juego)** → **Deporte (ID_Deporte)** (Uno a muchos)
- **Atleta (ID_Atleta)** → **Evento (ID_Evento)** (Relación de muchos a muchos)
- **Atleta (ID_Atleta)** → **Medalla (ID_Medalla)** (Uno a muchos)

### Listado de las tablas que comprenden la base de datos

Descripción detallada de las **tablas**, sus **atributos** y las **relaciones** que conforman el **Diagrama Entidad-Relación**:

### 1. **Tabla: Atleta**
   - **Descripción**: Esta tabla contiene la información de cada atleta que participa en los juegos olímpicos.
   - **Atributos**:
     - **ID**: Identificador único del atleta (clave primaria).
     - **Name**: Nombre del atleta.
     - **Sex**: Sexo del atleta (M para masculino, F para femenino).
     - **Age**: Edad del atleta.
     - **Height**: Altura del atleta en centímetros.
     - **Weight**: Peso del atleta en kilogramos.
     - **Team**: Nombre del equipo o país al que pertenece el atleta.
     - **NOC**: Código del Comité Olímpico Nacional (National Olympic Committee).
   
### 2. **Tabla: Juego**
   - **Descripción**: Esta tabla almacena la información sobre los juegos olímpicos en los que los atletas participan.
   - **Atributos**:
     - **ID_Juego**: Identificador único del juego (clave primaria).
     - **Games**: Nombre del evento o edición de los juegos (por ejemplo, "1992 Summer").
     - **Year**: Año en que se celebraron los juegos olímpicos.
     - **Season**: Temporada del evento ("Summer" para los juegos de verano y "Winter" para los juegos de invierno).
     - **City**: Ciudad que fue sede de los juegos olímpicos.

### 3. **Tabla: Deporte**
   - **Descripción**: Esta tabla contiene la información sobre los deportes en los que los atletas compiten durante los juegos.
   - **Atributos**:
     - **ID_Deporte**: Identificador único del deporte (clave primaria).
     - **Sport**: Nombre del deporte (por ejemplo, "Basketball", "Judo").

### 4. **Tabla: Evento**
   - **Descripción**: En esta tabla se registran los diferentes eventos de un deporte específico durante los juegos.
   - **Atributos**:
     - **ID_Evento**: Identificador único del evento (clave primaria).
     - **Event**: Descripción del evento (por ejemplo, "Basketball Men's Basketball", "Judo Men's Extra-Lightweight").

### 5. **Tabla: Medalla**
   - **Descripción**: Esta tabla contiene la información sobre las medallas ganadas por los atletas en los eventos.
   - **Atributos**:
     - **ID_Medalla**: Identificador único de la medalla (clave primaria).
     - **Medal**: Tipo de medalla (por ejemplo, "Gold", "Silver", "Bronze", o "NA" si no ganó medalla).

---

### **Relaciones entre las tablas**:

1. **Atleta participa en Juego**:
   - **Tipo de relación**: Muchos a Muchos.
   - **Descripción**: Un atleta puede participar en varios juegos olímpicos, y un juego olímpico puede tener muchos atletas participando.
   - **Implementación**: Para representar esta relación en la base de datos, se utiliza una tabla intermedia llamada **Atleta_Juego**, que tiene las claves foráneas de **ID (Atleta)** e **ID Juego**.

2. **Juego tiene Deporte**:
   - **Tipo de relación**: Uno a Muchos.
   - **Descripción**: Un juego olímpico puede tener múltiples deportes, pero un deporte específico pertenece solo a un juego olímpico determinado.
   - **Implementación**: La relación entre **Juego** y **Deporte** es uno a muchos, y la tabla **Juego** contiene una clave foránea a la tabla **Deporte**.

3. **Atleta compite en Evento**:
   - **Tipo de relación**: Muchos a Muchos.
   - **Descripción**: Un atleta puede competir en varios eventos dentro de un juego, y un evento puede tener varios atletas participando.
   - **Implementación**: Esta relación se maneja mediante una tabla intermedia llamada **Atleta_Evento**, que incluye las claves foráneas de **ID Atleta** e **ID Evento**.

4. **Atleta recibe Medalla**:
   - **Tipo de relación**: Uno a Muchos.
   - **Descripción**: Un atleta puede recibir una medalla en un evento específico, y cada medalla está asociada con un solo atleta.
   - **Implementación**: La relación entre **Atleta** y **Medalla** es uno a muchos, donde **Atleta** tiene una clave foránea en **Medalla**.

---

### Diagrama de Relaciones:

| Relación                        | Entidad 1        | Entidad 2        | Tipo de Relación |
|----------------------------------|------------------|------------------|------------------|
| **Participa en**                 | Atleta           | Juego            | Muchos a Muchos |
| **Tiene**                        | Juego            | Deporte          | Uno a Muchos    |
| **Compite en**                   | Atleta           | Evento           | Muchos a Muchos |
| **Recibe**                       | Atleta           | Medalla          | Uno a Muchos    |

Este es el diseño general de la base de datos, sus tablas y las relaciones. Con esta estructura, se puede almacenar y consultar fácilmente la información sobre atletas, juegos olímpicos, deportes, eventos y medallas.

### Descripcion de los tipos de datos por tabla:

### 1. **Tabla: Atleta**
   - **ID**: `INT` (Entero). Es la clave primaria, por lo que debe ser único y no nulo.
   - **Name**: `VARCHAR(255)` (Cadena de texto). Almacena el nombre completo del atleta.
   - **Sex**: `CHAR(1)` (Carácter). Puede almacenar un solo carácter, por ejemplo, "M" para masculino y "F" para femenino.
   - **Age**: `INT` (Entero). La edad del atleta.
   - **Height**: `INT` (Entero). Altura del atleta en centímetros (puede ser `NULL` si no está disponible).
   - **Weight**: `INT` (Entero). Peso del atleta en kilogramos (puede ser `NULL` si no está disponible).
   - **Team**: `VARCHAR(255)` (Cadena de texto). Nombre del equipo o país al que pertenece el atleta.
   - **NOC**: `CHAR(3)` (Cadena de 3 caracteres). Código del Comité Olímpico Nacional, que es un identificador estándar de tres letras (por ejemplo, "USA" para Estados Unidos).

### 2. **Tabla: Juego**
   - **ID_Juego**: `INT` (Entero). Es la clave primaria, por lo que debe ser único y no nulo.
   - **Games**: `VARCHAR(255)` (Cadena de texto). Nombre del evento o edición de los juegos (por ejemplo, "1992 Summer").
   - **Year**: `INT` (Entero). Año en que se celebraron los juegos olímpicos.
   - **Season**: `VARCHAR(10)` (Cadena de texto). Temporada de los juegos, puede ser "Summer" o "Winter".
   - **City**: `VARCHAR(255)` (Cadena de texto). Ciudad donde se celebraron los juegos olímpicos.

### 3. **Tabla: Deporte**
   - **ID_Deporte**: `INT` (Entero). Es la clave primaria, por lo que debe ser único y no nulo.
   - **Sport**: `VARCHAR(255)` (Cadena de texto). Nombre del deporte (por ejemplo, "Basketball", "Judo").

### 4. **Tabla: Evento**
   - **ID_Evento**: `INT` (Entero). Es la clave primaria, por lo que debe ser único y no nulo.
   - **Event**: `VARCHAR(255)` (Cadena de texto). Descripción del evento (por ejemplo, "Basketball Men's Basketball", "Judo Men's Extra-Lightweight").

### 5. **Tabla: Medalla**
   - **ID_Medalla**: `INT` (Entero). Es la clave primaria, por lo que debe ser único y no nulo.
   - **Medal**: `VARCHAR(20)` (Cadena de texto). Tipo de medalla (por ejemplo, "Gold", "Silver", "Bronze", o "NA" si no se ganó medalla).

---

### **Relaciones entre las tablas**:

1. **Atleta participa en Juego (Atleta_Juego)**
   - **ID_Atleta**: `INT` (Entero). Clave foránea que hace referencia a **ID** en la tabla **Atleta**.
   - **ID_Juego**: `INT` (Entero). Clave foránea que hace referencia a **ID_Juego** en la tabla **Juego**.

2. **Atleta compite en Evento (Atleta_Evento)**
   - **ID_Atleta**: `INT` (Entero). Clave foránea que hace referencia a **ID** en la tabla **Atleta**.
   - **ID_Evento**: `INT` (Entero). Clave foránea que hace referencia a **ID_Evento** en la tabla **Evento**.

3. **Atleta recibe Medalla (Atleta_Medalla)**
   - **ID_Atleta**: `INT` (Entero). Clave foránea que hace referencia a **ID** en la tabla **Atleta**.
   - **ID_Medalla**: `INT` (Entero). Clave foránea que hace referencia a **ID_Medalla** en la tabla **Medalla**.

### **Tipo de datos para tablas intermedias**:
- Las tablas intermedias como **Atleta_Juego**, **Atleta_Evento** y **Atleta_Medalla** suelen tener claves foráneas que se refieren a las claves primarias de las tablas relacionadas. Estas claves foráneas generalmente tienen el tipo de dato `INT` y actúan como enlaces entre las entidades.

---

### **Resumen de los tipos de datos**:


| **Tabla**        | **Atributo**         | **Tipo de Dato**    | **Descripción**                                                                 | **Tipo de Clave**        |
|------------------|----------------------|---------------------|---------------------------------------------------------------------------------|--------------------------|
| **Atleta**       | **ID**               | `INT`               | Identificador único del atleta, clave primaria.                                 | **PK**                   |
|                  | **Name**             | `VARCHAR(255)`      | Nombre completo del atleta.                                                     |                          |
|                  | **Sex**              | `CHAR(1)`           | Sexo del atleta (M = Masculino, F = Femenino).                                  |                          |
|                  | **Age**              | `INT`               | Edad del atleta.                                                                |                          |
|                  | **Height**           | `INT`               | Altura del atleta en centímetros.                                                |                          |
|                  | **Weight**           | `INT`               | Peso del atleta en kilogramos.                                                  |                          |
|                  | **Team**             | `VARCHAR(255)`      | Nombre del equipo o país al que pertenece el atleta.                           |                          |
|                  | **NOC**              | `CHAR(3)`           | Código del Comité Olímpico Nacional del atleta (por ejemplo, "USA" para EE.UU.).|                          |
| **Juego**        | **ID Juego**         | `INT`               | Identificador único del juego, clave primaria.                                  | **PK**                   |
|                  | **Games**            | `VARCHAR(255)`      | Nombre del evento o edición de los juegos (por ejemplo, "1992 Summer").         |                          |
|                  | **Year**             | `INT`               | Año en el que se celebraron los juegos olímpicos.                               |                          |
|                  | **Season**           | `VARCHAR(10)`       | Temporada del evento (puede ser "Summer" o "Winter").                           |                          |
|                  | **City**             | `VARCHAR(255)`      | Ciudad donde se celebraron los juegos olímpicos.                                |                          |
| **Deporte**      | **ID Deporte**       | `INT`               | Identificador único del deporte, clave primaria.                                | **PK**                   |
|                  | **Sport**            | `VARCHAR(255)`      | Nombre del deporte (por ejemplo, "Basketball", "Judo").                         |                          |
| **Evento**       | **ID Evento**        | `INT`               | Identificador único del evento, clave primaria.                                 | **PK**                   |
|                  | **Event**            | `VARCHAR(255)`      | Descripción del evento (por ejemplo, "Basketball Men's Basketball").             |                          |
| **Medalla**      | **ID Medalla**       | `INT`               | Identificador único de la medalla, clave primaria.                              | **PK**                   |
|                  | **Medal**            | `VARCHAR(20)`       | Tipo de medalla (por ejemplo, "Gold", "Silver", "Bronze", o "NA" si no se ganó).|                          |
| **Atleta_Juego** | **ID Atleta**        | `INT`               | Clave foránea que hace referencia a la tabla **Atleta** (ID Atleta).             | **FK**                   |
|                  | **ID Juego**         | `INT`               | Clave foránea que hace referencia a la tabla **Juego** (ID Juego).               | **FK**                   |
| **Atleta_Evento**| **ID Atleta**        | `INT`               | Clave foránea que hace referencia a la tabla **Atleta** (ID Atleta).             | **FK**                   |
|                  | **ID Evento**        | `INT`               | Clave foránea que hace referencia a la tabla **Evento** (ID Evento).             | **FK**                   |
| **Atleta_Medalla**| **ID Atleta**       | `INT`               | Clave foránea que hace referencia a la tabla **Atleta** (ID Atleta).             | **FK**                   |
|                  | **ID Medalla**       | `INT`               | Clave foránea que hace referencia a la tabla **Medalla** (ID Medalla).           | **FK**                   |

### Descripción de las **Claves**:
- **PK (Primary Key)**: Indica que el atributo es la **clave primaria** de la tabla, lo que significa que debe ser único y no nulo.
- **FK (Foreign Key)**: Indica que el atributo es una **clave foránea**, lo que significa que hace referencia a la clave primaria de otra tabla. Esto establece una relación entre las tablas.

---

### **Ejemplo de cómo se usa**:
- En la tabla **Atleta_Juego**, los campos **ID_Atleta** e **ID_Juego** son claves foráneas (**FK**) que hacen referencia respectivamente a las tablas **Atleta** y **Juego**. Esto permite asociar a un atleta con un juego específico en que participó.
  
- En la tabla **Atleta_Medalla**, **ID_Atleta** es una clave foránea que se refiere a **ID** en la tabla **Atleta**, y **ID_Medalla** se refiere a **ID_Medalla** en la tabla **Medalla** para vincular un atleta con una medalla ganada.

---

### Resumen de las claves por tabla:
- **Atleta**: La clave primaria es **ID**.
- **Juego**: La clave primaria es **ID_Juego**.
- **Deporte**: La clave primaria es **ID_Deporte**.
- **Evento**: La clave primaria es **ID_Evento**.
- **Medalla**: La clave primaria es **ID_Medalla**.
- **Atleta_Juego**, **Atleta_Evento**, **Atleta_Medalla**: Estas tablas intermedias contienen claves foráneas (**FK**) que vinculan las tablas principales entre sí.














