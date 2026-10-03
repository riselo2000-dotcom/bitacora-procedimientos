# Bitácora de Procedimientos

PWA gratuita para que profesionales sanitarios registren su propia actividad de procedimientos (fecha, hora, tipo, complicaciones) con fines de autoevaluación y recertificación.

**App en producción:** https://bitacora-procedimientos.vercel.app

## Características

- Registro de procedimientos con fecha, hora, tipo (lista predefinida de 16 procedimientos médico-quirúrgicos) e identificador interno opcional.
- Marcado de complicaciones con detalle opcional.
- Estadísticas rápidas (total, del mes, complicaciones).
- Resumen anual (por tipo de procedimiento y por mes) para recertificación.
- Exportación a CSV (registro completo y resumen anual).
- Instalable como PWA (Android/desktop vía `beforeinstallprompt`, iOS vía "Añadir a pantalla de inicio").
- Funciona offline (service worker con cache del shell de la app).
- **Privacidad por diseño**: todos los datos se guardan únicamente en `localStorage`, en el dispositivo del usuario. No hay backend, no hay servidor, no se recogen datos de pacientes.

## Stack

HTML + CSS + JavaScript vainilla, sin dependencias de build. Un único archivo `index.html` con todo el markup, estilos y lógica inline, más `manifest.json` y `sw.js` para la capa PWA.

## Estructura

```
index.html        — aplicación completa
manifest.json     — Web App Manifest
sw.js             — service worker (cache offline)
privacidad.html   — política de privacidad
terminos.html     — términos de uso
icons/            — iconos PWA (192, 512, apple-touch-icon)
```

## Desarrollo local

No requiere build. Basta con servir el directorio con cualquier servidor estático, por ejemplo:

```bash
npx serve .
```

## Despliegue

Desplegado en Vercel como sitio estático (sin framework). Cualquier push a `main` puede conectarse a un despliegue automático configurando el proyecto en Vercel con este repositorio.

## Aviso legal

Esta herramienta no es un dispositivo médico, no sustituye la historia clínica oficial del paciente y no debe usarse para introducir datos que identifiquen a un paciente. Ver `terminos.html` y `privacidad.html` para más detalle.

## Roadmap

- [ ] Capa de cuentas y suscripción freemium (sincronización en la nube, backup, informes PDF).
- [ ] Integración de pago (Stripe).

---

_Despliegue automático verificado: 2026-10-03 22:32 UTC_
