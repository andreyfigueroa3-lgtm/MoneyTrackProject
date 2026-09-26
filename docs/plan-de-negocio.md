# MoneyTrack — Plan de negocio (v0.2, borrador)

> Documento de trabajo. Las cifras son **supuestos para validar**, no datos de mercado confirmados.
> Detalle técnico de cada conexión: [integraciones.md](integraciones.md).

---

## 1. Resumen

**MoneyTrack** es la plataforma de finanzas personales con IA que le permite a un tico ver y controlar
**todo** su dinero en un solo lugar: bancos, tarjetas, SINPE Móvil, efectivo, criptomonedas e inversiones,
en colones y dólares.

- **Referencia:** Monarch Money (EE. UU.), adaptado a la realidad de Costa Rica y América Latina.
- **Problema:** en Costa Rica no hay open banking. El dinero de una persona está repartido entre
  varios bancos, SINPE, efectivo, dos monedas, cripto y brokers, y ninguna herramienta lo junta.
- **Solución:** captura automática por varios canales (notificaciones, SMS, correo, Google Wallet,
  Apple Pay, estados de cuenta, blockchains y brokers), con **IA como eje central** que lee, ordena,
  categoriza y aconseja.
- **Visión:** empezar en Costa Rica, expandirse a Latinoamérica y, más adelante, ofrecer versiones Enterprise.

---

## 2. El problema en Costa Rica

1. **Sin open banking:** las apps no pueden conectarse a los bancos como en EE. UU. o Europa.
2. **Dinero fragmentado:** la mayoría usa varios bancos, SINPE Móvil, efectivo y a veces cooperativas.
3. **Dos monedas:** salarios, alquileres, ahorros y deudas se mezclan entre colones y dólares.
4. **Nueva generación inversora:** cada vez más ticos tienen cripto o invierten en brokers
   internacionales, sin una vista consolidada de su patrimonio.
5. **Herramientas actuales:** Excel, las apps de cada banco (que solo ven su propio banco) o apps
   extranjeras que no funcionan con bancos locales.

---

## 3. Cliente ideal

| | Perfil principal | Perfil secundario |
|---|---|---|
| **Quién** | Profesionales de 25 a 45 años, ingresos medios y altos, urbanos | Parejas y familias que manejan las finanzas del hogar |
| **Situación** | 2 o más bancos, tarjetas de crédito, SINPE; algunos con cripto o broker | Gastos compartidos, metas en conjunto |
| **Dolor** | "No tengo idea de cuánto tengo ni en qué se me va" | "No sabemos cuánto gastamos como hogar" |
| **Disposición a pagar** | Alta si les ahorra tiempo y dinero | Media o alta |

> Monarch demostró que existe un público dispuesto a **pagar** por una vista completa y sin anuncios de
> sus finanzas. Nuestro primer cliente es ese perfil, en versión tica.

---

## 4. Producto: qué hace MoneyTrack (estilo Monarch)

| Módulo | Qué hace |
|---|---|
| **Panel principal** | Saldo total, gastos del mes, próximos pagos y alertas |
| **Cuentas** | Todos los bancos, tarjetas, efectivo, cripto e inversiones en un solo lugar |
| **Transacciones** | Captura automática, categorías y búsqueda por IA |
| **Flujo de caja** | Ingresos contra gastos por mes, en CRC y USD |
| **Presupuestos** | Por categoría o flexibles, con alertas |
| **Recurrentes** | Detecta suscripciones y pagos fijos (Netflix, luz, agua, préstamos, marchamo) |
| **Metas** | Ahorro para viaje, fondo de emergencia, prima de una casa… |
| **Patrimonio (net worth)** | Activos menos deudas a lo largo del tiempo |
| **Inversiones** | Portafolio de brokers y cripto, con rendimiento y composición |
| **Asistente IA** | Preguntas en lenguaje natural, consejos y proyecciones, en la app y por WhatsApp |
| **Hogar compartido** | Invitar a la pareja o la familia con permisos |
| **Reportes** | Tendencias, comparación entre meses y exportación |

### Lo que Monarch no tiene y MoneyTrack sí
- Captura **sin open banking** (SMS, notificaciones, correo, billeteras y estados de cuenta)
- **Factura electrónica de Hacienda** con detalle de cada compra, artículo por artículo
- **SINPE Móvil** como fuente principal de datos
- **Colones y dólares** nativos, con el tipo de cambio oficial del BCCR
- Gastos típicos de Costa Rica: marchamo, aguinaldo, CCSS, RTV, pulpería, feria

---

## 5. Competencia

| Alternativa | Fortaleza | Debilidad |
|---|---|---|
| Monarch Money, YNAB, Copilot | Productos excelentes | Dependen del open banking de EE. UU.; no sirven con bancos de Costa Rica |
| Apps de cada banco | Datos automáticos | Solo ven su propio banco; no incluyen efectivo, cripto ni otras inversiones |
| Apps de gastos manuales (Monefy, Wallet, Spendee) | Simples | Todo es manual; no hay IA ni vista de patrimonio |
| Excel / Google Sheets | Flexible | Tedioso y todo manual |

**Nuestra ventaja defendible:** los lectores de datos ticos (SMS, correos y estados de cuenta de cada banco,
facturas de Hacienda), el diccionario de comercios locales y una IA entrenada con el comportamiento
financiero costarricense. Eso toma tiempo y datos, y un competidor extranjero no lo replica fácilmente.

---

## 6. Modelo de ingresos

**Suscripción, con prueba gratis** (modelo tipo Monarch, adaptado a Costa Rica):

| Plan | Precio inicial a probar | Incluye |
|---|---|---|
| **Gratis** | ₡0 | Registro manual, 1 canal automático, presupuesto básico |
| **Premium** | ~₡3 500–5 000/mes o ~₡35 000–45 000/año | Todos los canales, IA completa, cripto e inversiones, patrimonio, hogar compartido |
| **Enterprise** (futuro) | A la medida | Ver sección 11 |

- Prueba Premium gratis de 14 días.
- Precios por validar con entrevistas y pruebas de precio.
- Sin publicidad y **sin vender datos**: esa es parte de la promesa de marca.

---

## 7. Números básicos (supuestos a validar)

| Supuesto | Año 1 | Año 2 |
|---|---|---|
| Usuarios registrados | 15 000 | 60 000 |
| % en Premium | 5 % | 7 % |
| Usuarios Premium | 750 | 4 200 |
| Ingreso mensual por usuario Premium | ~7 USD | ~7 USD |
| **Ingreso anual recurrente aprox.** | **~63 000 USD** | **~350 000 USD** |

**Costos principales:** equipo de desarrollo, servidores y base de datos, uso de IA (baja si primero se
usan reglas y la IA solo cuando hace falta), correo entrante, auditorías de seguridad, asesoría legal y marketing.

> Costa Rica sirve para **validar y afinar** el producto. Los números grandes vienen con la expansión
> regional y la versión Enterprise.

---

## 8. Cómo conseguir usuarios

1. **Contenido de finanzas personales para ticos** (TikTok, Instagram, YouTube): aguinaldo, marchamo,
   "¿en qué se me fue la quincena?", colones contra dólares.
2. **Alianzas con creadores** de finanzas y cripto de Costa Rica.
3. **Comunidades:** grupos de inversión, cripto y emprendimiento; universidades.
4. **Referidos:** 1 mes de Premium gratis por cada amigo que se suscriba.
5. **Momentos clave del año:** enero (propósitos), aguinaldo (diciembre), marchamo (noviembre y diciembre).

---

## 9. Métricas clave

| Métrica | Meta inicial |
|---|---|
| Usuarios que conectan al menos 1 canal automático en el primer día | > 50 % |
| Transacciones capturadas automáticamente (contra manuales) | > 80 % |
| Precisión de la categorización por IA | > 90 % |
| Retención al día 30 | > 25 % |
| Conversión de prueba a Premium | > 20 % |
| Cancelación mensual de Premium | < 5 % |

---

## 10. Hoja de ruta

| Fase | Tiempo aprox. | Qué incluye |
|---|---|---|
| **0. Validación** | 1 mes | 20–30 entrevistas; recolectar ejemplos reales (tapados) de SMS, correos y estados de cuenta de los bancos principales; landing con lista de espera (meta: 500 personas); prototipos técnicos de Atajos en iOS y del lector de notificaciones en Android |
| **1. MVP** | 3–4 meses | App iOS, Android y web. Cuentas, transacciones, flujo de caja, presupuestos y patrimonio. Captura: correo + factura electrónica, Android (SMS, apps bancarias, Google Wallet), iOS (Atajos para SMS y Apple Pay), estados de cuenta con IA, efectivo. IA: lectura, categorización, eliminación de duplicados y asistente básico |
| **2. Beta cerrada** | 1–2 meses | 100–300 usuarios; medir precisión y retención; ajustar precios |
| **3. Lanzamiento + Premium** | Mes 6–7 | Tiendas de apps, marketing y cobro de Premium |
| **4. Inversiones** | Mes 7–10 | Billeteras y exchanges de cripto; brokers; recurrentes; metas; hogar compartido; asistente por WhatsApp |
| **5. Expansión** | Año 2 | Panamá, Guatemala, Colombia u otros; alianzas con bancos y cooperativas |
| **6. Enterprise** | Año 2+ | Ver sección 11 |

---

## 11. Enterprise (más adelante)

Ideas a validar cuando el producto personal ya funcione:
- **Pymes y emprendedores:** finanzas del negocio separadas de las personales, facturación e impuestos.
- **Beneficio para empleados:** empresas que pagan MoneyTrack Premium a su personal como bienestar financiero.
- **Asesores financieros y contadores:** panel para ver, con permiso, las finanzas de sus clientes.
- **Bancos y cooperativas:** versión de marca blanca o datos anónimos y agregados (siempre con consentimiento).

---

## 12. Equipo necesario (mínimo)

| Rol | Para qué |
|---|---|
| Fundador / producto | Visión, clientes, alianzas, ventas |
| Desarrollo móvil (React Native) | Apps iOS y Android, módulo nativo de notificaciones y Atajos |
| Desarrollo backend + datos | API, captura, base de datos, seguridad |
| IA / aprendizaje automático | Lectura, categorización, asistente |
| Diseño UX/UI | Que se sienta tan pulido como Monarch |
| Legal y seguridad (externo) | Ley 8968, PRODHAB, términos y auditorías |

> Gran parte del desarrollo lo podemos avanzar juntos en este repositorio.

---

## 13. Riesgos y cómo reducirlos

| Riesgo | Mitigación |
|---|---|
| Apple o Google cambian lo que permiten (Atajos, notificaciones) | Varios canales a la vez; el correo y los estados de cuenta funcionan siempre |
| El usuario no configura los canales | Asistente de configuración paso a paso, videos cortos y ayuda por WhatsApp |
| Desconfianza al compartir datos financieros | Solo lectura, nunca contraseñas bancarias, cifrado y política de privacidad clara |
| Costo de la IA | Reglas primero y la IA solo cuando hace falta; medir el costo por usuario |
| Los bancos cambian el formato de sus mensajes | La IA como respaldo cuando falla una plantilla, y monitoreo de errores de lectura |
| Regulación | Asesoría legal antes de lanzar y antes de cualquier función de pagos o inversiones |
| Alcance muy grande | Lanzar por fases; el MVP se centra en el núcleo estilo Monarch con la captura tica |

---

## 14. Próximos pasos inmediatos

- [ ] Elegir los bancos del MVP (sugerencia: BAC, BCR, BN, Banco Popular)
- [ ] Recolectar ejemplos reales, tapados, de SMS, correos y estados de cuenta de esos bancos
- [ ] Prototipo iOS: Atajo que envía un SMS del banco y un pago con Apple Pay a una API de prueba
- [ ] Prototipo Android: lector de notificaciones que capta SINPE y Google Wallet
- [ ] Guion de entrevistas y 20–30 conversaciones con el cliente ideal
- [ ] Landing page con lista de espera
- [ ] Definir el equipo y el presupuesto inicial
- [ ] Consulta legal: Ley 8968, PRODHAB y alcance frente a SUGEF
