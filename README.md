# Proyecto LAN9696 - Switch L3 de Fibra Óptica y Ethernet

Este repositorio contiene el desarrollo del diseño electrónico de un **switch de capa 3** basado en el componente **LAN9696**, orientado a aplicaciones de comunicación de red de alto rendimiento.  
El proyecto incluye el diseño esquemático, el layout PCB y los archivos auxiliares necesarios para documentar, revisar y modificar la tarjeta dentro del entorno de diseño de Cadence.

El sistema está planteado como una solución de conmutación de red con múltiples interfaces Ethernet, conectividad por fibra óptica y memoria externa, integrando los bloques principales necesarios para el funcionamiento de un switch administrable de alto desempeño.

## Descripción general del proyecto

El diseño corresponde a una tarjeta electrónica basada en el **LAN9696**, un dispositivo orientado a aplicaciones de networking y switching.  
La tarjeta fue diseñada considerando la integración de interfaces de red cableadas, comunicación de alta velocidad, memoria externa y los circuitos de soporte necesarios para alimentación, configuración y operación del sistema.

Entre las características principales del diseño se incluyen:

- Switch de red de **capa 3 (L3)**.
- **24 puertos RJ45** para conectividad Ethernet.
- **1 puerto de fibra óptica** para enlace de alta velocidad.
- Memoria externa **DDR3 RAM**.
- Diseño esquemático desarrollado en **OrCAD Capture**.
- Layout PCB desarrollado en **Allegro PCB Editor**.
- Organización de librerías, símbolos y footprints personalizados.
- Exportación del esquemático en formato PDF para revisión.

## Objetivo del repositorio

El objetivo de este repositorio es organizar y documentar los archivos principales del proyecto LAN9696, permitiendo que el diseño pueda ser revisado, compartido y respaldado de manera ordenada.

Este repositorio sirve como entrega técnica del proyecto, incluyendo los archivos fuente necesarios para abrir el diseño en Cadence, así como archivos exportados para facilitar la revisión sin necesidad de modificar directamente el proyecto.

## Contenido del repositorio

```text
Proyecto_LAN9696/
│
├── Esquemático/
├── Exportación/
├── Layout_PCB/
├── Librerias/
└── README.md
