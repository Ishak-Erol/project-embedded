#### Header Dateien 
Header-Dateien (mit der Endung `.h`) sind reine Textdateien, die Deklarationen enthalten. Sie enthalten keinen ausführbaren Code, sondern dienen dazu, dem Compiler Informationen über Funktionen und Datenstrukturen bereitzustellen, die an anderer Stelle (meist in einer `.c`-Datei) definiert sind. Durch das Einbinden einer Header-Datei mit `#include` kann eine Quellcodedatei diese Deklarationen verwenden.
#Header_Datei

#### Rolle des Compilers:
`#include "gpio.h"`
`int main(void) {`
    `init_gpio();         // Funktion aus einer anderen Datei`
    `return 0;`
`}`

- **Er ersetzt `#include "gpio.h"`** durch den Inhalt der Datei `gpio.h`.
- Er **überprüft, ob `init_gpio()` gültig deklariert** ist.
- Er kompiliert `main.c` zu `main.o`, ohne zu wissen, **wo `init_gpio()` definiert ist** – das macht später der **Linker**.

### Volatile
#volatile in C actually came into existence for the purpose of not caching the values of the variable automatically. It will tell the compiler not to cache the value of this variable. So it will generate code to take the value of the given volatile variable from the main memory every time it encounters it. This mechanism is used because at any time the value can be modified by the OS or any interrupt. So using volatile will help us accessing the value afresh every time.
[Stackoverflow](https://stackoverflow.com/questions/246127/why-is-volatile-needed-in-c)