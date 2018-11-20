# Elektrical Symbol Library for Inkscape

This is a SVG file that can be used as symbol library for Inkscape.

## Install

The file must be copied into the "symbols" folder of inkscape.

On Linux, this is `$HOME/.config/inkscape/symbols/` or `/usr/share/inkscape/symbols/`.

On Windows, this is `C:\Program Files\Inkscape\share\symbols`.

On OSX, this is `/Applications/Inkscape.app/Contents/Resources/share/inkscape`

## Usage

In Inkscape, open the "Symbols" dialog (SHIFT+CTRL+Y), select 
"Electrical symbols" from the drop down menu and drag the symbols into the document.

## Editing

If you edit this file in inkscape, you have to do some post-processing in the file's
source. Every `style="fill:#rrggbb` must be replaced with an attribute 
`fill="param(fill) #rrggbb"` and every `style="stroke:#rrggbb"` must be
replaced with `stroke="param(outline) #rrggbb" strike-width="param(outline-width) 1"`,
with the exception for the root element where the colors must still be defined in the
`style` attribute.

I'm using these VIM commands for these changes:

```vim
" This will match the root element
%s/^   style=/   stylex=/
" Replace all stroke styles
%s/\(style="[^"]*;\?\)stroke:#ff0000;\?/stroke="param(outline) #F00" stroke-width="param(outline-width) 1" \1/g
" Replace all fill styles
%s/\(style="[^"]*;\?\)fill:#ff0000;\?/fill="param(fill) #F00" \1/g
" Restore root's style
%s/^   stylex=/   style=/
```


