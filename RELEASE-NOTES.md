Tessera 0.1.26, built from 7d01b38.

- `Tessera-Windows-Setup.exe`: Windows installer
- `Tessera-Windows.msi`: Windows MSI package
- `Tessera-macOS-AppleSilicon.dmg`: Apple Silicon
- `Tessera-macOS-Intel.dmg`: Intel
- `Tessera-Linux-x86_64.AppImage`: AppImage
- `Tessera-Linux-amd64.deb`: Debian / Ubuntu
- `Tessera-Linux-x86_64.rpm`: Fedora / RHEL / openSUSE

Installed copies update themselves: Tessera checks for a newer version when it starts, and Help ▸ Check for Updates checks on demand. Download page: https://skuirrels.github.io/tessera-releases/

## Change log

### 0.1.26 · 20 October 2026

- The window has the system's own title bar again, with the usual minimise, maximise and close buttons. The menus are in a row below it, as in Mapster.

### 0.1.25 · 19 October 2026

- **Save As** keeps a JSON document's .json extension. The dialog starts on the document's own file type, so on Windows a name without an extension no longer became .xml or .xsd.
- An XSLT result written as text that is valid JSON opens as a JSON document, named .json.
- The Messages panel is now **Logs**, and the XPath tab says **JSONPath** for JSON and YAML documents.

### 0.1.24 · 19 October 2026

- Clicking in the text after using the scrollbar, a tab or the outline puts the cursor where you click. On macOS it could jump back to the previous cursor and select everything in between.
- **Go to Line** is Ctrl+G (⌃G on macOS). ⌘⌥G clashed with shortcuts of other apps, such as Google Drive.
- **Find Next** and **Find Previous** are F3 and Shift+F3 on Windows and Linux (⌘G and ⌘⇧G on macOS), and in the Edit menu.

### 0.1.23 · 19 October 2026

- Right-click a tab to copy the file name, or the file name with its path.

### 0.1.22 · 19 October 2026

- With long file names, the close button on a tab keeps its full size. Only the name is shortened.

### 0.1.21 · 19 October 2026

- The XPath tab is shown only for XML, JSON and YAML documents. Markdown and text documents show Messages instead, and Evaluate XPath/JSONPath is turned off for them.
- In the dark theme, selected text in the XPath box is readable, with the same selection colour as the editor.

### 0.1.20 · 19 October 2026

- The Markdown, Markdown and Preview, and Preview switch is in the toolbar, so it stays in place when you change the view. Windows and Linux already had this in 0.1.19.

### 0.1.19 · 19 October 2026

- **Tessera Settings** (File ▸ Settings…, Ctrl+, or ⌘,): the editor and checking options as tick boxes, in one place.
- **Open with Tessera**: tick the extensions (.xml, .xsd, .json, .yml, .md and the rest) and make Tessera their default app. macOS asks you to confirm each kind of file; on Windows, Tessera opens Settings ▸ Default apps for you to choose it.
- On macOS, Tessera now appears in Open With for .xsd, .xsl, .xslt, .wsdl, .rng, .sch, .jsonc, .json5 and .jsonl files.

### 0.1.18 · 18 October 2026

- **Markdown views**: show the source, the preview, or both side by side, from the switch at the right of the tabs, the View menu, or Ctrl+Shift+V. The outline stays in every view, and clicking a heading scrolls the preview.
- **Find** opens as a compact box at the top right of the editor, as in other editors. It shows the number of matches, selects the nearest one as you type, and has match case, whole word and regular expression toggles (Alt+C, Alt+W, Alt+R). **Replace** is Ctrl+H.

### 0.1.17 · 18 October 2026

- The app name in the title bar is centred on the window and drawn in the normal text colour.

### 0.1.16 · 18 October 2026

- The title bar shows the app name; the tabs already show the file.
- New download page: a download button that picks your system (and Mac architecture where the browser says), a card per platform with sizes and SHA-256 checksums, and installers under names that never change.

### 0.1.15 · 17 October 2026

- **JSON Schema** for JSON and YAML: live validation located in the text, completion and hover from the schema, Assign/Go to JSON Schema, and checks of schemas against their meta-schema.
- **YAML 1.2** as a full format: outline, breadcrumb, JSONPath, aliases and merge keys, multi-document streams, and JSON ↔ YAML conversion.
- **Generate sample** XML from an XSD, and sample JSON/YAML from a JSON Schema, with XMLSpy's options.
- **Conversion dialogs** for XML ↔ JSON/YAML: prefixes, arrays, type detection, comments and processing instructions.
- **Markdown**: highlighting, heading outline and a live preview that follows the editor.
- **AI assist** through your own Claude Code or Codex CLI: chat panel, Explain, Fix with AI, XSLT from examples (checked by running it) and realistic sample values. Off by default; every request shows what will be sent.
- F7/F8 validate from the editor instead of jumping to the diagnostics.

### 0.1.14 · 17 October 2026

- macOS: the window buttons are centred on the title bar, and the menus have more room.

### 0.1.13 · 17 October 2026

- Each platform has its own update feed, so a Mac no longer reports “None of the fallback platforms were found” when another platform was released first. No update for your platform now reads as up to date.

### 0.1.12 · 17 October 2026

- Right-click ▸ Evaluate XPath/JSONPath in the editor, outline or breadcrumb starts from the clicked element.

### 0.1.11 · 17 October 2026

- Very deeply nested XML and entity “bombs” no longer crash the app or exhaust memory.
- Much faster XML → JSON, schema generation and XPath results on large or deep documents; JSON tools use far less memory.
- XPath works on documents with a DOCTYPE, and copied XPaths select their node when prefixes are rebound or default namespaces nest.
- Fixes in JSON → XML, schema generation and schema/DTD assignment.
- Validation (F8) no longer times out the first time after start; the language server and XSLT worker exit with Tessera.
- Saves of a document are serialised, pretty-print on open can't open a file twice, and updates download before asking about unsaved work.
- Shortcuts follow the keyboard layout, ignore AltGr characters and don't auto-repeat Save.

### 0.1.10 and earlier · 16–17 October 2026

- **Editor** for XML and JSON with lossless pretty-print: encoding, BOM and line endings survive a save. Saves detect files changed by other programs.
- **XML tools**: live well-formedness checks, outline, breadcrumb, Copy XPath (plain, with positions, or with attribute values) and XML ↔ JSON conversion.
- **XPath 3.1 window** like XMLSpy's: live results beside the expression, matches highlighted in the editor, default-namespace names, syntax colouring and history.
- **Schema validation** with XML Schema, DTD and RELAX NG via LemMinX: diagnostics as you type, completion, hover docs and Go to Schema/DTD.
- **XSL Transformation** (F10) in an isolated worker with a timeout and Stop; output opens in a new tab.
- **Generate Schema**: an XSD or a JSON Schema 2020-12 from a sample document.
- **JSON paths**: JSON outline and breadcrumb, Copy JSONPath and JSON Pointer, and JSONPath (RFC 9535) in the XPath window.
- Toolbar, right-click menus, File ▸ Recent Files, and Pretty-Print on Open.
- Islands layout with Tessera's own title bar and resizable, remembered panels.
- Opens files from the OS: file associations for XML and JSON, and a second launch hands its files to the running window.
- Automatic updates: checked at start and with Help ▸ Check for Updates.
