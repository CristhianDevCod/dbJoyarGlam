# Base de datos de la Joyeria
Este diseño permite una gestión integral de una joyería al almacenar los datos de cada entidad (clientes, proveedores, joyeros, piezas, y ventas) en 
colecciones independientes y bien estructuradas. La separación en colecciones facilita el acceso a información detallada y permite generar informes 
personalizados, esenciales para la administración de la joyería.

## 1. Crear (Create)
Para insertar un nuevo cliente en la colección:

```mongodb
db.clientes.insertOne({
  _id: "cliente006",
  nombre: "Andrea Gómez",
  contacto: "+57 311 8765432",
  email: "andrea.gomez@example.com",
  historialDeCompras: [
    { ventaId: "venta011", fecha: "2024-11-12", total: 300 },
    { ventaId: "venta012", fecha: "2024-11-13", total: 150 }
  ]
});
```

## 2. Leer (Read)
a. Leer todos los clientes:
```mongodb
db.clientes.find();
```
b. Leer un cliente específico por su ID:
```mongodb
db.clientes.findOne({ _id: "cliente002" });
```
c. Leer clientes que hayan realizado compras superiores a un monto específico:
```
db.clientes.find({ "historialDeCompras.total": { $gt: 200 } });
```

## 3. Actualizar (Update)
a. Actualizar el contacto de un cliente específico:
```mongodb
db.clientes.updateOne(
  { _id: "cliente003" },
  { $set: { contacto: "+57 300 1234567" } }
);
```

b. Agregar una nueva compra al historial de un cliente:
```mongodb
db.clientes.updateOne(
  { _id: "cliente001" },
  { $push: { historialDeCompras: { ventaId: "venta013", fecha: "2024-11-14", total: 250 } } }
);
```















