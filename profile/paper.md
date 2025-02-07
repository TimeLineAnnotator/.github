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
 - name: Universidade Federal do Rio de Janeiro, Brazil
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
over audio, video and musical scores. Developed in Python with the 
the PyQt UI framework, TiLiA is available primarily as a desktop GUI, but is supported by a command line interface and
a (free and open) online platform where users may upload, view and query 
existing analyses.

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
on the coordination of standards and corpora for formal analysis.

In this digital age, we have also come to expect certain basic interactive
functionality across visual interfaces, such as **resizing**
content to fit the window, keyboard shortcuts, edit history, and so on. Musical contexts extend this with additional
expectations, such as **real-time synchronisation** (a.k.a., audio or
score following), and to win over the community of prospective users,
any such tool will need to represent that community's analytical ideas
in a natural and germane way with minimal UI friction.

// F: I would also mention similar software like AudioTimeline, Dezrann, etc and what TiLIA offers that they do not have. 

In response to these challenges (user-friendly design, interoperable
formats, real-time interactivity ... ), we present 'TiLiA': a timeline
annotator for all.

# Specifications

TiLiA consists of several pieces of software, primarily of its open-source desktop application and command-line interface ADD REPO LINK, but also of a supporting online platform, which we plan to make open-source in the future. The desktop application is developed in Python using the PyQt binding for the Qt UI framework. Automated testing is done with `pytest`, and partially-automated deployment via GitHub Actions. The code base is loosely organized around a MVC pattern, which allows both the CLI and the GUI to benefit from the same backend logic. We provide object-oriented base-classes such as `Timeline`, `TimelineUI` and `TimelineComponent` as a means to promote extensibility and allow for gradual support for ever-wider annotation needs. 

TiLiA is designed both as an environment for *creating* analyses,
particularly where this requires complex alignment with audio/video sources,
and for the (conversion and) *importing* of analyses that originated elsewhere through CSV files. 
This effort thus connects to wider datasets and scholarship, and also to wider
functionality. The [tilia-dcml](add link) repository gives an example of how the TiLiA CLI might be used to visualize data from an external corpus of musical analyses. There is also the possibility to *export* timelines created in TiLiA to a JSON file suitable for processing by other software.

## The desktop application

The main part of TiLiA is a cross-platform WYSIWYG GUI, designed to feel intuitive to anyone who has worked with audiovisual editing software. An annotation is composed of one or more timelines that house annotations that may be aligned to an audio, video, YouTube stream or musical score. The general user benefits from several
*types*  of timelines designed to support conventional formal annotation
and flexible use with a wide range of other analytical styles.
Each of these timeline *types* contains one or more *component* types
(e.g., *markers* for marker timelines) that support several
*properties* to convey information including comments, colour and
labels. 

// Add an image of the UI here

Currently, there are six types of timelines:
- Hierarchy timelines, for representing hierarchical structures
- Marker timelines, for highlight discrete timepoints
- Audiowave timelines, to visually display amplitude graph
- PDF timelines, to synchronize PDF document exhibition with playback
- Score timeline, providing a to-scale and synchronized "piano roll" notation as well as conventional musical notatoin from digital score
- Harmony timelines, for properly-formatted chord symbols and roman numeral analysis 

## Command-line interface
In addition to the desktop GUI and the web app, a **command line
interface** allows the automation of file and timeline creation and
edition, media loading and external data importing. Sequences of
commands can be loaded by the CLI from scripts written in plain text
files. Those tools enable programmatic conversion from various data
formats to TiLiA files.

// F: How can we format this to look different from the rest of the text?

metadata set-media-length 120
timelines add hierarchy --name "Form"
timelines add marker --name "Formal closures"
timelines add hierarchy --name "Harmonic segments"
timelines add beat --name "Measures" --beat-pattern 1
timelines add marker --name "Harmony"
timelines add marker --name "Harm. functions"
timelines add marker --name "Keys"

load-media <path to audio> --scale-timelines yes
metadata set title "Title"
save --overwrite <path to TiLiA file>

## Online platform

The TiLiA desktop application is supported by an [online platform](tilia-app.com). that lets users store, share,
visualize and even query existing analyses. Registration is free and only required when using the
upload function. This reflects a goal of TiLiA to support not only the creation and
storage of analysis in an digital-age manner, but also to support the
still-rare practice of analytical *collaboration* and structured
*searches* on the corpora both which benefit from network effects
facilitated by lower entry barriers.
