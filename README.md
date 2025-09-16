# sitelen2pseudo
Command-line glyph converter from Sitelen Pona UCSUR to official Unicode approximations

## purpose
Until Unicode officially includes hieroglyphics of the Toki Pona language and they're widely supported by mainstream fonts, it is often necessary to convert to what I call pseudoglyphs: alternative symbols that approximate the appearance of the intended glyphs.

## usage
```
$ echo '󱤴󱤃 󱤉󱦀' | ./sitelen2pseudo 
ᑭ⭄ ≫ഫ
$ echo 'ᑭ⭄ ≫ഫ' | ./sitelen2pseudo --reverse
󱤴󱤃 󱤉󱦀
```
> [!NOTE]
> If you can't see the various symbols in the first command given above or in the output of the second command, then this illustrates exactly why this script is needed. If you *can* see them, that's fantastic! You still may need this sometimes when your font choices are limited.
