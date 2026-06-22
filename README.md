# EDUPI4.0

**PLC educativo, modular y de bajo coste basado en Raspberry Pi Zero 2 W.**

EDUPI4.0 acerca la automatización industrial a aulas, talleres y laboratorios mediante una plataforma abierta que combina entradas de 24 V, salidas por relé, conectividad y una carcasa imprimible en 3D. El repositorio reúne el diseño electrónico, la lista de materiales, el conjunto mecánico y evidencias de su evaluación en el aula.

![Arquitectura de EDUPI4.0](Transferencia/Imágenes/Arquitectura%20%282%29.png)

## Características principales

| Bloque | Especificación |
| --- | --- |
| Unidad de procesamiento | Raspberry Pi Zero 2 W |
| Alimentación de entrada | 18–36 VDC |
| Entradas digitales | 8 entradas optoacopladas para señales de 24 VDC |
| Salidas digitales | 4 relés con contactos NC, COM y NO |
| Capacidad indicada de los relés | Hasta 10 A; 240 VAC o 28 VDC, según el diseño |
| Expansión | 16 señales GPIO/SPI/UART/I²C/PWM y líneas de 12 V, 5 V, 3,3 V y GND |
| Interfaces de la Raspberry Pi | Wi-Fi, GPIO, PWM, UART, SPI e I²C |
| Programación prevista | CODESYS, compatible con lenguajes IEC 61131-3 |
| Coste electrónico estimado | 27,63 € por unidad según la BOM incluida |

La alimentación se convierte internamente de 18–36 VDC a 12 VDC, 5 VDC y 3,3 VDC para los distintos bloques del sistema. Las entradas y el control de los relés incorporan aislamiento mediante optoacopladores.

> [!IMPORTANT]
> Este es un equipo educativo y no un PLC industrial certificado. Trabajar con 230/240 VAC implica riesgo de descarga, incendio y daños materiales. El montaje y las pruebas a tensión de red deben realizarlos personas cualificadas, con protecciones, envolvente y procedimientos adecuados. Verifica siempre el componente montado y sus límites reales antes de conectar una carga.

## Contenido del repositorio

```text
EDUPI4.0/
├── Hardware/
│   └── PLC_Raspberry_Microdesys_FA/   # Proyecto, esquemas, PCB y librerías Altium
├── BOM/
│   └── PLC_Raspberry_EDUPI4.0_FA.xlsx # Lista de materiales y precios de referencia
├── Archivos 3D/
│   └── CARCASA_PLC_EDUPI4.0/          # Inventor, STEP, 3MF y STL de la carcasa
├── Transferencia/
│   └── Imágenes/                       # Diagramas y fotografías para divulgación
├── Evaluación en aula/
│   ├── Formulario alumnos/             # Encuesta, respuestas anonimizadas y PDF
│   └── Imágenes montajes/               # Evidencias de prácticas y montajes
├── LICENSE
└── README.md
```

### Diseño electrónico

El proyecto principal se abre desde [`PLC_Raspberry_Microdesys_FA.PrjPcb`](Hardware/PLC_Raspberry_Microdesys_FA/PLC_Raspberry_Microdesys_FA.PrjPcb) con **Altium Designer**. Incluye:

- esquemáticos jerárquicos y documento de arquitectura;
- PCB actual `PCB_Raspberry_V5.PcbDoc` y revisiones anteriores;
- librerías locales de símbolos y encapsulados;
- configuraciones CAM para Gerber y taladrado NC.

Los archivos Gerber de fabricación no están exportados en el repositorio. Deben generarse desde las configuraciones CAM y revisarse antes de encargar la placa.

### Carcasa

Los archivos fuente mecánicos son de **Autodesk Inventor** (`.ipt` y `.iam`). Para imprimir sin modificar el diseño, utiliza los modelos vigentes de [`Impresión 3D`](Archivos%203D/CARCASA_PLC_EDUPI4.0/Impresión%203D/):

- `INFERIOR.stl`;
- `SUPERIOR v4.stl`;
- `CARCASA_PLC_V6_Tapa v4.stl`;
- `CUBRE EXP v4.stl`;
- `CLIP.stl`.

La subcarpeta `Antiguo` y la carpeta `OldVersions` contienen iteraciones previas y no son la opción recomendada para un montaje nuevo.

### Lista de materiales

La [BOM](BOM/PLC_Raspberry_EDUPI4.0_FA.xlsx) contiene 33 partidas de componentes y una estimación total de **27,63 €**, incluyendo Raspberry Pi Zero 2 W y PCB. Los precios son orientativos: no incluyen necesariamente impuestos, transporte, montaje, carcasa ni herramientas, y pueden variar con el proveedor y el volumen de compra.

### Evaluación educativa

`Evaluación en aula` conserva el formulario empleado con el alumnado, sus respuestas anonimizadas y fotografías de los montajes. Los materiales cubren comprensión y aprendizaje, experiencia práctica, motivación, usabilidad, realismo industrial, valor y accesibilidad.

## Cómo reproducir el proyecto

1. Revisa la arquitectura, los esquemas y las especificaciones de cada componente.
2. Abre el proyecto de Altium y ejecuta las comprobaciones ERC y DRC.
3. Genera y valida Gerbers, archivos de taladrado y documentación de montaje.
4. Actualiza precios, referencias y disponibilidad en la BOM antes de comprar.
5. Fabrica y ensambla la PCB siguiendo prácticas adecuadas de ESD y seguridad eléctrica.
6. Imprime las piezas STL actuales y comprueba ajustes, ventilación y aislamiento.
7. Instala el sistema operativo y el entorno de ejecución elegido en la Raspberry Pi.
8. Configura CODESYS y asigna los GPIO de acuerdo con el esquemático del hardware.
9. Prueba primero con baja tensión y cargas seguras antes de utilizar los contactos de los relés con tensiones peligrosas.

> [!NOTE]
> Este repositorio no incluye actualmente una imagen del sistema, un proyecto CODESYS, ejemplos de aplicación ni un mapa de variables listo para desplegar. La configuración de software debe prepararse y validarse para cada instalación.

## Estado del proyecto

El repositorio contiene fuentes de diseño y material de validación educativa. Antes de fabricar o utilizar una unidad, conviene revisar al menos:

- coherencia entre esquemático, PCB, BOM y componente realmente adquirido;
- reglas eléctricas y de diseño de la revisión V5;
- separación, aislamiento y protecciones para cargas de red;
- pinout y lógica activa de entradas y salidas;
- compatibilidad de versiones entre Raspberry Pi OS y CODESYS.

## Contribuciones

Las incidencias y propuestas son bienvenidas. Para cambios de hardware, indica la revisión afectada y adjunta, cuando corresponda, esquemas, DRC/ERC, Gerbers actualizados y fotografías o resultados de prueba. Evita incluir datos personales en nuevas evidencias de aula.

## Licencia

El contenido se publica bajo la [licencia MIT](LICENSE). Comprueba por separado las licencias y condiciones de uso de modelos CAD, librerías, componentes de terceros y software externo.

## Cita

Si utilizas este trabajo en docencia o investigación, puedes citarlo provisionalmente como:

> *EDUPI4.0: PLC educativo de bajo coste para automatización industrial e Industria 4.0*, 2026.

Sustituye esta referencia por la publicación académica definitiva cuando esté disponible.
