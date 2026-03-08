# Weaver Playground

**Interactive DataWeave transformation playground for VS Code**

Transform data effortlessly with DataWeave's powerful transformation language. Weaver Playground provides a 3-panel interactive editor with automatic CLI download, intelligent session management, and support for multiple data formats.

![Version](https://img.shields.io/badge/version-1.2.0-blue)
![VS Code](https://img.shields.io/badge/VS%20Code-1.85.0+-green)
![License](https://img.shields.io/badge/license-MIT-orange)
[!["Buy me a coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://buymeacoffee.com/manikanta_nandamuri)
## ✨ Features

### 🚀 Zero Configuration Setup
- **Auto-Download CLI** - Automatically downloads DataWeave CLI on first use
- **No Admin Rights** - Installs to user directory, no elevated permissions needed
- **Cross-Platform** - Works on macOS, Windows, and Linux

### 🎯 Interactive 3-Panel Editor
- **Input Panel** - Paste or load your data
- **Script Panel** - Write DataWeave transformations
- **Output Panel** - See results instantly

### 📊 Multi-Format Support
- JSON, XML, CSV, YAML
- Properties, NDJSON
- Auto-detection from file extensions
- Syntax validation for all formats

### ⚡ Performance Optimized
- **Session-Based Temp Files** - Reuses files for identical content
- **Worker Threads** - Handles large files (>1MB) efficiently
- **Automatic Cleanup** - No orphaned temp files

### 🎨 Developer Experience
- Syntax highlighting for DataWeave
- Real-time validation
- Example templates included
- Auto-execute on file load

## 📦 Installation

### From VS Code Marketplace
1. Open VS Code
2. Go to Extensions (Cmd+Shift+X / Ctrl+Shift+X)
3. Search for "Weaver Playground"
4. Click Install

### From VSIX File
```bash
code --install-extension weaver-playground-1.2.0.vsix
```

## 🎯 Quick Start

1. **Open Playground**
   - Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
   - Type "Weaver Playground: Open Panel"
   - Or click the Weaver icon in the Activity Bar

2. **Try an Example**
   - Click "Examples" button
   - Select "Filter Example"
   - Click "Run" to see the transformation

3. **Load Your Data**
   - Click "Load File" to import data
   - Or paste directly into the Input panel
   - Select the correct input format

4. **Write Transformation**
   ```dataweave
   %dw 2.0
   output application/json
   ---
   payload filter (item) -> item.age >= 18
   ```

5. **Execute**
   - Click "Run" or enable auto-execute
   - View results in Output panel

## 🔧 Configuration

Access settings via `Cmd+,` (Mac) or `Ctrl+,` (Windows/Linux), then search for "wp":

| Setting | Default | Description |
|---------|---------|-------------|
| `wp.cliPath` | (auto) | Custom CLI path (leave empty for auto-download) |
| `wp.autoDownload` | `true` | Automatically download CLI if not found |
| `wp.timeout` | `30000` | Execution timeout in milliseconds |
| `wp.defaultInputFormat` | `application/json` | Default input MIME type |
| `wp.defaultOutputFormat` | `application/json` | Default output MIME type |
| `wp.autoValidate` | `true` | Validate scripts on save |

## 📚 Examples

### Filter Array
```dataweave
%dw 2.0
output application/json
---
payload filter (item) -> item.age >= 18
```

**Input:**
```json
[{"name":"Alice","age":25},{"name":"Bob","age":17}]
```

**Output:**
```json
[{"name":"Alice","age":25}]
```

### Transform Structure
```dataweave
%dw 2.0
output application/json
---
{
  users: payload map {
    fullName: $.name,
    isAdult: $.age >= 18
  }
}
```

### Aggregate Data
```dataweave
%dw 2.0
output application/json
---
{
  total: sizeOf(payload),
  avgAge: avg(payload.age)
}
```

## 🎨 Supported Formats

| Format | Input | Output | Validation |
|------------|-------|--------|------------|
| JSON       | ✅    | ✅     | ✅ |
| XML        | ✅    | ✅     | ✅ |
| CSV        | ✅    | ✅     | ✅ |
| YAML       | ✅    | ✅     | ✅ |
| Properties | ✅    | ✅     | ✅ |
| NDJSON     | ✅    | ✅     | ✅ |

## 🚀 Commands

| Command | Shortcut | Description |
|---------|----------|-------------|
| `wp.openPanel` | - | Open interactive playground |
| `wp.run` | - | Execute current script |
| `wp.validate` | - | Validate script syntax |
| `wp.installCLI` | - | Manually download CLI |
| `wp.openDocs` | - | Open DataWeave documentation |
| `wp.openSettings` | - | Open extension settings |
| `wp.loadExample` | - | Load example transformation |

## 🏗️ Architecture

### Session Management
- Creates unique session directory per VS Code instance
- Reuses temp files based on content hash (MD5)
- Automatic cleanup on extension deactivate
- No duplicate files for identical content

### Worker Threads
- Large files (>1MB) processed in separate thread
- Prevents UI blocking
- Efficient memory usage

### CLI Integration
- Auto-downloads from GitHub releases
- Extracts to user storage directory
- No PATH modification required
- Automatic version detection

## 🐛 Troubleshooting

### CLI Not Found
- Check status bar shows "✓ WP"
- If shows "⚠ WP (No CLI)", run command: "Weaver Playground: Install CLI"
- Verify `wp.autoDownload` is enabled in settings

### Execution Timeout
- Increase `wp.timeout` in settings
- Default is 30 seconds (30000ms)
- Large transformations may need more time

### Validation Errors
- Ensure script starts with `%dw 2.0`
- Check input format matches selected type
- Verify DataWeave syntax is correct


## 📖 Resources

- [DataWeave Documentation](https://docs.mulesoft.com/dataweave/latest/)
- [DataWeave CLI](https://github.com/mulesoft/data-weave-cli)
- [DataWeave Tutorial](https://developer.mulesoft.com/tutorials-and-howtos/dataweave/)


## 📄 License

MIT License - See [LICENSE](https://github.com/nmk32/weaver-playground?tab=MIT-1-ov-file) file for details

## 🙏 Acknowledgments

- Built on [DataWeave CLI](https://github.com/mulesoft/data-weave-cli)
- Powered by [MuleSoft](https://www.mulesoft.com/)
- Community contributions and feedback

## 📊 What's New

### Version 1.2.0
- ✅ Session-based temp file management
- ✅ Intelligent file reuse (no duplicates)
- ✅ Fixed input validation for multiple file formats
- ✅ Automatic session cleanup
- ✅ Performance optimizations

### Version 1.1.0
- ✅ Auto-download CLI feature
- ✅ No admin permissions required
- ✅ Worker threads for large files
- ✅ Improved error handling

---

**Made with ❤️ for the DataWeave community**

[Report Issue](https://github.com/nmk32/weaver-playground/issues) | [Request Feature](https://github.com/nmk32/weaver-playground/issues/new)

## Legal

This extension integrates with the DataWeave CLI (“dw”) from  
https://github.com/mulesoft/data-weave-cli.

DataWeave CLI is licensed under the BSD‑3‑Clause License.  
Full license text is included in `THIRD_PARTY_NOTICES`.

Weaver Playground itself is licensed under the MIT License (see `LICENSE`).

This project is not affiliated with MuleSoft.  
"MuleSoft" and "DataWeave" may be trademarks of their respective owners.
