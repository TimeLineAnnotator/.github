---
title: TiLiA – TimeLineAnnotator
tags:
  - music
  - scores
  - film
  - visualisation
  - data science
authors:
  - name: Felipe D. Martins
    orcid: https://orcid.org/0000-0002-9965-042X
    equal-contrib: true
    affiliation: 1
  - name: Anne Foo
    orcid: https://orcid.org/0009-0003-9839-473X
    equal-contrib: true
    affiliation: 2
  - name: Mark R. H. Gotham
    orcid: https://orcid.org/0000-0003-0722-3074
    corresponding: true # (This is how to denote the corresponding author)
    equal-contrib: true
    affiliation: 3
affiliations:
 - name: Federal University of Rio de Janeiro (UFRJ)
   index: 1
 - name: Durham, England
   index: 2
 - name: KCL, England
   index: 3
date: 2025-02
bibliography: paper.bib

---


# Summary

'TiLiA' (**Ti**me**Li**ne **A**nnotator) is an open-source,
cross-platform graphical user interface designed for creating,
displaying, and interacting in real-time with timeline-style annotations
over audio and video. Developed using the Python programming language
with the PyQt UI framework, TiLiA is available in both a desktop app and
a complementary online platform where users may upload, view and query 
existing analyses.

In addition to the desktop GUI and the web app, a **command line
interface** allows the automation of file and timeline creation and
edition, media loading and external data importing. Sequences of
commands can be loaded by the CLI from scripts written in plain text
files. Those tools enable programmatic conversion from various data
formats to TiLiA files.

Use of the online platform is also free and open.
We require registration only when using the upload function.
This reflects a goal of TiLiA to support not only the creation and
storage of analysis in an digital-age manner, but also to support the
still-rare practice of analytical *collaboration* and structured
*searches* on the corpora both which benefit from network effects
facilitated by lower entry barriers.


# Statement of need

Visual analyses of music have proven to be an enduringly popular,
useful, and versatile tool for conveying a wide range of musical ideas.
As the famous adage goes, 'a picture speaks a thousand words'. As these
analytical images are primarily connected to the *analysis* rather than
the *music*, they are readily useful not only for the already visual
sources of notated music, but also for the much wider range of musical
styles and repertoires that are primarily transmitted without relying on
notation.

And whatever power a *static* image has, an *interactive* one has
considerably more. Formal analysis is one of the most clear
beneficiaries of the visual summary of music. Form can be hard to parse
(especially in real-time) but is often easy to display in relatively
simple, at-a-glance summaries. Some applications offer some basic tools
for this from those really designed for score and/or audio editing, to
those specifically aimed at the task, though only relatively simple
annotations are possible, and take up from the community has been
limited.

Overall, musical scholarship has not yet made the leap into this
technological space with any degree of decisiveness or consistency.
Despite some notable exceptions, even most visually minded music
analysis are consigned to static images embedded in print (or in
e-copies at best) and not subject to the expectations for FAIR,
open-source data sharing that are now *de rigueur* in other fields. Even
among the more computational communities, there has been little progress
on the coordination of standards and corpora for formal analysis. In
response to these challenges (user-friendly design, interoperable
formats, real-time interactivity ... ), we present 'TiLiA': a timeline
annotator for all.

In this digital age, we have come to expect certain basic interactive
functionality across all such visual interfaces, such as **resizing**
content to fit the window. Musical contexts extend this with additional
expectations, such as **real-time synchronisation** (a.k.a., audio or
score following), and to win over the community of prospective users,
any such tool will need to represent that community's analytical ideas
in a natural and germane way with minimal UI friction.

TiLiA supports a wide range of analytical expression by providing
flexible options for users engaging at either the level of the GUI or
the source code. The general user benefits from a WYSIWYG GUI with several
timeline *types*, designed to support conventional formal annotation
and flexible use with a wide range of other analytical styles.
Each of these timeline *types* contains one or more *component* types
(e.g., *hierarchies* for hierarchy timelines) that support several
*properties* to convey information including comments, colour and
labels.

TiLiA is designed both as an environment for *creating* analyses,
particularly where this requires complex alignment with audio/video sources,
and for the (conversion and) *importing* of analyses that originated elsewhere. 
This effort thus connects to wider datasets and scholarship, and also to wider
functionality. For instance, the video-specific features include automatic 
assistance with scene detection, using 
[`PySceneDetect`](https://www.scenedetect.com/)'s `content-aware`.

