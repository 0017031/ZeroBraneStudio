---
layout: default
title: General Preferences
---

<ul id='toc'>&nbsp;</ul>

To **modify default general preferences**, you can use these commands and apply them
as described in the [configuration](doc-configuration.html) section
and as shown in [user-sample.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/user-sample.lua).
The values shown are the default values.

## General

- `activateoutput = true`: activate Output or Console window on new content added.
- `allowinteractivescript = true`: allow interaction in the output window.
- `autoanalyzer = true`: enable autoanalyzer that adds scope aware indicators to variables (up to v0.50 it was spelled as `autoanalizer`).
- `autorecoverinactivity = 10`: trigger saving auto-recovery after N seconds of inactivity.
- `filehistorylength = 20`: set history length for files.
- `language = "en"`: set the language to use in the IDE; this requires a language file in cfg/i18n directory.
- `projectautoopen = true`: auto-open windows on project switch.
- `projecthistorylength = 15`: set history length for projects.
- `savebak = false`: create backup on file save.
- `singleinstance = true`: enable check that prevents starting multiple instances of the IDE.

## Debugger

- `debugger.allowediting = false`: enable editing of files while debugging.
- `debugger.hostname = "hostname.or.IP.address"`: set hostname to use for debugging.
- `debugger.redirect = nil`: specify how `print` results should be redirected in the application being debugged (0.39+).
Use `'c'` for 'copying' (appears in the application output and the Output panel),
`'r'` for 'redirecting' (only appears in the Output panel),
or `'d'` for 'default' (only appears in the application output).
This is mostly useful for remote debugging to specify how the output should be redirected.
- `debugger.runonstart = false`: execute script immediately after starting debugging.
- `debugger.verbose = false`: enable verbose output.

## Auto-complete and tooltip

- `acandtip.nodynwords = true`: do not offer dynamic (user entered) words;
when set to `false` will collect all words from all open editor tabs and offer them as part of the auto-complete list.
- `acandtip.shorttip = true`: show short calltip when typing; shows long calltip when set to `false`.
- `acandtip.startat = 2`: start suggesting dynamic words after N characters.
- `acandtip.strategy = 2`: method of selecting auto-complete candidates:
    - `0`: substring comparison (`fo`, but not `fb` matches `foo_bar`);
    - `1`: substring leading characters, CamelCase or _ separated (`fo` and `fb`, but not `fa` match `foo_bar`);
    - `2`: leading + any correctly ordered fragments (`fo`, `fa`, `fb`, but not `bf` match `foo_bar`).
- `acandtip.width = 60`: specify width of the tooltip window in characters.
- `autocomplete = true`: enable auto-complete.

## Formats

- `format.menurecentprojects = "%f | %i"`: format of the `Recent Project` menu and the toolbar dropdown.
- `format.apptitle = "%T - %F"`: format of the application title.

Possible placeholder values to use in formats (0.61+):

- `%f`: full project name (project path)
- `%s`: short project name (directory name)
- `%i`: interpreter name
- `%S`: file name
- `%F`: file path
- `%n`: line number
- `%c`: line content
- `%T`: application title
- `%v`: application version
- `%t`: current tab name

## Key mapping

To modify a key mapping for a particular menu item, you can add the following command to your [configuration](doc-configuration.html):
`local G = ...; keymap[G.ID_STARTDEBUG] = "Ctrl-Shift-D"`.
This will modify the default shortcut for `Program | Start Debugging` command.

See an [example in user-sample.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/user-sample.lua#L18),
the description for possible [accelerator values](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/src/editor/keymap.lua#L4),
and the full list of IDs in [src/editor/keymap.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/src/editor/keymap.lua).

## Editor key mapping

The editor component provides its own shortcut handling mechanism linked to specific editor actions.
For example, `Ctrl-D` will duplicate the current line.

The editor provides [default commands](doc-editor-keyboard-shortcuts.html) that can be modified to map to the key combinations you prefer.
To modify the key mapping, you can add the following line to the configuration file:

{% highlight lua %}
editor.keymap[#editor.keymap+1] =
  {('E'):byte(), wxstc.wxSTC_SCMOD_CTRL, wxstc.wxSTC_CMD_LINEEND}
{% endhighlight %}

This will bind `Ctrl-E` combination to remove the line content from the current position to the end of the line.
The description takes four parameters:

- key code, which may be a code for a visible character (`('E'):byte()`) or a [special code](http://www.scintilla.org/ScintillaDoc.html#KeyBindings) (`wxstc.wxSTC_KEY_UP`);
- key modifiers, which is a combination of `wxstc.wxSTC_SCMOD_CTRL`, `wxstc.wxSTC_SCMOD_SHIFT`, `wxstc.wxSTC_SCMOD_META`, and `wxstc.wxSTC_SCMOD_ALT`. On OSX, the Command key is mapped to wxSTC_SCMOD_CTRL and the Control key to wxSTC_SCMOD_META.
- [Keyboard command](http://www.scintilla.org/ScintillaDoc.html#KeyboardCommands), which specify the action that needs to be tied to the key combination;
- operating system, which is one of `'Windows'`, `'Macintosh'`, and `'Unix'` strings. If no operating system is specified, then the combination is available on all systems.

Note that the editor key mapping is different from the IDE key mapping as the former only works when the editor is in focus and the latter may work when other components have focus.
When there is a conflict, the IDE shortcuts take preference over editor shortcuts.

## Command line parameters

(0.50+) Command line parameters can be specified in two ways (for those interpreters that support them):
(1) by going to `Project | Command Line Parameters` and entering command line parameters (if the menu item is disabled, it means that the interpeter doesn't support command line parameters), and
(2) by setting `arg.any` value in the config file. For example, `arg.any = 'a "b c"'` will pass two parameters to the script: `a` and `b c`.

The parameters set using the first option will only be active until you exit the IDE. If you want to remove parameters, set the value to the empty string.

Some interpreters also allow interpreter specific arguments:

- `arg.lua`: sets arguments for Lua interpreters,
- `arg.love2d`: sets arguments for Love2d interpreter, and
- `arg.gslshell`: sets arguments for GSL-shell interpreter.

## Interpreter path

These settings can be used to change the location of the executable file for different interpreters.
In most cases you don't need to specify this as ZeroBrane Studio will check default locations for the executable, but in those cases when auto-detection fails, you can specify the path yourself.
You can use this setting to specify an alternative interpreter you want to use (for example, LuaJIT instead of Lua interpreter).

Note that the **full executable name** is expected, not a directory name. The values shown are examples, not default values.

- `path.lua = 'd:/lua/lua'`: specify path to Lua interpreter.
- `path.love2d = 'd:/lua/love/love'`: specify path to love2d executable.
- `path.moai = 'd:/lua/moai/moai'`: specify path to Moai executable.
- `path.gideros = 'd:/Program Files/Gideros/GiderosPlayer.exe'`: specify path to Gideros executable.
- `path.corona = 'd:/path/to/Corona SDK/Corona Simulator.exe'`: specify path to Corona executable.
- `path.gslshell = [[D:\Lua\gsl-shell\gsl-shell.exe]]`: specify path to GSL-shell executable.
