# Nota metodológica — Base de datos CRM del plan de marketing (muestra)
**Proyecto:** ibis Styles Armenia · **Fecha:** 17/10/2026

## 1. Qué es esta base y de dónde se sacó
La base `crm_ibis_styles_armenia.db` (con su script `crm_ibis_styles_armenia.sql` y su copia de consulta en Excel) es una **base de datos relacional de ejemplo construida para la sección 7 del plan de marketing** del proyecto ibis Styles Armenia.

- **No proviene de clientes reales ni de un CRM corporativo.** Los nombres, correos, celulares, interacciones y operaciones son **100 % ficticios**: se inventaron para el ejercicio, tal como lo declaran la hoja "Instrucciones" del Excel y el encabezado del script.
- Lo que sí es real del proyecto es el **diseño**: modela el embudo comercial completo (captación → calificación con puntaje → reunión/visita → opción → venta), el inventario de suites y el cumplimiento de la Ley 1581 de 2012.

## 2. Insumos usados para construirla
- **Metas y supuestos del plan:** 6.000 leads en 12 meses, 90 suites vendidas, conversión meta 1,5 %, 10 % de referidos, presupuesto de marketing (parámetro del plan) y campañas Fase 0 y C1–C4 con fechas, presupuestos y metas propias.
- **Segmentos objetivo** (A–E) y su meta de suites; **canales** de captación (Digital, Eventos, Referidos, Alianzas).
- **Tabla 17 del plan:** criterios y puntos del lead scoring (reunión 25, capacidad 25, referido 20, etc.).
- **Inventario del proyecto:** 180 suites con las **áreas por habitación tomadas de la planta tipo del PDF** y precios de lista como supuestos del plan.
- **Marco legal:** cada cliente tiene su registro de autorización de tratamiento de datos (Ley 1581 de 2012).

## 3. Cómo se armó la muestra (200 leads)
- Fechas de registro alineadas con la línea de tiempo del plan (nov-2026 → oct-2027).
- El embudo respeta las tasas meta: **200 → 80 MQL → 40 SQL → 20 reunión → 5 opción → 3 venta**.
- Interacciones simuladas por cliente (correo abierto, dossier, recorrido virtual, eventos, visitas, reuniones, intentos sin respuesta) para que **el puntaje de cada lead sea un cálculo real** sobre datos, no un valor digitado.
- Casos límite incluidos a propósito para probar las reglas: 2 clientes con **baja y autorización revocada** (no contactables), 9 **referidos** con relación autorreferencial, 2 **opciones** en curso y 3 **ventas**, unidades separadas/vendidas coherentes con cada operación.

## 4. Por qué esta muestra (justificación)
1. **Representatividad:** replica el embudo completo con todos sus estados y canales; permite calcular puntaje, conversión, CAC por campaña y KPIs *con datos*, no con supuestos sueltos.
2. **Trazabilidad:** cada cifra del informe sale de tablas relacionadas y puede rastrearse hasta la fila que la origina.
3. **Tamaño manejable:** 200 leads y 1.156 interacciones demuestran el modelo sin ser un dataset pesado para consultar en Excel o SQLite.
4. **Ética y legalidad:** al ser ficticia puede publicarse sin exponer datos personales, e incluye el mecanismo de autorización/baja que exige la ley.
5. **Reemplazable:** cuando existan datos reales (CRM o formularios), se cargan en las mismas tablas (`cliente`, `interaccion`, `operacion`, `autorizacion_datos`) **sin cambiar la estructura ni las vistas**: el modelo queda listo para producción.

## 5. Uso y límites
- **Uso:** consultas de negocio del `.sql`, vistas `v_*` para KPIs y el Excel para consulta; puesta en marcha verificada (integridad, relaciones y KPIs contra meta).
- **Límite:** los resultados (3 ventas, 1.148 COP millones) describen la **muestra de ejemplo**, no ventas reales; las metas y supuestos sí son los del plan.
- **No usar para contactar a nadie:** los contactos son inventados y pueden parecerse a personas reales.
