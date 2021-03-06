<div>
<img src="docs/images/logo.png" align="left" width="300"/>
<img src="docs/images/huygenslogo.png" align="right" width="200"/>
<img src="docs/images/tf.png" align="right" width="200"/>
<img src="docs/images/dans.png" align="right" width="100"/>
</div>

# General Missives

[![SWH](https://archive.softwareheritage.org/badge/origin/https://github.com/Nino-cunei/oldassyrian/)](https://archive.softwareheritage.org/browse/origin/?origin_url=https://github.com/Dans-labs/clariah-gm)

[![DOI](https://zenodo.org/badge/292204502.svg)](https://zenodo.org/badge/latestdoi/292204502)


Status
------

This is **work in progress!**

*   2021-01-30 A new TF version (0.7) has been delivered.
    This  version as a major encoding difference: whereas in version 0.6 footnote material ended
    up in the values of a feature, now footnotes are treated like text material.
    That means: the words in footnotes occupy slots, the footnotes themselves are nodes.
    As a consequence, footnotes and the words in it can be annotated, e.g. with named entities.
    This is a reuqirement for the kind of processing that Sophie Arnoult is currently devising.
*   2020-12-07 A new TF version (0.6) has been delivered.
    Fixed some folio references.
    Also: a simple data export has been made: a csv file with all the words, and for each
    word whether it is editorial or original, and if a word has a footnote, the footnote is
    also given. See the
    [export notebook](https://nbviewer.jupyter.org/github/Dans-labs/clariah-gm/tree/master/usage/SimpleData.ipynb).
    The
    [exported data](https://github.com/Dans-labs/clariah-gm/releases/download/v0.6/words.tsv.gz)
    is attached to this release.
*   2020-11-24 Experimenting with a [Blacklab](http://inl.github.io/BlackLab/index.html) interface.
*   2020-11-17 A new TF version (0.5) has been delivered
    Fixed the generation of spurious newlines in footnote bodies.
*   2020-11-16 A new TF version (0.4) has been delivered
    Footnote bodies and marks have been checked and corrected, all encoded footnote marks
    have been linked to all encoded footnote bodies.
    Docs have been updated, and tutorials have been written.
*   2020-10-13 A new TF version (0.3) has been delivered
    Footnote bodies are almost all checked and corrected (12247 in total),
    footnote marks have been checked
    en corrected for volumes 1-4, there remain at least (300) pages with unlinked footnotes
    out of the 5270 pages that have footnotes.
    Editorial text is now in the main text, on equal footing with the original letter content,
    but separable from it in a number of ways.
*   2020-10-13 A new TF version (0.2) has been delivered, and there is now a TF-app
    [missieven](https://github.com/annotation/app-missieven) for this corpus.
    That means that functions like the Text-Fabric browser and easy downloading of data are supported.
    There is still cleaning work to do, especially in linking the footnotes to the proper
    footnote references.
    There are also a few mis-encoded tables (from landscape format), that need manual adjustment,
    and some pages that are altoghether missing.
    See [trimTei0.py](https://github.com/Dans-labs/clariah-gm/blob/master/programs/trimTei0.py) where some of those
    pages have already been added.
*   2020-10-07 Many checks have been performed, many structural corrections
    w.r.t the TEI source have been performed,
    the metadata of all metadata has been thoroughly checked and corrected.
    See the reports in
    [trimreport2](trimreport2).
*   2020-09-16 First TF dataset created, but incomplete (notes are left out, checks needed)
    See 
    [last trimTei run](log-trimTei.txt)
    and
    [last tfFromTrim run](log-tfFromTrim.txt)
*   2020-09-02 Repository created, no content yet, start of conversion coding.

Corpus
------

This repo contains a structurally clean version of the data of the *General Missives*.

The *Generale Missiven* is a collection of letters from governors of the
VOC (Dutch East Indian Company) to
the *Heren 17*, the council of the governors of the 17 provinces of the Netherlands,
which was the effective
government of the Low Countries at the time of the 17th and 18th century.

The letters comprise 13 volumes and date from 1610 to 1761.

The Huygens-ING institute publishes this material:
[General Missives Website](http://resources.huygens.knaw.nl/retroboeken/generalemissiven/#page=0&accessor=toc&view=homePane),
see also
[General Missives Project](http://resources.huygens.knaw.nl/vocgeneralemissiven);
both websites are in Dutch.

The CLARIAH project uses a TEI version of this corpus in its Work Package 6 which deals with
new infrastructure for academic text processing:
[WP6-Text](https://www.clariah.nl/en/work-packages/focus-areas/text?layout=blog).
That work is conducted and carried out by

* [Lodewijk Petram](https://www.lodewijkpetram.nl) (HuygensING)
* [Jesse de Does](https://www.researchgate.net/profile/Jesse_De_Does) (INT)
* [Sophie Arnoult](http://www.illc.uva.nl/People/person/3601/Ir-Sophie-Arnoult)

This repo does not publish the source/intermediate data as developed in CLARIAH-WP6;
they will publish their materials in due course.

# Rationale for this representation of the corpus

Cleaning a textual dataset is a lot of work.
If such a dataset is a standard work, it will be studied by many students/researchers from several
disciplines. 
To make life easier for those people, they should be able to start with a dataset that is readily
processable by any tool of their choice.

[Text-Fabric](https://github.com/annotation/text-fabric)
provides a
[data model](https://annotation.github.io/text-fabric/tf/about/datamodel.html)
that captures the data at the end of the cleaning process just
before it goes into other tools.
It also support the integration of subsequent enrichment with the original data.

The Missieven corpus is an example how that works.

# Getting started

Start with the
[tutorial](https://nbviewer.jupyter.org/github/annotation/tutorials/blob/master/generalmissives/start.ipynb).

See
[other corpora](https://annotation.github.io/text-fabric/tf/about/corpora.html)
for more experiences with Text-Fabric as a corpus pre-processing tool.

Text-Fabric operates in the ecosystem of Python and its libraries
and is particularly suited to Jupyter notebooks and lab.

# Conversion steps

The CLARIAH WP6 people kindly provided me with a TEI version of the corpus.

However, this TEI version contains many inaccuracies.
There are many instances of miscategorized material:
page headers and footers end up in body text and vice versa;
editorial notes and footnotes are not always properly detected; dozens of letters have not been separated;
metadata is often incorrect.

In order to produce a quality dataset, I needed to do something about it: checks and corrections.

1. all metadata has been freshly distilled from the letter headings, an in case of doubt the
   online images of the missives have been inspected.
2. all footnote marks are linked to all footnote bodies.
   It is still possible that there are missed footnotes and missed footnote marks,
   but chances are slim because footnote marks and footnote bodies are detected
   independently.

Yet, most OCR errors within words and numbers are mostly untouched.
The main concern was to get a correct separation between the kinds of text:

* original letter
* editorial text
* footnotes
* page headers and footers

[trimTei.py](https://github.com/Dans-labs/clariah-gm/blob/master/programs/trimTei.py)
consists of a battery of 4 conversions to clean the incoming TEI ,
leaving out all bits that do not end up in the final dataset,
and reorganizing some material to facilitate the conversion to TF.

The first result of the laundry is a set of XML files, which contain a clean, simplified TEI-like
encoding of the material, with all non-essential parts stripped, such as page headers and footers,
title pages, etc.
There is also an exact correspondence between files and letters.

Then I used the
[walker module from TF](https://annotation.github.io/text-fabric/tf/convert/walker.html)
to turn the simple XML into Text-Fabric.
See
[tfFromTrim.py](https://github.com/Dans-labs/clariah-gm/blob/master/programs/tfFromTrim.py).

For details about the features of the end result, see 
[transcription](docs/transcription.md)

# Using this corpus data

At the moment the data delivered is available

* as simple, TEI-like XML (see the xml directory in this repo)
* as plain text-fabric files (see the tf directory in this repo)

You can fire up a Text-Fabric browser and Query tool for this data by installing text-fabric and running
a command:

* have Python installed (at least 3.6)
* `pip3 install text-fabric`
* `text-fabric missieven:latest --checkout=latest`

This will download the corpus and fire up a local webserver and your webbrowser pointing to a in interface
for this corpus.

Another version of the data (less cleaned) is visible online in a
[Blacklab interface ](http://corpora.ato.ivdnt.org/corpus-frontend/Missiven/search/)

The next step is to make the data of this repository available in a Blacklab interface.
In this repo we show how to set up a local Blacklab server and front-end and how to get the
present data into Blacklab.

**This is work in progress**, at this point follow the
[blacklab install guide for macos](https://github.com/Dans-labs/clariah-gm/blob/master/blacklab/install.md).

Thanks to Jesse de Does (key user of Blacklab, INT) and
Jan Niestadt (main author of Blacklab, INT) for helping out with setting up and using Blacklab.

# Authors

This repo is by

*   [Dirk Roorda](https://pure.knaw.nl/portal/en/persons/dirk-roorda) at
    [DANS](https://www.dans.knaw.nl)

with the help of the people mentioned above.

**N.B.:** Releases of this repo have been archived:

* at [Zenodo](https://zenodo.org)
* at [Software Heritage](https://archive.softwareheritage.org)

Click the respective badges above to be taken to the archives.
There you find ways to cite this work.
