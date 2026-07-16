# Desinstalar todo sin dejar rastro

Guía para revertir por completo la instalación de MarkItDown, Docling, pipx y Homebrew en tu Mac.

---

## ⚠️ Lee esto primero

**Si vas a regalar o vender el equipo, esta guía NO es suficiente.**

Borrar estas herramientas no borra: tus archivos personales, tu sesión de iCloud, tus contraseñas guardadas, tu historial de navegación, tus mensajes, tus fotos, ni tu cuenta de usuario.

Para entregar un Mac a otra persona, Apple tiene un procedimiento propio: **Ajustes del Sistema → General → Transferir o restablecer → Borrar contenido y ajustes**. Eso deja el equipo como recién salido de fábrica, en unos minutos, sin instalar nada.

Esta guía sirve para el otro escenario: **quieres tu Mac limpio pero seguir usándolo**.

Si tu meta es regalarlo, salta al final, sección "Si vas a entregar el equipo".

---

## Regla de oro

**Un comando → Enter → esperar al `%` → siguiente comando.**

Nunca los pegues todos juntos.

---

## Antes de empezar: sobre `rm -rf`

Varios comandos de esta guía usan `rm -rf`. Ese comando **borra sin preguntar y sin papelera**. No hay deshacer.

**Cópialos exactamente como están aquí. Nunca los escribas de memoria. Nunca los modifiques.**

---

## PASO 1 — Abrir la Terminal

1. Presiona **⌘ + barra espaciadora**
2. Escribe: `Terminal`
3. Enter

---

## PASO 2 — Borrar los atajos de Finder

Si creaste los atajos de clic derecho con Automator:

1. Ve a **Finder**
2. Barra de arriba → **"Ir"**
3. Mantén presionada la tecla **⌥ (Option)** → aparece **"Biblioteca"**
4. Clic en **"Biblioteca"**
5. Abre la carpeta **"Services"**
6. Arrastra a la papelera los archivos:
   - `Convertir a Markdown (Docling).workflow`
   - `Convertir a Markdown (MarkItDown).workflow`
7. Vacía la papelera

---

## PASO 3 — Borrar la carpeta del Escritorio

Si creaste las carpetas de salida, en el Escritorio tendrás esta estructura:

```
Escritorio/
└── Markdown/
    ├── Docling/
    └── MarkItDown/
```

Arrastra la carpeta **`Markdown`** completa a la papelera. Se lleva las dos de adentro.

⚠️ **Revisa que no tenga archivos que quieras conservar** antes de borrarla.

---

## PASO 4 — Desinstalar Docling

```bash
pipx uninstall docling
```

---

## PASO 5 — Desinstalar MarkItDown

```bash
pipx uninstall markitdown
```

---

## PASO 6 — Borrar los modelos de IA de Docling

Esto libera cerca de 1 GB.

```bash
rm -rf ~/.cache/docling
```

---

## PASO 7 — Borrar la caché de pipx

```bash
rm -rf ~/.local/pipx
```

---

## PASO 8 — Desinstalar pipx

```bash
brew uninstall pipx
```

---

## PASO 9 — Verificar qué más instaló Homebrew

Antes de borrar Homebrew, revisa si tienes otras cosas instaladas con él que quieras conservar:

```bash
brew list
```

Esto solo **muestra** una lista. No borra nada.

Si ves herramientas que usas (por ejemplo `pandoc`, `git`, `node`), **detente aquí**. Ya borraste MarkItDown y Docling, que era el objetivo. Borrar Homebrew se llevaría todo lo demás por delante.

Si la lista está vacía o solo tiene cosas que no reconoces, continúa.

---

## PASO 10 — Desinstalar Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/uninstall/HEAD/uninstall.sh)"
```

**Qué va a pasar:**

1. Te muestra una lista larga de todo lo que va a borrar
2. Pregunta: `Are you sure you want to uninstall Homebrew?` → escribe `y` → Enter
3. Te pide tu **contraseña de Mac** → escríbela a ciegas (no verás nada) → Enter
4. Pasan muchas líneas de texto. Espera al `%`

---

## PASO 11 — Borrar los restos de Homebrew

El script oficial es bueno, pero **deja residuos**. Estos comandos los limpian.

```bash
sudo rm -rf /opt/homebrew
```

Te pedirá tu contraseña. Es normal.

Luego:

```bash
rm -rf ~/Library/Caches/Homebrew
```

Y:

```bash
rm -rf ~/Library/Logs/Homebrew
```

> **Nota:** si tu Mac es Intel (no Apple Silicon), la primera ruta es `/usr/local` en vez de `/opt/homebrew`. Pero **no borres `/usr/local` completo** — ahí puede haber otras cosas. En Intel, sáltate ese comando y confía en el script del Paso 10.

---

## PASO 12 — Limpiar la configuración del shell

Este es el paso que casi todas las guías omiten. **El script de Homebrew no borra las líneas que agregó a tu configuración.** Si las dejas, verás un mensaje de error cada vez que abras la Terminal.

Primero mira qué hay:

```bash
cat ~/.zprofile
```

Esto solo **muestra** el contenido. Vas a ver algo como:

```
eval "$(/opt/homebrew/bin/brew shellenv zsh)"
```

Ahora ábrelo para editar:

```bash
open -e ~/.zprofile
```

Se abre en TextEdit. **Borra la línea que contiene `brew shellenv`.** Deja el resto intacto.

Guarda con ⌘ + S y cierra.

Repite la revisión con este otro archivo:

```bash
cat ~/.zshrc
```

Si también tiene una línea con `brew shellenv` o `pipx`, ábrelo igual:

```bash
open -e ~/.zshrc
```

Y bórrala.

> Si alguno de los dos comandos `cat` dice `No such file or directory`, perfecto — ese archivo no existe y no hay nada que limpiar.

---

## PASO 13 — Verificar

Cierra la Terminal por completo (**⌘ + Q**) y vuelve a abrirla.

```bash
brew --version
```

Debe decir `command not found`. ✅

```bash
pipx --version
```

Debe decir `command not found`. ✅

```bash
docling --version
```

Debe decir `command not found`. ✅

Si los tres responden `command not found`, quedó todo desinstalado.

---

## PASO 14 — Cazar rastros olvidados (opcional)

Para los meticulosos:

```bash
find ~ -iname "*homebrew*" -maxdepth 4 2>/dev/null
```

```bash
find ~ -iname "*docling*" -maxdepth 4 2>/dev/null
```

Estos comandos solo **buscan y muestran**. No borran nada.

Si aparece algo, revísalo antes de borrarlo. No borres a ciegas.

---

## Lo que NO se desinstala (y está bien)

**Xcode Command Line Tools.** Homebrew lo instaló como dependencia. Ocupa espacio, pero es una herramienta oficial de Apple, no de terceros. Muchas apps la usan. Déjala.

**Python del sistema.** macOS lo trae de fábrica. Nunca lo tocamos.

---

## Si vas a entregar el equipo

Todo lo de arriba **no es lo que necesitas**. Es demasiado poco.

**El procedimiento correcto de Apple:**

1. **Ajustes del Sistema** → **General** → **Transferir o restablecer**
2. **Borrar contenido y ajustes**
3. Sigue el asistente

Eso hace en unos minutos lo que esta guía no puede hacer nunca:

| | Esta guía | Borrar contenido y ajustes |
|---|---|---|
| Homebrew, pipx, Docling | ✅ | ✅ |
| Tus archivos personales | ❌ | ✅ |
| Sesión de iCloud | ❌ | ✅ |
| Contraseñas del Llavero | ❌ | ✅ |
| Mensajes, Fotos, Notas | ❌ | ✅ |
| Historial de Safari | ❌ | ✅ |
| Tu cuenta de usuario | ❌ | ✅ |
| Bloqueo de activación | ❌ | ✅ |

**Antes de hacerlo:**

- Haz una copia de seguridad (Time Machine o disco externo)
- Cierra sesión en iCloud
- Desactiva "Buscar mi Mac"

Sin esos tres pasos, la persona que reciba el equipo puede quedarse con un Mac bloqueado a tu cuenta.

---

## Resumen de comandos

Para copiar rápido, en orden:

```
pipx uninstall docling
pipx uninstall markitdown
rm -rf ~/.cache/docling
rm -rf ~/.local/pipx
brew uninstall pipx
brew list
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/uninstall/HEAD/uninstall.sh)"
sudo rm -rf /opt/homebrew
rm -rf ~/Library/Caches/Homebrew
rm -rf ~/Library/Logs/Homebrew
open -e ~/.zprofile
```

**Uno a la vez. Nunca todos juntos.**
