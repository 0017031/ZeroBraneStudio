---
layout: default
title: Styles and Color schemes
---

<ul id='toc'>&nbsp;</ul>

To **modify colors and appearance** of text, markers, or indicators in the editor and Output/Console panels,
you can use these commands and apply them as described in the [configuration](doc-configuration) section
and as shown in [user-sample.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/user-sample.lua).

## Example

The following configuration will set text background to be light red: `styles.text = {bg = {250,200,200}}`.

## Style attributes

- `fg`: foreground; a table with three color components `{red,green,blue}` (0-255)
- `bg`: background; a table with three color components `{red,green,blue}` (0-255)
- `alpha`: translucency; 0-255 (0 - transparent, 255 - opaque, 256 - opaque/faster)
- `sel`: color of the selected block (only applies to folds); `{red,green,blue}` (0-255)
- `u`: underline; boolean value
- `b`: bold; boolean value
- `i`: italic; boolean value
- `fill`: fill to the end of line; boolean value
- `fn`: font face name; string ("Lucida Console")
- `fs`: font size; number (11)

## Style elements

See [style.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/src/editor/style.lua#L26-L88) for the complete list of elements
and [tomorrow.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/tomorrow.lua) for an example of how these elements can be used.

(**v0.50+**) `alpha` attribute is supported for `sel`, `seladd`, and `caretlinebg` style elements.

## Indicators

(**v0.38+**) Indicators add visual elements to the text in the editor, for example, a dotted underline for local variables or a solid line for global ones.

- `styles.indicator.fncall`: function call
- `styles.indicator.varlocal`: local variable
- `styles.indicator.varglobal`: global variable
- `styles.indicator.varmasking`: masking variable -- a local variable masking another variable in the same block
- `styles.indicator.varmasked`: masked variable -- a local variable being masked by another variable in the same block
- `styles.indicator.varself`: implicit `self` variable used in functions defined with colon syntax (**v1.61+**)

You can change the color of an indicator (by setting its `fg` property), its type (by setting its `st` property) or disable it by setting its value to `nil`:

- `styles.indicator.fncall = {st = wxstc.wxSTC_INDIC_PLAIN, fg = {240,0,0}}`: set color and type
- `styles.indicator.fncall = {fg = {240,0,0}}`: set color
- `styles.indicator.fncall = nil`: disable the indicator

If you want to **disable an indicator**, set its value to `nil`: `styles.indicator.varlocal = nil`.
If you want to **disable all indicators**, use `styles.indicator = {}`.

## Indicator types

The following list shows possible **indicator types**:

- `wxstc.wxSTC_INDIC_DOTS`: Dotted underline
- `wxstc.wxSTC_INDIC_PLAIN`: Single-line underline
- `wxstc.wxSTC_INDIC_TT`: Line of T-shapes
- `wxstc.wxSTC_INDIC_STRIKE`: Strike-out
- `wxstc.wxSTC_INDIC_SQUIGGLE`: Squiggly underline
- `wxstc.wxSTC_INDIC_SQUIGGLELOW`: Squiggly underline (2 pixels)
- `wxstc.wxSTC_INDIC_SQUIGGLEPIXMAP`: Similar to `INDIC_SQUIGGLE`, but draws a pixmap instead of a series of line segments for performance (**v1.40+**)
- `wxstc.wxSTC_INDIC_BOX`: Box
- `wxstc.wxSTC_INDIC_ROUNDBOX`: Rounded Box
- `wxstc.wxSTC_INDIC_STRAIGHTBOX`: Box with trasparency
- `wxstc.wxSTC_INDIC_DOTBOX`: Dotted rectangle
- `wxstc.wxSTC_INDIC_FULLBOX`: Rectangle around the text using translucent drawing similar to `INDIC_STRAIGHTBOX` but covering the entire character area (**v1.40+**)
- `wxstc.wxSTC_INDIC_DASH`: Dashed underline
- `wxstc.wxSTC_INDIC_DIAGONAL`: Diagonal hatching
- `wxstc.wxSTC_INDIC_TEXTFORE`: Changes the colour of the text (**v1.40+**)
- `wxstc.wxSTC_INDIC_HIDDEN`: No visual effect

See [Scintilla documentation](http://www.scintilla.org/ScintillaDoc.html#SCI_INDICSETSTYLE) for indicator style examples.

## Color schemes

Color schemes allow configuring colors and attributes in coordinated set.
See [tomorrow.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/tomorrow.lua) for an example of how these colors and attributes can be manipulated,
[scheme-picker.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/scheme-picker.lua) for how they can be used,
and [user-sample.lua](https://github.com/pkulchenko/ZeroBraneStudio/blob/master/cfg/user-sample.lua#L83-L88) for how a color scheme can be configured.
