---
description: Saves the current session context to REAMDE.md and pushes to git
---

1. **Check User Input:** If the user explicitly requests to skip the context update (e.g., "sin actualizar el contexto", "don't update context"), **SKIP steps 2 through 4** and proceed directly to step 5. Use the git commit message "cierre de sesión rápido" or similar if skipping.

2. Read the file `REAMDE.md`. If it does not exist, create it.

3. Insert a item in the list with the name of the new workflow created (json file) at the beginning of `REAMDE` (immediately after the autor name)

4. Save the file.

5. **Check Git Status (Safety Filter):**
   - Before running any git commands, verified if the project is synchronized with a remote repository.
   - Run `git remote -v`.
   - **IF** the output is empty or returns an error (meaning no remote is configured), **STOP HERE**. Do NOT run Step 9.
   - **IF** a remote is configured, proceed to Step 9.

6. Run the following git commands to push the changes:
   ```bash
   git add .
   git commit -m "cierre de sesión con REAMDE.md actualizado y nuevo n8n Workflow agregado"
   git push
   ```