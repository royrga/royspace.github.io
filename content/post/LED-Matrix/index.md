---
title: "Matriz de LEDs"
description: "Elaboración de matriz de LEDs e implementación del sistema que genera, procesa y despliega imagenes/video desde un ordenador por comunicación serial"
date: 2025-09-23T10:42:05-06:00
image: "LEDsMatrix.png"
categories: [
  "Ingenieria",
  "Arte"
] 
math: 
license: 
hidden: false
comments: false 
---

## Descripción

Matriz de LEDs con la capacidad de mostrar imágenes o video con
una resolución de 9x20 pixeles y una tasa de refresco de 90 fps.
Las imágenes/videos son procesados desde una computadora para
codificar los datos y enviarlos a un microcontrolador (stm32)
para generar la señal con los datos que serán consumidos por
las tiras LED.

El proyecto consta de 3 elementos principales:

- Tiras LEDs(ws2812b): conectadas en serie
- Microcontrolador(STM32 Nucleo-C031C6): Recibe los datos procesados por
  comunicación serial
- Computadora (Windows, OS, Linux): Ejecuta script que procesa las
  imágenes/videos y envía los datos por serial. Adicionalmente también es
  capaz de enviar animaciones generadas con el software Processing.

## Construcción

Tiras
<iframe src="https://drive.google.com/file/d/1jGsHLDiE8iEuCQnZ_e_qlwAACXyo7wcH/preview" width="640" height="480" allow="autoplay"></iframe>

Cableado
<iframe src="https://drive.google.com/file/d/1O0PWjU6M_5IP3a468848yCramvv21C1N/preview" width="640" height="480" allow="autoplay"></iframe>

## Desarrollo

### 1er Prototipo

Usa el microcontrolador Arduino NANO.

Primeras pruebas procesando imágenes para adecuar a la resolución de la matriz
y obtener datos de cada pixel

<iframe src="https://drive.google.com/file/d/1r-5-okGCz9bAncuUuZtjhijFxamQi8sb/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1cABqsmE-tSfhUwAzuJUTofJxQn_K5qEz/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1IdqRH6i3iWQoCqvb2NYy3a6TcUdu2diJ/preview" width="640" height="480" allow="autoplay"></iframe>

Primera prueba enviando multiples imágenes, en el monitor se muestra la animación que generó
las imágenes. Las velocidades de reproducción entre la matriz LEDs y el monitor
no coinciden por las capacidades limitadas del microcontrolador.

<iframe src="https://drive.google.com/file/d/1A4c_a9bTwjHB_z-FzImyxUiTiTNOU898/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1pKZGJBVLj4ZRMxI0JSbFlXFXAXh7fBK9/preview" width="640" height="480" allow="autoplay"></iframe>

### 2do Prototipo

Para este prototipo se uso el microcontrolador Nucleo-C031C6 de STM32,
lo cual mejoro significativamente el rendimiento ya que se hizo uso
de la función de DMA(Direct Memory Access) para la comunicación serial y
para la generación de PWM la cual se usa como señal de salida hacia las
tiras LED, así logrando una tasa de hasta 90 fps.

Los frames generados para los videos proyectados por la matriz de LEDs
son generados, procesados y enviados uno tras otro sin necesidad de
almacenar cada frame a diferencia del 1er prototipo que requería tener
todos los frames almacenados como imágenes.

Las animaciones son generadas con código desarrollado en Processing.

Animación interactiva en tiempo real , interacción con el cursor.
<iframe src="https://drive.google.com/file/d/1EK_LVnaq31ZS-c8XeCOHUmZpKKA7tsvD/preview" width="640" height="480" allow="autoplay"></iframe>

Animaciones
<iframe src="https://drive.google.com/file/d/1HV0y0gYDatqPG0RqtwYk1_7pcZH2C5g4/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1IP98pjyZ0BjVF7B2LfbkUCixOCzOVuJM/preview" width="640" height="480" allow="autoplay"></iframe>

Video tomado de la cámara web y direccionado a la matriz de LEDs
<iframe src="https://drive.google.com/file/d/1dnlYpQqgUCracpzM0efwfWHSnAPcrTGG/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1V2TbvfwGl3p5MWDXpLCNgd-ieySDpzkh/preview" width="640" height="480" allow="autoplay"></iframe>

Animación interactiva con entrada de audio desde guitarra
<iframe src="https://drive.google.com/file/d/1LQXzg63VPCh1lM5jYrQVkoGE7Sm4vYp2/preview" width="640" height="480" allow="autoplay"></iframe>
