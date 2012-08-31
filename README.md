## About this work
This presentation was given as part of a [talk series][acm-talks] put on
by the [NUS Student Chapter of the ACM][nusacm] on August 30th, 2012.

## Synopsis/promotional tagline

> An introduction to bioinformatics- an expanding field focused on
> solving biological problems through applications of computer science.
> The talk includes a survey of common procedures, algorithms, and tools
> used in this fast-growing field.

## Extra-slide demonstrations
- A [`clustalx`][clustal] alignment was performed on the sequences within
  `H1N1_seqs.fasta` as part of an exploration of sequences.
- The PyMOL sessions `alpha.pse` and `beta.pse` were used when discussing
  secondary structures
- The PyMOL session `1ktr.pse` demonstrates docking software's predictive
  capabilities on real-world data.

## Modifying/distributing this presentation
The source of the slide show, `slides.md` is written in an extension of
Markdown, [Pandoc's markdown][pandoc-markdown]. That is, it has some
features not within the standard implementation of Markdown as well as
some HTML and Latex constructs.

To render the presentation in the style of the provided PDF, one should
install [Pandoc][pandoc], and run the following:

    $ pandoc -t beamer -V theme:Warsaw -s slides.md -o pres.pdf

Myriad other output formats are available. For more information, see the
[Pandoc README][pandoc-readme].


## License
The content of this presentation is released under the GPL, v.3. The
images used within are governed by the terms of their respective
licenses, which may not be compatible with the GPL. See the LICENSE file
for details.


  [acm-talks]: http://nusacm.org/events/talks/index.html
  [nusacm]: http://nusacm.org/index.html
  [pandoc]: http://johnmacfarlane.net/pandoc
  [pandoc-markdown]: http://johnmacfarlane.net/pandoc/demo/example9/pandocs-markdown.html
  [pandoc-readme]: http://johnmacfarlane.net/pandoc/README.html

  [clustal]: http://www.clustal.org
