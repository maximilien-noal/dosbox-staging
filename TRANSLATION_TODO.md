# French Translation TODO

## Current Status
- **Completed**: 288/1,080 entries (27%)
- **Remaining**: 792 entries need translation
- **Fuzzy**: 885 entries marked for review

## Categories Needing Translation

### High Priority (User-Facing)
1. **Country Names** ✅ DONE (104 entries)
   - All COUNTRY_NAME_* entries translated

2. **Configuration Options** (95 entries)
   - CONFIG_* entries
   - These appear in `config -h` command output
   - **Must respect 80-column limit**

3. **Help Text** (~50 entries)
   - DOSBOX_HELP and related
   - PROGRAM_*_HELP entries
   - Command usage instructions

### Medium Priority
4. **Keyboard Layout Names** (107 entries)
   - KEYBOARD_LAYOUT_NAME_* entries
   - Displayed in `keyb /list` command

5. **Code Page Descriptions** (154 entries)
   - CODE_PAGE_DESCRIPTION_* entries
   - Technical descriptions of character encodings

6. **Shell Commands** (~100 entries)
   - SHELL_CMD_* entries
   - DOS command help text
   - **Must respect 80-column limit**

### Lower Priority
7. **Error Messages** (~100 entries)
   - Various error and status messages

8. **Program-Specific** (~186 entries)
   - PROGRAM_* entries for various utilities
   - Mount, mixer, memory commands, etc.

## Translation Guidelines

### 80-Column Limit
From `docs/TRANSLATING.md`:
- Configuration options: max 80 chars/line
- Command help: max 80 chars/line  
- Startup screens: test with `startup_verbosity = high`

### Format Strings
Preserve printf format strings:
- `%s` = string placeholder
- `%d` = number placeholder
- `%02d` = zero-padded number
- Keep these unchanged in translations

### Technical Terms
Consider keeping in English:
- MIDI, BIOS, ROM, RAM, CPU
- File extensions: .conf, .po, .exe, .bat
- Command names: config, mount, imgmount

### PO File Format
- Use UTF-8 encoding
- Unix line endings (LF)
- Multiline strings:
  ```
  msgstr ""
  "First line\n"
  "Second line\n"
  ```

## How to Continue

### Option 1: Manual Translation with PO Editor
1. Install Poedit, Lokalize, or Gtranslator
2. Open `resources/translations/fr.po`
3. Translate entries marked as "fuzzy" or empty
4. Save and run `extras/translations/normalize.sh`

### Option 2: Collaborative Translation
1. Post on DOSBox Staging forums/Discord
2. Recruit French-speaking community members
3. Divide work by category
4. Review and merge contributions

### Option 3: Professional Translation
- Hire translator familiar with:
  - Retro computing/DOS terminology
  - French technical writing
  - 80-column text formatting

## Testing Translations

After translating, test with DOSBox:
```bash
# Build DOSBox with French translations
meson setup build
meson compile -C build

# Test
build/dosbox -lang fr -c "config -h" -c "help /all" -c "exit"
```

Check for:
- Proper text wrapping
- No cut-off lines
- Correct character encoding
- Proper display of accented characters

## Estimated Effort

Based on professional translation rates:
- ~792 entries remaining
- Average 2-5 minutes per entry (research, translate, format, verify)
- **Total**: 26-66 hours of work
- Plus testing and QA time

This is a substantial project requiring dedicated translation effort.
