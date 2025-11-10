# French Translation Status for DOSBox Staging

## Overview

The French translation file (`contrib/resources/translations/fr.lng`) has been updated and structured for completion.

## Current Statistics

- **Total entries:** 725
- **Fully translated to French:** ~515 entries (~71%)
- **Still in English (need translation):** ~210 entries (~29%)
- **Lines exceeding 80 characters:** 21 (mostly special UI formatting)

## What Has Been Done

### ✅ Completed Tasks

1. **File Structure Updated**
   - Added all 313 missing entries from `en.lng`
   - Preserved all 412 existing French translations
   - Entries now in correct order matching `en.lng`

2. **Translations Added**
   - 99 country names translated to French
   - Simple help text headers translated
   - File properly normalized to UTF-8 NFC encoding

3. **Line Length Compliance**
   - Reduced from 361 long lines to 21
   - Remaining 21 lines are special cases (UI elements, box-drawing, ANSI codes)

## What Needs Translation

### Priority 1: User-Facing Messages (~50 entries)

These are messages users will see during normal operation:

- `DOSBOX_HELP` - Main help text (command-line options)
- `TITLEBAR_HINT_*` - Mouse capture hints in title bar
- `PROGRAM_*_ERROR` - Error messages
- `SHELL_CMD_*_HELP` - Shell command help text
- Various status and informational messages

### Priority 2: Configuration Help (~100 entries)

These appear in configuration help (`config -h`):

- `CONFIG_*` entries starting around line 500
- Descriptions of video, audio, input settings
- Examples and recommendations for configuration values

### Priority 3: Advanced Features (~60 entries)

- Keyboard layout names and descriptions
- MIDI and audio device descriptions
- Network and serial port configurations
- Advanced emulation settings

## Translation Guidelines

### Important Rules from `README.md`

1. **80 Column Limit**
   - Configuration option descriptions must not exceed 80 characters per line
   - Commands like `config -h fullscreen` won't display properly otherwise
   - Use line breaks to wrap long text

2. **Format Strings**
   - Keep printf format strings like `%s`, `%d`, `%02d` unchanged
   - These are placeholders that get replaced with values at runtime
   - Example: `"Usage: %s [OPTION]"` → `"Utilisation : %s [OPTION]"`

3. **Technical Terms**
   - Keep technical terms in English when appropriate: MIDI, BIOS, ROM, etc.
   - Keep command names in English: `config`, `mount`, `boot`, etc.
   - Keep file extensions in English: `.conf`, `.lng`, etc.

4. **Color Codes**
   - Preserve ANSI color codes like `[color=white]`, `[reset]`, `[bgcolor=blue]`
   - These control text color in the DOSBox interface

5. **Indentation and Structure**
   - Preserve indentation for option lists
   - Keep the visual structure of help text and tables

## Examples of Good Translations

### Country Names
```
:COUNTRY_NAME_USA
États-Unis
.
```

### Simple Configuration
```
:CONFIG_FULLSCREEN
Démarrer DOSBox directement en mode plein écran.
.
```

### Multi-line with Formatting
```
:CONFIG_WINDOWRESOLUTION
Défini la taille de la fenêtre pendant l'utilisation en mode fenêtré :
  default:   Sélectionne la meilleure option basée sur
             votre environnement et d'autres paramètres.
  original:  Redimensionne la fenêtre suivant la résolution
             choisie par le programme émulé.
.
```

## Tools for Translation

### Recommended Text Editors

- **Notepad++** (Windows) - Free, supports UTF-8
- **Visual Studio Code** (All platforms) - Free, excellent UTF-8 support
- **Sublime Text** (All platforms) - Good for large files

### Important Editor Settings

1. **Encoding:** UTF-8 (without BOM)
2. **Line Endings:** Unix (LF)
3. **Tab Characters:** Use spaces, not tabs
4. **Column Guide:** Set at 80 characters

### After Editing

Always run the normalization script:
```bash
cd contrib/resources/translations
./normalize.sh
```

This ensures proper UTF-8 NFC normalization.

## Testing Your Translation

If you have DOSBox built, test with:
```bash
dosbox -lang fr -c "config -h" -c "help /all" -c "exit"
```

Check that:
- Text wraps correctly at 80 columns
- No lines are cut off or display weirdly
- Colors and formatting look correct
- Accented characters display properly

## Key Entries Awaiting Translation

Here are some of the most visible entries that need French translation:

1. **DOSBOX_HELP** (lines 5-80) - Main command-line help
2. **TITLEBAR_HINT_CAPTURED_HOTKEY** - "mouse captured, %s+F10 to release"
3. **TITLEBAR_HINT_SEAMLESS_HOTKEY** - "seamless mouse, %s+F10 to capture"
4. **CONFIG_VIEWPORT_RESOLUTION** (line 27) - Viewport size setting
5. **CONFIG_WINDOW_POSITION** (line 33) - Window position setting
6. **CONFIG_WINDOW_DECORATIONS** (line 39) - Window decorations setting
7. **CONFIG_TRANSPARENCY** (line 42) - Window transparency setting
8. **CONFIG_HOST_RATE** (line 49) - Host refresh rate setting

And many more configuration and help entries throughout the file.

## Contact

For questions or assistance with the translation:
- Open an issue on GitHub
- Reference the translation guide: `contrib/resources/translations/README.md`
- Check the main documentation: https://github.com/dosbox-staging/dosbox-staging

## Notes

- This is the `.lng` format used by this fork
- The upstream DOSBox Staging has migrated to `.po` format
- If syncing with upstream becomes important, consider migrating to `.po` format in the future
