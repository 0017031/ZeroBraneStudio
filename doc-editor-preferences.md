---
layout: default
title: Editor Preferences
---

To **modify default editor preferences**, you can use these commands and apply them 
as described in the [configuration](doc-configuration.html) section
and as shown in [user-sample.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/user-sample.lua).
The values shown are the default values.

## Editor

- `editor.autoactivate = false`: auto-activate files during debugging.
- `editor.autoreload = false`: auto-reload externally modified files (if no conflict detected).
- `editor.autotabs = false`: use tabs if detected.
- `editor.calltipdelay = 500`: calltip delay (assign `nil` or `0` to disable).
- `editor.caretline = true`: show caret line.
- `editor.checkeol = true`: check for mixed end-of-line encodings in loaded files (assign `nil` or `false` to disable).
- `editor.defaulteol = nil`: default EOL encoding (`wxstc.wxSTC_EOL_CRLF` or `wxstc.wxSTC_EOL_LF`).
- `editor.extraascent = nil`: extra spacing (in pixels) between editor lines (0.51+).
- `editor.fold = true`: enable folding (0.39+).
- `editor.foldcompact = true`: set compact fold that includes empty lines after a block.
- `editor.fontname = "Courier New"`: set font name.
- `editor.fontsize = 11`: set font size (the default value is `12` on OSX).
- `editor.nomousezoom = false`: disable zoom with mouse wheel as it may be too sensitive.
- `editor.saveallonrun = nil`: save modified files before executing Run/Debug commands (0.39+).
- `editor.smartindent = true`: use smart indentation.
- `editor.showfncall = true`: mark function calls.
- `editor.tabwidth = 2`: set tab width.
- `editor.usetabs = false`: enable using tabs.
- `editor.usewrap = true`: wrap long lines.
- `editor.whitespace = false`: display whitespaces.

## Output and Console

- `outputshell.fontname = "Courier New"`: set font name.
- `outputshell.fontsize = 10`: set font size (the default value is `11` on OSX).
- `outputshell.nomousezoom = false`: disable zoom with mouse wheel in Output/Console windows as it may be too sensitive.

## Project/Filetree

- `filetree.fontname = nil`: set font name; Project/Filetree window has no default font as it is system dependent.
- `filetree.fontsize = 10`: set font size (the default size is `11` on OSX).
