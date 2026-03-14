Compile the screenplay into DOCX.

1. Read CLAUDE.md — check the "Type" field. If empty — stop: "Project type not set. Run /startproject."
2. Check scenes/ — list all files in order
3. Check for problems:
   - Empty files (0 lines of content)
   - Files without a `# Scene` / `# Block` heading
   - Gaps in numbering (e.g.: 01, 02, 04 — 03 is missing)
   - If there are problems — list them and ask whether to continue
4. Run the converter:
   ```bash
   python converter_MD_DOCX/md_to_docx.py
   ```
   If `converter_MD_DOCX/md_to_docx.py` is not found — tell the user to run `/sync-plugin-files` to copy it from the plugin.
5. Output the result: file path, number of scenes, number of paragraphs
6. If there are errors — show them and suggest a fix

If error `ModuleNotFoundError: No module named 'docx'`:
```
pip install python-docx
```
(Use `python-docx`, not `docx` — they are different packages.)

The converter reads all .md files from scenes/ alphabetically. The 00_* file is used as the title page.
