# MoneyTrack — Plan de negocio (v0.1, borrador)

> Documento de trabajo. Las cifras son **supuestos para validar**, no datos de mercado confirmados.

---

## 1. Resumen

**MoneyTrack** es una app de finanzas personales que ayuda a las personas a saber en qué se les va el dinero y a ahorrar más, **sin tener que conectar su cuenta bancaria**.

- **Problema:** mucha gente llega a fin de mes sin saber en qué gastó. Las apps que existen o son complicadas, o piden conectar el banco (desconfianza), o no funcionan bien con los bancos y monedas locales.
- **Solución:** registrar un gasto en menos de 5 segundos, ver un resumen claro del mes y recibir alertas simples ("ya gastaste el 80 % de tu presupuesto de comida").
- **Diferencial:** privacidad (los datos quedan en tu teléfono), rapidez para registrar y diseño pensado para el usuario hispanohablante (moneda local, efectivo, gastos informales).
- **Modelo de ingresos:** freemium (gratis + versión Pro de pago).

---

## 2. Cliente ideal

| | Perfil principal |
|---|---|
| **Quién** | Personas de 20 a 35 años con ingresos propios (empleados jóvenes, estudiantes que trabajan) |
| **Situación** | Cobran quincenal o mensual, usan tarjeta y efectivo, no llevan un control |
| **Dolor** | "No sé en qué se me va el dinero", "quiero ahorrar pero no me alcanza" |
| **Qué intentaron** | Excel, notas del celular, apps que abandonaron por complicadas |
| **Qué valoran** | Rapidez, simplicidad, privacidad, que se vea bien |

**Perfil secundario (más adelante):** parejas que comparten gastos.

---

## 3. Competencia

| App | Fortaleza | Debilidad que aprovechamos |
|---|---|---|
| Excel / Google Sheets | Gratis y flexible | Tedioso, no funciona bien en el celular |
| Monefy | Muy simple | Pocos análisis, poca motivación para ahorrar |
| Wallet (BudgetBakers), Spendee, Money Lover | Completas | Recargadas; varias funciones clave son de pago |
| YNAB | Método de presupuesto muy fuerte | Caro, en inglés, curva de aprendizaje alta |
| Apps de los bancos | Datos automáticos | Solo ven un banco; no incluyen el efectivo |

**Nuestro lugar:** tan simple como Monefy, con metas de ahorro y alertas útiles, en español, con buen soporte para el efectivo.

---

## 4. Propuesta de valor

> "Sabe en qué se va tu dinero en 5 segundos al día."

1. **Registro ultrarrápido:** monto → categoría → listo.
2. **Resumen del mes claro:** cuánto entró, cuánto salió y en qué.
3. **Presupuestos por categoría** con alertas.
4. **Metas de ahorro** con progreso visual.
5. **Privado por defecto:** sin cuentas bancarias ni registro obligatorio.

---

## 5. Producto: MVP (primera versión)

Lo **mínimo** para probar que la gente lo usa todos los días.

### Entra en el MVP
- Registrar ingresos y gastos (monto, categoría, fecha, nota opcional)
- Categorías predefinidas y editables
- Pantalla de inicio: saldo del mes, total de gastos y gráfico por categoría
- Historial con filtros por mes y categoría
- Presupuesto mensual por categoría con alerta al 80 % y al 100 %
- Datos guardados en el dispositivo
- Exportar a CSV (para que el usuario no sienta que sus datos quedan "atrapados")

### NO entra en el MVP (después)
- Cuentas de usuario y sincronización en la nube
- Conexión con bancos
- Gastos compartidos
- Varias monedas
- Lectura automática de SMS o notificaciones del banco

---

## 6. Modelo de ingresos

**Freemium**

| Gratis | Pro (suscripción) |
|---|---|
| Gastos e ingresos ilimitados | Todo lo gratuito |
| Hasta 3 presupuestos | Presupuestos ilimitados |
| 1 meta de ahorro | Metas ilimitadas |
| Resumen mensual | Reportes avanzados y comparación entre meses |
| — | Respaldo en la nube y varios dispositivos |
| — | Exportar a PDF/Excel |

**Precio inicial para probar:** aprox. 2–3 USD/mes o 20–25 USD/año (ajustar al país; precios regionales en Play Store / App Store).

**Otras fuentes posibles (más adelante):** alianzas con productos financieros (cuentas de ahorro, inversión), siempre transparentes y sin vender los datos del usuario.

---

## 7. Números básicos (supuestos a validar)

| Supuesto | Valor |
|---|---|
| Usuarios activos al mes, año 1 | 10 000 |
| % que paga Pro | 3 % → 300 usuarios |
| Ingreso promedio por usuario de pago | 2 USD/mes |
| **Ingreso mensual estimado** | **~600 USD/mes** |

Con los datos guardados en el teléfono, el costo de servidores del MVP es casi **cero**. Los costos principales son el tiempo de desarrollo, las cuentas de desarrollador (Google Play: pago único de 25 USD; Apple: 99 USD/año) y el marketing.

**Conclusión:** el negocio escala por **volumen de usuarios** y por la **tasa de conversión a Pro**. Esas son las dos métricas que hay que empujar.

---

## 8. Cómo conseguir usuarios

1. **Contenido en TikTok, Instagram Reels y YouTube Shorts** sobre finanzas personales ("en qué se me fue la quincena", retos de ahorro de 30 días).
2. **Retos de ahorro dentro de la app** que se comparten en redes.
3. **Posicionamiento en tiendas (ASO):** palabras clave como "control de gastos", "presupuesto" y "ahorro".
4. **Comunidades:** grupos universitarios y comunidades de finanzas personales.
5. **Recomendaciones:** 1 mes de Pro gratis por cada amigo que se una.

---

## 9. Métricas clave

| Métrica | Meta inicial |
|---|---|
| Usuarios que registran al menos 1 gasto el primer día | > 60 % |
| Retención al día 7 | > 25 % |
| Retención al día 30 | > 12 % |
| Gastos registrados por usuario activo por semana | > 10 |
| Conversión a Pro | 2–5 % |

---

## 10. Riesgos y cómo reducirlos

| Riesgo | Mitigación |
|---|---|
| La gente deja de registrar gastos (el problema #1 de estas apps) | Registro en 5 segundos, recordatorio diario, rachas y metas |
| Mercado con mucha competencia | Nicho claro: simple, privado, en español y con buen manejo del efectivo |
| Pocos usuarios pagan | Probar precios y beneficios Pro pronto; precios por país |
| Perder datos al cambiar de teléfono | Exportar/importar desde el MVP; respaldo en la nube en Pro |
| Temas legales con datos financieros | Al no conectar bancos ni guardar datos en servidores, el riesgo inicial es bajo; revisarlo antes de lanzar la nube |

---

## 11. Hoja de ruta

| Fase | Duración aprox. | Objetivo |
|---|---|---|
| **0. Validación** | 2–3 semanas | Entrevistar a 15–20 personas del perfil; landing page con lista de espera (meta: 200 correos) |
| **1. MVP** | 6–8 semanas | App con las funciones de la sección 5; prueba cerrada con 50–100 personas |
| **2. Lanzamiento** | 4 semanas | Publicar en tiendas, empezar contenido en redes y medir retención |
| **3. Monetización** | Mes 4–6 | Lanzar Pro, respaldo en la nube y reportes avanzados |
| **4. Crecimiento** | Mes 6+ | Gastos compartidos, varias monedas, alianzas |

---

## 12. Próximos pasos inmediatos

- [ ] Definir el país o los países de lanzamiento
- [ ] Escribir el guion de entrevistas y hablar con 15–20 personas
- [ ] Crear una landing page con lista de espera
- [ ] Diseñar las pantallas del MVP (inicio, agregar gasto, historial, presupuestos)
- [ ] Elegir la tecnología (sugerencia: app web instalable o React Native, con los datos en el dispositivo)

---

## Preguntas abiertas

1. ¿En qué país o países lanzamos primero?
2. ¿Tienes presupuesto para marketing o será 100 % orgánico?
3. ¿Quién va a programar la app (tú, un socio, o la hacemos juntos aquí)?
4. ¿Nombre final: "MoneyTrack" o algo más pegajoso en español?
