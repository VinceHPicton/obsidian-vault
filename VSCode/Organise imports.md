`Shift + Alt + O (Windows/Linux)
`Shift + Option + O (Mac)``

Alternatively, you can use the **Command Palette**:

1. Press `Ctrl + Shift + P` (Windows/Linux) or `Cmd + Shift + P` (Mac).
2. Search for **"Organize Imports"**.
3. Select **"Organize Imports"** to remove unused imports and sort them.

---

### 🛠 **Automating It on Save**

You can configure VS Code to **automatically remove unused imports** every time you save a file:

1. Open your **settings.json** (`Ctrl + ,` and search for "settings.json").
2. Add the following:

```
"editor.codeActionsOnSave": {
  "source.organizeImports": true
}
```

Now, **unused imports will be removed automatically on save**! 