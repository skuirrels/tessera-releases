Tessera 0.1.34, built from f094b19.

- `Tessera-Windows-Setup.exe`: Windows installer (version 0.1.31)
- `Tessera-Windows.msi`: Windows MSI package (version 0.1.31)
- `Tessera-macOS-AppleSilicon.dmg`: Apple Silicon
- `Tessera-macOS-Intel.dmg`: Intel
- `Tessera-Linux-x86_64.AppImage`: AppImage (version 0.1.31)
- `Tessera-Linux-amd64.deb`: Debian / Ubuntu (version 0.1.31)
- `Tessera-Linux-x86_64.rpm`: Fedora / RHEL / openSUSE (version 0.1.31)

Installed copies update themselves: Tessera checks for a newer version when it starts, and Help ▸ Check for Updates checks on demand. Download page: https://skuirrels.github.io/tessera-releases/

## Change log

### 0.1.34 · 9 November 2026

- Avro types from other files are found when a file of the same name defines a different type. A schema that refers to `com.example.common.Identifier`, beside an `Identifier.avsc` for another namespace's `Identifier`, now reads it from the `common` folder instead of reporting that `Identifier.avsc` doesn't define it. When no file defines it, the message names the files searched and what each defines.

### 0.1.33 · 9 November 2026

- **Avro schemas in several files.** A type an `.avsc` refers to but doesn't define, such as `com.example.Value`, is read from `Value.avsc` beside the schema, or from a folder named after its namespace (`com/example/Value.avsc`) there or in a folder above. Checking as you type, *Validate Against Schema…*, *Assign Avro Schema…* and *Convert JSON/XML to Avro…* all use it. The Avro file a conversion writes holds the whole schema, with those types written in, so other tools can read it.
- **Go to Definition** (`F12`) in an `.avsc`, from the *Avro* menu or the right-click menu: with the cursor on a type name, it goes to where that type is defined, opening its file when it's in another one.

### 0.1.32 · 9 November 2026

- **Antigravity for AI assist.** *AI ▸ AI Settings…* can now use Google's Antigravity CLI (`agy`), so requests run on your Google account's plan with Gemini or another model it lists. *Sign In…* opens it in a terminal window, since it signs in only interactively there.
- *AI ▸ Sign In…* checks first. When the tool is already signed in, the item is ticked and reads *Sign In Again…*, and it asks before starting a new sign-in instead of opening the browser straight away.
- **Convert JSON/XML to Avro.** *Convert ▸ Convert JSON/XML to Avro…* writes the records of a JSON, JSON Lines, YAML or XML file to an Avro data file, read with an `.avsc` schema, and opens it in the viewer. The schema the document names in `$schema`, or an `.avsc` of the same name beside it, is offered first. Values can be plain (dates, timestamps and decimals as text, bytes as base64, unions unwrapped) or in Avro's JSON encoding, and Tessera tells which from the records. Any of the six codecs can compress the file. A record that doesn't fit the schema stops the conversion at its line, writing nothing, unless you choose to leave such records out and list them. *Convert ▸ Stop Converting* cancels.
- What *Convert Avro to JSON/XML…* writes now converts back to the same records. Plain values use XML Schema's forms: bytes are base64 (they were hex), durations are `xs:duration` such as `P1M2DT0.5S`, timestamps leave out a zero fraction, and `big-decimal` values are numbers. The table still shows bytes as hex.
- An `xz` block that decompresses past the 512 MB limit is reported as too large, not as corrupt.

### 0.1.31 · 8 November 2026

- *Convert ▸ Convert Avro to JSON/XML…* converts a whole Avro file to JSON, JSON Lines or XML, however large. Values come out readable (dates as dates, decimals as numbers, unions unwrapped). JSON can instead use Avro's JSON encoding, so it reads back as Avro. A long conversion shows in the bar, and *Stop* cancels it.
- Saving a new file in a folder reached through a symbolic link (such as macOS's `/var`) gives its tab the file's real path, so opening the file again goes to that tab instead of a second one.

### 0.1.30 · 8 November 2026

- **Avro support.** Avro schemas (`.avsc`) are checked against the Avro specification as you type, with completion and hover for the schema format.
- Avro data files (`.avro`) open read-only, 1,000 records at a time, as JSON or as a table. The Blocks pane lists the records in blocks, and you can search the values, go to a record, and open or save the embedded schema. All six codecs are read.
- *Validate Avro File* (`F8`) checks every record against the embedded schema, and *Validate Against Schema…* checks that the file can be read with another schema.
- *Assign Avro Schema…* validates a JSON or YAML document against an Avro schema, in Avro's JSON encoding.
- Tessera registers itself for `.avsc` and `.avro` files.

### 0.1.29 · 6 November 2026

- On macOS, quitting with ⌘Q, from the Dock or by logging out asks to save documents with unsaved changes first, as closing the window does. Before, it quit straight away and the changes were lost. With nothing unsaved, Tessera still quits at once.

### 0.1.28 · 3 November 2026

- You can edit a Markdown document in the preview. Click into a paragraph, heading, list or table and type; the source follows as you go, and only the block you edit is rewritten, so the rest of the file keeps its exact text.
- A strip above the preview formats what you're editing: paragraph and headings, **bold**, *italic*, strikethrough, inline code, links, bulleted and numbered lists, quotes, code blocks and horizontal rules. ⌘B, ⌘I, ⌘E, ⌘K and ⌘⇧X work too (Ctrl on Windows and Linux).
- While editing, clicking a link puts the caret in it; ⌘-click (Ctrl-click) opens it. Pasted formatted text arrives as Markdown, and web images in it stay blocked until you allow them.

### 0.1.27 · 29 October 2026

- In **Markdown and Preview**, the source and the preview scroll together, whichever one you scroll. The line you're editing sits at the same height in both, so you can see it in the preview as you type.
- Clicking a block in the preview moves the cursor to its source and lines the editor up with the preview, without the preview jumping.

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
