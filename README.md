# 🏬 Frontend App Tienda

Aplicación móvil de gestión para una tienda: catálogo de productos, carrito de compras, registro de clientes y generación de facturas en PDF. Construida con **Ionic + Angular**, standalone components.

Proyecto desarrollado como práctica para aplicar un flujo completo de e-commerce/gestión (catálogo → carrito → pedido → factura) consumiendo una API REST propia, reforzando el manejo de formularios reactivos, modales, guards de ruta y comunicación HTTP autenticada.

## 🎯 Propósito del proyecto

La idea fue construir el frontend de un sistema de punto de venta simplificado, cubriendo dos frentes:

- **Gestión administrativa:** CRUD de clientes y productos (incluyendo carga de imágenes).
- **Flujo de venta:** selección de productos desde un catálogo, armado de carrito, identificación del cliente por cédula/RUC (con autocompletado si ya existe) y cierre del pedido con factura descargable en PDF.

Todo el flujo está protegido con autenticación JWT, de forma que las rutas de gestión solo son accesibles con sesión iniciada.

## ✨ Funcionalidades

- **Autenticación:** login contra la API, con token JWT adjuntado automáticamente a cada petición mediante un interceptor HTTP.
- **CRUD de clientes:** listado, creación, edición y eliminación mediante modales.
- **CRUD de productos:** listado con miniaturas, creación y edición con subida de imagen (`FormData`).
- **Catálogo de compra:** vista de productos disponibles con control de stock, agregado al carrito y badge de cantidad.
- **Carrito y checkout:** resumen de pedido con cálculo de totales, pasarela de pago con búsqueda de cliente existente por identificación o registro de uno nuevo.
- **Facturación:** generación de factura en PDF en el propio cliente (con `jsPDF` + `jspdf-autotable`), incluyendo detalle de productos y totales.

## 🛠️ Stack tecnológico

- **Ionic + Angular** — standalone components, sin NgModules.
- **TypeScript**
- **RxJS** (Observables para las llamadas HTTP)
- **HTTP Interceptor** — inyección automática del token JWT en cada request.
- **jsPDF / jspdf-autotable** — generación de facturas en PDF del lado del cliente.

## 📁 Estructura relevante

```
src/app/
├── paginas/
│   ├── login/               # Autenticación
│   ├── listado-clientes/    # CRUD de clientes
│   ├── listado-productos/   # CRUD de productos
│   ├── detalle-cliente/     # Modal de alta/edición de cliente
│   ├── detalle-producto/    # Modal de alta/edición de producto (con imagen)
│   ├── catalogo/            # Vista de compra + carrito
│   ├── detalle-pedido/      # Resumen del pedido antes de pagar
│   └── pasarela-pago/       # Identificación de cliente + confirmación + factura
├── servicios/                # Servicios HTTP (auth, cliente, producto, pedidos)
├── interceptors/              # Interceptor que agrega el Bearer token
└── interfaces/                # Modelos TypeScript (Cliente, Producto, Pedido)
```

## 🚀 Cómo correrlo localmente

```bash
npm install
ionic serve
```

Por defecto apunta a `http://localhost:3000/api` (ver `environment.ts`), por lo que necesitas el [backend-api-tienda](https://github.com/santiago-orozcov/backend-api-tienda) corriendo en ese puerto para que la app funcione completa.

## ⚠️ Estado actual y alcance

- Proyecto de práctica enfocado en el flujo funcional, no en un despliegue de producción.
- El token JWT se maneja actualmente en el cliente sin lógica de expiración/renovación automática.
- No incluye tests automatizados de los flujos de compra ni cobertura de errores de red exhaustiva.

## 👤 Autor

Santiago Orozco — Estudiante de Ingeniería en Tecnologías de la Información (UPSE)
