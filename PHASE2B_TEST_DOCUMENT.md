# Phase 2B Test Document

## Introduction

This document is designed to test Phase 2B features of the CEF Canvas Extension. Use the test scenarios below to verify markdown conversion, quality evaluation, and other Phase 2B enhancements.

## Test Scenario 1: Basic Markdown Conversion

This is a simple paragraph that needs improvement. It lacks detail and structure.

**Test this:** Select the paragraph above, press Ctrl+K, and type:
```
Please expand with bullet points and add bold headings
```

**Expected Result:**
- Paragraph converted to bullet list with `<ul><li>` tags
- Bold text using `<strong>` tags
- Proper HTML formatting

## Test Scenario 2: Quality Evaluation

The system works fine. Everything is good. No problems detected.

**Test this:** Select the lazy response above, press Ctrl+K, and type:
```
Please give more explanation and specific details
```

**Expected Result:**
- AgenticEvaluator detects minimal change (<10%)
- Console shows: `[AgenticEvaluator] Quality score: X.XX`
- AI provides substantial rewrite with details

## Test Scenario 3: Anti-Pattern Detection

Please update this paragraph to include the following improvements: add more detail, use bullet points, and improve clarity.

**Test this:** This text contains instruction leakage. Ask AI to rephrase it.

**Expected Result:**
- AgenticEvaluator detects instruction text pattern
- Quality score penalized (completeness < 0.5)
- AI provides clean output without instructions

## Test Scenario 4: Nested Lists

Create a simple list here:
- Item 1
- Item 2
- Item 3

**Test this:** Select the list and ask:
```
Convert to nested list with sub-items
```

**Expected Result:**
```html
<ul>
  <li>Item 1
    <ul>
      <li>Sub-item 1.1</li>
      <li>Sub-item 1.2</li>
    </ul>
  </li>
  <li>Item 2</li>
</ul>
```

## Test Scenario 5: Code and Formatting

Some text with inline code and formatting needs.

**Test this:** Ask AI to add:
```
Add inline code examples and format with bold/italic
```

**Expected Result:**
- Inline code: `<code>example</code>`
- Bold: `<strong>text</strong>`
- Italic: `<em>text</em>`

## Test Scenario 6: Comprehensive Rewrite

Short text.

**Test this:** Select and type:
```
Please provide a comprehensive analysis with multiple sections, each containing detailed bullet points with bold headings
```

**Expected Result:**
- Multiple sections with headings
- Bullet lists with bold labels
- Substantial content (>500 characters)
- Quality score > 0.80

## Performance Benchmarks

| Feature | Phase 2A | Phase 2B Target | Status |
|---------|----------|-----------------|--------|
| Token Cost per Remark | ~5,000 | ~300-500 (96% savings) | ⏳ Wired |
| Quality Score | ~0.65 | ~0.85 (+29%) | ✅ Active |
| Anti-Pattern Detection | None | 3 patterns | ✅ Active |
| Markdown Support | Basic | Full (nested, code, etc.) | ✅ Active |

## Verification Checklist

Before testing, verify these console logs appear on extension load:

- [ ] `[Phase 2B] Initializing LLMProviderFactory...`
- [ ] `[Phase 2B] LLM Provider initialized: VS Code Copilot`
- [ ] `[Phase 2B] AgenticEvaluator initialized (max 3 iterations, threshold 0.75)`

During testing, watch for these logs:

- [ ] `[RemarkService] Markdown detected, converting to HTML...` (if backend path used)
- [ ] `[CEF Canvas] Detected bullet list, converting to HTML` (if webview path used)
- [ ] `[AgenticEvaluator] Quality score: X.XX (completeness: X.XX, accuracy: X.XX)`
- [ ] `[AgenticEvaluator] Response below threshold...` (if quality < 0.75)

## Advanced Tests

### Test 7: LLM Provider Switching

1. Open VS Code Settings (Ctrl+,)
2. Search for `cefCanvas.llm.provider`
3. Change to `openai` or `anthropic`
4. Set environment variable: `OPENAI_API_KEY=sk-...`
5. Reload window (Ctrl+Shift+P → "Reload Window")
6. Check console: `[Phase 2B] LLM Provider initialized: OpenAI`

### Test 8: Undo/Redo

1. Make a change to the document
2. Press **Ctrl+Z** (Undo)
3. Press **Ctrl+Shift+Z** (Redo)

**Expected:**
- Undo reverts last change
- Redo reapplies it
- Canvas updates immediately

### Test 9: Quality Threshold

Create a remark that asks for minimal changes. The evaluator should:
1. Detect low quality (< 0.75)
2. Log warning in console
3. (Future) Auto-refine response

## Troubleshooting

**Markdown not converting?**
- Check console for conversion logs
- Webview conversion happens in browser (webview-main.js)
- Backend conversion happens in extension host (RemarkService.ts)

**No quality scores?**
- Ensure you're testing 'fix' type remarks (not 'ask' or 'explain')
- Check console for `[AgenticEvaluator]` prefix
- Evaluation runs asynchronously (won't block UI)

**Undo/Redo not working?**
- Ensure `cefCanvasActive` context is set
- Check keybindings with Ctrl+K Ctrl+S (Keyboard Shortcuts)

## Success Criteria

✅ **Phase 2B Backend Complete** if:
- All 3 providers initialize (Copilot by default)
- AgenticEvaluator shows quality scores in console
- Markdown converts to proper HTML (bullets, bold, lists)
- No TypeScript compilation errors
- 48/48 backend tests pass

🎯 **Next Steps:**
- Complete token optimization (CanvasQueryHandler wiring)
- Write unit tests (target >85% coverage)
- Performance benchmarks (measure actual token savings)
- User acceptance testing

---

**Document Version:** 1.0  
**Test Date:** February 4, 2026  
**Phase:** 2B Integration Complete
