# 🚛 LogiTrans - Plataforma de Gestión de Envíos y Logística

## 📌 Descripción
LogiTrans es un ejercicio para construir una plataforma basada en microservicios para la gestión de envíos y logística. Permite a clientes registrar envíos, a transportistas aceptar pedidos y actualizar su estado, y a administradores gestionar métricas y usuarios.

El sistema se construye en **.NET 9** y usa **RabbitMQ** para mensajería basada en eventos, con **bases de datos distribuidas** para un rendimiento óptimo.

---

## 🏛 Arquitectura del Proyecto
El sistema sigue **DDD (Domain-Driven Design)** y se divide en los siguientes microservicios:

1. **Customer Service**: Gestión de clientes y autenticación.
2. **Shipping Order Service**: Creación y seguimiento de envíos.
3. **Carrier Service**: Registro y gestión de transportistas.
4. **Tracking Service**: Actualización y monitoreo de estados de los envíos.
5. **Payment Service**: Procesamiento de pagos y tarifas.

### 📡 Comunicación entre Microservicios
Los microservicios se comunican mediante **eventos en RabbitMQ**:

- `EnvioCreado`
- `TransportistaAsignado`
- `EstadoEnvioActualizado`
- `PagoRealizado`

---

## 🚀 Tecnologías Utilizadas
- **.NET 9** - Backend con ASP.NET Core
- **Entity Framework Core** - ORM para bases de datos
- **RabbitMQ + MassTransit** - Mensajería basada en eventos
- **MongoDB / PostgreSQL** - Persistencia de datos
- **Docker + Kubernetes** - Orquestación y despliegue
- **IdentityServer4** - Autenticación y autorización

---

## 🔹 Instalación y Configuración
### 📥 Prerrequisitos
Asegúrate de tener instalado:
- [.NET 9 SDK](https://dotnet.microsoft.com/download)
- [Docker](https://www.docker.com/)
- [RabbitMQ](https://www.rabbitmq.com/download.html)
- [MongoDB / PostgreSQL](https://www.mongodb.com/ o https://www.postgresql.org/)

### 🚀 Instrucciones de Ejecución
1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/tu_usuario/logitrans.git
   cd logitrans
   ```
2. **Levantar infraestructura con Docker Compose:**
   ```bash
   docker-compose up -d
   ```
3. **Ejecutar los microservicios:**
   ```bash
   dotnet run --project src/ShippingOrderService/ShippingOrderService.csproj
   ```

---

## 📜 Casos de Uso
### **1️⃣ Crear un Envío**
📌 **Actor**: Cliente  
📌 **Flujo**:
1. Cliente ingresa dirección y detalles del paquete.
2. Se calcula la tarifa y se crea el envío.
3. Se genera un evento `EnvioCreado`.

📌 **Criterios de Aceptación**:
✅ Si la dirección es válida, se confirma el envío.
✅ Si hay errores, se muestra un mensaje al usuario.

### **2️⃣ Asignar un Transportista**
📌 **Actor**: Transportista  
📌 **Flujo**:
1. Transportista recibe notificación de nuevo envío.
2. Puede aceptar o rechazar el pedido.
3. Se genera un evento `TransportistaAsignado`.

📌 **Criterios de Aceptación**:
✅ Si acepta, el pedido se le asigna.
✅ Si rechaza, otro transportista será notificado.

---

## 📧 Contacto
Si tienes preguntas o sugerencias, contáctanos en **soporte@logitrans.com** o crea un issue en el repositorio.

---

¡Gracias por contribuir a LogiTrans! 🚀
