# Cotizador y analizador

Herramienta personal para cotizar apps y sitios web.

- **Cotizar paso a paso:** armás el presupuesto con lo que te pidió el cliente.
- **Analizar trabajo hecho:** cargás un enlace, un .zip o una carpeta. Detecta qué tiene la app, lista cada función con su precio, la compara con el mercado y te deja aplicar descuentos.

## Archivos

- `index.html`: la herramienta completa. Los precios están al principio de cada `<script>` (`PLANES`, `ADICIONALES`, `MERCADO`, `GENERICOS`).
- `api/analizar.js`: función de Vercel que descarga la página de un enlace para poder analizarla. Solo acepta sitios públicos.
- `vercel.json`: le da a esa función hasta 30 segundos.

## Publicarlo en Vercel

1. Creá un repositorio nuevo en GitHub, por ejemplo `cotizador`, y subí estos archivos respetando la carpeta `api`.
2. En vercel.com: **Add New → Project**, elegí el repositorio y tocá **Deploy**. No hace falta configurar nada.
3. Abrí la dirección que te da Vercel (`cotizador-xxx.vercel.app`).

Si abrís `index.html` directo desde la computadora, el cotizador y el análisis por .zip o carpeta funcionan igual. El análisis por enlace necesita estar publicado en Vercel.

## Actualizar precios

- Lista propia: `PLANES` y `ADICIONALES` (cotizador) y `GENERICOS` (analizador).
- Mercado: `MERCADO` (dólares, por nivel) y `DOLAR_DEF` (dólar BNA). El dólar también se puede cambiar desde la pantalla.

Fuentes de mercado: Develop Argentina (julio 2026), Develop Argentina tiendas online (junio 2026) y Neolo (diciembre 2025). Dólar oficial BNA venta $1.560 al 30/10/2026.

## Límites del análisis

- Detecta funciones buscando señales en el código: librerías, conexiones y nombres de funciones. Siempre revisá la lista y desmarcá lo que no corresponda.
- En sitios grandes analiza hasta 12 páginas y 35 archivos.
- Los archivos `.env` y la carpeta `node_modules` se ignoran.
