## creacion de tablas de vuelos 
```sql
CREATE TABLE paises (
    pais_id INT PRIMARY KEY,
    nombre_pais VARCHAR(100)
);

CREATE TABLE ciudades (
    ciudad_id INT PRIMARY KEY,
    nombre_ciudad VARCHAR(100),
    pais_id INT,
    FOREIGN KEY (pais_id) REFERENCES paises(pais_id)
);

CREATE TABLE sucursales (
    sucursal_id INT PRIMARY KEY,
    nombre_sucursal VARCHAR(100),
    direccion VARCHAR(255),
    ciudad_id INT,
    FOREIGN KEY (ciudad_id) REFERENCES ciudades(ciudad_id)
);

CREATE TABLE clientes (
    cliente_id INT PRIMARY KEY,
    nombre_cliente VARCHAR(100),
    correo VARCHAR(100),
    direccion VARCHAR(255),
    telefono VARCHAR(15)
);

CREATE TABLE paquetes (
    paquete_id INT PRIMARY KEY,
    numero_seguimiento VARCHAR(50),
    peso DECIMAL(10, 2),
    dimensiones VARCHAR(50),
    contenido VARCHAR(255),
    valor_declarado DECIMAL(10, 2),
    tipo_servicio ENUM('Nacional', 'Internacional', 'Exprés', 'Estándar'),
    sucursal_id INT,
    FOREIGN KEY (sucursal_id) REFERENCES sucursales(sucursal_id)
);

CREATE TABLE envios (
    envio_id INT PRIMARY KEY,
    cliente_id INT,
    paquete_id INT,
    sucursal_id INT,
    fecha_envio DATETIME,
    estado ENUM('Recibido', 'En tránsito', 'Entregado', 'Retenido en aduana'),
    ruta_id INT,
    numero_seguimiento VARCHAR(50),
    FOREIGN KEY (cliente_id) REFERENCES clientes(cliente_id),
    FOREIGN KEY (paquete_id) REFERENCES paquetes(paquete_id),
    FOREIGN KEY (sucursal_id) REFERENCES sucursales(sucursal_id),
    FOREIGN KEY (ruta_id) REFERENCES rutas(ruta_id)
);

CREATE TABLE seguimiento (
    seguimiento_id INT PRIMARY KEY,
    paquete_id INT,
    ubicacion VARCHAR(255),
    fecha_evento DATETIME,
    estado ENUM('Recibido', 'En tránsito', 'Entregado', 'Retenido en aduana'),
    FOREIGN KEY (paquete_id) REFERENCES paquetes(paquete_id)
);

CREATE TABLE rutas (
    ruta_id INT PRIMARY KEY,
    nombre_ruta VARCHAR(100),
    conductor_id INT,
    vehiculo_id INT,
    FOREIGN KEY (conductor_id) REFERENCES conductores(conductor_id),
    FOREIGN KEY (vehiculo_id) REFERENCES vehiculos(vehiculo_id)
);

CREATE TABLE conductores (
    conductor_id INT PRIMARY KEY,
    nombre_conductor VARCHAR(100),
    telefono VARCHAR(15),
    sucursal_id INT,
    FOREIGN KEY (sucursal_id) REFERENCES sucursales(sucursal_id)
);

CREATE TABLE vehiculos (
    vehiculo_id INT PRIMARY KEY,
    placa VARCHAR(20),
    modelo VARCHAR(100),
    sucursal_id INT,
    FOREIGN KEY (sucursal_id) REFERENCES sucursales(sucursal_id)
);

CREATE TABLE auxiliares (
    auxiliar_id INT PRIMARY KEY,
    nombre_auxiliar VARCHAR(100),
    telefono VARCHAR(15),
    sucursal_id INT,
    FOREIGN KEY (sucursal_id) REFERENCES sucursales(sucursal_id)
);

CREATE TABLE asignaciones_rutas (
    asignacion_id INT PRIMARY KEY,
    ruta_id INT,
    auxiliar_id INT,
    FOREIGN KEY (ruta_id) REFERENCES rutas(ruta_id),
    FOREIGN KEY (auxiliar_id) REFERENCES auxiliares(auxiliar_id)
);

CREATE TABLE empleados (
    empleado_id INT PRIMARY KEY,
    nombre VARCHAR(100),
    salario DECIMAL(10, 2),
    departamento_id INT,
    jobtitle VARCHAR(50),
    sucursal_id INT,
    FOREIGN KEY (sucursal_id) REFERENCES sucursales(sucursal_id)
);

CREATE TABLE ventas (
    venta_id INT PRIMARY KEY,
    vendedor_id INT,
    producto VARCHAR(100),
    total_venta DECIMAL(10, 2),
    fecha DATETIME,
    FOREIGN KEY (vendedor_id) REFERENCES empleados(empleado_id)
);

```
Hecho por (jhorman jesus castellanos morales )

> [!NOTE]
> complicaciones 

> [!TIP]
> 

> [!IMPORTANT]  
> se encuntra culminado 

> [!WARNING]  
> 

> [!CAUTION]
>
