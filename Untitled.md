
**Syscalls** (System Calls) sind Schnittstellen zwischen dem C-Programm und dem Betriebssystem. Da STM32-Anwendungen meist **ohne Betriebssystem laufen, müssen grundlegende Funktionen wie `printf()`  über sogenannte Syscalls z. B. an UART oder SWO angebunden werden.


Syscalls müssen selbst implementiert werden, z. B.:

| Syscall | Zweck |
|--------|-------|
| `_write()` | Für `printf()`-Ausgabe |
| `_read()` | Für `scanf()` oder Eingaben |
| `_sbrk()` | Für Speicherverwaltung (`malloc`) |
| `_close()`, `_fstat()`, `_lseek()` | Für Dateisystem (meist leer) |

### Beispiel: UART-Ausgabe über `_write()`:

```c
int _write(int file, char *ptr, int len) {
    HAL_UART_Transmit(&huart2, (uint8_t*)ptr, len, HAL_MAX_DELAY);
    return len;
}
 ```
 oder
 Beispiel: ITM-Ausgabe über `_write()`:
 ```c
 void ITM_SendChar(uint8_t ch)
{
	DEMCR |= ( 1 << 24);
	ITM_TRACE_EN |= ( 1 << 0);
	while(!(ITM_STIMULUS_PORT0 & 1));
	ITM_STIMULUS_PORT0 = ch;
}

int _write(int file, char *ptr, int len)
{
	(void)file;
	int DataIdx; 
	for (DataIdx = 0; DataIdx < len; DataIdx++)
	{
		ITM_SendChar(*ptr++);
	}
	return len;
}
```

!!! ITM ist teil des ARM-Coretex-M, daher keien externe Initialisierung nötig