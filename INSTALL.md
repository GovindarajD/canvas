# CEF Canvas Extension - Installation Guide

## Package Information
- **Version:** 0.1.0
- **File:** cef-canvas-extension-0.1.0.vsix
- **Size:** 3.36 MB
- **Location:** `dist\vsix\cef-canvas-extension-0.1.0.vsix`

## Installation Methods

### Method 1: Using VS Code UI (Recommended)
1. Open Visual Studio Code
2. Go to Extensions view (`Ctrl+Shift+X`)
3. Click the `...` menu at the top right
4. Select "Install from VSIX..."
5. Browse to `dist\vsix\cef-canvas-extension-0.1.0.vsix`
6. Click "Install"
7. Reload VS Code when prompted

### Method 2: Using Command Line
```powershell
code --install-extension "dist\vsix\cef-canvas-extension-0.1.0.vsix"
```

### Method 3: Using PowerShell Script
```powershell
# Navigate to workspace
cd "c:\MyWorkspace\CEF\canvas"

# Install extension
code --install-extension "dist\vsix\cef-canvas-extension-0.1.0.vsix" --force

# Verify installation
code --list-extensions | Select-String "cef-canvas"
```

## Verification Steps

After installation:
1. Open Command Palette (`Ctrl+Shift+P`)
2. Type "CEF Canvas"
3. Verify these commands appear:
   - **CEF Canvas: Open Canvas**
   - **CEF Canvas: Load HTML File into Canvas**
   - **CEF Execution: Open Execution View**
   - **CEF Execution: New Document**

## Dependencies Included

This VSIX package includes all required dependencies:
- ✅ TinyMCE Editor (v8.3.2) - Rich text editing
- ✅ Marked (v11.1.1) - Markdown parser
- ✅ SQL.js - Database functionality
- ✅ KaTeX (v0.16.9) - Math rendering
- ✅ Mermaid (v10.7.0) - Diagram rendering
- ✅ DOCX, ExcelJS, PptxGenJS - Export functionality
- ✅ All other npm packages bundled

## Features Included

### Phase 2B Features (Latest)
- ✅ Markdown bullet point conversion
- ✅ AgenticEvaluator quality scoring (4-dimension)
- ✅ Yellow banner structured response display
- ✅ Accept/Reject buttons for fix suggestions
- ✅ Multi-fix sequential application
- ✅ Hover tooltip showing instructions
- ✅ 5000 character text selection limit

### Core Features
- Canvas document system
- Virtual workspace integration
- Inline remarks (Fix, Clarify, Question)
- TinyMCE rich text editor
- Export to DOCX, XLSX, PPTX
- Diagram rendering (Mermaid, PlantUML)
- Math formula support (KaTeX)

## System Requirements
- **VS Code Version:** 1.100.0 or higher
- **Operating System:** Windows, macOS, or Linux
- **Node.js:** Not required (all dependencies bundled)

## Troubleshooting

### Extension Not Loading
1. Check VS Code version: Help → About → Version should be >= 1.100.0
2. Restart VS Code completely
3. Check Output panel: Help → Toggle Developer Tools → Console
4. Look for extension activation errors

### Missing Features or Editor
1. Uninstall extension completely:
   - Extensions view → Find "CEF Canvas" → Uninstall
2. Restart VS Code
3. Reinstall from VSIX
4. Reload window (`Ctrl+R`)

### TinyMCE Editor Not Loading
1. Open Developer Tools: Help → Toggle Developer Tools
2. Check Console for errors
3. Verify webview is loading: Look for "webview-main.js loaded"
4. If issues persist, reinstall extension

### Quality Score Not Showing
1. Ensure you're using Fix remarks (not Clarify or Question)
2. Click "Process" button and wait for evaluation (2-5 seconds)
3. Quality score appears in yellow banner after evaluation completes
4. Check that AgenticEvaluator is enabled in settings

### Tooltip Not Showing Instructions
1. Hover over highlighted text in document
2. Wait 1-2 seconds for tooltip to appear
3. Ensure remarks have instructions/comments entered
4. Tooltip shows original instruction provided when creating remark

## Known Limitations
- Text selection limit: 5000 characters
- TinyMCE runs in webview (some plugins may not work)
- Export features require sufficient memory for large documents

## Build Information
This VSIX was built using the comprehensive build script (`build-vsix.ps1`) with:
- ✅ Full dependency validation
- ✅ TypeScript compilation
- ✅ TinyMCE asset verification
- ✅ Critical file checks
- ✅ Size optimization

## Rebuilding from Source
If you need to rebuild the VSIX:

```powershell
# Verify dependencies
npm run verify

# Build with tests
npm run build

# Build without tests (faster)
npm run build:fast

# Clean build
npm run build:clean
```

## Support and Documentation
- **Extension Logs:** Command Palette → "Developer: Open Extension Logs Folder"
- **Documentation:** See `README.md` in workspace
- **Phase 2B Guide:** See development documentation in workspace
- **Bug Reports:** Check extension console for errors

## Distribution
To distribute this extension:
1. Share the `cef-canvas-extension-0.1.0.vsix` file
2. Provide this INSTALL.md file
3. Ensure recipients have VS Code >= 1.100.0
4. No additional setup required - all dependencies bundled

## Uninstallation
```powershell
code --uninstall-extension cef.cef-canvas-extension
```

Or use VS Code UI:
1. Extensions view (`Ctrl+Shift+X`)
2. Find "CEF Canvas Extension"
3. Click Uninstall

---
**Build Date:** 2026-02-04
**Package Status:** Ready for Distribution ✅
