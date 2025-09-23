# waka-toki-pona
A command-line toolset for processing text in the Toki Pona language.

## latin2sitelen & sitelen2latin
These tools transcribe text from Latin script to Sitelen Pona hieroglyphics,
and vice versa.

### requirements
- python3

### usage
```
$ echo 'sina wile e mani anu seme' | ./latin2sitelen
󱥞󱥷󱤉󱤲󱤇󱥙
$ echo '󱥞󱥷󱤉󱤲󱤇󱥙' | ./sitelen2latin
sina wile e mani anu seme
```

## sitelen2pseudo & pseudo2sitelen
These tools swap hieroglyphic text (consisting of Sitelen Pona glyphs, UCSUR
encoded) for pseudo-hieroglyphics (visual approximations of the proper glyphs,
in official Unicode), and vice versa.

### purpose
Until Unicode officially includes the hieroglyphic symbols of the Toki Pona
language and they're widely supported by mainstream fonts, it is often
necessary to convert to pseudoglyphs.

### requirements
- bash
- perl

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


## tpcount
Given a Toki Pona text in Latin script, this tool counts features in each line.
The features supported are _morae_ and _syllables_. These stats are useful in
creating poetry.

### usage
```
$ ./tpcount syllables < riddle
 6: mi lon insa suno
11: mi lili li kili li kama tan ma
 3: mi seme
$ ./tpcount morae < riddle
 7: mi lon insa suno
12: mi lili li kili li kama tan ma
 3: mi seme
```
