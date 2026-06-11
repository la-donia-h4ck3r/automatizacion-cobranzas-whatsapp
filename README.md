# Sistema de Recordatorios de Cobro por WhatsApp

Automatización en producción para Berta, agencia de marketing de Leones, Córdoba.
Reemplaza el seguimiento manual de cobranzas con una secuencia escalonada de mensajes
WhatsApp automáticos, adjunto de PDF y alertas al administrador.

## Problema

Berta gestiona +25 clientes con contratos de monto y fecha de vencimiento fijos.
El seguimiento de cobros era 100% manual: la administrativa identificaba facturas
vencidas, enviaba WhatsApp uno por uno, reenviaba remitos a pedido y hacía
seguimiento de morosos — todo de memoria, sin trazabilidad y dependiente de que
la persona se acordara en el momento correcto.

## Solución

Workflow en n8n que corre de **lunes a sábado a las 09:00 hs**. Consulta Zoho Books,
clasifica cada remito según su proximidad al vencimiento y envía el mensaje
correspondiente con o sin PDF adjunto según el tipo de recordatorio.

## Secuencia de recordatorios

| Tipo | Cuándo | Contenido |
|------|--------|-----------|
| `aviso_7_dias` | 7 días antes del vencimiento | Texto + PDF del remito adjunto |
| `vencimiento` | Día del vencimiento | Texto de aviso |
| `recordatorio_3` | 3 días después del vencimiento | Texto de seguimiento |
| `recordatorio_7` | 7 días después del vencimiento | Texto al cliente + alerta al admin |

## Arquitectura

