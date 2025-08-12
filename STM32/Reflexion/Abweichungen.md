#### Wechsel von ST-Link Tools zu OpenOCD
- **Grund:** Mein STM32-Board besitzt einen **alten ST-LINK-Hardwareadapter (V1)**
- **Problem:** Der offizielle **ST-Link GDB Server** unterstützt **nur ST-LINK V2 und neuer**
- **Lösung:** Einsatz von **OpenOCD** als GDB-Server
---
#### Umstieg von SPL zu HAL + STM32CubeMX

Ab dem 14.06.2025 Umstieg von der **Standard Peripheral Library (SPL)** auf **HAL** + **STM32CubeMX**.
- **HAL** – C-Bibliothek von ST mit höherer Hardwareabstraktion.
- **STM32CubeMX** – Grafisches Tool zur automatischen Code-Generierung (HAL/LL).
- **SPL** – wird nicht mehr verwendet.

**Grund:** Schnellerer Entwicklungsstart ohne tief in Register-Details einzusteigen – Fokus auf Logik & Funktionalität statt manueller Hardware-Initialisierung.