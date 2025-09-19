# waka-toki-pona

A command-line toolset for processing text written in the Toki Pona language.


## latin2sitelen & sitelen2latin

These tools transcribe text from Latin script to Sitelen Pona hieroglyphics,
and vice versa.


## sitelen2pseudo & pseudo2sitelen

These tools swap hieroglyphic text (consisting of Sitelen Pona glyphs, UCSUR
encoded) for pseudo-hieroglyphics (visual approximations of the proper glyphs,
in official Unicode), and vice versa.


### purpose

Until Unicode officially includes the hieroglyphic symbols of the Toki Pona
language and they're widely supported by mainstream fonts, it is often
necessary to convert to pseudoglyphs.


### usage

```
$ echo '󱤴󱤃 󱤉󱦀' | ./sitelen2pseudo 
ᑭ⭄ ≫ഫ
$ echo 'ᑭ⭄ ≫ഫ' | ./pseudo2sitelen
󱤴󱤃 󱤉󱦀
```

> [!NOTE]
> If you can't see the various symbols in the first command given above or in
> the output of the second command, then this illustrates exactly why this
> script is needed. If you *can* see them, that's fantastic! You still may need
> this sometimes when your font choices are limited.
