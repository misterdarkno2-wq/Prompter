# Prompter

`mejorar-preguntas` convierte solicitudes de desarrollo web en prompts técnicos y los aplica en el mismo turno. Usa el código y las versiones del proyecto cuando están disponibles. Para bugs, pide evidencia de la causa y verifica la corrección. Para seguridad defensiva, revisa los controles del flujo afectado y cómo comprobarlos.

## Descargar

En GitHub, abre el archivo ZIP y selecciona **Download raw file**. Si ya clonaste el repositorio, usa el ZIP que está en su raíz. [mejorar-preguntas.zip](mejorar-preguntas.zip)

## Instalar en Codex o Claude Code

Los comandos asumen que guardaste `mejorar-preguntas.zip` en `Downloads` (Descargas). Ajusta la ruta si lo guardaste en otro lugar. En el bloque de tu sistema, ejecuta la primera línea para indicar dónde está el ZIP y luego las líneas de la aplicación que quieras configurar.

### Windows PowerShell

```powershell
$prompterZip = Join-Path $env:USERPROFILE 'Downloads\mejorar-preguntas.zip'

# Codex
$codexSkills = Join-Path $env:USERPROFILE '.agents\skills'
Expand-Archive -LiteralPath $prompterZip -DestinationPath $codexSkills -Force

# Claude Code
$claudeSkills = Join-Path $env:USERPROFILE '.claude\skills'
Expand-Archive -LiteralPath $prompterZip -DestinationPath $claudeSkills -Force
```

### macOS y Linux

```bash
prompter_zip="$HOME/Downloads/mejorar-preguntas.zip"

# Codex
mkdir -p "$HOME/.agents/skills"
unzip -o "$prompter_zip" -d "$HOME/.agents/skills"

# Claude Code
mkdir -p "$HOME/.claude/skills"
unzip -o "$prompter_zip" -d "$HOME/.claude/skills"
```

La carpeta `mejorar-preguntas` debe quedar dentro de `skills`, con `SKILL.md` y la carpeta `references`. Para actualizar, vuelve a extraer el ZIP en el mismo destino. Si ya la instalaste en `~/.codex/skills`, usa esa ruta para actualizar esa copia. [Guía de Codex](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills) · [Guía de Claude Code](https://code.claude.com/docs/en/skills#choose-where-skills-load)

## Instalar en Claude web

1. Abre **Personalizar → Habilidades**.
2. Pulsa **+ → Crear habilidad → Cargar una habilidad**.
3. Selecciona `mejorar-preguntas.zip` y activa `mejorar-preguntas` en la lista.

Si la sección **Habilidades** no aparece, revisa que esté habilitada la ejecución de código en **Configuración → Capacidades**. [Guía de Claude](https://support.claude.com/es/articles/12512180-usar-habilidades-en-claude)

## Usar la skill

Escribe `$mejorar-preguntas` en Codex, `/mejorar-preguntas` en Claude Code o «Usa la habilidad mejorar-preguntas» en Claude web. La aplicación también puede seleccionarla automáticamente cuando la solicitud coincide con su descripción.

> Mi web se queda cargando después de iniciar sesión. Encuentra la causa y corrígela.

Por defecto, la skill aplica la reformulación y entrega el resultado. Para obtener el texto del prompt, añade «Devuélveme solo el prompt mejorado».
