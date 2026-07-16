# PLANTILLA DE PROMPTS
## Convertir archivos a Markdown en Mac

---

## ⚠️ SOLO PARA MAC

**Esta plantilla es exclusivamente para equipos Apple:** MacBook Air, MacBook Pro, iMac, Mac mini, Mac Studio. Intel o Apple Silicon — ambos sirven.

**Si estás en Windows o Linux, NO uses esta plantilla.** Ni la adaptes, ni le pidas al asistente que la traduzca. Vas a perder tiempo y probablemente rompas algo.

**Por qué:** las herramientas (MarkItDown y Docling) sí existen en Windows y Linux. Lo que **no** existe fuera de Mac es casi todo lo demás de esta guía:

| | Mac | Windows / Linux |
|---|---|---|
| Homebrew (el instalador) | ✅ | ❌ Otro método |
| Automator (clic derecho) | ✅ | ❌ No existe |
| Finder | ✅ | ❌ Es el Explorador |
| Rutas (`$HOME/.local/bin`) | ✅ | ❌ Distintas |
| Comandos de desinstalación | ✅ | ❌ Distintos |

Lo único que sí aplica en cualquier sistema es el **criterio de cuándo usar cada herramienta** (ver "Lo que debes saber antes de empezar") y las **7 reglas de prompting** del final.

**Esta plantilla fue validada ejecutándola paso a paso en un Mac real**, no escrita en teoría. Ahí está su valor — y ahí está el motivo de no adaptarla a ciegas a otro sistema.

Si estás en Windows, usa la plantilla complementaria: **[plantilla-windows.md](plantilla-windows.md)**, que está diseñada para descubrir los pasos contigo en lugar de asumirlos.

---

**Cómo usarla:** copia el bloque de cada prompt, rellena lo que esté entre corchetes, y envíalo. Empieza por el Prompt 0.

---

## PROMPT 0 — EL DE APERTURA

ROL
Eres desarrollador senior con experiencia en macOS y herramientas de IA. Tu prioridad es que yo no rompa nada ni me sienta perdido.

MI EQUIPO
Estoy en un Mac (MacBook o iMac). No sé el chip ni la RAM y no quiero averiguarlo. Asumo que estas herramientas no comprometen mi hardware — confírmamelo o corrígeme antes de seguir.

- ¿Tengo Homebrew instalado? [sí / no / no sé]

MI NIVEL CON LA TERMINAL
[Elige uno:]
- PRINCIPIANTE TOTAL: nunca la he abierto. No asumas nada. Dime cómo abrirla, qué es un comando, qué significa cada símbolo que aparezca en pantalla. Si tengo que descargar algo, dame la dirección exacta y cómo hacerlo.
- INTERMEDIO: he copiado comandos sin entenderlos. Explícame el porqué, no solo el qué.
- AVANZADO: dame los comandos directos, salta lo básico.

QUÉ QUIERO
Convertir mis archivos a Markdown (.md) desde mi Mac, sin depender de webs.

QUÉ TIPOS DE ARCHIVO CONVIERTO
[Marca todos los que apliquen:]
- PDF [ ]  ← si marcaste esto, es tu caso principal
- Word (DOCX) [ ]
- Excel (XLSX) [ ]
- PowerPoint [ ]
- Otros: [___]

PARA QUÉ LO NECESITO
[El motivo real — cambia la recomendación:]
- Reducir tokens antes de pasar contenido a un LLM [ ]
- Alimentar Obsidian / una base de conocimiento [ ]
- Publicar en web / GitHub [ ]
- Archivo personal [ ]
- Otro: [___]

MIS RESTRICCIONES
[Marca las que apliquen:]
- Mis archivos son confidenciales o tienen NDA → no pueden salir de mi Mac
- Necesito desinstalar todo limpio si me arrepiento
- No quiero pagar
- No quiero depender de internet
- Otra: [___]

OBJETIVO FINAL
Quiero terminar con una automatización: clic derecho sobre un archivo en Finder → se convierte a .md solo, sin abrir la Terminal.

LO QUE YA ENTIENDO DEL PANORAMA
Sé que existen dos herramientas complementarias:
- MarkItDown (Microsoft): cubre más formatos, más rápido
- Docling (IBM): más preciso en PDF, más lento y pesado
Confírmame si esto sigue vigente y si aplica a MI caso.

CÓMO QUIERO QUE ME RESPONDAS
1. Primero: confirma que estas herramientas no comprometen mi equipo, y valida el panorama de arriba. Nada de instalación todavía.
2. Después: paso a paso, UN comando por bloque.
3. En cada comando dime: qué hace, qué voy a ver en pantalla, cuánto tarda, cómo sé que terminó bien.
4. Avísame antes de cualquier paso que no se pueda deshacer.
5. Si algo NO es 100% confiable, dímelo sin adornos.
6. NO avances sin mi confirmación.
7. Si me das dos caminos posibles, dime explícitamente por cuál empezar. No me hagas elegir sin criterio.

Empieza solo con el punto 1.

---

## PROMPT 1 — ANTES DE INSTALAR

Confirmado, seguimos.
Antes del primer comando: ¿qué se va a instalar exactamente, dónde va a vivir en mi Mac, cuánto ocupa, y cómo lo borro todo si me arrepiento?
Después de eso, dame el primer paso.

---

## PROMPT 2 EN ADELANTE — EL PING-PONG

**Cuando funciona:**

Listo. [pega la última línea de la Terminal]
Siguiente paso.

**Cuando falla:**

[pega TODO el texto tal cual, sin resumir ni traducir]
¿Qué pasó? ¿Rompí algo? ¿Cómo lo arreglo?

**Cuando dudas:**

No entendí [X]. Explícamelo como si nunca hubiera visto una Terminal.
No sigas hasta que confirme.

---

## PROMPT DE CONTROL — CUANDO TE PIERDAS

Me perdí. Antes de darme más pasos:
1. ¿Dónde estoy en el proceso?
2. ¿Qué ya está hecho y funcionando?
3. ¿Qué falta?
4. Dame UN solo siguiente paso.

---

## PROMPT DE VALIDACIÓN — EL MÁS IMPORTANTE

Ya instalé las dos herramientas.
Quiero comprobar con MIS archivos cuál me sirve mejor, en vez de creerte a ciegas.
Dame los comandos para convertir el MISMO archivo con las dos.
Después te paso los dos .md y me ayudas a comparar:
- títulos detectados
- tablas reconstruidas
- basura repetida (encabezados, números de página)

> Por qué este importa más que todos: que `--help` responda no prueba nada. Comparar dos salidas reales con tu archivo sí. Es cuando dejas de confiar y empiezas a saber.

---

## PROMPT DE AUTOMATIZACIÓN

Ya funciona desde la Terminal. Ahora quiero no volver a abrirla.

Arma un atajo de clic derecho en Finder para cada herramienta.
Quiero que los .md se guarden en el Escritorio con esta estructura, creándose sola si no existe:

Escritorio/
└── Markdown/
    ├── Docling/
    └── MarkItDown/

Es decir: una carpeta contenedora, y dentro una subcarpeta por herramienta.

Considera dos cosas:
- Automator NO hereda la configuración de mi Terminal → usa rutas absolutas
- Antes de empezar, dime cómo averiguar dónde está instalada cada herramienta en MI Mac

Guía paso a paso, describiendo cada pantalla que voy a ver.

> Las dos consideraciones del final son el corazón del prompt. El PATH roto es la causa del 90% de los atajos que no hacen nada.

---

## PROMPT DE AUDITORÍA — OPCIONAL, RECOMENDADO

Toma la guía que me diste y revísala como si fueras otro desarrollador buscando errores, no confirmándola.
¿Qué omitiste? ¿Qué asumes que yo ya sé? ¿Qué es lo más probable que me falle?

> Mejor aún: pásasela a otro modelo y trae la respuesta de vuelta.

---

## PROMPT DE CIERRE

Terminamos. Dame todo en un solo .md descargable:
- Qué quedó instalado y dónde
- Cuándo usar cada herramienta (regla corta y memorizable)
- Comandos de mantenimiento
- Comandos de desinstalación completa
- Tabla de errores comunes y su solución
Que sirva sin volver a este chat.

---

# LO QUE DEBES SABER ANTES DE EMPEZAR

## El panorama, en corto

| | MarkItDown | Docling |
|---|---|---|
| Formatos | Más variedad | Buena cobertura |
| Precisión en PDF | Aceptable | Mejor |
| Velocidad | Segundos | Minutos |
| Peso | Ligero | ~1 GB de modelos |

## La regla que probablemente aplique

- **PDF → Docling**
- **Todo lo demás → MarkItDown**

**Pero verifícala tú.** En una comparación real con un libro de 120 páginas, Docling detectó 145 títulos y MarkItDown ninguno. Es una diferencia enorme — pero es *un* documento. Con PDFs simples y bien maquetados la brecha se achica. Por eso existe el Prompt de Validación.

## Lo que no cambia

Ninguna de las dos es 100% precisa. El PDF guarda coordenadas, no estructura. Todo conversor adivina. Revisa siempre el .md — sobre todo tablas y páginas con diagramas.

## Sobre tu equipo

Estas herramientas no pueden dañar tu Mac. Corren en espacio de usuario, sin acceso privilegiado. En el peor caso van lentas. Cualquier Mac de los últimos ~10 años las corre sin problema.

---

# ANEXO — Scripts de Automator ya probados

Si el asistente se enreda con la automatización, estos son los scripts finales que funcionan. Van dentro de una acción **"Ejecutar shell script"** en Automator, configurada así:

| Campo | Valor |
|---|---|
| El flujo de trabajo recibe | archivos o carpetas |
| en | Finder |
| Shell | `/bin/zsh` |
| Pasar entrada | **como argumentos** |

> El "como argumentos" es obligatorio. Viene en "a stdin" por defecto y así no funciona.

## Script para Docling

```
DEST="$HOME/Desktop/Markdown/Docling"
mkdir -p "$DEST"

for f in "$@"
do
    cd "$DEST"
    $HOME/.local/bin/docling "$f" --to md --output "$DEST"
done

open "$DEST"
```

## Script para MarkItDown

```
DEST="$HOME/Desktop/Markdown/MarkItDown"
mkdir -p "$DEST"

for f in "$@"
do
    NOMBRE=$(basename "$f")
    SALIDA="$DEST/${NOMBRE%.*}.md"
    $HOME/.local/bin/markitdown "$f" -o "$SALIDA"
done

open "$DEST"
```

## Antes de usarlos: verifica tu ruta

En Terminal:

```
which docling
which markitdown
```

Si no devuelven algo terminado en `.local/bin/`, ajusta la ruta en los scripts.

## Qué hace cada línea

| Línea | Qué hace |
|---|---|
| `DEST="$HOME/Desktop/..."` | Define la carpeta destino |
| `mkdir -p "$DEST"` | Crea la carpeta **y su carpeta padre** si no existen. Si ya existen, no hace nada ni da error |
| `basename "$f"` | Saca solo el nombre del archivo, sin la ruta |
| `${NOMBRE%.*}.md` | Cambia la extensión: `informe.pdf` → `informe.md` |
| `open "$DEST"` | Abre la carpeta en Finder al terminar — así sabes que acabó |

---

# LAS 7 REGLAS DETRÁS DE LA PLANTILLA

1. **La densidad va al frente.** Prompt 0 largo, después mensajes de dos líneas.
2. **Di el "para qué", no solo el "qué".** Cambia la herramienta recomendada.
3. **Declara tu nivel sin maquillar.** "Sé algo" produce guías que fallan.
4. **Nombra las restricciones invisibles.** El NDA, el presupuesto, la manía por el orden.
5. **Pega la salida cruda.** "No funcionó" no es información.
6. **Exige un solo camino.** La ambigüedad es la falla más común del asistente, no la alucinación.
7. **Verifica con tus archivos.** No con los ejemplos del asistente.
