# 💬 Automatización de Recordatorios de Cobranza por WhatsApp

Sistema de cobranza automatizado que reemplaza el seguimiento manual de pagos con mensajes automáticos por WhatsApp, registros de auditoría y métricas de gestión.

---

## 🧩 Problema

La empresa realizaba el seguimiento de pagos de forma completamente manual. Cada mes, una persona debía revisar qué clientes tenían facturas pendientes, controlar fechas de vencimiento, enviar mensajes uno por uno por WhatsApp y hacer seguimiento de los morosos.

Esto generaba:

- Alto consumo de tiempo operativo
- Olvidos en el envío de recordatorios
- Cobros tardíos por falta de seguimiento
- Nula trazabilidad del proceso

---

## ✅ Solución

Sistema de automatización completo que detecta facturas pendientes, calcula qué recordatorio corresponde según la fecha de vencimiento y envía mensajes automáticos por WhatsApp con plantillas adaptadas al contexto de la deuda.

---

## 🔁 Flujo del sistema

```
Zoho Invoice (facturas pendientes)
        ↓
    n8n (motor de automatización)
        ↓
Lógica de fechas → ¿qué recordatorio corresponde?
        ↓
Evolution API → WhatsApp Business
        ↓
Google Sheets + PostgreSQL (logs y métricas)
```

---

## 📅 Recordatorios automáticos

| Momento | Tipo de mensaje |
|---|---|
| 5 días antes del vencimiento | Recordatorio preventivo |
| Día de vencimiento | Aviso de vencimiento |
| 3 días después | Primera gestión de mora |
| 7 días después | Segunda gestión de mora |

Cada mensaje utiliza plantillas adaptadas al contexto y estado de la deuda.

---

## ⚙️ Stack tecnológico

| Herramienta | Rol |
|---|---|
| **n8n** | Motor de automatización (self-hosted) |
| **Zoho Invoice** | Fuente de datos de facturas |
| **Evolution API** | Envío de mensajes por WhatsApp Business |
| **Google Sheets** | Logs de envíos y métricas |
| **PostgreSQL** | Base de datos para deduplicación y auditoría |
| **Docker / EasyPanel** | Infraestructura self-hosted en VPS |

---

## 🏗️ Infraestructura

El sistema corre completamente self-hosted sobre un VPS con Docker gestionado mediante EasyPanel. No depende de servicios externos de pago para la automatización.

---

## 📋 Funcionalidades principales

- Consulta automática de facturas/remitos pendientes en Zoho Invoice
- Identificación de fecha de vencimiento y cálculo del tipo de recordatorio
- Envío de mensajes por WhatsApp con plantillas contextuales
- Registro de cada envío en logs para auditoría
- Deduplicación: evita enviar el mismo recordatorio dos veces
- Generación de métricas para análisis de gestión de cobranzas

---

## 📈 Resultados

- ✅ Eliminación del trabajo manual de seguimiento mensual
- ✅ Mayor consistencia y puntualidad en las cobranzas
- ✅ Trazabilidad completa de cada comunicación enviada
- ✅ Proceso escalable a cientos o miles de clientes sin aumentar carga operativa

---

## 📁 Estructura del repositorio

```
├── workflows/          # Exportaciones JSON del workflow de n8n
├── docs/               # Diagramas y documentación técnica
└── README.md
```

---

## ⚠️ Nota sobre credenciales

Este repositorio no contiene credenciales, tokens ni datos de clientes reales. Las variables de entorno sensibles se gestionan mediante `.env` y no se suben al repositorio.

---

*Desarrollado como solución productiva en entorno real — Berta Multimedios, Leones, Córdoba, Argentina.*
