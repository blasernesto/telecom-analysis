# 📊 Análisis de Uso de Servicios Móviles - ConnectaTel

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es analizar el comportamiento real de uso de los servicios móviles (llamadas y mensajes de texto) por parte de los clientes de **ConnectaTel** en Latinoamérica (México y Colombia). 

A través del procesamiento y análisis exploratorio de datos, el estudio busca:
- Identificar patrones de consumo y perfiles estadísticos por segmentos demográficos y tipo de plan.
- Detectar valores atípicos (*outliers*) o patrones inusuales que puedan indicar comportamientos extremos o errores de registro.
- Crear segmentaciones de clientes basadas en edad y nivel de consumo[cite: 1].
- Formular recomendaciones comerciales estratégicas para optimizar la oferta de planes, reducir el churn y mejorar la satisfacción del usuario[cite: 1].

---

## 📂 Datasets Utilizados
El análisis integra información proveniente de tres fuentes de datos principales[cite: 1]:

1. **`plans.csv`**: Catálogo de los planes comerciales vigentes[cite: 1]. Incluye precio mensual, cuota incluida de minutos, mensajes y GB, así como los costos por excedente[cite: 1].
2. **`users_latam.csv`**: Información demográfica y contractual de los clientes (ID, nombre, edad, ciudad, fecha de registro, plan contratado y fecha de cancelación/churn)[cite: 1].
3. **`usage.csv`**: Detalle del tráfico y consumo real generado por los usuarios (ID de evento, fecha, tipo de servicio, duración de llamadas y longitud de mensajes)[cite: 1].

---

## 🔄 Etapas del Análisis Realizadas
El flujo de trabajo analítico se estructuró en las siguientes etapas clave[cite: 1]:

1. **Carga y Exploración Inicial:** Inspección de estructuras, dimensiones (`.shape`), tipos de datos e identificación de inconsistencias iniciales (`.info()`)[cite: 1].
2. **Control de Calidad y Limpieza de Datos:**
   - Análisis de valores nulos y confirmación de mecanismos **MAR** (*Missing At Random*) en métricas de uso[cite: 1].
   - Detección y corrección de valores *sentinel* (imputación de la mediana en `age` tras corregir `-999` y reemplazo de `"?"` por nulos en `city`)[cite: 1].
   - Saneamiento y estandarización de fechas fuera de rango temporal (registros del año 2026)[cite: 1].
3. **Resumen Estadístico y Agregación:** Agrupación del consumo a nivel de usuario para construir variables agregadas de tráfico histórico (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`) e integración con el perfil del usuario[cite: 1].
4. **Visualización de Distribuciones y Detección de Outliers:**
   - Construcción de histogramas con diferenciación por plan comercial[cite: 1].
   - Identificación y evaluación de *heavy users* utilizando el método estadístico del Rango Intercuartílico ($Q3 + 1.5 \times \text{IQR}$) mediante *boxplots*[cite: 1].
5. **Segmentación Estratégica de Clientes:** Clasificación de la base en grupos por nivel de uso (`Bajo uso`, `Uso medio`, `Alto uso`) y por rangos de edad (`Joven`, `Adulto`, `Adulto Mayor`)[cite: 1].
6. **Insight Ejecutivo y Recomendaciones:** Formulación de conclusiones de negocio y oportunidades comerciales para la directiva[cite: 1].
