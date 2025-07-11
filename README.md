# ChatGPT PDF Export Bookmarklet

This repository contains a single-file bookmarklet (code below) that prepares the ChatGPT web interface for clean PDF export or printing.

## Purpose

After clicking the bookmarklet, you can use **Ctrl+P** (Windows/Linux) or **Cmd+P** (Mac), or select **File > Print** in your browser, to generate a clean, readable PDF of your ChatGPT conversation.

## Features

- Hides sidebar and various UI elements (user avatar, Plus icon, "Skip to content", thread bottom container, etc.)
- Applies custom fonts for better readability
- Prevents message bubbles from being split across printed pages

## Installation & Usage

1. **Copy the entire code below:**

```javascript
javascript:(function(){var customStyles=':not(.katex):not(.katex *) {font-family: Arial, sans-serif !important;}:not(.katex) code:not(.katex *), :not(.katex) span:not(.katex *) {font-family: Menlo, monospace !important;white-space: pre-wrap !important;overflow-wrap: break-word !important;}:not(.katex) .overflow-auto:not(.katex *), :not(.katex *) .overflow-auto {overflow: visible !important;}:not(.katex) .h-full:not(.katex *), :not(.katex *) .h-full {height: auto !important;}:not(.katex) #text:not(.katex *), :not(.katex *) #text {white-space: pre-wrap !important;}@media print {.bg-token-message-surface{break-inside:avoid;page-break-inside:avoid;display:block;}}';var styleSheet=document.createElement('style');styleSheet.type='text/css';styleSheet.innerText=customStyles;document.head.appendChild(styleSheet);var sidebar=document.querySelector('#stage-slideover-sidebar');if(sidebar)sidebar.style.display='none';var plusIcon=document.querySelector('img[alt*=\"Plus\"],[class*=\"plus\"],[data-testid*=\"plus\"],span:has(svg)');if(plusIcon)plusIcon.remove();var avatar=document.querySelector('img[alt*=\"User\"],img[alt*=\"Avatar\"],[class*=\"avatar\"]');if(avatar)avatar.remove();var skip=Array.from(document.querySelectorAll('a,button')).find(function(el){return el.textContent.trim().toLowerCase().includes('skip to content')});if(skip)skip.remove();var ph=document.querySelector('#page-header > div:nth-child(3)');if(ph)ph.remove();var tts=document.querySelectorAll('.text-token-text-secondary');tts.forEach(function(e){e.style.display='none';});var tbc=document.querySelector('#thread-bottom-container');if(tbc)tbc.style.display='none';})();
```

2. **Create a new bookmark in your browser.**
  

- Right-click the bookmarks bar and select "Add page" or "Add bookmark".
- Name it (e.g., `ChatGPT PDF Export`).
- Paste the copied code into the URL/location field.

3. **Navigate to your desired ChatGPT conversation in your browser.**
4. **Click the bookmarklet** to prepare the page for export.
5. **Press Ctrl+P (Windows/Linux) or Cmd+P (Mac), or use File > Print** to open the print dialog and save as PDF.

## What it does

- Hides the sidebar (`#stage-slideover-sidebar`)
- Removes user image, Plus icon, and "Skip to content" button
- Removes the third child of `#page-header` and the thread bottom container
- Hides all elements with `.text-token-text-secondary`
- Prevents message bubbles (`.bg-token-message-surface`) from being split across printed pages
- Applies custom fonts for better readability

---

**Get perfect, clean PDF exports of your ChatGPT conversations!**
