# HamletRNAWorld (jtrotsky's fork)

Simulated *C. elegans* worms crawl over a field of words from *Hamlet* and eat
the words they touch. The words a worm eats, in order, are its poem. A Claude
model scores the poems, and the worms' connectomes evolve towards higher
scores.

**This is a fork.** The project is [Yitong Tseo](https://github.com/YitongTseo)'s,
and the current code lives upstream at
[YitongTseo/HamletRNAWorld](https://github.com/YitongTseo/HamletRNAWorld). The
live site is [wordswordsworms.org](https://wordswordsworms.org). This fork's
`main` is an old snapshot from August 2026. Read and run the upstream repo.

![One worm in the Vivarium viewer](docs/vivarium-focus.png)

*One worm in the Vivarium viewer, which I built in
[#5](https://github.com/YitongTseo/HamletRNAWorld/pull/5). The panel at top
left counts the words it has eaten. Screenshot from an August 2026 build.*

## What I contributed

Seven pull requests, all merged upstream:

| PR | What it did |
|---|---|
| [#1](https://github.com/YitongTseo/HamletRNAWorld/pull/1) | Fixed comments and docs that had drifted from the code |
| [#5](https://github.com/YitongTseo/HamletRNAWorld/pull/5) | Lifelike mode (plasticity, hunger, habituation). The *Tao Te Ching*, *Beowulf* and 道德經 flasks, with smell, grammar and judging for each text. The Vivarium viewer. A judge backend for any OpenAI-compatible model. |
| [#6](https://github.com/YitongTseo/HamletRNAWorld/pull/6) | Measured whether selection works, and found it did not (below). Added shared seeds per flask and a tunable judge sample. |
| [#7](https://github.com/YitongTseo/HamletRNAWorld/pull/7) | `/debug/objects`, which counts live worlds to help find a slow memory leak |
| [#8](https://github.com/YitongTseo/HamletRNAWorld/pull/8) | Merged two lines of development that had fixed the same bug two ways |
| [#9](https://github.com/YitongTseo/HamletRNAWorld/pull/9) | Fixed a gene migration that would have stopped evolution on three of four processes |
| [#10](https://github.com/YitongTseo/HamletRNAWorld/pull/10) | Cut the gardener's API cost with prompt caching and a run-every-Nth-epoch setting |

## Has it learned anything?

Not yet, as far as anyone has shown. On 1 September 2026 a test compared
genomes kept from the previous generation against fresh mutants, over 153
generations of one lineage. The kept genomes should have won. They did not:
Cohen's d = −0.009, 95% CI [−0.080, +0.061]. Selection could not tell two
genomes apart. Shared seeds and one judge per lineage followed (#6). Whether
the worms now learn is untested. The upstream `CLAUDE.md` keeps the record.

## Credits

HamletRNAWorld is Yitong Tseo's work, from the simulation and viewer to the
judge and evolution. It builds on the *C. elegans* connectome port in
[heyseth/worm-sim](https://github.com/heyseth/worm-sim), texts from
[Project Gutenberg](https://www.gutenberg.org), and
[nomic-embed-text-v1.5](https://huggingface.co/nomic-ai/nomic-embed-text-v1.5)
with NLTK for the smell and grammar channels.
