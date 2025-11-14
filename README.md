# 🚗 Proyecto: Coche Arduino con Inteligencia Artificial (Red Neuronal)

Este repositorio contiene la implementación en Python de la red neuronal utilizada para controlar un coche Arduino capaz de evitar obstáculos de manera autónoma. El código está pensado para entrenar la red en PC y luego transferir los pesos a Arduino para la fase de ejecución.

---

## 📌 Arquitectura del Proyecto

El sistema se divide en **tres bloques principales**:

### 1️⃣ Entrenamiento de la red neuronal (Python)
- Se entrena una red neuronal `feed-forward` con estructura **[2, 3, 5]**.
- Entradas:
  - Distancia medida por el sensor ultrasónico.
  - Ángulo del servo que orienta el sensor.
- Ambas entradas se normalizan entre **-1 y +1**.
- Salidas (5):
  - Motor 1
  - Motor 2
  - Motor 3
  - Motor 4
  - Función adicional (freno/luz/alerta)

La función de activación utilizada es **tanh**, tanto en capa oculta como en la capa de salida.

Tras el entrenamiento, los pesos son exportados para su uso en Arduino (fase de inferencia).

---

### 2️⃣ Ejecución en Arduino (inferencias)
Aunque este repositorio se enfoca en el entrenamiento, el proyecto se complementa con un Arduino que:
- Recibe los pesos entrenados.
- Ejecuta únicamente la inferencia.
- Lee sensores en tiempo real.
- Decide acciones de movimiento del coche.

---

### 3️⃣ Hardware utilizado
- Arduino Uno o Mega  
- Sensor ultrasónico HC-SR04  
- Servo para mover el sensor  
- Controlador de motores  
- Cuatro motores DC  
- Batería de alimentación  

---

## 📋 Enfoques de resolución de problemas aplicados

✔ **Descomposición del problema**  
Separar la tarea en: detección, decisión y movimiento.

✔ **Enfoque analítico y matemático**  
Uso de una red neuronal para representar relaciones entrada–salida.

✔ **Enfoque iterativo-experimental**  
Ajuste de parámetros mediante prueba y error hasta obtener un modelo útil.

✔ **Transferencia de soluciones**  
Se entrena en PC donde hay más recursos y luego se ejecuta en Arduino, que es limitado.

✔ **Experimentación práctica**  
Se prueba el comportamiento del coche y se corrigen fallas basadas en la observación.

---

## 🧪 Simulación de dos entradas nuevas
Se agregaron dos escenarios adicionales no presentes en los datos de entrenamiento:

- `[-0.5, 0.8]` → Obstáculo leve en la izquierda  
- `[0.7, -0.4]` → Obstáculo cercano en la derecha  

Ambas entradas generan una predicción automática en el código (`main.py`).

---

## 📜 Archivos del repositorio

| Archivo     | Descripción |
|-------------|-------------|
| `main.py`   | Entrenamiento de la red neuronal + simulaciones |
| `README.md` | Resumen del proyecto, arquitectura y enfoques |

---

## 👨‍💻 Autor
Trabajo práctico basado en el proyecto “Programa un coche Arduino con Inteligencia Artificial”.

