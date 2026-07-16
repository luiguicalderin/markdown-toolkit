# PLANTILLA DE PROMPTS
## Convertir archivos a Markdown en Windows

---

## ⚠️ LEE ESTO PRIMERO — ES DISTINTA A LA DE MAC

Existe una plantilla hermana para Mac: **[plantilla-mac.md](plantilla-mac.md)**. **Esa está probada.** Alguien la ejecutó paso a paso en un Mac real, encontró los errores, y los corrigió.

**Esta no.**

MarkItDown y Docling **sí funcionan en Windows** — eso está confirmado en la documentación oficial de ambos proyectos. Lo que no está confirmado es *cómo se comportan en TU Windows*: qué versión tienes, si Python está instalado, si tu antivirus se mete, si tu cuenta tiene permisos de administrador, si el clic derecho se puede personalizar en tu equipo.

**Por eso esta plantilla no te da comandos. Te da preguntas.**

Está diseñada para que tú y el asistente **descubran juntos** los pasos correctos para tu máquina, en vez de que él te dicte una guía teórica que falla en el paso 3.

Es más lenta. Y es la única forma honesta de hacerlo bien.

---

## Lo que sí sabemos de entrada

| | Confirmado |
|---|---|
| Docling funciona en Windows | ✅ Documentación oficial |
| MarkItDown funciona en Windows | ✅ Es una librería de Python, multiplataforma |
| Homebrew existe en Windows | ❌ **No.** Es exclusivo de Mac y Linux |
| Automator existe en Windows | ❌ **No.** Es exclusivo de Mac |
| Windows tiene un menú "Enviar a" personalizable | ✅ Pero en Windows 11 está escondido bajo "Mostrar más opciones" |

**Lo que cambia respecto a Mac:** el instalador, la terminal, las rutas, y la automatización. O sea: casi todo.

**Lo que NO cambia:** el criterio de cuándo usar cada herramienta, y las reglas de cómo hablarle al asistente.

---

## PROMPT 0 — EL DE APERTURA

ROL
Eres desarrollador senior con experiencia en Windows y herramientas de IA. Tu prioridad es que yo no rompa nada ni me sienta perdido.

⚠️ IMPORTANTE SOBRE ESTA CONVERSACIÓN
No quiero que me des una guía teórica. Quiero que descubramos juntos los pasos correctos para MI equipo.

Eso significa:
- Verifica en la web antes de afirmar cualquier cosa. No te inventes comandos.
- Si no estás seguro de algo, dímelo. Prefiero "no lo sé, verifiquemos" antes que un comando que falle.
- Antes de darme un paso, pregúntame lo que necesites saber de mi equipo.
- Si un comando puede comportarse distinto según mi versión de Windows, dímelo y pídeme que lo verifique.

MI EQUIPO
Estoy en un PC con Windows. No sé la versión exacta ni las especificaciones, y no quiero averiguarlas por mi cuenta.

Si necesitas saber algo de mi equipo (versión de Windows, si tengo Python, si soy administrador, etc.), dime CÓMO averiguarlo paso a paso y yo te lo reporto.

Antes de nada, confírmame: ¿estas herramientas pueden dañar mi PC de alguna forma?

MI NIVEL CON LA TERMINAL
Nulo. Nunca he abierto una terminal en mi vida. Apenas sé usar mi computador para lo básico.

Eso significa:
- No asumas NADA
- Dime cómo abrir cada programa, paso a paso
- Explícame qué es cada cosa antes de pedirme que la use
- Si tengo que descargar algo, dame la dirección exacta y cómo hacerlo
- Si aparece una ventana o un mensaje, descríbeme qué voy a ver
- Un comando por vez. Nunca varios juntos.

QUÉ QUIERO
Convertir mis archivos a Markdown (.md) desde mi PC, sin depender de webs.

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
- Mis archivos son confidenciales o tienen NDA → no pueden salir de mi PC
- Necesito desinstalar todo limpio si me arrepiento
- No quiero pagar
- No quiero depender de internet
- Otra: [___]

OBJETIVO FINAL
Quiero terminar con una automatización: clic derecho sobre un archivo → se convierte a .md solo, sin abrir la terminal.

Si eso no es posible en Windows, o es muy riesgoso, dímelo desde ahora y propón la alternativa más simple.

LO QUE YA ENTIENDO DEL PANORAMA
Sé que existen dos herramientas complementarias:
- MarkItDown (Microsoft): cubre más formatos, más rápido
- Docling (IBM): más preciso en PDF, más lento y pesado

Sé que ambas funcionan en Windows, pero que la instalación es distinta a la de Mac (allá se usa Homebrew, que en Windows no existe).

Verifica esto en la web y confírmame si sigue vigente.

CÓMO QUIERO QUE ME RESPONDAS
1. Primero: confirma que esto no daña mi PC, verifica el panorama de arriba en la web, y dime qué necesitas saber de mi equipo. Nada de instalación todavía.
2. Después: paso a paso, UN comando por bloque.
3. En cada comando dime: qué hace, qué voy a ver en pantalla, cuánto tarda, cómo sé que terminó bien.
4. Avísame antes de cualquier paso que no se pueda deshacer.
5. Si algo NO es 100% confiable, dímelo sin adornos.
6. NO avances sin mi confirmación.
7. Si me das dos caminos posibles, dime explícitamente por cuál empezar. No me hagas elegir sin criterio.

Empieza solo con el punto 1.

---

## PROMPT 1 — RECONOCIMIENTO DEL EQUIPO

Dime paso a paso cómo averiguar lo que necesitas saber de mi PC.

Para cada dato:
- Dime dónde hacer clic o qué escribir
- Dime qué voy a ver en pantalla
- Dime para qué te sirve ese dato (no quiero darte información porque sí)

Yo te reporto los resultados y seguimos.

> **Por qué importa:** en Mac, el asistente pidió el modelo del chip "por costumbre" y no servía para nada. En Windows sí hay datos que cambian el camino: la versión, si tienes Python, si eres administrador. Que te explique el porqué de cada pregunta.

---

## PROMPT 2 — ANTES DE INSTALAR

Antes del primer comando, quiero saber:

1. ¿Cuál es la forma MÁS SEGURA de instalar estas herramientas en mi Windows? Verifícalo en la web, no me lo digas de memoria.
2. ¿Qué se va a instalar exactamente, dónde va a vivir en mi PC, y cuánto ocupa?
3. ¿Cómo lo borro todo si me arrepiento?
4. ¿Necesito permisos de administrador? ¿Mi antivirus puede bloquear algo?
5. ¿Qué terminal debo usar y por qué? (Sé que en Windows hay varias y no sé la diferencia)

Después de responder eso, dame el primer paso.

> **Por qué importa:** Windows tiene varias terminales (Símbolo del sistema, PowerShell, Terminal de Windows). No son lo mismo. Y el antivirus sí puede bloquear instalaciones. Que te lo aclare antes, no cuando falle.

---

## PROMPT 3 EN ADELANTE — EL PING-PONG

**Cuando funciona:**

Listo. [pega la última línea de la terminal]
Siguiente paso.

**Cuando falla:**

[pega TODO el texto tal cual, sin resumir ni traducir]
¿Qué pasó? ¿Rompí algo? ¿Cómo lo arreglo?

**Cuando dudas:**

No entendí [X]. Explícamelo como si nunca hubiera visto una terminal.
No sigas hasta que confirme.

**Cuando el asistente asume algo:**

Me estás dando por sabido [X]. No lo sé.
Explícame eso primero y luego seguimos.

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

> **Por qué este importa más que todos:** que un `--help` responda no prueba nada. Comparar dos salidas reales con tu archivo sí. En la prueba que se hizo en Mac con un libro de 120 páginas, Docling detectó 145 títulos y MarkItDown ninguno. Comprueba si en tu Windows pasa lo mismo.

---

## PROMPT DE AUTOMATIZACIÓN

Ya funciona desde la terminal. Ahora quiero no volver a abrirla.

Antes de darme instrucciones, verifica en la web:
1. ¿Cuáles son las formas de agregar una acción al clic derecho en MI versión de Windows?
2. ¿Cuál es la MENOS riesgosa? Me han dicho que hay métodos que tocan el Registro de Windows y no quiero eso si hay alternativa.
3. ¿Existe algo como la carpeta "Enviar a" (Send To)? ¿Sirve para esto?
4. ¿La automatización va a heredar la configuración de mi terminal, o hay que darle rutas completas? (En Mac esto rompe el 90% de los intentos)

Dime primero cuál método recomiendas y por qué. No me des los pasos todavía.

> **Por qué importa:** hay dos caminos en Windows — la carpeta "Enviar a" (no toca nada del sistema) y editar el Registro (más potente, más riesgoso). No dejes que el asistente elija por ti sin explicarte la diferencia.

---

## PROMPT DE AUDITORÍA — OPCIONAL, RECOMENDADO

Toma la guía que me diste y revísala como si fueras otro desarrollador buscando errores, no confirmándola.
¿Qué omitiste? ¿Qué asumes que yo ya sé? ¿Qué es lo más probable que me falle?

> Mejor aún: pásasela a otro modelo de IA y trae la respuesta de vuelta. Dos opiniones encuentran más errores que una.

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

## PROMPT BONUS — CIERRA EL CÍRCULO

Si llegaste hasta aquí y todo funcionó, este prompt convierte tu sesión en la plantilla que le faltaba a la comunidad:

Ya terminamos y todo funciona.
Ahora conviértelo en una plantilla definitiva para Windows, igual de precisa que la de Mac:
- Los pasos exactos que funcionaron en MI equipo
- Los errores que encontramos y cómo los resolvimos
- Lo que asumiste mal al principio y tuviste que corregir
- Los detalles que ninguna guía teórica menciona

Que la siguiente persona no tenga que descubrirlo desde cero.

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

**Pero verifícala tú.** La evidencia detrás de esta regla viene de una prueba en Mac con un libro de 120 páginas: Docling detectó 145 títulos, MarkItDown ninguno. Es una diferencia enorme — pero es *un* documento, en *un* sistema. Con PDFs simples y bien maquetados la brecha se achica. Por eso existe el Prompt de Validación.

## Lo que no cambia en ningún sistema operativo

Ninguna de las dos es 100% precisa. El PDF guarda coordenadas, no estructura. Todo conversor adivina. Revisa siempre el .md — sobre todo tablas y páginas con diagramas.

## Sobre tu equipo

Estas herramientas corren en espacio de usuario, sin acceso privilegiado. No pueden dañar tu hardware. En el peor caso van lentas o el proceso se cierra solo.

Lo que **sí** puede pasar en Windows y no en Mac: que tu antivirus bloquee la instalación, o que necesites permisos de administrador. Ninguna de las dos cosas rompe nada — solo te detiene. Por eso el Prompt 2 pregunta por ambas.

---

# LAS 7 REGLAS DETRÁS DE LA PLANTILLA

Estas aplican en cualquier sistema operativo:

1. **La densidad va al frente.** Prompt 0 largo, después mensajes de dos líneas.
2. **Di el "para qué", no solo el "qué".** Cambia la herramienta recomendada.
3. **Declara tu nivel sin maquillar.** "Sé algo" produce guías que fallan.
4. **Nombra las restricciones invisibles.** El NDA, el presupuesto, la manía por el orden.
5. **Pega la salida cruda.** "No funcionó" no es información.
6. **Exige un solo camino.** La ambigüedad es la falla más común del asistente, no la alucinación.
7. **Verifica con tus archivos.** No con los ejemplos del asistente.

---

# LA REGLA EXTRA DE ESTA PLANTILLA

**8. Exige verificación, no memoria.**

En Mac la plantilla pudo dar comandos exactos porque alguien los ejecutó. Aquí no.

Cada vez que el asistente te dé un comando de Windows, la pregunta correcta es: *"¿esto lo verificaste o lo recuerdas?"*

Un asistente que responde "lo recuerdo" te está adivinando el camino. Uno que busca y cita la documentación oficial te está ayudando.

Esa diferencia es todo.
