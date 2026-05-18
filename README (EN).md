# LAN9696 Project - L3 Ethernet and Fiber Optic Switch

This repository contains the development of an electronic design project based on the **LAN9696** device, focused on the implementation of a **Layer 3 (L3) switch** with Ethernet interfaces, fiber optic connectivity, external DDR4 memory, and the required power circuits for its operation.

The project was developed using **Cadence** tools, specifically **OrCAD Capture** for the schematic design and **Allegro PCB Editor** for the physical PCB layout. The main purpose of this repository is to document the design progress in an organized way, including the schematic, PCB layout, libraries, exported files, and representative images of the most important blocks of the system.

---

## Table of Contents

1. [Project Explanation](#1-project-explanation)
2. [Block Diagram](#2-block-diagram)
3. [Important Project Blocks](#3-important-project-blocks)
   - [System Control](#31-system-control)
   - [Quad PHY with PoE MagJack](#32-quad-phy-with-poe-magjack)
   - [SFP](#33-sfp)
   - [DDR4](#34-ddr4)
   - [Power Stage](#35-power-stage)
4. [Requirements and Design Decisions](#4-requirements-and-design-decisions)
5. [Project Scope](#5-project-scope)
6. [Repository Structure](#6-repository-structure)

---

# 1. Project Explanation

This project consists of the electronic design of an **L3 fiber optic and Ethernet switch**, based on the main component **LAN9696**. The objective of the design is to represent a high-performance network board capable of integrating multiple wired communication interfaces, optical connectivity, external memory, and support circuits for power, control, and configuration.

A Layer 3 switch combines network switching functions with routing capabilities, which means this type of system can be used in applications where traffic must be managed between different devices, networks, or network segments. In this project, the LAN9696 acts as the central block responsible for managing and processing the system interfaces.

The design includes an architecture composed of several functional blocks:

- Central processing and switching block based on the **LAN9696**.
- Ethernet interfaces through external **PHYs**.
- **RJ45 MagJack** connectors for physical network connection.
- **SFP** interface for fiber optic connectivity.
- External **DDR4** memory.
- Power circuits using DC-DC converters and regulators.
- Control, reset, communication, synchronization, and configuration signals.
- Complete schematic design and partial PCB layout progress.

The original system proposal is focused on a switch with multiple network ports, including **24 RJ45 ports** and at least **1 fiber optic interface**, as well as external memory for system support. Due to the complexity of the design, the work focused mainly on the most representative and necessary blocks to demonstrate the general architecture of the project.

The project was developed as an advanced electronic design practice, using professional tools for schematic creation and PCB layout design. In addition, this repository documents the development process, organizes the source files, and visually presents the most important blocks of the design.

---

# 2. Block Diagram

The following diagram shows the general architecture of the proposed system. It represents the main functional blocks of the switch, including power, system control, memory, Ethernet interfaces, fiber optic modules, and synchronization signals.

<div align="center">
  <img src="Imagenes/Diagrama de Bloques Switch L3.jpeg" alt="Block diagram" width="45%"/>
</div>

The system is organized around the central processing block, where the main device responsible for managing the network interfaces is located. From this block, the different sections of the design are connected, such as system memories, Ethernet PHYs, RJ45 connectors, SFP modules, and auxiliary circuits.

## Block Diagram Explanation

The diagram is divided into the following main sections:

### Power

The power section is responsible for receiving the main system supply and converting it into the different voltage levels required by each block. In this project, DC-DC converters and LDO regulators are considered to generate voltages such as 5V, 3.3V, and other levels required for the LAN9696, memories, PHYs, and external modules.

### Switch / Central Processing

This block represents the core of the system. It contains the device responsible for processing, managing, and switching network traffic. Ethernet interfaces, memories, control signals, synchronization signals, and other required peripherals are connected from this block.

### Management and I/O

This section includes system control and management elements, such as USB/UART console, GPIOs, status indicators, and reset signals. These elements allow the system to be configured, monitored, and debugged during operation or laboratory testing.

### Ethernet Interfaces

This block represents the connection between the central system and the RJ45 ports. The Ethernet PHYs are responsible for adapting the signals from the main processor into the electrical signals used by Ethernet cables. These signals are then connected to the RJ45 MagJack connectors.

### Fiber Interfaces

The fiber optic section uses SFP or SFP+ modules to allow optical links. These links are useful for longer-distance connections, trunk links, or uplinks to other network devices.

### System Memories

The system includes external DDR4 memory, as well as other possible support memories such as Flash or eMMC. These memories allow configuration information, firmware, tables, buffers, or other data used during switch operation to be stored.

### Clocks and Synchronization

This section includes clock, synchronization, and timing signals. These blocks are important in communication systems because they provide stable timing references for the correct operation of high-speed interfaces.

---

# 3. Important Project Blocks

The following sections present the most important blocks of the project. Each block includes a schematic image, a layout image when applicable, and a brief explanation of its function within the system.

---

## 3.1 System Control

The **System Control** block is one of the main sections of the design, since it groups configuration, control, communication, and support signals associated with the LAN9696.

### Schematic - System Control

<div align="center">
  <img src="Imagenes/LAN9696 System Control esquematico.png" alt="System control schematic" width="45%"/>
</div>

This schematic section shows connections related to the general control of the system. These signals include configuration interfaces, GPIO lines, JTAG signals, reset, auxiliary communication, and connections required for the operation of the main device.

This block is important because it allows system initialization, debugging, and management. It also provides access to key signals during testing, diagnosis, or hardware configuration.

### Layout - System Control

<div align="center">
  <img src="Imagenes/LAN9696 System Control layout.png" alt="System control layout" width="45%"/>
</div>

The layout shows the physical placement of components associated with the control block. Connectors, resistors, capacitors, and auxiliary components related to control and communication signals can be observed.

The placement of these elements aims to keep an organized PCB distribution and provide easier access to important signals for testing or debugging.

---

## 3.2 Quad PHY with PoE MagJack

The **Quad PHY Ethernet** block allows the main system to connect with the physical Ethernet ports. PHYs are circuits responsible for converting and adapting the digital signals from the central system into the electrical signals used by Ethernet.

### Schematic - Quad PHY

<div align="center">
  <img src="Imagenes/Quad PHY esquematico.png" alt="Quad PHY schematic" width="45%"/>
</div>

The Quad PHY schematic shows differential signals, power connections, decoupling capacitors, configuration resistors, and communication signals with the LAN9696.

This block is essential because it works as an intermediary between the switch main processor and the RJ45 connectors. Without the Ethernet PHYs, the system would not be able to communicate directly with external devices through network cables.

### Layout - Quad PHY

<div align="center">
  <img src="Imagenes/Quad PHY layout.png" alt="Quad PHY layout" width="45%"/>
</div>

The layout shows the physical distribution of the PHYs and their proximity to the RJ45 connectors. This section requires special care due to the use of high-speed signals and differential pairs.

The routing of this block is one of the most complex parts of the project, since Ethernet signals must follow good design practices such as impedance control, proper pair spacing, appropriate trace lengths, and interference reduction.

### Schematic - PoE MagJack

<div align="center">
  <img src="Imagenes/POE Magjack.png" alt="RJ45" width="45%"/>
</div>

The **RJ45 MagJack** connectors represent the physical interface between the switch and the Ethernet cables. These connectors integrate the RJ45 port together with the magnetic elements required for coupling and electrical isolation of the Ethernet signal.

This part of the schematic shows differential pair connections, status LED signals, and auxiliary lines. The LEDs allow link or activity status to be indicated, while the main signals allow communication between the external device and the Ethernet PHY.

Using MagJack connectors simplifies the design implementation because they integrate the physical connector and the magnetic components required for Ethernet into a single component.

---

## 3.3 SFP

The **SFP** block corresponds to the fiber optic interface of the system. This section allows an optical transceiver module to be connected in order to establish longer-distance or high-speed links.

### Schematic - SFP

<div align="center">
  <img src="Imagenes/SFP esquematico.png" alt="SFP schematic" width="45%"/>
</div>

The SFP schematic shows differential transmit and receive signals, module power, control lines, detection signals, and passive components required for its operation.

This interface allows the switch to avoid depending only on RJ45 ports, since it can also connect through fiber optics. This is useful in networks where longer transmission distance, reduced electromagnetic interference, or trunk links between network devices are required.

### Layout - SFP

<div align="center">
  <img src="Imagenes/SFP layout.png" alt="SFP layout" width="45%"/>
</div>

The layout shows the physical location of the SFP connector and its associated routing. Normally, this type of connector must be placed close to the edge of the PCB to allow the transceiver module to be inserted from outside the device.

The design of this section requires care due to the use of high-speed differential signals, as well as proper mechanical placement so the module can be connected correctly.

---

## 3.4 DDR4

The **DDR4** memory is part of the system support blocks. Its main function is to provide high-speed temporary storage for switch processing and operation.

### Schematic - DDR4

<div align="center">
  <img src="Imagenes/DDR4 esquematico.png" alt="DDR4 schematic" width="45%"/>
</div>

The DDR4 schematic shows address, data, control, clock, power, voltage reference, and decoupling capacitor signals.

This is one of the most delicate blocks of the project because DDR memories require careful design. It is necessary to consider aspects such as trace lengths, impedances, signal spacing, power references, and the placement of capacitors close to the component.

External memory allows the system capabilities to be expanded, especially in applications where temporary storage, buffer management, network tables, or support for internal switch processes are required.

### Layout - DDR4

<div align="center">
  <img src="Imagenes/DDR4 layout.png" alt="DDR4 layout" width="45%"/>
</div>

The layout shows the physical placement of the DDR4 memory and its nearby components. This section represents one of the most complex parts of the PCB design, since high-speed memory routing requires length control, good signal distribution, and proper placement of decoupling capacitors.

Although the project layout was not fully completed, the placement of this block helps visualize the level of complexity involved in integrating external memory into a high-performance network board.

---

## 3.5 Power Stage

The **power stage** is responsible for generating and distributing the voltages required to supply the different blocks of the system. This section includes DC-DC converters, regulators, inductors, capacitors, feedback resistors, and power connectors.

### Schematic - Power Stage

<div align="center">
  <img src="Imagenes/potencia esquematico.png" alt="Power schematic" width="45%"/>
</div>

The schematic shows different voltage regulation circuits. These circuits generate the required supply levels for the LAN9696, memories, PHYs, connectors, and other components of the board.

Proper implementation of the power stage is essential, since unstable power can affect the operation of the entire system. For this reason, input and output capacitors, filters, regulator stability, current distribution, and ground references must be considered.

### Layout - Power Stage

<div align="center">
  <img src="Imagenes/potencia layout.png" alt="Power layout" width="45%"/>
</div>

The layout shows the physical distribution of the power components. This part of the design requires special attention due to current handling, trace widths, copper planes, thermal dissipation, and placement of critical components.

The power design should use short paths, solid ground connections, and proper capacitor placement to improve stability and reduce electrical noise.

---

# 4. Requirements and Design Decisions

During the development of the project, several important decisions were made to adapt the design to the academic scope, available time, and system complexity.

The original design included additional sections that were removed or simplified due to their level of complexity. These sections mainly include:

- **PCIe** block.
- Advanced **timing** and synchronization blocks.
- Some auxiliary sections of the original design that were not essential for the main deliverable.
- Some circuits that considerably increased the complexity of PCB routing and validation.

These parts were removed from the final scope because they required a more advanced design level, especially due to high-speed signal handling, strict impedance rules, length matching, differential pairs, synchronization, and more complex validation processes.

In addition, these modifications were made following the instruction of the engineer in charge of the project, who recommended focusing on the main system blocks in order to achieve a more manageable, functional design aligned with the objectives of the deliverable.

For this reason, the project focused mainly on the following blocks:

- LAN9696 and main control signals.
- System Control.
- Quad PHY Ethernet.
- RJ45 MagJack connectors.
- SFP interface.
- DDR4 memory.
- Power stage.
- Libraries, footprints, and design documentation.

This decision allowed a balance between functionality, complexity, and development time. Instead of attempting to complete all the blocks of the original design without enough validation, the priority was to work properly on the most important and representative parts of the system.

---

# 5. Project Scope

The project had two main levels of development: the schematic design and the physical PCB design.

---

## Schematic Scope

The schematic design was fully completed, reaching approximately **100% of the planned development** for this stage.

The schematic includes the main blocks of the system:

- LAN9696.
- System Control.
- Quad PHY Ethernet.
- RJ45 MagJack connectors.
- SFP interface.
- DDR4 memory.
- Power stage.
- Control signals.
- Communication signals.
- Power signals.
- Passive components and auxiliary circuits.

This part of the project made it possible to define the complete electrical architecture of the system and establish the required connections between the different functional blocks.

---

## PCB Layout Scope

In the PCB design stage, approximately **40% to 50%** of the total layout was completed.

This progress mainly includes:

- Placement of main components.
- General distribution of functional blocks.
- Progress in routing some sections.
- Partial organization of signals.
- Placement of RJ45 connectors, SFP, memories, PHYs, and power components.
- Initial physical connections between design blocks.
- Initial review of board placement and organization.

The layout was not completed 100% due to several important factors:

- The project corresponds to a highly complex board.
- This was the first time designing a PCB of this level.
- The system includes high-speed signals.
- There are complex blocks such as DDR4, SFP, Ethernet, and power.
- Differential pairs must be handled.
- The number of components and connections is considerable.
- There was limited time available to complete all stages.
- The design requires advanced experience in multilayer PCB design.
- The size of the project is greater than that of a basic or introductory PCB.

Although the full layout was not completed, the progress made demonstrates the design process, block organization, and initial implementation of the board in Allegro PCB Editor.

---

# 6. Repository Structure

The repository structure is organized to separate source files, documentation, images, and exported files.

```text
Proyecto_LAN9696/
│
├── Esquemático/
│   └── Schematic design files in OrCAD Capture
│
├── Exportación/
│   └── Exported project files
│
├── Layout_PCB/
│   └── Physical PCB design file in Allegro
│
├── Librerias/
│   └── Symbols, footprints, and libraries used
│
├── Imagenes/
│   └── Schematic, layout, and block diagram screenshots
│
├── EVB LAN9696/
│   └── Project reference files
```
