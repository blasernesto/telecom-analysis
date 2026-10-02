# 📊 Análisis de Consumo de Servicios Móviles - ConnectaTel

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es analizar cómo usan los servicios móviles (llamadas y SMS) los clientes de **ConnectaTel** en Latinoamérica (operaciones en México y Colombia).

A través del procesamiento y análisis exploratorio de datos (EDA), el estudio busca:
- Entender el comportamiento de consumo y armar perfiles estadísticos según demografía y tipo de plan.
- Identificar valores atípicos (*outliers*) o patrones raros que puedan marcar consumos extremos o fallas en los registros.
- Segmentar a los usuarios por rango etario y nivel de uso.
- Tirar recomendaciones comerciales clave para optimizar la oferta de planes, bajar el churn (cancelaciones) y mejorar la retención de clientes.

---

## 📂 Datasets Utilizados
El análisis cruza información de tres fuentes de datos principales:

1. **`plans.csv`**: El catálogo de planes vigentes. Incluye precio mensual, cuotas de minutos, mensajes y GB incluidos, más las tarifas por excedente.
2. **`users_latam.csv`**: Datos demográficos y de contrato de los clientes (ID, nombre, edad, ciudad, fecha de alta, plan contratado y fecha de baja).
3. **`usage.csv`**: Registro detallado del tráfico real generado (ID de evento, fecha, tipo de servicio, duración de llamadas y cantidad de caracteres en mensajes).

---

## 🔄 Etapas del Análisis
El flujo de trabajo se dividió en las siguientes etapas clave:

1. **Carga y Exploración Inicial:** Chequeo de estructuras, dimensiones (`.shape`), tipos de datos y detección de inconsistencias a simple vista (`.info()`).
2. **Limpieza y Saneamiento de Datos:**
   - Análisis de valores nulos y confirmación de patrones **MAR** (*Missing At Random*) en métricas de uso.
   - Corrección de valores centinela (imputación de la mediana en `age` tras limpiar el `-999` y reemplazo de `"?"` por nulos en `city`).
   - Depuración de fechas fuera de rango (registros colados del año 2026).
3. **Agregación y Métricas por Usuario:** Agrupación del consumo histórico por cliente (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`) e integración con la tabla de usuarios.
4. **Visualizaciones y Detección de Outliers:**
   - Gráficos de distribución (histogramas) comparando por plan comercial.
   - Detección de *heavy users* aplicando el método del Rango Intercuartílico ($Q3 + 1.5 \times \text{IQR}$) mediante *boxplots*.
5. **Segmentación Estratégica:** Clasificación de la base en grupos por nivel de consumo (`Bajo uso`, `Uso medio`, `Alto uso`) y por franjas de edad (`Joven`, `Adulto`, `Adulto Mayor`).
6. **Conclusiones e Insights de Negocio:** Elaboración de hallazgos clave y propuestas estratégicas para la toma de decisiones.
