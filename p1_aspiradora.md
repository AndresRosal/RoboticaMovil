# Vlog de Práctica: Algoritmo para Aspiradora Autónoma

## 1. Introducción y Retos Técnicos
El objetivo de esta práctica es programar el comportamiento de una aspiradora autónoma para que sea capaz de limpiar la mayor superficie posible de una vivienda. El algoritmo debe gestionar los movimientos del robot para evitar obstáculos y asegurar que no queden zonas sin recorrer, optimizando el tiempo de limpieza.

Antes de explicar el funcionamiento, quería comentar que he tenido bastantes complicaciones técnicas con mi portátil para ejecutar el simulador. Por este motivo, entrego la práctica con una semana de retraso. Le agradezco que me haya facilitado el acceso a los laboratorios de la universidad para poder trabajar allí y completar la tarea, ya que era la única forma de avanzar. Disculpe las molestias por la demora.

## 2. Demostración del Algoritmo
A continuación, presento un vídeo que muestra el comportamiento del robot en el entorno de pruebas. Es importante notar que el vídeo es una muestra del funcionamiento de la lógica programada; aunque no se vea la limpieza de la casa completa por cuestiones de duración del clip, el algoritmo está diseñado para que, con el tiempo suficiente, la aspiradora cubra la totalidad de la superficie.

<!-- Contenedor del video -->
<div style="text-align: center; margin: 20px 0;">
    <video width="100%" controls style="border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.2);">
        <source src="video-practica.mp4" type="video/mp4">
        Tu navegador no soporta la reproducción de video.
    </video>
</div>

## 3. Estrategia de Implementación: Máquina de Estados
Para lograr una cobertura eficiente, he diseñado una **Máquina de Estados Finitos**. El robot alterna entre diferentes tipos de movimiento según lo que detectan sus sensores:

1.  **Retroceso y Giro:** Cuando el sensor láser detecta un obstáculo cerca (menos de 0.35m), el robot retrocede un poco y gira hacia una dirección aleatoria. He programado tanto el tiempo de giro como el sentido (izquierda o derecha) de forma **aleatoria** para evitar que el robot se quede atrapado en bucles o esquinas.
2.  **Movimiento Recto:** Tras girar, el robot avanza en línea recta para desplazarse a una nueva zona.
3.  **Movimiento en Espiral:** Si el robot detecta que tiene mucho espacio libre a su alrededor, activa el modo espiral. Incrementando la velocidad lineal poco a poco, consigue limpiar grandes áreas abiertas de forma mucho más eficiente que con movimientos aleatorios.

## 4. Control y Sensores
He configurado un filtrado de los datos del láser para que el robot reaccione correctamente incluso si el sensor devuelve valores no válidos en algún momento. El control de la velocidad y el giro está ajustado para que las transiciones entre estados sean fluidas, permitiendo que la aspiradora reaccione rápido ante las paredes mientras mantiene un patrón de limpieza constante en las zonas despejadas.

En resumen, la combinación de trayectorias rectas, giros aleatorios y patrones en espiral permite que el robot explore el entorno de manera autónoma y efectiva.
