# Comercio de filatelia online

Tienda online especializada en **filatelia clásica**: primeras emisiones de cada país, época victoriana (hasta 1901) y China imperial (hasta 1912). Sellos, piezas e historia postal. Venta B2C y B2B a España, UE y resto del mundo.
Este archivo es el contexto común de todos los agentes. Rellena lo que falta en **[CORCHETES]**.

## Datos del negocio
- Razón social / autónomo: [PENDIENTE]
- NIF: [PENDIENTE]
- Domicilio fiscal: [PENDIENTE]
- Forma jurídica: [autónomo / SL]
- Régimen de IVA principal: [general / REBU (bienes usados y objetos de colección)]
- ¿Inscrito en el ROI/VIES (operaciones intracomunitarias)?: [sí/no]
- ¿Alta en OSS (ventanilla única UE)?: [sí/no]
- Banco(s): [PENDIENTE]
- Asesor/gestor fiscal externo: [PENDIENTE]

## Stack (lo decide y lo documenta el agente `tecnologia-web`)
- Plataforma tienda: [PENDIENTE: Shopify / WooCommerce / PrestaShop]
- Pasarelas de pago: [PENDIENTE: Stripe / PayPal / Redsys / Bizum]
- Marketplaces: [PENDIENTE: Delcampe / eBay / todocoleccion / Catawiki]
- Paquetería: [PENDIENTE: Correos / Packlink / Sendcloud ...]
- Facturación: [PENDIENTE: software compatible con VeriFactu]

## Equipo de agentes (`.claude/agents/`)
| Agente | Se ocupa de |
|---|---|
| `tecnologia-web` | Tienda online, pasarelas de pago, integraciones, seguridad, rendimiento |
| `experto-filatelico` | Filatelia CLÁSICA (primeras emisiones, siglo XIX hasta 1901, China hasta 1912): identificación, valoración, autenticidad, fichas |
| `administracion-fiscal` | Facturas, IVA/REBU/OSS, contabilidad, bancos, modelos AEAT |
| `logistica-envios` | Transportistas, tarifas, embalaje, etiquetas, aduanas, incidencias |
| `atencion-cliente` | Consultas, pedidos, devoluciones, reclamaciones, fidelización |
| `marketing-marketplaces` | SEO, newsletter, redes, publicación en Delcampe/eBay/todocoleccion |
| `legal-cumplimiento` | RGPD, LSSI, condiciones de venta, consumidores, contratos |

La sesión principal hace de **coordinador**: reparte el trabajo y junta los resultados cuando una tarea toca a varias áreas (p. ej. "dar de alta un lote nuevo" pasa por experto → marketing → web).

## Carpetas
- `catalogos/`: catálogos de referencia (Edifil, Michel, Scott, Yvert, Stanley Gibbons…) en PDF/CSV. Solo los lee `experto-filatelico`.
- `inventario/inventario.csv`: inventario maestro. Es la única fuente de verdad del stock.
- `ventas/`: pedidos exportados de la tienda y de los marketplaces.
- `facturas/`, `contabilidad/`: documentación fiscal y contable.
- `envios/`: tarifas, plantillas de etiquetas y aduanas, seguimiento.
- `clientes/`: plantillas de respuesta y registro de incidencias (sin datos personales en claro fuera de lo necesario).
- `legal/`: textos legales y contratos.
- `marketing/`: calendario editorial, campañas, textos.
- `web/`: código, configuración y documentación técnica de la tienda.

## Reglas comunes
1. Nunca inventes un dato que no puedas verificar (precio de catálogo, tipo de IVA, tarifa de envío, plazo legal). Si no lo sabes, dilo y explica cómo comprobarlo.
2. La normativa fiscal y aduanera cambia. Indica la fecha y la fuente de cada dato normativo y márcalo como "a validar con el asesor" cuando tenga consecuencias económicas.
3. Ningún agente envía dinero, presenta impuestos, publica anuncios ni manda correos a clientes sin la confirmación explícita del titular.
4. Las claves de API y las contraseñas no se guardan nunca en este repositorio.
5. Trabaja en español. Para fichas y comunicaciones internacionales, añade también la versión en inglés.

## Ofertas de compra recibidas (NO es stock propio)
| Fecha | Proveedor | Material | Dónde | Estado |
|---|---|---|---|---|
| 25/09/2026 | Vendedor externo (cuenta "sfincsvof", carpeta compartida "Miguel Rodriguez" en Google Drive) | ~37 piezas de Bélgica clásica (OBP 1–37: Epaulettes, Medallones, planchas, bloques, márgenes de hoja, un ensayo), ~127 fotos | Google Drive, solo lectura, propiedad del vendedor | Examen previo de Epaulettes hecho (ver `ofertas/belgica-2026-09/`). Resto pendiente |

Las piezas de una oferta no entran en `inventario/inventario.csv` hasta que se compran. El experto hace primero el examen previo (piezas clave, riesgos, valor de reventa y precio máximo de compra).

## Google Drive (documentos, fotos y catálogos)
Carpeta raíz **Filatelia** en el Drive del titular:
- `01 Agentes (copia de seguridad)`: copia de este repositorio. La versión buena es la de GitHub.
- `02 Inventario`: hoja de cálculo "Inventario filatelia clásica" (misma estructura que `inventario/inventario.csv`).
- `03 Catálogos`: catálogos en PDF o escaneados (COB/OBP, Sassone, Ferchenbauer, Edifil, Michel, SG…).
- `04 Ofertas de compra`: lotes que ofrecen vendedores (fotos y listas). No es stock.
- `05 Valoraciones y certificados`: valoraciones, certificados de expertos (p. ej. "Valutazione francobollo Sicilia.xlsx").
- `06 Fotos de stock`: fotos de las piezas propias, nombradas por SKU.
- `07 Administración (facturas, impuestos)`.
Los documentos personales del titular están aparte en "Personal - Privado": ningún agente debe usarlos.
