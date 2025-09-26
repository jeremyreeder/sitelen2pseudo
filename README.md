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


## tokicount
Given a Toki Pona text in Latin script, this tool counts features of each line.
The features supported are _morae_ and _syllables_. These stats are useful in
creating poetry.

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
This tool suggests hieroglyphic spellings of a proper noun. Unlike the Latin
script, in Sitelen Pona there are often many ways to represent a given sequence
of syllables. Some are more efficient than others, and some may use symbols
that the name's owner would prefer to be associated with. These can be
challenging to work out manually.

> [!NOTE]
> This tool is under construction. At present it generates only one spelling,
> taking one phoneme from each glyph, and outputs the transcription only in the
> Latin script with the pronounced phonemes in bold. Generation of more
> efficient spellings in the Nasin Sitelen Kalama style is planned, and output
> is planned to include the actual hieroglyphics.

### usage
```
$ ./sitelenspell Jasimun
jo akesi suwi ijo meli utala nimi
```

## sitelentidy
This tool is a pretty-printer for Sitelen Pona hieroglyphic text. In this
writing system, sentences are most readable when verbs of a compound sentence
and objects of a compound predicate are aligned. For such alignment, this tool
assumes a monospace font.

```
$ ./sitelentidy < text | ./sitelen2pseudo
🜨◡LႴ[Siko]>⍵≫ꘖ☋⫠.
↓)ᓄ>ᐼ≫☋
     ≫↓:
ጻꔖ>󱥉≫ꘖKꔖ)🝆
  >⛣≫↓:
ꘖ?>◡#1.
```
