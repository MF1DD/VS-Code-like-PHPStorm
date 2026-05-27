## Ziel

VS Code soll sich möglichst wie PHPStorm verhalten (ca. 95–99%).

Das beinhaltet:

* JetBrains-Keybindings
* Navigation wie PHPStorm
* Refactoring
* IntelliSense
* PHP-Unterstützung
* Tabs / Editor-Verhalten
* Terminal-Verhalten
* Code-Style
* Suche
* Multi-Cursor
* Autocomplete
* Git-Integration

---

# 1. Benötigte Extensions installieren

## Pflicht-Extensions

Installiere folgende Extensions:

```bash
code --install-extension PKief.material-icon-theme
code --install-extension zhuangtongfa.Material-theme
code --install-extension bmewburn.vscode-intelephense-client
code --install-extension xdebug.php-debug
code --install-extension onecentlin.laravel-blade
code --install-extension eamodio.gitlens
code --install-extension usernamehw.errorlens
code --install-extension formulahendry.auto-close-tag
code --install-extension formulahendry.auto-rename-tag
code --install-extension streetsidesoftware.code-spell-checker
code --install-extension EditorConfig.EditorConfig
code --install-extension mhutchie.git-graph
code --install-extension Gruntfuggly.todo-tree
code --install-extension christian-kohler.path-intellisense
code --install-extension esbenp.prettier-vscode
code --install-extension foxundermoon.shell-format
code --install-extension ms-vscode.makefile-tools
```

---

# 2. JetBrains Keymap aktivieren

## Extension installieren

```bash
code --install-extension k--kato.intellij-idea-keybindings
```

ODER:

```bash
code --install-extension isudox.vscode-jetbrains-keybindings
```

Die zweite Variante ist oft näher an PHPStorm.

---

# 3. PHPStorm Keymap importieren

## Export aus PHPStorm

In PHPStorm:

```text
File → Manage IDE Settings → Export Settings
```

Exportiere:

* Keymaps
* Editor Settings
* Code Style (optional)

---

## Keymap in VS Code übernehmen

### Variante A (empfohlen)

Die exportierte Keymap als Referenz nutzen und manuell in:

```text
keybindings.json
```

übernehmen.

Öffnen:

```text
CTRL + SHIFT + P
Preferences: Open Keyboard Shortcuts (JSON)
```

---

## Beispiel-Mapping

```json
[
    {
        "key": "ctrl+d",
        "command": "editor.action.duplicateSelection"
    },
    {
        "key": "shift+f6",
        "command": "editor.action.rename"
    },
    {
        "key": "ctrl+alt+l",
        "command": "editor.action.formatDocument"
    },
    {
        "key": "ctrl+e",
        "command": "workbench.action.quickOpen"
    },
    {
        "key": "alt+1",
        "command": "workbench.view.explorer"
    }
]
```

---

# 4. settings.json wie PHPStorm konfigurieren

Öffne:

```text
CTRL + SHIFT + P
Preferences: Open Settings (JSON)
```

Dann:

```json
{
    "editor.fontSize": 14,
    "editor.fontFamily": "JetBrains Mono",
    "editor.tabSize": 4,
    "editor.insertSpaces": true,
    "editor.detectIndentation": false,

    "editor.minimap.enabled": false,
    "editor.renderWhitespace": "selection",
    "editor.smoothScrolling": true,
    "editor.cursorSmoothCaretAnimation": "on",

    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.fixAll": "explicit"
    },

    "editor.inlineSuggest.enabled": true,
    "editor.suggestSelection": "first",
    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": true
    },

    "workbench.iconTheme": "material-icon-theme",
    "workbench.colorTheme": "One Dark Pro",

    "workbench.editor.enablePreview": false,
    "workbench.startupEditor": "none",

    "breadcrumbs.enabled": true,

    "files.autoSave": "afterDelay",
    "files.autoSaveDelay": 500,

    "terminal.integrated.defaultProfile.windows": "PowerShell",

    "php.validate.enable": false,

    "intelephense.environment.phpVersion": "8.2",

    "explorer.confirmDelete": false,

    "git.autofetch": true,

    "editor.guides.indentation": true,
    "editor.stickyScroll.enabled": true
}
```

---

# 5. PHP-Unterstützung verbessern

## Intelephense konfigurieren

Sehr wichtig für PHPStorm-ähnliche Features:

```json
"intelephense.files.maxSize": 5000000,
"intelephense.completion.insertUseDeclaration": true,
"intelephense.format.enable": true
```

---

# 6. Refactoring wie PHPStorm

## Gute Unterstützung bekommst du durch:

* Intelephense
* PHP Namespace Resolver
* IntelliJ Keybindings

Optional:

```bash
code --install-extension MehediDracula.php-namespace-resolver
```

---

# 7. JetBrains Font installieren

## JetBrains Mono

[JetBrains Mono Download](https://www.jetbrains.com/lp/mono/?utm_source=chatgpt.com)

Danach in VS Code aktivieren:

```json
"editor.fontFamily": "JetBrains Mono"
```

---

# 8. Optionales Setup-Script (Windows)

## setup-vscode-phpstorm.ps1

```powershell
$extensions = @(
"PKief.material-icon-theme",
"zhuangtongfa.Material-theme",
"bmewburn.vscode-intelephense-client",
"xdebug.php-debug",
"onecentlin.laravel-blade",
"eamodio.gitlens",
"usernamehw.errorlens",
"formulahendry.auto-close-tag",
"formulahendry.auto-rename-tag",
"EditorConfig.EditorConfig",
"mhutchie.git-graph",
"Gruntfuggly.todo-tree",
"christian-kohler.path-intellisense",
"esbenp.prettier-vscode",
"k--kato.intellij-idea-keybindings"
)

foreach ($ext in $extensions) {
    code --install-extension $ext
}
```

Ausführen:

```powershell
powershell -ExecutionPolicy Bypass -File .\setup-vscode-phpstorm.ps1
```

---

# 9. Dinge die VS Code NICHT perfekt kann

## Unterschiede zu PHPStorm

### Nicht 100% identisch:

* Deep PHP Refactoring
* Framework-Intelligence
* Doctrine Support
* Symfony Inspections
* Laravel Magic Methods
* Datenbank-Tools
* Remote Deployment
* Advanced Structural Search

---

# 10. Empfehlung für 99% PHPStorm-Feeling

## Beste Kombination

### Extensions

* IntelliJ Keybindings
* Intelephense Premium
* ErrorLens
* GitLens

### Theme

* One Dark Pro
* Material Theme

### Font

* JetBrains Mono

### Settings

* Preview Tabs deaktivieren
* Autosave aktivieren
* Minimap deaktivieren

---

# 11. Bonus: Cursor IDE als Alternative

Falls du zusätzlich AI-Features möchtest:

[Cursor IDE](https://cursor.com/?utm_source=chatgpt.com)

Cursor basiert auf VS Code und fühlt sich oft näher an JetBrains an.

erstellen.
