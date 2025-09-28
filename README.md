# waka-toki-pona
A command-line toolset for processing text in the Toki Pona language.

> [!NOTE]
> This language has two primary writing systems: a script using a subset of the
> Latin alphabet, and a hieroglyphic system called Sitelen Pona. I'll call
> these Latin and Sitelen.

## latin2sitelen & sitelen2latin
These tools transcribe text from Latin to Sitelen, and vice versa.

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
These tools swap Sitelen glyphs with what I call "pseudoglyphs". Until the
Sitelen codepoints officially become part of Unicode, they're unlikely to be
supported by mainstream fonts. In those fonts we can sometimes make do with
these alternative symbols which kind of resemble the proper Sitelen glyphs.

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
> the output of the second command, then this illustrates exactly why these
> tools are needed.


## tokicount
This tool counts features of a given Toki Pona text. For now, only the Latin
script is supported. The countable features are _morae_ and _syllables_. These
stats are most useful in creating poetry.

### usage
```
$ ./tokicount morae < riddle
 7: mi lon insa suno
12: mi lili li kili li kama tan ma
 3: mi seme
$ ./tokicount syllables < riddle
...
```

## sitelenspell
Sitelen is a mostly logographic system, where each glyph represents a whole
word. But the _sounds_ of _proper names_ are enclosed within a cartouche and
represented by glyphs of words which start with those sounds. One or more
phonemes are taken from each word. This system gives the Sitelen writer a lot
of freedom to inject meaning into a name. Take "Sinalela", for instance. This
is a Toki Pona form of the name Cinderella, in the Latin script. In Sitelen, it
can be written with the glyphs for "*sin*a *le*n *la*so", which means "you in
the blue dress". Or as "*sin*pin *ale la*npan", meaning identity thief --
depending on your perspective. This tool aims to help you work out some
creative possibilities, including meaningful and efficient ones.

> [!NOTE]
> This tool is under construction. At present it generates only one spelling, a
> simple but inefficient one that takes just one phoneme from each glyph.
> Output is currently only in Latin, not Sitelen. But I've got big dreams for
> this one.

### usage
```
$ ./sitelenspell Jasimun
jo akesi suwi ijo meli utala nimi
```

## sitelentidy
This tool is a pretty-printer for Sitelen. The text is generally most readable
when verbs of a compound sentence and objects of a compound predicate are
aligned. This is a common Sitelen convention, and one of its benefits is
reduced dependence on punctuation. This tool assumes a monospace font.

```
$ ./sitelentidy < text | ./sitelen2pseudo
🜨◡LႴ[Siko]>⍵≫ꘖ☋⫠
↓)ᓄ>ᐼ≫☋
     ≫↓
ጻꔖ>󱥉≫ꘖKꔖ)🝆
  >⛣≫↓
ꘖ?>◡#1
```
