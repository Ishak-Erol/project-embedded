![[Pasted image 20250823093819.png]]
## Ausgangslage
- Projekt: `SPI_Loopback`
- Workspace: ursprünglich `Projekte`
- IntelliSense zeigte Fehler:
  - `SPI_HandleTypeDef is undefined`
  - `__IO is undefined`
- Grund: Include-Pfade stimmten nicht mit Workspace überein, falsches HAL-Makro, alte IntelliSense-Datenbank

## Probleme
1. Workspace vs. Include-Pfade
2. Falsches HAL-Makro (`STM32F100RB` statt `STM32F100xB`)
3. IntelliSense-Cache veraltet

## Lösung
1. **JSON-Datei erstellt:** `.vscode/c_cpp_properties.json`
```json
{
    "configurations": [
        {
            "name": "STM32",
            "includePath": [
                "${workspaceFolder}/Core/Inc",
                "${workspaceFolder}/Drivers/STM32F1xx_HAL_Driver/Inc",
                "${workspaceFolder}/Drivers/CMSIS/Device/ST/STM32F1xx/Include",
                "${workspaceFolder}/Drivers/CMSIS/Include"
            ],
            "defines": ["STM32F100xB", "USE_HAL_DRIVER"],
            "compilerPath": "/usr/bin/arm-none-eabi-gcc",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "gcc-arm"
        }
    ],
    "version": 4
}

    Workspace auf SPI_Loopback gesetzt