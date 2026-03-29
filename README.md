# Latencia del Mercado Sectorial a Noticias

Medición de la Eficiencia Sectorial ante Eventos de Ganancias

## 📌Descripción

Este proyecto analiza qué tan rápido reacciona el mercado, a nivel sectorial, ante un evento corporativo relevante, específicamente anuncios de Ganancias.

La reacción se mide observando el tiempo (en días) que tarda el volumen de negociación en mostrar un spike significativo, definido como un volumen 2.5 veces superior al promedio de los últimos 30 días.

El objetivo es identificar sectores más eficientes (reaccionan rápido) frente a sectores más lentos (reaccionan con retraso), lo que puede revelar:
-  Diferencias en seguimiento institucional
- Asimetrías de información
- Oportunidades de arbitraje temporal

## 🧠Insight clave

- ¿Qué sector presenta el menor retraso promedio entre un anuncio de Ganancias y una reacción fuerte de volumen?

Un menor retraso implica:
- Mayor eficiencia informacional
- Participación institucional temprana
- Menor ventana de oportunidad para traders tácticos

Un mayor retraso puede indicar:
- Menor cobertura analítica
- Dominancia de inversores minoristas
- Potenciales oportunidades de late entry

## 📊Valor de negocio

Este análisis es útil para:
- Trading cuantitativo
Ajustar horizontes de entrada post-evento según el sector.

- Gestión de riesgo
Sectores con reacción tardía pueden experimentar movimientos más violentos cuando el volumen finalmente aparece.

- Asignación sectorial
Preferir sectores con alta eficiencia si se busca menor incertidumbre post-noticia.

- Análisis de microestructura
Medir la velocidad de incorporación de la información al precio.

## 🗂️Estructura de datos requerida

El proyecto utiliza cuatro tablas principales:
- eventos_corporativos
- ticker_id
- fecha
- tipo_evento (filtrado a 'Ganancias')
- precios_diarios
- ticker_id
- fecha
- volume
- tickers
- ticker_id
- sector

## ⚙️Lógica del análisis

- Identificación del evento
- Se seleccionan anuncios de Ganancias por ticker.
- Detección de volumen anómalo
- Se busca el primer día posterior al evento donde:
   volumen_del_día > 2.5 × promedio_volumen_30_días


Cálculo de latencia

Se calcula la diferencia en días entre:
- fecha_evento
- fecha_volumen_anomalo
- Agregación sectorial

*Se obtiene el promedio de días de reacción por sector.*

*Se descartan sectores con menos de 2 observaciones para robustez estadística.*

## 📈Interpretación de resultados

- Promedio bajo de días de reacción
- Sector altamente eficiente
- Reacción casi inmediata a la información
- Promedio alto de días de reacción
- Retraso en absorción de noticias
- Posibles oportunidades de event-driven trading
- El ranking final ordena los sectores desde el más rápido al más lento en reaccionar.

## 🚀 Posibles extensiones

-  reacción de volumen vs. reacción de precio
- Medir latencia para otros eventos (Dividendo, M&A, Problemas Regulatorios)
- Analizar dispersión (no solo promedio) por sector
- Introducir normalización por capitalización bursátil
- Construir un Índice de Eficiencia Informacional Sectorial

## 🧪Notas técnicas

- El umbral de volumen (2.5x) puede ajustarse según el mercado.
- El promedio móvil de 30 días reduce falsos positivos por estacionalidad.
- Recomendado usar índices en:

(ticker_id, fecha) en precios_diarios

(ticker_id, fecha, tipo_evento) en eventos_corporativos

## 👤Autora
Flavia Hepp Proyecto de SQL aplicó un análisis de riesgo basado en eventos.

***
🚀 **¿Qué tan rápido reacciona el mercado… según el sector?**

En mercados eficientes, la información debería reflejarse en precios (y volumen) casi instantáneamente. Pero en la práctica, no todos los sectores reaccionan igual.

👉 Estuve analizando la **latencia sectorial ante eventos de Ganancias**, midiendo cuántos días tarda en aparecer un *spike* significativo de volumen (ratio > 2.5 vs. promedio de 30 días).

💡 **Insight clave:**
Hay sectores donde el mercado reacciona casi de inmediato… y otros donde la señal tarda varios días en materializarse.

---

📊 **¿Qué significa esto?**

* Sectores con **baja latencia** → mayor eficiencia informacional
* Sectores con **alta latencia** → posibles ineficiencias explotables
* Oportunidad para estrategias de **event-driven trading** o **post-earnings drift**

---

🧠 **Cómo lo medí:**

* Detecté eventos de *Ganancias*
* Identifiqué el primer día posterior con volumen anómalo
* Calculé el retraso promedio por sector
* Filtré sectores con suficiente cantidad de eventos

---

⚡ **¿Por qué importa?**

Porque no todos los mercados son igual de rápidos.
Y donde hay retrasos… puede haber oportunidad.

---

📌 Me interesa saber:
¿Han visto diferencias claras en la velocidad de reacción entre sectores en sus análisis?

#DataScience #QuantFinance #StockMarket #SQL #Trading #MachineLearning #Analytics
