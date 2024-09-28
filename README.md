# Consumidor de Eventos para Procesamiento de Pagos

Este proyecto forma parte de una práctica universitaria para la asignatura de Arquitectura de Software, que implementa un consumidor en una arquitectura orientada a eventos utilizando Node.js, Express, y RabbitMQ.

## Descripción

El sistema actúa como un consumidor de eventos que:

1. Se conecta a una cola RabbitMQ
2. Consume mensajes de pago de la cola
3. Procesa los pagos enviándolos a un servicio externo

Este consumidor forma parte de una arquitectura más amplia orientada a eventos, donde diferentes componentes se comunican de manera asíncrona a través de mensajes.

## Requisitos

- Node.js
- npm (Node Package Manager)
- Acceso a un servidor RabbitMQ (se usa CloudAMQP en este ejemplo)
- Acceso a un servicio de procesamiento de pagos

## Instalación

1. Clona este repositorio:
   ```
   git clone https://github.com/betooxx-dev/arq-ed-consumer
   ```
2. Navega al directorio del proyecto:
   ```
   cd arq-ed-consumer
   ```
3. Instala las dependencias:
   ```
   npm install
   ```
4. Crea un archivo `.env` en la raíz del proyecto y añade las siguientes variables:
   ```
   CLOUDAMQP_URL=tu_url_de_cloudamqp
   PAYMENT_URL=url_del_servicio_de_pagos
   ```

## Uso

1. Inicia el servidor:
   ```
   npm run dev
   ```
2. El servidor se iniciará en el puerto 4000 y comenzará a consumir mensajes de la cola RabbitMQ.

3. Los mensajes consumidos deben tener el siguiente formato:
   ```json
   {
     "amount": 1000
   }
   ```
   Donde `amount` es el monto del pago a procesar.

4. El consumidor procesará cada mensaje, enviará el pago al servicio externo y registrará la actividad en la consola.

## Estructura del proyecto

```
├── src/
│   ├── index.js
├── package.json
├── .env
└── README.md
```

## Características

- Uso de RabbitMQ para implementar un consumidor de eventos
- Procesamiento asíncrono de pagos
- Integración con un servicio externo de pagos
- Manejo de errores básico
- Uso de variables de entorno para configuración

## Consideraciones

- Este es un ejemplo simplificado y no debe usarse en producción sin las medidas de seguridad adecuadas.
- En un entorno de producción, se debería implementar un manejo más robusto de errores y reintentos.
- La seguridad de las comunicaciones y la autenticación no están implementadas en este ejemplo.

## Contribuciones

Este es un proyecto educativo, pero las sugerencias y mejoras son bienvenidas. Si deseas contribuir, por favor abre un "issue" o envía un "pull request".

## Licencia

Este proyecto es de código abierto y está disponible bajo la Licencia MIT.
