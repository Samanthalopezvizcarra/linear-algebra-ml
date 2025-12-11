# 🧮 Álgebra Lineal Aplicada a Machine Learning

Proyecto de Álgebra Lineal que combina teoría matemática con aplicaciones prácticas de machine learning en la compañía de seguros **Sure Tomorrow**.

---

## 📘 Descripción del proyecto
El objetivo del proyecto es demostrar aplicaciones del álgebra lineal en machine learning mediante varias tareas basadas en datos de clientes de seguros. Se trabaja con el dataset `/datasets/insurance_us.csv` que contiene información sobre:

**Características:**  
- Sexo  
- Edad  
- Salario  
- Número de familiares  

**Objetivo:** Número de beneficios de seguro recibidos por persona en los últimos cinco años.

Las tareas a desarrollar incluyen:

1. **Encontrar clientes similares** a un cliente determinado para ayudar en marketing.  
2. **Predecir probabilidad de recibir un beneficio de seguro** y comparar con un modelo dummy.  
3. **Predecir la cantidad de beneficios esperados** mediante regresión lineal.  
4. **Proteger los datos personales** mediante ofuscación sin afectar la calidad del modelo.  

---

## 🛠️ Proceso del proyecto

### 1. Preparación de datos
- Carga y exploración del dataset.  
- Verificación de valores faltantes, outliers y consistencia de los datos.  
- Escalado de características para tareas basadas en distancias (kNN).

---

### 2. Tarea 1: Búsqueda de clientes similares
- Escalado de datos balancea la influencia de variables grandes (`income`) y pequeñas (`age`).  
- Se probó distancia Manhattan; con estos datos la elección fue indistinta, aunque en otros datasets puede afectar el desempeño.  

---

### 3. Tarea 2: Predicción de probabilidad de recibir beneficio
- Modelo kNN vs modelo Dummy.  
- Resultados para k=1:
  - Datos originales: F1 = 0.6  
  - Datos escalados: F1 = 0.92  
- Con k más alto, el F1 de datos originales disminuye mientras que con datos escalados se mantiene alto.  
- Conclusión: **escalado de variables es crucial para kNN**, asegurando estabilidad y mejores predicciones.

---

### 4. Tarea 3: Predicción de cantidad de beneficios (Regresión Lineal)
- Datos originales: RMSE = 0.34, R² = 0.43 → buen ajuste.  
- Datos escalados: R² cerca de 0 → la normalización afecta la solución analítica simple.  
- Conclusión: **Regresión lineal funciona mejor con datos originales** en esta implementación, aunque el escalado puede ser útil en otros contextos o librerías.

---

### 5. Tarea 4: Protección de datos (Ofuscación)
- Se aplicó una **transformación lineal invertible** a los datos.  
- Resultados:
  - RMSE y R² idénticos entre datos originales y ofuscados.  
  - Los coeficientes individuales cambian, pero las predicciones y calidad del modelo permanecen iguales.  
- Conclusión: La ofuscación protege la privacidad sin afectar la precisión de la regresión lineal.

---

## 🏆 Resultados principales
- kNN con datos escalados supera al modelo Dummy en todas las configuraciones.  
- Regresión lineal es efectiva con datos originales para predecir beneficios esperados.  
- Ofuscación de datos garantiza privacidad manteniendo la exactitud de predicciones.  

---

## 🧰 Tecnologías utilizadas
- Python  
- pandas · numpy  
- scikit-learn  
- matplotlib / seaborn  
