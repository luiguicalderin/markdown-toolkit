# Markdown Toolkit

Convertir PDF, Word, Excel y PowerPoint a Markdown (`.md`) desde tu propio equipo, sin subir archivos a ninguna web.

Pensado para gente que **no sabe usar la terminal** y no quiere aprender.

---

## Por qué existe esto

Trabajo con documentos de clientes: briefs, contratos, research. Necesitaba convertirlos a Markdown para reducir tokens antes de pasarlos a un LLM.

Los conversores web resuelven el problema técnico y crean uno peor: **el archivo sale de tu computador.** Si firmaste un NDA, subir ese PDF a un servidor de terceros no identificados es un incumplimiento contractual. "Pero decían que lo borraban" no es una defensa.

Así que lo hice local. Y documenté cada paso, incluyendo los que fallaron.

---

## La regla corta

📄 **¿Es PDF? → Docling**
📎 **¿Es cualquier otra cosa? → MarkItDown**

---

## La evidencia detrás de la regla

No me creas. Estos son los números de una prueba real: el mismo PDF (un libro de 120 páginas), convertido con las dos herramientas.

| | MarkItDown | Docling |
|---|---|---|
| **Títulos detectados** | **0** | **145** |
| **Tablas reconstruidas** | **0** | 11 |
| Listas | 32 | 272 |
| Peso del archivo | 199 KB | 184 KB |

Cero títulos y cero tablas es texto plano con extensión `.md`, no Markdown.

**El detalle que importa para tokens:** MarkItDown produjo un archivo *más pesado* con *menos información útil*. Arrastró el encabezado y el número de cada página — repetido 120 veces. Docling lo identificó como ruido de página y lo descartó.

Estructura > tamaño. Ese es el punto entero de convertir a Markdown.

---

## Contenido de este repo

| Archivo | Qué es | Estado |
|---|---|---|
| [`plantilla-mac.md`](plantilla-mac.md) | Plantilla de prompts para instalar y automatizar en Mac | ✅ **Probada** |
| [`plantilla-windows.md`](plantilla-windows.md) | Plantilla de prompts para Windows | ⚠️ **Sin validar** |
| [`desinstalar-mac.md`](desinstalar-mac.md) | Cómo borrar todo sin dejar rastro | ✅ Probada |

---

## ⚠️ La plantilla de Windows no está validada

Y quiero ser explícito al respecto.

La de Mac se escribió **ejecutándola paso a paso en un Mac real**. Ahí aparecieron cosas que ninguna guía teórica predice:

- El instalador imprimió una variante de comando que no estaba documentada en ninguna guía que encontré
- MarkItDown instaló una versión antigua sin avisar — solo se detectó probando con un archivo real
- El atajo de clic derecho falla si no usas rutas absolutas, porque Automator no hereda la configuración de la terminal

Ninguna de esas tres se predice desde un escritorio. Se descubren ejecutando.

**La de Windows no pasó por eso.** Está escrita para *descubrir* los pasos contigo, no para dictártelos. Es más lenta a propósito.

**Si la ejecutas en un Windows real, manda un PR.** Ese es el trabajo que le falta a este repo.

---

## Lo que NO te van a decir en otros lados

**Ninguna herramienta es 100% precisa. Ninguna.**

El PDF guarda *coordenadas*, no *estructura*. Dice "texto en X=120, Y=340, 18pt". No dice "esto es un H2". Todo conversor tiene que **adivinar** la jerarquía.

Docling adivina mejor porque literalmente *mira* la página con modelos de visión. Pero adivina.

**Siempre revisa el `.md`.** Es un borrador, no un entregable. Ojo con:

- PDF escaneado sin OCR
- Tablas con celdas combinadas
- Layouts a 2-3 columnas
- XLSX con fórmulas (obtienes el valor, no la fórmula)

---

## Las herramientas

| | Qué es | Enlace |
|---|---|---|
| **Docling** | Conversor de IBM. Usa modelos de visión para entender el layout | [docling-project/docling](https://github.com/docling-project/docling) |
| **MarkItDown** | Conversor de Microsoft. Multiformato y rápido | [microsoft/markitdown](https://github.com/microsoft/markitdown) |

Ambas son gratis, open source, y corren 100% en local.

---

## Cómo usar este repo

1. Abre la plantilla de tu sistema operativo
2. Copia el **Prompt 0**, rellena lo que está entre corchetes
3. Pégaselo a un asistente de IA (Claude, ChatGPT, el que uses)
4. Sigue el ping-pong: un paso, lo ejecutas, reportas, siguiente

Las plantillas no son guías. Son **conversaciones estructuradas** para que el asistente descubra los pasos correctos para *tu* equipo.

---

## Cómo contribuir (todo desde el navegador)

Este repo está escrito para gente que no usa la terminal. Sería incoherente pedir contribuciones que la requieran.

**Todo se hace desde el navegador.**

### Si encuentras un error o quieres mejorar algo

1. Abre el archivo aquí en GitHub
2. Clic en el **lápiz ✏️** (arriba a la derecha del archivo)
3. Edita
4. Abajo, escribe qué cambiaste
5. Marca **"Create a new branch for this commit and start a pull request"**
6. **Propose changes**

Eso es un *pull request*: una propuesta de cambio. No modifica nada hasta que alguien la revise. **No puedes romper nada.**

### Si prefieres solo avisar

Ve a la pestaña **Issues** → **New issue**. Cuentas qué falló y ya. Igual de útil.

### Lo que más falta ahora mismo

**Validar la plantilla de Windows.** Si la ejecutas en un Windows real:

- Los pasos que sí funcionaron
- Los que fallaron y cómo los resolviste
- Lo que la plantilla asumía mal
- Los detalles que ninguna guía teórica menciona

Con eso, la de Windows deja de ser teoría.

---

## Las 7 reglas (aplican a cualquier tarea técnica con IA)

1. **La densidad va al frente.** Prompt inicial largo, después mensajes de dos líneas.
2. **Di el "para qué", no solo el "qué".** Cambia la herramienta recomendada.
3. **Declara tu nivel sin maquillar.** "Sé algo" produce guías que fallan.
4. **Nombra las restricciones invisibles.** El NDA, el presupuesto, la manía por el orden.
5. **Pega la salida cruda.** "No funcionó" no es información.
6. **Exige un solo camino.** La ambigüedad es la falla más común del asistente, no la alucinación.
7. **Verifica con tus archivos.** No con los ejemplos del asistente.

---

## Licencia

MIT. Úsalo, cámbialo, compártelo.
