# Proyecto LAN9696 - Switch L3 Ethernet y Fibra Óptica

Este repositorio contiene el desarrollo de un proyecto de diseño electrónico basado en el dispositivo **LAN9696**, orientado a la implementación de un **switch de capa 3 (Layer 3)** con interfaces Ethernet, conectividad por fibra óptica, memoria externa DDR4 y circuitos de alimentación necesarios para su funcionamiento.

El proyecto fue desarrollado utilizando herramientas de **Cadence**, específicamente **OrCAD Capture** para el diseño esquemático y **Allegro PCB Editor** para el diseño físico de la PCB. La finalidad principal del repositorio es documentar de forma ordenada el avance del diseño, incluyendo el esquemático, el layout PCB, las librerías utilizadas, archivos exportados e imágenes representativas de los bloques más importantes del sistema.

---

## Tabla de contenido

1. [Explicación del proyecto](#1-explicación-del-proyecto)
2. [Diagrama de bloques](#2-diagrama-de-bloques)
3. [Bloques importantes del proyecto](#3-bloques-importantes-del-proyecto)
   - [System Control](#31-system-control)
   - [Quad PHY con PoE MagJack](#32-quad-phy-con-poe-magjack)
   - [SFP](#33-sfp)
   - [DDR4](#34-ddr4)
   - [Potencia](#35-potencia)
4. [Requerimientos y decisiones de diseño](#4-requerimientos-y-decisiones-de-diseño)
5. [Alcance del proyecto](#5-alcance-del-proyecto)
6. [Estructura del repositorio](#6-estructura-del-repositorio)

---

# 1. Explicación del proyecto

Este proyecto consiste en el diseño electrónico de un **switch L3 de fibra óptica y Ethernet**, basado en el componente principal **LAN9696**. El objetivo del diseño es representar una tarjeta de red de alto desempeño, capaz de integrar múltiples interfaces de comunicación cableada, conectividad óptica, memoria externa y circuitos de soporte para alimentación, control y configuración.

Un switch de capa 3 combina funciones de conmutación de red con capacidades de enrutamiento, por lo que este tipo de sistema puede utilizarse en aplicaciones donde se requiere administrar tráfico entre diferentes dispositivos, redes o segmentos de red. En este proyecto, el LAN9696 actúa como el bloque central encargado de la gestión y procesamiento de las interfaces del sistema.

El diseño contempla una arquitectura compuesta por varios bloques funcionales:

- Bloque central de procesamiento y switching basado en el **LAN9696**.
- Interfaces Ethernet mediante **PHYs externos**.
- Conectores **RJ45 MagJack** para conexión física de red.
- Interfaz **SFP** para fibra óptica.
- Memoria externa **DDR4**.
- Circuitos de potencia mediante conversores DC-DC y reguladores.
- Señales de control, reset, comunicación, sincronización y configuración.
- Diseño esquemático completo y avance parcial del layout PCB.

La propuesta original del sistema está orientada a un switch con múltiples puertos de red, incluyendo **24 puertos RJ45** y al menos **1 interfaz de fibra óptica**, además de memoria externa para soporte del sistema. Por la complejidad del diseño, se trabajó principalmente en los bloques más representativos y necesarios para demostrar la arquitectura general del proyecto.

El proyecto se desarrolló como una práctica de diseño electrónico avanzado, utilizando herramientas profesionales para la creación del esquemático y del layout PCB. Además, el repositorio permite documentar el proceso de desarrollo, organizar los archivos fuente y presentar visualmente los bloques más importantes del diseño.

---

# 2. Diagrama de bloques

El siguiente diagrama muestra la arquitectura general del sistema propuesto. En él se representan los principales bloques funcionales del switch, incluyendo potencia, control del sistema, memoria, interfaces Ethernet, módulos de fibra óptica y señales de sincronización.

<div align="center">
  <img src="Imagenes/Diagrama de Bloques Switch L3.jpeg" alt="Diagrama de bloques" width="45%"/>
</div>
El sistema está organizado alrededor del bloque central de procesamiento, donde se encuentra el dispositivo principal encargado de la administración de las interfaces de red. Desde este bloque se conectan las diferentes secciones del diseño, como las memorias del sistema, los PHYs Ethernet, los conectores RJ45, los módulos SFP y los circuitos auxiliares.

## Explicación del diagrama de bloques

El diagrama se divide en las siguientes secciones principales:

### Potencia

La sección de potencia se encarga de recibir la alimentación principal del sistema y convertirla a los diferentes niveles de voltaje requeridos por cada bloque. En este proyecto se contemplan conversores DC-DC y reguladores LDO para generar voltajes como 5V, 3.3V y otros niveles necesarios para el funcionamiento del LAN9696, memorias, PHYs y módulos externos.

### Switch / Procesamiento central

Este bloque representa el núcleo del sistema. Aquí se encuentra el dispositivo encargado de procesar, administrar y conmutar el tráfico de red. Desde este bloque se conectan las interfaces Ethernet, memorias, señales de control, sincronización y otros periféricos necesarios.

### Gestión e I/O

Esta sección incluye elementos de control y administración del sistema, como consola USB/UART, GPIOs, indicadores de estado y señales de reset. Estos elementos permiten configurar, monitorear y depurar el sistema durante su funcionamiento o durante pruebas de laboratorio.

### Interfaces Ethernet

Este bloque representa la conexión entre el sistema central y los puertos RJ45. Los PHYs Ethernet son los encargados de adaptar las señales del procesador principal hacia las señales eléctricas utilizadas en los cables Ethernet. Posteriormente, estas señales llegan a los conectores RJ45 MagJack.

### Interfaces de fibra

La sección de fibra óptica utiliza módulos SFP o SFP+ para permitir enlaces ópticos. Estos enlaces son útiles para conexiones de mayor distancia, enlaces troncales o uplinks hacia otros equipos de red.

### Memorias del sistema

El sistema incluye memoria externa DDR4, además de otras posibles memorias de soporte como Flash o eMMC. Estas memorias permiten almacenar información de configuración, firmware, tablas, buffers u otros datos utilizados durante la operación del switch.

### Clocks y sincronización

Esta sección incluye señales de reloj, sincronización y temporización. Estos bloques son importantes en sistemas de comunicación, ya que permiten mantener referencias de tiempo estables para el funcionamiento correcto de interfaces de alta velocidad.

---

# 3. Bloques importantes del proyecto

A continuación se presentan los bloques más importantes del proyecto. Cada bloque incluye una imagen del esquemático, una imagen del layout cuando corresponde y una breve explicación de su función dentro del sistema.

---

## 3.1 System Control

El bloque de **System Control** corresponde a una de las secciones principales del diseño, ya que agrupa señales de configuración, control, comunicación y soporte asociadas al LAN9696.

### Esquemático - System Control

<div align="center">
  <img src="Imagenes/LAN9696 System Control esquematico.png" alt="System control esquematico" width="45%"/>
</div>

En esta sección del esquemático se observan conexiones relacionadas con el control general del sistema. Entre estas señales se incluyen interfaces de configuración, líneas GPIO, señales JTAG, reset, comunicación auxiliar y conexiones necesarias para la operación del dispositivo principal.

Este bloque es importante porque permite la inicialización, depuración y administración del sistema. Además, permite tener acceso a señales clave durante pruebas, diagnóstico o configuración del hardware.

### Layout - System Control

<div align="center">
  <img src="Imagenes/LAN9696 System Control layout.png" alt="System control layout" width="45%"/>
</div>

En el layout se muestra la ubicación física de componentes asociados al bloque de control. Se observan conectores, resistencias, capacitores y componentes auxiliares relacionados con señales de control y comunicación.

La colocación de estos elementos busca mantener una distribución ordenada dentro de la PCB y facilitar el acceso a señales importantes para pruebas o depuración.

---

## 3.2 Quad PHY con PoE MagJack

El bloque de **Quad PHY Ethernet** permite conectar el sistema principal con los puertos físicos Ethernet. Los PHYs son circuitos encargados de convertir y adaptar las señales digitales provenientes del sistema central hacia las señales eléctricas utilizadas por Ethernet.

### Esquemático - Quad PHY

<div align="center">
  <img src="Imagenes/Quad PHY esquematico.png" alt="Quad PHY esquematico" width="45%"/>
</div>


En el esquemático del Quad PHY se observan señales diferenciales, conexiones de alimentación, capacitores de desacoplo, resistencias de configuración y señales de comunicación con el LAN9696.

Este bloque es fundamental porque funciona como intermediario entre el procesador principal del switch y los conectores RJ45. Sin los PHYs Ethernet, el sistema no podría comunicarse directamente con dispositivos externos a través de cables de red.

### Layout - Quad PHY

<div align="center">
  <img src="Imagenes/Quad PHY layout.png" alt="Quad PHY layout" width="45%"/>
</div>

En el layout se puede observar la distribución física de los PHYs y su cercanía con los conectores RJ45. Esta sección requiere especial cuidado debido al manejo de señales de alta velocidad y pares diferenciales.

El ruteo de este bloque es una de las partes más complejas del proyecto, ya que las señales Ethernet deben respetar buenas prácticas de diseño, como control de impedancia, separación entre pares, longitudes adecuadas y reducción de interferencias.

### Esquemático - PoE MagJack

<div align="center">
  <img src="Imagenes/POE Magjack.png" alt="Rj45" width="45%"/>
</div>

Los conectores **RJ45 MagJack** representan la interfaz física entre el switch y los cables Ethernet. Estos conectores integran el puerto RJ45 junto con elementos magnéticos necesarios para el acoplamiento y aislamiento eléctrico de la señal Ethernet.

En esta parte del esquemático se observan conexiones de pares diferenciales, señales LED de estado y líneas auxiliares. Los LEDs permiten indicar estados de enlace o actividad, mientras que las señales principales permiten la comunicación entre el equipo externo y el PHY Ethernet.

El uso de conectores MagJack facilita la implementación del diseño porque integra en un solo componente la conexión física y los elementos magnéticos requeridos para Ethernet.

---

## 3.3 SFP

El bloque **SFP** corresponde a la interfaz de fibra óptica del sistema. Esta sección permite conectar un módulo transceptor óptico para establecer enlaces de mayor distancia o enlaces de alta velocidad.

### Esquemático - SFP

<div align="center">
  <img src="Imagenes/SFP esquematico.png" alt="SFP esquematico" width="45%"/>
</div>

En el esquemático del bloque SFP se observan señales diferenciales de transmisión y recepción, alimentación del módulo, líneas de control, señales de detección y elementos pasivos necesarios para su funcionamiento.

Esta interfaz permite que el switch no dependa únicamente de puertos RJ45, sino que también pueda conectarse mediante fibra óptica. Esto resulta útil en redes donde se requiere mayor distancia de transmisión, reducción de interferencia electromagnética o enlaces troncales entre equipos de red.

### Layout - SFP

<div align="center">
  <img src="Imagenes/SFP layout.png" alt="SFP layout" width="45%"/>
</div>

En el layout se observa la ubicación física del conector SFP y el ruteo asociado. Normalmente, este tipo de conector debe colocarse cerca del borde de la PCB para permitir la inserción del módulo transceptor desde el exterior del equipo.

El diseño de esta sección requiere cuidado por el manejo de señales diferenciales de alta velocidad, además de una correcta ubicación mecánica para que el módulo pueda conectarse adecuadamente.

---

## 3.4 DDR4

La memoria **DDR4** forma parte de los bloques de soporte del sistema. Su función principal es proporcionar almacenamiento temporal de alta velocidad para el procesamiento y operación del switch.

### Esquemático - DDR4

<div align="center">
  <img src="Imagenes/DDR4 esquematico.png" alt="DDR4 esquematico" width="45%"/>
</div>

En el esquemático de la DDR4 se observan señales de dirección, datos, control, reloj, alimentación, referencias de voltaje y capacitores de desacoplo.

Este bloque es uno de los más delicados del proyecto, debido a que las memorias DDR requieren un diseño cuidadoso. Es necesario considerar aspectos como longitudes de pista, impedancias, separación entre señales, referencias de alimentación y ubicación de capacitores cercanos al componente.

La memoria externa permite ampliar las capacidades del sistema, especialmente en aplicaciones donde se requiere almacenamiento temporal, manejo de buffers, tablas de red o soporte para procesos internos del switch.

### Layout - DDR4

<div align="center">
  <img src="Imagenes/DDR4 layout.png" alt="DDR4 layout" width="45%"/>
</div>

En el layout se muestra la ubicación física de la memoria DDR4 y sus componentes cercanos. Esta sección representa una de las partes más complejas del diseño PCB, ya que el ruteo de memoria de alta velocidad requiere control de longitudes, buena distribución de señales y una correcta colocación de capacitores de desacoplo.

Aunque el layout del proyecto no se completó en su totalidad, la colocación de este bloque permite visualizar el nivel de complejidad que implica integrar memoria externa en una tarjeta de red de alto desempeño.

---

## 3.5 Potencia

La etapa de **potencia** se encarga de generar y distribuir los voltajes necesarios para alimentar los diferentes bloques del sistema. Esta sección incluye conversores DC-DC, reguladores, inductores, capacitores, resistencias de realimentación y conectores de alimentación.

### Esquemático - Potencia

<div align="center">
  <img src="Imagenes/potencia esquematico.png" alt="Potencia Esquematico" width="45%"/>
</div>

En el esquemático se observan diferentes circuitos de regulación de voltaje. Estos circuitos permiten obtener los niveles de alimentación necesarios para el LAN9696, memorias, PHYs, conectores y demás componentes de la tarjeta.

La correcta implementación de la etapa de potencia es fundamental, ya que una alimentación inestable puede afectar el funcionamiento del sistema completo. Por esta razón, se deben considerar capacitores de entrada y salida, filtros, estabilidad de reguladores, distribución de corriente y referencias de tierra.

### Layout - Potencia

<div align="center">
  <img src="Imagenes/potencia layout.png" alt="Potencia Layout" width="45%"/>
</div>

En el layout se observa la distribución física de los componentes de potencia. Esta parte del diseño requiere especial atención debido al manejo de corriente, anchos de pista, planos de cobre, disipación térmica y ubicación de componentes críticos.

El diseño de potencia debe procurar rutas cortas, conexiones sólidas a tierra y ubicación adecuada de los capacitores para mejorar la estabilidad y reducir ruido eléctrico.

---

# 4. Requerimientos y decisiones de diseño

Durante el desarrollo del proyecto se tomaron varias decisiones importantes para adaptar el diseño al alcance académico, al tiempo disponible y a la complejidad del sistema.

El diseño original contemplaba secciones adicionales que fueron retiradas o simplificadas debido a su nivel de complejidad. Entre estas secciones se encuentran principalmente:

- Bloque de **PCIe**.
- Bloques avanzados de **timing** y sincronización.
- Algunas secciones auxiliares del diseño original que no eran indispensables para la entrega principal.
- Parte de los circuitos que aumentaban considerablemente la complejidad del ruteo y validación del PCB.

Estas partes fueron removidas del alcance final porque implicaban un nivel de diseño más avanzado, especialmente por el manejo de señales de alta velocidad, reglas estrictas de impedancia, control de longitudes, pares diferenciales, sincronización y validaciones más complejas.

Además, estas modificaciones fueron realizadas siguiendo la indicación del ingeniero encargado del proyecto, quien recomendó concentrarse en los bloques principales del sistema para lograr un diseño más manejable, funcional y enfocado en los objetivos de la entrega.

Por esta razón, el proyecto se enfocó principalmente en los siguientes bloques:

- LAN9696 y señales principales de control.
- System Control.
- Quad PHY Ethernet.
- Conectores RJ45 MagJack.
- Interfaz SFP.
- Memoria DDR4.
- Etapa de potencia.
- Librerías, footprints y documentación del diseño.

Esta decisión permitió mantener un balance entre funcionalidad, complejidad y tiempo de desarrollo. En lugar de intentar completar todos los bloques del diseño original sin suficiente validación, se priorizó trabajar correctamente las partes más importantes y representativas del sistema.

---

# 5. Alcance del proyecto

El proyecto tuvo dos niveles principales de desarrollo: el diseño esquemático y el diseño físico de la PCB.

---

## Alcance del esquemático

El diseño esquemático se logró completar en su totalidad, alcanzando aproximadamente el **100% del desarrollo planteado** para esta etapa.

En el esquemático se incluyeron los bloques principales del sistema:

- LAN9696.
- System Control.
- Quad PHY Ethernet.
- Conectores RJ45 MagJack.
- Interfaz SFP.
- Memoria DDR4.
- Etapa de potencia.
- Señales de control.
- Señales de comunicación.
- Señales de alimentación.
- Elementos pasivos y circuitos auxiliares.

Esta parte del proyecto permitió definir la arquitectura eléctrica completa del sistema y establecer las conexiones necesarias entre los diferentes bloques funcionales.

---

## Alcance del layout PCB

En el diseño de PCB se logró avanzar aproximadamente entre un **40% y 50%** del layout total.

Este avance incluye principalmente:

- Colocación de componentes principales.
- Distribución general de bloques funcionales.
- Avance en el ruteo de algunas secciones.
- Organización parcial de señales.
- Ubicación de conectores RJ45, SFP, memorias, PHYs y componentes de potencia.
- Primeras conexiones físicas entre bloques del diseño.
- Revisión inicial de ubicación y organización de la tarjeta.

El layout no se completó al 100% debido a varios factores importantes:

- El proyecto corresponde a una tarjeta de alta complejidad.
- Es la primera vez que se realiza una PCB de este nivel.
- El sistema incluye señales de alta velocidad.
- Existen bloques complejos como DDR4, SFP, Ethernet y potencia.
- Se deben manejar pares diferenciales.
- La cantidad de componentes y conexiones es considerable.
- Hubo disponibilidad limitada de tiempo para completar todas las etapas.
- El diseño requiere experiencia avanzada en PCB multicapa.
- El tamaño del proyecto es superior al de una PCB básica o introductoria.

A pesar de no haberse completado todo el layout, el avance realizado permite demostrar el proceso de diseño, la organización por bloques y la implementación inicial de la tarjeta en Allegro PCB Editor.

---

# 6. Estructura del repositorio

La estructura del repositorio está organizada para separar los archivos fuente, documentación, imágenes y archivos exportados.

```text
Proyecto_LAN9696/
│
├── Esquemático/
│   └── Archivos del diseño esquemático en OrCAD Capture
│
├── Exportación/
│   └── Archivos exportados del proyecto
│
├── Layout_PCB/
│   └── Archivo del diseño físico de la PCB en Allegro
│
├── Librerias/
│   └── Símbolos, footprints y librerías utilizadas
│
├── Imagenes/
│   └── Capturas del esquemático, layout y diagrama de bloques
│
├── EVB LAN9696/
│   └── Archivos de referencia del proyecto

