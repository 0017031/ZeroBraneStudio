---
layout: default
title: General Preferences
---

To **modify default general preferences**, you can use these commands and apply them
as described in the [configuration](doc-configuration.html) section
and as shown in [user-sample.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/user-sample.lua).
The values shown are the default values.

## General

- `activateoutput = true`: activate Output or Console window on new content added.
- `allowinteractivescript = true`: allow interaction in the output window.
- `autoanalizer = true`: enable autoanalizer that adds scope aware indicators to variables.
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
Use `c` for 'copying' (appears in the application output and the Output panel), `r` for 'redirecting' (only appears in the Output panel), or `d` for 'default' (only appears in the application output).
This is mostly useful for remote debugging to specify how the output should be redirected.
- `debugger.runonstart = false`: execute script immediately after starting debugging.
- `debugger.verbose = false`: enable verbose output.

## Auto-complete

- `acandtip.nodynwords = true`: do not offer dynamic (user entered) words;
when set to `false` will collect all words from all open editor tabs and offer them as part of the auto-complete list.
- `acandtip.shorttip = true`: show short calltip when typing; shows long calltip when set to `false`.
- `acandtip.startat = 2`: start suggesting dynamic words after N characters.
- `autocomplete = true`: enable auto-complete.

## Interpreter Path

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
