# MoneyTrack — Integraciones y captura de datos (v0.2)

> Costa Rica no tiene open banking. MoneyTrack captura los movimientos por los canales donde ya existen
> (notificaciones, SMS, correo, pagos con billetera, estados de cuenta, blockchains y brokers)
> y usa IA para convertirlos en un solo registro financiero.
>
> Lo técnico de este documento está verificado a nivel general, pero **cada integración se debe probar
> con un prototipo** antes de prometerla a los usuarios.

---

## 1. Resumen de viabilidad

| Canal | Android | iOS | Cómo | Viabilidad |
|---|---|---|---|---|
| SMS del banco | ✅ | ⚠️ | Android: lector de notificaciones. iOS: automatización de Atajos (Shortcuts) | Alta en Android; media en iOS (el usuario la configura una vez) |
| Notificaciones de apps bancarias | ✅ | ❌ | Android: lector de notificaciones | Alta en Android; iOS no lo permite |
| Correo | ✅ | ✅ | Dirección de reenvío personal (`usuario@in.moneytrack.cr`) | Alta |
| Google Wallet | ✅ | — | Notificación que Google Wallet muestra tras cada pago | Alta |
| Apple Wallet / Apple Pay | — | ⚠️ | Automatización "Transacción" de Atajos al pagar con Apple Pay | Media (FinanceKit no está disponible para Costa Rica) |
| Estados de cuenta | ✅ | ✅ | Subir PDF / Excel / CSV; la IA extrae los movimientos | Alta |
| Criptomonedas | ✅ | ✅ | Direcciones públicas (solo lectura) + API de solo lectura de exchanges | Alta |
| Bolsa / brokers | ✅ | ✅ | API de solo lectura, agregador o importación de reportes | Media; depende de cada broker |
| Efectivo | ✅ | ✅ | Voz, foto del tiquete, WhatsApp, registro rápido | Alta |

**Regla de oro:** MoneyTrack **nunca** pide usuario y contraseña del banco (*screen scraping*).
Toda conexión es de **solo lectura**; nunca puede mover dinero.

---

## 2. Detalle por canal

### 2.1 SMS y notificaciones — Android
- Se usa `NotificationListenerService`: el usuario da permiso de "acceso a notificaciones" y la app lee
  las notificaciones de su app de SMS, de las apps bancarias y de Google Wallet.
- **No usar el permiso `READ_SMS`:** Google Play solo lo permite a apps de SMS predeterminadas y a unas
  pocas excepciones. El lector de notificaciones está permitido, pero Play pide justificarlo en su formulario.
- Se filtra por remitente o app (BAC, BCR, BN, Popular, Davivienda, Promerica, cooperativas, SINPE Móvil)
  y **solo se envían al servidor los mensajes financieros**. Los demás no salen del teléfono.

### 2.2 SMS — iOS
- iOS no permite que ninguna app lea SMS ni notificaciones de otras apps.
- **Alternativa:** una automatización personal de Atajos (Shortcuts) con el disparador "Mensaje"
  (remitente = banco, o mensaje contiene "SINPE" / "compra"). La automatización envía el texto a la API
  de MoneyTrack.
- MoneyTrack entrega un atajo listo para instalar, con una guía en video de 1 minuto.
- Riesgos: el usuario tiene que configurarlo y el comportamiento puede cambiar entre versiones de iOS.
  Se debe probar en cada versión nueva.

### 2.3 Correo — Android e iOS
- **Opción principal:** cada usuario recibe una dirección única (`andrey.x7k2@in.moneytrack.cr`) y configura
  en Gmail u Outlook una regla que reenvía las alertas del banco y las facturas electrónicas.
- Un servicio de correo entrante (Amazon SES, Postmark o SendGrid Inbound Parse) recibe el correo y
  lo pasa a la API.
- **Factura electrónica de Hacienda:** los XML que llegan por correo traen el detalle de la compra
  artículo por artículo. Esto es un **diferencial único en Costa Rica**.
- **Opción futura:** conectar Gmail u Outlook con OAuth de solo lectura. Gmail exige una auditoría de
  seguridad anual (CASA) por usar permisos restringidos, así que conviene hacerlo cuando ya haya tracción.

### 2.4 Google Wallet
- No existe una API pública para leer el historial de Google Wallet.
- Al pagar con el teléfono, Google Wallet muestra una notificación con el comercio y el monto.
  Se captura con el mismo lector de notificaciones de Android (2.1).

### 2.5 Apple Wallet / Apple Pay
- **FinanceKit** (la API de Apple para leer transacciones de Wallet) solo cubre Apple Card, Apple Cash
  y Apple Savings, además de mercados específicos, y requiere permiso especial de Apple.
  **No aplica a tarjetas de bancos de Costa Rica.**
- **Alternativa:** la automatización "Transacción" de Atajos, que se dispara al pagar con Apple Pay y
  entrega el comercio, el monto y la tarjeta. El atajo la envía a MoneyTrack.
- Solo capta pagos hechos con Apple Pay; las compras con tarjeta física llegan por SMS o correo.

### 2.6 Estados de cuenta (manual)
- El usuario sube un PDF, Excel o CSV desde la app o lo reenvía al correo de MoneyTrack.
- **La IA extrae los movimientos**, así que no hace falta programar un lector a mano para cada banco.
  Para los bancos más usados se hacen plantillas específicas, más baratas y precisas.
- Sirve para cuadrar: detecta lo que no llegó por los otros canales y marca las diferencias.

### 2.7 Criptomonedas
- **Billeteras propias (solo lectura):** el usuario pega su dirección pública (BTC, ETH, Solana, etc.)
  y se consulta el saldo y el historial en exploradores o proveedores de datos de blockchain.
  Nunca se piden llaves privadas ni frases semilla.
- **Exchanges:** claves de API **de solo lectura** (Binance, Coinbase, Kraken, Bitget, etc.).
- **Precios:** una API de precios (por ejemplo CoinGecko) convertida a USD y CRC.

### 2.8 Inversiones y brokers
Los ticos invierten sobre todo por dos vías:

| Tipo | Ejemplos | Cómo conectar |
|---|---|---|
| Brokers internacionales | Interactive Brokers, Charles Schwab, otros de EE. UU. | API de solo lectura del broker, o un agregador de brokers (p. ej. SnapTrade) |
| Apps de inversión para LatAm | Hapi, eToro, otras | Si no tienen API: importar el reporte o estado de cuenta |
| Puestos de bolsa locales (BNV) | BN Valores, BCR Valores, Popular Valores, INS Inversiones… | Importar estados de cuenta en PDF con IA |
| Fondos de pensión | ROP / FCL (operadoras de pensiones) | Importar estado de cuenta; más adelante, alianzas |

- Se muestran las posiciones, el valor actual, las ganancias y la composición del portafolio (acciones,
  bonos, fondos, cripto).
- Se debe confirmar la disponibilidad real de cada broker y agregador para usuarios de Costa Rica.

### 2.9 Efectivo e informal
- Registro por voz ("gasté 3 500 en la feria"), foto del tiquete, WhatsApp o registro rápido de 5 segundos.

---

## 3. La IA como eje central

La IA está en todo el flujo, no solo en un chat:

1. **Lectura:** convierte textos sueltos (SMS, correos, PDFs, tiquetes) en transacciones estructuradas
   (monto, moneda, comercio, fecha, tarjeta y tipo).
2. **Limpieza:** normaliza el nombre del comercio ("AUTO MERC ESCAZU 04" → Auto Mercado).
3. **Categorización:** asigna la categoría y aprende de las correcciones de cada usuario.
4. **Eliminación de duplicados:** une la misma compra aunque llegue por SMS, correo y estado de cuenta.
5. **Detección:** encuentra suscripciones y pagos recurrentes, cobros raros o duplicados y comisiones.
6. **Asistente:** responde preguntas en lenguaje natural ("¿cuánto gasté en Uber este mes?",
   "¿me alcanza para el marchamo?") por la app y por WhatsApp.
7. **Proyecciones:** flujo de caja, aguinaldo, marchamo, metas y patrimonio a futuro.

**Costo y privacidad:**
- Primero se aplican reglas y plantillas, que son baratas. La IA se usa solo cuando las reglas no alcanzan.
- Se eliminan los datos personales innecesarios (números de tarjeta completos, cédulas) antes de enviar
  información al modelo.
- Se usa un proveedor de IA que no entrene con los datos de los clientes.

---

## 4. Arquitectura (alto nivel)

```
 Captura                          Procesamiento                     Producto
 ─────────                        ─────────────                     ────────
 App Android (notificaciones) ─┐
 Atajos iOS (SMS, Apple Pay)  ─┤
 Correo de reenvío            ─┼─► API de ingesta ─► Cola ─► Motor IA ─► Libro de      ─► App móvil / web
 Estados de cuenta (subida)   ─┤                            (leer,       transacciones    Asistente IA
 Cripto (direcciones / APIs)  ─┤                             limpiar,    (PostgreSQL,     WhatsApp
 Brokers (APIs / reportes)    ─┤                             categorizar, cifrado)        Alertas
 Efectivo (voz / foto / chat) ─┘                             deduplicar)
                                                  Tipo de cambio BCCR y precios cripto/acciones
```

**Tecnología sugerida (se puede ajustar):**
- **Móvil:** React Native (Expo) para iOS y Android con un módulo nativo para el lector de
  notificaciones de Android.
- **Web:** React / Next.js, para usar MoneyTrack también en la computadora.
- **Backend:** TypeScript (Node) o Python, con PostgreSQL y colas para procesar en segundo plano.
- **Correo entrante:** Amazon SES, Postmark o SendGrid.
- **IA:** un modelo de lenguaje por API (por ejemplo Claude de Anthropic).
- **Tipo de cambio:** servicio web de indicadores económicos del BCCR.

---

## 5. Seguridad y legal (Costa Rica)

- **Ley 8968** (protección de datos personales): consentimiento informado, derecho a borrar los datos
  e inscripción de la base de datos ante la **PRODHAB**.
- Datos cifrados en tránsito y en reposo, doble factor de autenticación y registro de accesos.
- Solo lectura: MoneyTrack no mueve dinero, así que en la etapa inicial no se considera una entidad
  financiera regulada por SUGEF. **Validar con un abogado** antes del lanzamiento, sobre todo si más
  adelante se ofrecen inversiones, pagos o recomendaciones personalizadas de inversión.
- Plan de respuesta a incidentes y auditorías de seguridad antes de manejar datos de empresas (Enterprise).
